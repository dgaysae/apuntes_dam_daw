---
{"dg-publish":true,"permalink":"/programacion-1-dam/unidad-06-java-fx/apendice-recursos-del-proyecto/","tags":["java/swing","proyecto"],"dg-note-properties":{"unidad":["[[Unidad 6 - Interfaz gráfica de usuario (GUI) - Swing]]","[[Unidad 6 - Interfaz gráfica de usuario (GUI) - JavaFX]]"],"descripcion":"En lugar de incluir todo el código (componentes y eventos) en un fichero, podemos separarlos en distintos objetos de forma que cada uno se ocupa de algo en concreto.","orden":3,"tags":["java/swing","proyecto"]}}
---



<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/programacion-1-dam/unidad-06-apendice-recursos-proyecto/apendice-recursos-del-proyecto/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

<div class="markdown-embed-title">

# Apéndice - recursos del proyecto

</div>




Al crear un proyecto en nuestro IDE elegimos un gestor concreto: Maven, Gradle, etc. Hasta ahora hemos estado usando Maven, así que este apéndice se centrará en su estructura, pero puede indagar sobre la organización de ficheros y directorios de otros gestores para obtener los mismos resultados.

Maven ofrece una estructura de directorios que organiza todos los ficheros que queramos incluir en nuestro entregable (un fichero JAR, por ejemplo). Ya no se trata sólo de los ficheros compilados (`.class`), sino también de otros recursos como las dependencias (código de terceros) o las imágenes e iconos que usamos para nuestra interfaz gráfica.

En un proyecto Maven, todos los recursos que no son código fuente (imágenes, configuraciones, iconos) deben ir en la carpeta de recursos **`src/main/resources`**. Y, como buena práctica, es conveniente organizarla con los subdirectorios que creamos oportunos. Por ejemplo:

**`src/main/resources/icons/iconoBuscar.png`**  
**`src/main/resources/imgs/logo.png`**

¿Y cómo accedemos a esos recursos desde nuestro código fuente? Para que esas imágenes funcionen tanto al ejecutar el programa desde el IDE como en el entregable y ejecutable JAR, **nunca deben usarse rutas absolutas** (`C:\\MisImagenes...`). La API de Java nos ofrece el **`ClassLoader`** que busca dentro del classpath de nuestro proyecto.

Así, para cargar un icono simplemente usamos el método `getResource(*<ruta dentro de src/main/resources/>)`. Este método busca la ruta introducida como argumento partiendo de la ruta de recursos **`src/main/resources/`**.

Para el icono del ejemplo anterior sería:

```java
URL url = getClass().getResource("/icons/iconoBuscar.png");
ImageIcon icono = new ImageIcon(url);
```



</div></div>


---

<p><span>🏠 <strong>Unidad:</strong> <a data-tooltip-position="top" aria-label="Programación_1DAM/Unidades/Unidad 6 - Interfaz gráfica de usuario (GUI) - Swing.md" data-href="Programación_1DAM/Unidades/Unidad 6 - Interfaz gráfica de usuario (GUI) - Swing.md" href="Programación_1DAM/Unidades/Unidad 6 - Interfaz gráfica de usuario (GUI) - Swing.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 6 - Interfaz gráfica de usuario (GUI) - Swing</a>,<a data-tooltip-position="top" aria-label="Programación_1DAM/Unidades/Unidad 6 - Interfaz gráfica de usuario (GUI) - JavaFX.md" data-href="Programación_1DAM/Unidades/Unidad 6 - Interfaz gráfica de usuario (GUI) - JavaFX.md" href="Programación_1DAM/Unidades/Unidad 6 - Interfaz gráfica de usuario (GUI) - JavaFX.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 6 - Interfaz gráfica de usuario (GUI) - JavaFX</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="Programación_1DAM/Unidad 06 JavaFX/Apéndice - Principios de diseño de interfaces gráficas de usuario.md" data-href="Programación_1DAM/Unidad 06 JavaFX/Apéndice - Principios de diseño de interfaces gráficas de usuario.md" href="Programación_1DAM/Unidad 06 JavaFX/Apéndice - Principios de diseño de interfaces gráficas de usuario.md" class="internal-link" target="_blank" rel="noopener nofollow">Apéndice - Principios de diseño de interfaces gráficas de usuario</a> ➡️</span></p>


