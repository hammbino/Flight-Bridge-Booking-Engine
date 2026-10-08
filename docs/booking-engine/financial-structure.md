---
title: "Booking Engine: Financial Structure"
project: Flight Bridge Booking Engine
status: Active
owner: Mauricio Melendez / Jeffrey Hammond
last_updated: 2026-10-07
source_transcripts: [SV, FS, M0610, M0924, PARENT]
tags: [finance, revenue, arc, payments, booking-engine]
---

# Financial Structure (booking-relevant)

This covers how bookings make money and how money moves. Company-wide finance (credit card choice, banking, expense policy, team trips, Profit First accounting) stays in the parent repo's `financial-structure.md`.

## Partnership

- Flight Bridge is a 50/50 partnership between Mauricio Melendez and Jeffrey Hammond (PARENT).
- Jeff builds the software. Mauricio runs travel operations and business development (PARENT).
- No owner draws unless the partners talk first. ARC income stays in the account (FS 00:01:00).
- Entity details are disputed (CONF-BE-003).

## Funding the build

- Discussed, not finalized in SV: a $30k to $40k credit line paid by Traverse, with the builder keeping the points. Segment shares from the booking tool pay the builder until the software is built (SV 00:37:45 to 00:41:09). Mauricio would put 25 to 50 percent of his segment-share income toward the build (SV 00:43:05).
- In place by 05-22: Jeff's $2,500 a month is charged on a card through Traverse's merchant account, grossed up for fees (about $2,540 to $2,560), then moved to Flight Bridge and on to Jeff by ACH (FS 00:02:57). A Flight Bridge card cannot be charged on Flight Bridge's own merchant account, which is why Traverse's account is used (FS 00:04:26).

## Booking revenue streams

| Stream | What is known | Source | Status |
|--------|---------------|--------|--------|
| Sabre segment shares | About 30 cents per segment on the simple contract. Expected to rise after a 1,000-segment month ("two seventy", "up to seven", units unstated). Paid quarterly, or monthly at 50,000+ segments a year | SV 00:33:55, SV 00:45:01 | Rates unconfirmed (Q-BE-001) |
| Per-booking split | About $150 per booking, split between Traverse and Flight Bridge "the way we have it". Flight Bridge gets the commission "as the agent" | M0924 00:16:18, 00:17:18, 00:26:25 | Terms unknown (MI-BE-007, CONF-BE-006) |
| Newsletter-sourced bookings | Flight Bridge earns a percentage of anything booked from the newsletter | M0610 01:12:42 | Rate unknown |
| Corporate booking fee | $5 to $10 suggested per self-booking | SV 00:28:50 | Needs Review (DEC-BE-002) |
| Consumer booking fee | Suggested for price shoppers, no amount | SV 00:26:56 | Open (Q-BE-005) |
| Agency access fee | Centrav-style; at least covers hosting and AI | M0924 00:51:32 | Amount open (Q-BE-011) |

## ARC

- Bookings run under Traverse's ARC, including licensee agencies' bookings (DEC-BE-011).
- History: ARC was under Winifred's name. Mauricio sent her $1 per transaction, and she sent $0.50 to Flight Bridge (FS 00:00:00). She was to exit "in October" (year unstated) (FS 00:00:29). Mauricio gets 50 percent of segment shares (SV 00:27:28). On 09-24: Traverse "just barely got the ARC back about a year ago" (M0924 00:41:37).
- Some Traverse bookings still run through Brian Dickerson's ARC because of contracts he holds (M0924 00:23:59).
- Current status: open (Q-BE-002).

## Payments for bookings

- Flight Bridge does not process booking payments for now (DEC-BE-005). It captures card details through an authorization link without charging (SV 00:13:09).
- Stripe was planned for the email product only, with a later move to a regular merchant account to cut fees (FS 00:03:56). The newsletter now bills through a Kit-managed Stripe Express account (PARENT DEC-NL-014).
- How a Phase 2 self-booking customer pays is open (MI-BE-006).

## Competitor pricing reference

| Who | Price | Source |
|-----|-------|--------|
| Brian (competitor) | About $30 per booking | SV 00:28:50 |
| Trace | About $2,000 a year for what Mauricio needs | SV 00:31:27 |
| "T" (agent CRM) | $100/month for 5 users + $10 per extra user | SV 00:31:53 |
| SAP Concur via Dickerson | $500 to onboard Traverse; $1,500 to $2,000 setup for clients; per-ticket figure garbled | M0924 00:26:57, 00:43:55 |
| JourneyFuse | $25 per person (billing period unconfirmed) | PP 00:16:43 |
