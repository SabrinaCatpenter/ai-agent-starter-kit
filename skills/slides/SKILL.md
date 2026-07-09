---
name: slides
description: Turn a plain-markdown outline into a polished, self-contained reveal.js
  slide deck the student can open by double-clicking. Triggers when the user wants
  slides, a deck, a presentation, or to pitch a project/idea visually.
---

# Skill: Markdown → reveal.js Slide Deck

## What this skill does
The student writes their talk as a simple markdown outline in `your-deck.md`
(slides separated by `---`). The agent injects it into `template/deck.html` and
produces a **single self-contained HTML file** the student opens by double-clicking
— no build step, no install. Presentation polish (theme, transitions, layout) comes
from reveal.js; the student only writes content.

## When to trigger
- "make me slides / a deck / a presentation about X"
- "turn these notes into a pitch deck"
- "build slides for my AI agent project"

## Inputs
1. `your-deck.md` — the student's slide content as markdown.
2. `template/deck.html` — the reveal.js shell (theme + plugins wired up).
3. `examples/ai-agent-pitch.html` — a full worked example (open it to see the result).

## Steps the agent follows
1. Read `your-deck.md`.
2. Copy `template/deck.html` and replace the `<!-- SLIDES -->` markdown block with
   the student's content (keep the `<script type="text/template">` wrapper).
3. Set the `<title>` and pick a theme (see below).
4. Save as `<name>.html` and tell the student to double-click it.

## Markdown → slides rules (reveal.js)
- `---` on its own line = new horizontal slide.
- `--` on its own line = a vertical (drill-down) sub-slide.
- Standard markdown inside each slide: `#`/`##` headings, `-` bullets, `**bold**`,
  code fences, images, links.
- Speaker notes: put `Note:` on a line, then the note text.
- Keep ~1 idea per slide and ≤ 6 bullets — decks are not documents.

## Themes
reveal.js ships themes: `white` (default, clean), `black`, `league`, `night`,
`solarized`, `moon`, `sky`. Swap the theme name in the `theme` stylesheet link.

## Output flavor — reveal.js (this skill) or PPTX (student picks)
Two ways to deliver slides; offer both:
- **reveal.js (this skill):** a self-contained HTML deck — best for web sharing, tech talks,
  embedding, and no-install double-click.
- **PPTX (PowerPoint):** best for business / classroom settings where people expect an
  editable `.pptx`. Use a PPTX-generator skill for this — drop one into `skills/` to include
  it in the kit (e.g. the Great Monkey Lab PPTX generator).
Both can read the same `brand.json` (colors/fonts) so decks stay on-brand either way.

## Opening / presenting  (pick per student)
- **Double-click the .html** — opens in any browser. Works because the slide content
  is inlined in the file. Needs internet the first time (reveal.js loads from a CDN).
  Press `F` for fullscreen, `S` for speaker view, `Esc` for the slide overview,
  arrow keys to navigate.
- **Run a local server (recommended for reliability / offline external .md):** some
  browsers restrict `file://` pages, and loading a *separate* `your-deck.md` via
  `data-markdown="your-deck.md"` needs http (a `file://` page cannot fetch it). Serve
  the folder and open it over `http://`:
  ```bash
  # from the folder that contains the .html (and your-deck.md if external)
  python -m http.server 8000
  # then open http://127.0.0.1:8000/your-deck.html in the browser
  ```
  Stop the server with Ctrl+C when done. (Any static server works — e.g.
  `npx serve` if the student has Node instead of Python.)
- **Fully offline** — download reveal.js and repoint the three CDN URLs at a local
  `dist/` copy (the workspace already contains a reveal.js checkout to borrow from),
  then serve with the local-server step above.
- **Export to PDF** — open the deck with `?print-pdf` appended to the URL (over the
  local server), then use the browser's Print → Save as PDF.

## Portability note (Claude Code vs Codex)
Content and output are identical in both agents; only the invocation differs.
