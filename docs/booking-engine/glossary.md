---
title: "Booking Engine: Glossary"
project: Flight Bridge Booking Engine
status: Active
owner: Jeffrey Hammond
last_updated: 2026-10-07
source_transcripts: [SV, EM, FS, PP, R1205, M0610, M0924]
tags: [glossary, terms, people, booking-engine]
---

# Glossary

Terms, names and transcription quirks an agent needs to read the docs and digests.

## Industry terms

| Term | Meaning |
|------|---------|
| GDS | Global Distribution System, the airline inventory network (Sabre, Amadeus, Worldspan). Flight Bridge uses Sabre and will not build its own |
| Sabre | The GDS Traverse has direct access to. Transcripts also spell it "Saber", "Saver" |
| ARC | Airlines Reporting Corporation. An agency needs an ARC number to issue tickets and get paid. Bookings run under Traverse's ARC (DEC-BE-011) |
| PNR | Passenger Name Record, the booking record in the GDS. Transcripts sometimes say "PMR" |
| PCC | Pseudo City Code, an agency's identifier in Sabre |
| Segment / segment share | One flight leg. Sabre pays the agency per segment booked |
| Simple vs subscriber contract | Sabre contract tiers. Subscriber needs a 1,000-segment month and pays more |
| Host / "Picasso" | An agency with an ARC that books for agencies without one. "Picasso" is the transcript spelling |
| TAAP | Expedia's travel agent booking program |
| VAX | VAX VacationAccess, a package booking tool agents use |

## Agent vs agent

Jeff often says "agent" for an **AI agent**. Mauricio says "agent" for a **human booking agent** (EM 00:04:43). Docs here mean a human agent unless they say "AI agent".

## Companies and products

| Name | Who / what |
|------|------------|
| Flight Bridge | The platform company (50/50 Jeff and Mauricio). Transcripts also spell it "Flybridge", "FlightBridge" |
| Traverse / Traverse Tours | Mauricio's travel agency and the first Flight Bridge licensee. The SV transcript calls the whole effort "Traverse". Website flytraverse.com |
| Kit | The newsletter email platform (formerly ConvertKit), adopted 2026-09-24 (parent repo) |
| JourneyFuse | Agent CRM / proposal tool Traverse is moving to. Transcripts also say "Journey Fuse" |
| VCRM / VacationCRM | Older client CRM. Also "BCRM", "BC RM", "BCMM" in transcripts |
| Trace / Travify | Older itinerary and billing tool, being dropped |
| Victor / Viktor | AI tool Mauricio uses for flight tracking, fare watching and handling replies. Probably one tool (unconfirmed) |
| Grit | Corporate client. Traverse runs its group trips but not its individual travel. Transcripts also say "grip" |
| BK Marketing | Ben Knell's door-to-door company in Orem. Target client (BE-FB-009) |

## People

| Name | Role |
|------|------|
| Jeffrey (Jeff) Hammond | Partner. Builds the software |
| Mauricio Melendez | Partner. Runs Traverse travel operations and business development |
| Denise | Traverse staff. Assigns incoming leads to agents in the V1 flow |
| Missy | Group coordinator client (for example a 40-person dentist group to Ecuador). Books large hotel blocks |
| Winifred | Held the ARC under her name and received a pass-through. Transcripts also say "Winby" |
| Brian / Brian (Brandon) Dickerson | Competitor and partner in corporate travel. Uses SAP Concur. Possibly the same person (CONF-BE-009) |
