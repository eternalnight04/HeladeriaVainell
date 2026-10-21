# Test Case 4 — Accesibilidad Web (axe-core)

- **Momento de ejecución:** Momento 1 (Testing pre-merge)
- **URL de prueba:** `http://localhost:3000`
- **Herramienta utilizada:** **Playwright MCP** (`@playwright/mcp`) con inyección automatizada del motor de auditoría **axe-core 4.7.2**.
- **Responsable:** Lautaro Chavez
- **Rama:** `feature/doc-qa-tester-add-test-cases`

---

## 1. Objetivo

Garantizar la accesibilidad web (WCAG) en la página de Heladería Vainell evaluando la semántica de la interfaz, el comportamiento para lectores de pantalla y la estructura de elementos interactivos mediante auditoría automatizada con `axe-core`.

---

## 2. Prompt Utilizado en Copilot Agent Mode

```text
Usa Playwright MCP para realizar la auditoría del Test Case 4: Accesibilidad Web en la aplicación local de Heladería Vainell.

URL:
http://localhost:3000

Instrucciones:
1. Abre la página en http://localhost:3000.
2. Inyecta la librería axe-core en la página.
3. Corre axe.run() y analiza los resultados.
4. Reporta el número de violaciones de accesibilidad encontradas agrupadas por nivel de impacto e indica los elementos HTML afectados.
5. Si encuentras violaciones críticas o graves, usa GitHub MCP para registrar un issue de tipo bug.
6. Toma una captura de pantalla como evidencia.

No modifiques ningún archivo del proyecto.