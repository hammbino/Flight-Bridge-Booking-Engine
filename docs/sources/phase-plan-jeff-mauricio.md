---
title: Source Digest - Jeff and Mauricio Phase Plan
project: Flight Bridge Booking Engine
status: Active
owner: Jeffrey Hammond / Mauricio Melendez
last_updated: 2026-10-07
source_transcripts: [Mauricio and Jeff Phase Plan-transcript.txt]
tags: [source-digest, phase-plan, build-sequence, sabre, arc, white-label, licensing, host-agency, competitors, journeyfuse, pci, offline-caching, ai-strategy, merchant-billing]
---

# Jeff and Mauricio Phase Plan

**Date:** Unknown (filename has no date)  **Participants:** Jeffrey Hammond, Mauricio Melendez (labeled "Speaker 1"; identified as Mauricio when Jeff addresses him by name at 00:23:33)
**Aliases (identical files in parent repo Transcripts/):** Mauricio and Jeff Phase Plan-transcript.txt
**Booking relevance:** High. This is the conversation that lays out the phase 0/1/2 build sequence, with the Sabre-integrated Flight Bridge booking tool as phase 1.

## Summary for agents
Jeff sets the phase plan. Phase 0 is an email campaign on Active Campaign with no booking engine; agents handle bookings by hand. Phase 1 is the Flight Bridge booking site ("like a Google Flights") for Traverse, using Traverse's ARC number and integrating with Sabre. Phase 2 is software that replaces VAX and Travify, includes merchant billing, and integrates with the booking tool. After that comes maintenance, then white-labeling the software to license to other agencies. Licensee agencies would still book flights through Flight Bridge under Traverse's ARC, so Flight Bridge earns on both licensing and flight bookings. A possible phase 4 is AI. Mauricio also walks through a competitor CRM (likely JourneyFuse, name uncertain) whose quote-to-booking flow he likes, but it has no GDS integration.

## Points
| # | Type | Point | Who | Time | Quote (decisions only) |
|---|------|-------|-----|------|------------------------|
| 1 | FACT | In the new CRM tool Mauricio is testing, credit card info is stored per trip, not per client profile. The vendor told him this. | Mauricio | 00:00:00 | |
| 2 | ASSUMPTION | Mauricio thinks the per-trip card storage is for PCI compliance. He believes profile-level storage (the way "VCM" does it) can also be PCI compliant. | Mauricio | 00:00:32 | |
| 3 | REQUIREMENT | Storing client card data needs to be covered in Flight Bridge's terms and conditions, accepted when the client creates an account. Jeff frames it as "our security and how we're setting up our security." | Jeff | 00:00:49 | |
| 4 | FACT | Current agent workflow: build a proposal in VAX, email it to self, clean it up, upload everything to Travify, send the client a Travify link. If accepted, collect client info, enter it in VCRM, then enter it in whatever booking portal is in use. Any client change means redoing the whole process from VAX. | Mauricio | 00:01:05 | |
| 5 | FACT | Competitor feature: agent copies the itinerary page from VAX and pastes it into the tool. An "AI export" parses hotel, airfare and other parts into a quote white-labeled for Traverse ("Travers" in transcript). | Mauricio | 00:02:46 | |
| 6 | FACT | Jeff says Travify has a similar import feature. Mauricio says in Travify he must copy airfare from Sabre and paste it in. The new tool can also take pasted Sabre airfare, but its advantage is importing a whole itinerary at once. | Jeff, Mauricio | 00:03:31 | |
| 7 | FACT | Competitor feature: pulls in vendor images automatically. Supports up to three option comparisons sent as one link. When the client clicks accept, a form opens for card info and all passenger info, which the client submits. | Mauricio | 00:03:34 | |
| 8 | FACT | Competitor feature: leads move automatically through pipeline stages (lead, then proposal, and onward) as they progress. Mauricio can view where each agent's clients sit in the customer journey. [borderline] | Mauricio | 00:04:22 | |
| 9 | FACT | The competitor tool has no GDS integration. | Mauricio | 00:05:20 | |
| 10 | REQUIREMENT | Flight Bridge's own tool must integrate with Sabre. Mauricio says this is what allows it to connect to a booking tool. | Jeff, Mauricio | 00:05:38 | |
| 11 | DECISION | Jeff needs a breakdown of the tools in use: what Mauricio likes, what he does not like, and what he needs. The competitor tool is to be used as a template for likes, dislikes and modifications. | Jeff | 00:06:05 | "I need a breakdown of what we're using, what we like about what we're using, what we don't like about what we're using" |
| 12 | FACT | The competitor tool replaces both VCRM and Travify for Mauricio. He removed Travify billing and nobody noticed for about two weeks. [borderline] | Mauricio | 00:06:15 | |
| 13 | IDEA | Long term, build this capability in-house so Flight Bridge does not pay for a third-party program. | Jeff | 00:07:12 | |
| 14 | DECISION | Phase 0 is an email campaign on Active Campaign. No flight booking agent is built for it. Subscribers contact Mauricio's agents, who handle everything manually. Building a custom CRM is deferred. | Jeff, Mauricio agrees | 00:07:12 | "phase one is email campaign, and we're not building that with a flight booking agent" |
| 15 | FACT | Jeff first called the email campaign "phase one", then corrected it to "phase zero" (00:08:58). Numbering below uses his corrected scheme. | Jeff | 00:08:58 | |
| 16 | DECISION | Phase 1 is the Flight Bridge booking site where people book their own flights, "like a Google flight," specifically for Traverse, using Traverse's ARC number and integrating with Sabre. | Jeff | 00:08:58 | "Phase one is uh the flight bridge. The landing where people can book their own flights like a Google flight, but specifically for Traverse using our ARC number" |
| 17 | DECISION | Phase 2 is software that replaces VAX and Travify, includes merchant billing, and integrates with the booking tool ("We expand our booking agent and they're integrated"). | Jeff, Mauricio agrees | 00:08:58 | "phase two is, a software that takes the place of Vax and Travify merchant includes merchant billing" |
| 18 | CONFLICT | Phase 2 "includes merchant billing." This may conflict with DEC-BE-005 (Flight Bridge will NOT act as a payment processor for flight bookings, from "Strategic Vision for a Unified Travel Management Platform"). The transcript does not say whether merchant billing covers flights or only VAX-style package bookings. | Jeff | 00:08:58 | |
| 19 | DECISION | After phase 2 the product goes into maintenance, and the plan is to white-label the software and license it to other agencies. | Jeff | 00:09:39 | "we're in maintenance, and we're trying to white label the software also. So that we can license it to others" |
| 20 | IDEA | Go-to-market for the licensed software: big travel trade shows (e.g. "travel mart") and getting in with the three top consortiums, which then push it to their agents. [borderline] | Mauricio | 00:10:08 | |
| 21 | DECISION | Licensee agencies would still book flights under Traverse's ARC. The ARC part is not white-labeled. Revenue comes from licensing plus flights booked through the Flight Bridge tool. | Jeff, Mauricio agrees | 00:10:48 | "they would be using RARC still correct We're not trying to white label that part." |
| 22 | FACT | Jeff states most travel agencies book vacations but typically do not handle flights. | Jeff | 00:10:59 | |
| 23 | FACT | At that point Flight Bridge becomes an air host, comparable to Picasso and Skybird. Consistent with DEC-BE-004. | Mauricio | 00:11:20 | |
| 24 | ASSUMPTION | Mauricio projects Flight Bridge alone could reach eight to nine figures gross. No basis given. | Mauricio | 00:11:46 | |
| 25 | ASSUMPTION | Each phase (0, 1, 2) can generate revenue on its own. | Mauricio | 00:14:29 | |
| 26 | QUESTION | How much AI should the product include? Mauricio does not know; he says the industry has not figured out what to do with it. | Jeff | 00:12:36 | |
| 27 | IDEA | Offer agencies an add-on: a local machine with an AI model installed behind their firewall, to address data privacy concerns ("PPI" in transcript, likely PII). | Jeff | 00:13:23 | |
| 28 | RISK | Fast-moving market. A competitor could beat Flight Bridge to market. | Jeff | 00:15:02 | |
| 29 | FACT | Competitor CRM pricing: $25 per person. Mauricio said "No" when Jeff asked if it was per month per user and just gave "the rate per person", so the billing period is not confirmed. AI included in the subscription, no usage cap. It is web based. Mauricio does not think it works offline. Jeff calls it "vCRM ... vacation client retention management", but Mauricio later names the company "Journey? Fuse" (00:19:57). The tool's actual name is uncertain. | Mauricio | 00:16:43 | |
| 30 | DECISION | Travelers (end users) must be able to cache their trip and flight info so they keep it in an airport with no internet. Done via browser cache or a native app. Agent-side offline mode is not needed. | Jeff, Mauricio agrees | 00:18:27 | "Strictly we want users to be able to cache their trip information, flight information and things like that." |
| 31 | FACT | Sabre does not work offline. | Mauricio | 00:18:23 | |
| 32 | RISK | AI providers are losing money (Jeff cites about $1.69 cost per $1 spent). Unlimited token pricing will likely end, which could raise cost or break AI features built on a third-party API. | Jeff | 00:18:27 | |
| 33 | ASSUMPTION | Jeff guesses the competitor CRM runs AI through a white-labeled third-party API on a pro subscription, and would break if that access were cut. | Jeff | 00:21:43 | |
| 34 | DECISION | AI approach: start building on a hosted API (Claude/Anthropic subscription mentioned), and quickly build a self-hosted model server as a fallback, possibly switching before any provider change. | Jeff | 00:22:08 | "we could start building it with the open API with the cloud subscription into it. And just know that we need to very quickly work on building the alternatives" |
| 35 | ASSUMPTION | Local AI is the future for small and medium businesses. Travel use cases (scraping travel pages, generating images, organizing content) need small models and few tokens. | Jeff | 00:22:08 | |
| 36 | FACT | Jeff has outside developers who offered to help if the team needs to scale quickly (e.g. to stand up the AI fallback fast). | Jeff | 00:23:44 | |
| 37 | DECISION | Phase plan has three, maybe four phases. The possible fourth phase is AI. AI is not a focus now but should be kept in mind while building. | Jeff, Mauricio | 00:24:24 | "our phase plan, We've got three, maybe four phases right now, the fourth phase being. Uh, the AI portion of it." |
| 38 | ASSUMPTION | Jeff thinks keeping AI in mind will not add much build time. | Jeff | 00:25:01 | |
| 39 | DECISION | Plan heavily before building. Record conversations and store them, because better docs mean faster, cheaper AI-assisted coding with fewer iterations. | Jeff | 00:25:31 | "The more we can plan before we start to build, the better." |
| 40 | DECISION | Next steps: launch Active Campaign next week. Then hold a recorded session on the tools Mauricio uses (likes, dislikes, how he sees them working) with screenshots for reference. | Jeff | 00:25:31 | "let's get the active campaign going next week. And, then let's have another conversation where we're talking about the tools" |
| 41 | RISK | The hardest part will be the back end: migrating data and connecting all backend pieces so they work and do not break. Jeff expects the front end to go fast. | Jeff | 00:26:01 | |
| 42 | RISK | Apps built quickly with AI often do not manage context, caching or data correctly, making them slow and expensive. Jeff cites this as the failure mode to avoid. | Jeff | 00:26:36 | |
| 43 | FACT | Working style agreed: ship when it works, fix as you go. Note: the transcript labels the line "That's why I need you, Jeff. Push it" as Jeff speaking, but the content suggests Mauricio or a labeling error. Attribution uncertain. | Jeff / Mauricio (uncertain) | 00:28:26 | |

## Topics skipped (not booking)
Active Campaign email details beyond phase placement, AI token economics and Anthropic subscription history, an exit-strategy anecdote about a friend's software and Ford, industry ownership demographics, and personal chat about acquaintances (Thomas Doxetter, Dan Dunn, Seth Hood) and their apps.
