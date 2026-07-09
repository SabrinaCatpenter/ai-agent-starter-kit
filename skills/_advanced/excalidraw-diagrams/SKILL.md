---
name: excalidraw-diagrams
description: (ADVANCED) Generate editable Excalidraw diagrams — flowcharts, mind maps,
  system architectures — from a natural-language description, then drop them into an
  Obsidian vault. Wraps an existing open-source skill; not for live non-technical use.
tier: advanced
---

# Skill: Excalidraw Diagrams  (advanced / take-home)

## Status: wrapper, not rebuilt
We DON'T reimplement this. Excalidraw's JSON (arrow binding, labels, layout) is
fiddly and an existing skill already does it well:

- Source: **coleam00/excalidraw-diagram-skill**
  https://github.com/coleam00/excalidraw-diagram-skill

**Licensing:** the source repo does **not** declare a license (= all rights
reserved by default). So do **not** copy its code into this kit or redistribute it,
especially in a paid workshop. Point students to the repo to install it themselves,
and confirm terms with the author before bundling. Keep this attribution.

## Why it's ADVANCED, not core
Setup is heavier than the other skills — it needs **Python (uv) + Playwright +
Chromium** to render/validate diagrams. That's fine as a take-home for keen
students, but do **not** run it live in the workshop for a non-technical cohort.

## Install (student does this at home)
1. Download/clone the repo above.
2. Copy it into your project's `.claude/skills/` directory and rename the folder to
   `excalidraw-diagram`.
3. From its `references/` folder run the one-time setup:
   ```bash
   uv sync
   uv run playwright install chromium
   ```

## Use
Ask the agent naturally, e.g.:
> "Create an Excalidraw diagram showing how my study-agent kit turns notes into
>  flashcards."

It generates the Excalidraw JSON (`.excalidraw`) and renders a PNG preview,
validating the layout before delivery.

## Using the output in Obsidian
The generated file is a standard Excalidraw file. To edit/annotate it in your notes:
1. Install the **Excalidraw** community plugin in Obsidian.
2. Put the `.excalidraw` file into your vault (or the PNG for a static image).
3. Open it — the plugin renders and lets you keep editing by hand.

Note: this is manual — the source skill has no built-in Obsidian integration; it just
produces standard Excalidraw files that the Obsidian plugin understands.

## Where this fits
Pairs with the Obsidian knowledge-base advanced track: generate a diagram of an idea
or system, then store and refine it inside your vault.
