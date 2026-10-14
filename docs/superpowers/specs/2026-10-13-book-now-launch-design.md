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

**Done means:** a real Kit test email to Jeff, clicked on a phone, produces a request that Mauricio confirms arrived at info@flytraverse.com. Then the deal email goes out with Mauricio's approval. Whether Viktor turns it into a JourneyFuse lead is checked in the same test. If Viktor misses it, the email still sends and Mauricio handles requests by hand until the wording is fixed (section 10).

## 2. Scope

**In (scope B, agreed 2026-10-13):**
- The Book Now page and form
- The deal-link format and a simple way to make a link each week
- Hosting at `deals.flight-bridge.com/traverse-tours/`
- Requests emailed to info@flytraverse.com
- This week's first free deal email in Kit, with a working Book Now button
- An end-to-end test

**Out today:**
- The bookable engine (on hold until the ARC transfer, DEC-BE-015)
- Black Friday setup in Kit, list growth (scope C, not chosen), and any Black Friday teaser this week (Jeff, 2026-10-14).
- **Social post of the free deal** (PARENT REQ-NL-005). The same Book Now link works there, so Mauricio can post it any time.
- **Tagging these leads to Flight Bridge in JourneyFuse** (DEC-BE-016). Every request email's subject starts with "Book Now request", so these leads can be found and tagged later.
- **The "Deals you missed" footer** (PARENT REQ-NL-002, content strategy). It teases paid-tier deals, and there are none before November (PARENT DEC-NL-017). It returns when paid deals exist.

## 3. Choices made, and why

Each was compared against at least two others. The rule: the cheapest option that does the whole job, as long as it stays simple, easy and repeatable.

| Choice | Picked | Compared against | Why |
|--------|--------|------------------|-----|
| Lead inbox | info@flytraverse.com | info@traversetours.com | It is the address on Traverse's website. traversetours.com belongs to an unrelated company (CONF-BE-011). |
| Link domain | `deals.flight-bridge.com/traverse-tours/` | `deals.traversetours.flight-bridge.com`; `book.flytraverse.com`; a page inside the Duda site | Jeff controls flight-bridge.com. One setup serves every future agency (new agency = new folder). `traversetours.flight-bridge.com` is excluded because it carries the newsletter's email records. `ui-notes.md` says there is no public Flight Bridge consumer site; the page itself is fully Traverse-branded, and the address bar is the only place "flight-bridge" shows. Jeff accepted that for repeatability (2026-10-13). |
| Form and page | Our own page + Web3Forms | Tally free; Tally Pro ($29/mo); Formspree; Fillout; Google Forms; Kit; Beehiiv | The only $0 option that keeps Traverse branding, keeps the customer on our domain, and emails each request to the inbox we choose. Web3Forms Pro (~$12/mo, 10,000 a month) is the upgrade if needed. Formspree's free tier (50 a month) is too small for Black Friday. |
| Hosting | GitHub Pages | Cloudflare Pages; Netlify | $0, Jeff is already signed in to GitHub here, and publishing is a `git push`. It needs a public repo, which is fine: the page holds no secrets (the Web3Forms key is designed to be public). |
| Making a weekly link | A small link-builder page next to the Book Now page | Hand-editing a template link; a Google Sheet formula; Claude adding it to each draft | Anyone can make a correct link without Claude or URL editing. Small to build. |
| Who gets the email | A Kit segment: "subscribed to form 9964131 or 9958519" | The hand-applied `landing-page-confirmed` tag (already misses one person who signed up on 10-12); the tag plus a Kit rule (rules may need a paid Kit plan; the account is on the free plan); Claude re-tagging through the API before each send; all 1,338 imported contacts | Jeff chose sign-ups only (2026-10-13). A segment updates itself, needs no weekly work, and the Kit API sends to segments. Fallback if segments are not available on the free plan: Claude re-tags every form sign-up through the API before each send. |

## 4. How it works for the customer

1. The deal email shows this week's deal with a **Book Now** button, and a line under it: "A Traverse agent will email you to confirm."
2. The button opens `deals.flight-bridge.com/traverse-tours/?v=1&deal=...`.
3. The page shows the deal: route, dates, price per person, branded "Traverse Tours powered by Flight Bridge".
4. The customer enters: number of travelers, name, email. Optional: a **My dates are different** box that opens two date pickers (no new price shown), and an **Anything else?** message box.
5. They press **Send my request**. The page shows a thank-you: an agent will email them.
6. Web3Forms emails the request to info@flytraverse.com.
7. Viktor picks up the lead and creates it in JourneyFuse. An agent replies by email (email only, no phone).

If the link is missing details or broken, the page still works. The deal box is left out, and the customer says which deal in the message box. Every request still produces a lead.

## 5. The pieces

**5.1 Book Now page.** First step, before any page code: pull the real brand assets from flytraverse.com (`ui-notes.md`): Traverse's logo file from the flytraverse.com image CDN (1920x476 transparent PNG, white text, made for a dark band; never a cropped screenshot), and the small Flight Bridge mark already used in the 09-30 email footer (PARENT DEC-NL-021) for "powered by Flight Bridge". Then one HTML file with its style and a little script, in folder `traverse-tours/`. Colors and fonts match the live Traverse pages: slate teal `#4E6A6A` band, sage `#66857B` buttons, cream `#F2EEE6`, Fraunces headings, Instrument Sans body (`ui-notes.md`, PARENT DEC-NL-028). No stock photos or made-up stats. Phone first, since most people open email on a phone.

Copy says exactly what happens (`ui-notes.md`): the button reads **Send my request**, and the page says a Traverse agent will email them to confirm the trip and the price. When "My dates are different" is ticked, the page says the agent will confirm the price for the new dates (RISK-BE-006). The price line reads "as found on [date], subject to change" (PARENT automation.md language guard, RISK-NL-007).

**5.2 Link builder.** `traverse-tours/build.html`. Boxes for: flight or package, from, to, depart date, return date, price per person, the date the price was found, and a short title (needed for package deals, `deal-links.md`). The deal ID is filled in automatically from the travel month and route (for example `2026-11-slc-cun`), or the title for packages. It shows the finished link with a Copy button.

**5.3 Hosting and domain.** A new public GitHub repo (`flight-bridge-deals`) published with GitHub Pages. Two DNS records in GoDaddy:
- `deals` CNAME to `hammbino.github.io` (added first thing, so it has time to spread)
- a TXT record GitHub gives for domain verification, added in the same visit. GitHub recommends verifying before adding the domain, so nobody else can claim `deals.flight-bridge.com` on GitHub Pages

Order matters: the site is tested at its github.io address first. The custom domain is switched on in GitHub only once `deals.flight-bridge.com` resolves, then HTTPS is turned on when the certificate is issued. GitHub says this usually takes up to an hour, and in rare cases up to 24 hours. flight-bridge.com has no CAA record, so nothing blocks the certificate (checked 2026-10-14). If the domain is switched on too early, the github.io address redirects to a domain that does not work yet.

**5.4 Form service.** Web3Forms free plan. Jeff enters info@flytraverse.com at web3forms.com to create the access key. The key is emailed to that inbox, and Mauricio sends it to Jeff (Jeff, 2026-10-14). On the free plan the page can set the email subject, and the customer's email becomes the reply-to automatically (Web3Forms docs). Spam protection: Web3Forms' hidden honeypot field.

**5.5 The request email.** Subject: `Book Now request: SLC to CUN, Nov 14 to 21 (Jane Doe, jane@example.com)`. The customer's email is in the subject as well as Reply-To and the body, because the From address is always Web3Forms'. If "My dates are different" is ticked, the subject shows the customer's dates and says so: `Book Now request: SLC to CUN, NEW DATES Dec 2 to 9 (deal was Nov 14 to 21) (Jane Doe, jane@example.com)`. It always starts with "Book Now request" (so these leads can be found later, DEC-BE-016). Viktor's lead words (Mauricio supplies them, section 8) are added to the subject, never in place of that prefix. The body lists every field, plus the full link the customer came from (REQ-BE-008, `deal-links.md` rule 4). The agent hits Reply to answer the customer.

**5.6 This week's deal email.** Built by Claude through the Kit API (Kit's editor rejects browser automation, PARENT KNOWN_ISSUES 2026-09-29; PARENT DEC-NL-019). It starts from the 09-30 broadcast's HTML in the "Text only" template: the slate teal logo band and the sage HTML button (PARENT DEC-NL-021). Content: the featured destination (PARENT REQ-NL-002 format: destination, info, tip), this week's deal with "as found on [date], subject to change", and the Book Now button. Claude drafts from Mauricio's deal and updates the draft through the API. Kit's API has no test-send, so Jeff presses Send test in Kit. Mauricio reviews the test and replies with changes; Claude applies them through the API. Nothing sends without his written OK, and Jeff presses Send (PARENT DEC-NL-013, automation.md). No mention of paid tiers or upgrades before November (PARENT DEC-NL-017).

Recipients: a Kit segment of everyone subscribed to either signup form (9964131, 9958519). Jeff creates it once in Kit. It stays current by itself. Fallback if the free plan has no segments: Claude adds the `landing-page-confirmed` tag to every form sign-up through the API before each send, and sends to the tag.

**5.7 Replies to the deal email.** Kit sends from deals@traversetours.flight-bridge.com. Replies land in owner@flight-bridge.com (PARENT DEC-NL-018), not in info@flytraverse.com. Options compared:
- **A Gmail filter on owner@ (picked, set up today, Jeff 2026-10-14):** mail sent to deals@traversetours.flight-bridge.com is forwarded automatically to info@flytraverse.com. Automatic forwarding keeps the customer as the sender, so Viktor sees a normal lead. $0, one rule, done once. Gmail sends a confirmation code to info@ once, which Mauricio passes on in the same check as the Web3Forms key. If Google Workspace blocks automatic forwarding, Jeff (as admin) allows it. Auto-replies and out-of-office mail would also be forwarded; Viktor should ignore them.
- Jeff forwards replies by hand: no setup, but forwarded mail comes from owner@, so Viktor may not treat it as a lead.
- A "do not reply" address: rejected. The notes chose replies on purpose (PARENT DEC-NL-018, CONF-NL-005), a reply is a warm lead, and replies help keep the newsletter out of spam.
- Change Kit's reply-to: not confirmed Kit allows a reply-to different from the sender.

This settles who handles replies to deals@ (PARENT CONF-NL-005, which said it was not settled). Mauricio agrees in his morning message (section 8).

## 6. Link format (v1)

```
https://deals.flight-bridge.com/traverse-tours/?v=1&deal=2026-11-slc-cun&type=flight&from=SLC&to=CUN&depart=2026-11-14&return=2026-11-21&price=289&found=2026-10-13
```

This follows `deal-links.md` with two changes: the deal ID moves from the path into `deal=` (a plain static host serves one page per folder, so a path like `/deal/<id>` would need extra setup for no gain), and `found=` carries the date the price was seen, for the "as found on" line. Package links add `title=`. `deal-links.md` is updated to match. Price is display only, per person. Phase 2 must never charge from it.

## 7. Weekly checklist (repeatable)

1. Mauricio sends this week's deal: route, dates, price per person, and where and when he found it.
2. Claude drafts the email (destination, info, tip, the deal) through the Kit API. **Jeff** presses Send test in Kit, to Mauricio and himself (Kit's API has no test-send). Mauricio replies with changes; he does not edit in Kit's editor, which could break the hand-coded layout. Claude applies them through the API and Jeff sends a fresh test.
3. **Mauricio**, on send day (Wednesday): re-checks the deal against its source. Pulls it if the price is gone.
4. **Claude:** makes the link with the link builder (anyone else can use it the same way).
5. **Claude:** puts the link on the Book Now button through the API. No paid-tier mention before November.
6. **Jeff** sends a Kit test to Mauricio and himself, clicks the button on a phone, and checks the deal shows correctly. If the step 3 re-check changed the price or dates, Claude rebuilds the link and the draft first, and the test is redone.
7. Mauricio gives his written OK on the final test email. Jeff presses Send in Kit, to the sign-ups segment. Any change after the OK needs a new OK (PARENT workflows, approval rule 1; automation.md: a human is always the send trigger).

New agency later: copy the `traverse-tours/` folder, change logo, colors and inbox key.

## 8. Today (Wed 2026-10-14)

**First thing, one message to Mauricio** (Jeff sends; Claude drafts it). It asks for:
1. This week's deal: route, dates, price per person, where and when he found it.
2. The Web3Forms key email, once Jeff creates it. Check Junk and Quarantine (info@ is on Microsoft 365).
3. The words Viktor looks for in lead emails, and where Viktor takes the customer's email address from. Web3Forms always sends from its own address, which cannot be changed. The customer's email will be in Reply-To, the body, and the subject. If Viktor reads only the From line, that needs a change on Viktor's side (pointing it at Reply-To or the body).
4. OK for replies to deal emails to be forwarded automatically to info@ (PARENT CONF-NL-005), and the Gmail confirmation code that arrives at info@ when Jeff sets up the forwarding (check Junk too).
5. Is he available today for the test and the approval?

| When | Who | Step |
|------|-----|------|
| Morning | Jeff | Sends the message to Mauricio. Creates the Web3Forms key with info@flytraverse.com. At github.com/settings/pages, adds `deals.flight-bridge.com` and copies the TXT value GitHub shows. In one GoDaddy visit, adds two records: TXT with Name `_github-pages-challenge-hammbino.deals` (not the full name GitHub shows, which GoDaddy would double) and GitHub's value; and CNAME with Name `deals`, Value `hammbino.github.io`. Clicks Verify on the GitHub page after Claude confirms the TXT record is live (`dig`). Creates the Kit segment "subscribed to form 9964131 or 9958519" (if segments are not on the free plan, tells Claude to use the tag fallback).  In owner@'s Gmail, adds info@flytraverse.com as a forwarding address and a filter: mail to deals@traversetours.flight-bridge.com → forward to info@flytraverse.com (finished once Mauricio sends the code). |
| Morning | Claude | Pulls brand assets. Builds the page and link builder. Creates the repo and publishes to GitHub Pages at the github.io address. |
| Morning | Mauricio | Sends the deal, the Web3Forms key, the Gmail forwarding code, Viktor's keywords, and his OK on replies. |
| Midday | Claude | Puts in the Web3Forms key and Viktor's lead words, before the end-to-end test. The From address cannot be changed (Web3Forms sends from its own address); the customer's email goes in Reply-To, the body and the subject. Switches on the custom domain once DNS resolves, then HTTPS. Drafts the Kit email through the API, with the real link. |
| Midday | Jeff + Claude | Jeff presses Send test in Kit, to Mauricio and himself, for content review. This can happen before HTTPS is live; nobody clicks the button until the gate below passes. Claude applies Mauricio's changes through the API, and Jeff sends a fresh test, until he is happy. |
| Midday | Jeff + Mauricio | **Gate:** Claude first confirms `https://deals.flight-bridge.com/traverse-tours/` loads with a valid certificate and tells Jeff; until then, page testing continues over plain http (once the custom domain is on, the github.io address redirects there). **End-to-end test:** Kit test email to Jeff → click on phone → submit → Mauricio confirms the request arrived at info@flytraverse.com (checking Junk and Quarantine if not) and whether Viktor created the JourneyFuse lead with the test customer's email address, not the Web3Forms address. Also test a broken link. Reply to the test email and confirm the reply arrives at info@flytraverse.com through the forwarding rule, from the replier's address. |
| Afternoon | Mauricio, then Jeff | Mauricio re-checks the deal against its source (send day). If the price or dates changed, Claude rebuilds the link and updates the draft, Jeff sends a new test and re-clicks the button. Then Mauricio gives his written OK on the final test. Jeff presses Send in Kit. Any change after the OK needs a new OK. |
| After | Claude | Records in both repos: the form stack and link format (`deal-links.md`, BE-FB-010), deal sourcing now from Mauricio rather than an AI run (PARENT DEC-NL-013, workflows), Mauricio reviewing by test email instead of editing in Kit (PARENT workflows approval rule 2), reply handling (PARENT CONF-NL-005), the footer dropped until paid deals exist, and USD in `assumptions.md`. Resolves Q-BE-007 and the `deal-links.md` section 5 open items with this design. |

**Human-only steps:** the GitHub domain verification and the two GoDaddy DNS records, and the Kit segment (Jeff); pressing Send test and Send in Kit (Jeff); creating the Web3Forms key (Jeff) and passing it on (Mauricio); the Gmail forwarding rule on owner@ (Jeff) and its confirmation code (Mauricio); the deal, the keywords and send approval (Mauricio); confirming the request arrived (Mauricio). Everything else is done by Claude.

## 9. Requirements check

"Implied" marks entries from `implicit-requirements.md`, which are not confirmed requirements.

| From the notes | How this meets it |
|----------------|-------------------|
| Prefilled with the deal (REQ-BE-008, M0610 00:47:33) | Deal fields read from the link and shown on the page |
| Preloaded deal is editable (REQ-BE-003, ui-notes) | Dates via "My dates are different", traveler count, and an "Anything else?" message |
| "My dates are different" calendar, no new price (REQ-BE-008, RISK-BE-006) | Optional date pickers; agent confirms price |
| Traveler count, name, email (REQ-BE-008, M0924 00:22:33) | Form fields |
| Email only, no phone (M1008P L910-920) | No phone field or option |
| Goes to info@flytraverse.com, watched by Mauricio and Viktor (Q-BE-010, CONF-BE-011) | Web3Forms emails that inbox |
| Lands on our page, not the airline or Google Flights (REQ-BE-011) | Hosted on deals.flight-bridge.com |
| "Traverse Tours powered by Flight Bridge", real brand assets (PARENT DEC-NL-009, ui-notes) | Traverse colors, fonts, real logo file, powered-by badge |
| CTA says an agent follows up (ui-notes) | Line under the email button; page copy |
| Price "as found on [date], subject to change" (PARENT automation.md, RISK-NL-007) | Email and page |
| Links on a domain we control, versioned (RISK-BE-007) | Our domain, `v=1` |
| Works from social posts and forwarded emails (implied, IMP-BE-010; forwarding allowed by Jeff 2026-10-14) | Nothing depends on Kit or on who clicks |
| Package deals supported (Black Friday package 2026-11-30) | `type=package` and `title=` in v1 |
| Record the link the customer came from (`deal-links.md` rule 4) | Full link in every request email |
| A broken link still produces a lead (`deal-links.md` rule 2) | Page works without deal details |
| No account needed (REQ-BE-007) | No sign-in |
| Verify submissions arrive end to end (implied, IMP-BE-009; RISK-BE-014) | Section 8 test |
| Live before the pre-Black Friday sends (implied, IMP-BE-014) | Live 2026-10-14 |
| Free deal emails start this week (PARENT DEC-NL-017 update) | Section 5.6 |
| Nothing sends without Mauricio's approval (PARENT DEC-NL-013) | Sections 7 and 8 |
| Send-day deal re-check (PARENT RISK-NL-007, workflows) | Section 7 step 3 |
| No paid-tier mention before November (PARENT DEC-NL-017) | Sections 5.6 and 7 |
| Replies to deal emails reach a watched inbox (RISK-BE-014) | Section 5.7: Gmail forwarding rule, set up today |
| Social post with Book Now (PARENT REQ-NL-005) | Out today; same link works |
| Booking share tracked in JourneyFuse (DEC-BE-016) | Out today; leads findable by subject |

## 10. Risks and fallbacks

- **Viktor does not pick up the request email.** Caught by the test. Mauricio handles requests by hand while it is fixed: subject words on our side, or, if Viktor reads only the From line, pointing Viktor at Reply-To or the body on Viktor's side (the From address cannot be changed). Re-test whenever lead handling changes, and again before 2026-11-25.
- **Requests pass 250 in a month.** Check the count mid-November and move to Web3Forms Pro (~$12/mo) before 2026-11-25 if needed.
- **Web3Forms becomes a problem.** The form service is one setting in the page. Sent links keep working, because they point at our domain.
- **DNS or HTTPS is slow.** The CNAME goes in first thing. If `https://deals.flight-bridge.com` is not working by mid-afternoon, the email waits; the links must use the real domain, because sent emails cannot be changed.
- **Request or setup emails land in Junk on Microsoft 365.** Mauricio checks Junk and Quarantine and adds an allow rule.
- **New sign-ups miss the email.** Fixed by sending to a self-updating segment (5.6).
- **Deal content is not ready from Mauricio.** The page can launch without it. The email waits until the deal is approved, even into Thursday; a deal-less email is not sent, since the deal and Book Now are its point.
- **Mauricio is not available today.** Most steps wait on him. Asked first thing (section 8).

## 11. Decisions and open items

**Answered:**
- Recipients: sign-ups only, not the imported contacts (Jeff, 2026-10-13).
- Destination content: Claude drafts, Mauricio approves (Jeff, 2026-10-14). Mauricio now supplies the deal, where the parent workflow had an AI run source it; recorded after launch.
- Pre-fill the subscriber's name and email: no (Jeff, 2026-10-14). The 9 sign-ups have no names stored, and forwarding is welcome.
- Price: per person (Jeff, 2026-10-14). USD is an assumption.
- Forwarded deals work for friends: yes, for the free deal (Jeff, 2026-10-14). A friend's request is a new lead. Whether paid deals (from November) are limited to members is decided then.
- The 10-08 message page never existed (Jeff, 2026-10-14).
- Black Friday teaser: not this week (Jeff, 2026-10-14).
- Replies to deal emails: forwarded automatically to info@ by a Gmail rule, set up today (Jeff, 2026-10-14).

**Open:**
1. **Jeff's Friday inbox spot-check** (PARENT workflows, RISK-NL-008). Jeff has no access to info@flytraverse.com. Not blocking today; decide after launch (for example, Mauricio reports the week's request count).
