# Document format

Default sections and formatting for every document in a Portable Brand System (PBS) brand package. The goal is that any file, opened by a person or an AI, reads the same way: what it is, what's fixed, what can flex, and why.

## Document types

Every file is one of four types. The type decides the formatting mode.

| Type        | Lives in                                 | Mode                                                         | Can contain rules? |
| ----------- | ---------------------------------------- | ------------------------------------------------------------ | ------------------ |
| `meta`      | `README.md`, `BRAND.md`, `CHANGELOG.md`, `CONTRIBUTING.md`, `DESIGN.md` | Orientation. Indexes, summaries, how the system works.       | Summarises them    |
| `guideline` | `brand/`, `design/`                      | Prescriptive. Rules, guidance, examples, rationale.          | Yes                |
| `profile`   | `profiles/`                              | Descriptive. Maintained facts with sources.                  | No (only approved wording) |
| `source`    | `resources/`              | Evidence. Dated, never edited after the fact, never canon.   | No                 |

## Shared conventions

### Frontmatter

Every file starts with the same minimal frontmatter. `description` is what an agent reads to decide whether to load the file, so it carries real information, not a label.

```yaml
---
title: Voice
type: guideline            # meta | guideline | profile | source
description: How Kurnl sounds, how tone shifts by context, and the words we use and avoid.
---
```

`source` files add `date`, `author` and `method`.

### Body pattern

1. **H1 title** that matches `title`.
2. **Opening paragraph** of 2–4 sentences. If someone reads nothing else, this is enough to act on.
3. **H2 sections** in the default order for that document (below). Remove sections that don't apply rather than leaving them empty. Add new sections after the defaults.

H3 and lower are free for structure inside a section. No H2 should need more than a screen to read; split into a new file before that happens.

### Fixed and Flexible

The core formatting device, taken straight from the principles (*Consistency must reinforce identity without flattening expression* and *The system makes clear what can change and what holds the brand together*). Any guideline section that sets direction splits into:

- **Fixed:** rules that hold everywhere. Each has an ID, a one-line rule, and a reason.
- **Flexible:** what teams are free to adapt by context, and the range they can move within.

Rules are written like this:

```markdown
**Fixed**

- **VOI-01 — Lead with the outcome.** Open with what the reader gets, not what we do. *Why:* our audience is time-poor and skeptical of vendor talk.
- **VOI-02 — Never say "seamless".** *Why:* every competitor says it, and it promises something we can't guarantee.

**Flexible**

- Sentence length and formality can move with the channel: shorter and looser on social, fuller in proposals.
```

Rule IDs use a three-letter prefix per file (`IDN`, `VOI`, `COL`, `TYP`, `LOG`, `VIS`, `MOT`; design outputs use their own, e.g. `PRS`, `WEB`) and a two-digit number. IDs are never reused: retire a rule, mark it ~~struck through~~ with the version it was retired in, and move on to the next number. That lets anyone (a reviewer, a brand-check skill) cite a rule and have the reference stay meaningful.

### Examples

Show, don't only tell. Every guideline file should have at least one example section.

- **Do / Don't** lists for behaviour.
- **Instead of → Write** tables for language.
- Image examples link into `assets/` with alt text that explains what the example shows, so it still works for a model that can't see the image.

### Values and tokens

`tokens.json` is the single source for design values. Markdown can show a value for human convenience, but always next to its token name, and the token wins if they disagree.

```markdown
| Name      | Token                 | Value   | Role                          |
| --------- | --------------------- | ------- | ----------------------------- |
| Signal    | `color.brand.signal`  | #FF4D1A | Primary accent, CTAs only     |
```

`visual.md` and the other direction files describe intent and reference tokens. They never define values.

### Prompts

Reusable prompt fragments go in a `Prompts` section as fenced `text` blocks with a one-line label above each. They're written to be pasted whole, so no surrounding context is assumed.

### Template guidance

Instructions for filling a template are HTML comments (`<!-- … -->`). They're invisible in Obsidian reading view and on GitHub, an AI can follow them when drafting, and they can be stripped on export. This keeps the methodology inside the template without cluttering the finished document.

### Portability

Plain CommonMark only: no wikilinks, callouts, or plugin syntax. Links are relative Markdown links (`[voice](voice.md#tone)`). Tables over nested bullets for anything with more than two attributes.

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

| Spectrum           | Position                  |
| ------------------ | ------------------------- |
| Formal ↔ Casual    | Leans casual              |
| Serious ↔ Playful  | Serious, with dry moments |

## Tone

<!-- How the voice adapts by context and audience. Link audience profiles rather than redescribing them. -->

**Fixed**

- **VOI-01 — …** … *Why:* …

**Flexible**

| Context             | Shift             | Example |
| ------------------- | ----------------- | ------- |
| Sales proposal      | …                 | …       |
| Social              | …                 | …       |
| Support / bad news  | …                 | …       |

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

| File               | Sections                                                                                                                                                                                                             |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `BRAND.md`         | In short · Positioning · Essential rules (the ~10 most important Fixed rules, by ID, across all files) · Voice at a glance · Look at a glance (logo, color, type with token refs) · How to use this system (task → files to load) · Ownership · Index (every file with its description) |
| `README.md`        | What this is · What's inside · How it's organized · Getting started: people · Getting started: AI tools · Version and license                                                                                        |
| `CHANGELOG.md`     | One H2 per version, newest first: `## 1.2.0 — 2026-10-06`, then `Added` · `Changed` · `Retired` · `Decisions`                                                                                                         |
| `CONTRIBUTING.md`  | Roles (Owner, Steward, Contributor) · What changes how (change type → who approves → version bump) · Proposing a change: people · Proposing a change: AI · Bringing work back                             |
| `DESIGN.md` (root) | How the brand applies across outputs · Shared foundations (what's in `assets/data/tokens.json`) · Outputs (table: output → guide) · Adding a new output                                                     |

**Versioning** (in `CONTRIBUTING.md`): major = strategy changes (identity, positioning); minor = new or changed guidance, a new output guide; patch = corrections and clarifications.

**Decision entries** (in `CHANGELOG.md`):

```markdown
- **D-014 — Retire "Internet that sparks joy" for "Joy at the speed of light".** Approved by Jane Smith. *Why:* … *Affects:* [IDN-03](brand/identity.md#positioning), [VOI-04](brand/voice.md#tone)
```

### Guidelines: `brand/`

| File            | Sections                                                                                                                  |
| --------------- | ------------------------------------------------------------------------------------------------------------------------- |
| `identity.md`   | Essence · Purpose · Positioning (statement, category, competitive frame, differentiators) · Personality ("X, not Y") · Principles · Story |
| `voice.md`      | Identity · Dimensions · Tone · Vocabulary · Mechanics · Samples · Prompts                                                 |
| `color.md`      | Palette · Proportion · Combinations (approved pairings with contrast ratios) · Gradients · Scales · Prompts               |
| `typography.md` | Typefaces (family, token, license, fallbacks) · Scale · Styles · Hierarchy · Guardrails                                   |
| `logo.md`       | Variants · Color (which version on which background) · Clearspace · Sizing · Guardrails                                  |
| `visual.md`     | Principles · Photography · Illustration · Iconography · Composition · Prompts                                            |
| `motion.md`     | Principles · Timing (token refs) · Usage · Accessibility · Prompts                                                        |

Every section that sets direction uses **Fixed / Flexible**. Guardrails sections are Fixed rules with Don't examples.

### Guidelines: `design/<output>/DESIGN.md`

One per output (presentations, website, social, events…). Same sections for all, so a new output is just a new folder:

Job (what this output has to do, for whom) · What holds, what flexes (Fixed / Flexible for this context) · Layout (grid, margins, token refs to the output's `tokens.json`) · Type and color in use · Patterns (each: when to use, structure, what can vary) · Templates (file → when to use) · Checklist (before it ships) · Lessons (dated notes from real use, the "every project makes it more useful" loop)

### Profiles: `profiles/`

Profiles are facts, not guidance. They use tables with a **Source** column and, where wording matters, an **Approved wording** column. They don't contain rules; if a fact needs a rule (e.g. "never claim carbon neutral"), the rule goes in the relevant guideline and links here.

| File                      | Sections                                                                                                                         |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `org/corporate.md`        | Names (legal, trading, how to write the name) · Entities · Locations · Digital properties · Social profiles · Contacts           |
| `org/structure.md`        | Overview · Entities and ownership · Business units · Leadership (links to `team/`)                                               |
| `org/assurances.md`       | Table: claim · type (certification, standard, compliance) · issuer · valid until · evidence · approved wording                  |
| `org/history.md`          | Origin · Timeline (date → event) · Stories worth telling                                                                         |
| `audience/icp.md`         | Summary · Firmographics · Buying group · Qualifying signals · Disqualifiers                                                      |
| `audience/<profile>.md`   | Summary · Who they are · Goals · Pains · Triggers · Objections · What they need to hear · Their language · Where to reach them · Evidence |
| `industries/<industry>.md`| Summary · Landscape · Pressures · What they value · Their language · Relevant offerings · Proof                                  |
| `offerings/<offering>.md` | Summary · What it is · Who it's for · Problem it solves · How it works · Features → benefits · Proof · Packaging and pricing · Approved claims |
| `team/<person>.md`        | Name and role · Bio (short, long) · Expertise · Photo · Links · Approved for (quoting, speaking, bylines)                        |

`industries/` is for B2B packages.

### Sources: `resources/`

File name: `{topic}-{yyyy-mm-dd}.md`. Sections: Summary · Question · Method · Findings · Implications for the brand · Sources.

Sources are never edited after they're dated. A new finding is a new file. Implications become canon only when a guideline or profile changes and a decision is logged in `CHANGELOG.md`.
