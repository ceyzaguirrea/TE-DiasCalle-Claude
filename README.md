# PBIP + VS Code (+Git)

Este repositorio está preparado para trabajar proyectos **Power BI** en formato **PBIP (Power BI Project)** utilizando **VS Code** y **Git**, permitiendo tratar el modelo y el reporte como código versionable y auditable.

El proyecto incorpora además un **flujo gobernado para el uso de agentes AI** (por ejemplo Codex) como apoyo al análisis y la generación de propuestas de cambio.

---

## Estructura esperada del proyecto

```
MiProyecto.pbip
MiProyecto.Report/
MiProyecto.SemanticModel/
.vscode/
docs/
```

- `*.pbip`  
  Archivo de proyecto de Power BI.

- `*.SemanticModel/`  
  Modelo semántico en formato **TMDL** (tablas, columnas, medidas, relaciones, RLS, perspectivas).

- `*.Report/`  
  Definición del reporte en formato **PBIR** (páginas, visuales, filtros, bookmarks).

- `.vscode/`  
  Configuración de VS Code compartida por el equipo.

- `docs/`  
  Documentación oficial del proyecto (estándares, checklist, flujo AI).

> Abre siempre el archivo `.pbip` con **Power BI Desktop** (Developer Mode activo) para validar cambios en el modelo y el reporte.

---

## 🤖 Trabajo con agentes (AI / Codex)

Este proyecto permite el uso de **agentes AI** como apoyo para:
- Auditoría del modelo (TMDL)
- Identificación de riesgos y malas prácticas
- Propuesta de mejoras
- Generación de parches revisables

El uso de agentes está **estrictamente gobernado**.

### Documentación obligatoria
Antes de iniciar cualquier trabajo asistido por AI, **DEBES** leer y seguir:

- 📘 **Guía paso a paso para instruir al agente** (`docs/AGENT_PLAYBOOK.md`)
- 🧭 Guía de contribución (`docs/CONTRIBUTING.md`)
- 🏷️ Estándar de nombres (`docs/NAMING.md`)
- ✅ Checklist de Pull Request (`docs/PR_CHECKLIST.md`)

### Reglas clave
- Los agentes **no modifican archivos directamente**.
- Todos los cambios se entregan como **parches revisables (.patch)**.
- Todo cambio debe validarse manualmente en **Power BI Desktop**.
- Ningún cambio puede violar los estándares definidos en `/docs`.

---

## Extensiones recomendadas para VS Code

- GitLens (`ms-vscode.gitlens`)
- Code Spell Checker (`streetsidesoftware.code-spell-checker`)
- Prettier – Code formatter (`esbenp.prettier-vscode`)
- YAML (`redhat.vscode-yaml`)
- Markdown All in One (`yzhang.markdown-all-in-one`)

VS Code sugerirá instalarlas automáticamente gracias a `.vscode/extensions.json`.

---

## Ajustes del editor

El archivo `.vscode/settings.json` define configuraciones comunes para todo el equipo:

- End of line: `LF`
- `tabSize = 2`
- Espacios en lugar de tabs
- Trim de espacios en blanco
- Formateo automático al guardar

Esto asegura **diffs limpios y consistentes** en archivos TMDL y PBIR.

---

## Buenas prácticas de Git

- **Commits atómicos**, con mensajes claros y prefijos por ámbito:
  - `model(tmdl): agrega [Ventas Netas]`
  - `report(pbir): renombra página Ventas`
  - `repo: actualiza documentación`

- Todo cambio debe pasar por **Pull Request**.
- El PR debe cumplir el checklist definido en `docs/PR_CHECKLIST.md`.
- **Nunca** versionar archivos binarios:
  - `.pbix`
  - `.pbit`

---

## Flujo de trabajo recomendado

1. Crear rama desde `main`.
2. Análisis en modo solo lectura.
3. Planificación de cambios (P0–P3).
4. Propuesta de cambios mediante parches.
5. Validación manual en Power BI Desktop.
6. Apertura de Pull Request con evidencia.
7. Revisión y aprobación.

---

## Referencias rápidas

- Guía de agentes AI: `docs/AGENT_PLAYBOOK.md`
- Contribución: `docs/CONTRIBUTING.md`
- Naming: `docs/NAMING.md`
- Checklist PR: `docs/PR_CHECKLIST.md`
