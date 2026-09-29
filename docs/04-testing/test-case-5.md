# Test Case 5 — Validación de Estructura HTML Semántica y W3C

- **Momento de ejecución:** Momento 1 (Testing pre-merge)
- **URL de prueba:** `http://localhost:3000`
- **Herramienta utilizada:** **Playwright MCP** (`@playwright/mcp`) con inspección de *accessibility snapshot* y evaluación W3C.
- **Responsable:** Lautaro Chavez
- **Rama:** `feature/doc-qa-tester-add-test-cases`

---

## 1. Objetivo

Verificar la jerarquía semántica del árbol de accesibilidad y validar la conformidad sintáctica del código HTML del sitio web de Heladería Vainell frente a los estándares HTML5 definidos por la W3C.

---

## 2. Prompt Utilizado en Copilot Agent Mode

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

No modifiques ningún archivo del proyecto.