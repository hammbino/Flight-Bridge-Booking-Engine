---
title: "Booking Engine: Product Decisions"
project: Flight Bridge Booking Engine
status: Needs Review
owner: Mauricio Melendez / Jeffrey Hammond
last_updated: 2026-10-07
source_transcripts: [SV, EM, FS, PP, R1205, M0610, M0924]
tags: [decisions, booking-engine]
---

# Booking Engine Product Decisions

Source keys (`SV`, `M0924`, and so on) are defined in `docs/sources/README.md`. Timestamps point to the digest row and the raw transcript.

**2026-10-07 review note:** while splitting this repo out, every decision was re-checked against its transcript. DEC-BE-002, DEC-BE-003 and DEC-BE-005 said more than the transcript supports. Each is corrected below, with a "Correction" line keeping the old wording. See `migration-notes.md`.

## Quick index

| ID | Decision (short) | Status |
|----|------------------|--------|
| DEC-BE-001 | Build on Sabre. Start with PNR import, wrapper is "eventually". Never build a GDS | Agreed |
| DEC-BE-002 | Corporate self-booking with a small per-booking fee | Needs Review |
| DEC-BE-003 | Booking revenue model (segment shares, fees, per-booking split) | Needs Review |
| DEC-BE-004 | Be a host agency ("the Picasso, but better") with paid access, no buy-outs | Agreed |
| DEC-BE-005 | Do not process payments for now. Capture card details only | Agreed |
| DEC-BE-006 | Phase 1 "Book Now" is lead capture, not a booking | Agreed |
| DEC-BE-007 | Flight-only deals move to the engine first. Packages stay with agents | Agreed |
| DEC-BE-008 | Agents use the engine internally 1 to 2 weeks before it goes to the newsletter | Agreed |
| DEC-BE-009 | Phase 2: customer books on our landing page, an agent still follows up | Agreed |
| DEC-BE-010 | Build order: newsletter, then booking tool, then a Concur-style B2B product | Agreed |
| DEC-BE-011 | Bookings run under Traverse's ARC, including bookings by licensee agencies | Agreed |
| DEC-BE-012 | Traverse's own agents do not book through the fee-bearing portal | Needs Review |
| DEC-BE-013 | AI: start on a hosted API, build a self-hosted fallback soon | Agreed |

---

## DEC-BE-001

| Field | Value |
|-------|-------|
| Decision ID | DEC-BE-001 |
| Decision | Keep Sabre as the GDS. Start with a system that imports bookings by PNR and last name. A full Sabre UI wrapper is the "eventually" goal, not the starting point. Flight Bridge will never build its own GDS. |
| Reasoning | Traverse now has direct Sabre access (SV 00:26:00). Jeff: "The easiest way is to have this CRM and then just be able to import from a last name and PNR" (SV 00:09:26). Mauricio wants the wrapper "eventually" but does not know how it would work (SV 00:09:26 to 00:10:09). Jeff flagged that a wrapper "makes a lot harder to look at flights" (SV 00:10:17). GDSs are regulated and Flight Bridge "cannot and would not" build one (M0924 00:49:41). |
| Alternatives Considered | Full Sabre UI wrapper from day one (Mauricio's Continental Airlines shell is the model, SV 00:10:23); building a GDS (rejected, M0924 00:49:41); VAX or other GDSs (not chosen) |
| Status | Agreed |
| Date | SV (date unknown); reaffirmed 2026-09-24 |
| Source Transcript(s) | SV 00:09:26, SV 00:11:48, M0924 00:49:41 |
| Related Requirements | REQ-BE-001 |
| Notes | Correction 2026-10-07: the old wording "do NOT build a Sabre wrapper for MVP" is an inference. The transcript only orders the work (PNR import first, wrapper eventually). Integration ideas still open: Sabre's AI MCP (M0924 00:50:15) and pushing bookings into an agency's Sabre by PCC/PNR, like Expedia TAAP (M0924 00:48:42). Both feed Q-BE-004. |

## DEC-BE-002

| Field | Value |
|-------|-------|
| Decision ID | DEC-BE-002 |
| Decision | Corporate clients (for example Grit employees) can self-book through the online booking tool. Each corporate self-booking carries a small fee, suggested at $5 to $10. Traverse still supports those travelers (missed flights, ticket problems) so the client company does not have to. |
| Reasoning | Traverse runs Grit's group trips but captures none of Grit's individual travel (SV 00:28:50 to 00:30:19). Mauricio, on the fee: "this isn't to undercut Brian because his clients are very different than our clients. This would be like for people who just want to book it on their own for a corporate company" (SV 00:28:50). Client employees book one-off trips but Traverse handles problems (R1205 00:03:27). |
| Alternatives Considered | No fee; a fee matching Brian's ~$30 (Brian's clients are a different market, SV 00:28:50) |
| Status | Needs Review |
| Date | SV (date unknown) |
| Source Transcript(s) | SV 00:27:51, SV 00:28:50, R1205 00:03:27 |
| Related Requirements | REQ-BE-002, REQ-BE-004 |
| Notes | Correction 2026-10-07. The old version said the fee was set "below competitor Brian's ~$30/booking to attract volume". The transcript says the opposite. The old version also treated a 1-hour agent review window as agreed. In the transcript it is Mauricio's idea for a future dedicated hire who watches corporate accounts (SV 00:27:51). It is now tracked as an idea in BE-FB-004. The $5 to $10 figure is a suggestion, not a set price. Needs Jeff and Mauricio to confirm the fee. |

## DEC-BE-003

| Field | Value |
|-------|-------|
| Decision ID | DEC-BE-003 |
| Decision | The online booking tool earns money through Sabre segment shares on every ticket, plus booking fees where they apply. How booking revenue is split between Traverse and Flight Bridge is not settled in the docs. |
| Reasoning | Mauricio: the online booking tool earns through segment shares (SV 00:27:10). Revenue streams named: corporate booking fee, segment shares, and software licensing (SV 00:30:19). Rate today is about 30 cents per segment on Sabre's simple contract. "Come January" it was expected to rise to "two seventy" and be negotiated "up to seven" (SV 00:33:55), but the units are never stated. Hitting 1,000 segments in a month is the track record needed for a subscriber contract (SV 00:43:05). On 09-24 booking revenue was framed per booking instead: about $150 per booking, split with Traverse "the way we have it" (M0924 00:16:18, 00:17:18), and Flight Bridge gets the commission "as the agent" (M0924 00:26:25). |
| Alternatives Considered | Not discussed |
| Status | Needs Review |
| Date | SV (date unknown); M0924 2026-09-24 |
| Source Transcript(s) | SV 00:27:10, SV 00:30:19, SV 00:33:55, SV 00:43:05, M0924 00:16:18, M0924 00:17:18, M0924 00:26:25 |
| Related Requirements | REQ-BE-005 |
| Notes | Correction 2026-10-07. The old version said segment shares are "the primary revenue model" and fees "secondary". No one ranked them. The segment figures were framed around Winifred's earnings, and their units are unconfirmed. See CONF-BE-006 for the revenue-framing conflict. |

## DEC-BE-004

| Field | Value |
|-------|-------|
| Decision ID | DEC-BE-004 |
| Decision | Flight Bridge will act as an air host for other travel agencies: "the Picasso, but better". Agencies pay a fee for access to the booking tool, Centrav-style. Flight Bridge will not buy out agencies. |
| Reasoning | Most small agencies have no ARC and book through hosts such as Picasso, Skybird, Sky Travel and Centrav, which keep the ARC kickbacks (M0924 00:46:04, 00:47:22). Jeff: "we are going to be the Picasso. But. Better because our system's going to integrate and be easier" (M0924 00:47:00). The access fee should at least cover hosting and AI overhead (M0924 00:51:32). Agencies are used to paying hosting fees. The edge over Centrav or Skybird is a real point of contact (M0924 00:51:59). Mauricio's Facebook test campaign to agencies drew 20 responses in 3 days, and half started booking through Traverse (M0924 00:50:27). First raised as "is that what we're thinking?", "Yep" (SV 00:32:47). Licensees become an air host's customers like Picasso or Skybird (PP 00:11:20). |
| Alternatives Considered | Brian Dickerson's buy-out model: buy small agencies with about 10% up front, paid over about five years (M0924 00:33:14 to 00:41:26). Rejected: "we actually don't need to follow Brian's method" (M0924 00:48:08). |
| Status | Agreed (B2B timing: after the booking tool, per DEC-BE-010) |
| Date | SV (date unknown); confirmed and extended 2026-09-24 |
| Source Transcript(s) | SV 00:32:47, PP 00:11:20, M0924 00:46:04, M0924 00:47:00, M0924 00:48:08, M0924 00:51:32 |
| Related Requirements | REQ-BE-006, REQ-BE-013 |
| Notes | Update 2026-10-07: the 09-24 meeting adds the access-fee model and the no-buy-out rule. The fee amount is not set (Q-BE-011). The earlier "8 to 9 agencies from Kansas to the West Coast" count comes only from SV 00:33:30 and is unverified (ASM-BE-004). "Picasso" is the transcript's spelling. |

## DEC-BE-005

| Field | Value |
|-------|-------|
| Decision ID | DEC-BE-005 |
| Decision | For now, Flight Bridge will not process payments for bookings. The platform captures card details through a payment authorization link but does not charge them. Third-party processing (for example Stripe) could come "down the line". |
| Reasoning | Travel has high chargeback and fraud risk. Per Mauricio, Stripe would not take travel, and We Travel only works because it became the fiduciary on top of Stripe (SV 00:15:42). Mauricio: "for the time being, I wouldn't want to be because of the fiduciary responsibility" (SV 00:15:11 to 00:16:40). Card capture: the client gets a link, enters card details, and the system records them and the IP address without charging (SV 00:13:09 to 00:14:44). |
| Alternatives Considered | Attach a processor now; become a fiduciary like We Travel |
| Status | Agreed |
| Date | SV (date unknown) |
| Source Transcript(s) | SV 00:13:09, SV 00:15:11, SV 00:15:42, SV 00:16:40 |
| Related Requirements | REQ-BE-001, REQ-BE-014 |
| Notes | Correction 2026-10-07: the old version said bookings go "through Sabre with established airline/agent billing relationships". The transcript does not say that, and the old version left out the "down the line" option. The Phase Plan's Phase 2 "includes merchant billing" (PP 00:08:58); see CONF-BE-005. Stripe was planned only for the email product (FS 00:03:56), and newsletter billing now runs through a Kit-managed Stripe Express account (PARENT DEC-NL-014). How a self-booking customer pays is still open (MI-BE-006). |

## DEC-BE-006

| Field | Value |
|-------|-------|
| Decision ID | DEC-BE-006 |
| Decision | Phase 1 "Book Now" is lead capture, not a booking. A deal's Book Now button leads to a form on our site, prefilled with the deal. The form captures the customer's details and sends them to Traverse for an agent to follow up and book by hand. |
| Reasoning | The booking engine does not exist yet, and newsletter subscribers need a way to act on a deal now. 06-10 V1 flow: "I want it to go from email to form landing page. Okay. To agent" (M0610 00:48:22). 09-24 restated it: "phase one. We can do a book now button that just takes their email and gets... them in contact with you through Victor" (M0924 00:21:33). Jeff saw no reason it could not ship right away (M0924 00:22:33). Jeff also said there is "no one point two": Phase 1 covers both subscriptions and bookings (M0924 00:25:51). |
| Alternatives Considered | Send users to Google Flights the way Flights From Home does (rejected, M0610 00:38:57); send users to the airline's site (rejected, M0924 00:20:38) |
| Status | Agreed |
| Date | 2026-06-10, restated 2026-09-24 |
| Source Transcript(s) | M0610 00:47:33 to 00:51:14, M0924 00:21:33, M0924 00:22:33, M0924 00:25:51 |
| Related Requirements | REQ-BE-008, REQ-BE-011 |
| Notes | Same flow as PARENT DEC-NL-011. Where the lead goes is stated three ways: a generic inbox with Denise assigning (M0610 00:50:14), Mauricio through Victor (M0924 00:21:33), and an info@ address for "an agent" (M0924 00:22:33). See CONF-BE-007 and Q-BE-010. |

## DEC-BE-007

| Field | Value |
|-------|-------|
| Decision ID | DEC-BE-007 |
| Decision | Flight-only deals (newsletter Basic tier) are the first to move into the booking engine. Flight-plus-destination packages (VIP tier) still go through human agents. |
| Reasoning | "Then the basic tier funnels easier to flight bridge when it's up and running. Yep" (M0610 00:33:33). JourneyFuse self-booking is "only for the VIP packages. The flights right now would be a form that go to an agent" (M0610 00:52:30). |
| Alternatives Considered | Not discussed |
| Status | Agreed |
| Date | 2026-06-10 |
| Source Transcript(s) | M0610 00:33:33, M0610 00:52:30 |
| Related Requirements | REQ-BE-003, REQ-BE-008 |
| Notes | How VIP packages get booked once they launch (planned early December 2026) was not discussed on 09-24 (M0924 00:59:40). See Q-BE-013. |

## DEC-BE-008

| Field | Value |
|-------|-------|
| Decision ID | DEC-BE-008 |
| Decision | Traverse agents must use the booking engine internally for at least one to two weeks before it is connected to the newsletter. |
| Reasoning | "we would want at least a week or two or more with the agents using Flight Bridge before we put this into put it into the mailer system. Yep" (M0610 00:54:01). This proves the engine on real bookings before customers see it. |
| Alternatives Considered | Not discussed |
| Status | Agreed |
| Date | 2026-06-10 |
| Source Transcript(s) | M0610 00:54:01 |
| Related Requirements | REQ-BE-001, REQ-BE-003 |
| Notes | This conflicts with DEC-BE-012, where agents do not use the portal. See CONF-BE-008. |

## DEC-BE-009

| Field | Value |
|-------|-------|
| Decision ID | DEC-BE-009 |
| Decision | Phase 2: the customer books directly on our landing page. The page is preloaded with the deal from the email. The customer can change dates and times and see the price change. After booking, the booking still goes to an agent, who follows up by email with the itinerary. |
| Reasoning | Mauricio: "Phase two, they can actually they can book it right on on our landing page" (M0924 00:23:04). Jeff: preload the flight, let the user change dates and see price changes, like a Google Flights spread (M0924 00:21:12). Jeff: the booking still goes to an agent who sends the itinerary (M0924 00:23:19). Jeff and Mauricio liked calling this "White Glove Service", the answer to "why not just use Google Flights myself?" (M0924 00:23:19, 00:23:59). |
| Alternatives Considered | Fully automated booking with no agent follow-up (not discussed as an option) |
| Status | Agreed |
| Date | 2026-09-24 |
| Source Transcript(s) | M0924 00:21:12, M0924 00:23:04, M0924 00:23:19 |
| Related Requirements | REQ-BE-003, REQ-BE-009, REQ-BE-010 |
| Notes | No date was set for Phase 2. Jeff said only that it should follow the newsletter "quickly" (M0924 00:19:27). See Q-BE-009. "White Glove Service" is agreed language, not an adopted brand name. |

## DEC-BE-010

| Field | Value |
|-------|-------|
| Decision ID | DEC-BE-010 |
| Decision | Build order: newsletter first, then the booking tool, then a Concur-style B2B product for other businesses and agencies. Expense tracking is not being built for now. |
| Reasoning | Mauricio: "Newsletter first, then booking tool. Newsletter, booking tool, and then attacking something like this" (M0924 00:45:11). Jeff on SAP Concur-style expense tracking: "Is that what we're building? Initially, no" (M0924 00:42:37). Earlier sources agree the email list comes before the booking engine (EM 00:03:49) and the booking site comes before the agent software (PP 00:08:58, R1205 00:00:00). |
| Alternatives Considered | JourneyFuse before the booking engine (M0610 00:54:01); CRM and portals first (SV 00:16:49); a partnership with Bill.com for expenses instead of building them (M0924 00:44:39, still "on the table") |
| Status | Agreed |
| Date | 2026-09-24 (most recent statement) |
| Source Transcript(s) | M0924 00:42:37, M0924 00:45:11, EM 00:03:49, PP 00:08:58, R1205 00:00:00 |
| Related Requirements | REQ-BE-001 |
| Notes | Sources disagree on phase numbering and on where JourneyFuse, the CRM and PNR import fit. See CONF-BE-004. |

## DEC-BE-011

| Field | Value |
|-------|-------|
| Decision ID | DEC-BE-011 |
| Decision | Bookings made through the booking tool run under Traverse's ARC number. Licensee agencies that use the Flight Bridge software also book flights under Traverse's ARC. The ARC side is not white-labeled. |
| Reasoning | Phase 1 is a booking site "specifically for Traverse using our ARC number" (PP 00:08:58). On licensees: "they would be using RARC still correct We're not trying to white label that part" (PP 00:10:48). The online booking tool links to "the sabre arc" (R1205 00:00:00). Jeff wants bookings to go through "your ARC number" (M0924 00:20:57). |
| Alternatives Considered | Not discussed |
| Status | Agreed |
| Date | PP (date unknown), R1205, M0924 |
| Source Transcript(s) | PP 00:08:58, PP 00:10:48, R1205 00:00:00, M0924 00:20:57 |
| Related Requirements | REQ-BE-005, REQ-BE-006 |
| Notes | ARC history: ARC was held under Winifred's name with a revenue pass-through, and she was due to exit "in October" (FS 00:00:29). On 09-24 Mauricio said Traverse "just barely got the ARC back about a year ago" (M0924 00:41:37). Some Traverse bookings still run through Brian Dickerson's ARC because of his contracts (M0924 00:23:59). See Q-BE-002. |

## DEC-BE-012

| Field | Value |
|-------|-------|
| Decision ID | DEC-BE-012 |
| Decision | Traverse's own agents will not use the online booking portal to book, because the portal carries a fee. It is for clients. |
| Reasoning | "our agents aren't going to necessarily use that portal to book or would they? No. They're not going to use that." (R1205 00:02:52). Mauricio already has clients lined up to use it (R1205 00:02:52). |
| Alternatives Considered | Not discussed |
| Status | Needs Review |
| Date | 12-05 (year not stated) |
| Source Transcript(s) | R1205 00:02:52 |
| Related Requirements | REQ-BE-002 |
| Notes | Speaker labels in R1205 are unreliable, so who said this is uncertain. It conflicts with M0610, where agents use the engine for 1 to 2 weeks first (DEC-BE-008) and "agents would book through Flight Bridge instead of Sabre directly" (M0610 00:54:01). See CONF-BE-008. |

## DEC-BE-013

| Field | Value |
|-------|-------|
| Decision ID | DEC-BE-013 |
| Decision | For AI features, start on a hosted model API (a Claude/Anthropic subscription was mentioned). Then quickly build a self-hosted model as a fallback, possibly switching before any provider pricing change. AI is a possible phase 4: not the focus now, but keep it in mind while building. |
| Reasoning | Jeff expects AI providers to end cheap or unlimited pricing, which could break third-party-API features (PP 00:18:27). "we could start building it with the open API with the cloud subscription into it. And just know that we need to very quickly work on building the alternatives" (PP 00:22:08). "We've got three, maybe four phases right now, the fourth phase being. Uh, the AI portion of it" (PP 00:24:24). |
| Alternatives Considered | Hosted API only (rejected because of cost and access risk, RISK-BE-008) |
| Status | Agreed |
| Date | PP (date unknown) |
| Source Transcript(s) | PP 00:18:27, PP 00:22:08, PP 00:24:24 |
| Related Requirements | None yet |
| Notes | Platform-wide decision, recorded here because it shapes booking engine architecture. Jeff has outside developers who offered to help if this needs to scale fast (PP 00:23:44). |
