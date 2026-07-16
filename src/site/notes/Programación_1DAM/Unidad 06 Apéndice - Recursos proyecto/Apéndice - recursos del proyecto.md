---
{"dg-publish":true,"permalink":"/programacion-1-dam/unidad-06-apendice-recursos-proyecto/apendice-recursos-del-proyecto/","tags":["java/swing","proyecto"],"dg-note-properties":{"unidad":"[[Unidad 6 - Interfaz gráfica de usuario (GUI) - Swing]]","descripcion":"En lugar de incluir todo el código (componentes y eventos) en un fichero, podemos separarlos en distintos objetos de forma que cada uno se ocupa de algo en concreto.","orden":8,"tags":["java/swing","proyecto"]}}
---


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

