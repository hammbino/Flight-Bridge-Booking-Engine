# Flight Bridge Booking Engine

Flight booking for Traverse Tours, powered by Flight Bridge. It is built on Traverse's direct Sabre access and tickets under Traverse's ARC, with a human agent following up on every booking.

This repo was split out of [Flight-Bridge](https://github.com/hammbino/Flight-Bridge) on 2026-10-07. The Newsletter and CRM stay there.

## Status

Documentation, plus a clickable demo page (`demo/`, sample fares, not connected to Sabre). No booking code yet. See `docs/booking-engine/project-state.md`.

## Where things are

| Path | What |
|------|------|
| `CLAUDE.md` | Repo standards and the agent "start here" map |
| `docs/booking-engine/` | Knowledge base: requirements, decisions, roadmap, questions, backlog |
| `docs/booking-engine/migration-notes.md` | What changed in the split, including corrections to review |
| `demo/index.html` | Clickable demo of the booking flow. Notes in `docs/booking-engine/demo.md` |
| `docs/sources/` | Booking-only digests of every source conversation, with timestamps |
| `docs/ai/` | Short working-state files for the `/start`, `/build`, `/checkpoint`, `/finish` commands |
| `Transcripts/` | Drop new raw transcripts here, then run `/process-transcripts` |

## Claude commands

`/start`, `/build`, `/review`, `/checkpoint`, `/finish`, `/process-transcripts`. Skills: `project-state`, `scoped-build`, `session-handoff`.
