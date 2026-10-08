# Specification changelog

This records changes to the Portable Brand System specification and template. Brand packages keep their own versions and decisions in `template/CHANGELOG.md` after copying the template.

## 0.3.0 — 2026-10-08

### Added

- Optional root `dna/` folder for approved reusable generative-AI treatments, indexed in the root README, with a copyable treatment template.
- An explicit seven-section treatment format containing Precision, Semantic and Relationships layers, generation instructions, review criteria, source references and unresolved decisions.
- Frontmatter descriptions explain the nature of content and when to use it, within 280 characters.

### Changed

- Brand guides link to DNA treatments instead of owning reusable generation prompt blocks. Output assembly recipes remain in output guides.
- Package navigation describes six parts and makes the roles of brand guidance, generation instructions, output guidance, profiles and assets explicit.
- Prompt literals reference owning value tables; model-specific adaptations are optional, and relocation does not approve unresolved uses.

Research, experiments, compiled outputs and project deliverables remain external. The broader redesign of brand guideline sections remains separate from this release.

## 0.2.0 — 2026-10-08

### Added

- Asset folders for photography, art, icons, motion, and audio.
- Optional audio guidance, reusable output templates, and narrative guidance within voice.
- An annotated package tree and an explicit boundary between the open standard and platforms.

### Changed

- Describe five parts: guidelines, profiles, assets, design values, and patterns/templates.
- Keep approved reusable knowledge and materials portable, including assets created by tools.
- Keep research and working outputs external while retaining essential rationale, source references, and decisions.
- Use one copyable output folder, direct links to brand guidance, and README wayfinding.
- Broaden visual guidance from illustration to art and simplify the statement on learning through use.

### Retired

- The `resources/` research template and `source` document type.
- The shared `design/DESIGN.md` index and pre-created presentation and website folders.
- The blanket exclusion of generated materials; compiled outputs remain external, while approved reusable assets and templates may belong in the package.

## 0.1.0

Initial specification and blank brand package.
