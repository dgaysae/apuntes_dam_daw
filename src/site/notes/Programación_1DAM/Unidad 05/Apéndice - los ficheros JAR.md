---
{"dg-publish":true,"permalink":"/programacion-1-dam/unidad-05/apendice-los-ficheros-jar/","tags":["java/jar"],"dg-note-properties":{"unidad":"[[Unidad 5 - Estructuras de almacenamiento]]","descripcion":"Un proyecto Java necesita muchos ficheros y configuraciones para funcionar. ¿Cómo nos llevamos todo eso de un equipo a otro? Con ficheros JAR.","orden":11,"tags":["java/jar"]}}
---


```table-of-contents
```

---

Los programas que hemos hecho hasta ahora han sido pequeños tirando a minúsculos, pero, cuando una aplicación crece, el número de ficheros fuente que necesita empieza a dispararse inquietantemente. Entonces trasladar todo ese código fuente de una máquina a otra puede ser un problema. 

Para solucionarlo se crearon los archivos **<abbr title="Java ARchive">JAR</abbr>**. Son, simple y llanamente, archivos comprimidos, como los ZIP o los RAR, que incorporan en sus tripas todos los ficheros `.java`, `.class`, la estructura de directorios y cuantas cosas haya en tu carpeta de trabajo. 

Vamos a ver cómo se trabaja con los ficheros JAR desde una consola de texto. Por supuesto, los IDE incorporan herramientas para obviar todos estos farragosos comandos, pero recuerda: no siempre tendrás disponible un IDE y, además... ¡puedes fardar mucho más si lo haces desde la consola\! 

## Crear un JAR

Para crear un fichero `hola.jar` que contenga el archivo `holamundo.class`, escribimos:

```bash
$ jar cfv hola.jar holamundo.class
```

Y, si queremos incluir todos los ficheros del directorio (y, si hay subdirectorios, se añadirán también):

```bash
$ jar cfv hola.jar *
```

## Agregar ficheros a un JAR

Para agregar, digamos, un `adiosmundo.class` a un fichero `hola.jar` que ya existe, se usa el mismo comando que antes:

```bash
$ jar cfv hola.jar adiosmundo.class
```


## Ver el contenido de un JAR

Esto mostrará la lista de archivos contenidos en un JAR:

```bash
$ jar tfv hola.jar
```


## Extraer los ficheros de un JAR

Esto extraerá todos los ficheros:

```bash
$ jar xfv hola.jar
```

Y esto extraerá solo el fichero holamundo.class:

```bash
$ jar xfv hola.jar holamundo.class
```

## Ejecutar la aplicación contenida en un JAR

Pues sí. Si tienes una aplicación completa en un JAR, puedes ejecutarla sin necesidad de extraerla, así:

```bash
$ java -cp hola.jar clasemain
```

> [!question] ¿Cómo lo harías? 🤔
> ¿Cómo harías todo esto a través de tu IDE? Busca la forma de realizar estas operaciones desde Netbeans, IntelliJ, Eclipse, etc.

---

<p><span>⬅️ <strong>Anterior:</strong> <a data-tooltip-position="top" aria-label="Programación_1DAM/Unidad 05/10. Hemos aprendido....md" data-href="Programación_1DAM/Unidad 05/10. Hemos aprendido....md" href="Programación_1DAM/Unidad 05/10. Hemos aprendido....md" class="internal-link" target="_blank" rel="noopener nofollow">10. Hemos aprendido...</a> | 🏠 <strong>Unidad:</strong> <a data-tooltip-position="top" aria-label="Programación_1DAM/Unidades/Unidad 5 - Estructuras de almacenamiento.md" data-href="Programación_1DAM/Unidades/Unidad 5 - Estructuras de almacenamiento.md" href="Programación_1DAM/Unidades/Unidad 5 - Estructuras de almacenamiento.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 5 - Estructuras de almacenamiento</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="Plantillas/Plantilla - Referencias documentales.md" data-href="Plantillas/Plantilla - Referencias documentales.md" href="Plantillas/Plantilla - Referencias documentales.md" class="internal-link" target="_blank" rel="noopener nofollow">Plantilla - Referencias documentales</a> ➡️</span></p>


