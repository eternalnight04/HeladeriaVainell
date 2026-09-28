# Comparativa de modelos de IA

## Objetivo

Comparar dos modelos de IA aplicados a una misma tarea del proyecto Heladería Vainell, observando las diferencias entre los resultados obtenidos y determinando para qué tipo de trabajo resulta más útil cada uno.

## Comparación

Para realizar la comparación, se seleccionaron dos prompts que abordaron la misma tarea: definir y generar la estructura HTML5 inicial del proyecto Heladería Vainell.

Se compararon **GPT-4o**, utilizado en el Prompt 1 mediante Zero-shot prompting, y **Gemini**, utilizado en el Prompt 2 mediante Role prompting.

| Prompt | Tarea | Modelo | Método | Resultado / aporte |
|---|---|---|---|---|
| Prompt 1 | Estructura semántica inicial en HTML5 | GPT-4o | Zero-shot | Propuso una estructura inicial para organizar el contenido del proyecto utilizando etiquetas semánticas HTML5. Permitió analizar la organización de las secciones necesarias para la primera entrega. |
| Prompt 2 | Generación del HTML inicial | Gemini | Role prompting | Generó una propuesta de código HTML5 utilizando etiquetas semánticas, incorporando aspectos de accesibilidad como la relación entre `label`, `for` e `id`, y una estructura de tabla con `caption`, `thead` y `tbody`. También dejó indicaciones para futuras incorporaciones de CSS y JavaScript. |

### Conclusión

Los dos modelos fueron útiles para trabajar sobre la estructura inicial del proyecto, pero aportaron resultados diferentes.

En esta tarea concreta, **GPT-4o fue útil para analizar y proponer la organización semántica general de la página**, mientras que **Gemini resultó más útil para obtener una propuesta de código HTML5 detallada**, incluyendo aspectos de accesibilidad y organización de elementos del documento.

Por lo tanto, para tareas de planificación y definición de estructura, GPT-4o aportó una base útil para organizar el proyecto. Para tareas que requieren una propuesta de código HTML5 más detallada y elementos técnicos específicos, el resultado obtenido con Gemini fue más completo.

Esta conclusión se basa en los resultados documentados durante el desarrollo de Heladería Vainell y se refiere específicamente a la tarea comparada.