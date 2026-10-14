---
title: Source Digest - AI Agent Development, ARC Approval, Monetization (10-08 strategy)
project: Flight Bridge Booking Engine
status: Active
owner: Jeffrey Hammond / Mauricio Melendez
last_updated: 2026-10-13
source_transcripts: ["10-08 Meeting: FlightBridge Strategy on AI Agent Development, ARC Approval, and Monetization"]
tags: [source-digest, ai-agent, sabre, arc, fares, agency-subscription]
---

# AI Agent Development, ARC Approval, Monetization (10-08 strategy)

**Date:** 2026-10-08 (recording starts 18:12:58), later the same day as M1008P  **Participants:** Jeffrey Hammond, Mauricio Melendez
**Aliases:** "10-08 Meeting: FlightBridge Strategy on AI Agent Development, ARC Approval, and Monetization" (parent repo `Transcripts/`)
**Booking relevance:** Medium. Mauricio's fare-building skill as future AI-agent IP, ARC timing, and the booking engine as part of an agent subscription.

**How to cite:** no per-line timestamps and no speaker labels. Cite by line number in the raw file, for example `M1008S L38`. Speakers are inferred from context.

## Summary for agents

Mauricio gets lower fares in Sabre than airline or consumer sites show, by pricing each segment and combining one-way fares on different airlines into one reservation. The plan is to record how he works in the browser and use AI to build an agent that does the same. That agent becomes Flight Bridge IP for licensing to other agencies. The flight engine is paused until the ARC transfer, estimated at 3 to 4 weeks. They hope to have booking engines in place by January, and see agency subscriptions that include access to the engine.

## Points

| # | Type | Point | Who | Line | Quote (decisions only) |
|---|------|-------|-----|------|------------------------|
| 1 | FACT | In Sabre, Mauricio prices each segment and finds fares airline sites do not offer. Example: a group fare shown as $2,300 on the airline's site, booked for $1,600 each. | Mauricio | L2-13 | |
| 2 | FACT | Consumer systems rarely allow a "broken" fare (out on one airline, back on another). Google Flights may show it, but the customer books two separate reservations on two airline sites. In Sabre, both one-way fares go into one reservation. | Mauricio | L19-38 | |
| 3 | IDEA | Record Mauricio's browser actions with a tool like Playwright, have AI analyze the script, and build an AI agent that searches the way he does. It becomes Flight Bridge IP as the product goes to other agencies. Comes after the Sabre and ARC work. | Jeff | L14-18, L39-41 | |
| 4 | FACT | The flight engine is on pause until the ARC transfer. Mauricio estimates the ARC takes 3 to 4 weeks, because the main work (about six months) is already done. | Jeff, Mauricio | L66-72 | |
| 5 | ASSUMPTION | If things stay on track, booking engines will be working by January. | Mauricio | L83-85 | |
| 6 | IDEA | Once the flight engine runs, agents could pay a subscription that includes access to the Flight Bridge engine. | Jeff, Mauricio | L91-94 | |

## Topics skipped (not booking)

An education product idea ("Flight Bridge School"), its timing and pricing, and personal plans belong outside this repo.
