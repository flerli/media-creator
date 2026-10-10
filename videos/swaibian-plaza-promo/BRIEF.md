---
workflow: product-launch-video
flow: automation
storyboard: yes
message: "One private desktop that works while you live — and reports back."
destination: website
aspect: 1920x1080
language: en
length: 60s
audience: prospective clients and teams discovering Plaza
narration: no
angle: "Donna's Dispatch — the film is one of Donna's dispatches delivered to the viewer; report cards carry real captured screens as evidence; cards stack and stamp on the beat"
---

## Intent

A 60-second promo for Plaza (www.swaibian.com/plaza) — Swaibian's one private
desktop: AI assistant Donna, live canvas, visual workflows (The Metro),
execution boards (Swaiboard), and the Globetrotter companion on phone/watch.
Concept **"Donna's Dispatch"** (pitched and chosen): the film is one of Donna's
dispatches delivered to the viewer — "While you were away" — a report of
everything already done, each report card carrying a real captured screen as
evidence. Tone: dry, deadpan confidence — the brand's own humor ("Donna eats
lobster for breakfast") — never hype. Close: "Your move." → short studio
reference requested by the user: Plaza by Swaibian — swaibian.com, with the
Swaibian wordmark.

## Customizations

- **Website capture enabled** (route default): crawl www.swaibian.com/plaza for
  screens, brand tokens, and assets — including the full-res product imagery
  (`/products/plaza/*.png` up to 7680px, `/products/plaza-globetrotter/*.jpg`).
- **Series design system:** carry the Koi Zauber frame system (Neue Haas,
  warm paper/petrol) into this project, extended with Plaza's own register —
  charcoal ground, mint accent — for the dispatch feed. Film is
  charcoal-dominant; paper returns once in the closing Swaibian tag. Exact
  balance shown in the sketch pass.
- **Stamp-and-clack SFX:** report cards land with a dry stamp thunk on the
  beat, under the music bed.
- **Beat-locked cuts:** frame durations land on the measured beat grid.
- **Closing studio tag:** "Your move." → *Plaza, by Swaibian — swaibian.com*,
  with the wordmark.

## Notes

- No narration; music + on-screen type only (the dispatch reads muted, and it
  is the series voice).
- Music: generated locally with MusicGen via the shared audio engine; HeyGen
  signed out is the studio's normal state — no cloud pull needed. HyperFrames
  usage unknown on this host (`unsupported_harness`); no allowance quoted.
- 16:9 · 1920×1080; 60s target — final cut locks to the beat grid, ±a second.
- Review: storyboard yes, automation pipeline → collaborative mode (plan →
  sketches → review passes → preview gate).
- No user-supplied media (asked at intent capture; none arrived).
- Site note: www.swaibian.com serves an incomplete TLS chain (curl needs `-k`;
  Chrome/capture unaffected).
- Reusable material from sibling projects: brand system + fonts + wordmark
  from `videos/swaibian-com-promo/` (frame.md, capture/assets/fonts,
  swaibian-black-logo.png, plaza-donna-command-center.png).
- Never commit or push.