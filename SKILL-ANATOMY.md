# Skill Anatomy — the 6 parts of every skill

A "skill" is just a folder that teaches your agent to do **one job well, the same way
every time**. Every skill in this kit — and every skill you build — has the same six
parts. Learn them once; they apply to all skills.

| # | Part | The question it answers | Example |
|---|------|--------------------------|---------|
| 1 | **Trigger (When)** | When should the agent use this skill? | "when I ask for a resume / CV" |
| 2 | **Prompt / Instructions** | What should it actually do? | "fill the template, one achievement per bullet" |
| 3 | **Context** | What background must it know? | your profile, a target market's rules |
| 4 | **Examples** | What does good output look like? | a worked resume it can imitate |
| 5 | **Constraints** | What must it NOT do / limits? | "no photo for the AU market; ≤ 2 pages" |
| 6 | **Output format** | What exactly is delivered? | a compilable `.tex` file |

> The **Trigger** is the part beginners forget and the one that matters most — a skill
> the agent never knows to use is useless.

## How the 6 parts map to files in a skill folder

```
skills/<your-skill>/
├── SKILL.md         # parts 1, 2, 5, 6 live here (trigger, instructions, constraints, output)
├── your-input.md    # part 3 — the context you fill in once
├── template.*       # part 6 — the shape of the output (optional)
└── examples/        # part 4 — worked examples to imitate
```

`SKILL.md` starts with frontmatter — the `name` and a `description`. The **description
is the trigger**: it's how the agent decides this skill is relevant, so write it as
"…triggers when the user wants X".

```markdown
---
name: my-skill
description: What it does. Triggers when the user wants <X>, or asks to <Y>.
---
```

## The golden rule
Separate **content** (facts that change per person/use — part 3) from the **engine**
(the fixed instructions and template — parts 2 & 6). Fill content once; reuse the engine
forever. Every skill here is built this way: `your-profile.md` + a template, `brief.md`
+ build rules, `source.md` + shaping rules.

## Where to go next
- Copy `skills/_template/` to start a new skill by hand.
- Or run the **`create-your-own-skill`** skill and let the agent interview you and
  scaffold it for you.
