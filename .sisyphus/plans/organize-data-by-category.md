# Plan: Organize Data by Category (Per-Category Reorganization)

TL;DR
- Create a clean, category-based folder structure for questions and answers to improve revision speed and maintenance.
- Move existing items into per-category folders, introduce metadata-driven indexing, and provide a simple migration map.
- Deliver a catalog (index pages) and a minimal README to guide contributors.

Deliverables
- A canonical folder layout (questions/ and answers/ split by category).
- Per-item front matter with id, title, category, tags, date_added, last_modified, and sources.
- Metadata registry and index pages to navigate by category and tag.
- A migration guide mapping current items to the new structure.

Assumptions (discoverable from the repo)
- The README currently lists categories and topics (e.g., BASICS, FUNCTIONS) but there are no per-item front matters yet.
- Content currently lives as Markdown files in a flat structure (per-topic questions in the README context and separate Markdown files may exist elsewhere).
- We will infer category taxonomy from the README and from existing filenames/titles during migration.

Scope (IN)
- Create directory tree: questions/by-category/{category-slug}/, answers/by-category/{category-slug}/
- Enforce slug-based filenames: YYYY-MM-DD-title-slug.md
- Add metadata files under metadata/ (schema.yaml, categories.yaml, tags.yaml, items.yaml)
- Generate index/pages under index/ (by-category.md, by-tag.md, index.md)
- Provide a migration map to guide moving existing items.

Scope (OUT)
- Any code changes outside of plan planning (no execution in this phase)
- No removal of data without confirmation
- No automate data transformation in this step (plan-only)

Key Decisions
- Directory structure: Questions and Answers are organized by category. This enables fast revision by category and supports per-category progress tracking.
- Front matter: Each item will have a canonical YAML front matter including id, title, category, tags, topics, difficulty, date_added, last_modified, sources, and related.
- Indexing: Metadata-driven index pages will be maintained in index/ (generated or hand-maintained as a README-like index).
- Migration approach: Use a mapping template to translate existing files to the new structure, without loss of content; preserve old locations temporarily for traceability.

Gaps / Risks and Mitigations
- Gap: Determining an authoritative category taxonomy. Mitigation: start with the top-level categories visible in the README (e.g., basics, functions) and expand as items are migrated.
- Risk: Slug collisions. Mitigation: enforce YYYY-MM-DD-<slug> naming and, if needed, a per-day counter.
- Risk: Metadata drift. Mitigation: centralize metadata in metadata/*, generate item front matter from that registry.

Migration Plan (high level)
- Phase 1: Prepare structure and templates
  - Create top-level folders: questions/by-category, answers/by-category, index/
  - Add metadata/schema.yaml with the core fields; add categories.yaml and tags.yaml placeholders.
  - Create a simple migration map template file: migrations/README.md.
- Phase 2: Move a representative subset (pilot)
  - Pick 2-3 categories (e.g., basics, functions) and migrate 2-4 sample items into new structure.
  - Create front matter for these items and verify index generation reads them.
- Phase 3: Extend to all items
  - Complete migration for all items; populate items in metadata/items.yaml.
- Phase 4: Build index pages and search index; update README with conventions.
- Phase 5: Review and finalize (Metis/Momus optional) and hand off to execution.

Open Questions for You (Decision Needed)
- Which taxonomy is the preferred canonical source of truth for categories (e.g., BASICS, FUNCTIONS, PROMISES, etc.)? If you provide a list, I will lock it in the metadata and folder names.
- Do you want a per-category index page generated dynamically or a single static index with category sections?
- Should we immediately generate a machine-readable search index (JSON) as part of this migration, or start with static HTML index pages and add search later?

Plan traceability
- All changes will be tracked in .sisyphus/plans/organize-data-by-category.md and associated metadata in metadata/ and index/
- A migration map template will be used to map existing items to new paths and IDs.

Next steps
- If you approve, I’ll generate a concrete migration map template and a starter folder skeleton, then draft the corresponding .sisyphus/drafts/{topic-slug}.md with the first set of concrete moves.

Decision required: Do you want me to proceed to generate the concrete skeleton by category and a sample migration map now? (Recommended: Yes, to begin the concrete steps.)
