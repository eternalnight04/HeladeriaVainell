# Decisiones SDD - Heladería Vainell

## 1. Propósito

Este documento registra las decisiones tomadas para aplicar la metodología Spec-Driven Development (SDD) en el proyecto Heladería Vainell.

El objetivo es establecer una forma de trabajo común para que las tareas de cada integrante sean especificadas antes de su desarrollo y mantengan trazabilidad con el `plan.md`.

---

## 2. Decisión 1: Crear una spec por cada rol

Se decidió que cada integrante del equipo deberá contar con un archivo de especificación individual siguiendo el formato:

`docs/03-specs/spec-[rol].md`

Cada spec deberá describir las responsabilidades del rol, su alcance, requerimientos, criterios de aceptación y relación con el `plan.md`.

**Motivo:**  
Permite definir claramente qué realizará cada rol antes de comenzar el desarrollo y facilita la organización del trabajo.

---

## 3. Decisión 2: Utilizar un template común

Se decidió utilizar una estructura común para todos los archivos `spec-[rol].md`.

El template incluirá:

- Información general.
- Objetivo de la especificación.
- Alcance.
- Trazabilidad con `plan.md`.
- Requerimientos del rol.
- Criterios de aceptación.
- Dependencias.
- Validación contra `plan.md`.
- Entregables.
- Historial de cambios.

**Motivo:**  
El uso de un template permite mantener consistencia entre las especificaciones de los diferentes roles.

---

## 4. Decisión 3: Orden de elaboración de las specs

Se decidió que las especificaciones deberán elaborarse antes de comenzar las tareas de desarrollo correspondientes a cada rol.

El flujo definido será:

1. Consultar el `plan.md`.
2. Identificar los requerimientos relacionados con el rol.
3. Redactar la `spec-[rol].md`.
4. Verificar la trazabilidad con el `plan.md`.
5. Validar los criterios de aceptación.
6. Realizar el desarrollo o tarea especificada.
7. Registrar los cambios mediante Pull Request y `changelog.md`.

**Motivo:**  
Este orden permite que la planificación y los requerimientos guíen el desarrollo, evitando implementar tareas sin una especificación previa.

---

## 5. Decisión 4: Trazabilidad obligatoria

Se decidió mantener la siguiente cadena de trazabilidad:

`plan.md` → `spec-[rol].md` → Pull Request → `changelog.md`

Cada tarea debe poder relacionarse con un requerimiento definido previamente en el plan del proyecto.

**Motivo:**  
Permite verificar el origen de cada decisión y comprobar que el desarrollo responde a los objetivos establecidos para Heladería Vainell.

---

## 6. Decisión 5: Validación de las specs

Antes de considerar una spec lista, se verificará que:

- Esté relacionada con uno o más puntos del `plan.md`.
- Defina claramente el alcance del rol.
- Incluya requerimientos específicos.
- Contenga criterios de aceptación verificables.
- No incluya funcionalidades fuera del alcance definido en el proyecto.
- Identifique los entregables esperados.

**Motivo:**  
La validación previa permite detectar inconsistencias antes de comenzar el desarrollo.

---

## 7. Decisión 6: Uso de IA y documentación de prompts

Se decidió documentar los prompts reales utilizados durante el desarrollo en la carpeta:

`docs/02-prompts/`

Cada prompt documentado deberá reflejar una interacción real con una herramienta o modelo de Inteligencia Artificial y demostrar su aporte concreto al proyecto.

**Motivo:**  
El proyecto establece como requerimiento documentar al menos 5 prompts reales utilizados durante el desarrollo de Heladería Vainell.

---

## 8. Resumen del flujo SDD

El proceso de trabajo definido para el proyecto será:

1. Definir los requerimientos generales en `plan.md`.
2. Crear una especificación por cada rol.
3. Validar cada spec contra el plan.
4. Realizar las tareas definidas en la especificación.
5. Documentar los cambios mediante Pull Request.
6. Registrar los cambios relevantes en `changelog.md`.

---

## 9. Historial de cambios

| Fecha | Decisión o cambio | Responsable |
|---|---|---|
| 30/08/2026 | Creación inicial del documento de decisiones SDD | Lautaro Chavez |