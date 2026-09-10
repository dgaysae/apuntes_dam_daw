---
{"dg-publish":true,"permalink":"/1-dam-programacion/unidades/unidad-8-bases-de-datos/","tags":["java/jdbc"],"dg-note-properties":{"modulo":"[[Módulos/Programación]]","libro":"[[Apuntes/Programación (1º DAM, 1º DAW)]]","descripcion":"Veremos cómo conectar nuestra aplicación a distintas bases de datos, como las relacionales.","orden":10,"tags":["java/jdbc"],"estado":"revisar"}}
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

Bloque de contenidos básicos: **Gestión de bases de datos relacionales:**  
- **Conexión con bases de datos relacionales. Características, tipos y métodos de acceso.**  
- **Establecimiento de conexiones. Componentes de acceso a datos.**  
- **Recuperación de información. Selección de registros. Uso de parámetros.**  
- **Manipulación de la información. Altas, bajas y modificaciones.**  
- **Ejecución de consultas sobre la base de datos.**

| Peso RA en trim. | RA asociado | Periodo |  | Criterios de evaluación | Peso CE en la RA | Peso RA en módulo |
| :---: | :---- | :---: | :---: | :---- | :---: | :---: |
| 42,86% | RA 9. Gestiona información almacenada en bases de datos manteniendo la integridad y consistencia de los datos. | 30/3/2027 | 16/4/2027 | a) Se han identificado las características y métodos de acceso a sistemas gestores de bases de datos. | 5,00% | 15,00% |
|  |  |  |  | b) Se han programado conexiones con bases de datos. | 5,00% |  |
|  |  |  |  | c) Se ha escrito código para almacenar información en bases de datos. | 5,00% |  |
|  |  |  |  | d) Se han creado programas para recuperar y mostrar información almacenada en bases de datos. | 5,00% |  |
|  |  |  |  | e) Se han efectuado borrados y modificaciones sobre la información almacenada. | 5,00% |  |
|  |  |  |  | f) Se han creado aplicaciones que muestren la información almacenada en bases de datos. | 5,00% |  |
|  |  |  |  | g) Se han creado aplicaciones para gestionar la información presente en bases de datos. | 70,00% |  |

---

En las primeras unidades hemos hecho programas que usan los datos que hardcodeamos: un array al que le indicábamos los datos, un `List` que rellenábamos con una ristra de objetos, etc.

Después hemos visto los flujos y los ficheros, lo que nos ha permitido extraer los datos en ficheros de datos.

En este capítulo daremos el salto a trabajar con **bases de datos relacionales**, una pieza fundamental en el desarrollo de **aplicaciones reales**. Aprenderás cómo conectar tus programas Java con una base de datos utilizando **`JDBC`** (*Java Database Connectivity*), la API estándar que permite establecer la comunicación, enviar consultas y procesar resultados.

A lo largo del capítulo verás cómo **abrir y gestionar conexiones, ejecutar sentencias SQL y recorrer los datos obtenidos de forma eficiente**. También profundizarás en el manejo de **excepciones** específicas de `JDBC`, esenciales para detectar y tratar errores relacionados con la conexión, las consultas o la integridad de los datos.

Además, explorarás el uso de **metadatos**, que te permitirán obtener información sobre la estructura de la base de datos y adaptarte dinámicamente a ella. Darás un paso más integrando estos datos en interfaces gráficas mediante JavaFX, utilizando componentes como `TableView` para mostrar la información de forma clara y estructurada.

Por último, conocerás el **patrón DAO** (*Data Access Object*), una técnica de diseño que separa la lógica de acceso a datos del resto de la aplicación, facilitando el mantenimiento y la escalabilidad del código.

Este capítulo te permitirá construir aplicaciones más completas, capaces de almacenar, consultar y gestionar información de manera profesional.

¡Vamos a ello!

---
## Índice de contenidos

| File                                                                                                                            | Descripción                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| [[1DAM_Programación/Unidad 09/1. JDBC\|1. JDBC]]                                                                             | ¿Qué es JDBC? Una visión de la API que nos permite conectar nuestra aplicación Java a distintos gestores de bases de datos. |
| [[1DAM_Programación/Unidad 09/2. Utilizando una BD desde Java\|2. Utilizando una BD desde Java]]                             | ...                                                                                                                         |
| [[1DAM_Programación/Unidad 09/3. Manejando excepciones\|3. Manejando excepciones]]                                           | Podemos identificar los errores que nos devuelve cualquier operación contra la base de datos a través de las excepciones.   |
| [[1DAM_Programación/Unidad 09/4. Metadatos\|4. Metadatos]]                                                                   | Desde nuestro programa Java podemos obtener datos de la estructura de una base de datos, de sus tablas, etc.                |
| [[1DAM_Programación/Unidad 09/5. Otras operaciones con la BD\|5. Otras operaciones con la BD]]                               | Transacciones, funciones, etc.                                                                                              |
| [[1DAM_Programación/Unidad 09/6. Interfaz gráfico y acceso a bases de datos\|6. Interfaz gráfico y acceso a bases de datos]] | ...                                                                                                                         |
| [[1DAM_Programación/Unidad 09/7. El patrón DAO\|7. El patrón DAO]]                                                           | ...                                                                                                                         |

{ .block-language-dataview}

---

<p><span>⬅️ <strong>Anterior:</strong> <a data-tooltip-position="top" aria-label="1DAM_Programación/Unidades/Unidad 7 - POO - Aspectos avanzados.md" data-href="1DAM_Programación/Unidades/Unidad 7 - POO - Aspectos avanzados.md" href="1DAM_Programación/Unidades/Unidad 7 - POO - Aspectos avanzados.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 7 - POO - Aspectos avanzados</a> | 🏠 <strong>Libro:</strong> <a data-tooltip-position="top" aria-label="Apuntes/Programación (1º DAM, 1º DAW).md" data-href="Apuntes/Programación (1º DAM, 1º DAW).md" href="Apuntes/Programación (1º DAM, 1º DAW).md" class="internal-link" target="_blank" rel="noopener nofollow">Programación (1º DAM, 1º DAW)</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="1DAM_Programación/Unidades/Unidad 9 - Bases de datos OO y NoSQL.md" data-href="1DAM_Programación/Unidades/Unidad 9 - Bases de datos OO y NoSQL.md" href="1DAM_Programación/Unidades/Unidad 9 - Bases de datos OO y NoSQL.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 9 - Bases de datos OO y NoSQL</a> ➡️</span></p>
