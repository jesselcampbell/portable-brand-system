---
title: Portable Brand System spec
type: meta
spec_version: 0.1.0
description: The Portable Brand System specification, not the brand itself. How every file in this package is structured, document types, frontmatter, body pattern, fixed and flexible rules, tokens, prompts, and default sections per file. Examples are illustrative, not rules for the brand contained.
---

# Portable Brand System spec

Here we outline the default sections and formatting for every document in a Portable Brand System (PBS). The goal is that any file, opened by a person or an AI, reads the same way: what it is, what's fixed, what can flex, and why.

## Document types

Every file is one of four types.

| Type        | Lives in                                                                          | Mode                                                       | Contains rules |
| ----------- | --------------------------------------------------------------------------------- | ---------------------------------------------------------- | -------------- |
| `meta`      | `README.md`, `CHANGELOG.md`, `CONTRIBUTING.md`, `GLOSSARY.md`, `design/DESIGN.md` | Orientation. Indexes, summaries, how the system works.     | Summaries      |
| `guideline` | `brand/`, `design/`                                                               | Prescriptive. Rules, guidance, examples, rationale.        | Yes            |
| `profile`   | `profiles/`                                                                       | Descriptive. Maintained facts with sources.                | No             |
| `source`    | `resources/`                                                                      | Evidence. Dated, never edited after the fact, never canon. | No             |

## Shared conventions

### Frontmatter

Every file starts with some minimal frontmatter. `description` is what an agent reads to decide whether to load the file, so it carries real information, not a label.

```yaml
---
title: Voice
type: guideline
description: How Kurnl sounds, how tone shifts by context, and the words we use and avoid.
---
```

`source` files add `date`, `author` and `method`.

### Body pattern

1. **H1 title** that matches `title`.
2. **Opening paragraph** of 2–4 sentences. If someone reads nothing else, this is enough to act on.
3. **H2 sections** in the default order for that document (outlined below). Remove sections that don't apply rather than leaving them empty. Add new sections after the defaults.
4. **H3 and lower** are free for structure inside a section. No H2 should need more than a screen to read; split into a new file before that happens.

### Fixed and flexible rules

One of the core principles of the Portable Brand System says *consistency must reinforce identity without flattening expression*. So the system needs to make clear what can change and what holds the brand together. 

Any part of our guidelines that set direction splits into:

- **Fixed:** rules that hold everywhere. Each is a one-line rule, followed by a reason.
- **Flexible:** what teams are free to adapt by context, and the range they can move within.

Rules are written like this:

```markdown
**Fixed**

- **Lead with the outcome.** Open with what the reader gets, not what we do. *Why:* our audience is time-poor and skeptical of vendor talk.
- **Never say "seamless".** *Why:* every competitor says it, and it promises something we can't guarantee.

**Flexible**

- Sentence length and formality can move with the channel: shorter and looser on social, fuller in proposals.
```

To cite a rule, link to it by its own words: `[never claim a track record we haven't earned](brand/voice.md#tone)`. To retire a rule, delete it and log the change in `CHANGELOG.md` under Retired.

### Examples

Show, don't only tell. Every guideline file should have at least one example section.

- **Do / Don't** lists for behaviour.
- **Instead of → Write** tables for language.
- Image examples link into `assets/` with alt text that explains what the example shows, so it still works for a model that can't see images.

### Values and tokens

Design values live in Markdown tables in the `brand/` files (color, typography, layout), each value next to its token name. The token name is the stable identifier a platform uses to build `tokens.json` or any other format; the table is the source.

```markdown
| Name    | Token                 | Value   | Role                      |
| ------- | --------------------- | ------- | ------------------------- |
| Example | `color.brand.example` | #FF4D1A | Primary accent, CTAs only |
```

Each value is defined once, in the file that owns it. The `visual.md` file and the other direction files describe intent and reference tokens by name; they never define values.

### Prompts

Reusable prompt fragments go in a `Prompts` section as fenced `text` blocks with a one-line label above each. They're written to be pasted whole, so no surrounding context is assumed.

### Well-known and built files

The Portable Brand System package is a reference structure, not a build. It holds no generated files. Standardized files like `tokens.json`, a compiled `brand.md`, `llms.txt` and output kits are produced and held outside this repo.

### Template guidance

Instructions for filling a template are HTML comments (`<!-- … -->`). They're invisible in Obsidian reading view and on GitHub, an AI can follow them when drafting. They should be stripped on export. This keeps the methodology inside the template without cluttering the finished document.

### Portability

Plain CommonMark only: no wikilinks, callouts, or plugin syntax. Links are relative Markdown links (`[voice](voice.md#tone)`). Tables over nested bullets for anything with more than two attributes.

### Formatting conventions

Small rules that keep every file consistent. Apply them everywhere, including tables, links and frontmatter, but not inside fenced prompts that are meant to be pasted.

- **No ": " inside frontmatter values.** Use a dash or rephrase. *Why:* a colon followed by a space breaks YAML parsing.
- **Tables stay aligned.** Where a table's columns are padded, keep them padded after any edit.
- **GAP vs TODO.** `<!-- GAP: … -->` marks a question only the brand's organization can answer. `<!-- TODO: … -->` marks an open item the brand steward can own. Search for either to list what's open. *Why:* it separates what's waiting on the external input from internal action.

## Example: `brand/voice.md`

The full pattern in one file.

````markdown
---
title: Voice
type: guideline
description:
---

# Voice

<!-- 2–4 sentences: who the brand sounds like and the one thing every piece of writing should do. -->

## Identity

<!-- Describe the voice as a person: who are they, what's their relationship to the reader? One paragraph, then 3–5 traits written as "X, not Y" to draw the boundary. -->

## Dimensions

<!-- Place the voice on 3–5 spectrums. The position is fixed; how far it can move by context goes in Tone. -->

| Spectrum          | Position                  |
| ----------------- | ------------------------- |
| Formal ↔ Casual   | Leans casual              |
| Serious ↔ Playful | Serious, with dry moments |

## Tone

<!-- How the voice adapts by context and audience. Link audience profiles rather than redescribing them. -->

**Fixed**

- **…** … *Why:* …

**Flexible**

| Context            | Shift | Example |
| ------------------ | ----- | ------- |
| Sales proposal     | …     | …       |
| Social             | …     | …       |
| Support / bad news | …     | …       |

## Vocabulary

| Instead of | Write | Why |
| ---------- | ----- | --- |
|            |       |     |

## Mechanics

<!-- Capitalization, punctuation, numbers, dates, names, spelling (e.g. Canadian English). Only what's specific to this brand; defer to a named style guide for the rest. -->

## Samples

<!-- 3+ before/after rewrites across different channels. These are the most useful few-shot examples for AI tools. -->

## Prompts

Draft in the brand voice:

```text
…
```

````

## Default sections by document

### Meta

| File               | Sections                                                                                                                                                                                                                                 |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `README.md`        | · Opening (what this is)<br>· What's inside (folder map)<br>· Where to find things (wayfinding: task → file)<br>· Using it with AI tools<br>· Who looks after it<br>· Version and license                                                |
| `CHANGELOG.md`     | One H2 per version, newest first: `## 1.2.0 — 2026-10-06`, then `Added` · `Changed` · `Retired` · `Decisions`                                                                                                                            |
| `CONTRIBUTING.md`  | · Roles (Owner, Steward, Contributor)<br>· What changes how (change type → who approves → version bump)<br>· Proposing a change: people<br>· Proposing a change: AI<br>· Bringing work back<br>· Open decisions (what blocks work today) |
| `design/DESIGN.md` | The brand-wide DESIGN.md (and names the per-output files)<br>· How the brand applies across outputs<br>· Shared foundations (where values live)<br>· Outputs (table: output → guide)<br>· Adding a new output                            |
| `GLOSSARY.md`      | Terms (table: term → meaning, linked to where it's explained)                                                                                                                                                                            |

**Versioning** (in `CONTRIBUTING.md`):

- major = strategy changes (identity, positioning);
- minor = new or changed guidance, a new output guide;
- patch = corrections and clarifications.

**Decision entries** (in `CHANGELOG.md`):

```markdown
- **Retire "Internet that sparks joy" for "Joy at the speed of light".** Approved by Jane Smith. *Why:* … *Affects:* [a teacher, not a pitcher](brand/identity.md#positioning), [never claim a track record we haven't earned](brand/voice.md#tone)
```

### Guidelines: `brand/`

| File            | Sections                                                                                                                                                                                                                                   |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `identity.md`   | · Overview (who it's for, what's sold, who has a stake, who the end user is)<br>· Essence<br>· Purpose<br>· Positioning (statement, category, competitive frame, differentiators)<br>· Personality ("X, not Y")<br>· Principles<br>· Story |
| `voice.md`      | · Identity<br>· Dimensions<br>· Tone<br>· Vocabulary<br>· Mechanics<br>· Samples<br>· Prompts                                                                                                                                              |
| `color.md`      | · Palette<br>· Proportion<br>· Combinations (approved pairings with contrast ratios)<br>· Gradients<br>· Scales<br>· Prompts                                                                                                               |
| `typography.md` | · Typefaces (family, token, license, fallbacks)<br>· Scale<br>· Styles<br>· Hierarchy<br>· Guardrails                                                                                                                                      |
| `logo.md`       | · Variants<br>· Color (which version on which background)<br>· Clearspace<br>· Sizing<br>· Guardrails                                                                                                                                      |
| `visual.md`     | · Principles<br>· Photography<br>· Illustration<br>· Iconography<br>· Composition<br>· Prompts                                                                                                                                             |
| `layout.md`     | · Spacing (token table)<br>· Radius (token table)<br>· Grid                                                                                                                                                                                |
| `motion.md`     | · Principles<br>· Timing (token refs)<br>· Usage<br>· Accessibility<br>· Prompts                                                                                                                                                           |

Sections that sets direction use **Fixed vs. Flexible** rule setting. Guardrails sections are Fixed rules with Don't examples.

### Guidelines: `design/<output>/DESIGN.md`

One per output type (presentations, website, social, events…). Same sections for all, so a new output is just a new folder:

- Job (what this output has to do, for whom)
- What holds, what flexes (Fixed / Flexible for this context)
- Layout (grid, margins, by token)
- Type and color in use
- Patterns (each: when to use, structure, what can vary)
- Templates (file → when to use)
- Checklist (before it ships)
- Lessons (dated notes from real use, the "every project makes it more useful" loop)
- Values (table: token → shared token or value → note)

### Profiles: `profiles/`

Profiles are facts, not guidance. They use tables with a **Source** column and, where wording matters, an **Approved wording** column. They don't contain rules; if a fact needs a rule (e.g. "never claim carbon neutral"), the rule goes in the relevant guideline and links here.

| File                       | Sections                                                                                                                                                                 |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `org/corporate.md`         | · Names (legal, trading, how to write the name)<br>· Entities<br>· Locations<br>· Digital properties<br>· Social profiles<br>· Contacts                                  |
| `org/structure.md`         | · Overview<br>· Entities and ownership<br>· Business units<br>· Leadership (links to `team/`)                                                                            |
| `org/assurances.md`        | Table: claim · type (certification, standard, compliance) · issuer · valid until · evidence · approved wording                                                           |
| `org/history.md`           | · Origin<br>· Timeline (date → event)<br>· Stories worth telling                                                                                                         |
| `audience/icp.md`          | · Summary<br>· Firmographics<br>· Buying group<br>· Qualifying signals<br>· Disqualifiers                                                                                |
| `audience/<profile>.md`    | · Summary<br>· Who they are<br>· Goals<br>· Pains<br>· Triggers<br>· Objections<br>· What they need to hear<br>· Their language<br>· Where to reach them<br>· Evidence   |
| `industries/<industry>.md` | · Summary<br>· Landscape<br>· Pressures<br>· What they value<br>· Their language<br>· Relevant offerings<br>· Proof                                                      |
| `offerings/<offering>.md`  | · Summary<br>· What it is<br>· Who it's for<br>· Problem it solves<br>· How it works<br>· Features → benefits<br>· Proof<br>· Packaging and pricing<br>· Approved claims |
| `team/<person>.md`         | · Name and role<br>· Bio (short, long)<br>· Expertise<br>· Photo<br>· Links<br>· Approved for (quoting, speaking, bylines)                                               |

`industries/` is for B2B packages.

### Sources: `resources/`

File name: `{topic}-{yyyy-mm-dd}.md`. Sections: Summary · Question · Method · Findings · Implications for the brand · Sources.

Sources are never edited after they're dated. A new finding is a new file. Implications become canon only when a guideline or profile changes and a decision is logged in `CHANGELOG.md`.
