---
{"dg-publish":true,"permalink":"/programacion-1-dam/unidades/unidad-8-flujos-y-ficheros/","tags":["java/io"],"dg-note-properties":{"modulo":"[[Módulos/Programación]]","libro":"[[Libro Programación (1º DAM, 1º DAW)]]","descripcion":"Nuestro programa se aloja en la RAM mientras se ejecuta. Pero necesita obtener datos de fuentes externas a dicha memoria: un fichero, una base de datos, una conexión a Internet... Los flujos permiten abrir un canal que va desde la RAM hasta esas fuentes.","orden":9,"tags":["java/io"],"estado":"revisar"}}
---



<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



> [!info]
> &copy; Departamento de Informática del IES Celia Viñas
> ![by-nc-sa.png\|150](/img/user/attach/by-nc-sa.png)
> El contenido original ha sido escrito por &copy; **[Alfredo Moreno Vozmediano](https://www.instagram.com/amvozmediano/)** y está bajo licencia Creative Commons **[Attribution-NonCommercial-ShareAlike 4.0 International](https://creativecommons.org/licenses/by-nc-sa/4.0/)**, que permite su libre distribución, comunicación pública y adaptación sin fines lucrativos, siempre que se cite la autoría y se indique si se han realizado cambios. No se permite el uso comercial.
> Este material toma como base la obra del compañero Alfredo y, con su permiso, se han ido realizando cambios.

</div></div>


Normalmente, las operaciones de entrada y salida de datos de nuestros programas se hacen a través del teclado o ratón (dispositivos típicos de entrada) y la pantalla (dispositivo típico de salida). Pero los programas pueden enviar y recibir datos desde otros dispositivos, como la memoria secundaria; es decir, pueden **enviar datos hacia un archivo o recibirlos de él**.

Además, todos los datos que hemos manejado, ya sea mediante tipos de datos simples o estructuras complejas, han estado alojados en la **memoria principal** del ordenador, de manera que al apagar éste, o antes, al terminar el programa, toda esa información se perdía. Como es natural, también es posible almacenar datos en **memoria secundaria**, es decir, en dispositivos tales como discos duros, discos flexibles, discos ópticos, memorias USB, etc. Estas memorias se caracterizan por ser **más** **lentas** que la memoria principal del ordenador, pero también disponen de **más espacio** de almacenamiento, y **no son volátiles**, es decir, no pierden su contenido al desconectar el ordenador.

Para **almacenar datos en estas memorias secundarias** tenemos dos opciones: o usar un sistema gestor de bases de datos (algo que trabajamos en otro capítulo de este curso) o una estructura de ficheros.

Los **archivos** o **ficheros** (en inglés, files) no son más que agrupaciones de datos en memoria secundaria. En este tema vamos a aprender a manipular archivos desde Java tanto con el enfoque clásico (**java.io**) como con el enfoque moderno (**NIO2**). Empezaremos con los conceptos básicos sobre archivos y progresaremos hacia el uso de ficheros secuenciales y de acceso aleatorio con java.io (librería clásica de Java) y con NIO2 (la librería actual de Java). Terminaremos el tema con una colección de buenas prácticas recomendables para trabajar con ficheros desde Java.

¡Al ataque!

| File                                                                                                                                                                      | Descripción                                                                                                                                                   |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[Programación_1DAM/Unidad 08/1. Conceptos básicos sobre ficheros\|1. Conceptos básicos sobre ficheros]]                                                               | ¿Qué es un fichero? ¿Como almacena y organiza la información?                                                                                                 |
| [[Programación_1DAM/Unidad 08/2. La API clásica de Java - java.io\|2. La API clásica de Java - java.io]]                                                               | Qué mecanismos incorpora Java para enviar/recibir datos hacia/desde ficheros y en qué formas (como caracteres, datos primitivos o incluso objetos completos). |
| [[Programación_1DAM/Unidad 08/3. Procesamiento de ficheros secuenciales en Java\|3. Procesamiento de ficheros secuenciales en Java]]                                   | Operaciones básicas que se pueden hacer sobre ficheros.                                                                                                       |
| [[Programación_1DAM/Unidad 08/4. Procesamiento de ficheros de acceso directo o aleatorio en Java\|4. Procesamiento de ficheros de acceso directo o aleatorio en Java]] | Operaciones sobre ficheros de acceso directo.                                                                                                                 |
| [[Programación_1DAM/Unidad 08/5. Los ficheros en Java moderno - NIO2\|5. Los ficheros en Java moderno - NIO2]]                                                         | NIO2, o cómo abrir un solo canal o stream bidireccional hacia ficheros.                                                                                       |
| [[Programación_1DAM/Unidad 08/6. Buenas prácticas\|6. Buenas prácticas]]                                                                                               | Para mitigar los posibles problemas del tratamiento de ficheros, veamos algunas buenas prácticas.                                                             |

{ .block-language-dataview}

---

<p><span>⬅️ <strong>Anterior:</strong> <a data-tooltip-position="top" aria-label="Programación_1DAM/Unidades/Unidad 7 - POO - Aspectos avanzados.md" data-href="Programación_1DAM/Unidades/Unidad 7 - POO - Aspectos avanzados.md" href="Programación_1DAM/Unidades/Unidad 7 - POO - Aspectos avanzados.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 7 - POO - Aspectos avanzados</a> | 🏠 <strong>Libro:</strong> <a data-tooltip-position="top" aria-label="Libros/Libro Programación (1º DAM, 1º DAW).md" data-href="Libros/Libro Programación (1º DAM, 1º DAW).md" href="Libros/Libro Programación (1º DAM, 1º DAW).md" class="internal-link" target="_blank" rel="noopener nofollow">Libro Programación (1º DAM, 1º DAW)</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="Programación_1DAM/Unidades/Unidad 9 - Bases de datos.md" data-href="Programación_1DAM/Unidades/Unidad 9 - Bases de datos.md" href="Programación_1DAM/Unidades/Unidad 9 - Bases de datos.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 9 - Bases de datos</a> ➡️</span></p>
