---
{"dg-publish":true,"dg-permalink":"/apuntes/1-dam-ed/unidades/unidad-04-pruebas-optimizacion-y-documentacion/","permalink":"/apuntes/1-dam-ed/unidades/unidad-04-pruebas-optimizacion-y-documentacion/","tags":["java/ide","java/tests","java/junit"],"dg-note-properties":{"modulo":"[[Módulos/Entornos de desarrollo]]","libro":"[[Libros/Entornos de desarrollo (1º DAM, 1º DAW)]]","descripcion":"Veremos qué son las pruebas de software, cuántos tipos hay y cómo implementar nuestros propios tests unitarios para automatizarlas.","orden":5,"ra":"RA3","tags":["java/ide","java/tests","java/junit"]}}
---


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

| File                                                                                                                                            | Descripción                                                                                                                            | Criterios                                           |
| ----------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------- |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/1. Planificación de las pruebas\|1. Planificación de las pruebas]]                                   | ...                                                                                                                                    | <ul><li>RA3.a</li><li>RA3.g</li></ul>               |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/2. Tipos de pruebas\|2. Tipos de pruebas]]                                                           | ...                                                                                                                                    | <ul><li>RA3.a</li></ul>                             |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/3. El flujo de pruebas\|3. El flujo de pruebas]]                                                     | ...                                                                                                                                    | <ul><li>RA3.a</li><li>RA3.b</li></ul>               |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/4. Pruebas de caja blanca - análisis estructural\|4. Pruebas de caja blanca - análisis estructural]] | ...                                                                                                                                    | <ul><li>RA3.b</li></ul>                             |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/5. Pruebas funcionales (caja negra\|5. Pruebas funcionales (caja negra]]                             | ...                                                                                                                                    | <ul><li>RA3.b</li><li>RA3.f</li></ul>               |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/6. Pruebas de regresión\|6. Pruebas de regresión]]                                                   | ...                                                                                                                                    | <ul><li>RA3.a</li><li>RA3.g</li></ul>               |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/7. Herramientas de depuración\|7. Herramientas de depuración]]                                       | ...                                                                                                                                    | <ul><li>RA3.c</li><li>RA3.d</li><li>RA3.e</li></ul> |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/8. Depuración estándar en el IDE\|8. Depuración estándar en el IDE]]                                 | ...                                                                                                                                    | <ul><li>RA3.d</li><li>RA3.e</li></ul>               |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/9. Depuración avanzada (debugging)\|9. Depuración avanzada (debugging)]]                             | ...                                                                                                                                    | <ul><li>RA3.d</li><li>RA3.e</li></ul>               |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/10. Herramientas de testeo\|10. Herramientas de testeo]]                                             | ...                                                                                                                                    | <ul><li>RA3.c</li></ul>                             |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/11. Automatización de pruebas\|11. Automatización de pruebas]]                                       | ...                                                                                                                                    | <ul><li>RA3.f</li><li>RA3.g</li></ul>               |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/12. Documentación e informes\|12. Documentación e informes]]                                         | ...                                                                                                                                    | <ul><li>RA3.g</li><li>RA3.h</li></ul>               |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/13. Dobles de prueba\|13. Dobles de prueba]]                                                         | Qué son los dobles de prueba, sus tipos (dummy, stub, spy, mock y fake) y cómo usarlos con Mockito para aislar la clase que se prueba. | <ul><li>RA3.i</li></ul>                             |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/Referencias documentales\|Referencias documentales]]                                                 | ...                                                                                                                                    | \-                                                  |
| [[Asignaturas/1DAM_ED/Apuntes/Unidad 03/Anexos\|Anexos]]                                                                                     | ...                                                                                                                                    | <ul><li>RA3.b</li></ul>                             |

{ .block-language-dataview}


---

<p><span>⬅️ <strong>Anterior:</strong> <a data-tooltip-position="top" aria-label="Asignaturas/1DAM_ED/Unidades/Unidad 02/Unidad 02 - Entornos de desarrollo.md" data-href="Asignaturas/1DAM_ED/Unidades/Unidad 02/Unidad 02 - Entornos de desarrollo.md" href="Asignaturas/1DAM_ED/Unidades/Unidad 02/Unidad 02 - Entornos de desarrollo.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 02 - Entornos de desarrollo</a> | 🏠 <strong>Libro:</strong> <a data-tooltip-position="top" aria-label="Libros/Entornos de desarrollo (1º DAM, 1º DAW).md" data-href="Libros/Entornos de desarrollo (1º DAM, 1º DAW).md" href="Libros/Entornos de desarrollo (1º DAM, 1º DAW).md" class="internal-link" target="_blank" rel="noopener nofollow">Entornos de desarrollo (1º DAM, 1º DAW)</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="Asignaturas/1DAM_ED/Unidades/Unidad 04/Unidad 04 - Optimización, control de versiones e integración continua.md" data-href="Asignaturas/1DAM_ED/Unidades/Unidad 04/Unidad 04 - Optimización, control de versiones e integración continua.md" href="Asignaturas/1DAM_ED/Unidades/Unidad 04/Unidad 04 - Optimización, control de versiones e integración continua.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 04 - Optimización, control de versiones e integración continua</a> ➡️</span></p>
