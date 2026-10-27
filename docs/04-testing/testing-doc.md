# Informe de Estrategia y Ejecución de QA Testing

- **Proyecto:** Heladería Vainell — Sitio Web Promocional
- **Documento:** Informe Integrado de QA Testing (Momentos 1 y 2)
- **Responsable de QA:** Lautaro Chavez
- **Rama de Trabajo:** `feature/doc-qa-tester-add-test-cases`
- **Momento 1 (pre-merge):** septiembre de 2026 (issues registrados el 28/09/2026)
- **Momento 2 (retest):** octubre de 2026

---

## 1. Introducción y Estrategia de Testing

Este informe documenta las pruebas de calidad (QA) realizadas sobre el sitio web promocional de **Heladería Vainell** con **Playwright MCP** (`@playwright/mcp`) mediante GitHub Copilot Agent Mode, junto con axe-core para accesibilidad y la Performance API del navegador para carga.

Los cinco test cases ejecutados son:
1. **TC-01:** Compatibilidad de escritorio
2. **TC-02:** Responsive en dispositivos móviles
3. **TC-03:** Performance y carga de página
4. **TC-04:** Accesibilidad web (axe-core)
5. **TC-05:** Estructura HTML semántica y validación W3C

---

## 2. Matriz de Resultados y Trazabilidad

| ID | Nombre del test | Herramienta / método | Momento 1 (pre-merge) | Issue asociado | Detectado | Momento 2 (retest) |
| :--- | :--- | :--- | :---: | :--- | :--- | :---: |
| | **TC-01** | Compatibilidad de escritorio | Playwright MCP (Chromium) | Sin resultados documentados | [#57](https://github.com/eternalnight04/HeladeriaVainell/issues/57) | 27/10/2026 (Momento 2) | **PARCIAL** ⚠️ |
| **TC-02** | Responsive en dispositivos móviles | Playwright MCP (viewports) | **FAIL** ❌ (iPhone y Samsung); iPad PASS | [#23](https://github.com/eternalnight04/HeladeriaVainell/issues/23) | 28/09/2026 (Momento 1) | **PASS** ✅ |
| **TC-03** | Performance y carga de página | Navigation / Resource Timing | Sin resultados documentados | [#57](https://github.com/eternalnight04/HeladeriaVainell/issues/57) | 27/10/2026 (Momento 2) | **MEDIDO** (sin criterio PASS/FAIL) |
| **TC-04** | Accesibilidad web (axe-core) | axe-core 4.7.2 / Playwright MCP | **FAIL** ❌ | [#24](https://github.com/eternalnight04/HeladeriaVainell/issues/24) | 28/09/2026 (Momento 1) | 0 violaciones; 2 reglas **INCOMPLETAS** ⚠️ |
| **TC-05** | HTML semántico y validación W3C | Playwright MCP / Nu Validator | **FAIL** ❌ | [#25](https://github.com/eternalnight04/HeladeriaVainell/issues/25) | 28/09/2026 (Momento 1) | Estructura sin hallazgos; W3C formal **PENDIENTE** ⚠️ |

**Notas:**
- TC-01: favicon.ico responde 404 (FAIL); autocomplete y título en observación; Firefox, Safari y Edge sin verificar.
- TC-03: se registró el favicon 404 y que `logo_vainell.png` (≈2,5 MB) y `capitan-helado-reboot.png` (≈1,6 MB) son los recursos más pesados.
- TC-04: quedan pendientes de revisión manual las reglas `aria-allowed-attr` y `color-contrast`.
- Los resultados del Momento 1 de TC-04 y TC-05 se toman de los issues #24 y #25; los archivos de test case no conservan las mediciones originales.

---

## 3. Issues Registrados en GitHub

Los issues #23, #24 y #25 fueron abiertos por `lautarochavez14` el 28/09/2026 (Momento 1) y hoy figuran cerrados. El issue #57 se registró el 27/10/2026 por `britezacostaalexis-pixel` (Momento 2) y hoy figura cerrado.

| Issue | Título | Test case | Detectado | Estado |
| :--- | :--- | :---: | :--- | :---: |
| [#23](https://github.com/eternalnight04/HeladeriaVainell/issues/23) | [BUG] Desbordamiento horizontal (overflow) en versión mobile por imagen hero | TC-02 | 28/09/2026 (Momento 1) | Cerrado |
| [#24](https://github.com/eternalnight04/HeladeriaVainell/issues/24) | [BUG] Estructura de lista de definición invalida (regla dlitem) en sección de características | TC-04 | 28/09/2026 (Momento 1) | Cerrado |
| [#25](https://github.com/eternalnight04/HeladeriaVainell/issues/25) | [BUG] Errores de validación HTML W3C, marcado sintáctico e incorrecta estructura de footer | TC-05 | 28/09/2026 (Momento 1) | Cerrado |
| [#57](https://github.com/eternalnight04/HeladeriaVainell/issues/57) | [BUG] Error 404 al solicitar favicon.ico (el sitio no tiene favicon) | TC-01, TC-03 (también observado en TC-04 y TC-05) | 27/10/2026 (Momento 2) | Abierto |

---

## 4. Detalle de Archivos de Test Cases

Los reportes detallados y las evidencias están en `docs/04-testing/`:

- [test-case-1.md](test-case-1.md) — Compatibilidad de escritorio
- [test-case-2.md](test-case-2.md) — Responsive en dispositivos móviles
- [test-case-3.md](test-case-3.md) — Performance y carga de página
- [test-case-4.md](test-case-4.md) — Accesibilidad web (axe-core)
- [test-case-5.md](test-case-5.md) — HTML semántico y W3C

---

## 5. Estado Actual y Próximos Pasos

El Momento 2 (retest post-merge) ya fue ejecutado. Pendientes:
1. TC-01: verificar Firefox, Safari y Edge; resolver el favicon 404 y revisar `autocomplete` y el título esperado.
2. TC-04: revisión manual de `aria-allowed-attr` y `color-contrast`.
3. TC-05: validar el HTML con Nu HTML Checker.
4. Decidir si el favicon 404 y las imágenes pesadas se registran como issues.