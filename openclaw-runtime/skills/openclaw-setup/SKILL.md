---
name: openclaw-setup
description: Bridge skill — install and configure OpenClaw (a local-first personal AI
  agent runtime) from inside Claude Code / Codex, and run a bespoke starter-kit skill
  in it. Triggers when the user wants to install, set up, or configure OpenClaw, or
  deploy their agent kit locally.
---

# Skill: OpenClaw Setup (bridge)

## Purpose
Claude Code can usually *install* OpenClaw fine — what trips students up is the
**configuration** (what the options mean, which model to point it at, which channels,
where the workspace and sandbox are). This skill has the agent do the install AND walk
the student through configuration in plain language. It is deliberately **doc-driven**:
OpenClaw changes, so the agent reads the current official docs for exact values instead
of trusting hardcoded config here.

**Especially for Codex users:** follow the ordered checklist below literally and read
the linked docs before editing any config — do not guess field names.

## Authoritative sources (read these at setup time)
- Repo: https://github.com/openclaw/openclaw
- Docs: https://docs.openclaw.ai  (Install, Onboarding, Configuration, Channels)
Have the agent fetch the relevant docs page for any exact command, flag, or config key
before running it, and confirm the current version's requirements.

## Known-good facts (verify against docs, but these are the baseline)
- **Runtime:** Node 24 recommended (or 22.19+).
- **Install (recommended, auto-detects OS + installs Node + onboards):**
  - macOS/Linux: `curl -fsSL https://openclaw.ai/install.sh | bash`
  - Windows PowerShell: `iwr -useb https://openclaw.ai/install.ps1 | iex`
- **Install (via npm), then onboard:**
  ```bash
  npm install -g openclaw@latest
  openclaw onboard --install-daemon
  ```
- **Docker (always-on):**
  ```bash
  docker run -d --name openclaw --restart unless-stopped \
    -v ~/.openclaw:/root/.openclaw -p 18789:18789 ghcr.io/openclaw/openclaw:latest
  ```
- **Web UI:** http://localhost:18789
- **Config & memory:** `~/.openclaw`   ·   **Agent workspace:** `~/openclaw/workspace`

## Steps the agent follows
1. **Check prerequisites:** Node version (24 / 22.19+), or Docker if going that route.
2. **Install** using one method above (default: the installer script; Docker if the
   student wants always-on).
3. **Run onboarding** (`openclaw onboard`) and, reading the official Onboarding/Config
   docs, help the student make these choices — explained plainly:
   - **Model / provider:** which LLM it uses + API key, OR a local model (e.g. Ollama)
     for a no-key setup. *For the workshop, prefer a local model or a sandbox key.*
   - **Channels:** start with **WebChat only** (the built-in web UI). Do NOT wire up
     WhatsApp / WeChat / Telegram during the workshop — those need real accounts and
     add risk. Add channels later at home.
   - **Workspace / sandbox:** point the agent at a **dedicated sandbox folder** with no
     real personal data, secrets, or production keys (matches the kit's safety rule).
   - **Daemon:** install the always-on daemon only if the student wants it running 24/7.
4. **Load a starter-kit skill:** copy one skill from the agent-starter-kit into the
   OpenClaw workspace so it can run there, per the OpenClaw docs on tools/skills.
5. **Verify:** open http://localhost:18789, send a test message in WebChat, confirm the
   agent responds and can use the loaded skill.

## Safety rules (match the workshop's risk control)
- Sandbox workspace only — no personal Gmail/calendar, production keys, or sensitive files.
- WebChat-only during the session; external messaging channels are a take-home extra.
- Prefer a local model or a throwaway/sandbox API key for the demo.

## If something fails
Don't loop. Read the relevant docs page, report what failed (command + error), and fall
back to the instructor demo — the starter kit itself does not require OpenClaw to be
running (that's the whole point of the take-home kit).
