 # Checklist de Pull Request – Proyecto PBIP

> Usa este checklist antes de solicitar revisión. No merges sin marcar todos los P0 y P1.

 ## 1) Validación en Desktop (obligatorio)
 - [ ] Abrí el `.pbip` con **Power BI Desktop (Developer Mode habilitado)**.
 - [ ] **Sin errores de carga** del modelo ni advertencias de artefactos PBIR/TMDL.
 - [ ] Todas las **medidas compilan** (sin `X` rojas en el Model view).
 - [ ] **Visuales sin errores** (no aparece “Ocurrió un error”, icono de advertencia, o campos faltantes).
 - [ ] **Auto Date/Time** deshabilitado (si no es política del proyecto usarlo).
 - [ ] **Referencias de campos** en visuals/filters válidas tras renombres.

 ## 2) Modelo (TMDL)
 - [ ] **Relaciones**: cardinalidad correcta, sin ambigüedades, sin bidireccionalidad innecesaria.
 - [ ] **M:M** solo si está justificado y documentado en el PR.
 - [ ] **RLS**: roles actualizados → filtros correctos y probados en Desktop (View as role).
 - [ ] **Medidas**: formato definido (%, moneda, miles), `DisplayFolder` correcto, nombres consistentes.
 - [ ] **Columnas**: tipo de datos adecuado, formato (si aplica), sin columnas huérfanas.
 - [ ] **Perspectivas** (si existen): incluyen las medidas clave y están sincronizadas con cambios.
 - [ ] **Cultures/format strings**: consistentes (p.ej., `es-CL` o la cultura oficial del proyecto).

 ## 3) Reporte (PBIR)
 - [ ] **Páginas** y **visuals**: sin dependencias rotas; bookmarks/selection panes funcionales.
 - [ ] **Theme/branding** aplicados o documentada su ausencia.
 - [ ] **Filtros** a nivel Visual/Página/Reporte revisados (evitar “filtros sorpresa”).
 - [ ] Nombres de páginas claros y consistentes con navegación.

 ## 4) Estructura de carpetas y Git
 - [ ] `.gitignore` vigente (excluye `.pbix/.pbit` y temporales).
 - [ ] Archivos en texto (PBIR/TMDL) formateados (EOL LF, espacios, tab=2).
 - [ ] Sin binarios innecesarios ni archivos temporales.
 - [ ] `README.md` actualizado si cambian prácticas o requisitos.
 - [ ] **Commits atómicos** y mensajes claros (prefijo `model/`, `report/`, `repo/`).

 ## 5) Seguridad y datos
 - [ ] **RLS probado** y documentado si cambia.
 - [ ] No hay credenciales/secretos en archivos del repo.
 - [ ] Datos de prueba sintéticos (o referencias) si se añaden ejemplos.

 ---

 ## Niveles de Prioridad
 - **P0**: rompe visuals/cálculos o introduce riesgo de seguridad (RLS).
 - **P1**: alto impacto en performance/mantenibilidad (relaciones M:M, bidireccional sin justificación).
 - **P2**: calidad/UX (nombres, carpetas, theme).
 - **P3**: nitidez/estándar (metadatos menores).

 ## Evidencia sugerida en el PR
 - Capturas de Desktop (Model/Report) post-cambios.
 - Diff enfocado (fragmentos TMDL relevantes).
 - Breve “antes/después” de medidas/relaciones claves.

 ## Post-merge (opcional)
 - [ ] Crear tarea para “Acciones estructurales (30 días)” si quedaron P2/P3 pendientes.
