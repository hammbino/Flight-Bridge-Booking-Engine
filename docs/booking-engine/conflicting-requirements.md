---
title: "Booking Engine: Conflicting Requirements"
project: Flight Bridge Booking Engine
status: Needs Review
owner: Mauricio Melendez / Jeffrey Hammond
last_updated: 2026-10-07
source_transcripts: [SV, FS, PP, R1205, M0610, M0924, PARENT]
tags: [conflicts, booking-engine]
---

# Booking Engine Conflicting Requirements

Sources that disagree are recorded here. No winner is picked. A human resolves each one, then the answer moves into the right document.

## Quick index

| ID | Topic | Status |
|----|-------|--------|
| CONF-BE-001 | Sabre wrapper: start vs long-term | Partially resolved |
| CONF-BE-002 | Corporate fee vs Brian's pricing | Superseded (was based on a misreading) |
| CONF-BE-003 | Company formation date and entity type | Unresolved |
| CONF-BE-004 | Phase numbering and build order | Unresolved. Blocks roadmap |
| CONF-BE-005 | "Merchant billing" in Phase 2 vs no payment processing | Unresolved |
| CONF-BE-006 | How booking revenue is framed | Unresolved |
| CONF-BE-007 | Where Phase 1 leads go | Unresolved. Blocks Phase 1 |
| CONF-BE-008 | Do Traverse agents use the booking engine? | Unresolved |
| CONF-BE-009 | Competitor pricing figures (Brian / Dickerson) | Unresolved, low impact |
| CONF-BE-010 | Flight Bridge brand colors | Unresolved, low impact |

---

## CONF-BE-001

**Topic:** Sabre UI wrapper as the starting point or as the long-term goal
**Conflict:** Both partners want a full wrapper eventually, so that all Sabre work happens in the Flight Bridge UI. Jeff called it hard and proposed starting with PNR/last-name import.
**Source A:** "Eventually... because then it's one location for everything" (Mauricio, SV 00:09:26 to 00:10:09)
**Source B:** "makes a lot harder to look at flights" (Jeff, SV 00:10:17)
**Source C:** "The easiest way is to have this CRM and then just be able to import from a last name and PNR" (Jeff, SV 00:09:26)
**Status:** Partially resolved. Start with import; the wrapper comes later (DEC-BE-001). The path and timeline to the wrapper are open (SV 00:12:18).
**Source Transcript(s):** SV

## CONF-BE-002

**Topic:** Corporate fee vs competitor Brian's ~$30 per booking
**Original entry (2026-06-30):** said the $5 to $10 fee was "explicitly positioned to undercut competitor Brian".
**Correction (2026-10-07):** the transcript says the opposite: "this isn't to undercut Brian because his clients are very different than our clients" (SV 00:28:50). There is no conflict in the source. DEC-BE-002 is corrected to match.
**Status:** Superseded. Kept for history.
**Source Transcript(s):** SV 00:28:50

## CONF-BE-003

**Topic:** Company formation date and entity type (Flightbridge Travel LLC)
**Conflict:** The Utah business registry shows Flightbridge Travel LLC filed 11/13/2025 as a domestic LLC (entity 14630153-0160, active). The 12-05 transcript lists "partnership agreement" and then "EIN and state registration for the company" as future steps, and the year of that meeting is not stated (R1205 00:01:42). The partnership agreement drafts in Drive (Traverse_Partnership_Agreement_FINAL_v2, v3, v5_formatted) were created 2026-01-06, are marked DRAFT, are unsigned, and use the placeholder "[New LLC Name]". Parent docs also call Flight Bridge a "Utah corporation" while the registry shows an LLC.
**Source A:** Utah Division of Corporations entity search (checked 2026-09-30): filed 11/13/2025, Domestic LLC
**Source B:** Drive drafts dated 2026-01-06 and R1205 00:01:42: partnership and registration described as not yet done
**Status:** Unresolved. Jeff chose January 2026 as the partnership start date for LinkedIn (2026-09-30). Needs: the year of the 12-05 meeting, a signed operating agreement if one exists, and whether docs should say "LLC". Company-wide issue; the same entry is CONF-NL-006 in the parent repo.
**Source Transcript(s):** R1205 00:01:42, FS; PARENT Traverse_Partnership_Agreement_FINAL_v3.docx (Drive)

## CONF-BE-004

**Topic:** Phase numbering and build order across sources
**Conflict:** Every source orders the work a little differently and numbers phases differently.

| Source | Order stated |
|--------|--------------|
| SV 00:16:49, 00:26:00 | CRM + client portal + agent back end with PNR import first. Online booking tool named the "lowest hanging fruit" for revenue |
| EM 00:03:49 | Email list first, then the booking function |
| PP 00:08:58 | Phase 0 email campaign (Active Campaign, no booking agent) → Phase 1 Flight Bridge booking site under Traverse's ARC → Phase 2 VAX/Travify replacement with merchant billing → maintenance + white-label → maybe Phase 4 AI |
| R1205 00:00:00 | Online booking tool → CRM that pulls Sabre records (replacing Trace) → group and personal portals |
| M0610 00:52:22 to 00:54:01 | V1 form to agent → Phase 2 JourneyFuse (VIP packages) → Phase 3 Flight Bridge booking engine → Phase 4 CRM. Jeff wanted Flight Bridge as Phase 2 "if we can" but settled on JourneyFuse first |
| M0924 00:19:59 to 00:25:51, 00:45:11 | Phase 1 Book Now = lead form. Phase 2 = real booking on our page. Order: newsletter → booking tool → Concur-style B2B |
| Parent booking roadmap (2026-06-30) | Phase 1 = deal landing page + PNR import; Phase 2 = consumer self-serve; Phase 3 = corporate portal; Phase 4 = host agency; Phase 5 = wrapper |
| PARENT docs/ai/KNOWN_ISSUES.md | "Flight Bridge booking engine: Phase 3. No ETA." |

**Where they agree:** the email list comes before the booking engine. The booking engine comes before the full CRM in every source except SV. A real Flight Bridge booking page comes after a human-handled interim step.
**Where they differ:** (1) whether JourneyFuse sits between the interim form and the booking engine; (2) whether PNR import comes before or after self-serve booking (old roadmap vs R1205); (3) what "Phase 1" means.
**Status:** Unresolved. `roadmap.md` uses M0924 as its working sequence because it is the most recent, and labels it as such. Jeff should confirm (Q-BE-018).
**Source Transcript(s):** SV, EM, PP, R1205, M0610, M0924, PARENT

## CONF-BE-005

**Topic:** "Merchant billing" in Phase 2 vs not processing payments
**Conflict:** DEC-BE-005 says Flight Bridge will not process payments for now (SV 00:15:11). The Phase Plan says Phase 2 "is, a software that takes the place of Vax and Travify merchant includes merchant billing" (PP 00:08:58). Separately, Flight Bridge plans to move from Stripe to its own merchant account (FS 00:03:56).
**Source A:** SV 00:15:11 to 00:16:40
**Source B:** PP 00:08:58; FS 00:03:56
**Status:** Unresolved. It is not clear whether "merchant billing" covers flight bookings or only package bookings and agency billing.
**Source Transcript(s):** SV, PP, FS

## CONF-BE-006

**Topic:** How booking revenue is framed
**Conflict:** SV frames booking revenue as Sabre segment shares (about 30 cents per segment now, possibly "two seventy" to "seven" later, units unstated) plus fees (SV 00:27:10, 00:33:55). M0924 frames it as about $150 per booking, split between Traverse and Flight Bridge "the way we have it" (M0924 00:16:18, 00:17:18), with Flight Bridge getting the commission "as the agent" (M0924 00:26:25). M0924 does not mention segment shares as Flight Bridge income.
**Status:** Unresolved. It is unclear whether $150 is ticket value or revenue, and what the Traverse / Flight Bridge split is.
**Source Transcript(s):** SV, M0924

## CONF-BE-007

**Topic:** Where Phase 1 Book Now leads go
**Conflict:**
- **Source A (M0610 00:50:14 to 00:51:14):** the form goes to a generic inbox. Denise reviews it and assigns an agent. Same as PARENT DEC-NL-011.
- **Source B (M0924 00:21:33):** the lead gets in contact with Mauricio "through Victor" (an AI tool Mauricio uses).
- **Source C (M0924 00:22:33):** an email goes to info@ (Traverse domain) for "an agent" to follow up.
- **Related (PARENT CONF-NL-005, 2026-09-30):** the newsletter's Deal Alerts product uses a reply-to-email flow handled by Mauricio's AI tool "Viktor". Jeff confirmed that flow is intentional.
**Status:** Unresolved for the Book Now form. Blocks shipping Phase 1 (Q-BE-010). "Victor" and "Viktor" are probably the same tool, unconfirmed.
**Source Transcript(s):** M0610, M0924, PARENT

## CONF-BE-008

**Topic:** Do Traverse's own agents use the booking engine?
**Conflict:**
- **Source A (R1205 00:02:52):** agents will not use the portal to book, because it has a fee. Speaker labels in R1205 are unreliable.
- **Source B (M0610 00:54:01):** "Flight Bridge is just built on top of Sabre". Agents would book through Flight Bridge instead of Sabre directly, and must use it internally for 1 to 2 weeks before the newsletter launch (DEC-BE-008).
**Possible reading (not confirmed):** these may describe two different things: a fee-bearing client portal vs an internal agent booking screen.
**Status:** Unresolved.
**Source Transcript(s):** R1205, M0610

## CONF-BE-009

**Topic:** Competitor pricing figures
**Conflict:** SV says competitor Brian charges about $30 per booking (SV 00:28:50). M0924 says Brian Dickerson's SAP Concur setup costs Traverse $500 to onboard and clients $1,500 to $2,000 to set up, with a per-ticket figure transcribed as "$320", which looks garbled (M0924 00:26:57, 00:43:55). It is not certain that "Brian" in SV and "Brandon/Brian Dickerson" in M0924 are the same person.
**Status:** Unresolved, low impact. Affects fee positioning only.
**Source Transcript(s):** SV, M0924

## CONF-BE-010

**Topic:** Flight Bridge brand colors
**Conflict:** In M0610, Jeff described Flight Bridge colors as "navy, royal blue and green-blue" with whites, blacks and grays (M0610 01:08:21). The later Flight Bridge brand guide uses Jet Black `#0B0B0D`, Forest Green `#10A85B`, Dark Slate `#1A1F24`, Stone `#E5E7EB`, Sand `#CFC7B5`, with Montserrat / Inter fonts (PARENT docs/ai/KNOWN_ISSUES.md, landing page pass 3).
**Status:** Unresolved, low impact. The brand guide is newer. Customer pages are Traverse-branded anyway, with Flight Bridge only in the "powered by" mark (see `ui-notes.md`).
**Source Transcript(s):** M0610, PARENT
