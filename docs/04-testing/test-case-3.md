# Test Case 3 — Performance y Carga de Página

- **Momento de ejecución:** Momento 1 (Testing pre-merge)
- **URL de prueba:** `http://localhost:3000/`
- **Herramienta utilizada:** **Playwright MCP** (`@playwright/mcp`) mediante la evaluación de la **Performance API** del navegador (`window.performance`).
- **Responsable:** Lautaro Chavez
- **Rama:** `feature/doc-qa-tester-add-test-cases`

---

## 1. Objetivo

Evaluar la velocidad de respuesta, tiempos de renderizado y el impacto de la carga de recursos de la página web de Heladería Vainell midiendo las métricas obtenidas por la Performance API del navegador en un estado completo de carga (`document.readyState = 'complete'`).

---

## 2. Prompt Utilizado en Copilot Agent Mode

```text
Usa Playwright MCP para realizar la auditoría del Test Case 3: Performance y Carga de la aplicación local de Heladería Vainell.

URL:
http://localhost:3000/

Instrucciones de prueba:
1. Abre la página usando Playwright MCP.
2. Inyecta y ejecuta un script de evaluación en el navegador usando la Performance API (`window.performance.getEntriesByType('navigation')[0]` y `window.performance.getEntriesByType('resource')`).
3. Mide y extrae los siguientes indicadores:
   - TTFB (Time to First Byte / responseStart - requestStart).
   - DomContentLoaded (domContentLoadedEventEnd - fetchStart).
   - Tiempo de carga total (loadEventEnd - fetchStart).
   - Lista los recursos/archivos (imágenes, CSS o JS) que hayan tardado más tiempo en cargar o de mayor peso.
4. Toma una captura de pantalla del estado final cargado como evidencia.

Registra todas las métricas obtenidas con precisión. No modifiques ningún archivo del proyecto.