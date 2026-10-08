---
title: "Booking Engine: Competitive Landscape"
project: Flight Bridge Booking Engine
status: Active
owner: Mauricio Melendez / Jeffrey Hammond
last_updated: 2026-10-07
source_transcripts: [SV, EM, PP, M0610, M0924, PARENT]
tags: [competitors, market, booking-engine]
---

# Competitive Landscape (booking-relevant)

The full CRM competitor analysis is in the parent repo (`docs/crm/competitive-analysis.md`).

## Deal sites (consumer)

| Competitor | What it does | Gap Flight Bridge fills | Source |
|------------|--------------|-------------------------|--------|
| Flights From Home | Deal newsletter. Logged-in users filter by 6 departure cities. Deal page links to Google Flights with sample dates. Prices one traveler only. Uses Active Campaign | Does not book. Price can change by the time the user rebuilds the search. No person in the loop | EM 00:10:19 to 00:12:27, M0610 00:38:27 to 00:48:13 |
| Going | Deal site | Does not let users book | M0924 00:19:08 |
| Airline sites (Delta, American, United) | Built on GDSs | Deal sites send users here, losing the booking | M0924 00:20:35, 00:49:21 |

## Hosts and agency booking tools (B2B)

| Competitor | What it does | Source |
|------------|--------------|--------|
| Picasso | Host for agencies without an ARC. Client-facing as Picasso, owned by All Continents Travel (DBA). The model for "powered by" branding | M0924 00:46:04, M0610 01:08:53 |
| Skybird, Sky Travel | Hosts using their ARC for agencies | M0924 00:46:04, PP 00:11:20 |
| Centrav | Agents pay a monthly fee for its booking engine. The model for Flight Bridge's agency access fee | M0924 00:47:22 |
| Expedia TAAP | Travel agent booking. "GDS" button pushes a booking into the agent's Sabre by PCC/PNR | M0924 00:48:42 |
| SAP Concur (via Brian Dickerson) | Expense platform with travel. White-labeled. Books air, hotel and car. "Just a wrapper around the GDS". Microsoft Teams integration | M0924 00:26:57, 00:42:19 |
| Brian Dickerson | Corporate travel. Buys out small agencies over about 5 years. Moving into leisure | M0924 00:31:19 to 00:41:26 |
| Brian (competitor, SV) | Charges about $30 per booking. Different clients from Traverse. Possibly the same person as Dickerson (CONF-BE-009) | SV 00:28:50 |

## Agent tools (context)

| Tool | Booking-relevant point | Source |
|------|------------------------|--------|
| JourneyFuse | Traverse is migrating to it. AI itinerary import, branded proposals, click-to-accept with card capture. **No GDS integration and no booking engine tied in.** Also no expense tracking or QuickBooks | PP 00:02:46 to 00:05:20, M0924 00:42:55 to 00:43:23 |
| Trace / Travify | Sabre import needs an uploader on a virtual machine. Being dropped | SV 00:07:29, M0924 00:42:55 |
| UMAPped | Imported trips with just PNR and last name | SV 00:06:53 |
| We Travel | Processes payments by being the fiduciary on top of Stripe | SV 00:15:42 |

## Positioning summary

- Against deal sites: we book, and a real agent follows up (REQ-BE-010).
- Against hosts: easier and integrated, and agents book themselves (DEC-BE-004).
- Against JourneyFuse: Sabre integration and a booking engine (PP 00:05:38).
