# 7-Day Post-Workshop Support

This is where students go to get unstuck in the week after the workshop. It's part of the
value of the paid packages (in-person standard + online), and especially matters for
online and Chinese-speaking participants.

## How support works
- **Window:** 7 days after the workshop.
- **Channel:** <fill in — support group / email / chat link>.
- **Language:** English-first, with **中文 support / Q&A** available.
- **Scope:** getting your take-home kit working, building your own skill, and (optional)
  installing OpenClaw. Out of scope: production deployments, unrelated coding help.

## Fastest self-help first
1. **The kit doesn't need OpenClaw.** If a local runtime is fighting you, drop it — your
   skills still run inside Claude Code / Codex. Ship the kit, add OpenClaw later.
2. **Read the error, then the docs.** For OpenClaw, https://docs.openclaw.ai; for a skill,
   re-read its `SKILL.md`.
3. **Ask your agent.** Paste the exact command + error into Claude Code / Codex.

## FAQ

**"My skill doesn't trigger."** The `description` in `SKILL.md` is the trigger — make it
say "…triggers when the user wants X". Vague descriptions don't fire. See
`../SKILL-ANATOMY.md`.

**"LaTeX won't compile / I don't have LaTeX."** Use Prism (https://prism.openai.com, free)
or Overleaf — no install. See the resume skill's compile options.

**"reveal.js / my website is blank on double-click."** Some browsers restrict `file://`.
Run a local server: `python -m http.server 8000` and open `http://127.0.0.1:8000/...`.

**"Claude keeps switching to Japanese/Korean."** Install the `language-lock` gift skill
(a Stop + UserPromptSubmit hook). See `../skills/_gift/language-lock`.

**"OpenClaw install failed."** Check Node is 24 (or 22.19+), or use the Docker route. Then
re-run `openclaw onboard`. Confirm steps at https://docs.openclaw.ai/install.

**"How do I make a skill for my own task?"** Run `create-your-own-skill` — it interviews
you and scaffolds it. Keep the job narrow.

## Escalation
If self-help + the FAQ don't resolve it, post in the support channel with: what you tried,
the exact command, and the full error message.
