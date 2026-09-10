---
{"dg-publish":true,"permalink":"/1-dam-programacion/unidades/unidad-5-estructuras-de-almacenamiento/","tags":["java/estructuras_de_datos"],"dg-note-properties":{"modulo":"[[Módulos/Programación]]","libro":"[[Apuntes/Programación (1º DAM, 1º DAW)]]","descripcion":"Hasta ahora hemos tratado cada dato de forma atómica: una variable que contiene un dato primitivo o apunta a un objeto en memoria. En esta unidad veremos cómo usar distintas estructuras para almacenar y organizar un conjunto de esos datos en un solo sitio.","orden":5,"tags":["java/estructuras_de_datos"]}}
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

Bloque de contenidos básicos: **Aplicación de las estructuras de almacenamiento:**  
- **Estructuras. Definición y uso.**  
- **Concepto de Array. Tipos. Creación de arrays. Recorrido y búsquedas en un array.**  
- **Arrays multidimensionales.**  
- **Cadenas de caracteres. Uso de las cadenas. Recorrido y manipulación.**  
- **Uso de expresiones regulares en cadenas de texto.**  
- **Concepto de Lista. Tipos. Operaciones.**  
- **Aplicación del estándar XML.**  
- **Concepto de XML Estructura de un documento XML.**  
- **Especificación de documentos. DTD y XSD.**  
- **Clases para la creación y manipulación de documentos XML.**

| Peso RA en trim. | RA asociado | Periodo |  | Criterios de evaluación | Peso CE en la RA | Peso RA en módulo |
| :---: | :---- | :---: | :---: | :---- | :---: | :---: |
| 50,00% | RA 6. Escribe programas que manipulen información seleccionando y utilizando tipos avanzados de datos. | 14/12/2026 | 29/1/2027 | a) Se han escrito programas que utilicen matrices (arrays). | 10,00% | 12,00% |
|  |  |  |  | b) Se han reconocido las librerías de clases relacionadas con tipos de datos avanzados. | 10,00% |  |
|  |  |  |  | c) Se han utilizado listas para almacenar y procesar información. | 10,00% |  |
|  |  |  |  | d) Se han utilizado iteradores para recorrer los elementos de las listas. | 10,00% |  |
|  |  |  |  | e) Se han reconocido las características y ventajas de cada una de las colecciones de datos disponibles. | 10,00% |  |
|  |  |  |  | f) Se han creado clases y métodos genéricos. | 10,00% |  |
|  |  |  |  | g) Se han utilizado expresiones regulares en la búsqueda de patrones en cadenas de texto. | 10,00% |  |
|  |  |  |  | h) Se han identificado las clases relacionadas con el tratamiento de documentos escritos en diferentes lenguajes de intercambio de datos. | 10,00% |  |
|  |  |  |  | i) Se han realizado programas que realicen manipulaciones sobre documentos escritos en diferentes lenguajes de intercambio de datos. | 10,00% |  |
|  |  |  |  | j) Se han utilizado operaciones agregadas para el manejo de información almacenada en colecciones. | 10,00% |  |

---

Llegamos a una de las unidades más relevantes de este curso: las estructuras de datos.

Cualquier programa del mundo real no se hace solo con variables sencillas que contienen números, textos u otros objetos. Se hace manejando **grandes cantidades de esos datos**.

Si hemos de crear una aplicación para gestionar al alumnado de un instituto, por ejemplo, que tiene unos 2000 estudiantes, ¿tendríamos que crear 2000 variables, una para cada objeto `Estudiante`? A todas luces es **inviable**.

En el mundo real creamos una variable que contenga un banco de datos, un conjunto de esos objetos `Estudiante` y que nos permita gestionarlos (leerlos, borrarlos o cambiarlos). Ese "banco de datos" se conoce como **estructura de datos**, y en esta unidad veremos las más relevantes.

---
## Índice de contenidos

| File                                                                                                                | Descripción                                                                                                                                                                                                                                                                                                           |
| ------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[1DAM_Programación/Unidad 05/1. Estructuras de almacenamiento\|1. Estructuras de almacenamiento]]               | Introducción a la unidad. Diferencia entre estructuras estáticsa y dinámicas.                                                                                                                                                                                                                                         |
| [[1DAM_Programación/Unidad 05/2. Arrays unidimensionales (vectores)\|2. Arrays unidimensionales (vectores)]]     | La estructura estática más básica: el array                                                                                                                                                                                                                                                                           |
| [[1DAM_Programación/Unidad 05/3. Arrays bidimensionales (matrices)\|3. Arrays bidimensionales (matrices)]]       | Las matrices son arrays de arrays o, para hacernos una idea mental más clara, son tablas de datos. Dándole dos índices (x e y) accedemos a cada posición.                                                                                                                                                             |
| [[1DAM_Programación/Unidad 05/4. Cadenas o strings\|4. Cadenas o strings]]                                       | Una cadena de texto es un array de caracteres. Pero, al tratarse de un objeto, ofrece muchas funcionalidades ya implementadas en la API de Java. Veamos algunas de ellas.                                                                                                                                             |
| [[1DAM_Programación/Unidad 05/5. Expresiones regulares\|5. Expresiones regulares]]                               | Podemos tratar cadenas de texto identificando patrones.                                                                                                                                                                                                                                                               |
| [[1DAM_Programación/Unidad 05/6. Arrays de objetos\|6. Arrays de objetos]]                                       | Si creamos un array y lo llenamos de objetos, ¿cómo lo gestionamos? Aunque esto pueda parecer harto difícil, puedes dormir con tranquilidad. Se gestionan exactamente igual que los arrays de datos primitivos, solo que aquí en cada posición tienes un objeto. Empieza por ele-, acaba por -fante y tiene trompa... |
| [[1DAM_Programación/Unidad 05/7. Colecciones y listas\|7. Colecciones y listas]]                                 | Podemos tratar cadenas de texto identificando patrones.                                                                                                                                                                                                                                                               |
| [[1DAM_Programación/Unidad 05/8. Comparar objetos\|8. Comparar objetos]]                                         | Los datos primitivos son fáciles de comparar: si dos valores coinciden, son iguales. Pero ¿cómo comparamos dos objetos? Porque cada uno es un conjunto de datos...                                                                                                                                                    |
| [[1DAM_Programación/Unidad 05/9. Clases y métodos con tipos genéricos\|9. Clases y métodos con tipos genéricos]] | Los genéricos nos permiten ampliar el uso de un método o clase a cualquier tipo de objeto.                                                                                                                                                                                                                            |
| [[1DAM_Programación/Unidad 05/10. Enumerados\|10. Enumerados]]                                                   | Los enumerados son una fantástica opción para aglutinar en un mismo sitio un conjunto de constantes relacionadas entre sí, sus valores ¡e incluso sus funcionalidades!                                                                                                                                                |
| [[1DAM_Programación/Unidad 05/11. Hemos aprendido...\|11. Hemos aprendido...]]                                   | Conclusiones de esta unidad                                                                                                                                                                                                                                                                                           |
| [[1DAM_Programación/Unidad 05/Apéndice - los ficheros JAR\|Apéndice - los ficheros JAR]]                         | Un proyecto Java necesita muchos ficheros y configuraciones para funcionar. ¿Cómo nos llevamos todo eso de un equipo a otro? Con ficheros JAR.                                                                                                                                                                        |
| [[1DAM_Programación/Unidad 05/Referencias internas\|Referencias internas]]                                       | Aquí tienes distintas fuentes y referencias documentales para consultar, ahondar y aprender más sobre los temas que hemos tratado en esta unidad                                                                                                                                                                      |
| [[1DAM_Programación/Unidad 05/Referencias\|Referencias]]                                                         | Aquí tienes distintas fuentes y referencias documentales para consultar, ahondar y aprender más sobre los temas que hemos tratado en esta unidad                                                                                                                                                                      |

{ .block-language-dataview}

---

<p><span>⬅️ <strong>Anterior:</strong> <a data-tooltip-position="top" aria-label="1DAM_Programación/Unidades/Unidad 4 - POO. Clases.md" data-href="1DAM_Programación/Unidades/Unidad 4 - POO. Clases.md" href="1DAM_Programación/Unidades/Unidad 4 - POO. Clases.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 4 - POO. Clases</a> | 🏠 <strong>Libro:</strong> <a data-tooltip-position="top" aria-label="Apuntes/Programación (1º DAM, 1º DAW).md" data-href="Apuntes/Programación (1º DAM, 1º DAW).md" href="Apuntes/Programación (1º DAM, 1º DAW).md" class="internal-link" target="_blank" rel="noopener nofollow">Programación (1º DAM, 1º DAW)</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="1DAM_Programación/Unidades/Unidad 6 - Interfaz gráfica de usuario (GUI) - Swing.md" data-href="1DAM_Programación/Unidades/Unidad 6 - Interfaz gráfica de usuario (GUI) - Swing.md" href="1DAM_Programación/Unidades/Unidad 6 - Interfaz gráfica de usuario (GUI) - Swing.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 6 - Interfaz gráfica de usuario (GUI) - Swing</a> ➡️</span></p>
