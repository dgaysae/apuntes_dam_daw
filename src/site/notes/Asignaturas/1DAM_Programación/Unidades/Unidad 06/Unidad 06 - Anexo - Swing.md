---
{"dg-publish":true,"dg-permalink":"/apuntes/1-dam-programacion/unidades/unidad-06-anexo-swing/","permalink":"/apuntes/1-dam-programacion/unidades/unidad-06-anexo-swing/","tags":["java/swing"],"dg-note-properties":{"modulo":"[[Módulos/Programación]]","libro":"[[Libros/Programación (1º DAM, 1º DAW)]]","descripcion":"La mayoría de los usuarios necesitan una interfaz que les permita realizar tareas de forma visualmente fácil e intuitiva. Aquí entran en juego las GUI.","orden":6.5,"ra":"RA5","tags":["java/swing"],"estado":"revisar"}}
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
> Este anexo forma parte de [[Asignaturas/1DAM_Programación/Unidades/Unidad 06/Unidad 06 - Entrada y salida de información\|Unidad 06 - Entrada y salida de información]], donde se recogen el RA 5 y sus criterios de evaluación. Presenta **Swing** como alternativa a JavaFX (bloque B) para trabajar los criterios f), g) y h).

---

De momento, solo has programado **aplicaciones en «modo texto»**, donde la interacción con el usuario se limita a la consola: leer datos y mostrar resultados línea a línea. Este enfoque es perfecto para aprender lógica y estructuras básicas, pero **el software que usamos a diario va mucho más allá**. En este capítulo darás el salto a la **programación gráfica**, donde tus programas podrán tener **ventanas, botones, menús e interfaces mucho más intuitivas**.

En el ecosistema de Java existen varias tecnologías para crear interfaces gráficas: **<abbr title="Abstract Window Toolkit">AWT</abbr>, Swing y JavaFX**. **AWT** fue la primera aproximación, con componentes básicos dependientes del sistema operativo. **Swing** supuso un gran avance al ofrecer componentes más ricos y portables. **JavaFX**, más moderno, incorpora estilos visuales, animaciones y una arquitectura más flexible para aplicaciones actuales.

Aprenderás cómo construir ventanas, organizar elementos en pantalla, responder a eventos del usuario (como clics o pulsaciones de teclas) y separar la lógica de tu programa de su presentación visual usando **Java Swing**. Este cambio no solo mejora la apariencia de tus aplicaciones, sino también la forma de diseñarlas.

---
## Índice de contenidos

| File                                                                                                                                                                                                      | Descripción                                                                                                                                                                           |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[Asignaturas/1DAM_Programación/Apuntes/Unidad 06/Anexo - Swing/1. AWT, Swing y JavaFX. ¿Qué es mejor?\|1. AWT, Swing y JavaFX. ¿Qué es mejor?]]                                                       | Comparativa entre las distintas librerías de interfaz gráfica en Java.                                                                                                                |
| [[Asignaturas/1DAM_Programación/Apuntes/Unidad 06/Anexo - Swing/2. Componentes de swing\|2. Componentes de swing]]                                                                                     | Estructura de clases de Swing.                                                                                                                                                        |
| [[Asignaturas/1DAM_Programación/Apuntes/Unidad 06/Anexo - Swing/3. Contenedores de Swing\|3. Contenedores de Swing]]                                                                                   | Los contenedores son los elementos que sirven para mostrar otros componentes. En ellos se incluirán botones, etiquetas, etc.                                                          |
| [[Asignaturas/1DAM_Programación/Apuntes/Unidad 06/Anexo - Swing/4. LayoutManager - Cómo distribuir los componentes en la ventana\|4. LayoutManager - Cómo distribuir los componentes en la ventana]]   | Los LayoutManager indican al contendor cómo debe distribuir los componentes que se le añaden.                                                                                         |
| [[Asignaturas/1DAM_Programación/Apuntes/Unidad 06/Anexo - Swing/5. Otros componentes de Swing\|5. Otros componentes de Swing]]                                                                         | Botones, etiquetas, radio buttons, etc.                                                                                                                                               |
| [[Asignaturas/1DAM_Programación/Apuntes/Unidad 06/Anexo - Swing/6. Eventos\|6. Eventos]]                                                                                                               | Podemos capturar lo que sucede en nuestras ventanas (se pulsa un botón, se escribe un texto, etc.) e indicarle a nuestra aplicación que haga algo.                                    |
| [[Asignaturas/1DAM_Programación/Apuntes/Unidad 06/Anexo - Swing/7. Patrón MVC (Modelo-Vista-Controlador)\|7. Patrón MVC (Modelo-Vista-Controlador)]]                                                   | En lugar de incluir todo el código (componentes y eventos) en un fichero, podemos separarlos en distintos objetos de forma que cada uno se ocupa de algo en concreto.                 |
| [[Asignaturas/1DAM_Programación/Apuntes/Unidad 06/Anexo - Swing/8. Ejemplo práctico\|8. Ejemplo práctico]]                                                                                             | Pongamos en práctica lo visto hasta ahora                                                                                                                                             |
| [[Asignaturas/1DAM_Programación/Apuntes/Unidad 06/Anexo - Swing/Apéndice - recursos del proyecto\|Apéndice - recursos del proyecto]]                                                                   | Dónde guardar las imágenes, iconos y otros recursos de un proyecto Maven y cómo cargarlos desde el código, tanto en Swing como en JavaFX, para que funcionen también en el JAR final. |
| [[Asignaturas/1DAM_Programación/Apuntes/Unidad 06/Anexo - Swing/Apéndice - Principios de diseño de interfaces gráficas de usuario\|Apéndice - Principios de diseño de interfaces gráficas de usuario]] | Principios universales de diseño de interfaces gráficas, en forma de lo que se debe y no se debe hacer, para mejorar la usabilidad de nuestras aplicaciones.                          |
| [[Asignaturas/1DAM_Programación/Apuntes/Unidad 06/Anexo - Swing/Referencias\|Referencias]]                                                                                                             | Aquí tienes distintas fuentes y referencias documentales para consultar, ahondar y aprender más sobre los temas que hemos tratado en esta unidad                                      |
| [[Asignaturas/1DAM_Programación/Apuntes/Unidad 06/Anexo - Swing/Referencias internas\|Referencias internas]]                                                                                           | Aquí tienes distintas fuentes y referencias documentales para consultar, ahondar y aprender más sobre los temas que hemos tratado en esta unidad                                      |

{ .block-language-dataview}

---

<p><span>🏠 <strong>Libro:</strong> <a data-tooltip-position="top" aria-label="Libros/Programación (1º DAM, 1º DAW).md" data-href="Libros/Programación (1º DAM, 1º DAW).md" href="Libros/Programación (1º DAM, 1º DAW).md" class="internal-link" target="_blank" rel="noopener nofollow">Programación (1º DAM, 1º DAW)</a></span></p>
