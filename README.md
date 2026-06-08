# SonicWall NSM – Dark Theme Design System
**Version 2.0.0** | 2026-06-07

> **v2.0.0 rebases the system onto the NSM (Network Security Manager) dark theme.**
> The palette, type, spacing, and radii now follow NSM (extracted from `index.html`).
> 15 component definitions that were previously missing have been drawn in from NSM.
> The token set was kept lean: existing token slots were re-valued (not expanded), and
> NSM's extra accent/status distinctions were **collapsed** onto existing tokens
> (warning-yellow → accent, link/info-blue → accent).

## Files
| File | Description |
|------|-------------|
| `sonicwall-cc-tokens.json` | W3C design tokens — colors, type, spacing, radius, shadows, and 25 component groups |
| `sonicwall-cc-theme.css` | CSS custom properties (token layer rebased to NSM) + component styles |
| `index.html` | Live token + component gallery with per-component token maps |
| `component-token-map.md` | Text hand-off spec for developers |

---

## Palette (NSM baseline)

### Surfaces
| Token | Hex | Usage |
|-------|-----|-------|
| `surface.l0-page` | `#282828` | App canvas — darkest base |
| `surface.l1-chrome` | `#333333` | Nav · header · panels · inputs · tables · modals |
| `surface.l2-card` | `#333333` | Cards · tab groups · table body |
| `surface.l3-raised` | `#434343` | Zebra (even) rows · selected items |
| `surface.l3-hover` | `#515151` | Hover / active / slider track |
| `surface.l-sink` | `#282828` | Recessed (= app canvas) |

### Borders
| Token | Hex | Usage |
|-------|-----|-------|
| `border.default` | `#515151` | Panel / table / divider borders |
| `border.subtle` | `#65656a` | Input · checkbox · radio borders |

### Text
| Token | Hex | Usage |
|-------|-----|-------|
| `text.primary` | `#ffffff` | Headings, values, counts |
| `text.secondary` | `#cccccc` | Body, nav, cells, labels, table headers |
| `text.muted` | `#868686` | Captions, placeholders, disabled |
| `text.inverse` | `#333333` | Dark text on light status chips |
| `text.on-accent` | `#ffffff` | Text on orange / red backgrounds |

### Accent & semantic
| Token | Hex | Usage |
|-------|-----|-------|
| `accent.default` | `#ff791a` | Icons, active, CTA, focus, **links** (blue collapsed here) |
| `accent.secondary` | `#fda348` | Secondary accent |
| `accent.hover` | `#e6640a` | Primary button hover |
| `semantic.critical` / `not-mitigated` | `#cc0000` | Critical · error · offline |
| `semantic.mitigated` | `#99cc00` | Success · online · done |
| `semantic.warning` | `#ff791a` | Warning (NSM yellow collapsed to accent) |
| `semantic.benign` | `#868686` | Neutral · inactive (NSM info-blue collapsed) |

---

## Typography
System font stack: `-apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif`.

| Token | Size | Usage |
|-------|------|-------|
| `fs-xs` | 11px | Captions, badges, step labels |
| `fs-sm` | 12px | Secondary labels, table headers, tooltips |
| `fs-base` | 13px | **Default** — body, nav, cells, inputs, buttons |
| `fs-md` | 14px | App name / links, modal & panel headers |
| `fs-lg` | 16px | Large body, logo |
| `fs-xl` | 18px | Panel header / h4 |
| `fs-2xl` | 20px | Section heading / h3 |
| `fs-3xl` | 28px | Dashboard title / h2 · icon size |

Weights: regular 400 · semibold 600 (NSM medium-500 collapses here) · bold 700.

---

## Spacing & radius
- **Spacing scale:** 3 · 5 · 10 · 20 · 29 px. Control height = 29px. Header = 83px. Sidebar = 200px.
- **Radius:** `badge` 2px (status flags) · `input` 3px (buttons, inputs) · `card` 5px (panels, modals) · `pill` 50% (dots, avatars).
- **Shadows:** `overlay` `0 4px 16px rgba(0,0,0,.4)` (modals) · `tooltip` `0 2px 8px rgba(0,0,0,.35)`.

---

## Component inventory (25 groups)

**Carried over & re-valued to NSM:** topbar, sidebar, breadcrumb, buttonPrimary, buttonSecondary, formInput, checkbox, tabs, stepper *(+ done state)*, dataTable *(+ zebra)*.

**New — drawn from NSM (15):** iconButton, select, radio, slider, titlePane, treeItem, countBlock, statusFlag, ledDot, haStatus, avatar, badge, modal, tooltip, scrollbar.

**Retired in v2.0.0 (not present in NSM):** footer, notification center, content toolbar, action icon button, key-value row, section title, textarea, stat row, keyword tag, date range picker, React-Select. *Provide details to re-add any of these.*

---

## Collapse decisions (lean-token tradeoff)
1. **warning-yellow `#ffcc00` → accent `#ff791a`** — affects status flag "minor", LED "yellow", HA "secondary".
2. **link/info-blue `#47afe8` → accent `#ff791a`** — affects clickable breadcrumb, input focus, status flag "info", LED "blue".
3. **medium-500 → semibold-600**, **light-200 → regular-400**, **radius 2px → badge**.

To restore yellow/blue distinctions, add `semantic.warning-yellow` and `semantic.info` to the JSON `color.semantic` group and the matching `--sev-*` CSS variables.
