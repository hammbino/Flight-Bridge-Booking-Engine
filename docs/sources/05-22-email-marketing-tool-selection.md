---
title: Source Digest - Email Marketing Strategy and Tool Selection
project: Flight Bridge Booking Engine
status: Active
owner: Jeffrey Hammond / Mauricio Melendez
last_updated: 2026-10-07
source_transcripts: ["05-22 Weekly Meeting Flight-Bridge_ Email Marketing Strategy, Tool Selection, and Monetization-transcript.txt", "JeffandMauricio.md.md", "email_marketing_strategy_tool_selection_and_monotization"]
tags: [source-digest, deal-landing-page, booking-flow, email-to-booking, build-sequence, competitors, flights-from-home, ai-agents, social]
---

# Email Marketing Strategy and Tool Selection

**Date:** 05-22  **Participants:** Jeffrey Hammond, Mauricio Melendez
**Aliases (identical files in parent repo Transcripts/):** "05-22 Weekly Meeting Flight-Bridge_ Email Marketing Strategy, Tool Selection, and Monetization-transcript.txt", "JeffandMauricio.md.md", "email_marketing_strategy_tool_selection_and_monotization" (the two aliases are byte-identical to each other and differ from the dated file only by extra blank lines)
**Booking relevance:** High. It sets the core rule that a marketed deal opens a Flight Bridge booking page ready to pay but still editable. It also ranks the booking engine as the second revenue lever after the email list.

## Summary for agents
Jeff states the core flow. A deal in an email or marketing piece links straight to a Flight Bridge booking landing page that is "ready to pay now" but can still be changed, like a regular booking engine. The open technical question is how to pass tokens from the email so the landing page arrives pre-filled. Mauricio names the two fastest revenue levers: the email list (MRR) first, then the booking engine, with the email list sending people to the booking engine. They look at Flights From Home as the reference competitor. They discuss two deal-creation workflows, one started by a human booking agent and one by AI agents. They agree social posts carry free-tier deals with two links: "Book now" and "Join email list" (premium). The target is an email campaign live by the end of June. The tool choice (Active Campaign, Go High Level, or custom-built with Claude) is left open.

## Points
| # | Type | Point | Who | Time | Quote (decisions only) |
|---|------|-------|-----|------|------------------------|
| 1 | REQUIREMENT | Marketing content must link back to Flight Bridge. Clicking a deal takes the user straight to Flight Bridge "ready to pay now", but in a state that can still be modified and edited, "just like a regular booking engine". | Jeff | 00:00:00 | |
| 2 | QUESTION | How do we set up tokens in the email so that the Flight Bridge landing page arrives with everything pre-set? Jeff says "we have explore", meaning this still needs to be explored. | Jeff | 00:00:00 | |
| 3 | FACT | No email tool (such as Active Campaign) is in use at this point. | Jeff | 00:00:00 | |
| 4 | FACT | VacationCRM has an email component, but Mauricio says "it sucks". Active Campaign was robust in his past use. Mailchimp "wouldn't work for this". He compared them a couple of years ago, and they may have changed since. | Mauricio | 00:00:46 | |
| 5 | QUESTION | Can Flight Bridge be run through Go High Level, along with a CRM and AI marketing tools? It needs exploring. Jeff wants to go "as fast as humanly possible". [borderline] | Jeff | 00:01:35 | |
| 6 | FACT | Mauricio ranks the lowest-hanging revenue: first the email list (MRR), then the booking engine. The email list will send people to the booking engine. | Mauricio | 00:02:02 | |
| 7 | DECISION | Sequence the work by those two verticals: the email list first, then the booking function. Go quickly but not at "lightning speed". This is a soft agreement (Mauricio proposes, Jeff says "Okay"). | Mauricio | 00:03:49 | "We look at the email list. And then we look at the uh booking function." |
| 8 | FACT | The customer email list already exists in VacationCRM. | Mauricio | 00:02:43 | |
| 9 | FACT | Trade-off stated by Jeff: going fast is probably expensive, and going cheaper is probably slower. | Jeff | 00:03:25 | |
| 10 | FACT | Terminology clash: when Jeff says "agent" he means an AI agent. When Mauricio says "agent" he means a human booking agent on the team (example: Denise). Docs should say which one is meant. | Jeff | 00:04:43 | |
| 11 | IDEA | Mauricio's deal workflow: a human booking agent (e.g., Denise) builds the special or booking and emails it to an address like specials@flightbridge.com. The email tool's AI then builds the email and visual and sends it to the right campaign or list. | Mauricio | 00:04:57 | |
| 12 | IDEA | Jeff's deal workflow: an AI agent finds the deal and passes it to content-generator AI agents. They build it out to match the customer profile, then send it to the matching demographic. | Jeff | 00:05:30 | |
| 13 | IDEA | Tag CRM contacts by destination interest (examples: Cartagena, Colombia, beach, South America) to route deals. Everyone would have to be tagged by hand. [borderline] | Mauricio | 00:05:58 | |
| 14 | QUESTION | Deal types are not settled. There are "airfare specials", "package specials" and possibly more, and Mauricio says he gets "lost in the weeds". This affects what a deal landing page must support. | Mauricio | 00:07:14 | |
| 15 | FACT | Flights From Home (competitor): logged-in users filter deals by departure city. It serves only six cities, including Salt Lake City and Las Vegas. Users can also filter domestic or international and show points or deals. | Mauricio | 00:10:19 | |
| 16 | FACT | A Flights From Home deal page shows a description, the deal, "how to book", and a link to Google Flights with sample dates. It sends the user away to book, rather than booking on its own site. Example deals mentioned (00:11:08): 13,000 Southwest points to California, Miami $259 round trip. | Mauricio | 00:11:39 | |
| 17 | IDEA | Jeff: "So we need a landing page for the email flights from home website." The wording is unclear. It may mean Flight Bridge needs a deal landing page like Flights From Home's. | Jeff | 00:10:15 | |
| 18 | ASSUMPTION | Jeff thinks Flights From Home gets its deals by scraping: "You have a bot that's just putting in the flags and pulling them up." This is a guess, not confirmed. | Jeff | 00:12:11 | |
| 19 | FACT | Flights From Home uses Active Campaign. | Mauricio | 00:12:27 | |
| 20 | IDEA | Three options to seriously evaluate: custom-built (have Claude build it), Active Campaign, or Go High Level. Go High Level can run "upwards of two grand a month" depending on tier, and Active Campaign is "around two hundred a month". Jeff says Claude is "so freaking fast". [borderline] | Jeff | 00:12:30 | |
| 21 | RISK | The hard part of a custom build is the back end. Jeff's example: someone built a landing page whose form sent submissions nowhere, so no data was captured. | Jeff | 00:13:39 | |
| 22 | IMPLIED | Seems to imply that every booking or deal landing page form must actually store or route what it captures. Not stated as a requirement. | Jeff | 00:13:39 | |
| 23 | DECISION | Free-tier deals may also go on social media. Paid (premium) deals must not go on social, so premium keeps its value. [borderline] | Jeff | 00:15:59 | "We don't want to send the paid messaging or deals on social, because then people will be like, oh, why am I paying?" |
| 24 | DECISION | Social deal posts carry two links: "Book now" and "Join email list". The email list link points to the premium (upgraded) list, not the free tier. | Jeff | 00:16:23 | "we could have two links on this social: 'book now,' 'join email list.'" |
| 25 | IMPLIED | Seems to imply that each deal needs a shareable "Book now" URL that works from social posts as well as from email. Not stated as a requirement. | Jeff | 00:16:23 | |
| 26 | DECISION | Target: an email campaign up and running by the end of June. The booking engine comes after, per point 7. [borderline] | Jeff | 00:17:12 | "We want an email campaign up and going by the end of June." |
| 27 | CONFLICT | The tool choice here is Active Campaign versus Go High Level versus custom. Later decision: the final newsletter platform is Kit (formerly ConvertKit), DEC-NL-007, adopted 2026-09-24 when they switched from Beehiiv. Active Campaign was never adopted. One older parent-repo roadmap still says "Phase 0 = Newsletter (Active Campaign)", which is stale. Whatever passes tokens from email to the booking page must work with Kit, not Active Campaign. | Jeff / Mauricio | 00:12:30 | |

## Completeness note
The recording appears to be cut off. The file ends mid-sentence ("if we need to do.") during the banking talk. Later discussion may be missing.

## Topics skipped (not booking)
Free versus premium email frequency (free gets one deal a week plus a "specials you missed" list, premium gets about four or five a week), preventing a spammy feel through targeting, a story about a contact's landing page and his business partner, and banking (Mountain America, Chase, keeping two banks).
