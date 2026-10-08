---
title: "Booking Engine: Implicit Requirements"
project: Flight Bridge Booking Engine
status: Needs Review
owner: Mauricio Melendez / Jeffrey Hammond
last_updated: 2026-10-07
source_transcripts: [SV, EM, FS, AV, PA, M0610, M0924]
tags: [implicit-requirements, booking-engine, needs-human-review]
---

# Booking Engine Implicit Requirements

These seem implied by the conversations but were never stated as requirements. **Do not build from this file.** A human must promote each one to `requirements.md` or discard it.

## IMP-BE-001

**Implied requirement:** the booking engine issues tickets through Sabre, not just shows prices and sends people to the airline.
**What was said:** Mauricio's Continental shell example: "hit price... which credit card... hit ticket. Boom. It would ticket." (SV 00:10:23 to 00:11:47). Book Now must keep people on our site (M0924 00:20:38).
**Why implied:** segment shares come only from tickets issued under Traverse's credential.
**Source:** SV, M0924

## IMP-BE-002

**Implied requirement:** support VAX and other booking sources, not only Sabre.
**What was said:** "Import the trips from Sabre or VAX or yeah, whatever." (SV 00:16:49)
**Why implied:** Traverse books through several tools, and trips originate in Expedia TAAP, VAX, Sabre and others (SV 00:05:55).
**Source:** SV

## IMP-BE-003

**Implied requirement:** show real-time availability and pricing.
**What was said:** the Continental shell showed a Sabre-like availability window (SV 00:10:23). Phase 2 shows price changes as dates change (M0924 00:21:12).
**Why implied:** core to any booking engine. Partly covered by REQ-BE-009.
**Source:** SV, M0924

## IMP-BE-004

**Implied requirement:** the booking landing page is public. No login needed to view it.
**What was said:** "now you have all your price shoppers that can come and use us" (SV 00:26:56).
**Status note 2026-10-07:** now largely covered by REQ-BE-007 (09-24 form asks only name, email, flight). Candidate to close.
**Source:** SV, EM

## IMP-BE-005

**Implied requirement:** corporate bookings attach to the corporate client's account, so fees and reporting work.
**What was said:** Grit's individual travel is being missed and the portal would capture it (SV 00:28:50 to 00:30:19).
**Source:** SV

## IMP-BE-006

**Implied requirement:** the booking engine may eventually need hotel (and car) booking.
**What was said:** Missy books large hotel blocks. The SAP Concur stopgap covers hotels, air and car (M0924 00:26:57, 00:29:07).
**Source:** M0924
**Related:** Q-BE-012

## IMP-BE-007

**Implied requirement:** the agency booking tool can push a booking into the agency's own Sabre by PCC and PNR, the way Expedia TAAP's "GDS" button does.
**What was said:** Mauricio described the TAAP flow (M0924 00:48:42 to 00:49:21).
**Source:** M0924
**Related:** Q-BE-004, BE-FB-014

## IMP-BE-008

**Implied requirement:** the site can list and sell curated experience packages, not just flights.
**What was said:** "advertise these packaged experiences and sell them on our website" (PA 00:08:47).
**Source:** PA
**Related:** BE-FB-008

## IMP-BE-009

**Implied requirement:** every booking or lead form actually stores or routes what it captures, and this is verified.
**What was said:** Jeff's warning example: someone built a landing page whose form sent submissions nowhere (EM 00:13:39).
**Source:** EM
**Related:** REQ-BE-008, RISK-BE-010

## IMP-BE-010

**Implied requirement:** each deal has a shareable Book Now URL that works from social posts as well as email.
**What was said:** social posts carry "Book now" and "Join email list" links (EM 00:16:23).
**Source:** EM
**Related:** REQ-BE-003, Q-BE-007

## IMP-BE-011

**Implied requirement:** the booking flow handles a payer who is not the traveler, for example grandparents paying for a honeymoon, or a gift.
**What was said:** in past honeymoon campaigns, parents and grandparents paid, and "we got hit up by so many grandmas" (AV 00:08:48).
**Source:** AV

## IMP-BE-012

**Implied requirement:** booking payments, if Flight Bridge ever takes them, are not locked to Stripe.
**What was said:** start on a Flight Bridge Stripe account for email, then move to a regular merchant account to cut fees (FS 00:03:56).
**Source:** FS
**Related:** DEC-BE-005, CONF-BE-005

## IMP-BE-013

**Implied requirement:** Flight Bridge eventually offers its own client-bookable link generated from AI output, replacing JourneyFuse's link feature.
**What was said:** "we would need this capability" when the CRM is built (M0610 00:46:28).
**Source:** M0610
**Related:** Q-BE-013
