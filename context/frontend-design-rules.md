# Front-end Design Rules

Standing rules for all HTML/CSS/component work in this repo, not a
one-off checklist — apply to every page, not just the one that
prompted adding this file. UK English in all copy and comments.

Source: user-supplied ruleset, saved 2026-09-16 so it persists across
sessions instead of being re-typed each time.

---

## Tokens — never hard-code values

```css
:root {
  --space-1: .25rem; --space-2: .5rem;  --space-3: .75rem; --space-4: 1rem;
  --space-6: 1.5rem; --space-8: 2rem;   --space-12: 3rem;  --space-16: 4rem;

  --text-xs: .75rem; --text-sm: .875rem; --text-base: 1rem;
  --text-lg: 1.25rem; --text-xl: 1.5625rem; --text-2xl: 1.953rem;
  --text-3xl: 2.441rem; --text-4xl: 3.052rem;

  --radius: .5rem;
  --transition-fast: .15s ease; --transition-mid: .3s ease;
}
```

- Spacing: 4px base, 8px rhythm. Every gap, padding and margin comes
  from the scale.
- Type: 16px base, 1.25 ratio (16 → 20 → 25 → 31.25 → 39 → 48.8). No
  sizes outside the scale.
- Body text never below 16px. 14px for secondary labels only. Never
  below 12px.
- Maximum two font families. Third only for `monospace` code.
- Define colour tokens once by role (`--text-primary`, `--surface`,
  `--border`, `--accent`, status colours). For dark mode, keep the
  same token names and change the values inside
  `@media (prefers-color-scheme: dark)`. Never create `-dark` twin
  tokens.

## Contrast

- Normal text: 4.5:1 minimum.
- Large text (≥24px, or ≥18.66px bold): 3:1.
- Non-text UI — borders of inputs, icons carrying meaning, focus
  rings, chart strokes: 3:1.
- Disabled controls: exempt, but disabled state must not be signalled
  by colour alone.
- Never convey meaning by colour alone. Pair with text, icon or shape.

## Focus and keyboard

- Use `:focus-visible`, never bare `:focus`, and never
  `outline: none` without a replacement.
- Focus ring must contrast 3:1 against both the control and the
  adjacent background. Do not put a blue ring on a blue button — use
  `outline-offset` plus a neutral or inverted ring.
- Every interactive element reachable and operable by keyboard. Tab
  order follows visual order.
- Provide a skip link as the first focusable element.
- Trap focus inside modals; restore focus to the trigger on close.

## Semantics before ARIA

- Use `button`, `a`, `label`, `fieldset`, `nav`, `main`, `header`,
  `footer`, `table` before reaching for roles.
- ARIA only where no native element exists. No redundant roles on
  semantic elements.
- One `h1` per page. Never skip heading levels. If something looks
  like a heading but isn't structural, style a `p` or `span` instead.
- Landmarks labelled when repeated (`<nav aria-label="Primary">`).
- Every input has a programmatically associated `<label>`. Placeholder
  is not a label.
- Validation errors: `aria-describedby` on the field,
  `aria-invalid="true"`, and a persistent `aria-live="polite"` region
  for summaries. Never announce by replacing the live region's
  container.

## Layout

- Mobile first. Base styles are the small-screen case; `min-width`
  media queries only.
- Container: `width: 100%; max-width: 1280px; margin-inline: auto;
  padding-inline: var(--space-4)`.
- Prefer `grid-template-columns: repeat(auto-fit, minmax(280px, 1fr))`
  over breakpoint-by-breakpoint column counts.
- Body copy `max-width: 65ch`. Line height 1.5–1.7 body, 1.1–1.25
  headings.
- No horizontal scroll at 320px. Content must survive 200% zoom and
  400% reflow.
- Touch targets: WCAG 2.2 AA minimum 24×24px with adequate spacing.
  Aim for 44×44px where layout allows; do not distort dense UI to
  reach it.
- Reserve space for images, ads, embeds and consent banners — set
  `width`/`height` or `aspect-ratio` on every image.

## Motion

- Transitions 150–300ms. Animate `transform` and `opacity` only.
- Always honour `prefers-reduced-motion: reduce`.
- No auto-playing motion longer than 5s without a pause control. No
  flashing above 3Hz.

## Performance

- INP < 200ms, LCP < 2.5s, CLS < 0.1 — judged on field data at the
  75th percentile, not Lighthouse alone.
- Self-host fonts. Preload the `.woff2` itself with `crossorigin`.
  `font-display: swap`. Set `size-adjust`/`ascent-override` on the
  fallback to prevent shift.
- Two weights maximum per family. Subset to the character ranges used.
- Images: modern format, `loading="lazy"` below the fold,
  `fetchpriority="high"` on the LCP image, `srcset` for responsive
  sizes.
- No blocking third-party scripts. Load async or defer; audit anything
  added.

**Platform note (Artifacts):** the Artifact CSP only permits font
*stylesheets* from `fonts.googleapis.com` (files serving from
`fonts.gstatic.com`) — self-hosting an arbitrary `.woff2` isn't
reachable from a published artifact, and inlining font binaries as
data URIs isn't practical for a lightweight single-file page. Treat
"self-host fonts" as aspirational for this platform: use Google Fonts
with `font-display: swap`, keep it to the fewest weights actually
used, and preconnect — that's the closest compliant equivalent here.

## States

Every interactive component defines: default, hover, focus-visible,
active, disabled, loading, error, success. A component is incomplete
without all eight — though a component with no error/loading/disabled
condition in reality (e.g. a static calculator with no submit action)
doesn't need those states fabricated.

## Content robustness

- Design for the worst content: empty, single item, very long
  strings, missing image, 40-character unbroken word, 3× longer
  translated label.
- Support `forced-colors` mode — do not rely on background images or
  box-shadow to convey state.
- Never assume left-to-right; use logical properties
  (`margin-inline`, `padding-block`, `inset-inline-start`).

## Before saying done

- Contrast checked on every text/background pair actually shipped.
- Keyboard-only pass through the whole flow.
- 320px, 768px, 1440px and 200% zoom checked.
- Axe run clean — knowing automated tooling catches only a minority of
  real failures.
- No values outside the token scales.
