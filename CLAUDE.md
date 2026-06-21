# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

Single-page static wedding website for Lucía & Raúl (October 10, 2026, Monterrey). The entire site lives in one file: `index.html`, which contains all HTML, CSS, and JavaScript inline. No build step, no framework, no bundler.

## Serving locally

Open `index.html` directly in a browser, or serve with any static server:

```bash
open index.html
# or
npx serve .
# or
python3 -m http.server 8080
```

## URL parameters

The page is personalized via query string parameters:

| Parameter | Effect |
|-----------|--------|
| `nombre`  | Guest name shown in RSVP greeting |
| `invitados` | Number of guests; populates the WhatsApp RSVP message |
| `civil=si` | Shows the "Ceremonia Civil" row in the schedule (hidden by default) |

Example: `index.html?nombre=Ana&invitados=2&civil=si`

## Architecture

Everything is in `index.html`:

- **CSS** — custom properties (`--bg`, `--accent`, etc.) defined in `:root`. No external stylesheet.
- **JavaScript** — two blocks at the bottom of `<body>`:
  1. Countdown timer to `2026-10-10T17:00:00-06:00`.
  2. URL param reader that personalizes the RSVP section and controls the civil ceremony row visibility.
- **Media** — all photos live in `media/fotos/`. Adding or replacing images only requires updating the `src` attributes in the HTML.

## Key element IDs

| ID | Purpose |
|----|---------|
| `countdown` | Countdown timer container |
| `rsvp-greeting` | Guest name greeting text |
| `rsvp-count` | Guest count inside RSVP button |
| `btn-rsvp` | WhatsApp RSVP link |
| `row-civil` | Ceremonia Civil schedule row (hidden unless `civil=si`) |
