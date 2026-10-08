# Flight Bridge Booking Engine: Repository Standards

These standards apply to all documentation and code in this repository. Every command and agent that produces or edits documentation must follow them.

---

## Start Here (for agents)

Read in this order. Stop once you have what the task needs.

1. `docs/ai/PROJECT_CONTEXT.md`: what the booking engine is, who it serves, business rules.
2. `docs/ai/CURRENT_STATE.md` and `docs/ai/NEXT_TASK.md`: where work stands and what is next.
3. `docs/booking-engine/project-state.md`: full status, blockers, pending decisions.
4. Look up specifics by ID in `docs/booking-engine/` (requirements, decisions, questions, backlog).
5. Need the evidence behind an entry? Open the matching digest in `docs/sources/`. Each digest point has a speaker and timestamp.

Do not scan the whole repo unless the task needs it.

---

## Project

This repository holds one product: the **Flight Bridge Booking Engine**.

- `docs/booking-engine/`: the living knowledge base (requirements, decisions, roadmap, and so on).
- `docs/sources/`: one agent-optimized digest per source transcript, booking content only.
- `docs/ai/`: short working-state files used by `/start`, `/build`, `/checkpoint`, `/finish`.
- `Transcripts/`: drop new raw transcripts here, then run `/process-transcripts`.

**Parent repo:** this repo was split out of `/Users/jeffrey/Sandbox/Flight-Bridge` (GitHub `hammbino/Flight-Bridge`) on 2026-10-07. The Newsletter and CRM products, and the original raw transcripts, live there. Do not recreate `docs/newsletter/` or `docs/crm/` here.

**Sibling products:** anything the booking engine needs from, or provides to, the Newsletter or CRM is recorded in `docs/booking-engine/sibling-dependencies.md`. IDs with `-NL-` or `-CRM-` (for example `DEC-NL-011`, `REQ-CRM-004`) belong to the parent repo. Cite them, but do not edit or renumber them here.

---

## Required Files

`docs/booking-engine/` MUST contain:

```
project-state.md
vision.md
requirements.md
implicit-requirements.md
product-decisions.md
assumptions.md
conflicting-requirements.md
missing-information.md
open-questions.md
risks.md
mvp-recommendations.md
roadmap.md
backlog.md
```

---

## Additional Documentation

Create additional markdown files whenever a topic naturally deserves its own document. Examples:

```
pricing.md          marketing.md         content-strategy.md
launch-plan.md      user-personas.md     workflows.md
automation.md       integrations.md      entities.md
database.md         api.md               technical-architecture.md
journeyfuse-analysis.md                  missing-features.md
ui-notes.md
```

Prefer many focused markdown files over a few extremely large ones. Do not force unrelated information into `requirements.md`.

---

## YAML Front Matter

Every markdown document MUST begin with this front matter block:

```yaml
---
title:
project:
status:
owner:
last_updated:
source_transcripts:
tags:
---
```

Update this metadata whenever the document changes.

Valid `status` values for general documents: `Draft`, `Active`, `Needs Review`, `Superseded`.

---

## Requirement Management

Every requirement must receive a permanent identifier (e.g. `REQ-001`).

Each requirement must contain:

| Field | Description |
|-------|-------------|
| ID | Permanent unique identifier |
| Requirement | One-line statement |
| Description | Full detail |
| Priority | High / Medium / Low |
| Status | Draft / Confirmed / Deferred / Complete |
| Source Transcript(s) | Filename(s) |
| Related Requirements | IDs |
| Related Decisions | IDs |

Never duplicate requirements. Update existing requirements when new information is discovered. Preserve existing requirement IDs.

---

## Product Decisions

Maintain `product-decisions.md`. Each decision must receive a permanent identifier (e.g. `DEC-001`).

Each decision must include:

| Field | Description |
|-------|-------------|
| Decision ID | Permanent unique identifier |
| Decision | What was decided |
| Reasoning | Why |
| Alternatives Considered | What else was discussed |
| Status | Proposed / Agreed / Final / Needs Review |
| Date | If known |
| Source Transcript(s) | Filename(s) |
| Related Requirements | IDs |

If a later source finalizes, clarifies, or changes an earlier discussion, update the existing decision instead of creating a duplicate. Preserve existing decision IDs.

---

## Open Questions

Maintain `open-questions.md`. Each question must receive a permanent identifier (e.g. `Q-001`).

Each question must include:

| Field | Description |
|-------|-------------|
| Question | The open question |
| Why it matters | Impact if unresolved |
| Owner | If known |
| Priority | High / Medium / Low |
| Blocking | What it blocks |
| Source Transcript(s) | Filename(s) |

Remove a question only when it is clearly resolved, then convert the answer into the appropriate documentation. Preserve existing question IDs.

---

## Backlog

Maintain `backlog.md`. Every feature request or enhancement must receive a permanent identifier (e.g. `FB-001`).

Each backlog item must contain:

| Field | Description |
|-------|-------------|
| ID | Permanent unique identifier |
| Title | Short label |
| Description | Full detail |
| Business Value | Why it matters |
| Priority | High / Medium / Low |
| Dependencies | Blocking items |
| Status | Idea / Planned / In Progress / Deferred / Complete |
| Source Transcript(s) | Filename(s) |

Preserve existing backlog IDs.

---

## Project State

Maintain `project-state.md` so it always reflects the current state of the project. Include:

- Current Goal
- Current Phase
- Overall Health
- Completion Estimate
- Current Blockers
- Critical Decisions Pending
- Next Milestone
- Immediate Next Actions
- Recent Changes
- Last Review Date

This file must provide enough context for a new engineer or AI agent to immediately understand where the project stands.

---

## Roadmap

Maintain `roadmap.md`. Include:

- Current Phase
- Completed Milestones
- Upcoming Milestones
- Future Milestones
- Out of Scope
- Release Goals
- Known Dependencies

---

## File Management Rules

- If a required file does not exist: create it.
- If it already exists: update it.
- Never overwrite useful information.
- Merge duplicates. Consolidate similar ideas.
- Preserve historical decisions. Preserve existing IDs.
- Maintain consistent formatting across the repository.
- If sources disagree on a fact, requirement, or decision, document the conflict in `conflicting-requirements.md` rather than choosing a winner. Do not silently discard either position.

---

## Traceability

Every requirement, decision, assumption, risk, question, backlog item, and recommendation must reference one or more source files. Documentation must always be traceable back to its sources.

Cite sources with the **short source keys** defined in `docs/sources/README.md`, plus a timestamp where one exists (for example `SV 00:28:50`). Each key maps to a digest and to the original transcript filename(s). YAML `source_transcripts` fields use the keys too, except in the digests in `docs/sources/`, which list the original filenames so the key-to-filename mapping is kept. When a new transcript is processed, add its key to that table first. Raw transcripts processed before 2026-10-07 are not in this repo; they live in the parent repo's `Transcripts/` folder. Non-transcript sources (a direct decision in a working session, a document in Drive) are cited by name and date.

---

## Cross-References

Cross-link related documentation wherever appropriate:

- Requirements → related decisions
- Decisions → requirements
- Risks → assumptions
- Roadmap items → backlog items
- MVP recommendations → requirements
- Open questions → affected documents

Maintain a connected knowledge base rather than isolated documents.

---

## Extraction Rules

- Extract only supported information.
- Separate facts from opinions.
- Separate confirmed decisions from ideas.
- Separate assumptions from requirements.
- Separate risks from open questions.
- Never invent information. Never make assumptions.
- When information is uncertain or confidence is below 100%, explicitly document the uncertainty and explain why.
- Do not infer missing information.
- When a requirement is not explicitly stated but appears to be implied by the conversation, do NOT add it to `requirements.md`. Instead, add it to `implicit-requirements.md` for human review. Document exactly what was said and what requirement appears to be implied. Do not treat it as confirmed. A human must promote it to `requirements.md` or discard it.