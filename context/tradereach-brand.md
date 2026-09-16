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

## Typography (unchanged from prior elevation pass)

```css
--font-display: "Bricolage Grotesque", ui-sans-serif, system-ui, sans-serif;
--font-body: "Public Sans", ui-sans-serif, system-ui, sans-serif;
--font-mono: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, monospace;
```

Type scale and spacing scale also unchanged (see prior entries in git
history) — this pass only touched color usage and semantics, not
sizing.

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

## Where this is used

- TradeReach PPC webapp (single-page site + missed-call calculator) —
  live at the artifact URL in chat history.
- Applies to TradeReach only. Smile Local has no visual identity yet —
  don't reuse these tokens there without an explicit decision to share
  a look across both ventures.
