---
name: create-your-own-skill
description: >-
  Interview the student about a job they want their agent to do, then scaffold a brand-new
  skill folder for it. Triggers when the user wants to build/make/create their own skill,
  automate something personal, or "make the agent do X for me" that no existing skill covers.
---

# Skill: Create Your Own Skill  (the meta-skill)

This is the heart of the kit. The other skills are **worked examples**; this one lets the
student build an **unlimited number of their own** — for their life, study, side project,
or job. Read `../../SKILL-ANATOMY.md` first: every skill is the same six parts.

## When to trigger
- "I want to make my own skill for X"
- "can the agent do <some personal, repeated task> for me?"
- "automate <thing> — turn it into a skill"

## How it works: interview → scaffold → test
Don't ask for everything at once. Walk the student through the six parts with plain
questions, one topic at a time, then generate the folder.

### 1. Find the job (Trigger + purpose)
Ask:
- "What's a task you do repeatedly that you'd like the agent to handle?"
- "When should the agent reach for this — what would you say to invoke it?"
Turn the answer into a skill `name` (kebab-case) and a trigger `description`.

### 2. Inputs (Context)
Ask: "What information does it need each time? What stays the same vs changes per use?"
→ decide what goes in a `your-input.md` (the changing content) vs baked into instructions.

### 3. Output (Format)
Ask: "What exactly do you want back — an email? a file? a post? a diagram? what format?"
→ if the output has a fixed shape, plan a `template.*` file.

### 4. Rules (Constraints)
Ask: "Anything it must always do, or never do? Length, tone, things to avoid?"

### 5. Show, don't tell (Examples)
Ask: "Do you have one good example of the result?" If yes, save it under `examples/`.
If not, generate a plausible one *with the student* so the agent has something to imitate.

## Then scaffold the folder
Create `skills/<name>/`:
```
skills/<name>/
├── SKILL.md          # filled from the interview (all six parts)
├── your-input.md     # the context fields, ready to fill (if needed)
├── template.*        # only if the output has a fixed shape
└── examples/         # the worked example(s)
```
Base `SKILL.md` on `skills/_template/SKILL.md`. Write the `description` as a real trigger
("…triggers when the user wants X").

## Then test it immediately
Run the brand-new skill once, end to end, with the student's real input, and show them the
result. Fix the instructions or example until the output is good. **A skill isn't done
until it's produced one good result.**

## Coaching notes (keep the student learning, not just receiving)
- Push for a **narrow** job. "Manage my life" is not a skill; "turn my meeting notes into
  a task list" is. Narrow skills work; broad ones flail.
- Make them articulate the **trigger** — it's the part people skip and the one that makes a
  skill usable.
- Reuse the **content/engine split**: fill content once, reuse the engine forever.
- One good example beats a page of instructions — invest in the example.

## Output
A new, working skill folder under `skills/`, tested with the student's own input, plus a
one-line summary of what it does and how to invoke it.
