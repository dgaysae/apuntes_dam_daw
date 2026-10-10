---
{"dg-publish":true,"dg-permalink":"/apuntes/2-dam-pmdm/unidades/unidad-03-conceptos-avanzados/","permalink":"/apuntes/2-dam-pmdm/unidades/unidad-03-conceptos-avanzados/","tags":["kotlin"],"dg-note-properties":{"modulo":"[[Módulos/PMDM]]","libro":"[[Libros/PMDM (2º DAM)]]","descripcion":"Veamos Kotlin en mayor profundidad. Funciones de extensión, lambdas, etc.","orden":3,"tags":["kotlin"]}}
---



<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



> [!info]
> **PMDP - Apuntes**  © 2024 by Diego G. S. is licensed under CC BY-NC-SA 4.0. To view a copy of this license, visit https://creativecommons.org/licenses/by-nc-sa/4.0/
> ![by-nc-sa.png|150](https://upload.wikimedia.org/wikipedia/commons/4/4b/CC_BY-NC-SA.svg)
> 
> El contenido original ha sido redactado por estudiantes del curso de 2º DAM de [**IES Celia Viñas**](https://iescelia.org/) (curso 2024-25):
> * [Develatter - Alejandro López Martínez](https://www.linkedin.com/in/develatter/) | [Github](https://github.com/develatter/) | [Instagram](https://www.instagram.com/develatter/)
> * Juan González Cobo
> * [Juan Diego Rondón Bedoya](https://www.linkedin.com/in/juandiegorondon/)
> 
>  y por el profesor &copy; **Diego Gay Sáez** y está bajo licencia Creative Commons **[Attribution-NonCommercial-ShareAlike 4.0 International](https://creativecommons.org/licenses/by-nc-sa/4.0/)**, que permite su **libre distribución**, **comunicación pública** y **adaptación sin fines lucrativos**, siempre que se cite la autoría y se indique si se han realizado cambios.
>  **No se permite el uso comercial**.


</div></div>



<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



> [!warning] Aviso importante 
> Para estudiar esta unidad sobre Kotlin, es conveniente tener nociones de programación.
> Si no tienes conocimientos en programación, te recomendamos que empieces [[Libros/Programación (1º DAM, 1º DAW)\|aprendiendo Java]].

</div></div>


| File                                                                                                          | Descripción                                                                    |
| ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [[Asignaturas/2DAM_PMDM/Apuntes/Unidad 03/1. Funciones de extensión\|1. Funciones de extensión]]           | Cómo extender la funcionalidad de clases existentes, incluso de la propia API. |
| [[Asignaturas/2DAM_PMDM/Apuntes/Unidad 03/2. Funciones de orden superior\|2. Funciones de orden superior]] | Funciones especiales en Kotlin.                                                |
| [[Asignaturas/2DAM_PMDM/Apuntes/Unidad 03/3. Funciones como parámetros\|3. Funciones como parámetros]]     | Funciones pasadas como parámetros a otras funciones.                           |
| [[Asignaturas/2DAM_PMDM/Apuntes/Unidad 03/4. Funciones como resultado\|4. Funciones como resultado]]       | Funciones que devuelven otras funciones como resultado.                        |
| [[Asignaturas/2DAM_PMDM/Apuntes/Unidad 03/5. Lambdas\|5. Lambdas]]                                         | Tipos de datos en Kotlin.                                                      |
| [[Asignaturas/2DAM_PMDM/Apuntes/Unidad 03/6. Typealias\|6. Typealias]]                                     | Typealias en Kotlin.                                                           |
| [[Asignaturas/2DAM_PMDM/Apuntes/Unidad 03/7. Fechas\|7. Fechas]]                                           | Fechas en Kotlin.                                                              |

{ .block-language-dataview}

## Unidad completa

En el siguiente enlace tienes la unidad completa en una sola página, por si quieres imprimirla o pasarla a PDF:

[[Asignaturas/2DAM_PMDM/Apuntes/Unidad 03-Conceptos avanzados\|Unidad 03-Conceptos avanzados]]

---

<p><span>⬅️ <strong>Anterior:</strong> <a data-tooltip-position="top" aria-label="Asignaturas/2DAM_PMDM/Unidades/Unidad 02/Unidad 02 - POO en Kotlin.md" data-href="Asignaturas/2DAM_PMDM/Unidades/Unidad 02/Unidad 02 - POO en Kotlin.md" href="Asignaturas/2DAM_PMDM/Unidades/Unidad 02/Unidad 02 - POO en Kotlin.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 02 - POO en Kotlin</a> | 🏠 <strong>Libro:</strong> <a data-tooltip-position="top" aria-label="Libros/PMDM (2º DAM).md" data-href="Libros/PMDM (2º DAM).md" href="Libros/PMDM (2º DAM).md" class="internal-link" target="_blank" rel="noopener nofollow">PMDM (2º DAM)</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="Asignaturas/2DAM_PMDM/Unidades/Unidad 04/Unidad 04 - Estructura de un proyecto Android.md" data-href="Asignaturas/2DAM_PMDM/Unidades/Unidad 04/Unidad 04 - Estructura de un proyecto Android.md" href="Asignaturas/2DAM_PMDM/Unidades/Unidad 04/Unidad 04 - Estructura de un proyecto Android.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 04 - Estructura de un proyecto Android</a> ➡️</span></p>
