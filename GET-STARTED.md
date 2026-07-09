# Get Started (5 minutes)

## You need
- **Claude Code** or **Codex** installed and working.
- That's it for the core skills. Some advanced skills need extras (Node, Obsidian) —
  each `SKILL.md` says so.

## 1. Load the kit
Copy the skill folders you want into your project's `.claude/skills/` (Claude Code) —
or keep the whole kit as a folder your agent can read.

## 2. Set your agent's identity
Open `agent.profile.md` and fill it in — purpose, who it serves, your style. Do this first;
the skills all serve this profile.

## 3. Try a skill
Pick one and just ask your agent, e.g.:
- "Make me an Australian resume" → `resume` (fill `your-profile.md` first)
- "Turn these notes into a blog post and a LinkedIn post" → `content`
- "Build me a personal website" → `website` (fill `brief.md`)
- "Make a slide deck about my project" → `slides`

The agent reads the skill's `SKILL.md`, asks for the input file, and produces the output.

## 4. Build your OWN skill (the real goal)
Ask: **"help me make my own skill for &lt;your task&gt;"** → runs `create-your-own-skill`.
It interviews you (what job? when to trigger? inputs? output?) and scaffolds a new skill
folder, then tests it once. Keep the job **narrow** — narrow skills work, broad ones flail.

## 5. Go further (optional)
- Set up a brand once (`brand.json` + `tone-of-voice.md`) so website/content/slides match.
- Run your kit in a local always-on agent with OpenClaw (see the `openclaw-runtime/` folder).

## Stuck?
- A skill won't trigger? Its `description` is the trigger — make it say "…triggers when
  the user wants X". See `SKILL-ANATOMY.md`.
- 7-day support after the workshop: see `openclaw-runtime/support/`.
