# Known Issues

## Documentation

- **Phase numbering disagrees across sources** (CONF-BE-004). Roadmap uses the 09-24 sequence until Jeff confirms (Q-BE-018).
- **Corrected decisions need sign-off:** DEC-BE-002, DEC-BE-003, DEC-BE-012 are Needs Review. See `docs/booking-engine/migration-notes.md`.
- **Transcript speaker labels are unreliable** in R1205 (almost everything labeled Mauricio) and FS. Attributions there are flagged in the digests.
- **Some recordings are cut off:** FS, EM and AV end mid-conversation. Later discussion may be missing.
- **PNR import is tracked in two repos** (BE-FB-002 here, CRM-FB-004 in the parent). Ownership open (Q-BE-008).

## Risks to watch

- Two Stripe accounts exist (Flight Bridge's and Kit's Express). Matters if bookings ever take payment (RISK-BE-012).

## Book Now launch (see ledger for full list)

- **Edits made directly in Kit's editor bypass Mauricio's OK check.** Process forbids them, and Jeff's last look before Send is the only catch (parked M4).
- **Minor items deferred by the final review**, none needed before go-live:
  - Kit script: no urlopen timeout, no 429 retry, unencoded cursor
  - footer contrast is about 3:1
  - builder: errors show on first load
- **Jeff has no access to info@.** The Friday inbox spot-check depends on Mauricio (RISK-NL-008).
- **Parent repo:** Kit script commits are not pushed. The two 10-08 raw transcripts are deliberately uncommitted (private content).
