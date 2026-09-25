---
{"dg-publish":true,"permalink":"/1-dam-programacion/unidad-01-introduccion-a-la-programacion-con-java/","dg-note-properties":{"unidad":"[[1DAM_Programación/Unidades/Unidad 1 - Introducción a la programación con Java]]","modulo":"[[Módulos/Programación]]","libro":"[[Apuntes/Programación (1º DAM, 1º DAW)]]"}}
---


```table-of-contents
```

---


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/1-dam-programacion/unidades/unidad-1-introduccion-a-la-programacion-con-java/#datos-de-la-unidad" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## Datos de la unidad

La siguiente tabla muestra los contenidos básicos de la norma educativa que contempla esta unidad, al igual que el objetivo o RA que se quiere alcanzar y los criterios de evaluación que se seguirán para ello.

### Contenidos básicos

Identificación de los elementos de un programa informático:
- Estructura y bloques fundamentales.
- Variables.
- Tipos de datos.
- Literales.
- Constantes.
- Operadores y expresiones.
- Conversiones de tipo.
- Comentarios.

### RA asociado y criterios de evaluación

**RA 1. Reconoce la estructura de un programa informático, identificando y relacionando los elementos propios del lenguaje de programación utilizado.**

Criterios de evaluación para el RA:
a) Se han identificado los bloques que componen la estructura de un programa informático.
b) Se han creado proyectos de desarrollo de aplicaciones.
c) Se han utilizado entornos integrados de desarrollo.
d) Se han identificado los distintos tipos de variables y la utilidad específica de cada uno.
e) Se ha modificado el código de un programa para crear y utilizar variables.
f) Se han creado y utilizado constantes y literales.
g) Se han clasificado, reconocido y utilizado en expresiones los operadores del lenguaje.
h) Se ha comprobado el funcionamiento de las conversiones de tipos explícitas e implícitas.
i) Se han introducido comentarios en el código.

---


</div></div>


---

# 1. Introducción

Los ordenadores se han hecho para realizar tareas siguiendo un conjunto de instrucciones finitas. Esto es, un **programa**. Por su naturaleza (electrónica) manejan sólo dos posibles valores:
- **0** cuando no hay señal eléctrica.
- **1** en caso contrario.

Esta unidad de información, que puede tomar dos posibles valores, se conoce como **bit** (_**bi**nary digi**t**_). El ordenador realiza operaciones manejando bits. Esto lo hace sincronizando sus operaciones y los componentes que las realizan mediante un reloj interno que les envía pulsos. Por eso se dice que el ordenador es una **máquina síncrona**.

El ordenador realiza estas tareas cargándolas en la **memoria principal** a la que accede directamente la CPU, tomando las instrucciones a ejecutar y los datos con los que operar.

## 1.1. Programa

Estas tareas están definidas en los distintos **programas**. Un programa es un conjunto de instrucciones ordenadas y comprensibles para un ordenador y de datos que pueden usar esas instrucciones, de manera que cuando se ejecutan en el ordenador se obtiene un resultado.

Cada programa tiene como finalidad resolver un problema realizando alguna tarea concreta:

- Calcular las nóminas de una empresa.
- Navegar por Internet ([Brave](https://brave.com/es/), [Chrome](https://www.google.com/intl/es_es/chrome/), [Firefox](https://www.firefox.com/es-ES/), [Edge](https://www.microsoft.com/es-es/edge/), etc.).
- Enviar correos (Thunderbird, Outlook, etc.).

 En general, para que un programa realice su función, debe **comunicarse** de alguna manera **con el exterior** para recibir datos y devolver resultados.

Esos datos pueden ser de distinta naturaleza, pero en todos los casos **deben convertirse en datos binarios** para que el ordenador pueda manejarlos.

## 1.2. Algoritmo

Un algoritmo es un **conjunto ordenado y finito de operaciones** que permiten hallar la solución a un problema. La implementación de algoritmos genera programas que puede ejecutar el ordenador y pueden procesar datos para devolver la solución:

![ud01_prog_01_algoritmo.png\|500](/img/user/adjuntos/1DAM_Programacion/Unidad_01/ud01_prog_01_algoritmo.png)

### 1.2.1. Carecterísticas

Un algoritmo **no debe ser ambiguo** en sus resultados, ya que será la base del algoritmo posterior. Para que un algoritmo produzca un resultado en un **tiempo finito**, debe tener las siguientes características:

- **Preciso**: establece el orden en que se realizan los pasos de la operación.
- **Definido**: si se sigue dos o más veces (con los mismos datos), se obtiene siempre el mismo resultado.
- **Finito**: hay un número determinado y finito de pasos.
- **Independiente** del lenguaje de programación en el que se codificará posteriormente.

Veamos un ejemplo de algoritmo implementado en lenguaje natural:

- Inicio.
- Pedir un número N que represente la edad de una persona.
- Si N es **mayor o igual a 18**, la persona **ES MAYOR DE EDAD**.
- Si N es **menor que 18**, la persona **ES MENOR DE EDAD**.
- Fin del programa.

Si te fijas en el algoritmo podrás comprobar que cumple todas las características de un algoritmo.

> [!example] Material de apoyo 
> [[1DAM_Programación/Unidad 01/Referencias#Introducción a la programación y los algoritmos\|1DAM_Programación/Unidad 01/Referencias#Introducción a la programación y los algoritmos]]
> [[1DAM_Programación/Unidad 01/Referencias#Representación de algoritmos\|1DAM_Programación/Unidad 01/Referencias#Representación de algoritmos]]


# 2. Codificación de la información

Como se indicaba al principio de este tema, el ordenador sólo maneja datos en **binario**.

Tanto el binario (usado por los ordenadores) como el decimal (usado por los humanos) son **sistemas posicionales de numeración**.

Estos sistemas se componen de:

- Un conjunto de **símbolos** (números en este caso). El número de símbolos del sistema es su **base**.
- Una serie de **reglas** para combinarlos.
- En esas combinaciones de números, la **posición** de cada uno repercute en su valor.

**Sistemas posicionales**<br>En el sistema decimal (base 10), que usa los símbolos {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}, si tenemos los dígitos 1 y 3 podemos crear los números 31 y 13. Así se puede entender que la posición de cada símbolo define el valor del número.

Veamos a continuación los sistemas de numeración que suelen utilizarse en informática.  

## 2.1. Sistema binario

Usa un conjunto de dos símbolos (base 2): {0, 1}

A priori parece un sistema con pocas opciones, pero sólo con esos dos dígitos se pueden representar los mismos números que hacemos los humanos con el sistema decimal.

Veámoslo con el siguiente ejemplo:

| Decimal | Binario |
| ---- | ---- |
| 0 | 0 |
| 1 | 1 |
| 2 | 10 |
| 3 | 11 |
| 4 | 100 |
| 5 | 101 |
| 6 | 110 |
| 7 | 111 |
| 8 | 1000 |
| 9 | 1001 |
| 10 | 1010 |
| 11 | 1011 |
| 12 | 1100 |
| ... | ... |
| 19 | 10011 |
| 20 | 10100 |
| 21 | 10101 |

Si observas la columna **Decimal** verás que para contar empezamos recorriendo cada símbolo desde el primero (0) hasta el último (9). Para continuar, se añade el símbolo 1 al principio y se vuelve a hacer el mismo recorrido (1**0**, 1**1**, 1**2**...) y así sucesivamente. Al cubrir todos los números posibles de dos dígitos y llegar al último (99), volvemos a añadir un 1 al principio y comenzamos de nuevo el ciclo.

El sismeta binario hace lo mismo aunque usando sólo dos símbolos (0 y 1). Pero se puede ver que un número entero como el **20** para nosotros puede interpretarlo un ordenador al convertirlo en **10100**.

### De binario a decimal

Para convertir un número binario en su equivalente decimal debemos tener en cuenta lo siguiente:

1. Cada dígito ocupa una posición en el número, empezando por la posición 0 de la derecha e incrementándola dígito a dígito hacia la izquierda.
2. Se multiplica cada dígito binario por 2 (la base o número de símbolos del sistema binario) elevado a la posición del dígito y, por último, se suman todos ellos.
3. El resultado es el número decimal equivalente al número binario inicial.

Observa estos pasos en el siguiente ejemplo:

![ud01_prog_02_binario.png\|650](/img/user/adjuntos/1DAM_Programacion/Unidad_01/ud01_prog_02_binario.png)
> Conversión de número binario a decimal

Al sumar todos ellos:

`16 + 0 + 0 + 2 + 1 = 19`

Así, el número binario **10011** es equivalente a **19** en decimal.

### De decimal a binario

Si queremos comprobar cómo maneja el ordenador los números que usamos los humanos podemos convertir un número decimal en binario siguiente los pasos:

1. Dividir el número decimal y sus sucesivos cocientes entre 2 hasta llegar al último cocinete válido.
2. Comprobarás que tantos los restos de las sucesivas divisiones como el último cociente son binarios (sólo hay ceros y unos). Para componer el número binario equivalente se toma el cociente y los restos en ese orden y se escriben en el orden opuesto para componer el binario.

![ud01_prog_03_binario.png\|300](/img/user/adjuntos/1DAM_Programacion/Unidad_01/ud01_prog_03_binario.png)
> Conversión de número decimal a binario

De esa forma podemos comprobar que **19** es equivalente a **10011**.

> [!example]  Ejercicio propuesto
> Convierte a decimal los siguientes binarios: 1001101, 11100 y 1001001.

## 2.2. Sistemas intermedios

Si se observan los ejemplos anteriores, **la base influye en la cantidad de dígitos necesarios para representar un número**.

Así, si el número 19 sólo requiere 2 dígitos (el 1 y el 9) para representar dicho número, el sistema binario necesita 5 dígitos (10011). Para números más grandes, el equivalente binario podría resultar inmanejable para las personas ya que la cantidad de dígitos sería demasiado grande.

Por eso se idearon sistemas de numeración intermedios que permiten la representación del mismo dato con un número diferente de dígitos. Estos sistemas eran el **octal** y el **hexadecimal** (que veremos en el siguiente apartado).

### 2.2.1. Octal

El octal usa el conjunto de símbolos {0, 1, 2, 3, 4, 5, 6, 7}. Es decir, es de **base 8**. Por eso se conoce como octal: **8 símbolos en total**.

La conversión de octal a decimal y viceversa se consigue de la misma forma que en binario, pero usando los 8 símbolos y el 8 como base para las potencias y las divisiones.

> [!example] Ejercicio propuesto
> Convierte a octal los siguientes decimales: 42, 27 y 111.

> [!example] Ejercicio propuesto
> Convierte a decimal los siguientes octales: 42, 27 y 111.

### 2.2.2. Hexadecimal (hex)

El hexadecimal usa 16 símbolos (base 16): {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F}

Se usan letras ya que en nuestro sistema decimal no existen más símbolos, pero se puede intuir que:

- A = 10
- B = 11
- C = 12
- D = 13
- E = 14
- F = 15

Para ver todos los sistemas de un vistazo, aquí tienes una tabla de equivalencias de distintos números en todos los sistemas de numeración explicados:

| Decimal | Binario | Octal | Hex |
| ---- | ---- | ---- | ---- |
| 0 | 0000 | 00 | 0 |
| 1 | 0001 | 01 | 1 |
| 2 | 0010 | 02 | 2 |
| 3 | 0011 | 03 | 3 |
| 4 | 0100 | 04 | 4 |
| 5 | 0101 | 05 | 5 |
| 6 | 0110 | 06 | 6 |
| 7 | 0111 | 07 | 7 |
| 8 | 1000 | 10 | 8 |
| 9 | 1001 | 11 | 9 |
| 10 | 1010 | 12 | A |
| 11 | 1011 | 13 | B |
| 12 | 1100 | 14 | C |
| 13 | 1101 | 15 | D |
| 14 | 1110 | 16 | E |
| 15 | 1111 | 17 | F |

> [!example] Ejercicio propuesto
> Convierte a hex los siguientes decimales: 42, 27 y 111.

> [!example] Ejercicio propuesto
> Convierte a decimal los siguientes hex: 4A, FF y 11.

## 2.3. Código ASCII

Efectivamente, también **las letras pueden representarse en el sistema binario**.

Para ello se creó el **[código ASCII](https://es.wikipedia.org/wiki/ASCII)**, que se basa en una tabla de equivalencia donde cada letra usa 8 bits para representarla.

Así, la letra **`A`** se representa con el binario **`01000001`** (65 en decimal) mientras que la **`a`** equivale a **`01100001`**.

La palabra `Hola`, por ejemplo, se traduciría al siguiente código binario usando la conversión de ASCII:

`01001000 01101111 01101100 01100001`

Donde:

* `H` = `01001000`
* `o` = `01101111`
* `l` = `01101100`
* `a` = `01100001`

> [!example] Actividad propuesta 🏗️
> Usando la tabla de código ASCII del enlace anterior, escribe tu nombre (sin tildes) en código binario.

> [!example] Actividad propuesta 🏗️
> ¿Cuál es el mensaje oculto en este código binario?
> `01001101 01101111 01101100 01100001 00100001`

# 3. Resolución de problemas

La programación como tal requiere de conocimientos específicos en algún lenguaje de programación, pero eso no es lo esencial.

> [!note] Nota
> Un **programador** es aquella persona **capaz de encontrar soluciones** a determinados problemas mediante el diseño e implementación de programas.

## 3.1 Ingeniería del software

El término de **ingeniería** aparece en el campo de la informática tras la **crisis del software**[^1]. Hasta entonces se programaba sin seguir metodologías, reglas, paradigmas o normas básicas. Cada cual con algunos conocimientos del funcionamiento de un ordenador podía escribir programas.

Pero el hardware evolucionaba muy deprisa y los programas debían adaptarse. Y sin reglas a seguir... cada cual *hacía de su capa un sayo* y los programas se hacían más grandes, más difíciles de entender y, por tanto, de reparar y/o mantener.

Esto provocó la crisis y la reacción no se hizo esperar. Surge así la **ingeniería del software** para establecer modelos y paradigmas de programación que permitan desarrollar programas siguiendo unas normas de organización.

## 3.2 Ciclo de vida clásico

Como en cualquier otra ingeniería, la del software comenzó por descomponer el desarrollo de un programa en fases, lo que se conoce como el **ciclo de vida del software**.

> [!note] Nota
> El ciclo de vida es un proceso extenso y que requiere el trabajo en equipo. Por eso durante el curso nos vamos a centrar en la **especificación de clases** y la **codificación**. El resto se estudian en otros módulos.

Existen muchos modelos de ciclos de vida y en su mayoría tienen en común las siguientes fases:

### Análisis  
El **análisis** sirve para responder a la pregunta *¿**QUÉ** problema hay que resolver?*

Se trata de comprender cuál es el problema y los factores que le rodean e influyen en él.

Por ejemplo, si nos encargan programar un carrito de la compra para una tienda *on-line* ¿quién puede añadir productos al carrito? ¿Existe un límite de productos? ¿Qué ocurre con los productos del carrito si el usuario sale de la aplicación sin realizar la compra?

Es fundamental establecer qué información va a manejar el programa y cómo lo va a hacer de la forma más detallada posible. Por eso y para evitar conflictos con los clientes, todo esto se plasma en un **documento de requisitos**.

### Diseño de soluciones

El **diseño** responde a la pregunta *¿**CÓMO** se resuelve el problema?*

En esta fase se realiza un diseño de la solución al problema planteado en la fase anterior. Un modelo de diseño muy habitual es el de **divide y vencerás** o **top-down** que consiste en dividir el problema principal en subproblemas más sencillos.

![ud01_prog_04_top_down.png](/img/user/adjuntos/1DAM_Programacion/Unidad_01/ud01_prog_04_top_down.png)
> Top-down o "Divide y venderás"

Es en esta fase, una vez definido el CÓMO, donde se decide el **lenguaje de programación** que se va a usar para desarrollar el software ya que se puede sopesar cuál es el que mejor se adapta a las necesidades del proyecto.

### Especificación de módulos/clases y codificación
El *top-down* permite organizar mejor el trabajo ya que se puede implementar de forma independiente cada una de las soluciones a los subproblemas planteados en la fase de diseño.

En nuestro caso, como veremos más adelante, se hará mediante la codificación de **clases** ya que usaremos el lenguaje Java orientado a objetos. Aunque dependiendo del paradigma o estilo de programación que se use puede ser, por ejemplo, un **módulo**[^2] en JavaScript, etc.

En el caso de la <abbr title="Programación Orientada a Objetos">POO</abbr> (<abbr title="Object-Oriented Programming">OOP</abbr> en inglés) suelen usarse diagramas **[UML](https://es.wikipedia.org/wiki/Lenguaje_unificado_de_modelado)** para indicar qué clases se han de codificar, cómo se van a comportar y cómo se relacionan entre si.

Estos diagramas se estudian en el módulo de **Entornos de desarrollo**, aunque los usaremos también en nuestras clases.

En esta fase se materializan en **código fuente** las clases planteadas. Es decir, se var a **codificar** o, como se dice en el mundillo, se va a **picar código**.

### Pruebas
Es imprescindible comprobar que el código fuente funciona correctamente. Por eso esta fase es esencial.

Los errores básicos son de **sintaxis** o escritura de código. Son aquellos que ocurren cuando se escribe mal una instrucción y, por tanto, no se reconoce. Estos errores los detecta y subsana el propio programador mientras programa.

Cada programador va realizando las pruebas oportunas conforme va codificando. Así detecta errores de **sintaxis**, que ocurren cuando se escribe mal una instrucción y, por tanto, no se reconoce como expresión válida.

Pero esto **no es suficiente** ya que los programadores tienen una visión sesgada del funcionamiento de sus programas. Es decir, en muchas ocasiones no se ponen en la piel del usuario que utilizará ese programa. Por eso es conveniente que otras personas (*testers*) realicen baterías de pruebas guiándose en el análisis de requisitos y en diseño propuesto.

La experiencia y el tiempo han dado pie al despliegue de una ciencia alrededor de las pruebas. Así, podemos encontrar distintos tipos de pruebas[^3]:

- Tests unitarios.
- Pruebas de integración.
- Pruebas funcionales.
- Pruebas de aceptación.
- ...

### Mantenimiento

Una vez en producción (el programa ya está siendo usado por los usuarios) pueden surgir errores no contemplados en la fase de pruebas, o la necesidad de replantear algunas funcionalidades en base a las necesidades del usuario o las limitaciones del sistema, etc.

Es entonces cuando se hacen labores de **mantenimiento**, que pueden ser de distintos tipos:

- **Correctivo**, para enmendar errores que no se hubieran detectado en la fase de pruebas).
- **Perfectivo**, para mejorar el rendimiento o añadir más funciones.
- **Adaptativo**, para adaptar el programa a otros entornos.

> [!note] Nota
> El ciclo de vida es un proceso extenso y que requiere el trabajo en equipo. Por eso durante el curso nos vamos a centrar en la **especificación de clases** y la **codificación**. El resto se estudian en otros módulos.

## 3.3 El papel del programador

Dentro del proceso del desarrollo de software, el programador tiene una tarea clara y precisa: codificar programas en base a las especificaciones que se le asignan.

Generalmente las fases de análisis y diseño suelen ser tarea para otros perfiles, aunque en la vida real el programador "*sirve para un roto y un descosido*". Es decir, que acaba haciendo de todo un poco.
  

[^1]: Wikipedia contributors. (s/f). **_Crisis del software_**. Wikipedia, The Free Encyclopedia. <https://es.wikipedia.org/w/index.php?title=Crisis_del_software&oldid=164378777>

[^2]: Módulos JavaScript. (s/f). **_MDN Web Docs_**. Recuperado el 22 de agosto de 2025, de <https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Modules>{:target="_blank"}

[^3]: Atlassian. (s/f). **_Los distintos tipos de pruebas en software_**. Atlassian. Recuperado el 26 de agosto de 2025, de <https://www.atlassian.com/es/continuous-delivery/software-testing/types-of-software-testing>



# 4. Estilos y Paradigmas

Recordemos que un programa de ordenador es un conjunto de instrucciones que el ordenador puede entender y que ejecuta en un determinado orden.

Generalmente, el ordenador ejecuta ese código de la misma forma que nosotros leemos un libro. Es decir, el orden de ejecución de las instrucciones es el mismo en el que están escritas.

Pero en sus primeros pasos, los programas no eran tan *ordenados*.

La evolución de los lenguajes de programación desde

Si es cierto que los lenguajes permitían escribir código más legible, pero cada programador tenía su propio estilo y el código era difícil de mantener (incluso para el propio autor). La falta de unos estándares de programación, los errores de planificación y los largos periodos de desarrollo llevaron a desconfiar del desarrollo de software y de los ordenadores como elementos tecnológicos que ayudas en al ser humano.

Desde los primeros pasos en la programación, eso no siempre era así (como veremos en unidades posteriores). Existen bucles, que repiten varias veces un mismo bloque de instrucciones, o instrucciones que (según unas determinadas condiciones) evitan (condicionales) su ejecución o saltan (instrucción GOTO) a otra parte del código.

Esto suena a código caótico... ¡Y lo es! Y más aún cuando el programa crece, el número de líneas de código es ingente y resulta difícil de leer, arreglar y mantener[^1]. Esta fue la causa de la **crisis del software de los años 70**[^2] que mencionamos anteriormente.

[Edsger W. Dijkstra](https://es.wikipedia.org/wiki/Edsger_Dijkstra) lo advirtió en su carta "*GoTo Statement Considered Harmful*"[^3] que publicó en 1968 en la revista "*Communications of the ACM*".

Veamos los tipos de programación que surgieron a partir de esta crisis.

> [!note] Nota
> Estos paradigmas o estilos de programación no son excluyentes. Esto es, un paradigma puede usar los principios de otro/s.

## 4.1. Evolución histórica de los lenguajes de programación

Desde los gloriosos tiempos del **[ENIAC](https://es.wikipedia.org/wiki/ENIAC)** y el **[UNIVAC](https://es.wikipedia.org/wiki/UNIVAC)**, que se programaban accionando interruptores y palancas, han cambiado mucho las cosas.

Los estilos de programación han evolucionado mediante un proceso continuo de investigación, ensayo y error, y podemos distinguir estos periodos:

- El periodo de programación desestructurada de las primeras décadas de la informática (más o menos, entre 1950 y 1970).
- El periodo de la programación estructurada clásica (entre 1970 y 1990)
- El periodo de la programación modular, que coexiste con la anterior (entre 1970 y 1990)
- El periodo de la programación orientada a objetos (desde la década de 1990 hasta la actualidad)
- El periodo de la programación dirigida por eventos, que coexiste con el anterior (desde 2000, aproximadamente, hasta la actualidad)

### 4.1.1. Programación desestructurada

Un programa de ordenador, como hemos dicho, es un conjunto de instrucciones que el ordenador puede entender y que ejecuta en un determinado orden. Generalmente, el orden de ejecución de las instrucciones es el mismo que el orden en el que el programador las escribió, pero en ocasiones, como veremos, es imprescindible repetir un conjunto de instrucciones varias veces (a esto se le llama técnicamente bucle), o saltar hacia delante o hacia atrás en la lista de instrucciones.

La programación desestructurada clásica utiliza indistintamente bucles y saltos entremezclados hasta conseguir el correcto funcionamiento del programa. Debido a ésto, este tipo de programación es farragosa, confusa, e implica una alta probabilidad de errores. Estos defectos se hacen más patentes cuanto más grande es el programa, llegando a un punto en que el código se hace inmanejable (es lo que se suele denominar, muy gráficamente, código spaghetti)

Este tipo de programación cayó en desuso tras la crisis del software de los años 70. Hoy se considera una mala práctica y debe ser evitada siempre.

Los lenguajes de programación más antiguos pertenecen a esta época: [Fortran](https://es.wikipedia.org/wiki/Fortran), [Cobol](https://es.wikipedia.org/wiki/COBOL), [Simula](https://es.wikipedia.org/wiki/Simula), [Basic](https://es.wikipedia.org/wiki/BASIC)... Muchos de ellos han evolucionado y cambiado con el tiempo para adaptarse a los nuevos paradigmas, y por eso aún siguen usándose, aunque de forma mucho más marginal que en sus buenos tiempos.

### 4.1.2. Programación estructurada

El mismo Edsger W. Dijkstra, en los años 70 del siglo XX, propuso un paradigma que ofrecía los mecanismos para crear un código más organizado eliminando las limitaciones de la programación convencional: la **programación estructurada**.

Se base en tres tipos de **estructuras básicas de control** que optimizan los recursos lógicos y físicos del ordenador: **secuencial**, **alternativa** e **iterativa**.  

Dichas estructuras (de ahí el nombre de programación **estructurada**) y las reglas de uso que implican se han preservado hasta nuestros días y las estudiaremos y usaremos en las siguientes unidades.

A este tipo de lenguajes también se les llama a veces imperativos o de tercera generación.

Los lenguajes estructurados más populares y significativos son [C](https://es.wikipedia.org/wiki/C_(lenguaje_de_programaci%C3%B3n)), [Pascal](https://es.wikipedia.org/wiki/Pascal_(lenguaje_de_programaci%C3%B3n)) o [Modula-2](https://es.wikipedia.org/wiki/Modula-2).

> [!note] Nota
> Los lenguajes más antiguos, como **Fortran** o **Cobol**, evolucionaron para adaptarse a este paradigma, aunque seguían permitiendo hacer programación desestructurada si el programador así lo deseaba.

### 4.1.3. Programación modular

Consiste en dividir un programa complejo en varios subprogramas más sencillos que pueden interactuar entre sí. Cada subprograma es un **módulo** y son independientes del resto. Es decir, un módulo no debe interferir en otro/s módulo/s pero sí deben cooperar en la resolución del problema principal.

> [!note] Nota
> Esta técnica de programación no es excluyente de la anterior, sino que se pueden utilizar conjuntamente. Es decir, un programa **puede ser a la vez modular y estructurado**. Y, de hecho, suele serlo.

Un módulo es un subprograma, por lo que hace el papel de un programa. Es decir, puede tener: una **sección de declaraciones** (variables, constantes, funciones, procedimientos, etc…), unos **datos de entrada** sobre los que realizar operaciones y **datos de salida**, que pueden usarse como entrada de otro módulo o bien contribuir directamente a la salida final del programa. Esto permite que el módulo sea **totalmente independiente** del programa principal.

Cada módulo del programa debe tener claramente definidos su **finalidad**, los **límites** de su funcionalidad y una **interfaz** lo más sencilla posible que permita interactuar con él. De esta forma se consigue su **independencia funcional**, esto es, que no dependa de otros módulos para funcionar. Esta independencia se mide con dos parámetros:

- **Cohesión**: tiene que ver con que cada módulo se refiera a un único proceso o entidad. La cohesión es el grado de relación entre los elementos del módulo, de forma que estén bien definidos y alineados con la finalidad o tarea que debe realizar. La **cohesión es alta** cuando cada módulo realiza una única tarea trabajando sobre una sola estructura de datos.
- **Acoplamiento**: indica el **nivel de dependencia** entre los módulos, es decir, hasta qué punto un módulo necesita de otros para poder funcionar.

Dos módulos están **desacoplados** cuando no se necesitan el uno al otro para hacer su trabajo. Pero esta situación es casi inalcanzable en casi cualquier proyecto de desarrollo. Por tanto, lo deseable es que un módulo tenga un acoplamiento bajo, ya que así se evita el **efecto onda** o **propagación**, donde un fallo en un módulo se propagaría al resto de módulos acoplados.

> [!info]
> La **cohesión** y el **acoplamiento** son parámetros usados en programación en general, no en la programación modular en particular.

### 4.1.4. Programación orientada a objetos

La <abbr title="Programación Orientada a Objetos">POO</abbr> es una evolución de la modular, cambiando por completo las estructuras lógicas. Es el paradigma más extendido en la actualidad (prácticamente no hay lenguaje de programación que no sea orientado a objetos).

La principal diferencia con la programación estructurada es que la <abbr title="Programación Orientada a Objetos">POO</abbr> considera que tanto los datos como las operaciones sobre ellos están **totalmente interconectados**, por lo que deben encapsularse en un objeto:

![ud01_prog_05_poo.png](/img/user/adjuntos/1DAM_Programacion/Unidad_01/ud01_prog_05_poo.png)
> Comparativa entre prog. estructurada y POO sobre la relación de los datos y las operaciones que se realizan con ellos

En el ejemplo anterior, tanto los datos de una persona (nombre y edad) y las funciones que se pueden realizar sobre dichos datos (comprobar mayoría de edad) **se encapsulan en un objeto** Persona.

Todos estos conceptos se entenderá en unidades posteriores.

La programación orientada a objetos <abbr title="Object-Oriented Programming">OOP</abbr> es una evolución de las anteriores. Básicamente, se trata de programación estructurada y modular en la que las instrucciones y los datos se encierran en entidades llamadas clases, de las que luego se crean los objetos. Tanquilidad: por ahora no te preocupes de esos detalles. Pronto llegaremos.

En la actualidad, todos los lenguajes imperativos modernos permiten algún tipo de orientación a objetos, y es el estilo de programación predominante en la industria desde finales del siglo XX. Incluso los lenguajes más clásicos (como C), han evolucionado para permitir la orientación a objetos (C++).

Casi todos los lenguajes de los que hayas oído hablar recientemente son orientados a objetos en mayor o menor medida: C++, C#, Java, Python, Ruby, PHP (en sus primeras versiones, no lo era), Javascript (no confundir con Java), Visual Basic, Dephi, Rust, Go y un largo etcétera.

Java, el lenguaje que aprenderemos a usar en este curso, está orientado a objetos y fue creado y diseñado con ese propósito. En Java no se puede desarrollar solo programación estructurada y modular: por narices hay que desarrollar los programas usando la orientación a objetos.

### 4.1.5. Otros paradigmas

Tras la POO surgieron otros paradigmas[^4]: programación declarativa, <abbr title="Aspect-oriented programming">AOP</abbr>, programación funcional, programación lógica, etc.

Por ejemplo, la **programación funcional** es uno de los paradigmas que más se ha asentado (tras la POO) en los distintos lenguajes de programación. En la programación funcional algunas sentencias o partes del código se tratan como si fueran **funciones matemáticas** (si, esas `f(x)` que habrás estudiado en tus años mozos)). Veremos algo en unidades posteriores.

No te preocupes. Aunque nos vamos a centrar en POO vamos a sentar las bases para que puedas abordar otros paradigmas por tu cuenta con facilidad.

[^1]: Esto se conoce como **código _spaghetti_**.

[^2]: Wikipedia contributors. (s/f). **_Crisis del software_**. Wikipedia, The Free Encyclopedia. <https://es.wikipedia.org/w/index.php?title=Crisis_del_software&oldid=164378777>

[^3]: Wikipedia contributors. (2025, julio 28). **_Considered harmful_**. Wikipedia, The Free Encyclopedia. <https://en.wikipedia.org/w/index.php?title=Considered_harmful&oldid=1303063020>

[^4]: Bustos, J. L. (2022, August 18). **_Paradigmas de programación: Guía completa 2025_**. KeepCoding Bootcamps. <https://keepcoding.io/blog/paradigmas-de-programacion/>


# 5. Los lenguajes de programación

Podemos definir un lenguaje de programación como **un conjunto de símbolos que se combinan de acuerdo con una sintaxis bien definida para posibilitar la transmisión de instrucciones a la CPU**[^1].

## 5.1. Lenguajes de alto y bajo nivel

Dicho de otro modo: el lenguaje de programación es el código en el que podemos transmitir al ordenador las órdenes de un programa.

Lenguajes de programación hay muchos, cada uno con sus ventajas e inconvenientes. Conviene, por tanto, clasificarlos en categorías. Nosotros haremos dos clasificaciones:

- La primera, atendiendo al **nivel de abstracción** del lenguaje, distinguirá entre lenguajes de bajo nivel y de alto nivel.
- La segunda, según el **proceso de traducción** a código máquina, distinguirá entre lenguajes interpretados, compilados y ensamblados.

### 5.1.1. Lenguajes de alto nivel

El ordenador, como es sabido, solo puede manejar ceros y unos, es decir, código o **lenguaje binario**. Los seres humanos, por el contrario, utilizamos un lenguaje mucho más complejo, con montones de símbolos y reglas sintácticas y semánticas, que denominaremos **lenguaje natural**.

Entre estos dos extremos (lenguaje binario y lenguaje natural) se encuentran los lenguajes de programación. Tienen cierto parecido con el lenguaje natural, pero son mucho más reducidos y estrictos en su sintaxis y semántica, para acercarse a las limitaciones del lenguaje binario.

Hay lenguajes de programación muy próximos al lenguaje binario: a éstos los llamamos **lenguajes de bajo nivel** de abstracción. Y los hay más próximos al lenguaje natural: son los **lenguajes de alto nivel** de abstracción.

Podemos definir un lenguaje de programación como un **conjunto de símbolos que se combinan utilizando una sintaxis estricta para transmitir instrucciones a un ordenador**.

Dicho de otro modo: el lenguaje de programación es el código con el que podemos pasarle al ordenador las órdenes de un programa. Hasta ahora hemos usado el lenguaje natural para escribir esas órdenes. Ahora llega el momento de traducir ese lenguaje natural en un código real, el lenguaje de programación, comprensible por la máquina.

Lenguajes de programación hay muchos, cada uno con sus ventajas e inconvenientes. Conviene, por tanto, clasificarlos en categorías. Encontrarás habitualmente estas tres clasificaciones:

- La primera, según la época del lenguaje y el paradigma (o estilo) de programación que permite.
- La segunda, atendiendo al nivel de abstracción del lenguaje, distinguirá entre lenguajes de bajo nivel y de alto nivel.
- La tercera, según el proceso de traducción a código máquina, distinguirá entre lenguajes interpretados, compilados y ensamblados.

Hay otras formas de clasificar los lenguajes, desde luego, pero por ahora nos servirá para orientarnos.

### 5.1.2. Lenguajes de bajo nivel

Son los lenguajes más cercanos a la máquina. Los programas directamente escritos en código binario se dice que están en **lenguaje máquina** que, por lo tanto, *es el lenguaje de más bajo nivel que existe*.

Las instrucciones del lenguaje máquina realizan **tareas muy sencillas**, como, por ejemplo, sumar dos números, detectar qué tecla se ha pulsado en el teclado o escribir algo en la pantalla del ordenador. Cuando se **combinan adecuadamente muchas de estas instrucciones** sencillas se obtiene un **programa de ordenador** que puede realizar tareas muy complejas.

A pesar de la simplicidad de las instrucciones del lenguaje máquina, la forma de escribirlas es muy complicada, ya que hay que hacerlo en binario. En los primeros años de la informática los ordenadores se programaban directamente en lenguaje máquina, lo cual convertía la tarea de programar en una verdadera pesadilla. Por ejemplo, una instrucción para sumar dos números en lenguaje máquina puede tener este aspecto:

```
110100100101110010100010001001111010010110110
```

Cuando los ordenadores fueron haciéndose más potentes, pronto se vio que con el lenguaje máquina *no se podrían crear programas que aprovechasen esa potencia* por la sencilla razón de que era demasiado difícil programar así: no se podía hacer nada demasiado complicado porque el cerebro humano no está "diseñado" para pensar en binario.

Surgió entonces la idea de *utilizar el propio ordenador como traductor*: ¿por qué no escribir una instrucción como la anterior, que suma dos números, de una forma más parecida al lenguaje humano y que luego un pequeño programa de ordenador se encargue de traducir esa instrucción a su correspondiente ristra de ceros y unos? Así apareció el **lenguaje ensamblador**, cuyas instrucciones son equivalentes a las del lenguaje máquina, pero se escriben con palabras similares a las del lenguaje humano. Por ejemplo, para sumar dos números, la instrucción en ensamblador puede ser algo como:

```
ADD D1, D2
```

Los lenguajes de bajo nivel se caracterizan por ser **dependientes del hardware** de la máquina. Es decir: un programa escrito en lenguaje máquina o en ensamblador para una arquitectura Intel Core i5 no funcionará, por ejemplo, en un iMac o en una tableta con Android a menos que sea modificado sustancialmente. Incluso puede tener serios problemas para funcionar en máquinas de la misma familia pero con el resto del hardware diferente, o con un sistema operativo distinto.

## 5.2. Ensambladores, compiladores e intérpretes

### 5.2.1. Ensambladores

Se llaman ensambladores los programas encargados de **traducir los programas escritos en ensamblador** a código binario.

Fíjate que tanto el programa traductor como el lenguaje se llaman del mismo modo: ensamblador.

Como el lenguaje ensamblador es muy próximo al binario, estos traductores son programas relativamente sencillos.

![ud01_prog_06_ensamblador.png](/img/user/adjuntos/1DAM_Programacion/Unidad_01/ud01_prog_06_ensamblador.png)
> Proceso de ensamblado de un programa

### 5.2.2. Compiladores

El compilador es un programa que **traduce el código de alto nivel a código binario**. Es, por tanto, parecido al ensamblador, pero mucho más complejo, ya que las diferencias entre los lenguajes de alto nivel y el código binario son muy grandes.

![ud01_prog_07_compilador.png](/img/user/adjuntos/1DAM_Programacion/Unidad_01/ud01_prog_07_compilador.png)
> Proceso de compilación de un programa

El programa escrito en lenguaje de alto nivel se denomina **programa o código fuente**. El programa traducido a código binario se llama **programa o código objeto**. Por lo tanto, el compilador se encarga de convertir el programa fuente en un programa objeto.

Una vez que se ha obtenido el programa objeto ya no es necesario volver a realizar la traducción (o compilación), a menos que se haga alguna modificación en el programa fuente, en cuyo caso habría que volver a compilarlo.

El programa objeto, una vez generado, puede ejecutarse en la máquina en la que fue compilado, o en otra de similares características (procesador, sistema operativo, etc.). Cuando se usa programación modular, puede ser necesario un proceso previo de **enlace** de los diferentes módulos, pero de esto ya hablaremos más adelante.

### 5.2.3. Intérpretes

El intérprete es un programa que **traduce el código de alto nivel a código binario** pero, a diferencia del compilador, lo hace **en tiempo de ejecución**. Es decir, no se hace un proceso previo de traducción de todo el programa fuente a binario, sino que se va traduciendo y ejecutando instrucción por instrucción.

![ud01_prog_08_interprete.png](/img/user/adjuntos/1DAM_Programacion/Unidad_01/ud01_prog_08_interprete.png)
> Intérprete compilando y ejecutando línea a línea

### 5.2.4. Compiladores Vs. Intérpretes

**El intérprete es notablemente más lento que el compilador**, ya que realiza la traducción al mismo tiempo que la ejecución. Además, esa traducción se lleva a cabo siempre que se ejecuta el programa, mientras que el compilador sólo la hace una vez. Por estos motivos, un mismo programa interpretado y compilado se ejecuta mucho más despacio en el primer caso.

La ventaja de **los intérpretes es que hacen que los programas sean más portables**. Así, un programa compilado en una máquina PC bajo Windows no funcionará en un Macintosh, o en un PC bajo Linux, a menos que se vuelva a compilar el programa fuente en el nuevo sistema. En cambio, un programa interpretado funcionará en todas las plataformas, siempre que dispongamos del intérprete en cada una de ellas.

**JavaScript** es un ejemplo de lenguaje interpretado. Esto permite que los scripts puedan funcionar en cualquier máquina que disponga de un navegador de Internet capaz de interpretarlos, algo común en todos los sistemas actuales. En cambio, **C/C++** es un lenguaje compilado, lo que hace que los programas desarrollados con estos lenguajes se ejecuten más rápido que sus equivalentes en JavaScript, aunque obliga a volver a compilarlos si se desea ejecutarlos en una máquina con diferente hardware o diferente sistema operativo.

(De hecho, muchos programas en C no podrían escribirse en JavaScript, pero esa es otra historia)

### 5.2.5. La semicompilación. El caso peculiar de Java

En el diseño original del lenguaje Java estaba la premisa de hacer un lenguaje altamente portable (como son todos los lenguajes interpretados) y, al mismo tiempo, altamente eficiente (como son, por regla general, los lenguajes compilados). Prueba de que lo consiguieron es la ubicuidad actual del lenguaje Java en todo tipo de soportes y plataformas.

Para ello, los diseñadores de Java idearon lo que podríamos denominar una semicompilación, de modo que el código fuente se compila en un código binario, pero no el código binario de una máquina real, sino el de una máquina ficticia. Ese código binario se denomina **bytecode**.

Esa máquina ficticia, con su CPU, sus registros y todo su hardware, se emula mediante un software especial denominado **máquina virtual de Java** (JVM = Java Virtual Machine). La JVM toma el código binario del bytecode y lo interpreta, traduciéndolo en tiempo de ejecución al código binario real del sistema sobre el que se está trabajando.

La ventaja de este procedimiento es que la traducción del bytecode al código binario real es mucho más rápida que una interpretación tradicional, porque el bytecode ya es un código binario. Por lo tanto, la JVM se limita a formatear las instrucciones del bytecode para hacerlas comprensibles por la máquina real, y no tiene que realizar una traducción completa.

Por ese motivo, un programa escrito en Java y compilado en una arquitectura cualquiera, funcionará sin problemas al ejecutarlo en cualquier otra arquitectura, con el único requisito de haber instalado la JVM en el ordenador de destino.

Todo este proceso se describe en las siguientes figuras. Por ejemplo, supongamos que tenemos una plataforma Intel con un sistema Windows y el JDK instalado, y en ella desarrollamos una aplicación escrita en Java y la compilamos:

![Compilar a bytecode y ejecutar dicho bytecode en la JVM](https://docs.oracle.com/javase/tutorial/figures/getStarted/getStarted-compiler.gif)
> Compilar a bytecode y ejecutar dicho bytecode en la JVM

Hemos obtenido un programa “semicompilado” en un código binario de una máquina virtual. Nótese que hubiéramos obtenido exactamente lo mismo si estuviéramos trabajando bajo GNU/Linux, MacOS, Android o cualquier otro sistema.

Ahora, nos llevamos ese programa “semicompilado” a alguna otra plataforma, digamos un smartphone con Android y la JVM correctamente instalada. Bastará con lanzar la aplicación para que la JVM tome el control y realice la traducción final, al modo de los antiguos intérpretes, del bytecode al código binario nativo de nuestro smartphone:

![ud01_prog_10_bytecode.png](/img/user/adjuntos/1DAM_Programacion/Unidad_01/ud01_prog_10_bytecode.png)
> Ejecución de bytecode

Este doble proceso de “semicompilación” seguida de “semiinterpretacion” consigue el doble objetivo planteado en el diseño de Java: ser un lenguaje altamente portable al mismo tiempo que razonablemente eficiente.

### 5.2.6. Máquinas virtuales

Para entender completamente el funcionamiento de Java y su singular proceso de semicompilación, es necesario tener claro en concepto de máquina virtual, que introducimos a continuación.

Una **máquina virtual** es un programa informático que emula a un ordenador y puede ejecutar programas como si fuese un ordenador real. La máquina virtual puede emular un ordenador real o ficticio (esto último puede tener sentido con propósitos didácticos)

Una característica esencial de las máquinas virtuales es que los procesos que ejecutan están limitados por los recursos proporcionados por la máquina virtual. Es decir, si la máquina virtual "tiene" 1 GB de RAM, por ejemplo, los programas que ejecutemos en ella sólo pueden usar 1 GB, independientemente de que la máquina real tenga disponible más memoria física.

Uno de los usos domésticos más extendidos de las máquinas virtuales es ejecutar sistemas operativos para "probarlos". De esta forma podemos ejecutar un sistema operativo que queramos probar (GNU/Linux, por ejemplo) desde nuestro sistema operativo habitual (MacOS, por ejemplo) sin necesidad de instalarlo directamente en nuestra computadora y sin miedo a que se desconfigure el sistema operativo primario.

### 5.2.7. Tipos de máquina virtual

Las máquinas virtuales se pueden clasificar en dos grandes categorías según su funcionalidad y su grado de equivalencia a una verdadera máquina. Son las **máquinas virtuales de sistema o de proceso**.

Veamos ambos tipos de máquinas:

**A. Máquinas virtuales de sistema (System Virtual Machine)**  
  Las máquinas virtuales de sistema, también llamadas máquinas virtuales de hardware, permiten a la máquina física subyacente "dividirse" entre varias máquinas virtuales, cada una ejecutando su propio sistema operativo. A la capa de software que permite la virtualización se la llama monitor de máquina virtual o "hypervisor". Un monitor de máquina virtual puede ejecutarse o bien directamente sobre el hardware o bien sobre un sistema operativo ("host operating system").

  Estas máquinas virtuales permiten a varios sistemas operativos distintos pueden coexistir sobre la misma computadora, en completo aislamiento el uno del otro.
  
  Varias máquinas virtuales, cada una con su propio sistema operativo, pueden ser utilizadas en servidores para ejecutar diferentes servicios en la misma máquina de manera completamente aislada y compartiendo los recursos de una única computadora. Esto contribuye a reducir el coste total de las instalaciones necesarias para mantener los servicios, dado que permiten ahorrar en hardware.
  
  Además, la virtualización es una excelente opción hoy día, ya que los PCs de sobremesa en la mayoría de los casos están siendo infrautilizados (gran capacidad de disco duro, memoria RAM, etc). Al virtualizar, la necesidad de nuevas máquinas en una ya existente permite un ahorro considerable de los costos asociados (energía, mantenimiento, espacio, etc).
  
  La mayoría de los programas de virtualización conocidos pertenecen a esta categoría de máquina virtual. Entre los más famosos están:

  - **[VMWare](https://www.vmware.com/products/desktop-hypervisor)**. Ha sido el software de virtualización por excelencia durante muchos años. Es software privativo, aunque tiene una versión gratuita. Funciona en Windows, Linux y Mac.
  - **[VirtualBox](https://www.virtualbox.org/)** de Oracle (antes Sun). Funciona también en Windows, Linux y Mac. Tiene una versión Open Source (VirtualBox OSE), y es el que vamos a usar nosotros este curso.
  - **[VirtualPC](https://support.microsoft.com/es-es/topic/descripci%C3%B3n-de-windows-virtual-pc-262c8961-90e5-1125-654f-d87cd5ba16f8)**. Está desarrollado por Microsoft, por lo que es una excelente opción para virtualizar sistemas Windows. No funciona bajo Linux, aunque sí bajo Mac.

**B. Máquinas virtuales de proceso (Process Virtual Machine)**
  Una máquina virtual de proceso, a veces llamada "máquina virtual de aplicación", se ejecuta como un proceso normal dentro de un sistema operativo y soporta un solo proceso. La máquina se inicia automáticamente cuando se lanza el proceso que se desea ejecutar y se detiene para cuando éste finaliza. Su objetivo es el de proporcionar un entorno de ejecución independiente de la plataforma de hardware y del sistema operativo, que oculte los detalles de la plataforma subyacente y permita que un programa se ejecute siempre de la misma forma sobre cualquier plataforma.

  **La máquina virtual Java es de este tipo**. Por lo tanto, cada vez que lanzamos un programa compilado en el bytecode de Java, la JVM emula el hardware necesario para realizar la ejecución (interpretación) del código y ejecutar así la aplicación independientemente del hardware real.

  Otra máquina virtual con la misma filosofía y muy extendida es la del entorno .Net de Microsoft.



[^1]: QUERO, E., Fundamentos de programación, Ed. Paraninfo, 2003

# 6. Herramientas para desarrollar con Java

Para empezar a programar, en este caso con el lenguaje Java, se necesitan las siguientes herramientas:

1. El <abbr title="Java Development Kit">JDK</abbr> o *kit de desarrollo de Java*.
2. Un <abbr title="Integrated Development Environment">IDE</abbr> o un editor de código.

Veámoslos con más detalle en los siguientes apartados.


## 6.1. El JDK

El <abbr title="Java Development Kit">JDK</abbr> es un paquete de software que contiene todo lo necesario para desarrollar aplicaciones escritas en Java, excepto un editor de texto, del que hablaremos más adelante.

En concreto, el **JDK** incluye:

- La **biblioteca de clases** estándar de Java.
- La **<abbr title="Java Virtual Machine">JVM</abbr>** o *Máquina Virtual Java* (`java`).
- El **compilador** de java (`javac`).
- Un **desensamblador** de clases (`javap`).
- Un **depurador** de consola (`jdb`).
- El **generador automático de documentación** (`javadoc`).

No te preocupes si no sabes aún qué son algunas de estas cosas. Lo irás aprendiendo a lo largo del curso. ¡No se conquistó Roma en un solo día!

Todos los elementos de la lista, excepto el primero, constituyen lo que se llama **JRE**. Son los componentes necesarios para compilar y ejecutar aplicaciones java. Pero, para desarrollar programas nuevos, necesitamos además la biblioteca de clases. El conjunto de JRE más biblioteca de clases es lo que se denomina JDK.

Una vez instalado el JDK, y dependiendo de la versión de Java, deberás revisar el valor de dos variables de entorno para que el compilador funcione correctamente:

- **Variable PATH**: debe apuntar al directorio bin del JDK. Si no la cambias, estarás obligado compilar siempre desde el directorio bin, lo cual es bastante engorroso.

- **Variable CLASSPATH**: debe apuntar al directorio raíz en donde estén las clases del JDK (solo para versiones antiguas del JDK)

La última versión del JDK puede descargarse gratuitamente de:

- El **[sitio web de Oracle](https://www.oracle.com/es/java/technologies/downloads/)**.
- El de **[OpenJDK](https://openjdk.org/)**, la implementación open-source del JDK.
- La de **[Eclipse Adoptium (Temurin)](https://adoptium.net/es/temurin/releases)**, también gratuita y de código abierto.
- El OpenJDK de **[Microsoft Build](https://learn.microsoft.com/es-es/java/openjdk/download)**, optimizada para trabajar de forma con entornos en la nube (como Azure).
- La de **[Amazon Corretto](https://aws.amazon.com/es/corretto/)**, otra OpenJDK mantenida por AWS.

> [!warning] ¡Cuidado!
> Estos sitios son de confianza, aunque existen algunos más. Lo más recomendable es usar alguna de estas versiones de JDK. El resto deben mirarse con cautela, con ojos recelosos...

## 6.2. Editores de texto

Decíamos antes que el JDK incluye todo lo necesario para desarrollar aplicaciones en Java, excepto un editor de texto.

El editor de textos nos servirá para teclear el código de nuestro programa para posteriormente compilarlo y ejecutarlo. Puedes escoger el editor de texto que prefieras, solo teniendo en cuenta dos cosas:

- Que guarde los archivos en **texto plano**, no formateado. En este sentido, no son apropiados los editores de texto como Microsoft Word o LibreOffice Writer, aunque pueden usarse si no tienes otra cosa a mano.

- Que permita seleccionar la codificación de caracteres. En general, preferiremos usar la codificación **UTF-8**, pero puede haber casos en los que necesitemos otra. Esto será útil, sobre todo, cuando desarrolles aplicaciones que accedan a bases de datos o que generen páginas web. Prácticamente todos los editores lo permiten en la actualidad.

Además, es muy interesante que el editor reconozca el lenguaje en el que estamos programando y nos coloree las palabras clave, identificadores, etc. Eso facilita enormemente la lectura y comprensión del código que estamos desarrollando. Así que, no, no es buena idea usar el bloc de notas de Windows.

Editores que cumplan estas características hay miles, y muchos son gratuitos. Aunque la mayoría ya son multiplataforma (funcionan en distintos sistemas operativos)...

- **[Sublime Text](https://www.sublimetext.com/)**
- **[emacs](https://www.gnu.org/software/emacs/)**
- **[kwrite](https://apps.kde.org/es/kwrite/)**
- **[gEdit](https://gedit-text-editor.org/)**
- **[UltraEdit](https://www.ultraedit.com/es/ultraedit/)**
- **[Akelpad](https://akelpad.sourceforge.net/en/index.php)**

... hay otros editores creados exclusivamente para plataformas como:

- En entornos **Windows**:
  - **[Notepad++](https://notepad-plus-plus.org/)**

- En entornos **Mac**:
  - TextWrangler
  - Xemacs
  - BBEdit
  - ...

## 6.3. Entornos integrados de desarrollo

Finalmente, está la posibilidad de usar el **Entorno Integrado de Desarrollo** (<abbr title="Integrated Development Environment">IDE</abbr>, por sus siglas en inglés). Esta es la elección de la inmensa mayoría de los programadores profesionales, y con seguridad también será la tuya dentro de unos meses.

Un <abbr title="Integrated Development Environment">IDE</abbr> es **una herramienta que proporciona, dentro del mismo interfaz, acceso a todas las funciones anteriores**:

- Edición del código fuente
- Compilación
- Depuración
- Ejecución
- ...

En realidad, lo que hace es invocar de forma transparente a las herramientas del JDK, de modo que el programador se ahorra ese trabajo. Así, resulta mucho más cómodo y rápido programar con la ayuda de un IDE que compilando e invocando los comandos del JDK desde la consola.

Sin embargo, consideramos (y, con nosotros, mucha gente) que, para un aprendiz, es mucho más ilustrativo trabajar con las herramientas básicas que hemos descrito aquí para adquirir una visión global del funcionamiento del JDK. Más adelante, cuando esto esté claro, habrá tiempo de saborear las bondades de un buen IDE.

Algunos IDEs son monstruos *devorarrecursos* que disponen de herramientas adicionales potentísimas, como autocompleción de sentencias, generador automático de código, analizador del rendimiento, refactorizador, soporte multilenguaje... Otros son más simples y ligeros, y disponen de un editor sencillo y unos pocos menús para guardar, editar y compilar.

**La elección del IDE es algo muy personal**. Llegarás a una conclusión después de tener alguna experiencia con varios de ellos. Por ahora, te vamos mencionando algunos de los más populares para el desarrollo de aplicaciones Java, para que sus nombres de vayan sonando:

- Entre los IDEs *pesados*:
  - [IntelliJ](https://www.jetbrains.com/es-es/idea/download/)
  - [Eclipse](https://eclipseide.org/)
  - [NetBeans](https://netbeans.apache.org/front/main/index.html).

- Entre los IDEs *ligeros*:
  - [BlueJ](https://www.bluej.org/)
  - [Geany](https://www.geany.org/)



# 7. Qué es Java

Para empezar a programar en Java primero hemos de entender un poco qué es y de dónde viene.

Si te estás preguntando qué demonios es Java, la respuesta es sencilla: es un **lenguaje de programación de ordenadores**. Si no tienes claro qué es un lenguaje de programación, repasa las secciones anteriores. Por supuesto, tiene una serie de características que lo hacen diferente del resto de lenguajes. Sigue leyendo para descubrirlas.

## 7.1. Un poco de historia

Java fue creado en 1991 por **[James Gosling](https://es.wikipedia.org/wiki/James_Gosling)**, cuando trabajaba en **Sun Microsystems**, aunque la primera versión no vio la luz hasta **1996**. Tuvo como referentes a **C** y **C++**, y por eso su sintaxis se parece mucho a la de estos lenguajes, aunque ahí acaban sus similitudes. Existen varias teorías levemente absurdas sobre el origen de su nombre, todas sin comprobar. El propio Gosling ha sugerido que fue elegido aleatoriamente entre una lista de palabras.

Las primeras versiones se denominaron **JDK 1.0**, **JDK 1.1**, etc. Luego, pasaron a llamarse **Java 2** o **J2**, diferenciando las versiones:

- Estándar (<abbr title="Standard Edition">SE</abbr>)
- Empresarial (<abbr title="Enterprise Edition">EE</abbr>)
- Doméstica (<abbr title="Micro Edition">ME</abbr>), pensada para dispositivos con hardware limitado.

Así, es posible que encuentres versiones llamadas **J2SE 1.4**. Significa que es la versión JDK 1.4, edición estándar. Lógicamente, las diferencias entre la SE, EE y ME estriban en la cantidad de componentes que incorpora el JDK y su coste (gratuito para las SE y ME).

La versión JDK 1.5 se denominó **J2SE 5**. A partir de aquí, dejó de usarse la denominación “J2” y se habla de **Java SE 6**, **Java SE 7**, etc.

En **2010**, el gigante de la informática Oracle se fusionó con Sun Microsystems. Desde entonces, la tecnología **Java es propiedad de Oracle**, aunque la mayor parte de su código tiene licencia GNU/GPL, es decir, es software libre cuyo código fuente está a disposición de todo el mundo. De hecho, existen versiones alternativas del JDK que no están desarrolladas por Oracle, como la GNU Classpath, que es completamente libre.

Sobre el **2014** aparece **Java 8**, considerada la versión más relevante, donde se ven cambios y una evolución muy superior a las versiones anteriores. Entre otros avances, incorpora la **programación funcional** (*expresiones lambda* y la *Stream API*, que veremos en unidades posteriores).

En el 2017, con **Java 9**, aparece **Project Jigsaw** para implementar un sistema de módulos de la plataforma Java, dividiendo el ya enorme núcleo de Java en módulos independientes. De esa forma se podía optimizar el rendimiento y la creación de aplicaciones en la nube. Acabaron con el entorno monolítico que era la plataforma Java, permitiendo empaquetar solo las dependencias que usara cada aplicación.

A partir del **2018** Oracle decide replantear el ciclo de lanzamientos. Hasta entonces, una nueva versión de Java podía tardar años en publicarse. Desde este año, Oracle se comprometía a sacar una nueva versión **cada 6 meses**.

> [!info] Para saber más... 
> Antes el JRE y el JDK se distribuían por separado. Desde Java 11, todo está incluido en un solo paqute: el JDK.
> 
> Si quieres saber más, consulta [[1DAM_ED/Unidad 02/4. Codificación#4.7.1. Funcionamiento del entorno de ejecución\|las notas del módulo de Entornos de Desarrollo]].

## 7.2. Características principales de Java

Según Wikipedia, Java se caracteriza porque:

- Es un lenguaje de programación de **propósito general, concurrente, orientado a objetos y basado en clases**.

- Fue diseñado para tener tan **pocas dependencias** de implementación como fuera posible, es decir, para ser muy **portable** de un sistema a otro (esta característica es conocida en inglés como WORA, o "write once, run anywhere"). Esto se consigue gracias a la compilación en bytecode y a la ejecución en máquina virtual de la que hablábamos más arriba.

- Tiene **recolección de basura automática**. Esto significa que la memoria ocupada por los objetos no tiene que ser liberada por el programador cuando éstos dejan de usarse, sino que la propia máquina virtual se encarga de ello. La gestión de la memoria es una de las mayores pesadillas de los programadores en C/C++.

- Es, en la actualidad, **uno de los lenguajes de programación más populares del mundo**, particularmente para **aplicaciones de cliente-servidor de web**, **dispositivos móviles** y **sistemas empotrados**. Sin embargo, su uso en applets (miniaplicaciones web ejecutables en el navegador del cliente), muy popular en los años 90, se descartó a partir de Java 26 debido a sus problemas de compatibilidad y seguridad y a la pujanza de JavaScript.


# 8. Primeros pasos en Java

Por fin ha llegado el momento. ¡Comenzamos con el código!

En los siguientes apartados vamos a empezar a ver qué aspecto tiene el código Java y cómo empezar a usarlo. 

## 8.1. Estructura básica de un programa en Java

Echa un vistazo al siguiente código fuente. **No te agobies si no lo entiendes todo**. Supón que estás leyendo algo escrito en el idioma de algún país al que vas a viajar próximamente y en el que vas a vivir durante un tiempo. Te han dicho que el idioma de ese país se parece un poco al inglés, y por eso tienes ciertas esperanzas de entenderlo, al menos un poco.

Venga, inténtalo: 

```java
public class HolaMundo {
    /* Programa HolaMundo */
    public static void main(String[] args) {
        /*
        Lo único que hace este programa es
        mostrar un saludo por la pantalla
        */
    
        System.out.println(“Hola, mundo!”);
    }
}
```

En este sencillo programa podemos apreciar varias características importantes de Java:

- Todo el código Java se debe incrustar dentro de unas estructuras llamadas **clases**. Todas las clases deben tener un nombre (`HolaMundo`)

- Dentro del código se pueden intercalar comentarios escritos en lenguaje natural, rodeados con los caracteres `/*` y `*/`, o precedidos de una doble barra: `//`

- Dentro de las clases puede haber muchas cosas. En concreto, al menos una clase debe disponer de un bloque de código (técnicamente hablando, un **método**) con el nombre **`main()`**: por ahí comenzará la ejecución del programa. Este método es **público** (se puede ejecutar desde cualquier lugar), es **estático** (se puede invocar sin instanciar la clase) y **no devuelve ningún valor** (`void`) a quien lo ejecutó.

¿Que no lo entiendes todo? **No pasa nada**. Por ahora, bastará con que entiendas una pequeña parte. Vuelve sobre estas líneas dentro de dos semanas y te sorprenderá lo mucho que has aprendido.

Puedes consultar el material de apoyo:

> [!example] Material de apoyo 
> [[1DAM_Programación/Unidad 01/Referencias#Introducción\|1DAM_Programación/Unidad 01/Referencias#Introducción]]
> [[1DAM_Programación/Unidad 01/Referencias#Hola Mundo en JAVA\|1DAM_Programación/Unidad 01/Referencias#Hola Mundo en JAVA]]

> [!info] Para más información... 
> Consulta el [[1DAM_Programación/Unidad 01/10. Apéndice. Entrada y salida por consola\|apéndice]] de esta unidad, donde se explica cómo mostrar información por consola y cómo permitir al usuario introducir en nuestro programa datos desde teclado.

## 8.2. Ejecutando mi primer programa en Java

Para ejecutar el programa `HolaMundo` en tu ordenador, debes tener instalado el JDK y configurada la variables de entorno PATH (y CLASSPATH, en versiones antiguas) como se explicó anteriormente.

Teclea el programa “HolaMundo” con un editor de texto y guárdalo en un directorio de trabajo con el nombre HolaMundo.java. Es importante que el nombre del archivo coincida con el de la clase que hay dentro de él, incluyendo las mayúsculas, si las hubiera.

Abre una consola de texto en tu directorio de trabajo y teclea:

```bash
$ javac HolaMundo.java
```

> [!note] Nota
> Para los neófitos: el carácter **`$`** NO se teclea, solo representa el símbolo del intérprete de comandos. Cuando lo veas escrito delante de un comando, significa que ese comando está destinado a escribirse en la consola)

Si has escrito bien el código de HolaMundo, no se mostrará ningún error y se generará un archivo llamado **`HolaMundo.class`**. Este archivo es el HolaMundo compilado a bytecode. Pero si te aparece algún error, tendrás que volver a editar tu código fuente y corregirlo antes de continuar. Fíjate bien en el mensaje de error: suele dar bastantes pistas.

Cuando consigas tu `HolaMundo.class`, podrás ejecutarlo con:

```bash
$ java HolaMundo
```

En la pantalla deberías ver el saludo **`Hola, mundo!`**:

```bash
$ java HolaMundo
Hola, mundo!
$ 
```

Ese es tu primer programa ejecutándose y saludándote. **¡Enhorabuena!** Tal vez no te parezca gran cosa, pero ten en cuenta algo: **todos hemos empezado exactamente por ahí**.

## 8.3. El compilador javac, a fondo

En esta sección vamos a ver con más detalle cómo funciona el compilador de consola del JDK. Esta concebida como una referencia para usuarios más avanzados. Si es la primera vez que lees esto, es mejor que saltes a la siguiente sección.

El compilador de java suele denominarse javac (Java Compiler). Es un fichero ejecutable que se invoca desde los IDE para java cada vez que seleccionamos la opción adecuada, pero también puede ejecutarse desde la línea de comandos.

Para poder usar javac desde la línea de comandos debemos situarnos en el directorio donde está el archivo ejecutable. En un sistema Windows, tendrá la forma c:\Archivos de programa\Java\jdkX.Y.Z\bin, o algo similar. También existe la posibilidad de modificar la variable de sistema PATH para que apunte al directorio de javac, y así poder invocarlo desde cualquier lugar. En los sistema Linux, podrá invocarse javac desde cualquier directorio, ya que se instala junto con el resto de programas en /bin o en /usr/bin

Como todos los programas de línea de comandos, javac tiene una sintaxis determinada que permite modificar la forma en la que el programa se ejecuta. Esta sintaxis es:

```bash
$ javac [ opciones ] [ ficheros_fuente]
```

En “ficheros_fuente” colocaremos los nombres de los archivos fuente que queremos compilar. Las opciones sirven para ajustar el funcionamiento del compilador. Por ejemplo:

```bash
$ javac -g miPrograma.java
```

Las opciones principales de `javac` son:

- `cp directorios`: especifica un conjunto de directorios (separados por : en sistemas Linux y por ; en sistemas Windows) donde buscar las clases adicionales necesarias para la compilación. Sustituye a la variable de entorno `CLASSPATH`.

- `d directorio`: especifica el directorio de destino de los archivos compilados. El directorio debe existir. Si no se indica ningún directorio, los archivos compilados se guardarán en el mismo directorio donde estén los fuentes.

- `g`: añade al archivo compilado información de depuración, para poder depurarlo posteriormente. Debe usarse siempre, excepto en la versión definitiva del programa, donde puede omitirse.

- `nowarn`: deshabilita los avisos (“warnings”)

- `verbose`: hace que la ejecución del compilador muestre información adicional en la consola al mismo tiempo que compila el código, como las clases que se van usando. Puede ayudar en la depuración.

- `Jopciones`: pasa “opciones” a la máquina virtual que posteriormente ejecutará el código compilado. Ejemplo:  

  ```bash
  $ javac -g -nowarn -d /home/usuario/mis_clases miPrograma.java
  ```

## 8.4. El depurador jdb

El jdb es el depurador de Java. Al funcionar desde la línea de comandos resulta complejo de aprender a usar. En realidad, casi nadie lo utiliza si no es a través de los menús de un IDE, de modo que esta sección solo es una referencia rápida para aquellos que estén muy interesados en este asunto. Si no es tu caso, puedes pasar sin problemas a la siguiente sección.

Recuerda que para usar el depurador las aplicaciones Java deben estar compiladas con la opción -g. Posteriormente, para depurarlas usaremos:

```bash
$ jdb [nombreclass]
```

Entramos entonces en un nuevo prompt, el del jdb, a través del cual podemos realizar la depuración de la clase. Para ello se usan los siguientes comandos:

- `help`: proporciona una lista de los comandos que están disponibles en la sesión de jdb.
- `print <id> [id(s)]`: imprime un objeto o campo
- `dump <id> [id(s)]`: imprime toda la información del objeto
- `locals`: imprime las variables locales de la pila actual
- `classes`: lista las clases conocidas
- `methods <class id>`: lista los métodos de una clase
- `stop in <class id>.<method>`: fija un punto de ruptura en un método
- `stop at <class id>:<line>`: establece un punto de ruptura en una línea
- `clear <class id>:<line>`: eliminar un punto de ruptura
- `step`: ejecutar la línea actual
- `cont`: continuar la ejecución desde el punto de ruptura
- `catch <class id>`: parar por la excepción especificada
- `ignore <class id>`: ignorar la excepción especificada
- `list [line number]`: imprimir código fuente
- `use [source file path]`: ver o cambiar la ruta del fichero fuente
- `memory`: informe del uso de la memoria
- `load <classname>`: carga la clase Java a ser depurada
- `run <args>`: comienza la ejecución de la clase cargada
- `!!`: repite el último comando
- `exit (o quit)`: salir del depurador

## 8.5. La ejecución del código objeto

Nuevamente, este apartado está concebido como una referencia para usuarios que quieren usar el comando de ejecución de forma más avanzada. Si no es tu caso, puedes saltar a la siguiente sin perderte nada.

El comando java lanza una aplicación compilada con javac, es decir, lanza la JVM para interpretar el código objeto en `bytecodes`.

Como todos los comandos, java tiene una sintaxis definida:

```bash
$ java [ opciones ] fichero.class [ argumentos ]
```

Las opciones modifican el funcionamiento de la JVM. La clase se refiere a un archivo .class, y los argumentos son los que se pasarán al programa compilado.

También se puede ejecutar un .jar de este modo:

```bash
$ java [ opciones ] -jar fichero.jar [ argumentos ]
```

Algunas opciones del comando java son:

- `d32` y `d64`: hacen que el programa se ejecute en una JVM de 32 o de 64 bits, respectivamente.
- `verbose`: para mostrar información adicional de la ejecución.
- `X`: lista de opciones no-estándar (variarán de una JVM a otra)

> [!example] Material de apoyo 
> [[1DAM_Programación/Unidad 01/Referencias#Introducción a Java - Aula Informática\|1DAM_Programación/Unidad 01/Referencias#Introducción a Java - Aula Informática]]
> [[1DAM_Programación/Unidad 01/Referencias#Introducción a Java - Aula en la nube\|1DAM_Programación/Unidad 01/Referencias#Introducción a Java - Aula en la nube]]
> [[1DAM_Programación/Unidad 01/Referencias#JAVA Salida por pantalla - Aula en la nube\|1DAM_Programación/Unidad 01/Referencias#JAVA Salida por pantalla - Aula en la nube]]
> [[1DAM_Programación/Unidad 01/Referencias#JAVA Entrada de datos - Aula en la nube\|1DAM_Programación/Unidad 01/Referencias#JAVA Entrada de datos - Aula en la nube]]


# 9. Tipos de datos simples

Como vimos al definir qué es un programa de ordenador, tan importantes son las instrucciones de que consta un programa como los datos que maneja.

Los **_datos_**, como definimos al principio del tema, son representaciones simples de los objetos del mundo real. Esos objetos pueden ser simples (por ejemplo, la edad de una persona, o el número de trabajadores de una empresa) o complejos (por ejemplo, la flota de camiones de una empresa de transportes).

Nosotros nos referiremos ahora a los **tipos de datos simples** u objetos simples. Son importantes porque los objetos más complejos se fundamentan en ellos, y es necesario informar a Java de cuáles son los tipos que vamos a usar porque necesita saberlo para reservar los recursos necesarios para almacenarlos (principalmente, memoria RAM)

En ocasiones, también se distinguen los lenguajes según cómo manejen los tipos de datos. Se entiende por tipo de datos el dominio en el que un determinado dato puede tomar un valor. Así, determinada variable puede ser de tipo “número entero”, lo que significa que sólo puede contener números sin decimales, o puede ser de tipo “cadena alfanumérica”, que significa que puede contener un número indefinido de caracteres alfanuméricos.

## 9.1. ¡Tipos de tipos!

Distinguir el tipo de dato de cada variable es engorroso para el programador principiante, pero el necesario para indicar al ordenador cuánta memoria es necesario reservar para almacenar los datos del programa que se pretende ejecutar.

Pues bien, atendiendo a cómo el lenguaje maneja los tipos de datos, podemos distinguir:

- **Lenguajes con tipado dinámico**: una misma variable puede cambiar de tipo a lo largo de la ejecución del programa. Ejemplos: **JavaScript**, **PHP**, **Python**, **Perl**, **Lisp**.

- **Lenguajes con tipado estático**: una variable, una vez que es asignada a un tipo de dato, no puede cambiar de tipo. Es menos flexible que el tipado dinámico, pero también más eficiente. Ejemplos: **C**, **C++**, **Java**, **Basic**, **Pascal**.

- **Lenguajes débilmente tipados**: no hacen comprobaciones exhaustivas de tipos de datos. Así, permiten manipular los datos de determinado tipo como si fueran de otro tipo. Por ejemplo, un dato de tipo carácter puede manipularse, si al programador le conviene, como un dato numérico (ya que en el fondo los caracteres son números). Esto puede provocar resultados extraños si el programador comete un error, pero proporciona mucha flexibilidad si se usa correctamente.

- **Lenguajes fuertemente tipados**: comprueban exhaustivamente que las variables de cada tipo sólo se usan conforme a lo que ese tipo permite. Por ejemplo, no se permitirá realizar una operación de suma con caracteres. Son menos flexibles y, además, más ineficientes, puesto que deben realizar comprobaciones de tipo en tiempo de ejecución, es decir, deben introducir código máquina adicional para hacer las comprobaciones de tipo. A cambio, suelen generar programas mucho más robustos y tolerantes a fallos.

Es habitual confundir el tipado estático con el tipado fuerte, y el dinámico con el débil. En realidad, son categorías complementarias que se pueden mezclar: existen lenguajes con tipado estático y débil (como C) y otros con tipado dinámico y fuerte (como Visual Basic)

> [!example] Material de apoyo 
> [[1DAM_Programación/Unidad 01/Referencias#JAVA Tipos de variables - Aula en la nube\|1DAM_Programación/Unidad 01/Referencias#JAVA Tipos de variables - Aula en la nube]]

## 9.2. Tipos de datos primitivos en Java

Java es un lenguaje con tipado estático y fuerte. En Java, se llama tipo de datos simple a lo que en realidad es una clase, pero esta diferencia no nos importa por el momento. Cada tipo de datos, además, tiene asociado un conjunto de operaciones para manipularlos.

Cada tipo de datos dispone de una representación interna diferente en el ordenador; por eso es importante distinguir entre tipos de datos a la hora de programar.

Los tipos primitivos de Java son:

- Números enteros
- Números reales
- Caracteres
- Lógicos

Así, por ejemplo, en el caso de un programa de gestión de nóminas, la edad de los empleados será un dato de tipo número entero, mientras que el dinero que ganan al mes será un dato de tipo número real.

### 9.2.1. Tipos primitivos
#### Números enteros

Es probablemente el tipo más sencillo de entender. Los datos de tipo entero sólo pueden tomar como valores:

```
..., -4, -3, -2, -1, 0, 1, 2, 3, 4, ...
```

Como el ordenador tiene una memoria finita, la cantidad de valores enteros que puede manejar también es finita y depende del número de bits que emplee para ello (recuerda que el ordenador, internamente, representa todos los datos en binario).

Además, los enteros pueden ser **con signo** y **sin signo**. Si tienen signo, se admiten los números negativos; si no lo tienen, los números sólo pueden ser positivos (sería más correcto llamarlos números naturales).

(Los enteros con signo se almacenan en binario en **complemento a uno** o en **complemento a dos**. Estas representaciones internas las estudiarás en el módulo de Sistemas, por lo que no vamos a detenernos ahora en detallarlas)

Por lo tanto:

- Si se utilizan **8 bits** para codificar los números enteros, el rango de valores permitido irá **de 0 a 255** (sin signo) o **de -128 a +127** (con signo).

- Si se utilizan **16 bits** para codificar los números enteros, el rango será **de 0 a 65535** (sin signo) o **de -32768 a 32767** (sin signo).

- Si se utilizan **32 bits**, el rango será **de 0 a más de 4 mil millones** (sin signo), o **de menos dos mil millones a más dos mil millones** (aproximadamente) con signo.

- Si se utilizan **64, 128 bits o más**, se pueden manejar números enteros mayores. Puedes calcular los rangos de números resultantes y sentir escalofríos.  

Los tipos enteros primitivos en Java son:

- **`byte`**: entero de 8 bits con signo.
- **`short`**: entero de 16 bits con signo.
- **`int`**: entero de 32 bits con signo.
- **`long`**: entero de 64 bits con signo.

Estas representaciones son independientes de la plataforma, a diferencia de lo que ocurre con otros lenguajes, en los que un tipo de datos puede tener una longitud distinta en cada sistema.

#### Números reales

El tipo de dato número real permite representar números con decimales. La cantidad de decimales de un número real puede ser infinita, pero al ser el ordenador una máquina finita es necesario establecer un número máximo de dígitos decimales significativos.

La representación interna de los números reales se denomina coma flotante (también existe la representación en coma fija, pero no es habitual). La coma flotante es una generalización de la notación científica convencional, consistente en definir cada número con una mantisa y un exponente.

La notación científica es muy útil para representar números muy grandes economizando esfuerzos. Por ejemplo, el número **129439000000000000000** tiene la siguiente representación científica:

1,29439 x 10<sup>20</sup>

Pero el ordenador representaría este número siempre con un 0 a la izquierda de la coma, así:

0,129439 x 10<sup>21</sup>

La mantisa es el número situado en la posición decimal (129439) y el exponente es 21.

La notación científica es igualmente útil para números decimales muy pequeños. Por ejemplo, el número 0,0000000000000000000259 tiene esta notación científica:

2,59 x 10<sup>-23</sup>

Pero el ordenador lo representará así:

0,259 x 10<sup>-22</sup>

Siendo 259 la **mantisa** y -22 el **exponente**.  

Internamente, el ordenador reserva varios bits para la mantisa y otros más para el exponente. Como en el caso de los números reales, la magnitud de los números que el ordenador pueda manejar estará directamente relacionada con el número de bits reservados para su almacenamiento.

Java dispone de dos tipos primitivos para manejar números reales:

- **float**: coma flotante de 32 bits (1 bit de signo, 8 de exponente y 23 de mantisa)
- **double**: coma flotante de 64 bits (1 bit de signo, 11 de exponente y 52 de mantisa)

> [!example] Material de apoyo 
> [[1DAM_Programación/Unidad 01/Referencias#JAVA Decimales y precisión\|1DAM_Programación/Unidad 01/Referencias#JAVA Decimales y precisión]]

#### Overflow

Cuando se realizan operaciones con números (tanto enteros como reales), es posible que el resultado de una de ellas dé lugar a un número fuera del rango máximo permitido. Por ejemplo, si tenemos un dato de tipo entero sin signo de 8 bits cuyo valor sea 250 y le sumamos 10, el resultado es 260, que sobrepasa el valor máximo (255).

En estos casos, estamos ante un caso extremo denominado **_overflow_** o **desbordamiento**. Los ordenadores pueden reaccionar de forma diferente ante este problema, dependiendo del sistema operativo y del lenguaje utilizado. Algunos lo detectan como un error de ejecución del programa, mientras que otros lo ignoran, convirtiendo el número desbordado a un número dentro del rango permitido pero que, obviamente, no será el resultado correcto de la operación, por lo que el programa probablemente fallará.

En el caso de Java, la JVM proporcionará un error en tiempo de ejecución si se produce un desbordamiento. Ese error puede capturarse mediante una excepción para tratarlo adecuadamente. Veremos más adelante como hacer todo esto.

#### Caracteres y cadenas

El tipo de dato **_carácter_** sirve para representar datos alfanuméricos. El conjunto de elementos que puede representar está estandarizado según el código ASCII, que, como ya vimos, consiste en una combinación de 7 u 8 bits asociada a un carácter alfanumérico concreto.

Java proporciona el tipo `char`, de **16 bits**, para manejar caracteres.

Las combinaciones de 7 bits de ASCII clásico dan lugar a un total de 127 valores distintos (desde 0000 0000 hasta 1111 1111). En Java, se siguen reservando esos 127 valores para la codificación ASCII. El resto, sirve para almacenar los caracteres en formato Unicode. Los caracteres válidos que pueden almacenarse en una variable tipo char son:

- Las letras minúsculas: 'a', 'b', 'c' ... 'z'
- Las letras mayúsculas: 'A', 'B', 'C' ... 'Z'
- Los dígitos: '1', '2', '3' ...
- Caracteres especiales o de otros idiomas: '$', '%', '¿', '!' , 'ç'...

Nótese que no es lo mismo el valor entero 3 que el carácter '3'. Para distinguirlos, usaremos siempre **comillas para escribir los caracteres**.

Los datos tipo carácter sólo pueden contener UN carácter. Una generalización del tipo carácter es el tipo **_cadena de caracteres_**, utilizado para representar series de varios caracteres. Éste, sin embargo, es un **objeto complejo** y será estudiado más adelante. Sin embargo, las cadenas se utilizan tan a menudo que no podremos evitar usarlas en algunos ejercicios antes de estudiarlas a fondo.

#### Datos lógicos

El tipo dato lógico, también llamado booleano[^1], es un dato que sólo puede tomar un valor entre dos posibles. Esos dos valores son:

- **Verdadero** (en inglés, `true`)
- **Falso** (en inglés, `false`)

Este tipo de datos se utiliza para representar alternativas del tipo sí/no. En algunos lenguajes, el valor true se representa con el número 1 y el valor false con el número 0. Es decir, los datos lógicos contienen información **binaria**. Esto ya los hace bastante importantes, pero la mayor utilidad de los datos lógicos viene por otro lado: son el resultado de todas las operaciones lógicas y relacionales, como veremos en el siguiente epígrafe.

En Java, los datos booleanos se manejan mediante el tipo **`boolean`**.

### 9.2.2. Conversiones de tipo (casting)

Java es un lenguaje **fuertemente _tipado_**, por lo que suele reaccionar mal ante el intento de mezclar tipos de datos distintos en la misma expresión.

En general, en estos casos se puede hablar de dos tipos de conversión de datos:

- **Conversiones implícitas**: se realizan de forma automática al mezclar tipos de datos. En Java solo puede hacerse si la **variable receptora** del resultado **tiene más precisión** que las variables situadas en la expresión. Por ejemplo, puede asignarse un int a un long, pero no al revés.

- **Conversiones explícitas**: el programador especifica mediante el código la conversión de un tipo en otro, indicando el nuevo tipo entre paréntesis durante la asignación. Este proceso se denomina casting y se muestra en el siguiente ejemplo:

  ```java
  int dato_i = 5;
  byte dato_b;
  dato_b = (byte)dato_i; // La variable entera dato_i se convertirá a byte
  ```

  Como un `int` puede contener números más grandes que un `byte`, esta conversión puede suponer la pérdida de parte de la información y **debe ser, en general, evitada**.

> [!warning] Cuidado
> Cuando hagas un _casting_ procura que el tipo de dato al que vas a pasar un dato no sea de menor tamaño que del tipo de dato original, como en el ejemplo anterior.

## 9.3. Operaciones con datos

Como dijimos más atrás, los tipos de datos se caracterizan por la clase de objeto que representan y por las operaciones que se pueden hacer con ellos. Los datos que participan en una operación se llaman **operandos**, y el símbolo de la operación se denomina **operador**. Por ejemplo, en la operación entera 5 + 3, los datos 5 y 3 son los operandos y `+` es el operador.

Podemos clasificar las operaciones básicas con datos en dos grandes grupos:

- **Operaciones aritméticas**
- **Operaciones lógicas**

### 9.3.1. Operaciones aritméticas

Son análogas a las operaciones matemáticas convencionales, aunque cambian los símbolos. Se emplean, en general, con datos de tipo entero o real:

| Operación | Operador |
| :----: | :----: |
| suma | + |
| resta | - |
| multiplicación | * |
| división | / |
| módulo (resto) | % |

Seguramente la operación **módulo (`%`)** es la única que no te suena de nada. Sirve para calcular el resto de la división entera.

Es decir, si divides un número entero entre otro (por ejemplo, 5 entre 2), el cociente será otro número entero (2), y el resto será 1. Pues bien, el operador / te proporciona el cociente, y el operador `%` te proporciona el resto. Es un operador muy útil en una gran diversidad de circunstancias, como verás pronto.

El **tipo del resultado** de cada operación dependerá del tipo de los operandos. Por ejemplo, si sumamos dos números enteros, el resultado será otro número entero. En cambio, si sumamos dos números reales, el resultado será un número real. La suma de un número entero con otro real no está permitida en muchos lenguajes, entre ellos Java, así que intentaremos evitarla.

Aquí tenemos algunos ejemplos de operaciones aritméticas con números enteros y reales:

| Operandos | Operador | Operación | Resultado |
| ---- | :----: | :----: | :----: |
| 35 y 9 (enteros) | + | 35 + 9 | 44 (entero) |
| 35 y 9 (enteros) | - | 35 - 9 | 26 (entero) |
| 35 y 9 (enteros) | * | 35 * 9 | 315 (entero) |
| 35 y 9 (enteros) | / | 35 / 9 | 3 (entero) |
| 35 y 9 (enteros) | % | 35 % 9 | 8 (entero) |
| 8,5 y 6,75 (reales) | + | 8,5 + 6,75 | 15,25 (real) |
| 8,5 y 6,75 (reales) | - | 8,5 - 6,75 | 1,75 (real) |
| 8,5 y 6,75 (reales) | * | 8,5 * 6,75 | 57,375 (real) |
| 8,5 y 6,75 (reales) | / | 8,5 / 6,75 | 1,259 (real) |

Nótese que el operador `–` también se usa para preceder a los números negativos, como en el álgebra convencional.

#### Operadores de incremento y decremento

Hay, además, otros dos operadores aritméticos muy utilizados, y ambos usan un solo operando:

- **Operador incremento: `++`**  
  Se utiliza para aumentar en una unidad el valor de una variable numérica entera. Por ejemplo, `x++` es equivalente a `x = x + 1`.

- **Operador decremento: --**  
  Se utiliza para disminuir en una unidad el valor de una variable numérica entera. La expresión `x--` es equivalente a `x = x – 1`.

Ambos operadores (`++` y `--`) **pueden alterar su comportamiento según su posición**. Es decir, si el incremento o el decremento se ponen antes o después de un valor. De esa forma podemos tener:

- **Pre-incremento**: cuando el operador de incremento se sitúa delante de la variable (`++x`).
  Así se incrementa el valor de una variable en uno y **luego utiliza ese valor incrementado** en la expresión o asignación actual.

  Ejemplo:

  ```java
  int a = 5;
  int b = ++a;
  // b será 6 porque a se incrementa a 6 ANTES de ser asignado a b

  System.out.println("a: " + a); // Imprime: a: 6
  System.out.println("b: " + b); // Imprime: b: 6
  ```

- **Post-incremento**: el operador de incremento va detrás de la variable (x++). En este caso **se usa el valor original antes de incrementarlo**.

  Ejemplo:
  ```java
  int a = 5;
  int b = a++;
  // b será 5 porque a se ASIGNA primero a b y luego se incrementa

  System.out.println("a: " + a); // Imprime: a: 6
  System.out.println("b: " + b); // Imprime: b: 5
  ```

> [!tip] Importante
> Lo mismo ocurre con los operadorer **pre-decremento** y **post-decremento**.

#### Operadores de asignación compuesta

Al igual que los operadores de incremento y decremento, existen otros operadores que permiten ahorrar código para realizarlas. Estos operadores permiten **hacer una operación concreta y después asignar el valor resultante a una variable**. Veamos algunos:

- **Operador asignación con suma: `+=`**  
Una expresión `x+=n` equivale a `x = x + n`. Es decir, suma a `x` el valor `n` y asigna a `x` el resultado.

Si queremos incrementar en un número distinto a 1 (p.e. 3) puedo usa el operador `+=`. Se utiliza para aumentar en `n` unidades el valor de una variable numérica entera. Por ejemplo, `x+=3` es equivalente a `x = x + 3`.
`x+=-3` es lo mismo que `x = x + (-3) = x - 3`.

- **Operador asignación con resta: `-=`**  
Igual que el anterior, pero restando.

Por ejemplo, `x-=3` es equivalente a `x = x - 3`.
`x+=-3` es lo mismo que `x = x - (-3) = x + 3`.

- **Operador asignación con multiplicación: `*=`**  
Donde `x*=3` es equivalente a `x = x * 3`.
`x*=-3` es lo mismo que `x = x * (-3)`.

- **Operador asignación con división: `/=`**  
Adivina...

> [!example] Material de apoyo 
> [[1DAM_Programación/Unidad 01/Referencias#Operadores aritméticos\|1DAM_Programación/Unidad 01/Referencias#Operadores aritméticos]]
> [[1DAM_Programación/Unidad 01/Referencias#JAVA Asignaciones complejas\|1DAM_Programación/Unidad 01/Referencias#JAVA Asignaciones complejas]]


### 9.3.2. Operaciones lógicas (o booleanas)

Estas operaciones sólo pueden dar como resultado **_verdadero_** o **_falso_**, es decir, **su resultado debe ser un valor lógico**.

Hay dos tipos de operadores que se utilizan en estas operaciones: los **operadores de relación** y los **operadores lógicos**.

#### Operadores de relación

Son los siguientes:

| Operación | Operador |
| --- | :---: |
| menor que | < |
| mayor que | > |
| menor o igual que | <= |
| mayor o igual que | >= |
| distinto de | != |

Muchos lenguajes prefieren el símbolo `<>` para "distinto de". En realidad, es un asunto de notación que no tiene mayor importancia.

Los operadores de relación se pueden usar con todos los tipos de datos simples: **entero, real, carácter** o **lógico**. El resultado será **verdadero** si la relación es cierta, o **falso** en caso contrario.

Aquí tienes algunos ejemplos:

| Operandos | Operador | Operación | Resultado |
| --- | :---: | :---: | :---: |
| 35, 9 (enteros) | > | 35 > 9 | verdadero |
| 35, 9 (enteros) | < | 35 < 9 | falso |
| 35, 9 (enteros) | == | 35 == 9 | falso |
| 35, 9 (enteros) | != | 35 != 9 | verdadero |
| 5, 5 (enteros) | < | 5 < 5 | falso |
| 5, 5 (enteros) | <= | 5 <= 5 | verdadero |
| 5, 5 (enteros) | != | 5 != 5 | falso |
| "a", "c" (caracteres) | == | 'a' == 'c' | falso |
| "a", "c" (caracteres) | >= | 'a' >= 'c' | falso |
| "a", "c" (caracteres) | <= | 'a' <= 'c' | verdadero |

En cuanto a los datos lógicos, se considera que "falso" es menor que "verdadero". Por lo tanto:

| Operandos | Operador | Operación | Resultado |
| --- | --- | --- | --- |
| verdadero, falso | > | verdadero > falso | verdadero |
| verdadero, falso | < | verdadero < falso | falso |
| verdadero, falso | == | verdadero == falso | falso |

#### Operadores lógicos.

Los operadores lógicos son `and` (y), `or` (o) y `not` (no). Sólo se pueden emplear con tipos de datos lógicos.

El operador `and`, que también podemos llamar y, se escribe en Java como `&&`, y da como resultado verdadero sólo si los dos operandos son verdaderos:

| Operandos | Operador | Operación | Resultado |
| --- | :---: | :---: | :---: |
| verdadero, falso | && | verdadero && falso | falso |
| falso, verdadero | && | falso && verdadero | falso |
| verdadero, verdadero | && | verdadero && verdadero | verdadero |
| falso, falso | && | falso && falso | falso |

El operador or (también nos vale o) da como resultado verdadero cuando al menos uno de los dos operandos es verdadero. En Java se escribe ||

| Operandos | Operador | Operación | Resultado |
| --- | :---: | :---: | :---: |
| verdadero, falso | \|\| | verdadero \|\| falso | verdadero |
| falso, verdadero | \|\| | falso \|\| verdadero | verdadero |
| verdadero, verdadero | \|\| | verdadero \|\| verdadero | verdadero |
| falso, falso | \|\| | falso \|\| falso | falso |

El operador **not** (o no), que se escribe `!`, es uno de los escasos operadores que sólo afectan a un operando (operador monario), no a dos (operador binario). El resultado es la negación del valor del operando, es decir, que le cambia el valor de verdadero a falso y viceversa:

| Operandos | Operador | Operación | Resultado |
| --- | :---: | :---: | :---: |
| verdadero | ! | ! verdadero | falso |
| falso | ! | ! falso | verdadero |

> [!example] Material de apoyo 
> * [[1DAM_Programación/Unidad 01/Referencias#Operadores lógicos\|1DAM_Programación/Unidad 01/Referencias#Operadores lógicos]]
> * [[1DAM_Programación/Unidad 01/Referencias#Operadores relaciones\|1DAM_Programación/Unidad 01/Referencias#Operadores relaciones]]
> * [[1DAM_Programación/Unidad 01/Referencias#JAVA Operadores lógicos\|1DAM_Programación/Unidad 01/Referencias#JAVA Operadores lógicos]]
> * [[1DAM_Programación/Unidad 01/Referencias#JAVA Operadores relaciones\|1DAM_Programación/Unidad 01/Referencias#JAVA Operadores relaciones]]


### 9.3.3. Otros operadores

Existen otros operadores que se usan en circunstancias más minoritarias, tales como el operador lógico **`XOR`** (`^`), el operador **complemento a 1** (`~`) o los operadores que trabajan a nivel de bits. Aunque tienen su indudable utilidad, no son imprescindibles en un curso de introducción a la programación y solo se verán en los casos en los que se revelen necesarios. El lector interesado puede encontrar abundantes referencias en Internet sobre este asunto.

#### Operador XOR

En cualquier caso, es posible que le encontremos algunas utilidades al operador `^`. El **`XOR`** (`^`) es un operador lógico. Devuelve `true` si y solo si los operandos son diferentes. En caso contrario, si ambos son iguales, devuelve `false`.

Supongamos que estamos implementando un programa que compruebe la elección del usuario para decidir qué método de pago quiere usar: con tarjeta o con efectivo. Crearemos dos variables para esos métodos de pago que representarán el método que el usuario ha elegido. Obviamente, solo puede escoger una de las dos formas de pago:

```java
public class Main {
    public static void main(String[] args) {
        boolean tieneEfectivo = true;
        boolean tieneTarjeta = true;

        // Queremos usar solo un método de pago, no ambos ni ninguno
        boolean pagoValido = tieneEfectivo ^ tieneTarjeta;

        System.out.println("¿Pago válido?: " + pagoValido);
        // Imprime: false (porque tiene ambos)
    }
}
```

Juega con el código anterior y cambia los valores de las variables. Verás que si el usuario elige solo una de las dos (una a `true` y otra a `false`) el pago si será válido.

Dicho de otra forma, con `^` nos aseguramos de que las dos condiciones o expresiones lógicas que evalúa sean **distintas**.

### 9.3.4. Prioridad de los operadores

Es habitual encontrar **varias operaciones** juntas en una misma línea. En estos casos es **imprescindible** conocer la **prioridad** de los operadores, porque las operaciones se calcularán en el orden de prioridad y el resultado puede ser muy distinto del esperado. Por ejemplo, en la operación `6 + 4 / 2`, no es lo mismo calcular primero la operación `6 + 4` que calcular primero la operación `4 / 2`.

La prioridad de cálculo respeta las reglas generales del álgebra. Así, por ejemplo, la división y la multiplicación tienen más prioridad que la suma o la resta. Pero el resto de prioridades pueden diferir de manera importante de un lenguaje de programación a otro. Como nosotros vamos a usar C, emplearemos las prioridades de C, que son las siguientes:

<table>
<tr>
<td>Operador</td>
<td>Prioridad</td>
</tr>
<tr>
<td>!  --  ++</td>
<td>máxima prioridad</td>
</tr>
<tr>
<td>*  /  %</td>
<td></td>
</tr>
<tr>
<td>+  -</td>
<td></td>
</tr>
<tr>
<td><  <=  >  >=</td>
<td></td>
</tr>
<tr>
<td>!=  ==</td>
<td></td>
</tr>
<tr>
<td>&&</td>
<td></td>
</tr>
<tr>
<td>||</td>
<td></td>
</tr>
<tr>
<td>=</td>
<td>mínima prioridad</td>
</tr>
</table>

La prioridad del cálculo se puede alterar usando **paréntesis**, como en álgebra. Los paréntesis se pueden anidar tantos niveles como sean necesarios. Por supuesto, a igualdad de prioridad entre dos operadores, la operación se calcula **de izquierda a derecha**, en el sentido de la lectura de los operandos.

En general, **es una excelente idea hacer explícita la prioridad mediante paréntesis** y no dejarla a merced de los deseos del lenguaje.

Aquí tenemos algunos ejemplos de operaciones conjuntas y su resultado según el orden de prioridad que hemos visto:

| Operación | Resultado |
| :---: | :---: |
| 6 + 4 / 2 | 8 |
| (6 + 4) / 2 | 5 |
| (33 + 3 * 4) / 5 | 9 |
| 2 ^ 2 * 3 | 12 |
| 3 + 2 * (18 – 4 ^ 2) | 7 |
| 5 + 3 < 2 + 9 | verdadero |
| 2 + 3 < 2 + 4 y 7 > 5 | verdadero |
| "A" > "Z" o 4 / 2 + 4 > 6 | falso |
| "A" > "Z" o 4 / (2 + 2) <= 6 | verdadero |

> [!example] Material de apoyo 
> [[1DAM_Programación/Unidad 01/Referencias#JAVA Precedencia de operadores\|1DAM_Programación/Unidad 01/Referencias#JAVA Precedencia de operadores]]

### 9.3.5. ¿Y las operaciones más complejas?

Además de todas estas operaciones aritméticas, lógicas y relacionales, los lenguajes de programación disponen de mecanismos para realizar operaciones más complejas con los datos, como, por ejemplo, calcular raíces cuadradas, logaritmos, senos, cosenos, redondeo de números reales, etc.

Todas estas operaciones (y muchas más) se realizan a través de objetos predefinidos de la biblioteca de clases de Java. Una de ellas es la clase `Math`, que integra un conjunto de datos y funciones matemáticas que realizan operaciones completas y ofrecen datos estandarizados (como el valor de la constante **Pi**).

Cuando llegue el momento, ya veremos con más detalle esta y otras clases de esa biblioteca y cómo se usan. Incluso aprenderemos a hacer las nuestras. Por ahora nos basta saber que algunas de ellas sirven para hacer cálculos más complejos que una simple suma o una división.

La ejecución de los métodos de la clase `Math` requiere que se le pasen los parámetros necesarios para que haga sus cálculos, y nos devuelva el resultado.

Algunos de esos métodos son:

| Operación | Resultado |
| --- | :---: |
| `Math.abs(-5)` | 5 |
| `Math.abs(6)` | 6 |
| `Math.round(5.7)` | 6 |
| `Math.round(5.2)` | 5 |
| `Math.pow(2, 6)` | 64 |
| `Math.sqrt(64)` | 8 |

> [!info]  
> Esta clase se citará más adelante, en [[1DAM_Programación/Unidad 03/3. Ejemplos de la API - Math y String#3.2. La clase `Math`\|unidades posteriores]].

## 9.4. Constantes y variables

Se define un **dato constante** (o, simplemente, "una constante") como un dato de un programa cuyo valor no cambia durante la ejecución. Por el contrario, un **dato variable** (o, simplemente, "una variable") es un dato cuyo valor sí cambia en el transcurso del programa.

### 9.4.1. Identificadores

A los datos variables se les asigna un identificador alfanumérico, es decir, un nombre. Por lo tanto, es necesario distinguir entre el **identificador** de una variable y su **valor**. Por ejemplo, una variable llamada `x` puede contener el valor 5. En este caso, `x` es el identificador y 5 el valor de la variable.

Los identificadores o nombres de variable deben cumplir ciertas reglas que, aunque varían de un lenguaje a otro, podemos resumir en que:

- **Deben empezar por una letra** y, en general, no contener símbolos especiales excepto el subrayado ("`_`")

- **No deben coincidir con alguna palabra reservada** del lenguaje, tales como `class` o `function`.

| Identificador | ¿Es válido?                                   |
| :-----------: | --------------------------------------------- |
|       `x`     | Sí                                            |
|      `5x`     | No, porque no empieza por una letra           |
|      `x5`     | Sí                                            |
|     `pepe`    | Sí                                            |
|     `_pepe`   | No, porque no empieza por una letra           |
|   `pepe_luis` | Sí                                            |
|   `pepe!luis` | No, porque contiene caracteres especiales (!) |
|     `raiz`    | No, porque coincide con la función raiz(x)    |

Las **constantes** también deben tener un identificador. Por cuestión de estilo, en Java los identificadores de las constantes se escriben en MAYÚSCULA, y, los de las variables, en minúscula. Pero solo es una regla de estilo: conveniente, pero no imprescindible. En cada organización pueden tener sus propias reglas.

### 9.4.2. Declaración y asignación

#### Variables

Las variables, si son simples, tienen que ser de un **tipo de datos determinado**, es decir, debemos indicar explícitamente qué tipo de datos va a almacenar a lo largo del programa. Y, si son complejas, deben ser instancias de una clase concreta, aunque esto ya lo explicaremos más adelante. 

Por ahora, recuerda esto: es imprescindible indicar cuál va a ser el identificador de la variable, y qué tipo de datos va a almacenar. A esto se le llama **declarar la variable**. 

Una **declaración de variables** en Java será algo así:

```java
int x;
double y;
char z;
```

x, y, z son los identificadores de variable. Es necesario declararlas porque, como vimos, el ordenador maneja internamente cada variable de una forma diferente: en efecto, no es lo mismo una variable entera de 8 bits sin signo que otra real en coma flotante de 64 bits. El ordenador debe saber de antemano qué variables va a usar el programa y de qué tipo son para poder asignarles la memoria necesaria. 

Para adjudicar un valor a una variable, se emplea una sentencia de **asignación**, que tienen esta forma:

```java
x = 5;
y = 7.445;
z = 'J';
```

A partir de la asignación, pueden hacerse operaciones con las variables exactamente igual que se harían con datos. Por ejemplo, la operación `x + x` daría como resultado 10. A lo largo del programa, la misma variable x puede contener otros valores (siempre de tipo entero) y utilizarse para otras operaciones. Por ejemplo:

```java
int x;
int y;
int z;
x = 8;
y = 2;
z = x / y;
x = 5;
y = x + z;
```

Después de esta serie de operaciones, realizadas de arriba a abajo, la variable `x` contendrá el valor 5, la variable y contendrá el valor 9 y, la variable z, el valor 4. 

También se puede declarar una variable e inicializarla (asignarle un valor inicial) en la misma línea de código:

```java
int x = 8;
int y = 2;
int z = x / y;
```

A partir de Java 10 podemos hacer estas declaraciones usando el tipo var para declarar variables:

```java
var x = 8;
var y = 2;
var z = x / y;
```

En estos casos, Java **infiere** el tipo de dato de la variable. Es decir, deduce qué tipo de dato es gracias al valor que se le asigna. Para que haga esa inferencia de tipo, la variable debe inicializarse en la declaración:

```java
var x;    // Error! No se puede usar var porque no sabe qué tipo debe inferir 
x = 8;
```

> [!warning] Importante
> El uso de `var` tiene ciertas restricciones y condiciones concretas de uso que se irán viendo a lo largo de las siguientes unidades.

#### Constantes

En cambio, **las constantes son valores que nunca cambian**. Sólo se les puede **asignar valor una vez**, ya que, por su propia naturaleza, son invariables a lo largo del programa. 

En Java, una constante se distingue con el modificador **`final`** colocado antes de la declaración, y la asignación debe hacerse en ese mismo momento. Por ejemplo:

```java
final double PI = 3.141592;
```

### 9.4.3. El modificador `static`

En la declaración de una variable o una constante aparece a menudo la palabra `static`. Por ejemplo:

```java
static int x; 
final static double PI = 3.141592;
```

El modificador `static` significa que esa variable o constante **sólo se creará una vez en toda la ejecución del programa**, aunque aparezcan declaradas varias veces. También es aplicable, como veremos, a métodos, y resulta muy conveniente en una enorme diversidad de situaciones. 

### 9.4.4. Vida y ámbito de las variables

Las variables en Java son, por definición, todas **locales al bloque** en el que se han declarado, entendiendo por bloque a cualquier conjunto de instrucciones enmarcado entre una llave de apertura `{` y otra llave de cierre `}`

Esto quiere decir que la variable sólo existirá dentro del bloque y se destruirá cuando el bloque finalice, resultando inaccesible al resto del código. Estas variables **no pueden ser declaradas como `static`**.

En cambio, las variables miembros de una clase son accesibles en todo el código de la clase, y sí pueden ser declaradas como static.

Veámoslo con un ejemplo:

```java
class Prueba
{
    static int n = 50; // Variable miembro de la clase

    public static void main(String[] args) 
    {
        // Variables locales. No pueden ser static.
        int m = 5, r = 0;
        r = n * m;
        System.out.println("El resultado es: " + r); 
    }

    public void otro_metodo()
    {
        int x = 2, r = 0;	// Variables locales
        r = n + x + m;	// ¡Esta asignación fallará!
        System.out.println("El resultado es: " + r);
    }
}
```

La variable **n** es miembro de la clase, por lo que puede ser usada dentro del bloque del método `main()` o en el de `otro_metodo()` sin problema. 

Sin embargo, las variables locales `m` o `r` no pueden ser usadas fuera de su ámbito. Por eso fallará la asignación `r = n + x + m` de `otro_metodo()`: la variable `m` es local al método `main()`, y no puede ser accedida desde `otro_metodo()`.

En cambio, sí puede usarse la variable `r` en `otro_metodo()`, pero no es la misma variable que en `main()`, sino otra diferente: observa que se declara `r` como variable local en `otro_metodo()`. El hecho de que tenga el mismo nombre que la variable `r` de `main()` no significa que sean la misma variable, sino que hemos reutilizado el nombre del identificador.  

### 9.4.5. Expresiones

Una **expresión** es una combinación de constantes, variables, operadores, métodos y expresiones literales, tales como 5 o 28.33. Es decir, se trata de operaciones aritméticas o lógicas en las que se pueden combinar todos los elementos vistos hasta ahora, y que resultan evaluables por la máquina para **proporcionar un resultado único**.

Por ejemplo: 

```java
(5 + x) / 2
```

En esta expresión, aparecen dos constantes literales (5 y 2), una variable (x) y dos operadores (+ y /), además de los paréntesis, que sirven para alterar la prioridad de las operaciones. Lógicamente, para resolver la expresión, es decir, para averiguar su resultado, debemos conocer cuál es el valor de la variable x. Supongamos que la variable x tiene el valor 7. Entonces, el resultado de la expresión es 6. El cálculo del resultado de una expresión se suele denominar **evaluación de la expresión**. 

Otro ejemplo más complejo:

```java
(–b + Math.sqrt(Math.pow(b, 2) – 4 * a * c)) / (2 * a)
```

Esta expresión tiene tres variables (a, b y c), 3 operadores (–, + y \*, aunque algunos aparecen varias veces), 2 constantes literales (2 y 4, apareciendo el 2 dos veces) y dos métodos (`sqrt` y `pow`, que calculan la raíz cuadrada y la potencia respectivamente). Si el valor de las variables fuera `a = 2`, `c = 3` y `b = 4`, al evaluar la expresión el resultado sería `–0.5`

**La forma más habitual** de encontrar una expresión es **combinada con una sentencia de asignación** a una variable. Por ejemplo:

```java
y = (5 + x) / 2;
```

En estos casos, la expresión (lo que hay a la derecha del signo `=`) se evalúa y su resultado es asignado a la variable situada a la izquierda del `=`. En el ejemplo anterior, asumiendo que la variable `x` vale 7, la expresión `(5 + x) / 2` tendría el valor 6, y, por lo tanto, ese es el valor que se asignará a la variable `y`.


[^1]: En honor a [George Boole](https://es.wikipedia.org/wiki/George_Boole) (1815-1864), matemático británico que desarrolló una rama del álgebra llamada lógica o de Boole.


# 10. Apéndice. Entrada y salida por consola

Aunque no tiene una relación directa con los asuntos tratados en esta unidad, vamos a terminar mencionando la **entrada de datos por teclado y la salida de datos por consola**, porque son imprescindibles para realizar cualquier programa que empiece a hacer cosas interesantes.

Ambos dispositivos se manejan mediante la **clase System**. Esta clase está en el paquete `java.lang`, que se carga automáticamente en todas las aplicaciones Java, sin necesidad de hacer `import` (en el ejemplo de la sección anterior, por lo tanto, hicimos un poco de trampa al ejecutar `import java.lang.System`) 

La clase `System` contiene dos objetos `static` que se crean automáticamente al ejecutar cualquier programa Java, y que se destruyen ellos solitos al terminar. Estos objetos son: 

* **`System.out`**: para manejar la salida estándar (consola) 
* **`System.in`**: para manejar la entrada estándar (teclado) 
* **`System.err`**: para manejar la salida de errores. No la usaremos de momento. 

## 10.1. Salida por consola

La salida a través del objeto `System.out` y, en concreto, del método `System.out.println()`, ya la has visto en multitud de ejemplos.

## 10.2. Entrada desde teclado

Podemos hacer que nuestro código admita datos del usuario. En este punto esos datos se introducirán por consola desde el teclado.

Observa el siguiente código (y no desesperes):

```java
char c;  
try {  
    c = (char) System.in.read();   
} catch (Excepcion e) {   
    e.printStackTrace();   
}
```

😭 ¡Uff! A menudo se dice que Java no es un lenguaje adecuado para aprender a programar, y esta es una de las ocasiones en las que uno piensa que es completamente cierto. Es arduo explicar a un principiante qué demonios pone ahí. Digamos que Java tiene una obsesión un pelín delirante por la seguridad, y que ese mamotreto que ves ahí arriba es un reflejo de ello. 

Ese trozo de código sirve para leer un carácter, un simple carácter, por el teclado, y almacenarlo en la variable `c`. Todo ello se envuelve en un bloque try-catch de manejo de excepciones, de forma que si ocurre algo inesperado (como que el usuario teclea veinte caracteres en lugar de uno, o que haya pulsado CTRL-C, o que la CPU haya explotado, o vaya usted a saber qué), el programa es capaz de detectarlo y reaccionar adecuadamente. 

**No te agobies ahora por los detalles** 💪. Recuerda que, para hacer una entrada por teclado, necesitas copiar y pegar el código de más arriba, y adaptarlo a tus variables. Ya volveremos más adelante, cuando estemos preparados, sobre el manejo de excepciones y el bloque `try-catch`. 

Si lo que quieres es algo más versátil, como **leer una cadena de caracteres completa** desde el teclado, existen un par de métodos.  

### Método 1: `console()`

```java
String dato = System.console().readLine();
```

Sencillo, ¿verdad? La variable `dato` contiene el valor que el usuario haya introducido por teclado. Y, teniendo ya dicho valor, podemos operar con él.

Un ejemplo un poco más completo para que puedas ver la entrada por teclado en acción:

```java
System.out.println("Por favor, teclea tu nombre: ");  
String nombre = System.console().readLine();  
System.out.println("Ahora teclea tu edad: ");  
int edad = Integer.parseInt(System.console().readLine());  
System.out.println("Hola, " + nombre + ", tienes " + edad + " años");
```

Sí, lo has adivinado: **`Integer.parseInt()`** convierte a `int` una cadena de caracteres, porque todo lo que se recibe desde el teclado es procesado como cadena. Así que hemos de convertirlo antes de usarlo. Teóricamente, la conversión puede fallar y debería estar dentro de un bloque `try-catch`, pero esa... esa es otra historia.

La mala noticia es que `console().readLine()` podría fallar en algunas consolas. Para hacer un código totalmente fiable, necesitas recurrir a otros métodos. Veámoslos.

### Método 2: `BufferedReader`

```java
InputStreamReader isr = new InputStreamReader(System.in);  
BufferedReader buff = new BufferedReader(isr);  
String dato = buff.readLine();
```

Pero... el anterior era más sencillo, ¿no? Dónde va a parar. ¿Por qué tanto lío para leer unos cuantos caracteres del teclado? Bien, la biblioteca de clases de Java está diseñada para ser muy robusta y versátil, y eso hace que haya que pagar algún pequeño precio en cuanto a usabilidad y legibilidad en ocasiones. 

La forma ortodoxa de hacer la entrada de datos con Java es esta segunda: crear un objeto `Reader` para leer los caracteres de la entrada estándar. Es mucho más seguro y funcionará en cualquier circunstancia, pero requiere varios esfuerzos adicionales:

* Hay que importar el paquete [java.io.\*](https://docs.oracle.com/javase/8/docs/api/java/io/package-summary.html).
* Hay que encerrar obligatoriamente las instrucciones de lectura en un bloque `try-catch`.
* Y, como has visto, hay que escribir mucho más código 

Si tenemos en cuenta que el método anterior puede fallar y queremos rehacer el mismo ejemplo, quedaría más o menos así (observa cómo hemos resumido en una línea la creación de los objetos `InputStreamReader` y `BufferedReader`):

```java
import java.io.*;  
...  
    BufferedReader buff =
        new BufferedReader(new InputStreamReader([System.in](System.in)));  
    try {  
        String nombre = buff.readLine();  
    }  
        catch (Exception e) {  
        e.printStackTrace();  
    }  
    System.out.println("Ahora teclea tu edad: ");  
    int edad = Integer.parseInt(buff.readLine());  
    System.out.println("Hola, " + nombre + ", tienes " + edad + " años");
```

### ⭐ Método 3: `Scanner`

```java
import java.util.Scanner; // 1. Importamos la herramienta

public class EjemploScanner {
    public static void main(String[]String[] args) {
        // 2. Creamos el objeto Scanner para leer desde el teclado
        Scanner teclado = new Scanner(System.in);

        // 3. Pedir y leer un texto (String)
        System.out.print("Introduce el nombre del producto: ");
        String producto = teclado.nextLine();

        // 4. Pedir y leer un número decimal (double)
        System.out.print("Introduce el precio de " + producto + ": ");
        double precio = teclado.nextDouble();

        // 5. Pedir y leer un número entero (int)
        System.out.print("¿Cuántas unidades vas a llevar?: ");
        int cantidad = teclado.nextInt();

        // 6. Procesar los datos de la entrada
        double total = precio * cantidad;

        // 7. Mostrar el resultado final
        System.out.println("\n--- TICKET DE COMPRA ---");
        System.out.println("Producto: " + producto);
        System.out.println("Total a pagar: $" + total);

        // 8. Cerrar el scanner (buena práctica)
        teclado.close();
    }
}
```

Este va a ser, por ahora, el **método ganador**. El que vamos a usar hasta nuevo aviso.

En este caso:

* Hay que importar el paquete [**java.util.Scanner**](https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html).
* En esta ocasión no es necesario encerrar las instrucciones de lectura en un bloque `try-catch`.
* Es **EXTREMADAMENTE RECOMENDABLE** (si no obligatorio) **cerrar** el objeto con un **`.close()`**. Ya veremos el porqué más adelante.
* `Scanner` ofrece formas de leer datos según el tipo:  
   * **`.nextLine()`** lee toda la línea de texto hasta presionar `Enter`. 
   * **`.nextInt()`** lee un número entero. 
   * **`.nextDouble()`** lee un número con decimales. 

Existen otras funcionalidades como las siguientes, que se verán más adelante:
* **`.next()`** lee una palabra (hasta encontrar un espacio). 
* **`.hasNextInt()`** comprueba si el siguiente dato es un número entero. 

> [!warning] Recuerda
> Para hacer entrada por teclado, por el momento las instrucciones son: copia, pega y adapta.

---

<p><span>🏠 <strong>Unidad:</strong> <a data-tooltip-position="top" aria-label="1DAM_Programación/Unidades/Unidad 1 - Introducción a la programación con Java.md" data-href="1DAM_Programación/Unidades/Unidad 1 - Introducción a la programación con Java.md" href="1DAM_Programación/Unidades/Unidad 1 - Introducción a la programación con Java.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 1 - Introducción a la programación con Java</a></span></p>


# Referencias - Material de refuerzo

> [!info]  
> Todos estos vídeos se han extraído de las playlists:
> * [**MEGA Curso JAVA desde 0 [ DAM - DAW ]**](https://www.youtube.com/playlist?list=PLG1qdjD__qH6ULjW5iN8E45m5nkaCNbUu) de [**Aula en la nube**](https://www.youtube.com/@aulaenlanube).
> * [**Programación Java**](https://youtube.com/playlist?list=PLP5w4RviLcV2xUnpafRiDJQvkSlkATClO&si=Inift60wj4sFnEuQ) de [**Aula informática**](https://www.youtube.com/@aulainformatica2118)

## Pseudocódigo

* Aula en la nube. (2022, 19 septiembre). _Introducción a la programación y los algoritmos  ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=dfEEG4A_Hoo

* Aula en la nube. (2022r, octubre 14). _JAVA: Operadores matemáticos ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=4NIgC5ArKTI

* Aula en la nube. (2022c, septiembre 20). _Introducción a la programación: **operadores relaciones** ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=98m39gc3YpM

* Aula en la nube. (2022e, septiembre 21). _Introducción a la programación: operadores lógicos ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=GwwRkMo012Y

* Aula en la nube. (2022b, septiembre 19). _Representación de algoritmos  ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=b003s0CJ2KU

* Aula en la nube. (2022c, septiembre 20). _Variables y expresiones aritméticas ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=pgF8U9WxPts

* Aula en la nube. (3 de octubre de 2021). _1.6 Instrucciones en pseudocódigo_ [Vídeo]. YouTube. https://youtu.be/taSJeALBVGk?si=TRiD-30p3-KXCVuw

## Java

* Aula Informática. (2022b, marzo 28). _Programación Java - Introducción_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=1-fNqKf-8WE

* Aula en la nube. (2022f, octubre 2). _Introducción a JAVA ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=8gkaitxt-CI

* Aula en la nube. (2022g, octubre 3). _JAVA: Preparando el entorno (JRE, JDK y VS Code)  ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=Q_2j8aYnmYk

* Aula en la nube. (2022h, octubre 4). _Hola Mundo en JAVA  ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=AVEU8AEZ5YE

* Aula en la nube. (2022i, octubre 5). _JAVA: Salida por pantalla ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=QRDePHN91UY

* Aula en la nube. (2022aa, octubre 20). _JAVA: Entrada de datos - Clase Scanner  ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=HSq3rRfBmDg

* Aula en la nube. (2022j, octubre 6). _JAVA: Tipos de variables ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=dy1qD-jwcIs

* Aula Informática. (2022d, marzo 28). _Programación Java - Variables y Tipos_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=PpkIVxLtZdg

* Aula en la nube. (2022k, octubre 7). _JAVA: Declarar variables numéricas ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=9OpBxj5kYss

* Aula en la nube. (2022z, octubre 20). _JAVA: Decimales y precisión ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=noQbTZdYYZo

* Aula en la nube. (2022l, octubre 9). _JAVA: El sistema hexadecimal ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=9P8M1V0XnVo

* Aula en la nube. (2022m, octubre 10). _JAVA: Char y boolean + ASCII + UNICODE  ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=mAi5o9rsJS4

* Aula en la nube. (2022n, octubre 11). _Strings en JAVA  ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=EAEVn9JKP9Q

* Aula en la nube. (2022q, octubre 13). _JAVA: Secuencias de escape ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=p7p9f7wKd9Y

* Aula en la nube. (2022t, octubre 16). _JAVA: Operadores relacionales ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=nJUURIe3Nc0

* Aula en la nube. (2022v, octubre 17). _JAVA: Operadores lógicos ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=Z06XfYcrDN4

* Aula en la nube. (2022t, octubre 15). _JAVA: Asignaciones complejas ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=DIbhR5cdtL0

* Aula en la nube. (2022w, octubre 18). _JAVA: Precedencia de operadores ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=_GJldn1wQvw

* Aula en la nube. (2022x, octubre 19). _JAVA: Clase Math ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=4znSjME7tNU

* Aula en la nube. (2022y, octubre 19). _JAVA: Funciones matemáticas ☕ DAM - DAW_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=jKs6kq6z1sI

