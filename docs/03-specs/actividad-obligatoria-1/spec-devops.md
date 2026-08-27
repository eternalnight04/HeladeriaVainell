# spec-devops.md — Coordinador / DevOps

**Proyecto:** Vainell
**Entrega:** Actividad Obligatoria N°1
**Rol:** Coordinador / DevOps
**Rama:** `feature/coordinador-setup-repo-and-pages`

---

## 1. Qué se va a hacer

Configurar la infraestructura base del repositorio de Vainell en GitHub y generar el documento de requerimientos funcionales (`plan.md`) que guiará el resto del desarrollo. Concretamente:

1. Crear el repositorio público `HeladeriaVainell` en GitHub.
2. Configurar las ramas `master` y `develop`, con reglas de protección en ambas (mínimo 1 revisor requerido, push directo bloqueado).
3. Invitar como colaboradores al profesor (`MVelasquez98`) y a todos los integrantes del grupo.
4. Realizar el commit inicial con la estructura base de carpetas (según sección 4.1 de la consigna) e `index.html` vacío.
5. Usando **GitHub Copilot en modo Agente**, generar `plan.md` en la raíz del repositorio a partir de la consigna de la actividad y de las decisiones de alcance del simulador consensuadas con el equipo (heladería Vainell, con pedidos por delivery o retiro en local).
6. Configurar el template de Pull Request (`.github/PULL_REQUEST_TEMPLATE/`) para las ramas `feature` y `release`, de uso obligatorio para todo el equipo.
7. Administrar las Pull Requests del proyecto: asegurar que cada una tenga al menos una revisión aprobada antes del merge, y realizar como mínimo 4 code reviews asistidos con IA, evaluando el cumplimiento de los requerimientos declarados en `plan.md` (no solo aspectos sintácticos), dejando `request changes` en las líneas correspondientes cuando corresponda.
8. Crear la rama `release/actividad-obligatoria-1` desde `develop` una vez integradas todas las features, y habilitar GitHub Pages sobre esa rama.
9. Publicar la Pull Request de release en el canal de Slack correspondiente y subir los enlaces (PR y sitio publicado) al campus virtual.
10. Registrar la propia contribución en `changelog.md`, con el link a la Pull Request asociada.

## 2. Por qué

- El **repositorio y su branch model** son la base sobre la que trabajará todo el equipo; sin ramas protegidas y un flujo de Pull Requests definido, no se puede garantizar trazabilidad ni calidad en las próximas entregas.
- El **`plan.md`** es el documento central del proyecto: sin requerimientos funcionales claros y consensuados, cada rol (Frontend, UX, IA) no tendría una referencia común contra la cual especificar y validar su trabajo, y los code reviews carecerían de un criterio objetivo.
- La **administración de Pull Requests con revisión asistida por IA** asegura que el código que se integra a `develop` cumple con lo especificado, no solo que "funciona", incorporando así una práctica real de desarrollo de software profesional.
- La **rama de release y GitHub Pages** son necesarias para poder entregar un enlace público y verificable del trabajo, tal como exige el formato de entrega de la consigna.

## 3. Criterios de aceptación

- [ ] Repositorio `HeladeriaVainell` creado en GitHub, público, con ramas `master` y `develop`.
- [ ] Reglas de protección activas en `master` y en `develop` (revisor obligatorio, push directo bloqueado).
- [ ] Profesor y todos los integrantes agregados como colaboradores.
- [ ] Commit inicial con la estructura de carpetas completa (`docs/01-mockup/`, `docs/02-prompts/`, `docs/03-specs/`, `.github/PULL_REQUEST_TEMPLATE/`) e `index.html` vacío.
- [ ] `plan.md` existe en la raíz del repositorio, generado con GitHub Copilot en modo Agente, con requerimientos funcionales concretos de Vainell (no copia literal de la consigna) y el alcance del simulador definido.
- [ ] Templates de Pull Request configurados y utilizados por todo el equipo.
- [ ] Todas las Pull Requests del proyecto cuentan con al menos una revisión aprobada antes del merge.
- [ ] Al menos 4 code reviews asistidos con IA documentados como evidencia en los comentarios de las PRs, evaluando cumplimiento contra `plan.md`.
- [ ] Rama `release/actividad-obligatoria-1` creada desde `develop`, con GitHub Pages habilitado y el sitio accesible públicamente.
- [ ] Pull Request de release publicada en Slack (con el formato de título indicado en la consigna) y enlaces subidos al campus virtual.
- [ ] `changelog.md` actualizado con la Pull Request propia (número, link, autor y resumen del aporte).
- [ ] Issue creada para la tarea de este rol, vinculada correctamente a la Pull Request y cerrada tras el merge.

## 4. PR asociado

Esta especificación se incluye en la Pull Request `feature/coordinador-setup-repo-and-pages → develop`, que agrega o actualiza la estructura base del proyecto, la configuración de GitHub Pages y el archivo `plan.md`, redactado antes de iniciar el desarrollo.