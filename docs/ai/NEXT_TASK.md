# Next Task

## Objective

Jeffrey reviews the repo split, especially the corrections in `docs/booking-engine/migration-notes.md` section 3. Then pick the first build task.

## Proposed first build task (after review)

Phase 1 Book Now lead form (BE-FB-010, REQ-BE-008). It needs no Sabre work. Lead routing is settled: info@flytraverse.com, monitored by Mauricio and Viktor (Q-BE-010, resolved 2026-10-13). Before building, answer:
1. CONF-BE-011: confirm the inbox address (info@flytraverse.com or info@flytraverse.com).
2. Q-BE-007: what goes in the deal link? Draft: `docs/booking-engine/deal-links.md`. Jeff picks the open items in its section 5, starting with the domain.

Confirmed 2026-10-14: no form or message page exists yet. On 10-08, "set to owner@" referred to the owner@ address recorded in the notes (working session 2026-10-07), not a built page (Jeff). The form is built new (see `docs/superpowers/specs/2026-10-13-book-now-launch-design.md`).

## Success criteria

A test deal link opens the form prefilled. A test submission reaches info@flytraverse.com and is confirmed received.

## Relevant Files

- `docs/booking-engine/requirements.md` (REQ-BE-008)
- `docs/booking-engine/workflows.md` (W1)
- `docs/booking-engine/ui-notes.md`
