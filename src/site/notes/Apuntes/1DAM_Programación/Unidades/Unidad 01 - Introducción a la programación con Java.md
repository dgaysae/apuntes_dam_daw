---
{"dg-publish":true,"permalink":"/apuntes/1-dam-programacion/unidades/unidad-01-introduccion-a-la-programacion-con-java/","tags":["programación/conceptos_básicos"],"dg-note-properties":{"modulo":"[[Módulos/Programación]]","libro":"[[Libros/Programación (1º DAM, 1º DAW)]]","descripcion":"Conceptos básicos sobre lo que es un programa y un algoritmo. Cómo se representa la información en un ordenador y cómo el código fuente de un programa se transforma en un objeto ejecutable mediante la compilación. También se explican conceptos básicos de ingeniería de software, tipos de lenguajes de programación, paradigmas y se entra tímidamente en el código Java mediante las variables y constantes.","orden":1,"ra":"RA1","tags":["programación/conceptos_básicos"]}}
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

### Contenidos básicos

Identificación de los elementos de un programa informático:
- Estructura y bloques fundamentales.
- Variables.
- Tipos de datos.
- Literales.
- Constantes.
- Operadores y expresiones.
- Conversiones de tipo.
- Comentarios.

### RA asociado y criterios de evaluación

**RA 1. Reconoce la estructura de un programa informático, identificando y relacionando los elementos propios del lenguaje de programación utilizado.**

Criterios de evaluación para el RA:
a) Se han identificado los bloques que componen la estructura de un programa informático.
b) Se han creado proyectos de desarrollo de aplicaciones.
c) Se han utilizado entornos integrados de desarrollo.
d) Se han identificado los distintos tipos de variables y la utilidad específica de cada uno.
e) Se ha modificado el código de un programa para crear y utilizar variables.
f) Se han creado y utilizado constantes y literales.
g) Se han clasificado, reconocido y utilizado en expresiones los operadores del lenguaje.
h) Se ha comprobado el funcionamiento de las conversiones de tipo explícitas e implícitas.
i) Se han introducido comentarios en el código.

---

## Índice de contenidos

| File                                                                                                                              | Descripción                                                                                                                                                                                                                                                                                                                                      |
| --------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [[Apuntes/1DAM_Programación/Unidad 01/1. Introducción\|1. Introducción]]                                                       | Conceptos básicos de la programación: qué es un programa y qué es un algoritmo, y cuáles son las características de un buen algoritmo.                                                                                                                                                                                                           |
| [[Apuntes/1DAM_Programación/Unidad 01/2. Codificación de la información\|2. Codificación de la información]]                   | Cómo se representa la información en un ordenador: el sistema binario y la conversión entre binario y decimal, los sistemas octal y hexadecimal, y el código ASCII.                                                                                                                                                                              |
| [[Apuntes/1DAM_Programación/Unidad 01/3. Resolución de problemas\|3. Resolución de problemas]]                                 | En qué consiste la ingeniería del software, las etapas del ciclo de vida clásico del desarrollo de software (análisis, diseño, codificación, pruebas y mantenimiento) y el papel del programador.                                                                                                                                                |
| [[Apuntes/1DAM_Programación/Unidad 01/4. Estilos y Paradigmas\|4. Estilos y Paradigmas]]                                       | Evolución de los lenguajes de programación desde sus inicios y, consecuentemente, de la forma de programar: crisis del software, programación estructurada, modular, orientada a objetos, etc.                                                                                                                                                   |
| [[Apuntes/1DAM_Programación/Unidad 01/5. Los lenguajes de programación\|5. Los lenguajes de programación]]                     | Clasificación de los lenguajes de programación: lenguajes de bajo y alto nivel. También se ven los componentes que convierte el código fuente en un ejecutable. Se explica la forma particular en la que compila Java.                                                                                                                           |
| [[Apuntes/1DAM_Programación/Unidad 01/6. Herramientas para desarrollar con Java\|6. Herramientas para desarrollar con Java]]   | Herramientas necesarias para programar en Java: el JDK, los editores de texto y los entornos integrados de desarrollo (IDE). Qué es un proyecto, cómo se organiza un proyecto Maven y cómo crearlo en NetBeans.                                                                                                                                  |
| [[Apuntes/1DAM_Programación/Unidad 01/7. Qué es Java\|7. Qué es Java]]                                                         | Qué es Java, cómo comenzó y lo que le diferenciaba del resto de lenguajes existentes hasta la época. También se hace un recorrido por su historia, indicando los hitos que ha ido alcanzando.                                                                                                                                                    |
| [[Apuntes/1DAM_Programación/Unidad 01/8. Primeros pasos en Java\|8. Primeros pasos en Java]]                                   | Estructura básica de un programa Java y tipos de comentarios, incluidos los de documentación (Javadoc). Cómo compilar, ejecutar y depurar un programa Java desde la consola.                                                                                                                                                                     |
| [[Apuntes/1DAM_Programación/Unidad 01/9. Tipos de datos simples\|9. Tipos de datos simples]]                                   | Tipos de datos primitivos de Java. Números enteros, reales (con decimales), lógicos, caracteres y cadenas de texto. Conversiones de tipos de datos (casting). Operaciones con estos tipos de datos. Variables y constantes, cómo declararlas y usarlas. Qué es static, una breve introducción. Ámbito de las variables. Qué son las expresiones. |
| [[Apuntes/1DAM_Programación/Unidad 01/10. Apéndice. Entrada y salida por consola\|10. Apéndice. Entrada y salida por consola]] | Para permitir que un usuario pueda comunicarse con nuestro programa podemos usar la entrada por teclado, con la que el usuario nos envía datos, y la salida por pantalla con la que el programa le dice los resultados.                                                                                                                          |
| [[Apuntes/1DAM_Programación/Unidad 01/Referencias\|Referencias]]                                                               | Material de refuerzo en vídeo (pseudocódigo y primeros pasos en Java) y documentación de referencia de la unidad.                                                                                                                                                                                                                                |

{ .block-language-dataview}

## Unidad completa

En el siguiente enlace tienes la unidad completa en una sola página, por si quieres imprimirla o pasarla a PDF:

[[Unidad 02-Estructuras de control. Calidad del software\|Unidad 02-Estructuras de control. Calidad del software]]

---

<p><span>🏠 <strong>Libro:</strong> <a data-tooltip-position="top" aria-label="Libros/Programación (1º DAM, 1º DAW).md" data-href="Libros/Programación (1º DAM, 1º DAW).md" href="Libros/Programación (1º DAM, 1º DAW).md" class="internal-link" target="_blank" rel="noopener nofollow">Programación (1º DAM, 1º DAW)</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="Apuntes/1DAM_Programación/Unidades/Unidad 02 - Estructuras de control. Calidad del software.md" data-href="Apuntes/1DAM_Programación/Unidades/Unidad 02 - Estructuras de control. Calidad del software.md" href="Apuntes/1DAM_Programación/Unidades/Unidad 02 - Estructuras de control. Calidad del software.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 02 - Estructuras de control. Calidad del software</a> ➡️</span></p>
