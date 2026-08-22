# design.md — "The Signal Core"

A living 3D systems map for Prince Kumar's portfolio landing page.

## Design read

Developer portfolio, overhaul redesign. Audience: recruiters + senior engineering
hiring managers scanning fast. Language: dark-tech, monospace-anchored, single
emerald accent. Dials: `VARIANCE 8 / MOTION 8 / DENSITY 3`. The hero's one job:
make a hiring manager stop scrolling in under two seconds and think
*"this person builds real things."*

## Concept

The old hero was flat SVG doodles plus a fake terminal (an AI-tell pattern).
The new hero is a **real-time Three.js visualization of the thing Prince actually
sells: distributed event-driven architecture** — rendered as an object you can
grab and spin.

One scene, four layers:

| Layer | What it is | What it says |
|---|---|---|
| Core | Glowing wireframe icosahedron, counter-rotating shells | The event bus / heart of every system |
| Nodes | 26 service nodes on a Fibonacci sphere, each a tiny glowing tetra | Microservices around the bus |
| Links | Curved quadratic bezier lines from rim to core | Service-to-bus wiring |
| Packets | Light pulses traveling along links at staggered rates | Kafka messages in flight |

The metaphor is honest: it literally is his job title as geometry.

## Interaction model

- **Idle**: slow auto-rotation, packets streaming, subtle core breathing.
- **Pointer parallax**: whole system tilts toward cursor (damped, never snappy).
- **Drag to orbit**: grab anywhere on the hero canvas and spin the cluster.
  Cursor becomes `grabbing`. Momentum decays naturally.
- **Scroll**: camera pulls back slightly as you leave the hero; render loop
  pauses entirely when the hero scrolls out of view (IntersectionObserver).
- **Reduced motion**: everything static, one frame rendered, no loop.
- **No WebGL / load failure**: silent fallback to a static radial-glow CSS
  backdrop. The page must never show a broken hero.

## Visual system

- Palette locked: near-black `#07090d` base, emerald accent `#34d399`,
  slate neutrals. One accent across the whole page, including the 3D scene.
- Type unchanged: JetBrains Mono + Space Grotesk (brand tokens preserved).
- Hero layout: asymmetric split. Left column = status pill → headline → subtext
  → CTAs → contact row (max stack discipline). Right = full-bleed 3D canvas,
  edge-to-edge against the viewport right side on desktop.
- Corner-radius system unchanged (`14px` cards / `10px` buttons).
- No eyebrows added anywhere new; existing section labels stay as-is.

## Motion rules

Every animation needs one sentence of justification:

- Auto-rotation + packets → communicates "live system" (the entire concept).
- Pointer tilt → depth feedback, makes the object feel physical.
- Drag orbit → invites touch, signals confidence ("go ahead, play with it").
- Scroll fade/pullback → hands attention from hero to page content.

All motion honors `prefers-reduced-motion` by collapsing to a static frame.
Render loop pauses off-screen. Canvas is `aria-hidden`; screen readers get the
headline text only.

## Performance budget

- Three.js r128 loaded from CDN with `defer`, module-free classic build.
- Single `<canvas>` in hero only. No post-processing passes; glow comes from
  additive blending + sprite textures, not bloom (cheap on mobile GPUs).
- Geometry counts are fixed and small (< ~3k triangles total).
- `devicePixelRatio` clamped to 2. Resize handled with debounce.
- LCP element remains the headline text; canvas paints behind/beside it.

## What stays

Copy voice, all section content, IA, nav labels, anchors, resume link,
contact details, metrics, diagrams. This is a visual overhaul of the hero plus
copy hygiene (em-dash ban), not a content rewrite.

## What goes

- Fake typing terminal in the hero (div-based fake product UI, banned tell).
- Flat SVG "network" doodle behind the hero.
- Em-dashes everywhere (page-wide copy hygiene pass).
