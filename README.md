# media-creator

Repo for producing Swaibian media: HyperFrames videos (HTML → deterministic
MP4), decks, and motion graphics. Every video is a self-contained HyperFrames
project under `videos/<project>/`.

## Projects

| Project | What | Status |
| --- | --- | --- |
| `videos/swaibian-one-promo/` | 25s promo for [one.swaibian.com](https://one.swaibian.com) — no-code AI use cases | Delivered — `renders/video.mp4` |
| `videos/swaibian-com-promo/` | 60s promo for [www.swaibian.com](https://www.swaibian.com) — "No magic. Just work." | In progress |

Each project holds its own `index.html`, `BRIEF.md`, `frame.md`,
`STORYBOARD.md`, `storyboard.html`, `compositions/`, `capture/`, `assets/`,
`renders/`, plus its own `hyperframes.json` and pinned `package.json` scripts.

## Structure

| Path | What |
| --- | --- |
| `videos/` | One HyperFrames project per video |
| `project_management/` | Swaibian One V-Model product planning — separate concern, never mixed with media tasks |
| `.opencode/` | `swaibian-video-producer` agent + skill (the production playbook) |

## Working with a project

Run every HyperFrames command with the project folder as the working directory:

```bash
cd videos/<project>

npm run check          # lint + runtime + layout + motion + contrast gates
npm run dev            # Studio preview (foreground)
npx hyperframes preview --background   # agent-safe preview, prints Studio URL
npm run render -- --quality high --output renders/<name>.mp4
```

Scaffold a new project:

```bash
npx hyperframes init videos/<kebab-name> --non-interactive --example=blank --skill=<workflow>
```

## Gate discipline

brief confirmed → plan (+ sketches when requested) → `npm run check` green →
Studio preview → explicit user approval → render. Never render without
approval; never commit or push unless asked.

## Rules

- Start any video request from the HyperFrames router
  (`~/.agents/skills/hyperframes/SKILL.md`); install the matched workflow
  before executing it.
- Deterministic compositions only: no render-time clocks, unseeded randomness,
  or network fetches for required assets.
- Project truth is per project: `BRIEF.md` → `STORYBOARD.md` → `frame.md` →
  `compositions/`. Read it before editing; never re-scaffold over an existing
  project.
- Never touch `project_management/` from media tasks.

## Producing videos

Use the `swaibian-video-producer` agent or skill for any video work — it loads
the HyperFrames router, owns the gates above, and carries the verified
environment facts (offline audio engines, pinned CLI version).
