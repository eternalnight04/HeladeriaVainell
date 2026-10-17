# Spec - Especialista en IA y Prompt Engineering

## 1. Información general

- **Rol:** Especialista en IA y Prompt Engineering
- **Responsable:** Lautaro Chavez

---

## 2. Objetivo de la especificación

Definir las responsabilidades del Especialista en IA y Prompt Engineering dentro del proyecto Heladería Vainell, estableciendo cómo se aplicará la metodología Spec-Driven Development (SDD) y cómo se documentará el uso de herramientas de Inteligencia Artificial y los prompts utilizados durante el desarrollo.

El objetivo es asegurar que el uso de IA aporte valor concreto al proyecto y que exista documentación y trazabilidad entre el `plan.md`, las especificaciones por rol y los prompts utilizados.

---

## 3. Alcance

### Incluido

- Investigar y definir la aplicación de la metodología Spec-Driven Development (SDD) dentro del proyecto.
- Definir qué información debe contener cada archivo `docs/03-specs/spec-[rol].md`.
- Establecer un template común para las especificaciones de los diferentes roles.
- Definir el orden de elaboración de las especificaciones.
- Establecer criterios para validar las specs contra el `plan.md`.
- Documentar prompts reales utilizados durante el desarrollo del proyecto.
- Registrar en `docs/02-prompts/` al menos 5 prompts utilizados con herramientas o modelos de IA.
- Garantizar que los prompts documentados hayan aportado valor concreto al desarrollo de Heladería Vainell.
- Mantener la trazabilidad entre la planificación, las especificaciones y el uso de IA.

### Fuera de alcance

- Desarrollar la estructura HTML completa del sitio.
- Aplicar estilos CSS al proyecto.
- Implementar funcionalidades con JavaScript.
- Diseñar el mockup visual del sitio.
- Implementar una base de datos.
- Procesar pagos reales.
- Implementar sistemas de autenticación.
- Desarrollar funcionalidades que correspondan a otros roles del equipo.

---

## 4. Trazabilidad con plan.md

| Punto del plan.md | Aplicación en esta spec |
|---|---|
| 4. Tecnologías utilizadas | Documentación del uso de herramientas y modelos de IA dentro del proyecto. |
| 5.6. Especificación técnica (Spec-Driven Development) | Definición de la metodología SDD y de la estructura de `spec-[rol].md`. |
| 5.7. IA y Prompt Engineering | Documentación de al menos 5 prompts reales utilizados durante el desarrollo. |
| 7. Criterios de aceptación | Validación de la trazabilidad entre `plan.md`, specs, Pull Requests y changelog. |
| 8. Referencias | Aplicación de SDD por parte del Especialista en IA para el equipo. |

---

## 5. Requerimientos del rol

### RF-IA-01: Definición de la metodología SDD

**Descripción:**  
Investigar la metodología Spec-Driven Development (SDD) y definir cómo será aplicada dentro del proyecto Heladería Vainell.

**Justificación:**  
El `plan.md` establece que cada rol debe redactar su especificación antes de comenzar el desarrollo, permitiendo planificar, documentar y validar las tareas antes de su implementación.

---

### RF-IA-02: Definición de estructura para las specs

**Descripción:**  
Definir la información mínima que debe contener cada archivo `docs/03-specs/spec-[rol].md`.

La estructura debe permitir identificar:

- El rol responsable.
- El objetivo de la especificación.
- El alcance.
- Los requerimientos.
- La justificación de las tareas.
- Los criterios de aceptación.
- La trazabilidad con el `plan.md`.
- Los entregables.

**Justificación:**  
Una estructura común facilita la organización y permite que todas las especificaciones del proyecto mantengan un formato consistente.

---

### RF-IA-03: Creación del template de specs

**Descripción:**  
Diseñar un template reutilizable para la creación de los archivos `spec-[rol].md` utilizados por los diferentes integrantes del equipo.

**Justificación:**  
El template permite estandarizar la documentación de las responsabilidades de cada rol y facilita la validación de las especificaciones.

---

### RF-IA-04: Validación contra plan.md

**Descripción:**  
Definir un mecanismo de validación que permita comprobar que cada especificación esté relacionada con los requerimientos establecidos en el `plan.md`.

La validación debe comprobar:

- Que las tareas definidas tengan relación con el alcance del proyecto.
- Que los requerimientos del rol no contradigan el `plan.md`.
- Que los criterios de aceptación puedan ser verificados.
- Que exista trazabilidad entre las tareas del rol y los puntos correspondientes del plan.

**Justificación:**  
El `plan.md` establece la necesidad de mantener trazabilidad completa entre la planificación y el desarrollo del proyecto.

---

### RF-IA-05: Documentación de prompts

**Descripción:**  
Documentar en la carpeta `docs/02-prompts/` al menos 5 prompts reales utilizados durante el desarrollo del proyecto.

Cada prompt debe representar una interacción real con una herramienta o modelo de Inteligencia Artificial y demostrar un aporte concreto al desarrollo de Heladería Vainell.

**Justificación:**  
El `plan.md` establece como requerimiento la documentación de prompts reales utilizados con modelos de IA.

---

### RF-IA-06: Aplicación responsable de IA

**Descripción:**  
Utilizar herramientas de Inteligencia Artificial como apoyo para tareas relacionadas con investigación, documentación, planificación y desarrollo, verificando que los resultados obtenidos sean coherentes con los requerimientos establecidos en el proyecto.

**Justificación:**  
El uso de IA forma parte de las tecnologías y herramientas definidas para el proyecto, pero sus resultados deben ser revisados y contextualizados antes de ser incorporados.

---

## 6. Etapas del rol y criterios de aceptación

El trabajo del Especialista en IA y Prompt Engineering se organiza en dos etapas: una PR inicial, orientada a establecer y documentar las bases del rol, y una PR final, orientada a completar, revisar y validar los entregables.

### 6.1 PR inicial

La PR inicial tiene como objetivo establecer la estructura de trabajo del rol y documentar las primeras definiciones relacionadas con SDD, las especificaciones y el uso de IA.

**Criterios de aceptación:**

- [ ] Se definió el rol y sus responsabilidades dentro del proyecto.
- [ ] Se documentó la aplicación de la metodología SDD en Heladería Vainell.
- [ ] Se definió la estructura que deben tener las especificaciones `spec-[rol].md`.
- [ ] Se creó o documentó el template reutilizable para las especificaciones.
- [ ] Se estableció la relación entre la spec y los puntos correspondientes del `plan.md`.
- [ ] La documentación inicial corresponde al alcance definido para el rol.

### 6.2 PR final

La PR final tiene como objetivo completar y validar los entregables del Especialista en IA y Prompt Engineering antes de la entrega de la actividad.

**Criterios de aceptación:**

- [ ] Se documentaron al menos 5 prompts reales utilizados durante el desarrollo.
- [ ] Cada prompt documentado identifica la herramienta o modelo utilizado y su aporte al proyecto.
- [ ] La comparativa de modelos está completa y actualizada.
- [ ] Se documentaron las decisiones relacionadas con el uso de IA.
- [ ] Se verificó la trazabilidad entre `plan.md`, las specs, los prompts y el `changelog.md`.
- [ ] Los entregables del rol cumplen con los requerimientos definidos en esta especificación.
- [ ] La PR final cuenta con al menos una revisión aprobada antes del merge.

### 6.3 Criterios generales de aceptación

- [ ] Se definió un mecanismo para validar las specs contra el plan del proyecto.
- [ ] Los prompts documentados aportaron valor concreto al proyecto.
- [ ] Se mantiene la trazabilidad entre `plan.md`, `spec-[rol].md`, Pull Requests y `changelog.md`.

---

## 7. Dependencias

- `plan.md` como documento base del proyecto.
- Especificaciones de los diferentes roles del equipo.
- Carpeta `docs/03-specs/` para almacenar las especificaciones.
- Carpeta `docs/02-prompts/` para documentar los prompts utilizados.
- Pull Requests para registrar los cambios realizados.
- `changelog.md` para mantener el historial de modificaciones del proyecto.

---

## 8. Validación contra plan.md

| Criterio definido en la spec | Punto relacionado del plan.md | Estado |
|---|---|---|
| Aplicación de la metodología SDD | 5.6 Especificación técnica | Pendiente |
| Definición de `spec-[rol].md` | 5.6 Especificación técnica | Pendiente |
| Trazabilidad con el plan | 7. Criterios de aceptación | Pendiente |
| Documentación de prompts | 5.7 IA y Prompt Engineering | Pendiente |
| Mínimo de 5 prompts reales | 5.7 IA y Prompt Engineering | Pendiente |
| Uso de IA como herramienta del proyecto | 4. Tecnologías utilizadas | Pendiente |
| Relación entre specs, PR y changelog | 7. Criterios de aceptación | Pendiente |

---

## 9. Entregables

- Archivo `docs/03-specs/spec-ia.md`.
- Template para la creación de `spec-[rol].md`.
- Definición de la aplicación de Spec-Driven Development en el proyecto.
- Documentación de al menos 5 prompts reales en `docs/02-prompts/`.
- Criterios de validación y trazabilidad entre las specs y el `plan.md`.

---

## 10. Historial de cambios

| Fecha | Cambio | Responsable |
|---|---|---|
| 30/08/2026 | Creación inicial de la especificación | Lautaro Chavez |