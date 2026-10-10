# media-creator

Repo for producing Swaibian media: HyperFrames videos (HTML → deterministic
MP4), decks, and motion graphics. Every video is a self-contained HyperFrames
project under `videos/<project>/`.

You do not operate this repo by hand. You **brief the video producer agent**
and it plans, builds, checks, and renders the video for you. Projects are
local-only: `videos/` is gitignored except the `swaibian-plaza-promo/` example.

## How to use — brief the agent

1. Open this repo in opencode and select the **`swaibian-video-producer`**
   agent (or just ask for a video; any video request routes to it).
2. Tell it in plain language what you want: the product, the message, who it's
   for, how long, where it plays, and any source material — a website URL,
   existing footage or a script, brand assets.
3. The agent asks clarifying questions with concrete options and turns your
   answers into a **brief** (`BRIEF.md`) — message, destination, aspect ratio,
   length, audience, narration.
4. It shows you the plan (and sketches/storyboard when requested). You review,
   adjust, and approve.
5. It builds, checks, and shows you a **Studio preview**. You give feedback or
   approve.
6. On your explicit approval it renders the MP4. Until then, nothing renders;
   nothing is ever committed or pushed.

You are in the loop at every gate: brief confirmed → plan approved → preview
reviewed → render approved.

## How the agent produces it

1. **Routes the request** through the HyperFrames router, which selects and
   installs the owning workflow — `product-launch-video` for promos and site
   tours, `general-video` for multi-scene or freeform pieces,
   `motion-graphics` for short motion-first units.
2. **Gathers assets**: for a URL it captures the live site — screenshots,
   brand tokens, fonts, visible text — which become the featured visuals;
   audio (music bed, voiceover) comes from offline local engines or the media
   catalog, frozen into local files so renders stay deterministic.
3. **Writes the project truth layers** in order: `BRIEF.md` →
   `STORYBOARD.md` → `frame.md` → `compositions/` — message, scene-by-scene
   plan, design spec, then the actual animated HTML.
4. **Builds compositions** as deterministic HyperFrames HTML: a single paused
   timeline, seek-safe animation (GSAP), no clocks, no unseeded randomness, no
   network fetches at render time.
5. **Runs the gates** and verifies on disk: `npm run check` (lint, runtime,
   layout, motion, contrast) must reach zero errors, and the agent inspects the
   real artifacts — captured assets, each frame's HTML, the contact sheets —
   fixing or rebuilding in place instead of trusting a tool's success message.
6. **Previews in Studio** for your review, iterating on your feedback.
7. **Renders** `renders/video.mp4` — reproducibly, only after approval.

## What you get

- A **self-contained project** under `videos/<project>/` that is the full
  source of truth: brief, storyboard, design spec, compositions, assets.
- The **deliverable**: `renders/video.mp4` at the aspect ratio and length you
  briefed.
- **Full editability**: every scene is HTML + animation you can ask the agent
  to change — new line, new pacing, new music, new cut — and re-render.
- **Snapshots/contact sheets** for quick visual review and diffs.
- **Determinism**: the same composition always renders the same MP4, so
  re-renders never drift.

## Example use case

> **You:** "Make a 30-second promo for our new booking feature at
> swaibian.com/book. No narration, energetic music, for LinkedIn."

The agent then, without further prompting:

- asks 3–4 quick questions (audience, key message, tone, deadline) and drafts
  `BRIEF.md`;
- captures swaibian.com/book — real screens, brand colours, fonts — and sketches
  the scene plan into `storyboard.html` (real fonts/colors/copy, no motion)
  before any build;
- builds the composition (product screens in device frames, statement cards
  cut to the music's beat), generates an offline music bed, writes
  `STORYBOARD.md`, `frame.md`, and the compositions;
- runs `npm run check` until it reports zero errors, then hands you a Studio
  preview URL;
- after your notes ("hold the last card longer, warmer music") it re-checks and
  re-previews;
- on your "approved" it renders `videos/swaibian-book-promo/renders/video.mp4`.

What you end up with: a LinkedIn-ready 30s MP4, plus the full project folder
so any line, cut, or beat can be changed later and re-rendered identically.

## Example project

`videos/swaibian-plaza-promo/` is the one project kept in git — the reference
for how a project is laid out: `index.html`, `BRIEF.md`, `frame.md`,
`STORYBOARD.md`, `storyboard.html`, `compositions/`, `capture/`, `assets/`,
`renders/`, plus its own `hyperframes.json` and pinned `package.json` scripts.
It is currently briefed and in progress — a 60s "Donna's Dispatch" promo.

Other projects under `videos/` are local-only and never leave your machine.

## Reference

`AGENTS.md` carries the repo rules; `.opencode/` holds the agent and its
production-playbook skill. Manual commands exist for maintenance only — work
is done through the agent:

```bash
cd videos/<project>

npm run check          # lint + runtime + layout + motion + contrast gates
npm run dev            # Studio preview (foreground)
npm run render -- --quality high --output renders/<name>.mp4
```
