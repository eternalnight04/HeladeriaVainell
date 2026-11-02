# spec-frontend.md — Desarrollador Frontend/CSS

**Proyecto:** Heladería Vainell
**Materia:** Programación Web I — UCES (1er cuatrimestre 2026), Lic. Matias Velasquez
**Entrega:** Actividad Obligatoria N°2 (CSS, diseño responsive y QA asistido por MCP)
**Rol:** Desarrollador Frontend/CSS
**Rama:** `feature/dev-frontend-css-add-styles` → `develop`
**Ubicación:** `docs/03-specs/actividad-obligatoria-2/spec-frontend.md`

---

## PARTE 1 — PLANIFICACIÓN PREVIA

### 1. Qué se va a hacer

Generar la capa de presentación de la página `index.html` a partir del mockup de Figma actualizado por el Coordinador/DevOps, usando el **servidor MCP de Figma** junto con **GitHub Copilot en modo Agente**. Se entregan dos archivos:

| Archivo | Responsabilidad |
|---|---|
| `css/styles.css` | Variables CSS en `:root` (paleta, tipografías, escala tipográfica, espaciados, radios, sombras, transiciones), reset, estilos base, layout base de header, hero, secciones, catálogo, formularios y footer. |
| `css/components.css` | Componentes reutilizables: navegación, botones, cards, formularios, tablas del catálogo, galería de imágenes, franja de beneficios, con estados `hover`, `focus-visible` y `disabled`. |

`css/responsive.css` es responsabilidad del Especialista en Responsive Design; este spec solo define la base sobre la que trabaja (sin overflow horizontal y con grillas que colapsan solas).

### 2. Por qué

- Cumplir con la consigna: CSS separado por responsabilidad, coherente con el mockup actualizado (tipografías, paleta y espaciados).
- Mantener el HTML limpio: toda la presentación vive en CSS y el HTML conserva solo estructura semántica y contenido.
- Dejar tokens de diseño centralizados (`:root`) para que el Especialista en Responsive y futuras entregas puedan reutilizarlos sin duplicar valores.
- Aprovechar Figma MCP para reducir errores de transcripción del mockup y dejar evidencia del flujo asistido por IA.

### 3. Decisiones técnicas previstas

- **Selectores:** mezcla de selectores de elemento, clase, id, descendientes, hijos directos (`>`), pseudo-clases (`:hover`, `:focus-visible`, `:has()`, `:invalid`) y pseudo-elementos (`::before`, `::after`), aprovechando herencia (color y fuente definidos en `body`) y especificidad controlada (se prefiere `body > header` y `#seccion > …` antes que `!important`).
- **Box model:** `box-sizing: border-box` global y control explícito de `padding`, `margin` y `border` en cada componente.
- **En línea vs. bloque:** decisión explícita y comentada. En línea: `a`, `em`, `strong`, `span`, `small`. En bloque: `img`, `figure`, `blockquote`, `address`, `label`. Cambios deliberados de `display` donde el diseño lo pide (ej. `small` a bloque dentro de las métricas del hero).
- **Layout:** `display: grid` para hero, grillas de cards, catálogo, testimonios, cuenta y footer; `display: flex` para header, navegación, botones, métricas y fieldset de modalidad. Se usa `repeat(auto-fit, minmax(min(100%, X), 1fr))` para que las grillas colapsen sin media queries.
- **Accesibilidad:** foco visible global (`:focus-visible`), contraste de texto sobre fondos de la paleta y `prefers-reduced-motion`.
- **Comentarios:** cada bloque lleva un comentario explicando la decisión de estilo.

### 4. Criterios de aceptación

- [ ] Este `spec-frontend.md` existe en `docs/03-specs/actividad-obligatoria-2/` y está commiteado antes que cualquier archivo CSS.
- [ ] Figma MCP se usó con Copilot Agent para generar los estilos desde el mockup actualizado.
- [ ] El prompt exacto, el resultado y los ajustes manuales quedan documentados en este archivo (Parte 2).
- [ ] `css/styles.css` define variables en `:root`, reset, tipografías, colores y layout base coherentes con el mockup.
- [ ] `css/components.css` define botones, cards, navegación y formularios con estados `hover`/`focus`.
- [ ] Se aplican selectores, herencia y especificidad de forma correcta (sin `!important` salvo `prefers-reduced-motion`).
- [ ] Box model con control explícito de `padding`, `margin` y `border`.
- [ ] Elementos en línea y en bloque diferenciados mediante CSS.
- [ ] Ningún título ni texto queda tapado por imágenes o elementos decorativos.
- [ ] Todas las imágenes del proyecto se ven en la página y no generan overflow horizontal.
- [ ] Se realizaron pruebas de integración con el Especialista en Responsive en localhost y GitHub Pages.
- [ ] Los bugs reportados por el QA Tester se resolvieron antes del merge a `develop`.
- [ ] El PR fue revisado y aprobado por el Coordinador, está enlazado en `changelog.md` y tiene un issue vinculado, cerrado post-merge.

---

## PARTE 2 — EVIDENCIA AL CIERRE

### 5. Herramientas y flujo

- **Mockup:** archivo Figma actualizado por el Coordinador (Dev Mode, nodo `1:3`).
- **IA:** GitHub Copilot en modo Agente en VS Code, con el servidor **MCP de Figma**.
- **Contexto:** este spec, `index.html`, `plan.md` y las imágenes de la carpeta `imagenes/`.
- **Verificación:** navegador local en tres anchos (390, 820 y 1280 px), comprobación de enlaces internos e IDs, y `git diff --check`.

### 6. Prompts utilizados y resultados

El trabajo se hizo de forma iterativa, con seis prompts consecutivos en un mismo chat de Copilot Agent.

#### Prompt 1 — Verificar la conexión con Figma MCP y generar el HTML base

```text
Primero verifica si la conexión con Figma MCP al siguiente Dev Mode link funciona correctamente.
Una vez que se comprobó la conexión, extrae el código html de este modelo de Figma y ponlo en el archivo index.html, incluye comentarios a tener en cuenta para poder incluir los estilos y componentes en archivos aparte.
```

**Resultado:** la conexión MCP con Figma quedó comprobada: Copilot consultó los metadatos del nodo `1:3` y obtuvo la captura. Sin embargo, `get_design_context` no devolvió el HTML, solo indicó que había recursos de código. Por eso el contenido de `index.html` es una **reconstrucción semántica a partir de la captura**, no una extracción literal. Se actualizaron el encabezado, el hero y la franja de beneficios, y se añadieron comentarios que separan responsabilidades entre `styles.css`, `components.css` y `responsive.css`. Se dejó indicado dónde incorporar la ilustración exacta de Capitán Helado, que aún no estaba entre los recursos locales.
**Fidelidad al mockup:** estructura y jerarquía fieles; los detalles visuales finos requirieron los prompts siguientes.

#### Prompt 2 — Ubicar las imágenes y adaptar los estilos

```text
Ahora, siguiendo el archivo index.html, ubica las imagenes correspondientes de la carpeta en la página y modifica los archivos styles.css, components.css y responsive.css, si es necesario.
```

**Resultado:** se ubicó el logo en el header y el footer, Capitán Helado en el hero y tres fotos de producto en la galería del catálogo. Se agregaron estilos para el hero y las imágenes, y se adaptó la galería a móvil, tablet y escritorio. Copilot detectó que `helados.png` era en realidad un archivo AVIF y corrigió la extensión a `helados.avif`. Verificación en 390, 820 y 1280 px: todas las imágenes cargan y no hay desbordamiento horizontal.

#### Prompt 3 — Evitar que las imágenes opaquen el texto

```text
Modifica el código de la página de forma tal que ningún título o palabra se vea opacado por imagenes o visuales. Especialmente la imagen del Capitan Helado. Debe verse y lucirse pero no debe opacar el texto.
```

**Resultado:** el hero prioriza visualmente el texto. La ilustración queda limitada al espacio de su columna y el rótulo se separó de la imagen para que no se superpongan. Verificado en los tres anchos. Cambios en `styles.css` y `responsive.css`.

#### Prompt 4 — Integrar el encabezado de sección "Nuestro secreto"

```text
La oración "Nuestro secreto" se ve un poco fuera de lugar con el resto de la página. Haz que destaque y encaje teniendo en cuenta que un usuario de la web leería el texto en el siguiente órden: "Nuestro secreto... ✨Un poco de magia✨"
```

**Resultado:** la sección se lee en el orden pedido: "Nuestro secreto" seguido de "✨ Un poco de magia ✨". La frase introductoria destaca con líneas decorativas y el título mantiene la jerarquía visual del resto de la página. Cambios en `index.html` y `styles.css`.

#### Prompt 5 — Dar más presencia a Capitán Helado

```text
Agranda un poco la imagen del Capitan Helado y acerca un poco más los globos "Menta" y "Vainilla" hacia este. La imagen puede estar ligeramente debajo del cuadro de texto "Conoce a Capitán Helado Guardían del Sabor". Esto es para que se destaque y no haya tanto espacio vacío cuando el usuario mire al personaje.
```

**Resultado:** se agrandó la ilustración y se acercaron las etiquetas "Menta" y "Vainilla". El rótulo se superpone ligeramente a la parte inferior de la imagen, con fondo opaco (`--color-cream`) para conservar la legibilidad. Comprobado en móvil, tablet y escritorio: la imagen carga, el título no queda cubierto y no hay desbordamiento horizontal. Cambio en `styles.css`.

### 7. Ajustes manuales realizados

| Ajuste | Motivo |
|---|---|
| Corrección de `helados.png` → `helados.avif` | El archivo era AVIF con extensión incorrecta, por lo que la referencia fallaba. |
| Ajuste del héroe (columna de texto, rótulo y etiquetas de sabor) | Evitar que la ilustración opaque el título y reducir el espacio vacío alrededor del personaje. |
| Tratamiento visual de "Nuestro secreto" | Integrarlo con el resto de la página y respetar el orden de lectura. |


### 8. Estructura de los archivos CSS generados

**`css/styles.css`**
1. Variables (`:root`): paleta (teal, menta, dorado, crema, rosa), neutros, tipografías (Fredoka para títulos, Nunito para cuerpo), escala tipográfica `--fs-*`, espaciados `--space-1` a `--space-8`, radios, sombras, transición y `--gutter`.
2. Reset (box-sizing, márgenes, `fieldset`, controles de formulario).
3. Estilos base (herencia desde `body`, títulos h1–h3, enlaces, `:focus-visible`, elementos en línea vs. bloque).
4. Layout base: secciones del `main`, header sticky, hero en grid de dos columnas con burbujas decorativas, ilustración de Capitán Helado, grillas de "Por qué Vainell", catálogo, "Cómo pedir", formulario de pedido, "Mi cuenta", testimonios y footer.

**`css/components.css`**
1. Navegación (pills, botón de pedido con contador, categorías del catálogo, links del footer).
2. Botones (base compartida, secundario, "Agregar" de tablas, envío de formularios) con estados `hover`, `focus-visible`, `active` y `disabled`.
3. Cards (¿Por qué Vainell?, pasos de "Cómo pedir" con contador CSS, testimonios, cuenta) y galería del catálogo con `object-fit`.
4. Formularios (inputs, select, textarea, radios tipo chip, estados `hover`, `focus` e `invalid`).
5. Tablas del catálogo con filas tipo card y `border-spacing`.
6. `prefers-reduced-motion`.

### 9. Estado de los criterios de aceptación

- [x] Figma MCP usado con Copilot Agent (conexión comprobada sobre el nodo `1:3`).
- [x] Prompts, resultados y ajustes manuales documentados en este archivo.
- [x] `styles.css` con variables, reset, tipografías, colores y layout base.
- [x] `components.css` con componentes y estados hover/focus.
- [x] Selectores, herencia y especificidad aplicados.
- [x] Box model con control explícito.
- [x] Elementos en línea y en bloque diferenciados.
- [x] Texto no opacado por imágenes (verificado en 390, 820 y 1280 px).
- [x] Imágenes cargan y no hay overflow horizontal en los tres anchos probados.
- [x] Pruebas de integración con el Especialista en Responsive en localhost y GitHub Pages.
- [x] Bugs del QA Tester resueltos antes del merge:
    + [BUG] Desbordamiento horizontal (overflow) en versión mobile por imagen hero. Issue [#23](https://github.com/eternalnight04/HeladeriaVainell/issues/23)
    + [BUG] Estructura de lista de definición invalida (regla dlitem) en sección de características. Issue [#24](https://github.com/eternalnight04/HeladeriaVainell/issues/24)
    + [BUG] Errores de validación HTML W3C, marcado sintáctico e incorrecta estructura de footer. Issue [#25](https://github.com/eternalnight04/HeladeriaVainell/issues/25)
- [x] PR aprobado por el Coordinador, enlazado en `changelog.md`, con issue vinculado y cerrado.
