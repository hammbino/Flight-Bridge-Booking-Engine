---
title: "Booking Engine: MVP Recommendations"
project: Flight Bridge Booking Engine
status: Active
owner: Mauricio Melendez / Jeffrey Hammond
last_updated: 2026-10-13
source_transcripts: [SV, EM, M0610, M0924]
tags: [mvp, booking-engine]
---

# Booking Engine MVP Recommendations

These are recommendations, not decisions. Each one is tied to the requirements and decisions it rests on.

## Recommended MVP scope

The MVP is the smallest thing that turns a newsletter deal into a booking under Traverse's ARC, with an agent in the loop.

### Must have

1. **Book Now lead form (Phase 1).** Prefilled deal, date change, traveler count, email-only contact, routed to info@traversetours.com (address disputed, CONF-BE-011). Needed before the pre-Black Friday sends (IMP-BE-014). Ship this first; it needs no Sabre work. Related: REQ-BE-008, REQ-BE-011, DEC-BE-006, BE-FB-010.
2. **Stable deal-link tokens.** Design them once, versioned, so links already sent keep working. Related: REQ-BE-003, Q-BE-007, RISK-BE-007.
3. **Bookable landing page (Phase 2).** Same page, now with live Sabre pricing, repricing on date change, and booking. Related: REQ-BE-001, REQ-BE-003, REQ-BE-009, DEC-BE-009.
4. **Agent follow-up on every booking.** Related: REQ-BE-010, BE-FB-012.
5. **Segment and source tracking from the first ticket.** Related: REQ-BE-005, BE-FB-005.

### Should have (soon after)

6. **Internal agent pilot** before wiring into the newsletter. Related: DEC-BE-008, BE-FB-011.
7. **Inquiry-to-booking tracking.** Related: REQ-BE-012, BE-FB-018.
8. **Corporate self-booking with fee.** Related: REQ-BE-002, BE-FB-004.

### Defer

- Agency hosting and the Concur-style product (DEC-BE-004, DEC-BE-010)
- PNR import, until ownership is settled (Q-BE-008)
- Full Sabre wrapper, hotels, packages, delay alerts

## Why this order

- Phase 1 needs no Sabre integration, so it can ship while Q-BE-003 and Q-BE-004 are answered.
- Flight-only deals are expected to move into the engine most easily (DEC-BE-007), so flights come before packages.
- Every source puts a human-handled step before self-booking (CONF-BE-004, "where they agree").

## Related Requirements

REQ-BE-001, REQ-BE-002, REQ-BE-003, REQ-BE-005, REQ-BE-008, REQ-BE-009, REQ-BE-010, REQ-BE-011, REQ-BE-012
