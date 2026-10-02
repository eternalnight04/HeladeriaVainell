# Changelog

Este archivo se actualiza con cada Pull Request para registrar avances y correcciones.

---

# [Unreleased]

---

# [Release - Actividad Obligatoria Nº1] - 2026-08-31

## Added

- [feature/coordinador-setup-repo-and-pages] Se agregaron los archivos y carpetas necesarias para el proyecto. Algunos deben ser completados por los demás roles según corresponda.
Al mismo tiempo, se agregó un changelog, un archivo index.html vacío, una carpeta con plantillas para Pull Requests, una carpeta para la maqueta y los prompts, un archivo plan.md con las especificaciones del proyecto y un readme con la información básica del proyecto y sus integrantes. PR: [#2](https://github.com/eternalnight04/HeladeriaVainell/pull/2) - @eternalnight04 (Coordinador / DevOps)

- [feature/ia-add-prompts-1-to-5] Agrega especificaciones de IA y decisiones SDD. PR: [#4](https://github.com/eternalnight04/HeladeriaVainell/pull/4) - @lautarochavez14 (Especialista en IA y Prompt Engineering)

- [feature/ia-add-prompts-1-to-5] Se hicieron pequeñas correcciones en los archivos de prompts. PR: [#5](https://github.com/eternalnight04/HeladeriaVainell/pull/5) - @lautarochavez14 (Especialista en IA y Prompt Engineering)

*Nota: La PR #5 no se pudo mergear debido a problemas con cambios en la base, por lo que los cambios fueron trasladados a la PR #9 para que se pueda mergear sin complicaciones.*

- [feature/doc-ux-add-readme-and-mockup] Se generó el README.md del proyecto utilizando GitHub Copilot en modo Agente, tomando como contexto la consigna y el plan.md. El resultado fue revisado, corregido y completado manualmente.
Además, como parte del flujo de UX previo al diseño en Figma:
Se le pasó el plan.md a Copilot Agente para obtener sugerencias de layout, estructura de secciones y jerarquía visual. Se documentaron en docs/specs/spec-ux.md las consultas realizadas a la IA, las sugerencias obtenidas, y cuáles se usaron y cuáles se descartaron. Se diseñó el mockup final en Figma y se subió a docs/01-mockup/. Se incluyó el enlace al mockup dentro del README.md para que el equipo de Frontend pueda usarlo y conectar el servidor MCP. PR: [#6](https://github.com/eternalnight04/HeladeriaVainell/pull/6) - @britezacostaalexis-pixel (Documentador / Diseñador UX)

- [fix/correcciones-archivos-1] Se completo el archivo index con el codigo fuente de la pagina. PR: [#9](https://github.com/eternalnight04/HeladeriaVainell/pull/9) - @eternalnight04 (Coordinador / DevOps)

- [feature/frontend-add-html-structure] Se generó la estructura HTML5 inicial del sitio (index.html) a partir del mockup diseñado en Figma, utilizando el servidor MCP de Figma (Dev Mode) conectado a VS Code junto con GitHub Copilot en modo Agente. PR: [#12](https://github.com/eternalnight04/HeladeriaVainell/pull/12) - @britezacostaalexis-pixel (Desarrollador Frontend)

- [feature/ia-add-prompts-1-to-5-copy] Correcciones de archivos de prompts. Se corrigieron y modificaron los archivos del prompt 1 al 5. Al mismo tiempo que se agregaron imágenes de estos. PR: [#13](https://github.com/eternalnight04/HeladeriaVainell/pull/13) - @eternalnight04 (Coordinador / DevOps)

## Changed

- [fix/desarrollo-frontend-ux-correccion-1] RC 9, 10, 11, 12, 13, 14, 15. PR: [#18](https://github.com/eternalnight04/HeladeriaVainell/pull/18) - @britezacostaalexis-pixel (Documentador / Diseñador UX / Desarrollador Frontend)

- [fix/plan-sesion] Fix: Se agregó una nueva función al plan. Se agregó el concepto de un sistema de inicio de sesión y creación de usuarios para la página. También se actualizó el archivo README. Esto busca contribuir a resolver el Issue #1. PR: [#3](https://github.com/eternalnight04/HeladeriaVainell/pull/3) - @eternalnight04 (Coordinador / DevOps)

## Fixed

- [fix/Rc-act-1] RC2,RC7,RC39 corregidos. Se realizo la corrección de las siguientes RC 2, 7 y 39, con lo que solicito el docente. PR: [#29](https://github.com/eternalnight04/HeladeriaVainell/pull/29) - @britezacostaalexis-pixel (Documentador / Diseñador UX / Desarrollador Frontend)

- [fix/correcciones-act1] Fix/correcciones act1. Se realizo las RC 39,RC 12, RC 14, RC 43 y RC 2. PR: [#28](https://github.com/eternalnight04/HeladeriaVainell/pull/28) - @britezacostaalexis-pixel (Documentador / Diseñador UX / Desarrollador Frontend)

- [fix/correcciones-rc-act-1] correcciónes de request change. Este PR responde a las observaciones del revisor sobre spec, changelog e imágenes del HTML. PR: [#27](https://github.com/eternalnight04/HeladeriaVainell/pull/27) - @britezacostaalexis-pixel (Documentador / Diseñador UX / Desarrollador Frontend)

- [release/actividad-obligatoria-1] Commit directo: "agregado nombre de ia utilizada en cuarto prompt" (17/09/2026). Commit: [`c3b2790`](https://github.com/eternalnight04/HeladeriaVainell/commit/c3b2790b4fd57b8708bf8b0e11c1791fad8a1e86) - @eternalnight04 (Coordinador / DevOps)

- [fix/ia-correcciones-release] Fix/ia correcciones release: se agregó la spec de IA y las decisiones SDD, se documentaron los prompts 1 a 5 con la comparativa de modelos, se corrigió el modelo del prompt 4, se separaron los criterios de aceptación por etapa y se corrigieron la comparativa y los resultados de prompts. PR: [#20](https://github.com/eternalnight04/HeladeriaVainell/pull/20) - @lautarochavez14 (Especialista en IA y Prompt Engineering)

- [fix/ia-correcciones-release] Fix/ia correcciones release. PR: [#22](https://github.com/eternalnight04/HeladeriaVainell/pull/22) - @lautarochavez14 (Especialista en IA y Prompt Engineering)

- [fix/devops-correcciones-1] Correcciones del changelog. Se corrigieron el changelog y el archivo spec-devops.md según los request changes solicitados. PR: [#16](https://github.com/eternalnight04/HeladeriaVainell/pull/16) - @eternalnight04 (Coordinador / DevOps)

- [fix/devops-correcciones-2] Fix - Corrección archivo DevOps. Se agregó la sección "Criterios de Aceptación" del archivo spec-devops md. Además de incluir pequeñas correcciones en algunas entradas del changelog. PR: [#17](https://github.com/eternalnight04/HeladeriaVainell/pull/17) - @eternalnight04 (Coordinador / DevOps)

- [fix/ia-correcciones-release] docs: corrige textos de prompts 1 a 5. PR: [#30](https://github.com/eternalnight04/HeladeriaVainell/pull/30) - @lautarochavez14 (Especialista en IA y Prompt Engineering)

- [fix/correcciones-2] Correcciones de Request Changes varios. Se realizaron varios RC con respecto a prompts, el changelog, el sdd-decisions y el index. PR: [#32](https://github.com/eternalnight04/HeladeriaVainell/pull/32) - @eternalnight04 (Coordinador / DevOps)

---

# Cómo usar este archivo

- Para cada PR, simplemente agregar una línea breve en la sección correspondiente a su cambio (Added, Changed, Fixed).
- No es necesario escribir párrafos, sólo una frase corta + link a PR y responsable con rol.
- Al hacer la entrega final, copiar todo lo que está en **[Unreleased]** a una nueva sección con la fecha y nombre de la entrega (release).
- Mantener el órden y formato para facilitar el seguimiento.