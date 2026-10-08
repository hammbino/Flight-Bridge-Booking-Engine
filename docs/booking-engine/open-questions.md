---
title: "Booking Engine: Open Questions"
project: Flight Bridge Booking Engine
status: Active
owner: Mauricio Melendez / Jeffrey Hammond
last_updated: 2026-10-07
source_transcripts: [SV, EM, FS, PA, PP, M0610, M0924]
tags: [open-questions, booking-engine]
---

# Booking Engine Open Questions

## Quick index (by what it blocks)

| ID | Question (short) | Owner | Priority | Blocks |
|----|------------------|-------|----------|--------|
| Q-BE-010 | Where do Phase 1 leads go, and who watches them? | Mauricio | High | Shipping Phase 1 |
| Q-BE-018 | What is the official phase numbering and order? | Jeff + Mauricio | High | Roadmap |
| Q-BE-007 | What is the deal-link token schema? | Jeff | High | Deal landing page |
| Q-BE-003 | SQL or NoSQL? | Jeff | High | All development |
| Q-BE-004 | Which Sabre API / integration method? | Jeff | High | All Sabre work |
| Q-BE-009 | When does Phase 2 (real booking) ship? | Jeff + Mauricio | High | Planning |
| Q-BE-002 | Whose ARC, and current segment-share split? | Mauricio | High | Revenue model |
| Q-BE-001 | Was the Sabre subscriber contract reached? | Mauricio | High | Revenue model |
| Q-BE-008 | Does the booking engine or the CRM own PNR import? | Jeff | Medium | Architecture |
| Q-BE-013 | How do VIP packages get booked? | Mauricio | Medium | VIP tier (Dec 2026) |
| Q-BE-017 | Which deal types must the landing page support? | Mauricio | Medium | Landing page design |
| Q-BE-005 | Consumer booking fee amount? | Mauricio | Medium | REQ-BE-004 |
| Q-BE-006 | How do group coordinators book and pay? | Mauricio | Medium | Group booking |
| Q-BE-011 | Agency access fee amount? | Jeff + Mauricio | Medium | B2B |
| Q-BE-012 | Is hotel booking in scope? | Mauricio | Low | Scope |
| Q-BE-014 | Which JourneyFuse / Concur gaps should the tool fill? | Mauricio | Low | B2B scope |
| Q-BE-015 | How much AI goes in the product? | Jeff + Mauricio | Low | Architecture |
| Q-BE-016 | Is there demand for premium experience packages? | Mauricio | Low | BE-FB-008 |

---

## Q-BE-001

| Field | Value |
|-------|-------|
| Question | Did Traverse reach 1,000 segments in a month (the December push) and move to a Sabre subscriber contract? At what rate? |
| Why it matters | The subscriber contract was expected to raise the per-segment payment well above about 30 cents (SV 00:33:55). That changes the booking revenue model. |
| Owner | Mauricio Melendez |
| Priority | High |
| Blocking | Revenue projections; DEC-BE-003 |
| Source Transcript(s) | SV 00:41:44, SV 00:43:05 |

## Q-BE-002

| Field | Value |
|-------|-------|
| Question | Whose ARC do bookings run under today, and what is the current segment-share split? Is the Winifred arrangement over? |
| Why it matters | ARC was under Winifred's name, with money passed through her ($1 per transaction to her, $0.50 on to Flight Bridge), and she was to exit "in October" (FS 00:00:00, 00:00:29). On 09-24 Mauricio said Traverse "just barely got the ARC back about a year ago" with her help (M0924 00:41:37). Some Traverse bookings still run through Brian Dickerson's ARC (M0924 00:23:59). Mauricio receives 50 percent of segment shares (SV 00:27:28). DEC-BE-011 puts all booking-tool bookings under Traverse's ARC. |
| Owner | Mauricio Melendez |
| Priority | High |
| Blocking | Revenue model; DEC-BE-003, DEC-BE-011 |
| Source Transcript(s) | SV 00:27:28, FS 00:00:00, FS 00:00:29, M0924 00:23:59, M0924 00:41:37 |
| Update 2026-10-07 | Added the 09-24 ARC statements. Still unanswered: is the pass-through finished, and what is the split now? |

## Q-BE-003

| Field | Value |
|-------|-------|
| Question | SQL or NoSQL for the booking engine (and the shared platform)? |
| Why it matters | Jeff knows SQL better but thinks NoSQL might suit the build. He said "I have no idea" (SV 00:20:29). It shapes the data model for trips, PNRs, deals and bookings. The CRM shares this decision. |
| Owner | Jeffrey Hammond |
| Priority | High |
| Blocking | Technical architecture; all development |
| Source Transcript(s) | SV 00:20:29 |

## Q-BE-004

| Field | Value |
|-------|-------|
| Question | Which Sabre API or integration method will the booking engine use? |
| Why it matters | It sets what is technically possible, the effort, and the timeline. Options named so far: Sabre APIs (unspecified), Sabre's AI MCP (M0924 00:50:15), and a TAAP-style push of bookings into an agency's Sabre by PCC/PNR (M0924 00:48:42). |
| Owner | Jeffrey Hammond |
| Priority | High |
| Blocking | REQ-BE-001; PNR import; all Sabre work |
| Source Transcript(s) | SV 00:26:00, M0924 00:48:42, M0924 00:50:15 |

## Q-BE-005

| Field | Value |
|-------|-------|
| Question | What fee, if any, do consumer self-bookers (price shoppers) pay? |
| Why it matters | Jeff suggested charging price shoppers extra because they do the work (SV 00:26:56). No amount was set. The corporate fee suggestion is $5 to $10. |
| Owner | Mauricio Melendez |
| Priority | Medium |
| Blocking | REQ-BE-004 |
| Source Transcript(s) | SV 00:26:56 |

## Q-BE-006

| Field | Value |
|-------|-------|
| Question | How does a group coordinator (for example Missy) book and pay for group travel through Flight Bridge? |
| Why it matters | Groups are Traverse's major revenue source (SV 00:18:33). As a stopgap, Missy is moving to Brian Dickerson's SAP Concur to book hotels: $500 one time, commission split 70/30 with Dickerson, maybe 10% back to Missy (M0924 00:29:07 to 00:30:57). |
| Owner | Mauricio Melendez |
| Priority | Medium |
| Blocking | Group booking design; Q-BE-012 |
| Source Transcript(s) | SV 00:17:03, SV 00:18:33, M0924 00:29:07 |
| Update 2026-10-07 | Added the Missy / SAP Concur stopgap from 09-24. |

## Q-BE-007

| Field | Value |
|-------|-------|
| Question | What goes in the deal-link token, and how is it versioned? |
| Why it matters | Deal links must open the page preloaded (REQ-BE-003). Jeff: "how do we set up tokens in the email... we have explore" (EM 00:00:00). Links must keep working if the page changes (PARENT RISK-NL-005). The newsletter now runs on Kit, so tokens must work in Kit emails. The parent backlog says tokens encode route, dates and price (PARENT NL-FB-005). |
| Owner | Jeffrey Hammond |
| Priority | High |
| Blocking | BE-FB-001; Phase 1 form prefill |
| Source Transcript(s) | EM 00:00:00; PARENT NL-FB-005, RISK-NL-005 |

## Q-BE-008

| Field | Value |
|-------|-------|
| Question | Is Sabre PNR / last-name import a booking engine feature or a CRM feature? |
| Why it matters | It is tracked in both repos (BE-FB-002 here, CRM-FB-004 in the parent). R1205 puts the CRM's Sabre import after the booking tool (R1205 00:00:00). The old booking roadmap put it in booking Phase 1. It should be built once. |
| Owner | Jeffrey Hammond |
| Priority | Medium |
| Blocking | Architecture; roadmap ordering |
| Source Transcript(s) | SV 00:09:26, R1205 00:00:00 |

## Q-BE-009

| Field | Value |
|-------|-------|
| Question | When does Phase 2 (customers booking on our landing page) ship? |
| Why it matters | Jeff said only that a booking page should "quickly" follow the newsletter (M0924 00:19:27). The Basic flights tier goes live the first week of November 2026 (PARENT DEC-NL-017). Agents need 1 to 2 weeks on the engine first (DEC-BE-008). On 06-10 Mauricio said he did not know how feasible an early booking engine was (M0610 00:53:22). |
| Owner | Jeffrey Hammond / Mauricio Melendez |
| Priority | High |
| Blocking | Planning |
| Source Transcript(s) | M0924 00:19:27, M0610 00:53:22 |

## Q-BE-010

| Field | Value |
|-------|-------|
| Question | Where does a Phase 1 Book Now submission go (Denise's generic inbox, Mauricio via Victor, or info@), and who watches it day to day? |
| Why it matters | Sources disagree (CONF-BE-007). A dropped lead is lost revenue (PARENT RISK-NL-008). |
| Owner | Mauricio Melendez |
| Priority | High |
| Blocking | Shipping BE-FB-010 |
| Source Transcript(s) | M0610 00:50:14, M0924 00:21:33, M0924 00:22:33; PARENT Q-NL-010, CONF-NL-005 |

## Q-BE-011

| Field | Value |
|-------|-------|
| Question | What do agencies pay for access to the booking tool? |
| Why it matters | Agreed only that it should at least cover hosting and AI overhead (M0924 00:51:32). For reference, the other agent CRM ("T") costs $100/month for 5 users plus $10 per extra user (SV 00:31:53). |
| Owner | Jeffrey Hammond / Mauricio Melendez |
| Priority | Medium |
| Blocking | DEC-BE-004, BE-FB-006 |
| Source Transcript(s) | M0924 00:51:32, SV 00:31:53 |

## Q-BE-012

| Field | Value |
|-------|-------|
| Question | Should the booking engine eventually book hotels (and cars), not just flights? |
| Why it matters | Group clients like Missy book large hotel blocks, and the SAP Concur stopgap covers hotels, air and car (M0924 00:26:57, 00:29:07). Current scope is flights only. See IMP-BE-006. |
| Owner | Mauricio Melendez |
| Priority | Low |
| Blocking | Scope |
| Source Transcript(s) | M0924 00:26:57, M0924 00:29:07 |

## Q-BE-013

| Field | Value |
|-------|-------|
| Question | How will VIP package deals be booked when the VIP tier launches (planned early December 2026)? |
| Why it matters | On 06-10, JourneyFuse was the plan for VIP packages (M0610 00:52:30). On 09-24, Mauricio said "everything is migrating to JourneyFuse" (M0924 00:42:55), but no booking path for packages was discussed (M0924 00:59:40). Packages are "huge ticket items" (M0924 00:56:27). |
| Owner | Mauricio Melendez |
| Priority | Medium |
| Blocking | VIP tier revenue; BE-FB-008 |
| Source Transcript(s) | M0610 00:52:30, M0924 00:42:55, M0924 00:59:40 |

## Q-BE-014

| Field | Value |
|-------|-------|
| Question | Which gaps in JourneyFuse and SAP Concur should Flight Bridge's tool fill, and how close to Concur should it be? |
| Why it matters | Jeff asked for Mauricio's list of what JourneyFuse is not doing (M0924 00:43:00) and whether the tool will come close to Concur (M0924 00:42:09). Gaps named: no booking engine tied in, no business expense tracking, no QuickBooks connection (M0924 00:43:23). Earlier Jeff asked for a likes/dislikes/needs breakdown of every tool in use (PP 00:06:05). |
| Owner | Mauricio Melendez |
| Priority | Low |
| Blocking | B2B product scope (BE-FB-016) |
| Source Transcript(s) | PP 00:06:05, M0924 00:42:09, M0924 00:43:00, M0924 00:43:23 |

## Q-BE-015

| Field | Value |
|-------|-------|
| Question | How much AI should the product include? |
| Why it matters | Mauricio did not know and said the industry has not figured it out (PP 00:12:36). DEC-BE-013 sets the approach but not the scope. |
| Owner | Jeffrey Hammond / Mauricio Melendez |
| Priority | Low |
| Blocking | DEC-BE-013 scope |
| Source Transcript(s) | PP 00:12:36 |

## Q-BE-016

| Field | Value |
|-------|-------|
| Question | Is there real demand for premium experience packages? |
| Why it matters | The 03-16 monologue explicitly asks "Am I blowing smoke?" and gets no answer (PA 00:10:42). Antarctica cruises did sell (PA 00:08:47). |
| Owner | Mauricio Melendez |
| Priority | Low |
| Blocking | BE-FB-008 |
| Source Transcript(s) | PA 00:08:47, PA 00:10:42 |

## Q-BE-017

| Field | Value |
|-------|-------|
| Question | Which deal types must the landing page support? |
| Why it matters | "Airfare specials", "package specials" and possibly more were named, and Mauricio said he gets "lost in the weeds" (EM 00:07:14). Newsletter Basic deals are flights: about 5 domestic and 5 international from the home airport, SLC first (M0924 00:07:08). VIP deals are packages (M0924 00:56:27). |
| Owner | Mauricio Melendez |
| Priority | Medium |
| Blocking | Landing page design; token schema (Q-BE-007) |
| Source Transcript(s) | EM 00:07:14, M0924 00:07:08, M0924 00:56:27 |

## Q-BE-018

| Field | Value |
|-------|-------|
| Question | What are the official phase numbers and order for the booking engine? |
| Why it matters | Sources disagree (CONF-BE-004). The roadmap is using the 09-24 sequence for now. |
| Owner | Jeffrey Hammond / Mauricio Melendez |
| Priority | High |
| Blocking | Roadmap; project-state |
| Source Transcript(s) | See CONF-BE-004 |
