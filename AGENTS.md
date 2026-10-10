# media-creator — Swaibian media production

Repo for producing Swaibian media: HyperFrames videos (HTML → deterministic
MP4), decks, and motion graphics. Every video is a **self-contained
HyperFrames project under `videos/<project>/`**.

## Structure

- `videos/<project>/` — one HyperFrames project per video: `index.html`,
  `BRIEF.md`, `frame.md`, `STORYBOARD.md`, `storyboard.html`,
  `compositions/`, `capture/`, `assets/`, `renders/`, plus its own
  `hyperframes.json` + pinned `package.json` scripts. Committed example:
  `videos/swaibian-plaza-promo/`; every other project is local-only and
  gitignored.
- `.opencode/agents/swaibian-video-producer.md` — the video producer agent;
  it loads the `swaibian-video-producer` skill (`.opencode/skills/`) that
  carries the full production playbook. Use either for any video work.
- `README.md` — this overview's short form.

## Working with a project

Run every HyperFrames command with the project folder as the working
directory:

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

## Repo rules

- Start any video request from the HyperFrames router
  (`~/.agents/skills/hyperframes/SKILL.md`); install the matched workflow
  before executing it.
- Gate discipline: brief confirmed → plan (+ sketches when requested) →
  `npm run check` green → Studio preview → explicit user approval →
  render. Never render without approval.
- Deterministic compositions only: no render-time clocks, unseeded
  randomness, or network fetches for required assets.
- Project truth is per project: `BRIEF.md` → `STORYBOARD.md` → `frame.md` →
  `compositions/`. Read it before editing; never re-scaffold over an
  existing project.
- Never commit or push unless asked.
