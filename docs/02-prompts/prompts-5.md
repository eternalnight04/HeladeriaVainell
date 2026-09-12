# Prompt 5 - Optimización y validación del código

## Información general

- **Modelo:** gemini
- **Método:** Chain-of-thought guiado
- **Objetivo:** Revisar el código HTML y verificar su cumplimiento con los requerimientos del proyecto.

---

## Prompt exacto

> Actuá como revisor de código especializado en HTML5.
>
> Necesito que analices la estructura de un proyecto académico llamado Heladería Vainell.
>
> La primera entrega debe cumplir los siguientes requisitos:
>
> 1. Utilizar HTML5 válido.
> 2. Incluir estructura semántica.
> 3. Contener header, main y footer.
> 4. Incluir navegación.
> 5. Contener textos descriptivos reales.
> 6. Incluir imágenes con atributo alt.
> 7. Contener enlaces.
> 8. Incluir una lista.
> 9. Incluir una tabla con th y td.
> 10. Contener un formulario de pedido.
> 11. Permitir indicar delivery o retiro en local.
> 12. No utilizar todavía CSS ni JavaScript funcional.
> 13. Incluir comentarios indicando futuras integraciones de CSS y JavaScript.
>
> Analizá el código paso a paso y generá una lista de verificación.
>
> Para cada requisito indicá:
>
> - Cumple.
> - No cumple.
> - Requiere revisión.
>
> Si detectás un problema, explicá brevemente cómo podría corregirse sin modificar innecesariamente la estructura existente.

---

## Resultado esperado

Obtener una revisión estructurada del código para detectar posibles errores o incumplimientos antes de realizar la entrega.

---

## Resultado obtenido

[Completar con el resultado real obtenido al ejecutar el prompt.]Lista de Verificación de Requisitos
Utilizar HTML5 válido: Cumple.
El documento inicia con <!DOCTYPE html>, especifica el idioma en <html lang="es">, contiene la codificación UTF-8 y no presenta etiquetas obsoletas.

Incluir estructura semántica: Cumple.
Hace un uso impecable de etiquetas semánticas (<header>, <nav>, <main>, <section>, <article>, <fieldset>, <legend>, <table>, <footer>).

Contener header, main y footer: Cumple.
Las tres secciones estructurales principales se encuentran presentes y correctamente delimitadas.

Incluir navegación: Cumple.
La sección <nav> contiene una lista desordenada con enlaces internos (href="#id").

Contener textos descriptivos reales: Cumple.
No utiliza texto de relleno (Lorem Ipsum); toda la información describe productos, precios y el flujo real de la heladería.

Incluir imágenes con atributo alt: No cumple.
No se incluyó ninguna etiqueta <img> dentro del documento.

Contener enlaces: Cumple.
El menú de navegación incluye enlaces de salto interno a los IDs de las secciones.

Incluir una lista: Cumple.
Se utilizan listas desordenadas (<ul>) para el menú y los sabores, y una lista ordenada (<ol>) para los pasos de compra.

Incluir una tabla con th y td: Cumple.
La tabla de precios utiliza <caption>, <thead>, <tbody>, <th> (con sus respectivos atributos scope) y <td>.

Contener un formulario de pedido: Cumple.
Se implementa un elemento <form> completo con inputs de texto, correo, teléfono, menú desplegable y áreas de texto.

Permitir indicar delivery o retiro en local: Cumple.
Contiene un grupo de botones de opción (type="radio") con el atributo name="modalidad".

No utilizar todavía CSS ni JavaScript funcional: Cumple.
No hay código CSS en línea, bloques <style> ni archivos de JavaScript ejecutables.

Incluir comentarios indicando futuras integraciones de CSS y JavaScript: Cumple.
Se incluyen comentarios explícitos en el <head> y antes del cierre del </body>.

Corrección para los puntos observados
1. Faltante de imágenes (<img> con atributo alt)
Para cumplir al 100% con los requisitos sin alterar la estructura existente, se pueden incorporar imágenes en la sección de presentación y en la sección del catálogo.
---

## Correcciones manuales

[Indicar qué correcciones fueron aplicadas manualmente después de revisar la respuesta.]

---

## Aporte al proyecto

Este prompt permitió utilizar la IA como herramienta de revisión y control de calidad para verificar el cumplimiento de los requerimientos definidos en el `plan.md`.

![alt text](image.png)
