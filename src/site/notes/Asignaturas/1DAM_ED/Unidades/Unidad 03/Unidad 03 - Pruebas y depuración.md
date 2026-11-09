---
{"dg-publish":true,"dg-permalink":"/apuntes/1-dam-ed/unidades/unidad-04-pruebas-optimizacion-y-documentacion/","permalink":"/apuntes/1-dam-ed/unidades/unidad-04-pruebas-optimizacion-y-documentacion/","tags":["java/ide","java/tests","java/junit"],"dg-note-properties":{"modulo":"[[Módulos/Entornos de desarrollo]]","libro":"[[Libros/Entornos de desarrollo (1º DAM, 1º DAW)]]","descripcion":"Veremos qué son las pruebas de software, cuántos tipos hay y cómo implementar nuestros propios tests unitarios para automatizarlas.","orden":5,"ra":"RA3","tags":["java/ide","java/tests","java/junit"]}}
---


En la [[Asignaturas/1DAM_ED/Unidades/Unidad 02/Unidad 02 - Entornos de desarrollo\|Unidad 02]] aprendimos a escribir y a construir programas con un IDE. Pero que un programa compile no significa que funcione: puede dar resultados incorrectos, fallar con ciertos datos o dejar de funcionar cuando cambiamos otra parte del código. Para comprobarlo, el código se somete a **pruebas**, y cuando algo falla, se busca la causa con el **depurador**.

Probar no es «ejecutar el programa a ver qué pasa». Tampoco es inundar el código de `System.out.pringln` mostrando resultados por todas partes. Es una tarea que se **planifica**, con casos de prueba diseñados para encontrar errores, y que hoy se **automatiza** para repetirla cada vez que el código cambia. Así, los errores se detectan pronto, cuando corregirlos es más barato.

En esta unidad vamos a **verificar** el funcionamiento de programas diseñando y realizando pruebas:

* **Conocer** los tipos de pruebas (funcionales, estructurales, de regresión…) y cuándo se usa cada uno.
* **Diseñar casos de prueba** con técnicas como las clases de equivalencia, los valores límite o la cobertura del código.
* **Depurar** con el IDE: puntos de ruptura, ejecución paso a paso y consulta y modificación de variables en tiempo de ejecución.
* **Automatizar** pruebas unitarias con JUnit y **aislar** los componentes con dobles de prueba.
* **Documentar** las incidencias detectadas para poder corregirlas.

## Datos de la unidad

### RA asociado y criterios de evaluación

**RA 3.** Verifica el funcionamiento de programas diseñando y realizando pruebas.

Criterios de evaluación:

- a) Se han identificado los diferentes tipos de pruebas.
- b) Se han definido casos de prueba.
- c) Se han identificado las herramientas de depuración y prueba de aplicaciones ofrecidas por el entorno de desarrollo.
- d) Se han utilizado herramientas de depuración para definir puntos de ruptura y seguimiento.
- e) Se han utilizado las herramientas de depuración para examinar y modificar el comportamiento de un programa en tiempo de ejecución.
- f) Se han efectuado pruebas unitarias de clases y funciones.
- g) Se han implementado pruebas automáticas.
- h) Se han documentado las incidencias detectadas.
- i) Se han utilizado dobles de prueba para aislar los componentes durante las pruebas.

### Contenidos básicos

Diseño y realización de pruebas:

- Planificación de Pruebas.
- Tipos de pruebas: Funcionales, estructurales y regresión, entre otras.
- Procedimientos y casos de prueba.
- Pruebas de Código: Cubrimiento, valores límite y clases de equivalencia, entre otras.
- Pruebas unitarias; herramientas de automatización.
- Documentación de las incidencias.
- Dobles de prueba. Tipos. Características.

## Índice de contenidos

| File                                                                                                                                            | Descripción                                                                                                                                                                      | Criterios                                           |
| ----------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------- |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/1. Planificación de las pruebas\|1. Planificación de las pruebas]]                                   | Cómo se planifican las pruebas de software: la pirámide de pruebas, el desarrollo guiado por pruebas (TDD) y la verificación continua con CI/CD.                                 | <ul><li>RA3.a</li><li>RA3.g</li></ul>               |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/2. Tipos de pruebas\|2. Tipos de pruebas]]                                                           | Los dos enfoques principales para probar software: las pruebas de caja blanca, que analizan la lógica interna, y las de caja negra, que comprueban el comportamiento externo.    | <ul><li>RA3.a</li></ul>                             |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/3. El flujo de pruebas\|3. El flujo de pruebas]]                                                     | Las fases de prueba (unitaria, de integración, de validación y de sistema) y cómo han pasado de hacerse al final del desarrollo a hacerse lo antes posible (Shift-Left Testing). | <ul><li>RA3.a</li><li>RA3.b</li></ul>               |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/4. Pruebas de caja blanca - análisis estructural\|4. Pruebas de caja blanca - análisis estructural]] | Diseño de pruebas de caja blanca con el método del camino básico: grafos de flujo, complejidad ciclomática, caminos independientes y casos de prueba.                            | <ul><li>RA3.b</li></ul>                             |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/5. Pruebas funcionales (caja negra\|5. Pruebas funcionales (caja negra]]                             | Diseño de pruebas de caja negra con clases de equivalencia y análisis de valores límite, y su aplicación en pruebas unitarias siguiendo el ciclo TDD.                            | <ul><li>RA3.b</li><li>RA3.f</li></ul>               |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/6. Pruebas de regresión\|6. Pruebas de regresión]]                                                   | Qué son las pruebas de regresión, por qué conviene automatizarlas y cómo elegir qué tests ejecutar tras cada cambio en el código.                                                | <ul><li>RA3.a</li><li>RA3.g</li></ul>               |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/7. Herramientas de depuración\|7. Herramientas de depuración]]                                       | Las herramientas de depuración que ofrecen los IDE: puntos de ruptura, tipos de ejecución paso a paso y examinadores de variables.                                               | <ul><li>RA3.c</li><li>RA3.d</li><li>RA3.e</li></ul> |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/8. Depuración estándar en el IDE\|8. Depuración estándar en el IDE]]                                 | El ciclo básico de depuración en el IDE: colocar breakpoints, iniciar el modo debug, avanzar con Step Over, Step Into y Step Out e inspeccionar las variables.                   | <ul><li>RA3.d</li><li>RA3.e</li></ul>               |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/9. Depuración avanzada (debugging)\|9. Depuración avanzada (debugging)]]                             | Técnicas de depuración avanzada: puntos de ruptura condicionales, watchpoints y depuración remota.                                                                               | <ul><li>RA3.d</li><li>RA3.e</li></ul>               |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/10. Herramientas de testeo\|10. Herramientas de testeo]]                                             | Las principales herramientas y frameworks para hacer pruebas de software, como JUnit o TestNG, y sus características.                                                            | <ul><li>RA3.c</li></ul>                             |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/11. Automatización de pruebas\|11. Automatización de pruebas]]                                       | Cómo automatizar pruebas unitarias con JUnit: anotaciones, aserciones, pruebas de excepciones y ejecución de los tests con Maven.                                                | <ul><li>RA3.f</li><li>RA3.g</li></ul>               |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/12. Documentación e informes\|12. Documentación e informes]]                                         | Cómo documentar las pruebas y sus resultados: escenarios para el cliente con BDD y Gherkin, y registro, ciclo de vida y seguimiento de las incidencias.                          | <ul><li>RA3.g</li><li>RA3.h</li></ul>               |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/13. Dobles de prueba\|13. Dobles de prueba]]                                                         | Qué son los dobles de prueba, sus tipos (dummy, stub, spy, mock y fake) y cómo usarlos con Mockito para aislar la clase que se prueba.                                           | <ul><li>RA3.i</li></ul>                             |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/Referencias documentales\|Referencias documentales]]                                                 | Fuentes y recursos de la unidad (documentación, libros y vídeos) sobre pruebas de software, JUnit, Maven, Mockito y gestión de incidencias.                                      | \-                                                  |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/Anexos\|Anexos]]                                                                                     | Material complementario de la unidad: el algoritmo del adivinador de números, usado en los ejemplos de pruebas de caja blanca.                                                   | <ul><li>RA3.b</li></ul>                             |

{ .block-language-dataview}


## Unidad completa

En el siguiente enlace tienes la unidad completa en una sola página, por si quieres imprimirla o pasarla a PDF:

[[Asignaturas/1DAM_ED/Apuntes/Unidad 03-Pruebas y depuración\|Unidad 03-Pruebas y depuración]]

---

<p><span>⬅️ <strong>Anterior:</strong> <a data-tooltip-position="top" aria-label="Asignaturas/1DAM_ED/Unidades/Unidad 02/Unidad 02 - Entornos de desarrollo.md" data-href="Asignaturas/1DAM_ED/Unidades/Unidad 02/Unidad 02 - Entornos de desarrollo.md" href="Asignaturas/1DAM_ED/Unidades/Unidad 02/Unidad 02 - Entornos de desarrollo.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 02 - Entornos de desarrollo</a> | 🏠 <strong>Libro:</strong> <a data-tooltip-position="top" aria-label="Libros/Entornos de desarrollo (1º DAM, 1º DAW).md" data-href="Libros/Entornos de desarrollo (1º DAM, 1º DAW).md" href="Libros/Entornos de desarrollo (1º DAM, 1º DAW).md" class="internal-link" target="_blank" rel="noopener nofollow">Entornos de desarrollo (1º DAM, 1º DAW)</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="Asignaturas/1DAM_ED/Unidades/Unidad 04/Unidad 04 - Optimización, control de versiones e integración continua.md" data-href="Asignaturas/1DAM_ED/Unidades/Unidad 04/Unidad 04 - Optimización, control de versiones e integración continua.md" href="Asignaturas/1DAM_ED/Unidades/Unidad 04/Unidad 04 - Optimización, control de versiones e integración continua.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 04 - Optimización, control de versiones e integración continua</a> ➡️</span></p>
