# Test Case 5 — Validación de Estructura HTML Semántica y W3C

- **Momentos de ejecución:** Momento 1 (Testing pre-merge) y Momento 2 (retesting).
- **URL Momento 1:** `http://localhost:3000`
- **URL Momento 2:** `http://127.0.0.1:3000/index.html?vscode-livepreview=true`
- **Herramienta utilizada:** Playwright MCP (`@playwright/mcp`), inspección del DOM y árbol de accesibilidad.
- **Responsable:** Lautaro Chavez
- **Rama de referencia del documento original:** `feature/doc-qa-tester-add-test-cases`

---

## 1. Objetivo

Verificar la jerarquía semántica del árbol de accesibilidad, la estructura HTML5 del sitio web de Heladería Vainell y la presencia de nombres accesibles en imágenes y controles interactivos. La validación formal mediante W3C se registra por separado de la inspección realizada en el navegador.

---

## 2. Prompt original — Copilot Agent Mode (Momento 1)

```text
Usa Playwright MCP para realizar la auditoría del Test Case 5: Validación de estructura HTML semántica sobre la aplicación local de Heladería Vainell.

URL:
http://localhost:3000

Instrucciones de prueba:
1. Abre la página en http://localhost:3000.
2. Obtén un snapshot de accesibilidad (accessibility tree / snapshot) para verificar la jerarquía de encabezados (h1, h2, h3) y los landmarks principales (header, nav, main, section, footer).
3. Inspecciona la estructura del código HTML generado y evalúa su conformidad con la sintaxis semántica de HTML5 / W3C.
4. Identifica si existen errores como encabezados salteados (ej. pasar de h1 a h3), etiquetas no semánticas innecesarias o atributos obligatorios faltantes.
5. Toma una captura de pantalla como evidencia.
```

---

## 3. Resultados del Momento 1 — Testing pre-merge

El documento original identifica el objetivo, las herramientas y el procedimiento previsto para la prueba. En el registro disponible no se cuenta con resultados detallados suficientes para reconstruir las mediciones del Momento 1.

Por lo tanto, no se asigna un resultado histórico de PASS o FAIL sin evidencia verificable.

---

## 4. Resultados del Momento 2 — Retesting

### 4.1 Estado de carga

- **Estado:** `document.readyState === "complete"`.
- **Inspección:** DOM renderizado y árbol de accesibilidad obtenidos mediante Playwright MCP.

### 4.2 Encabezados

Se encontraron **17 encabezados**: 1 `h1`, 9 `h2` y 7 `h3`. No se encontraron encabezados `h4`, `h5` ni `h6`, encabezados vacíos o saltos de nivel en la secuencia inspeccionada.

| Orden | Nivel | Texto |
|---:|---|---|
| 1 | `h1` | El frío que enamora. |
| 2 | `h2` | ¿Por qué Vainell? |
| 3 | `h3` | 100% Artesanal |
| 4 | `h3` | Delivery y retiro |
| 5 | `h3` | Atención rápida |
| 6 | `h3` | Para toda ocasión |
| 7 | `h2` | Nuestro catálogo |
| 8 | `h2` | ¿Cómo pedir? |
| 9 | `h2` | Hacé tu pedido |
| 10 | `h2` | Mi cuenta Vainell |
| 11 | `h3` | Iniciar sesión |
| 12 | `h3` | Crear cuenta |
| 13 | `h2` | Lo que dicen nuestros clientes |
| 14 | `h2` | Vainell |
| 15 | `h2` | Navegación |
| 16 | `h2` | Contacto |
| 17 | `h3` | Horarios |

### 4.3 Elementos semánticos

| Elemento | Cantidad observada |
|---|---:|
| `header` | 1 |
| `nav` | 4 |
| `main` | 1 |
| `section` | 10 |
| `aside` | 0 |
| `footer` | 4 |

Los cuatro elementos `footer` corresponden a tres pies de artículo dentro de los testimonios y al pie global de la página. El conteo por sí solo no demuestra un uso incorrecto.

El árbol de accesibilidad mostró los landmarks principales de banner, navegación, contenido principal y pie de página, además de regiones relacionadas con secciones y formularios.

### 4.4 Imágenes y controles interactivos

- **Imágenes:** se encontraron 4; las 4 tienen atributo `alt`. Tres contienen texto alternativo y una tiene `alt=""` en el logo del pie de página, lo que podría ser apropiado si se trata de una imagen decorativa.
- **Controles interactivos:** se inspeccionaron 68. La comprobación del DOM mediante texto, etiquetas, `aria-label`, `aria-labelledby` y `title` no identificó controles sin una fuente reconocible de nombre accesible.
- **IDs duplicados:** no se encontraron.
- **Alcance:** estas comprobaciones son estructurales; no equivalen a una prueba completa con lector de pantalla ni verifican por sí solas toda la accesibilidad.

### 4.5 Validación formal W3C

**Estado: PENDIENTE.**

No se realizó una validación contra el servicio W3C Nu HTML Checker. La inspección del DOM y del árbol de accesibilidad en el navegador no constituye una validación formal W3C, por lo que no se puede afirmar que el documento HTML cumpla completamente con dicho estándar.

### 4.6 Consola del navegador

Se observó un error de carga independiente de los hallazgos semánticos:

- `http://127.0.0.1:3000/favicon.ico` respondió con **404 (Not Found)**.

Este error corresponde al recurso del favicon y no demuestra, por sí solo, un problema en la jerarquía semántica del HTML.

### 4.7 Evidencia del Momento 2

Captura completa obtenida con Playwright MCP:

`docs/04-testing/evidencia-test-case-5-momento-2.png`

La captura se copió al directorio de evidencias y se verificó su existencia mediante PowerShell (`Test-Path` devolvió `True`).

---

## 5. Conclusión del Momento 2

La inspección encontró una jerarquía de encabezados sin saltos de nivel ni encabezados vacíos, los principales landmarks semánticos y atributos `alt` en todas las imágenes inspeccionadas. La revisión estructural de los 68 controles no identificó controles sin una fuente reconocible de nombre accesible y tampoco se encontraron IDs duplicados.

Estos resultados no certifican la accesibilidad completa del sitio ni su conformidad formal con W3C. La validación con Nu HTML Checker permanece pendiente. También queda registrado el error 404 del favicon como observación independiente.
