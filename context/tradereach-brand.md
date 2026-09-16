# TradeReach PPC — Visual Identity

**Reopened 2026-09 — cream/coral light theme.** Supersedes
kinetic-dark-portal (dark, dual glow blobs) at the user's explicit
request to change direction again. If a new token set arrives after
this without saying so, check scope before rebuilding — same rule as
before, just re-anchored to this version.

Design tokens for anything visual built for TradeReach PPC (webapp,
reports, future ad creative). No trigger logic — read this whenever
building something visual for TradeReach.

## Given tokens (source of truth — Tokens Studio format)

```json
{
  "brand-accent-row": {
    "swatch-01": { "value": "#E06C53", "displayName": "Claude Coral Primary", "contrastRatio": "4.8:1" },
    "swatch-02": { "value": "#F5E6D3", "displayName": "Claude Cream Background", "contrastRatio": "7.2:1" }
  }
}
```

Only two colors given, one explicitly named "Background" — read as a
light theme (cream base, coral accent), a reversal from every prior
dark theme this venture has had.

## Derived tokens (not given — filled in for a working system)

```css
--bg: #F5E6D3;          /* given — cream background */
--surface: #FBF4E9;     /* card background, lifted lighter than bg */
--surface-2: #F0DFC5;   /* nested panel, deeper than bg */
--fg: #2A1F16;          /* primary text — dark warm brown, not pure black, for contrast on cream */
--muted: #8A7A6B;       /* secondary text, warm grey-brown */
--line: #E3D0B4;        /* hairline borders */
--accent: #E06C53;      /* given — coral */
--accent-strong: #C85640;/* accent hover, darker (buttons darken on hover on a light ground, unlike the brighten-on-hover pattern used on dark themes) */
--accent-ink: #FFF8F2;  /* near-white text on coral-filled buttons */
--good: #6E8F5A;        /* status/success, earthy green to match the warm palette rather than a cool stock green */
--radius: 4px;          /* carried over from prior themes — not specified, no reason to change it */
--pad: 1rem;            /* carried over — not specified */
--font: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, monospace; /* carried over — not specified, no reason given to change it */
```

## Design note

No effects tokens (no glow, no easing) came with this set, so the
glow-blob/kinetic-motion treatment from kinetic-dark-portal was
dropped rather than carried forward onto a light background it wasn't
designed for. Kept: monospace type, the terminal-chrome calculator
card, `// comment`-style section eyebrows, and the blinking cursor —
all recolored for a light ground, simple color/border transitions on
hover instead of the lift+glow pattern.

Worth naming for future direction decisions: this warmer, lighter
palette reads less like a dev-tool and more like an approachable local
service business — arguably a closer fit for TradeReach's actual
audience (van-based tradespeople) than the dark terminal themes tried
before it.

## Where this is used

- TradeReach PPC webapp (single-page site + missed-call calculator) —
  live at the artifact URL in chat history.
- Applies to TradeReach only. Smile Local has no visual identity yet —
  don't reuse these tokens there without an explicit decision to share
  a look across both ventures.
