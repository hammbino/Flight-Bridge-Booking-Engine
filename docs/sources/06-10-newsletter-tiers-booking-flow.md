---
title: Source Digest - Newsletter Tiers and Deal Booking Flow (06-10)
project: Flight Bridge Booking Engine
status: Active
owner: Jeffrey Hammond / Mauricio Melendez
last_updated: 2026-10-07
source_transcripts: ["06-10 Weekly Meeting_ Newsletter Content Strategy, Subscription Tiers, and Booking Flow-transcript.txt"]
tags: [source-digest, booking-flow, deal-booking, lead-form, agent-assignment, journeyfuse, phasing, sabre, ai-deal-generation, branding, newsletter-handoff]
---

# Newsletter Tiers and Deal Booking Flow (06-10)

**Date:** 06-10  **Participants:** Jeffrey Hammond, Mauricio Melendez, unidentified "Speaker 2" (short interjections only)
**Aliases (identical files in parent repo Transcripts/):** 06-10 Weekly Meeting_ Newsletter Content Strategy, Subscription Tiers, and Booking Flow-transcript.txt
**Booking relevance:** High. The second half defines how a newsletter subscriber books a deal, a phased path from a lead form to JourneyFuse to the Flight Bridge booking engine, and agent assignment via Denise.

## Summary for agents
This meeting sets how a newsletter reader turns into a booking. Version 1 has no self-serve booking. The deal links to a landing page with a form, prefilled from the deal. The customer can change dates, give the traveler count and choose call or email. The form goes to a generic email that Denise reviews and assigns to an agent. Phase 2 adds JourneyFuse so package deals can be booked through a JourneyFuse page, with an agent still doing the actual booking. Phase 3 is the Flight Bridge booking engine, built on top of Sabre. It opens prefilled from the deal and lets the customer change dates, see pricing and book. Agents should use it for a week or two before it is wired into the newsletter. Phase 4 is the CRM. Flight deals are expected to move into Flight Bridge more easily than packages, which still need agents. AI (GPT, possibly Claude later) generates the deals, and a human reviews them before they are published. The branding is "Traverse Tours powered by Flight Bridge", with Flight Bridge kept as a pure platform company.

## Points
| # | Type | Point | Who | Time | Quote (decisions only) |
|---|------|-------|-----|------|------------------------|
| 1 | FACT | Today a customer who wants a destination deal has to contact Traverse and an agent, "because we do not have a flight bridge up." The deal draws interest, then the customer contacts Traverse and Traverse calls or emails them back. | Jeff | 00:17:01 | |
| 2 | FACT | Mauricio showed a ChatGPT project that searches Google Flights, Kayak and other sites. It produced pricing for a sample August 4-8 trip, including flight/hotel price ranges. | Mauricio | 00:18:47, 00:19:49 | |
| 3 | IDEA | Deals for the newsletter are AI-generated from that search output. Jeff confirmed: "you have AI generate the deal that goes in newsletter." | Jeff, Mauricio | 00:21:40 | |
| 4 | FACT [borderline] | Jeff said deal sourcing does not matter much ("You're just doing it through Google Flights or through whatever, because we don't care. Because we can match it."). This implies Traverse can match publicly found fares. Not explained further. | Jeff | 00:15:08 | |
| 5 | IDEA | Jeff wondered whether agents could be set up to log in to the various tools Traverse has. Not resolved. | Jeff | 00:15:08 | |
| 6 | IDEA | VIP deals could come from several origin airports, for example Salt Lake City and Los Angeles, so more deals can be found. A sample AI search was SLC to Paris for July to October 2026. | Mauricio | 00:27:41 | |
| 7 | FACT | Jeff raised whether all deals would originate from SLC and called it "the hard part." | Jeff | 00:27:33 | |
| 8 | IDEA | One speaker said they might exclude Frontier. The speaker is unclear: the transcript labels it "Speaker 2". | Speaker 2 | 00:28:27 | |
| 9 | DECISION | AI-generated deals must be reviewed by a person before they are published. How the review is routed (a Claude draft, an email) was left open. | Jeff, Mauricio | 00:29:41 | "So, we would want these to be reviewed before published right? Yeah" |
| 10 | FACT | A published deal shows available dates and a price, for example seven days in August for about $850 round trip. Those may not be the customer's dates. That gap is where an agent calls them. | Mauricio, Jeff | 00:30:21, 00:30:32 | |
| 11 | FACT | Mauricio expects the deal funnel could bring in booking revenue within about a week of launch ("They'll sign up, they'll book."). | Mauricio | 00:32:50 | |
| 12 | DECISION | Flight-only deals (Basic tier) will move to Flight Bridge more easily once it is running. Flight plus destination packages will still need to go through travel agents. | Jeff, Mauricio | 00:33:33 | "Then the basic tier funnels easier to flight bridge when it's up and running. Yep" |
| 13 | REQUIREMENT | The newsletter needs a "to book one of these, click here" link, not just booking instructions. | Mauricio | 00:37:45 | |
| 14 | FACT | Competitor Flights From Home does not book. It gives instructions and sends the user to Google Flights with the search parameters filled in. It prices for one traveler only, so the user has to change the search on Google Flights, and by then the price may have changed. | Mauricio, Jeff | 00:38:27 to 00:48:13 | |
| 15 | DECISION | Eventually the booking link goes to a Flight Bridge landing page, not Google Flights. The transcript reads "our RSC" here; it may be a mistranscription. | Jeff | 00:38:57 | "instead of going to Google Flights, we would go through our landing page with our RSC. Yep." |
| 16 | FACT | The differentiator against Flights From Home is that Traverse has a real person (an agent) in the loop. | Mauricio | 00:48:13 | |
| 17 | FACT | In Travify, Jeff can build a destination or trip and share a bookable link, for example on social media. | Jeff | 00:39:50 | |
| 18 | FACT | JourneyFuse demo: an agent builds a trip and generates a generic shareable link showing all trip details, such as the hotel. The customer can continue to book or type a question. The trip creator gets an email about the question. | Mauricio | 00:40:55, 00:41:30 | |
| 19 | FACT | Jeff called the JourneyFuse link "a better flow for the customer." | Jeff | 00:41:26 | |
| 20 | FACT | JourneyFuse has "AI import." In the demo, Jeff and Mauricio pasted the GPT output into JourneyFuse by hand ("we were the middleman"). Jeff said a destination may need to exist in JourneyFuse before import works. | Jeff, Mauricio | 00:42:17 to 00:45:45 | |
| 21 | REQUIREMENT | The LLM (now GPT, "probably" Claude later) needs to talk to JourneyFuse so trips are created automatically. An MCP server would work if JourneyFuse has one. | Jeff | 00:40:30, 00:43:53 | |
| 22 | QUESTION | Can JourneyFuse auto-generate packages and send them back? What web API, webhooks and MCP does it offer? Mauricio did not know. Jeff: "we have to dig into it." | Jeff, Mauricio | 00:41:45 to 00:45:29 | |
| 23 | IMPLIED [borderline] | Jeff said that when the CRM is built, "we would need this capability" (a client-bookable link generated from LLM output). This implies the in-house system eventually replaces JourneyFuse's link feature. Not stated as a requirement. | Jeff | 00:46:28 | |
| 24 | DECISION | Version 1 booking flow: newsletter email, then a form on a landing page, then an agent. The agent takes over the conversation and sends options back. | Mauricio, Jeff | 00:48:22 | "I want it to go from email to form landing page. Okay. To agent" |
| 25 | REQUIREMENT | The V1 form is prefilled with the deal's details. | Jeff | 00:47:33 | |
| 26 | REQUIREMENT | The V1 form has a "my dates are different" option that opens a calendar for the customer's own dates. | Mauricio | 00:47:37 | |
| 27 | REQUIREMENT | The V1 form asks how many people are traveling (unlike Flights From Home, which is one person only). | Mauricio | 00:47:58 | |
| 28 | FACT | V1 form does not show a new price when the customer changes dates. Mauricio confirmed "No" when Jeff asked. | Jeff, Mauricio | 00:47:53 | |
| 29 | DECISION | V1: the customer chooses whether to be contacted by phone or email. The form has both options. | Jeff, Mauricio | 00:50:14 | "Version one, we're just going to have an agent contact them... They decide. Call me or email me." |
| 30 | DECISION | V1: the form is sent to a generic email inbox. | Jeff, Mauricio | 00:50:14 | "that goes to our email. Yeah... it just goes to the generic email at that point, though, yes." |
| 31 | DECISION | V1 agent assignment: Denise reviews the form email and assigns it to an agent. No cherry-picking by agents. | Jeff, Mauricio | 00:50:54 to 00:51:14 | "It would just go to Denise and she'd assign it out somebody." |
| 32 | REQUIREMENT | Back-end tracking: know which email subscriber is asking for information and which ones book. Mauricio said this comes after the V1 flow is done. | Mauricio | 00:48:22 | |
| 33 | DECISION | Phase 2 is JourneyFuse. The customer clicks Book and goes to the JourneyFuse page. Comments or questions go to Denise, who assigns an agent to contact them. | Jeff, Mauricio | 00:51:52, 00:54:01 | "Phase two is we get journey fuse, so then the customer can click book, and it'll go to that page." |
| 34 | FACT | JourneyFuse self-booking is meant for package deals, for example a Disney family package with set dates. The customer submits all their information. The agent gets a notification and books it by hand using the collected card details. | Mauricio | 00:49:25, 00:53:43 | |
| 35 | DECISION | JourneyFuse packages apply only to VIP packages. Flights stay on the form-to-agent path until Flight Bridge exists. | Jeff | 00:52:30 | "That's only for the VIP packages. The flights right now would be a form that go to an agent" |
| 36 | DECISION | Phase 3 is the Flight Bridge booking engine. Phase 4 is the CRM. The order of phases 2 and 3 was debated, then settled as JourneyFuse first, because JourneyFuse needs much less work. | Jeff, Mauricio | 00:52:22, 00:54:01 | "So phase two is Journey, phase three is Flight Bridge, and then phase four is CRM. Yeah, okay." |
| 37 | REQUIREMENT | The Flight Bridge booking engine opens prefilled from the deal, not Google Flights. The customer can change dates, see the updated options and book. | Jeff, Mauricio | 00:52:55, 00:53:05 | |
| 38 | QUESTION | How feasible is it to have the Flight Bridge booking engine as phase 2, and how long would it take? Mauricio: "I just don't know what the feasibility is." The order was set without answering this. | Mauricio | 00:53:22 to 00:53:26 | |
| 39 | FACT | "Flight Bridge is just built on top of Sabre." Agents would book through Flight Bridge instead of Sabre directly. | Jeff, Mauricio | 00:54:01 | |
| 40 | DECISION | Agents must use Flight Bridge internally for at least a week or two before it is connected to the newsletter or mailer system. | Jeff, Mauricio | 00:54:01 | "we would want at least a week or two or more with the agents using Flight Bridge before we put this into put it into the mailer system. Yep" |
| 41 | FACT | CRM is last because, by then, the earlier pieces "will have been worked out." | Mauricio | 00:54:44 | |
| 42 | FACT [borderline] | Tier structure that affects which deals feed booking: Free gets info content plus a teaser of last week's VIP flight deal and package deal. Basic (paid) gets multiple flight deals in one email. VIP gets package deals at least once a week, as available. Pricing mentioned: about $49/yr (Basic, early example), $99/yr (example). Mauricio once proposed only Free and VIP. They ended with three tiers. | Jeff, Mauricio | 00:25:39 to 01:05:09 | |
| 43 | IDEA | Long term, building deals and packages moves from agents to automation: a cron job (a timed script trigger) plus a human reviewer. Jeff pointed to the JourneyFuse demo as proof. He said no VA would be needed. | Jeff | 01:06:11 | |
| 44 | IDEA | The deal reviewer could be a Traverse agent spending 2-3 hours a week. Or a separate person paid about 10% commission on bookings who never talks to clients. Other agents handle clients. | Mauricio, Jeff | 01:06:41 to 01:07:41 | |
| 45 | FACT [borderline] | Agent commission at Traverse is about 20-25%. Mauricio said it went to 20% and was then boosted. The exact current figure is unclear in the transcript. | Jeff, Mauricio | 01:06:59 | |
| 46 | DECISION | Branding: "Traverse Tours powered by Flight Bridge" on emails and on the landing page customers reach. | Jeff, Mauricio | 01:09:19, 01:10:28 | "So it's going to be Traverse powered by Flight Bridge. Yeah, okay." |
| 47 | DECISION | Flight Bridge is strictly a platform company. No public Flight Bridge website is needed right now. A logo is needed for the "powered by" mark. | Jeff, Mauricio | 01:10:28 | "so we want FlightBridge strictly to be platform. Yeah, it's gonna be a platform company." |
| 48 | FACT | The model for this branding is Picasso: client-facing as Picasso, owned by All Continents Travel (DBA). | Mauricio | 01:08:53 | |
| 49 | FACT [borderline] | Mauricio expects that once ARC is in place and "Winifred's out" (no more ties to "Winby"), everything becomes Flight Bridge. Customers who already saw "powered by Flight Bridge" will find the transition easier. The names Winifred and Winby may be mistranscribed. | Mauricio | 01:09:33 | |
| 50 | IDEA | White-labeling later, at the CRM level, also as "Traverse powered by Flight Bridge." | Mauricio, Jeff | 01:10:17, 01:10:28 | |
| 51 | FACT [borderline] | Flight Bridge earns a percentage of anything booked from the newsletter. Example: Clark's Holy Land tours pay a commission and are high value. | Mauricio | 01:12:42, 01:13:18 | |
| 52 | ASSUMPTION [borderline] | Conversion estimate from the existing client list: about 4,000-5,000 emails, about 1% to the free newsletter (about 40), about 1% of those (about 4) to VIP. Stated as a rough guess. | Jeff, Mauricio | 00:56:34 to 00:57:05 | |
| 53 | FACT [borderline] | Flight Bridge brand colors are navy, royal blue and green-blue, with whites, blacks and grays. Jeff warned these could clash with Traverse branding. | Jeff | 01:08:21 | |
| 54 | RISK | Customers may change dates on the V1 form without seeing a price. The original deal price may not hold, and the agent has to follow up. Mauricio noted the same problem with Flights From Home. This is derived from points 14, 26 and 28. It was not stated as a risk. | Mauricio, Jeff | 00:47:53 to 00:48:13 | |
| 55 | CONFLICT | Booking phase numbering here (V1 form, Phase 2 JourneyFuse, Phase 3 Flight Bridge, Phase 4 CRM) does not match the parent repo's booking-engine roadmap (Phase 1 is the deal landing page MVP, Phase 2 is consumer self-serve). It also does not match the newsletter docs (Newsletter Phase 0, Booking Engine Phase 1, CRM Phase 2). JourneyFuse as a phase before Flight Bridge does not appear in the booking-engine roadmap. | n/a | 00:52:22, 00:54:01 | |
| 56 | CONFLICT | Jeff asked "Do we want phase three to be journeyfuse? In phase two, to be flight bridge" and said "We do. We want that to be phase two If. We can." Minutes later he settled it as JourneyFuse phase 2 and Flight Bridge phase 3. This is resolved within the transcript, but the Flight Bridge-first preference was conditional on feasibility. | Jeff | 00:52:30, 00:53:05, 00:54:01 | |

## Topics skipped (not booking)
Newsletter content format (destination highlight, travel tip, info section), the first launch/announcement email, sign-up landing page design (email-only, minimum barrier), Beehiiv as the list tool and the vCRM CSV export for a one-time opt-in campaign, tier naming brainstorm, ChatGPT project settings and context-window tips, merch and logo on hats, Chase/MACU bank accounts, Zelle, owner draws and the Profit First accounting policy.
