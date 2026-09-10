---
{"dg-publish":true,"permalink":"/1-dam-programacion/unidades/unidad-2-estructuras-de-control-calidad-del-software/","tags":["programación/poo","java/estructuras_de_control"],"dg-note-properties":{"modulo":"[[Módulos/Programación]]","libro":"[[Apuntes/Programación (1º DAM, 1º DAW)]]","descripcion":"Existen 3 estructuras de control heredadas de la programación estructurada: secuencial, iterativa y selectiva (condicional). Con ellas se puede realizar cualquier programa. También veremos distintas formas de probar nuestro código (alguna de ellas automática).","orden":2,"tags":["programación/poo","java/estructuras_de_control"],"estado":"revisar"}}
---



<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



> [!info]
> &copy; Departamento de Informática del IES Celia Viñas
> ![by-nc-sa.png|150](https://upload.wikimedia.org/wikipedia/commons/4/4b/CC_BY-NC-SA.svg)
> 
> El contenido original ha sido escrito por &copy; **[Alfredo Moreno Vozmediano](https://www.instagram.com/amvozmediano/)** y está bajo licencia Creative Commons **[Attribution-NonCommercial-ShareAlike 4.0 International](https://creativecommons.org/licenses/by-nc-sa/4.0/)**, que permite su libre distribución, comunicación pública y adaptación sin fines lucrativos, siempre que se cite la autoría y se indique si se han realizado cambios. No se permite el uso comercial.
> Este material toma como base la obra del compañero Alfredo y, con su permiso, se han ido realizando cambios.

</div></div>



```table-of-contents
```

---
## Datos de la unidad

La siguiente tabla muestra los contenidos básicos de la norma educativa que contempla esta unidad, al igual que el objetivo o RA que se quiere alcanzar y los criterios de evaluación que se seguirán para ello.

Bloque de contenidos básicos: **Uso de estructuras de control:**  
- **Estructuras de selección.**  
- **Estructuras de repetición.**  
- **Estructuras de salto.**  
- **Control de excepciones.**  
- **Depuración de programas.**  
- **El depurador como herramienta de control de errores.**  
- **Documentación de programas.**  
- **Documentación interna, comentarios.**  
- **Documentación externa, diagramas de clases, requisitos, guías, etc.**

| Peso RA en trim. | RA asociado | Periodo |  | Criterios de evaluación | Peso CE en la RA | Peso RA en módulo |
| :---: | :---- | :---: | :---: | :---- | :---: | :---: |
| 24,39% | RA 3. Escribe y depura código, analizando y utilizando las estructuras de control del lenguaje. | 28/09/2026 | 23/10/2026 | a) Se ha escrito y probado código que haga uso de estructuras de selección. | 10,00% | 10,00% |
|  |  |  |  | b) Se han utilizado estructuras de repetición. | 10,00% |  |
|  |  |  |  | c) Se han reconocido las posibilidades de las sentencias de salto. | 10,00% |  |
|  |  |  |  | d) Se ha escrito código utilizando control de excepciones. | 15,00% |  |
|  |  |  |  | e) Se han creado programas ejecutables utilizando diferentes estructuras de control. | 15,00% |  |
|  |  |  |  | f) Se han probado y depurado los programas. | 5,00% |  |
|  |  |  |  | g) Se ha comentado y documentado el código. | 10,00% |  |
|  |  |  |  | h) Se han creado excepciones. | 15,00% |  |
|  |  |  |  | i) Se han utilizado aserciones para la detección y corrección de errores durante la fase de desarrollo. | 10,00% |  |

---
## Índice de contenidos

| File                                                                                                            | Descripción                                                                                                                                                                                           |
| --------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[1DAM_Programación/Unidad 02/1. La programación estructurada\|1. La programación estructurada]]             | Con solo 3 estructuras de control se puede implementar cualquier programa (hasta ahora se ha hecho así). Esas 3 estructuras se establecieron con el paradigma de programación estructurada.           |
| [[1DAM_Programación/Unidad 02/2. Estructura secuencial\|2. Estructura secuencial]]                           | La estructura de control secuencial es la más simple: las instrucciones se ejecutan en el orden en que se escriben, y cada una se ejecuta cuando la anterior ha acabado.                              |
| [[1DAM_Programación/Unidad 02/3. Estructura selectiva (condicional)\|3. Estructura selectiva (condicional)]] | La estructura de control selectiva, que en adelante conoceremos como CONDICIONAL, permite decidir si un conjunto de instrucciones se ejecutan o no.                                                   |
| [[1DAM_Programación/Unidad 02/4. Estructura repetitiva (bucles)\|4. Estructura repetitiva (bucles)]]         | La estructura de control repetitiva, que en adelante conoceremos como BUCLE, permite repetir la ejecución de un conjunto de instrucciones mientras se cumpla una condición.                           |
| [[1DAM_Programación/Unidad 02/5. Instrucciones de salto\|5. Instrucciones de salto]]                         | Podemos alterar el comportamiento de un bucle mediante las instrucciones de salto.                                                                                                                    |
| [[1DAM_Programación/Unidad 02/6. Reglas de estilo\|6. Reglas de estilo]]                                     | Para facilitar la vida a nuestro yo futuro o a otras personas que puedan ver nuestro código, lo mejor es usar unas reglas a la hora de escribir código para que sea más fácil de entender y mantener. |
| [[1DAM_Programación/Unidad 02/7. Excepciones\|7. Excepciones]]                                               | Veamos cómo controlar errores que harían que nuestro programa se rompiese y finalizase su ejecución.                                                                                                  |
| [[1DAM_Programación/Unidad 02/8. Pruebas\|8. Pruebas]]                                                       | No es recomendable que quien escribe un código, luego lo pruebe para ver si funciona correctamente. Veamos algunas pautas para ello.                                                                  |
| [[1DAM_Programación/Unidad 02/Referencias\|Referencias]]                                                     | No es recomendable que quien escribe un código, luego lo pruebe para ver si funciona correctamente. Veamos algunas pautas para ello.                                                                  |

{ .block-language-dataview}

---

<p><span>⬅️ <strong>Anterior:</strong> <a data-tooltip-position="top" aria-label="1DAM_Programación/Unidades/Unidad 1 - Introducción a la programación con Java.md" data-href="1DAM_Programación/Unidades/Unidad 1 - Introducción a la programación con Java.md" href="1DAM_Programación/Unidades/Unidad 1 - Introducción a la programación con Java.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 1 - Introducción a la programación con Java</a> | 🏠 <strong>Libro:</strong> <a data-tooltip-position="top" aria-label="Apuntes/Programación (1º DAM, 1º DAW).md" data-href="Apuntes/Programación (1º DAM, 1º DAW).md" href="Apuntes/Programación (1º DAM, 1º DAW).md" class="internal-link" target="_blank" rel="noopener nofollow">Programación (1º DAM, 1º DAW)</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos.md" data-href="1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos.md" href="1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 3 - POO. Los objetos</a> ➡️</span></p>
