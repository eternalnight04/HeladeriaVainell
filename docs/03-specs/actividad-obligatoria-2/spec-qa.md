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

### TC-05 — Estructura HTML semántica

Inspeccionar encabezados, imágenes, controles, identificadores y elementos semánticos. La validación mediante W3C Nu HTML Checker debe registrarse por separado.

**Limitación:** la inspección del DOM no reemplaza una validación completa del documento mediante el validador W3C.

## 4. Herramientas y evidencias

- **Playwright MCP:** navegación, inspección del DOM, comprobación de controles, emulación de viewports y capturas.
- **Chromium:** navegador utilizado en las verificaciones de Momento 2.
- **axe-core 4.7.2:** auditoría automatizada de accesibilidad.
- **Performance API:** registro de métricas de carga.
- **GitHub MCP:** previsto para el registro de issues, pero no se documentó la creación de nuevos issues durante la ejecución de Momento 2.
- **W3C Nu HTML Checker:** validación pendiente de confirmar en Momento 2.

Las evidencias disponibles en `docs/04-testing/` son:

- `evidencia-test-case-1.png`
- `evidencia-test-case-1-momento-2.png`
- `evidencia-test-case-2-iphone.png`
- `evidencia-test-case-2-samsung.png`
- `evidencia-test-case-2-ipad.png`
- `evidencia-test-case-3-momento-2.png`
- `evidencia-test-case-4-momento-2.png`
- `evidencia-test-case-5-momento-2.png`

Los resultados detallados deben consultarse en los cinco archivos `test-case-1.md` a `test-case-5.md`.

## 5. Prompts y trazabilidad

Los siguientes puntos describen el objetivo de las instrucciones de prueba. **No son transcripciones literales de los prompts originales**, ya que no se dispone aquí de su texto exacto.

### Prompt TC-01 — Compatibilidad de escritorio

Solicitar a Playwright MCP que abra el sitio local, compruebe que la página carga, inspeccione su visualización general y registre errores relevantes de consola o de recursos. Limitar las conclusiones a los navegadores realmente probados.

### Prompt TC-02 — Responsive

Solicitar la evaluación del sitio con viewports de 390 × 844, 360 × 800 y 768 × 1024. Comprobar visibilidad e interacción de controles y comparar `scrollWidth` con `clientWidth` para detectar desbordamiento horizontal.

### Prompt TC-03 — Rendimiento

Solicitar la lectura de `document.readyState`, las métricas de navegación disponibles y los tiempos de carga de recursos. Registrar valores medidos y errores de red sin inventar umbrales de aceptación.

### Prompt TC-04 — Accesibilidad

Solicitar la ejecución de axe-core 4.7.2 sobre la página local, con el registro de infracciones confirmadas, reglas incompletas, elementos afectados y comprobaciones manuales pendientes.

### Prompt TC-05 — HTML semántico

Solicitar la inspección de encabezados, elementos semánticos, imágenes y textos alternativos, nombres accesibles de controles e identificadores duplicados. Registrar por separado si se ejecutó o no el validador W3C.

## 6. Resultados del Momento 1 — Pre-merge

El informe histórico `docs/04-testing/testing-doc.md` contiene una matriz anterior con cinco resultados: un PASS y cuatro FAIL, además de referencias a los issues `#21`, `#22`, `#23`, `#24` y `#25`.

Sin embargo, esa matriz histórica utiliza categorías de pruebas distintas de las definidas en los test cases actuales. Por lo tanto, sus estados no deben trasladarse automáticamente a los TC-01 a TC-05 de esta especificación.

| Registro histórico | Estado consignado en el informe anterior | Observación |
|---|---|---|
| TC-01 — Accesibilidad | FAIL | Asociado históricamente al issue `#21`. |
| TC-02 — Atributos ALT | PASS | El informe anterior lo registra como aprobado. |
| TC-03 — Formulario | FAIL | Asociado históricamente a los issues `#22` y `#23`. |
| TC-04 — Lighthouse | FAIL | Asociado históricamente al issue `#24`. |
| TC-05 — HTML/W3C | FAIL | Asociado históricamente al issue `#25`. |

**Cierre del Momento 1:** documentación histórica disponible, pero el estado actual de los issues y el detalle de cada ejecución deben verificarse en GitHub y en los reportes originales. No se afirma que los issues estén abiertos, cerrados o resueltos sin comprobarlo.

## 7. Resultados del Momento 2 — Post-merge

| Caso | Resultado documentado | Estado de cierre |
|---|---|---|
| TC-01 — Compatibilidad | Página cargada y captura general obtenida en Chromium. Se observó un 404 de `/favicon.ico` y mensajes de consola relacionados con `autocomplete`. | Parcial; otros navegadores pendientes. |
| TC-02 — Responsive | iPhone 390 × 844, Samsung 360 × 800 e iPad 768 × 1024: controles visibles e interactuables, sin desbordamiento horizontal en las mediciones registradas. | **PASS** para los tres viewports emulados. |
| TC-03 — Rendimiento | `readyState`: `complete`; TTFB: 2,6 ms; DOMContentLoaded: 32,8 ms; carga total: 79,2 ms. | Métricas registradas; sin PASS/FAIL formal por falta de umbral definido. |
| TC-04 — Accesibilidad | axe-core: 0 infracciones automatizadas confirmadas, 47 comprobaciones aprobadas, 2 incompletas y 39 no aplicables. | Parcial; revisión manual pendiente. |
| TC-05 — HTML semántico | 17 encabezados, 4 imágenes con atributo `alt`, 68 controles inspeccionados y ningún ID duplicado observado. | Parcial; validación W3C pendiente. |

### Detalles relevantes

**TC-01 — Compatibilidad**

Se observó un error 404 al solicitar `/favicon.ico`. También se registraron mensajes de consola relacionados con atributos `autocomplete`. Estos mensajes requieren revisión antes de decidir si representan defectos funcionales.

**TC-02 — Responsive**

Las tres resoluciones emuladas pasaron las comprobaciones registradas. La prueba se realizó en Chromium con viewports emulados; no equivale a probar físicamente los dispositivos ni a certificar otros navegadores.

**TC-03 — Rendimiento**

Los tiempos registrados corresponden a una ejecución local. No representan una prueba de carga ni garantizan el rendimiento en producción. Sin criterios numéricos definidos previamente, no se asigna un resultado formal de aceptación.

**TC-04 — Accesibilidad**

La auditoría no detectó infracciones automatizadas confirmadas. Quedaron dos reglas incompletas: `aria-allowed-attr` y `color-contrast`. Es necesario revisar los elementos señalados manualmente. No se declara conformidad total con WCAG.

**TC-05 — HTML semántico**

La inspección registró 17 encabezados: 1 `h1`, 9 `h2` y 7 `h3`; 4 imágenes con atributo `alt`, de las cuales 3 tienen texto no vacío; y 68 controles inspeccionados. No se encontraron identificadores duplicados. La validación W3C sigue pendiente de confirmación.

## 8. Resumen cuantitativo del Momento 2

- **Casos de prueba documentados:** 5.
- **PASS formal:** 1 — TC-02, limitado a los tres viewports emulados.
- **FAIL formal:** 0 asignados en este resumen.
- **Casos con cierre parcial o sin criterio formal de aprobación:** 4 — TC-01, TC-03, TC-04 y TC-05.
- **Issues nuevos creados durante esta ejecución:** 0 documentados.
- **Issues históricos mencionados en el informe anterior:** 5 referencias (`#21` a `#25`); su estado actual no está verificado.

Que un caso no tenga un FAIL formal asignado no significa que esté completamente aprobado.

## 9. Hallazgos y decisiones

| Hallazgo | Decisión de QA |
|---|---|
| Error 404 de `/favicon.ico` | Registrar como hallazgo técnico y evaluar corrección. No se afirma que exista un issue nuevo. |
| Mensajes relacionados con `autocomplete` | Revisar los campos afectados y determinar si requieren corrección. No clasificar automáticamente como bug confirmado. |
| Reglas de accesibilidad incompletas | Mantener la revisión manual pendiente antes de cerrar la auditoría. |
| Validación W3C no confirmada | Mantener TC-05 parcialmente cerrado hasta ejecutar y documentar la validación. |
| Rendimiento sin umbral acordado | Conservar las métricas y definir un criterio de aceptación antes de declarar PASS o FAIL. |
| Compatibilidad en otros navegadores no comprobada | No declarar compatibilidad completa hasta ejecutar las pruebas pendientes. |

No se documentaron nuevos issues creados durante el Momento 2. Los issues históricos deben verificarse en GitHub antes de informar su estado definitivo.

## 10. Notificaciones y comunicación

- **Momento 1:** la especificación original contemplaba notificar los hallazgos al Desarrollador Frontend y al Especialista en Responsive. No hay evidencia en los reportes consultados que permita confirmar el envío o la recepción de esas notificaciones.
- **Momento 2:** no se documentó una notificación efectivamente enviada al Coordinador ni a los responsables. Debe registrarse el envío cuando exista evidencia verificable.

No se declara completada ninguna notificación sin constancia de envío.

## 11. Cierre de la ejecución

### Momento 1

**Estado documental:** histórico registrado, con necesidad de verificar la trazabilidad entre los test cases, los resultados originales y los issues `#21` a `#25`.

### Momento 2

**Estado documental:** cinco casos documentados; TC-02 aprobado para los viewports emulados y cuatro casos con verificaciones pendientes o sin criterio formal de aceptación.

### Pendientes para el cierre definitivo

- [ ] Verificar en GitHub la existencia y el estado actual de los issues históricos `#21` a `#25`.
- [ ] Revisar el 404 de `/favicon.ico`.
- [ ] Investigar los mensajes de consola relacionados con `autocomplete`.
- [ ] Completar las revisiones manuales de accesibilidad.
- [ ] Ejecutar y registrar la validación W3C.
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
