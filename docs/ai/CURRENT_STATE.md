# Current State

## Current Status

This repo holds the Booking Engine docs. It was split from the parent Flight-Bridge repo on 2026-10-07.

The newsletter (parent repo) launched its free tier 2026-09-30. Free deal emails start the week of 2026-10-12. The paid upgrade is offered from 2026-11-01 (PARENT DEC-NL-017, M1008P). Those deal emails are the main traffic source for Book Now.

Sabre and ARC work is on hold until the ARC moves to Flight Bridge (DEC-BE-014, DEC-BE-015). Phase 1 Book Now is not on hold and is being launched now.

## In Progress: Phase 1 Book Now launch

Spec: `docs/superpowers/specs/2026-10-13-book-now-launch-design.md`. Plan: `docs/superpowers/plans/2026-10-14-book-now-launch.md` (10 tasks, subagent-driven). Ledger: `.superpowers/sdd/2026-10-14-book-now-launch/progress.md` (git-ignored, keep until Task 10).

- Tasks 1 to 6 done and reviewed. Final whole-branch review clean.
- Task 7 partly done (2026-10-15):
  - DNS added, and the domain is verified in GitHub.
  - Custom domain set, certificate approved (expires 2027-01-12), HTTPS forced.
  - HTTPS gate passed. The old github.io links redirect to the new domain.
  - Web3Forms key is in `config.js` (commit 1458ac3). Viktor's lead words are still empty.
  - 2026-10-21: Jeff submitted a Book Now test request from the Kauai test email. Not yet confirmed: that it reached info@flytraverse.com, and whether Viktor captured the customer email.
- Tasks 8 to 10 not started.

## Where the code lives

- Public repo `hammbino/flight-bridge-deals`, at `/Users/jeffrey/Sandbox/flight-bridge-deals`. Live at https://deals.flight-bridge.com/traverse-tours/ and `.../build.html`. 20 tests (`npm test`). Pushed. GitHub added commit d4a8c2c "Create CNAME".
- Kit draft script, in the parent repo: `scripts/kit_deal_email.py`, with 34 tests. Committed locally, not pushed.

## Waiting on people

- **Jeff:**
  - Kit segment size, or say "use the tag".
  - Gmail forwarding, once Mauricio sends the code.
- **Mauricio:**
  - Gmail code
  - Viktor's lead words
  - confirm the 2026-10-21 Book Now test arrived, and his OK on the Kauai deal email (PARENT Kit draft 26523663)
  - when he is free to test and approve

## Other blockers

- Q-BE-003 / Q-BE-004: database and Sabre method (Phase 2).
- ARC transfer (DEC-BE-014, Q-BE-019).
