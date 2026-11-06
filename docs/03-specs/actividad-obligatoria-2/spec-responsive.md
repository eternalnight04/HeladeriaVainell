# spec-responsive.md — Especialista en Responsive Design

**Proyecto:** Vainell
**Entrega:** Actividad Obligatoria N°2
**Rol:** Especialista en Responsive Design
**Rama:** `feature/responsive-design-add-responsive-styles` → `develop`
**Ruta:** `docs/03-specs/actividad-obligatoria-2/spec-responsive.md`

---

## PARTE A — Planificación previa

> Esta parte conserva el análisis y el plan iniciales. La implementación vigente,
> los ajustes que se apartaron del plan y la evidencia de pruebas están en la Parte B.

## 1. Qué se va a hacer

- Crear `css/responsive.css`: media queries organizadas por breakpoint (mobile, tablet, desktop, más dos refinamientos) que adaptan layout, tipografías y componentes del sitio usando Flexbox y CSS Grid.
- Confirmar que `index.html` enlaza `<link rel="stylesheet" href="css/responsive.css">` en el `<head>`, **después** de `styles.css` y `components.css`, para que sus reglas ganen en la cascada.
- Usar una herramienta de IA con este spec, `css/styles.css`, `css/components.css`, `index.html` y el mockup como contexto (la herramienta efectivamente usada se declara en la Parte B).
- No se modifican `styles.css` ni `components.css` (son del Desarrollador Frontend/CSS). Si hace falta un cambio en ellos, se coordina con esa persona y queda registrado en el `changelog.md`.

## 2. Qué hay que adaptar (análisis de los CSS actuales)

Revisión de `styles.css` y `components.css` sobre el `index.html` actual:

| Elemento | Estado actual | Problema en pantallas chicas |
|---|---|---|
| `body > header` | `position: sticky`, flex con `flex-wrap`: marca + 6 enlaces + botón "Pedir ahora" | En mobile y tablet el menú se parte en varias filas y el header fijo ocupa demasiado alto |
| Logo "V" del header | El HTML ahora trae `<span>V</span>` en lugar de una imagen y no tiene estilo | Se ve como texto suelto |
| `#inicio` | Grid `auto-fit` con `minmax(min(100%, 24rem), 1fr)` | La cantidad de columnas depende del ancho y no se controla por breakpoint |
| `.hero-imagen` | Foto del cono, nueva en el HTML, sin estilo; el atributo `height="400"` no manda porque `img` tiene `height: auto` | Sin tope de alto: ocupa casi toda la pantalla en mobile |
| `#inicio ul` | Las métricas ahora son texto simple, pero `styles.css` las estiliza como números grandes (`--fs-xl`) | Quedan desproporcionadas |
| `.hero-tarjeta img` | `width: 100%` | El SVG de Capitán Helado, cuadrado, resulta gigante en la columna de desktop |
| `#inicio > figure img` | `aspect-ratio: 21 / 9` | En mobile queda una tira muy fina |
| `#caracteristicas dl`, "¿Por qué?", "¿Cómo pedir?", testimonios, cuenta | `auto-fit` + `minmax` | En 820px dejan filas huérfanas (3 + 1, 2 + 1) |
| Tablas del catálogo | 4 columnas; `td:nth-child(2)` con `min-width: 14rem`; scroll en `#catalogo > div` | En mobile obligan a scrollear horizontalmente; el botón "Agregar" mide ~37px de alto |
| `main > section` | Padding vertical `var(--space-8)` (4.5rem) | Excesivo en mobile |
| `body > footer` | Grid `auto-fit` con `minmax(min(100%, 15rem), 1fr)` | En tablet deja una columna huérfana |
| `<h2>Vainell</h2>` del footer | Oculto visualmente en `styles.css` porque antes estaba la marca con logo (`.marca`), que ya no está en el HTML | La primera columna del footer queda sin título visible |
| Efectos `:hover` con `translateY` | Definidos sin condición | En pantallas táctiles el hover queda "pegado" |
| Header fijo | Siempre `sticky` | En celulares en horizontal tapa media pantalla |

## 3. Breakpoints y por qué

Se definen tres breakpoints principales, alineados con los dispositivos que el QA Tester debe probar según la consigna (test-case-1 y test-case-2), más dos de refinamiento. Se expresan en `rem` (1rem = 16px).

| Nombre | Regla | Dispositivos objetivo | Justificación |
|---|---|---|---|
| Mobile | Base (sin media query), hasta 767px | iPhone 14 Pro 390×844, Samsung Galaxy S23 412×915. Se revisa también 360px y 320px como piso | Es donde más cambia el layout: todo pasa a una columna |
| Tablet | `@media (min-width: 48rem)` (768px) | iPad Air 820×1180 (vertical); 768px como ancho tablet clásico | Alcanza para 2 columnas en hero, tarjetas, cuenta y footer |
| Desktop | `@media (min-width: 64rem)` (1024px) | Safari y Edge 1280×800, Firefox 1440×900, Chrome 1920×1080 | El menú entra en una fila y se pasa a grillas de 3 y 4 columnas |
| Wide | `@media (min-width: 90rem)` (1440px) | Firefox 1440×900, Chrome 1920×1080 | Se amplía `--container-width` a 1320px y la imagen de Capitán Helado |
| Micro | `@media (max-width: 22.5rem)` (360px) | Celulares compactos de 320 a 360px | Ajustes finos de título, marca y rellenos |

Reglas auxiliares que no son breakpoints de ancho: `@media (max-width: 47.9375rem)` (solo mobile, para mostrar las tablas como cards), `@media (hover: none)` (pantallas táctiles) y `@media (orientation: landscape) and (max-height: 30rem)` (celulares en horizontal).

**Por qué cinco:** las grillas ahora tienen columnas explícitas por breakpoint (con `minmax(0, 1fr)`) en lugar de depender de `auto-fit`, porque en 820px `auto-fit` dejaba filas huérfanas. Wide y Micro se agregan solo donde las pruebas lo justifican (ancho del contenedor y celulares de 360px o menos).

**Fidelidad al mockup:** Figma MCP permitió identificar la página y el frame `Heladeria Vainell Segundo Mockup` (`1:3`). La comparación visual de este cierre se hizo con las cinco capturas adjuntas a la solicitud.

**Mobile-first:** `responsive.css` define el layout mobile como base (reglas sin media query) y usa `min-width` para ampliar a tablet, desktop y wide. Como `styles.css` ya declara valores de escritorio (padding de secciones, hero, footer), `responsive.css` los sobrescribe en mobile y los vuelve a declarar dentro de las queries `min-width`. Esa duplicación es un costo conocido. Una excepción: las tablas como cards usan `max-width`, porque en tablet y desktop vuelve la tabla normal y así no hay que restaurar todos los `display` de la tabla.

## 4. Enfoque de layout por sección

Flexbox para alineación en una dimensión (header, menús, filas de botones, interior de cards). Grid para estructuras de columnas.

| Sección | Mobile (base) | Tablet (≥768px) | Desktop (≥1024px) |
|---|---|---|---|
| Header + nav (Flex) | Dos filas y menú con scroll horizontal propio; `scroll-padding-top` en 9rem | Igual que mobile | Una fila; `scroll-padding-top` en 6rem |
| Hero `#inicio` (Grid) | 1 columna; CTA apilados y personaje debajo del contenido | 2 columnas | 2 columnas con mayor espacio |
| Beneficios (Flex) | Elementos se envuelven según el ancho disponible | Se envuelven según el ancho disponible | Se distribuyen en una franja |
| Por qué Vainell (Grid) | 1 columna | 2 columnas | 4 columnas |
| Catálogo (Grid + tabla) | Galería de 1 columna; pills; cada fila de tabla se presenta como card | Galería de 2 columnas; tablas normales | Galería de 4 columnas; tablas normales |
| Cómo pedir (Grid) | 1 columna | 2 columnas | 4 columnas |
| Pedido (Grid) | 1 columna | 2 columnas | 2 columnas |
| Mi cuenta (Grid) | 1 columna | 2 columnas | 2 columnas |
| Testimonios (Grid) | 1 columna | 2 columnas | 3 columnas |
| Footer (Grid) | 1 columna | 2 columnas | 3 columnas |

## 5. Reglas transversales

- **Variables y espaciados:** el padding vertical de las secciones y de los bloques grandes se redefine por breakpoint. En Wide solo cambia la variable `--container-width`.
- **Sin parches de overflow:** no se usa `overflow-x: hidden` en `html` ni en `body`. Se corrige la causa: columnas con `minmax(0, 1fr)`, `overflow-wrap: anywhere` en los links largos del footer e imágenes con `max-width: 100%` (ya en `styles.css`). El único scroll horizontal es el del menú del header, contenido dentro de su propio `<nav>`.
- **Zonas táctiles:** enlaces del menú, pills del catálogo y botón "Agregar" (en mobile, dentro de la card) de al menos 44px de alto. En tablet y desktop el botón "Agregar" de la tabla conserva su tamaño compacto (~37px): es una decisión a revisar con el QA.
- **Hover en pantallas táctiles:** la elevación de cards y botones se neutraliza con `@media (hover: none)`.
- **Campos de formulario:** se mantiene `font-size` de 1rem (16px) para evitar el zoom automático de iOS al enfocar un campo.
- **Celulares en horizontal:** con poca altura, el header deja de ser fijo.
- **Ajustes por cambios del HTML:** el responsive actual adapta la ilustración y las etiquetas de sabor del hero, la galería del catálogo, el menú y las grillas de contenido. Los componentes reutilizables se mantienen en `components.css`; los cambios de composición por ancho, en `responsive.css`.
- **Organización de `responsive.css`:** un bloque por breakpoint, con comentarios que documentan cada decisión y el motivo del breakpoint.

## 6. Criterios de aceptación

- [x] Breakpoints definidos y documentados (mobile, tablet, desktop) en `responsive.css` y en este spec.
- [x] Layout mobile-first implementado (base mobile + `min-width` para tablet, desktop y wide).
- [x] Secciones adaptadas por breakpoint; composición y legibilidad verificadas en la matriz de viewports de la sección 7.
- [x] No hay overflow horizontal de página en ningún viewport probado (el menú puede desplazarse dentro de su propio contenedor en mobile).
- [x] Layouts con Flexbox y CSS Grid.
- [x] Navegación interna verificada: los destinos quedan debajo del header sticky, también en mobile.
- [x] En mobile, las filas de catálogo se representan como cards; tablet y desktop conservan las tablas.
- [x] Enlaces del menú y pills de categorías con altura medida de al menos 44px.
- [x] Capitán Helado cargado y sin superposición con el título en todos los viewports probados; imágenes de la página cargadas.
- [x] `responsive.css` enlazado después de `components.css` en `index.html`.
- [x] Verificación en localhost por HTTP, registrada en la sección 10.
- [x] Revalidación actual de GitHub Pages.
- [x] Bugs reportados por el QA Tester resueltos antes del merge a `develop`.
- [x] PR hacia `develop` con `changelog.md` actualizado e issue vinculado.

## 7. Plan de pruebas

Con Live Preview en `http://localhost:3000` y con GitHub Pages, usando la emulación de dispositivos del navegador:

| Viewport | Dispositivo / uso |
|---|---|
| 320×640 | Piso de ancho |
| 360×800 | Android compacto |
| 390×844 | iPhone 14 Pro |
| 412×915 | Samsung Galaxy S23 |
| 768×1024 | Tablet clásica |
| 820×1180 | iPad Air |
| 1024×768 | Límite tablet/desktop |
| 1280×800 | Perfil de escritorio |
| 1440×900 | Perfil wide |
| 1920×1080 | Monitor wide |
| 844×390 | Móvil en horizontal (regla auxiliar de landscape) |

Los nombres de dispositivos del plan son referencias de dimensiones, no una afirmación de que se haya usado el dispositivo físico o su navegador nativo. En cada viewport se revisa:

1. Overflow de página, con esta línea en la consola del navegador (debe dar `false`):
   ```js
   document.documentElement.scrollWidth > document.documentElement.clientWidth
   ```
2. Que ninguna sección se vea cortada, superpuesta o con columnas demasiado angostas.
3. Que los enlaces internos del menú y las categorías lleven al destino sin que el header sticky lo tape.
4. Que los enlaces del menú y las categorías tengan una altura de al menos 44px; que los campos de los formularios sigan siendo utilizables.
5. Que en mobile las tablas se vean como cards y que en tablet y desktop entren sin scroll de página.
6. Que el menú del header scrollee solo dentro de su contenedor, sin mover la página.
7. Que las imágenes de la página carguen y que el título del hero no se superponga con la ilustración ni con su rótulo.

---

## PARTE B — Cierre con evidencia

## 8. Primer prompt exacto usado

**Herramienta realmente usada:** Copilot Agent con Figma MCP.

Archivos adjuntados como contexto: `index.html`, `css/styles.css`, `css/components.css` y `plan.md`.

```
Crea el archivo responsive.css para contribuir al diseño visual de index.html (ten en cuenta los comentarios). El diseño debe ser igual o parecido a este modelo de Figma: (dev mode link).
```


### Resultado obtenido

La implementación vigente usa `css/responsive.css` mobile-first: tablet desde 768px, desktop desde 1024px, wide desde 1440px y refinamiento micro hasta 360px. En mobile/tablet, la marca y el menú ocupan filas separadas; el menú se desplaza dentro de su propio `nav`. El hero pasa de una a dos columnas, las filas del catálogo se presentan como cards por debajo de 768px y las secciones se reorganizan con grillas explícitas. Las categorías siguen siendo anclas y las cinco tablas permanecen en la página; no se implementaron pestañas. Los resultados reproducibles de integración están en la sección 10.

## 8.1 Segundo prompt exacto usado

**Herramienta realmente usada:** Copilot Agent con Figma MCP.

```
Realiza las pruebas de integración para la página web. Verifica que cada diseño se vea visualmente bien con cada dispositivo que se usará mediante responsive.
```

### Resultado obtenido

```
El ajuste previo de `scroll-padding-top` a 9rem mantiene visibles los cinco destinos del catálogo bajo el header móvil. En la nueva verificación de cierre también se detectó y corrigió que los enlaces del menú medían 43,6px: ahora tienen un mínimo efectivo de 44px. La matriz completa y el alcance de la ejecución están documentados en la sección 10.
```

## 9. Comparación visual con el mockup y ajustes manuales

**Referencia visual:** [Mockup Heladería Vainell en Figma](https://www.figma.com/design/nYfkVF5ih7W14TxU7FpDPQ/Heladeria-Vainell-Segundo-Mockup?node-id=0-1&m=dev&t=xd9ZpLnqhpfok1b9-1) y las cinco capturas adjuntas (inicio, características, catálogo, cómo pedir e inicio de sesión). El nodo `0:1` corresponde a la página; los metadatos identifican el frame/código `1:3`. Las capturas son de escritorio; la adaptación móvil se evalúa con la matriz de viewports de la sección 10.

| Área | Mockup | Implementación al cierre | Comparación / decisión |
|---|---|---|---|
| Header y hero | Marca y navegación en una línea; título editorial a la izquierda e ilustración circular de Capitán Helado a la derecha. | Conserva la marca, el orden del menú y la composición de dos columnas en desktop; mobile/tablet separa marca y menú, y apila el hero en mobile. | Se conserva la jerarquía y se prioriza el contenido en pantallas estrechas. La ilustración, el título y el rótulo no se superponen en los viewports probados. |
| Tipografía y paleta | Títulos de display serif, fondos verde petróleo/crema y acentos coral y menta. | `styles.css` utiliza Fredoka/Nunito, una paleta menta/crema y superficies más claras. | Diferencia visual pendiente respecto del mockup; no se sobrescribieron los tokens del responsable de Frontend desde `responsive.css`. No se declara equivalencia tipográfica ni cromática. |
| Características | Franja coral y cuatro beneficios en una composición horizontal sobre fondo crema. | Mantiene la franja, los cuatro beneficios y su orden; las columnas se adaptan por breakpoint. | Se preserva el contenido y se adapta la cantidad de columnas al ancho disponible. El tratamiento de tarjetas e iconos no es idéntico. |
| Catálogo | Panel verde petróleo, categorías en una fila y productos en filas compactas con acciones. | Incluye galería, cinco enlaces de categoría y cinco tablas apiladas; cada fila pasa a card en mobile. | Se priorizan navegación por anclas, legibilidad y uso en mobile. El fondo, la galería previa y la presentación tabular no replican exactamente la composición del mockup; las categorías no son pestañas. |
| Cómo pedir | Cuatro pasos alineados horizontalmente sobre fondo menta. | Conserva los cuatro pasos y cambia de una a dos y cuatro columnas según breakpoint. | Mismo orden y contenido; distribución responsive deliberada. |
| Pedido y footer | Título y formulario lado a lado en una sección verde petróleo; footer crema. | El formulario está en una sección clara y el footer usa el fondo oscuro de la paleta del sitio. | Diferencia de composición y fondos. Queda fuera del alcance responsive porque requiere coordinar los estilos base/componentes con Frontend. |

### Ajustes manuales realizados

- Se ajustó la composición del hero para priorizar el título y evitar que el personaje o los elementos decorativos lo tapen. Capitán Helado se amplió en su columna; el rótulo opaco puede solaparse ligeramente con la ilustración y las etiquetas “Menta” y “Vainilla” se acercaron al personaje. El motivo es destacar la ilustración sin competir con el texto.
- “Nuestro secreto” se presenta como introducción y “✨ Un poco de magia ✨” como título inmediatamente posterior, para que la lectura tenga el orden solicitado y el conjunto encaje con la sección.
- Se organizó la galería y las cinco categorías del catálogo con enlaces a anclas; el modo actual conserva todas las tablas en vertical y no introduce el comportamiento de pestañas.
- Se ajustaron grillas y proporciones por breakpoint para que el hero, la galería, las secciones de contenido, las tablas y el footer se reorganicen sin desbordar en pantallas pequeñas.
- Se conservó el scroll horizontal del menú dentro de su `nav` en mobile/tablet, en lugar de permitir que ensanche toda la página; las filas del catálogo se presentan como cards por debajo de 768px.
- Tras la prueba de anclas se cambió `scroll-padding-top` mobile de 8rem a 9rem: el header medía 137px y el buffer de 128px dejaba el destino parcialmente bajo el header. El nuevo buffer de 144px deja 7px de margen en el viewport más estrecho probado. En desktop se mantiene el buffer de 6rem.
- En la prueba de integración se midió una altura de 43,6px para los enlaces principales del header. Se agregó `min-height: 2.75rem` en `responsive.css` para cumplir el mínimo táctil de 44px en todos los breakpoints.
- `responsive.css` está enlazado en `index.html` después de `components.css`.
- No se modificaron los tokens de tipografía, paleta ni los estilos base de catálogo/pedido/footer: las diferencias visuales registradas arriba requieren coordinación con el responsable de Frontend y no se ocultaron como si fueran ajustes responsive.

## 10. Pruebas de integración — cierre

**Entorno y método:** Chromium integrado, página servida localmente por HTTP. Se usó un servidor estático temporal desde la raíz del repositorio; no se agregaron dependencias ni archivos de prueba. Se emularon los viewports de la matriz y se midieron `scrollWidth`, disposición de las tablas, scroll del menú, alturas táctiles y separación entre el título del hero y la ilustración.

| Viewport | Overflow de página | Catálogo | Menú | Hero sin superposición | Resultado |
|---|---|---|---|---|---|
| 320×640 | No | Cards | Scroll interno | Sí | PASS |
| 360×800 | No | Cards | Scroll interno | Sí | PASS |
| 390×844 | No | Cards | Scroll interno | Sí | PASS |
| 412×915 | No | Cards | Scroll interno | Sí | PASS |
| 768×1024 | No | Tabla | Sin scroll | Sí | PASS |
| 820×1180 | No | Tabla | Sin scroll | Sí | PASS |
| 1024×768 | No | Tabla | Sin scroll | Sí | PASS |
| 1280×800 | No | Tabla | Sin scroll | Sí | PASS |
| 1440×900 | No | Tabla | Sin scroll | Sí | PASS |
| 1920×1080 | No | Tabla | Sin scroll | Sí | PASS |
| 844×390 (landscape) | No | Tabla | Sin scroll | Sí | PASS |

**Comprobaciones complementarias**

- Los 11 viewports quedaron sin overflow horizontal (`scrollWidth === clientWidth`) y sin superposición del título con la columna visual del hero.
- En los 11 viewports, los enlaces del menú y las categorías midieron al menos 44px de alto. El menú tuvo scroll propio en 320–412px; desde 768px no necesitó scroll horizontal.
- En 320–412px, las filas usaron `grid` y la tabla se mostró como cards; desde 768px se restauraron `table` y `table-row`.
- En 844×390, el header pasó a `position: static`, como define la regla de landscape.
- Se cargaron las 6/6 imágenes tras permitir la carga de las imágenes lazy; se encontraron las 5 tablas y las tres hojas CSS en el orden esperado (`styles.css`, `components.css`, `responsive.css`).
- Se activaron los cinco enlaces de categoría en 390×844: cada destino quedó a 144px del borde superior, por debajo del header de 137px.

**Alcance:** esta ejecución verifica la página local en Chromium/Firefox/Safari/Edge y GitHub Pages.
