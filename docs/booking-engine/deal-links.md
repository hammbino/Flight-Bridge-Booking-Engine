---
title: "Booking Engine: Deal Link Format (Draft Proposal)"
project: Flight Bridge Booking Engine
status: Draft
owner: Jeffrey Hammond
last_updated: 2026-10-13
source_transcripts: [EM, M0610, M0924, PARENT, M1008P]
tags: [deal-links, tokens, newsletter, kit, phase-1, proposal]
---

# Deal Link Format (Draft Proposal)

**Status:** a draft for Jeff to review. Nothing here is decided. It answers Q-BE-007 once Jeff picks the open items in section 5. Until then, no decision or requirement is created from it.

Fields and rules marked **sourced** come from a transcript or the parent repo. Fields and rules marked **proposal** were added in a working session on 2026-10-13 and have no source behind them yet.

---

## 1. What a deal link has to do

| Need | Sourced or proposal | Source |
|------|---------------------|--------|
| Open the deal page with the deal already filled in | Sourced | M0610 00:47:33, REQ-BE-003, REQ-BE-008 |
| Carry route, dates and price | Sourced | PARENT NL-FB-005 |
| Keep working after it is sent, since sent emails cannot be changed | Sourced | RISK-BE-007, PARENT RISK-NL-005 |
| Work in Kit emails | Sourced | PARENT DEC-NL-007 |
| Work when shared on social posts, not only in email | Implied, not confirmed | IMP-BE-010 (EM 00:16:23) |
| Support package deals as well as flights | Proposal. The Black Friday plan sends a package deal on the Monday after Black Friday (M1008P L1304-1307), so package links may be needed by late November 2026. A flight-only format would need a second version within weeks. Deal types are not settled (EM, digest point 14). | M1008P; PARENT DEC-NL-017; EM |

## 2. Where links point (open item)

**Proposal:** every deal link points at a domain Flight Bridge or Traverse controls. It never points straight at a third-party form tool.

**Why:** the parent launch plan suggests a hosted form (Google Forms or Tally) for the interim flow. That is labeled a proposal, not a decision (PARENT launch-plan, deal contact form task). Each form tool uses its own prefill parameter names. If emails link straight to one, switching tools breaks every link already sent. A link on our own domain can forward to whatever form or page exists at the time. The tool can then change without breaking old emails.

**Not known:** which domain hosts deal pages. The docs name flytraverse.com as Traverse's website (glossary) and info@traversetours.com as the lead inbox (Q-BE-010). Neither is recorded as the home for deal pages. See section 5, item 1.

## 3. Proposed link format (v1)

```
https://<deal-domain>/deal/<deal-id>?v=1&type=flight&from=SLC&to=CUN&depart=2026-11-14&return=2026-11-21&price=289
```

| Parameter | Meaning | Example | Sourced or proposal |
|-----------|---------|---------|---------------------|
| `<deal-id>` (in the path) | A stable ID for the deal. Lets Phase 2 look the deal up later instead of trusting the link. | `2026-11-slc-cun` | Proposal |
| `v` | Format version. Lets the format change later without breaking old links. | `1` | Proposal, from the versioning need in RISK-BE-007 |
| `type` | `flight` or `package` | `flight` | Proposal |
| `from`, `to` | Route, as airport codes | `SLC`, `CUN` | Sourced (route: PARENT NL-FB-005). Airport codes are a proposal. |
| `depart`, `return` | Dates, as YYYY-MM-DD. `return` is left out for one-way deals. | `2026-11-14` | Sourced (dates: PARENT NL-FB-005). Date format is a proposal. |
| `price` | Price per person shown in the email, in USD | `289` | Sourced (price: PARENT NL-FB-005). Per person and USD are proposals and need confirming. |

**Package deals:** what a package link must carry is not known. Until it is, a `type=package` link carries only the deal ID and a short title (`title=`). The agent gets the rest from the deal ID.

## 4. Rules the page follows (proposal)

1. **The price in the link is for display only.** Anyone can edit a URL. In Phase 1 that is harmless, because an agent quotes the real price. **Phase 2 must never charge or confirm a price taken from the link.** It looks the deal up by ID and reprices through Sabre (REQ-BE-009).
2. **Missing or broken fields never block the customer.** If a field is missing or unreadable, the form shows it blank and the customer fills it in. A bad link must still produce a lead.
3. **Unknown parameters are ignored.** That way tracking tags (for example UTM tags), or a later `v=2` field, do not break the page.
4. **Every submission records the full link it came from.** The agent can then see exactly what the customer saw.
5. **Test the link before every send** (existing mitigation in RISK-BE-007).

## 5. Open items for Jeff

These come in order. Each one changes what follows.

1. **Which domain do deal links use?** This decides what the link looks like and who controls it. The rest of the format does not depend on the answer.
2. **Should links also fill in the subscriber's own name and email?**
   - *For:* the customer only confirms their details and taps submit. Fewer steps means more leads.
   - *Note:* contact is email only (M1008P L910-920), so the form needs the email address either way.
   - *Against:* email addresses end up inside URLs. That means they show up in server logs, browser history and forwarded emails. It only works in email, not on social posts (IMP-BE-010).
   - *How it would work in Kit:* Kit supports Liquid in links, with the `url_encode` filter for email addresses ([Kit help: Advanced Email Personalization with Liquid](https://help.kit.com/en/articles/2502501-advanced-email-personalization-with-liquid)). Kit says links containing Liquid cannot be edited after the broadcast is sent ([Kit help: Change a URL after sending an email](https://help.kit.com/en/articles/3437318-change-a-url-after-sending-an-email)). This has not been tested in a real send.
3. **What does a package deal link need to carry?** This can wait until the VIP tier is closer, as long as v1 reserves `type=package`.
4. **Is the price per person, and always in USD?**

## Related

- Q-BE-007 (the question this answers), REQ-BE-003, REQ-BE-008, BE-FB-001, BE-FB-010
- RISK-BE-007 (sent links breaking), IMP-BE-010 (social sharing)
- PARENT NL-FB-005, RISK-NL-005, DEC-NL-007, DEC-NL-017
- `sibling-dependencies.md` section 1.1
