---
name: language-lock
description: (GIFT · Claude Code only) Stop the well-known bug where Claude Code drifts
  out of Chinese into Japanese or Korean mid-session. A Stop hook checks each finished
  reply and, on UNINTENDED drift, makes Claude rewrite it in the language you're using.
tier: gift
---

# Skill: Language Lock  (gift · Claude Code only)

## The problem this fixes
For East Asian users, Claude Code sometimes **drifts out of the language you're using**
— you're working in Chinese and a whole reply comes back in Japanese or Korean,
usually after tool calls or context compaction. It's a documented bug
(github.com/anthropics/claude-code issues #57212, #30025, #46846). The built-in
language setting helps but doesn't always hold.

This is **Claude Code only** — it uses Claude Code hooks, which Codex doesn't have.

## It follows you — it does NOT lock you (default: mirror mode)
Despite the name, the default snippet does **not** trap you in one language. It's a
consistency guard: it checks that each reply is in **the language you used in your
last message**. So:

- You write Chinese → reply must be Chinese (drift to Japanese/Korean gets fixed).
- You switch to English → an English reply is fine, no correction.
- You ask for Japanese, or for a translation/quote → allowed.

You change language any time just by changing yours; the guard follows. It only
corrects *unintended* drift.

## How it works — two layers: prevent + catch
Drift clusters right after context compaction (the anchor "use Chinese" gets weakened
when context is compressed). So the snippet uses two hooks that complement each other:

**1. Prevent — a `UserPromptSubmit` hook (cheap, no LLM).** Before each of your
messages, it echoes a one-line reminder into Claude's context: "reply in the language
the user just used; don't drift to Japanese/Korean." `UserPromptSubmit` stdout is added
to context, so this keeps the language anchor fresh every turn — especially valuable
after a compaction. It's a nudge, not a guarantee, but it's essentially free.

**2. Catch — a `Stop` hook (`type: "prompt"`, Haiku judge).** After each finished
reply, a small model checks the message — no regex needed:
- Reply matches the language you're using → `{"ok": true}` → nothing happens.
- Reply drifted into an unrequested language (kana / hangul) → `{"ok": false, "reason": ...}`
  → Claude **rewrites the whole message** in the language you're using.

Because `Stop` returning `ok:false` feeds the reason back to Claude, this fixes the
transcript and ongoing context — not just what's on screen.

**Together:** the prevent layer lowers how often drift happens; the catch layer fixes
whatever slips through. The only real cost is one regeneration on the rare turns where
drift still occurs.

## Install (student does this once)
1. Open your Claude Code settings file:
   - global: `~/.claude/settings.json`   (all projects)
   - or per-project: `.claude/settings.json`
2. Merge in the contents of `settings.snippet.json` from this folder (if a `hooks`
   block already exists, add the `Stop` entry alongside your others).
3. Restart Claude Code (or start a new session). Done.

Tip: the `update-config` skill / `/config` can help you edit settings safely.

## Turn it on / off  (the switch)
Hooks are just settings, so the on/off switch is simple:
- **Off for everything:** delete the `Stop` block (or the whole snippet) from your
  settings file, or rename the key `"Stop"` to `"Stop_disabled"`, and restart.
- **On only where you want it:** put the snippet in a **project** `.claude/settings.json`
  instead of the global `~/.claude/settings.json`. It then applies only in that project.
- There's no per-message toggle, but you don't need one: in the default mirror mode you
  simply switch languages and the guard follows.

## Optional: hard-lock variant (only if you truly want one fixed language)
If you specifically want every reply forced into one language regardless of what you
type, replace the prompt with a hard-lock version:

> "Every assistant reply must be in Simplified Chinese. If the latest reply is not,
>  respond {\"ok\": false, \"reason\": \"Rewrite the entire message in Simplified
>  Chinese.\"}; otherwise {\"ok\": true}. Allow English/technical terms, code, and
>  proper nouns."

Use this only deliberately — it *will* fight you when you try to write in another
language. Mirror mode (the default) is the safer choice for most people.

Kana (ひらがな/カタカナ) and hangul (한글) are the reliable drift tells, because Chinese
and Japanese share many characters (kanji/hanzi) — so the guard keys on the writing
systems that are unambiguous.

## Why not the MessageDisplay hook?
A `MessageDisplay` hook can rewrite what you *see*, but it's display-only: it doesn't
fix the transcript or the context Claude carries forward, so the next reply keeps
drifting — and truly translating would need its own model call inside a 10s timeout.
Use the `Stop` approach as the real fix; treat MessageDisplay as at most a cosmetic
patch.

## Optional: make it cheaper / stricter
- Add `"model": "<a-model-id>"` to the hook to use a stronger judge than the default
  Haiku (rarely needed).
- Keep the hook scoped to `Stop` only — don't broaden it; you only want to check
  finished replies.
