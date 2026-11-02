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

**Fidelidad al mockup:** el archivo de Figma no pudo leerse; por eso no se afirma fidelidad pixel-perfect. La implementación conserva la paleta, tipografías y componentes definidos en `styles.css` y `components.css`.

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
- [x] Pruebas en GitHub Pages y en un servidor localhost.
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

**Herramienta realmente usada:** Claude (chat de claude.ai) fue utilizada para realizar el archivo `responsive.css` por primera vez, este fue modificado conforme se empezaron a hacer más pruebas con más cambios con Copilot Agent.

Archivos adjuntados como contexto: `index.html`, `css/styles.css`, `css/components.css` y `plan.md`.


```
Crea el archivo responsive.css para contribuir al diseño visual de index.html (ten en cuenta los comentarios). El diseño debe ser igual o parecido a este modelo de Figma: (dev mode link).
```


### Resultado obtenido

```
La implementación vigente usa `css/responsive.css` mobile-first: tablet desde 768px, desktop desde 1024px, wide desde 1440px y refinamiento micro hasta 360px. La composición revisada incluye:

- Header: marca y menú en filas separadas en mobile/tablet; el menú conserva su scroll horizontal dentro del `nav`. Desde desktop se dispone en una fila.
- Hero: una columna en mobile y dos desde tablet; el título permanece separado de la ilustración de Capitán Helado y de su rótulo opaco. La ilustración y las etiquetas de sabor se ajustan por breakpoint.
- Catálogo: galería de productos antes de las cinco categorías. Las categorías son enlaces de ancla y las cinco tablas siguen apiladas en la página (no son pestañas). En mobile cada fila se presenta como card; desde 768px se recupera la tabla.
- Resto de secciones: grillas explícitas que pasan de una columna a dos y, en las secciones correspondientes, a tres o cuatro columnas.
- `styles.css` y `components.css` conservan la presentación base y los componentes; `responsive.css` controla los cambios de layout por viewport. No se oculta el overflow de `html` o `body` como parche.

**Pruebas de integración:** página abierta desde `file:///.../index.html` en el navegador Chromium integrado, GitHub Pages y localhost. Se revisaron 11 viewports: 320×640, 360×800, 390×844, 412×915, 768×1024, 820×1180, 1024×768, 1280×800, 1440×900, 1920×1080 y 844×390 (landscape).

- En los 10 tamaños portrait/desktop: `document.documentElement.scrollWidth > clientWidth` fue `false`; el título no se superpuso a Capitán Helado ni a su rótulo; se cargaron las 6/6 imágenes; se encontraron las 5 tablas.
- Entre 320px y 412px, las filas se muestran como cards y el menú scrollea dentro de su contenedor. Desde 768px las tablas vuelven a su presentación tabular y no se observó scroll interno del menú.
- En los viewports medidos, los enlaces del menú y las pills de categorías tuvieron 44px de alto.
- Al comprobar los anchors se detectó que el buffer original de 8rem podía quedar 9px por debajo del header móvil (137px). Se aumentó a 9rem (144px); después del ajuste, los destinos quedan por debajo del header. En landscape bajo el header deja de ser sticky.
- El formulario conserva validación nativa: los campos requeridos vacíos no pasan `checkValidity()`, como se espera antes de completar el formulario. La prueba no envía pedidos ni verifica servicios de backend.

La revisión se hizo en Chromium con emulación de viewport y métricas de layout.
```

## 8.1 Segundo prompt exacto usado

**Herramienta realmente usada:** Copilot Agent con MCP.

```Realiza las pruebas de integración para la página web. Verifica que cada diseño se vea visualmente bien con cada dispositivo que se usará mediante responsive.````

### Resultado obtenido

```
Actualicé responsive.css: las pruebas mostraron que el espacio para anclas en móvil era menor que la altura del header. Lo aumenté a 9rem y confirmé que las categorías quedan visibles al navegar.

Registré en spec-responsive.md los cambios, sus motivos y los resultados de 11 tamaños de viewport. No se detectó desbordamiento horizontal; el hero mantuvo el título separado del personaje, y se verificaron las tablas, las imágenes y los destinos de navegación.

git diff --check pasó. La prueba se hizo en Chromium con el archivo local.
```

## 9. Ajustes manuales realizados

- Se ajustó la composición del hero para priorizar el título y evitar que el personaje o los elementos decorativos lo tapen. Capitán Helado se amplió en su columna; el rótulo opaco puede solaparse ligeramente con la ilustración y las etiquetas “Menta” y “Vainilla” se acercaron al personaje. El motivo es destacar la ilustración sin competir con el texto.
- “Nuestro secreto” se presenta como introducción y “✨ Un poco de magia ✨” como título inmediatamente posterior, para que la lectura tenga el orden solicitado y el conjunto encaje con la sección.
- Se organizó la galería y las cinco categorías del catálogo con enlaces a anclas; el modo actual conserva todas las tablas en vertical y no introduce el comportamiento de pestañas.
- Se ajustaron grillas y proporciones por breakpoint para que el hero, la galería, las secciones de contenido, las tablas y el footer se reorganicen sin desbordar en pantallas pequeñas.
- Se conservó el scroll horizontal del menú dentro de su `nav` en mobile/tablet, en lugar de permitir que ensanche toda la página; las filas del catálogo se presentan como cards por debajo de 768px.
- Tras la prueba de anclas se cambió `scroll-padding-top` mobile de 8rem a 9rem: el header medía 137px y el buffer de 128px dejaba el destino parcialmente bajo el header. El nuevo buffer de 144px deja 7px de margen en el viewport más estrecho probado. En desktop se mantiene el buffer de 6rem.
- `responsive.css` está enlazado en `index.html` después de `components.css`.
