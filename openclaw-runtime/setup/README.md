# OpenClaw Setup Notes

Optional install reference. The `../skills/openclaw-setup` skill does this interactively;
this file is the quick human-readable version. Always confirm current details at
https://docs.openclaw.ai (OpenClaw changes).

## Prerequisites
- **Node 24** recommended (or **22.19+**) for the npm / native install.
- **Docker** (Desktop or Engine) + Compose v2, ≥ 2 GB RAM, for the container route.

## Install options

**A. Installer script (recommended — detects OS, installs Node, runs onboarding)**
```bash
# macOS / Linux
curl -fsSL https://openclaw.ai/install.sh | bash
# Windows PowerShell
iwr -useb https://openclaw.ai/install.ps1 | iex
```

**B. npm, then onboard**
```bash
npm install -g openclaw@latest
openclaw onboard --install-daemon
```

**C. Docker (always-on)**
```bash
docker run -d --name openclaw --restart unless-stopped \
  -v ~/.openclaw:/root/.openclaw -p 18789:18789 ghcr.io/openclaw/openclaw:latest
```

## After install
- **Web UI:** http://localhost:18789
- **Config & memory:** `~/.openclaw`
- **Agent workspace (files it can touch):** `~/openclaw/workspace`

## What to configure (in onboarding)
- **Model / provider:** an LLM + API key, or a **local model (e.g. Ollama)** for a no-key,
  fully-local setup. *For the workshop, prefer local or a sandbox key.*
- **Channels:** start with **WebChat only**. Messaging channels (WhatsApp, Telegram,
  WeChat, Slack, …) are a take-home step — they need real accounts.
- **Workspace / sandbox:** a dedicated folder with **no** personal data or production secrets.
- **Daemon:** install only if you want it running 24/7.

## Running a kit skill in OpenClaw
Copy a skill folder from the `agent-starter-kit` into the OpenClaw workspace and load it
per the OpenClaw tools/skills docs. Verify by sending a WebChat message that should
trigger it.
