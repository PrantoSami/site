# Editing pranto.me

This repository is Pranto Ahad's portfolio site. The whole site is one file, `index.html`. Netlify publishes the `main` branch automatically, so every commit to `main` goes live in about a minute.

## How to make changes safely

- **Small fixes (typos, a word, a date):** edit `index.html` on `main` and commit.
- **Redesigns or new sections:** create a branch (for example `redesign-poetry`), commit there, and open a pull request. Netlify posts a preview link on the pull request. Pranto checks the preview, then merges to `main` to go live.
- Never force-push to `main`. Every old version stays in the commit history, so any change can be undone.

## How the file is organized

- **Views.** Each page is a block with a `data-view` attribute: `front`, `section`, `about`, and one `<article data-view="read/SLUG">` per piece. A small script at the bottom shows one view at a time based on the URL hash (`#/read/turkey`, `#/section/poetry`, `#/about`).
- **Adding a piece takes two edits:**
  1. Add an `<article data-view="read/SLUG" class="wrap article">` block (copy an existing one of the same type).
  2. Add a matching entry to the `PIECES` array in the script, with the same `slug` and a `section` of `journalism`, `columns`, `poetry` or `fiction`. Section index pages are built from this array.
- **Front page stories** are written by hand in the `front` view. Update them separately.
- **Links that aren't full pieces** (Encounters editions, the WBMB reel, Instagram) live in the `EXTRA` object in the script.
- **Hindi-Urdu poems** have two `.verses` blocks, `data-script="deva"` (Devanagari, shown by default) and `data-script="roman"` (Roman, as first posted). Keep them line-for-line identical in structure.
- **Headshot** is embedded as base64 in the `--portrait` CSS variable.
- **Colors** are CSS variables on `:root`, with dark-mode overrides. Headlines use Schibsted Grotesk; body text uses Newsreader; Devanagari uses Tiro Devanagari Hindi.
- **Animation:** headlines in `.lead-hed` and `.article h1` get the redaction reveal automatically. Anyone with "reduce motion" on sees no animation. Keep that.

## Rules for any writing in Pranto's name

- Never change his poems or prose without asking. Punctuation, capitals and lowercase "i" are often deliberate (for example, the shifting i/I in "But I st*i*ll? do").
- Non-native English constructions in his work are voice markers, not errors.
- Copy written for him (deks, bios, blurbs): short declaratives mixed with longer sentences, contractions, em dashes rarely, no "delve / moreover / furthermore / foster / leverage / tapestry / landscape," no neat three-item lists, no summary closers.
- Byline is always "Pranto Ahad."
- When a piece first ran somewhere else, keep the "First published in…" note and link.

## Before committing

- Open the page and click every nav section, one article, the social icons, the email copy button and the Devanagari/Roman switch.
- Check a phone-width view (390px).
- Check for console errors.
