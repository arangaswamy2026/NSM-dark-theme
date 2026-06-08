# NSM Dark Theme — Component → Token Map (Dev Hand-off)

**Source of truth:** `sonicwall-cc-tokens.json` v2.0.0
**Implementation layer:** `sonicwall-cc-theme.css` (CSS custom properties)
**Visual reference:** `storybook.html` (live render of every row below)

> Lean-token collapses: warning-yellow → `--accent`, link/info-blue → `--accent`.

---

## Color token → CSS variable

| Source token | Value | CSS variable |
|---|---|---|
| color.surface.l0-page | `#282828` | `--surface-l0` |
| color.surface.l1-chrome | `#333333` | `--surface-l1` |
| color.surface.l2-card | `#333333` | `--surface-l2` |
| color.surface.l3-raised | `#434343` | `--surface-l3` |
| color.surface.l3-hover | `#515151` | `--surface-hover` |
| color.surface.l-sink | `#282828` | `--surface-sink` |
| color.border.default | `#515151` | `--border` |
| color.border.subtle | `#65656a` | `--border-subtle` |
| color.text.primary | `#ffffff` | `--text-primary` |
| color.text.secondary | `#cccccc` | `--text-secondary` |
| color.text.muted | `#868686` | `--text-muted` |
| color.text.inverse | `#333333` | `--text-inverse` |
| color.text.on-accent | `#ffffff` | `--text-on-accent` |
| color.accent.default | `#ff791a` | `--accent` |
| color.accent.secondary | `#fda348` | `--accent-secondary` |
| color.accent.hover | `#e6640a` | `--accent-hover` |
| color.semantic.critical / not-mitigated | `#cc0000` | `--sev-critical` / `--sev-not-mitigated` |
| color.semantic.mitigated | `#99cc00` | `--sev-mitigated` |
| color.semantic.warning | `#ff791a` | `--sev-warning` |
| color.semantic.benign | `#868686` | `--sev-benign` |

**Radius:** badge `2px` `--r-badge` · input `3px` `--r-input` · card `5px` `--r-card` · pill `50%` `--r-pill`.
**Shadow:** `--shadow-overlay` (modals) · `--shadow-tooltip`. **Spacing:** `--space-1..5` (3/5/10/20/29px), `--header-height` 83px, `--sidebar-width` 200px.
**Sizes:** xs `--fs-xs` 11 · sm 12 · base 13 · md 14 · lg 16 · xl 18 · 2xl 20 · 3xl 28.

---

## Components (25 defined groups)

### Carried over from Capture Client (re-valued to NSM)

**Top header bar** `component.topbar`
- bg `--surface-l1` · height `--header-height` (83px) · radius `--r-card`
- app name `--accent` `--fs-md`; divider `--border`; nav item `--text-muted` → active `--text-primary` with bottom 2px `--accent`

**Sidebar nav** `component.sidebar`
- bg `--surface-l1` · width `--sidebar-width` (200px)
- item `--text-sidebar` (#cccccc) → hover `--text-primary` (#fff); hover bg `--surface-hover`, active bg `--surface-l3`
- item icon `--accent`; selected marker left 3px `--accent`; level-1 `--fs-sm` indented

**Breadcrumb** `component.breadcrumb`
- bg `--surface-l1`; text `--text-secondary`; slash `--text-muted`; **clickable** `--accent` (blue collapsed) hover underline

**Primary button** `component.buttonPrimary`
- bg/hover `--accent`/`--accent-hover`; text `--text-on-accent`; **radius `--r-input` (3px, not pill)**; height `--space-5` (29px)

**Secondary button** `component.buttonSecondary`
- bg transparent; border `--border`; text `--text-secondary`; radius `--r-input`; hover bg `--surface-hover`

**Input** `component.formInput`
- bg `--surface-l2` (#333); border `--border`; text `--text-primary`; placeholder `--text-muted`
- focus `--accent` + ring `--accent-ring` (blue collapsed); height 30px; radius `--r-input`; label `--text-secondary` `--fs-sm`

**Checkbox** `component.checkbox`
- box `--surface-l2` + `--border-subtle`; checked `--accent`; size 14px; radius `--r-badge`

**Tabs** `component.tabs`
- group bg `--surface-l1` radius `--r-card`; nav bottom 1px `--border`
- tab `--text-muted` → hover/active `--text-primary`; active bottom 2px `--accent` weight 600

**Steps / wizard** `component.stepper` *(+ done state)*
- done `--sev-mitigated` (#99cc00); active `--accent` text `--text-on-accent`; inactive `--surface-hover` border 2px `--border` text `--text-muted`
- connector `--border`; label `--text-muted` → active `--text-secondary` `--fs-xs`

**Data table** `component.dataTable` *(+ zebra)*
- header `--surface-l1` text `--text-table-header` weight 600 `--fs-sm`
- row `--surface-l2`, **even rows `--surface-l3`**, hover `--surface-hover`; text `--text-secondary`; border bottom 1px `--border`; cell padding 7px 12px

### New — drawn from NSM

**Icon button** `component.iconButton`
- default: bg transparent → hover `--surface-hover`; icon `--text-secondary` → hover `--text-primary`
- primary: `--accent` text `--text-on-accent`; accent: `--accent`; min-w 29px, height `--space-5`, radius `--r-input`

**Select** `component.select`
- bg `--surface-l2`; border `--border`; text `--text-primary`; chevron `--text-muted`; height 30px; radius `--r-input`

**Radio** `component.radio`
- circle `--surface-l2` + `--border-subtle`; checked dot `--accent`; size 14px; radius `--r-pill`

**Slider** `component.slider`
- track `--surface-hover`; fill + thumb `--accent`; thumb shadow `0 1px 4px rgba(0,0,0,.4)`

**Title pane** `component.titlePane`
- bg `--surface-l1` radius `--r-card`; header bottom 1px `--border` `--text-primary` weight 600; body `--text-secondary`

**Tree list** `component.treeItem`
- item `--text-secondary` → hover `--text-primary`; selected `--surface-l3` text `--text-primary`; indent per level

**Count block (KPI)** `component.countBlock`
- bg `--surface-l1` → hover `--surface-hover`; icon + divider `--accent` (vertical gradient); label `--text-muted` `--fs-xs`; count `--text-primary` 22px bold

**Status flag** `component.statusFlag` — 20px square, radius `--r-badge`
- critical `--sev-not-mitigated` (#cc0000); major `--accent`; minor `--sev-warning`→accent; info `--accent` (blue collapsed); text `--text-on-accent`

**LED dot** `component.ledDot` — 12px, radius `--r-pill`
- green `--sev-mitigated`; red `--sev-not-mitigated`; grey `--sev-benign`; yellow/orange/blue → `--accent` (collapsed)

**HA status** `component.haStatus` — 20px round, text `--text-inverse` (#333)
- primary `--sev-mitigated` (#99cc00); secondary `--sev-warning`→accent

**Avatar** `component.avatar`
- bg `--accent`; text `--text-on-accent`; size `--space-5` (29px); radius `--r-pill`; bold `--fs-sm`

**Notification badge** `component.badge`
- bg `--sev-not-mitigated` (#cc0000); text `--text-on-accent`; 10px bold; radius 8px

**Modal** `component.modal`
- surface `--surface-l1` radius `--r-card`; `--shadow-overlay`; scrim `rgba(0,0,0,.8)`
- header/footer border `--border`; header `--text-primary` weight 600 `--fs-md`; body `--text-secondary` line-height `--lh-loose`

**Tooltip** `component.tooltip`
- bg `rgba(51,51,51,.9)`; text `--text-primary` `--fs-sm`; radius `--r-input`; `--shadow-tooltip`

**Scrollbar** `component.scrollbar`
- track `--surface-l1`; thumb `--border-subtle`

---

## Retired in v2.0.0 (not present in NSM)
footer · notification center · content toolbar · action icon button · key-value row · section title · textarea · stat row · keyword tag · date range picker · select-with-search.

Provide details for any of these — or any new component — and it will be folded into the tokens, storybook, and this map.

## To restore collapsed colors
Add `semantic.warning-yellow` (`#ffcc00`) and `semantic.info` (`#47afe8`) to the JSON `color.semantic` group and the matching `--sev-*` CSS variables, then point the status-flag/LED-dot/HA `minor`/`yellow`/`info`/`secondary` slots at them.
