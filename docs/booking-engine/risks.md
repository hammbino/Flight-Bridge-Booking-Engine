---
title: "Booking Engine: Risks"
project: Flight Bridge Booking Engine
status: Active
owner: Mauricio Melendez / Jeffrey Hammond
last_updated: 2026-10-07
source_transcripts: [SV, FS, PP, M0610, M0924, PARENT]
tags: [risks, booking-engine]
---

# Booking Engine Risks

Likelihood and impact ratings are judgments made when the doc was written, not values stated in the sources.

## RISK-BE-001

**Risk:** the 1,000 segments/month threshold is missed, so the Sabre subscriber contract and its higher rate do not happen. Part of the build funding depends on segment payments (SV 00:45:01).
**Likelihood:** Low-Medium. **Impact:** High.
**Mitigation:** track monthly segment count (REQ-BE-005). Capture every booking under Traverse's credential.
**Related:** ASM-BE-002, ASM-BE-003, DEC-BE-003, Q-BE-001
**Source:** SV 00:43:05 to 00:45:01

## RISK-BE-002

**Risk:** Sabre integration is harder than expected and delays the booking engine. Jeff has not worked with Sabre before.
**Likelihood:** Medium. **Impact:** High.
**Mitigation:** research the integration early (Q-BE-004). Start with import-only (DEC-BE-001).
**Related:** ASM-BE-001, Q-BE-004
**Source:** SV

## RISK-BE-003

**Risk:** the Winifred ARC arrangement lasts longer than planned, so Flight Bridge keeps receiving only a pass-through share.
**Likelihood:** Low (M0924 says Traverse got the ARC back about a year ago). **Impact:** Medium.
**Mitigation:** confirm current status (Q-BE-002).
**Related:** DEC-BE-011, Q-BE-002
**Source:** FS 00:00:29, SV 00:27:28, M0924 00:41:37

## RISK-BE-004

**Risk:** corporate clients (for example Grit) keep booking through existing channels and do not adopt self-booking.
**Likelihood:** Medium. **Impact:** Medium.
**Mitigation:** pilot with a client Mauricio already has lined up (R1205 00:02:52).
**Related:** ASM-BE-005, REQ-BE-002
**Source:** SV, R1205

## RISK-BE-005

**Risk:** an early SQL vs NoSQL choice locks in the wrong data model.
**Likelihood:** Medium. **Impact:** Medium.
**Mitigation:** write down the decision and its reasoning in product-decisions.md when it is made.
**Related:** Q-BE-003
**Source:** SV 00:20:29

## RISK-BE-006

**Risk:** on the Phase 1 form, customers change dates without seeing a new price. The deal price may not hold, which can disappoint the customer when the agent calls.
**Likelihood:** Medium. **Impact:** Medium.
**Mitigation:** set expectations on the form. Phase 2 repricing (REQ-BE-009) removes the gap.
**Note:** derived from M0610 00:47:53 and the Flights From Home comparison (M0610 00:38:27). Not stated as a risk in the meeting.
**Related:** REQ-BE-008, ASM-BE-013

## RISK-BE-007

**Risk:** deal links already sent in emails break if the landing page URL or token format changes.
**Likelihood:** Low-Medium. **Impact:** High.
**Mitigation:** a stable, versioned token schema (Q-BE-007). Test links before every send.
**Related:** REQ-BE-003; PARENT RISK-NL-005
**Source:** EM; PARENT RISK-NL-005

## RISK-BE-008

**Risk:** AI providers raise prices or cap access, breaking AI features built on a hosted API.
**Likelihood:** Medium. **Impact:** Medium-High.
**Mitigation:** DEC-BE-013 (self-hosted fallback).
**Related:** ASM-BE-012, DEC-BE-013
**Source:** PP 00:18:27

## RISK-BE-009

**Risk:** a competitor ships first in a fast-moving market.
**Likelihood:** Medium. **Impact:** Medium.
**Mitigation:** follow the build order (DEC-BE-010). Ship each phase when it works.
**Source:** PP 00:15:02

## RISK-BE-010

**Risk:** the back end (data migration, connecting the pieces) is harder than the front end. Apps built fast with AI often handle context, caching and data badly, making them slow and costly.
**Likelihood:** Medium. **Impact:** High.
**Mitigation:** plan heavily before building (PP 00:25:31). Verify that every form stores or routes its data (IMP-BE-009).
**Related:** IMP-BE-009
**Source:** PP 00:26:01, PP 00:26:36, EM 00:13:39

## RISK-BE-011

**Risk:** build pace is limited by Jeff's available time.
**Likelihood:** High. **Impact:** Medium.
**Mitigation:** Jeff has outside developers who offered to help (PP 00:23:44).
**Source:** SV 00:41:09

## RISK-BE-012

**Risk:** Stripe may not process travel bookings because of chargebacks. Two Stripe accounts already exist (Flight Bridge's own and Kit's Express account), which confuses any plan to take booking payments.
**Likelihood:** Medium. **Impact:** Medium.
**Mitigation:** decide the payment path before Phase 2 (MI-BE-006).
**Related:** DEC-BE-005, CONF-BE-005, IMP-BE-012
**Source:** SV 00:15:42, FS 00:03:56; PARENT DEC-NL-014

## RISK-BE-013

**Risk:** agency demand outruns capacity. Mauricio's agency Facebook campaign was stopped because the team could not keep up.
**Likelihood:** Medium. **Impact:** Medium.
**Mitigation:** self-service booking for agencies (REQ-BE-006). Onboarding instructions (REQ-BE-013).
**Related:** DEC-BE-004
**Source:** M0924 00:50:27

## RISK-BE-014

**Risk:** a lead from the Phase 1 form is dropped because nobody clearly owns the inbox.
**Likelihood:** Medium. **Impact:** High (lost booking revenue).
**Mitigation:** answer Q-BE-010 before shipping.
**Related:** CONF-BE-007; PARENT RISK-NL-008
**Source:** M0610, M0924; PARENT RISK-NL-008
