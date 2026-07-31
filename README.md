# Synthesis 2026 — DevSoc Tech Summit

Event promotion and registration site for **Synthesis 2026**, a two-day campus tech summit hosted by
DevSoc and the School of Management and Information Technology at De La Salle-College of Saint Benilde.

**Live:** https://nyrrine.github.io/BenildeHackathon/

## What it does

- **Hero** — masthead headline, event facts, and a live countdown to 18 September 2026, 09:00 (UTC+8).
- **Programme** — two-day tabbed schedule, filterable by track, with each session expanding to a
  description. Fourteen sessions across Engineering, Design, Career and Workshop tracks.
- **Speakers** — six speakers; each card opens a detail dialog that links back to that speaker's
  slot in the programme.
- **Registration** — a "Register now" call to action opens a modal capturing name, student number,
  Benilde email, course, year level, days attending, track interests, dietary needs and consent.
  On submit it issues a confirmation code, saves the pass to `localStorage`, and offers a real
  `.ics` calendar file generated in the browser.

## Design

The whole site is built to a **broadside poster** brief: one hundred percent warm monochrome, no
chromatic accent anywhere, all emphasis carried by type scale and full-bleed paper-to-ink inversion.

| | |
|---|---|
| Paper | `#fafafa` |
| Ink | `#2a2722` |
| Radius | `12px`, everywhere, nothing else |
| Shadows | none — hierarchy comes from scale, inversion and 1px rules |

Type is the brand: **Fraunces** for editorial display serif, **Antonio** for the ultra-condensed
section mastheads, **Inter** for all UI at 12–32px. Sections alternate between paper and ink bands
like a broadsheet. Schedule tracks are distinguished by *border treatment* — solid, dashed, dotted,
double — rather than by colour, so the monochrome rule holds without losing the distinction.

## Running it

There is no build step. Clone and open `index.html`, or:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## Notes

- Single self-contained `index.html`. No framework, no bundler, no dependencies beyond Google Fonts.
- Registration is client-side only — it persists to `localStorage` and does not hit a server. Wiring
  it to a real backend means replacing the `setTimeout` in the submit handler with a `fetch`.
- Both dialogs trap focus, close on Escape and backdrop click, lock body scroll, mark the background
  `inert`, and return focus to the element that opened them.
- Every animation is disabled under `prefers-reduced-motion: reduce`.
- Speaker names, affiliations and session descriptions are fictional placeholders for the demo.
