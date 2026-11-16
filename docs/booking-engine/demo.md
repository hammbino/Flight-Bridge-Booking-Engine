---
title: "Booking Engine: Demo Page"
project: Flight Bridge Booking Engine
status: Needs Review
owner: Jeffrey Hammond
last_updated: 2026-11-15
source_transcripts: [Direct work session, Jeffrey Hammond and Claude, 2026-11-15]
tags: [demo, ui, booking-engine]
---

# Demo Page

`demo/index.html` is a single-file clickable demo of the booking flow. It is for showing the idea to Mauricio and others. It is not the Phase 1 Book Now page, which lives in the `flight-bridge-deals` repo (see `docs/ai/CURRENT_STATE.md`).

## What is real and what is mocked

- **Mocked:** every fare except the $299 San Diego deal, all flight times, the date-spread prices, the reference number. Nothing is sent or charged. Sabre is not connected (DEC-BE-015).
- **Real:** the look (Traverse colors, fonts and logo, Flight Bridge badge from the newsletter footer), the deal-link format (`deal-links.md`), and the lead email subject format (Book Now launch design, section 5.5). The default deal is `scripts/deals/2026-12-slc-san.json` in the parent repo.

## How it follows the docs

| Behavior | Source |
|----------|--------|
| Branded "Traverse Tours, powered by Flight Bridge" | `ui-notes.md`, PARENT DEC-NL-009 |
| Deal preloaded from the link and editable | REQ-BE-003, REQ-BE-008 |
| Date spread with prices, "My dates are different" | REQ-BE-009 |
| Traveler count, every traveler priced | `ui-notes.md` (M0610 00:47:58) |
| No account, no phone field, email only | REQ-BE-007, M1008P L910-920 |
| No payment step, agent confirms price | DEC-BE-005, REQ-BE-010 |
| Stays on our site | REQ-BE-011 |
| Price shown "as found on [date], subject to change" | PARENT automation.md language guard |

## Open points for review

- The demo shows Phase 2 style browsing (search, pick a flight) that ends in a Phase 1 style request. That hybrid is not in any decision. It is a picture of where the two phases meet, not a plan.
- The "Flight Bridge" badge is the newsletter footer logo. The brand guide badge in `ui-notes.md` was not compared (CONF-BE-010).
- Each traveler's name as on their ID and date of birth are collected. This was a direct instruction from Jeffrey on 2026-11-15. It is not yet in `requirements.md`, and where DOB is stored and who may see it is not decided.
- Email: required on every request. If the deal link carries `&email=` the field is prefilled and editable, and the request records whether the address came from the link or was typed. On 2026-10-14 Jeffrey decided not to prefill name and email (Book Now launch design, section 11). His 2026-11-15 instruction (email can be filled from the link, but one is always needed) reverses that for email. Kit's merge tag for the subscriber email in the link is not verified.
- Hosting is not decided. It needs GitHub Pages on this repo, or another host.

## Preview locally

Open `demo/index.html` in a browser. To preload a deal, add `?from=SLC&to=SAN&depart=2026-12-03&return=2026-12-07&price=299&found=2026-11-02&travelers=2`.
