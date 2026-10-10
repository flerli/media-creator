---
name: swaibian-video-producer
description: Use when producing, editing, checking, or rendering any Swaibian video or HyperFrames composition in the media-creator repo — site promos, explainers, motion graphics, decks, title cards. Covers the repo's multi-project layout, brief/plan/preview/render gates, offline audio engines, and the verified environment.
---

# Swaibian video producer

Repo: `media-creator` — Swaibian's production house for media. HyperFrames
turns HTML into deterministic MP4s. This is the playbook: the repo's layout,
how work flows, and which gates are non-negotiable.

## 1. First read — mandatory

1. The HyperFrames router: load the `/hyperframes` skill if available;
   otherwise read `~/.agents/skills/hyperframes/SKILL.md`. It routes every
   "make me a…" request to the owning workflow. Read the matched route file
   (`~/.agents/skills/hyperframes/references/routes/<workflow>.md`) and install
   the workflow before executing it:
   `npx hyperframes skills update <workflow>`.
2. The project's truth layers for the piece you are on, in order:
   `BRIEF.md` → `STORYBOARD.md` → `frame.md` → `compositions/`.

Never write composition HTML from memory. The HyperFrames domain skills
(`hyperframes-core`, `hyperframes-animation`, `hyperframes-keyframes`,
`hyperframes-creative`, `media-use`, `hyperframes-audio`, `hyperframes-cli`,
`hyperframes-registry`) own the authoring contracts — load the ones the active
workflow names, plus their cited rule/blueprint bodies before writing motion.

## 2. The repo

`media-creator` manages **several** video projects — one self-contained
HyperFrames project per video under `videos/<project>/`. Run every HyperFrames
command with the project folder as the working directory; nothing video-related
lives at the repo root.

- `videos/swaibian-one-promo/` — built + delivered 25.0s promo for
  https://one.swaibian.com. Layout: `index.html` (6 frame slots + root audio),
  `compositions/frames/01-hook…06-cta.html`, `capture/` (real site capture with
  screens, tokens, assets), `assets/fonts/inter-var.woff2`,
  `assets/bgm/track.wav`, `beats/`, `snapshots/`, `renders/video.mp4`,
  `audio_request.json` + `audio_meta.json`.
- Each project's truth layers: `BRIEF.md` → `STORYBOARD.md` → `frame.md` →
  `compositions/`. The swaibian one brand tokens live in
  `videos/swaibian-one-promo/frame.md` (Inter, bundled; ink `#111827` on light
  canvas; green `#10A37F`; purple `#7C3AED`; soft tints).
- Each project has its own `.media/preferences.json` (project-tier memory) and
  its own pinned `package.json` scripts.
- Repo root: `README.md`, `AGENTS.md`, `project_management/` (V-Model product
  work — media tasks never modify it), `.opencode/` (agents + this skill).

## 3. Where new work lives

- Edit requests on the swaibian-one promo → edit
  `videos/swaibian-one-promo/` in place; never re-scaffold over it.
- A new stand-alone video → `npx hyperframes init videos/<kebab-name>
  --non-interactive --example=blank --skill=<workflow>` (from the repo root),
  then run every subsequent command with `videos/<kebab-name>` as its working
  directory.
- Reusable swaibian one material (brand tokens, captured assets, fonts) comes
  from `videos/swaibian-one-promo/`; other brands get captured or defined
  fresh inside their own project.

## 4. Environment facts (verified 2026-10-10)

- macOS; Node v23; ffmpeg at `/Applications/ffmpeg`; **ffprobe installed** at
  `/Applications/ffprobe` (`/Applications` is on PATH) — render/media probing
  needs it.
- HeyGen: signed out. Local engines: BGM = MusicGen via the shared audio
  engine; Kokoro TTS NOT installed (`pip install kokoro-onnx soundfile` to
  enable); whisper-cpp NOT installed (import SRT/JSON, or
  `brew install whisper-cpp`); Lyria generation is policy-blocked on the
  current Google key — force MusicGen with
  `GEMINI_API_KEY= GOOGLE_API_KEY= node ~/.agents/skills/media-use/audio/scripts/audio.mjs …`.
- Before any authenticated provider action run `npx hyperframes auth status`
  and relay it; if signed out, ask sign-in vs continue offline (question tool).
- `npx hyperframes usage --json` reports unknown (`unsupported_harness`) — say
  usage is unknown; never guess an allowance.
- CLI pins live in the project's `package.json` scripts. After bumping a pin,
  re-verify with `npm run check` and name the old/new versions in the summary.

## 5. Golden path — the gates are not optional

All commands below run with the project's folder (`videos/<project>/`) as the
working directory.

1. **Brief.** Fresh creation → run the router's intent layer: memory
   (`node ~/.agents/skills/media-use/scripts/prefs.mjs get --hyperframes .`),
   route, must-haves, then the two run-shape questions (storyboard?;
   automation vs companion) as separate asks. Never build without a confirmed
   brief. `BRIEF.md` records it and is the no-repeat token.
2. **Design.** Resolve `frame.md` → `design.md` → `DESIGN.md`; if none exists,
   create one from brand capture tokens before any HTML.
3. **Plan.** `STORYBOARD.md` — one bulleted block per frame with its cited
   blueprint/rules. When `storyboard: yes`, sketch every frame into
   `storyboard.html` (real fonts/colors/copy, no motion) and lock layouts only
   after user confirmation.
4. **Audio early.** Start BGM/TTS generation in the background as soon as the
   mood/script is known — shared engine at
   `~/.agents/skills/media-use/audio/scripts/audio.mjs` via
   `audio_request.json`; run `wait-bgm.mjs` before assembly. Music-only pieces
   use volume `0.9`; under narration `0.12` and carve the bed
   (`hyperframes-audio`).
5. **Build.** Sub-compositions under `compositions/frames/` (template wrapper,
   IIFE script, prefixed ids, `window.__timelines[<id>]`); root `index.html`
   stays thin (slot divs + root audio + near-empty root timeline). Follow the
   workflow's build order and read each cited rule body before its motion.
6. **Check.** `npm run check` must pass (it includes lint). Fix findings; the
   `data-layout-*` attributes are only for genuinely intentional layout
   choices. Inspect `npx hyperframes snapshot` contact sheets at frame
   midpoints and ±0.1s around every cut; fix any visible pop before rendering.
7. **Preview gate.** `npx hyperframes preview --background`; hand the user the
   Studio URL and ask the one question: render now, or what changes? Render
   only after explicit approval.
8. **Render + verify.** `npm run render -- --quality high --output
   renders/<name>.mp4`; verify the file with ffprobe (duration, streams);
   deliver path + real duration + frame ids; relay the render's desktop-app
   line; offer the recipe freeze once (`recipe.mjs freeze --name <name>`).
   Leave the preview running and say how to stop it
   (`npx hyperframes preview --stop`); stop it yourself when the review ends.

## 6. Standing rules

- Use the `question` tool for every user decision — concrete options, the
  recommended one first and labeled "(Recommended)"; plain-text questions only
  when no option list is possible. Never batch unrelated fields into one ask
  beyond what the intent layer allows.
- Deterministic compositions only: no render-time clocks, no unseeded
  randomness, no render-time network fetches for required assets. The skills
  own the details — when a conflict appears, the skill wins.
- Keep scope exact: build what was briefed and offer additions before adding
  them.
- Never commit or push. Never overwrite project files unrelated to the ask.
- Keep capture assets, audio, fonts, and rendered outputs in-repo; clean up
  temp files you created outside the project.
