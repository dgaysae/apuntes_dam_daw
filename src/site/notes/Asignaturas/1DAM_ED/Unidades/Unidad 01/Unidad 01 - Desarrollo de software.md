---
{"dg-publish":true,"dg-permalink":"/apuntes/1-dam-ed/unidades/unidad-01-lenguajes-y-algoritmos/","permalink":"/apuntes/1-dam-ed/unidades/unidad-01-lenguajes-y-algoritmos/","tags":["programación/conceptos_básicos","ingeniería_sw"],"dg-note-properties":{"modulo":"[[Módulos/Entornos de desarrollo]]","libro":"[[Libros/Entornos de desarrollo (1º DAM, 1º DAW)]]","descripcion":"El desarrollo de software: programas y su relación con el hardware, lenguajes y paradigmas, código fuente, objeto y ejecutable, fases del ciclo de vida y metodologías ágiles.","orden":1,"ra":"RA1","tags":["programación/conceptos_básicos","ingeniería_sw"]}}
---


```table-of-contents
```

---

## Introducción

Antes de abrir un entorno de desarrollo y escribir la primera línea de código, conviene entender **qué es un programa**, cómo se relaciona con el **hardware**, qué **lenguajes** podemos usar y qué **fases** recorre un proyecto de software hasta que se pone en funcionamiento.

En esta unidad vas a:

- **Ver lo que pasa por dentro**: qué recursos consume un programa y cómo el código fuente se convierte en un ejecutable, compilando a mano en C y en Java.
- **Comparar lenguajes** escribiendo el mismo programa en C, Java y Python.
- **Recorrer las fases del desarrollo** con un proyecto real y pequeño: una aplicación para reservar aulas del instituto.
- **Investigar las herramientas** que usan los proyectos profesionales (control de versiones, integración continua, IDE, asistentes de IA).
- **Trabajar como un equipo ágil**, con un *sprint* de Scrum y un tablero Kanban.

> [!info] Enfoque clásico
> Algunos apartados incluyen técnicas que se usaban antes (modelo en cascada, herramientas CASE, diagramas de flujo de datos…). Se conservan como contexto y van marcadas con un aviso como este.

> [!quote]- Un poco de historia: la ingeniería del software
> Allá por el año 1963 una muchacha llamada [**Margaret Hamilton**](https://es.wikipedia.org/wiki/Margaret_Hamilton_(cient%C3%ADfica)), matemática y con dotes especiales para las ciencias de la computación, dirigía el desarrollo del software de navegación que usaría la nave de los astronautas del **Programa Espacial Apolo**.
>
> ![ud02_ed_01_Margaret_Hamilton-768x956.gif\|500](/img/user/adjuntos/1DAM_ED/Unidad_02/ud02_ed_01_Margaret_Hamilton-768x956.gif)
> *Margaret Hamilton posando junto al código fuente del sistema de navegación del Apolo impreso en papel.*
>
> Durante su trabajo en la NASA comenzó a asentar unas bases específicas para el proceso de desarrollo de software, proclamando que se trataba de una labor de *ingeniería*. Aunque no se le tomó muy en serio.
>
> En 1968, [**Friedrich L. Bauer**](https://en.wikipedia.org/wiki/Friedrich_L._Bauer), profesor de ciencias de la computación y una de las figuras más relevantes  insistió en usar el término "*ingeniería del software*" en un momento delicado para el mundo de la programación: la **crisis del software**. La ingeniería se postulaba como la solución para evitar una artesanía enrevesada y difícil de escalar, el desorden y la dificultad del mantenimiento y reparación del software.
>
> Friedrich lo hizo en la <abbr title="NATO Software Engineering Conference">Conferencia de software de la OTAN</abbr> en ese mismo año, organizada por él y en la que consiguió la asistencia de gente de la categoría de [**Edsger Dijkstra**](https://es.wikipedia.org/wiki/Edsger_Dijkstra) (pionero en programación estructurada), [**Alan Perlis**](https://es.wikipedia.org/wiki/Alan_Perlis) (primer [Premio Turing](https://es.wikipedia.org/wiki/Premio_Turing) del mundo, muy influyente en tema de compiladores) o Charles Antony Richard Hoare, más conocido como [**Tony Hoare**](https://es.wikipedia.org/wiki/C._A._R._Hoare) (padre del algoritmo *Quicksort*).
>
> El trabajo de todas estas personas demostró que el desarrollo de software tenía todas las cualidades para ser tratado como una rama de ingeniería. Y hoy en día podemos ver el resultado.
>
> Aunque ha llovido bastante desde entonces, y las técnicas y estándares han ido cambiando para amoldarse a la evolución de software y hardware, fueron quienes pusieron los cimientos de lo que hoy asumimos como una profesión técnica. Os recomiendo que echéis un vistazo a su carrera. Merece la pena.

## Datos de la unidad

### RA asociado y criterios de evaluación

**RA 1.** Reconoce los elementos y herramientas que intervienen en el desarrollo de un programa informático, analizando sus características y las fases en las que actúan hasta llegar a su puesta en funcionamiento.

Criterios de evaluación:

- a) Se ha reconocido la relación de los programas con los componentes del sistema informático: memoria, procesador, periféricos, entre otros.
- b) Se han identificado las fases de desarrollo de una aplicación informática.
- c) Se han diferenciado los conceptos de código fuente, objeto y ejecutable.
- d) Se han reconocido las características de la generación de código intermedio para su ejecución en máquinas virtuales.
- e) Se han clasificado los lenguajes de programación, identificando sus características.
- f) Se ha evaluado la funcionalidad ofrecida por las herramientas utilizadas en el desarrollo de software.
- g) Se han identificado las características y escenarios de uso de las metodologías ágiles de desarrollo de software.

### Contenidos básicos

Desarrollo de software:

- Concepto de programa informático.
- Código fuente, código objeto y código ejecutable; tecnologías de virtualización.
- Tipos de lenguajes de programación. Paradigmas.
- Características de los lenguajes más difundidos.
- Fases del desarrollo de una aplicación: análisis, diseño, codificación, pruebas, documentación, explotación y mantenimiento, entre otras.
- Proceso de obtención de código ejecutable a partir del código fuente; herramientas implicadas.
- Metodologías ágiles. Técnicas. Características.

## Índice de contenidos

| File                                                                                                                        | Descripción                                                                                                                                                                                               | Criterios                                                         |
| --------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 01/1. Software y programas\|1. Software y programas]]                               | Qué es el software, software de sistema y de aplicación, y licencias del software (libre, código abierto, propietario y dominio público).                                                                 | <ul><li>RA1.a</li></ul>                                           |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 01/2. Relación hardware-software\|2. Relación hardware-software]]                   | Relación entre los programas y el hardware: arquitectura de Von Neumann, procesador, memoria, buses y periféricos, qué ocurre al ejecutar un programa y el papel del sistema operativo.                   | <ul><li>RA1.a</li></ul>                                           |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 01/3. Algoritmos\|3. Algoritmos]]                                                   | Qué es un algoritmo y cómo se describe con pseudocódigo y diagramas de flujo.                                                                                                                             | <ul><li>RA1.e</li></ul>                                           |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 01/4. Lenguajes de programación\|4. Lenguajes de programación]]                     | Clasificación de los lenguajes de programación por nivel, mecanismo de traducción y propósito; compiladores, intérpretes y máquinas virtuales.                                                            | <ul><li>RA1.c</li><li>RA1.d</li><li>RA1.e</li></ul>               |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 01/5. Paradigmas y lenguajes\|5. Paradigmas y lenguajes]]                           | Paradigmas de programación: estructurada, modular y orientada a objetos.                                                                                                                                  | <ul><li>RA1.e</li></ul>                                           |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 01/6. Ciclo de vida del software\|6. Ciclo de vida del software]]                   | Modelos de ciclo de vida, roles del equipo de desarrollo e introducción a las metodologías ágiles y a las herramientas de apoyo.                                                                          | <ul><li>RA1.b</li><li>RA1.g</li></ul>                             |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 01/7. Metodologías ágiles. Scrum y Kanban\|7. Metodologías ágiles. Scrum y Kanban]] | El manifiesto ágil, Scrum (roles, eventos y artefactos) y Kanban, con su uso en un proyecto real y cuándo conviene cada enfoque.                                                                          | <ul><li>RA1.b</li><li>RA1.g</li></ul>                             |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 01/8. Análisis\|8. Análisis]]                                                       | Fase de análisis: toma de requisitos, planificación y documentación (DFD, diccionario de datos, diagramas E/R).                                                                                           | <ul><li>RA1.b</li></ul>                                           |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 01/9. Diseño\|9. Diseño]]                                                           | Fase de diseño: diseño estructurado y diseño orientado a objetos.                                                                                                                                         | <ul><li>RA1.b</li></ul>                                           |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 01/10. Codificación\|10. Codificación]]                                             | Fase de codificación: código fuente, objeto y ejecutable, máquinas virtuales, frameworks y entornos de ejecución.                                                                                         | <ul><li>RA1.b</li><li>RA1.c</li><li>RA1.d</li><li>RA1.f</li></ul> |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 01/11. Pruebas\|11. Pruebas]]                                                       | Fase de pruebas: comprobar que el software cumple los requisitos.                                                                                                                                         | <ul><li>RA1.b</li></ul>                                           |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 01/12. Documentación\|12. Documentación]]                                           | Fase de documentación: documentación técnica y de usuario.                                                                                                                                                | <ul><li>RA1.b</li></ul>                                           |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 01/13. Explotación\|13. Explotación]]                                               | Fase de explotación: instalación, configuración y puesta en producción.                                                                                                                                   | <ul><li>RA1.b</li></ul>                                           |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 01/14. Mantenimiento\|14. Mantenimiento]]                                           | Fase de mantenimiento: tipos de mantenimiento del software.                                                                                                                                               | <ul><li>RA1.b</li></ul>                                           |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 01/15. Herramientas del desarrollo actual\|15. Herramientas del desarrollo actual]] | Herramientas que se usan hoy en cada fase del desarrollo (IDE, Git, Maven y Gradle, pruebas, integración continua, gestión de tareas, contenedores e IA), un recorrido por todas ellas y cómo evaluarlas. | <ul><li>RA1.f</li><li>RA1.b</li></ul>                             |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 01/Referencias documentales\|Referencias documentales]]                             | Bibliografía y recursos de la unidad, en formato APA.                                                                                                                                                     | \-                                                                |

{ .block-language-dataview}

## Anexos

- [[Asignaturas/1DAM_ED/Unidades/Unidad 01/Unidad 01 - Anexo - Requisitos\|Unidad 01 - Anexo - Requisitos]]
- [[Asignaturas/1DAM_ED/Unidades/Unidad 01/Unidad 01 - Anexo - Enfoque clásico\|Unidad 01 - Anexo - Enfoque clásico]]: lo que se usaba antes (cascada, CASE, DFD, roles tradicionales…).

## Unidad completa

En el siguiente enlace tienes la unidad completa en una sola página, por si quieres imprimirla o pasarla a PDF:

[[Asignaturas/1DAM_ED/Apuntes/Unidad 01-Desarrollo de software\|Unidad 01-Desarrollo de software]]

---

<p><span>🏠 <strong>Libro:</strong> <a data-tooltip-position="top" aria-label="Libros/Entornos de desarrollo (1º DAM, 1º DAW).md" data-href="Libros/Entornos de desarrollo (1º DAM, 1º DAW).md" href="Libros/Entornos de desarrollo (1º DAM, 1º DAW).md" class="internal-link" target="_blank" rel="noopener nofollow">Entornos de desarrollo (1º DAM, 1º DAW)</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="Asignaturas/1DAM_ED/Unidades/Unidad 01/Unidad 01 - Anexo - Requisitos.md" data-href="Asignaturas/1DAM_ED/Unidades/Unidad 01/Unidad 01 - Anexo - Requisitos.md" href="Asignaturas/1DAM_ED/Unidades/Unidad 01/Unidad 01 - Anexo - Requisitos.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 01 - Anexo - Requisitos</a> ➡️</span></p>
