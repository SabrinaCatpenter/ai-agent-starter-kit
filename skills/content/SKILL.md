---
name: content
description: Turn one markdown source (your notes or a draft) or a topic into
  platform-shaped writing — a blog post and a LinkedIn post from the same material.
  Triggers when the user wants a blog post, LinkedIn post/article, or to repurpose
  notes into content. Text only; no front-end.
---

# Skill: One Source → Blog + LinkedIn

## What this skill does
The student drops raw material into `source.md` (lecture notes, a project write-up,
a rough draft) or just names a topic. The agent extracts the core idea and reshapes
it for each platform: a **blog post** (markdown) and a **LinkedIn post** (plain text),
optionally a longer **LinkedIn article**. Output is text you paste into Medium /
Substack / Dev.to / LinkedIn — the platform renders it, so no front-end is needed.

(Want your own page instead of a platform? Use the `website` skill to render a post,
or an SSG like Astro for a full multi-post blog — that's the advanced path.)

## When to trigger
- "write a blog post about X" / "turn these notes into an article"
- "make a LinkedIn post from this" / "repurpose my draft for LinkedIn"

## Inputs
1. `source.md` — the student's raw notes / draft / topic + audience + goal + tone.
2. `examples/` — a worked source and the blog + LinkedIn posts made from it.

## Fact integrity (hard rule)
Only use facts, numbers, and claims that appear in `source.md`. Do **not** invent
statistics, quotes, or results. If a specific is missing, leave a clearly-marked
`[TODO: add ...]` placeholder rather than making something up.

## Blog post — shaping rules
- **Title** that's specific and curiosity-driving; optional one-line subtitle.
- **Open with a hook** (a problem, a surprising line, a short story) — never
  "In this article I will...".
- Structure with `##` / `###` headings, short paragraphs, one idea per section.
- Prefer concrete examples over abstraction. Optional **TL;DR** at the top.
- End with a takeaway + a soft call-to-action.
- Length ~600–1200 words. Output in markdown.
- Suggest a one-sentence **meta description** for SEO at the very end (as a comment).

## LinkedIn post — shaping rules
- **First line is everything** — it's the only line shown before "…see more". Front-load
  the hook; no throat-clearing.
- Short lines, blank line between thoughts (LinkedIn rewards whitespace).
- First person, conversational. LinkedIn strips markdown — use plain text, not `**bold**`
  or `#` headings.
- End with **one** question or CTA to invite comments, then **3–5 hashtags**.
- Sweet spot ~1300 characters (max 3000).
- Best practice: put any external link in the **first comment**, not the post body
  (LinkedIn down-ranks posts with outbound links) — tell the student this.

## LinkedIn article (optional, long-form)
Like the blog post but hosted on LinkedIn: keep a clear title, headings, and a
personal voice. Use when the student wants depth on LinkedIn itself.

## Repurposing logic
From the same `source.md`: the blog post is the full argument; the LinkedIn post is
the single sharpest insight from it + a human angle + a CTA. Keep the student's voice
and match the audience and goal stated in the source.

## Brand voice (optional — plugs into brand-voice-generator)
If the student has a `tone-of-voice.md` (from the `brand-voice-generator` skill), follow it
as the voice source — its sentence patterns and Do's/Don'ts override the generic "tone"
field. For example, the Great Monkey Lab voice is bold / technical / approachable, short
sentences, keeps English tech terms, problem-first, and **never says "this is simple"**.
Match whatever the student's `tone-of-voice.md` specifies.

## Portability note (Claude Code vs Codex)
Identical content and output in both agents; only the invocation differs.
