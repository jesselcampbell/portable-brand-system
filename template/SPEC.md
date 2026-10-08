---
title: Portable Brand System spec
type: meta
spec_version: 0.3.0
description: "PBS package structure, document conventions and template guidance. Use this when maintaining or validating a brand package; examples illustrate the format rather than define brand rules."
---

# Portable Brand System spec

Here we outline the default sections and formatting for every document in a Portable Brand System (PBS). The goal is that any file, opened by a person or an AI, reads the same way: what it is, what's fixed, what can flex, and why.

## Package boundary

The standard defines a small, documented structure for approved, reusable brand knowledge and materials. People and AI must be able to read and maintain the package without a particular account, platform, or runtime. Platforms can research, manage workflows, produce assets, and assemble outputs around it.

A package brings together guidelines, profiles, assets, design values, patterns/templates, and reusable generation instructions. It carries essential rationale alongside rules, source references alongside facts, and approved decisions in `CHANGELOG.md`. Research archives, interviews, audits, experiments, working files, and project deliverables remain outside the package.

Compiled `BRAND.md`, `brand.json`, root `DESIGN.md`, `llms.txt`, JSON-LD, `tokens.json`, and assembled output kits are platform outputs. Approved reusable assets and templates can become source materials through review, regardless of whether a person or a tool created them.

## Package structure

Copy the template and keep only what the brand needs. Files and folders starting with `_` are templates for repeated items; copy and rename them, then remove the originals. `brand/audio.md` is optional. Each output folder has its own `DESIGN.md` and `templates/`; the package README provides wayfinding.

```text
template/
├── CHANGELOG.md           // Versions, changes, decisions
├── CONTRIBUTING.md        // Roles, approvals, contributions
├── GLOSSARY.md            // Terms
├── README.md              // Navigation, AI use, stewardship
├── SPEC.md                // Structure, conventions, examples
├── assets/                // Brand materials referenced in the brand and for use in production
│   ├── fonts/             // Font files
│   ├── logos/             // Approved logo artwork and prepared logo assets
│   │   ├── PNG/           // Raster logo files
│   │   ├── SVG/           // Vector logo files
│   │   └── composed/      // Prepared logo compositions for avatars, icons, and similar uses
│   ├── photography/       // Approved photography for use across brand applications
│   ├── art/               // Illustrations, renderings, patterns, textures, and other artwork
│   ├── icons/             // Approved icons and icon sets
│   ├── motion/            // Animations, motion graphics, and reusable motion assets
│   └── audio/             // Sonic logos, music, sound effects, and other brand audio
├── brand/                 // Brand strategy and expression, with rules, rationale, examples, and values
│   ├── audio.md           // Sound identity, music, usage (optional)
│   ├── color.md           // Palette, pairings, proportions
│   ├── identity.md        // Purpose, positioning, personality, story
│   ├── layout.md          // Spacing, radius, grid
│   ├── logo.md            // Variants, sizing, usage
│   ├── motion.md          // Timing, usage, accessibility
│   ├── typography.md      // Typefaces, scale, hierarchy
│   ├── visual.md          // Art direction and composition; links to generation treatments
│   └── voice.md           // Tone, vocabulary, mechanics, narratives, samples
├── design/                // Guidance and reusable starting points for each output type
│   └── _output/           // Blank output folder to copy and adapt for a medium or format (e.g. slide-decks/)
│       ├── DESIGN.md      // Rules, patterns, templates, values
│       └── templates/     // Reusable templates for this output type
├── dna/                   // Reusable instructions for generative AI
│   └── _treatment.md      // Purpose, precision, semantic, relationships, instructions, review, references
└── profiles/              // Maintained facts about the organization and the people and markets it serves
    ├── audience/          // Audience needs, behaviors, and ideal customer criteria
    │   ├── _profile.md    // Needs, motivations, messaging, evidence
    │   └── icp.md         // Customer fit, buyers, signals
    ├── industries/        // Industry context for B2B brands
    │   └── _industry.md   // Context, pressures, language, proof
    ├── offerings/         // Product and service facts, benefits, proof, and approved claims
    │   └── _offering.md   // Benefits, proof, pricing, claims
    ├── org/               // Organizational identity, structure, credentials, and history
    │   ├── assurances.md  // Assurances
    │   ├── corporate.md   // Names, locations, channels, contacts
    │   ├── history.md     // Origin, timeline, stories
    │   └── structure.md   // Ownership, units, leadership
    └── team/              // Approved team biographies, expertise, photos, and uses
        └── _person.md     // Role, bio, expertise, permissions
```

## Document types

Every Markdown document is one of three types. Asset files and reusable templates retain the formats appropriate to their use.

| Type        | Lives in                                                                 | Mode                                    | Contains rules                    |
| ----------- | ------------------------------------------------------------------------ | --------------------------------------- | --------------------------------- |
| `meta`      | `README.md`, `SPEC.md`, `CHANGELOG.md`, `CONTRIBUTING.md`, `GLOSSARY.md` | Orientation and conventions             | Summaries and package conventions |
| `guideline` | `brand/`, `dna/<treatment>.md`, `design/<output>/DESIGN.md`                                    | Rules, guidance, examples, rationale    | Yes                               |
| `profile`   | `profiles/`                                                              | Maintained facts with source references | No                                |

## Shared conventions

### Frontmatter

Every Markdown document starts with some minimal frontmatter. `description` is what an agent reads to decide whether to load the file, so it carries real information, not a label. It describes the nature of the content in one or two sentences, followed by one or two sentences explaining when to use it. The complete description must be no longer than 280 characters; describe the knowledge rather than restating it.

```yaml
---
title: Voice
type: guideline
description: "Writing guidance covering tone, vocabulary, mechanics and examples. Use this when drafting or reviewing brand copy for an audience and context."
---
```

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

Reusable generative-AI instructions belong in `dna/<treatment>.md`, with fenced `text` prompt blocks and clearly declared variables and dependencies. Brand guides may keep a `Prompts` section as navigation to the relevant DNA files. Output assembly recipes remain in `design/<output>/`; research and task-specific experiments remain external.

### DNA — reusable generation instructions

`dna/` lives at the package root, beside `brand/`, `design/`, `profiles/`, and `assets/`. It holds approved reusable instructions for generating brand-consistent material. A treatment can describe photography, artwork, animation, audio, writing, or another form of expression; include only what the brand has defined.

The folders have distinct roles:

| Folder | Owns |
| --- | --- |
| `brand/` | Brand meaning, rules, values, and rationale |
| `dna/` | How that knowledge translates into generation instructions |
| `design/` | How to construct particular outputs, with reusable templates |
| `profiles/` | Maintained facts, evidence boundaries, and approved claims |
| `assets/` | Approved reusable media and artwork |

Keep one independently usable creative treatment per file. Name files for the treatment, such as `strand-art.md`, rather than for a particular AI tool. An agent should be able to select the file, identify its dependencies, supply a brief, and apply it. Use subfolders only when the library needs them. The root `README.md` provides the full treatment index; `_treatment.md` is the copyable scaffold and is removed from an active package after use.

Each treatment uses `type: guideline` and these sections in this order:

| Section | Contains |
| --- | --- |
| Purpose and scope | What the treatment produces and when to use it |
| Precision | Required assets, token references, and defined technical constraints |
| Semantic | Creative character, mood, subject treatment, intended meaning, and misleading interpretations to avoid |
| Relationships | Governing guidance, dependencies, application conditions, permitted variation, and documented exceptions |
| Generation instructions | Reusable prompt blocks, exclusions, and variables supplied by the brief |
| Review criteria | How to judge whether the result follows the treatment |
| References and open decisions | Supporting examples, provenance, permission limits, and missing knowledge |

**Precision, Semantic, and Relationships remain explicit.** A layer without defined knowledge says what is missing; it does not manufacture camera settings, motion timings, brand associations, or other decisions to complete a template. Exact wording or an asset reference can be precision even when no numerical value is involved.

Brand guidance remains the authority. DNA links to its governing rules and owning value tables rather than maintaining competing definitions. Where prompt blocks repeat exact values so they can be used directly, treat those literals as dependent representations and keep them aligned with their named sources. Relationships should state what the link does — governed by, depends on, applies when, may adapt, or exception — rather than leaving the connection to inference.

Distinguish fixed constraints from the creative variables a brief may supply. Keep portable instructions independent of model-specific syntax; label optional tool adaptations separately inside Generation instructions. Existing instructions can be relocated without changing their wording, but relocation does not approve unresolved uses or override newer guidance. Record conflicts, permissions, and draft evidence where they affect application.

Reusable generation prompts belong here; brand guides link to the relevant treatments. Output assembly recipes remain with their output guides. Campaign prompts, experiments, generation logs, and project deliverables stay outside the source package. Only approved reusable learning and materials come back through review.

This structure draws on [Sameness's image-consistency framework](https://www.sameness.io/ai-image-consistency), while retaining PBS's portable source files and separation between brand guidance, generation instructions, and project work.

### Well-known and built files

The package supplies source context for compiled files and assembled output kits. Those outputs are produced and maintained outside the package; there is no `outputs/` or `dist/` folder. The `DESIGN.md` in each output folder is source guidance, distinct from a compiled root `DESIGN.md`. Approved reusable assets and templates may be included regardless of how they were made.

### Template guidance

Instructions for filling a template are HTML comments (`<!-- … -->`). They're invisible in Obsidian reading view and on GitHub, an AI can follow them when drafting. They should be stripped on export. This keeps the methodology inside the template without cluttering the finished document.

### Portability

Use plain Markdown with tables; no wikilinks, callouts, or plugin syntax. Links are relative Markdown links (`[voice](voice.md#tone)`). Tables over nested bullets for anything with more than two attributes.

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

## Narratives

<!-- Reusable narrative structures and messaging themes, grounded in identity.md and maintained profile facts. Explain when each fits and what can vary; link to facts and claims instead of redefining them. -->

## Samples

<!-- 3+ before/after rewrites across different channels. These are the most useful few-shot examples for AI tools. -->

## Prompts

<!-- Link to the relevant completed treatment in dna/. Reusable prompt blocks live there. -->

<!-- Link directly to each relevant completed dna/<treatment>.md file. The root README contains the full index. -->

````

## Default sections by document

### Meta

| File               | Sections                                                                                                                                                                                                                                 |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `README.md`        | · Opening (what this is)<br>· What's inside (folder map)<br>· Where to find things (wayfinding: task → file)<br>· Using it with AI tools<br>· Who looks after it<br>· Version and license                                                |
| `CHANGELOG.md`     | One H2 per version, newest first: `## 1.2.0 — 2026-10-06`, then `Added` · `Changed` · `Retired` · `Decisions`                                                                                                                            |
| `CONTRIBUTING.md`  | · Roles (Owner, Steward, Contributor)<br>· What changes how (change type → who approves → version bump)<br>· Proposing a change: people<br>· Proposing a change: AI<br>· Bringing work back<br>· Open decisions (what blocks work today) |
| `SPEC.md`          | Package boundary · Package structure · Document types · Shared conventions · Example · Default sections by document                                                                                                                      |
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
| `voice.md`      | · Identity<br>· Dimensions<br>· Tone<br>· Vocabulary<br>· Mechanics<br>· Narratives<br>· Samples<br>· Prompts                                                                                                                              |
| `color.md`      | · Palette<br>· Proportion<br>· Combinations (approved pairings with contrast ratios)<br>· Gradients<br>· Scales<br>· Prompts                                                                                                               |
| `typography.md` | · Typefaces (family, token, license, fallbacks)<br>· Scale<br>· Styles<br>· Hierarchy<br>· Guardrails                                                                                                                                      |
| `logo.md`       | · Variants<br>· Color (which version on which background)<br>· Clearspace<br>· Sizing<br>· Guardrails                                                                                                                                      |
| `visual.md`     | · Principles<br>· Photography<br>· Art (illustrations, renderings, patterns, textures)<br>· Iconography<br>· Composition<br>· Prompts                                                                                                      |
| `layout.md`     | · Spacing (token table)<br>· Radius (token table)<br>· Grid                                                                                                                                                                                |
| `motion.md`     | · Principles<br>· Timing (token refs)<br>· Usage<br>· Accessibility<br>· Prompts                                                                                                                                                           |
| `audio.md`      | Optional: Sound identity · Sonic logo · Music · Usage · Accessibility · Examples · Prompts                                                                                                                                                 |

Sections that set direction use **Fixed vs. Flexible** rule setting. Guardrails sections are Fixed rules with Don't examples.

### Guidelines: `dna/<treatment>.md`

Copy `dna/_treatment.md` for each defined treatment. The default sections are Purpose and scope · Precision · Semantic · Relationships · Generation instructions · Review criteria · References and open decisions. Keep all three layers explicit and mark missing knowledge without inventing it. See [DNA conventions](#dna--reusable-generation-instructions). The root `README.md` indexes completed treatments and their application limits; there is no `dna/README.md`.

### Guidelines: `design/<output>/DESIGN.md`

Copy `design/_output/` for each output type (slide-decks, website, social, events…). Link shared rules directly to `brand/`, add the guide to the package README, and keep reusable templates in the output's `templates/` folder. Remove irrelevant sections and add medium-specific guidance as needed:

- Job (what this output has to do, for whom)
- What holds, what flexes (Fixed / Flexible for this context)
- Layout (grid, margins, by token)
- Type and color in use
- Patterns (each: when to use, structure, what can vary)
- Templates (file → when to use)
- Checklist (before it ships)
- Lessons (approved learning, dated and supported by rationale; raw feedback stays outside)
- Values (table: token → shared token or value → note)

### Profiles: `profiles/`

Profiles are facts, not guidance. Keep enough supporting context to understand and use each fact without the research platform. Link to external evidence; do not copy research archives into the package. Profiles use tables with a **Source** column and, where wording matters, an **Approved wording** column. They don't contain rules; if a fact needs a rule (e.g. "never claim carbon neutral"), the rule goes in the relevant guideline and links here.

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
