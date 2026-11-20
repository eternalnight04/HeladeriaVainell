# spec-devops.md — Coordinador / DevOps

**Proyecto:** Vainell
**Entrega:** Actividad Obligatoria Nº2
**Rol:** Coordinador / DevOps
**Rama:** `feature/coord-devops-update-figma-and-readme`

---

# PARTE 1 — PLANIFICACIÓN PREVIA (commitear primero)

## 1. Contexto

**Vainell** es un simulador web de pedidos de helados (delivery o retiro en local, más "Mi cuenta Vainell" simulada con login/registro). La Actividad N°1 construyó la estructura HTML5. Esta Actividad N°2 suma CSS, diseño responsive y QA asistido por MCP (Figma MCP, Playwright MCP, GitHub MCP).

El Coordinador/DevOps es responsable de que el flujo de ramas, PRs, mockup, documentación y release se cumpla de punta a punta, y de que todo quede enlazado en `changelog.md`.

## 2. Qué se va a hacer y por qué

| # | Tarea | Por qué es relevante |
|---|---|---|
| 1 | Resolver los Request Changes de la Actividad N°1 con ramas `fix/` contra `release/actividad-obligatoria-1` | Dejar una base corregida y aprobada (LGTM) antes de construir sobre ella |
| 2 | Backport de `release/actividad-obligatoria-1` hacia `develop` | Establecer la base de código de la Actividad N°2 |
| 3 | Actualizar el mockup de Figma (paleta, tipografías, espaciados, estados) y exportar `diseño-con-estilos.png` | Es la fuente de verdad que usa el Frontend con Figma MCP |
| 4 | Actualizar `plan.md` y `README.md` con los requerimientos de esta entrega | Mantener alineado el proyecto general y la trazabilidad |
| 5 | Coordinar PRs y realizar mínimo 4 code reviews asistidos con Copilot Agent | Validar coherencia del CSS con el mockup y el `plan.md` |
| 6 | Mantener `changelog.md` e índices enlazados (`testing-doc.md`) | Sin PR enlazada en el changelog no hay justificación de trabajo |
| 7 | Crear `release/actividad-obligatoria-2`, habilitar GitHub Pages y publicar la PR release | Entregable evaluable por el docente |

## 3. Decisiones de planificación

- **Orden de trabajo:** (1) commitear este spec → (2) fixes y backport → (3) Figma + `plan.md` + README (antes de que Frontend empiece) → (4) code reviews durante las PRs → (5) release tras el Momento 2 del QA.
- **Herramientas:** Git/GitHub (branch model y PRs), Figma, GitHub Copilot Agent Mode (code reviews), Slack (notificaciones al docente), GitHub Pages.
- **Dependencias con otros roles:**
  - Frontend/CSS necesita el enlace Figma y la imagen del mockup.
  - Responsive necesita el mockup y los CSS del Frontend.
  - QA necesita que todas las `feature/` estén mergeadas en `develop` para el Momento 2.
- **Ramas protegidas:** `master` (aprobación del profesor) y `develop` (aprobación de otro integrante / Coordinador).

## 4. Criterios de aceptación (checklist)

### Resolución de Request Changes — Actividad N°1
- [x] Por cada Request Change existe una rama `fix/...` creada desde `release/actividad-obligatoria-1`
- [x] Cada fix tiene su PR contra `release/actividad-obligatoria-1`
- [x] Cada fix está registrado en `changelog.md` bajo `[Fixed]` con link a la PR
- [x] Docente notificado con ✅ en el hilo de Slack al resolver todos los comentarios
- [x] Backport `backport/release-actividad-obligatoria-1` → `develop` realizado post-merge a `master`

### spec-devops.md
- [x] Existe en `docs/03-specs/actividad-obligatoria-2/`
- [x] Commiteado antes que cualquier otro cambio de la entrega
- [x] Completado al cierre con decisiones del mockup, cambios y evidencia disponible

### Mockup Figma y plan.md
- [x] Paleta y dirección tipográfica/visual documentadas a partir de las capturas exportadas
- [x] Enlace al Figma actualizado en `README.md`
- [x] Imagen exportada en `docs/01-mockup/actividad-obligatoria-2/diseño-con-estilos.png`
- [x] `plan.md` actualizado con los requerimientos de esta entrega

### Coordinación de PRs y Code Reviews
- [x] Todas las PRs tienen al menos 1 revisión aprobada antes del merge
- [ ] Mínimo 4 code reviews asistidos con Copilot Agent
- [x] Request Changes cargados en las líneas del diff correspondientes
- [x] `changelog.md` con la contribución de cada integrante en cada PR
- [ ] Enlace directo entre `README.md` y `testing-doc.md` (no está presente en el README actual)

### Release y publicación
- [x] `release/actividad-obligatoria-2` creada desde `develop` tras los merges y la validación del QA
- [x] GitHub Pages habilitado y sitio accesible públicamente
- [x] PR release → `master` con template de release, título `[GRUPO N°4][Actividad Obligatoria N°2] Entrega de la actividad`
- [x] PR publicada en Slack (`#2026-1er-cuat-pw1`) mencionando al docente y link subido al campus

### Feature branch y changelog (propios)
- [x] Trabajo en `feature/coord-devops-update-figma-and-readme`
- [x] PR propia revisada y aprobada por otro integrante
- [x] `changelog.md` con entrada correcta (número de PR, link, autor, resumen)
- [x] Issue creado y vinculado a la PR, cerrado post-merge

## 5. PRs previstas

| Rama origen → destino | Propósito | Estado |
|---|---|---|
| `fix/` → `release/actividad-obligatoria-1` | Un fix por Request Change | Realizado |
| `backport/release-actividad-obligatoria-1` → `develop` | Base de la Actividad N°2 | Realizado |
| `feature/coord-devops-update-figma-and-readme` → `develop` | Mockup, README, plan.md | Realizado |

---

# PARTE 2 — EVIDENCIA AL CIERRE

## 6. Decisiones del mockup en Figma

- **Primer mockup — Figma Make:** [Ice Cream Shop](https://www.figma.com/make/8UBb5SIznSz81a6y57nQ7v/Ice-Cream-Shop?t=MiOriddmlnQAfXnL-20&fullscreen=1). Sus capturas están en `docs/01-mockup/actividad-obligatoria-1/`.
- **Segundo mockup — Figma:** [Heladeria Vainell Segundo Mockup](https://www.figma.com/design/nYfkVF5ih7W14TxU7FpDPQ/Heladeria-Vainell-Segundo-Mockup?node-id=0-1&p=f&t=xd9ZpLnqhpfok1b9-0).
- **Evolución entre propuestas:** el primer diseño usaba una identidad más luminosa y de tarjetas: crema y menta, acento verde/turquesa, hero partido en dos fondos, personaje tipo superhéroe y catálogo en tarjetas. En el segundo se renovaron el logo y la ilustración de Capitán Helado y se adoptó una dirección más editorial: títulos serif grandes, navegación más discreta, franja coral de beneficios, catálogo en filas sobre fondo petróleo y formulario de pedido dividido entre texto y panel claro. El cambio buscó una identidad más distintiva y con mayor contraste entre secciones; quedó incorporado en el conjunto de cinco capturas de la Actividad 2.

| Rol cromático observado en los mockups | Primer mockup | Segundo mockup |
|---|---|---|
| Superficie clara | Crema `#FFF8F2` | Crema `#F8F2E7` |
| Fondo menta | `#E6FAF5` | `#E0F3EB` |
| Acento de marca | Verde/turquesa `#38D9A9`, `#1A8A6E` | Coral `#EC7668`; menta suave `#A9DFCB` |
| Texto/fondo oscuro | Verde petróleo `#1A3A35` | Petróleo `#16363C` / `#17383D` |
| Acento cálido | Caramelo `#C8874A` | Dorado `#F1BE73` y crema cálida `#F8E8BC` |

Los HEX se muestrearon de las áreas planas de los PNG exportados y describen los mockups visibles. El segundo set también incluye detalles pastel en los iconos (por ejemplo, lila y coral claro).

**Tipografía y jerarquía visual:** el segundo mockup presenta títulos de display serif de alto contraste, cuerpo sans serif y etiquetas pequeñas en mayúsculas con tracking. El CSS que quedó implementado usa Fredoka para encabezados y Nunito para cuerpo; el cuerpo parte de `1rem`, `h1` usa `clamp(2.6rem, 7vw, 4.6rem)`, `h2` `clamp(1.9rem, 4vw, 2.6rem)` y `h3` `1.35rem`. Esa diferencia queda registrada: la apariencia tipográfica del mockup no se trasladó literalmente al CSS.

**Espaciado y componentes implementados en CSS:** escala `0.25rem`, `0.5rem`, `0.75rem`, `1rem`, `1.5rem`, `2rem`, `3rem` y `4.5rem`; radios `0.5rem`, `1rem`, `1.5rem`, `2rem` y pill; botones, navegación, cards, formularios y tablas.

**Estados:** `components.css` implementa `hover`, `focus-visible`, `active` y `disabled` para los controles pertinentes.

- **Imagen principal exportada:** `docs/01-mockup/actividad-obligatoria-2/diseño-con-estilos.png` (hero). Las vistas de características, catálogo, cómo pedir e inicio de sesión están en los PNG `02` a `05` de esa carpeta.
- **Nota sobre fidelidad:** la paleta final del CSS tampoco coincide exactamente con los colores muestreados del segundo mockup. Por ejemplo, `styles.css` define `--color-primary: #1f7a70`, `--color-primary-dark: #14484a`, `--color-primary-deep: #0f2f35`, `--color-mint: #aee9df` y `--color-cream: #fffaf0`. Se conserva aquí la distinción entre la dirección visual de Figma y los tokens realmente implementados.

## 7. Code reviews asistidos con Copilot Agent

Las revisiones y aprobaciones siguientes se verificaron en GitHub. Las anotaciones fueron publicadas por el revisor `@britezacostaalexis-pixel`.

| PR | Revisión y observaciones registradas | Cierre |
|---|---|---|
| [#48 — estilos CSS](https://github.com/eternalnight04/HeladeriaVainell/pull/48) | Se señaló el bajo contraste del acento menta en texto y botones, y el desbordamiento de la navegación en anchos pequeños. | Los dos hilos figuran resueltos; PR aprobada el 21/10/2026. |
| [#50 — responsive](https://github.com/eternalnight04/HeladeriaVainell/pull/50) | Se señaló el contraste insuficiente del texto de botones y del indicador `:focus-visible`. | Los dos hilos figuran resueltos; PR aprobada el 21/10/2026. |
| [#51 — mockup, recursos y documentación](https://github.com/eternalnight04/HeladeriaVainell/pull/51) | Se observó que el logo y la mascota eran PNG grandes sin dimensiones/restricciones de presentación y que `index.html` aún no enlazaba estilos. | Hilo resuelto; PR aprobada y mergeada a `develop` el 20/10/2026. |

El seguimiento de QA de [#26](https://github.com/eternalnight04/HeladeriaVainell/pull/26) también tiene una aprobación registrada, pero es una revisión de documentación y no se cuenta como code review de CSS. En GitHub constan tres PRs de implementación con comentarios de revisión y aprobación.

## 8. Actualización de plan.md, README y changelog

- **plan.md:** se actualizó la tabla de tecnologías de la Actividad 2 con CSS base/componentes, responsive, Figma MCP, testing y trazabilidad a specs, PRs y changelog. La tabla identifica las capturas en `docs/01-mockup/actividad-obligatoria-2/`. Se mantuvo la definición del simulador y sus límites funcionales.
- **README.md:** describe el objetivo del simulador, tecnologías y funcionalidades previstas; incluye enlaces a los mockups 1 y 2, al plan, prompts, changelog y specs. El vínculo local al PNG principal del segundo mockup apunta al archivo existente `diseño-con-estilos.png`; el vínculo a Figma usa Figma Make. En el README actual no hay enlace directo a `docs/04-testing/testing-doc.md`; queda pendiente completar ese vínculo.
- **changelog.md:** la sección `[Release Actividad Obligatoria N°2]` registra las PRs #26 (QA), #48 (Frontend/CSS), #50 (Responsive) y #51 (actualización de mockup y documentación), además de las PRs de corrección posteriores. La entrada de #51 aclara que la tarea se completó entre integrantes por la ausencia de quien tenía la asignación original. En el estado actual del archivo, `[Unreleased]` no tiene entradas.
- **Obstáculos y límites documentales:** se mantuvieron dos enlaces de Figma distintos para el segundo mockup (Make y Design/Dev Mode); el segundo permite ubicar la página y el frame.
