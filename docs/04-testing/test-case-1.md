# Test Case 1 — Compatibilidad de escritorio

- **Momento de ejecución:** Momento 1 (Testing pre-merge)
- **URL de prueba:** `http://127.0.0.1:3000/index.html?vscode-livepreview=true`
- **Herramienta utilizada:** **Playwright MCP** (`@playwright/mcp`) desde GitHub Copilot Agent Mode.

---

## Objetivo

Verificar que la página web de Heladería Vainell se visualice y funcione correctamente en los principales navegadores de escritorio (Chrome, Firefox, Safari y Edge).

---

## Alcance y Criterios de Verificación

Se evaluará la página sobre los siguientes componentes principales:

- Carga correcta de la página y título `"Heladeria Vainell"`.
- Visibilidad e integridad de la navegación principal.
- Renderizado de la sección principal (*hero section*).
- Visibilidad del catálogo de productos y formulario.
- Ausencia de errores de consola o bloqueos de interfaz.

---

## Prompt Utilizado en Copilot Agent Mode

```text
Usa Playwright MCP para realizar una prueba de compatibilidad de escritorio sobre la aplicación local de Heladería Vainell.

URL:
[http://127.0.0.1:3000/index.html?vscode-livepreview=true](http://127.0.0.1:3000/index.html?vscode-livepreview=true)

Verifica la página en Chrome, Firefox, Safari y Edge.

Para cada navegador comprueba:
- que la página cargue correctamente;
- que el título sea "Heladeria Vainell";
- que la navegación, hero section, catálogo y formulario sean visibles;
- que no haya errores que impidan utilizar la página.

Registra los resultados de cada navegador y toma capturas de pantalla como evidencia.

No modifiques ningún archivo del proyecto.