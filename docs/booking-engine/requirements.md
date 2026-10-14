---
title: "Booking Engine: Requirements"
project: Flight Bridge Booking Engine
status: Active
owner: Mauricio Melendez / Jeffrey Hammond
last_updated: 2026-10-13
source_transcripts: [SV, EM, PP, R1205, M0610, M0924, M1008P]
tags: [requirements, booking-engine]
---

# Booking Engine Requirements

Only explicitly stated requirements belong here. Requirements that only seem implied are in `implicit-requirements.md` until a human promotes them. Source keys are defined in `docs/sources/README.md`.

## Quick index

| ID | Requirement (short) | Priority | Status | Phase |
|----|---------------------|----------|--------|-------|
| REQ-BE-001 | Self-serve flight booking on Traverse's direct Sabre access | High | Confirmed | 2 |
| REQ-BE-002 | Corporate self-booking with a per-booking fee | High | Confirmed | Later |
| REQ-BE-003 | Deal links open the booking page preloaded and editable | High | Confirmed | 2 (form version in 1) |
| REQ-BE-004 | Booking fees configurable by customer type | Medium | Confirmed | Later |
| REQ-BE-005 | Track every ticket for segment and revenue attribution by source | High | Confirmed | 2 |
| REQ-BE-006 | Host other agencies' bookings ("Picasso") | Medium | Confirmed | B2B |
| REQ-BE-007 | No account needed to view a deal or start a booking | Medium | Confirmed | 1 |
| REQ-BE-008 | Phase 1 Book Now lead form | High | Confirmed | 1 |
| REQ-BE-009 | Show the new price when the customer changes dates | High | Confirmed | 2 |
| REQ-BE-010 | Every self-booking routes to an agent for follow-up | High | Confirmed | 2 |
| REQ-BE-011 | Book Now keeps the customer on our site | High | Confirmed | 1 |
| REQ-BE-012 | Track which subscribers inquire and which book | Medium | Confirmed | After 1 |
| REQ-BE-013 | Onboarded agencies get booking tool access and instructions | Medium | Confirmed | B2B |
| REQ-BE-014 | Terms and conditions cover stored card data | Medium | Confirmed | 2 |
| REQ-BE-015 | Travelers can view trip and flight info offline | Medium | Confirmed | Later |

"Phase" uses the 09-24 meaning: Phase 1 = lead capture, Phase 2 = real booking on our page. Numbering is disputed. See CONF-BE-004.

---

## REQ-BE-001

| Field | Value |
|-------|-------|
| ID | REQ-BE-001 |
| Requirement | Self-serve flight booking on Traverse's direct Sabre access |
| Description | Customers search, pick and book flights through the online booking tool, which uses Traverse's direct Sabre connection. The tool must integrate with Sabre, because that is what lets it be a real booking tool (PP 00:05:38). Target experience: like Google Flights, but for Traverse and under its ARC (PP 00:08:58). This was not possible before Traverse got direct Sabre access (SV 00:26:00). Price shoppers who want to do it themselves are a target user (SV 00:26:56). |
| Priority | High |
| Status | Confirmed |
| Source Transcript(s) | SV 00:26:00, SV 00:26:56, PP 00:05:38, PP 00:08:58, R1205 00:00:00 |
| Related Requirements | REQ-BE-002, REQ-BE-003, REQ-BE-005, REQ-BE-010 |
| Related Decisions | DEC-BE-001, DEC-BE-009, DEC-BE-011 |

## REQ-BE-002

| Field | Value |
|-------|-------|
| ID | REQ-BE-002 |
| Requirement | Corporate self-booking with a per-booking fee |
| Description | Corporate clients' employees (for example Grit) can book one-off travel on their own through the online booking tool. Their bookings flow into the same system (SV 00:27:51). Each corporate self-booking carries a fee, possibly automated; $5 to $10 was suggested (SV 00:28:50). Traverse still supports these travelers on flights and tickets, for example missed flights, so the client company does not have to (R1205 00:03:27). |
| Priority | High |
| Status | Confirmed |
| Source Transcript(s) | SV 00:27:51, SV 00:28:50, R1205 00:03:27 |
| Related Requirements | REQ-BE-001, REQ-BE-004 |
| Related Decisions | DEC-BE-002, DEC-BE-012 |
| Change log | 2026-10-07: removed "1-hour review window" from the requirement. In the source it is an idea tied to a future hire (SV 00:27:51), now in BE-FB-004. Added Traverse's support role (R1205). |

## REQ-BE-003

| Field | Value |
|-------|-------|
| ID | REQ-BE-003 |
| Requirement | Deal links open the booking page preloaded with the deal and editable |
| Description | A deal in an email, social post or other marketing links back to Flight Bridge. The landing page opens with the deal already loaded, "ready to pay now", but still editable "just like a regular booking engine" (EM 00:00:00). The customer can change dates and book (M0610 00:52:55, M0924 00:21:12). Deal context travels in URL tokens. How the tokens work is not designed yet (EM 00:00:00, Q-BE-007). The newsletter platform is now Kit, so tokens must work with Kit emails (PARENT DEC-NL-007). |
| Priority | High |
| Status | Confirmed |
| Source Transcript(s) | EM 00:00:00, M0610 00:52:55, M0924 00:21:12 |
| Related Requirements | REQ-BE-007, REQ-BE-008, REQ-BE-009; PARENT REQ-NL-004 |
| Related Decisions | DEC-BE-007, DEC-BE-009; PARENT DEC-NL-002 |

## REQ-BE-004

| Field | Value |
|-------|-------|
| ID | REQ-BE-004 |
| Requirement | Booking fees configurable by customer type |
| Description | Fees differ by booking type. Corporate self-booking: about $5 to $10 suggested (SV 00:28:50). Price shoppers who book themselves: Jeff suggested an extra fee because they do the work (SV 00:26:56); amount not set (Q-BE-005). The system must support different fees per account type. |
| Priority | Medium |
| Status | Confirmed |
| Source Transcript(s) | SV 00:26:56, SV 00:28:50 |
| Related Requirements | REQ-BE-002 |
| Related Decisions | DEC-BE-002 |

## REQ-BE-005

| Field | Value |
|-------|-------|
| ID | REQ-BE-005 |
| Requirement | Track every ticket for segment and revenue attribution by source |
| Description | Every ticket issued through the booking tool must be tracked under Traverse's Sabre/ARC credential. Count segments per month, because 1,000 in a month is the track record needed for a Sabre subscriber contract (SV 00:43:05). Attribute revenue by source: consumer, corporate, group, newsletter, partner agency. Flight Bridge earns a percentage of anything booked from the newsletter, so newsletter attribution matters (M0610 01:12:42). |
| Priority | High |
| Status | Confirmed |
| Source Transcript(s) | SV 00:27:10, SV 00:43:05, M0610 01:12:42 |
| Related Requirements | REQ-BE-001, REQ-BE-012 |
| Related Decisions | DEC-BE-003, DEC-BE-011 |

## REQ-BE-006

| Field | Value |
|-------|-------|
| ID | REQ-BE-006 |
| Requirement | Host other agencies' bookings ("the Picasso, but better") |
| Description | Other travel agencies, most of which have no ARC, can book flights through Flight Bridge's booking tool under Traverse's ARC (M0924 00:46:04, PP 00:10:48). They pay an access fee (M0924 00:51:32). The tool must be easier and more integrated than existing hosts (Picasso, Skybird, Centrav), and agents must be able to book themselves instead of calling (M0924 00:47:15). |
| Priority | Medium |
| Status | Confirmed (B2B stage, after the booking tool) |
| Source Transcript(s) | SV 00:32:47, PP 00:10:48, M0924 00:46:04, M0924 00:47:15, M0924 00:51:32 |
| Related Requirements | REQ-BE-001, REQ-BE-005, REQ-BE-013 |
| Related Decisions | DEC-BE-004, DEC-BE-011 |

## REQ-BE-007

| Field | Value |
|-------|-------|
| ID | REQ-BE-007 |
| Requirement | No account needed to view a deal or start a booking |
| Description | Customers arriving from a deal link can view the deal and act on it without creating an account first. The Phase 1 form asks only for name, email and the flight (M0924 00:22:33). Account creation or guest checkout is an option, never a prerequisite. |
| Priority | Medium |
| Status | Confirmed |
| Source Transcript(s) | EM 00:00:00, M0924 00:22:33 |
| Related Requirements | REQ-BE-003, REQ-BE-008 |
| Related Decisions | DEC-BE-006 |
| Change log | 2026-10-07: source corrected. The parent cited JeffandMauricio.md.md (EM) only. EM supports direct access to the deal page, but "no account" is stated most clearly by the 09-24 form fields. |

## REQ-BE-008

| Field | Value |
|-------|-------|
| ID | REQ-BE-008 |
| Requirement | Phase 1 Book Now lead form |
| Description | Clicking Book Now on a deal opens a form on our landing page. The form: (1) is prefilled with the deal details (M0610 00:47:33); (2) has a "my dates are different" option that opens a calendar (M0610 00:47:37); (3) asks how many people are traveling (M0610 00:47:58); (4) contact is by email only (M1008P L910-920; the 06-10 version let the customer pick call or email, M0610 00:50:14); (5) captures name, email and the flight (M0924 00:22:33); (6) sends the submission to Traverse for an agent to follow up (M0610 00:50:14, M0924 00:22:33). It does not show a new price when dates change (M0610 00:47:53). |
| Priority | High |
| Status | Confirmed |
| Source Transcript(s) | M0610 00:47:33 to 00:51:14, M0924 00:21:33, M0924 00:22:33 |
| Related Requirements | REQ-BE-003, REQ-BE-007, REQ-BE-011 |
| Related Decisions | DEC-BE-006; PARENT DEC-NL-011 |
| Notes | Change 2026-10-08: email only, no call option (M1008P L910-920). Destination: info@traversetours.com (Jeff, working session 2026-10-12), resolving CONF-BE-007. The 10-08 meeting says "info at FlightTraverse" instead (CONF-BE-011). Mauricio and his AI tool Viktor monitor it (Jeff, working session 2026-10-13). |

## REQ-BE-009

| Field | Value |
|-------|-------|
| ID | REQ-BE-009 |
| Requirement | Show the new price when the customer changes dates or times |
| Description | On the Phase 2 landing page the customer can change dates and times and see how the price changes, like the Google Flights date spread (M0924 00:21:12, 00:21:15). The customer sees updated options before booking (M0610 00:53:05). |
| Priority | High |
| Status | Confirmed |
| Source Transcript(s) | M0924 00:21:12, M0924 00:21:15, M0610 00:53:05 |
| Related Requirements | REQ-BE-003 |
| Related Decisions | DEC-BE-009 |

## REQ-BE-010

| Field | Value |
|-------|-------|
| ID | REQ-BE-010 |
| Requirement | Every self-booking routes to an agent for follow-up |
| Description | When a customer books directly on our page, the booking still goes to an agent, who follows up by email with the itinerary (M0924 00:23:19). This human touch is Traverse's edge over deal sites with no person in the loop (M0610 00:48:13, M0924 00:23:59). |
| Priority | High |
| Status | Confirmed |
| Source Transcript(s) | M0924 00:23:19, M0924 00:23:59, M0610 00:48:13 |
| Related Requirements | REQ-BE-001 |
| Related Decisions | DEC-BE-009 |

## REQ-BE-011

| Field | Value |
|-------|-------|
| ID | REQ-BE-011 |
| Requirement | Book Now keeps the customer on our site |
| Description | Book Now must send the customer to Flight Bridge's own page, not to an airline's site or to Google Flights the way competitors do (M0924 00:20:38 to 00:20:43, M0610 00:38:57). The newsletter needs an actual "to book one of these, click here" link, not just instructions (M0610 00:37:45). |
| Priority | High |
| Status | Confirmed |
| Source Transcript(s) | M0924 00:20:38, M0610 00:37:45, M0610 00:38:57 |
| Related Requirements | REQ-BE-003, REQ-BE-008 |
| Related Decisions | DEC-BE-006 |

## REQ-BE-012

| Field | Value |
|-------|-------|
| ID | REQ-BE-012 |
| Requirement | Track which subscribers inquire and which book |
| Description | The back end should show which email subscribers ask for information and which ones actually book. Mauricio placed this after the V1 flow is working (M0610 00:48:22). |
| Priority | Medium |
| Status | Confirmed |
| Source Transcript(s) | M0610 00:48:22 |
| Related Requirements | REQ-BE-005, REQ-BE-008 |
| Related Decisions | DEC-BE-006 |

## REQ-BE-013

| Field | Value |
|-------|-------|
| ID | REQ-BE-013 |
| Requirement | Onboarded agencies get booking tool access and instructions |
| Description | When an agency signs on, it is pointed to the booking tool with instructions on how to work with Flight Bridge (M0924 00:51:20). |
| Priority | Medium |
| Status | Confirmed |
| Source Transcript(s) | M0924 00:51:20 |
| Related Requirements | REQ-BE-006 |
| Related Decisions | DEC-BE-004 |

## REQ-BE-014

| Field | Value |
|-------|-------|
| ID | REQ-BE-014 |
| Requirement | Terms and conditions cover stored card data |
| Description | If client card data is stored, Flight Bridge's terms and conditions must cover it, and the client accepts them when creating an account (PP 00:00:49). Mauricio believes card storage at the client-profile level can be PCI compliant, but that is his belief, not verified (PP 00:00:32). |
| Priority | Medium |
| Status | Confirmed |
| Source Transcript(s) | PP 00:00:32, PP 00:00:49 |
| Related Requirements | REQ-BE-007 |
| Related Decisions | DEC-BE-005 |

## REQ-BE-015

| Field | Value |
|-------|-------|
| ID | REQ-BE-015 |
| Requirement | Travelers can view trip and flight info offline |
| Description | Travelers must be able to cache their trip and flight info so they still have it in an airport with no internet, through browser cache or a native app. Agent-side offline mode is not needed (PP 00:18:27). Sabre itself does not work offline (PP 00:18:23). |
| Priority | Medium |
| Status | Confirmed |
| Source Transcript(s) | PP 00:18:23, PP 00:18:27 |
| Related Requirements | None |
| Related Decisions | None |
| Notes | This mostly belongs to the client portal, which the parent repo tracks under the CRM. It is recorded here so the booking engine's trip data model supports it. |
