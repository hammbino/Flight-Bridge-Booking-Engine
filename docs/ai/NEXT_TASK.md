# Next Task

## Objective

Jeffrey reviews the repo split, especially the corrections in `docs/booking-engine/migration-notes.md` section 3. Then pick the first build task.

## Proposed first build task (after review)

Phase 1 Book Now lead form (BE-FB-010, REQ-BE-008). It needs no Sabre work. Lead routing is settled: info@traversetours.com, monitored by Mauricio and Viktor (Q-BE-010, resolved 2026-10-13). Before building, answer:
1. CONF-BE-011: confirm the inbox address (info@traversetours.com or info@flytraverse.com).
2. Q-BE-007: what goes in the deal link? Draft: `docs/booking-engine/deal-links.md`. Jeff picks the open items in its section 5, starting with the domain.

Checked 2026-10-13: no contact form was found in the parent repo or in Kit. But on 10-08 Jeff described a send-a-message page that already exists, pointed at owner@ (M1008P L896-901). Find out where it lives before building anything.

## Success criteria

A test deal link opens the form prefilled. A test submission reaches info@traversetours.com and is confirmed received.

## Relevant Files

- `docs/booking-engine/requirements.md` (REQ-BE-008)
- `docs/booking-engine/workflows.md` (W1)
- `docs/booking-engine/ui-notes.md`
