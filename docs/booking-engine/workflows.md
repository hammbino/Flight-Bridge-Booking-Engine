---
title: "Booking Engine: Workflows"
project: Flight Bridge Booking Engine
status: Active
owner: Mauricio Melendez / Jeffrey Hammond
last_updated: 2026-10-13
source_transcripts: [SV, PP, M0610, M0924, M1008P]
tags: [workflows, booking-flow, booking-engine]
---

# Booking Engine Workflows

Step-by-step flows. IDs point to the requirement or decision behind each step.

## W1: Phase 1 Book Now (lead capture)

1. Subscriber gets a newsletter deal email (parent repo, Kit).
2. Clicks **Book Now** and lands on our deal page, not Google Flights or the airline (REQ-BE-011).
3. The form is prefilled with the deal (REQ-BE-008).
4. Optional: "my dates are different" opens a calendar. No new price is shown (REQ-BE-008, RISK-BE-006).
5. Enters traveler count, name and email. Contact is by email only (REQ-BE-008, M1008P L910-920).
6. Submission goes to info@traversetours.com (Jeff, 2026-10-12; address disputed, CONF-BE-011). Mauricio and his AI tool Viktor monitor it (Jeff, 2026-10-13). For now Viktor turns lead emails into JourneyFuse leads and assigns them to an agent (M1008P L920-926). Viktor is due to move to a Claude-based setup (RISK-BE-017). Leads are tagged to Flight Bridge in JourneyFuse (DEC-BE-016).
7. An agent contacts the customer, sends options, and books by hand in Sabre (DEC-BE-006).

**Status:** Agreed. Not built.

## W2: Phase 2 self-booking with agent follow-up

1. Subscriber clicks the deal and lands on our page, preloaded (REQ-BE-003).
2. Changes dates or times and sees prices update (REQ-BE-009).
3. Picks a flight and enters passenger details.
4. Payment step: **undecided** (MI-BE-006).
5. Ticket is issued under Traverse's ARC (DEC-BE-011).
6. The booking goes to an agent, who emails the itinerary ("White Glove Service") (REQ-BE-010).
7. Segment and source are recorded (REQ-BE-005).

**Status:** Agreed. Not built. Agents pilot it internally first (DEC-BE-008).

## W3: Corporate self-booking

1. A corporate client's employee books a one-off trip on the booking tool (REQ-BE-002).
2. A per-booking fee applies ($5 to $10 suggested).
3. The booking attaches to the corporate account (IMP-BE-005).
4. Traverse handles problems such as missed flights (R1205 00:03:27).
5. Idea only: a dedicated hire handles each corporate booking within an hour (SV 00:27:51).

## W4: Partner agency booking

1. An agency signs on and gets booking tool access and instructions (REQ-BE-013).
2. The agency's agent books directly, no phone call (M0924 00:47:15).
3. The booking runs under Traverse's ARC (DEC-BE-011).
4. Idea: push the booking into the agency's own Sabre by PCC/PNR (BE-FB-014).
5. The agency pays an access fee (DEC-BE-004).

## W5: Sabre PNR / last-name import (shared with the CRM)

1. The agent opens a client profile and picks "Import from Sabre".
2. Enters the PNR and passenger last name.
3. The system queries Sabre, and segments and passenger data populate a trip.
4. The agent reviews and confirms.

Source: SV 00:09:26; PARENT docs/crm/workflows.md Workflow 2. Ownership is open (Q-BE-008).

## Reference: the target booking UX (Continental shell)

From Mauricio's time at Continental Airlines (SV 00:10:23 to 00:11:47): enter origin, destination and dates on a calendar → submit → Sabre-like availability window → click segments to sell → hit price → take card → enter passenger info → hit ticket → enter client email → client gets confirmation. "That's what you want to see eventually."
