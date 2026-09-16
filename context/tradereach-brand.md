# TradeReach PPC — Visual Identity

**Palette settled 2026-09 (cream/coral light theme)** — hex values
below are fixed; don't change them without the user explicitly
reopening the palette. **Accessibility-audited 2026-09** against a
user-supplied web design framework (WCAG 2.x contrast rules, semantic
HTML, target size) — several real contrast failures were found and
fixed; this section is the record of what changed and why.

## Colour system (audited — computed via WCAG relative luminance)

| Token | Value | Role | Checked against | Ratio | Passes |
|---|---|---|---|---|---|
| `--bg` | `#F5E6D3` | Page background | — | — | — |
| `--surface` | `#FBF4E9` | Card background | — | — | — |
| `--surface-2` | `#F0DFC5` | Nested panel | — | — | — |
| `--fg` | `#2A1F16` | Primary text | `--bg` | ~14:1 | Yes (normal text 4.5:1) |
| `--muted` | `#6B5D4F` | Secondary text | `--bg`/`--surface-2` | ~5.1:1 | Yes — **was `#8A7A6B` at 3.1:1, failed** |
| `--line` | `#E3D0B4` | Hairline borders | — | decorative, no text | n/a |
| `--accent` | `#E06C53` | Fill only (buttons, badges, tints) | — | used as background, paired with dark ink text | — |
| `--accent-text` | `#9C3E2B` | Accent used AS TEXT (links, emphasis, live dot, step numbers, focus ring) | `--bg`/`--surface` | ~5.0:1 | Yes — **raw `--accent` as text was 2.45:1, failed even large-text 3:1** |
| `--accent-hover` | `#E8836D` | Button hover fill (lighter, not darker — paired with dark ink text) | with `--fg` text | ~6.0:1 | Yes — **darkening on hover as originally built dropped fg-on-fill to 3.7:1, failed** |
| `--accent-ink` | `= --fg` (`#2A1F16`) | Text on accent/accent-hover fills | `--accent` | ~4.9:1 | Yes — **was near-white at 3.1:1, failed** |
| `--good` | `#466534` | Status text ("taking new callouts") | `--bg` | ~5.0:1 | Yes — **was `#6E8F5A` at 2.75:1, failed** |

**Rule going forward**: never use `--accent` as a foreground/text/icon
color directly on a light surface — it fails contrast at that
lightness. Use `--accent-text` for anything read as text or a small
meaningful mark; reserve `--accent` for fills large enough to pair
with a separately-chosen ink color.

## Typography and layout tokens (realigned 2026-09 to `context/frontend-design-rules.md`)

Font families unchanged (Bricolage Grotesque display / Public Sans
body / monospace for data), but font weights trimmed to the two-per-
family limit: Bricolage now loads as a single static 700 weight (only
weight actually used), Public Sans loads 400+700 (was 400/500/700).

```css
--font-display: "Bricolage Grotesque", ui-sans-serif, system-ui, sans-serif;
--font-body: "Public Sans", ui-sans-serif, system-ui, sans-serif;
--font-mono: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, monospace;

--text-xs: .75rem;    /* 12px — the absolute floor, was 11px in places */
--text-sm: .875rem;   /* 14px — secondary labels only */
--text-base: 1rem;    /* 16px — body floor, was 15px */
--text-lg: 1.25rem;   /* 20px */
--text-xl: 1.5625rem; /* 25px */
--text-2xl: 1.953rem; /* 31.25px */
--text-3xl: 2.441rem; /* 39px */
--text-4xl: 3.052rem; /* 48.8px */

--space-1: .25rem; --space-2: .5rem;  --space-3: .75rem; --space-4: 1rem;
--space-6: 1.5rem; --space-8: 2rem;   --space-12: 3rem;  --space-16: 4rem;

--radius: .5rem; /* was 4px */
--transition-fast: .15s ease; --transition-mid: .3s ease;
```

Renamed to match the standard scale exactly (previous names like
`--space-5`/`--space-7` didn't line up with the px-based numbering
convention). Body text and the smallest label size were both below the
new rules' floors (15px/11px) and are now at the 16px/12px minimums.

## Layout: mobile-first (rebuilt 2026-09)

Was desktop-first (base styles assumed multi-column, `max-width`
media queries collapsed to mobile) — rebuilt so base styles are the
single-column mobile case and `min-width` queries add columns.
Checklist, steps, pricing and the booking grid now use
`grid-template-columns: repeat(auto-fit, minmax(280px, 1fr))` instead
of hardcoded per-breakpoint column counts, per the rules' explicit
preference. Container widened from 960px to the rules' 1280px — body
text keeps its own `max-width: 65ch` regardless, so line length isn't
affected, only the multi-column sections got more breathing room.

## Semantic/accessibility fixes applied this pass

- Calculator card title was an `<h3>` appearing directly under the
  page's only `<h1>` with no intervening `<h2>` — a heading-hierarchy
  skip. Changed to a non-heading `<p class="slip-title">` since it's a
  UI panel label, not document structure.
- Added a skip link (`Skip to main content` → `#main-content`) and
  `aria-label="Primary navigation"` on the nav landmark.
- Added `aria-live="polite" aria-atomic="true"` on the calculator's
  readout — figures update on input without a page reload, and
  screen-reader users weren't previously told a value had changed.
- Focus ring switched from raw `--accent` (2.45:1, fails the 3:1
  non-text minimum) to `--accent-text` (~5:1).

## Not changed / explicitly out of scope

- Target size: buttons/inputs already exceed the WCAG 2.2 AA 24×24px
  minimum; padding nudged slightly toward the 44px usability goal
  where it cost nothing, not treated as a compliance requirement.
- No images on this page, so no alt-text audit applies.
- No form validation exists yet (calculator has no submit/error
  state) — add accessible error summary + `aria-invalid`/
  `aria-describedby` if a real booking form replaces the
  WhatsApp/email links later.
- Font self-hosting: `context/frontend-design-rules.md` calls for
  self-hosted `.woff2` with preload, but the Artifact platform's CSP
  only permits font *stylesheets* from `fonts.googleapis.com` — see
  that file's platform note. Used Google Fonts + `font-display: swap`
  + minimum weights as the closest compliant equivalent.
- Dark mode: the rules ask for a `prefers-color-scheme: dark` variant
  under the same token names. Not added — this palette's exact hex
  values came from the user as a deliberate single (light) theme
  commitment, and inventing dark-mode colours not requested by them
  would contradict the "don't change settled colours without asking"
  rule already in place above. Flagging rather than assuming; ask if
  a dark variant is wanted.

## Where this is used

- TradeReach PPC webapp (single-page site + missed-call calculator) —
  live at the artifact URL in chat history.
- Applies to TradeReach only. Smile Local has no visual identity yet —
  don't reuse these tokens there without an explicit decision to share
  a look across both ventures.
