# Project Context

## What This Project Is

The Flight Bridge Booking Engine: a flight booking tool built on Traverse's direct Sabre access, ticketing under Traverse's ARC number. Newsletter deal links land here. Phase 1 is a "Book Now" lead form that routes to a human agent. Phase 2 lets customers book on the page, and an agent still follows up on every booking. Later: corporate self-booking with a fee, and paid access for other agencies ("the Picasso, but better").

Split out of the parent repo `/Users/jeffrey/Sandbox/Flight-Bridge` on 2026-10-07. The Newsletter and CRM live there.

## Who This Is For

- Newsletter subscribers acting on a deal (Traverse Tours customers)
- Price shoppers and corporate travelers who self-book
- Traverse's human agents, who follow up on every booking
- Later: other travel agencies that lack an ARC

Business: Flight Bridge (50/50 Jeffrey Hammond and Mauricio Melendez). Traverse Tours is the first licensee. Pages are branded "Traverse Tours powered by Flight Bridge".

## Tech Stack

Not decided. Known constraints:
- GDS: Sabre (direct access). Integration method open: Q-BE-004
- Database: SQL vs NoSQL open: Q-BE-003
- AI: hosted API first, self-hosted fallback (DEC-BE-013)
- Newsletter platform (link source): Kit, in the parent repo
- Payments: not processed for now (DEC-BE-005)

## How To Run

No code yet.

## How To Test

No code yet.

## Important Business Rules

- Bookings run under Traverse's ARC, including partner agencies' bookings (DEC-BE-011)
- Book Now keeps the customer on our site, never the airline's or Google Flights (REQ-BE-011)
- Every self-booking goes to a human agent for follow-up (REQ-BE-010)
- No account required to view or act on a deal (REQ-BE-007)
- Flight Bridge does not process payments for now (DEC-BE-005)
- Never build a GDS (DEC-BE-001)
- "Agent" means a human booking agent unless the doc says "AI agent"

## Important Technical Rules

- Deal-link tokens must be stable and versioned, because sent emails cannot be changed (RISK-BE-007)
- Every form must be verified to store or route what it captures (IMP-BE-009)
- Customer-facing pages use real Traverse brand assets (`docs/booking-engine/ui-notes.md`)

## Notes For Claude

- Start with CLAUDE.md "Start Here". Look up IDs in `docs/booking-engine/`.
- Evidence is in `docs/sources/` (source keys + timestamps).
- Do not recreate newsletter or CRM docs here. Cross-product links are in `docs/booking-engine/sibling-dependencies.md`.
- Keep context tight. Do not scan the whole repo unless needed.
