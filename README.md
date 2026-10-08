# Portable Brand System

An open standard for delivering and maintaining brands as portable files. A shared foundation for people and AI to grow and manage brands, preserving identity while expanding expression.

## Why

People get to know a company through what it says and does. As a company grows, more people have a hand in that work. Teams change, tools multiply, and the thinking behind the brand gets scattered. With AI, more people make websites, presentations, and campaigns, but they aren't always working from the same understanding. Drift happens.

A Portable Brand System is the common starting point. It puts the brand's thinking, assets, and reusable patterns into the hands of the people and tools doing the work, so every deck, page, and post benefits from the work that came before it.

It makes doing the right thing the easy thing.

## What's in a brand package

It brings together six parts:

1. **Guidelines:** The documented thinking behind the brand: its strategy, voice, visual direction, motion, and sound, with the reasons behind important decisions and guidance for applying them.
2. **Profiles:** Maintained facts about the organization, its audiences, industries, offerings, and people, with source references and approved wording where needed.
3. **Assets:** Approved materials teams create with: logos, fonts, photography, art, icons, motion, and audio.
4. **Design values:** Named, reusable values, such as colors, type scales, and spacing, written in Markdown tables beside their token names. These tables give people and tools the source information needed to generate `tokens.json` or other formats.
5. **Patterns and templates:** Reusable starting points, such as slide layouts, website sections, product components, and proposal templates, with guidance on when and how to use them.
6. **DNA:** Reusable generation instructions that translate brand knowledge into creative treatments, with explicit precision, semantic meaning, relationships, prompts, and review criteria.

The package holds approved, reusable brand knowledge and materials that remain useful independently of a platform. People and their tools are the execution layer.

## The open standard and the platforms around it

**The standard must stand on its own.** A brand delivered as a Portable Brand System should be readable, editable, and useful without an account, a subscription, or a particular provider’s software. Its foundation is a set of text files, with the assets they describe, that people and AI tools can understand and use directly.

The standard defines how that information is organized, what it means, and how the parts relate. It needs clear documentation, useful examples, and a small set of dependable conventions. As we build it, we need to be precise about what's required and what's optional. Add complexity only when it solves a demonstrated problem shared across implementations. Adoption should be easy, and a simple brand should remain simple.

**The package is the source context for generated outputs.** There is deliberately no root `BRAND.md` or `DESIGN.md`. A platform can assemble those files for a particular tool or task, alongside `llms.txt`, `tokens.json`, or other formats. The source retains the detail, rationale, and relationships needed to produce a good version of each. The guides inside `design/` remain part of that source: they explain how the brand applies across outputs and within each medium.

**Platforms make the standard useful in different ways.** They can conduct research, manage editing and approvals, distribute updates, connect tools, generate assets, check outputs, and propose improvements from finished work. This is where opinionated workflows, interfaces, automation, and services belong. Different platforms should be free to serve different needs using the same underlying standard.

People should be able to build their own platforms, integrate the files into existing tools, or use them directly with an AI system. None of those paths should depend on a particular provider’s permission or infrastructure. Platform features must not become hidden requirements for understanding or maintaining the brand. Approved changes to the shared brand belong in the portable files so they can travel with it.

**The standard succeeds when others can adopt it easily. Platforms succeed by making it more useful.**

## The brand grows through use

A brand system should grow with the people who use it. Every application is a chance to discover a new expression, sharpen an idea, or learn what matters. The best of that work should carry forward, giving the next person more to build on. That is how the brand becomes richer over time: its identity holds while its possibilities expand.

## Principles

| Principle | In short |
| --------- | -------- |
| Platform agnostic | The system sets the rules. The tools adapt. |
| Ecosystem aware | The brand responds to its context. |
| Scalable | Start with one brand. Grow without starting again. |
| Distributable | Many people contribute. Everyone knows what to use. |

## This repository

The repository contains this overview, a [specification changelog](CHANGELOG.md), and `template/`, a blank brand package. The current [specification](template/SPEC.md) is version 0.3.0. A brand's own version and decision history belong in its package's `CHANGELOG.md`.

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
│   ├── README.md          // Treatment index, selection, dependencies
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

Files and folders beginning with `_` are templates. Copy and rename them, then remove the originals once the package is in use. Keep only the guidance and asset folders a brand needs. `brand/audio.md` is optional. `assets/art/` covers illustrations, renderings, patterns, textures, and other artwork.

## Getting started

1. Copy `template/` and rename it for the brand.
2. Fill in `brand/identity.md` first. Everything else traces back to it.
3. Work through `brand/` and `profiles/`, removing sections that don't apply.
4. Copy `design/_output/` for each output type the brand needs, such as `design/slide-decks/`. Keep approved reusable templates in that output's `templates/` folder.
5. Copy `dna/_treatment.md` for each approved reusable generation treatment. Index finished treatments in `dna/README.md`, link them from the governing brand guides, and remove the blank scaffold.
6. Write the `README.md` last, linking directly to the finished files, output guides, and treatments.
7. Record approved decisions in the brand package's `CHANGELOG.md`.

Each fact or value is defined once and linked elsewhere. Leave a `GAP` comment for questions the brand's organization must answer or a `TODO` for work the steward owns. Do not guess. Template instructions use HTML comments so they remain readable to AI tools without cluttering the rendered guidance.

## DNA — reusable generation instructions

`dna/` lives at the package root, beside `brand/`, `design/`, `profiles/`, and `assets/`. It holds approved reusable instructions for generating brand-consistent material. A treatment can describe photography, artwork, animation, audio, writing, or another form of expression; include only what the brand has defined.

The folders have distinct roles:

| Folder | Owns |
| --- | --- |
| `brand/` | Brand meaning, rules, values, and rationale |
| `dna/` | How that knowledge translates into generation instructions |
| `design/` | How to construct particular outputs, with reusable templates |
| `profiles/` | Maintained facts, evidence boundaries, and approved claims |
| `assets/` | Approved reusable media and artwork |

Keep one independently usable creative treatment per file. Name files for the treatment, such as `strand-art.md`, rather than for a particular AI tool. An agent should be able to select the file, identify its dependencies, supply a brief, and apply it. Use subfolders only when the library needs them. `dna/README.md` provides a short treatment index; `_treatment.md` is the copyable scaffold and is removed from an active package after use.

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

## What stays outside

Research archives, interviews, audits, experiments, working files, and project deliverables stay in a platform or other external workspace. Essential rationale, source references, and approved decisions travel with the brand.

Platforms assemble output kits and compiled formats such as `BRAND.md`, `brand.json`, `DESIGN.md`, `llms.txt`, JSON-LD, and `tokens.json`. The package has no root `BRAND.md` or `DESIGN.md`, and no `resources/`, `outputs/`, or `dist/` folder. The `DESIGN.md` inside each output folder is maintained source guidance.

Approved reusable assets, patterns, and templates can become part of the package through review, whether created by a person or generated by a tool. What matters is their role as maintained brand materials.
