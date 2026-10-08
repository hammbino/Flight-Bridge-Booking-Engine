---
title: "Booking Engine: Backlog"
project: Flight Bridge Booking Engine
status: Active
owner: Mauricio Melendez / Jeffrey Hammond
last_updated: 2026-10-07
source_transcripts: [SV, EM, PA, PP, R1205, M0610, M0924]
tags: [backlog, booking-engine]
---

# Booking Engine Backlog

IDs use the `BE-FB-` prefix (kept from the parent repo). Phase uses the 09-24 meaning. See `roadmap.md`.

## Quick index

| ID | Title | Priority | Status | Phase |
|----|-------|----------|--------|-------|
| BE-FB-010 | Phase 1 Book Now lead form | High | Planned | 1 |
| BE-FB-001 | Deal landing page with token prefill | High | Planned | 1 (form) / 2 (bookable) |
| BE-FB-002 | Sabre PNR / last-name import | High | Planned | Disputed (Q-BE-008) |
| BE-FB-003 | Consumer search and self-booking | High | Planned | 2 |
| BE-FB-012 | Agent follow-up routing for self-bookings | High | Planned | 2 |
| BE-FB-011 | Internal agent pilot (1 to 2 weeks) | High | Planned | 2 |
| BE-FB-005 | Segment and revenue tracking | High | Planned | 2 |
| BE-FB-018 | Inquiry-to-booking conversion tracking | Medium | Planned | After 1 |
| BE-FB-004 | Corporate self-booking with fee | High | Planned | Later |
| BE-FB-006 | Host agency access ("Picasso, but better") | Medium | Planned | B2B |
| BE-FB-009 | BK Marketing (Ben Knell) as a target client | Medium | Idea | Later |
| BE-FB-016 | Concur-style B2B product | Low | Idea | After booking tool |
| BE-FB-013 | Explore Sabre's AI MCP | Medium | Idea | Research |
| BE-FB-014 | Push bookings into an agency's Sabre (TAAP-style) | Low | Idea | B2B |
| BE-FB-015 | Hotel booking | Low | Idea | Later |
| BE-FB-017 | Self-hosted AI fallback and on-prem add-on | Low | Idea | Later |
| BE-FB-019 | Proactive delay alerts and rebooking | Low | Idea | Later |
| BE-FB-008 | Premium experience packages | Low | Idea | Later |
| BE-FB-007 | Full Sabre UI wrapper | Low | Idea | Long-term |

---

## BE-FB-001

| Field | Value |
|-------|-------|
| ID | BE-FB-001 |
| Title | Deal landing page with token prefill |
| Description | The page deal links point to. Reads URL tokens for the deal and shows it ready to act on and editable. In Phase 1 it hosts the lead form (BE-FB-010). In Phase 2 it becomes bookable, with repricing when dates change (REQ-BE-009). |
| Business Value | Closes the loop from newsletter deal to revenue. No dead links. |
| Priority | High |
| Dependencies | Token schema (Q-BE-007); PARENT NL-FB-005 |
| Status | Planned |
| Source Transcript(s) | EM 00:00:00, M0610 00:52:55, M0924 00:21:12 |

## BE-FB-002

| Field | Value |
|-------|-------|
| ID | BE-FB-002 |
| Title | Sabre PNR / last-name import |
| Description | The agent enters a PNR and last name, and the system pulls all segments and passenger data from Sabre into a trip record. Replaces the uploader-on-a-virtual-machine workflow (SV 00:07:29). Competitor UMAPped did this with just PNR and last name (SV 00:06:53). |
| Business Value | Ends double entry. Foundation for CRM trip management. |
| Priority | High |
| Dependencies | Q-BE-004 (Sabre method); Q-BE-008 (which product owns it) |
| Status | Planned |
| Source Transcript(s) | SV 00:06:53, SV 00:09:26 |
| Notes | Also tracked in the parent repo as CRM-FB-004. Build it once. |

## BE-FB-003

| Field | Value |
|-------|-------|
| ID | BE-FB-003 |
| Title | Consumer search and self-booking |
| Description | Origin, destination and dates → Sabre availability and price → pick flight → passenger details → ticket under Traverse's ARC → agent follow-up (BE-FB-012). Target UX: Mauricio's Continental shell (SV 00:10:23) and "like a Google Flights" (PP 00:08:58). |
| Business Value | The main transaction revenue stream. |
| Priority | High |
| Dependencies | Q-BE-003, Q-BE-004, MI-BE-006 (payment path) |
| Status | Planned |
| Source Transcript(s) | SV 00:10:23, PP 00:08:58, M0924 00:23:04 |

## BE-FB-004

| Field | Value |
|-------|-------|
| ID | BE-FB-004 |
| Title | Corporate self-booking with fee |
| Description | Corporate clients' employees book their own one-off travel. Per-booking fee ($5 to $10 suggested). Bookings attach to the corporate account. Traverse supports travelers when problems happen. **Idea from the source:** a dedicated hire watches corporate accounts and handles each booking within a one-hour window (SV 00:27:51). Not decided. |
| Business Value | Captures individual travel from existing corporate group clients (for example Grit). |
| Priority | High |
| Dependencies | BE-FB-003; corporate accounts in the CRM |
| Status | Planned |
| Source Transcript(s) | SV 00:27:51, SV 00:28:50, R1205 00:03:27 |
| Change log | 2026-10-07: the "1-hour agent review window" moved from requirement to idea, per the source. |

## BE-FB-005

| Field | Value |
|-------|-------|
| ID | BE-FB-005 |
| Title | Segment and revenue tracking |
| Description | Track every ticket under Traverse's credential. Report segments per month (against the 1,000/month threshold) and revenue by source (consumer, corporate, group, newsletter, partner agency). |
| Business Value | Needed for the Sabre renegotiation and for the partner revenue split. |
| Priority | High |
| Dependencies | BE-FB-003 |
| Status | Planned |
| Source Transcript(s) | SV 00:43:05, M0610 01:12:42 |

## BE-FB-006

| Field | Value |
|-------|-------|
| ID | BE-FB-006 |
| Title | Host agency access ("the Picasso, but better") |
| Description | Other agencies book flights through Flight Bridge's tool under Traverse's ARC. They pay a Centrav-style access fee that at least covers hosting and AI. Self-service booking, not phone calls. Onboarding instructions included (REQ-BE-013). No buy-outs. |
| Business Value | Scalable B2B revenue. Early demand: 20 agency responses in 3 days (M0924 00:50:27). |
| Priority | Medium |
| Dependencies | BE-FB-003; Q-BE-011 (fee) |
| Status | Planned |
| Source Transcript(s) | SV 00:32:47, PP 00:10:48, M0924 00:46:04 to 00:51:59 |
| Change log | 2026-10-07: Idea → Planned. 09-24 made this an agreed direction (DEC-BE-004). Added the access-fee model. |

## BE-FB-007

| Field | Value |
|-------|-------|
| ID | BE-FB-007 |
| Title | Full Sabre UI wrapper |
| Description | All Sabre operations happen in the Flight Bridge UI, so no Sabre terminal is needed. Modeled on Mauricio's Continental shell. Airfare would be an add-on in software sold to agencies, since many do not sell air (SV 00:11:55). |
| Business Value | Lowers training needs. Opens the platform to agencies that do not know Sabre. |
| Priority | Low |
| Dependencies | All earlier phases |
| Status | Idea |
| Source Transcript(s) | SV 00:09:26 to 00:12:18 |

## BE-FB-008

| Field | Value |
|-------|-------|
| ID | BE-FB-008 |
| Title | Premium experience packages |
| Description | Sell curated experience trips on the site. See `premium-adventure-experiences.md`. |
| Business Value | Higher price point and margin (ASM-BE-011). |
| Priority | Low |
| Dependencies | Q-BE-013, Q-BE-016; supplier partners |
| Status | Idea |
| Source Transcript(s) | PA, M0924 00:56:27 |

## BE-FB-009

| Field | Value |
|-------|-------|
| ID | BE-FB-009 |
| Title | BK Marketing (Ben Knell) as a target client |
| Description | Ben Knell's BK Marketing (door-to-door sales, started in pest control, office in Orem) runs Philippines trips, humanitarian trips and rewards trips. Mauricio wants to get in front of him after December. He has called (no answer), tried dropping in at the office, and has mutual connections (a former baseball teammate on Ben's team; BNI-style referrals). |
| Business Value | Possible anchor corporate client. |
| Priority | Medium |
| Dependencies | BE-FB-004 |
| Status | Idea |
| Source Transcript(s) | R1205 00:03:58 |
| Change log | 2026-10-07: removed "Do not cold-call. Use network referrals." The transcript does not say that. It also does not explicitly name him as a booking portal client. |

## BE-FB-010

| Field | Value |
|-------|-------|
| ID | BE-FB-010 |
| Title | Phase 1 Book Now lead form |
| Description | Build the REQ-BE-008 form on the deal landing page: prefilled deal, "my dates are different" calendar, traveler count, call or email preference, name and email. Route each submission to the agreed inbox (Q-BE-010) and verify it arrives (IMP-BE-009). Jeff said it could ship now (M0924 00:22:33). |
| Business Value | Lets newsletter subscribers act on a deal before the engine exists. |
| Priority | High |
| Dependencies | Q-BE-010 (destination); Q-BE-007 (prefill tokens) |
| Status | Planned |
| Source Transcript(s) | M0610 00:47:33 to 00:51:14, M0924 00:21:33, M0924 00:22:33 |
| Notes | Same flow as PARENT NL-FB-013. Check the parent repo for whether a version already exists before building. |

## BE-FB-011

| Field | Value |
|-------|-------|
| ID | BE-FB-011 |
| Title | Internal agent pilot |
| Description | Traverse agents use the booking engine for at least one to two weeks before it is wired into the newsletter (DEC-BE-008). |
| Business Value | Catches problems before customers see them. |
| Priority | High |
| Dependencies | BE-FB-003; CONF-BE-008 resolved |
| Status | Planned |
| Source Transcript(s) | M0610 00:54:01 |

## BE-FB-012

| Field | Value |
|-------|-------|
| ID | BE-FB-012 |
| Title | Agent follow-up routing for self-bookings |
| Description | Each Phase 2 self-booking notifies an agent, who emails the itinerary ("White Glove Service") (REQ-BE-010). |
| Business Value | The human touch that sets Traverse apart from deal sites. |
| Priority | High |
| Dependencies | BE-FB-003 |
| Status | Planned |
| Source Transcript(s) | M0924 00:23:19 |

## BE-FB-013

| Field | Value |
|-------|-------|
| ID | BE-FB-013 |
| Title | Explore Sabre's AI MCP |
| Description | Jeff has looked at Sabre's AI MCP as a way to build features. Mauricio has not. Evaluate it as part of Q-BE-004. |
| Business Value | Could speed up the Sabre integration. |
| Priority | Medium |
| Dependencies | None |
| Status | Idea |
| Source Transcript(s) | M0924 00:50:15 |

## BE-FB-014

| Field | Value |
|-------|-------|
| ID | BE-FB-014 |
| Title | Push bookings into an agency's Sabre (TAAP-style) |
| Description | After booking, push the reservation into the agency's own GDS using its PCC and an existing PNR, the way Expedia TAAP's "GDS" button does (IMP-BE-007). |
| Business Value | Fits agencies' existing workflow. |
| Priority | Low |
| Dependencies | BE-FB-006; Q-BE-004 |
| Status | Idea |
| Source Transcript(s) | M0924 00:48:42 |

## BE-FB-015

| Field | Value |
|-------|-------|
| ID | BE-FB-015 |
| Title | Hotel booking |
| Description | Book hotels (and possibly cars) alongside flights. Prompted by Missy's group hotel volume and the SAP Concur stopgap (IMP-BE-006). |
| Business Value | Keeps hotel commission in-house instead of splitting 70/30 with Dickerson (M0924 00:29:07). |
| Priority | Low |
| Dependencies | Q-BE-012 |
| Status | Idea |
| Source Transcript(s) | M0924 00:26:57, M0924 00:29:07 |

## BE-FB-016

| Field | Value |
|-------|-------|
| ID | BE-FB-016 |
| Title | Concur-style B2B product |
| Description | After the booking tool, "attack something like" SAP Concur: white-labeled booking for client companies. Expense tracking is not being built initially. A Bill.com partnership for expenses is "on the table" (M0924 00:44:39). Concur-style setup fees run about $1,500 to $2,000 per client (M0924 00:43:55). |
| Business Value | B2B revenue beyond consumer bookings. |
| Priority | Low |
| Dependencies | BE-FB-003; Q-BE-014 |
| Status | Idea |
| Source Transcript(s) | M0924 00:42:37 to 00:45:11 |

## BE-FB-017

| Field | Value |
|-------|-------|
| ID | BE-FB-017 |
| Title | Self-hosted AI fallback and on-prem add-on |
| Description | Build a self-hosted model server as the fallback in DEC-BE-013. Later, offer agencies a local machine with a model behind their firewall to address data privacy (PP 00:13:23). |
| Business Value | Protects against AI price changes. Sellable add-on. |
| Priority | Low |
| Dependencies | DEC-BE-013 |
| Status | Idea |
| Source Transcript(s) | PP 00:13:23, PP 00:22:08 |

## BE-FB-018

| Field | Value |
|-------|-------|
| ID | BE-FB-018 |
| Title | Inquiry-to-booking conversion tracking |
| Description | Show which subscribers asked about a deal and which booked (REQ-BE-012). |
| Business Value | Measures newsletter revenue and Flight Bridge's share. |
| Priority | Medium |
| Dependencies | BE-FB-010 |
| Status | Planned |
| Source Transcript(s) | M0610 00:48:22 |

## BE-FB-019

| Field | Value |
|-------|-------|
| ID | BE-FB-019 |
| Title | Proactive delay alerts and rebooking |
| Description | Track booked flights live. Alert the on-call agent before the client knows. Offer or make a rebooking ("we've already booked you on the next flight"). Weather overlay from weather.gov. Possibly run by an AI agent. |
| Business Value | Lets a small team look like a large one (SV 00:25:29). |
| Priority | Low |
| Dependencies | BE-FB-003 |
| Status | Idea |
| Source Transcript(s) | SV 00:22:15 to 00:25:29 |
| Notes | Mostly a CRM feature in the parent repo. Listed here because rebooking runs through the booking engine. |
