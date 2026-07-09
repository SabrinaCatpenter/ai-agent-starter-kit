# OpenClaw Runtime

The **optional, take-home runtime** for the AI Agent Starter Kit. This repo is where
"make it actually run" lives — the end-of-workshop demo and the 7-day support path.

It is deliberately kept as an optional subfolder of the [starter kit](../README.md): the
kit is the guaranteed deliverable (skills you build and keep, no infrastructure). This
repo is the *optional* next step — running those skills in your own local agent with
[OpenClaw](https://github.com/openclaw/openclaw).

## What's here
| Folder | What it is |
|---|---|
| `skills/openclaw-setup/` | Bridge skill: install + configure OpenClaw from Claude Code / Codex (rescues Codex users on config). |
| `examples/scheduled-pm-agent/` | Demo: a scheduled "remind me / do this daily" agent — shows what an always-on runtime adds. |
| `setup/` | Optional install notes (Node / Docker / local model). |
| `support/` | 7-day post-workshop support: FAQ + troubleshooting. |

## How it's used in the workshop
- **Minutes 2:40–3:00 (Runtime Demo):** the instructor demos installing OpenClaw and
  running a bespoke kit skill locally, then shows the scheduled PM agent as "look what
  an always-on runtime can do."
- **After class (7-day support):** students who want to go further follow
  `skills/openclaw-setup` at home; `support/` is where they get unstuck.

## Important
Running OpenClaw is **never required** to complete the workshop. The starter kit works
on its own inside Claude Code / Codex. This repo is the upgrade path, not a dependency.

## Links
- OpenClaw repo: https://github.com/openclaw/openclaw
- OpenClaw docs: https://docs.openclaw.ai
