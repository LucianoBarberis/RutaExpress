# Design System: Data-Dense Dashboard

## 1. Definição do Estilo

- **Nome:** Data-Dense Dashboard
- **Tipo:** BI/Analytics
- **Keywords:** Multiple charts/widgets, data tables, KPI cards, minimal padding, grid layout, space-efficient, maximum data visibility
- **Era:** 2020s Modern
- **Light/Dark:** ✓ Full / ✓ Full

## 2. Paleta de Cores

- **Primárias:** Neutral primary (light grey/white #F5F5F5), data colors (blue/green/red), dark text #333333
- **Secundárias:** Chart colors: success (green #22C55E), warning (amber #F59E0B), alert (red #EF4444), neutral (grey)

## 3. Efeitos Visuais

Hover tooltips, chart zoom on click, row highlighting on hover, smooth filter animations, data loading spinners

## 4. AI Prompt Keywords

Design a data-dense dashboard. Use: multiple chart widgets, KPI cards row, data tables with sorting, minimal padding (8-12px), efficient grid layout, filter sidebar, dense but readable typography, maximum information density.

## 5. CSS Technical

```css
display: grid, grid-template-columns: repeat(12, 1fr), gap: 8px, padding: 12px, font-size: 12-14px, overflow: auto for tables, compact card design, sticky headers
```

## 6. Design System Variables

```css
--grid-gap: 8px, --card-padding: 12px, --font-size-small: 12px, --table-row-height: 36px, --sidebar-width: 240px, --header-height: 56px
```

## 7. Checklist de Implementação

- ☐ Grid layout 12 columns
- ☐ KPI cards responsive
- ☐ Tables sortable
- ☐ Filters functional
- ☐ Loading states for data
- ☐ Export functionality

## 8. Visual Theme & Atmosphere

Data-Dense Dashboard — Design bi/analytics com multiple charts/widgets, data tables, kpi cards. Template e prompt pronto para IA. Estilo Data-Dense Dashboard representa uma tendência moderna em design UI/UX web com foco em bi/analytics.

- Density: 8/10 — Dense
- Variance: 2/10 — Structured
- Motion: 6/10 — Expressive

## 9. Color Palette & Roles

- **light grey/white** (#F5F5F5) — Light surface, card backgrounds
- **dark text** (#333333) — Dark surface, primary background
- **green** (#22C55E) — Success states, positive indicators
- **amber** (#F59E0B) — Warning states, attention indicators
- **red** (#EF4444) — Error states, destructive actions

## 10. Typography Rules

- **Display / Hero:** System UI stack (-apple-system, sans-serif) — Weight 700, tight tracking, used for headline impact
- **Body:** System UI stack (-apple-system, sans-serif) — Weight 400, 16px/1.6 line-height, max 72ch per line
- **UI Labels / Captions:** System UI stack (-apple-system, sans-serif) — 0.875rem, weight 500, slight letter-spacing
- **Monospace:** JetBrains Mono — Used for code, metadata, and technical values

Scale:
- Hero: clamp(2.5rem, 5vw, 4rem)
- H1: 2.25rem
- H2: 1.5rem
- Body: 1rem / 1.6
- Small: 0.875rem

## 11. Component Stylings

- **Primary Button:** Subtly rounded (0.5rem) shape. Accent color fill. Hover: 8% darken + subtle lift shadow. Active: -1px translate tactile press. Font weight 600. No outer glows.
- **Secondary / Ghost Button:** Outline variant. 1.5px border in muted color. Text in primary color. Hover: subtle background fill.
- **Cards:** Subtly rounded (0.5rem) corners. Surface background. Subtle shadow (0 2px 12px rgba(0,0,0,0.06)). 1px border stroke.
- **Inputs:** Label above input. 1px border stroke. Focus ring: 2px accent color offset 2px. Error text below in semantic red. No floating labels.
- **Navigation:** Primary surface background. Active item: accent color indicator. Font weight 500 when active.
- **Skeletons:** Shimmer animation matching component dimensions. No circular spinners.
- **Empty States:** Icon-based composition with descriptive text and action button.

## 12. Layout Principles

- **Grid:** CSS Grid primary. Max-width containment: 1280px centered with 1.5rem side padding.
- **Spacing rhythm:** Balanced. Base unit: 0.5rem (8px).
- **Section vertical gaps:** clamp(4rem, 8vw, 8rem).
- **Hero layout:** Split-screen (text left, visual right).
- **Feature sections:** Zig-zag alternating text+image rows. No 3-equal-columns.
- **Mobile collapse:** All multi-column layouts collapse below 768px. No horizontal overflow.
- **z-index contract:** base (0) / sticky-nav (100) / overlay (200) / modal (300) / toast (500).

## 13. Motion & Interaction

- **Physics:** Spring — stiffness 120, damping 20. Confident, weighted transitions.
- **Entry animations:** Fade + translate-Y (16px → 0) over 480ms ease-out. Staggered cascades for lists: 100ms between items.
- **Hover states:** Scale(1.03) + shadow lift over 200ms.
- **Page transitions:** Fade + slide (300ms).
- **Performance:** Only transform and opacity animated. No layout-triggering properties.

## 14. Anti-Patterns (Banned)

- No emojis in UI — use icon system only (Lucide, Heroicons)
- No decorative gradients — flat color only
- No shadows heavier than 0 2px 8px rgba(0,0,0,0.08)
- No pure black (#000000) — use off-black or charcoal variants
- No oversaturated accent colors (saturation cap: 80%)
- No 3-column equal-width feature layouts — use zig-zag or asymmetric grid
- No `h-screen` — use `min-h-[100dvh]`
- No AI copywriting clichés: "Elevate", "Seamless", "Unleash", "Next-Gen"
- No broken external image links — use picsum.photos or inline SVG
- No generic lorem ipsum in demos

## Contexto Histórico

Estilo Data-Dense Dashboard representa uma tendência moderna em design UI/UX web com foco em bi/analytics.

## Caso de Uso

Landing pages, Websites modernas
