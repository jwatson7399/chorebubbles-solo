# ChoreBubbles Solo direction

This repository is the independent single-person fork of ChoreBubbles.

## Boundary

- All solo-oriented product and data-model work belongs in this repository.
- The original `/Users/julian/Claude Code/chorebubbles` repository remains the Kristine/Julian shared-household application.
- This repository intentionally has no Git remote until a separate destination is chosen.
- The initial fork runs local-only under its own storage ID; Supabase configuration and deployment credentials must not be reused without an explicit migration decision.

## Preserve

- Living bubble mechanics, urgency growth, dragging, and release behavior
- Chore importance, effort, frequency, history, and last-done state
- Two-step alternating chores
- Rolling seven-active-day effort zones
- Chore suggestions, vacation pauses, cleaning-service resets, and offline support

## Convert

1. Done — replaced the paired Julian/Kristine identity model with one editable owner profile.
2. Done — replaced dual tallies and teamwork totals with one rolling tally and solo streak.
3. Done — new completions use one `owner` identity; paired choices are absent from the interface.
4. Done — simplified onboarding, vacation mode, history copy, and goal suggestions.
5. Done — added a solo-specific Supabase row, one-email allowlist, and migration guidance.
6. Partly external — the app has its own package, manifest, local storage ID, and no remote; a new repository and deployment destination still need to be chosen.

Legacy `a`, `b`, and `joint` records remain backward-readable and count once toward the solo owner's history and tally.
