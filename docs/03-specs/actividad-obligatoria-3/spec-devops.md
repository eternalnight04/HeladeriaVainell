# Especificación DevOps — Actividad Obligatoria 3

- **Rol:** Coordinador / DevOps
- **Responsable:** Lautaro Chavez
- **Rama de trabajo:** `feature/coord-devops-tercera-entrega`
- **Rama base:** `develop`
- **Entrega:** Actividad Obligatoria 3

## 1. Objetivo

Coordinar la integración, revisión y publicación de los cambios correspondientes a la tercera entrega de Heladería Vainell, manteniendo la trazabilidad del trabajo mediante Git, GitHub Pull Requests, documentación y herramientas de gestión del proyecto.

Se buscará asegurar que los cambios de los integrantes sean revisados, integrados y documentados antes de publicar la versión final.

## 2. Estado inicial

- Se actualizó la rama local `develop` desde `origin/develop`.
- Se verificó que la primera entrega está integrada en `master`, mediante el PR #15.
- Se verificó que el backport de la primera entrega hacia `develop` ya fue integrado mediante el PR #46.
- La rama de trabajo se creó desde `develop` actualizado.
- Se creó el directorio `docs/03-specs/actividad-obligatoria-3/`.

## 3. Estrategia de trabajo

### 3.1. Correcciones de entregas anteriores

- Verificar las observaciones pendientes de la primera entrega.
- Confirmar la resolución de los RC accionables, incluido RC84.
- Mantener registro de las correcciones y de su estado.
- Evitar repetir el backport de la primera entrega, ya integrado mediante el PR #46.

### 3.2. Integración de cambios del equipo

- Revisar las ramas y Pull Requests de los integrantes.
- Comprobar que los cambios respeten `plan.md` y el mockup actualizado.
- Coordinar la integración de las funcionalidades en `develop`.
- Solicitar correcciones cuando se detecten problemas.
- Revisar y aprobar los Pull Requests antes de su integración, respetando las protecciones y aprobaciones requeridas.
- Mantener actualizados `README.md`, `plan.md` y `changelog.md`.

### 3.3. Revisiones de código asistidas por IA

Se realizarán al menos cuatro revisiones de código utilizando GitHub Copilot en Agent Mode.

Las revisiones deberán comprobar:

- Correspondencia entre el código JavaScript y el mockup actualizado.
- Cumplimiento de los requisitos definidos en `plan.md`.
- Organización y legibilidad del código.
- Posibles errores funcionales o problemas de integración.

Cuando corresponda, se utilizará la revisión `CHANGES_REQUESTED` para solicitar modificaciones antes de aprobar un Pull Request.

Se conservará como evidencia:

- Prompt exacto utilizado.
- Pull Request revisado.
- Archivos y líneas analizadas.
- Resultado de la revisión.
- Cambios solicitados y su resolución.

### 3.4. Publicación y entrega

- Configurar y verificar GitHub Pages para la rama de publicación correspondiente.
- Preparar la rama `release/tercera-entrega`.
- Crear y revisar el Pull Request de publicación.
- Compartir el enlace de la entrega final en Slack y en el campus.
- Una vez integrada la entrega en `master`, crear la release formal `v1.1-tercera-entrega`.

### 3.5. Organización del proyecto

- Mantener el repositorio organizado y actualizado.
- Actualizar los índices y enlaces de documentación.
- Verificar la existencia y vinculación de:
  - `docs/05-diagramas/01-diagrama-de-actividades/diagramas-doc.md`
  - `js/test/testing-doc.md`
- Gestionar las tareas mediante GitHub Projects, utilizando un tablero Kanban.
- Registrar problemas, decisiones y resoluciones.
- Coordinar reuniones y resolver conflictos de integración con los integrantes.

## 4. Uso de GitHub Copilot Agent Mode

Se utilizará Copilot Agent Mode como asistencia para analizar Pull Requests y detectar posibles incumplimientos.

La herramienta permitirá revisar varios archivos relacionados, contrastar el código con los requisitos del proyecto y proponer correcciones.

Las decisiones finales de aprobación e integración serán responsabilidad del Coordinador / DevOps. Las sugerencias de IA deberán verificarse antes de aceptarse.

## 5. Criterios de aceptación

- [ ] Correcciones de la primera entrega verificadas y documentadas.
- [ ] Backport de la primera entrega comprobado en `develop` (PR #46).
- [ ] Cambios del equipo revisados e integrados en `develop`.
- [ ] Al menos cuatro revisiones de código asistidas por Copilot Agent Mode documentadas.
- [ ] Revisiones con solicitudes `CHANGES_REQUESTED` y evidencia de los cambios solicitados.
- [ ] GitHub Pages activo y verificado.
- [ ] Documentación actualizada y coherente.
- [ ] README con información de la tercera entrega, JavaScript y testing.
- [ ] Changelog actualizado con las contribuciones y los enlaces a los Pull Requests.
- [ ] Índices de documentación actualizados.
- [ ] Issues y tareas gestionados mediante GitHub Projects.
- [ ] Rama `release/tercera-entrega` preparada y revisada.
- [ ] Pull Request final publicado y comunicado.
- [ ] Release `v1.1-tercera-entrega` creada después de integrar la entrega en `master`.
- [ ] Limpieza final de ramas, conservando únicamente `master`, `develop` y `release/tercera-entrega`.

## 6. Evidencias y cierre

Al finalizar las tareas se incorporarán a esta especificación:

1. Los prompts exactos utilizados en las revisiones asistidas por IA.
2. Los diffs o archivos correspondientes a las revisiones.
3. El resumen individual de cada revisión: Pull Request, archivos analizados, observaciones y resultado.
4. Las solicitudes `CHANGES_REQUESTED` y las modificaciones realizadas.
5. Los obstáculos encontrados y las soluciones aplicadas.
6. Los enlaces a los Pull Requests, GitHub Pages y release final.

La documentación se completará con resultados reales y verificables, sin registrar como realizadas tareas que todavía estén pendientes.