---
title: "Booking Engine: Sibling Product Dependencies"
project: Flight Bridge Booking Engine
status: Active
owner: Jeffrey Hammond / Mauricio Melendez
last_updated: 2026-10-14
source_transcripts: [EM, SV, M0610, M0924, PARENT]
tags: [dependencies, newsletter, crm, interfaces, parent-repo]
---

# Sibling Product Dependencies

The booking engine is one of three Flight Bridge products. The other two, the **Newsletter** and the **CRM**, are documented in the parent repo (`/Users/jeffrey/Sandbox/Flight-Bridge`, folders `docs/newsletter/` and `docs/crm/`). This file records every place the booking engine depends on them or they depend on it. Cited `-NL-` and `-CRM-` IDs live in the parent repo. Read them there for full detail. Do not edit them here.

Snapshot taken 2026-10-07. If a parent-repo ID below looks stale, re-read the parent repo before acting.

---

## 1. Newsletter → Booking Engine

### 1.1 Deal links land on a booking-ready page (core interface)

- **What the newsletter expects:** every deal email links to a booking engine landing page, pre-populated with the deal and editable by the subscriber. Token-based URL parameters carry the deal context.
- **Parent IDs:** REQ-NL-004, DEC-NL-002, NL-FB-005 (token system: route, dates, price), RISK-NL-005 (links break if the URL structure changes; mitigation is a stable, versioned token schema).
- **Booking engine IDs:** REQ-BE-003, REQ-BE-007, BE-FB-001.
- **Open:** the token schema has not been defined. See Q-BE-007. Draft proposal in `deal-links.md` (2026-10-13).
- **Source:** EM 00:00:00

### 1.2 Interim booking flow until the engine exists

The booking engine is not built yet. Until it is, newsletter bookings go through people.

| Flow | How it works | Status | Parent IDs |
|------|--------------|--------|-----------|
| V1 contact form | Deal email → landing page form prefilled with the deal → "my dates are different" calendar and traveler count (no repricing) → customer picks call or email → generic inbox → Denise assigns an agent (superseded: now email only, to an inbox Mauricio and Viktor monitor) → agent books by hand in Sabre | Agreed 2026-06-10 | DEC-NL-011, NL-FB-013, Q-NL-010, RISK-NL-008 |
| Deal Alerts reply | Subscriber replies to the alert email → Traverse confirms the fare is live and books it. Handled by Mauricio's AI tool "Viktor" | Resolved as intentional 2026-09-30. Who monitors replies day to day is still open | CONF-NL-005 |
| JourneyFuse packages | VIP package deals only: customer clicks Book on a JourneyFuse proposal page → JourneyFuse captures card and passenger info → agent books by hand | Idea / Phase 2 in the 06-10 sequence | NL-FB-014 |

**Out of date in the parent (checked 2026-10-13):** the V1 contact form row still routes leads to a generic inbox where Denise assigns an agent. That is no longer the plan. Book Now leads now go to info@flytraverse.com, which Mauricio and Viktor monitor (Q-BE-010, resolved 2026-10-13). The parent IDs still saying Denise are DEC-NL-011, NL-FB-013, Q-NL-010, RISK-NL-008 and the launch-plan tasks for the deal contact form. They were updated in the parent on 2026-10-13. No form exists yet (confirmed by Jeff 2026-10-14).

Booking engine relevance: the V1 form fields (deal prefill, date change, traveler count, contact preference) are the minimum the booking engine's deal landing page must also handle. Agents must use the booking engine internally for at least one to two weeks before it is wired into the newsletter (DEC-BE-008).

**Source:** M0610 00:47:33 to 00:54:01; PARENT CONF-NL-005

### 1.3 Tier timing drives booking volume

- Free tier launched 2026-09-30. Basic (flight deals) is planned to go live the first week of November 2026. VIP (packages) is planned for early December 2026. Parent ID: DEC-NL-017. The 10-08 Black Friday plan proposes selling VIP over Black Friday weekend, with a package deal on 2026-11-30 (PARENT DEC-NL-029, proposed).
- Flight-only deals (Basic) are expected to move to the booking engine most easily. Packages (VIP) still need agents. See DEC-BE-007.
- **Source:** M0924 00:54:33, M0924 00:59:40, M0610 00:33:33

### 1.4 Branding on customer-facing pages

- Customer-facing pages, including the booking landing page, use "Traverse Tours powered by Flight Bridge". Flight Bridge is strictly a platform company with no consumer brand. Parent ID: DEC-NL-009.
- Live Traverse Tours pages (Kit landing page, built 2026-09-26 to 2026-10-06) use slate teal `#4E6A6C` / `#4E6A6A`, sage `#8FA9A0` / `#66857B`, cream text `#F2EEE6`, Fraunces headings and Instrument Sans body. The real logo comes from flytraverse.com's image CDN.
- Flight Bridge brand guide (for the "powered by" mark): Jet Black `#0B0B0D`, Forest Green `#10A85B`, Dark Slate `#1A1F24`, Stone `#E5E7EB`, Sand `#CFC7B5`; fonts Montserrat / Inter.
- **Uncertainty:** in the 06-10 meeting Jeff described the Flight Bridge colors as "navy, royal blue and green-blue", which does not match the later brand guide. The brand guide is newer. Confirm before using.
- **Source:** M0610 01:08:21, M0610 01:09:19; PARENT `docs/ai/KNOWN_ISSUES.md` (landing page passes 1 to 3, 2026-09-26 to 2026-09-29). See also CONF-BE-010 and `ui-notes.md`.

### 1.5 Revenue attribution

Flight Bridge earns a percentage of anything booked from the newsletter. The booking engine must track booking source, including newsletter referral (REQ-BE-005). Mauricio also wants to know which subscribers ask for information and which ones book. He placed this after the V1 flow (REQ-BE-012).

**Source:** M0610 00:48:22, M0610 01:12:42

---

## 2. CRM ↔ Booking Engine

### 2.1 Sabre PNR / last-name import (shared feature)

- The same capability is tracked in both products: the agent enters a PNR and last name, and all segments populate a trip record. There is no virtual-machine uploader.
- **Parent IDs:** REQ-CRM-004, DEC-CRM-003, CRM-FB-004 (depends on Q-BE-004).
- **Booking engine IDs:** BE-FB-002, DEC-BE-001.
- **Ownership is not decided.** Build it once and decide which product owns it. See Q-BE-008.
- **Source:** SV 00:06:53, SV 00:09:26

### 2.2 Shared technical decisions

- **Database (SQL vs NoSQL)** is open for both products. Booking ID: Q-BE-003. The CRM roadmap says this decision must come before all CRM Phase 1 work.
- **Sabre API method** is open for both. Booking ID: Q-BE-004. CRM PNR import is blocked on it.

### 2.3 Corporate accounts

- The corporate booking portal (REQ-BE-002, BE-FB-004) needs corporate accounts such as Grit to exist in the CRM, so bookings and fees attach to an account (IMP-BE-005).
- The CRM roadmap lists employee self-booking as out of scope for the CRM and says it is "the Booking Engine's domain".

### 2.4 Payments

- Neither product processes payments for now (DEC-BE-005). The CRM captures card authorization only, through a no-login link tied to the trip. Parent IDs: CRM assumptions and Workflow 3 in `docs/crm/workflows.md`.

### 2.5 Competitor gap the booking engine fills

JourneyFuse, the CRM Mauricio moved to, has no Sabre integration and cannot book live. Jeff: "if we can do that then it can open the door because it allows it to be integrated with a booking tool." Parent ref: `docs/crm/competitive-analysis.md`.

---

## 3. Build order across products

Sources disagree on the order and numbering of phases across the three products. This is recorded in CONF-BE-004. Short version:

| Source | Order |
|--------|-------|
| Phase Plan transcript / parent CRM and newsletter roadmaps | Newsletter (Phase 0) → Booking Engine (Phase 1) → CRM (Phase 2) → white-label (Phase 3) |
| 06-10 meeting | V1 contact form → JourneyFuse (Phase 2) → Flight Bridge booking engine (Phase 3) → CRM (Phase 4) |
| Strategic Vision transcript | CRM + client portal + agent back end with PNR import first; online booking tool named the first revenue play |
| 09-24 meeting | Phase 1 Book Now = lead form → Phase 2 = real booking on our page. Order: newsletter → booking tool → Concur-style B2B |
