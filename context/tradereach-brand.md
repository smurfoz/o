# TradeReach PPC — Visual Identity

Design tokens for anything visual built for TradeReach PPC (webapp,
reports, future ad creative). No trigger logic — read this whenever
building something visual for TradeReach; it replaces the earlier
industrial "job docket" identity (Oswald/orange/hazard-stripe) as of
2026-09.

## Given tokens (source of truth)

```css
--cc-bg: #101010;      /* page background */
--cc-fg: #e6e1dc;      /* primary text */
--cc-accent: #e06c53;  /* terracotta — CTAs, highlights, links */
--cc-muted: #6f6a64;   /* secondary text, quiet borders */
--cc-font: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, monospace;
--cc-pad: 1rem;
--cc-radius: 4px;
```

Single dark theme, deliberately — no light-mode variant. Monospace
throughout; hierarchy comes from size/weight/letter-spacing, not a
second typeface.

## Derived tokens (not given — filled in for a working system)

```css
--cc-surface: #181818;      /* card/panel background, one step off bg */
--cc-surface-2: #1f1f1f;    /* nested panel background */
--cc-line: #2a2a2a;         /* hairline borders */
--cc-accent-strong: #c85a42;/* accent hover/active state */
--cc-accent-ink: #101010;   /* text on accent-filled buttons */
--cc-good: #8fa878;         /* status/success, muted sage (not a saturated green — stays in the warm-neutral family) */
```

Rationale: the accent is mid-brightness, so dark ink reads better than
white on an accent-filled button. Surfaces step up in ~5-8% luminance
increments off the near-black base rather than jumping to grey, to
keep the terminal-like flatness. `--cc-good` is desaturated to avoid a
stock-green clashing with the warm terracotta/off-white palette.

## Spacing & shape

- Base unit `--cc-pad` (1rem); multiples of it (1.5rem, 2rem, 3rem) for
  section rhythm — don't introduce an unrelated spacing scale.
- `--cc-radius` (4px) on every card, button, and input — flat and
  slightly softened, not pill-shaped, not sharp.

## Where this is used

- TradeReach PPC webapp (single-page site + missed-call calculator) —
  rebuilt to this system.
- Applies to TradeReach only. Smile Local has no visual identity yet —
  don't reuse these tokens there without an explicit decision to share
  a look across both ventures.
