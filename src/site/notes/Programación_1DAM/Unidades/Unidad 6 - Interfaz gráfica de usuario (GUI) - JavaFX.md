---
{"dg-publish":true,"permalink":"/programacion-1-dam/unidades/unidad-6-interfaz-grafica-de-usuario-gui-java-fx/","tags":["java/swing"],"dg-note-properties":{"modulo":"[[Módulos/Programación]]","libro":"[[Libro Programación (1º DAM, 1º DAW)]]","descripcion":"La mayoría de los usuarios necesitan una interfaz que les permita realizar tareas de forma visualmente fácil e intuitiva. Aquí entran en juego las GUI.","orden":7,"tags":["java/swing"],"estado":"revisar"}}
---



<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



> [!info]
> &copy; Departamento de Informática del IES Celia Viñas
> ![by-nc-sa.png\|150](/img/user/attach/by-nc-sa.png)
> El contenido original ha sido escrito por &copy; **[Alfredo Moreno Vozmediano](https://www.instagram.com/amvozmediano/)** y está bajo licencia Creative Commons **[Attribution-NonCommercial-ShareAlike 4.0 International](https://creativecommons.org/licenses/by-nc-sa/4.0/)**, que permite su libre distribución, comunicación pública y adaptación sin fines lucrativos, siempre que se cite la autoría y se indique si se han realizado cambios. No se permite el uso comercial.
> Este material toma como base la obra del compañero Alfredo y, con su permiso, se han ido realizando cambios.

</div></div>


```table-of-contents
```

---

De momento, solo has programado **aplicaciones en «modo texto»**, donde la interacción con el usuario se limita a la consola: leer datos y mostrar resultados línea a línea. Este enfoque es perfecto para aprender lógica y estructuras básicas, pero **el software que usamos a diario va mucho más allá**. En este capítulo darás el salto a la **programación gráfica**, donde tus programas podrán tener **ventanas, botones, menús e interfaces mucho más intuitivas**.

En el ecosistema de Java existen varias tecnologías para crear interfaces gráficas: **<abbr title="Abstract Window Toolkit">AWT</abbr>, Swing y JavaFX**. **AWT** fue la primera aproximación, con componentes básicos dependientes del sistema operativo. **Swing** supuso un gran avance al ofrecer componentes más ricos y portables. **JavaFX**, más moderno, incorpora estilos visuales, animaciones y una arquitectura más flexible para aplicaciones actuales.

Aprenderás cómo construir ventanas, organizar elementos en pantalla, responder a eventos del usuario (como clics o pulsaciones de teclas) y separar la lógica de tu programa de su presentación visual usando **JavaFX**. Este cambio no solo mejora la apariencia de tus aplicaciones, sino también la forma de diseñarlas.

| File                                                                                                                                                                           | Descripción                                                                                                                                                           |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[Programación_1DAM/Unidad 06 JavaFX/1. AWT, Swing y JavaFX. ¿Qué es mejor?\|1. AWT, Swing y JavaFX. ¿Qué es mejor?]]                                                       | Comparativa entre las distintas librerías de interfaz gráfica en Java.                                                                                                |
| [[Programación_1DAM/Unidad 06 JavaFX/2. JavaFX\|2. JavaFX]]                                                                                                                 | Comparativa entre las distintas librerías de interfaz gráfica en Java.                                                                                                |
| [[Programación_1DAM/Unidad 06 JavaFX/Apéndice - recursos del proyecto\|Apéndice - recursos del proyecto]]                                                                   | En lugar de incluir todo el código (componentes y eventos) en un fichero, podemos separarlos en distintos objetos de forma que cada uno se ocupa de algo en concreto. |
| [[Programación_1DAM/Unidad 06 JavaFX/Apéndice - Principios de diseño de interfaces gráficas de usuario\|Apéndice - Principios de diseño de interfaces gráficas de usuario]] | Pongamos en práctica lo visto hasta ahora                                                                                                                             |

{ .block-language-dataview}
---

<p><span>⬅️ <strong>Anterior:</strong> <a data-tooltip-position="top" aria-label="Programación_1DAM/Unidades/Unidad 6 - Interfaz gráfica de usuario (GUI) - Swing.md" data-href="Programación_1DAM/Unidades/Unidad 6 - Interfaz gráfica de usuario (GUI) - Swing.md" href="Programación_1DAM/Unidades/Unidad 6 - Interfaz gráfica de usuario (GUI) - Swing.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 6 - Interfaz gráfica de usuario (GUI) - Swing</a> | 🏠 <strong>Libro:</strong> <a data-tooltip-position="top" aria-label="Programación_1DAM/Libros/Libro Programación (1º DAM, 1º DAW).md" data-href="Programación_1DAM/Libros/Libro Programación (1º DAM, 1º DAW).md" href="Programación_1DAM/Libros/Libro Programación (1º DAM, 1º DAW).md" class="internal-link" target="_blank" rel="noopener nofollow">Libro Programación (1º DAM, 1º DAW)</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="Programación_1DAM/Unidades/Unidad 7 - POO - Aspectos avanzados.md" data-href="Programación_1DAM/Unidades/Unidad 7 - POO - Aspectos avanzados.md" href="Programación_1DAM/Unidades/Unidad 7 - POO - Aspectos avanzados.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 7 - POO - Aspectos avanzados</a> ➡️</span></p>
