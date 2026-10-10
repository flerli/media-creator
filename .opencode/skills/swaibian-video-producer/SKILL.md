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
- `videos/swaibian-com-promo/` — the www.swaibian.com promo ("Koi Zauber"):
  cliché-kill concept, 10 frames / 58.5s, blue-professional preset remixed onto
  the captured brand (Neue Haas woffs + warm paper/petrol palette), six real
  product captures + wordmark, offline MusicGen bed with a built-in silence
  window, beat-locked durations.
- Each project's truth layers: `BRIEF.md` → `STORYBOARD.md` → `frame.md` →
  `compositions/`. The swaibian one brand tokens live in
  `videos/swaibian-one-promo/frame.md` (Inter, bundled; ink `#111827` on light
  canvas; green `#10A37F`; purple `#7C3AED`; soft tints).
- Each project has its own `.media/preferences.json` (project-tier memory) and
  its own pinned `package.json` scripts.
- Repo root: `README.md`, `AGENTS.md`, `.opencode/` (agents + this skill).

## 3. Where new work lives

- Edit requests on the swaibian-one promo → edit
  `videos/swaibian-one-promo/` in place; never re-scaffold over it.
- A new stand-alone video → `npx hyperframes init videos/<kebab-name>
  --non-interactive --example=blank --skill=<workflow>` (from the repo root),
  then run every subsequent command with `videos/<kebab-name>` as its working
  directory.
- Reusable swaibian one material (brand tokens, captured assets, fonts) comes
  from `videos/swaibian-one-promo/`; the www.swaibian.com brand kit (Neue Haas
  woffs, product captures, wordmark) lives in `videos/swaibian-com-promo/`.
  Other brands get captured or defined fresh inside their own project.

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
  and relay it. Signed out is the studio's normal state: when no credentialed
  capability is needed (no VO, local music), state the status and continue
  offline; raise sign-in vs offline at the next checkpoint only when it would
  change the output (e.g., pulling from HeyGen's music library).
- `npx hyperframes usage --json` reports unknown (`unsupported_harness`) — say
  usage is unknown; never guess an allowance.
- Capture budgets: image-heavy marketing sites (Next.js etc.) exhaust the
  default post-navigation budget — fonts/assets/vision phases degrade. Pass
  `--capture-budget 300000` (5 min) or more on the first capture and read the
  phase table; recovery recipe in §7. `www.swaibian.com` serves an incomplete
  TLS chain — `curl` needs `-k`; Chrome/capture are unaffected.
- Snapshot vision (`snapshots/descriptions.md`) may be all 403s on the current
  Google key — inspect `snapshots/contact-sheet-*.jpg` directly instead.
- `npm run check` passes on **0 errors**; expect ~40–50 warnings
  (`id_requires_css_escape`, `studio_missing_editable_id`) from the mandatory
  digit-leading `<frame_id>-` prefixes — cosmetic; don't rename the prefixes.
  `data-layout-allow-overlap` / `-overflow` silence genuinely intentional
  layout infos (glitch layering, scaled cameras, transition zooms).
- CLI pins live in the project's `package.json` scripts. After bumping a pin,
  re-verify with `npm run check` and name the old/new versions in the summary.

## 5. Golden path — the gates are not optional

All commands below run with the project's folder (`videos/<project>/`) as the
working directory.

1. **Brief.** Fresh creation → run the router's intent layer: memory
   (`node ~/.agents/skills/media-use/scripts/prefs.mjs get --hyperframes .`),
   route, must-haves, then the two run-shape questions (storyboard?;
   automation vs companion) as separate asks. Never build without a confirmed
   brief. `BRIEF.md` records it and is the no-repeat token. Record confirmed
   answers with `prefs.mjs record --hyperframes . --key <k> --value <v>`
   (`style_preset` additionally needs `--workflow <workflow>`); `prefs.mjs` has
   no `--help` — the verbs are `get --hyperframes . [--json]` and `record …`.
2. **Design.** Resolve `frame.md` → `design.md` → `DESIGN.md`; if none exists,
   create one from brand capture tokens before any HTML. After `build-frame`,
   read the output before building: (a) the colors block — a neutral key that
   took a saturated accent (the known `text-muted` → `accent2` collision) or a
   canvas that lost the brand paper is a true-need hand-fix; (b) the generated
   `@font-face` block — every needed weight must be staged (font-renaming
   gotcha: §7).
3. **Plan.** `STORYBOARD.md` — one bulleted block per frame with its cited
   blueprint/rules. When `storyboard: yes`, sketch every frame into
   `storyboard.html` (real fonts/colors/copy, no motion) and lock layouts only
   after user confirmation. Storyboard edits ADD fields, never drop upstream
   ones (`asset_candidates`, `transition_in`, `sfx`, `scene`); `asset_candidates`
   separates candidates by `;` — never use `;` inside a description; `sfx:`
   values are bare bundled-library key names; keep every non-frame section
   ABOVE frame 1 (trailing sections leak into the last frame's packet); budget
   frame packets before writing motion (§7).
4. **Audio early.** Start BGM/TTS in the background as soon as the mood/script
   is known. Canonical offline sequence (HeyGen signed out):
   a. Write `audio_request.json` (`bgm.mode: "generate"` + a full prompt), then
      `GEMINI_API_KEY= GOOGLE_API_KEY= node ~/.agents/skills/media-use/audio/scripts/audio.mjs --request ./audio_request.json --hyperframes . --out ./audio_engine_meta.json`
      — the SIDECAR output matters: `fetch-sfx` rebuilds `audio_meta.json` from
      `audio_engine_meta.json`; a bed written straight to `audio_meta.json` is
      dropped. Never run the workflow adapter's default generate pass — its BGM
      mode is strict `retrieve` and would null an offline bed.
   b. Run `wait-bgm.mjs` before assembly. Without narration the engine's target
      is 30s regardless of cut length — finish the bed by hand to the final
      total (crossfade-loop extend, zeroed diegetic silences, tail fade);
      assembly's own extension is a raw `stream_loop` seam (§7).
   c. `fetch-sfx` resolves storyboard `sfx:` names from the bundled library
      offline; then hand-tune `offset_s` / `duration_s` / `volume` in
      `audio_meta.json` (offsets default to 0; long cues like the 10s riser can
      be trimmed).
   d. Beat-locked cuts: measure the groove (onset-flux autocorrelation → period
      + phase) and lock frame durations to `grooveStart + phase + k·T`; state
      the measured BPM/phase in the storyboard's Sound line.
   Music-only volume `0.9`; under narration `0.12` and carve the bed
   (`hyperframes-audio`).
5. **Build.** Sub-compositions under `compositions/frames/` (template wrapper,
   IIFE script, prefixed ids, `window.__timelines[<id>]`); root `index.html`
   stays thin (slot divs + root audio + near-empty root timeline). Follow the
   workflow's build order and read each cited rule body before its motion.
   Pre-install named registry blocks once before dispatch
   (`npx hyperframes add <id>`). Dispatch one worker per packet; verify every
   `compositions/frames/<id>.html` exists on disk afterwards — empty worker
   results happen; retry once, then build that frame inline. Inline gotcha:
   digit-leading selectors can't go into `querySelector` (`.01-cliche-dot`
   throws) — use `getElementById` or `[class~="01-cliche-dot"]`.
6. **Check.** `npm run check` must pass — that means **0 errors** and clean
   runtime/motion (cosmetic warnings and the snapshot-vision fallback are in
   §4). Fix findings; `data-layout-allow-overlap` / `-overflow` are only for
   genuinely intentional layout choices. Inspect `npx hyperframes snapshot`
   contact sheets at frame midpoints and ±0.1s around every cut; fix any
   visible pop before rendering.
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
  recommended one first and labeled "(Recommended)". When the harness exposes
  no question tool, ask in plain text as numbered options (recommended first);
  never batch unrelated fields into one ask beyond what the intent layer allows.
- Deterministic compositions only: no render-time clocks, no unseeded
  randomness, no render-time network fetches for required assets. The skills
  own the details — when a conflict appears, the skill wins.
- Keep scope exact: build what was briefed and offer additions before adding
  them.
- Never commit or push. Never overwrite project files unrelated to the ask.
- Keep capture assets, audio, fonts, and rendered outputs in-repo; clean up
  temp files you created outside the project.

## 7. Hard-won recipes (from the first www.swaibian.com run)

**Frame-packet budget.** Packets must stay ≤ 48,000 bytes — the builder fails
the whole run on the first over-budget frame. Budget BEFORE writing shot
sequences: packet ≈ block (~2–3KB) + blueprint + cited rules (+0.5KB overhead).
Measured sizes — blueprints: kinetic-type-beats 29,151 · logo-assemble-lockup
26,609 · device-surface-showcase 17,151 · titlecard-reveal 7,441. Rules:
chromatic-glitch 10,339 · ambient-glow-bloom 9,840 · gradient-text-sweep 8,751 ·
dynamic-content-sequencing 8,558 · multi-phase-camera 7,773 ·
press-release-spring 7,041 · gsap-effects 6,912 · spring-pop-entrance 6,533 ·
discrete-text-sequence 6,454 · sine-wave-loop 6,163 · scale-swap-transition
5,517 · stat-bars-and-fills 5,486. Rules are inlined by MENTION — naming an id
anywhere in the frame block pulls its full recipe into the packet; to drop a
recipe, drop its name from the prose too and keep an explicit `- rules:` line
listing exactly what should be inlined. `blueprint:` must END with its
parenthetical (`kinetic-type-beats (Adapt — …)`) or the id won't resolve.

**Completing a truncated capture.** When the capture's phase table shows
fonts/assets degraded, or `capture/assets/` holds no raster files: (1) parse
`capture/extracted/page.html` for image URLs (`<img src>`, `/_next/image?url=…`)
and the site CSS for `@font-face` `src` URLs; (2) `curl -sk <url> -o
capture/assets/<name>` — stage FLAT (`stageAssets` scans only `capture/assets`,
`assets/videos`, `assets/svgs`, `screenshots`; subdirectories are not searched);
(3) rename font files so weights parse (`…-75Bold.woff`, `…-56Italic.woff` —
`-75Bd`/`-56It` read as Regular and collapse to a single staged face), then
re-run `build-frame` so `@font-face` picks them up; (4) append one line per file
to `capture/extracted/asset-descriptions.md`.

**Offline music finishing.** The engine's generate target is 30s without
narration, regardless of video length — finish the bed by hand: crossfade-loop
extend to ≥ total, zero-sample diegetic silences (e.g., the kill window),
tail-fade into the final hold; avoid assembly's raw `stream_loop` seam. The
first project landed at 107.1 BPM, T = 0.5602s, boundaries at
`9.772 + k·0.5602` (assembly reported +0.01s drift).
