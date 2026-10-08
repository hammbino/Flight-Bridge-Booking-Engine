---
title: Source Digest - Financial Structure and Payment Processing
project: Flight Bridge Booking Engine
status: Active
owner: Jeffrey Hammond / Mauricio Melendez
last_updated: 2026-10-07
source_transcripts: ["05-22 Meeting Flight-Bridge_ Financial Structure, Credit Cards, and Payment Processing-transcript.txt", "Financial_Structure"]
tags: [source-digest, arc, revenue-flow, payment-processing, stripe, merchant-account, traverse]
---

# Financial Structure and Payment Processing

**Date:** 05-22  **Participants:** Mauricio Melendez (only labeled speaker), Jeffrey Hammond (his replies are merged into Mauricio's turns)
**Aliases (identical files in parent repo Transcripts/):** "05-22 Meeting Flight-Bridge_ Financial Structure, Credit Cards, and Payment Processing-transcript.txt", "Financial_Structure" (alias differs only by extra blank lines)
**Booking relevance:** Medium. It explains how ARC revenue reaches Flight Bridge and sets the plan of Stripe first, then a regular merchant account. Most of the rest is company finance.

## Speaker attribution note
Every turn is labeled "Mauricio Melendez", but Jeff's short replies ("Yeah", "Okay", "Gotcha") are clearly mixed in. Substantive statements below are attributed to Mauricio. Where a line reads like Jeff, that is noted.

## Summary for agents
ARC is held under Winifred's name for now, because she got ARC for them. Winifred runs the ARC report, Mauricio sends her money per transaction, and she passes half to Flight Bridge. Per the arrangement, she is out in October and the money stops going through her. ARC revenue is small for now ("a couple dollars" a week) and is expected to grow a lot once "Grit" starts traveling. For payments, Flight Bridge will start with a FlightBridge Stripe account, said in the context of the email product. It will move to a regular merchant account later to cut fees, and that will deposit straight into the Flight Bridge account. A company credit card cannot be run through the company's own merchant account. So Jeff's monthly pay is charged through Traverse's merchant account instead. (Traverse is Mauricio's existing agency, per parent-repo docs.)

## Points
| # | Type | Point | Who | Time | Quote (decisions only) |
|---|------|-------|-----|------|------------------------|
| 1 | FACT | Winifred runs the ARC report. Example: for 20 transactions Mauricio sends her $20, she sends $10 to Flight Bridge, and the partners split that. Read literally, that is $1 per transaction to Winifred and $0.50 to Flight Bridge. The per-transaction unit is inferred from the example only. | Mauricio | 00:00:00 | |
| 2 | FACT | Winifred sends money to Flight Bridge because ARC is still under her name. She got ARC for them, and that is part of Mauricio's agreement with her. | Mauricio | 00:00:00 | |
| 3 | FACT | "The whole October thing": starting in October the money no longer goes to her, and she is no longer involved. The year is not stated. | Mauricio | 00:00:29 | |
| 4 | QUESTION | Who holds ARC after Winifred leaves in October? Does Flight Bridge get its own ARC number, or does it run under Traverse? Not discussed. | (unresolved) | 00:00:29 | |
| 5 | FACT | ARC income is small right now, "every week it's a couple dollars". It becomes "a lot of money" once "Grit starts to travel". Who or what "Grit" is is not explained. It may be a client or group, or a transcription error. | Mauricio | 00:00:29 | |
| 6 | DECISION | ARC income stays in the account. No owner draws unless the partners talk first. [borderline] | Mauricio | 00:01:00 | "We're not doing draws unless we talk to each other, so who cares? It just stays there anyway." |
| 7 | FACT | Flow: Winifred sends Mauricio the report, he sends her the money, and she transfers money "from Win B" over to Flight Bridge. The transcript is garbled here ("from the PED drugs that she sent me the report"). The meaning is not certain. | Mauricio | 00:01:00 | |
| 8 | FACT | Jeff's monthly $2,500 is charged on a card through the Traverse merchant account. The amount is grossed up for fees (about $2,540 to $2,560). It lands in Traverse's account, moves to Flight Bridge, then goes by ACH to Jeff's business checking. [borderline] | Mauricio | 00:02:57 | |
| 9 | FACT | Jeff currently takes payments at Nerd Hero by ACH or Venmo. (Jeff speaking.) [borderline] | Jeff (merged into Mauricio label) | 00:01:58 | |
| 10 | DECISION | Start with a FlightBridge Stripe account, set up along with the email product. | Mauricio | 00:03:56 | "for the email, when we set up the email, we'll get a FlightBridge Stripe account to start out." |
| 11 | DECISION | Later, move from Stripe to a regular merchant account to pay less in fees. Flight Bridge "will have to get" its own merchant account in the future. | Mauricio | 00:03:56 | "But then we're going to transition over to a regular merchant account. Because then we're not paying as much in fees." |
| 12 | FACT | The future Flight Bridge merchant account deposits straight into the Flight Bridge bank account. | Mauricio | 00:04:26 | |
| 13 | RISK | A FlightBridge credit card cannot be charged on a FlightBridge merchant account. Card networks see it as "loaning against yourself". This is why Traverse's merchant account is used for the card charges. | Mauricio | 00:04:26 | |
| 14 | IMPLIED | Seems to imply that payment processing for bookings should not be locked to Stripe, since a move to a merchant account is planned. Stripe was only stated for the email product. Nothing was said about which processor takes booking payments. | Mauricio | 00:03:56 | |
| 15 | RISK | Stripe is the starting processor here, but only for the email product. Other Flight Bridge material (the We Travel competitor notes in the parent repo) records that Stripe will not process travel payments directly because the industry has high chargebacks. Extending this Stripe account to flight or package bookings may not be possible. | Mauricio | 00:03:56 | |
| 16 | CONFLICT | The Stripe plan here is "a FlightBridge Stripe account". Later decision: the newsletter runs on Kit, with billing through Kit Commerce (DEC-NL-014). An amendment dated 2026-09-26 records that Kit Commerce always provisions its own Kit-managed Stripe Express sub-account. Newsletter billing therefore does not run through the original FlightBridge Stripe account, so two Stripe accounts now exist. This affects which Stripe account any booking payments would use. | Mauricio | 00:03:56 | |
| 17 | FACT | Agency trips (destination visits, hotels, spas, concierge) are largely expensable (Mauricio relaying a talk with Brian Dickerson), because agents need to know the experience to relay it to customers. This was said in a business-expense context. It ties loosely to experience content for premium packages. [borderline] | Mauricio | 00:08:17 | |

## Completeness note
The recording appears to stop mid-conversation. The file ends at "it takes forty eight hours." Later discussion may be missing.

## Topics skipped (not booking)
Choosing a company credit card (Amex Gold or Platinum versus Capital One, and credit reporting), airport lounge perks, partner reward trips twice a year with wives and families, personal remarks about other people, and fixing Winifred's name on the Utah corporate registration (corporations.utah.gov, $14 fee, 48-hour processing).
