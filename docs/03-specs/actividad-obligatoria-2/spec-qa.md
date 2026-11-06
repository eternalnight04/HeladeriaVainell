# Spec QA — Actividad Obligatoria N.º 2

## 1. Rol y responsabilidad

- **Rol:** Documentador / QA Tester.
- **Responsable:** Lautaro Chavez.
- **Rama de trabajo original:** `feature/doc-qa-tester-add-test-cases`.
- **Rama de ejecución de Momento 2:** `qa/momento-2`.
- **Proyecto:** Heladería Vainell.

## 2. Objetivo

Verificar la calidad del sitio web de Heladería Vainell mediante pruebas de compatibilidad, diseño responsive, rendimiento, accesibilidad y estructura HTML semántica.

El proceso se dividió en dos momentos:

- **Momento 1 — Pre-merge:** pruebas históricas realizadas antes de integrar los cambios de desarrollo.
- **Momento 2 — Post-merge:** nuevas verificaciones realizadas sobre la versión integrada disponible localmente.

Las pruebas de Momento 2 se ejecutaron en Chromium mediante Playwright MCP. La URL observada durante esa ejecución fue:

`http://127.0.0.1:3000/index.html?vscode-livepreview=true`

Esta dirección corresponde al entorno local de Live Preview y no demuestra por sí sola el comportamiento en producción ni en otros navegadores.

## 3. Plan y alcance de los test cases

### TC-01 — Compatibilidad en navegadores de escritorio

Verificar la carga, visualización y comportamiento general del sitio en navegadores de escritorio.

**Alcance comprobado en Momento 2:** inspección mediante Chromium, carga de la página y captura general.

**Pendiente:** ejecución equivalente en Firefox, Safari y Edge. No se declara compatibilidad completa entre navegadores.

### TC-02 — Diseño responsive

Comprobar la visualización, el desbordamiento horizontal y la accesibilidad de los controles en tamaños de pantalla representativos de iPhone, Samsung Galaxy e iPad.

**Criterios:** contenido visible, controles disponibles para la interacción y ausencia de desbordamiento horizontal en los viewports evaluados.

### TC-03 — Rendimiento y carga

Registrar métricas de carga disponibles mediante la Performance API del navegador y revisar los recursos cargados.

**Limitación:** no se definió previamente un umbral numérico de aceptación. Por ello, las métricas registradas no bastan para asignar un PASS o FAIL formal de rendimiento.

### TC-04 — Accesibilidad

Ejecutar una auditoría automatizada con axe-core mediante Playwright MCP y registrar las infracciones, comprobaciones incompletas y verificaciones manuales pendientes.

**Limitación:** una auditoría automatizada sin infracciones confirmadas no demuestra por sí sola conformidad completa con WCAG 2.1 AA.

### TC-05 — Estructura HTML semántica y validación W3C

Inspeccionar encabezados, imágenes, controles, identificadores y elementos semánticos, y validar el documento con el W3C Nu HTML Checker.

**Alcance comprobado en Momento 2:** inspección del DOM y del árbol de accesibilidad, y validación formal con W3C Nu HTML Checker ejecutada el 01/11/2026 sobre `index.html`.

**Limitación:** la validación W3C cubre solo `index.html`; los archivos CSS no se validaron.

## 4. Herramientas y evidencias

- **Playwright MCP:** navegación, inspección del DOM, comprobación de controles, emulación de viewports y capturas.
- **Chromium:** navegador utilizado en las verificaciones de Momento 2.
- **axe-core 4.7.2:** auditoría automatizada de accesibilidad.
- **Performance API:** registro de métricas de carga.
- **GitHub:** registro de issues. Durante el Momento 2 se crearon los issues [#57](https://github.com/eternalnight04/HeladeriaVainell/issues/57) y [#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60).
- **W3C Nu HTML Checker:** ejecutado el 01/11/2026 sobre `index.html` (3 errores y 3 advertencias; ver `test-case-5.md`, sección 4.5, e issue [#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60)).

Las evidencias disponibles en `docs/04-testing/` son:

- `evidencia-test-case-1.png`
- `evidencia-test-case-1-momento-2.png`
- `evidencia-test-case-2-iphone.png`
- `evidencia-test-case-2-samsung.png`
- `evidencia-test-case-2-ipad.png`
- `evidencia-test-case-3-momento-2.png`
- `evidencia-test-case-4-momento-2.png`
- `evidencia-test-case-5-momento-2.png`
- `evidencia-test-case-5-w3c-momento-2.png`

Los resultados detallados deben consultarse en los cinco archivos `test-case-1.md` a `test-case-5.md`.

## 5. Prompts y trazabilidad

Se transcriben los prompts utilizados en Copilot Agent Mode con Playwright MCP.

- **TC-01, TC-02, TC-03, TC-04 y TC-05:** texto literal registrado en `test-case-1.md``test-case-2.md``test-case-3.md``test-case-4.md` y `test-case-5.md`.


La ejecución de cada caso está respaldada por la evidencia de `docs/04-testing/` (capturas, registros de consola y métricas) descrita en la sección 4.

### 5.1 TC-01 — Compatibilidad de escritorio

```text
Usa Playwright MCP para realizar la auditoría del Test Case 1: Compatibilidad de escritorio en la aplicación local de Heladería Vainell.

URL:
http://127.0.0.1:3000/index.html?vscode-livepreview=true

Instrucciones:
1. Abre la página en Chromium.
2. Verifica que la página cargue correctamente.
3. Comprueba el título del documento HTML.
4. Verifica la visibilidad de la navegación principal.
5. Verifica el renderizado de la sección principal (hero section).
6. Verifica la visibilidad del catálogo de productos y del formulario de pedido.
7. Inspecciona la consola en busca de errores y recursos que no se cargan.
8. Toma una captura de pantalla completa de la página como evidencia (desde la navegación hasta el formulario).
9. Reporta el resultado de cada comprobación (PASS / FAIL / OBSERVACIÓN / PENDIENTE).

No modifiques ningún archivo del proyecto.
```

### 5.2 TC-02 — Responsive

```text
Usa Playwright MCP para realizar la auditoría del Test Case 2: Responsive en dispositivos móviles en la aplicación local de Heladería Vainell.

URL:
http://127.0.0.1:3000/index.html?vscode-livepreview=true

Instrucciones:
1. Abre la página en Chromium.
2. Configura y prueba los siguientes viewports uno por uno:
   - iPhone: 390 × 844
   - Samsung Galaxy: 360 × 800
   - iPad: 768 × 1024
3. En cada viewport verifica que:
   - La página alcance `readyState: complete`.
   - La navegación principal, la sección Hero, el catálogo y el formulario estén visibles.
   - No exista desbordamiento horizontal (compara `clientWidth` y `scrollWidth`).
   - Los controles del formulario estén visibles, habilitados, editables, reciban foco y acepten interacción con el puntero.
4. No envíes el formulario.
5. Toma una captura de pantalla completa de cada viewport como evidencia.
6. Reporta los resultados en el siguiente formato de tabla:

| Dispositivo / viewport | Resultado | `innerWidth × innerHeight` | `clientWidth` | `scrollWidth` | Desbordamiento horizontal |
|---|---|---:|---:|---:|---|
| iPhone (390 × 844) | ... | ... | ... | ... | ... |
| Samsung Galaxy (360 × 800) | ... | ... | ... | ... | ... |
| iPad (768 × 1024) | ... | ... | ... | ... | ... |

No modifiques ningún archivo del proyecto.
```

### 5.3 TC-03 — Rendimiento

```text
Usa Playwright MCP para realizar la auditoría del Test Case 3: Performance y Carga de Página en la aplicación local de Heladería Vainell.

URL:
http://127.0.0.1:3000/index.html?vscode-livepreview=true

Instrucciones:
1. Abre la página en Chromium.
2. Espera hasta que `document.readyState` sea `complete`.
3. Mide los tiempos de navegación con `window.performance.getEntriesByType('navigation')[0]` y calcula:
   - TTFB: `responseStart - requestStart`
   - DOMContentLoaded: `domContentLoadedEventEnd - fetchStart`
   - Tiempo total de carga: `loadEventEnd - fetchStart`
4. Inspecciona los recursos con `window.performance.getEntriesByType('resource')`.
5. Identifica y lista los recursos con mayor duración y mayor tamaño transferido (`transferSize`).
6. Revisa la consola y registra cualquier error de carga.
7. Toma una captura de pantalla de la página cargada como evidencia.
8. Reporta las métricas de navegación, los recursos destacados y los errores encontrados.

No modifiques ningún archivo del proyecto.
```

### 5.4 TC-04 — Accesibilidad (literal, Momento 1)

```text
Usa Playwright MCP para realizar la auditoría del Test Case 4: Accesibilidad Web en la aplicación local de Heladería Vainell.

URL:
http://localhost:3000

Instrucciones:
1. Abre la página.
2. Inyecta la librería axe-core en la página.
3. Ejecuta axe.run() y analiza los resultados.
4. Reporta las violaciones por nivel de impacto e indica los elementos HTML afectados.
5. Si encuentras violaciones críticas o graves, prepara un issue de tipo bug en GitHub.
6. Toma una captura de pantalla como evidencia.

No modifiques ningún archivo del proyecto.
```

### 5.5 TC-05 — HTML semántico (literal, Momento 1)

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

## 10. Notificaciones y comunicación

Las notificaciones se registran con la fecha real de envío y su constancia. Las comunicaciones del Momento 1 no cuentan con constancia verificable y no se declaran como realizadas.

### Momento 2

Los hallazgos del Momento 2 se registraron como issues en GitHub: [#57](https://github.com/eternalnight04/HeladeriaVainell/issues/57) (404 de `favicon.ico`, cerrado el 01/11/2026) y [#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60) (errores de la validación W3C en los testimonios).

El equipo no cuenta con un responsable separado para el HTML de los testimonios. El Coordinador, que registró los hallazgos, corrigió el hallazgo #60 directamente, de modo que no hubo una notificación a un tercero. La constancia de la gestión es la siguiente:

| Hallazgo | Responsable de la corrección | Medio | Fecha | Evidencia |
|----------|------------------------------|-------|-------|-----------|
| [#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60) | Coordinador / DevOps | Corrección en `index.html` mediante pull request | `[5/11/2026]` | [PR:#69](https://github.com/eternalnight04/HeladeriaVainell/pull/69) |

No se documentó una notificación adicional a otros integrantes; no se declara ninguna que no tenga constancia verificable.

### Momento 1

Sin constancia verificable de notificación. Los issues [#23](https://github.com/eternalnight04/HeladeriaVainell/issues/23), [#24](https://github.com/eternalnight04/HeladeriaVainell/issues/24) y [#25](https://github.com/eternalnight04/HeladeriaVainell/issues/25) fueron resueltos y cerrados; el cierre consta en GitHub.

## 6. Resultados del Momento 1 — Pre-merge

El informe histórico `docs/04-testing/testing-doc.md` contenía una matriz anterior con cinco resultados: un PASS y cuatro FAIL, además de referencias a los issues `#21`, `#22`, `#23`, `#24` y `#25`.

Esa matriz histórica utilizaba categorías de pruebas distintas de las definidas en los test cases actuales. Por lo tanto, sus estados no se trasladan automáticamente a los TC-01 a TC-05 de esta especificación.

| Registro histórico | Estado consignado en el informe anterior | Observación |
|---|---|---|
| TC-01 — Accesibilidad | FAIL | Asociado históricamente al issue `#21`, que corresponde a una tarea de DevOps de la Actividad 2 y no a un hallazgo de QA. |
| TC-02 — Atributos ALT | PASS | El informe anterior lo registra como aprobado. |
| TC-03 — Formulario | FAIL | Asociado históricamente a los issues `#22` y `#23`. El `#22` no existe; el `#23` corresponde al desbordamiento horizontal en mobile (TC-02 actual). |
| TC-04 — Lighthouse | FAIL | Asociado históricamente al issue `#24`, que corresponde a la lista de definición detectada con axe-core (TC-04 actual). |
| TC-05 — HTML/W3C | FAIL | Asociado al issue `#25`, que corresponde al TC-05 actual. |

**Cierre del Momento 1 (verificado en GitHub):** los hallazgos reales del Momento 1 son [#23](https://github.com/eternalnight04/HeladeriaVainell/issues/23) (TC-02), [#24](https://github.com/eternalnight04/HeladeriaVainell/issues/24) (TC-04) y [#25](https://github.com/eternalnight04/HeladeriaVainell/issues/25) (TC-05), abiertos el 28/09/2026 y hoy cerrados. El `#21` es una tarea de DevOps de la Actividad 2 y no es de QA; el `#22` no existe.

## 7. Resultados del Momento 2 — Post-merge

| Caso | Resultado documentado | Estado de cierre |
|---|---|---|
| TC-01 — Compatibilidad | Página cargada y captura general obtenida en Chromium. Se observó un 404 de `/favicon.ico` (issue [#57](https://github.com/eternalnight04/HeladeriaVainell/issues/57), cerrado) y mensajes de consola relacionados con `autocomplete`. | Parcial; otros navegadores pendientes. |
| TC-02 — Responsive | iPhone 390 × 844, Samsung 360 × 800 e iPad 768 × 1024: controles visibles e interactuables, sin desbordamiento horizontal en las mediciones registradas. | **PASS** para los tres viewports emulados. |
| TC-03 — Rendimiento | `readyState`: `complete`; TTFB: 2,6 ms; DOMContentLoaded: 32,8 ms; carga total: 79,2 ms. | Métricas registradas; sin PASS/FAIL formal por falta de umbral definido. |
| TC-04 — Accesibilidad | axe-core: 0 infracciones automatizadas confirmadas, 47 comprobaciones aprobadas, 2 incompletas y 39 no aplicables. Los 3 nodos de `aria-allowed-attr` fueron confirmados como errores por el validador W3C (issue [#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60)). | Parcial; `color-contrast` pendiente de revisión manual. |
| TC-05 — HTML semántico y W3C | Inspección estructural sin hallazgos: 17 encabezados, 4 imágenes con atributo `alt`, 68 controles inspeccionados y ningún ID duplicado. Validación W3C Nu HTML Checker del 01/11/2026: 3 errores y 3 advertencias en los testimonios. Issue: [#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60). | **FAIL** en la validación W3C; estructura semántica sin hallazgos. |

### Detalles relevantes

**TC-01 — Compatibilidad**

Se observó un error 404 al solicitar `/favicon.ico`, registrado en el issue [#57](https://github.com/eternalnight04/HeladeriaVainell/issues/57) (cerrado el 01/11/2026). También se registraron mensajes de consola relacionados con atributos `autocomplete`. Estos mensajes requieren revisión antes de decidir si representan defectos funcionales.

**TC-02 — Responsive**

Las tres resoluciones emuladas pasaron las comprobaciones registradas. La prueba se realizó en Chromium con viewports emulados; no equivale a probar físicamente los dispositivos ni a certificar otros navegadores.

**TC-03 — Rendimiento**

Los tiempos registrados corresponden a una ejecución local. No representan una prueba de carga ni garantizan el rendimiento en producción. Sin criterios numéricos definidos previamente, no se asigna un resultado formal de aceptación.

**TC-04 — Accesibilidad**

La auditoría no detectó infracciones automatizadas confirmadas. Quedaron dos reglas incompletas: `aria-allowed-attr` y `color-contrast`. La regla `aria-allowed-attr` fue confirmada como error por el validador W3C (líneas 557, 569 y 581 de `index.html`; ver `test-case-5.md` e issue [#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60)). `color-contrast` requiere revisión manual de los elementos señalados. No se declara conformidad total con WCAG.

**TC-05 — HTML semántico y W3C**

La inspección registró 17 encabezados: 1 `h1`, 9 `h2` y 7 `h3`; 4 imágenes con atributo `alt`, de las cuales 3 tienen texto no vacío; y 68 controles inspeccionados. No se encontraron identificadores duplicados.

La validación con W3C Nu HTML Checker (01/11/2026) reportó 3 errores (`aria-label` en `p`, líneas 557, 569 y 581) y 3 advertencias (`article` sin encabezado), todos en los testimonios. Los tres errores coinciden con los nodos de la regla incompleta `aria-allowed-attr` de TC-04. Seguimiento en el issue [#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60). Los errores originales del issue [#25](https://github.com/eternalnight04/HeladeriaVainell/issues/25) ya no aparecen en el reporte.

## 8. Resumen cuantitativo del Momento 2

- **Casos de prueba documentados:** 5.
- **PASS formal:** 1 — TC-02, limitado a los tres viewports emulados.
- **FAIL formal:** 1 — TC-05, por la validación W3C (3 errores, issue [#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60)).
- **Casos con cierre parcial o sin criterio formal de aprobación:** 3 — TC-01, TC-03 y TC-04.
- **Issues creados durante esta ejecución:** [#57](https://github.com/eternalnight04/HeladeriaVainell/issues/57) (favicon, registrado el 27/10/2026 y cerrado el 01/11/2026) y [#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60) (W3C).
- **Issues históricos verificados:** #23, #24 y #25 (cerrados); #21 no es de QA y #22 no existe.

Que un caso no tenga un FAIL formal asignado no significa que esté completamente aprobado.

## 9. Hallazgos y decisiones

| Hallazgo | Decisión de QA |
|---|---|
| Error 404 de `/favicon.ico` | Registrado en [#57](https://github.com/eternalnight04/HeladeriaVainell/issues/57); cerrado el 01/11/2026. |
| Mensajes relacionados con `autocomplete` | Revisar los campos afectados y determinar si requieren corrección. No clasificar automáticamente como bug confirmado. |
| `aria-allowed-attr` (accesibilidad) | Confirmada como error por el validador W3C; seguimiento en [#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60). |
| `color-contrast` (accesibilidad) | Mantener la revisión manual pendiente antes de cerrar la auditoría. |
| Validación W3C | Ejecutada el 01/11/2026: 3 errores y 3 advertencias en los testimonios, registrados en [#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60). Verificar el cierre del issue y repetir la validación. |
| Rendimiento sin umbral acordado | Conservar las métricas y definir un criterio de aceptación antes de declarar PASS o FAIL. |
| Compatibilidad en otros navegadores no comprobada | No declarar compatibilidad completa hasta ejecutar las pruebas pendientes. |

Issues creados durante el Momento 2: [#57](https://github.com/eternalnight04/HeladeriaVainell/issues/57) y [#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60).

## 10. Notificaciones y comunicación

- **Momento 1:** la especificación original contemplaba notificar los hallazgos al Desarrollador Frontend y al Especialista en Responsive. No hay evidencia en los reportes consultados que permita confirmar el envío o la recepción de esas notificaciones.
- **Momento 2:** no se documentó una notificación efectivamente enviada al Coordinador ni a los responsables. Debe registrarse el envío cuando exista evidencia verificable.

No se declara completada ninguna notificación sin constancia de envío.

## 11. Cierre de la ejecución

### Momento 1

**Estado documental:** histórico verificado en GitHub. Los issues [#23](https://github.com/eternalnight04/HeladeriaVainell/issues/23), [#24](https://github.com/eternalnight04/HeladeriaVainell/issues/24) y [#25](https://github.com/eternalnight04/HeladeriaVainell/issues/25) corresponden a TC-02, TC-04 y TC-05; el `#21` no es de QA y el `#22` no existe.

### Momento 2

**Estado documental:** cinco casos documentados; TC-02 aprobado para los viewports emulados, TC-05 con FAIL en la validación W3C ([#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60)) y TC-01, TC-03 y TC-04 con verificaciones pendientes o sin criterio formal de aceptación.

### Pendientes para el cierre definitivo

- [x] Verificar en GitHub la existencia y el estado actual de los issues históricos `#21` a `#25`.
- [x] Registrar y revisar el 404 de `/favicon.ico` ([#57](https://github.com/eternalnight04/HeladeriaVainell/issues/57), cerrado).
- [ ] Investigar los mensajes de consola relacionados con `autocomplete`.
- [ ] Completar la revisión manual de `color-contrast`.
- [x] Ejecutar y registrar la validación W3C (01/11/2026).
- [ ] Verificar el cierre del issue [#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60) y repetir la validación W3C.
- [ ] Definir umbrales de aceptación de rendimiento.
- [ ] Completar la comprobación de compatibilidad en los navegadores pendientes.
- [ ] Verificar y documentar las notificaciones efectivamente enviadas.
- [ ] Actualizar `changelog.md` y vincular la PR correspondiente cuando se confirme su estado.

## 12. Documentación asociada

- `docs/04-testing/test-case-1.md`
- `docs/04-testing/test-case-2.md`
- `docs/04-testing/test-case-3.md`
- `docs/04-testing/test-case-4.md`
- `docs/04-testing/test-case-5.md`
- `docs/04-testing/testing-doc.md`
