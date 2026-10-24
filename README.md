# Lab Equipment Checkout

A single-file web app for the **Human–Technology Interaction Lab (HTIL)**, UA Department of
Computer Science, to track lab equipment checkouts — who has each item, what type it is, and when it
was returned.

Requested by Dr. Crawford (email, Oct 2026), for the ROS2 / TurtleBot lab:

> "Please create a checkout survey for the lab. The survey should keep track of who has checkout
> equipment, when it was returned, and the type of equipment checked out."

## What it does

- **Check out** — record name, CWID, email, equipment type (TurtleBot 4, LiDAR, cameras, dev boards,
  etc. + custom), quantity, checkout date, optional expected-return date, and notes.
- **Return** — pick any item that's currently out and record the return date + condition.
- **Dashboard** — live count of items out, an **overdue** count (expected return passed), and the
  list of every item currently out with days-out.
- **Record log** — full history, filterable (All / Out / Returned) and searchable by name, CWID, or
  equipment. **Export CSV** for spreadsheets or reports.
- **Overdue flagging** — set an expected return date and overdue items are highlighted in the list
  and log.

## Design

- Single self-contained `index.html` (inline CSS/JS, no build step, no dependencies).
- Mobile-first and responsive: one column on phones, wider centred column on tablet, full-width
  layout on desktop. Clean/minimal (Linear-style), no external assets.

## Data & storage

Records are stored in the browser's `localStorage` on the device that enters them. This suits a
**single shared station** (e.g. a tablet or laptop at the lab bench). It is **not** a shared
multi-user database — a record entered on one phone is not visible on another.

**Next step if you want it shared across everyone:** wire the same UI to a shared backend —
either a Google Sheet via an Apps Script Web App (free, no server) or Netlify Functions + Blobs.
Exports to CSV already work today, so a spreadsheet is easy to keep in parallel.

## Files

- `index.html` — the whole app.
- `.nojekyll` — tells GitHub Pages not to run Jekyll.

## Deploy

Static site → GitHub Pages. See the `netlify-deploy` skill, § GitHub Pages variant.
