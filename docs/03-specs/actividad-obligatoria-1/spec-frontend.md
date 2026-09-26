# spec-frontend.md — Desarrollador Frontend

**Proyecto:** Vainell
**Entrega:** Actividad Obligatoria N°1
**Rol:** Desarrollador Frontend
**Rama:** `feature/frontend-add-html-structure`

---

## 1. Qué se le solicitó a Copilot

Se conectó el servidor MCP de Figma (Dev Mode, remoto) a VS Code para que 
GitHub Copilot en modo Agente pudiera leer directamente el mockup diseñado 
en Figma.

El mockup se organizó previamente en 9 Frames independientes, uno por 
sección de la página (Header, Inicio, Características, Por qué Vainell, 
Catálogo, Cómo pedir, Pedido, Testimonios y Contacto), para poder 
trabajar la generación de código de forma ordenada, frame por frame, 
en lugar de pedir toda la página de una sola vez.

Para cada Frame, se le pidió a Copilot que:
- Analizara el diseño correspondiente a través del servidor MCP de Figma.
- Generara el fragmento de HTML5 semántico de esa sección específica 
  (título, párrafos, imágenes con atributo `alt`, enlaces, listas y 
  tablas donde correspondiera, y etiquetas semánticas como `header`, 
  `nav`, `main`, `section`, `footer`).
- No incluyera CSS ni JavaScript, y en su lugar dejara comentarios HTML 
  indicando en qué parte se aplicará el CSS y dónde se agregará el 
  JavaScript en etapas posteriores del proyecto.

---

## 2. Qué sugirió Copilot

Al leer cada Frame por separado, Copilot propuso ir generando la 
estructura como fragmentos de código independientes, correspondientes 
a cada sección del sitio:

1. Header fijo con logo, navegación y botón de acción principal ("Pedir ahora")
2. Hero section (Inicio) con título, subtítulo, botones de llamada a la 
   acción e imagen principal
3. Sección de características/estadísticas destacadas
4. Sección "¿Por qué Vainell?" con tarjetas de beneficios
5. Catálogo de productos con filtros por categoría y grilla de tarjetas
6. Sección "¿Cómo pedir?" con los pasos numerados
7. Formulario de pedido completo, con campos de datos y selector de 
   modalidad (Delivery / Retiro en local)
8. Sección de testimonios de clientes
9. Footer con datos de contacto, horarios y redes sociales


---

## 3. Qué decidí utilizar

- Se utilizaron los 9 fragmentos generados por Copilot, integrándolos en 
 un único archivo `index.html`, respetando el orden de las secciones tal 
 como fueron diseñadas en el mockup de Figma.Se modificaron leves partes de la  
 estructura general propuesta; se mantuvieron las etiquetas semánticas, 
 los atributos de accesibilidad
 sugeridos por Copilot, y los comentarios indicando dónde se aplicará el 
 CSS y el JavaScript en el futuro.

---

## 4. Qué se descartó

No se descartó contenido estructural de lo sugerido por Copilot. El 
único ajuste manual realizado fue de organización de donde debia ir cada estructura y frame del código en  el index, no 
del código HTML en sí, que se conservó tal como fue generado por 
Copilot a partir de cada Frame.