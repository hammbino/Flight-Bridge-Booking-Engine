---
title: "Booking Engine: UI Notes"
project: Flight Bridge Booking Engine
status: Active
owner: Jeffrey Hammond
last_updated: 2026-10-07
source_transcripts: [SV, M0610, M0924, PARENT]
tags: [ui, branding, design, booking-engine]
---

# UI Notes

## Branding on customer pages

- Customer pages read **"Traverse Tours powered by Flight Bridge"**. Flight Bridge is strictly a platform, with no public Flight Bridge consumer site (M0610 01:09:19, 01:10:28; PARENT DEC-NL-009).
- Match the live Traverse Tours pages already built for the newsletter (PARENT docs/ai/KNOWN_ISSUES.md, 2026-09-26 to 2026-10-06):
  - Slate teal `#4E6A6C` / `#4E6A6A` (header band, backgrounds), sage `#8FA9A0` / `#66857B` (accents, buttons), cream text `#F2EEE6`
  - Fraunces headings, Instrument Sans body
  - Traverse's real logo file from the flytraverse.com image CDN (1920x476 transparent PNG, white text plus teal icon, meant for a dark band). Never a cropped screenshot.
- "Powered by Flight Bridge" mark: a small badge cropped from the Flight Bridge brand guide. Brand guide colors: Jet Black `#0B0B0D`, Forest Green `#10A85B`, Dark Slate `#1A1F24`, Stone `#E5E7EB`, Sand `#CFC7B5`; Montserrat / Inter. Older color description disagrees (CONF-BE-010).
- Before building any customer-facing page, pull real brand assets from flytraverse.com. Do not ship template styling, stock photos, or made-up testimonials or stats. This is a standing rule from Jeffrey (memory: brand matching).

## Copy

- CTA copy says exactly what happens. Phase 1 is a request, so a label like "Book Now" should make clear an agent will follow up.
- "White Glove Service" is agreed language for why to book through Traverse (M0924 00:23:19). Not an adopted brand name.

## Booking page behavior

- Deal preloaded from the link. Editable (REQ-BE-003).
- Phase 1: date change opens a calendar, with no repricing. Show that an agent will confirm price (RISK-BE-006).
- Phase 2: Google Flights-style date spread with live prices (REQ-BE-009).
- Traveler count on every deal (Flights From Home prices one traveler only, which is a known pain point) (M0610 00:47:58).
- No account required (REQ-BE-007).

## Known UX pitfalls from competitors

- Search returning blank because of hidden default filters (Trace/Travify) (SV 00:01:31).
- Sending users off-site to book (Flights From Home, Going) (M0610 00:38:27, M0924 00:19:08).
