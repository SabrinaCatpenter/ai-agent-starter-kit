---
name: obsidian-kb
description: (ADVANCED) Turn an Obsidian vault into an AI-assisted knowledge base — the
  agent summarises, tags, and links each note, and (gift) pulls YouTube transcripts in.
  Triggers when the user wants to organise notes, build a knowledge base, or process
  notes/transcripts. Feeds the content skill. Needs Obsidian (free).
tier: advanced
---

# Skill: Obsidian Knowledge Base  (advanced / take-home)

Make your notes work for you: the agent reads a note and adds a short **summary**, useful
**tags**, and **[[links]]** to related notes. Over time this becomes a searchable,
connected knowledge base you can draw content from.

## Scope — read this first (avoid the knowledge-graph rabbit hole)
- **Obsidian already gives you the graph.** Its built-in backlinks and Graph view build
  the "knowledge graph" from your `[[wikilinks]]` automatically — you don't need AI for that.
- **The AI's job is narrow:** per note, *suggest* a summary + tags + links to existing
  notes. Do **not** try to build a fully-automatic, self-maintaining knowledge graph — it's
  fragile and a time sink. Suggestions per note, human stays in control.

## When to trigger
- "organise my notes / build a knowledge base"
- "summarise and link this note"
- "pull this YouTube video into my notes"

## Setup (student does this at home)
1. Install **Obsidian** (free) and create a **vault** (just a folder of `.md` files).
2. Point Claude Code / Codex at the vault folder.
3. Open Obsidian's **Graph view** (built-in) to see notes connect as links accumulate.

## Note-assistant flow
For a given note, the agent:
1. Reads the note and scans the vault's existing note titles/filenames.
2. Proposes **frontmatter tags**, a **1–2 line summary** at the top, and **`[[links]]`** to
   the most related existing notes (see `note-template.md`).
3. Shows the changes and **asks before editing** — never silently rewrites your notes.

## Gift: pull YouTube transcripts into the vault
Don't rebuild this — two ready-made options (link, don't bundle):
- **YouTube Transcript Fetcher** — Obsidian community plugin, installs in-app, grabs the
  transcript + timestamps: https://community.obsidian.md/plugins/youtube-transcript-fetcher
- **YouTube Transcript to Obsidian** — a Claude Code skill (yt-dlp based):
  https://mcpmarket.com/tools/skills/youtube-transcript-to-obsidian
Then run the note-assistant on the imported transcript to summarise, tag, and link it.

## Closes the loop with the `content` skill
This is the "採集 → 整理 → 生成" pipeline: notes/transcripts land in Obsidian, get
summarised and linked here, then feed the **`content`** skill to draft a blog post or
LinkedIn post from your own knowledge. The knowledge base is the hub; content is the output.

## Constraints
- Sandbox / your own vault only — no confidential notes you don't want an agent reading.
- Ask before editing notes; keep the student's words, add structure around them.
- Suggest links only to notes that actually exist — don't invent references.

## Honest note
Doc-driven; not verified end-to-end in the kit (needs a real Obsidian vault). Obsidian's
markdown, `[[wikilinks]]`, tags, and Graph view are standard — confirm plugin specifics in
Obsidian's community plugin browser.
