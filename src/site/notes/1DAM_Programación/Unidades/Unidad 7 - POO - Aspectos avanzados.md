---
{"dg-publish":true,"permalink":"/1-dam-programacion/unidades/unidad-7-poo-aspectos-avanzados/","tags":["programación/poo","java/poo","java/poo/clases"],"dg-note-properties":{"modulo":"[[Módulos/Programación]]","libro":"[[Apuntes/Programación (1º DAM, 1º DAW)]]","descripcion":"Vamos a dar un paso más en conceptos más avanzados de la POO.","orden":9,"tags":["programación/poo","java/poo","java/poo/clases"],"estado":"revisar"}}
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

Bloque de contenidos básicos: **Utilización avanzada de clases:**  
- **Composición de clases.**  
- **Herencia.**  
- **Superclases y subclases.**  
- **Clases y métodos abstractos y finales.**  
- **Sobreescritura de métodos.**  
- **Constructores y herencia.**

| Peso RA en trim. | RA asociado | Periodo |  | Criterios de evaluación | Peso CE en la RA | Peso RA en módulo |
| :---: | :---- | :---: | :---: | :---- | :---: | :---: |
| 42,86% | RA 7. Desarrolla programas aplicando características avanzadas de los lenguajes orientados a objetos y del entorno de programación. | 2/3/2027 | 19/3/2027 | a) Se han identificado los conceptos de herencia, superclase y subclase. | 10,00% | 15,00% |
|  |  |  |  | b) Se han utilizado modificadores para bloquear y forzar la herencia de clases y métodos. | 10,00% |  |
|  |  |  |  | c) Se ha reconocido la incidencia de los constructores en la herencia. | 10,00% |  |
|  |  |  |  | d) Se han creado clases heredadas que sobrescriban la implementación de métodos de la superclase. | 10,00% |  |
|  |  |  |  | e) Se han diseñado y aplicado jerarquías de clases. | 10,00% |  |
|  |  |  |  | f) Se han probado y depurado las jerarquías de clases. | 10,00% |  |
|  |  |  |  | g) Se han realizado programas que implementen y utilicen jerarquías de clases. | 10,00% |  |
|  |  |  |  | h) Se ha comentado y documentado el código. | 10,00% |  |
|  |  |  |  | i) Se han identificado y evaluado los escenarios de uso de interfaces. | 10,00% |  |
|  |  |  |  | j) Se han identificado y evaluado los escenarios de utilización de la herencia y la composición. | 10,00% |  |

---
## Índice de contenidos

| File                                                                                                                                                                                  | Descripción                                                                                                                                      |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| [[1DAM_Programación/Unidad 07/1. Wrappers\|1. Wrappers]]                                                                                                                           | Todo en Java son objetos. Y los que no lo son, pueden serlo gracias a los wrappers.                                                              |
| [[1DAM_Programación/Unidad 07/2. Excepciones\|2. Excepciones]]                                                                                                                     | ¿Creías que ya sabías todo sobre las excepciones? Aquí veremos cómo sacarle aún más jugo.                                                        |
| [[1DAM_Programación/Unidad 07/3. La API estándar de Java\|3. La API estándar de Java]]                                                                                             | De entras las muchas abstracciones que incluye la API de Java, vamos a ver cómo manejar las fechas.                                              |
| [[1DAM_Programación/Unidad 07/5. Expresiones lambda, clases anónimas y programación funcional con Java\|5. Expresiones lambda, clases anónimas y programación funcional con Java]] | ¡Vamos de lleno con la programación funcional!                                                                                                   |
| [[1DAM_Programación/Unidad 07/6. Comparable vs Comparator\|6. Comparable vs Comparator]]                                                                                           | ¡Vamos de lleno con la programación funcional!                                                                                                   |
| [[1DAM_Programación/Unidad 07/7. Reflections\|7. Reflections]]                                                                                                                     | Hay formas de "excavar" en una clase para descubrir cosas de ella o para guardar cosas.                                                          |
| [[1DAM_Programación/Unidad 07/8. El sistema de módulos de Java\|8. El sistema de módulos de Java]]                                                                                 | La forma en que Java gestiona sus ficheros es a través de los módulos.                                                                           |
| [[1DAM_Programación/Unidad 07/Referencias\|Referencias]]                                                                                                                           | Aquí tienes distintas fuentes y referencias documentales para consultar, ahondar y aprender más sobre los temas que hemos tratado en esta unidad |

{ .block-language-dataview}

---

<p><span>⬅️ <strong>Anterior:</strong> <a data-tooltip-position="top" aria-label="1DAM_Programación/Unidades/Unidad 6 - Flujos y ficheros.md" data-href="1DAM_Programación/Unidades/Unidad 6 - Flujos y ficheros.md" href="1DAM_Programación/Unidades/Unidad 6 - Flujos y ficheros.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 6 - Flujos y ficheros</a> | 🏠 <strong>Libro:</strong> <a data-tooltip-position="top" aria-label="Apuntes/Programación (1º DAM, 1º DAW).md" data-href="Apuntes/Programación (1º DAM, 1º DAW).md" href="Apuntes/Programación (1º DAM, 1º DAW).md" class="internal-link" target="_blank" rel="noopener nofollow">Programación (1º DAM, 1º DAW)</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="1DAM_Programación/Unidades/Unidad 8 - Bases de datos.md" data-href="1DAM_Programación/Unidades/Unidad 8 - Bases de datos.md" href="1DAM_Programación/Unidades/Unidad 8 - Bases de datos.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 8 - Bases de datos</a> ➡️</span></p>
