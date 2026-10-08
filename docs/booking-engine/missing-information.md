---
title: "Booking Engine: Missing Information"
project: Flight Bridge Booking Engine
status: Active
owner: Mauricio Melendez / Jeffrey Hammond
last_updated: 2026-10-07
source_transcripts: [SV, FS, M0924]
tags: [missing-information, booking-engine]
---

# Booking Engine Missing Information

Facts nobody has supplied yet. Questions that need a decision are in `open-questions.md`.

## MI-BE-001

**Missing:** database choice (SQL vs NoSQL).
**Impact:** blocks schema design. Jeff was undecided (SV 00:20:29).
**Needed from:** Jeffrey Hammond
**Tracked as:** Q-BE-003

## MI-BE-002

**Missing:** Sabre API integration method and access details.
**Impact:** sets what can be built and how fast.
**Needed from:** Jeffrey Hammond (research) and Sabre
**Tracked as:** Q-BE-004

## MI-BE-003

**Missing:** the current Sabre segment-share rate, its units, and whether the subscriber contract was reached.
**Impact:** booking revenue projections.
**Needed from:** Mauricio Melendez
**Tracked as:** Q-BE-001

## MI-BE-004

**Missing:** consumer booking fee amount.
**Impact:** REQ-BE-004.
**Needed from:** Mauricio Melendez
**Tracked as:** Q-BE-005

## MI-BE-005

**Missing:** commercial terms for hosting other agencies (fee, contract, onboarding).
**Impact:** DEC-BE-004, REQ-BE-006, REQ-BE-013.
**Needed from:** Mauricio Melendez
**Tracked as:** Q-BE-011

## MI-BE-006

**Missing:** how a self-booking customer pays.
**Impact:** Phase 2 cannot complete a booking without it. DEC-BE-005 rules out processing payments for now, and the platform captures card details without charging (SV 00:13:09). Stripe was planned only for the email product (FS 00:03:56). Newsletter billing now runs through a Kit-managed Stripe Express account, so two Stripe accounts exist (PARENT DEC-NL-014). Payment for Phase 2 bookings was not discussed on 09-24.
**Needed from:** Mauricio Melendez and Jeffrey Hammond
**Related:** CONF-BE-005, IMP-BE-012, RISK-BE-012

## MI-BE-007

**Missing:** the Traverse / Flight Bridge split on booking revenue.
**Impact:** M0924 says bookings are split "the way we have it" (M0924 00:17:18) but gives no terms.
**Needed from:** Mauricio Melendez and Jeffrey Hammond
**Related:** CONF-BE-006

## MI-BE-008

**Missing:** Mauricio's wireframes for the booking tool.
**Impact:** Mauricio has wireframes, some marked MVP, and planned to send them to Jeff (SV 00:02:38, R1205 00:01:07). They are not in this repo.
**Needed from:** Mauricio Melendez
