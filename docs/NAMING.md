 # Estándar de Nombres – Proyecto PBIP

> Objetivo: legibilidad, consistencia y mantenibilidad del modelo y reporte.

 ## Tablas
 - **Hechos**: `Fact Ventas`, `Fact Transacciones`
 - **Dimensiones**: `Dim Cliente`, `Dim Producto`, `Dim Fecha`
 - Evitar acrónimos opacos; si se usan, documentarlos en el README.
 - Singular/Plural: usar **singular** salvo casos muy conocidos (`Dim Fechas`).

 ## Columnas
 - Nombres en **Título Capitalizado** si son de negocio: `Fecha Venta`, `Precio Lista`.
 - Propiedades técnicas/IDs en PascalCase si aplica: `CustomerId`, `OrderId`.
 - Evitar prefijos redundantes del nombre de la tabla (no `Cliente Nombre` dentro de `Dim Cliente`).

 ## Medidas (DAX)
 - Corchetes en referencias: `[Ventas]`, `[Margen %]`.
 - Prefijos solo si agregan valor (p.ej., `MTD Ventas`, `YTD Ventas`). Evitar `Med_` o `M_` si no es política.
 - **Display Folder** por dominio: `Ventas\Importes`, `Ventas\Ratios`, `Inventario\Stock`.
 - **Formato** obligatorio: moneda/porcentaje/miles; `es-CL` si el proyecto lo define.
 - Descripciones opcionales pero recomendadas (qué hace, supuestos).

 ### Estilo DAX
 - Palabras clave en mayúscula: `VAR`, `RETURN`, `CALCULATE`.
 - Sangría de 2 espacios y líneas cortas (<100 chars).
 - Ejemplo:
   ```DAX
   Ventas Netas :=
     VAR _desc = SUM(Fact Ventas[Descuentos])
     RETURN
       SUM(Fact Ventas[Importe]) - _desc
   ```

 ## Jerarquías
 - Nombre semántico: `Fecha (Año > Mes > Día)`, `Producto (Categoría > Subcategoría > SKU)`.

 ## Roles (RLS)
 - `RLS Ventas Región`, `RLS Soporte País`.
 - Documentar la columna/expresión usada en el filtro en la descripción del rol.

 ## Perspectivas
 - `SelfService`, `Executive`, `Finance`, etc.
 - Deben incluir **medidas clave** y ocultar columnas técnicas.

 ## Reporte (PBIR)
 - Páginas: `0. Portada`, `1. Ventas`, `2. Clientes`, `99. Auxiliar` (para pruebas/ocultas).
 - Visuals críticos identificados en la descripción del visual (opcional).
 - Bookmarks: `Navegación - Menu`, `Detalle - Cliente Seleccionado`.

 ## Culturas y Formatos
 - Cultura por defecto: `es-CL` (o la del proyecto).
 - Monedas: CLP/UF/USD según alcance; documentar `formatString`.
 - Fechas: `dd-MM-yyyy` si aplica; alinear con requerimientos locales.

 ## Renombres y migraciones
 - Cambios que rompen referencias deben ir en **ramas propias** y PR con evidencia.
 - Incluir tabla de mapeo en el PR (Antes → Después) para medidas/columnas.
 - Tras renombres, revisar: visuals, filtros, bookmarks, RLS, perspectivas.

 ## Commits y prefijos sugeridos
 - `model(tmdl): ...` cambios en modelo (medidas/relaciones/roles).
 - `report(pbir): ...` cambios en reporte (páginas/visuales/tema).
 - `repo: ...` housekeeping (README, .gitignore, tooling).
