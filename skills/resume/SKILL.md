---
name: resume
description: Generate a market-specific resume (AU / CN / DE / US) from one set of
  career facts, using the prism LaTeX engine. Triggers when the user wants a resume,
  CV, or Lebenslauf, or wants to re-target an existing resume to another country.
---

# Skill: Market-Aware Resume Builder

## What this skill does
The student writes their career facts ONCE in `your-profile.md`. This skill then
generates a resume tailored to a target job market — because Australia, China,
Germany, and the US each have completely different conventions (photo? length?
personal details? language? signature?). Same facts, different presentation.

## When to trigger
- "make me a resume / CV / Lebenslauf"
- "adapt my resume for Germany / China / a US company"
- "which sections should I drop for the Australian market?"

## Inputs
1. `your-profile.md` — the student's raw, market-neutral career data.
2. `markets/<country>/rules.md` — the conventions for the chosen market.
3. `markets/<country>/template.tex` — an authentic, per-market LaTeX template
   (AU = the prism engine; DE = a proper tabellarischer Lebenslauf; etc.).
4. `examples/*-sample.tex` — full worked examples (fictional persona, style reference).

## Architecture (per-market templates)
Each market has its OWN real template, because resume formats differ too much to
fake from one engine (photo, page length, tabular layout, signature, language).
The single source of truth for *content* is `your-profile.md`; the skill maps
those facts into the right template for the target market.

## Steps the agent follows
1. Ask the student for the **target market** (australia / china / germany / usa).
2. Read `your-profile.md` + `markets/<country>/rules.md` + `markets/<country>/template.tex`.
3. Fill the template with the student's facts:
   - keep the template's layout, section order, and language;
   - convert each achievement to `verb + what + measurable result`;
   - drop/keep photo, personal details, and signature per `rules.md`.
4. Output the `.tex` and tell the student how to turn it into a PDF (below).

## Template sourcing & licensing
Templates bundled here are self-authored or permissively licensed (keep any
required attribution in the file header). For markets where you prefer a specific
community template, DON'T copy its code in — instead point the student to its
Overleaf link and have the agent generate the fill-in content to paste. This
avoids redistributing third-party template code.

## Turning the .tex into a PDF  (pick per student)
- **Option A — Prism (recommended default, free, no install):**
  https://prism.openai.com — a free AI LaTeX editor (any ChatGPT account, no
  subscription or seat limits). Paste the `.tex` in → it compiles to PDF in the
  browser. AI-native, handles CJK, and is the same tool this template was built
  with. Best fit for a mixed / non-technical cohort.
- **Option B — Overleaf (alternative, no install):** paste the `.tex` into a new
  Overleaf project → Recompile → Download PDF. Free tier is enough. For Chinese
  text set the compiler to **XeLaTeX** and use `\usepackage{ctex}`.
- **Option C — Local compile via the agent:** *if* the student already has a LaTeX
  distribution (TeX Live / MiKTeX) installed, the agent can run
  `pdflatex resume.tex` (or `xelatex` for CJK) directly. Claude Code cannot render
  LaTeX by itself — it needs that toolchain on the machine.
- **Fallback — no LaTeX at all:** the agent outputs a clean Markdown/DOCX version
  instead. Trade-off: less typographic polish than the prism LaTeX output.

## Portability note (Claude Code vs Codex)
See `usage-claude.md` and `usage-codex.md` for how to invoke this same skill in
each agent. Content is identical; only the invocation differs.
