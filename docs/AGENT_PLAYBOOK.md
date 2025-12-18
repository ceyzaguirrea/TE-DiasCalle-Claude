# Guía paso a paso para instruir al agente (PBIP + VS Code + Git)

Este documento define **cómo darle instrucciones precisas al agente (Codex/AI)** para trabajar un proyecto **Power BI en formato PBIP**, considerando toda la documentación y estándares incorporados al repositorio.

---

## 0. Contexto del proyecto (lectura obligatoria)

Antes de ejecutar cualquier acción, el agente **DEBE** analizar y comprender el contexto completo del repositorio.

### Documentos de referencia

Indícale explícitamente que lea y respete:

1. **README.md**

   * Contexto general del proyecto PBIP.
   * Estructura esperada del repositorio.

2. **docs/CONTRIBUTING.md**

   * Flujo de trabajo con Git.
   * Convenciones de ramas y commits.
   * Reglas para TMDL (modelo) y PBIR (reporte).

3. **docs/NAMING.md**

   * Estándar de nombres para tablas, columnas, medidas, jerarquías, RLS y perspectivas.
   * Estilo DAX obligatorio.

4. **docs/PR_CHECKLIST.md**

   * Criterios P0–P3.
   * Validaciones obligatorias en Desktop.

5. **.vscode/settings.json**

   * Reglas de formato (EOL LF, tabSize=2, trim whitespace).

> 🔒 Regla base: **ningún cambio puede violar estos documentos**.

---

## 1. Instrucción inicial al agente (modo auditoría)

Siempre comienza con un prompt de **solo lectura**, sin modificar archivos.

### Prompt recomendado

```
Actúa como revisor senior de proyectos Power BI en formato PBIP.

Antes de hacer cualquier cambio:
1) Lee y comprende README.md y todos los documentos en /docs.
2) Confirma explícitamente que cumplirás docs/CONTRIBUTING.md y docs/NAMING.md.
3) Analiza el proyecto en modo SOLO LECTURA.

Entrega un informe en Markdown con:
- Resumen ejecutivo.
- Hallazgos priorizados P0–P3.
- Evidencia por archivo (ruta exacta).
- Limitaciones que requieran validación en Power BI Desktop.

No modifiques archivos.
```

**Resultado esperado:** un diagnóstico confiable y priorizado.

---

## 2. Traducción del análisis a un plan de acción

Una vez aprobado el informe, el siguiente paso es **planificar**, no ejecutar.

### Prompt recomendado

```
Usando el informe de hallazgos aprobado:

1) Crea PLAN_EJECUCION.md.
2) Divide acciones en:
   - P0 (crítico, hoy)
   - P1 (alto impacto, 48h)
   - P2 (calidad/UX)
   - P3 (estándar)
3) Lista archivos TMDL/PBIR afectados por cada acción.
4) Indica riesgos y validaciones manuales requeridas en Desktop.

No realices cambios aún.
```

---

## 3. Generación de cambios como parches (no aplicar)

El agente **NO debe editar directamente** el modelo ni el reporte. Todo se entrega como parches revisables.

### Prompt recomendado

```
Genera parches (.patch) sin aplicarlos para resolver P0 y P1:

- Un patch por tema.
- Ubícalos en patches/p0/ y patches/p1/.
- Cumple estrictamente docs/NAMING.md y docs/CONTRIBUTING.md.

Acompaña con:
- RESUMEN_CAMBIOS.md (qué cambia, por qué, impacto).
- Lista de validaciones requeridas en Power BI Desktop.

No apliques los parches.
```

---

## 4. Casos específicos de instrucciones

### 4.1 Medidas DAX

```
Identifica medidas sin formato o naming inconsistente.

Genera un patch que:
- Defina formatString correcto (%, moneda, miles).
- Use DisplayFolder por dominio.
- Respete el estilo DAX definido en docs/NAMING.md.

Incluye una tabla Antes → Después.
```

### 4.2 Relaciones

```
Revisa relaciones M:M o bidireccionales.

Propón alternativas 1:* o tablas puente.
Documenta cada cambio con justificación.
Genera patch separado para relaciones.
```

### 4.3 RLS

```
Audita roles RLS existentes.

- Detecta filtros inseguros o rotos.
- Propón expresiones seguras.
- Genera patch + docs/RLS_TESTS.md con pasos de validación.
```

---

## 5. Reporte (PBIR): enfoque conservador

PBIR se trabaja **solo cuando el modelo está estable**.

### Prompt recomendado

```
Analiza PBIR en modo lectura:
- Visuales con campos huérfanos.
- Bookmarks inconsistentes.
- Filtros ocultos riesgosos.

Entrega PBIR_FIX_PLAN.md.
No modifiques PBIR directamente.
```

---

## 6. Preparación del Pull Request

### Prompt recomendado

```
Usa docs/TEMPLATE_PR.md y .github/pull_request_template.md.

1) Rellena checklist P0/P1.
2) Enlaza docs/NAMING.md y docs/PR_CHECKLIST.md.
3) Agrega evidencia (diffs + capturas sugeridas).

No crees el PR, solo deja el contenido listo.
```

---

## 7. Regla de oro

> ❗ **El agente nunca decide aplicar cambios críticos por su cuenta.**
> Todo cambio debe ser:
>
> 1. Analizado
> 2. Planificado
> 3. Propuesto como patch
> 4. Validado en Desktop
> 5. Revisado vía PR

---

## 8. Frase de inicio recomendada (copy/paste)

```
Antes de comenzar:
- Lee README.md y todos los archivos en /docs.
- Confirma cumplimiento de docs/CONTRIBUTING.md y docs/NAMING.md.
- Trabaja primero en modo SOLO LECTURA.
- No apliques cambios sin entregar parches revisables.
```
