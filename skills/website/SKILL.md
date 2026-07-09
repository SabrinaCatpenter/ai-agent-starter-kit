---
name: website
description: Build a single, self-contained, responsive personal or project website
  from a filled-in brief. Triggers when the user wants a website, landing page,
  portfolio, or personal site. Collects a brand brief first, then generates the HTML.
---

# Skill: Brief → Self-Contained Website

## What this skill does
The student fills `brief.md` (name, sections, brand, fonts, contact, references).
The agent then generates ONE self-contained, responsive HTML file (inline CSS/JS,
no build step) the student opens by double-clicking. Ship first with placeholders,
refine later.

## When to trigger
- "make me a personal website / portfolio / landing page"
- "build a one-page site for my project"

## Flow
1. If `brief.md` is blank, walk the student through it question by question — don't
   generate until Section A (name + goal) and B (sections) are answered. Everything
   else can default.
2. Read `brief.md`.
3. Generate `<sitename>.html` following the build rules below.
4. Tell the student how to preview (below), and which fields still hold placeholders.

## Build rules (non-negotiable)
- **One file, self-contained:** inline all CSS and JS; no external build. Fonts load
  from Google Fonts (or self-hosted); no other external requests.
- **Responsive:** mobile-first, fluid layout (flex/grid), `max-width:100%` images.
- **Light/dark:** honour `prefers-color-scheme`; add a toggle if the brief asks for both.
- **Accessible:** semantic HTML5 landmarks, alt text on images, visible focus states,
  and body/background contrast that meets **WCAG AA (≥ 4.5:1)**.
- **Share metadata:** `<title>`, meta description, and Open Graph / Twitter tags so
  links preview nicely on LinkedIn / WeChat. Favicon from the brief (emoji or image).
- **Placeholders:** anything missing in the brief becomes a clearly-marked placeholder,
  never a blocker.

## Brand integration (optional — plugs into brand-voice-generator)
If the student has a `brand.json` (from the `brand-voice-generator` skill), use it as the
brand source and skip asking Section C of the brief. Real schema:
- `colors.gradient` (4 hex), `colors.accent` / `accent_secondary` / `accent_tertiary`,
  `text`, `text_secondary`, `card_bg`, `card_bg_alt`, `code_bg` → map to the site's CSS
  variables (accent, surfaces, text). A gradient makes a natural hero background.
- `fonts.heading_en` / `body_en`, plus `heading_cn` / `body_cn` (e.g. Noto Sans SC) for
  Chinese, and `fonts.code` (e.g. JetBrains Mono). These are already OFL/free.
- `assets.logo` for the wordmark / logo image.
A `brand.json` overrides the brief's Brand section so every skill stays visually consistent.

## Font licensing (hard rule)
Use only fonts that are free for commercial use.
- **Allowed by default:** Google Fonts (all OFL/Apache) and known OFL families.
- If the brief names a **proprietary** font, DON'T use it — swap a free look-alike and
  say so in a comment and to the student:
  - Helvetica / Arial → Inter, Arimo, Figtree
  - Gotham / Proxima Nova → Montserrat, Mona Sans
  - Futura → Jost   ·   Circular → Manrope   ·   SF Pro → Inter
  - Garamond → EB Garamond
- Record the chosen font's license (OFL/Apache) in an HTML comment.

## Image licensing (hard rule)
Only the student's own images or free-license images. Never embed copyrighted images.
When none are supplied, use CSS/gradient placeholders or a generated text card — not
a random web image. Note any required attribution in the footer or a comment.

## Bilingual option
If the brief asks for an EN/中文 toggle, put both languages in the markup (e.g.
`data-en` / `data-zh` attributes or two content blocks) and a small JS toggle button;
keep it in the single file. Use a CJK-capable free font for the Chinese text (e.g.
Noto Sans SC).

## Contact handling on a static site
No backend exists. Use a `mailto:` link by default. If the brief chose a form, wire it
to a form service (e.g. Formspree) and tell the student they need a free account +
their form endpoint — the site can't receive submissions on its own.

## Previewing  (same options as the slides skill)
- **Double-click the .html** — opens in any browser (needs internet for Google Fonts).
- **Local server** (more reliable / needed if you split assets out):
  ```bash
  python -m http.server 8000   # from the folder with the .html
  # open http://127.0.0.1:8000/<sitename>.html
  ```
- **Deploy:** drop the file into GitHub Pages or Netlify (drag-and-drop) — it's static.

## Portability note (Claude Code vs Codex)
Identical content and output in both agents; only the invocation differs.
