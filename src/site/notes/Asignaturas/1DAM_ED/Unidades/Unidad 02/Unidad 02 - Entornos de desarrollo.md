---
{"dg-publish":true,"dg-permalink":"/apuntes/1-dam-ed/unidades/unidad-03-entornos-de-desarrollo/","permalink":"/apuntes/1-dam-ed/unidades/unidad-03-entornos-de-desarrollo/","tags":["java/ide"],"dg-note-properties":{"modulo":"[[Módulos/Entornos de desarrollo]]","libro":"[[Libros/Entornos de desarrollo (1º DAM, 1º DAW)]]","descripcion":"Los IDE con la herramienta directa entre el desarrollador y el software. Veremos sus características, configuraciones y funcionalidades.","orden":4,"ra":"RA2","tags":["java/ide"]}}
---


En la [[Asignaturas/1DAM_ED/Unidades/Unidad 01/Unidad 01 - Desarrollo de software\|Unidad 01]] vimos el camino que recorre un programa desde el código fuente hasta su ejecución, y lo hicimos a mano, con un editor de texto y el terminal. En el día a día, ese camino se recorre con un **<abbr title="Integrated Development Environment">IDE</abbr>** (entorno de desarrollo integrado): un programa que reúne en una sola ventana el editor, el compilador o intérprete, el depurador y muchas otras herramientas, para que escribir código sea más rápido y fiable.

Hoy, además, el IDE es el centro de un ecosistema más amplio: herramientas de construcción como Maven, control de versiones, pruebas automáticas, integración continua o entornos en la nube, que se conectan con él mediante extensiones.

En esta unidad vamos a **evaluar** entornos de desarrollo, es decir, a conocerlos y usarlos para poder elegir el adecuado:

* **Conocer** qué es un IDE, cómo se organiza y qué tienen en común y en qué se diferencian los más usados.
* **Instalarlos**, libres y propietarios, y mantenerlos al día configurando sus actualizaciones.
* **Personalizarlos y ampliarlos** con módulos y extensiones, y **automatizar** tareas con herramientas de construcción.
* **Generar ejecutables** de varios lenguajes con un mismo entorno, y de un mismo código con varios entornos.

## Datos de la unidad

### RA asociado y criterios de evaluación

**RA 2.** Evalúa entornos integrados de desarrollo analizando sus características para editar código fuente y generar ejecutables.

Criterios de evaluación:

- a) Se han instalado entornos de desarrollo, propietarios y libres.
- b) Se han añadido y eliminado módulos en el entorno de desarrollo.
- c) Se ha personalizado y automatizado el entorno de desarrollo.
- d) Se ha configurado el sistema de actualización del entorno de desarrollo.
- e) Se han generado ejecutables a partir de código fuente de diferentes lenguajes en un mismo entorno de desarrollo.
- f) Se han generado ejecutables a partir de un mismo código fuente con varios entornos de desarrollo.
- g) Se han identificado las características comunes y específicas de diversos entornos de desarrollo.

### Contenidos básicos

Instalación y uso de entornos de desarrollo:

- Funciones de un entorno de desarrollo.
- Instalación de un entorno de desarrollo.
- Uso básico de un entorno de desarrollo.
- Personalización del entorno de desarrollo: temas, estilos de codificación, módulos y extensiones, entre otras.
- Edición de programas.
- Generación de ejecutables en distintos entornos.
- Herramientas y automatización.

## Índice de contenidos

| File                                                                                                                                                                                          | Descripción                                                                                                                                                         | Criterios                                                                       |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 02/1. El IDE\|1. El IDE]]                                                                                                                             | Qué es un IDE, cómo han evolucionado los entornos de desarrollo y qué características tienen los más usados.                                                        | <ul><li>RA2.g</li></ul>                                                         |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 02/2. Estructura de un IDE\|2. Estructura de un IDE]]                                                                                                 | Los menús y paneles típicos de un IDE y para qué sirve cada uno.                                                                                                    | <ul><li>RA2.g</li></ul>                                                         |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 02/3. Configuración y personalización de entornos de desarrollo\|3. Configuración y personalización de entornos de desarrollo]]                       | Opciones de configuración de un proyecto y personalización del entorno de desarrollo.                                                                               | <ul><li>RA2.c</li></ul>                                                         |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 02/4. Módulos, plugins y extensiones\|4. Módulos, plugins y extensiones]]                                                                             | Qué son los módulos, plugins y extensiones de un IDE y qué tipos de funcionalidades añaden.                                                                         | <ul><li>RA2.b</li></ul>                                                         |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 02/5. Herramientas de construcción (Build Tools) y gestión de dependencias\|5. Herramientas de construcción (Build Tools) y gestión de dependencias]] | Herramientas de construcción como Maven o npm: gestión de dependencias, automatización de tareas y generación de artefactos.                                        | <ul><li>RA2.c</li><li>RA2.e</li></ul>                                           |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 02/6. Otras herramientas\|6. Otras herramientas]]                                                                                                     | El terminal y las herramientas CLI, la integración y entrega continua (CI/CD) y los IDE en la nube y entornos en contenedores.                                      | <ul><li>RA2.c</li><li>RA2.g</li></ul>                                           |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 02/7. Entornos de desarrollo en la práctica\|7. Entornos de desarrollo en la práctica]]                                                               | Guía práctica para instalar IDE libres y propietarios, configurar sus actualizaciones, añadir y quitar extensiones y generar ejecutables con uno o varios entornos. | <ul><li>RA2.a</li><li>RA2.b</li><li>RA2.d</li><li>RA2.e</li><li>RA2.f</li></ul> |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 02/8. Referencias\|8. Referencias]]                                                                                                                   | Fuentes y recursos de la unidad.                                                                                                                                    | \-                                                                              |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 02/9. Anexos\|9. Anexos]]                                                                                                                             | Ejemplos de un pipeline de GitHub Actions y de un fichero devcontainer.json.                                                                                        | <ul><li>RA2.c</li></ul>                                                         |

{ .block-language-dataview}


---

<p><span>⬅️ <strong>Anterior:</strong> <a data-tooltip-position="top" aria-label="Asignaturas/1DAM_ED/Unidades/Unidad 01/Unidad 01 - Anexo - Enfoque clásico.md" data-href="Asignaturas/1DAM_ED/Unidades/Unidad 01/Unidad 01 - Anexo - Enfoque clásico.md" href="Asignaturas/1DAM_ED/Unidades/Unidad 01/Unidad 01 - Anexo - Enfoque clásico.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 01 - Anexo - Enfoque clásico</a> | 🏠 <strong>Libro:</strong> <a data-tooltip-position="top" aria-label="Libros/Entornos de desarrollo (1º DAM, 1º DAW).md" data-href="Libros/Entornos de desarrollo (1º DAM, 1º DAW).md" href="Libros/Entornos de desarrollo (1º DAM, 1º DAW).md" class="internal-link" target="_blank" rel="noopener nofollow">Entornos de desarrollo (1º DAM, 1º DAW)</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="Asignaturas/1DAM_ED/Unidades/Unidad 03/Unidad 03 - Pruebas y depuración.md" data-href="Asignaturas/1DAM_ED/Unidades/Unidad 03/Unidad 03 - Pruebas y depuración.md" href="Asignaturas/1DAM_ED/Unidades/Unidad 03/Unidad 03 - Pruebas y depuración.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 03 - Pruebas y depuración</a> ➡️</span></p>
