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

## 2. Resultados históricos — Momento 1

El informe histórico contiene la siguiente matriz:

| Prueba del informe original | Resultado histórico | Issues referenciados |
|---|---|---|
| Accesibilidad WCAG 2.1 AA | FAIL | `#21` |
| Atributos ALT e imágenes | PASS | No indicado |
| Formulario de contacto | FAIL | `#22`, `#23` |
| Lighthouse: rendimiento, SEO y buenas prácticas | FAIL | `#24` |
| HTML semántico y W3C | FAIL | `#25` |

El informe original atribuye los siguientes hallazgos a esos issues:

- **#21:** contraste insuficiente en textos y componentes interactivos.
- **#22:** validaciones HTML5 de formulario presuntamente ausentes o incompletas.
- **#23:** falta de respuesta o redirección tras el envío del formulario.
- **#24:** observaciones históricas sobre rendimiento, SEO y recursos de imagen.
- **#25:** errores históricos de validación HTML, idioma del documento y estructura semántica.

Estas referencias se conservan como antecedentes documentales. La existencia, vigencia y resolución actual de cada issue debe verificarse directamente en GitHub. La matriz histórica usa categorías diferentes de las pruebas actuales, por lo que no debe interpretarse como una medición comparable de los cinco casos del Momento 2.

## 3. Resultados — Momento 2

| Caso | Verificación | Resultado |
|---|---|---|
| TC-01 | Carga general en Chromium y captura del sitio | Parcial: otros navegadores pendientes. |
| TC-02 | Responsive en tres viewports emulados | PASS para los tres tamaños probados. |
| TC-03 | Métricas de navegación y carga de recursos | Métricas registradas; sin umbral formal de aceptación. |
| TC-04 | Auditoría axe-core 4.7.2 | Sin infracciones automatizadas confirmadas; revisión manual pendiente. |
| TC-05 | Inspección de estructura y accesibilidad del DOM | Inspección registrada; validación W3C pendiente. |

### 3.1 TC-01 — Compatibilidad de escritorio

La página cargó en Chromium y se guardó una captura general.

Se registraron:
- Un error 404 al solicitar `/favicon.ico`.
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

El recurso `imagenes/logo_vainell.png` presentó una duración registrada aproximada de 39,4 ms. Durante la ejecución también se observó el 404 de `/favicon.ico`.

**Conclusión:** métricas obtenidas en un entorno local. Como no se definió un umbral de aceptación previo, no se asigna PASS o FAIL formal. Estos resultados no constituyen una prueba de carga ni una medición de producción.

### 3.4 TC-04 — Accesibilidad

Auditoría realizada con axe-core 4.7.2:

| Resultado de axe-core | Cantidad |
|---|---:|
| Infracciones automatizadas confirmadas | 0 |
| Comprobaciones aprobadas | 47 |
| Comprobaciones incompletas | 2 |
| No aplicables | 39 |

Las reglas incompletas incluyen `aria-allowed-attr` y `color-contrast`. Se requiere inspección manual de los elementos señalados.

**Conclusión:** sin infracciones automatizadas confirmadas en esta ejecución. No se declara conformidad completa con WCAG 2.1 AA hasta completar las comprobaciones manuales pertinentes.

### 3.5 TC-05 — Estructura HTML semántica

La inspección del DOM registró:

- **17 encabezados:** 1 `h1`, 9 `h2` y 7 `h3`.
- **4 imágenes:** todas poseen atributo `alt`; 3 tienen texto alternativo no vacío.
- **68 controles:** inspeccionados respecto de sus nombres accesibles.
- **Identificadores duplicados:** ninguno observado.
- **Validador W3C:** ejecución pendiente de confirmar.

**Conclusión:** inspección estructural documentada. La conformidad HTML no queda certificada hasta completar y registrar la validación W3C.

## 4. Evidencias disponibles

Las capturas de Momento 2 están en `docs/04-testing/`:

- `evidencia-test-case-1-momento-2.png`
- `evidencia-test-case-2-iphone.png`
- `evidencia-test-case-2-samsung.png`
- `evidencia-test-case-2-ipad.png`
- `evidencia-test-case-3-momento-2.png`
- `evidencia-test-case-4-momento-2.png`
- `evidencia-test-case-5-momento-2.png`

También existe la captura histórica `evidencia-test-case-1.png`.

Los detalles de cada ejecución, sus limitaciones y sus conclusiones se encuentran en:

- `test-case-1.md`
- `test-case-2.md`
- `test-case-3.md`
- `test-case-4.md`
- `test-case-5.md`

## 5. Resumen cuantitativo del Momento 2

- **Casos documentados:** 5.
- **PASS formal:** 1.
- **FAIL formal asignado en el resumen:** 0.
- **Casos parciales o sin criterio formal de aceptación:** 4.
- **Issues nuevos documentados como creados durante la ejecución:** 0.
- **Referencias a issues históricos:** 5 (`#21` a `#25`), con estado actual sin verificar.

Los cuatro casos sin cierre formal son TC-01, TC-03, TC-04 y TC-05. La ausencia de un FAIL formal no equivale a aprobación completa.

## 6. Hallazgos, decisiones y seguimiento

| Hallazgo | Decisión |
|---|---|
| 404 de `/favicon.ico` | Registrar y evaluar la corrección. No se documenta un issue nuevo. |
| Mensajes relacionados con `autocomplete` | Inspeccionar los campos afectados antes de clasificarlos como defectos. |
| Reglas de accesibilidad incompletas | Mantener pendiente la revisión manual. |
| Validación W3C pendiente | No declarar conformidad HTML completa. |
| Rendimiento sin umbral definido | Conservar las métricas y definir criterios antes de emitir un PASS o FAIL. |
| Navegadores adicionales sin probar | No declarar compatibilidad completa. |

Durante el Momento 2 no se documentó la creación de nuevos issues mediante GitHub MCP. Tampoco se dispone en este informe de confirmación verificable del estado actual de los issues históricos.

## 7. Notificaciones

La documentación original contempla notificar los hallazgos del Momento 1 al Desarrollador Frontend y al Especialista en Responsive, y los del Momento 2 al Coordinador y a los responsables correspondientes.

**Estado documental:** no hay constancia de envío o recepción en los reportes consultados. Por tanto, las notificaciones no se consideran verificadas ni completadas en este informe.

Cuando se realicen, se debe registrar el destinatario, la fecha y el medio utilizado, sin afirmar que fueron enviadas antes de contar con evidencia.

## 8. Cierre y pendientes

### Momento 1

Se conserva la matriz histórica y sus referencias a issues. Para cerrar la trazabilidad, falta comprobar el estado de los issues y contrastarlos con las evidencias originales de cada prueba.

### Momento 2

Se documentaron los cinco casos. TC-02 pasó las verificaciones de los tres viewports emulados; los otros cuatro casos necesitan comprobaciones adicionales o criterios formales de aceptación.

### Acciones pendientes

- [ ] Verificar los issues históricos `#21` a `#25` en GitHub.
- [ ] Revisar el error 404 de `/favicon.ico`.
- [ ] Analizar los mensajes relacionados con `autocomplete`.
- [ ] Completar la revisión manual de accesibilidad.
- [ ] Ejecutar y registrar la validación W3C.
- [ ] Definir criterios de aceptación de rendimiento.
- [ ] Completar pruebas en los navegadores pendientes.
- [ ] Registrar las notificaciones cuando exista evidencia de envío.
- [ ] Actualizar `changelog.md` y documentar el enlace de la PR cuando corresponda.

**Estado general:** documentación integrada de ambos momentos, con cierre parcial del Momento 2 y pendientes identificados. No se declara la suite completa aprobada.
