# Current State

## Current Status

Repo created 2026-10-07 by splitting the Booking Engine out of the parent Flight-Bridge repo. Documentation only. No code yet.

The newsletter (parent repo) launched its free tier 2026-09-30. Basic (flight deals) goes live about the first week of November 2026, and VIP (packages) about early December 2026 (PARENT DEC-NL-017). On 10-08 the timeline moved up: free deal emails from the week of 2026-10-12 and the paid upgrade offered from 2026-11-01. The 10-08 Black Friday plan proposes selling VIP over Black Friday weekend, with a package deal on 2026-11-30 (PARENT DEC-NL-029, proposed). Those deals are the main traffic source for this engine.

On 10-08 the partners agreed to transfer the ARC to Flight Bridge (DEC-BE-014). Booking engine work that needs Sabre is on hold until then and will not be ready for November (DEC-BE-015). Phase 1 Book Now is not on hold.

## In Progress

Nothing. Waiting on Jeffrey's review of the split (`docs/booking-engine/migration-notes.md`).

## Important Files

- `docs/booking-engine/project-state.md`: full status and blockers
- `docs/booking-engine/migration-notes.md`: what changed in the split, including corrections to review
- `docs/booking-engine/roadmap.md`: phases (numbering disputed, CONF-BE-004)
- `docs/booking-engine/open-questions.md`: what blocks what

## Blockers

- CONF-BE-011: Phase 1 inbox address (info@traversetours.com or info@flytraverse.com)
- Q-BE-007: deal-link token schema
- ARC transfer (DEC-BE-014, Q-BE-019): all Sabre work is on hold until it is done (DEC-BE-015)
- Q-BE-003 / Q-BE-004: database and Sabre method (block Phase 2)
