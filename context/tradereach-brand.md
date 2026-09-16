# TradeReach PPC — Visual Identity

Design tokens for anything visual built for TradeReach PPC (webapp,
reports, future ad creative). No trigger logic — read this whenever
building something visual for TradeReach.

**Current: "kinetic-dark-portal"** (superseded the flat "cc-" palette
from 2026-09; that one read as too plain). Dark, layered, with dual
ambient glow blobs (orange + purple) and motion on interactive
elements — a modern dev-tool-at-night feel rather than a flat terminal.

## Given tokens (source of truth)

```json
{
  "theme": "kinetic-dark-portal",
  "color": {
    "bg-main": "#08080A",
    "bg-surface": "#121216",
    "fg-main": "#F3F4F6",
    "fg-muted": "#8E929E",
    "brand-accent": "#E06C53",
    "glow-primary": "rgba(224, 108, 83, 0.15)",
    "glow-secondary": "rgba(147, 51, 234, 0.1)"
  },
  "effects": {
    "blur-radial": "120px",
    "transition-kinetic": "cubic-bezier(0.16, 1, 0.3, 1)"
  }
}
```

## Derived tokens (not given — filled in for a working system)

```css
--surface-2: #191920;              /* nested panel background */
--line: rgba(243,244,246,.09);     /* hairline borders on dark surfaces */
--accent-strong: #F0876D;          /* accent hover/active state */
--accent-ink: #08080A;             /* text on accent-filled buttons */
--good: #7FBF9E;                   /* status/success, cool-toned to match fg-muted's blue-grey cast */
--radius: 4px;                     /* carried over from the prior token set */
--pad: 1rem;                       /* carried over from the prior token set */
--font: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, monospace; /* carried over — not specified in this token set, no reason given to change it */
```

## How the effects tokens are used

- **`blur-radial` (120px)**: three large, low-opacity circular blobs
  (`.glow-orange`, `.glow-purple`, `.glow-orange-2`) positioned behind
  the content, `filter: blur(120px)`. Orange (`glow-primary`) is the
  dominant one — appears twice, top-left and bottom — purple
  (`glow-secondary`) appears once, smaller, as a secondary accent, not
  equal-weight to orange. Fixed behind content, `pointer-events:none`.
- **`transition-kinetic`**: applied to button hovers (lift + glow
  shadow), card hovers (subtle lift), input focus rings, and nav link
  color changes. Not used for anything that loops or auto-plays —
  motion is a response to interaction, not ambient animation, so
  `prefers-reduced-motion` only needs to disable the blinking cursor
  and cut transition durations, not remove a background animation.

## Where this is used

- TradeReach PPC webapp (single-page site + missed-call calculator).
- Applies to TradeReach only. Smile Local has no visual identity yet —
  don't reuse these tokens there without an explicit decision to share
  a look across both ventures.
