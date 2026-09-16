# TradeReach PPC — Visual Identity

**Palette settled 2026-09 (cream/coral light theme)** — see color
tokens below. **Craft elevated 2026-09** on top of that same palette:
type pairing, a real type scale, a spacing scale, and more disciplined
accent-color usage. Don't change the hex values below without the user
explicitly reopening the palette again (same rule as before); the
elevation pass only touches how the palette is used, not what it is.

Design tokens for anything visual built for TradeReach PPC (webapp,
reports, future ad creative). No trigger logic — read this whenever
building something visual for TradeReach.

## Color tokens (settled — do not change without explicit request)

```css
--bg:#F5E6D3; --surface:#FBF4E9; --surface-2:#F0DFC5;
--fg:#2A1F16; --muted:#8A7A6B; --line:#E3D0B4;
--accent:#E06C53; --accent-strong:#C85640; --accent-ink:#FFF8F2;
--good:#6E8F5A;
```

## Typography (elevated — was one monospace face for everything)

```css
--font-display: "Bricolage Grotesque", ui-sans-serif, system-ui, sans-serif; /* headings, hero, brand mark */
--font-body: "Public Sans", ui-sans-serif, system-ui, sans-serif;            /* paragraphs, nav, buttons */
--font-mono: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, monospace; /* numbers, labels, calculator, docket meta */
```

Why a grotesque display face, not a serif: cream background + warm
terracotta-adjacent accent + serif display is a well-known templated
AI-design combination. A characterful grotesque sidesteps it while
keeping the same warm palette. Monospace is demoted from "the only
typeface" to a deliberate accent reserved for data and technical
labels (calculator figures, docket meta, section eyebrows) — it now
means something (precision/measurement) instead of being the default.

## Type scale (elevated — was ad hoc: 10/11/11.5/12.5/13/13.5/14/14.5/15/15.5px...)

```css
--text-xs: .6875rem;   /* 11px — micro labels, docket meta */
--text-sm: .8125rem;   /* 13px — nav, secondary body, buttons */
--text-base: .9375rem; /* 15px — body copy */
--text-md: 1.0625rem;  /* 17px — lede paragraph */
--text-lg: 1.25rem;    /* 20px — section h2 */
--text-xl: 1.75rem;    /* 28px — step/card headings */
--text-2xl: clamp(2rem, 4.2vw, 2.75rem); /* 32-44px — hero h1 */
```

## Spacing scale (elevated — was `--pad` × arbitrary factors like 0.65, 1.4, 2.6, 3.2)

```css
--space-1: .25rem;  --space-2: .5rem;  --space-3: .75rem;
--space-4: 1rem;    --space-5: 1.5rem; --space-6: 2rem;
--space-7: 3rem;    --space-8: 4rem;
```

## Color-usage rule (elevated — was accent on every interactive/decorative mark at once)

Accent (coral) is reserved for: primary buttons, the hero's emphasized
word, the "hot" calculator readout, the founding-rate price card, the
live status dot, and focus rings. Checklist checkmarks and other
minor marks use `--fg` or `--muted` instead of accent, so the accent
still reads as *the* signal color rather than blending into general
decoration.

## Where this is used

- TradeReach PPC webapp (single-page site + missed-call calculator) —
  live at the artifact URL in chat history.
- Applies to TradeReach only. Smile Local has no visual identity yet —
  don't reuse these tokens there without an explicit decision to share
  a look across both ventures.
