# Hospital UI design tokens

| Source | Coverage |
|---|---|
| `html/*.html` | The token declarations below are embedded in all 10 HTML files. Values are copied verbatim from the CSS custom-property declarations. |

## Dark theme colors

| Token | Dark |
|---|---|
| `--d-page` | `#130e0e` |
| `--d-panel` | `#221a18` |
| `--d-field` | `#170f0e` |
| `--d-ink` | `#f4ece5` |
| `--d-muted` | `#bcaea2` |
| `--d-line` | `#ffffff1c` |
| `--d-dashed` | `#6f635b` |
| `--d-dots-off` | `#ffffff21` |
| `--d-divider-dots` | `#4a403c` |
| `--d-skeleton` | `#2b211e` |
| `--d-glow` | `#aa283742` |
| `--d-red` | `#c8283c` |
| `--d-red-ink` | `#ff9c94` |
| `--d-red-big` | `#ff5a52` |
| `--d-accent` | `#ff8f94` |
| `--d-green` | `#8fd4a6` |
| `--d-amber` | `#e9bb5a` |
| `--d-blue` | `#a9c0e0` |
| `--d-side-bg` | `#1a1312` |
| `--d-side-ink` | `#f4ece5` |
| `--d-side-muted` | `#bcaea2` |
| `--d-side-line` | `#ffffff1a` |
| `--d-side-active-bg` | `#c8283c38` |
| `--d-side-active-ink` | `#ff9c94` |
| `--d-chip-red-bg` | `#dc3c4b33` |
| `--d-chip-red-fg` | `#ff9c94` |
| `--d-chip-green-bg` | `#5ab4782e` |
| `--d-chip-green-fg` | `#8fd4a6` |
| `--d-chip-amber-bg` | `#e1af3c2e` |
| `--d-chip-amber-fg` | `#e9bb5a` |
| `--d-chip-blue-bg` | `#78a0d733` |
| `--d-chip-blue-fg` | `#a9c0e0` |
| `--d-chip-neutral-bg` | `#ffffff14` |
| `--d-chip-neutral-fg` | `#bcaea2` |
| `--d-scrim` | `#0009` |
| `--d-logo` | `#f3d2ce` |

## Fixed color tokens

| Token | Value |
|---|---|
| `--d-terminal` | `#141010` |
| `--d-terminal-raised` | `#1e1816` |
| `--d-terminal-hover` | `#221b19` |
| `--d-on-terminal` | `#f4ece5` |
| `--d-muted-on-terminal` | `#bcaea2` |
| `--d-terminal-line` | `#ffffff17` |
| `--d-terminal-field-line` | `#3a302d` |
| `--d-terminal-dim` | `#4a403c` |
| `--d-red-on-terminal` | `#ff9c94` |
| `--d-red-pulse` | `#ff5a52` |
| `--d-amber-on-terminal` | `#e9bb5a` |
| `--d-blue-on-terminal` | `#a9c0e0` |
| `--d-on-red` | `#fff` |
| `--d-warn-panel` | `#4a1519` |
| `--d-warn-line` | `#6b2a2f` |
| `--d-warn-muted` | `#e6c9c3` |

## Typography

| Token | Value |
|---|---|
| `--d-font-display` | `"Space Mono", ui-monospace, monospace` |
| `--d-font-mono` | `"Space Mono", ui-monospace, "SFMono-Regular", Menlo, monospace` |
| `--d-font-serif` | `"Newsreader", Georgia, serif` |
| `--d-font-sans` | `"DM Sans", system-ui, -apple-system, "Segoe UI", sans-serif` |
| `--font-mono` | `"Space Mono", ui-monospace, monospace` |
| `--font-serif` | `"Newsreader", Georgia, serif` |
| `--font-sans` | `"DM Sans", system-ui, sans-serif` |

| Web font | CSS declaration |
|---|---|
| Doto | `font-weight: 900` |
| Space Mono | `font-weight: 400` and `font-weight: 700` |
| Newsreader | `font-weight: 200 800` |
| DM Sans | `font-weight: 400`, `font-weight: 500`, and `font-weight: 600` |

## Spacing, sizing, and radii

| Token | Value |
|---|---|
| `--d-radius` | `22px` |
| `--d-radius-sm` | `14px` |
| `--d-pill` | `999px` |
| `--d-gap` | `24px` |
| `--d-pad` | `28px` |
| `--d-control-h` | `44px` |
| `--d-sidebar-w` | `220px` |

## Landing page dark theme tokens

| Token | Dark |
|---|---|
| `--gutter` | `max(20px, calc((100% - 1160px) / 2))` |
| `--bg` | `#130e0e` |
| `--bg-alt` | `#191211` |
| `--card` | `#221a18` |
| `--card-2` | `#2b211e` |
| `--line` | `#ffffff1a` |
| `--line-strong` | `#ffffff47` |
| `--ink` | `#f4ece5` |
| `--muted` | `#bcaea2` |
| `--accent` | `#ff8f94` |
| `--red` | `#c8283c` |
| `--red-hover` | `#b01f33` |
| `--ring` | `#ff969624` |
| `--glow` | `#aa283752` |
| `--logo` | `#f3d2ce` |
| `--input` | `#170f0e` |
| `--shadow` | `0 30px 60px -30px #000c` |
| `--nav-bg` | `#130e0ed1` |

## Additional landing reference: `landing_1(1).html`

Use this attached file as an additional visual reference across Hospital screens. These exact dark-mode colors are the preferred palette for new styling; the file's logo is embedded as a PNG in its `--mark` CSS variable.

| CSS variable | Dark value |
|---|---|
| `--paper` | `#0e0a0a` |
| `--ink` | `#f3efec` |
| `--muted` | `#a59d96` |
| `--line` | `rgba(255,255,255,.15)` |
| `--card` | `#1a1413` |
| `--red` | `#ff3a4a` |
| `--logo` | `#f3d2ce` |
| `--accent` | `#ff8f94` |
| `--sans` | `"Inter Tight",system-ui,-apple-system,"Segoe UI",sans-serif` |
| `--mono` | `"Space Mono",ui-monospace,Menlo,monospace` |
| `--serif` | `"Newsreader",Georgia,serif` |

## Role-specific aliases

| Token | Value |
|---|---|
| `--wf-border` | `var(--d-line)` |
| `--wf-text` | `var(--d-ink)` |
| `--wf-bg` | `var(--d-panel)` |
| `--wf-font` | `var(--d-font-mono)` |

## Corporate reference overrides — 2026-10-27

| Property | Applied direction | Source |
|---|---|---|
| Display type | DM Sans Light, weight 300; landing hero 76px/82px; section headings 48px/56px | Biofarma computed heading family and weight; sizes adapted to Dugo+ 1440px canvas by user-authorized refinement |
| Application titles | DM Sans Regular, existing sizes retained | Corporate reference; prevent state layout reflow |
| Palette | Existing dark Dugo+ colors retained; muted body text at least source --d-muted #bcaea2 | Dark-only decision; shared HTML CSS |
| Surface shape | Existing 22px panel radius and 999px pill controls | Shared HTML CSS |
| Hero image | Biofarma public home-hero.webp, used as reference artwork in this prototype | https://biofarma.com.ar/wp-content/themes/biofarma-com-ar/img/home-hero.webp |

## Foundation implementation — 2026-10-27

| Item | Applied value / evidence |
|---|---|
| Current reusable tokens | [Foundation plan](foundation-plan.md) lists exact palette, DM Sans scale, spacing, radii and two elevations. [State ledger](foundation-state.json) records all IDs. |
| Authority | Foundation scale applies to reusable components and future migration. Earlier screen-specific sizes remain on unmigrated screens. Dark-only mode is retained. |
| Inventory | 101 variables, 8 text styles, 2 effect styles; semantic color aliases and scoped WEB syntax. |
| Completion | [Handoff and remaining migration work](foundation-handoff.md). |
