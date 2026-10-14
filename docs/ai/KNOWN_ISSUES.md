# Known Issues

## Documentation

- **Phase numbering disagrees across sources** (CONF-BE-004). Roadmap uses the 09-24 sequence until Jeff confirms (Q-BE-018).
- **Corrected decisions need sign-off:** DEC-BE-002, DEC-BE-003, DEC-BE-012 are Needs Review. See `docs/booking-engine/migration-notes.md`.
- **Transcript speaker labels are unreliable** in R1205 (almost everything labeled Mauricio) and FS. Attributions there are flagged in the digests.
- **Some recordings are cut off:** FS, EM and AV end mid-conversation. Later discussion may be missing.
- **PNR import is tracked in two repos** (BE-FB-002 here, CRM-FB-004 in the parent). Ownership open (Q-BE-008).

## Risks to watch

- Two Stripe accounts exist (Flight Bridge's and Kit's Express). Matters if bookings ever take payment (RISK-BE-012).
