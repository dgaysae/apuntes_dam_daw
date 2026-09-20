---
{"dg-publish":true,"permalink":"/1-dam-programacion/unidad-03-poo-los-objetos/","dg-note-properties":{"unidad":"[[1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos]]","modulo":"[[Módulos/Programación]]","libro":"[[Apuntes/Programación (1º DAM, 1º DAW)]]"}}
---


```table-of-contents
```

---


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/1-dam-programacion/unidades/unidad-3-poo-los-objetos/#datos-de-la-unidad" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## Datos de la unidad

La siguiente tabla muestra los contenidos básicos de la norma educativa que contempla esta unidad, al igual que el objetivo o RA que se quiere alcanzar y los criterios de evaluación que se seguirán para ello.

### Contenidos básicos

Utilización de objetos:  
- Características de los objetos.  
- Instanciación de objetos.  
- Utilización de métodos.  
- Utilización de propiedades.  
- Utilización de métodos estáticos.  
- Librerías de objetos. Inclusión y uso.  
- Constructores.  
- Destrucción de objetos y liberación de memoria.  
- Entornos de desarrollo para programación orientada a objetos.  
- Entornos específicos.  
- Plugins de integración en entornos genéricos.

### RA asociado y criterios de evaluación

**RA 2. Escribe y prueba programas sencillos, reconociendo y aplicando los fundamentos de la programación orientada a objetos.**

Criterios de evaluación para el RA:
a) Se han identificado los fundamentos de la programación orientada a objetos.
b) Se han escrito programas simples.
c) Se han instanciado objetos a partir de clases predefinidas
d) Se han utilizado métodos y propiedades de los objetos
e) Se han escrito llamadas a métodos estáticos 
f) Se han utilizado parámetros en la llamada a métodos 
g) Se han incorporado y utilizado librerías de objetos 
h) Se han utilizado constructores 
i) Se ha utilizado el entorno integrado de desarrollo en la creación y compilación de programas simples 

---

Las variables que hemos usado hasta ahora nos permitían guardar datos primitivos. Así, en cada variable se puede almacenar un número, un texto, un carácter, un valor lógico, etc.

Es decir, **una variable, un valor**.

Si tenemos que hacer un programa que gestione las cuentas de una empresa tendríamos que contemplar muchas variables:

- Las de los empleados: _nombre del empleado, fecha de nacimiento, documento de identificación, número de la seguridad social, nómina, retenciones, incentivos, número de cuenta_, etc. 
- Las de los clientes: _nombre del cliente, CIF/NIF, dirección, cuenta de facturación, flags de promociones y conciciones especiales_...
- Las de proveedores: bla, bla, bla...

Y así sucesivamente. Si empiezas a contar el número de variables que debes crear para tu programa, acabarás tirándote de los pelos.

Pero la POO vino al rescate hace ya unos años.

¿Y si en un bloque de código -al que llamamos `Empleado`- ponemos las variables y funcionalidades propias y adecuadas para su gestión? ¿Y si hacemos otro similar para los proveedores y para los clientes y así sucesivamente...?

Esto se conoce como encapsulamiento y es una de las características más básicas en la POO.

En esta unidad vamos a empezar a ver cómo funciona.

Estás a punto de empezar en el mundo de la POO ¡Vamos a ello!

---

</div></div>


---

# 1. Entendiendo la programación orientada a objetos

## 1.1 Pensamiento orientado a objetos

(Tanto esta sección como la siguiente han sido adaptadas de la "Guía del usuario de Ruby" escrita por Yukihiro "Matz" Matsumoto, creador del lenguaje Ruby) 

La orientación a objetos es una palabra con gancho. Llamar a cualquier cosa “orientada a objetos” puede hacerla parecer más elegante. Java reclama ser un lenguaje orientado a objetos: pero, ¿qué significa exactamente “orientado a objetos”?  

Existe una gran variedad de respuestas a esta pregunta, y probablemente todas ellas se pueden reducir a la misma cosa.  

En vez de recapitular demasiado deprisa, pensemos un momento en el paradigma de la programación tradicional. Tradicionalmente, un problema informático se ataca produciendo algún tipo de representación de datos y procedimientos que operan sobre esos datos. Bajo este modelo, los datos son inertes, pasivos e incapaces. Están a la completa merced de un gran cuerpo procedimental, que es activo, lógico y todopoderoso.  

El problema con esta aproximación es, que los programas los escriben programadores, que son humanos, que sólo pueden retener cierto número de detalles en sus cabezas en un momento determinado. A medida que crece el proyecto, el núcleo procedimental crece hasta un punto que se hace difícil recordar cómo funciona todo el conjunto. Pequeños lapsos de pensamiento o errores tipográficos llegan a ser errores muy ocultos. Empiezan a surgir interacciones complejas e inintencionadas dentro de este núcleo y el mantenimiento se convierte en algo parecido a transportar un calamar gigante intentando que ninguno de sus tentáculos te alcance la cara. Existen políticas de programación que ayudan a minimizar y localizar errores dentro de este paradigma tradicional pero existe una solución mejor que pasa fundamentalmente por cambiar la forma de trabajar.  

Lo que hace la programación orientada a objetos es, delegar la mayoría del trabajo mundano y repetitivo a los propios datos; modifica el concepto de los datos que pasan de pasivos a activos. Dicho de otra forma.  

* Dejamos de tratar cada pieza de dato como una caja en la que se puede abrir su tapa y arrojar cosas en ella.

* Empezamos a tratar cada pieza de dato como una máquina funcional cerrada con unos pocos interruptores y diales bien definidos.  

Lo que se define anteriormente como una “máquina” puede ser, en su interior, algo muy simple o muy complejo. No se puede saber desde el exterior y no se nos permite abrir la máquina (excepto cuando estamos completamente seguros de que algo está mal en su diseño), por lo que se nos obliga a conmutar interruptores y leer los diales para interactuar con los datos. Una vez construida, no queremos tener que pensar en cómo funciona internamente.  

Se podría pensar que estamos haciendo más trabajo nosotros mismos, pero esta forma de trabajo tiende a ser un buen método para evitar que vayan mal todo tipo de cosas.

Comencemos con un ejemplo que es demasiado simple para tener algún valor práctico pero que al menos muestra parte del concepto. Nuestro coche consta de un cuentakilómetros. Su trabajo consiste en llevar un registro de la distancia recorrida desde la última vez que se pulsó el botón de reinicialización. ¿Cómo podríamos representar esto en un lenguaje de programación? En C, por ejemplo, el cuentakilómetros sería, simplemente, una variable numérica de tipo float. El programa manipularía esa variable aumentando el valor en pequeños incrementos y ocasionalmente la reinicializaría a cero cuando fuese apropiado. ¿Qué hay de malo en esto?

Un error en el programa podría asignar un valor falso a la variable, por cualquier número de razones inesperadas. Cualquiera que haya programado en C sabe que se pueden perder horas o días tratando de encontrar ese error que una vez encontrado parece absurdamente simple. El momento de encontrar el error es indicado por una sonora palmada en la frente.

En un contexto orientado a objetos, el mismo problema se puede atacar desde un ángulo completamente diferente. La primera cosa que se pregunta un programador al diseñar el cuentakilómetros no es “¿qué tipos de datos son los más cercanos para representar esta cosa?” sino “¿cómo se supone que actúa esta cosa?”. La diferencia termina siendo profunda.

Es necesario dedicar cierto tiempo a decidir para qué es exactamente un cuentakilómetros y cómo se espera que el mundo exterior interactúe con él. Se decide entonces construir una pequeña máquina con controles que permitan incrementar, reinicializar y leer su valor y nada más.

El cuentakilómetros se crea sin un mecanismo para asignarle un valor arbitrario. ¿Por qué? Porque es de todos sabido que los cuentakilómetros no trabajan de esa forma. Existen sólo unas cuantas cosas que un cuentakilómetros puede hacer, y sólo permitimos esas cosas. Así, si alguien desde un programa trata de asignar algún otro valor (por ejemplo, la temperatura límite del sistema de control de climatización del vehículo) al cuentakilómetros, aparece de inmediato una indicación de lo que va mal. Al ejecutar el programa se nos dice (o posiblemente, al compilarlo dependiendo de la naturaleza del lenguaje) que NO se nos permite asignar valores arbitrarios al objeto Cuentakilómetros. El mensaje podría ser menos preciso, pero sí razonablemente próximo al problema. Esto no evita el error, ¿verdad? pero apunta rápidamente en la dirección de la causa. Esta es sólo alguna de las múltiples formas en las que la programación OO nos puede evitar muchas pérdidas de tiempo.  

Existe, normalmente, un nivel de abstracción superior a éste porque resulta que es igual de fácil construir una factoría que hace máquinas como hacer una máquina individual. Es poco probable que construyamos un único cuentakilómetros, sino que nos preparamos para construir cualquier cantidad de cuentakilómetros a partir de un único patrón. El patrón (o, si lo prefieres, la factoría de cuentakilómetros) es lo que se conoce como clase, y el cuentakilómetros individual sacado del patrón (o construido en la línea de montaje de la factoría) se conoce como objeto.  

Conviene resaltar aquí que la utilización de un lenguaje OO no obliga a un diseño OO válido. Es posible, en cualquier lenguaje, escribir código poco claro, descuidado, mal concebido, erróneo e inestable. Lo que permite Java (en oposición, especialmente, a C++) es que la práctica de la programación OO sea lo suficientemente natural para que, incluso, trabajando a pequeña escala no se sienta la necesidad de recurrir a un código mal estructurado por evitar esfuerzo.  

A continuación hablaremos de los “interruptores y diales” (métodos del objeto) y en próximos capítulos pasaremos a las "factorías" (clases) 

## 1.2 Métodos

¿Qué es un método? En la <abbr title="Programación Orientada a Objetos">POO</abbr> no se piensa en operar sobre los datos directamente desde el exterior de un objeto, sino que los objetos tienen algún conocimiento de cómo se debe operar sobre ellos (cuando se les pide amablemente). Podríamos decir que se pasa un mensaje al objeto y este mensaje obtiene algún tipo de acción o respuesta significativa. Esto debe ocurrir sin que tengamos necesariamente algún tipo de conocimiento o nos importe como realiza el objeto, interiormente, el trabajo. Las tareas que podemos pedir que un objeto realice (o lo que es lo mismo, los mensajes que comprende) son los métodos.

En Ruby, se llama a un método con la notación punto (como en C++ o Java). El objeto con el que nos comunicamos se nombra a la izquierda del punto. Por ejemplo:

```java
String mi_cadena = "Esto es una cadena de caracteres";   
System.out.println("La longitud de la cadena es: " + mi_cadena.length());
```

La salida por pantalla será:

```
La longitud de la cadena es 32
```

Intuitivamente, a este objeto cadena se le está pidiendo que diga la longitud que tiene (y, como es una cadena de caracteres, nos responde con la cantidad total de letras de que consta). Técnicamente, lo que hemos hecho se llama "invocar el método `length()` del objeto mi_cadena". 

Otros objetos pueden hacer una interpretación un poco diferente de length. La decisión sobre cómo responder a un mensaje se hace al vuelo, durante la ejecución del programa, y la acción a tomar puede cambiar dependiendo de la variable a que se haga referencia.

```java
String mi_cadena = "Esto es una cadena de caracteres";   
String[] mi_array = {mi_cadena, "Otra cadena"};   
System.out.println("La longitud de la cadena es: " + mi_cadena.length());
System.out.println("La longitud del array es: " + mi_array.length());
```

La salida por pantalla será:

```
La longitud de la cadena es 32   
La longitud del array es 2
```

Lo que indicamos con length puede variar dependiendo del objeto con el que nos comunicamos. En el primer caso, le pedimos a mi_cadena su longitud. Como se trata de una cadena de caracteres, solo hay una respuesta posible. En el segundo caso, se lo pedimos a mi_array. Podríamos pensar que el método length pudiera contar todos los caracteres en total almacenados en el objeto (43 en total). Pero lo más plausible es que nos devuelva 2, que es el número de elementos del array. 

No importa si por el momento no entiendes bien lo que son los strings o los arrays. Lo que hay que tener en cuenta ahora es que el objeto array conoce lo que significa ser un array, y el string, lo que significa ser string, y ambos saben exactamente lo que tienen que hacer si les pedimos que nos calculen su propia longitud (length).

En Java, las piezas de datos llevan consigo ese *conocimiento,* por lo que las solicitudes que se les hace se pueden satisfacer en las formas adecuadas para el tipo de dato. Esto libera al programador de la carga de memorizar una gran cantidad de nombres de funciones, ya que una cantidad relativamente pequeña de nombres de métodos, que corresponden a conceptos que sabemos como expresar en lenguaje natural, se pueden aplicar a diferentes tipos de datos siendo el resultado el que lógicamente cabría esperar. Esta característica de los lenguajes OO se conoce como polimorfismo[^1].

Cuando un objeto recibe un mensaje que no conoce, se produce un error. Por lo tanto, hay que conocer qué métodos son aceptables para un objeto, aunque no se necesita saber cómo están programados por dentro.

## 1.3 Atributos

Los atributos de un objeto definen las características del mismo. Por ejemplo, un atributo del cuentakilómetros es el contador del número de kilómetros, o un atributo de un String debe de ser el número de caracteres de que consta la cadena.

Al programador que usa un objeto deberían importarle un bledo los atributos del mismo. Él (o ella) se encargará de usar el objeto a través de sus métodos, y éstos operarán con los atributos, si ello es necesario, de forma totalmente transparente al programador. Es decir, los atributos raramente son accesibles desde el exterior del objeto, salvo que, por razones de diseño, el programador del objeto haya decidido lo contrario.



[^1]:   El polimorfismo es una característica muy interesante de los <abbr title="Object Oriented Language">OOL</abbr> que, lamentablemente, Java no explota en toda sus posibilidades, cosa que si hacen lenguajes posteriores como Ruby.


# 2. Definiciones formales

Una vez vista de manera informal la filosofía que subyace en el paradigma de orientación a objetos, pasamos a enumerar de manera más formal los diferentes conceptos que aparecerán de ahora en adelante de manera insistente. Como hemos dicho muchas veces, no te preocupes (aún) si no entiendes todo lo que aquí se dice. Preocúpate solo si, al finalizar el curso, sigues sin saber qué son algunos de los siguientes conceptos.

## 2.1. Objetos

Un objeto es una unidad que engloba dentro de sí un conjunto de datos y las funciones necesarias para el tratamiento de esos datos.

Un objeto se caracteriza por:

* **Su identidad**: cada objeto es único y diferente del resto. Internamente se le asigna un ID para diferenciarlo de otros objetos, aunque pertenezcan a la misma clase y tengan todos sus valores internos con el mismo valor. 

* **Su estado**: el estado de un objeto viene dado por el valor de sus atributos o variables internas. 

* **Su comportamiento**: el comportamiento de un objeto se define mediante los métodos o fragmentos de código que operan con los atributos internos del objeto e interactúan, si es necesario, con otros objetos.  

## 2.2. Atributos

Los atributos son los **datos incluidos en un objeto**. Son como las variables en los lenguajes de programación clásicos, pero están encapsuladas dentro de un objeto y, salvo que se indique lo contrario, son invisibles desde el exterior. 

También se les conoce como **propiedades** del objeto, y sirven para representar el **estado del objeto** en cada momento.

## 2.3. Métodos

Se llaman métodos a las funciones que pertenecen a un objeto. Es decir: son fragmentos de código con un nombre que permite invocarlos y ejecutarlos, pero están encapsulados dentro del objeto. Tienen acceso a los atributos del mismo y son la forma de operar con los atributos desde el exterior del objeto. Son, en definitiva, los "diales" de la caja negra.

En otras palabras, los métodos **establecen las acciones que puede realizar** el objeto.

## 2.4. Clases

Una clase es un patrón para construir objetos. Por tanto, un objeto es una variable perteneciente a una clase determinada. Es importante distinguir entre objetos y clases: la clase es simplemente una declaración, no tiene asociado ningún objeto. Y todo objeto debe pertenecer a una clase. 

## 2.5. Mensajes

El mensaje es el modo en que se comunican los objetos entre sí. Un mensaje no es más que una llamada a un método de un determinado objeto. Cuando llamemos a un método de un objeto, a menudo diremos que estamos enviando un mensaje a ese objeto, y el objeto reaccionará ejecutando el código asociado a ese mensaje.  

## 2.6. Interfaz

Las clases (y, por lo tanto, también los objetos) tienen partes públicas y partes privadas. La parte pública es visible para el resto de los objetos, mientras que la privada sólo es visible para el propio objeto. A la parte pública de un objeto se le denomina interfaz.  

## 2.7. Características de la OOP

### 2.7.1. Abstracción

Cuando se programa con OOP, se intentan abstraer las características de los objetos del problema que estamos tratando de informatizar, para crear a partir de ello las clases y sus métodos. 

### 2.7.2. Encapsulamiento

Como ya hemos dicho varias veces, los miembros privados de una clase no son accesibles desde otras clases. Es decir, desde una clase no se puede invocar un método de otra clase a menos que se indique lo contrario. 

Se denomina encapsulamiento al hecho de que cada objeto se comporte de modo autónomo, de manera que lo que pase en su interior sea invisible para el resto de objetos. Cada objeto sólo responde a ciertos mensajes (llamadas a sus métodos) y proporciona determinadas salidas. Los procesos que lleve a cabo para obtener esas están totalmente ocultos al resto de objetos. 

El concepto de encapsulamiento ya estaba presente en la programación modular, donde se perseguía maximizar la cohesión y minimizar el acoplamiento de los módulos. Esa idea es llevada a sus últimos términos por la programación orientada a objetos. 

### 2.7.3. Herencia

Es posible diseñar nuevas clases basándose en clases ya existentes. Esto se llama *herencia*. Cuando una clase hereda de otra, toma todos los atributos y todos los métodos de su clase “madre”, y puede añadir los suyos propios. A veces, algunos de los métodos o datos heredados no son útiles, por lo que pueden ser enmascarados, redefinidos o simplemente eliminados en la nueva clase. 

> [!question] Para saber más...
> El tema de la herancia lo veremos más adelante, en la </strong>, en el apartado de **[[1DAM_Programación/Unidad 04/8. Herencia\|herencia]]**.



### 2.7.4. Polimorfismo

Este "*palabro*" se refiere a la posibilidad de crear **varias versiones del mismo método**, de forma que se comporte de maneras diferentes dependiendo del estado del objeto o de los parámetros de entrada.

## 2.8. Ventajas de la OOP

La OOP se ha impuesto con fuerza en las dos últimas décadas, y no ha sido por casualidad. De hecho, proporciona varias ventajas importantes a la hora de desarrollar y mantener aplicaciones software, que se traducen, en definitiva, en un ahorro de tiempo y esfuerzo. Y, en consecuencia, de dinero. 

Estas ventajas son: 

* **Modularidad**: el código de un objeto puede modificarse, mantenerse o mejorarse sin que ello afecte al resto del sistema, siempre que respetemos su interfaz (así, los demás objetos del programa se seguirán comunicando con el objeto modificado sin que sepan que éste ha cambiado) 

* **Reutilización de código**: es muy sencillo utilizar clases y objetos de terceras partes. Solo tienen que publicar el interfaz de sus clases, y podemos empezar a usarlas en muy poco tiempo, sin preocuparnos de cómo funcionan por dentro, igual que el técnico de la lavadora sustituye una pieza electrónica por otra sin saber exactamente cómo están hechas. 

* **Facilidad de prueba y mantenimiento**: si tenemos un objeto que está dando problemas, es fácil aislar el elemento que falla y modificarlo sin que ello afecte al resto del código de la aplicación. 

* **Ocultación de información**: como cada objeto oculta los detalles de su implementación al resto, es virtualmente imposible que un mal funcionamiento en una parte del sistema pueda afectar a otras. 


# 3. Ejemplos de la API - Math y String

Teniendo claras estas definiciones, volvamos a recordar la clase **[`Math`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html)** que vimos en la [[1DAM_Programación/Unidades/Unidad 1 - Introducción a la programación con Java\|unidad 1]], en el apartado donde hablábamos de [[8. Tipos de datos simples#8.3.5. ¿Y las operaciones más complejas?\|operaciones más complejas]].

La clase `Math` **[[1DAM_Programación/Unidad 03/2. Definiciones formales#2.7.1 Abstracción\|abstrae]]** una serie de conceptos matemáticos y los **[[1DAM_Programación/Unidad 03/2. Definiciones formales#2.7.2 Encapsulamiento\|encapsula]]** para ofrecer desde un solo sitio una variedad de operaciones y propiedades relacionados.

Para usar los miembros encapsulados en ella, llamábamos a `Math` seguida de un punto y:

- El nombre de alguna función: `abs`, `round`, etc.
- O el nombre de un atributo o propiedad, como `Math.PI`.

Y si consultamos la documentación de la API de [`Math`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html) veremos que tiene varios métodos `abs`:

- `static double abs(double a)`
- `static float abs(float a)`
- `static int abs(int a)`

A esto se refería el **[[1DAM_Programación/Unidad 03/2. Definiciones formales#2.7.4 Polimorfismo\|polimorfismo]]** del apartado anterior, a varias **funciones que tienen el mismo nombre porque hacen los mismo pero con datos de distinto tipo**.

Esos miembros (métodos y propiedades) públicos son las [[1DAM_Programación/Unidad 03/2. Definiciones formales#2.6 Interfaz\|interfaces]] que `Math` nos ofrece para comunicarnos con ella.

> [!note] Nota 
> Esto se conoce también como **sobrecarga de un método**. Definir **varios métodos con el mismo nombre** pero **con distintos parámetros formales** (ya sea en número o en tipo).

Veamos otra clase de la API de Java que llevamos usando desde el principio y que puede ofrecernos muchas funcionalidades útiles para nuestro trabajo: las **cadenas de texto con la clase `String`**. 

> [!example] Material de apoyo 
> 
<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/1-dam-programacion/unidad-01/referencias/#java-clase-math" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



### JAVA: Clase Math

<iframe width="560" height="315" src="https://www.youtube.com/embed/4znSjME7tNU?si=caSIprEHAnD1mnms" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

> Aula en la nube. (2022x, octubre 19). _JAVA: Clase Math ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=4znSjME7tNU


</div></div>


> [!example] Material de apoyo 
> 
<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/1-dam-programacion/unidad-01/referencias/#java-funciones-matematicas" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



### JAVA: Funciones matemáticas

<iframe width="560" height="315" src="https://www.youtube.com/embed/jKs6kq6z1sI?si=neWhcLRZUrSt7gR1" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

> Aula en la nube. (2022y, octubre 19). _JAVA: Funciones matemáticas ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=jKs6kq6z1sI


---

<p><span>🏠 <strong>Unidad:</strong> <a data-tooltip-position="top" aria-label="1DAM_Programación/Unidades/Unidad 1 - Introducción a la programación con Java.md" data-href="1DAM_Programación/Unidades/Unidad 1 - Introducción a la programación con Java.md" href="1DAM_Programación/Unidades/Unidad 1 - Introducción a la programación con Java.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 1 - Introducción a la programación con Java</a></span></p>


</div></div>


## 3.1. La clase `String`

La clase `String` en Java representa una cadena de caracteres **inmutable** (no puede modificarse una vez creada).

Podemos guardar y manipular un texto guardándolo en un (objeto) `String`. Realmente se trata de una serie de caracteres, por lo que cada uno tiene ocupa una posición fija llamada **índice**, siendo 0 el del primer carácter.

### 3.1.1. Declaración y manipulación de cadenas

Hasta ahora hemos declarado una cadena de la siguiente forma:

```java
String saludo = "Hola, gente!";
```

> [!note] Nota
> Esta forma nos permite ahorrar memoria, ya que si encuentra otra cadena igual, no la creará en memoria. Usará la misma.

También podemos hacerlo así:
```java
String saludo = new String("Hola, gente!");

String despedida = "Adiós";
String despedida2 = new String(despedida);
```

> [!note] Nota
> En este caso, al ejecutar `new` **estamos forzando a que se cree otro objeto** de tipo `String` en memoria, aunque previamente haya otra cadena igual.


Y si queremos declarar un texto de varias línes podemos hacerlo usando las triples comillas `"""`:

```java
        String verso = """
                Ola ke ase,
                ola ke mira,
                ola ke kiere,
                ola mi vida.
                """;
```


### 3.1.2. Métodos más utilizados de `String`

Al igual que la clase `Math`, `String` **[[1DAM_Programación/Unidad 03/2. Definiciones formales#2.7.2 Encapsulamiento\|encapsula]]** un conjunto de **propiedades y métodos útiles** para ahorrarnos trabajo a la hora de tratar con textos. Ahí van unos cuantos:

* **`length()`**: muestra la longitud de la cadena, sin contar el nulo. Es decir, el número de caracteres útiles reales.
  
  ```java
  String saludo = "Hola, gente!";
  
  System.out.println("Longitud del saludo: " + saludo.length());
  // Longitud del saludo: 12
  ```

* **`concat(String s)`**: concatena (une) una cadena con otra.
  
  ```java
  String saludo = "Hola";
  String nombre = "Telmo";
  
  System.out.println(saludo.concat(", ").concat(nombre).concat("!"));
  // Hola, Telmo!
  ```

* **`compareTo(String s)`**: compara una cadena con otra. Devuelve un número entero con el número de diferencias alfabéticas encontradas. Si este número es 0, significa que las cadenas son idénticas.
  Esto lo estudiaremos con más detenimiento en unidades posteriores.


* **`equals()`**: este es un viejo conocido. Devolverá `true` si las cadenas contienen el mismo texto y `false` en caso contrario.
  
  ```java
  String nombre1 = "Anselmo";
  String nombre2 = "Telmo";
  
  if (nombre1.equals(nombre2)) {
      System.out.println(nombre1 + " y " + nombre2
              + " tienen el mismo nombre! :-)");
  }
  else {
      System.out.println(nombre1 + " y " + nombre2
              + " no tienen el mismo nombre :-(");
  }
  // Anselmo y Telmo no tienen el mismo nombre :-(
  ```

  > [!warning] Mucho cuidado...
  > Una duda habitual es: ¿y si comparo cadenas con ==?
  > Pues bien, el operador de comparación se limitará a mirar las **referencias** o **posiciones de memoria** de los objetos `String`. Es decir, devolverá `true` solo si ambas cadenas **son el mismo objeto**, **no si su contenido es el mismo**.

* **`trim()`**: elimina los **espacios en blanco** que pudieran existir al principio y al final.
  
  ```java
  String nombre1 = "Telmo          ";
  String nombre2 = "      Telmo";
  
  if (nombre1.equals(nombre2)) {
      System.out.println(nombre1 + " y " + nombre2
              + " tienen el mismo nombre! :-)");
  }
  else {
      System.out.println(nombre1 + " y " + nombre2
              + " no tienen el mismo nombre :-(");
  }
  // Telmo           y       Telmo no tienen el mismo nombre :-(
  
  // Quitamos los espacios en blanco en ambos nombres:
  nombre1 = nombre1.trim();
  nombre2 = nombre2.trim();
  
  if (nombre1.equals(nombre2)) {
      System.out.println(nombre1 + " y " + nombre2
              + " tienen el mismo nombre! :-)");
  }
  else {
      System.out.println(nombre1 + " y " + nombre2
              + " no tienen el mismo nombre :-(");
  }
  // Telmo y Telmo tienen el mismo nombre! :-)  
  
  ```

* **`toLowerCase()`**: convierte a minúscula.
  
  ```java
  String saludo = "OIGA USTED!";
  
  System.out.println(saludo);
  // OIGA USTED!
  
  System.out.println(saludo.toLowerCase());
  // oiga usted!
  
  System.out.println(saludo);
  // OIGA USTED!  
  ```

  No. No se me ha escapado el último saludo ni lo he repetido por despiste. Esto sirve para indicar qué significa eso de **inmutabilidad** de los textos `String`. Al ejecutar el método `.toLowerCase()` **no estoy almacenando el resultado en la variable `saludo`** porque es inmutable. Simplemente estoy devolviendo el valor de otra cadena `String` con el texto de la primera cadena en mayúsculas. Es decir, que mantengo la cadena original y genero otra nueva.

* **`toUpperCase()`**: convierte a mayúscula.
  
  El funcionamiento, salvo por las mayúsculas, es idéntico al anterior.

* **`replace(char c, char newc)`**: reemplaza cada ocurrencia del carácter `c` por `newc`.
  
  ```java
  String texto = "trasgo";
  
  System.out.println(texto);
  // trasgo
  
  System.out.println(texto.replace('g', 't'));
  // trasto
  
  System.out.println(texto);
  // trasgo, ¡recuerda que String es inmutable!
  ```

* **`substring(int i, int f)`**: devuelve un nuevo `String` que será la subcadena que comienza en el carácter número `i` y termina en el `f` de la cadena original.
  
  ```java
  String texto = "trasgo";
  
  System.out.println(texto);
  // trasgo
  
  System.out.println(texto.substring(0, 4));
  // tras
  
  System.out.println(texto);
  // trasgo, ¡recuerda que String es inmutable!
  ```

* **`charAt(int i)`**: devuelve un `String` con el carácter que ocupa la posición `i` de la cadena.
  
  ```java
  String texto = "trasgo";
  
  System.out.println(texto);
  // trasgo
  
  System.out.println(texto.charAt(4));
  // g
  
  System.out.println(texto);
  // trasgo, ¡recuerda que String es inmutable!
  ```

* **`indexOf(char c)`**: devuelve la posición en la que se encuentra el carácter c por primera vez. Si el carácter no está en la cadena, devuelve -1.
  
  ```java
  String texto = "carcasa";
  
  System.out.println(texto.indexOf('c'));
  // 0

  System.out.println(texto.indexOf('a'));
  // 1

  System.out.println(texto.indexOf('r'));
  // 2
  
  System.out.println(texto.indexOf('c'));
  // 0, ¡ojo! Devuelve la primera posición en la que encuentra 'c'
  ```

* **`valueOf(int i)`**: convierte el número `int` en un `String`. También funciona con `long`, `float` y `double`. Esto es solo una muestra. Hay muchos más métodos que encontrarás en: [Java SE 8 API Docs](http://docs.oracle.com/javase/8/docs/api/index.html)

Vemos a continuación un pequeño ejemplo de uso de algunos de estos métodos:

```java
String cad1 = "Hola";  
String cad2 = new String("Mundo");  
String cad3 = new String(cad2);  
System.out.println("¿Son cad2 y cad3 iguales?" + cad2.compareTo(cad3));  
System.out.println("Longitud de cad1 = " + cad1.length());  
System.out.println(cad1.concat(cad2));

String cad4 = new String(cad1.concat(", ").concat(cad2));  
System.out.println(cad4);  
System.out.println(cad4.toUpperCase());  
System.out.println(cad4.substring(0,3));
```

La salida por pantalla de este programa será la siguiente:  

```
¿Son cad2 y cad3 iguales? true   
Longitud de cad1 = 4   
HolaMundo   
Hola, Mundo   
HOLA, MUNDO   
Hola
```

> [!note] Nota 
> Existen otros métodos extremadamente útiles, como es el caso de `split()`, que veremos en la [[Unidad 5\|Unidad 5]], en el apartado de [[1DAM_Programación/Unidad 05/4. Cadenas o strings\|4. Cadenas o strings]].
> 
> En cualquier caso, **te animo a que te pases por la documentación de la API de la clase [`String`](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html)** y juegues con algunos de los métodos que allí se explican. Te va a resultar de gran interés.

---

<p><span>🏠 <strong>Unidad:</strong> <a data-tooltip-position="top" aria-label="1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos.md" data-href="1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos.md" href="1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 3 - POO. Los objetos</a></span></p>





## 4. Declaración de clases e instanciación de objetos en Java

---
dg-publish: true
unidad: "[[1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos\|Unidad 3 - POO. Los objetos]]"
descripcion: Veremos cómo declaramos una clase, con sus atributos y métodos, y luego instanciamos un objeto de dicha clase.
orden: 4
tags:
  - java
  - poo/clase
  - poo/objeto
  - poo/métodos
  - poo/atributos
---

```table-of-contents
```

---

Para crear un objeto y empezar a usarlo, es necesario que antes exista una clase (el molde, o la línea de producción de la factoría, en las metáforas que antes proponíamos). Dicho de otra forma, un objeto es una variable que almacena varios datos (y métodos) cuyo tipo de dato es la clase desde la que se instancia.

![ud02_01_clase_vs_objeto.png\|Clase vs. Objeto](/img/user/adjuntos/1DAM_Programacion/Unidad_02/ud02_01_clase_vs_objeto.png)

> [!warning] Diferencia entre clase y objeto
> Una clase es un diseño, un plano. Es el código fuente, es decir, una descripción de cómo serán los objetos (propiedades) y lo que podrán hacer (métodos).
> 
> Al pedir la creación de robots a partir de la clase se dice que estamos instanciando los objetos de tipo robot. Todos tienen los mismos atributos o propiedades, pero cada con sus propios valores (que definen su estado).

Veremos más detalles sobre cómo crear clases en temas posteriores, pero ahora aprenderemos a declarar clases simples. En Java, la forma más simple de declarar una clase es ésta:

```java
class MiClase {  
    private static int miAtributo1;  
    private float miAtributo2;

    public void mensaje() {  
        System.out.println("Esta es la ejecución del método mensaje()");  
    }

    public int resto(int a, b) {  
        int r;  
        r = a % b;  
        return r;  
    }  
} 
```

En este ejemplo, hemos declarado una clase llamada **`MiClase`** (que debemos guardar en un archivo llamado **`MiClase.java`**). La clase tiene dos **atributos o propiedades**, `miAtributo1` y `miAtributo2`, uno de tipo `int` y otro de tipo `float`. Ambos son `private`, lo que significa que **no son accesibles desde fuera** de la clase (típico de los atributos).

Además, uno de ellos es `static`, es decir, **solo se creará una vez aunque se definan varios objetos de esta clase**. 

Después, aparece la definición de dos **métodos**. Ambos son `public`, esto es, pueden ser usados por otros objetos externos a esta clase. El primero **no devuelve ningún resultado** (`void`), y el segundo devuelve un valor entero (`int`). Este último, además, tiene una variable local de tipo `int` llamada `r`. 

Recuerda que la clase solo es un molde, un patrón. Cuando escribimos una clase, lo hacemos en fase de codificación y sólo se trata de un bloque de código. Si queremos ver ese código en funcionamiento, hemos de crear o instanciar objetos de dicha clase. La forma de crear y usar un objeto usando este molde es esta:

```java
// Creamos o instanciamos un objeto a partir de esa clase:
MiClase miObjeto = new MiClase();
```

A partir de este momento existirá una variable en el programa llamada `miObjeto` en cuyo interior existirán todos los elementos de `MiClase`: los atributos y los métodos. Y **podemos crear todos los objetos que necesitemos** a partir de ese molde. Por ejemplo, para el objeto anterior:

```java
// Creamos o instanciamos un objeto a partir de esa clase:
MiClase miObjeto = new MiClase();

miObjeto.miAtributo1 = 7; // ❌ Error! miAtributo1 es private
miObjeto.miAtributo2 = 7; // ❌ Error! miAtributo2 es private

miObjeto.mensaje(); // puede ejecutar mensaje(), ya que es público

resto = miObjeto.resto(7, 3); // puede ejecutar resto(a,b), ya que es público
System.out.println("El resto es: " + resto);  
```


## 4.1 Un ejemplo más realista

Supongamos que estamos desarrollando una aplicación para administrar los datos personales y académicos del alumnado de un instituto. Dentro de la aplicación, hemos detectado que existe un tipo de dato llamado "persona" (también podría haber sido "alumno"), que tiene ciertas *características* (nombre, edad, sexo, etc) y con el que se pueden llevar a cabo ciertas *operaciones* (asignarle un nombre, preguntarle cuál es su edad, etc) 

Esas *características* son los **atributos**. Esas *operaciones* son los **métodos**. Así, el aspecto de la clase Persona sería, más o menos, este:

```java
class Persona {  
    private String nombre;  
    private String apellido;  
    private int edad;  
    private char sexo;

    public String getNombre() {  
        return nombre;  
    }

    public void setNombre(String txt) {  
        nombre = txt;  
    }

    public String getApellido() {  
        return apellido;  
    }

    public void setApellido(String txt) {  
        apellido = txt;  
    }

    public int getEdad() {  
        return edad;  
    }

    public void setEdad(int n) {  
        edad = n;  
    }

    public String getSexo() {  
        String s;  
        if (sexo == 'H' || sexo == 'h') s = "Hombre";  
        if (sexo == 'M' || sexo == 'm') s = "Mujer";  
        
        if ((sexo != 'H') && (sexo != 'h')
            && (sexo != 'M') && (sexo != 'm')) s = "Desconocido";

        return s;  
    }

    public void setSexo(char s) {  
        sexo = s;  
    }  
}
```

Observa como los atributos son privados, y hemos definido un método público para consultar y modificar cada uno de ellos. Los métodos saben cómo deben proceder con los atributos, y el programador que usa la clase no deben preocuparle esos detalles: una vez escrita y probada la clase, podemos olvidarnos de ella y usarla sin tener en cuenta su implementación. Solo tenemos que conocer cuáles son sus métodos públicos y para qué sirve cada uno. 

Este es un ejemplo de cómo podríamos usar esta clase para crear una persona llamada _Miguel Pérez_, de 23 años de edad y sexo masculino:

```java
class probarPersona {   
    public static void main(String[] args)   
    {   
        Persona a = new Persona();   
        a.setNombre("Miguel");   
        a.setApellido("Pérez");   
        a.setEdad(23);   
        a.setSexo('H');   
        // Ahora vamos a mostrar por pantalla la información del objeto
        // para asegurarnos que todo se ha almacenado correctamente
        System.out.println("Nombre: " + a.geNombre() + " " + a.getApellido());  
        System.out.println("Edad: " + a.getEdad());   
        System.out.println("Sexo: " + a.getSexo());   
    }  
}
```

Si compilamos y ejecutamos el programa `probarPersona`, la salida por pantalla debería ser esta:

```
Nombre: Miguel Pérez   
Edad: 23   
Sexo: Masculino 
```

Si te fijas, aunque en el interior del objeto el sexo se almacena como un carácter `H`, al recuperarlo con `getsexo()` se nos devuelve el string "Masculino". Ese es el comportamiento del objeto y, como usuarios del mismo, no nos importa cuál es el procedimiento interno por el que se ha obtenido ese resultado. Lo usamos y punto. 

> [!note] Por cierto...
> Si la clase `Persona` y la clase `probarPersona` están en el mismo paquete de nuestro proyecto, **NO es necesario hacer `import Persona`** ni nada parecido. El `import` se usa solo cuando se encuentran en paquetes distintos. 

### 4.1.1 Setters con sentido

Si obsevamos los `setters` de la clase `Persona` del apartado anterior, como es el caso de `setEdad(int n)`, no aportan mucho a nivel funcional. Es decir, ¿qué diferencia hay entre un `setter` así y poner la propiedad `edad` como `public`? **Ninguna**. Entonces, ¿lo de la encapsulación es un sinsentido? Para nada.

En general, cuando se consultan manuales o tutoriales de iniciación a la programación, se suele poner el `setter` estándar que introduce el valor que se pasa como argumento, tal cual. Pero hay que recordar que **los setters** son la puerta de entrada de datos a los objetos de nuestras clases y, por tanto, **deben establecer qué datos se permiten y cuáles no**.

En el ejemplo anterior, podríamos decir (porque los requisitos así nos lo exigen) que no admitimos **nombres y apellidos nulos**. Si así fuese, el nombre debería automáticamente ser un guión (`-`) y el apellido debería tener el valor por `Expósito` por defecto. Tampoco se deben admitir **edades negativas** (aunque es obvio), en cuyo caso debe ponerse por defecto, por ejemplo, un 0. De esta forma, los setters de la clase anterior quedarían así:

```java
class Persona {  
    private String nombre;  
    private String apellido;  
    private int edad;  
    private char sexo;

    public String getNombre() {  
        return nombre;  
    }

    /**
     * Si se introduce un valor null para el atributo nombre, se le asignará
     * automáticamente el texto "-".
     */
    public void setNombre(String txt) {  
        if (txt == null) nombre = "-";
        else nombre = txt;  
    }

    public String getApellido() {  
        return apellido;  
    }

    /**
     * Si se introduce un valor null para el atributo apellido, se asignará
     * automáticamente el texto "Expósito".
     */
    public void setApellido(String txt) {  
        apellido = (txt == null) ? "Expósito" : txt;  
    }

    public int getEdad() {  
        return edad;  
    }

    /**
     * Si se introduce un número negativo, se desprecia.
     * En su lugar se pone un 0 en el atributo edad.
     */
    public void setEdad(int n) {  
        edad = (n < 0) ? 0 : n;  
    }

    public String getSexo() {  
        String s;  
        if (sexo == 'H' || sexo == 'h') s = "Hombre";  
        if (sexo == 'M' || sexo == 'm') s = "Mujer";  
        
        if ((sexo != 'H') && (sexo != 'h')
            && (sexo != 'M') && (sexo != 'm')) s = "Desconocido";

        return s;  
    }

    public void setSexo(char s) {  
        sexo = s;  
    }  
}
```

---

<p><span>🏠 <strong>Unidad:</strong> <a data-tooltip-position="top" aria-label="1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos.md" data-href="1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos.md" href="1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 3 - POO. Los objetos</a></span></p>





## 5. Más sobre métodos

---
dg-publish: true
unidad: "[[1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos\|Unidad 3 - POO. Los objetos]]"
descripcion: Explicación más detallada de cómo declarar y usar métodos.
orden: 5
tags:
  - java
  - poo/clase
  - poo/objeto
  - poo/métodos
---

```table-of-contents
```

---

## 5.1 Paso de parámetros

Los métodos pueden recibir una serie de valores denominados parámetros. En la clase `Persona` del ejemplo anterior, el método `setEdad()`, por ejemplo, recibía un parámetro de tipo `int` llamado `n`. En ese parámetro se especifica cuál es la edad que debe almacenarse en el estado del objeto.

Por lo tanto, los parámetros son imprescindibles para que el objeto reciba los mensajes correctamente. Si no, ¿cómo le indicaríamos al objeto de tipo `Persona` cuál es la edad que tiene que almacenar?


Un método puede tener una lista larguísima de parámetros, o ninguno. Lo más habitual es que tenga entre cero y unos pocos.

> [!warning] Consejo
> Cuando declares métodos, procura que no tengan un número excesivo de parámetros. Eso los hace difíciles de usar y mantener y da pie a errores.

En la declaración del método **hay que indicar el tipo de cada parámetro**, por ejemplo así:

```java
public void setDatos(String nombre, String apellido, int edad, char sexo)
```

Este hipotético método `setDatos()` podría servir para asignar valor a todos los atributos de la clase `Persona` del ejemplo anterior. Por supuesto, cuando llamemos al método `setDatos()` para que se ejecute, será necesario pasarle cuatro datos que coincidan en tipo con los cuatro parámetros. Por ejemplo:

```java
p = new Persona();
p.setDatos("Miguel", "Pérez", 23, 'H');
```

## 5.2 Valores devueltos

Probablemente habrás observado que algunos métodos terminan con la sentencia return y otros nos. Los que sí lo hacen devuelven un resultado al código que los llamó. Ese resultado puede ser de cualquier tipo y también hay que indicarlo en la declaración del método.  

El método `setDatos()` anterior no devuelve nada, por lo que, en la declaración, se usa la palabra **`void`** (vacío). Pero el método `getEdad()`, por ejemplo, devuelve un valor entero (la edad de la persona), y por eso se indica `int` en la declaración:

```java
public int getEdad() {
    return edad;
}
```

## 5.3 Métodos y atributos estáticos

Algunos métodos, como algunos atributos, pueden estar precedidos de la palabra static.

Esto quiere decir que, para esa clase, se creará solo una instancia de ese método o atributo. No importa si se crean 800 objetos de tipo `Persona`: el atributo o el método static sólo se creará una vez, y todos los 800 objetos de esa clase lo compartirán.

Esto no solo permite ahorrar recursos en términos de memoria, sino que a veces resulta muy útil (si no, ¡no lo habrían inventado!). Por ejemplo, podemos usar un atributo static para llevar la cuenta del número de personas que se han creado:  

```java
class Persona {
    // Al crear la primera persona, esta variable se pondrá a 0
    private static int numPersonas = 0;

    static void nuevaPersona()
    {
        numPersonas++; **// Se incrementa cada vez que se crea una persona**
    }
    // El resto de la clase sería igual que antes
}
```

Si cada vez que creamos un objeto de la clase persona llamamos al método nuevaPersona(), el atributo numPersonas se incrementará en una unidad y contendrá el número total de objetos de esa clase que existen. En cambio, si no fuera un atributo static, cada objeto `Persona` tendría su propio atributo puesto a 0 en el momento de su creación, y la llamada a nuevaPersona() establecería su valor a 1.

## 5.4 Métodos constructores: una primera visión

En Java existen dos tipos de métodos especiales llamados **constructores** y **destructores** de objetos. No es obligatorio programarlos para cada clase, pero sí que aparecen con frecuencia, sobre todo los constructores (de los destructores hablaremos más adelante)  

El **constructor** es un método que *es invocado automáticamente al crear un objeto de la clase*. Su función suele ser inicializar el estado del objeto.

Por ejemplo, en la clase `Persona` de los ejemplos anteriores un posible constructor sería este:

```java
class Persona {
    Persona() {
        nombre = "";
        apellido = "";
        edad = 0;
        sexo = 'X';
        nuevaPersona();
    }
    // El resto de la clase quedaría igual
}
```

Observa varias cosas importantes:

* El nombre del constructor debe coincidir con el de la clase.
* El constructor se ha usado para inicializar con valores vacíos todos los atributos de la clase.
* También se ha aprovechado para invocar el método `nuevaPersona()`, que contabiliza todos los objetos `Persona` creados por el programa. Así, esa contabilización se automatiza, porque `nuevaPersona()` será invocado siempre que se cree un objeto `Persona`.
* El constructor no devuelve nada ni se indica su visibilidad (por definición, tiene que ser `public`)
* Los constructores pueden parametrizarse y, de hecho, sobrecargarse. Observa como en la siguiente variación de la clase `Persona` hay dos constructores, uno con parámetros y otro sin ellos:

```java
class Persona {
    Persona() {
        nombre = "";
        apellido = "";
        edad = 0;
        sexo = 'X';
        nuevaPersona();
    }

    Persona(String n, String a, int e, char s)
    {
        nombre = n;
        apellido = a;
        edad = e;
        sexo = s;
        nuevaPersona();
    }
    // El resto de la clase quedaría igual
}
```

Esto es una excelente idea, porque ahora podemos crear personas por dos vías con el mismo resultado:

```java
// Creamos una persona con el constructor sin parámetros
// y luego le asignamos los valores
Persona p1 = new Persona();
p1.setNombre("Miguel");
p1.setApellido("Pérez");
p1.setEdad(23);
p1.setSexo('H');

// Ahora creamos otra persona con el constructor parametrizado
Persona p2 = new Persona("Luisa", "Martínez", 21, 'M');
```

Presentamos por último la versión "todo junto" de la clase `Persona`, con todos los elementos que hemos ido añadiendo (método static y constructor polimórfico)

```java
// Versión definitiva de la clase Persona
class Persona {
    private String nombre;
    private String apellido;
    private int edad;
    private char sexo;

    // Al crear la primera persona esta variable se pondrá a 0
    private static int numPersonas = 0;

    // Constructor sin parámetros
    Persona() {
        nombre = "";
        apellido = "";
        edad = 0;
        sexo = 'X';
        nuevaPersona();
    }

    // Constructor con parámetros
    Persona(String n, String a, int e, char s) {
        nombre = n;
        apellido = a;
        edad = e;
        sexo = s;
        nuevaPersona();
    }

    // Método estático para contar en número de personas creadas
    static void nuevaPersona() {
        numPersonas++; // Se incrementa cada vez que se crea una persona
    }

    public String getNombre() {
        return nombre;
    }

    public void setNombre(String txt) {
        nombre = txt;
    }

    public String getApellido() {
        return apellido;
    }

    public void setApellido(String txt) {
        apellido = txt;
    }

    public int getEdad() {
        return edad;
    }

    public void setEdad(int n) {
        edad = n;
    }

    public String getSexo() {
        String s;
        if (sexo == 'H') s = "Hombre";
        if (sexo == 'M') s = "Mujer";
        if (sexo != 'H') && (sexo != 'M') s = "Desconocido"; 
        return s;
    }
 
    public void setSexo(char s) {
        sexo = s;
    }
}
```

---

<p><span>🏠 <strong>Unidad:</strong> <a data-tooltip-position="top" aria-label="1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos.md" data-href="1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos.md" href="1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 3 - POO. Los objetos</a></span></p>





## 6. Paquetes

---
dg-publish: true
unidad: "[[1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos\|Unidad 3 - POO. Los objetos]]"
descripcion: Nuestros programas pueden llegar a contener muchas clases. Para organizarlas podemos usar los paquetes.
orden: 6
tags:
  - java/paquetes
---

```table-of-contents
```

---

Un paquete o ***package*** es un conjunto de clases relacionadas entre sí empaquetadas en un archivo. En el JDK existen multitud de paquetes estándar que usarás continuamente, y, además, puedes encontrar paquetes de terceros para hacer todo tipo de cosas. Y tú mismo aprenderás a hacer tus propios paquetes. 

Por ejemplo, en el JDK existe un paquete llamado java.io, donde se agrupan todas las clases que permiten hacer la entrada/salida de datos (por consola y teclado, pero también escribir en archivos de disco, por ejemplo). 

El uso de paquetes permite agrupar las clases relacionadas en un solo lugar y, además, evitar posibles conflictos con nombres de clases y métodos que se repitan. Al estar en paquetes separados, ya no es posible la confusión. 

Para usar un paquete se utiliza la sentencia **`import`**. En este ejemplo puedes ver su uso:

```java
import java.lang.System;  // Importa la clase System del paquete java.lang
import java.lang.*;       // Importa todas las clases del paquete java.lang
```

Una vez importado un paquete, podemos usar los métodos del mismo sin indicar el nombre completo del paquete. Por ejemplo, en lugar de hacer esto:

```java
System.out.println("Hola, mundo");
```

Podemos hacer esto:

```java
import java.lang.System;  
println("Hola, mundo");
```

Para acceder correctamente a los paquetes, el compilador de Java necesita saber dónde están los archivos de la biblioteca de clases, es decir, tienes que configurar adecuadamente la variable de entorno `CLASSPATH`.

```bash
$ CLASSPATH = <ruta a la biblioteca de clases>:<ruta 2>:<ruta 3>:etc $ export CLASSPATH  
```
> (sustituye el carácter `:` por `;` si estás trabajando en un sistema Windows) 

Recuerda que, como vimos en el tema 1, también puedes compilar el programa con la opcion `-cp`, indicando a continuación el *classpath* de tu aplicación:

```bash
$ javac -cp /ruta/a/mis/clases nombre.java
```

![ud02_02_jerarquia_clases_java.png\|Jerarquía de clases en Java](/img/user/adjuntos/1DAM_Programacion/Unidad_02/ud02_02_jerarquia_clases_java.png)

---

<p><span>🏠 <strong>Unidad:</strong> <a data-tooltip-position="top" aria-label="1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos.md" data-href="1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos.md" href="1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 3 - POO. Los objetos</a></span></p>





## Referencias

---
dg-publish: true

unidad: "[[1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos\|Unidad 3 - POO. Los objetos]]"

descripcion: Para permitir que un usuario pueda comunicarse con nuestro programa podemos usar la entrada por teclado, con la que el usuario nos envía datos, y la salida por pantalla con la que el programa le dice los resultados.

orden: 8

---

```table-of-contents
```

---

# Material de apoyo

## String

### JAVA: Clase String

<iframe width="560" height="315" src="https://www.youtube.com/embed/443VORsWj2M?si=-hC-p4Nx0uUDkGcS" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

> Aula en la nube. (2022o, octubre 12). _JAVA: Clase String ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=443VORsWj2M

# Ejercicios

## String

### JAVA: Ejercicio String y funciones

<iframe width="560" height="315" src="https://www.youtube.com/embed/FNjyxclZmDQ?si=OuzAQSKikSf4bztH" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

> Aula en la nube. (2022p, octubre 13). _JAVA: Ejercicio String y funciones ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=FNjyxclZmDQ

---

<p><span>🏠 <strong>Unidad:</strong> <a data-tooltip-position="top" aria-label="1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos.md" data-href="1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos.md" href="1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 3 - POO. Los objetos</a></span></p>


