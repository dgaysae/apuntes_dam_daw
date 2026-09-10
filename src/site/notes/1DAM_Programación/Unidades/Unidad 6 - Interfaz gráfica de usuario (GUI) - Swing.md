---
{"dg-publish":true,"permalink":"/1-dam-programacion/unidades/unidad-6-interfaz-grafica-de-usuario-gui-swing/","tags":["java/swing"],"dg-note-properties":{"modulo":"[[Módulos/Programación]]","libro":"[[Apuntes/Programación (1º DAM, 1º DAW)]]","descripcion":"La mayoría de los usuarios necesitan una interfaz que les permita realizar tareas de forma visualmente fácil e intuitiva. Aquí entran en juego las GUI.","orden":6,"tags":["java/swing"],"estado":"revisar"}}
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

Bloque de contenidos básicos: **Lectura y escritura de información:**  
- **Tipos de flujos. Flujos de bytes y de caracteres.**  
- **Clases relativas a flujos.**  
- **Utilización de flujos.**  
- **Entrada desde teclado.**  
- **Salida a pantalla.**  
- **Ficheros de datos. Registros.**  
- **Apertura y cierre de ficheros. Modos de acceso.**  
- **Escritura y lectura de información en ficheros.**  
- **Utilización de los sistemas de ficheros.**  
- **Creación y eliminación de ficheros y directorios.**  
- **Interfaces.**  
- **Concepto de evento.**  
- **Creación de controladores de eventos.**

| Peso RA en trim. | RA asociado | Periodo |  | Criterios de evaluación | Peso CE en la RA | Peso RA en módulo |
| :---: | :---- | :---: | :---: | :---- | :---: | :---: |
| 50,00% | RA 5. Realiza operaciones de entrada y salida de información, utilizando procedimientos específicos del lenguaje y librerías de clases. | 1/2/2027 | 26/2/2027 | a) Se ha utilizado la consola para realizar operaciones de entrada y salida de información. | 5,00% | 12,00% |
|  |  |  |  | b) Se han aplicado formatos en la visualización de la información. | 5,00% |  |
|  |  |  |  | c) Se han reconocido las posibilidades de entrada / salida del lenguaje y las librerías asociadas. | 5,00% |  |
|  |  |  |  | d) Se han utilizado ficheros para almacenar y recuperar información. | 10,00% |  |
|  |  |  |  | e) Se han creado programas que utilicen diversos métodos de acceso al contenido de los ficheros. | 10,00% |  |
|  |  |  |  | f) Se han utilizado las herramientas del entorno de desarrollo para crear interfaces gráficos de usuario simples. | 10,00% |  |
|  |  |  |  | g) Se han programado controladores de eventos. | 10,00% |  |
|  |  |  |  | h) Se han escrito programas que utilicen interfaces gráficos para la entrada y salida de información. | 45,00% |  |

---

De momento, solo has programado **aplicaciones en «modo texto»**, donde la interacción con el usuario se limita a la consola: leer datos y mostrar resultados línea a línea. Este enfoque es perfecto para aprender lógica y estructuras básicas, pero **el software que usamos a diario va mucho más allá**. En este capítulo darás el salto a la **programación gráfica**, donde tus programas podrán tener **ventanas, botones, menús e interfaces mucho más intuitivas**.

En el ecosistema de Java existen varias tecnologías para crear interfaces gráficas: **<abbr title="Abstract Window Toolkit">AWT</abbr>, Swing y JavaFX**. **AWT** fue la primera aproximación, con componentes básicos dependientes del sistema operativo. **Swing** supuso un gran avance al ofrecer componentes más ricos y portables. **JavaFX**, más moderno, incorpora estilos visuales, animaciones y una arquitectura más flexible para aplicaciones actuales.

Aprenderás cómo construir ventanas, organizar elementos en pantalla, responder a eventos del usuario (como clics o pulsaciones de teclas) y separar la lógica de tu programa de su presentación visual usando **Java Swing**. Este cambio no solo mejora la apariencia de tus aplicaciones, sino también la forma de diseñarlas.

---
## Índice de contenidos

| File                                                                                                                                                                          | Descripción                                                                                                                                                           |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[1DAM_Programación/Unidad 06 Swing/1. AWT, Swing y JavaFX. ¿Qué es mejor?\|1. AWT, Swing y JavaFX. ¿Qué es mejor?]]                                                       | Comparativa entre las distintas librerías de interfaz gráfica en Java.                                                                                                |
| [[1DAM_Programación/Unidad 06 Swing/2. Componentes de swing\|2. Componentes de swing]]                                                                                     | Estructura de clases de Swing.                                                                                                                                        |
| [[1DAM_Programación/Unidad 06 Swing/3. Contenedores de Swing\|3. Contenedores de Swing]]                                                                                   | Los contenedores son los elementos que sirven para mostrar otros componentes. En ellos se incluirán botones, etiquetas, etc.                                          |
| [[1DAM_Programación/Unidad 06 Swing/4. LayoutManager - Cómo distribuir los componentes en la ventana\|4. LayoutManager - Cómo distribuir los componentes en la ventana]]   | Los LayoutManager indican al contendor cómo debe distribuir los componentes que se le añaden.                                                                         |
| [[1DAM_Programación/Unidad 06 Swing/5. Otros componentes de Swing\|5. Otros componentes de Swing]]                                                                         | Botones, etiquetas, radio buttons, etc.                                                                                                                               |
| [[1DAM_Programación/Unidad 06 Swing/6. Eventos\|6. Eventos]]                                                                                                               | Podemos capturar lo que sucede en nuestras ventanas (se pulsa un botón, se escribe un texto, etc.) e indicarle a nuestra aplicación que haga algo.                    |
| [[1DAM_Programación/Unidad 06 Swing/7. Patrón MVC (Modelo-Vista-Controlador)\|7. Patrón MVC (Modelo-Vista-Controlador)]]                                                   | En lugar de incluir todo el código (componentes y eventos) en un fichero, podemos separarlos en distintos objetos de forma que cada uno se ocupa de algo en concreto. |
| [[1DAM_Programación/Unidad 06 Swing/8. Ejemplo práctico\|8. Ejemplo práctico]]                                                                                             | Pongamos en práctica lo visto hasta ahora                                                                                                                             |
| [[1DAM_Programación/Unidad 06 Swing/Apéndice - recursos del proyecto\|Apéndice - recursos del proyecto]]                                                                   | En lugar de incluir todo el código (componentes y eventos) en un fichero, podemos separarlos en distintos objetos de forma que cada uno se ocupa de algo en concreto. |
| [[1DAM_Programación/Unidad 06 Swing/Referencias\|Referencias]]                                                                                                             | Aquí tienes distintas fuentes y referencias documentales para consultar, ahondar y aprender más sobre los temas que hemos tratado en esta unidad                      |
| [[1DAM_Programación/Unidad 06 Swing/Apéndice - Principios de diseño de interfaces gráficas de usuario\|Apéndice - Principios de diseño de interfaces gráficas de usuario]] | Pongamos en práctica lo visto hasta ahora                                                                                                                             |
| [[1DAM_Programación/Unidad 06 Swing/Referencias internas\|Referencias internas]]                                                                                           | Aquí tienes distintas fuentes y referencias documentales para consultar, ahondar y aprender más sobre los temas que hemos tratado en esta unidad                      |

{ .block-language-dataview}

---

<p><span>⬅️ <strong>Anterior:</strong> <a data-tooltip-position="top" aria-label="1DAM_Programación/Unidades/Unidad 5 - Estructuras de almacenamiento.md" data-href="1DAM_Programación/Unidades/Unidad 5 - Estructuras de almacenamiento.md" href="1DAM_Programación/Unidades/Unidad 5 - Estructuras de almacenamiento.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 5 - Estructuras de almacenamiento</a> | 🏠 <strong>Libro:</strong> <a data-tooltip-position="top" aria-label="Apuntes/Programación (1º DAM, 1º DAW).md" data-href="Apuntes/Programación (1º DAM, 1º DAW).md" href="Apuntes/Programación (1º DAM, 1º DAW).md" class="internal-link" target="_blank" rel="noopener nofollow">Programación (1º DAM, 1º DAW)</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="1DAM_Programación/Unidades/Unidad 6 - Interfaz gráficos (GUI) - JavaFX.md" data-href="1DAM_Programación/Unidades/Unidad 6 - Interfaz gráficos (GUI) - JavaFX.md" href="1DAM_Programación/Unidades/Unidad 6 - Interfaz gráficos (GUI) - JavaFX.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 6 - Interfaz gráficos (GUI) - JavaFX</a> ➡️</span></p>
