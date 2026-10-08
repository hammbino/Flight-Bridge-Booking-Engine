# /checkpoint

Update project state before /compact.

This is a mid-task checkpoint.

Update:

- docs/ai/CURRENT_STATE.md
- docs/ai/NEXT_TASK.md
- docs/ai/DECISIONS.md
- docs/ai/IDEAS.md
- docs/ai/KNOWN_ISSUES.md

Rules:

1. Summarize project state, not conversation history.
2. Keep files short.
3. Preserve only what is needed to continue.
4. Move future ideas to IDEAS.md.
5. Move bugs, risks, or technical debt to KNOWN_ISSUES.md.
6. Do not mark incomplete work as complete.
7. Do not update COMPLETED_TASKS.md unless work is actually complete.

End with:

- What changed
- Whether safe to run /compact
- Exact next step after compacting.
