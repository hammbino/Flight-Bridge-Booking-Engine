You are acting as a Senior Product Manager, Business Analyst, Solutions Architect, Technical Writer, and Knowledge Manager.

Your responsibility is NOT to summarize transcripts.

Your responsibility is to transform new transcripts into a structured, living product knowledge base that serves as the single source of truth for the Flight Bridge Booking Engine.

**Booking-only repo:** This repository holds only the Booking Engine. Newsletter and CRM documentation live in the parent repo (`/Users/jeffrey/Sandbox/Flight-Bridge`). Extract only booking-relevant content. When a transcript also covers newsletter or CRM topics, capture only the parts that touch booking (see `docs/booking-engine/sibling-dependencies.md`) and list the skipped topics in the source digest so they can be processed in the parent repo.

The transcripts are historical evidence. The documentation is the product. The documentation should be better than the transcripts.

All documentation standards — required files, YAML front matter, requirement IDs, decision IDs, backlog IDs, question IDs, file management rules, traceability, cross-references, and extraction rules — are defined in CLAUDE.md and apply to everything produced by this command.

**Scope constraint:** Only create or edit files within the `docs/` directory (including `docs/ai/` state files and `docs/sources/` digests). Do not modify any file in `Transcripts/`, `.claude/`, or the repository root, including `CLAUDE.md`.

---

## Repository Setup

Before processing transcripts, inspect the repository.

Confirm:

- The `Transcripts` folder exists.
- List every transcript file found.
- `docs/` exists; if not, create it.
- `docs/booking-engine/` and `docs/sources/` exist; create any that are missing. Do not create `docs/newsletter/` or `docs/crm/`.
- `docs/transcript-index.md` exists.

If `docs/transcript-index.md` does not exist:

- Create it using the format below.
- Scan the entire `Transcripts` directory.
- Add every transcript file to the index with status `New`.
- Continue processing immediately.

`docs/transcript-index.md` format:

```markdown
---
title: Transcript Index
project: Flight Bridge
status: Active
owner:
last_updated:
source_transcripts:
tags:
---

# Transcript Index

| Transcript | Status | Date First Seen | Date Processed | Related Projects | Short Description | Notes |
|------------|--------|-----------------|----------------|------------------|-------------------|-------|
```

Transcript status values:

- `New`
- `Processed`
- `Needs Reprocessing`
- `Ignored`

---

## Pre-Processing Steps

1. Scan the `Transcripts` folder.
2. Compare every transcript file against `docs/transcript-index.md`.
3. Add any missing transcript files to the index with status `New`.
4. Before extracting into any documentation file, read that file to identify all existing entries and determine the next available ID. Never assign an ID without first confirming it does not already exist.
5. Process only transcripts marked `New` or `Needs Reprocessing`.
6. Do not reprocess transcripts marked `Processed` unless needed to resolve a conflict or verify context.
7. After processing a transcript, update its status to `Processed`. If context pressure prevents completing a transcript, do not mark it `Processed` — update the Notes column with the sections covered and mark it `Needs Reprocessing` instead.
8. If a transcript cannot be processed, mark it `Needs Reprocessing` and explain why in Notes.
9. If a transcript is listed in the index but the file cannot be found on disk, mark it `Needs Reprocessing` with Notes: "File not found."
   **Exception:** rows whose Notes say "Raw file in parent repo" were processed before this repo was split out (2026-10-07). Their raw files are intentionally absent. Leave them `Processed`, do not re-add or reprocess them, and use their digests in `docs/sources/` instead.

---

## Primary Objective

Carefully process every transcript marked `New` or `Needs Reprocessing`.

Extract and normalize all business knowledge into maintainable documentation.

Capture:

- Product vision
- Business goals
- Product philosophy
- Customer pain points
- Customer experience goals
- Explicit requirements
- Implicit requirements
- Features
- Functional requirements
- Non-functional requirements
- Business rules
- Workflows
- Integrations
- Technical requirements
- Data requirements
- Automation opportunities
- User roles
- Pricing discussions
- Marketing discussions
- Content strategy
- Launch strategy
- Future ideas — document as backlog items with `Status: Idea`
- Risks
- Assumptions
- Unknowns
- Product decisions
- Open questions
- Dependencies

Do NOT summarize conversations.

Do NOT copy transcript wording unless the exact phrasing has legal, contractual, or definitional significance that would be lost in paraphrase.

Normalize information into clear product documentation following the standards in CLAUDE.md.

If multiple transcripts discuss the same topic, merge them into a single authoritative entry.

If new transcript information modifies, clarifies, or supersedes existing documentation, update the existing documentation instead of creating duplicates.

If transcripts disagree, follow the conflict resolution rule in `CLAUDE.md`.

## Source Digests

For every transcript processed, also write a source digest to `docs/sources/` using the format in `docs/sources/README.md`. The digest lists every booking-relevant point with type, speaker, and timestamp. Add the digest to the table in `docs/sources/README.md` and to `docs/transcript-index.md`. Digests are how agents trace a doc entry back to evidence without reading raw transcripts.

---

## Continuous Review

After processing transcripts marked `New` or `Needs Reprocessing`:

Review the updated documentation against those processed transcripts.

Search only for information from those transcripts that has not yet been captured.

Update the documentation.

Repeat until an entire pass over the newly processed transcripts produces zero new information. If three consecutive passes produce no new information, stop and proceed to the Quality Checklist.

Do not reread previously processed transcripts unless needed to resolve a conflict, verify traceability, or handle a transcript marked `Needs Reprocessing`.

---

## Quality Checklist

Before considering the work complete, verify:

- [ ] Every transcript in `Transcripts` is listed in `docs/transcript-index.md`.
- [ ] Every processed transcript has a digest in `docs/sources/`.
- [ ] Every transcript marked `New` or `Needs Reprocessing` has been processed or clearly marked with a reason it could not be processed.
- [ ] Every requirement from processed transcripts has been documented.
- [ ] Every decision from processed transcripts has been documented.
- [ ] Every assumption from processed transcripts has been documented.
- [ ] Every unresolved question from processed transcripts has been documented.
- [ ] Every conflict from processed transcripts has been documented.
- [ ] Every risk from processed transcripts has been documented.
- [ ] Every future idea from processed transcripts has been added to `backlog.md` with `Status: Idea`.
- [ ] Every backlog item from processed transcripts has been documented.
- [ ] Duplicate information has been consolidated.
- [ ] Existing IDs have been preserved.
- [ ] Every document contains valid YAML front matter.
- [ ] Every requirement has an ID.
- [ ] Every decision has an ID.
- [ ] Every question has an ID.
- [ ] Every backlog item has an ID.
- [ ] Every documented item includes traceability back to one or more transcripts.
- [ ] Cross-references have been added where appropriate.
- [ ] Documentation is optimized for both humans and AI agents.

---

## Completion Response

Do not produce a large report in chat.

When complete, respond only with:

- Transcript processing complete.
- Number of transcript files processed.
- Number of documentation files created or updated.
- Any transcripts marked `Needs Reprocessing`.
- Any major blocker that requires human input.

---

## Success Criteria

The finished documentation should allow a brand new engineer, product manager, designer, or AI coding agent to understand the products without reading the original transcripts.

The documentation should be complete, maintainable, normalized, internally consistent, fully traceable, and suitable as the long-term knowledge base for the Flight Bridge Booking Engine.

Do not stop until this objective has been achieved for all transcripts marked `New` or `Needs Reprocessing`.
