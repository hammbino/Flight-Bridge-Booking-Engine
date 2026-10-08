---
title: Source Digest - Strategic Vision for a Unified Travel Management Platform
project: Flight Bridge Booking Engine
status: Active
owner: Jeffrey Hammond / Mauricio Melendez
last_updated: 2026-10-07
source_transcripts: ["Strategic Vision for a Unified Travel Management Platform", "Call with Mauricio-transcript.txt"]
tags: [source-digest, sabre, pnr-import, online-booking-tool, corporate-booking, group-management, client-portal, payments, segment-shares, host-agency, flight-tracking, ai-agent, competitors, funding, database]
---

# Strategic Vision for a Unified Travel Management Platform

**Date:** Unknown (filename has no date; content references an upcoming December push and a January/February Sabre renegotiation)  **Participants:** Mauricio Melendez, Jeff Hammond
**Aliases (identical files in parent repo Transcripts/):** "Strategic Vision for a Unified Travel Management Platform", "Call with Mauricio-transcript.txt"
**Booking relevance:** High. This is the founding conversation for the booking engine: Sabre/PNR import, online booking tool, corporate booking with fees, group management, client portal, payment capture, segment-share revenue, and the host-agency ("Picasso") model.

## Summary for agents

Mauricio walks Jeff through why existing agent tools (Trace/Travify, VCRM, We Travel) are poor, and describes a unified platform for "Traverse" (the agency name used throughout; the transcript never says "Flight Bridge"). The agreed starting point is a CRM with an agent back end and a client front end, where trips are imported from Sabre (or VAX etc.) by PNR and last name. A full Sabre wrapper (agent books everything through the platform UI) is the "eventually" goal, not the start. An online booking tool is called the lowest-hanging fruit for revenue, earning Sabre segment shares and, for corporate self-bookers, a small per-booking fee. The platform will capture payment details but not process payments, because of travel chargeback and fiduciary risk. Later phases include a group management tool with organizer and traveler logins, live flight and weather tracking with proactive alerts, selling the software to other agencies by subscription, and acting as host for other agencies' bookings. Much of the money discussion uses unclear numbers; treat figures as approximate.

Naming note: "VCRM", "BCRM", "BC RM" and "BCMM" all appear and almost certainly refer to the same CRM product (transcription variants). "Saber"/"Saver"/"SABRE" are Sabre. "Picasso" is the transcript's spelling for a host-agency-type entity; the real term is not confirmed (possibly "PCC" or similar). "Grit"/"grip" are the same corporate client.

## Points

| # | Type | Point | Who | Time | Quote (decisions only) |
|---|------|-------|-----|------|------------------------|
| 1 | REQUIREMENT | Agent app needs a "Client" menu with New / Existing. New opens a form for client details. On submit, the back end is populated with that info. | Mauricio | 00:00:01 | |
| 2 | IDEA | A checkbox/toggle on the new-client form sends the client an automated welcome message from the logged-in agent ("Hey, it was great talking to you"). | Mauricio | 00:00:01 | |
| 3 | REQUIREMENT | Agents get a back-end dashboard view when they log in. | Mauricio | 00:01:00 | |
| 4 | REQUIREMENT | System has both a back end for Traverse team members and a front end for clients. Clients log in to see their flight, flight history, past flights, and enter or update payment. Mauricio: "Oh yeah." | Jeff (asked), Mauricio (agreed) | 00:01:16 | |
| 5 | FACT | Competitor UX complaint: client search in the current tool returns blank unless pre-set filters are removed. Trips and payments views also show blank because filters are pre-applied. Seen as easy to avoid. | Mauricio, Jeff | 00:01:31 | |
| 6 | IDEA | Customizable dashboards were raised and set aside as premature ("putting the cart before the horse"). | Jeff | 00:02:30 | |
| 7 | FACT | Mauricio has a wireframe. Some sections are MVP; others are add-ons to build later. He confirms wireframes exist for "all this." | Mauricio | 00:02:38, 00:26:00 | |
| 8 | FACT | Competitor: Trace is called a forerunner in agent software. Ships weekly releases Mauricio calls "garbage." Has no manifest report until a planned January 6 release. | Mauricio | 00:02:38, 00:03:54 | |
| 9 | REQUIREMENT | Manifest report is treated as a basic must-have that competitors lack. | Mauricio | 00:03:54 | |
| 10 | REQUIREMENT | Itineraries: send one overall itinerary to a group coordinator and individual itineraries to each traveler, without creating separate trips. "You should just be able to fork it." | Mauricio | 00:03:54, 00:04:30 | |
| 11 | FACT | Market search for "group travel management" returns corporate tools where "group" means a company whose employees book via a portal. No tool fits Traverse's meaning of group (leisure/incentive groups). We Travel is the exception noted. | Mauricio | 00:04:53 | |
| 12 | FACT | Agents currently juggle three systems daily: VCRM, We Travel, and a billing/itinerary tool (Travify). Unifying them is the core pain point. | Jeff, Mauricio | 00:05:41, 00:05:55 | |
| 13 | FACT | In current tools, trips are never created natively. Every trip originates in an outside booking tool (Expedia TAAP, VAX, Sabre, etc.), then is re-entered segment by segment. | Mauricio | 00:05:55 | |
| 14 | FACT | Competitor UMAPped imported trips with just PNR and last name. | Mauricio | 00:06:53 | |
| 15 | FACT | Trace's Sabre import requires an "uploader" hosted on a PC (a virtual machine). Jeff attributes this to the vendor not being ARC. Mauricio plans to run the uploader on his own PC to test. | Mauricio, Jeff | 00:07:29 to 00:08:28 | |
| 16 | FACT | Trace's current import flow: every flight issued through Sabre appears in a list; the agent must find it, click it, then "add reservation to trip." Previously, selling a segment in Sabre and hitting import sent segments straight into the trip. Mauricio says the old way was better. | Mauricio | 00:08:36 | |
| 17 | DECISION | Keep using Sabre as the GDS. The platform starts as a CRM that imports bookings by last name and PNR, not as a Sabre wrapper. | Jeff (proposed), Mauricio (agreed) | 00:09:26, 00:11:48 | "The easiest way is to have this CRM and then just be able to import from a last name. And PMR." |
| 18 | IDEA | Long-term goal: a wrapper over Sabre so agents do all Sabre commands through the platform UI, "one location for everything." Mauricio: "Eventually." He was unsure how it would work technically. | Jeff, Mauricio | 00:09:26 to 00:10:09 | |
| 19 | RISK | A Sabre wrapper "makes a lot harder to look at flights." | Jeff | 00:10:17 | |
| 20 | FACT | Precedent: at Continental Airlines, Mauricio used a UI shell over Sabre. Enter origin, destination, dates on a calendar, submit, see a Sabre-like availability window, click segments to sell, hit price, take card, enter passenger info, hit ticket, enter client email, client gets confirmation. Mauricio: "That's what you want to see eventually." | Mauricio | 00:10:23 to 00:11:47 | |
| 21 | IDEA | Airfare is an add-on in the software sold to other agencies, because many agencies do not sell airfare. | Mauricio | 00:11:55 | |
| 22 | QUESTION | Timeline for the Sabre wrapper / airfare add-on. Mauricio: "I don't know what timeline looks like." | Mauricio | 00:12:18 | |
| 23 | REQUIREMENT | Payments are attached to trips. Stored cards belong to the client profile, not the trip. A card added through a trip saves back to the user. | Jeff, Mauricio | 00:12:18 to 00:12:59 | |
| 24 | REQUIREMENT | Payment authorization: from a client profile, agent hits "add payment authorization," picks a trip, and the system sends the client a link to enter card details. It captures the info but does not charge. It records IP address and similar data. Submitted amount shows on the trip so the agent can apply it. | Mauricio | 00:13:09 to 00:14:44 | |
| 25 | REQUIREMENT | The payment authorization link must not require the client to create an account. It is tied to the trip on their existing profile. | Mauricio | 00:13:47 | |
| 26 | FACT | Current VCRM pain: to take a payment, agent creates the trip, assigns a booking number, sends a website link, and tells the client to enter the confirmation number so the form links to their profile. Example: Jared Hayes asked for a payment link. | Mauricio | 00:13:47 | |
| 27 | DECISION | The platform will not process payments (no attached payment processor) for now, because of travel chargeback/fraud risk and fiduciary responsibility. | Mauricio, Jeff | 00:15:11 to 00:16:40 | "And honestly, for the time being, I wouldn't want to be because of the fiduciary responsibility." |
| 28 | IDEA | Offering payment processing through a third party such as Stripe could come "down the line." | Mauricio | 00:15:11, 00:16:40 | |
| 29 | FACT | Per Mauricio: Stripe would not do travel because of chargebacks and fraud. We Travel exists because it became the backer/fiduciary on top of Stripe and carries chargeback liability. | Mauricio | 00:15:42 | |
| 30 | DECISION | Build order starts with the CRM, the client front-end portal, and the agent back end that imports trips from Sabre, VAX, etc. Mauricio adds the group management tool to this set. | Jeff (proposed), Mauricio (extended) | 00:16:49, 00:17:03 | "we would start with the CRM, The front portal for the customer and then the back end for us, where it imports the trips" |
| 31 | REQUIREMENT | Group management tool: agent enters a group's flights and tours. Group organizer (e.g. Missy, 40 people to Ecuador) logs in, sees the trip (e.g. "dentists Ecuador June 2026"), sees all registered travelers, and can open each traveler's reservation. | Mauricio | 00:17:03 | |
| 32 | REQUIREMENT | Master report toggle for organizers: lists travelers grouped by departure city and flight segment (e.g. 5 from Salt Lake on outbound X), merging names on shared connecting flights. Printable. Mauricio says an old tool used to do this. | Mauricio | 00:17:39 | |
| 33 | FACT | Groups are Traverse's major revenue source. | Jeff (stated), Mauricio (agreed) | 00:18:33 | |
| 34 | REQUIREMENT | Individual travelers get their own login, keyed to the email they submitted. They can view their trip and flight info. | Mauricio | 00:18:38, 00:19:13 | |
| 35 | IDEA | Travelers can cancel themselves without going through the agency or organizer. Any credit stays in their account instead of issuing a certificate. | Jeff, Mauricio | 00:19:05, 00:19:13 | |
| 36 | REQUIREMENT | Roles: admin user = group organizer; sub user = individual traveler. One-off clients have a login but no group flag. Back-end admins can access all of them. | Mauricio, Jeff | 00:19:13, 00:20:01 | |
| 37 | IDEA | Link from traveler's trip to the airline website for check-in. | Mauricio | 00:19:13 | |
| 38 | FACT | Mauricio believes no existing tool does this group management function. | Mauricio | 00:19:13 | |
| 39 | DECISION | Group organizer view, individual traveler view, and admin back end are built together as one system. | Jeff | 00:20:01 | "We're really building all three pieces together" |
| 40 | QUESTION | SQL vs NoSQL database. Jeff knows SQL better but thinks NoSQL might suit the build-out. Unresolved: "I have no idea." | Jeff | 00:20:29 | |
| 41 | IDEA | Flight tracker inside the dashboard. Jeff says APIs are widely available (he mentions Google Flights) and it could be linked in easily. Unverified claim. | Mauricio, Jeff | 00:21:18, 00:21:43 | |
| 42 | REQUIREMENT | Team calendar showing who is traveling (VCRM and Trace both have this). | Mauricio | 00:21:51 | |
| 43 | REQUIREMENT | Security: options to limit or open visibility of who is traveling. | Jeff | 00:22:09 | |
| 44 | IDEA | Live-track all client flights from data in the system. Alert the on-call agent (and whole team) on delays before the client knows. | Mauricio, Jeff | 00:22:15 to 00:23:07 | |
| 45 | IDEA | "Flight tracker" button opens a live map of flights in the air. Open source options exist. | Mauricio, Jeff | 00:23:07 to 00:23:33 | |
| 46 | IDEA | Weather overlay from weather.gov. Proactive client notices, e.g. weather at a layover city, "we're monitoring this." | Mauricio | 00:23:54 | |
| 47 | IDEA | Proactive rebooking: tell the client "your flight got delayed, we've already booked you on the next flight," or ask them to log in and accept one of offered options. | Jeff, Mauricio | 00:24:35 to 00:25:11 | |
| 48 | IDEA | Build an AI agent to do this monitoring work so the team looks like 150 people without growing. | Jeff | 00:25:29 | |
| 49 | FACT | Traverse now has direct Sabre access. That is why an online booking tool is newly possible. | Mauricio | 00:26:00 | |
| 50 | DECISION | The online booking tool is the first revenue play ("lowest hanging fruit"). | Mauricio | 00:26:00, 00:34:47 | "The lowest hanging fruit is an online booking tool, right?" |
| 51 | IDEA | Price shoppers can self-book through the online booking tool. Jeff suggests charging them an extra fee because they do the work themselves. | Jeff | 00:26:56 | |
| 52 | FACT | Online booking tool earns money through Sabre segment shares. | Mauricio | 00:27:10 | |
| 53 | FACT | Mauricio currently receives 50 percent of segment shares (linked to Winifred). Jeff suggests buying her out to capture more. | Jeff, Mauricio | 00:27:28, 00:27:41, 00:34:47 | |
| 54 | REQUIREMENT | Corporate site: the online booking tool can be given to clients like Missy or corporate travelers to book on their own. Bookings flow into the same system. | Mauricio | 00:27:51 | |
| 55 | IDEA | A dedicated hire monitors corporate accounts. Each incoming corporate booking gets a one-hour handling window. | Mauricio | 00:27:51 | |
| 56 | REQUIREMENT | Corporate self-bookings carry a fee, possibly automated. Mauricio suggests $5 to $10. Competitor Brian charges about $30. | Mauricio | 00:28:50 | |
| 57 | FACT | The fee is explicitly NOT meant to undercut Brian: "this isn't to undercut Brian because his clients are very different than our clients." Target is people who want to book on their own for a corporate company. | Mauricio | 00:28:50 | |
| 58 | FACT | Traverse handles Grit's group trips (pest control side) but captures none of Grit's individual travel. Some trips have 400 people. Grit is a hub for door-to-door sales; Aptiv uses Grit only partly, so Traverse will not get Aptiv trips. | Mauricio | 00:28:50 to 00:30:19 | |
| 59 | IDEA | Corporate travelers could self-change bookings (e.g. switch destination to Miami). | Jeff | 00:29:29 | |
| 60 | FACT | Revenue streams named: corporate booking fee, segment shares, and licensing the software to other travel agencies at a premium with paid add-ons. | Mauricio | 00:30:19 | |
| 61 | FACT | Competitor pricing: Trace subscription to do what Mauricio needs is about $2,000/year. Another vendor ("T", used by Traverse for a year) has over 10,000 subscribers at $100/month for the first five users plus $10 per additional user. Mauricio calls its software "horrible" but "a band aid that works." | Mauricio | 00:31:27, 00:31:53, 00:32:23 | |
| 62 | CONFLICT | Ambiguity within transcript: Mauricio says "over ten thousand subscribers and not ten thousand companies." Unclear whether 10,000 is users or companies, so the revenue math (Jeff: $200k/yr; Mauricio: about $1M/month) is unreliable. | Mauricio, Jeff | 00:31:53 to 00:32:46 | |
| 63 | IDEA | Software licensing is a numbers game. Licensed agencies could also route bookings through Traverse, so Traverse earns subscription fees and acts as the "Picasso" (host) for their transactions. Mauricio: "Yep, and we can do that through this software." | Jeff, Mauricio | 00:32:47 to 00:33:30 | |
| 64 | FACT | There are about eight or nine "Picasso" companies from Kansas to the West Coast. Term not verified. | Mauricio | 00:33:30 | |
| 65 | FACT | "This is a two-year rollout." Jeff ties this to buying out Winifred before rolling out the tech. Mauricio: "Yes and no." He wants revenue now. | Mauricio, Jeff | 00:33:30 to 00:33:55 | |
| 66 | FACT | Segment economics per Mauricio: currently 30 cents per segment. "Come January" it jumps to "our initial of two seventy," which he would negotiate "up to seven." Units not stated (likely dollars per segment, unconfirmed). This is framed around Winifred's earnings. | Mauricio | 00:33:55 | |
| 67 | IDEA | Partnership mechanic: half of Mauricio's 50 percent segment share from the online booking tool would go to the software build ("This feeds this"). | Mauricio | 00:34:47 | |
| 68 | FACT | Most build-out time is the back office. Jeff: "that's where my build out." | Mauricio, Jeff | 00:35:45, 00:35:50 | |
| 69 | QUESTION | Mauricio mentions another vertical but cannot remember it. | Mauricio | 00:35:53 | |
| 70 | FACT | [borderline] Traverse ownership: a silent partner owns 25 percent. One line of business is a 50/50 split with Winifred until she is bought out. Then a separate split funds the software. | Mauricio | 00:36:17 to 00:37:45 | |
| 71 | IDEA | [borderline] Funding via debt: a $30k to $40k credit card line. Traverse pays the card. The builder keeps the points. Segment-share revenue from the online booking tool pays the builder until the software is built. | Mauricio | 00:37:45 to 00:41:09 | |
| 72 | FACT | [borderline] Jeff's expenses are about $10k/month. Mauricio cannot pay $10k/month. | Mauricio, Jeff | 00:41:39, 00:43:04 | |
| 73 | FACT | Mauricio is pushing for 1,000 segments in December. He will have bookings built by others pulled into his Sabre so Traverse gets the segment credit. | Mauricio | 00:41:44 to 00:42:35 | |
| 74 | FACT | Traverse is on a Sabre "simple contract" (Mauricio paid a couple thousand dollars; it allows some ticketing). Hitting 1,000 segments in a month is the track record to move to a "subscriber contract," to renegotiate in January/February. | Mauricio | 00:43:05 to 00:45:01 | |
| 75 | FACT | Segment payments come quarterly, or monthly at 50,000 segments a year. These payments would partly fund the build. | Mauricio | 00:45:01 | |
| 76 | RISK | Sabre subscriber contract and higher segment rate depend on hitting 1,000 segments in December. Funding of the build depends partly on this. | Mauricio | 00:43:05 to 00:45:01 | |
| 77 | IDEA | Mauricio would put 25 to 50 percent of his segment-share income toward the build until it is built. | Mauricio | 00:43:05 | |
| 78 | IDEA | [borderline] Jeff proposes using his existing business credit card. Mauricio pays it as Jeff's compensation. Jeff would drop side work and focus 100 percent on the build. Mauricio says the number needs discussion and both sides must sacrifice. Not finalized. | Jeff, Mauricio | 00:46:02 to 00:46:47 | |
| 79 | RISK | Build pace is limited by Jeff's available time ("we can only go as fast as I have time"). | Mauricio | 00:41:09 | |
| 80 | FACT | [borderline] Both say they think they can do this, but Mauricio calls it "a major decision." No final agreement in this call. | Mauricio, Jeff | 00:47:29 to 00:47:45 | |

## Topics skipped (not booking)

Mauricio's views on working with Denise, a podcast Patreon aside, the silent partner's background (works at HP), and a closing joke about Jeff's wife doing bookings. Most partnership and equity detail is included above as [borderline] because it ties to funding the booking engine.
