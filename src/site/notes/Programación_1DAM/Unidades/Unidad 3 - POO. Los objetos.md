---
{"dg-publish":true,"permalink":"/programacion-1-dam/unidades/unidad-3-poo-los-objetos/","tags":["poo","java"],"dg-note-properties":{"modulo":"[[Módulos/Programación]]","libro":"[[Libro Programación (1º DAM, 1º DAW)]]","descripcion":"Qué son las clases, cómo se definen (declarando su atributos y métodos) y cómo crear o instanciar objetos a partir de ellas.","orden":3,"tags":["poo","java"]}}
---



<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



> [!info]
> &copy; Departamento de Informática del IES Celia Viñas
> ![by-nc-sa.png\|150](/img/user/attach/by-nc-sa.png)
> El contenido original ha sido escrito por &copy; **[Alfredo Moreno Vozmediano](https://www.instagram.com/amvozmediano/)** y está bajo licencia Creative Commons **[Attribution-NonCommercial-ShareAlike 4.0 International](https://creativecommons.org/licenses/by-nc-sa/4.0/)**, que permite su libre distribución, comunicación pública y adaptación sin fines lucrativos, siempre que se cite la autoría y se indique si se han realizado cambios. No se permite el uso comercial.
> Este material toma como base la obra del compañero Alfredo y, con su permiso, se han ido realizando cambios.

</div></div>


Las variables que hemos usado hasta ahora nos permitían guardar datos primitivos. Así, en cada variable se puede almacenar un número, un texto, un carácter, un valor lógico, etc.

Es decir, **una variable, un valor**.

Si tenemos que hacer un programa que gestione las cuentas de una empresa tendríamos que contemplar muchas variables:

- Las de los empleados: _nombre del empleado, fecha de nacimiento, documento de identificación, número de la seguridad social, nómina, retenciones, incentivos, número de cuenta_, etc. 
- Las de los clientes: _nombre del cliente, CIF/NIF, dirección, cuenta de facturación, flags de promociones y conciciones especiales_...
- Las de proveedores: bla, bla, bla...

Y así sucesivamente. Si empiezas a contar el número de variables que debes crear para tu programa, acabarás tirándote de los pelos.

Pero la POO vino al rescate hace ya unos años.

¿Y si en un bloque de código -al que llamamos `Empleado`- ponemos las variables y funcionalidades propias y adecuadas para su gestión? ¿Y si hacemos otro similar para los proveedores y para los clientes y así sucesivamente...?

Esto se conoce como encapsulamiento y es una de las características más básicas en la POO.

En esta unidad vamos a empezar a ver cómo funciona.

Estás a punto de empezar en el mundo de la POO ¡Vamos a ello!

| File                                                                                                                                                        | Descripción                                                                                                                                                                                                                    |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [[Programación_1DAM/Unidad 03/1. Entendiendo la programación orientada a objetos\|1. Entendiendo la programación orientada a objetos]]                   | ¿Qué es eso de la POO (Programación Orientada a Objetos)? En este apartado se verán las nociones para entenderlo y los mecanismos que usa para mantener un estado (mediante atributos) y realizar acciones (mediante métodos). |
| [[Programación_1DAM/Unidad 03/2. Definiciones formales\|2. Definiciones formales]]                                                                       | ¿Qué es eso de la POO (Programación Orientada a Objetos)? En este apartado se verán las nociones para entenderlo y los mecanismos que usa para mantener un estado (mediante atributos) y realizar acciones (mediante métodos). |
| [[Programación_1DAM/Unidad 03/3. Ejemplos\|3. Ejemplos]]                                                                                                 | La clase String encapsula multitud de métodos que nos ayudan a tratar textos de forma rápida y sencilla.                                                                                                                       |
| [[Programación_1DAM/Unidad 03/4. Declaración de clases e instanciación de objetos en Java\|4. Declaración de clases e instanciación de objetos en Java]] | Veremos cómo declaramos una clase, con sus atributos y métodos, y luego instanciamos un objeto de dicha clase.                                                                                                                 |
| [[Programación_1DAM/Unidad 03/5. Más sobre métodos\|5. Más sobre métodos]]                                                                               | Explicación más detallada de cómo declarar y usar métodos.                                                                                                                                                                     |
| [[Programación_1DAM/Unidad 03/6. Paquetes\|6. Paquetes]]                                                                                                 | Nuestros programas pueden llegar a contener muchas clases. Para organizarlas podemos usar los paquetes.                                                                                                                        |
| [[Programación_1DAM/Unidad 03/7. Apéndice. Entrada y salida por consola\|7. Apéndice. Entrada y salida por consola]]                                     | Para permitir que un usuario pueda comunicarse con nuestro programa podemos usar la entrada por teclado, con la que el usuario nos envía datos, y la salida por pantalla con la que el programa le dice los resultados.        |

{ .block-language-dataview}

---

<p><span>⬅️ <strong>Anterior:</strong> <a data-tooltip-position="top" aria-label="Programación_1DAM/Unidades/Unidad 2 - Estructuras de control. Calidad del software.md" data-href="Programación_1DAM/Unidades/Unidad 2 - Estructuras de control. Calidad del software.md" href="Programación_1DAM/Unidades/Unidad 2 - Estructuras de control. Calidad del software.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 2 - Estructuras de control. Calidad del software</a> | 🏠 <strong>Libro:</strong> <a data-tooltip-position="top" aria-label="Libros/Libro Programación (1º DAM, 1º DAW).md" data-href="Libros/Libro Programación (1º DAM, 1º DAW).md" href="Libros/Libro Programación (1º DAM, 1º DAW).md" class="internal-link" target="_blank" rel="noopener nofollow">Libro Programación (1º DAM, 1º DAW)</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="Programación_1DAM/Unidades/Unidad 4 - POO. Clases.md" data-href="Programación_1DAM/Unidades/Unidad 4 - POO. Clases.md" href="Programación_1DAM/Unidades/Unidad 4 - POO. Clases.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 4 - POO. Clases</a> ➡️</span></p>
