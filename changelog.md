# Changelog

Este archivo se actualiza con cada Pull Request para registrar avances y correcciones.

---

# [Unreleased]

---

# [Release - Actividad Obligatoria Nº1] - 2026-08-31

## Added

- [feature/frontend-add-html-structure] Se agregaron los códigos html, marcas de donde deben ir los css y javascrip. PR: [#12](https://github.com/eternalnight04/HeladeriaVainell/pull/12) - @britezacostaalexis-pixel (Desarrollador Fronted)

- [feature/coordinador-setup-repo-and-pages] Se agregaron las carpetas y los archivos correspondientes para asegurar la estructura del proyecto. Se agregó un changelog, plan.md con las especificaciones que debe seguir el proyecto y un archivo README.md con la información del mismo. PR: [#2](https://github.com/eternalnight04/HeladeriaVainell/pull/2) - @eternalnight04 (Coordinador / DevOps)

- [feature/ia-add-prompts-1-to-5] Se agregaron los archivos de prompts e IA. PR: [#4](https://github.com/eternalnight04/HeladeriaVainell/pull/4) - @lautarochavez14 (Especialista en IA y Prompt Engineering)

- [feature/ia-add-prompts-1-to-5] Se hicieron pequeñas correcciones en los archivos de prompts. PR: [#5](https://github.com/eternalnight04/HeladeriaVainell/pull/5) - @lautarochavez14 (Especialista en IA y Prompt Engineering)

*Nota: La PR #5 no se pudo mergear debido a problemas con cambios en la base, por lo que los cambios fueron trasladados a la PR #9 para que se pueda mergear sin complicaciones.*

- [feature/doc-ux-add-readme-and-mockup] Se agregaron las carpetas y los archivos correspondientes para el mockup, incluyendo un índice a todas sus características. También se actualizó README.md para incluir el link al mockup. PR: [#6](https://github.com/eternalnight04/HeladeriaVainell/pull/6) - @britezacostaalexis-pixel (Documentador / Diseñador UX)

- [fix/correcciones-archivos-1] Se agregó el archivo index.html con el código fuente de la página, además de que se agregaron los cambios hechos en la PR #5 a esta. PR: [#9](https://github.com/eternalnight04/HeladeriaVainell/pull/9) - @eternalnight04 (Coordinador / DevOps)

- [feature/ia-add-prompts-1-to-5-copy] Se trasladaron los nuevos cambios de la PR #5 a esta nueva PR debido a problemas de merge. PR: [#13](https://github.com/eternalnight04/HeladeriaVainell/pull/13) - @eternalnight04 (Coordinador / DevOps)

## Changed

- [fix/desarrollo-frontend-ux-correccion-1] RC9,10,11,12,13,14,15. PR: [#18](https://github.com/eternalnight04/HeladeriaVainell/pull/18) - @britezacostaalexis-pixel (Documentador / Diseñador UX-Frontend)

- [fix/plan-sesion] Se agregó una nueva función para inicio de sesión y creación de cuentas (como un concepto para la página), debido a esto, se actualizaron plan.md y README.md. PR: [#3](https://github.com/eternalnight04/HeladeriaVainell/pull/3) - @eternalnight04 (Coordinador / DevOps)

## Fixed

- [fix/correcciones-act1]Fix/correcciones act1. PR: [#28](https://github.com/eternalnight04/HeladeriaVainell/pull/28) - @britezacostaalexis-pixel (Documentador / Diseñador UX-fronted)

- [fix/correcciones-rc-act-1] Correcciones de solicitudes de cambio. PR: [#27](https://github.com/eternalnight04/HeladeriaVainell/pull/27) - @britezacostaalexis-pixel (Documentador / Diseñador UX-fronted)

- [release/actividad-obligatoria-1] Commit directo: "agregado nombre de ia utilizada en cuarto prompt" (17/09/2026). Commit: [`c3b2790`](https://github.com/eternalnight04/HeladeriaVainell/commit/c3b2790b4fd57b8708bf8b0e11c1791fad8a1e86) (fuera de la PR #15; la PR asociada [#14](https://github.com/eternalnight04/HeladeriaVainell/pull/14) quedó cerrada sin fusionar) - @eternalnight04 (Coordinador / DevOps)

- [fix/ia-correcciones-release] Fix/ia correcciones release: se agregó la spec de IA y las decisiones SDD, se documentaron los prompts 1 a 5 con la comparativa de modelos, se corrigió el modelo del prompt 4, se separaron los criterios de aceptación por etapa y se corrigieron la comparativa y los resultados de prompts. PR: [#20](https://github.com/eternalnight04/HeladeriaVainell/pull/20) - @lautarochavez14 (Especialista en IA y Prompt Engineering)

- [fix/ia-correcciones-release] Fix/ia correcciones release: se corrigieron los modelos de IA indicados en los prompts. PR: [#22](https://github.com/eternalnight04/HeladeriaVainell/pull/22) - @lautarochavez14 (Especialista en IA y Prompt Engineering)

- [fix/devops-correcciones-1] Se realizaron correcciones en las entradas del changelog y se eliminó una sección no solicitada del archivo spec-devops.md, de acuerdo a los Request Changes planteados. PR: [#16](https://github.com/eternalnight04/HeladeriaVainell/pull/16) - @eternalnight04 (Coordinador / DevOps)

- [fix/devops-correcciones-2] Se agregó la sección de "Criterios de Aceptacion" para el archivo spec-devops.md. PR: [#17](https://github.com/eternalnight04/HeladeriaVainell/pull/17) - @eternalnight04 (Coordinador / DevOps)

---

# Cómo usar este archivo

- Para cada PR, simplemente agregar una línea breve en la sección correspondiente a su cambio (Added, Changed, Fixed).
- No es necesario escribir párrafos, sólo una frase corta + link a PR y responsable con rol.
- Al hacer la entrega final, copiar todo lo que está en **[Unreleased]** a una nueva sección con la fecha y nombre de la entrega (release).
- Mantener el órden y formato para facilitar el seguimiento.