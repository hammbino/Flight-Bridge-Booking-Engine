---
title: "Book Now Launch: Design"
project: Flight Bridge Booking Engine
status: Needs Review
owner: Jeffrey Hammond
last_updated: 2026-10-13
source_transcripts: [M0610, M0924, M1008P, EM, PARENT]
tags: [spec, phase-1, book-now, deal-links, kit, launch]
---

# Book Now Launch: Design

**Status:** for Jeff's review. Nothing is built until he approves this document.
**Target:** live by end of day Wednesday 2026-10-14.

## 1. Goal

A subscriber opens this week's free deal email, clicks **Book Now**, and lands on a Traverse-branded page with the deal already filled in. They add their details and submit. The request arrives as an email at **info@flytraverse.com**, where Mauricio and Viktor pick it up.

**Done means:** a real Kit test email to Jeff, clicked on a phone, produces a request that Mauricio confirms he received at info@flytraverse.com. Then the deal email goes out to subscribers with Mauricio's approval.

## 2. Scope

**In (scope B, agreed 2026-10-13):**
- The Book Now page and form
- The deal-link format and a simple way to make a link each week
- Hosting at `deals.flight-bridge.com/traverse-tours/`
- Requests emailed to info@flytraverse.com
- This week's first free deal email in Kit, with a working Book Now button
- An end-to-end test

**Out:** the bookable engine (on hold until the ARC transfer, DEC-BE-015), Black Friday setup in Kit, list growth, the Viktor-to-Claude move.

## 3. Choices made, and why

Each was compared against at least two others. The rule: the cheapest option that does the whole job, as long as it stays simple, easy and repeatable.

| Choice | Picked | Compared against | Why |
|--------|--------|------------------|-----|
| Lead inbox | info@flytraverse.com | info@traversetours.com | It is the address on Traverse's website. traversetours.com belongs to an unrelated company (CONF-BE-011). |
| Link domain | `deals.flight-bridge.com/traverse-tours/` | `deals.traversetours.flight-bridge.com`; `book.flytraverse.com`; a page inside the Duda site | Jeff controls flight-bridge.com. One setup serves every future agency (new agency = new folder). `traversetours.flight-bridge.com` is excluded because it carries the newsletter's email records. |
| Form and page | Our own page + Web3Forms | Tally free; Tally Pro ($29/mo); Formspree; Fillout; Google Forms; Kit; Beehiiv | The only $0 option that keeps Traverse branding, keeps the customer on our domain, and emails each request to any inbox. Web3Forms Pro (~$12/mo, 10,000 a month) is the upgrade if needed. Formspree's free tier (50 a month) is too small for Black Friday. |
| Hosting | GitHub Pages | Cloudflare Pages; Netlify | $0, Jeff is already signed in to GitHub here, and publishing is a `git push`. It needs a public repo, which is fine: the page holds no secrets (the Web3Forms key is designed to be public). |
| Making a weekly link | A small link-builder page next to the Book Now page | Hand-editing a template link; a Google Sheet formula | Mauricio or Jeff types the deal into boxes and copies the link. No URL editing, no accounts, hard to get wrong. |

## 4. How it works for the customer

1. The deal email shows this week's deal with a **Book Now** button.
2. The button opens `deals.flight-bridge.com/traverse-tours/?v=1&deal=...`.
3. The page shows the deal: route, dates, price per person, branded "Traverse Tours powered by Flight Bridge".
4. The customer enters: number of travelers, name, email. An optional **My dates are different** box opens two date pickers. No new price is shown.
5. They press **Send my request**. The page shows a thank-you: an agent will email them.
6. Web3Forms emails the request to info@flytraverse.com.
7. Viktor sees the lead and creates it in JourneyFuse. An agent replies by email (email only, no phone).

If the link is missing details or broken, the page still works. The deal box is just left out, and the customer can say what they want in a short "Which deal?" field. Every request still produces a lead.

## 5. The pieces

**5.1 Book Now page.** One HTML file with its style and a little script, in folder `traverse-tours/`. Colors, fonts and logo come from Traverse's live brand (the Kit page set in PARENT DEC-NL-028: `#4E6A6A`, `#F2EEE6`, `#66857B`, Fraunces and Instrument Sans), checked against flytraverse.com during the build. It works on a phone first, since most people open email on a phone.

**5.2 Link builder.** `traverse-tours/build.html`. Boxes for: deal ID, flight or package, from, to, depart date, return date, price. It shows the finished link with a Copy button and a "Test this link" button.

**5.3 Hosting and domain.** A new public GitHub repo (`flight-bridge-deals`) published with GitHub Pages. One DNS record in GoDaddy: `deals` CNAME to `hammbino.github.io`. HTTPS is turned on in GitHub Pages.

**5.4 Form service.** Web3Forms free plan. The access key is created for info@flytraverse.com, so the key arrives in that inbox once. Spam protection: Web3Forms' hidden honeypot field.

**5.5 The request email.** Subject: `Book Now request: SLC to CUN, Nov 14 to 21 (Jane Doe)`. The body lists every field, plus the full link the customer came from (REQ-BE-008, `deal-links.md` rule 4). Reply-to is set to the customer's email, so an agent can just hit Reply (confirm during the build that Web3Forms does this). Whether Viktor recognizes it as a lead is unknown until the test (section 8).

**5.6 This week's deal email.** A Kit broadcast in the existing "Text only" template: the featured destination content (REQ-NL-002 format), this week's deal, and the Book Now button. Mauricio approves before it sends (DEC-NL-013).

## 6. Link format (v1)

```
https://deals.flight-bridge.com/traverse-tours/?v=1&deal=2026-10-slc-cun&type=flight&from=SLC&to=CUN&depart=2026-11-14&return=2026-11-21&price=289
```

This follows `deal-links.md` with one change: the deal ID moves from the path into `deal=`. A plain static host serves one page per folder, so a path like `/deal/<id>` would need extra setup for no gain. `deal-links.md` will be updated to match. Price is display only. Phase 2 must never charge from it.

## 7. Weekly checklist (repeatable)

1. Mauricio approves this week's deal.
2. Open the link builder, fill in the deal, copy the link.
3. Paste it as the Book Now button link in the Kit email.
4. Send a Kit test to yourself, click the button on a phone, check the deal shows correctly.
5. Mauricio approves, then the email is scheduled.

New agency later: copy the `traverse-tours/` folder, change logo, colors and inbox key.

## 8. Tomorrow (Wed 2026-10-14)

| When | Who | Step |
|------|-----|------|
| Morning | Mauricio | Sends this week's deal: route, dates, price, plus the destination content or approval for Claude to draft it |
| Morning | Mauricio | Creates the Web3Forms key for info@flytraverse.com (or forwards the key email) |
| Morning | Claude | Builds the page and link builder, creates the repo, publishes to GitHub Pages |
| Morning | Jeff | Adds the `deals` CNAME in GoDaddy (Claude gives the exact values) |
| Midday | Claude | Builds the Kit email draft with the real link |
| Midday | Jeff + Mauricio | **End-to-end test:** Kit test email to Jeff → click on phone → submit → Mauricio confirms the request arrived at info@flytraverse.com and that Viktor created the JourneyFuse lead. Also test a broken link. |
| Afternoon | Mauricio | Approves the email. It sends. |
| After | Claude | Records the decisions in both repos (form stack, link format change, BE-FB-010 status) |

**Human-only steps:** the GoDaddy DNS record (browser login), the Web3Forms key (needs the info@ inbox), deal content and send approval (Mauricio), confirming the lead arrived (Mauricio). Everything else is done by Claude.

## 9. Requirements check

| From the notes | How this meets it |
|----------------|-------------------|
| Prefilled with the deal (REQ-BE-008, M0610 00:47:33) | Deal fields read from the link and shown on the page |
| "My dates are different" calendar, no new price (REQ-BE-008, RISK-BE-006) | Optional date pickers; no repricing |
| Traveler count, name, email (REQ-BE-008, M0924 00:22:33) | Form fields |
| Email only, no phone (M1008P L910-920) | No phone field or option |
| Goes to info@flytraverse.com, watched by Mauricio and Viktor (Q-BE-010, CONF-BE-011) | Web3Forms emails that inbox |
| Lands on our page, not the airline or Google Flights (REQ-BE-011) | Hosted on deals.flight-bridge.com |
| "Traverse Tours powered by Flight Bridge", real brand assets (PARENT DEC-NL-009, ui-notes) | Traverse colors, fonts, logo |
| Links on a domain we control, versioned (RISK-BE-007) | Our domain, `v=1` |
| Works from social posts too (IMP-BE-010) | Nothing depends on Kit; any shared link works |
| Package deals supported (Black Friday package 2026-11-30) | `type=package` in v1 |
| Record the link the customer came from (`deal-links.md` rule 4) | Full link in every request email |
| A broken link still produces a lead (`deal-links.md` rule 2) | Page works without deal details |
| No account needed (REQ-BE-007) | No sign-in |
| Verify submissions arrive end to end (IMP-BE-009, RISK-BE-014) | Section 8 test, confirmed by Mauricio |
| Live before the pre-Black Friday sends (IMP-BE-014) | Live 2026-10-14 |
| Free deal emails start this week (PARENT DEC-NL-017 update) | Section 5.6 |
| Nothing sends without Mauricio's approval (PARENT DEC-NL-013) | Section 7 and 8 |

## 10. Risks and fallbacks

- **Viktor does not pick up the request email.** Caught by the test. Fallback: adjust the subject wording to Viktor's keywords, or Mauricio adds a rule.
- **Requests pass 250 in a month.** Check the count mid-November and move to Web3Forms Pro (~$12/mo) before 2026-11-25 if needed.
- **Web3Forms becomes a problem.** The form service is one setting in the page. Sent links keep working, because they point at our domain.
- **DNS takes time to update.** GitHub Pages usually works within an hour. If not ready by midday, the test uses the GitHub address and the email waits for the real one.
- **Deal content is not ready from Mauricio.** The page can launch without it. The email goes out when the deal is approved.

## 11. Open items for Jeff

1. **Who receives this week's deal email?** All 1,338 subscribers in Kit, or only the people who actually signed up (tag `landing-page-confirmed`)? The 09-30 announcement went to the whole imported list.
2. **Who writes this week's destination content:** Mauricio, or Claude drafts it for Mauricio to approve?
