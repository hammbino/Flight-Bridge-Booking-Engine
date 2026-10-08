---
title: "Booking Engine: Migration Notes (2026-10-07)"
project: Flight Bridge Booking Engine
status: Needs Review
owner: Jeffrey Hammond
last_updated: 2026-10-07
source_transcripts: [SV, R1205, M0610, M0924, PARENT]
tags: [migration, review, changelog]
---

# Migration Notes: split from the parent repo, 2026-10-07

What changed when the Booking Engine moved from `Flight-Bridge/docs/booking-engine/` into this repo. **Jeffrey: review sections 2 and 3.** They change what earlier docs said.

## 1. What moved, and how

- All 15 parent booking-engine files were carried over. Every existing ID is kept: REQ-BE-001 to 007, DEC-BE-001 to 005, Q-BE-001 to 006, BE-FB-001 to 009, ASM-BE-001 to 007, RISK-BE-001 to 005, IMP-BE-001 to 005, MI-BE-001 to 006, CONF-BE-001 to 003.
- The 15 raw transcript files (9 unique conversations) were **not** copied. Each conversation was re-read in full and turned into a booking-only digest in `docs/sources/`. Docs cite short source keys plus timestamps.
- Booking-relevant content from the parent's newsletter, CRM and `docs/ai` files was summarized in `sibling-dependencies.md`, citing the parent IDs.
- New topic files: `workflows.md`, `ui-notes.md`, `competitive-landscape.md`, `glossary.md`, `sibling-dependencies.md`, this file.
- `financial-structure.md` was cut down to booking-relevant finance. The full version stays in the parent repo.

## 2. Content captured for the first time

The 06-10 and 09-24 meetings were only ever processed into newsletter docs. Their booking content is new here:

- DEC-BE-006 Phase 1 Book Now is lead capture (M0610, M0924)
- DEC-BE-007 flight deals move to the engine first; packages stay with agents (M0610)
- DEC-BE-008 agents pilot the engine 1 to 2 weeks first (M0610)
- DEC-BE-009 Phase 2 real booking with agent follow-up (M0924)
- DEC-BE-010 build order: newsletter, booking tool, Concur-style B2B (M0924)
- DEC-BE-011 bookings run under Traverse's ARC, including licensees (PP, R1205, M0924)
- DEC-BE-012 Traverse agents do not use the fee portal (R1205) (conflicts with DEC-BE-008)
- DEC-BE-013 AI approach (PP)
- REQ-BE-008 to REQ-BE-015, Q-BE-007 to Q-BE-018, CONF-BE-004 to 010, RISK-BE-006 to 014, IMP-BE-006 to 013, ASM-BE-008 to 013, MI-BE-007 to 008, BE-FB-010 to 019
- DEC-BE-004 was extended with the 09-24 agency model (access fee, no buy-outs)

## 3. Corrections to earlier docs (checked against the transcript)

| ID | Earlier doc said | Transcript says | Change |
|----|------------------|-----------------|--------|
| DEC-BE-002 / CONF-BE-002 | The $5 to $10 corporate fee was set to undercut Brian's ~$30 | "this isn't to undercut Brian because his clients are very different than our clients" (SV 00:28:50) | Reasoning corrected. CONF-BE-002 superseded. Status → Needs Review |
| DEC-BE-002 / REQ-BE-002 | A 1-hour agent review window is agreed | Mauricio's idea for a future dedicated hire (SV 00:27:51) | Moved to an idea in BE-FB-004 |
| DEC-BE-003 | Segment shares are the primary revenue; fees are secondary | No ranking stated. 09-24 frames revenue per booking instead | Reworded. Status → Needs Review. CONF-BE-006 added |
| DEC-BE-005 | Bookings go "through Sabre with established airline/agent billing relationships" | Not stated. Mauricio said third-party processing could come "down the line" and card details are captured by link | Reworded |
| DEC-BE-001 | "Do NOT build a Sabre wrapper for MVP" | Order only: PNR import first, wrapper "eventually" | Reworded. Status unchanged |
| DEC-BE-004 | Reason: agencies lack Sabre access | Not stated in SV. 09-24 says most small agencies lack an ARC | Reason updated from 09-24 |
| ASM-BE-004 | 8 to 9 eligible agencies that could use Flight Bridge as host | 8 to 9 host ("Picasso") companies | Reworded |
| BE-FB-009 | "Do not cold-call. Use network referrals." | Mauricio called (no answer) and tried dropping in | Removed the instruction |
| BE-FB-006 | Status Idea | Agreed direction on 09-24 | Status → Planned |

Every correction keeps the earlier wording in a Notes or Change log field.

## 4. What stayed in the parent repo

- `docs/newsletter/`, `docs/crm/`, raw `Transcripts/`
- The Kit API key (`.env.local`) and the Kit API memory. Booking work does not need them.
- The parent repo was not modified by this split.
