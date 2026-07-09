# Demo: Scheduled "PM" Agent

A short end-of-workshop demo showing the one thing an **always-on runtime** adds that
Claude Code / Codex alone don't: **it can act on a schedule, without you prompting it.**

This is the "look what it can do" moment — not something students set up live.

## What it shows
A personal project-manager agent that, running inside OpenClaw's always-on daemon:
- **Reminds** you to do things at set times ("stand-up at 9am", "submit the report Friday").
- **Runs a task on a schedule** (e.g. every morning, summarise today's tasks from a notes
  file in the sandbox workspace).
- **Reaches you on a channel** (start with WebChat; messaging channels are a take-home extra).

The point students take away: *the same bespoke skills you built become proactive once
they live in an always-on agent.*

## How it's built (concept — confirm exact config in the OpenClaw docs)
OpenClaw is a local-first, always-on gateway with a daemon, a workspace, and an event
system — which is what makes scheduled/triggered behaviour possible (unlike a chat session
that only runs when you type). The moving parts:

1. **Install + daemon:** OpenClaw running with its daemon (see `../../skills/openclaw-setup`).
2. **A skill:** a small "daily plan / reminders" skill in the workspace that reads a
   tasks file and produces a plan or reminder message.
3. **A schedule / trigger:** configured via OpenClaw's scheduling / events mechanism so the
   skill fires at the chosen time.
4. **A channel:** WebChat for the demo (http://localhost:18789).

> ⚠️ The exact scheduling config (cron-style entries, event definitions, field names) must
> come from the current OpenClaw docs — https://docs.openclaw.ai — not from this file.
> Have the agent read the Scheduling/Events docs and set it up from there.

## Safety (same rules as the kit)
- Sandbox workspace only — no real calendar, email, or production keys in the demo.
- WebChat only during the session; wiring WhatsApp/WeChat/Telegram is a take-home step.

## Why this lives in the runtime repo, not the starter kit
Scheduling needs a running daemon = infrastructure. The starter kit stays infra-free and
guaranteed; anything that must "keep running" lives here as an optional upgrade.
