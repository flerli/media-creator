# frame.md — swaibian one · video design system

Brand truth, derived from `capture/extracted/tokens.json` (one.swaibian.com).
Hex values and fonts are sacred; sizes, spacing, and decoration scale for video.

## Palette

| Role          | Value                                                                 |
| ------------- | --------------------------------------------------------------------- |
| canvas        | `#F7F8FA` page ground · `#FFFFFF` panels · `#F0F1F4` soft panel       |
| ink           | `#111827` headlines · `#353740` text · `#6B7280` muted                |
| border        | `#E5E7EB` (use 2px at video scale, hairlines allowed)                 |
| accent (green)| `#10A37F` primary · soft `#E7F6F1` / `#CBF1E6` · ink-on-soft `#0D4636`    |
| ai (purple)   | `#7C3AED` · soft `#F0EAFF` / `#EFDCF7` · ink-on-soft `#4C1D95`        |
| warm          | `#FFE2C5` (rare third accent) · strong `#F59E0B` (hairlines/bars only) |
| faint         | `#CBD5E1` pending / inactive glyphs (tick marks before completion)     |
| status        | `#16A34A` success · `#EF4444` error — dashboard chips only            |
| tinted panels | gradient stops stay within the soft tints (`#FBF7FF` lilac-white)     |

## Typography

- **Family:** Inter (bundle 400 / 600 / 700 woff2 locally; no render-time fetch).
- Display: 88–120px / 700–800 / tracking −0.02em (800 for ghost type and the wordmark).
- Supporting: 30–38px / 400–500.
- Eyebrow/label: 20–24px / 600 / uppercase / 0.08em.
- Numerals: `font-variant-numeric: tabular-nums`.

## Layout feel — light cinematic

- White / soft-gray fields, 2px solid borders, hairline rules, soft cards; never a blank slide — ghost marks and tinted panels carry depth.
- Edge-anchored zones and split frames (copy left / visual right); structural rules animate `scaleX: 0 → 1`.
- Two focal points minimum; hero type 60–80% of frame width.
- Captured section renders are plates: always motion-treated (perspective tilt + slow zoom), never flat embeds.
- Accent visible: 15–25% opacity atmospheric, full saturation for focal elements.

## Components

- **Card:** white, 2px `#E5E7EB` border, 22–24px radius (buttons 18px), shadow `0 24px 60px rgba(15,23,42,.08)`, top accent hairline.
- **Pill:** soft tint background (green or purple), ink text, 999px radius.
- **Eyebrow:** uppercase, letterspaced, muted; paired with a small accent dot.
- **Cursor:** white pointer, 2px ink outline, 28px.

## Motion feel

- Calm-confident: entrances 0.4–0.7s `power3.out` / `expo.out`; exits faster than entrances.
- One ambient motion per scene (breathe / drift / sheen); one spring-pop allowed on the claim beat.
- Hard cuts on beat; crossfades only between continuous thoughts.

## Don'ts

- No dark mode, no full-screen linear gradients, no pure `#000`, no gradient text, no neon; no identical card grids without hierarchy; KaTeX fonts unused.
