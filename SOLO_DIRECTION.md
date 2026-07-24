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

1. Replace the paired Julian/Kristine identity model with one owner profile.
2. Replace dual effort tallies and teamwork totals with one rolling tally.
3. Remove joint and “other person” completion attribution.
4. Simplify onboarding, vacation mode, history copy, and goal suggestions for one person.
5. Create solo-specific Supabase authorization and schema migration guidance.
6. Give the solo app its own deployment target, household data, and GitHub repository.

The first implementation pass should keep stored chore and completion records backward-readable while removing paired-person choices from the interface.
