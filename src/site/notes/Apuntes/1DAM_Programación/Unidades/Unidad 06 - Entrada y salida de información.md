---
{"dg-publish":true,"permalink":"/apuntes/1-dam-programacion/unidades/unidad-06-entrada-y-salida-de-informacion/","tags":["java/io","java/consola","java/ficheros","java/javafx"],"dg-note-properties":{"modulo":"[[Módulos/Programación]]","libro":"[[Libros/Programación (1º DAM, 1º DAW)]]","descripcion":"Un programa necesita comunicarse con el exterior: leer lo que teclea el usuario, guardar y recuperar datos en ficheros y ofrecer una interfaz gráfica cómoda. En esta unidad aprenderás las tres formas de entrada y salida de información en Java.","orden":6,"ra":"RA5","tags":["java/io","java/consola","java/ficheros","java/javafx"],"estado":"revisar"}}
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

### Contenidos básicos

Lectura y escritura de información:  
- Tipos de flujos. Flujos de bytes y de caracteres.  
- Clases relativas a flujos.  
- Utilización de flujos.  
- Entrada desde teclado.  
- Salida a pantalla.  
- Ficheros de datos. Registros.  
- Apertura y cierre de ficheros. Modos de acceso.  
- Escritura y lectura de información en ficheros.  
- Utilización de los sistemas de ficheros.  
- Creación y eliminación de ficheros y directorios.  
- Interfaces.  
- Concepto de evento.  
- Creación de controladores de eventos.

### RA asociado y criterios de evaluación

**RA 5. Realiza operaciones de entrada y salida de información, utilizando procedimientos específicos del lenguaje y librerías de clases.**

Criterios de evaluación para el RA:
a) Se ha utilizado la consola para realizar operaciones de entrada y salida de información.
b) Se han aplicado formatos en la visualización de la información.
c) Se han reconocido las posibilidades de entrada / salida del lenguaje y las librerías asociadas.
d) Se han utilizado ficheros para almacenar y recuperar información.
e) Se han creado programas que utilicen diversos métodos de acceso al contenido de los ficheros.
f) Se han utilizado las herramientas del entorno de desarrollo para crear interfaces gráficos de usuario simples.
g) Se han programado controladores de eventos.
h) Se han escrito programas que utilicen interfaces gráficos para la entrada y salida de información.

### Organización de la unidad

La unidad se divide en dos bloques, según los criterios de evaluación que trabaja cada uno:

| Bloque | Criterios | Contenido |
| --- | --- | --- |
| **A. Consola y ficheros** | a), b), c), d), e) | Repaso de la consola y salida con formato; flujos; ficheros secuenciales y de acceso aleatorio con `java.io` y NIO2 |
| **B. Interfaces gráficas con JavaFX** | f), g), h) | Componentes, contenedores, eventos y Scene Builder |
| *Anexo: Swing* | f), g), h) | Alternativa a JavaFX con la librería clásica de Java |

---

> [!note]  
> Un programa necesita comunicarse con el exterior: leer lo que teclea el usuario, guardar y recuperar datos en ficheros y ofrecer una interfaz gráfica cómoda. En esta unidad aprenderás las tres formas de entrada y salida de información en Java.

Hasta ahora, tus programas han vivido casi aislados: leían algún dato del teclado, hacían cálculos en la memoria RAM y mostraban el resultado en la consola. Al terminar, **toda la información se perdía**. Y la interacción con el usuario se limitaba a líneas de texto.

En esta unidad vas a abrir tus programas al exterior en **tres direcciones**:

- **La consola**, que ya conoces, ahora con **salida con formato** para presentar la información de forma clara.
- **Los ficheros**, para **guardar datos en memoria secundaria** y recuperarlos más tarde. Aprenderás tanto el enfoque clásico (**`java.io`**) como el moderno (**NIO2**).
- **Las interfaces gráficas**, con **ventanas, botones y menús** que responden a las acciones del usuario mediante **eventos**. Usaremos **JavaFX**, la librería gráfica más moderna de Java.

Las tres tienen algo en común: son formas de **entrada y salida de información**. Y, como verás, la consola y los ficheros funcionan con el mismo mecanismo: los **flujos** (*streams*).

¡Al ataque!

---

## Índice de contenidos

### A. Consola y ficheros

> [!NOTE] Entrada y salida por consola
> Lo básico de la entrada por teclado y la salida por consola (RA 5 · CE a) se adelanta en la Unidad 01, porque se necesita desde la Unidad 02: [[Apuntes/1DAM_Programación/Unidad 01/10. Apéndice. Entrada y salida por consola\|10. Apéndice. Entrada y salida por consola]].

| File                                                                                                                                                                                                | Descripción                                                                                                                                                   |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[Apuntes/1DAM_Programación/Unidad 06 Flujos y ficheros/0. Repaso - Entrada y salida por consola\|0. Repaso - Entrada y salida por consola]]                                                     | Repaso de la entrada por teclado y la salida por consola, y cómo dar formato a la información que mostramos con printf, String.format y formatted.            |
| [[Apuntes/1DAM_Programación/Unidad 06 Flujos y ficheros/1. Conceptos básicos sobre ficheros\|1. Conceptos básicos sobre ficheros]]                                                               | ¿Qué es un fichero? ¿Como almacena y organiza la información?                                                                                                 |
| [[Apuntes/1DAM_Programación/Unidad 06 Flujos y ficheros/2. La API clásica de Java - java.io\|2. La API clásica de Java - java.io]]                                                               | Qué mecanismos incorpora Java para enviar/recibir datos hacia/desde ficheros y en qué formas (como caracteres, datos primitivos o incluso objetos completos). |
| [[Apuntes/1DAM_Programación/Unidad 06 Flujos y ficheros/3. Procesamiento de ficheros secuenciales en Java\|3. Procesamiento de ficheros secuenciales en Java]]                                   | Operaciones básicas que se pueden hacer sobre ficheros.                                                                                                       |
| [[Apuntes/1DAM_Programación/Unidad 06 Flujos y ficheros/4. Procesamiento de ficheros de acceso directo o aleatorio en Java\|4. Procesamiento de ficheros de acceso directo o aleatorio en Java]] | Operaciones sobre ficheros de acceso directo.                                                                                                                 |
| [[Apuntes/1DAM_Programación/Unidad 06 Flujos y ficheros/5. Los ficheros en Java moderno - NIO2\|5. Los ficheros en Java moderno - NIO2]]                                                         | NIO2, o cómo abrir un solo canal o stream bidireccional hacia ficheros.                                                                                       |
| [[Apuntes/1DAM_Programación/Unidad 06 Flujos y ficheros/6. Buenas prácticas\|6. Buenas prácticas]]                                                                                               | Para mitigar los posibles problemas del tratamiento de ficheros, veamos algunas buenas prácticas.                                                             |

{ .block-language-dataview}

### B. Interfaces gráficas con JavaFX

| File                                                                                                                                                                                   | Descripción                                                                                                                                                                           |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[Apuntes/1DAM_Programación/Unidad 06 JavaFX/3. Arquitectura típica de una aplicación con JavaFX\|3. Arquitectura típica de una aplicación con JavaFX]]                             | \-                                                                                                                                                                                    |
| [[Apuntes/1DAM_Programación/Unidad 06 JavaFX/5. Nodos de JavaFX\|5. Nodos de JavaFX]]                                                                                               | \-                                                                                                                                                                                    |
| [[Apuntes/1DAM_Programación/Unidad 06 JavaFX/9. Scene Builder\|9. Scene Builder]]                                                                                                   | \-                                                                                                                                                                                    |
| [[Apuntes/1DAM_Programación/Unidad 06 JavaFX/1. AWT, Swing y JavaFX. ¿Qué es mejor?\|1. AWT, Swing y JavaFX. ¿Qué es mejor?]]                                                       | Comparativa entre las distintas librerías de interfaz gráfica en Java.                                                                                                                |
| [[Apuntes/1DAM_Programación/Unidad 06 JavaFX/2. JavaFX\|2. JavaFX]]                                                                                                                 | Qué es JavaFX, cómo organiza la interfaz en un grafo de escena formado por nodos y qué ventajas ofrece frente a Swing.                                                                |
| [[Apuntes/1DAM_Programación/Unidad 06 JavaFX/4. Comprendiendo cómo funciona JavaFX con un ejemplo\|4. Comprendiendo cómo funciona JavaFX con un ejemplo]]                           | Un ejemplo completo, paso a paso, para ver cómo encajan la clase principal, el FXML, el controlador, el modelo, el CSS y los eventos.                                                 |
| [[Apuntes/1DAM_Programación/Unidad 06 JavaFX/6. Eventos\|6. Eventos]]                                                                                                               | Los principales tipos de eventos de JavaFX (ActionEvent, MouseEvent, KeyEvent…) y cuándo se producen.                                                                                 |
| [[Apuntes/1DAM_Programación/Unidad 06 JavaFX/7. Manejadores de eventos (listeners)\|7. Manejadores de eventos (listeners)]]                                                         | Cómo responder a los eventos del usuario con manejadores (listeners), tanto desde el FXML como desde el código Java.                                                                  |
| [[Apuntes/1DAM_Programación/Unidad 06 JavaFX/8. Contenedores (layouts)\|8. Contenedores (layouts)]]                                                                                 | Los layouts de JavaFX y cómo usarlos para organizar los nodos en la ventana y adaptarlos a su tamaño.                                                                                 |
| [[Apuntes/1DAM_Programación/Unidad 06 JavaFX/10. Compilar aplicaciones con JavaFX\|10. Compilar aplicaciones con JavaFX]]                                                           | Cómo compilar y ejecutar aplicaciones JavaFX desde la línea de comandos, NetBeans, IntelliJ IDEA y Visual Studio Code.                                                                |
| [[Apuntes/1DAM_Programación/Unidad 06 JavaFX/Apéndice - Principios de diseño de interfaces gráficas de usuario\|Apéndice - Principios de diseño de interfaces gráficas de usuario]] | Principios universales de diseño de interfaces gráficas, en forma de lo que se debe y no se debe hacer, para mejorar la usabilidad de nuestras aplicaciones.                          |
| [[Apuntes/1DAM_Programación/Unidad 06 JavaFX/Apéndice - recursos del proyecto\|Apéndice - recursos del proyecto]]                                                                   | Dónde guardar las imágenes, iconos y otros recursos de un proyecto Maven y cómo cargarlos desde el código, tanto en Swing como en JavaFX, para que funcionen también en el JAR final. |
| [[Apuntes/1DAM_Programación/Unidad 06 JavaFX/Referencias\|Referencias]]                                                                                                             | Aquí tienes distintas fuentes y referencias documentales para consultar, ahondar y aprender más sobre los temas que hemos tratado en esta unidad                                      |

{ .block-language-dataview}

### Anexo: interfaces gráficas con Swing

> [!TIP] ¿Prefieres Swing?
> Si en clase trabajáis con Swing, o tienes que mantener una aplicación antigua, consulta el anexo [[Apuntes/1DAM_Programación/Unidades/Unidad 06 - Anexo - Swing\|Unidad 06 - Anexo - Swing]]. Cubre los mismos criterios de evaluación que el bloque B.

---

<p><span>⬅️ <strong>Anterior:</strong> <a data-tooltip-position="top" aria-label="Apuntes/1DAM_Programación/Unidades/Unidad 05 - Estructuras de almacenamiento.md" data-href="Apuntes/1DAM_Programación/Unidades/Unidad 05 - Estructuras de almacenamiento.md" href="Apuntes/1DAM_Programación/Unidades/Unidad 05 - Estructuras de almacenamiento.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 05 - Estructuras de almacenamiento</a> | 🏠 <strong>Libro:</strong> <a data-tooltip-position="top" aria-label="Libros/Programación (1º DAM, 1º DAW).md" data-href="Libros/Programación (1º DAM, 1º DAW).md" href="Libros/Programación (1º DAM, 1º DAW).md" class="internal-link" target="_blank" rel="noopener nofollow">Programación (1º DAM, 1º DAW)</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="Apuntes/1DAM_Programación/Unidades/Unidad 07 - POO - Aspectos avanzados.md" data-href="Apuntes/1DAM_Programación/Unidades/Unidad 07 - POO - Aspectos avanzados.md" href="Apuntes/1DAM_Programación/Unidades/Unidad 07 - POO - Aspectos avanzados.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 07 - POO - Aspectos avanzados</a> ➡️</span></p>
