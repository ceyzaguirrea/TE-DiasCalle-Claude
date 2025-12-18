# CONTRIBUTING – Proyecto PBIP (Power BI as Code)

¡Gracias por contribuir! Este repositorio usa **PBIP** (PBIR/TMDL) para trabajar Power BI como código, con VS Code y Git.

## Flujo de trabajo
1. Crea una **rama** desde `main` siguiendo el prefijo:
   - `feat/` nuevas funcionalidades
   - `fix/` correcciones
   - `refactor/` refactor sin cambio funcional
   - `repo/` tooling, docs, housekeeping
2. Realiza **commits atómicos** (ver Convenciones de commit).
3. Abre un **PR** hacia `main` usando la plantilla y marca el checklist P0/P1.
4. Espera **aprobación** de revisión antes del merge. Rebase o squash si es necesario.

## Convenciones de commit
Prefijos por ámbito:
- `model(tmdl): ...` cambios en modelo (medidas, columnas, relaciones, roles)
- `report(pbir): ...` cambios en reporte (páginas, visuals, theme)
- `repo: ...` tooling, `.gitignore`, CI, docs
- `docs: ...` documentación del repo

Ejemplos:
- `model(tmdl): agrega [Ventas Netas] y formato % (es-CL)`
- `report(pbir): renombra página 2 y actualiza bookmarks`
- `repo: añade .vscode/settings.json para EOL LF`

## Estándar de nombres y estilo
- Sigue **docs/NAMING.md** para tablas, columnas, medidas, jerarquías, RLS y DAX.
- DAX: `VAR`/`RETURN` en mayúscula, sangría de 2 espacios, líneas < 100 chars.
- Define **formatString** en medidas (moneda/porcentaje/miles) y usa `DisplayFolder`.

## Reglas para el modelo (TMDL)
- Evita **relaciones bidireccionales** salvo justificación clara en el PR.
- Minimiza **M:M**; si es inevitable, documenta impacto/uso.
- Revisa **RLS** (roles/filtros) y prueba con “View as role” en Desktop.
- Mantén **perspectivas** sincronizadas con medidas clave.
- Usa cultura/formatos consistentes (p.ej. `es-CL`).

## Reglas para el reporte (PBIR)
- Evita campos huérfanos en visuals y filtros “ocultos” inesperados.
- Usa nombres claros para páginas y organización de navegación.
- Documenta cambios de **theme/branding**.

## Validación local (obligatoria antes del PR)
- Abre el `.pbip` en **Power BI Desktop** con Developer Mode habilitado.
- Verifica **sin errores de carga**, **medidas compilan**, **visuals operativos**.
- Revisa advertencias del model view y corrige o documenta.

## Seguridad y datos
- **No** incluir secretos/credenciales en el repo.
- No subir binarios `.pbix`/`.pbit` (ver `.gitignore`).
- Usa datos sintéticos si necesitas ejemplos.

## Pull Requests
- Usa la plantilla (`.github/pull_request_template.md`) o `docs/TEMPLATE_PR.md` para copiar/pegar.
- Marca el checklist crítico y adjunta evidencia (capturas, diffs).
- Prioriza hallazgos según P0–P3 (ver **docs/PR_CHECKLIST.md**).

## Code Review
- Tiempo objetivo de primera revisión: 1–2 días hábiles.
- Comentarios deben incluir **sugerencia concreta** y, cuando aplique, referencia a docs.

## Enlaces útiles
- Estándar de nombres: [docs/NAMING.md](NAMING.md)
- Checklist de PR: [docs/PR_CHECKLIST.md](PR_CHECKLIST.md)
