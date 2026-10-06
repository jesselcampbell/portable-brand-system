# Portable Brand System

A shared foundation for people and AI to grow and manage brands, keeping the identity intact while letting expression expand.

> **Status:** early draft (v0.1). The structure and formatting are working proposals, being tested on real brands.

## Why

People get to know a company through what it says and does. As a company grows, more people have a hand in that work. Teams change, tools multiply, and the thinking behind the brand gets scattered. With AI, more people make websites, presentations, and campaigns, but they aren't always working from the same understanding. Drift happens.

A Portable Brand System is the common starting point. It puts the brand's thinking, assets, and reusable patterns into the hands of the people and tools doing the work, so every deck, page, and post benefits from the work that came before it.

It makes doing the right thing the easy thing.

## What's in a brand package

1. **Guidelines.** The thinking behind the brand: strategy, voice, visual direction, and how to apply them.
2. **Assets.** Logos, fonts, photography, illustration, icons.
3. **Tokens.** Named design values (color, type, spacing) that tools can read and apply consistently.
4. **Composed elements and templates.** Slide layouts, website sections, proposal templates, and other starting points, each with guidance on when and how to use it.

People and their tools are the execution layer. They use the system to make the things a brand needs.

## Principles

| Principle | In short |
| --------- | -------- |
| Platform agnostic | The system sets the rules. The tools adapt. |
| Ecosystem aware | The brand responds to its context. |
| Scalable | Start with one brand. Grow without starting again. |
| Distributable | Many people contribute. Everyone knows what to use. |

## This repository

```text
README.md        This file
FORMAT.md        Document types, frontmatter, and default sections for every file
template/        A blank brand package: copy it to start a new brand
```

The template package:

```text
template/
├── BRAND.md              The brand on one page. Start here.
├── CHANGELOG.md          Versions and decisions
├── CONTRIBUTING.md       Roles and how changes are proposed and approved
├── DESIGN.md             How the brand applies across outputs
├── README.md             Orientation for the package
├── assets/
│   ├── data/tokens.json  Shared design values (DTCG format)
│   ├── fonts/
│   └── logos/            composed/, PNG/, SVG/
├── brand/                identity, voice, color, typography, logo, visual, motion
├── design/               One folder per output: presentations/, website/, _output/ (blank)
├── profiles/             Maintained facts: org/, audience/, industries/, offerings/, team/
└── resources/            Dated research and evidence
```

Files starting with `_` are templates for repeating files (one per audience, offering, person, industry, output, or source). Copy and rename them; delete the originals once the package is in use.

## Getting started

1. Copy `template/` and rename it for the brand.
2. Fill in `brand/identity.md` first. Everything else traces back to it.
3. Work through `brand/`, then `profiles/`, then `design/`. Delete sections that don't apply.
4. Compile `BRAND.md` from the finished files.
5. Log each decision in `CHANGELOG.md` as you go.

Guidance for each section is written as HTML comments in the template files. It's hidden when the files are rendered, and AI tools can follow it when drafting.

## Maintained by

[Partner Creative](https://heypartner.co)
