# Decisions

Short list for quick context. Full entries with reasoning and sources are in `docs/booking-engine/product-decisions.md`. Do not reopen these unless asked.

- **Sabre, never our own GDS.** Start with Sabre behind the scenes; a full wrapper is "eventually". DEC-BE-001
- **ARC.** All bookings, including partner agencies', run under Traverse's ARC. DEC-BE-011
- **No payment processing for now.** Card details captured by link, not charged. DEC-BE-005
- **Phase 1 = lead capture.** Book Now opens a prefilled form that goes to a human agent. DEC-BE-006
- **Phase 2 = real booking on our page,** with repricing on date change and agent follow-up ("White Glove Service"). DEC-BE-009
- **Flights first.** Flight-only deals move into the engine first; packages stay with agents. DEC-BE-007
- **Internal pilot.** Agents use the engine 1 to 2 weeks before it is wired into the newsletter. DEC-BE-008
- **Build order.** Newsletter, then booking tool, then a Concur-style B2B product. No expense tracking initially. DEC-BE-010
- **Agencies.** "The Picasso, but better": paid Centrav-style access, no buy-outs. DEC-BE-004
- **AI.** Hosted API first, self-hosted fallback soon. DEC-BE-013
- **Branding.** "Traverse Tours powered by Flight Bridge". PARENT DEC-NL-009

Needs review: DEC-BE-002 (corporate fee), DEC-BE-003 (revenue framing), DEC-BE-012 (agents and the fee portal).
