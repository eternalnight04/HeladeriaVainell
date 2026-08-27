# Heladeria Vainell - Plan

---

## 1. Descripción general del proyecto

**Vainell** es una página web interactiva para una heladería ficticia, cuyo objetivo es simular el proceso de pedido de helados, ya sea para **entrega a domicilio (delivery)** o para **retiro en el local (take away / pickup)**.

El proyecto se desarrolla de forma incremental a lo largo del cuatrimestre. Esta primera entrega (Actividad Obligatoria N°1) construye únicamente la **estructura base en HTML5**, sin estilos (CSS) ni comportamiento (JavaScript), dejando marcadores en el código para las funcionalidades que se incorporarán en las próximas entregas.

## 2. Problema que resuelve / propósito

Un cliente que quiere comprar helados de Vainell hoy solo puede hacerlo llamando por teléfono o yendo presencialmente al local, sin poder ver el catálogo de sabores y productos, ni elegir con anticipación la modalidad de entrega. Vainell busca resolver esto ofreciendo un **simulador de pedidos online**, que permita al usuario:

- Ver el catálogo de sabores, productos y precios.
- Elegir entre **delivery** o **retiro en local**.
- Completar sus datos y los del pedido a través de un formulario.
- Recibir información clara sobre el proceso de compra.

Como se trata de un **simulador**, el pedido no se procesa realmente (no hay pasarela de pago, ni conexión a una base de datos, ni notificación real al local): el objetivo es que el usuario reciba información de valor y una experiencia de flujo de compra realista, aunque el circuito no se complete de forma funcional en esta etapa del curso.

## 3. Alcance del simulador (consensuado por el equipo para la cursada)

**Incluido en el alcance del proyecto (a lo largo de las próximas entregas):**
- Catálogo de productos (helados por kilo, potes, palitos, tortas heladas, toppings).
- Selección de modalidad de compra: delivery o retiro en local.
- Formulario de pedido (datos del cliente, dirección si es delivery, horario de retiro si es en local, medio de pago declarado).
- Cálculo simulado de costo de envío según zona (a incorporar con JavaScript en entregas futuras).
- Confirmación visual del pedido (sin backend real).

**Fuera de alcance (no se resuelve realmente):**
- Procesamiento real de pagos.
- Persistencia de pedidos en una base de datos.
- Envío real de notificaciones (mail, WhatsApp, etc.) al local o al cliente.
- Sistema de usuarios con login/autenticación real.

## 4. Tecnologías utilizadas

| Etapa | Tecnología |
|---|---|
| Entrega 1 (actual) | HTML5 semántico |
| Próximas entregas | CSS3 (maquetación y diseño responsive) |
| Próximas entregas | JavaScript (interactividad, validaciones, cálculo de envío, simulación del pedido) |
| Gestión de proyecto | Git / GitHub (branch model, Pull Requests, Issues) |
| IA | GitHub Copilot (modo Agente), y otros modelos (ChatGPT, Gemini, Claude, etc.) para distintas tareas del proyecto |
| Diseño | Figma (mockup) + servidor MCP de Figma |

## 5. Requerimientos funcionales para esta entrega (Actividad Obligatoria N°1)

Extraídos y estructurados a partir de la consigna del profesor:

1. **Estructura HTML5**
   - Documento válido: `<!DOCTYPE html>`, `<head>` con `charset`, `viewport` y `title`, `<body>` con atributo `lang="es"`.
   - Etiquetas semánticas: `<header>`, `<main>`, `<footer>` y, según corresponda, `<nav>`, `<section>`, `<article>`, `<aside>`.
   - Contenido real de la heladería Vainell (nombre, presentación, propuesta de valor), no contenido genérico ni Lorem Ipsum.

2. **Elementos obligatorios en la página**
   - Título y párrafos descriptivos de Vainell y de su servicio.
   - Imágenes con atributo `alt` descriptivo (logo, productos, local).
   - Enlaces (`href`) de navegación interna y/o a redes sociales.
   - Al menos una lista (ordenada o desordenada) — por ejemplo, sabores disponibles.
   - Una tabla con `<th>`/`<td>` — por ejemplo, precios por tamaño/formato.
   - Un formulario con al menos 3 campos relevantes — el **formulario de pedido**, incluyendo como mínimo: nombre del cliente, modalidad de entrega (delivery / retiro en local) y datos asociados (dirección u horario de retiro).

3. **Maquetación CSS (no requerida aún)**
   - Dejar comentarios `<!-- CSS: ... -->` indicando dónde se aplicarán estilos en la próxima entrega (ej. sección hero, catálogo, formulario de pedido, footer).

4. **Interactividad JavaScript (no requerida aún)**
   - Dejar comentarios `<!-- JS: ... -->` indicando dónde se incorporará lógica interactiva futura: cálculo de costo de envío, validación del formulario de pedido, cambio dinámico de campos según modalidad elegida (delivery/local), simulación de confirmación del pedido.

5. **Documentación**
   - Comentarios claros en el HTML explicando estructura y elementos.
   - `README.md` con descripción del proyecto, objetivos, tecnologías, funcionalidades previstas, enlace al mockup y carátula del grupo.

6. **Especificación técnica (Spec-Driven Development)**
   - Cada rol redacta su `docs/03-specs/spec-[rol].md` **antes** de desarrollar, describiendo qué va a hacer, por qué y los criterios de aceptación, trazado contra este `plan.md`.

7. **IA y Prompt Engineering**
   - Documentar en `docs/02-prompts/` al menos 5 prompts reales (no ficticios) utilizados con modelos de IA distintos, que hayan aportado valor concreto al desarrollo de Vainell.

## 6. Estructura de la página (contenido esperado en `index.html`)

- **Header**: logo/nombre "Vainell", navegación (Inicio, Catálogo, Cómo pedir, Contacto).
- **Main**:
  - Sección de presentación (quiénes somos, propuesta de valor).
  - Sección de catálogo (lista de sabores y tabla de precios/formatos).
  - Sección "Cómo pedir" explicando delivery vs. retiro en local.
  - Formulario de pedido (nombre, contacto, modalidad de entrega, dirección/horario, comentarios).
- **Footer**: datos de contacto, horarios de atención, enlaces a redes sociales.

## 7. Criterios de aceptación de esta entrega

- [ ] El sitio se renderiza correctamente como HTML5 válido.
- [ ] Incluye todos los elementos obligatorios (título, párrafos, imágenes, enlaces, lista, tabla, formulario).
- [ ] El formulario contempla explícitamente la elección entre delivery y retiro en local.
- [ ] Usa etiquetas semánticas de forma pertinente.
- [ ] Contiene comentarios que documentan la estructura y marcan los puntos de futura integración de CSS y JS.
- [ ] Existe trazabilidad completa: `plan.md` → `docs/03-specs/spec-[rol].md` → Pull Request → `changelog.md`.
- [ ] README.md completo con carátula del grupo y enlaces requeridos.
- [ ] Al menos 5 prompts de IA documentados en `docs/02-prompts/`.

## 8. Referencias

- Este `plan.md` es la base para que el **Documentador/UX** diseñe el mockup y para que el **Especialista en IA** defina la aplicación de SDD en el equipo.
- Cada Pull Request debe justificar su cumplimiento contra los puntos declarados aquí.