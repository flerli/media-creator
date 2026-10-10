---
format: 1920x1080
duration: 60s
message: "One private desktop that works while you live — and reports back."
arc: Dispatch report — Future-Pacing hook → product promise → demo-loop evidence (×5) → the life → CTA + studio tag
audience: prospective clients and teams discovering Plaza
mode: collaborative
music: deadpan minimal tech — mechanical-quiet groove, soft ticking percussion, low warm pulse, not hype
---

## Decisions

- **Message**: One private desktop that works while you live — and reports back.
- **Audience and arc**: prospective clients/teams discovering Plaza; a dispatch report — the film is one of Donna's dispatches delivered to the viewer. Curiosity → promise → five report cards (evidence) → the life → your move.
- **Format**: 16:9 · 1920×1080 · target 60s (cut locks to the measured beat grid, ± a second) · **no voiceover** (on-screen type) · music yes (local MusicGen bed) · no captions (silent film).
- **The spine**: **the dispatch rail** — the charcoal canvas carrying a single mint "DONNA'S DISPATCH" chip through Frames 1–7, every beat landing into it; Frame 8 exits the rail onto paper. The report compiles; the viewer is the boss.
- **Held frame**: Frame 1's post-type hold — the line lands and nothing moves; the quiet is the deadpan.
- **Bans**: no fake product UI (every screen is a real capture); no glow/bokeh decoration; no hype risers or swells; **not a slideshow** (the rail and the stamp rhythm persist beat to beat); **not a screensaver** (every motion is a reveal, a stamp, or the camera reading evidence).

## Brand (from capture)

- **Palette**: canvas-dark `#0F1115` · accent-mint `#63D6D4` · petrol `#0B4A6F` · paper `#F0F0F0` · ink `#020617` · muted `#6B7280` · dark chips `rgba(240,240,240,.06)` fill / `rgba(240,240,240,.14)` border. Light evidence cards float on charcoal — the product's own canvas motif.
- **Type**: Neue Haas Grotesk Text Pro only — display h1/h2 (−0.02em, near-white on dark / ink on paper), chrome eyebrows uppercase 0.08em, numerals cobalt on paper / mint on dark.
- **Surface**: pills 100px · cards 10–14px · **no shadows** · stamp motion = spring-pop with a 2px press settle.
- Source: `capture/extracted/tokens.json` + measured product pixels (`frame.md` § Plaza extension).

## Sound plan

- **Music**: local MusicGen bed — deadpan mechanical-quiet groove (full prompt in `audio_request.json`); frame durations lock to the measured beat grid after generation.
- **SFX (bundled library)**: 01 `typing` · 02 `whoosh-short` · 03 `click` · 04 `pop` · 05 `ping` · 06 `chime` · 07 `notification` · 08 `impact-bass-1`; offsets/volumes hand-tuned after `fetch-sfx`.

## Frame 1 — While you were away

- scene: On the dark dispatch canvas, a mint caret types the report's opening line; the rail is born.
- onscreen: "While you were away —" (typed, mint on charcoal; caret holds after the dash)
- window: 0–5s
- duration: 5s
- poster: 3.5
- transition_in: cut
- status: outline
- voiceover: onscreen
- src: compositions/frames/01-while-you-were-away.html
- type: hook
- persuasion: Curiosity gap — the dispatch framing (the report's own voice, borrowed authority)
- beat: intrigue
- blueprint: typewriter-reveal (Adapt — the typed line IS the dispatch opening; no brand pop; the caret holds)
- sfx: typing
- asset_candidates:
- narrativeRole: Opens the report in Donna's own voice; the viewer becomes the boss being briefed.
- keyMessage: Something kept working while you weren't watching.

Typography-only. Hold after the dash — nothing moves. This is the held frame.

## Frame 2 — The desk

- scene: Close-up on the living desktop, then one decelerating pull-back reveals the whole workspace at once.
- onscreen: "Plaza didn't." (lands with the pull-back) + chrome chip "DONNA'S DISPATCH · LIVE"
- window: 5–12s
- duration: 7s
- poster: 5.5
- transition_in: zoom-through
- status: outline
- voiceover: onscreen
- src: compositions/frames/02-the-desk.html
- type: product_intro
- persuasion: Show-don't-tell proof + Future pacing (the desk is alive without you)
- beat: curiosity → control
- blueprint: zoom-out-workspace-reveal (Adapt — pull-back from a detail to the full desktop; the line answers "what am I looking at")
- sfx: whoosh-short
- asset_candidates: assets/plaza-workspace-detail.png — full desktop workspace (dark UI: sidebar, kanban, canvas, Donna chat); assets/plaza-donna-command-center.png — Donna chat + canvas
- constraint: no cursor, no fake hover states — the desk moves by itself
- narrativeRole: Beat 2 lands the promise: the desk kept working; "Plaza" is named.
- keyMessage: One desktop — and it didn't stop.

## Frame 3 — Pipelines ran

- scene: The Metro editor stamps in; a pulse travels Trigger → Agent → the execution board behind it.
- onscreen: "Your pipelines ran." + subline "Visual workflows, straight into execution. No handoffs."
- window: 12–19s
- duration: 7s
- poster: 4.5
- transition_in: push-slide LEFT
- status: outline
- voiceover: onscreen
- src: compositions/frames/03-pipelines-ran.html
- type: feature_showcase
- persuasion: Feature-to-benefit translation — no handoff, no context loss, no you
- beat: trust
- blueprint: device-surface-showcase (Adapt — the window is hero; the camera ranges along the node chain)
- sfx: click
- asset_candidates: assets/plaza-metro-swaiboard-workspace.png — The Metro pipeline editor + Swaiboard execution board
- constraint: no invented nodes or labels — only the captured screens
- narrativeRole: First report card; proves the desk executes, not just stores.
- keyMessage: Work moved while you were gone.

## Frame 4 — Boards moved

- scene: Locked stage on the board; task chips advance Planned → In Progress → Done, each flip a beat.
- onscreen: "Your boards moved." + subline "Built while you slept."
- window: 19–26s
- duration: 7s
- poster: 4.5
- transition_in: push-slide LEFT
- status: outline
- voiceover: onscreen
- src: compositions/frames/04-boards-moved.html
- type: feature_showcase
- persuasion: Show-don't-tell proof — the state mutation is the evidence
- beat: relief
- blueprint: cursor-ui-demo (Adapt — locked static stage, element swaps only; no cursor; chips hop columns and flip status)
- sfx: pop
- asset_candidates: assets/plaza-workspace-detail.png — kanban columns Planned / In Progress / Done; assets/plaza-metro-swaiboard-workspace.png — Swaiboard task cards
- constraint: no clock, no timestamps invented; motion is the only fiction
- narrativeRole: Second report card; the audit trail of work that advanced overnight.
- keyMessage: Everything moved a column closer.

## Frame 5 — Market read

- scene: The Dispatch canvas pushes through its chart to the headline it compiled on its own.
- onscreen: "I read the market." + subline "Researched, compiled, delivered. Unasked."
- window: 26–34s
- duration: 8s
- poster: 5.5
- transition_in: push-slide LEFT
- status: outline
- voiceover: onscreen
- src: compositions/frames/05-market-read.html
- type: feature_showcase
- persuasion: Show-don't-tell proof — the digest as artifact; analyst-grade judgment without an analyst
- beat: surprise → trust
- blueprint: dataviz-countup (Adapt — the camera pushes through the real digest chart to the headline; the figures are the product's own)
- sfx: ping
- asset_candidates: assets/plaza-donna-dispatch-canvas.png — Donna's Dispatch digest + market chart (full-res)
- constraint: never re-typeset a figure — the numbers live inside the captured screen
- narrativeRole: The concept's namesake beat — the machine delivers judgment, not just labor.
- keyMessage: She didn't wait to be asked.

## Frame 6 — Briefing ready

- scene: The briefing card assembles; three rows arrive and check off — calendar, open items, carry-overs.
- onscreen: "Your briefing is ready." + subline "Monday, 09:00 — calendar, open items, carry-overs."
- window: 34–41s
- duration: 7s
- poster: 4.5
- transition_in: push-slide LEFT
- status: outline
- voiceover: onscreen
- src: compositions/frames/06-briefing-ready.html
- type: feature_showcase
- persuasion: Friction reduction — the Monday scramble, removed
- beat: ease
- blueprint: agent-progress-theater (Adapt — the receipt checklist checks off; the deliverable is the confirmation)
- sfx: chime
- asset_candidates: assets/plaza-briefing-canvas.png — briefing canvas, planning cards; assets/plaza-donna-command-center.png — briefing rows with snooze/dismiss controls
- constraint: no invented meeting names or calendar entries
- narrativeRole: The desk anticipates the viewer's Monday — the proactive half of "reports back".
- keyMessage: It prepared what you'd have had to prepare.

## Frame 7 — From the surf

- scene: The register flips to full-bleed life — rooftop, beach, wrist — one line per photo, calm.
- onscreen: "Your thought from the surf — filed." + photo captions "Donna replied. Back to the sunset." / "Hands back on the board."
- window: 41–50s
- duration: 9s
- poster: 5
- transition_in: zoom-through
- status: outline
- voiceover: onscreen
- src: compositions/frames/07-from-the-surf.html
- type: benefit_highlight
- persuasion: Future pacing — the life the desk buys back
- beat: peace of mind
- blueprint: titlecard-reveal (Adapt — a chain of near-still photo cards, one restrained move each; captions settle)
- sfx: notification
- asset_candidates: assets/globetrotter-rooftop-donna-listening.jpg — rooftop dusk, "Donna — Listening"; assets/globetrotter-beach-donna-replied.jpg — beach reply; assets/globetrotter-watch-surfing.jpg — wrist capture above the surf; assets/globetrotter-tablet-plaza-received.jpg — café confirmation
- constraint: no slow-motion clichés, no invented captions — use the page's own lines
- narrativeRole: The emotional payoff — work didn't follow you; it waited, and still moved. Callback: the notification ding answers Frame 1's "While you were away".
- keyMessage: You live — it keeps the desk warm.

## Frame 8 — Your move

- scene: Paper returns. "Your move." holds alone, then the CTA row and the studio tag; the wordmark settles last.
- onscreen: "Your move." → CTA "Get Plaza" → "Plaza, by Swaibian — swaibian.com" + Swaibian wordmark
- window: 50–59s
- duration: 9s
- poster: 6
- transition_in: blur-crossfade
- status: outline
- voiceover: onscreen
- src: compositions/frames/08-your-move.html
- type: cta
- persuasion: Direct address + the maker's proof (studio tag, user-requested)
- beat: motivation
- blueprint: logo-assemble-lockup (Adapt — the wordmark draws on paper; the ask lands in the vacated center; URL extended)
- sfx: impact-bass-1
- asset_candidates: assets/swaibian-black-logo.png — Swaibian wordmark (black)
- constraint: one solid CTA only; no second color beyond petrol on paper
- narrativeRole: Turns the report's rapport into an invitation; names the maker.
- keyMessage: Plaza, by Swaibian — your move.