# TradeReach PPC — Visual Identity

**SETTLED as of 2026-09 — kinetic-dark-portal.** After trying three
directions (flat monospace terminal → warm charcoal/cream terminal →
this), the user confirmed "glowing portal" as the one to keep. Don't
propose or apply a different token set to TradeReach without the user
explicitly asking to change direction again — a new palette pasted
without that context should prompt a check, not an automatic rebuild.

Design tokens for anything visual built for TradeReach PPC (webapp,
reports, future ad creative). No trigger logic — read this whenever
building something visual for TradeReach.

## Tokens (source of truth)

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
--radius: 4px;
--pad: 1rem;
--font: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, monospace; /* not specified in this token set — carried over, no reason given to change it */
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
  color changes. Motion is a response to interaction, not ambient
  animation — `prefers-reduced-motion` disables the blinking cursor and
  cuts transition durations, nothing else needs to change.
- Terminal chrome (title bar, status dots) on the calculator card, and
  `// comment`-style section eyebrows, both carried over from the
  monospace-terminal lineage this theme descends from.

## Where this is used

- TradeReach PPC webapp (single-page site + missed-call calculator) —
  live at the artifact URL in chat history.
- Applies to TradeReach only. Smile Local has no visual identity yet —
  don't reuse these tokens there without an explicit decision to share
  a look across both ventures.
