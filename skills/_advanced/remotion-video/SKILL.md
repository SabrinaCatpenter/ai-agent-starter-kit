---
name: remotion-video
description: (ADVANCED) Turn a video brief into a short branded video with Remotion
  (React-based programmatic video). Triggers when the user wants to make a video, intro,
  promo, or animated explainer. Needs Node — take-home, not for live non-technical use.
tier: advanced
---

# Skill: Remotion Video  (advanced / take-home)

Make a short, branded video **programmatically** with [Remotion](https://www.remotion.dev)
— you describe it, the agent builds a React video project, and it renders to MP4.

The groundwork is basically the **website brief** plus video specifics (script, scenes,
duration, aspect ratio, music). Reuse the same brand answers.

## Why it's ADVANCED, not core
Remotion needs **Node** and renders via a headless browser + ffmpeg (bundled). Great as a
take-home for keen students; do **not** run it live for a non-technical cohort. Instructor
can demo the output.

## Licensing (tell the student)
Remotion is **free for individuals, non-profits, and for-profit teams of up to 3 people**
— including commercial videos. A **company license is required for for-profit
organisations of 4+ people**. If the student is building this for such a company, they need
a license: https://www.remotion.dev/docs/license

Fonts, images, and **music** must be free-for-commercial too (see the website skill's font
rule; for audio use royalty-free / your own — never copyrighted tracks).

## Inputs
1. `video-brief.md` — brand + script/scenes + format (fill this once).
2. Remotion's own scaffolded starter (created below) as the base project.

## Setup (student does this at home) — confirm commands at remotion.dev/docs
```bash
# scaffold a Remotion project (creates a starter with a preview studio)
npx create-video@latest
cd <project>
npm run dev          # opens Remotion Studio to preview live
# ...build the composition, then render:
npx remotion render  # outputs an MP4
```
Don't copy Remotion's template code into this kit — use their scaffolder (keeps you on the
current version and clear of licensing).

## Steps the agent follows
1. Read `video-brief.md`.
2. Scaffold a Remotion project with `npx create-video@latest`.
3. Set the **composition** from the brief:
   - **Aspect ratio → dimensions:** 16:9 = 1920×1080 · 9:16 = 1080×1920 · 1:1 = 1080×1080.
   - **fps** (30 default) and **duration** → `durationInFrames = seconds × fps`.
4. Build the video: one `<Sequence>` per scene from the script; apply brand colours and
   a license-checked font; animate with `interpolate` / `spring` per Remotion docs.
5. Preview in Remotion Studio (`npm run dev`); iterate with the student.
6. Render to MP4 (`npx remotion render`) and hand over the file.

## Constraints
- Keep it short (15–60s) — programmatic video gets slow to iterate when long.
- Only free-for-commercial fonts, images, and audio.
- No copyrighted music or clips.

## Showcase & inspiration (not a student setup)
A full programmatic-video pipeline — **voice-cloned bilingual voiceover** (IndexTTS2) +
**AI-generated music** (MusicGen) + an animated **"talking mascot"** (a transparent PNG +
mouth animation + audio sync in Remotion) — can produce finished videos like those at
**https://www.youtube.com/@GreatMonkeyLab**. Show these as the ceiling of what's possible.

Positioning: the TTS/BGM parts use **heavy local models tied to a specific machine**, and
voice cloning raises consent questions — so this is an **instructor showcase / take-home
inspiration, NOT a live student setup**. If a student wants voiceover or music, point them
to free online tools instead of local models. The "talking mascot" *technique* (image +
animated mouth + `<Audio>` sync) is lightweight and reusable, but the mascot itself is a
brand asset — don't ship someone else's character.

## Honest note
This skill is **doc-driven and not rendered-verified in the kit** (rendering needs the full
Node/Remotion toolchain). The agent should follow the current Remotion docs for exact API.
