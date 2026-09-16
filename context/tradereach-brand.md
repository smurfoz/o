# TradeReach PPC — Visual Identity

Design tokens for anything visual built for TradeReach PPC (webapp,
reports, future ad creative). No trigger logic — read this whenever
building something visual for TradeReach.

**Current: "claude-code" theme** (superseded "kinetic-dark-portal" from
2026-09; that one had dual glow blobs and kinetic motion, neither of
which is part of this token set, so both were dropped rather than
carried forward). Reads as a vintage amber-terminal / ledger aesthetic:
warm cream text on charcoal, a single orange accent, strict monospace.

## Given tokens (source of truth — W3C design-tokens format)

```json
{
  "color": {
    "charcoal-900": "#101010",
    "cream-100": "#F5E6D3",
    "orange-500": "#E67D22",
    "tan-500": "#8A847C"
  },
  "semantic": {
    "bg-canvas": "charcoal-900",
    "text-primary": "cream-100",
    "accent-interactive": "orange-500",
    "text-muted": "tan-500"
  },
  "typography": {
    "font-stack": ["JetBrains Mono", "Fira Code", "ui-monospace", "monospace"]
  }
}
```

## Derived tokens (not given — filled in for a working system)

```css
--surface: #181410;      /* card background, warm-lifted off bg-canvas, not neutral grey */
--surface-2: #1F1911;    /* nested panel background */
--line: rgba(245,230,211,.10); /* hairline borders, tinted from text-primary rather than a separate grey */
--accent-strong: #F2954A;/* accent hover — brighter, not darker (matches the pattern used in prior themes) */
--accent-ink: #101010;   /* text on accent-filled buttons */
--good: #9CAA6E;         /* status/success — muted olive-green, warm-compatible rather than a stock green */
--radius: 4px;           /* carried over — not specified, no reason to change it */
--pad: 1rem;             /* carried over — not specified, no reason to change it */
```

## Design direction taken

The token description calls out "horizontal grid alignment" for the
font choice — read as a cue toward a ledger/ruled-terminal look rather
than the glow-and-motion treatment of the prior theme: fine horizontal
rule lines in the background (very low opacity, tan-tinted) instead of
blurred glow blobs, tabular alignment on the calculator readout and
pricing figures, no page-load or hover motion beyond simple color/
border transitions. JetBrains Mono loaded from Google Fonts; Fira
Code/ui-monospace/monospace stay as unloaded fallbacks per the given
stack.

## Where this is used

- TradeReach PPC webapp (single-page site + missed-call calculator).
- Applies to TradeReach only. Smile Local has no visual identity yet —
  don't reuse these tokens there without an explicit decision to share
  a look across both ventures.
