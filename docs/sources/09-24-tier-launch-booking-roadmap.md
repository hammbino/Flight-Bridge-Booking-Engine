---
title: Source Digest - Tier Launch and Booking Engine Roadmap (09-24)
project: Flight Bridge Booking Engine
status: Active
owner: Jeffrey Hammond / Mauricio Melendez
last_updated: 2026-10-07
source_transcripts: ["09-24 Meeting_ Tiered Travel Subscription Launch, Email Campaign, and Booking Engine Roadmap-transcript.txt"]
tags: [source-digest, booking-phases, book-now, lead-capture, deal-landing-page, white-glove, host-agency, b2b-booking-tool, competitors, sap-concur, centrav, picasso, arc, sabre, journeyfuse-gaps, packages, revenue-model]
---

# Tier Launch and Booking Engine Roadmap (09-24)

**Date:** 09-24 (year not stated in transcript; parent repo docs record it as 2026-09-24)  **Participants:** Jeffrey Hammond (Jeff), Mauricio Melendez, Speaker 3 (unidentified, only filler words)
**Aliases (identical files in parent repo Transcripts/):** 09-24 Meeting_ Tiered Travel Subscription Launch, Email Campaign, and Booking Engine Roadmap-transcript.txt
**Booking relevance:** High. This is the most recent booking discussion: it sets a two-phase "Book Now" plan (lead capture first, real booking second), the build order (newsletter, then booking tool, then B2B), and the B2B agency booking-tool model.

## Summary for agents
The booking engine is framed as the real money maker; newsletter subscriptions are base MRR that feed it. Phase 1 "Book Now" is not a booking: it is a lead form on our site that captures name, email and the flight, then emails an agent to follow up. Phase 2 lets the customer book right on our landing page, preloaded from the email deal, with the ability to change dates and see price changes, and it still sends to an agent for white glove follow-up. Build order agreed: newsletter first, then the booking tool, then a B2B tool like SAP Concur. For other agencies the model shifts toward a Centrav-style booking tool that agencies pay a fee to use, not Brian Dickerson's buy-out method. Several items update or conflict with the 2026-06-30 booking docs; see the section after the Points table.

Name notes (transcription is noisy): "Flybridge"/"FlightBridge" = Flight Bridge. "Traverse"/"Traversa"/"Traverse Tours"/"trevorstores dot com" = Traverse (the email domain is uncertain). "Brandon Dickerson", "Breyer, with Dickerson" and "Brian" appear to be the same competitor/partner, but this is not certain. "SAP Concur"/"SVP Concure" = SAP Concur. "Centrav"/"Centraf" = Centrav. "Victor" = an AI agent tool Mauricio uses. "VCRM" = VacationCRM (inferred from repo context, not stated). "Journey Fuse" = JourneyFuse.

## Points
| # | Type | Point | Who | Time | Quote (decisions only) |
|---|------|-------|-----|------|------------------------|
| 1 | FACT | Revenue structure has two parts: subscriptions (MRR) and bookings (pay per use). | Mauricio | 00:05:19, 00:05:37 | |
| 2 | FACT | Jeff states bookings are where the real money is made, not subscriptions. | Jeff | 00:05:33 | |
| 3 | ASSUMPTION | Illustrative booking math: 1,000 subscribers, 1% book, so 10 bookings a month at an average of about $150 per booking, giving about $1,500 a month. Unclear whether $150 is ticket price or Flight Bridge revenue per booking. | Mauricio, Jeff | 00:16:18 to 00:17:11 | |
| 4 | FACT | International bookings are worth a lot more than $150. | Jeff | 00:17:14 | |
| 5 | FACT | Booking revenue is split between Traverse and Flight Bridge "the way we have it". Split terms not stated here. | Mauricio | 00:17:18 | |
| 6 | FACT | Competitors Going and Flights From Home do not let users book. Deals send users elsewhere. This is the gap Flight Bridge's booking fills. | Jeff, Mauricio | 00:19:08 to 00:19:22 | |
| 7 | REQUIREMENT | Right after the newsletter launch, a flight booking page must be up so subscribers can book the emailed flight from "our engine". | Jeff | 00:19:27 | |
| 8 | DECISION | Phase 1 vs Phase 2: moving from phase one to phase two adds the "Book Now" (booking out) button. | Mauricio | 00:19:59 | "along from phase one to phase two, is the booking out button" |
| 9 | FACT | On competitor sites, clicking an airline button (e.g. Delta) sends the user to the airline's site. | Mauricio, Jeff | 00:20:35, 00:20:38 | |
| 10 | REQUIREMENT | "Book Now" must send the user to our site, not the airline's. | Jeff, Mauricio | 00:20:38 to 00:20:43 | |
| 11 | IDEA | Booking should go through our own ARC number (Jeff says "BCR or your ARC number"; "BCR" unclear). | Jeff | 00:20:57 | |
| 12 | REQUIREMENT | Phase 2 landing page preloads the flight from the email. The user can change dates and times and see the price changes. Described like a Google Flights spread. | Jeff | 00:21:12, 00:21:15 | |
| 13 | DECISION | Phase 1 "Book Now" is lead capture only. It takes the user's details and puts them in contact with Mauricio through Victor. | Jeff, Mauricio | 00:21:33 to 00:22:24 | "phase one. We can do a book now button that just takes their email and gets... them in contact with you through Victor" |
| 14 | REQUIREMENT | Phase 1 lead page captures name, email and the flight information, then sends an email to info@(Traverse domain) for an agent to follow up. Jeff says there is no reason this cannot ship now. | Jeff | 00:22:33 | |
| 15 | CONFLICT | Phase 1 lead routing is stated two ways in this meeting: email to Mauricio via Victor (00:20:28, 00:21:33) and email to the info@ address for "an agent" (00:22:33). Not reconciled. | Jeff | 00:20:28, 00:22:33 | |
| 16 | DECISION | Phase 2: the customer books directly on our landing page. | Mauricio | 00:23:04 | "Phase two, they can actually they can book it right on on our landing page." |
| 17 | REQUIREMENT | Even after a Phase 2 self-booking, the booking still goes to an agent, who follows up by email with the itinerary. | Jeff | 00:23:19 | |
| 18 | IDEA | Brand the reason to book through us as "White Glove Service" (answer to "why not just use Google Flights myself?"). Mauricio agreed with the phrase; not formally adopted. | Jeff, Mauricio | 00:23:19, 00:23:59 | |
| 19 | FACT | Traverse books some travel through Brandon Dickerson's ARC because of contracts he holds. Traverse fulfils the contract and is paid; Dickerson keeps the ARC side. | Mauricio, Jeff | 00:23:59 to 00:24:39 | |
| 20 | DECISION | No "phase 1.2". Phase 1 covers both MRR (subscriptions) and bookings (in the lead-capture form above). | Jeff | 00:25:51 | "There's no one point two. We're we're going MRR and bookings phase one" |
| 21 | FACT | Positioning: Flight Bridge acts as an agent for Traverse Tours; the commission goes to Flight Bridge as "the agent". | Jeff | 00:26:25 | |
| 22 | FACT | SAP Concur (via Dickerson): $500 to onboard a client. A per-ticket cost was stated as "$320", which looks garbled (see conflicts). It books hotels, air and car and is "just a wrapper around the GDS" in an easy booking engine. | Mauricio | 00:26:57 | |
| 23 | FACT | Missy (group client) books large hotel volume, e.g. sold out twelve hotels in Cusco for a week. She used Hotels.com for free nights, but its switch to points cut her rewards. | Mauricio | 00:27:56 to 00:29:07 | |
| 24 | FACT | Interim plan for Missy: use Dickerson's SAP Concur ($500 one-time) to book hotels. Hotel commission splits 70/30 (Traverse 70, Dickerson 30). Missy may get about 10% back as cash back or future travel credit, so Flight Bridge/Traverse drops to about 60% and Dickerson stays at 30%. | Mauricio | 00:29:07 to 00:30:57 | |
| 25 | QUESTION | Whether Dickerson will share the cost of Missy's 10% incentive. Jeff: "make Dickerson share half." Mauricio is still negotiating. Mauricio is covering the $500. | Jeff, Mauricio | 00:31:00 to 00:31:19 | |
| 26 | IMPLIED | Hotel booking demand from a group client (Missy) and Concur's hotel/air/car scope suggest the booking engine may eventually need hotel booking. Not stated as a requirement. | Mauricio | 00:26:57, 00:29:07 | |
| 27 | FACT | Dickerson does corporate travel only. Traverse does leisure and incentive. He is moving into leisure using a strategy Mauricio gave him. | Mauricio | 00:31:19, 00:31:55 | |
| 28 | FACT [borderline] | Dickerson's growth model: buys out small agencies (often owners in their seventies) with about 10% up front and the rest in revenue-based installments over about five years. Agents keep their commissions. He earns from higher airline, hotel and car overrides due to volume, plus segment shares, and charges agencies booking fees. Exact commission percentages in the transcript are garbled and not reliable. | Mauricio, Jeff | 00:33:14 to 00:41:26 | |
| 29 | FACT | Traverse "just barely got the ARC back about a year ago" with Winifred's help. | Mauricio | 00:41:37 | |
| 30 | FACT | Traverse does not have a tool like Dickerson's (SAP Concur). Jeff: "But we're building that tool." | Mauricio, Jeff | 00:41:56, 00:42:04 | |
| 31 | QUESTION | Jeff asks whether Flight Bridge's tool will come close to SAP Concur. Not fully answered. | Jeff | 00:42:09 | |
| 32 | FACT | SAP Concur is integrated with Microsoft Teams and is its own accounting and booking platform with expense tracking. Mauricio describes it as an expense platform with travel added. | Mauricio | 00:42:19, 00:44:21 | |
| 33 | DECISION | Not building SAP Concur-style expense tracking initially. | Jeff | 00:42:37 | "Is that what we're building? Initially, no." |
| 34 | FACT | Everything is migrating to JourneyFuse; Travify is being dropped. The app Jeff builds is "JourneyFuse plus a couple of other things". | Mauricio, Jeff | 00:42:55 to 00:43:00 | |
| 35 | FACT | Gaps in JourneyFuse that Flight Bridge could fill: no booking engine tied into it, no business expense tracking, no QuickBooks connection. | Mauricio | 00:43:23 | |
| 36 | QUESTION | Jeff can reverse engineer JourneyFuse but needs Mauricio to list what JourneyFuse is not doing where he sees potential. Only the three gaps above were given. | Jeff | 00:43:00 | |
| 37 | FACT | Concur-style tool is white labeled for the client. Dickerson charges clients about $1,500 to $2,000 to set it up (he would charge Grit about $2,000, and Mauricio $500). | Mauricio | 00:43:55, 00:44:11 | |
| 38 | IDEA | Partner with Bill (Bill.com, inferred from "Bill with travel") instead of building expense tracking: Flight Bridge builds the travel side and Bill provides expenses. "On the table", but time-limited. | Jeff, Mauricio | 00:44:39 to 00:44:57 | |
| 39 | DECISION | Build order: newsletter first, then booking tool, then a Concur-style B2B product. | Mauricio | 00:45:11 | "Newsletter first, then booking tool. Newsletter, booking tool, and then attacking something like this." |
| 40 | FACT | Two audiences: B2C (current clients and email subscribers; Grit counts as B2C) and B2B (when Flight Bridge has software to offer other agencies so they can do what Traverse does). | Mauricio, Jeff | 00:45:11 to 00:46:00 | |
| 41 | FACT | Most small agencies lack an ARC. They book through hosts such as Picasso, Skybird and Sky Travel, using the host's ARC. The hosts earn the ARC kickbacks. | Jeff, Mauricio | 00:46:04 to 00:47:00 | |
| 42 | DECISION | Flight Bridge will be "the Picasso, but better": easier, integrated (like JourneyFuse), and agents can book themselves instead of calling. | Jeff | 00:47:00, 00:47:15 | "we are going to be the Picasso. But. Better because our system's going to integrate and be easier." |
| 43 | FACT | Host tools like Picasso are booking tools built on the GDS. Most agents lack GDS access and avoid the terminal screen. Centrav is widely used: agents pay a monthly fee to access its booking engine. | Mauricio | 00:47:22 | |
| 44 | DECISION | Agency model follows Centrav (paid access to our booking tool), not Dickerson's buy-out method. No buying out agencies. | Jeff, Mauricio | 00:48:08 to 00:48:42 | "That's what we're doing. So we actually don't need to follow Brian's method" |
| 45 | FACT | Expedia TAAP (travel agent access) has a "GDS" button after booking. It asks for the agent's PCC (pseudo city code) and an existing PNR, then pushes the booking into the agent's GDS (Sabre). | Mauricio, Jeff | 00:48:42 to 00:49:21 | |
| 46 | IMPLIED | Mauricio's TAAP example suggests the agency booking tool should push bookings into the agency's Sabre by PCC/PNR. Not stated as a requirement. | Mauricio | 00:48:42 | |
| 47 | FACT | Airline sites (Delta, American, United) are built on top of the GDSs (Sabre, Amadeus, Worldspan). | Mauricio | 00:49:21 | |
| 48 | FACT | Flight Bridge cannot and would not build its own GDS. GDSs are regulated (Jeff mentions FAA and other bodies). | Jeff | 00:49:41 | |
| 49 | IDEA | Use Sabre's AI MCP to build features. Jeff has looked at it; Mauricio has not. | Jeff | 00:50:15 | |
| 50 | FACT | Mauricio ran a Facebook campaign targeting travel agencies: 20 responses in 3 days, half started booking through Traverse. It was stopped because they could not keep up with the load. | Mauricio, Jeff | 00:50:27 to 00:51:12 | |
| 51 | REQUIREMENT | Onboarded agencies are pointed to the booking tool with instructions on how to work with Flight Bridge. | Mauricio | 00:51:20 | |
| 52 | DECISION | Charge agencies for the booking tool, at least enough to cover hosting and AI integration overhead. Amount not set. | Jeff, Mauricio | 00:51:32 to 00:51:59 | "You'll want the overhead for hosting AI, any AI integrations that we have going on with it." |
| 53 | FACT | Agencies are used to paying hosting fees. The differentiator vs Centrav/Skybird is a real point of contact. | Mauricio | 00:51:59 | |
| 54 | IDEA | A tool like Victor integrates with the booking tool and talks back to agencies. Agencies are fine with email rather than voice. | Jeff, Mauricio | 00:52:19 to 00:52:42 | |
| 55 | FACT [borderline] | Tier two newsletter (flights, Wed and Fri) and tier one free (weekly teaser) are the deal sources that feed the Book Now flow. Tier two goes live first Wednesday of November. | Mauricio, Jeff | 00:54:33, 00:59:40 | |
| 56 | QUESTION | No date was set for Phase 2 (real booking on the landing page). Jeff only says "quickly following" the newsletter. | Jeff | 00:19:27 | |
| 57 | FACT [borderline] | Tier two deals: about 5 domestic and 5 international from the home airport (SLC first), chosen on price only. Jeff also suggested coasts, cross-country, and international (South America, Europe). | Mauricio, Jeff | 00:07:08, 00:07:46 | |
| 58 | FACT [borderline] | Subscribers give a home airport at signup, with primary/secondary/tertiary departure options. Only primary is used for now. Target market is Salt Lake City first. | Mauricio, Jeff | 00:03:27, 00:04:38, 00:15:12 | |
| 59 | FACT [borderline] | Mauricio uses Victor flight-tracker and "Fairwatch" workflows (Mon/Wed/Fri) that report target fares and best booking windows from last year's data. Example: SLC to Hawaii in December found at $790 vs client's $1,100 target. | Mauricio | 00:08:17 to 00:11:15 | |
| 60 | IDEA [borderline] | Jeff plans a script (not AI) for fare lookup, plus a Google Flights scrape, and a Victor prompt to pull top destinations from VCRM and JourneyFuse to seed the city list. | Jeff | 00:11:42, 00:13:06 | |
| 61 | IDEA [borderline] | Weekly automated scrape picks top 5 domestic and 5 international, formats the email, with human approval until trusted. | Mauricio | 00:13:54 | |
| 62 | QUESTION [borderline] | How far in advance deals should be for (Jeff asked). Mauricio gave a 6 to 10 week Fairwatch example but no rule was set. | Jeff | 00:09:20 | |
| 63 | FACT [borderline] | Tier three packages: cruises (e.g. Viking River), tours (Egypt, humanitarian, faith-based), golf, Antarctica trekking, mountain biking, New Zealand rafting, Norway glass igloos. Sourced by scraping Vax, Funjet, Europe Express, Gate One. "Basically the stuff Jimmy's putting together." These are "huge ticket items". | Mauricio, Jeff | 00:56:27 to 00:59:12 | |
| 64 | RISK [borderline] | Whether package suppliers allow an agent to scrape their sites. Mauricio says yes and that Victor already does it; it is public content. | Jeff, Mauricio | 00:56:47 to 00:57:03 | |
| 65 | FACT [borderline] | Tier three (packages) target is beginning of December. No booking path for packages was discussed. | Mauricio | 00:59:40, 01:00:22 | |
| 66 | FACT [borderline] | Phase 1 tasks live in the GitHub repo. Jeff will send a weekly executive summary of progress and spend, tied to GitHub commits. | Jeff, Mauricio | 01:00:31 to 01:02:01 | |

## Updates and conflicts vs existing booking docs (dated 2026-06-30)

Each line cites the existing ID and the point number above.

- **roadmap.md Phase 1 / Release Goals (CONFLICT, update).** The roadmap's Phase 1 is "Build newsletter deal landing page (token-based pre-population)" with release goal "Newsletter has a working destination for deal links". This meeting defines Phase 1 "Book Now" as a lead form only (name, email, flight, email to agent). The preloaded, editable landing page is Phase 2 (points 12, 13, 14, 16). Note: "phase" here is the business launch phasing, not the roadmap's Phase 0 to 5 numbering, so mapping is uncertain.
- **roadmap.md Phase 2 and REQ-BE-001 (update).** Consumer self-booking is confirmed as the next step after lead capture (points 7, 16). New detail: every self-booking still routes to an agent for an emailed itinerary (point 17). The roadmap flow "search, select, passenger info, payment, ticket" has no agent follow-up step.
- **REQ-BE-003 (confirms, adds detail).** Preloaded deal with editable dates is confirmed (point 12). New: show price changes as dates and times change, Google Flights-style. Token mechanics not discussed. In this meeting the preloaded page is Phase 2, not Phase 1.
- **REQ-BE-007 (consistent).** Phase 1 lead form only asks for name, email and flight (point 14). No account needed.
- **DEC-BE-002 (CONFLICT on competitor pricing).** DEC-BE-002 says competitor Brian charges about $30 per booking. This meeting says Dickerson's SAP Concur costs $500 to onboard and "$320" per ticket, plus $1,500 to $2,000 setup charged to clients (points 22, 37). The "$320" figure is likely a transcription error, but it cannot be confirmed. It is also not certain that "Brian" and "Brandon Dickerson" are the same person.
- **DEC-BE-002 / REQ-BE-002 (update).** The corporate 1-hour review window is not mentioned. The new consumer Phase 2 adds a similar "agent follows up" step for consumers (point 17).
- **DEC-BE-003 (possible CONFLICT on revenue framing).** DEC-BE-003 makes Sabre segment shares the primary booking revenue (about $0.30 to $7 per segment). This meeting frames booking revenue as about $150 per booking, split with Traverse (points 3, 5). It does not mention segment shares for Flight Bridge (only as part of Dickerson's income, point 28). Whether $150 is ticket value or revenue is unclear.
- **DEC-BE-004 / REQ-BE-006 (update, partial CONFLICT).** The "Picasso" host agency direction is reaffirmed (point 42), but the revenue model changes. DEC-BE-004 relies on override segment shares. This meeting adds a Centrav-style paid access fee covering hosting and AI overhead (points 44, 52). New details: no buy-outs (point 44); agencies currently use Picasso, Skybird, Sky Travel and Centrav (points 41, 43); demand evidence from the Facebook campaign (point 50). Timing matches "medium-term": the B2B product comes after newsletter and booking tool (point 39). REQ-BE-006 says 8 to 9 eligible agencies between Kansas and the West Coast; this meeting gives no regional count.
- **DEC-BE-001 (related, no conflict).** Not building a GDS is reaffirmed (point 48). New ideas: Sabre AI MCP (point 49) and pushing bookings into an agency's Sabre by PCC/PNR like Expedia TAAP (points 45, 46). Both bear on Q-BE-004 (Sabre integration method).
- **DEC-BE-005 (no conflict, worth noting).** Stripe is discussed only for newsletter subscriptions. Payment handling for Phase 2 flight bookings was not discussed.
- **Q-BE-002 (partial update).** "We just barely got the ARC back about a year ago" with Winifred's help (point 29). Jeff also wants bookings under "our ARC number" (point 11). Separately, some Traverse bookings still go through Dickerson's ARC due to his contracts (point 19). This does not fully answer whether Winifred is out.
- **Q-BE-006 (update).** Missy (group coordinator) is being moved to Dickerson's SAP Concur for hotels as a stopgap, with a 70/30 split and a possible 10% incentive to her (points 23 to 25). This also raises hotel booking as a possible scope item (point 26). Current booking docs cover flights only.
- **roadmap.md Future Milestones "Adventure/experience package booking" (related).** Tier three packages launch in the newsletter around early December (points 63, 65). How packages get booked was not discussed, so this does not change the booking roadmap.
- **roadmap.md / project-state (new sequencing).** Agreed order: newsletter, then booking tool, then the Concur-style B2B product (point 39). Expense tracking is out for now (point 33). JourneyFuse gaps (booking engine tie-in, expense tracking, QuickBooks) are new inputs (point 35).

## Topics skipped (not booking)
Free/tier two/tier three newsletter content and send cadence (Wed; Wed and Fri; Mon), redacted "missed opportunities" free tier, Stripe tier setup, pricing ideas ($9.99 base, $1.99 per extra departure city), MRR projections, Kit migration from Beehiiv, first email target (first week of November) and October daily test sends, website/DNS setup, expansion markets (Phoenix, LA, NYC, Paris, California "flights from home" idea), Dickerson's agency buy-out math in detail, Jeff's spending card and loan against Traverse, weekly executive summary day (Sunday vs Monday stated both ways).
