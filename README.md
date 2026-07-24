# ChoreBubbles Solo 🫧

ChoreBubbles Solo is an independent, single-person PWA for keeping a home in rhythm. Chores are living bubbles that swell as they become due. Completing one resets its bubble and adds its effort to one rolling seven-active-day tally.

This repository is separate from the Kristine/Julian household app. It has its own package name, PWA identity, local storage namespace, data ID, schema setup, and no Git remote by default. See [`SOLO_DIRECTION.md`](SOLO_DIRECTION.md) for the project boundary and migration notes.

## Features

- Fluid bubble field with drag, release, and tap-to-complete interactions
- Readable compact labels for small bubbles
- Importance, effort, and goal frequency per chore
- Last-done banners and full per-chore histories
- Optional two-step chores with independently configured alternating bubbles
- One rolling seven-active-day effort tally with Getting started, Maintaining, and On top of it! zones
- Goal-closing suggestions with glowing bubble highlights and an off toggle
- Previous-period recap and solo green-zone streak
- Vacation pause that freezes bubble growth and the rolling tally
- Cleaning-service and board resets without effort credit
- Local time-machine sandbox for previewing growth and effort windows
- Installable offline PWA with a durable local write queue
- Optional passwordless Supabase sync for the owner's approved email

## Local-only setup

The checked-in [`src/config.js`](src/config.js) leaves Supabase blank and uses a solo-specific data ID. In that configuration the app works on one device without a sign-in screen.

```bash
npm install
npm run dev
```

Run the test suite and production build with:

```bash
npm test
npm run build
```

## Optional Supabase sync

Create a Supabase project, enable email authentication, and add the final deployed URL (plus the local Vite URL for development) to the allowed redirect URLs.

Before running [`supabase-schema.sql`](supabase-schema.sql), replace:

- `REPLACE_WITH_YOUR_SOLO_DATA_ID` with a long random ID used only by this solo app
- `owner@example.com` with the owner's email

Then copy the project URL, anon key, and the same solo data ID into `src/config.js`:

```js
export const SUPABASE_URL = "https://xxxx.supabase.co";
export const SUPABASE_ANON_KEY = "eyJ...";
export const HOUSEHOLD_ID = "the-solo-data-id-used-in-the-sql-file";
```

The URL and anon key are public client credentials. Security comes from Supabase authentication and row-level policies; knowing the data ID does not grant access.

## Deployment and installation

1. Create a new GitHub repository for this solo app and push it to `main`.
2. In **Settings → Pages**, choose **GitHub Actions** as the source.
3. Add the deployed URL to Supabase's authentication redirects if sync is enabled.
4. Open the deployed URL in Safari and use **Share → Add to Home Screen**.

The PWA installs as **CB Solo**, independently from the shared ChoreBubbles app.

## Data behavior

New completions are stored with the single `owner` identity. If data from the shared app is deliberately imported, legacy `a`, `b`, and `joint` completions remain readable and each counts once toward the owner's history and tally. Service and board-reset events award no effort.

The operation queue remains in local storage until a configured Supabase backend confirms each write. Saves use optimistic row revisions, so the same owner can safely use more than one device.

Simulation time never enters saved data. While fast-forwarded, completions and pauses apply only to a local sandbox that is discarded on returning to today.
