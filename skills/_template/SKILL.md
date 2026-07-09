---
name: CHANGE-ME
description: >-
  <One line: what this skill does.> Triggers when the user wants <X>, or asks to <Y>.
  ^ This description IS the trigger — the agent reads it to decide when to use the skill.
---

# Skill: <Your Skill Name>

<!-- This is the blank template. Copy this whole folder to skills/<your-skill>/,
     rename it, and fill in the six parts. See ../../SKILL-ANATOMY.md for the concept. -->

## What this skill does   (part 2 — instructions)
<In 1–3 sentences: what job does the agent do, and what does the student get out?>

## When to trigger   (part 1)
- "<example thing the user might say>"
- "<another phrasing>"

## Inputs   (part 3 — context)
1. `your-input.md` — <the info the student fills in once>.
2. `examples/` — <worked example(s) to imitate>.

## Steps the agent follows   (part 2)
1. Read `your-input.md`.
2. <do the core work>.
3. <produce the output>.
4. Tell the student what was produced and any placeholders left.

## Constraints   (part 5 — what NOT to do / limits)
- <a hard rule, e.g. "only use facts from the input; never invent numbers">
- <a limit, e.g. "keep it to one page">

## Output format   (part 6)
- <exactly what is delivered — a file? text? which format?>

## Notes
- Keep **content** (your-input.md) separate from the **engine** (this file + any template).
- If your output has a fixed shape, add a `template.*` file and have the agent fill it.
