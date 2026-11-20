# Informe de Estrategia y Ejecución de QA Testing

- **Proyecto:** Heladería Vainell — Sitio web promocional.
- **Responsable de QA:** Lautaro Chavez.
- **Rama de trabajo original:** `feature/doc-qa-tester-add-test-cases`.
- **Rama de ejecución de Momento 2:** `qa/momento-2`.
- **Momentos documentados:** Momento 1 (pre-merge) y Momento 2 (post-merge).
- **Entorno de Momento 2:** Chromium mediante Playwright MCP, con Live Preview local.
- **URL observada:** `http://127.0.0.1:3000/index.html?vscode-livepreview=true`.

## 1. Objetivo y estrategia

Este informe centraliza los resultados disponibles de las pruebas de calidad del sitio Heladería Vainell.

La estrategia contempla cinco áreas:

1. Compatibilidad en navegadores de escritorio.
2. Diseño responsive.
3. Rendimiento y carga.
4. Accesibilidad web.
5. Estructura HTML semántica y validación.

Las conclusiones se limitan a las comprobaciones efectivamente documentadas. Las pruebas con viewports emulados no equivalen a pruebas físicas de dispositivos y las auditorías automatizadas no garantizan por sí solas la conformidad total con estándares de accesibilidad o HTML.

## 2. Trazabilidad de hallazgos — Momento 1 y Momento 2

La matriz original del Momento 1 usaba las referencias `#21` a `#25`, algunas de las cuales no correspondían a hallazgos de QA. Se reemplaza por la trazabilidad verificada en GitHub (fecha de verificación: 02/11/2026).

| Issue | Título | Test Case | Momento de detección | Estado |
|---|---|---|---|---|
| [#23](https://github.com/eternalnight04/HeladeriaVainell/issues/23) |[BUG] Desbordamiento horizontal (overflow) en versión mobile por imagen hero| TC-02 Responsive | Momento 1 (28/09/2026) | Cerrado |
| [#24](https://github.com/eternalnight04/HeladeriaVainell/issues/24) |[BUG] Estructura de lista de definición invalida (regla dlitem) en sección de características | TC-04 Accesibilidad | Momento 1 (28/09/2026) | Cerrado |
| [#25](https://github.com/eternalnight04/HeladeriaVainell/issues/25) |[BUG] Errores de validación HTML W3C, marcado sintáctico e incorrecta estructura de footer| TC-05 HTML semántico y W3C | Momento 1 (28/09/2026) | Cerrado |
| [#57](https://github.com/eternalnight04/HeladeriaVainell/issues/57) | [BUG] Error 404 al solicitar favicon.ico (el sitio no tiene favicon) | TC-01 y TC-03 (también observado en TC-04 y TC-05) | Momento 2 (27/10/2026) | Cerrado |
| [#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60) |[BUG] Errores de validación W3C: aria-label en párrafos de puntuación de testimonios | TC-05 (relacionado con la regla incompleta `aria-allowed-attr` de TC-04) | Momento 2 (01/11/2026) | Abierto |

**Referencias históricas descartadas:** el informe original citaba `#21` y `#22`. El `#21` corresponde a "A2- Coordinador / DevOps" y no es un hallazgo de QA. El `#22` no existe en el repositorio. Ninguno de los dos se incluye en la matriz.

**Categorías del informe original sin issue verificable:** las pruebas de formulario de contacto y Lighthouse no tienen un issue real asociado ni evidencia del Momento 1 que pueda comprobarse, por lo que no se conservan como resultados históricos.

## 3. Resultados — Momento 2

| Caso | Verificación | Resultado |
|---|---|---|
| TC-01 | Carga general en Chromium y captura del sitio | Parcial: otros navegadores pendientes. |
| TC-02 | Responsive en tres viewports emulados | PASS para los tres tamaños probados. |
| TC-03 | Métricas de navegación y carga de recursos | Métricas registradas; sin umbral formal de aceptación. |
| TC-04 | Auditoría axe-core 4.7.2 | Sin infracciones automatizadas confirmadas; `aria-allowed-attr` confirmada como error por el validador W3C ([#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60)); `color-contrast` pendiente de revisión manual. |
| TC-05 | Inspección de estructura del DOM y validación W3C Nu HTML Checker | Inspección estructural sin hallazgos. Validación W3C (01/11/2026): 3 errores y 3 advertencias ([#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60)). FAIL en la validación W3C. |

### 3.1 TC-01 — Compatibilidad de escritorio

La página cargó en Chromium y se guardó una captura general.

Se registraron:
- Un error 404 al solicitar `/favicon.ico`, registrado en el issue [#57](https://github.com/eternalnight04/HeladeriaVainell/issues/57) (cerrado el 01/11/2026).
- Mensajes de consola relacionados con atributos `autocomplete`.
- Compatibilidad con Firefox, Safari y Edge pendiente de comprobación.

**Conclusión:** prueba parcialmente ejecutada. No se declara compatibilidad completa entre navegadores.

### 3.2 TC-02 — Diseño responsive

Se evaluaron estos viewports:

| Dispositivo emulado | Viewport | Resultado |
|---|---:|---|
| iPhone | 390 × 844 | PASS |
| Samsung Galaxy | 360 × 800 | PASS |
| iPad | 768 × 1024 | PASS |

En las mediciones registradas, los controles se encontraban visibles y disponibles para la interacción, y no se detectó desbordamiento horizontal.

**Conclusión:** PASS para los tres viewports emulados. No implica certificación en dispositivos físicos ni en otros navegadores.

### 3.3 TC-03 — Rendimiento y carga

Métricas registradas mediante la Performance API:

| Métrica | Valor |
|---|---:|
| `document.readyState` | `complete` |
| TTFB | 2,6 ms |
| DOMContentLoaded | 32,8 ms |
| Carga total | 79,2 ms |

El recurso `imagenes/logo_vainell.png` presentó una duración registrada aproximada de 39,4 ms. Durante la ejecución también se observó el 404 de `/favicon.ico` (issue [#57](https://github.com/eternalnight04/HeladeriaVainell/issues/57)).

**Conclusión:** métricas obtenidas en un entorno local. Como no se definió un umbral de aceptación previo, no se asigna PASS o FAIL formal. Estos resultados no constituyen una prueba de carga ni una medición de producción.

### 3.4 TC-04 — Accesibilidad

Auditoría realizada con axe-core 4.7.2:

| Resultado de axe-core | Cantidad |
|---|---:|
| Infracciones automatizadas confirmadas | 0 |
| Comprobaciones aprobadas | 47 |
| Comprobaciones incompletas | 2 |
| No aplicables | 39 |

Las reglas incompletas son `aria-allowed-attr` y `color-contrast`. La regla `aria-allowed-attr` fue confirmada como error por el validador W3C el 01/11/2026 (issue [#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60)). `color-contrast` requiere inspección manual de los elementos señalados.

**Conclusión:** sin infracciones automatizadas confirmadas en esta ejecución. No se declara conformidad completa con WCAG 2.1 AA hasta completar las comprobaciones manuales pendientes.

### 3.5 TC-05 — Estructura HTML semántica y validación W3C

La inspección del DOM registró:

- **17 encabezados:** 1 `h1`, 9 `h2` y 7 `h3`.
- **4 imágenes:** todas poseen atributo `alt`; 3 tienen texto alternativo no vacío.
- **68 controles:** inspeccionados respecto de sus nombres accesibles.
- **Identificadores duplicados:** ninguno observado.

La validación con W3C Nu HTML Checker (01/11/2026) sobre `index.html` reportó 3 errores (`aria-label` en `p`) y 3 advertencias (`article` sin encabezado), todos en los testimonios. Seguimiento en el issue [#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60). Los errores originales del issue [#25](https://github.com/eternalnight04/HeladeriaVainell/issues/25) ya no aparecen en el reporte.

**Conclusión:** la estructura semántica no presenta hallazgos, pero el documento no cumple completamente con W3C en esta versión. La validación cubre solo `index.html`.

## 4. Evidencias disponibles

Las capturas de Momento 2 están en `docs/04-testing/`:

- `evidencia-test-case-1-momento-2.png`
- `evidencia-test-case-2-iphone.png`
- `evidencia-test-case-2-samsung.png`
- `evidencia-test-case-2-ipad.png`
- `evidencia-test-case-3-momento-2.png`
- `evidencia-test-case-4-momento-2.png`
- `evidencia-test-case-5-momento-2.png`
- `evidencia-test-case-5-w3c-momento-2.png`

También existe la captura histórica `evidencia-test-case-1.png`.

Los detalles de cada ejecución, sus limitaciones y sus conclusiones se encuentran en:

- `test-case-1.md`
- `test-case-2.md`
- `test-case-3.md`
- `test-case-4.md`
- `test-case-5.md`

## 5. Resumen cuantitativo del Momento 2

- **Casos documentados:** 5.
- **PASS formal:** 1 — TC-02.
- **FAIL formal:** 1 — TC-05, por la validación W3C (3 errores, issue [#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60)).
- **Casos parciales o sin criterio formal de aceptación:** 3 — TC-01, TC-03 y TC-04.
- **Issues creados durante la ejecución:** [#57](https://github.com/eternalnight04/HeladeriaVainell/issues/57) (favicon) y [#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60) (W3C).
- **Issues históricos verificados:** #23, #24 y #25 (cerrados); #21 no es de QA y #22 no existe.

La ausencia de un FAIL formal en un caso no equivale a aprobación completa.

## 6. Hallazgos, decisiones y seguimiento

| Hallazgo | Decisión |
|---|---|
| 404 de `/favicon.ico` | Registrado en [#57](https://github.com/eternalnight04/HeladeriaVainell/issues/57); cerrado el 01/11/2026. |
| Mensajes relacionados con `autocomplete` | Inspeccionar los campos afectados antes de clasificarlos como defectos. |
| `aria-allowed-attr` | Confirmada como error por el validador W3C; seguimiento en [#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60). |
| `color-contrast` | Mantener pendiente la revisión manual. |
| Validación W3C | Ejecutada el 01/11/2026 con 3 errores y 3 advertencias ([#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60)). Verificar el cierre del issue y repetir la validación. |
| Rendimiento sin umbral definido | Conservar las métricas y definir criterios antes de emitir un PASS o FAIL. |
| Navegadores adicionales sin probar | No declarar compatibilidad completa. |

## 7. Notificaciones

La documentación original contempla notificar los hallazgos del Momento 1 al Desarrollador Frontend y al Especialista en Responsive, y los del Momento 2 al Coordinador y a los responsables correspondientes.

**Estado documental:** no hay constancia de envío o recepción en los reportes consultados. Por tanto, las notificaciones no se consideran verificadas ni completadas en este informe.

Cuando se realicen, se debe registrar el destinatario, la fecha y el medio utilizado, sin afirmar que fueron enviadas antes de contar con evidencia.

## 8. Cierre y pendientes

### Momento 1

Trazabilidad verificada en GitHub (ver sección 2): los hallazgos reales son #23, #24 y #25, abiertos el 28/09/2026 y hoy cerrados.

### Momento 2

Se documentaron los cinco casos. TC-02 pasó las verificaciones de los tres viewports emulados; TC-05 tiene FAIL en la validación W3C ([#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60)); TC-01, TC-03 y TC-04 necesitan comprobaciones adicionales o criterios formales de aceptación.

### Acciones pendientes

- [x] Verificar los issues históricos `#21` a `#25` en GitHub.
- [x] Registrar el error 404 de `/favicon.ico` ([#57](https://github.com/eternalnight04/HeladeriaVainell/issues/57), cerrado).
- [ ] Analizar los mensajes relacionados con `autocomplete`.
- [ ] Completar la revisión manual de `color-contrast`.
- [x] Ejecutar y registrar la validación W3C (01/11/2026).
- [ ] Verificar el cierre del issue [#60](https://github.com/eternalnight04/HeladeriaVainell/issues/60) y repetir la validación W3C.
- [ ] Definir criterios de aceptación de rendimiento.
- [ ] Completar pruebas en los navegadores pendientes.
- [ ] Registrar las notificaciones cuando exista evidencia de envío.
- [ ] Actualizar `changelog.md` y documentar el enlace de la PR cuando corresponda.

**Estado general:** documentación integrada de ambos momentos, con cierre parcial del Momento 2 y pendientes identificados. No se declara la suite completa aprobada.