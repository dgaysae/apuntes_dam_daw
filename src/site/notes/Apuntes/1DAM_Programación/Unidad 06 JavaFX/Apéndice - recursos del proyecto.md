---
{"dg-publish":true,"permalink":"/apuntes/1-dam-programacion/unidad-06-java-fx/apendice-recursos-del-proyecto/","tags":["java/javafx","proyecto"],"dg-note-properties":{"unidad":"[[Apuntes/1DAM_Programación/Unidades/Unidad 06 - Entrada y salida de información]]","descripcion":"Dónde guardar las imágenes, iconos y otros recursos de un proyecto Maven y cómo cargarlos desde el código, tanto en Swing como en JavaFX, para que funcionen también en el JAR final.","orden":18,"criterios":["RA5.f"],"tags":["java/javafx","proyecto"]}}
---



<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/apuntes/1-dam-programacion/unidad-06-swing/apendice-recursos-del-proyecto/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

<div class="markdown-embed-title">

# Apéndice - recursos del proyecto

</div>




```table-of-contents
```

---

Al crear un proyecto en nuestro IDE elegimos un gestor concreto: Maven, Gradle, etc. Hasta ahora hemos estado usando Maven, así que este apéndice se centrará en su estructura, pero puede indagar sobre la organización de ficheros y directorios de otros gestores para obtener los mismos resultados.

Maven ofrece una estructura de directorios que organiza todos los ficheros que queramos incluir en nuestro entregable (un fichero JAR, por ejemplo). Ya no se trata sólo de los ficheros compilados (`.class`), sino también de otros recursos como las dependencias (código de terceros) o las imágenes e iconos que usamos para nuestra interfaz gráfica.

En un proyecto Maven, todos los recursos que no son código fuente (imágenes, configuraciones, iconos) deben ir en la carpeta de recursos **`src/main/resources`**. Y, como buena práctica, es conveniente organizarla con los subdirectorios que creamos oportunos. Por ejemplo:

**`src/main/resources/icons/iconoBuscar.png`**  
**`src/main/resources/imgs/logo.png`**

¿Y cómo accedemos a esos recursos desde nuestro código fuente? Para que esas imágenes funcionen tanto al ejecutar el programa desde el IDE como en el entregable y ejecutable JAR, **nunca deben usarse rutas absolutas** (`C:\\MisImagenes...`). La API de Java nos ofrece el **`ClassLoader`** que busca dentro del classpath de nuestro proyecto.

Así, para cargar un recurso simplemente usamos el método `getResource("<ruta dentro de src/main/resources/>")`, que devuelve la **`URL`** del recurso. Si la ruta empieza por **`/`**, se busca partiendo de la carpeta de recursos **`src/main/resources/`**.

> [!WARNING] Dos detalles que conviene recordar
> - **Empieza siempre la ruta por `/`.** Sin ella, la ruta se busca a partir del **paquete de la clase** que hace la llamada (por ejemplo, `src/main/resources/app/vistas/...` si la clase está en el paquete `app.vistas`), y lo normal es que no encuentre nada.
> - Si el recurso no existe, `getResource()` **devuelve `null`**, y el error aparecerá más adelante como un `NullPointerException`. Si te ocurre, revisa primero la ruta y el nombre del fichero (se distinguen mayúsculas y minúsculas).

La forma de **usar** esa `URL` depende de la librería gráfica.

### En Swing

Para el icono del ejemplo anterior sería:

```java
URL url = getClass().getResource("/icons/iconoBuscar.png");
ImageIcon icono = new ImageIcon(url);
```

### En JavaFX

La clase **`Image`** de JavaFX recibe la ruta como texto, así que convertimos la `URL` con **`toExternalForm()`**:

```java
Image imagen = new Image(getClass().getResource("/icons/iconoBuscar.png").toExternalForm());
Button boton = new Button("Buscar", new ImageView(imagen));
```

También puedes cargarla como flujo de datos con `getResourceAsStream()`:

```java
Image imagen = new Image(getClass().getResourceAsStream("/icons/iconoBuscar.png"));
```

En JavaFX, además de imágenes, se cargan de la misma forma **otros recursos** del proyecto:

```java
// Vista diseñada con Scene Builder (fichero FXML)
Parent raiz = FXMLLoader.load(getClass().getResource("/vistas/principal.fxml"));
Scene escena = new Scene(raiz);

// Hoja de estilos CSS
escena.getStylesheets().add(getClass().getResource("/css/estilos.css").toExternalForm());

// Icono de la ventana
stage.getIcons().add(new Image(getClass().getResource("/imgs/logo.png").toExternalForm()));
```

Para que estos ejemplos funcionen, los ficheros deben estar en `src/main/resources/vistas/principal.fxml`, `src/main/resources/css/estilos.css` y `src/main/resources/imgs/logo.png`.

---

<p><span>⬅️ <strong>Anterior:</strong> <a data-tooltip-position="top" aria-label="Apuntes/1DAM_Programación/Unidad 06 Swing/8. Ejemplo práctico.md" data-href="Apuntes/1DAM_Programación/Unidad 06 Swing/8. Ejemplo práctico.md" href="Apuntes/1DAM_Programación/Unidad 06 Swing/8. Ejemplo práctico.md" class="internal-link" target="_blank" rel="noopener nofollow">8. Ejemplo práctico</a> | 🏠 <strong>Unidad:</strong> <a data-tooltip-position="top" aria-label="Apuntes/1DAM_Programación/Unidades/Unidad 06 - Anexo - Swing.md" data-href="Apuntes/1DAM_Programación/Unidades/Unidad 06 - Anexo - Swing.md" href="Apuntes/1DAM_Programación/Unidades/Unidad 06 - Anexo - Swing.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 06 - Anexo - Swing</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="Apuntes/1DAM_Programación/Unidad 06 Swing/Apéndice - Principios de diseño de interfaces gráficas de usuario.md" data-href="Apuntes/1DAM_Programación/Unidad 06 Swing/Apéndice - Principios de diseño de interfaces gráficas de usuario.md" href="Apuntes/1DAM_Programación/Unidad 06 Swing/Apéndice - Principios de diseño de interfaces gráficas de usuario.md" class="internal-link" target="_blank" rel="noopener nofollow">Apéndice - Principios de diseño de interfaces gráficas de usuario</a> ➡️</span></p>




</div></div>


---

<p><span>⬅️ <strong>Anterior:</strong> <a data-tooltip-position="top" aria-label="Apuntes/1DAM_Programación/Unidad 06 JavaFX/Apéndice - Principios de diseño de interfaces gráficas de usuario.md" data-href="Apuntes/1DAM_Programación/Unidad 06 JavaFX/Apéndice - Principios de diseño de interfaces gráficas de usuario.md" href="Apuntes/1DAM_Programación/Unidad 06 JavaFX/Apéndice - Principios de diseño de interfaces gráficas de usuario.md" class="internal-link" target="_blank" rel="noopener nofollow">Apéndice - Principios de diseño de interfaces gráficas de usuario</a> | 🏠 <strong>Unidad:</strong> <a data-tooltip-position="top" aria-label="Apuntes/1DAM_Programación/Unidades/Unidad 06 - Entrada y salida de información.md" data-href="Apuntes/1DAM_Programación/Unidades/Unidad 06 - Entrada y salida de información.md" href="Apuntes/1DAM_Programación/Unidades/Unidad 06 - Entrada y salida de información.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 06 - Entrada y salida de información</a></span></p>


