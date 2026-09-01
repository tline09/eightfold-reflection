# The Noble Eightfold Path — Reflection Dashboard

A quiet, single-file tool for reflecting on the eight factors of the Buddhist
Noble Eightfold Path. You rate how consciously you currently live each factor
on a scale of 1–5, add a short note, and revisit over time. The dashboard turns
those sessions into a radar chart, a per-factor breakdown, and a trend line so
you can see — at year's end, or whenever — where you have grown and where there
is still room.

It is **not a test and not a score to optimise.** It is a friendly mirror for
an honest check-in with yourself.

> The interface is bilingual: **German and English**, switchable via a toggle
> in the top-right corner. German is the default. The eight factors, their
> reflection questions, the introduction and the written review all switch
> language; your own notes are never translated and stay exactly as you wrote
> them. Factor titles show the common English names in English mode and the
> German names in German mode; the Pali terms are shown throughout.

## Screenshot

Open `index.html` to see: a Dharmachakra (eight-spoked wheel), your overall
average, a short introduction, an eight-axis radar chart, a detailed list with
your notes and the change since last time, and a trend chart across sessions.

## Features

- **Works on phone and desktop** — responsive layout: full-width buttons and
  larger touch targets on small screens, shortened radar labels so nothing is
  clipped, and a bottom-sheet style note-history dialog. The PDF export keeps
  the full labels regardless.
- **Bilingual interface (DE / EN)** — a top-right toggle switches the entire UI,
  including the reflection questions and the written review. Your notes are
  never translated.
- **Eight factors, three groups** — Wisdom, Ethical Conduct, Mental Discipline.
- **1–5 self-rating with notes** for each factor, using the original reflection
  questions.
- **Radar chart** for a single session and a **trend line** across all sessions.
- **Change indicators** (▲ / ▼) versus the previous session on every factor.
- **Note history per factor** — tap any factor to read all your past notes for
  it, newest first. Seeing your own words over months is where the insight is.
- **Year-end reflection** — a gentle, rule-based written summary of where you
  stand and how you have moved. Fully offline; no AI service, no network.
- **Gentle reminder** — a quiet line telling you how long since your last
  session. No push notifications, no nagging.
- **Print / PDF** — two exports. **“Save as PDF”** builds a laid-out report of
  the selected session (title page with the wheel, radar chart, all eight
  factors with questions and your notes, the trend chart and the written
  review). **“Whole year as PDF”** builds an archive of every session: an
  overview page (wheel, period, trend, review) followed by each factor's full
  note history across all sessions — ideal for a year-end record. Charts are
  embedded as images taken from their canvas, so they appear reliably, including
  offline. Falls back to the browser's print dialog if the PDF library isn't
  available.
- **Local, private storage** — sessions are saved in your browser via
  `localStorage`. No server, no account, no tracking; nothing leaves your device.
- **Export / import** your data as a JSON backup. Export saves *all* sessions
  (every date, score and note) to a single file; import restores them on another
  browser or device. Import **replaces** the current data rather than merging,
  so it restores exactly the sessions in the file.
- **Reset everything** — one button clears all stored sessions and returns to
  the empty starter (with a confirmation prompt), for a clean handover.
- **Single file, no build step.** The only external dependency is Chart.js from
  a CDN.

## Usage

1. Download `index.html`.
2. Open it in any modern browser (double-click, or drag it into a browser tab).
3. Click **“+ Neuer Durchgang”** (new session), rate each factor 1–5, add notes,
   and save.
4. Repeat every few weeks or months. The trend appears once you have two or more
   sessions.

Because data is stored per browser, use **“Sicherung exportieren”** (export
backup) if you want to keep your data long-term or move it elsewhere, and
**“Sicherung laden”** (load backup) to restore it.

### A note on storage

`localStorage` is tied to the specific browser and device, and to how the file
is opened. If you open the file from a sandboxed preview pane (rather than
directly in a browser), the browser may block storage; the dashboard detects
this and shows a hint pointing you to the export button. Opening the file
directly in a normal browser resolves it.

Because the data lives in the browser, it can be lost if you clear your
browser's site data or use private/incognito mode, and it does not sync between
devices. Export a backup now and then — especially after adding a session, and
at year's end — and keep the file somewhere safe. Your data is never uploaded
anywhere; a shared or published copy of the tool always starts empty, so your
own reflections stay private.

## Deploying on GitHub Pages

This is a static site, so GitHub Pages hosts it as-is:

1. Create a repository and add these files at its root.
2. In **Settings → Pages**, set the source to your default branch, root folder.
3. Your dashboard will be live at `https://<username>.github.io/<repo>/`.

## Customising

- **The eight factors and questions** live in the `GLIEDER` array near the top of
  the `<script>`. Each entry has German and English fields (`nDe`/`nEn`,
  `gDe`/`gEn`, `qDe`/`qEn`) plus the Pali term and a colour key. Edit them there —
  everything else (form, charts, detail list) is generated from it.
- **UI strings** for both languages live in the `T` dictionary just below
  `GLIEDER`. To add a third language, add another block there and a matching
  button in the header.
- **The starter session** is the `SEED` array. It ships as a single empty
  placeholder (all values 1, no notes, today's date) so a new user starts clean;
  the first real session you save replaces it automatically. Edit `SEED` if you
  want a different starting point.
- **Theme colours** are CSS custom properties in `:root` at the top of the
  `<style>` block.
- **Fully offline:** remove the Chart.js `<script>` tag and the two chart
  sections if you want zero external requests; the rating, notes, and detail
  list still work.

## Tech

Plain HTML, CSS and vanilla JavaScript in one file. Charts by
[Chart.js](https://www.chartjs.org/); PDF export by
[jsPDF](https://github.com/parallax/jsPDF). Both load from a CDN. No framework,
no build tooling. The Pali diacritics are transliterated to ASCII in the PDF
only (the built-in PDF font has no glyphs for them); on screen they display in
full.

## License

Released under the MIT License — see [LICENSE](LICENSE). Do whatever you like
with it; sharing with friends is warmly encouraged.

## A word on the content

The reflection questions come from a personal worksheet on the Noble Eightfold
Path (*Ariya Aṭṭhaṅgika Magga*). They are meant as gentle prompts, not doctrine.
If you adapt this for your own practice or tradition, that is entirely in its
spirit.
