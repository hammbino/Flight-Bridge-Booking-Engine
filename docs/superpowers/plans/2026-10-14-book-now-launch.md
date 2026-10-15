---
title: "Book Now Launch: Implementation Plan"
project: Flight Bridge Booking Engine
status: Needs Review
owner: Jeffrey Hammond
last_updated: 2026-10-14
source_transcripts: [M0610, M0924, M1008P, EM, PARENT]
tags: [plan, phase-1, book-now, deal-links, kit, launch]
---

# Book Now Launch Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** A subscriber clicks Book Now in this week's free deal email, lands on a Traverse-branded page with the deal filled in, sends a request, and the request arrives at info@flytraverse.com. The email goes out only after Mauricio's written OK.

**Architecture:** A static site in a new public GitHub repo (`flight-bridge-deals`), served by GitHub Pages at `deals.flight-bridge.com`. The page reads the deal from the link and posts the form to Web3Forms, which emails info@flytraverse.com. The deal email is built and updated through the Kit API by a small Python script in the parent repo. Jeff presses Send test and Send in Kit.

**Tech Stack:** Plain HTML, CSS and JavaScript modules (no build step, no framework). Node's built-in test runner (`node --test`, Node 26 is installed). Python 3 standard library for the Kit script, with `unittest`. GitHub Pages, GoDaddy DNS, Web3Forms free plan, Kit V4 API.

**Spec:** `docs/superpowers/specs/2026-10-13-book-now-launch-design.md` (approved by Jeff 2026-10-14). Read it alongside this plan.

## Global Constraints

- Lead inbox: `info@flytraverse.com`. Never info@traversetours.com (an unrelated company).
- Page address: `https://deals.flight-bridge.com/traverse-tours/`. Link builder: `https://deals.flight-bridge.com/traverse-tours/build.html`.
- Link format v1: `?v=1&deal=2026-11-slc-cun&type=flight&from=SLC&to=CUN&depart=2026-11-14&return=2026-11-21&price=289&found=2026-10-13`. Packages add `title=`. Unknown parameters are ignored.
- Price is display only, per person, USD assumed. Nothing ever charges from it.
- Colors: slate teal `#4E6A6A` band, sage `#66857B` buttons, cream `#F2EEE6`. Fonts: Fraunces headings, Instrument Sans body.
- Branding: "Traverse Tours, powered by Flight Bridge". Real logo files only. No stock photos, no made-up stats or testimonials.
- Button text: **Send my request**. The page says a Traverse agent will email them to confirm the trip and the price.
- Price line: "as found on [date], subject to change".
- Email only. No phone field or phone option anywhere.
- Request email subject always starts with `Book Now request`. Viktor's lead words are added after it, never in place of it.
- Example subjects (exact): `Book Now request: SLC to CUN, Nov 14 to 21 (Jane Doe, jane@example.com)` and `Book Now request: SLC to CUN, NEW DATES Dec 2 to 9 (deal was Nov 14 to 21) (Jane Doe, jane@example.com)`.
- Deal email: Kit template "Text only" (5550691), sender `deals@traversetours.flight-bridge.com`, sent only to the sign-ups (forms 9964131 and 9958519), never the 1,338 imported contacts.
- No paid tiers, upgrades or members-only talk in any email before 2026-11-01. No "Deals you missed" footer.
- Nothing sends without Mauricio's written OK on the final test email. Any change after the OK needs a new OK. Jeff presses Send. Claude never sends or schedules a broadcast.
- Never print the Kit API key. It lives in `/Users/jeffrey/Sandbox/Flight-Bridge/.env.local` as `KIT_API_KEY`.
- Plain English in all copy and docs. No em dashes.

## Review Focus

1. **Dates shifting by a day.** A customer in Utah opens a Nov 14 deal and must see Nov 14, not Nov 13. Dates stay as `YYYY-MM-DD` strings and are never turned into `Date` objects for display. Pinned in Task 2 (`formatRange` tests in a non-UTC time zone).
2. **Edited or broken links.** A forwarded link with a missing route, a bad date, `price=abc`, or `<script>` in the title must still show a working form and produce a lead. Pinned in Task 2 (`parseDeal` tests) and Task 3 (all page text set with `textContent`, checked in the browser test).
3. **Sending to the wrong people.** A wrong filter could send to all 1,338 imported contacts. Pinned in Task 6 (script builds the filter only from a segment or the sign-up tag, and refuses otherwise) and Task 9 (Jeff checks the recipient count in Kit is about 9 before pressing Send).
4. **Paid-tier wording slipping into a free email before November.** Pinned in Task 6 (the script refuses to build an email containing paid, upgrade, premium, VIP, member, subscription or tier words before 2026-11-01).
5. **A change after Mauricio's OK going out unreviewed.** Pinned in Task 6 (any push clears the recorded OK and says so).

---

## Files

**New repo `/Users/jeffrey/Sandbox/flight-bridge-deals` (public, GitHub `hammbino/flight-bridge-deals`):**

| File | Job |
|------|-----|
| `.nojekyll` | Tells GitHub Pages to serve files as they are |
| `package.json` | Marks `.js` files as modules so Node can test them; `npm test` |
| `traverse-tours/deal.js` | Pure functions: read a link, format dates and prices, build the subject and payload, build a link. No page access. |
| `traverse-tours/config.js` | The Web3Forms key, Viktor's lead words, the inbox address |
| `traverse-tours/index.html` | The Book Now page |
| `traverse-tours/style.css` | Styles for both pages |
| `traverse-tours/page.js` | Wires the Book Now page to `deal.js` and Web3Forms |
| `traverse-tours/build.html` | The link builder page |
| `traverse-tours/build.js` | Wires the link builder to `deal.js` |
| `traverse-tours/assets/traverse-logo.png` | Traverse logo from the flytraverse.com CDN |
| `traverse-tours/assets/flight-bridge-mark.png` | Flight Bridge mark from the 09-30 email footer |
| `tests/deal.test.js` | Tests for `deal.js` |

**Parent repo `/Users/jeffrey/Sandbox/Flight-Bridge`:**

| File | Job |
|------|-----|
| `scripts/kit_deal_email.py` | Builds the deal email HTML and creates or updates the Kit draft. Never sends. |
| `scripts/test_kit_deal_email.py` | Tests for the HTML builder and its guards |
| `scripts/deals/<deal-id>.json` | One file per weekly email: content, link, recipients, draft ID, Mauricio's OK |
| `.gitignore` | Adds `scripts/deals/*.preview.html` |

---

### Task 1: Kick-off message to Mauricio and Jeff's setup steps

Human steps start first because DNS and the emailed codes take time. Claude does not wait for them before starting Task 2.

**Files:** none.

- [ ] **Step 1: Give Jeff the message for Mauricio.** Paste this in chat, ready to send:

```
Hi Mauricio,

We're launching the Book Now button with this week's free deal email. I need five things from you:

1. This week's deal: route, travel dates, price per person, and where and when you found it.

2. Two codes will arrive at info@flytraverse.com from me setting things up. One from Web3Forms (the form that sends Book Now requests to info@) and one from Gmail (so replies to the newsletter reach info@). Please send me both. If you don't see them, check Junk and Quarantine.

3. Viktor: what words does Viktor look for in an email to treat it as a lead? And where does Viktor take the customer's email address from? Book Now requests will come from the form service's own address, with the customer's email in the Reply-To, the subject and the body. If Viktor only reads the From line, it will need to look at Reply-To or the body instead.

4. Is it OK if replies to the newsletter are forwarded automatically to info@? Right now they come to me.

5. Are you free today or tomorrow for a quick test and to approve the email before it goes out? Nothing sends without your written OK.

Thanks,
Jeff
```

- [ ] **Step 2: Give Jeff his setup steps.** Paste this in chat. Each part stands alone.

```
A. Web3Forms key (2 minutes)
   1. Go to https://web3forms.com
   2. Click "Create your Access Key". Enter info@flytraverse.com. Submit.
   3. The key is emailed to info@flytraverse.com. Mauricio forwards it.

B. GitHub domain check, then GoDaddy (10 minutes)
   1. Go to https://github.com/settings/pages
   2. Under "Verified domains" click "Add a domain". Enter deals.flight-bridge.com. Click "Add domain".
   3. GitHub shows a TXT record. Copy the VALUE only. Leave this tab open.
   4. In a new tab go to https://dcc.godaddy.com/control/portfolio, click flight-bridge.com, then "DNS".
   5. Click "Add New Record". Type: TXT. Name: _github-pages-challenge-hammbino.deals
      (not the full name GitHub shows; GoDaddy adds flight-bridge.com itself). Value: the value from step 3. Save.
   6. Click "Add New Record". Type: CNAME. Name: deals. Value: hammbino.github.io. Save.
   7. Tell Claude "DNS added". Claude checks the TXT record is live and tells you.
   8. Back on the GitHub tab, click "Verify".
   If GoDaddy says a "deals" record already exists, stop and tell Claude (we checked on 10-14 and there was none).

C. Kit segment (5 minutes)
   1. Log in to Kit. Go to Grow > Subscribers.
   2. Find the option to create a segment (often under "+ Add" or the filter menu).
   3. Name it exactly: Sign-ups (both forms)
   4. Rule: subscribed to form "Newsletter Signup", OR subscribed to form "Newsletter site". Save.
   5. It should show about 9 people. Tell Claude the number.
   If you can't find segments or Kit asks you to upgrade, tell Claude "use the tag". Claude handles it with no further steps from you.

D. Forward newsletter replies to info@ (10 minutes, finished when Mauricio sends the code)
   1. In owner@flight-bridge.com Gmail: gear icon > "See all settings" > "Forwarding and POP/IMAP".
   2. Click "Add a forwarding address". Enter info@flytraverse.com. Next > Proceed > OK.
      Gmail emails a code to info@. Do NOT turn on "Forward a copy of incoming mail" (that forwards everything).
   3. When Mauricio sends the code: same page, enter it, click "Verify". Leave "Disable forwarding" selected.
   4. Go to "Filters and Blocked Addresses" > "Create a new filter".
      To: deals@traversetours.flight-bridge.com > "Create filter".
   5. Tick "Forward it to:" and pick info@flytraverse.com. Click "Create filter".
   If step 2 says forwarding is disabled by your administrator: go to https://admin.google.com > Apps >
   Google Workspace > Gmail > End User Access > "Automatic forwarding" > Allow > Save. Then retry step 2.
```

- [ ] **Step 3: When Jeff says "DNS added", check the TXT record.**

Run: `dig +short TXT _github-pages-challenge-hammbino.deals.flight-bridge.com; dig +short deals.flight-bridge.com`
Expected: the TXT value in quotes, then `hammbino.github.io.` and GitHub's IP addresses. If empty, wait 5 minutes and re-run. If still empty after 30 minutes, ask Jeff for a screenshot of the GoDaddy DNS list.

Tell Jeff: "TXT is live. Click Verify on GitHub."

---

### Task 2: Repo and deal logic (`deal.js`) with tests

**Files:**
- Create: `/Users/jeffrey/Sandbox/flight-bridge-deals/.nojekyll`, `package.json`, `traverse-tours/deal.js`, `tests/deal.test.js`

**Interfaces:**
- Produces (all exported from `traverse-tours/deal.js`):
  - `LINK_BASE: string`, `SUBJECT_PREFIX: string`
  - `isIsoDate(value: string) -> boolean`
  - `shortDate(iso: string) -> string` ("Nov 14")
  - `formatRange(depart: string, ret: string|null) -> string` ("Nov 14 to 21")
  - `formatRangeWithYear(depart, ret) -> string` ("Nov 14 to 21, 2026")
  - `formatPrice(price: string) -> string` ("$1,299")
  - `parseDeal(search: string) -> Deal|null`, where `Deal = {id, type: "flight"|"package", title, from, to, depart, ret, price, found}` and `ret`, `price`, `found` may be `null`
  - `routeLabel(deal) -> string`, `priceLine(deal) -> string`
  - `checkNewDates(newDepart, newReturn, today) -> string` (empty when fine)
  - `buildSubject({deal, name, email, newDepart, newReturn, leadWords}) -> string`
  - `buildPayload({accessKey, deal, form, link, leadWords, honeypot}) -> object`, where `form = {name, email, travelers, datesDifferent, newDepart, newReturn, message}`
  - `slugify(text) -> string`, `buildDealId(fields) -> string`, `checkBuilderFields(fields) -> string[]`, `buildLink(fields) -> string`, where `fields = {type, from, to, depart, return, price, found, title}`

- [ ] **Step 1: Create the repo folder**

```bash
mkdir -p /Users/jeffrey/Sandbox/flight-bridge-deals/traverse-tours/assets /Users/jeffrey/Sandbox/flight-bridge-deals/tests
cd /Users/jeffrey/Sandbox/flight-bridge-deals && git init -b main && touch .nojekyll
```

Write `package.json`:

```json
{
  "name": "flight-bridge-deals",
  "private": true,
  "type": "module",
  "scripts": {
    "test": "TZ=America/Denver node --test tests/"
  }
}
```

`TZ=America/Denver` makes the tests run in Mountain time, where a date bug that shifts by a day would show up.

- [ ] **Step 2: Write the failing tests** in `tests/deal.test.js`:

```js
import { test } from "node:test";
import assert from "node:assert/strict";
import {
  isIsoDate, formatRange, formatRangeWithYear, formatPrice, parseDeal,
  priceLine, checkNewDates, buildSubject, buildPayload,
  slugify, buildDealId, checkBuilderFields, buildLink,
} from "../traverse-tours/deal.js";

const FULL = "?v=1&deal=2026-11-slc-cun&type=flight&from=SLC&to=CUN&depart=2026-11-14&return=2026-11-21&price=289&found=2026-10-13";

test("isIsoDate accepts real dates only", () => {
  assert.equal(isIsoDate("2026-11-14"), true);
  assert.equal(isIsoDate("2028-02-29"), true);
  assert.equal(isIsoDate("2026-02-29"), false);
  assert.equal(isIsoDate("2026-13-01"), false);
  assert.equal(isIsoDate("11/14/2026"), false);
  assert.equal(isIsoDate(""), false);
  assert.equal(isIsoDate(null), false);
});

test("formatRange does not shift dates in Mountain time", () => {
  assert.equal(formatRange("2026-11-14", "2026-11-21"), "Nov 14 to 21");
  assert.equal(formatRange("2026-11-28", "2026-12-05"), "Nov 28 to Dec 5");
  assert.equal(formatRange("2026-11-01", null), "Nov 1, one way");
});

test("formatRangeWithYear", () => {
  assert.equal(formatRangeWithYear("2026-11-14", "2026-11-21"), "Nov 14 to 21, 2026");
  assert.equal(formatRangeWithYear("2026-12-28", "2027-01-04"), "Dec 28, 2026 to Jan 4, 2027");
  assert.equal(formatRangeWithYear("2026-11-14", null), "Nov 14, 2026, one way");
});

test("formatPrice", () => {
  assert.equal(formatPrice("289"), "$289");
  assert.equal(formatPrice("1299"), "$1,299");
  assert.equal(formatPrice("0289"), "$289");
  assert.equal(formatPrice("289.50"), "$289.50");
});

test("parseDeal reads a full link", () => {
  assert.deepEqual(parseDeal(FULL), {
    id: "2026-11-slc-cun", type: "flight", title: "", from: "SLC", to: "CUN",
    depart: "2026-11-14", ret: "2026-11-21", price: "289", found: "2026-10-13",
  });
});

test("parseDeal ignores unknown parameters and lower-case codes", () => {
  const deal = parseDeal(FULL.replace("SLC", "slc") + "&utm_source=kit&v2field=x");
  assert.equal(deal.from, "SLC");
});

test("parseDeal returns null when the route or depart date is broken", () => {
  assert.equal(parseDeal(""), null);
  assert.equal(parseDeal("?from=SLC&to=CUN"), null);
  assert.equal(parseDeal("?from=SLC&to=CUN&depart=2026-11-31"), null);
  assert.equal(parseDeal("?from=SALT&to=CUN&depart=2026-11-14"), null);
});

test("parseDeal drops bad optional fields but keeps the deal", () => {
  const deal = parseDeal("?from=SLC&to=CUN&depart=2026-11-14&return=2026-11-01&price=abc&found=yesterday");
  assert.equal(deal.ret, null);
  assert.equal(deal.price, null);
  assert.equal(deal.found, null);
});

test("parseDeal keeps a package title as plain text, capped at 80 characters", () => {
  const deal = parseDeal("?type=package&from=SLC&to=CUN&depart=2026-11-27&title=" + encodeURIComponent("<script>x</script>" + "a".repeat(100)));
  assert.equal(deal.type, "package");
  assert.equal(deal.title.length, 80);
  assert.ok(deal.title.startsWith("<script>"));
});

test("parseDeal ignores a title on a flight", () => {
  assert.equal(parseDeal(FULL + "&title=Hi").title, "");
});

test("priceLine", () => {
  assert.equal(priceLine(parseDeal(FULL)), "$289 per person, as found on Oct 13, subject to change");
  assert.equal(priceLine(parseDeal(FULL.replace("&found=2026-10-13", ""))), "$289 per person, subject to change");
});

test("checkNewDates", () => {
  assert.equal(checkNewDates("2026-12-02", "2026-12-09", "2026-10-14"), "");
  assert.equal(checkNewDates("2026-12-02", "", "2026-10-14"), "");
  assert.match(checkNewDates("", "", "2026-10-14"), /leave/);
  assert.match(checkNewDates("2026-10-01", "", "2026-10-14"), /passed/);
  assert.match(checkNewDates("2026-12-09", "2026-12-02", "2026-10-14"), /before/);
});

test("buildSubject matches the spec examples exactly", () => {
  const deal = parseDeal(FULL);
  assert.equal(
    buildSubject({ deal, name: "Jane Doe", email: "jane@example.com", newDepart: "", newReturn: "", leadWords: "" }),
    "Book Now request: SLC to CUN, Nov 14 to 21 (Jane Doe, jane@example.com)",
  );
  assert.equal(
    buildSubject({ deal, name: "Jane Doe", email: "jane@example.com", newDepart: "2026-12-02", newReturn: "2026-12-09", leadWords: "" }),
    "Book Now request: SLC to CUN, NEW DATES Dec 2 to 9 (deal was Nov 14 to 21) (Jane Doe, jane@example.com)",
  );
});

test("buildSubject keeps the prefix first and adds lead words at the end", () => {
  const subject = buildSubject({ deal: null, name: "Jane Doe", email: "jane@example.com", newDepart: "", newReturn: "", leadWords: "New Lead" });
  assert.equal(subject, "Book Now request: deal not in link (Jane Doe, jane@example.com) New Lead");
});

test("buildPayload carries every field and the full link", () => {
  const deal = parseDeal(FULL);
  const form = { name: "Jane Doe", email: "jane@example.com", travelers: "2", datesDifferent: false, newDepart: "2026-12-02", newReturn: "", message: "" };
  const p = buildPayload({ accessKey: "KEY", deal, form, link: "https://deals.flight-bridge.com/traverse-tours/" + FULL, leadWords: "", honeypot: false });
  assert.equal(p.access_key, "KEY");
  assert.equal(p.email, "jane@example.com");
  assert.equal(p.subject, "Book Now request: SLC to CUN, Nov 14 to 21 (Jane Doe, jane@example.com)");
  assert.equal(p["Dates are different"], "No");
  assert.equal(p["Travelers"], "2");
  assert.equal(p["Deal ID"], "2026-11-slc-cun");
  assert.ok(p["Link they came from"].endsWith(FULL));
  assert.equal(p.botcheck, false);
  assert.equal(JSON.stringify(p).toLowerCase().includes("phone"), false);
});

test("buildPayload with new dates and no deal", () => {
  const form = { name: "Sam", email: "sam@example.com", travelers: "1", datesDifferent: true, newDepart: "2026-12-02", newReturn: "2026-12-09", message: "The Cancun one" };
  const p = buildPayload({ accessKey: "KEY", deal: null, form, link: "https://x/", leadWords: "", honeypot: false });
  assert.equal(p["Deal"], "Not in link. See message.");
  assert.equal(p["Dates are different"], "Yes: Dec 2 to 9, 2026");
  assert.equal(p["Anything else"], "The Cancun one");
});

test("slugify and buildDealId", () => {
  assert.equal(slugify("Cancún All-Inclusive, 5 nights!"), "cancun-all-inclusive-5-nights");
  assert.equal(buildDealId({ type: "flight", from: "SLC", to: "CUN", depart: "2026-11-14" }), "2026-11-slc-cun");
  assert.equal(buildDealId({ type: "package", from: "SLC", to: "CUN", depart: "2026-11-27", title: "Cancún Black Friday" }), "2026-11-cancun-black-friday");
});

test("checkBuilderFields lists every problem", () => {
  const errors = checkBuilderFields({ type: "package", from: "SL", to: "CUN", depart: "2026-11-14", return: "2026-11-01", price: "abc", found: "", title: "" });
  assert.equal(errors.length, 5);
});

test("buildLink round-trips through parseDeal", () => {
  const fields = { type: "flight", from: "SLC", to: "CUN", depart: "2026-11-14", return: "2026-11-21", price: "289", found: "2026-10-13", title: "" };
  assert.deepEqual(checkBuilderFields(fields), []);
  const link = buildLink(fields);
  assert.equal(link, "https://deals.flight-bridge.com/traverse-tours/" + FULL);
  const pkg = { ...fields, type: "package", title: "Cancún Black Friday", return: "" };
  const deal = parseDeal(new URL(buildLink(pkg)).search);
  assert.equal(deal.title, "Cancún Black Friday");
  assert.equal(deal.ret, null);
});
```

- [ ] **Step 3: Run the tests to see them fail**

Run: `cd /Users/jeffrey/Sandbox/flight-bridge-deals && npm test`
Expected: FAIL, "Cannot find module ... deal.js".

- [ ] **Step 4: Write `traverse-tours/deal.js`**

```js
// Pure functions for Traverse Tours deal links. Used by the Book Now page,
// the link builder and the tests. Nothing here touches the page.

export const LINK_BASE = "https://deals.flight-bridge.com/traverse-tours/";
export const SUBJECT_PREFIX = "Book Now request";

const MONTHS = ["Jan", "Feb", "Mar", "Apr", "May", "Jun",
  "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"];
const AIRPORT = /^[A-Z]{3}$/;
const ISO_DATE = /^(\d{4})-(\d{2})-(\d{2})$/;
const PRICE = /^\d{1,6}(\.\d{2})?$/;
const TITLE_MAX = 80;

// Dates stay as "YYYY-MM-DD" strings. Turning them into Date objects for
// display would shift them by a day in US time zones.
export function isIsoDate(value) {
  const m = ISO_DATE.exec(value || "");
  if (!m) return false;
  const year = Number(m[1]);
  const month = Number(m[2]);
  const day = Number(m[3]);
  if (month < 1 || month > 12 || day < 1) return false;
  const daysInMonth = new Date(Date.UTC(year, month, 0)).getUTCDate();
  return day <= daysInMonth;
}

export function shortDate(iso) {
  const [, month, day] = iso.split("-");
  return `${MONTHS[Number(month) - 1]} ${Number(day)}`;
}

export function formatRange(depart, ret) {
  if (!ret) return `${shortDate(depart)}, one way`;
  const sameMonth = depart.slice(0, 7) === ret.slice(0, 7);
  const end = sameMonth ? String(Number(ret.slice(8))) : shortDate(ret);
  return `${shortDate(depart)} to ${end}`;
}

export function formatRangeWithYear(depart, ret) {
  const year = depart.slice(0, 4);
  if (!ret) return `${shortDate(depart)}, ${year}, one way`;
  if (ret.slice(0, 4) !== year) {
    return `${shortDate(depart)}, ${year} to ${shortDate(ret)}, ${ret.slice(0, 4)}`;
  }
  return `${formatRange(depart, ret)}, ${year}`;
}

export function formatPrice(price) {
  const [whole, cents] = price.split(".");
  const withCommas = String(Number(whole)).replace(/\B(?=(\d{3})+(?!\d))/g, ",");
  return cents ? `$${withCommas}.${cents}` : `$${withCommas}`;
}

// Reads the deal from the link. Returns null when the route or depart date
// is missing or broken, so the page falls back to "tell us which deal".
// Bad optional fields are dropped rather than blocking the customer.
export function parseDeal(search) {
  const params = new URLSearchParams(search);
  const get = (key) => (params.get(key) || "").trim();
  const type = get("type") === "package" ? "package" : "flight";
  const from = get("from").toUpperCase();
  const to = get("to").toUpperCase();
  const depart = get("depart");
  if (!AIRPORT.test(from) || !AIRPORT.test(to) || !isIsoDate(depart)) return null;
  const ret = get("return");
  const price = get("price");
  const found = get("found");
  return {
    id: get("deal").slice(0, 60),
    type,
    title: type === "package" ? get("title").slice(0, TITLE_MAX) : "",
    from,
    to,
    depart,
    ret: isIsoDate(ret) && ret >= depart ? ret : null,
    price: PRICE.test(price) ? price : null,
    found: isIsoDate(found) ? found : null,
  };
}

export function routeLabel(deal) {
  const route = `${deal.from} to ${deal.to}`;
  return deal.type === "package" && deal.title ? `${deal.title} (${route})` : route;
}

export function priceLine(deal) {
  const found = deal.found ? `, as found on ${shortDate(deal.found)}` : "";
  return `${formatPrice(deal.price)} per person${found}, subject to change`;
}

export function checkNewDates(newDepart, newReturn, today) {
  if (!isIsoDate(newDepart)) return "Pick the date you want to leave.";
  if (newDepart < today) return "That leave date has already passed.";
  if (newReturn && !isIsoDate(newReturn)) return "Pick a valid return date.";
  if (newReturn && newReturn < newDepart) return "The return date is before the leave date.";
  return "";
}

export function buildSubject({ deal, name, email, newDepart, newReturn, leadWords }) {
  let what;
  if (!deal) {
    what = "deal not in link";
  } else if (newDepart) {
    what = `${routeLabel(deal)}, NEW DATES ${formatRange(newDepart, newReturn || null)} (deal was ${formatRange(deal.depart, deal.ret)})`;
  } else {
    what = `${routeLabel(deal)}, ${formatRange(deal.depart, deal.ret)}`;
  }
  const words = leadWords ? ` ${leadWords}` : "";
  return `${SUBJECT_PREFIX}: ${what} (${name}, ${email})${words}`;
}

// The object posted to Web3Forms. "email" becomes the Reply-To.
// The other keys show up as labeled lines in the request email.
export function buildPayload({ accessKey, deal, form, link, leadWords, honeypot }) {
  const newDepart = form.datesDifferent ? form.newDepart : "";
  const newReturn = form.datesDifferent ? form.newReturn : "";
  return {
    access_key: accessKey,
    subject: buildSubject({ deal, name: form.name, email: form.email, newDepart, newReturn, leadWords }),
    from_name: "Traverse Tours Book Now",
    name: form.name,
    email: form.email,
    "Travelers": form.travelers,
    "Deal": deal ? `${routeLabel(deal)}, ${formatRangeWithYear(deal.depart, deal.ret)}` : "Not in link. See message.",
    "Deal ID": deal && deal.id ? deal.id : "none",
    "Price": deal && deal.price ? priceLine(deal) : "not in link",
    "Dates are different": newDepart ? `Yes: ${formatRangeWithYear(newDepart, newReturn || null)}` : "No",
    "Anything else": form.message || "(nothing)",
    "Link they came from": link,
    botcheck: honeypot,
  };
}

export function slugify(text) {
  return text.normalize("NFD").replace(/[̀-ͯ]/g, "")
    .toLowerCase().replace(/[^a-z0-9]+/g, "-").replace(/^-+|-+$/g, "")
    .slice(0, 40).replace(/-+$/, "");
}

export function buildDealId(fields) {
  const name = fields.type === "package"
    ? slugify(fields.title)
    : `${fields.from}-${fields.to}`.toLowerCase();
  return `${fields.depart.slice(0, 7)}-${name}`;
}

export function checkBuilderFields(fields) {
  const errors = [];
  if (!AIRPORT.test(fields.from)) errors.push("From must be a 3-letter airport code, like SLC.");
  if (!AIRPORT.test(fields.to)) errors.push("To must be a 3-letter airport code, like CUN.");
  if (!isIsoDate(fields.depart)) errors.push("Pick a depart date.");
  if (fields.return && (!isIsoDate(fields.return) || fields.return < fields.depart)) {
    errors.push("The return date must be on or after the depart date. Leave it empty for one way.");
  }
  if (!PRICE.test(fields.price)) errors.push("Price must be a number, like 289 or 289.50.");
  if (!isIsoDate(fields.found)) errors.push("Pick the date the price was found.");
  if (fields.type === "package" && !fields.title) errors.push("Package deals need a short title.");
  if (fields.title && fields.title.length > TITLE_MAX) errors.push(`Keep the title under ${TITLE_MAX} characters.`);
  return errors;
}

export function buildLink(fields) {
  const params = new URLSearchParams();
  params.set("v", "1");
  params.set("deal", buildDealId(fields));
  params.set("type", fields.type);
  params.set("from", fields.from);
  params.set("to", fields.to);
  params.set("depart", fields.depart);
  if (fields.return) params.set("return", fields.return);
  params.set("price", fields.price);
  params.set("found", fields.found);
  if (fields.type === "package") params.set("title", fields.title);
  return `${LINK_BASE}?${params.toString()}`;
}
```

Note on the `checkBuilderFields` test: the five problems are bad From, bad return, bad price, missing found date, missing package title.

- [ ] **Step 5: Run the tests to see them pass**

Run: `cd /Users/jeffrey/Sandbox/flight-bridge-deals && npm test`
Expected: all tests pass, 0 failures.

- [ ] **Step 6: Commit**

```bash
cd /Users/jeffrey/Sandbox/flight-bridge-deals
git add .nojekyll package.json traverse-tours/deal.js tests/deal.test.js
git commit -m "Deal link logic and tests

Co-Authored-By: Claude Opus 5.5 <noreply@anthropic.com>"
```

---

### Task 3: Book Now page

**Files:**
- Create: `traverse-tours/assets/traverse-logo.png`, `traverse-tours/assets/flight-bridge-mark.png`, `traverse-tours/config.js`, `traverse-tours/style.css`, `traverse-tours/index.html`, `traverse-tours/page.js`

**Interfaces:**
- Consumes: from `deal.js`: `parseDeal`, `routeLabel`, `formatRangeWithYear`, `priceLine`, `checkNewDates`, `buildPayload`.
- Produces: `config.js` exports `WEB3FORMS_KEY` (string, empty until Task 7), `LEAD_WORDS` (string, empty until Task 7), `INBOX` (`"info@flytraverse.com"`). `style.css` is shared with the link builder (Task 4).

- [ ] **Step 1: Pull the real brand assets**

The Traverse logo comes from the flytraverse.com image CDN. The 470px version is the CDN's own resize of the 1920x476 file, sharp at the page's display size and a third of the weight. The Flight Bridge mark is the one in the 09-30 email footer.

```bash
cd /Users/jeffrey/Sandbox/flight-bridge-deals/traverse-tours/assets
curl -sf -o traverse-logo.png "https://irp.cdn-website.com/8cd93f82/dms3rep/multi/opt/Traverse_-_NEW_LOGO_Last-8c38425f-470w.png"
curl -sf -o flight-bridge-mark.png "https://embed.filekitcdn.com/e/pwrUjqw7cWBPsYraLtJiCm/oa8AAn4HVaf1RPPT2PXJa8/email"
file traverse-logo.png flight-bridge-mark.png
```

Expected: `traverse-logo.png: PNG image data, 470 x ...` with RGBA, and `flight-bridge-mark.png: PNG image data, 220 x 170`. Open both with the Read tool and confirm the first is the Traverse logo (white text, made for a dark band) and the second is the Flight Bridge mark. If the 470w file is missing, use `...-8c38425f-1920w.png` instead.

- [ ] **Step 2: Write `traverse-tours/config.js`**

```js
// Settings for the Traverse Tours Book Now page.

// Web3Forms access key for info@flytraverse.com. Public by design: it can
// only send to the inbox it was created for. Empty means the form is not live.
export const WEB3FORMS_KEY = "";

// Words Viktor looks for in lead emails. Added to the end of the subject.
export const LEAD_WORDS = "";

export const INBOX = "info@flytraverse.com";
```

- [ ] **Step 3: Write `traverse-tours/style.css`**

```css
:root {
  --teal: #4E6A6A;
  --sage: #66857B;
  --cream: #F2EEE6;
  --ink: #1A1A1A;
  --muted: #4A4A4A;
  --line: #E5DFD3;
  --error: #9B2C2C;
}

* { box-sizing: border-box; }

body {
  margin: 0;
  background: var(--cream);
  color: var(--ink);
  font-family: "Instrument Sans", -apple-system, BlinkMacSystemFont, Helvetica, Arial, sans-serif;
  font-size: 17px;
  line-height: 1.5;
}

.band {
  background: var(--teal);
  padding: 24px 16px;
  text-align: center;
}

.band img { width: 220px; max-width: 70%; height: auto; }

main {
  max-width: 560px;
  margin: 0 auto;
  padding: 28px 16px 40px;
}

h1, h2 {
  font-family: Fraunces, Georgia, "Times New Roman", serif;
  font-weight: 500;
  line-height: 1.25;
  margin: 0 0 12px;
}

h1 { font-size: 30px; }

.intro { color: var(--muted); margin: 0 0 24px; }

.deal {
  background: #fff;
  border: 1px solid var(--line);
  border-radius: 8px;
  padding: 20px;
  margin-bottom: 28px;
}

.deal-route { font-family: Fraunces, Georgia, serif; font-size: 24px; margin: 0 0 4px; }
.deal-dates { margin: 0 0 8px; }
.deal-price { color: var(--muted); font-size: 15px; margin: 0; }

label { display: block; font-weight: 600; margin: 0 0 6px; }

.field { margin-bottom: 20px; }

input[type="text"], input[type="email"], input[type="number"], input[type="date"], select, textarea {
  width: 100%;
  font: inherit;
  padding: 12px;
  border: 1px solid #C9C2B4;
  border-radius: 6px;
  background: #fff;
  color: var(--ink);
}

textarea { min-height: 96px; resize: vertical; }

.check { display: flex; gap: 10px; align-items: center; font-weight: 600; }
.check input { width: 22px; height: 22px; }

.note { color: var(--muted); font-size: 15px; margin: 6px 0 0; }

.new-dates { display: grid; gap: 12px; margin-top: 12px; }

.honeypot { display: none; }

button, .button {
  display: inline-block;
  width: 100%;
  background: var(--sage);
  color: #fff;
  border: 0;
  border-radius: 6px;
  padding: 16px;
  font: inherit;
  font-weight: 600;
  cursor: pointer;
  text-align: center;
  text-decoration: none;
}

button:disabled { opacity: 0.6; cursor: wait; }

.error {
  background: #FBEAEA;
  color: var(--error);
  border-radius: 6px;
  padding: 12px;
  margin-bottom: 16px;
}

.thanks h1 { margin-top: 8px; }

footer {
  text-align: center;
  border-top: 1px solid var(--line);
  margin: 0 16px;
  padding: 24px 0 32px;
  color: #8A8A8A;
  font-size: 13px;
}

footer img { width: 56px; height: auto; display: block; margin: 0 auto 8px; }

.link-out {
  word-break: break-all;
  background: #fff;
  border: 1px solid var(--line);
  border-radius: 6px;
  padding: 12px;
  font-size: 14px;
}

[hidden] { display: none !important; }
```

- [ ] **Step 4: Write `traverse-tours/index.html`**

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="robots" content="noindex">
  <title>Book this deal | Traverse Tours</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Fraunces:wght@500&family=Instrument+Sans:wght@400;600&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="style.css">
  <script type="module" src="page.js"></script>
</head>
<body>
  <header class="band">
    <img src="assets/traverse-logo.png" alt="Traverse Tours">
  </header>

  <main>
    <section id="request">
      <h1 id="title">Book this deal</h1>
      <p class="intro">Tell us who's traveling. A Traverse agent will email you to confirm the trip and the price. Nothing is booked or charged yet.</p>

      <div class="deal" id="deal">
        <p class="deal-route" id="deal-route"></p>
        <p class="deal-dates" id="deal-dates"></p>
        <p class="deal-price" id="deal-price"></p>
      </div>

      <form id="form">
        <div class="error" id="error" role="alert" hidden></div>

        <div class="field">
          <label for="travelers">How many travelers?</label>
          <input type="number" id="travelers" min="1" max="20" inputmode="numeric" required>
        </div>

        <div class="field">
          <label for="name">Your name</label>
          <input type="text" id="name" autocomplete="name" maxlength="80" required>
        </div>

        <div class="field">
          <label for="email">Your email</label>
          <input type="email" id="email" autocomplete="email" maxlength="120" required>
        </div>

        <div class="field" id="dates-different-row">
          <label class="check"><input type="checkbox" id="dates-different"> My dates are different</label>
          <div class="new-dates" id="new-dates" hidden>
            <div>
              <label for="new-depart">Leave</label>
              <input type="date" id="new-depart">
            </div>
            <div>
              <label for="new-return">Return (leave empty for one way)</label>
              <input type="date" id="new-return">
            </div>
            <p class="note">Your agent will confirm the price for your dates.</p>
          </div>
        </div>

        <div class="field">
          <label for="message" id="message-label">Anything else? (optional)</label>
          <textarea id="message" maxlength="2000"></textarea>
        </div>

        <input type="checkbox" id="botcheck" class="honeypot" tabindex="-1" autocomplete="off">

        <button type="submit" id="send">Send my request</button>
      </form>
    </section>

    <section class="thanks" id="thanks" hidden>
      <h1>Thanks, <span id="thanks-name"></span>. Your request is in.</h1>
      <p>A Traverse agent will email you at <strong id="thanks-email"></strong> to confirm the trip and the price.</p>
      <p class="note">If you don't hear back within a day, check your spam folder or email us at info@flytraverse.com.</p>
    </section>
  </main>

  <footer>
    <img src="assets/flight-bridge-mark.png" alt="Flight Bridge">
    Traverse Tours, powered by Flight Bridge
  </footer>
</body>
</html>
```

- [ ] **Step 5: Write `traverse-tours/page.js`**

```js
// Book Now page: shows the deal from the link and sends the request to
// Web3Forms, which emails it to the Traverse inbox.
import { WEB3FORMS_KEY, LEAD_WORDS, INBOX } from "./config.js";
import {
  parseDeal, routeLabel, formatRangeWithYear, priceLine, checkNewDates, buildPayload,
} from "./deal.js";

const deal = parseDeal(window.location.search);
const $ = (id) => document.getElementById(id);

// Local date as YYYY-MM-DD, used as the earliest pickable date.
function localToday() {
  const now = new Date();
  const pad = (n) => String(n).padStart(2, "0");
  return `${now.getFullYear()}-${pad(now.getMonth() + 1)}-${pad(now.getDate())}`;
}

// All text from the link goes in with textContent, never innerHTML,
// because anyone can edit a link.
function showDeal() {
  if (!deal) {
    $("deal").hidden = true;
    $("dates-different-row").hidden = true;
    $("title").textContent = "Request a trip";
    $("message-label").textContent = "Which deal are you interested in?";
    $("message").required = true;
    return;
  }
  $("deal-route").textContent = routeLabel(deal);
  $("deal-dates").textContent = formatRangeWithYear(deal.depart, deal.ret);
  if (deal.price) {
    $("deal-price").textContent = priceLine(deal);
  } else {
    $("deal-price").hidden = true;
  }
}

function setupDates() {
  const today = localToday();
  $("new-depart").min = today;
  $("new-return").min = today;
  $("dates-different").addEventListener("change", (event) => {
    $("new-dates").hidden = !event.target.checked;
    $("new-depart").required = event.target.checked;
  });
}

function showError(text) {
  $("error").textContent = text;
  $("error").hidden = false;
  $("error").scrollIntoView({ behavior: "smooth", block: "center" });
}

async function submit(event) {
  event.preventDefault();
  $("error").hidden = true;
  const form = {
    name: $("name").value.trim(),
    email: $("email").value.trim(),
    travelers: $("travelers").value,
    datesDifferent: deal ? $("dates-different").checked : false,
    newDepart: $("new-depart").value,
    newReturn: $("new-return").value,
    message: $("message").value.trim(),
  };
  if (!form.name) return showError("Please enter your name.");
  if (form.datesDifferent) {
    const problem = checkNewDates(form.newDepart, form.newReturn, localToday());
    if (problem) return showError(problem);
  }
  if (!WEB3FORMS_KEY) return showError(`This form is not live yet. Please email us at ${INBOX}.`);

  const button = $("send");
  button.disabled = true;
  button.textContent = "Sending...";
  try {
    const payload = buildPayload({
      accessKey: WEB3FORMS_KEY,
      deal,
      form,
      link: window.location.href,
      leadWords: LEAD_WORDS,
      honeypot: $("botcheck").checked,
    });
    const response = await fetch("https://api.web3forms.com/submit", {
      method: "POST",
      headers: { "Content-Type": "application/json", Accept: "application/json" },
      body: JSON.stringify(payload),
    });
    const result = await response.json();
    if (!response.ok || !result.success) throw new Error(result.message || String(response.status));
    $("request").hidden = true;
    $("thanks-name").textContent = form.name;
    $("thanks-email").textContent = form.email;
    $("thanks").hidden = false;
    window.scrollTo(0, 0);
  } catch (error) {
    console.error("Book Now send failed:", error);
    showError(`Something went wrong and your request was not sent. Please try again, or email us at ${INBOX}.`);
    button.disabled = false;
    button.textContent = "Send my request";
  }
}

showDeal();
setupDates();
$("form").addEventListener("submit", submit);
```

- [ ] **Step 6: Check the page in a browser**

Modules do not load from `file://`, so serve the folder locally:

Run (background): `cd /Users/jeffrey/Sandbox/flight-bridge-deals && python3 -m http.server 8787`

Load the Chrome tools in one ToolSearch call (`tabs_context_mcp, tabs_create_mcp, navigate, computer, read_page, resize_window, read_console_messages`). Open a new tab and check each case at phone width (390 x 844) and desktop width:

1. `http://localhost:8787/traverse-tours/?v=1&deal=2026-11-slc-cun&type=flight&from=SLC&to=CUN&depart=2026-11-14&return=2026-11-21&price=289&found=2026-10-13`
   Expected: logo on teal band, "SLC to CUN", "Nov 14 to 21, 2026", "$289 per person, as found on Oct 13, subject to change", Fraunces heading, no sideways scrolling, footer mark.
2. Same link, tick "My dates are different". Expected: two date pickers and the price note appear.
3. `http://localhost:8787/traverse-tours/` (no deal). Expected: "Request a trip", no deal box, no dates checkbox, message box labeled "Which deal are you interested in?" and required.
4. `...?type=package&from=SLC&to=CUN&depart=2026-11-27&title=%3Cimg%20src%3Dx%20onerror%3Dalert(1)%3E` Expected: the title shows as literal text `<img src=x onerror=alert(1)>`, no image, no alert. (Check with `read_page`; do not click anything that could open a dialog.)
5. Fill the form on case 1 and press Send my request. Expected: the red box says "This form is not live yet. Please email us at info@flytraverse.com." (the key is still empty).
6. `read_console_messages`: no errors besides the logged "Book Now send failed" if any.

Take a phone-width screenshot of case 1 and show it to Jeff with the screenshots for the other cases summarized in one line each.

- [ ] **Step 7: Commit**

```bash
cd /Users/jeffrey/Sandbox/flight-bridge-deals
git add traverse-tours/
git commit -m "Traverse Tours Book Now page

Co-Authored-By: Claude Opus 5.5 <noreply@anthropic.com>"
```

---

### Task 4: Link builder

**Files:**
- Create: `traverse-tours/build.html`, `traverse-tours/build.js`

**Interfaces:**
- Consumes: from `deal.js`: `checkBuilderFields`, `buildLink`. From Task 3: `style.css`.

- [ ] **Step 1: Write `traverse-tours/build.html`**

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="robots" content="noindex">
  <title>Deal link builder | Traverse Tours</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Fraunces:wght@500&family=Instrument+Sans:wght@400;600&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="style.css">
  <script type="module" src="build.js"></script>
</head>
<body>
  <header class="band">
    <img src="assets/traverse-logo.png" alt="Traverse Tours">
  </header>
  <main>
    <h1>Make a Book Now link</h1>
    <p class="intro">Fill in this week's deal. The link updates as you type. Test it before it goes in an email.</p>

    <form id="builder">
      <div class="field">
        <label for="type">Kind of deal</label>
        <select id="type">
          <option value="flight">Flight</option>
          <option value="package">Package</option>
        </select>
      </div>
      <div class="field" id="title-row" hidden>
        <label for="title">Short title (shown on the page)</label>
        <input type="text" id="title" maxlength="80" placeholder="Cancun Black Friday">
      </div>
      <div class="field">
        <label for="from">From airport code</label>
        <input type="text" id="from" maxlength="3" placeholder="SLC" autocapitalize="characters">
      </div>
      <div class="field">
        <label for="to">To airport code</label>
        <input type="text" id="to" maxlength="3" placeholder="CUN" autocapitalize="characters">
      </div>
      <div class="field">
        <label for="depart">Depart date</label>
        <input type="date" id="depart">
      </div>
      <div class="field">
        <label for="return">Return date (leave empty for one way)</label>
        <input type="date" id="return">
      </div>
      <div class="field">
        <label for="price">Price per person, USD (numbers only)</label>
        <input type="text" id="price" inputmode="decimal" placeholder="289">
      </div>
      <div class="field">
        <label for="found">Date the price was found</label>
        <input type="date" id="found">
      </div>
    </form>

    <div class="error" id="problems" hidden></div>

    <div id="result" hidden>
      <p class="link-out" id="link"></p>
      <button type="button" id="copy">Copy link</button>
      <p class="note"><a id="open" href="#" target="_blank" rel="noopener">Open the link to check it</a></p>
    </div>
  </main>
</body>
</html>
```

- [ ] **Step 2: Write `traverse-tours/build.js`**

```js
// Link builder: turns this week's deal into a Book Now link.
import { checkBuilderFields, buildLink } from "./deal.js";

const $ = (id) => document.getElementById(id);
const ids = ["type", "title", "from", "to", "depart", "return", "price", "found"];

function localToday() {
  const now = new Date();
  const pad = (n) => String(n).padStart(2, "0");
  return `${now.getFullYear()}-${pad(now.getMonth() + 1)}-${pad(now.getDate())}`;
}

function readFields() {
  const fields = Object.fromEntries(ids.map((id) => [id, $(id).value.trim()]));
  fields.from = fields.from.toUpperCase();
  fields.to = fields.to.toUpperCase();
  fields.price = fields.price.replace(/[$,\s]/g, "");
  if (fields.type !== "package") fields.title = "";
  return fields;
}

function update() {
  $("title-row").hidden = $("type").value !== "package";
  const fields = readFields();
  const problems = checkBuilderFields(fields);
  $("problems").hidden = problems.length === 0;
  $("problems").textContent = problems.join(" ");
  $("result").hidden = problems.length > 0;
  if (problems.length) return;
  const link = buildLink(fields);
  $("link").textContent = link;
  $("open").href = link;
}

async function copy() {
  try {
    await navigator.clipboard.writeText($("link").textContent);
    $("copy").textContent = "Copied";
  } catch {
    $("copy").textContent = "Select the link above and copy it";
  }
  setTimeout(() => { $("copy").textContent = "Copy link"; }, 2500);
}

$("found").value = localToday();
ids.forEach((id) => $(id).addEventListener("input", update));
$("copy").addEventListener("click", copy);
update();
```

- [ ] **Step 3: Check the builder in a browser** (server from Task 3 still running)

Open `http://localhost:8787/traverse-tours/build.html`. Enter: Flight, `slc`, `cun`, 2026-11-14, 2026-11-21, `$289`, found 2026-10-13.
Expected link exactly: `https://deals.flight-bridge.com/traverse-tours/?v=1&deal=2026-11-slc-cun&type=flight&from=SLC&to=CUN&depart=2026-11-14&return=2026-11-21&price=289&found=2026-10-13`
Then swap the host to `http://localhost:8787` in that link, open it, and confirm the Book Now page shows the deal. Switch to Package with no title: the error box asks for a title and the link hides.

- [ ] **Step 4: Commit**

```bash
cd /Users/jeffrey/Sandbox/flight-bridge-deals
git add traverse-tours/build.html traverse-tours/build.js
git commit -m "Deal link builder

Co-Authored-By: Claude Opus 5.5 <noreply@anthropic.com>"
```

---

### Task 5: Publish to GitHub Pages (github.io address)

**Files:** none new. Creates the GitHub repo.

- [ ] **Step 1: Create the public repo and push**

```bash
cd /Users/jeffrey/Sandbox/flight-bridge-deals
gh repo create hammbino/flight-bridge-deals --public --source . --push --description "Book Now deal pages for agencies powered by Flight Bridge"
```

Expected: repo URL printed, `main` pushed. Before pushing, run `git grep -n -i -E "api[_-]?key|secret|password"` and confirm nothing but the empty `WEB3FORMS_KEY` line shows.

- [ ] **Step 2: Turn on Pages from `main`**

```bash
gh api -X POST repos/hammbino/flight-bridge-deals/pages -f "source[branch]=main" -f "source[path]=/"
```

Expected: JSON with `"html_url": "https://hammbino.github.io/flight-bridge-deals/"`.

- [ ] **Step 3: Wait for the first build and check it**

Run: `gh api repos/hammbino/flight-bridge-deals/pages/builds/latest --jq .status` until it prints `built` (use Monitor with an until-loop, not sleep). Then:

Run: `curl -s -o /dev/null -w "%{http_code}\n" "https://hammbino.github.io/flight-bridge-deals/traverse-tours/"`
Expected: `200`.

Open `https://hammbino.github.io/flight-bridge-deals/traverse-tours/?v=1&deal=2026-11-slc-cun&type=flight&from=SLC&to=CUN&depart=2026-11-14&return=2026-11-21&price=289&found=2026-10-13` in Chrome at phone width. Expected: same as Task 3 case 1. Send Jeff this link so he can look on his phone.

---

### Task 6: Kit deal email script (parent repo)

Can run before Mauricio's deal arrives.

**Files:**
- Create: `/Users/jeffrey/Sandbox/Flight-Bridge/scripts/kit_deal_email.py`, `/Users/jeffrey/Sandbox/Flight-Bridge/scripts/test_kit_deal_email.py`
- Modify: `/Users/jeffrey/Sandbox/Flight-Bridge/.gitignore` (create if missing)

**Interfaces:**
- Consumes: a deal file `scripts/deals/<deal-id>.json`:

```json
{
  "subject": "Cancun from $289: this week's free deal",
  "preview_text": "Salt Lake City to Cancun, Nov 14 to 21",
  "destination": "Cancun",
  "info": ["First paragraph about the place.", "Second paragraph."],
  "tip": "One practical travel tip.",
  "deal": {
    "from_city": "Salt Lake City", "to_city": "Cancun",
    "depart": "2026-11-14", "return": "2026-11-21",
    "price": "289", "found": "2026-10-13"
  },
  "book_now_link": "https://deals.flight-bridge.com/traverse-tours/?v=1&...",
  "recipients": {"segment_id": null, "tag_id": null},
  "broadcast_id": null,
  "mauricio_ok": null
}
```

- Produces CLI commands: `preview <file>`, `push <file>`, `status <file>`, `tag-signups`.

- [ ] **Step 1: Write the failing tests** in `scripts/test_kit_deal_email.py`:

```python
import copy
import datetime
import unittest

import kit_deal_email as k

DEAL = {
    "subject": "Cancun from $289: this week's free deal",
    "preview_text": "Salt Lake City to Cancun, Nov 14 to 21",
    "destination": "Cancun",
    "info": ["Warm water & white sand."],
    "tip": "Bring pesos for small shops.",
    "deal": {"from_city": "Salt Lake City", "to_city": "Cancun", "depart": "2026-11-14",
             "return": "2026-11-21", "price": "289", "found": "2026-10-13"},
    "book_now_link": "https://deals.flight-bridge.com/traverse-tours/?v=1&deal=2026-11-slc-cun&type=flight&from=SLC&to=CUN&depart=2026-11-14&return=2026-11-21&price=289&found=2026-10-13",
    "recipients": {"segment_id": None, "tag_id": 24350319},
    "broadcast_id": None,
    "mauricio_ok": None,
}
OCT = datetime.date(2026, 10, 14)


class FormatTests(unittest.TestCase):
    def test_range(self):
        self.assertEqual(k.format_range("2026-11-14", "2026-11-21"), "Nov 14 to 21")
        self.assertEqual(k.format_range("2026-11-28", "2026-12-05"), "Nov 28 to Dec 5")
        self.assertEqual(k.format_range("2026-11-14", ""), "Nov 14, one way")

    def test_price(self):
        self.assertEqual(k.format_price("1299"), "$1,299")
        self.assertEqual(k.format_price("289.50"), "$289.50")


class HtmlTests(unittest.TestCase):
    def test_contains_link_price_line_and_agent_line(self):
        html = k.build_html(DEAL, today=OCT)
        self.assertIn('href="https://deals.flight-bridge.com/traverse-tours/?v=1&amp;deal=2026-11-slc-cun', html)
        self.assertIn("$289 per person, round trip, as found on Oct 13, subject to change", html)
        self.assertIn("A Traverse agent will email you to confirm.", html)
        self.assertIn("Book Now", html)
        self.assertIn("Traverse Tours, powered by Flight Bridge", html)

    def test_escapes_text(self):
        d = copy.deepcopy(DEAL)
        d["tip"] = "<b>bold</b>"
        self.assertIn("&lt;b&gt;bold&lt;/b&gt;", k.build_html(d, today=OCT))
        self.assertIn("Warm water &amp; white sand.", k.build_html(DEAL, today=OCT))

    def test_no_phone_and_no_footer_teaser(self):
        html = k.build_html(DEAL, today=OCT).lower()
        self.assertNotIn("phone", html)
        self.assertNotIn("deals you missed", html)


class GuardTests(unittest.TestCase):
    def test_paid_words_blocked_before_november(self):
        d = copy.deepcopy(DEAL)
        d["tip"] = "Upgrade to Premium for more."
        with self.assertRaises(k.DealError):
            k.check_deal(d, today=OCT)

    def test_paid_words_allowed_from_november(self):
        d = copy.deepcopy(DEAL)
        d["tip"] = "Upgrade to Premium for more."
        k.check_deal(d, today=datetime.date(2026, 11, 1))

    def test_prepaid_is_not_a_paid_word(self):
        d = copy.deepcopy(DEAL)
        d["tip"] = "Prepaid SIM cards are cheap. Remember your passport."
        k.check_deal(d, today=OCT)

    def test_link_must_be_ours(self):
        d = copy.deepcopy(DEAL)
        d["book_now_link"] = "https://hammbino.github.io/flight-bridge-deals/traverse-tours/?v=1"
        with self.assertRaises(k.DealError):
            k.check_deal(d, today=OCT)

    def test_exactly_one_recipient_group(self):
        d = copy.deepcopy(DEAL)
        d["recipients"] = {"segment_id": None, "tag_id": None}
        with self.assertRaises(k.DealError):
            k.check_deal(d, today=OCT)
        d["recipients"] = {"segment_id": 1, "tag_id": 2}
        with self.assertRaises(k.DealError):
            k.check_deal(d, today=OCT)

    def test_filter(self):
        self.assertEqual(k.subscriber_filter({"segment_id": 7, "tag_id": None}),
                         [{"all": [{"type": "segment", "ids": [7]}]}])
        self.assertEqual(k.subscriber_filter({"segment_id": None, "tag_id": 24350319}),
                         [{"all": [{"type": "tag", "ids": [24350319]}]}])


if __name__ == "__main__":
    unittest.main()
```

- [ ] **Step 2: Run to see them fail**

Run: `cd /Users/jeffrey/Sandbox/Flight-Bridge/scripts && python3 -m unittest test_kit_deal_email -v`
Expected: FAIL, `ModuleNotFoundError: No module named 'kit_deal_email'`.

- [ ] **Step 3: Write `scripts/kit_deal_email.py`**

```python
#!/usr/bin/env python3
"""Build this week's Traverse Tours deal email and keep it as a Kit draft.

This script never sends or schedules. Jeff presses Send test and Send in Kit,
and only after Mauricio's written OK on the final test email.

Usage:
  python3 kit_deal_email.py preview deals/<id>.json   write deals/<id>.preview.html
  python3 kit_deal_email.py push deals/<id>.json      create or update the Kit draft
  python3 kit_deal_email.py status deals/<id>.json    show the draft's state in Kit
  python3 kit_deal_email.py tag-signups               tag every sign-up (segment fallback)
"""
import datetime
import html
import json
import re
import sys
import urllib.error
import urllib.request
from pathlib import Path

API = "https://api.kit.com/v4"
ENV_FILE = Path(__file__).resolve().parents[1] / ".env.local"
LINK_BASE = "https://deals.flight-bridge.com/traverse-tours/"
TEMPLATE_ID = 5550691  # "Text only"
SENDER = "deals@traversetours.flight-bridge.com"
SIGNUP_FORMS = (9964131, 9958519)
SIGNUP_TAG = 24350319  # landing-page-confirmed
PAID_TALK_ALLOWED_FROM = datetime.date(2026, 11, 1)
PAID_WORDS = re.compile(r"\b(paid|upgrades?|premium|vip|members?|membership|subscriptions?|tiers?)\b", re.I)

LOGO = "https://embed.filekitcdn.com/e/pwrUjqw7cWBPsYraLtJiCm/3bk7dpBdxhPkSb1H2RJ6xM"
FB_MARK = "https://embed.filekitcdn.com/e/pwrUjqw7cWBPsYraLtJiCm/oa8AAn4HVaf1RPPT2PXJa8/email"
SERIF = "Fraunces, Georgia, 'Times New Roman', serif"
SANS = "-apple-system, BlinkMacSystemFont, 'Instrument Sans', Helvetica, Arial, sans-serif"
MONTHS = ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"]


class DealError(Exception):
    pass


def short_date(iso):
    _, month, day = iso.split("-")
    return f"{MONTHS[int(month) - 1]} {int(day)}"


def format_range(depart, ret):
    if not ret:
        return f"{short_date(depart)}, one way"
    end = str(int(ret[8:])) if depart[:7] == ret[:7] else short_date(ret)
    return f"{short_date(depart)} to {end}"


def format_price(price):
    whole, _, cents = price.partition(".")
    text = f"${int(whole):,}"
    return f"{text}.{cents}" if cents else text


def all_text(d):
    return " ".join([d["subject"], d["preview_text"], d["destination"], d["tip"], *d["info"]])


def check_deal(d, today):
    if not d["book_now_link"].startswith(LINK_BASE + "?v=1&"):
        raise DealError(f"book_now_link must start with {LINK_BASE}?v=1&")
    groups = [g for g in (d["recipients"].get("segment_id"), d["recipients"].get("tag_id")) if g]
    if len(groups) != 1:
        raise DealError("Set exactly one of recipients.segment_id or recipients.tag_id.")
    if today < PAID_TALK_ALLOWED_FROM:
        found = PAID_WORDS.search(all_text(d))
        if found:
            raise DealError(f'No paid-tier talk before November. Found "{found.group(0)}".')


def subscriber_filter(recipients):
    if recipients.get("segment_id"):
        return [{"all": [{"type": "segment", "ids": [recipients["segment_id"]]}]}]
    return [{"all": [{"type": "tag", "ids": [recipients["tag_id"]]}]}]


def p(text, extra=""):
    return (f'<p style="font-family:{SANS};font-size:16px;line-height:1.6;color:#4A4A4A;'
            f'margin:0 0 18px 0;{extra}">{html.escape(text)}</p>')


def build_html(d, today):
    check_deal(d, today)
    deal = d["deal"]
    trip = "round trip" if deal.get("return") else "one way"
    price_line = (f"{format_price(deal['price'])} per person, {trip}, "
                  f"as found on {short_date(deal['found'])}, subject to change")
    route = f"{deal['from_city']} to {deal['to_city']}"
    dates = format_range(deal["depart"], deal.get("return"))
    link = html.escape(d["book_now_link"], quote=True)
    info = "".join(p(par) for par in d["info"])
    return f"""<table cellPadding="0" cellSpacing="0" style="width:100%;margin:0 auto"><tbody><tr><td><div style="background-color:#F3EEE6;padding:0;margin:0;">
<div style="text-align:center;padding:32px 20px 32px 20px;background-color:#4E6A6A;">
<img src="{LOGO}" alt="Traverse Tours" style="max-width:200px;width:100%;height:auto;display:inline-block;border:0;">
</div>
<div style="padding:36px 28px 8px 28px;">
<h1 style="font-family:{SERIF};font-weight:500;font-size:30px;line-height:1.3;color:#1A1A1A;margin:0 0 20px 0;text-align:center;">{html.escape(d['destination'])}</h1>
{info}
<p style="font-family:{SANS};font-size:16px;line-height:1.6;color:#4A4A4A;margin:0 0 18px 0;"><strong style="color:#1A1A1A;">Travel tip:</strong> {html.escape(d['tip'])}</p>
</div>
<div style="margin:8px 24px 0 24px;padding:28px 20px 32px 20px;background-color:#FFFFFF;border:1px solid #E5DFD3;border-radius:8px;text-align:center;">
<p style="font-family:{SANS};font-size:13px;letter-spacing:1px;text-transform:uppercase;color:#66857B;margin:0 0 8px 0;font-weight:600;">This week's deal</p>
<h2 style="font-family:{SERIF};font-weight:500;font-size:24px;line-height:1.3;color:#1A1A1A;margin:0 0 6px 0;">{html.escape(route)}</h2>
<p style="font-family:{SANS};font-size:16px;color:#1A1A1A;margin:0 0 6px 0;">{html.escape(dates)}</p>
<p style="font-family:{SANS};font-size:14px;color:#4A4A4A;margin:0 0 24px 0;">{html.escape(price_line)}</p>
<a href="{link}" target="_blank" rel="noopener noreferrer" style="display:inline-block;background-color:#66857b;color:#ffffff;text-decoration:none;font-family:{SANS};font-size:16px;font-weight:600;padding:14px 34px;border-radius:6px;">Book Now</a>
<p style="font-family:{SANS};font-size:14px;color:#4A4A4A;margin:14px 0 0 0;">A Traverse agent will email you to confirm.</p>
</div>
<div style="text-align:center;padding:28px 20px 32px 20px;border-top:1px solid #E5DFD3;margin:32px 24px 0 24px;">
<img src="{FB_MARK}" alt="Flight Bridge" style="max-width:70px;width:100%;height:auto;display:inline-block;margin:24px 0 10px 0;border:0;">
<p style="font-family:{SANS};font-size:13px;color:#8A8A8A;margin:0;">Traverse Tours, powered by Flight Bridge</p>
</div>
</div></td></tr></tbody></table>"""


def api_key():
    for line in ENV_FILE.read_text().splitlines():
        if line.startswith("KIT_API_KEY="):
            return line.split("=", 1)[1].strip().strip('"').strip("'")
    sys.exit(f"KIT_API_KEY not found in {ENV_FILE}")


def kit(method, path, body=None):
    request = urllib.request.Request(
        API + path,
        method=method,
        data=json.dumps(body).encode() if body is not None else None,
        headers={"X-Kit-Api-Key": api_key(), "Content-Type": "application/json",
                 "Accept": "application/json", "User-Agent": "flight-bridge-scripts"},
    )
    try:
        with urllib.request.urlopen(request) as response:
            text = response.read().decode()
            return json.loads(text) if text else {}
    except urllib.error.HTTPError as error:
        sys.exit(f"Kit {method} {path} failed: {error.code} {error.read().decode()[:500]}")


def load(path):
    return json.loads(Path(path).read_text())


def save(path, d):
    Path(path).write_text(json.dumps(d, indent=2, ensure_ascii=False) + "\n")


def preview(path):
    out = Path(path).with_suffix(".preview.html")
    out.write_text(build_html(load(path), datetime.date.today()))
    print(f"Wrote {out}")


def push(path):
    d = load(path)
    body = {
        "subject": d["subject"],
        "preview_text": d["preview_text"],
        "content": build_html(d, datetime.date.today()),
        "email_template_id": TEMPLATE_ID,
        "email_address": SENDER,
        "public": False,
        "send_at": None,
        "subscriber_filter": subscriber_filter(d["recipients"]),
    }
    if d["broadcast_id"]:
        current = kit("GET", f"/broadcasts/{d['broadcast_id']}")["broadcast"]
        if current["status"] != "draft":
            sys.exit(f"Broadcast {d['broadcast_id']} is '{current['status']}', not a draft. Not changing it.")
        kit("PUT", f"/broadcasts/{d['broadcast_id']}", body)
        print(f"Updated draft {d['broadcast_id']}.")
    else:
        created = kit("POST", "/broadcasts", body)["broadcast"]
        d["broadcast_id"] = created["id"]
        print(f"Created draft {created['id']} (status: {created['status']}).")
    if d["mauricio_ok"]:
        print("The email changed, so Mauricio's earlier OK no longer counts. Send a new test and get a new OK.")
        d["mauricio_ok"] = None
    save(path, d)


def status(path):
    d = load(path)
    b = kit("GET", f"/broadcasts/{d['broadcast_id']}")["broadcast"]
    print(json.dumps({k: b.get(k) for k in ("id", "status", "subject", "send_at", "email_address",
                                             "subscriber_filter")}, indent=2))
    print(f"Mauricio's OK on file: {d['mauricio_ok'] or 'none'}")


def tag_signups():
    ids = set()
    for form in SIGNUP_FORMS:
        after = None
        while True:
            query = f"/forms/{form}/subscribers?per_page=500" + (f"&after={after}" if after else "")
            page = kit("GET", query)
            ids.update(s["id"] for s in page["subscribers"])
            if not page["pagination"]["has_next_page"]:
                break
            after = page["pagination"]["end_cursor"]
    for subscriber_id in sorted(ids):
        kit("POST", f"/tags/{SIGNUP_TAG}/subscribers/{subscriber_id}", {})
    print(f"Tagged {len(ids)} sign-ups with landing-page-confirmed ({SIGNUP_TAG}).")


def main(argv):
    commands = {"preview": preview, "push": push, "status": status}
    try:
        if argv[1:] == ["tag-signups"]:
            tag_signups()
        elif len(argv) == 3 and argv[1] in commands:
            commands[argv[1]](argv[2])
        else:
            sys.exit(__doc__)
    except DealError as error:
        sys.exit(f"Not built: {error}")


if __name__ == "__main__":
    main(sys.argv)
```

- [ ] **Step 4: Run the tests to see them pass**

Run: `cd /Users/jeffrey/Sandbox/Flight-Bridge/scripts && python3 -m unittest test_kit_deal_email -v`
Expected: all pass.

- [ ] **Step 5: Ignore preview files and commit**

```bash
cd /Users/jeffrey/Sandbox/Flight-Bridge
echo "scripts/deals/*.preview.html" >> .gitignore
git add .gitignore scripts/kit_deal_email.py scripts/test_kit_deal_email.py
git commit -m "Kit deal email script: builds and updates drafts, never sends

Co-Authored-By: Claude Opus 5.5 <noreply@anthropic.com>"
```

Do not `git add` the two uncommitted 10-08 transcripts. Add files by name only.

---

### Task 7: Go live on deals.flight-bridge.com

Waits on: Jeff's DNS and GitHub verification (Task 1 part B), the Web3Forms key, Viktor's lead words. Do the parts whose inputs have arrived; the rest when they do.

**Files:**
- Modify: `traverse-tours/config.js` (the two empty strings)

- [ ] **Step 1: Put in the key and lead words.** Set `WEB3FORMS_KEY` to the key Mauricio forwarded and `LEAD_WORDS` to Viktor's words exactly as he wrote them (empty string if he says Viktor needs none). Run `npm test`. Commit with message "Web3Forms key and Viktor lead words" and push.

- [ ] **Step 2: Switch on the custom domain** once `dig +short deals.flight-bridge.com` returns `hammbino.github.io.` and Jeff has clicked Verify.

```bash
gh api -X PUT repos/hammbino/flight-bridge-deals/pages -f cname=deals.flight-bridge.com
git -C /Users/jeffrey/Sandbox/flight-bridge-deals pull
```

Expected: GitHub adds a `CNAME` file to the repo, which the pull brings down.

- [ ] **Step 3: Turn on HTTPS once the certificate is issued.** Check with `gh api repos/hammbino/flight-bridge-deals/pages --jq '.https_certificate.state'` (Monitor until-loop, checking every 5 minutes). When it prints `approved`:

```bash
gh api -X PUT repos/hammbino/flight-bridge-deals/pages -F https_enforced=true
```

- [ ] **Step 4: The HTTPS gate.** All three must pass before anyone clicks a test link:

```bash
curl -s -o /dev/null -w "%{http_code} %{ssl_verify_result}\n" https://deals.flight-bridge.com/traverse-tours/
curl -s -o /dev/null -w "%{http_code} %{redirect_url}\n" http://deals.flight-bridge.com/traverse-tours/
curl -s -o /dev/null -w "%{http_code}\n" https://deals.flight-bridge.com/traverse-tours/build.html
```

Expected: `200 0`, then `301 https://deals.flight-bridge.com/traverse-tours/`, then `200`. Tell Jeff: "The HTTPS gate passed. Test links are safe to click."

If the certificate is not approved within 2 hours: remove and re-add the custom domain once (GitHub's documented fix), then wait again. If still not working by mid-afternoon on send day, tell Jeff the email waits (spec section 10). Never put a github.io link in an email.

- [ ] **Step 5: One real submission from Claude.** In Chrome, open the live link from Task 4 Step 3, fill in travelers 1, name `TEST Claude (ignore)`, email `owner@flight-bridge.com`, tick My dates are different with any future dates, and press Send my request. Expected: the thank-you screen. Ask Mauricio to confirm it arrived at info@ (and check Junk and Quarantine if not). This checks the key works before the full end-to-end test.

---

### Task 8: This week's deal email as a Kit draft

Waits on: Mauricio's deal (route, dates, price per person, where and when found). Recipients: the segment ID if Jeff created the segment, else the tag fallback.

**Files:**
- Create: `/Users/jeffrey/Sandbox/Flight-Bridge/scripts/deals/<deal-id>.json`

- [ ] **Step 1: Make the link.** Open `https://deals.flight-bridge.com/traverse-tours/build.html`. If the domain is not on yet, use the github.io address instead. The builder always outputs a `deals.flight-bridge.com` link either way. Enter Mauricio's deal. Copy the link.

- [ ] **Step 2: Set the recipients.**
  - Segment route: `curl` Kit `GET /v4/segments` with the API key header and find "Sign-ups (both forms)". Put its `id` in `recipients.segment_id`.
  - Tag route (Jeff said "use the tag", or no segment exists): run `python3 scripts/kit_deal_email.py tag-signups`. Expected: "Tagged N sign-ups", N about 9. Put `24350319` in `recipients.tag_id`.

- [ ] **Step 3: Draft the content and write the deal file.** Write the destination name, two short info paragraphs and one travel tip about the destination (REQ-NL-002 format: destination, info, tip). Facts only: nothing you cannot check, no made-up stats. Subject and preview text short and plain, no paid-tier words. Fill the deal block from Mauricio's message, using city names. Save as `scripts/deals/<deal-id>.json` using the format in Task 6.

- [ ] **Step 4: Preview locally.** Run `python3 scripts/kit_deal_email.py preview scripts/deals/<deal-id>.json`, open the preview HTML in Chrome at phone width, screenshot it.

- [ ] **Step 5: Push the draft.** Run `python3 scripts/kit_deal_email.py push scripts/deals/<deal-id>.json`, then `status`. Expected: `"status": "draft"`, `"send_at": null`, the sender `deals@traversetours.flight-bridge.com`, and the filter naming the segment or tag 24350319. If status is anything other than draft, stop and tell Jeff. If Kit rejects the segment filter (an error naming `subscriber_filter`), switch to the tag route in Step 2 and push again.

- [ ] **Step 6: Commit the deal file** in the parent repo (add the file by name). Message: "Deal email draft: <deal-id>".

- [ ] **Step 7: Review loop.** Tell Jeff: "Draft is in Kit. Please press Send test, to Mauricio and yourself." When Mauricio replies with changes, edit the JSON, run `push` (it clears any recorded OK), commit, and ask Jeff for a fresh test. Repeat until Mauricio is happy. The content review does not need HTTPS; nobody clicks the button until the Task 7 gate passes.

---

### Task 9: End-to-end test, approval, and send

Waits on: the Task 7 HTTPS gate, the Gmail forwarding rule (Task 1 part D), Mauricio being available.

**Files:**
- Modify: `scripts/deals/<deal-id>.json` (`mauricio_ok`)

- [ ] **Step 1: End-to-end test.** Ask Jeff to:
  1. Press Send test in Kit, to himself.
  2. On his phone, open the test email and tap Book Now. Check the deal shows correctly.
  3. Submit with his own name and a real address he can read.
  4. Reply to the test email with "test reply".

  Ask Mauricio to confirm three things: the request arrived at info@ (Junk and Quarantine if not); Viktor created a JourneyFuse lead with Jeff's address, not the Web3Forms address; the "test reply" arrived at info@ from Jeff's address. If Viktor missed it, the email still goes, and Mauricio handles requests by hand until the wording is fixed (spec section 10).

- [ ] **Step 2: Broken link test.** Claude opens `https://deals.flight-bridge.com/traverse-tours/?v=1&from=SL` in Chrome, submits with name `TEST broken link (ignore)` and a message, and asks Mauricio to confirm it arrived.

- [ ] **Step 3: Send-day re-check.** Mauricio re-checks the deal against its source. If price or dates changed: rebuild the link (Task 8 Step 1), update the JSON, `push`, and Jeff sends a new test and taps the button again.

- [ ] **Step 4: Record the OK.** When Mauricio gives his written OK on the final test email, put his words, who passed them on, and the time in `mauricio_ok` (for example `"OK, send it (Mauricio by text to Jeff, 2026-10-15 13:05)"`). Run `status` and confirm the OK shows. Commit. Do not run `push` after this point; a push clears the OK.

- [ ] **Step 5: Jeff sends.** Tell Jeff: "Mauricio's OK is recorded. In Kit, open the draft. Check the recipients show the sign-ups segment (or the landing-page-confirmed tag) and a count of about 9, not 1,338. Then press Send." If the count is wrong, stop and tell Claude.

- [ ] **Step 6: Confirm it went.** Run `status`. Expected: status no longer `draft`. Tell Jeff it went and how many it went to.

---

### Task 10: Record the outcome in both repos

Follow each repo's CLAUDE.md: YAML front matter updated, IDs kept, sources cited as "Working session 2026-10-13/14, Book Now launch spec" plus the spec path. Before adding any new ID, read the file and take the next free number.

**Booking repo (`/Users/jeffrey/Sandbox/Flight-Bridge-Booking-Engine`):**

- [ ] `docs/booking-engine/deal-links.md`: replace the section 3 format with the live v1 format (deal ID in `deal=`, `found=`, `title=` for packages, `return` optional for one way). Section 2: domain decided, `deals.flight-bridge.com/traverse-tours/`. Section 5: answer all four open items (domain; no pre-fill; packages use `type=package` and `title=`; per person, USD assumed). Status to Active.
- [ ] `product-decisions.md`: one new decision for the Phase 1 stack (own page on GitHub Pages at deals.flight-bridge.com, Web3Forms to info@flytraverse.com), with the alternatives from spec section 3.
- [ ] `backlog.md`: BE-FB-010 to Complete, with the live URL. Update the deal landing page item's dependency on Q-BE-007.
- [ ] `open-questions.md`: resolve Q-BE-007 per the CLAUDE.md rule (remove it and point to `deal-links.md`).
- [ ] `assumptions.md`: new assumption, deal prices are in USD.
- [ ] `risks.md`: add the Web3Forms 250-a-month limit with the mid-November check (spec section 10), if not already covered.
- [ ] `project-state.md`, `docs/ai/CURRENT_STATE.md`, `docs/ai/NEXT_TASK.md`: Book Now live, first deal email sent (date), Jeff's Friday spot-check still open.
- [ ] Spec and this plan: status to Active.

**Parent repo (`/Users/jeffrey/Sandbox/Flight-Bridge`):**

- [ ] `docs/newsletter/workflows.md` and DEC-NL-013: Mauricio now supplies the weekly deal (no AI run for now); Mauricio reviews by test email and replies with changes instead of editing in Kit (approval rule 2); Claude builds drafts with `scripts/kit_deal_email.py`.
- [ ] CONF-NL-005: resolved. Replies to deals@ are forwarded to info@flytraverse.com by a Gmail filter on owner@.
- [ ] Content strategy and REQ-NL-002: the "Deals you missed" footer is dropped until paid deals exist.
- [ ] Launch plan and roadmap: first free deal email sent (date).

- [ ] **Commit each repo separately**, adding files by name. In the parent repo, never add the two 10-08 transcripts.

- [ ] **Report to Jeff** in a few lines: what is live, the two URLs, what was recorded where, and what is still open (Friday spot-check). Leave the call on "done" to him.
