---
{"dg-publish":true,"permalink":"/1-dam-programacion/unidades/unidad-2-estructuras-de-control-calidad-del-software/","tags":["poo","java/estructuras_de_control"],"dg-note-properties":{"modulo":"[[Módulos/Programación]]","libro":"[[Apuntes Programación (1º DAM, 1º DAW)]]","descripcion":"Existen 3 estructuras de control heredadas de la programación estructurada: secuencial, iterativa y selectiva (condicional). Con ellas se puede realizar cualquier programa. También veremos distintas formas de probar nuestro código (alguna de ellas automática).","orden":2,"tags":["poo","java/estructuras_de_control"],"estado":"revisar"}}
---



<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



> [!info]
> &copy; Departamento de Informática del IES Celia Viñas
> ![by-nc-sa.png\|150](/img/user/adjuntos/by-nc-sa.png)
> El contenido original ha sido escrito por &copy; **[Alfredo Moreno Vozmediano](https://www.instagram.com/amvozmediano/)** y está bajo licencia Creative Commons **[Attribution-NonCommercial-ShareAlike 4.0 International](https://creativecommons.org/licenses/by-nc-sa/4.0/)**, que permite su libre distribución, comunicación pública y adaptación sin fines lucrativos, siempre que se cite la autoría y se indique si se han realizado cambios. No se permite el uso comercial.
> Este material toma como base la obra del compañero Alfredo y, con su permiso, se han ido realizando cambios.

</div></div>


| File                                                                                                            | Descripción                                                                                                                                                                                           |
| --------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[1DAM_Programación/Unidad 02/1. La programación estructurada\|1. La programación estructurada]]             | Con solo 3 estructuras de control se puede implementar cualquier programa (hasta ahora se ha hecho así). Esas 3 estructuras se establecieron con el paradigma de programación estructurada.           |
| [[1DAM_Programación/Unidad 02/2. Estructura secuencial\|2. Estructura secuencial]]                           | La estructura de control secuencial es la más simple: las instrucciones se ejecutan en el orden en que se escriben, y cada una se ejecuta cuando la anterior ha acabado.                              |
| [[1DAM_Programación/Unidad 02/3. Estructura selectiva (condicional)\|3. Estructura selectiva (condicional)]] | La estructura de control selectiva, que en adelante conoceremos como CONDICIONAL, permite decidir si un conjunto de instrucciones se ejecutan o no.                                                   |
| [[1DAM_Programación/Unidad 02/4. Estructura repetitiva (bucles)\|4. Estructura repetitiva (bucles)]]         | La estructura de control repetitiva, que en adelante conoceremos como BUCLE, permite repetir la ejecución de un conjunto de instrucciones mientras se cumpla una condición.                           |
| [[1DAM_Programación/Unidad 02/5. Instrucciones de salto\|5. Instrucciones de salto]]                         | Podemos alterar el comportamiento de un bucle mediante las instrucciones de salto.                                                                                                                    |
| [[1DAM_Programación/Unidad 02/6. Reglas de estilo\|6. Reglas de estilo]]                                     | Para facilitar la vida a nuestro yo futuro o a otras personas que puedan ver nuestro código, lo mejor es usar unas reglas a la hora de escribir código para que sea más fácil de entender y mantener. |
| [[1DAM_Programación/Unidad 02/7. Control de excepciones\|7. Control de excepciones]]                         | Veamos cómo controlar errores que harían que nuestro programa se rompiese y finalizase su ejecución.                                                                                                  |
| [[1DAM_Programación/Unidad 02/8. Pruebas\|8. Pruebas]]                                                       | No es recomendable que quien escribe un código, luego lo pruebe para ver si funciona correctamente. Veamos algunas pautas para ello.                                                                  |

{ .block-language-dataview}

---

<p><span>⬅️ <strong>Anterior:</strong> <a data-tooltip-position="top" aria-label="1DAM_Programación/Unidades/Unidad 1 - Introducción a la programación con Java.md" data-href="1DAM_Programación/Unidades/Unidad 1 - Introducción a la programación con Java.md" href="1DAM_Programación/Unidades/Unidad 1 - Introducción a la programación con Java.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 1 - Introducción a la programación con Java</a> | 🏠 <strong>Libro:</strong> <a data-tooltip-position="top" aria-label="Apuntes/Apuntes Programación (1º DAM, 1º DAW).md" data-href="Apuntes/Apuntes Programación (1º DAM, 1º DAW).md" href="Apuntes/Apuntes Programación (1º DAM, 1º DAW).md" class="internal-link" target="_blank" rel="noopener nofollow">Apuntes Programación (1º DAM, 1º DAW)</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos.md" data-href="1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos.md" href="1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 3 - POO. Los objetos</a> ➡️</span></p>
