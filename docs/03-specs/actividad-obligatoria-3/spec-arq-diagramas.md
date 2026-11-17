# spec-arq-diagramas.md — Arquitecto de Diagramas de Actividades

**Proyecto:** Vainell
**Entrega:** Actividad Obligatoria N°3
**Rol:** Arquitecto de Diagramas de Actividades
**Rama:** `feature/arq-diagramas-actividades`

---

# PARTE 1 — BEFORE (completar y commitear antes de abrir Copilot)

## 1.1 Qué se hace y por qué

Se modelan con PlantUML los **4 flujos principales** que el Desarrollador JavaScript implementará en `js/script.js`. Los diagramas son el punto de partida del código: el JS debe reflejar los flujos modelados, no al revés. Así se evita implementar lógica sin diseño y se facilita que el Tester derive los casos de prueba de las decisiones y ciclos de cada diagrama.

Restricciones heredadas de la consigna que condicionan los diagramas:

- Solo `prompt()`, `alert()` y `console.log()`; **no hay DOM ni eventos** en esta entrega. Por eso todas las interacciones del diagrama son entradas por `prompt()` y salidas por `alert()`/`console.log()`.
- Cada flujo sigue el patrón **entrada → proceso → salida**.
- Hay un **menú principal** con `prompt()` para elegir entre los 4 flujos; es el punto de entrada común, y cada diagrama arranca desde la opción elegida en ese menú.

## 1.2 Fuentes analizadas

| Fuente | Qué aporta a los flujos |
|---|---|
| `plan.md` | Alcance del simulador: catálogo, modalidad delivery/retiro, formulario de pedido, costo de envío por zona, confirmación visual sin backend, login/registro simulado ("Mi cuenta Vainell"). |
| `index.html` — `#catalogo` | 5 categorías de producto (por kilo, potes, palitos, tortas, toppings) con precio y botón "Agregar". Datos para el cotizador. |
| `index.html` — `#pedido` | Campos: nombre, apellido, teléfono, modalidad (delivery/retiro), dirección, medio de pago (efectivo/transferencia/tarjeta), comentarios. |
| `index.html` — `#mi-cuenta` | Login (usuario/mail + contraseña) y registro (nombre, mail, contraseña, confirmación). |
| `index.html` — footer y hero | Horarios de atención (Lun–Vie 11–22, Sáb–Dom 10–23) y entrega promedio de 20 min: sirven como reglas de validación y mensaje de salida. |
| Mockup (`docs/01-mockup/`) | **Pendiente de adjuntar a Copilot** junto con `plan.md` e `index.html`. |

## 1.3 Identificación de los 4 flujos

| # | Flujo | Archivo previsto | Actor(es) | Decisiones | Ciclos |
|---|---|---|---|---|---|
| 1 | **Cotizar pedido** desde el catálogo | `actividad-flujo-1-cotizador-pedido.puml` | Usuario, Sistema | ¿categoría válida? ¿producto válido? ¿cantidad válida? ¿agregar otro? | `repeat` para agregar productos; `while` para reintentar entradas inválidas |
| 2 | **Modalidad de entrega y costo de envío** | `actividad-flujo-2-modalidad-envio.puml` | Usuario, Sistema | ¿delivery o retiro? ¿zona con cobertura? ¿horario de retiro dentro del horario de atención? | `while` para reintentar zona/horario inválidos |
| 3 | **Confirmar pedido** (datos del cliente y resumen) | `actividad-flujo-3-confirmar-pedido.puml` | Usuario, Sistema | ¿hay productos cargados? ¿datos válidos? ¿dirección requerida (solo delivery)? ¿el usuario confirma? | `while` de validación por cada dato |
| 4 | **Mi cuenta Vainell** (registro e inicio de sesión simulados) | `actividad-flujo-4-mi-cuenta.puml` | Usuario, Sistema | ¿registro o login? ¿mail válido y no registrado? ¿contraseñas coinciden? ¿credenciales correctas? | `while` con máximo de intentos de login |

**Menú principal (entrada común):** el usuario elige 1–4 o 0 para salir, dentro de un `while` que reitera el menú hasta elegir salir. Se documenta en `diagramas-doc.md` y se dibuja como encabezado de cada flujo, sin sumar un quinto diagrama.

### Resumen entrada → proceso → salida

| Flujo | Entrada (`prompt`) | Proceso | Salida (`alert`/`console.log`) |
|---|---|---|---|
| 1 | Categoría, producto, cantidad, ¿otro? | Valida, agrega al array de ítems, suma subtotal recorriendo el array | Detalle del pedido y subtotal |
| 2 | Modalidad, zona o horario de retiro | Valida, aplica tarifa por zona (retiro = $0), calcula total | Costo de envío y total |
| 3 | Nombre, apellido, teléfono, dirección, medio de pago, comentarios, confirmación | Valida cada dato, arma el objeto pedido | Resumen y mensaje de pedido confirmado o cancelado |
| 4 | Opción (registro/login), nombre, mail, contraseña(s) | Valida, busca/guarda en el array de usuarios | Mensaje de cuenta creada, sesión iniciada con el nombre, o bloqueo |

## 1.4 Decisión sobre swimlanes

Se usan particiones **`|Usuario|` y `|Sistema|` en los 4 flujos**, porque en todos hay un intercambio explícito: el usuario ingresa datos por `prompt()` y el sistema valida, calcula y responde. El criterio aplicado es: *"si una acción la dispara una persona que tipea, va en Usuario; si es validar, calcular, almacenar o mostrar, va en Sistema"*. Las repeticiones por dato inválido cruzan entre ambas partes (Sistema rechaza → Usuario reingresa), y eso es justamente lo que las swimlanes permiten mostrar.

## 1.5 Criterios de aceptación (checklist)

- [x] Este spec está commiteado antes que cualquier archivo `.puml` (verificable en el historial).
- [x] Existen 4 diagramas de actividades en PlantUML, uno por flujo.
- [x] Cada diagrama tiene `start` y `stop` claramente marcados.
- [x] Las actividades usan la sintaxis `:Nombre de la actividad;`.
- [x] Cada diagrama incluye decisiones `if-then-else` y al menos un ciclo (`while` o `repeat`).
- [x] Hay swimlanes `|Usuario|` y `|Sistema|` en los flujos donde interviene el usuario y el sistema.
- [x] El flujo lógico es coherente con la implementación planificada en `plan.md` (ver tabla de trazabilidad).
- [x] Cada diagrama está exportado como `.puml` (editable) y `.png` (visualización).
- [x] Los archivos siguen la nomenclatura `actividad-flujo-N-[nombre].puml/.png` dentro de `docs/05-diagramas/01-diagrama-de-actividades/`.
- [x] Existe `diagramas-doc.md` con índice, descripción de cada flujo, enlace al `.puml`, imagen `.png` embebida e instrucciones de edición (plantuml editor online o extensión de VS Code).
- [x] Se usó Copilot en modo Agente con `plan.md`, `index.html` y el mockup como contexto.
- [x] Los diagramas fueron coordinados con el Desarrollador JavaScript.
- [x] Rama `feature/arq-diagramas-actividades`, al menos una issue asociada al rol, PR hacia `develop` con revisión de otro integrante, y participación registrada en `changelog.md` con link y resumen.

## 1.6 Trazabilidad con `plan.md`

| Flujo | Requerimiento de `plan.md` |
|---|---|
| 1 | "Ver el catálogo de sabores, productos y precios"; §3 "Catálogo de productos (helados por kilo, potes, palitos, tortas heladas, toppings)" |
| 2 | "Selección de modalidad de compra: delivery o retiro en local" y "Cálculo simulado de costo de envío según zona" |
| 3 | "Formulario de pedido" y "Confirmación visual del pedido (sin backend real)" |
| 4 | "Sistema de inicio de sesión y registro de usuario simulado (Mi cuenta Vainell)", con las restricciones de simulación de front-end de "Fuera de alcance" |

## 1.7 Plan de trabajo

1. Commitear este spec (sección BEFORE).
2. Abrir issue del rol y crear la rama `feature/arq-diagramas-actividades` desde `develop`.
3. Generar los `.puml` con Copilot Agent y corregirlos a mano.
4. Exportar los `.png`, escribir `diagramas-doc.md` y revisar los flujos con el Dev JS.
5. Completar la sección AT CLOSE, abrir el PR hacia `develop` y registrar en `changelog.md`.

---

# PARTE 2 — AT CLOSE (evidencia; completar al terminar)

## 2.1 Archivos de contexto utilizados

- index.html
- plan.md
- docs/01-mockup/actividad-obligatoria-2/diseño-con-estilos.png

## 2.2 Prompt exacto utilizado

```text
Actuá como arquitecto de software. Adjunto plan.md, index.html y el mockup del proyecto "Heladería Vainell" (simulador de pedidos, sin backend).
Generá 4 diagramas de actividades en PlantUML, uno por archivo, para estos flujos:
1) Cotizar pedido desde el catálogo, 
2) Modalidad de entrega y costo de envío,
3) Confirmar pedido, 
4) Mi cuenta Vainell (registro y login simulados).
Requisitos: usar start y stop; actividades con la sintaxis ":Texto;"; decisiones con if-then-else; ciclos con while o repeat; swimlanes |Usuario| y |Sistema|.
Las entradas son por prompt() y las salidas por alert()/console.log(); no hay DOM ni eventos. Cada flujo sigue entrada -> proceso -> salida y debe ser coherente con plan.md. Nombrá los archivos actividad-flujo-N-[nombre].puml.
```

## 2.3 Output generado por Copilot

```
Generé los cuatro diagramas en docs/05-diagramas/01-diagrama-de-actividades/, con las swimlanes Usuario y Sistema, menú común, decisiones, ciclos y entradas/salidas con prompt(), alert() y console.log().

Cotizar pedido — PlantUML · PNG
Modalidad y envío — PlantUML · PNG
Confirmar pedido — PlantUML · PNG
Mi cuenta — PlantUML · PNG

También incluí un índice y notas de diseño. No inventé tarifas de envío ni un máximo de intentos: quedan como parámetros por definir. Los cuatro archivos pasaron la validación de sintaxis PlantUML y se renderizaron a PNG
```

## 2.4 Ajustes manuales realizados

- Se corrigió la sintaxis y la ortografía de los diagramas.


