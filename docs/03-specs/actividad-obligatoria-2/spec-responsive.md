# spec-responsive.md — Especialista en Responsive Design

**Proyecto:** Vainell
**Entrega:** Actividad Obligatoria N°2
**Rol:** Especialista en Responsive Design
**Rama:** `feature/responsive-design-add-responsive-styles` → `develop`
**Ruta:** `docs/03-specs/actividad-obligatoria-2/spec-responsive.md`

> **Orden de commits:** esta spec (Parte A, secciones 1 a 7) debe commitearse **antes** que `css/responsive.css`. La Parte B (cierre con evidencia) se completa al terminar.

---

## PARTE A — Planificación previa

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

**Fidelidad al mockup:** el archivo de Figma no pudo leerse, así que la fidelidad en mobile y tablet se toma de la paleta, tipografías y componentes ya definidos en `styles.css` y `components.css`, y se contrasta con el mockup en la revisión manual (ver sección 10).

**Mobile-first:** `responsive.css` define el layout mobile como base (reglas sin media query) y usa `min-width` para ampliar a tablet, desktop y wide. Como `styles.css` ya declara valores de escritorio (padding de secciones, hero, footer), `responsive.css` los sobrescribe en mobile y los vuelve a declarar dentro de las queries `min-width`. Esa duplicación es un costo conocido. Una excepción: las tablas como cards usan `max-width`, porque en tablet y desktop vuelve la tabla normal y así no hay que restaurar todos los `display` de la tabla.

## 4. Enfoque de layout por sección

Flexbox para alineación en una dimensión (header, menús, filas de botones, interior de cards). Grid para estructuras de columnas.

| Sección | Mobile (base) | Tablet (≥768px) | Desktop (≥1024px) |
|---|---|---|---|
| Header + nav (Flex) | Dos filas: marca arriba y menú debajo, en una tira con scroll horizontal propio; `scroll-padding-top` en 8rem | Igual que mobile | Una sola fila, `scroll-padding-top` en 6rem |
| Hero `#inicio` (Grid) | 1 columna; `.hero-imagen` con alto máximo 15rem; CTA apilados a ancho completo; foto de helados en 4:3 | 2 columnas (`1.1fr 0.9fr`); Capitán Helado hasta 20rem; foto en 16:9 | 2 columnas (`1.05fr 0.95fr`) con más aire; Capitán Helado hasta 28rem; foto en 21:9 |
| Características (Grid) | 2 × 2 | 4 columnas | 4 columnas |
| Por qué Vainell (Grid) | 1 columna | 2 columnas | 4 columnas |
| Catálogo (Flex + Grid) | Pills de categorías de 44px de alto; cada fila de la tabla es una card (Grid dentro del `<tr>`: nombre y precio, descripción, botón a ancho completo) | Tabla normal | Tabla normal a ancho completo |
| Cómo pedir (Grid) | 1 columna | 2 columnas | 4 columnas |
| Pedido (Grid) | 1 columna | 2 columnas (`fieldset`, dirección, comentarios y botón ocupan el ancho completo) | Igual que tablet |
| Mi cuenta (Grid) | 1 columna | 2 columnas | 2 columnas (máx. 60rem) |
| Testimonios (Grid) | 1 columna | 2 columnas; la tercera card queda centrada debajo, a media anchura | 3 columnas |
| Footer (Grid) | 1 columna | 2 columnas; el bloque de marca ocupa la primera fila completa | 3 columnas (`1.4fr 1fr 1.2fr`) |

## 5. Reglas transversales

- **Variables y espaciados:** el padding vertical de las secciones y de los bloques grandes se redefine por breakpoint. En Wide solo cambia la variable `--container-width`.
- **Sin parches de overflow:** no se usa `overflow-x: hidden` en `html` ni en `body`. Se corrige la causa: columnas con `minmax(0, 1fr)`, `overflow-wrap: anywhere` en los links largos del footer e imágenes con `max-width: 100%` (ya en `styles.css`). El único scroll horizontal es el del menú del header, contenido dentro de su propio `<nav>`.
- **Zonas táctiles:** enlaces del menú, pills del catálogo y botón "Agregar" (en mobile, dentro de la card) de al menos 44px de alto. En tablet y desktop el botón "Agregar" de la tabla conserva su tamaño compacto (~37px): es una decisión a revisar con el QA.
- **Hover en pantallas táctiles:** la elevación de cards y botones se neutraliza con `@media (hover: none)`.
- **Campos de formulario:** se mantiene `font-size` de 1rem (16px) para evitar el zoom automático de iOS al enfocar un campo.
- **Celulares en horizontal:** con poca altura, el header deja de ser fijo.
- **Ajustes por cambios del HTML:** `responsive.css` incluye un bloque inicial (sección 0) que estiliza elementos nuevos que los otros CSS no cubren: el logo "V", `.hero-imagen`, las métricas del hero como chips y el título visible del footer. Si el equipo prefiere, ese bloque se puede mover a `components.css`.
- **Organización de `responsive.css`:** un bloque por breakpoint, con comentarios que documentan cada decisión y el motivo del breakpoint.

## 6. Criterios de aceptación

- [ ] Breakpoints definidos y documentados (mobile, tablet, desktop) en `responsive.css` y en este spec.
- [ ] Layout mobile-first implementado (base mobile + `min-width` para tablet, desktop y wide).
- [ ] Todas las secciones del mockup (header, inicio, características, por qué Vainell, catálogo, cómo pedir, pedido, mi cuenta, testimonios, footer) se adaptan correctamente en los tres breakpoints.
- [ ] No hay overflow horizontal de página en ningún dispositivo de la sección 7 (solo el menú del header scrollea, dentro de su contenedor).
- [ ] Layouts con Flexbox y/o CSS Grid coherentes con el mockup.
- [ ] La navegación es usable en mobile y tablet, y el header fijo no tapa el destino de los enlaces ancla.
- [ ] En mobile, cada fila del catálogo se ve como card legible, con nombre, descripción, precio y botón "Agregar".
- [ ] Zonas táctiles de al menos 44px en mobile (en tablet, menú y pills).
- [ ] Capitán Helado y las fotos del hero se ven completos y proporcionados en los tres breakpoints.
- [ ] `responsive.css` enlazado en `index.html` después de `components.css`.
- [ ] Pruebas de integración realizadas con el Desarrollador Frontend en GitHub Pages y localhost.
- [ ] Bugs reportados por el QA Tester resueltos antes del merge a `develop`.
- [ ] PR hacia `develop` con `changelog.md` actualizado e issue vinculado.

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
| 1280×800 | Safari / Edge |
| 1440×900 | Firefox |
| 1920×1080 | Chrome |

En cada viewport se revisa:

1. Overflow de página, con esta línea en la consola del navegador (debe dar `false`):
   ```js
   document.documentElement.scrollWidth > document.documentElement.clientWidth
   ```
2. Que ninguna sección se vea cortada, superpuesta o con columnas demasiado angostas.
3. Que los enlaces del menú lleven a la sección sin quedar tapada por el header fijo.
4. Que el botón "Agregar" y los campos se puedan tocar con comodidad.
5. Que en mobile las tablas se vean como cards y que en tablet y desktop entren sin scroll de página.
6. Que el menú del header scrollee solo dentro de su contenedor, sin mover la página.
7. Que las imágenes del hero (cono, Capitán Helado y foto de los helados) no se deformen ni se recorten de forma que se pierda lo importante.

---

## PARTE B — Cierre con evidencia

> Completar al terminar el trabajo con lo que **efectivamente** se hizo. Esta sección es evidencia: no reconstruir prompts de memoria ni describir pasos que no se hicieron.

## 8. Prompt exacto usado

**Herramienta realmente usada:** Claude (chat de claude.ai), no Copilot Agent. El enlace de Figma Make bloquea el acceso automatizado, por lo que el mockup **no pudo leerse** y la fidelidad se tomó de los CSS existentes.

Archivos adjuntados como contexto: `index.html`, `css/styles.css`, `css/components.css`, `plan.md` y la consigna de la Actividad Obligatoria N°2 (PDF).

```
Crea el archivo responsive.css para contribuir al diseño visual de index.html (ten en cuenta los comentarios). El diseño debe ser igual o parecido a este modelo de Figma: https://www.figma.com/make/Si4hHXYePCegrXfCQ5TNf3/Heladeria-Vainell-Segundo-Mockup?fullscreen=1&t=Xpd4GgpcrVNqz7z7-1&code-node-id=0-6
```

## 9. Resultado obtenido

```
Se generó css/responsive.css con enfoque mobile-first y estos breakpoints: tablet (min-width 48rem), desktop (min-width 64rem), wide (min-width 90rem) y micro (max-width 22.5rem).

- Header: en mobile y tablet, marca arriba y menú en una tira con scroll horizontal dentro del <nav>; en desktop, una sola fila.
- Hero: 1 columna en mobile y 2 desde tablet; la imagen de Capitán Helado crece con el ancho hasta 32rem.
- Catálogo: en mobile cada fila de la tabla es una card; desde tablet vuelve la tabla.
- Resto de secciones: 1 columna en mobile, 2 en tablet y 3 o 4 en desktop, con columnas explícitas (minmax(0, 1fr)).
- Se estilizaron elementos nuevos del HTML que los otros CSS no cubrían: logo "V", .hero-imagen, métricas del hero como chips y título visible del footer.
- No se modificaron styles.css ni components.css. No se usó overflow-x: hidden en html ni en body.

Controles realizados: se verificó que las llaves y los comentarios estén balanceados. No se abrió la página en un navegador ni se probó en los viewports del plan de pruebas.
```

## 10. Ajustes manuales realizados

- `responsive.css` está enlazado en `index.html` después de `components.css`.
- `<completar: comparación de los breakpoints y layouts contra el mockup de Figma, y qué se corrigió y por qué>`
- `<completar: ajustes hechos al probar en los viewports de la sección 7 (por ejemplo, altura de .hero-imagen, recorte de la foto del cono, ancho del menú)>`
- `<completar: decisión final sobre el tamaño del botón "Agregar" en tablet y desktop>`

### Pruebas de integración con el Desarrollador Frontend

| Fecha | Entorno (localhost / GitHub Pages) | Viewports revisados | Resultado |
|---|---|---|---|
| `<completar>` | `<completar>` | `<completar>` | `<completar>` |

Issues de QA recibidos y resueltos: `<completar con links a los issues de GitHub>`
