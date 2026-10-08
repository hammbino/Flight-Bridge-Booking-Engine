---
title: "Booking Engine: Assumptions"
project: Flight Bridge Booking Engine
status: Active
owner: Mauricio Melendez / Jeffrey Hammond
last_updated: 2026-10-07
source_transcripts: [SV, PA, PP, M0610, M0924]
tags: [assumptions, booking-engine]
---

# Booking Engine Assumptions

Beliefs stated in the sources but not verified. Risks that depend on them link back here.

## ASM-BE-001

Traverse has direct Sabre access. It no longer has to rely on a third party or the PC-based uploader on a virtual machine. This is what makes the booking engine possible.
**Source:** SV 00:26:00 ("Now we do"), SV 00:07:29
**Related:** DEC-BE-001, RISK-BE-002

## ASM-BE-002

Traverse is on Sabre's "simple contract". Mauricio paid a couple thousand dollars for it, and it allows some ticketing. The rate is about 30 cents per segment. Moving to a "subscriber contract" needs a track record of 1,000 segments in one month, with renegotiation planned for January/February.
**Uncertainty:** the later rates ("two seventy", "up to seven") have no stated units, and they were framed around Winifred's earnings.
**Source:** SV 00:33:55, SV 00:43:05 to 00:45:01
**Related:** DEC-BE-003, Q-BE-001, RISK-BE-001

## ASM-BE-003

Hitting 1,000 segments in a single month is achievable. Mauricio planned a December push, pulling bookings built by others into his Sabre so Traverse gets the credit.
**Source:** SV 00:41:44 to 00:42:35
**Related:** RISK-BE-001

## ASM-BE-004

There are about eight or nine host ("Picasso") companies between Kansas and the West Coast. Mauricio's estimate, not verified. "Picasso" is the transcript spelling.
**Source:** SV 00:33:30
**Related:** DEC-BE-004, REQ-BE-006
**Correction 2026-10-07:** the parent wording said these were "eligible travel agencies that could use Flight Bridge as a host". The transcript counts the host companies themselves, not client agencies.

## ASM-BE-005

Corporate travelers who want to book on their own would pay a small per-booking fee ($5 to $10 suggested).
**Source:** SV 00:28:50
**Related:** DEC-BE-002, RISK-BE-004

## ASM-BE-006

Flight Bridge does not need to build pricing from scratch. Sabre returns prices on request. Mauricio's Continental Airlines shell: "hit price... they would give you the price immediately". The work is the UI over Sabre.
**Source:** SV 00:10:23 to 00:11:47
**Related:** DEC-BE-001

## ASM-BE-007

A full Sabre wrapper is a future state. Early versions use Sabre behind the scenes, starting with PNR / last-name import.
**Source:** SV 00:09:26
**Related:** DEC-BE-001, CONF-BE-001

## ASM-BE-008

Illustrative booking math: 1,000 subscribers, 1% book, so 10 bookings a month at about $150 average, giving about $1,500 a month. International bookings are worth much more. Unclear whether $150 is ticket value or revenue.
**Source:** M0924 00:16:18 to 00:17:14
**Related:** CONF-BE-006

## ASM-BE-009

Earlier conversion guess from the existing client list: about 4,000 to 5,000 emails, about 1% to the free newsletter (about 40), about 1% of those (about 4) to VIP. A rough guess.
**Note:** the real list imported 2026-09-29 was 1,417 valid emails, and 8 people had confirmed signups as of 2026-10-06 (PARENT docs/ai/CURRENT_STATE.md).
**Source:** M0610 00:56:34 to 00:57:05
**Related:** ASM-BE-008

## ASM-BE-010

Each phase can generate revenue on its own.
**Source:** PP 00:14:29
**Related:** DEC-BE-010

## ASM-BE-011

Experience-based trips carry a higher price point because people want experiences they cannot get day to day. The speaker's own observation, not measured.
**Source:** PA 00:05:02
**Related:** BE-FB-008, Q-BE-016

## ASM-BE-012

Keeping AI in mind while building will not add much build time.
**Source:** PP 00:25:01
**Related:** DEC-BE-013

## ASM-BE-013

Traverse can match fares found publicly (for example on Google Flights), so where a deal is sourced does not matter much. Jeff: "we don't care. Because we can match it." Not explained further.
**Source:** M0610 00:15:08
**Related:** REQ-BE-003, RISK-BE-006
