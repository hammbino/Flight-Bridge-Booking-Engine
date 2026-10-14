---
title: "Book Now Launch: Design"
project: Flight Bridge Booking Engine
status: Needs Review
owner: Jeffrey Hammond
last_updated: 2026-10-14
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

**Out:** the bookable engine (on hold until the ARC transfer, DEC-BE-015), Black Friday setup in Kit, list growth, the Viktor-to-Claude move. Also out for today:
- **Social post of the free deal** with Book Now and Join Email List buttons (PARENT REQ-NL-005). The same Book Now link works there, so Mauricio can post it any time.
- **Tagging these leads to Flight Bridge in JourneyFuse** (DEC-BE-016), unless Mauricio can set it up today. Every request email has the subject prefix "Book Now request", so these leads can be found and tagged later.

## 3. Choices made, and why

Each was compared against at least two others. The rule: the cheapest option that does the whole job, as long as it stays simple, easy and repeatable.

| Choice | Picked | Compared against | Why |
|--------|--------|------------------|-----|
| Lead inbox | info@flytraverse.com | info@traversetours.com | It is the address on Traverse's website. traversetours.com belongs to an unrelated company (CONF-BE-011). |
| Link domain | `deals.flight-bridge.com/traverse-tours/` | `deals.traversetours.flight-bridge.com`; `book.flytraverse.com`; a page inside the Duda site | Jeff controls flight-bridge.com. One setup serves every future agency (new agency = new folder). `traversetours.flight-bridge.com` is excluded because it carries the newsletter's email records. Note: `ui-notes.md` says there is no public Flight Bridge consumer site. The page itself is fully Traverse-branded; the address bar is the only place "flight-bridge" shows, which Jeff accepted for repeatability (2026-10-13). |
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

**5.1 Book Now page.** First step, before any page code: pull the real brand assets from flytraverse.com (`ui-notes.md`): Traverse's logo file from the flytraverse.com image CDN (1920x476 transparent PNG, made for a dark band, never a cropped screenshot), and a small "powered by Flight Bridge" badge from the Flight Bridge brand guide. Then one HTML file with its style and a little script, in folder `traverse-tours/`. Colors and fonts match the live Traverse pages: slate teal `#4E6A6A`, sage `#66857B`, cream `#F2EEE6`, Fraunces headings, Instrument Sans body (`ui-notes.md`, PARENT DEC-NL-028). No stock photos or made-up stats. It works on a phone first, since most people open email on a phone.

Copy says exactly what happens (`ui-notes.md`): the button reads **Send my request**, and the page says a Traverse agent will email them to confirm the trip and the price. When "My dates are different" is ticked, the page says the agent will confirm the price for the new dates (RISK-BE-006).

**5.2 Link builder.** `traverse-tours/build.html`. Boxes for: flight or package, from, to, depart date, return date, price per person, and a short title (for package deals, `deal-links.md`). The deal ID is filled in automatically from the month and route (for example `2026-10-slc-cun`). It shows the finished link with a Copy button and a "Test this link" button.

**5.3 Hosting and domain.** A new public GitHub repo (`flight-bridge-deals`) published with GitHub Pages. One DNS record in GoDaddy: `deals` CNAME to `hammbino.github.io`. HTTPS is turned on in GitHub Pages once the certificate is issued. The domain is also verified in Jeff's GitHub settings, so nobody else can claim `deals.flight-bridge.com` on GitHub Pages.

**5.4 Form service.** Web3Forms free plan. Jeff enters info@flytraverse.com at web3forms.com to create the access key. The key is emailed to that inbox, and Jeff asks Mauricio to send it over (Jeff, 2026-10-14). Spam protection: Web3Forms' hidden honeypot field.

**5.5 The request email.** Subject: `Book Now request: SLC to CUN, Nov 14 to 21 (Jane Doe)`. The body lists every field, plus the full link the customer came from (REQ-BE-008, `deal-links.md` rule 4). Reply-to is set to the customer's email, so an agent can just hit Reply. Confirm during the build that Web3Forms supports the custom subject and reply-to on the free plan. Whether Viktor recognizes it as a lead is unknown until the test (section 8).

**5.6 This week's deal email.** A Kit broadcast to the `landing-page-confirmed` tag only (Jeff, 2026-10-13), in the existing "Text only" template: the featured destination content (PARENT REQ-NL-002 format: destination, info, tip), this week's deal, and the Book Now button (a clear link if the template has no button block). Claude drafts it from Mauricio's deal; Mauricio edits and approves before it sends (PARENT DEC-NL-013). Two newsletter rules apply: no mention of paid tiers or upgrades before November (PARENT DEC-NL-017), and the deal is re-checked on send day against its verification block (source link, price seen, time checked; PARENT RISK-NL-007).

**5.7 Replies to the deal email.** Kit sends from deals@traversetours.flight-bridge.com, and replies to it land in owner@flight-bridge.com (PARENT DEC-NL-018), not in info@flytraverse.com. A subscriber who hits Reply instead of Book Now would be a missed lead. Options:
- **Forwarding rule in owner@'s Gmail** (picked): a filter for mail sent to deals@traversetours.flight-bridge.com forwards it to info@flytraverse.com. $0, one rule, nothing changes in Kit. Gmail sends a confirmation to info@ once, so Mauricio sends Jeff the code or clicks the link. If the Google Workspace admin settings block automatic forwarding, Jeff (as admin) allows it or adds the same rule as an admin routing rule.
- Change Kit's reply-to to info@flytraverse.com. Not confirmed that Kit allows a reply-to different from the sender.
- Do nothing and tell readers to use the button. Replies would still be missed.

## 6. Link format (v1)

```
https://deals.flight-bridge.com/traverse-tours/?v=1&deal=2026-10-slc-cun&type=flight&from=SLC&to=CUN&depart=2026-11-14&return=2026-11-21&price=289
```

This follows `deal-links.md` with one change: the deal ID moves from the path into `deal=`. A plain static host serves one page per folder, so a path like `/deal/<id>` would need extra setup for no gain. `deal-links.md` will be updated to match. Price is display only. Phase 2 must never charge from it.

## 7. Weekly checklist (repeatable)

1. Mauricio sends this week's deal: route, dates, price per person, and where he found it.
2. Claude drafts the email (destination, info, tip, the deal). Mauricio edits.
3. On send day (Wednesday), re-check the deal against its verification block. Pull it if the price is gone.
4. Open the link builder, fill in the deal, copy the link.
5. Paste it as the Book Now link in the Kit email. No paid-tier mention before November.
6. Send a Kit test to yourself, click the link on a phone, check the deal shows correctly.
7. Mauricio approves, then the email is sent to the `landing-page-confirmed` tag.

New agency later: copy the `traverse-tours/` folder, change logo, colors and inbox key.

## 8. Today (Wed 2026-10-14)

| When | Who | Step |
|------|-----|------|
| Morning | Mauricio | Sends this week's deal: route, dates, price, and where he found it. Claude drafts the destination content from it |
| Morning | Jeff, then Mauricio | Jeff creates the Web3Forms key for info@flytraverse.com; Mauricio sends Jeff the key from that inbox |
| Morning | Claude | Builds the page and link builder, creates the repo, publishes to GitHub Pages |
| Morning | Jeff | Adds the `deals` CNAME in GoDaddy (Claude gives the exact values) |
| Morning | Jeff + Mauricio | Gmail forwarding rule: mail to deals@ forwards to info@flytraverse.com. Mauricio confirms the forwarding link (5.7) |
| Midday | Claude | Builds the Kit email draft with the real link |
| Midday | Jeff + Mauricio | **End-to-end test:** Kit test email to Jeff → click on phone → submit → Mauricio confirms the request arrived at info@flytraverse.com and that Viktor created the JourneyFuse lead. Also test a broken link. If the request is not in the inbox, Mauricio checks Junk and Quarantine (info@ is on Microsoft 365) and adds an allow rule for the Web3Forms sender. Then test the reply path: reply to the test email and confirm it reaches info@flytraverse.com. |
| Afternoon | Mauricio | Approves the email. It sends. |
| After | Claude | Records the decisions in both repos (form stack, link format change, BE-FB-010 status) |

**Human-only steps:** the GoDaddy DNS record and GitHub domain verification (Jeff, browser login); creating the Web3Forms key (Jeff) and passing it on (Mauricio); the Gmail forwarding rule (Jeff) and its confirmation (Mauricio); the deal and send approval (Mauricio); confirming the lead arrived (Mauricio). Everything else is done by Claude.

## 9. Requirements check

| From the notes | How this meets it |
|----------------|-------------------|
| Prefilled with the deal (REQ-BE-008, M0610 00:47:33) | Deal fields read from the link and shown on the page |
| "My dates are different" calendar, no new price (REQ-BE-008, RISK-BE-006) | Optional date pickers; no repricing |
| Traveler count, name, email (REQ-BE-008, M0924 00:22:33) | Form fields |
| Email only, no phone (M1008P L910-920) | No phone field or option |
| Goes to info@flytraverse.com, watched by Mauricio and Viktor (Q-BE-010, CONF-BE-011) | Web3Forms emails that inbox |
| Lands on our page, not the airline or Google Flights (REQ-BE-011) | Hosted on deals.flight-bridge.com |
| "Traverse Tours powered by Flight Bridge", real brand assets (PARENT DEC-NL-009, ui-notes) | Traverse colors, fonts, real logo file, powered-by badge |
| CTA says an agent follows up; agent confirms price on new dates (ui-notes, RISK-BE-006) | Section 5.1 copy |
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
| Send-day deal re-check and verification block (PARENT RISK-NL-007, workflows) | Section 7 step 2 |
| No paid-tier mention before November (PARENT DEC-NL-017) | Sections 5.6 and 7 |
| Replies to deal emails reach a watched inbox (RISK-BE-014) | Section 5.7 forwarding rule |
| Social post with Book Now (PARENT REQ-NL-005) | Out for tomorrow; same link works |
| Booking share tracked in JourneyFuse (DEC-BE-016) | Out for tomorrow unless Mauricio sets it up; leads are findable by subject |

## 10. Risks and fallbacks

- **Viktor does not pick up the request email.** Caught by the test. Fallback: adjust the subject wording to Viktor's keywords, or Mauricio adds a rule.
- **Requests pass 250 in a month.** Check the count mid-November and move to Web3Forms Pro (~$12/mo) before 2026-11-25 if needed.
- **Web3Forms becomes a problem.** The form service is one setting in the page. Sent links keep working, because they point at our domain.
- **DNS takes time to update.** GitHub Pages usually works within an hour. If not ready by midday, the test uses the GitHub address and the email waits for the real one.
- **Viktor is replaced by a Claude setup** (RISK-BE-017, planned around the week of 2026-10-19). The new setup must also watch info@flytraverse.com and recognize "Book Now request" emails. Re-run the test after the switch.
- **Request emails land in Junk on Microsoft 365.** Caught by the test; Mauricio adds an allow rule.
- **Deal content is not ready from Mauricio.** The page can launch without it. The email goes out when the deal is approved.

## 11. Open items for Jeff

1. ~~Who receives this week's deal email?~~ **Answered 2026-10-13:** only people who actually signed up (Kit tag `landing-page-confirmed`, about 8 people including Jeff's own test sign-up). Not the 1,338 imported contacts.
2. ~~Who writes this week's destination content?~~ **Answered:** Claude drafts it, Mauricio edits and approves (Jeff, 2026-10-14). Mauricio sends the deal: route, dates, price, and where he found it.
3. **Pre-filling the subscriber's own name and email** from Kit (`deal-links.md` open item 2). Proposed: not in v1. It would put email addresses in links, and the list is about 8 people. Say if you want it.
4. **Price is per person, in USD.** Assumed from the notes (`deal-links.md` open item 4). Mauricio confirms when he sends the deal.
5. **The message page from 10-08.** On 10-08 Jeff said he had a send-a-message page "set to owner at FlightBridge". Where is it? If it exists, it should be retired or pointed at the new page, so no lead lands in owner@.
