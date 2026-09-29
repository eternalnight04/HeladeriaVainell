# Test Case 2 — Responsive en dispositivos móviles

- **Momento de ejecución:** Momento 1 (Testing pre-merge)
- **URL de prueba:** `http://localhost:3000`
- **Herramienta utilizada:** **Playwright MCP** (`@playwright/mcp`) con emulación de viewport
- **Responsable:** Lautaro Chavez
- **Rama:** `feature/doc-qa-tester-add-test-cases`

---

## 1. Objetivo

Verificar la adaptación responsive del sitio web de Heladería Vainell en diferentes dispositivos móviles (iPhone, Samsung Galaxy e iPad), detectando desbordamientos horizontales, elementos fuera de pantalla y problemas de interacción visual o funcional.

---

## 2. Prompt Utilizado en Copilot Agent Mode

> Ejecutá el Test Case 2 de responsive definido en `docs/03-specs/actividad-obligatoria-2/spec-qa.md`.
>
> Probá la página en iPhone, Samsung Galaxy e iPad.
>
> Para cada viewport verificá que la página cargue correctamente, que no exista scroll horizontal, que los elementos principales estén dentro del viewport y que los controles del formulario sean utilizables.
>
> No modifiques ningún archivo del proyecto.

---

## 3. Resultados de la Ejecución (Momento 1)

### iPhone (Mobile - Viewport Small)
- **Resultado:** **FAIL ❌**
- **Hallazgos:**
  - Se detectó desbordamiento (overflow) horizontal no deseado.
  - La imagen principal del hero section sobresale aproximadamente **58 px** del área visible.
  - Los demás contenedores principales y el formulario se adaptan correctamente al ancho del dispositivo.
  - Los controles e inputs del formulario son interactivos y utilizables.

### Samsung Galaxy (Mobile - Viewport Medium)
- **Resultado:** **FAIL ❌**
- **Viewport:** `360 × 800 CSS px`
- **Ancho del documento:** `449 px`
- **Overflow horizontal:** `89 px`
- **Hallazgos:**
  - La imagen hero ocupa un rango de `x=48–448`, sobresaliendo aproximadamente **88 px** a la derecha del canvas.
  - El header, la navegación, el catálogo, el formulario y el footer se mantienen dentro del ancho visible.
  - La funcionalidad de los formularios se encuentra operativa.

### iPad (Tablet - Viewport Large)
- **Resultado:** **PASS ✅**
- **Viewport:** `768 × 1024 CSS px`
- **Hallazgos:**
  - La maquetación y la imagen del hero se ajustan correctamente sin provocar scroll horizontal.
  - Todos los bloques principales (navegación, catálogo, formulario) se visualizan de forma fluida.

---

## 4. Evidencias

![Evidencia Test Case 2 - Responsive](evidencia-test-case-2.png)

*Figura 1: Captura de pantalla evidenciando el scroll horizontal provocado por el overflow de la imagen en la sección Hero.*

---

## 5. Issues Generados (GitHub MCP)

- **Issue Creado:** `#1` (o el número correspondiente asignado por GitHub)
- **Título:** `[BUG] Desbordamiento horizontal (overflow) en versión mobile por imagen de hero section`
- **Etiqueta:** `bug` / `responsive`
- **Notificado a:** Especialista en Responsive / Desarrollador Frontend

> **Justificación:** Se registró como bug crítico de responsive ya que romper la cuadrícula del viewport con un scroll horizontal involuntario degrada fuertemente la experiencia de usuario (UX) en dispositivos móviles pequeños y medianos.

---

## 6. Conclusión

**Prueba completada con hallazgos (FAIL).**

Se confirmó que la estructura general responsive funciona correctamente salvo por la imagen contenedora de la sección **Hero**, la cual carece de reglas CSS adaptativas (`max-width: 100%` / `height: auto`), generando scroll horizontal no deseado en dispositivos iPhone y Samsung Galaxy. Se procede a notificar al Especialista en Responsive para su corrección antes de realizar el merge a `develop`.