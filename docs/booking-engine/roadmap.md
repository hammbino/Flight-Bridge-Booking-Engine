---
title: "Booking Engine: Roadmap"
project: Flight Bridge Booking Engine
status: Needs Review
owner: Mauricio Melendez / Jeffrey Hammond
last_updated: 2026-10-13
source_transcripts: [SV, EM, PP, R1205, M0610, M0924, PARENT]
tags: [roadmap, booking-engine]
---

# Booking Engine Roadmap

**Read this first:** sources disagree on phase numbers and order (CONF-BE-004). This roadmap uses the **09-24 meeting's sequence** because it is the most recent. Every source agrees the newsletter comes first and the booking tool comes next. Confirm with Jeff and Mauricio (Q-BE-018) before treating phase numbers as fixed.

## Current Phase

**Phase 0: Foundation (pre-development).** No booking engine code exists. The newsletter free tier launched 2026-09-30 (PARENT). Phase 1 (Book Now lead capture) can start now that its routing is settled (Q-BE-010, resolved 2026-10-13; exact address in CONF-BE-011). Work needing Sabre or the ARC is on hold until the ARC transfer (DEC-BE-014, DEC-BE-015).

## Completed Milestones

- Direct Sabre access established for Traverse (SV 00:26:00)
- Sabre simple contract in place (SV 00:43:05)
- Booking business model outlined: segment shares, booking fees, agency hosting (SV, M0924)
- Newsletter free tier launched 2026-09-30 to 1,417 contacts. This is the traffic source for deal links (PARENT docs/ai/COMPLETED_TASKS.md)
- Booking Engine split into its own repo, 2026-10-07

## Upcoming Milestones

### Phase 1: Book Now lead capture (09-24 definition)
- [x] Settle where leads go: info@flytraverse.com (CONF-BE-007, 2026-10-12)
- [x] Settle who watches that inbox: Mauricio and his AI tool Viktor (Q-BE-010, 2026-10-13)
- [ ] Define the deal-link token schema (Q-BE-007)
- [ ] Build the lead form on the deal landing page (BE-FB-010, BE-FB-001)
- [ ] Verify submissions arrive end to end (IMP-BE-009)
- [ ] Track inquiries vs bookings (BE-FB-018), after the form works
- [ ] Live and tested before the pre-Black Friday sends, 2026-11-25 (IMP-BE-014)

Timing context: the newsletter Basic (flights) tier goes live the first week of November 2026 (PARENT DEC-NL-017). On 09-24 Jeff said a booking page should be up right after the newsletter launch (M0924 00:19:27). No date was set for Phase 1.

### Phase 2: Real booking on our landing page
- [ ] ARC transferred to Flight Bridge (DEC-BE-014, Q-BE-019). Estimated 2 to 4 weeks from 2026-10-08 (ASM-BE-014)
- [ ] Decide database (Q-BE-003) and Sabre method (Q-BE-004, BE-FB-013)
- [ ] Decide the payment path (MI-BE-006, CONF-BE-005)
- [ ] Consumer search and self-booking (BE-FB-003)
- [ ] Repricing when dates change (REQ-BE-009)
- [ ] Agent follow-up for every self-booking (BE-FB-012)
- [ ] Segment and revenue tracking (BE-FB-005)
- [ ] Internal agent pilot, 1 to 2 weeks, before wiring into the newsletter (BE-FB-011, DEC-BE-008)
- [ ] Wire deal links to the bookable page

No date set (Q-BE-009). On hold until the ARC transfer, and not ready for the November launch (DEC-BE-015). Mauricio hopes for January (ASM-BE-014).

### Phase 3: Corporate self-booking
- [ ] Corporate self-booking with fee (BE-FB-004)
- [ ] Target clients: Grit; BK Marketing (BE-FB-009)

### Phase 4: B2B (agency hosting and Concur-style product)
- [ ] Host agency access, "the Picasso, but better" (BE-FB-006)
- [ ] Agency onboarding instructions (REQ-BE-013)
- [ ] Concur-style B2B product (BE-FB-016)

Phases 3 and 4 are ordered from the old roadmap and DEC-BE-010. No source sets their order relative to each other.

## Unplaced: Sabre PNR / last-name import

BE-FB-002 sat in the old roadmap's Phase 1. R1205 puts Sabre record import in the CRM step, after the booking tool. Where it goes depends on Q-BE-008.

## Future Milestones (Aspirational)

- Full Sabre UI wrapper (BE-FB-007)
- Push bookings into an agency's Sabre, TAAP-style (BE-FB-014)
- Hotel booking (BE-FB-015)
- Premium experience packages (BE-FB-008)
- Proactive delay alerts and rebooking (BE-FB-019)
- Self-hosted AI fallback and on-prem add-on (BE-FB-017)
- VAX and other GDS sources (IMP-BE-002)

## Out of Scope

- Building a GDS (DEC-BE-001)
- Processing payments, for now (DEC-BE-005)
- Expense tracking, initially (DEC-BE-010)
- Buying out agencies (DEC-BE-004)
- Newsletter and CRM work (parent repo)

## Release Goals

- Phase 1: every newsletter deal has a working Book Now that reaches an agent
- Phase 2: first customer books on our page and gets an agent follow-up
- Phase 3: first corporate client's employees self-book
- Phase 4: first partner agency books through Flight Bridge

## Known Dependencies

- Phase 1 needs the newsletter's deal emails (parent repo) and the lead inbox, info@flytraverse.com, which Mauricio and Viktor monitor
- Phase 2 needs Sabre API access, a database decision and a payment path
- The Sabre subscriber contract depends on 1,000+ segments in a month (RISK-BE-001)
- Corporate self-booking needs corporate accounts in the CRM (parent repo)
- Agency hosting needs an access fee and commercial terms (Q-BE-011, MI-BE-005)

## Old phase numbering (parent repo, 2026-06-30)

Kept for traceability. The old roadmap had: Phase 1 deal landing page + PNR import + segment tracking; Phase 2 consumer self-serve; Phase 3 corporate portal; Phase 4 host agency; Phase 5 full Sabre wrapper. The current Phases 2 to 4 match old Phases 2 to 4. Old Phase 1 is split: the lead form is now Phase 1, the bookable landing page is Phase 2, and PNR import is unplaced.
