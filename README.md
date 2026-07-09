# AI Agent Starter Kit

A take-home kit from the **[Great Monkey Lab](https://www.youtube.com/@GreatMonkeyLab)**
AI Agent Workshop. You leave with a reusable AI workflow asset — not just general AI
tool knowledge.

The kit is a set of **skills** (each a folder that teaches your agent to do one job well)
plus the tools to **build your own**. Use it inside **Claude Code** or **Codex**.

## Start here
1. Read **[SKILL-ANATOMY.md](SKILL-ANATOMY.md)** — every skill is the same 6 parts.
2. Fill **[agent.profile.md](agent.profile.md)** — who your agent is.
3. Try a skill (below), then build your own with **`create-your-own-skill`**.

## Skills

### Build your own (the point of the kit)
| Skill | What it does |
|---|---|
| `create-your-own-skill` | Interviews you and scaffolds a brand-new skill for your own need. |
| `_template/` | Blank skill to copy by hand. |

### Core (hands-on)
| Skill | Output |
|---|---|
| `resume` | Market-aware CV — Australia / China / Germany / USA (LaTeX → PDF). |
| `slides` | reveal.js deck from markdown (or PPTX). |
| `website` | Self-contained responsive personal site from a brief. |
| `content` | Blog post + LinkedIn post from one markdown source. |

### Advanced (take-home)
| Skill | Note |
|---|---|
| `_advanced/excalidraw-diagrams` | Diagrams (wraps an open-source skill). |
| `_advanced/remotion-video` | Programmatic video (needs Node). |
| `_advanced/obsidian-kb` | AI-assisted knowledge base + YouTube→notes. |

### Gift
| Skill | Note |
|---|---|
| `_gift/language-lock` | Stops Claude Code drifting Chinese→Japanese/Korean (Claude Code only). |

## Optional: run it live (openclaw-runtime/)
The **[openclaw-runtime/](openclaw-runtime/)** folder is the *optional* upgrade path —
running your skills in a local always-on agent with OpenClaw, the end-of-workshop demo,
and the 7-day support notes. **The kit works without it** — it's not a dependency.

## Brand hub (optional)
If you have a `brand.json` + `tone-of-voice.md` (from a brand-voice-generator), the
`website`, `content`, and `slides` skills read them so everything stays on-brand.

## Install into your agent
- **Claude Code:** copy the skill folders you want into `.claude/skills/` in your project
  (or `~/.claude/skills/` for all projects). Restart / start a new session.
- **Codex:** each skill's `SKILL.md` is portable — follow its "portability note".

See **[GET-STARTED.md](GET-STARTED.md)** for the 5-minute walkthrough.

## License & credits
Kit content: MIT (see [LICENSE](LICENSE)). Third-party tools (Excalidraw skill, YouTube
importers, Remotion, OpenClaw, Obsidian) are **linked, not bundled** — install them from
their own sources under their own licenses.
