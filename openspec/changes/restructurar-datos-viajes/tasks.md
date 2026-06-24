# Tasks: Restructurar datos viajes

## Review Workload Forecast

| Field | Value |
|-------|-------|
| Estimated changed lines | ~400-550 |
| 800-line budget risk | Low |
| Chained PRs recommended | No |
| Suggested split | Single PR |
| Chain strategy | size-exception |

Decision needed before apply: No
Chained PRs recommended: No
Chain strategy: size-exception
400-line budget risk: Low

### Suggested Work Units

| Unit | Goal | Likely PR | Notes |
|------|------|-----------|-------|
| 1 | Data + rendering + filters + verify | PR 1 → main | All interdependent; single PR |

## Phase 1: Data Migration

- [x] 1.1 Restructure `src/data/transportes.json` from flat array to `{ empresas[], viajes[] }` — deduplicate 15 entries → 6 empresas + 14 viajes, remove id 7
- [x] 1.2 Convert `horario_salida`/`horario_llegada` string pairs (`&`/space-separated) into typed `horarios: { salida: string, llegada: string }[]` per viaje
- [x] 1.3 Extract "Feriados" from `dias[]` entries into boolean `feriados: true` on affected viajes

## Phase 2: Grouped Rendering

- [x] 2.1 Update `src/pages/index.astro` frontmatter: remove `parseHorarios()`, add empresa grouping logic with `empresas` lookup by `empresa_id`
- [x] 2.2 Rewrite desktop table: wrap each empresa group in `<details>/<summary>` (company name, tipo, WhatsApp link), iterate viajes as `<tr class="transporte-row">` inside
- [x] 2.3 Rewrite mobile cards: same `<details>/<summary>` grouping, each viaje as `<article class="card-mobile">` inside
- [x] 2.4 Update service count from `transportes.length` to show aggregated counts (e.g., "6 empresas · 14 viajes")

## Phase 3: Filter Adaptation

- [x] 3.1 Adapt `Filtros.astro` JS: replace `.transporte-row, .card-mobile` selectors to target viaje elements within grouped DOM, read `data-dias` from new structure
- [x] 3.2 Add group-visibility logic: hide entire `<details>` parent when all its viaje children are `display: none`

## Phase 4: Cleanup & Verify

- [x] 4.1 Remove `parseHorarios()` function and any orphaned references to old flat structure
- [x] 4.2 Run `astro build` — verify zero errors, confirm 14 viajes under 6 empresas in rendered output
