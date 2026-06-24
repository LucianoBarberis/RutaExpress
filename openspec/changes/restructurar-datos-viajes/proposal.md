# Proposal: Restructurar datos viajes

## Intent

Eliminar duplicación de datos de empresa y horarios inconsistentes en `transportes.json`. La estructura plana actual repite nombre/teléfono por viaje (Los Ranqueles aparece 6 veces), mezcla "Feriados" como día suelto, y usa strings con `&` para múltiples horarios. La UI se reorganiza agrupando por empresa con acordeones (`<details>/<summary>`).

## Scope

### In Scope
- Migrar `transportes.json` de array plano a `{ empresas[], viajes[] }`
- Deduplicar empresas y eliminar viaje duplicado accidental (ids 6 y 7)
- Convertir `dias` con "Feriados" en booleano `feriados`
- Estructurar horarios múltiples (separados por `&` o espacio) en `horarios[]`
- Renderizado agrupado por empresa en tabla desktop y cards mobile
- Filtros adaptados a nuevo DOM agrupado

### Out of Scope
- Nuevos campos en la UI o datos adicionales
- Cambios visuales o de diseño
- Otras páginas (contacto, privacidad, 404)

## Capabilities

### New Capabilities
None — refactor interno de datos y renderizado, sin cambios en comportamiento observable.

### Modified Capabilities
None — las capacidades existentes (ver servicios, filtrar) se mantienen idénticas.

## Approach

1. **Migrar datos**: Mapear las 15 entradas → 6 empresas únicas, 13 viajes (eliminando id 7). Extraer `&`-horarios a `horarios[]`. Mover "Feriados" de array `dias` a booleano `feriados`.
2. **Renderizado**: Agrupar viajes por `empresa_id` con `<details>` anidando `<table>` rows o cards. El `<summary>` muestra empresa + tipo + botón WhatsApp. Cada viaje interno es un `<tr>` o sub-card con sus `data-*` attributes.
3. **Filtros**: Actualizar selectores JS de `.transporte-row, .card-mobile` a los nuevos elementos. La lógica de filtrado (tipo, origen, día, búsqueda) se aplica a cada viaje; si ningún viaje de una empresa es visible, se oculta el grupo entero.
4. **Eliminar `parseHorarios`**: Ya no es necesario porque `horarios[]` viene pre-estructurado.
5. **Verificar**: `astro build` pasa sin errores.

## Affected Areas

| Area | Impact | Description |
|------|--------|-------------|
| `src/data/transportes.json` | Modified | Nueva estructura `{ empresas[], viajes[] }` |
| `src/pages/index.astro` | Modified | Renderizado agrupado por empresa + acordeones |
| `src/components/Filtros.astro` | Modified | Selectores y lógica adaptados a DOM agrupado |

## Risks

| Risk | Likelihood | Mitigation |
|------|------------|------------|
| Filtros no funcionan con nuevo DOM | Medium | Probar cada filtro (tipo, origen, día, búsqueda) manualmente |
| Error en parsing de horarios con `&` | Low | Verificar visualmente que Gisala Sicacardi (ids 11,12) muestre horarios correctos |

## Rollback Plan

`git revert` del commit de migración, o restaurar `transportes.json` original + `index.astro` y `Filtros.astro` previos.

## Dependencies

Ninguna.

## Success Criteria

- [ ] `astro build` exitoso sin errores
- [ ] 13 viajes visibles (no 15), agrupados bajo 6 empresas
- [ ] Acordeones expanden/colapsan cada grupo de empresa
- [ ] Filtros (tipo, origen, día, búsqueda) ocultan viajes y grupos completos correctamente
- [ ] Vista mobile cards funciona con la misma agrupación
