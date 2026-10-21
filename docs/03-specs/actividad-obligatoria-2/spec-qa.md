# Spec QA — Actividad Obligatoria N° 2

## 1. Rol

**Rol:** Documentador / QA Tester

**Responsable:** Lautaro Chavez

**Rama:** `feature/doc-qa-tester-add-test-cases`

## 2. Objetivo

Realizar pruebas automatizadas sobre el sitio web de Heladería Vainell para verificar su funcionamiento, compatibilidad, adaptación a diferentes dispositivos, rendimiento, accesibilidad y correcta utilización de una estructura HTML semántica.

Las pruebas serán ejecutadas mediante Playwright MCP contra la versión local del proyecto disponible en:

`http://localhost:3000`

El testing se realizará en dos momentos:

- **Momento 1:** testing pre-merge sobre las ramas de integración del Desarrollador Frontend y del Especialista en Responsive.
- **Momento 2:** testing post-merge sobre la rama `develop`, una vez integrados los trabajos de los integrantes.

## 3. Plan de testing

Se ejecutarán cinco test cases:

### Test Case 1 — Compatibilidad en navegadores desktop

Se verificará el comportamiento y la visualización del sitio en navegadores desktop: Chrome, Firefox, Safari y Edge.

**Objetivo:** detectar problemas de compatibilidad que puedan afectar la visualización o interacción con el sitio.

### Test Case 2 — Responsive en dispositivos móviles

Se verificará la adaptación de la interfaz utilizando emulación de viewport para dispositivos como iPhone, Samsung Galaxy e iPad.

**Objetivo:** detectar problemas de diseño responsive, desbordamientos, elementos fuera de pantalla o dificultades de interacción.

### Test Case 3 — Performance y carga

Se analizará el rendimiento de carga del sitio utilizando la Performance API disponible en el navegador.

**Objetivo:** detectar tiempos de carga elevados o recursos que puedan afectar el rendimiento general de la página.

### Test Case 4 — Accesibilidad web

Se realizará una revisión automatizada de accesibilidad mediante Playwright MCP e inyección de axe-core.

**Objetivo:** detectar problemas de accesibilidad que puedan dificultar el uso del sitio por parte de diferentes usuarios.

### Test Case 5 — Estructura HTML semántica

Se analizará la estructura HTML mediante un snapshot de accesibilidad y validación de HTML y CSS mediante las herramientas correspondientes.

**Objetivo:** comprobar que la estructura del documento utiliza elementos semánticos adecuados y detectar errores de validación.

## 4. Herramientas

### Playwright MCP

Se utilizará Playwright MCP para automatizar la interacción con un navegador real y ejecutar los cinco test cases sobre el sitio local.

Permitirá comprobar visualmente el sitio, utilizar diferentes tamaños de viewport, analizar información del navegador y obtener capturas de pantalla como evidencia.

### GitHub MCP

Se utilizará GitHub MCP para registrar directamente los hallazgos relevantes como issues de tipo bug en el repositorio.

Cada issue deberá describir el problema encontrado, indicar el contexto de detección y quedar asociado al responsable correspondiente para su resolución.

## 5. Criterios de aceptación

- [ ] Ejecutar los 5 test cases mediante Playwright MCP.
- [ ] Ejecutar los tests contra `http://localhost:3000`.
- [ ] Ejecutar los tests correspondientes durante el Momento 1.
- [ ] Repetir los tests durante el Momento 2 sobre `develop`.
- [ ] Documentar cada test case en `docs/04-testing/`.
- [ ] Registrar el prompt utilizado para cada test case.
- [ ] Registrar los hallazgos encontrados.
- [ ] Incorporar capturas de pantalla como evidencia.
- [ ] Crear un issue de tipo bug mediante GitHub MCP por cada hallazgo relevante.
- [ ] Registrar los issues generados en la documentación.
- [ ] Mantener `testing-doc.md` como índice central de los test cases.
- [ ] Registrar en `testing-doc.md` los issues generados durante cada momento.
- [ ] Notificar al Desarrollador Frontend y al Especialista en Responsive sobre los bugs encontrados durante el Momento 1.
- [ ] Notificar al Coordinador y a los responsables correspondientes sobre los bugs encontrados durante el Momento 2.
- [ ] Completar este documento con los prompts utilizados y los resultados de ambos momentos.
- [ ] Registrar la cantidad de tests ejecutados, aprobados y fallidos.
- [ ] Registrar la cantidad de bugs creados.
- [ ] Documentar las decisiones tomadas respecto de los hallazgos.
- [ ] Actualizar `changelog.md` con la contribución y el enlace a la PR.
- [ ] Crear la PR `feature/doc-qa-tester-add-test-cases` hacia `develop`.

## 6. Evidencia de ejecución

Esta sección será completada una vez finalizados los tests.

### Prompts utilizados

Se incorporarán los prompts utilizados en Copilot Agent Mode junto con Playwright MCP para cada test case.

### Resultados

Se registrará:

- Tests ejecutados.
- Tests aprobados.
- Tests fallidos.
- Bugs detectados.
- Issues creados.
- Momento de detección.

### Decisiones sobre hallazgos

Se documentará qué hallazgos fueron registrados como bugs y cuáles no, explicando el motivo de cada decisión.

## 7. Documentación asociada

Los resultados detallados de las pruebas estarán documentados en:

`docs/04-testing/`

Incluyendo:

- `test-case-1.md`
- `test-case-2.md`
- `test-case-3.md`
- `test-case-4.md`
- `test-case-5.md`
- `testing-doc.md`

## Estado de Ejecución de Pruebas (Momento 1 - Pre-Merge)

- **Última actualización:** Septiembre 2026
- **Responsable:** Lautaro Chavez

### Tabla Resumen
- **TC-01:** Auditoría de Accesibilidad — **FAIL** ❌ (Issue `#21`)
- **TC-02:** Atributos ALT e Imágenes — **PASS** ✅
- **TC-03:** Formulario de Contacto — **FAIL** ❌ (Issues `#22`, `#23`)
- **TC-04:** Auditoría Lighthouse — **FAIL** ❌ (Issue `#24`)
- **TC-05:** Estructura HTML y W3C — **FAIL** ❌ (Issue `#25`)