# Next Task

## Objective

Finish the Book Now launch: plan Tasks 7 (rest) to 10 in `docs/superpowers/plans/2026-10-14-book-now-launch.md`. Read the ledger's last lines first: `.superpowers/sdd/2026-10-14-book-now-launch/progress.md`.

## Steps, each waiting on its input

1. **Task 7, rest** (needs the Web3Forms key and Viktor's words):
   - Put both in `traverse-tours/config.js` in flight-bridge-deals. Commit and push.
   - Send one test request from Chrome, named "TEST Claude (ignore)".
   - Mauricio confirms it arrived at info@.
2. **Task 8** (needs Mauricio's deal, plus the segment or "use the tag"):
   - Make the link with build.html.
   - Set the `SIGNUP_SEGMENT` constant, or run `tag-signups` and use tag 24350319.
   - Write `scripts/deals/<deal-id>.json`.
   - Run preview, then push, then status. Expect draft, with send_at null.
3. **Task 9** (needs Gmail forwarding and Mauricio free):
   - Run the end-to-end test and the broken-link test.
   - Record Mauricio's OK. No pushes after that.
   - Jeff checks recipients are about 9, not 1,338, then presses Send.
   - Confirm with status.
4. **Task 10:**
   - Record the outcome in both repos.
   - Delete the workspace.
   - Present the result to Jeff for review.

## Success criteria

The deal email goes to the sign-ups only. A test Book Now request reaches info@flytraverse.com and becomes a JourneyFuse lead. Mauricio gave his OK before Send.

## Rules

- Never print the Kit key.
- Jeff is the only one who presses Send.
- Do not push the parent or booking repo without asking.
- Never put a github.io link in an email.
