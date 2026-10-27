---
{"dg-publish":true,"permalink":"/asignaturas/1-dam-programacion/unidades/unidad-06/unidad-06-anexo-java-fx/","tags":["java/javafx"],"dg-note-properties":{"modulo":"[[Módulos/Programación]]","libro":"[[Libros/Programación (1º DAM, 1º DAW)]]","descripcion":"Interfaces gráficas modernas en Java con JavaFX: ventanas, controles, contenedores, eventos, hojas de estilo y Scene Builder.","orden":6.4,"ra":"RA5","tags":["java/javafx"],"estado":"revisar"}}
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

> [!NOTE] Anexo de la Unidad 06
> Este anexo forma parte de [[Asignaturas/1DAM_Programación/Unidades/Unidad 06/Unidad 06 - Entrada y salida de información\|Unidad 06 - Entrada y salida de información]], donde se recogen el RA 5 y sus criterios de evaluación. Desarrolla el bloque B de la unidad, **interfaces gráficas con JavaFX**, para trabajar los criterios f), g) y h). Si prefieres la librería clásica de Java, consulta [[Asignaturas/1DAM_Programación/Unidades/Unidad 06/Unidad 06 - Anexo - Swing\|Unidad 06 - Anexo - Swing]].

---

Hasta ahora, tus programas se comunicaban con el usuario a través de la **consola**: leer datos y mostrar resultados línea a línea. Las aplicaciones que usamos a diario, en cambio, tienen **ventanas, botones, menús y listas** con los que el usuario interactúa con el ratón y el teclado. Eso es una **interfaz gráfica de usuario** (*GUI*, *Graphical User Interface*).

En este anexo aprenderás a construirlas con **JavaFX**, la librería gráfica más moderna de Java:

- Cómo se organiza una aplicación JavaFX: **ventana** (`Stage`), **escena** (`Scene`) y **nodos**.
- Cómo describir la interfaz en un archivo **FXML** y separarla de la lógica, que va en el **controlador**.
- Cómo colocar los componentes con **contenedores** (*layouts*) y darles estilo con **CSS**.
- Cómo responder a las acciones del usuario mediante **eventos** y sus **manejadores**.
- Cómo diseñar la interfaz de forma visual con **Scene Builder**.

---
## Índice de contenidos

| File                                                                                                                                                                                                       | Descripción                                                                                                                                                                           |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[Asignaturas/1DAM_Programación/Apuntes/Unidad 06/Anexo - JavaFX/1. AWT, Swing y JavaFX. ¿Qué es mejor?\|1. AWT, Swing y JavaFX. ¿Qué es mejor?]]                                                       | Comparativa entre las distintas librerías de interfaz gráfica en Java.                                                                                                                |
| [[Asignaturas/1DAM_Programación/Apuntes/Unidad 06/Anexo - JavaFX/2. Qué es JavaFX\|2. Qué es JavaFX]]                                                                                                   | Qué es JavaFX, cómo organiza la interfaz en ventanas, escenas y nodos, y qué piezas forman una aplicación (FXML, controlador, modelo y CSS).                                          |
| [[Asignaturas/1DAM_Programación/Apuntes/Unidad 06/Anexo - JavaFX/3. Crear un proyecto JavaFX\|3. Crear un proyecto JavaFX]]                                                                             | Cómo crear, compilar y ejecutar un proyecto JavaFX con Maven en NetBeans y Visual Studio Code, qué archivos genera y cómo hacerlo desde la línea de comandos.                         |
| [[Asignaturas/1DAM_Programación/Apuntes/Unidad 06/Anexo - JavaFX/4. Comprendiendo cómo funciona JavaFX con un ejemplo\|4. Comprendiendo cómo funciona JavaFX con un ejemplo]]                           | Un ejemplo completo, paso a paso, para ver cómo encajan la clase principal, la vista FXML, el controlador, el modelo y los eventos.                                                   |
| [[Asignaturas/1DAM_Programación/Apuntes/Unidad 06/Anexo - JavaFX/5. Contenedores (layouts)\|5. Contenedores (layouts)]]                                                                                 | Los contenedores (layouts) de JavaFX y cómo usarlos y combinarlos para organizar los nodos en la ventana y adaptarlos a su tamaño.                                                    |
| [[Asignaturas/1DAM_Programación/Apuntes/Unidad 06/Anexo - JavaFX/6. Controles y otros nodos\|6. Controles y otros nodos]]                                                                               | Los componentes de la interfaz: controles (botones, campos de texto, casillas, listas…), imágenes, menús y controles especiales, con ejemplos en FXML y Java.                         |
| [[Asignaturas/1DAM_Programación/Apuntes/Unidad 06/Anexo - JavaFX/7. Eventos y manejadores\|7. Eventos y manejadores]]                                                                                   | Qué son los eventos, los tipos más habituales (acción, ratón y teclado) y cómo responder a ellos con manejadores desde FXML y desde código Java.                                      |
| [[Asignaturas/1DAM_Programación/Apuntes/Unidad 06/Anexo - JavaFX/8. Hojas de estilo CSS\|8. Hojas de estilo CSS]]                                                                                       | Cómo cambiar el aspecto de la interfaz con hojas de estilo CSS en JavaFX, dónde guardarlas, cómo cargarlas y qué propiedades se usan más.                                             |
| [[Asignaturas/1DAM_Programación/Apuntes/Unidad 06/Anexo - JavaFX/9. Scene Builder\|9. Scene Builder]]                                                                                                   | Scene Builder: diseño visual de interfaces JavaFX arrastrando componentes, sin escribir el FXML a mano.                                                                               |
| [[Asignaturas/1DAM_Programación/Apuntes/Unidad 06/Anexo - JavaFX/Apéndice - Principios de diseño de interfaces gráficas de usuario\|Apéndice - Principios de diseño de interfaces gráficas de usuario]] | Principios universales de diseño de interfaces gráficas, en forma de lo que se debe y no se debe hacer, para mejorar la usabilidad de nuestras aplicaciones.                          |
| [[Asignaturas/1DAM_Programación/Apuntes/Unidad 06/Anexo - JavaFX/Apéndice - recursos del proyecto\|Apéndice - recursos del proyecto]]                                                                   | Dónde guardar las imágenes, iconos y otros recursos de un proyecto Maven y cómo cargarlos desde el código, tanto en Swing como en JavaFX, para que funcionen también en el JAR final. |
| [[Asignaturas/1DAM_Programación/Apuntes/Unidad 06/Anexo - JavaFX/Referencias\|Referencias]]                                                                                                             | Aquí tienes distintas fuentes y referencias documentales para consultar, ahondar y aprender más sobre los temas que hemos tratado en esta unidad                                      |

{ .block-language-dataview}

---

<p><span>🏠 <strong>Libro:</strong> <a data-tooltip-position="top" aria-label="Libros/Programación (1º DAM, 1º DAW).md" data-href="Libros/Programación (1º DAM, 1º DAW).md" href="Libros/Programación (1º DAM, 1º DAW).md" class="internal-link" target="_blank" rel="noopener nofollow">Programación (1º DAM, 1º DAW)</a></span></p>
