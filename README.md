# 🍦 Heladeria Vainell

---

## Datos Académicos

**Carrera:** Tecnicatura Universitaria en Programación de Sistemas

**Materia:** Programación Web I

**Cuatrimestre:** 2do Cuatrimestre / 2026

**Profesor:** Lic. Matías Velasquez

---

## Descripción

**Vainell** es una página web interactiva desarrollada para una heladería ficticia, que permite simular la realización de pedidos mediante entrega a domicilio (delivery) o retiro en el local (take away), además de ofrecer una simulación de cuenta de usuario.

El proyecto se desarrolla progresivamente a lo largo del cuatrimestre. La primera entrega incorporó la estructura semántica con HTML5, la segunda agregó estilos CSS3 y diseño responsive, y la tercera incorpora lógica de negocio e interactividad mediante JavaScript, junto con diagramas de actividades y pruebas automatizadas con Jasmine.

Vainell es un simulador académico: no procesa pagos reales ni utiliza un backend o una base de datos para persistir información.

---

## Objetivos del proyecto

- Ofrecer un catálogo digital de los productos de Vainell (sabores, formatos y precios).
- Permitir al usuario elegir entre las dos modalidades de entrega: delivery o retiro en local.
- Simular el flujo completo de un pedido a través de un formulario, brindando información de valor sobre el proceso de compra.
- Ofrecer un sistema de inicio de sesión, donde, hipotéticamente, se podrían ganar puntos con cada compra para descuentos.
- Sentar una base de código sólida, documentada y escalable, que permita incorporar progresivamente estilos e interactividad en las próximas entregas.

> **Nota:** Vainell es un simulador, por lo que no procesa pagos reales ni persiste datos en una base de datos.

---

## Tecnologías utilizadas

- **HTML5** — estructura semántica.
- **CSS3** — maquetación y diseño responsive.
- **JavaScript** — lógica de negocio, funciones, validaciones y simulación de flujos.
- **PlantUML** — diagramas de actividades.
- **Jasmine** — pruebas automatizadas de JavaScript.
- **Git / GitHub** — gestión de ramas, Pull Requests, Issues y GitHub Projects.
- **GitHub Pages** — publicación del sitio.
- **IA generativa** — GitHub Copilot en modo Agente y otros modelos utilizados durante el desarrollo.
- **Figma** — diseño y documentación del mockup.
---

## Funcionalidades previstas

- Catálogo de sabores y productos (potes, kilos, palitos y tortas heladas).
- Selección de modalidad de entrega: delivery o retiro en local.
- Formulario de pedido con datos del cliente.
- Simulación del cálculo del costo de envío.
- Simulación de registro e inicio de sesión.
- Implementación de cuatro flujos principales de negocio mediante JavaScript.
- Menú interactivo mediante `prompt()`.
- Validación de datos y presentación de resultados mediante `alert()` y/o `console.log()`.
- Diagramas de actividades desarrollados con PlantUML.
- Pruebas automatizadas de los flujos mediante Jasmine.

---

## Maqueta de diseño web

El mockup del proyecto fue desarrollado en Figma y toma como referencia los requerimientos funcionales definidos en [plan.md](plan.md). La propuesta visual busca reflejar una identidad moderna, fresca y amigable para una heladería.

---

## Documentación

-  Plan del proyecto: [plan.md](plan.md)
-  [`docs/01-mockup/actividad-obligatoria-1/`](./docs/01-mockup/actividad-obligatoria-1/01-diseño-inicial-inicio.png) — Ver en Figma: https://www.figma.com/make/8UBb5SIznSz81a6y57nQ7v/Ice-Cream-Shop?t=MiOriddmlnQAfXnL-20&fullscreen=1
- [`docs/01-mockup/actividad-obligatoria-2/`](docs/01-mockup/actividad-obligatoria-2/01-diseño-con-estilos-inicio.png) - Ver en Figma: https://www.figma.com/make/Si4hHXYePCegrXfCQ5TNf3/Heladeria-Vainell-Segundo-Mockup?fullscreen=1&t=tJRtkXQdmbSxJK3J-1&code-node-id=0-6
-  Prompts de IA: [docs/02-prompts/prompts.md](docs/02-prompts/prompts.md)
-  Changelog: [changelog.md](changelog.md)
-  Especificaciones técnicas: [docs/03-specs](docs/03-specs)
- Especificación del Coordinador / DevOps: [spec-devops.md](docs/03-specs/actividad-obligatoria-3/spec-devops.md)
- Diagramas de actividades: [diagramas-doc.md](docs/05-diagramas/01-diagrama-de-actividades/diagramas-doc.md)
- Documentación de testing JavaScript: [testing-doc.md](js/test/testing-doc.md)

---

## Integrantes del Grupo

| Nombre completo | N° de Matrícula | Usuario GitHub | Rol en esta entrega |
|---|---|---|---|
| Milenka Vila | 157550 | @eternalnight04 | Arquitecto de Diagramas de Actividades |
| Alexis Matias Britez Acosta | 158100 | @britezacostaalexis-pixel | Desarrollador JavaScript |
| Lautaro Chavez | 151222 | @lautarochavez14 | Coordinador / DevOps |