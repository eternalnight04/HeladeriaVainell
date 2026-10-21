# Informe de Estrategia y Ejecución de QA Testing

- **Proyecto:** Heladería Vainell — Sitio Web Promocional
- **Documento:** Informe Integrado de QA Testing (Momento 1)
- **Responsable de QA:** Lautaro Chavez
- **Rama de Trabajo:** `feature/doc-qa-tester-add-test-cases`
- **Fecha de Ejecución:** Septiembre 2026

---

## 1. Introducción y Estrategia de Testing

Este informe documenta los resultados de las pruebas de calidad (QA) realizadas sobre el sitio web promocional de **Heladería Vainell** utilizando **Playwright MCP** (`@playwright/mcp`) en combinación con la suite de auditorías automatizadas de Lighthouse y Axe Core.

La estrategia de testing adoptada cubre cinco pilares clave de calidad digital:
1. **Accesibilidad Web (WCAG 2.1 AA)**
2. **Atributos ALT e Imágenes Accesibles**
3. **Formulario de Contacto e Interactividad**
4. **Performance, SEO y Best Practices (Lighthouse)**
5. **Estructura HTML Semántica y Validación W3C**

---

## 2. Matriz de Resultados Generales (Momento 1)

| ID Test Case | Nombre del Test | Herramienta / Método | Estado | Issue Asociado |
| :--- | :--- | :--- | :---: | :---: |
| **TC-01** | Auditoría de Accesibilidad (WCAG 2.1 AA) | Axe Core / Playwright MCP | **FAIL** ❌ | `#21` |
| **TC-02** | Validación de Atributos ALT en Imágenes | Inspección DOM / Playwright MCP | **PASS** ✅ | N/A |
| **TC-03** | Funcionalidad del Formulario de Contacto | Interacción DOM / Playwright MCP | **FAIL** ❌ | `#22`, `#23` |
| **TC-04** | Auditoría Lighthouse (Performance, SEO, BP) | Lighthouse / Playwright MCP | **FAIL** ❌ | `#24` |
| **TC-05** | Validación HTML Semántico y W3C | Nu Validator W3C / Playwright MCP | **FAIL** ❌ | `#25` |

---

## 3. Resumen de Issues Registrados en GitHub

A partir de las pruebas ejecutadas en el Momento 1, se abrieron los siguientes tickets de corrección para el Desarrollador Frontend:

1. **Issue `#21` [BUG - Accesibilidad]:** Contraste insuficiente de color en textos y componentes interactivos según WCAG AA.
2. **Issue `#22` [BUG - Formulario]:** Ausencia de validaciones de formato HTML5 (email sin validación de sintaxis, campos obligatorios sin atributo `required`).
3. **Issue `#23` [BUG - Formulario]:** Falta de redirección / respuesta tras el envío exitoso del formulario (`mailto:` o endpoint AJAX).
4. **Issue `#24` [BUG - Performance/SEO]:** Métricas deficientes de Performance/SEO y recursos de imagen pesados sin optimización.
5. **Issue `#25` [BUG - HTML/W3C]:** 21 errores de validación W3C, marcado sintáctico (`</d1>`), idioma `lang="en"` erróneo y `<footer>` anidado en `<main>`.

---

## 4. Detalle de Archivos de Test Cases

Los reportes detallados y con evidencias de cada caso de prueba se encuentran disponibles en la carpeta `docs/04-testing/`:

- `docs/04-testing/test-case-1.md`
- `docs/04-testing/test-case-2.md`
- `docs/04-testing/test-case-3.md`
- `docs/04-testing/test-case-4.md`
- `docs/04-testing/test-case-5.md`

---

## 5. Próximos Pasos (Momento 2: Post-Merge & Retest)

Una vez que el equipo de desarrollo resuelva las incidencias reportadas (Issues `#21` a `#25`) y realice el merge a la rama principal:
1. Re-ejecutar la suite completa de Test Cases (TC-01 al TC-05) utilizando los mismos prompts de Playwright MCP.
2. Verificar el cierre efectivo de los tickets en GitHub.
3. Actualizar la matriz de trazabilidad al estado final **PASS** ✅.