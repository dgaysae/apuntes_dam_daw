---
{"dg-publish":true,"dg-permalink":"/apuntes/1-dam-ed/unidades/unidad-05-repositorios-documentacion-y-refactorizacion/","permalink":"/apuntes/1-dam-ed/unidades/unidad-05-repositorios-documentacion-y-refactorizacion/","tags":["git","git/repo_remoto","java/refactoring","java/javadoc"],"dg-note-properties":{"modulo":"[[Módulos/Entornos de desarrollo]]","libro":"[[Libros/Entornos de desarrollo (1º DAM, 1º DAW)]]","descripcion":"¿Qué otras herramientas orbitan alrededor del desarrollo de software? Además del IDE existen otras herramientas que nos ayudan a gestionar los cambios a lo largo de desarrollo (control de versiones), replantear nuestro código (refactorización) y documentarlo.","orden":6,"ra":"RA4","tags":["git","git/repo_remoto","java/refactoring","java/javadoc"]}}
---


En las unidades anteriores hemos aprendido a usar el **entorno de desarrollo** y a **probar y depurar** el código. Sin embargo, en el mundo profesional, el software **no se escribe una sola vez ni lo hace una sola persona**: se mejora continuamente y lo desarrollan equipos.

Los contenidos de esta unidad son el puente entre «saber programar» y «**saber trabajar**» con las herramientas de la ingeniería del software. Vamos a aprender a:

* **Mejorar el código sin cambiar lo que hace**, con la **refactorización**, apoyándonos en las pruebas de la [[Asignaturas/1DAM_ED/Unidades/Unidad 03/Unidad 03 - Pruebas y depuración\|Unidad 03]] y en las herramientas del IDE.

* **Revisar la calidad del código** con **analizadores** que detectan errores, malas prácticas y deuda técnica, y configurarlos.

* **Documentar** las clases con las herramientas del entorno, como Javadoc.

* **Gestionar los cambios** con un **sistema de control de versiones** (Git).  
  ¿Tienes carpetas con nombres como **`proyecto\final\v2\definitivo\v1.zip`** o **`proyecto\final\v2\definitivo\ESTA\VEZ\SI.zip`**? Con Git tendremos un historial de la evolución del código, con hitos (*commits*) a los que volver, y podremos combinar nuestro trabajo con el de otras personas.

* **Trabajar en equipo** con **repositorios remotos** como GitHub, desde el terminal y desde el IDE.

* **Comprobar automáticamente** cada cambio con la **integración continua**.

## Datos de la unidad

### RA asociado y criterios de evaluación

**RA 4.** Optimiza código empleando las herramientas disponibles en el entorno de desarrollo.

Criterios de evaluación:

- a) Se han identificado los patrones de refactorización más usuales.
- b) Se han elaborado las pruebas asociadas a la refactorización.
- c) Se ha revisado el código fuente usando un analizador de código.
- d) Se han identificado las posibilidades de configuración de un analizador de código.
- e) Se han aplicado patrones de refactorización con las herramientas que proporciona el entorno de desarrollo.
- f) Se ha realizado el control de versiones integrado en el entorno de desarrollo.
- g) Se han utilizado herramientas del entorno de desarrollo para documentar las clases.
- h) Se han utilizado repositorios remotos para el desarrollo de código colaborativo.
- i) Se han utilizado herramientas para la integración continua del código.

### Contenidos básicos

Optimización y documentación:

- Refactorización. Concepto. Limitaciones. Patrones de refactorización más usuales. Refactorización y pruebas. Herramientas de ayuda a la refactorización.
- Analizadores de código.
- Control de versiones. Estructura de las herramientas de control de versiones. Repositorio. Herramientas de control de versiones. Uso integrado en el entorno de desarrollo.
- Repositorios remotos.
- Documentación. Uso de comentarios. Alternativas.
- Integración continua. Herramientas.

## Índice de contenidos

| File                                                                                                                                                  | Descripción                                                                                                                                               | Criterios                                           |
| ----------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------- |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 04/1. Control de versiones - repositorios\|1. Control de versiones - repositorios]]                           | Qué es un sistema de control de versiones, sus conceptos básicos y su uso en el sector productivo.                                                        | <ul><li>RA4.f</li><li>RA4.h</li></ul>               |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 04/2. Git\|2. Git]]                                                                                           | Git paso a paso: estados, flujo básico, historial, deshacer cambios, ramas, conflictos, repositorios remotos y Git flow.                                  | <ul><li>RA4.f</li><li>RA4.h</li></ul>               |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 04/3. Refactorización\|3. Refactorización]]                                                                   | Qué es la refactorización, sus patrones más usuales, cómo aplicarlos con las herramientas del IDE y los principios SOLID.                                 | <ul><li>RA4.a</li><li>RA4.b</li><li>RA4.e</li></ul> |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 04/4. Optimización - Análisis estático y deuda técnica\|4. Optimización - Análisis estático y deuda técnica]] | Analizadores de código, su configuración y el concepto de deuda técnica.                                                                                  | <ul><li>RA4.c</li><li>RA4.d</li></ul>               |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 04/5. Documentación\|5. Documentación]]                                                                       | Documentación de las clases con Javadoc: comentarios, plantillas, generación desde el terminal y el IDE, y documentación viva.                            | <ul><li>RA4.g</li></ul>                             |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 04/6. Trabajo colaborativo con repositorios remotos\|6. Trabajo colaborativo con repositorios remotos]]       | Trabajo en equipo con un repositorio remoto en GitHub: clonar, sincronizar, ramas, pull requests y revisiones, desde el terminal y desde el IDE.          | <ul><li>RA4.f</li><li>RA4.h</li></ul>               |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 04/7. Integración continua\|7. Integración continua]]                                                         | Qué es la integración continua y cómo configurar con GitHub Actions un flujo que compila, prueba y analiza un proyecto Maven en cada push y pull request. | <ul><li>RA4.i</li><li>RA4.b</li></ul>               |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 04/Anexos\|Anexos]]                                                                                           | Ejemplo de fichero .gitignore para un proyecto Maven.                                                                                                     | <ul><li>RA4.f</li></ul>                             |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 04/Referencias\|Referencias]]                                                                                 | Fuentes y recursos de la unidad.                                                                                                                          | \-                                                  |

{ .block-language-dataview}


---

<p><span>⬅️ <strong>Anterior:</strong> <a data-tooltip-position="top" aria-label="Asignaturas/1DAM_ED/Unidades/Unidad 03/Unidad 03 - Pruebas y depuración.md" data-href="Asignaturas/1DAM_ED/Unidades/Unidad 03/Unidad 03 - Pruebas y depuración.md" href="Asignaturas/1DAM_ED/Unidades/Unidad 03/Unidad 03 - Pruebas y depuración.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 03 - Pruebas y depuración</a> | 🏠 <strong>Libro:</strong> <a data-tooltip-position="top" aria-label="Libros/Entornos de desarrollo (1º DAM, 1º DAW).md" data-href="Libros/Entornos de desarrollo (1º DAM, 1º DAW).md" href="Libros/Entornos de desarrollo (1º DAM, 1º DAW).md" class="internal-link" target="_blank" rel="noopener nofollow">Entornos de desarrollo (1º DAM, 1º DAW)</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="Asignaturas/1DAM_ED/Unidades/Unidad 05/Unidad 05 - Diagramas de clases.md" data-href="Asignaturas/1DAM_ED/Unidades/Unidad 05/Unidad 05 - Diagramas de clases.md" href="Asignaturas/1DAM_ED/Unidades/Unidad 05/Unidad 05 - Diagramas de clases.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 05 - Diagramas de clases</a> ➡️</span></p>
