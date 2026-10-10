---
format: 1920x1080
duration: 34.4s
message: "One private desktop that works while you live — and reports back."
arc: Dispatch report — Future-Pacing hook → product promise → demo-loop evidence (×5) → the life → CTA + studio tag
audience: prospective clients and teams discovering Plaza
mode: collaborative
music: deadpan minimal tech — mechanical-quiet groove, soft ticking percussion, low warm pulse, not hype
---

## Decisions

- **Message**: One private desktop that works while you live — and reports back.
- **Audience and arc**: prospective clients/teams discovering Plaza; a dispatch report — the film is one of Donna's dispatches delivered to the viewer. Curiosity → promise → five report cards (evidence) → the life → your move.
- **Format**: 16:9 · 1920×1080 · target ~34.4s (cut locks to the measured beat grid) · **no voiceover** (on-screen type) · music yes (local MusicGen bed) · no captions (silent film).
- **The spine**: **the dispatch rail** — the warm paper carrying a single petrol "DONNA'S DISPATCH" chip through Frames 1–8, every beat landing into it. The report compiles; the viewer is the boss.
- **Held frame**: Frame 1's post-type hold — the line lands and nothing moves; the quiet is the deadpan.
- **Bans**: no fake product UI (every screen is a real capture); no glow/bokeh decoration; no hype risers or swells; **not a slideshow** (the rail and the stamp rhythm persist beat to beat); **not a screensaver** (every motion is a reveal, a stamp, or the camera reading evidence).

## Changes from v1 (sketch review)

- Note (verbatim): "use brighter, warmer style. too black right now. else of that is great" — register flipped in v2: warm paper dominant, petrol accent; charcoal retired as a ground — dark surfaces remain only inside real product windows. Layouts and copy otherwise approved.

## Locked (v3 — final-review revisions applied)

- Layouts + copy locked through three review rounds; v3 (final review): cut tightened 59.18s → ~34.4s on the same beat grid, copy rewritten as Donna speaking directly to the viewer, media-forward gloss (F2/F3/F5 full-bleed like F7), CSS-3D settles on F2–F6/F8. Skeletons in `storyboard.html` v3; never redraw downstream — dress them.

## Changes from v2 (final-review round)

- Note (verbatim): "1. massively tighten and speed up 2. more enterprise high gloss like part 7 3. use more impressive 3d animations 4. text shall be more like Donna is really talking to the user"
- Applied: total cut 59.18s → ~34.4s (same beat grid, compressed multiples); all copy rewritten in Donna's first-person voice addressing the viewer; report beats go media-forward — F2/F3/F5 full-bleed with cinematic scrims (the F7 gloss) — and F2–F6/F8 carry CSS-3D camera work (tilted panels settling flat, z-depth pushes); faster reveals, holds ≤1s.

## Brand (from capture)

- **Palette (v2 — brighter, warmer)**: paper `#FAF8F5` · petrol `#0B4A6F` · ink `#020617` · muted `#6B7280` · tinted cards 4% petrol fill / 20% border. The product's own dark surfaces (Dispatch canvas, photo scrims) are real evidence windows — `#0F1115` scrim, mint `#63D6D4` lives inside them only.
- **Type**: Neue Haas Grotesk Text Pro only — display h1/h2 (−0.02em, ink), chrome eyebrows uppercase 0.08em petrol, numerals petrol; mint only inside dark windows.
- **Surface**: pills 100px · cards 10–14px · **no shadows** · stamp motion = spring-pop with a 2px press settle.
- Source: `capture/extracted/tokens.json` + measured product pixels (`frame.md` § Plaza extension).

## Sound plan

- **Music**: local MusicGen bed — deadpan mechanical-quiet groove (full prompt in `audio_request.json`); frame durations lock to the measured beat grid after generation.
- **SFX (bundled library)**: 01 `typing` · 02 `whoosh-short` · 03 `click` · 04 `pop` · 05 `ping` · 06 `chime` · 07 `notification` · 08 `impact-bass-1`; offsets/volumes hand-tuned after `fetch-sfx`.
- **Measured groove**: T = 0.5278s (113.68 BPM), phase 0.070s — cut boundaries at `0.070 + k·0.5278`s; frame durations re-locked to the grid (sum 34.38s, tightened); the bed trimmed + tail-faded to 35.5s.

## Video direction

- **Palette**: warm paper `#FAF8F5` ground everywhere; petrol `#0B4A6F` carries every accent on the paper stage (rail chip, progress strip, CTA, overlay elements — including overlays over light captures); ink `#020617` headlines; muted `#6B7280` secondary. The product's dark surfaces are real evidence windows — `#0F1115` scrim; mint `#63D6D4` lives only inside the product's own surfaces. Never paint mint on the paper stage.
- **Gloss**: media-forward — full-bleed captures (F2/F3/F5/F7) under cinematic bottom scrims with a faint top vignette; tilted 3D panels settle flat; one sheen sweep on card beats; no shadows.
- **Motion grammar + reveal model**: one camera feel — smooth long-tail settles (`power3`-class; soft springs only, never bounce) with **CSS-3D depth as part of the gesture** (perspective wrappers, rotateX/Y settles, translateZ pushes — seek-safe, no libraries); reveals land fast; at t=0 only the first phrase's piece is on screen; nothing front-loads.
- **Rhythm / held frames**: snappy — 3.2–6.3s per beat; holds ≤1s except F7's calm chain and the final lockup; F1's held beat is short; the progress strip advances one eighth per beat (chrome, extreme bottom edge only).
- **Caption band**: all content sits above the bottom ~17%; the strip is the only thing at the extreme edge.
- **Negative list**: no fake product UI (screens are real captures); no cursor anywhere; no glow/bokeh; no hype risers or swells; **no slideshow** (never front-loaded-then-frozen); **no screensaver** (no independent floating; no lazy breathing, no back-half drift).

## Frame 1 — While you were away

- scene: On warm paper, a petrol caret types the report's opening line; the rail is born.
- onscreen: "While you were out —" (typed, petrol on warm paper; caret holds after the dash)
- window: 0–3.24s
- duration: 3.24s
- poster: 2.6
- transition_in: cut
- status: animated
- voiceover: onscreen
- src: compositions/frames/01-while-you-were-away.html
- type: hook
- persuasion: Curiosity gap — the dispatch framing (the report's own voice, borrowed authority)
- beat: intrigue
- blueprint: typewriter-reveal (Adapt — the typed line IS the dispatch opening; no brand pop; the caret holds)
- sfx: typing
- focal: none (typography-only stage)
- roles: none (typography-only)
- rules: discrete-text-sequence, context-sensitive-cursor
- registry: typewriter (component — restyle to a petrol caret on paper)
- asset_candidates:
- narrativeRole: Opens the report in Donna's own voice; the viewer becomes the boss being briefed.
- keyMessage: Something kept working while you weren't watching.

Typography-only. Hold after the dash — nothing moves. This is the held frame.

Adapt — keep the live type-on + blinking caret as the whole engine; faster; drop the collapse/brand-pop; the line holds and nothing else enters; registry `typewriter` restyled to petrol-on-paper.

Scene 1 (0.0–1.9s): warm paper, empty stage; rail chip seated top-left (static); the caret blinks at the line's start, center (~46% height), and "While you were out" types on fast behind it (→ discrete-text-sequence); caret trails and blinks (→ context-sensitive-cursor); nothing else on screen.
Scene 2 (1.9–2.6s): the em-dash lands; the caret keeps blinking; the line settles onto the paper — no further movement.
Scene 3 (2.6–3.24s): the held read — nothing moves at all; the stillness is the beat. No exit motion (the seam owns the exit).

## Frame 2 — The desk

- scene: Full-bleed: the workspace panel settles from a 3D angle to flat as the camera pulls back; the line lands on the lock.
- onscreen: "I kept working." (lands with the 3D settle) + chrome chip "DONNA'S DISPATCH · LIVE"
- window: 3.24–7.46s
- duration: 4.22s
- poster: 3.4
- transition_in: zoom-through
- status: animated
- voiceover: onscreen
- src: compositions/frames/02-the-desk.html
- type: product_intro
- persuasion: Show-don't-tell proof + Future pacing (the desk is alive without you)
- beat: curiosity → control
- blueprint: zoom-out-workspace-reveal (Adapt — pull-back from a detail to the full desktop; the line answers "what am I looking at")
- sfx: whoosh-short
- focal: assets/plaza-workspace-detail.png
- roles: plaza-workspace-detail = background (single world; close-up → wide pull-back); plaza-donna-command-center = supporting (reserve for an alternate close-up)
- rules: multi-phase-camera, depth-of-field-blur
- asset_candidates: assets/plaza-workspace-detail.png — full desktop workspace (dark UI: sidebar, kanban, canvas, Donna chat); assets/plaza-donna-command-center.png — Donna chat + canvas
- constraint: no cursor, no fake hover states — the desk moves by itself
- narrativeRole: Beat 2 lands the promise: the desk kept working; "Plaza" is named.
- keyMessage: One desktop — and it didn't stop.

Adapt — same single decelerating move, now full-bleed and 3D: the workspace floats as a panel held at an angle, settling to flat while the camera pulls back from a detail; a cinematic scrim carries the line.

Scene 1 (0.0–1.6s): the workspace is full-bleed, held in 3D (perspective ~1600px, rotateY −12°, rotateX 6°, slightly scaled in) on a detail of the chat region; the pull-back is ALREADY running and the panel rotates to face the camera as it recedes — one continuous move (CSS-3D transforms + → multi-phase-camera); a touch of soft focus sharpens as it settles (→ depth-of-field-blur).
Scene 2 (1.6–3.2s): the panel reaches flat and decelerating; the bottom scrim deepens; "I kept working." fades up over the scrim (lower-left ~38%); chip holds top-left.
Scene 3 (3.2–4.22s): lock — no camera motion; one faint reading light crosses the media; hold.

## Frame 3 — Pipelines ran

- scene: Full-bleed: the Metro under a bottom scrim; a pulse runs the node chain as the camera leans through.
- onscreen: "I ran your pipelines." + subline "Design goes in, execution comes out — no handoffs."
- window: 7.46–11.15s
- duration: 3.70s
- poster: 2.6
- transition_in: push-slide LEFT
- status: animated
- voiceover: onscreen
- src: compositions/frames/03-pipelines-ran.html
- type: feature_showcase
- persuasion: Feature-to-benefit translation — no handoff, no context loss, no you
- beat: trust
- blueprint: device-surface-showcase (Adapt — the window is hero; the camera ranges along the node chain)
- sfx: click
- focal: assets/plaza-metro-swaiboard-workspace.png
- roles: plaza-metro-swaiboard-workspace = background (window hero; the connector chain carries the pulse)
- rules: viewport-change, svg-icon-enrichment
- asset_candidates: assets/plaza-metro-swaiboard-workspace.png — The Metro pipeline editor + Swaiboard execution board
- constraint: no invented nodes or labels — only the captured screens
- narrativeRole: First report card; proves the desk executes, not just stores.
- keyMessage: Work moved while you were gone.

Adapt — media-forward: the Metro fills the frame full-bleed under a bottom scrim; the camera leans through a subtle 3D arc while the pulse travels; one breath, fast.

Scene 1 (0.0–1.2s): full-bleed Metro capture (cover, slightly zoomed); headline + subline seat over the bottom-left scrim; the panel starts at a gentle 3D lean (rotateY 5°) and settles flat as the scene opens (CSS-3D transforms).
Scene 2 (1.2–2.6s): a petrol pulse departs the Trigger node and runs the captured connector chain rightward (dash-flow — → svg-icon-enrichment); the camera eases laterally with it (→ viewport-change).
Scene 3 (2.6–3.70s): the pulse lands and dissipates; the camera decelerates; hold.

## Frame 4 — Boards moved

- scene: The board panel settles flat; task chips hop the columns, each flip a beat.
- onscreen: "I moved your boards forward." + subline "Built while you slept. You're welcome."
- window: 11.15–14.85s
- duration: 3.70s
- poster: 2.6
- transition_in: push-slide LEFT
- status: animated
- voiceover: onscreen
- src: compositions/frames/04-boards-moved.html
- type: feature_showcase
- persuasion: Show-don't-tell proof — the state mutation is the evidence
- beat: relief
- blueprint: cursor-ui-demo (Adapt — locked static stage, element swaps only; no cursor; chips hop columns and flip status)
- sfx: pop
- focal: assets/plaza-workspace-detail.png
- roles: plaza-workspace-detail = background (board region, holds the columns); plaza-metro-swaiboard-workspace = supporting (alternate board close-up)
- rules: spring-pop-entrance, dynamic-content-sequencing
- asset_candidates: assets/plaza-workspace-detail.png — kanban columns Planned / In Progress / Done; assets/plaza-metro-swaiboard-workspace.png — Swaiboard task cards
- constraint: no clock, no timestamps invented; motion is the only fiction
- narrativeRole: Second report card; the audit trail of work that advanced overnight.
- keyMessage: Everything moved a column closer.

Adapt — the locked static stage gains 3D: the card arrives as a tilted panel that settles flat; three quick hops; faster.

Scene 1 (0.0–1.0s): board card arrives tilted (rotateY −8°, rotateX 4°) and settles flat (CSS-3D transforms), headline + subline left; the captured board behind at low emphasis.
Scene 2 (1.0–2.9s): three quick hops, one per beat (→ dynamic-content-sequencing): a chip lifts and lands In Progress with a soft 3D dip-settle (→ spring-pop-entrance); a second hops to Done, its pill flipping to a filled check; the subline fades up after hop one.
Scene 3 (2.9–3.70s): the advanced board holds; still.

## Frame 5 — Market read

- scene: Full-bleed: a z-depth push through the dark canvas to the chart it compiled.
- onscreen: "I read the market for you." + subline "Researched, compiled, delivered — before you asked."
- window: 14.85–19.60s
- duration: 4.75s
- poster: 3.6
- transition_in: push-slide LEFT
- status: animated
- voiceover: onscreen
- src: compositions/frames/05-market-read.html
- type: feature_showcase
- persuasion: Show-don't-tell proof — the digest as artifact; analyst-grade judgment without an analyst
- beat: surprise → trust
- blueprint: dataviz-countup (Adapt — the camera pushes through the real digest chart to the headline; the figures are the product's own)
- sfx: ping
- focal: assets/plaza-donna-dispatch-canvas.png
- roles: plaza-donna-dispatch-canvas = background (dark evidence window; the chart region is the landing target)
- rules: multi-phase-camera, coordinate-target-zoom
- asset_candidates: assets/plaza-donna-dispatch-canvas.png — Donna's Dispatch digest + market chart (full-res)
- constraint: never re-typeset a figure — the numbers live inside the captured screen
- narrativeRole: The concept's namesake beat — the machine delivers judgment, not just labor.
- keyMessage: She didn't wait to be asked.

Adapt — media-forward hero: the dispatch canvas fills the frame (its dark chart region); the push becomes a z-depth fly-through into the chart; a scrim carries the lines.

Scene 1 (0.0–1.2s): full-bleed dark canvas (cover on the card region); headline + subline seat over the bottom-left scrim; the media sits low-lit (a soft dusk overlay).
Scene 2 (1.2–3.4s): one steady z-depth push — scale plus translateZ into the chart with a slight rotateY arc (CSS-3D transforms + → multi-phase-camera), landing the chart dead-center (→ coordinate-target-zoom); the dusk lifts as it pushes; nothing overlays the figures.
Scene 3 (3.4–4.75s): lock — chart legible, full-bleed; hold.

## Frame 6 — Briefing ready

- scene: The briefing card settles from a lean; rows arrive and check off.
- onscreen: "I drafted your Monday briefing." + subline "Calendar, open items, carry-overs — done."
- window: 19.60–23.29s
- duration: 3.70s
- poster: 2.6
- transition_in: push-slide LEFT
- status: animated
- voiceover: onscreen
- src: compositions/frames/06-briefing-ready.html
- type: feature_showcase
- persuasion: Friction reduction — the Monday scramble, removed
- beat: ease
- blueprint: agent-progress-theater (Adapt — the receipt checklist checks off; the deliverable is the confirmation)
- sfx: chime
- focal: assets/plaza-briefing-canvas.png
- roles: plaza-briefing-canvas = background (the card); plaza-donna-command-center = supporting (briefing rows reference)
- rules: dynamic-content-sequencing, spring-pop-entrance, svg-path-draw
- registry: success-check (component — restyle to a petrol square badge draw)
- asset_candidates: assets/plaza-briefing-canvas.png — briefing canvas, planning cards; assets/plaza-donna-command-center.png — briefing rows with snooze/dismiss controls
- constraint: no invented meeting names or calendar entries
- narrativeRole: The desk anticipates the viewer's Monday — the proactive half of "reports back".
- keyMessage: It prepared what you'd have had to prepare.

Adapt — the card settles from a slight 3D lean; rows arrive and check off fast; camera static.

Scene 1 (0.0–0.9s): briefing card (rotateY −7° settling flat — CSS-3D transforms) + headline; three rows wait as dim outlines with number badges.
Scene 2 (0.9–2.6s): rows arrive fast, one per beat (→ spring-pop-entrance, staggered windows paced by → dynamic-content-sequencing); subline seated beneath the headline.
Scene 3 (2.6–3.70s): badges flip to filled petrol checks, each check drawing on (→ svg-path-draw); hold.

## Frame 7 — From the surf

- scene: Full-bleed life: rooftop, beach, wrist — one line per photo, calm.
- onscreen: "You were out living. I was listening." + photo captions "Donna replied. Back to the sunset." / "Hands back on the board."
- window: 23.29–29.63s
- duration: 6.33s
- poster: 3.2
- transition_in: zoom-through
- status: animated
- voiceover: onscreen
- src: compositions/frames/07-from-the-surf.html
- type: benefit_highlight
- persuasion: Future pacing — the life the desk buys back
- beat: peace of mind
- blueprint: titlecard-reveal (Adapt — a chain of near-still photo cards, one restrained move each; captions settle)
- sfx: notification
- focal: assets/globetrotter-rooftop-donna-listening.jpg
- roles: globetrotter-rooftop-donna-listening = background (card 1); globetrotter-beach-donna-replied = background (card 2); globetrotter-watch-surfing = background (card 3); globetrotter-tablet-plaza-received = supporting (reserve)
- rules: scale-swap-transition, discrete-text-sequence
- asset_candidates: assets/globetrotter-rooftop-donna-listening.jpg — rooftop dusk, "Donna — Listening"; assets/globetrotter-beach-donna-replied.jpg — beach reply; assets/globetrotter-watch-surfing.jpg — wrist capture above the surf; assets/globetrotter-tablet-plaza-received.jpg — café confirmation
- constraint: no slow-motion clichés, no invented captions — use the page's own lines
- narrativeRole: The emotional payoff — work didn't follow you; it waited, and still moved. Callback: the notification ding answers Frame 1's "While you were out".
- keyMessage: You live — it keeps the desk warm.

Adapt — unchanged treatment (the film's gloss reference); faster chain, ~2.1s per card.

Scene 1 (0.0–2.1s): rooftop photo, full-bleed — fades in with one restrained settle (→ scale-swap-transition); headline "You were out living. I was listening." fades up in the lower third, above the bottom band; caption "Donna is listening. The cocktail can wait." settles beneath; chip seated top-left.
Scene 2 (2.1–4.2s): hard cut to the beach photo; caption swaps in place — slide-up crossfade (→ discrete-text-sequence): "Donna replied. Back to the sunset."
Scene 3 (4.2–6.33s): hard cut to the wrist/surf photo; caption "Hands back on the board."; the last photo holds dead still.

## Frame 8 — Your move

- scene: Paper close: "Your move." then "I'll keep watch."; the CTA and wordmark settle.
- onscreen: "Your move. I'll keep watch." → CTA "Get Plaza" → "Plaza, by Swaibian — swaibian.com" + Swaibian wordmark
- window: 29.63–34.38s
- duration: 4.75s
- poster: 3.4
- transition_in: blur-crossfade
- status: animated
- voiceover: onscreen
- src: compositions/frames/08-your-move.html
- type: cta
- persuasion: Direct address + the maker's proof (studio tag, user-requested)
- beat: motivation
- blueprint: logo-assemble-lockup (Adapt — the wordmark draws on paper; the ask lands in the vacated center; URL extended)
- sfx: impact-bass-1
- focal: assets/swaibian-black-logo.png
- roles: swaibian-black-logo = cutout (lockup member; settles last)
- rules: svg-path-draw, spring-pop-entrance
- asset_candidates: assets/swaibian-black-logo.png — Swaibian wordmark (black)
- constraint: one solid CTA only; no second color beyond petrol on paper
- narrativeRole: Turns the report's rapport into an invitation; names the maker.
- keyMessage: Plaza, by Swaibian — your move.

Adapt — same paper close, faster, with a light 3D settle on the lockup.

Scene 1 (0.0–1.4s): warm paper; "Your move." holds at (~28%), then "I'll keep watch." fades up beneath it (petrol, smaller).
Scene 2 (1.4–3.0s): the CTA pill strokes its own border on (→ svg-path-draw) and fills petrol; "swaibian.com" fades in beside it.
Scene 3 (3.0–4.75s): the wordmark lockup settles with a soft 3D rise (rotateX 8°→0 — CSS-3D transforms + → spring-pop-entrance); placed clear of the bottom band; hold.