# design.md — "Zapier-Warm Portfolio"

Living design spec for Prince Kumar's portfolio landing page.
Reference: VoltAgent/awesome-design-md — `design-md/zapier/DESIGN.md` (inspired interpretation).

## Design read

Senior backend engineer portfolio (**Senior Software Engineer / Backend**), copy
aligned to `Prince-Kumar-Resume.pdf` and backend-first (Node.js, TypeScript,
PostgreSQL, MongoDB, Redis, Kafka, Kubernetes). Audience: recruiters + engineering
hiring managers scanning fast. Voice: **confident-warm, not cool-tech** — a cream
canvas, coffee ink, and a single saturated orange CTA. No pure white, no pure
black, one chromatic accent. Dials: `VARIANCE 6 / MOTION 6 / DENSITY 3`.

## Tokens

- Palette: canvas `#fffefb`, canvas-soft `#f8f4f0`, ink `#201515`,
  ink-soft `#2f2a26`, body `#605d52`, body-mid `#939084`, primary `#ff4f00`,
  on-primary `#fffefb`. Orange is reserved for CTAs, live-status dots, diagram
  packets + underline highlights only.
- Radius: `6px` inputs/badges, **12px** buttons + cards (the signature middle
  radius), `9999px` pills. Never full-pill CTAs.
- Spacing: 2/4/8/12/16/24/32/48/64. Section bands pad `64px+` top/bottom;
  marketing container ~1280px centered with gutters.
- Type: **Space Grotesk** (Degular stand-in; hero, section displays, eyebrows,
  footer display) + **Inter** (body, buttons, card titles, tables). Two faces,
  two roles. Eyebrows are 13px/500 +0.2em UPPERCASE with an orange tick.
- Elevation: hairline 1px ink borders; one soft warm card shadow. No glow, no
  harsh dark shadows on light surfaces.

## Structure (top to bottom)

- Fixed cream nav (blur) + hairline border, orange active dot + scroll-progress.
- **Hero**: warm cream; left copy = availability pill → Space Grotesk 500
  headline → CTAs (primary orange "View my work", ink "Download CV", text mail
  link). Right 55% = **Warm Signal Core** Three.js scene (below).
- **Work** (cream-soft band): alternating screenshot-card rows, product-frame
  chrome + architecture diagrams recolored coffee/cream with orange packets.
- **About** (canvas): centered statement + three stat cards.
- **Experience** (cream-soft): role list + outline CV button.
- **Skills** (canvas): 4 equal feature cards with orange index numerals.
- **Footer** (ink): link grid, big display "Contact", orange mail CTA, meta row.

## Warm Signal Core (hero)

Same interaction model as before — idle auto-rotation, damped pointer tilt,
drag-to-orbit, scroll pullback, IntersectionObserver render pause, reduced
motion = static frame, silent CSS fallback on WebGL failure. Only the palette
changed: coffee-ink `#201515` wireframe/nodes on the cream canvas, **orange**
message packets with warm glow sprites, soft ink halo. `aria-hidden`, headline
is the LCP + a11y element.

## Rules

- Orange belongs to CTAs and signal (dots/packets/ticks/underlines), nowhere else.
- Canvas stays warm cream `#fffefb`; ink is coffee `#201515`, never pure black.
- Buttons and cards are 12px rounded rectangles — never pills, never square.
- Copy is backend-first and grounded in `Prince-Kumar-Resume.pdf`; this file
  documents the visual system, so keep tokens, radius, type and the single-accent
  rule fixed when copy changes.
- All motion honors `prefers-reduced-motion`.
