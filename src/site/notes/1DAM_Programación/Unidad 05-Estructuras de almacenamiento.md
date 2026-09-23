---
{"dg-publish":true,"permalink":"/1-dam-programacion/unidad-05-estructuras-de-almacenamiento/","dg-note-properties":{"unidad":"[[1DAM_Programación/Unidades/Unidad 5 - Estructuras de almacenamiento]]","modulo":"[[Módulos/Programación]]","libro":"[[Apuntes/Programación (1º DAM, 1º DAW)]]"}}
---


```table-of-contents
```

---


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/1-dam-programacion/unidades/unidad-5-estructuras-de-almacenamiento/#datos-de-la-unidad" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## Datos de la unidad

La siguiente tabla muestra los contenidos básicos de la norma educativa que contempla esta unidad, al igual que el objetivo o RA que se quiere alcanzar y los criterios de evaluación que se seguirán para ello.

### Contenidos básicos

Aplicación de las estructuras de almacenamiento:  
- Estructuras. Definición y uso.  
- Concepto de Array. Tipos. Creación de arrays. Recorrido y búsquedas en un array.  
- Arrays multidimensionales.  
- Cadenas de caracteres. Uso de las cadenas. Recorrido y manipulación.  
- Uso de expresiones regulares en cadenas de texto.  
- Concepto de Lista. Tipos. Operaciones.  
- Aplicación del estándar XML.  
- Concepto de XML Estructura de un documento XML.  
- Especificación de documentos. DTD y XSD.  
- Clases para la creación y manipulación de documentos XML.

### RA asociado y criterios de evaluación

**RA 6. Escribe programas que manipulen información seleccionando y utilizando tipos avanzados de datos.**

Criterios de evaluación para el RA:
a) Se han escrito programas que utilicen matrices (arrays).
b) Se han reconocido las librerías de clases relacionadas con tipos de datos avanzados.
c) Se han utilizado listas para almacenar y procesar información.
d) Se han utilizado iteradores para recorrer los elementos de las listas.
e) Se han reconocido las características y ventajas de cada una de las colecciones de datos disponibles.
f) Se han creado clases y métodos genéricos.
g) Se han utilizado expresiones regulares en la búsqueda de patrones en cadenas de texto.
h) Se han identificado las clases relacionadas con el tratamiento de documentos escritos en diferentes lenguajes de intercambio de datos.
i) Se han realizado programas que realicen manipulaciones sobre documentos escritos en diferentes lenguajes de intercambio de datos.
j) Se han utilizado operaciones agregadas para el manejo de información almacenada en colecciones.

---

Llegamos a una de las unidades más relevantes de este curso: las estructuras de datos.

Cualquier programa del mundo real no se hace solo con variables sencillas que contienen números, textos u otros objetos. Se hace manejando **grandes cantidades de esos datos**.

Si hemos de crear una aplicación para gestionar al alumnado de un instituto, por ejemplo, que tiene unos 2000 estudiantes, ¿tendríamos que crear 2000 variables, una para cada objeto `Estudiante`? A todas luces es **inviable**.

En el mundo real creamos una variable que contenga un banco de datos, un conjunto de esos objetos `Estudiante` y que nos permita gestionarlos (leerlos, borrarlos o cambiarlos). Ese "banco de datos" se conoce como **estructura de datos**, y en esta unidad veremos las más relevantes.

---

</div></div>


---

# 1. Estructuras de almacenamiento

Hasta ahora hemos trabajado con los tipos primitivos de Java (enteros, reales, caracteres y lógicos) y con clases más o menos complejas creadas por nosotros o utilizadas a partir de la librería de clases del <abbr title="Java Development Kit">JDK</abbr>. 

Sin embargo, en los programas reales esto no suele ser suficiente, sino que es necesario recurrir a determinadas estructuras compuestas por varios datos primitivos. A estas estructuras las llamamos estructuras de almacenamiento o estructuras de datos. 

En los lenguajes de programación clásicos, las estructuras de datos eran tipos primitivos especiales establecidos por el lenguaje, o bien tipos definidos por el programador. En los lenguajes orientados a objetos, todas las viejas estructuras de datos se han reconvertido en clases de la jerarquía de clases de las que podemos instanciar los objetos que necesitemos. 

Las estructuras de almacenamiento pueden ser de dos tipos: 

* **Estáticas**: son aquéllas que ocupan un espacio determinado en la memoria del ordenador. Este espacio es **invariable** y lo especifica el programador durante la escritura del código fuente. 

* **Dinámicas**: sin aquéllas cuyo espacio ocupado en la memoria **puede modificarse durante la ejecución** del programa. 

Además, se pueden mencionar como una clase de estructura de almacenamiento diferente las estructuras externas, entendiendo como tales aquéllas que no se almacenan en la memoria principal (RAM) del ordenador, sino en alguna memoria secundaria (típicamente, un disco duro). Las estructuras externas, que suelen organizarse en archivos o ficheros, son en realidad estructuras dinámicas almacenadas en memoria secundaria. De los ficheros hablaremos en un tema posterior. 


# 2. Arrays unidimensionales (vectores)

Un array[^1] es una agrupación de **muchos datos individuales del mismo tipo bajo el mismo nombre**. Cada dato individual de un array es accesible mediante un **índice**. 

El caso más simple de array es el **array unidimensional**, también llamado **array**. El array es, sin duda, el rey de las estructuras de almacenamiento.

Por ejemplo, un array de números enteros es una colección de muchos números enteros a los que les adjudicamos un único identificador. 

## 2.1. Declaración

La declaración de un array en Java se puede hacer de dos modos:

```java
tipo_base nombre_array[];  
tipo_base[] nombre_array;
```

Por ejemplo:

```java
int serie[];  
int[] serie;
```

La variable serie será un array que contendrá números enteros. Todos los números recibirán el mismo nombre, es decir, serie. Observa que aún no hemos especificado cuántos elementos contendrá el array. 

Java trata a los arrays unidimensionales como **objetos**. Por lo tanto, para crear el array se usará esta expresión:

```java
serie = new int[5];
```

A partir de ahora, serie será un array de 5 números enteros. Se puede acceder a cada uno de los números que forman el array escribiendo a continuación del nombre un número entre corchetes. Ese número se denomina **índice**. Observa el siguiente ejemplo:

```java
int serie[];  
serie = new int[5];  
serie[2] = 20;  
serie[3] = 15;  
serie[4] = serie[2] + serie[3];  
System.out.println(serie[4]);
```

El array serie puede almacenar hasta 5 números enteros. En su posición 2 se almacena el número 20, y en su posición 3, el 15. Luego se suman ambos valores, y el resultado se almacena en la posición 4. Finalmente, se imprime en la pantalla el resultado de la suma, es decir, 35. 

Es muy útil representar los arrays unidimensionales de forma gráfica para entenderlos mejor. El array serie del ejemplo anterior se puede representar así:

![ud05_array_01.png](/img/user/adjuntos/1DAM_Programacion/Unidad_05/ud05_array_01.png)

Observa algo muy importante: **el primer elemento del array tiene el índice 0**, es decir, el primer elemento es `serie[0]`. Como este array tiene 5 elementos, el último será `serie[4]`, no `serie[5]`. Observa también que los elementos 0 y 1 no han sido utilizados y, por lo tanto, tienen un valor desconocido, exactamente lo mismo que ocurre con cualquier variable de tipo simple que no se inicialice. 

**Java realiza una comprobación en tiempo de ejecución de los índices** de los arrays, por lo que, si intentas usar un índice fuera del rango válido (por ejemplo, `serie[7]`), se producirá un error de ejecución. 

Como es lógico, se pueden construir arrays unidimensionales cuyos elementos sean de cualquier otro tipo primitivo, como `byte` o `double`, con la única restricción de que **todos los elementos sean del mismo tipo**. Los **arrays unidimensionales de caracteres** se denominan **cadenas** de caracteres, y por sus especiales características los estudiaremos en un epígrafe posterior. 

Y, por supuesto, pueden construirse arrays unidimensionales cuyos elementos sean objetos complejos, o incluso otros arrays unidimensionales. De todo esto iremos hablando en las siguientes secciones.

## 2.2. Operaciones con arrays unidimensionales

### 2.2.1. Manipulación de elementos individuales

Los arrays unidimensionales en Java pueden manipularse **elemento a elemento**. No se pueden modificar todos los elementos a la vez. 

Para **asignar valores** a los elementos de un array, por lo tanto, el mecanismo es este:

```java
int[] serie = new int[5];  
serie[0] = 5;  
serie[1] = 3;  
serie[2] = 7;  
// ...etc...
```

La inicialización de los valores de un array también puede hacerse conjuntamente **en el momento de declararlo**, así:

```java
int serie[] = {5, 3, 7, 9, 14};
```

El resultado de esta declaración será un array de 5 elementos de tipo entero a los que se les asigna estos valores:

![ud05_array_02.png](/img/user/adjuntos/1DAM_Programacion/Unidad_05/ud05_array_02.png)

Cada elemento del array es, a todos los efectos, una variable que puede **usarse independientemente** de los demás elementos. Así, por ejemplo, un elemento del array serie puede usarse en una instrucción de **salida** igual que cualquier variable simple de tipo int:

```java
int serie[] = new int[5];  
serie[0] = 21;  
System.out.println(serie[0]);
```

Del mismo modo, pueden usarse elementos de array en una instrucción de **entrada**. Por ejemplo:

```java
int[] serie = new int[5];  
serie[0] = Integer.parseInt(System.console().readLine());  
serie[1] = serie[0] + 15;  
System.out.println(serie[1]); 
```

### 2.2.2. Recorrido de un array

Una forma muy habitual de manipular un array es **accediendo secuencialmente a todos sus elementos**, uno tras otro. Para ello, se utiliza un **bucle con contador**, de modo que la variable contador nos sirve como índice para acceder a cada uno de los elementos del array. 

Supongamos, por ejemplo, que tenemos un array de 10 números enteros declarado llamado v, y una variable entera llamada i. Por medio de un bucle, con ligeras modificaciones, podemos realizar todas estas operaciones: 

1) **Inicializar** todos los elementos a un **valor** cualquiera (por ejemplo, 0):
  ```java
  for (i = 0; i <= 9; i++) {  
      v[i] = 0;  
  }
  ```

2) **Inicializar** todos los elementos con **valores introducidos por teclado**:
  ```java
  for (i = 0; i <= 9; i++) {  
      printf("Escriba el valor del elemento nº %i: ", i);   
      v[i] = Integer.parseInt(System.console().readLine());  
  }
  ```


3) **Mostrar** todos los elementos en la pantalla:
  ```java
  for (i = 0; i <= 9; i++) {  
      System.out.println("El elemento nº " + i + " vale " + v[i]);  
  }
  ```

4) **Realizar alguna operación** que implique a todos los elementos. Por ejemplo, sumarlos:
  ```java
  suma = 0;   
  for (i = 0; i <= 9; i++) {  
      suma = suma + v[i];  
  }
  ```

### 2.2.3. Ordenación de arrays unidimensionales

Otra operación típica que se realiza con arrays unidimensionales es **ordenar sus elementos** mediante algún criterio. Por ejemplo, un array de números enteros puede ordenarse **de menor a mayor**. Si el array original es este:

![ud05_array_03.png](/img/user/adjuntos/1DAM_Programacion/Unidad_05/ud05_array_03.png)

...después de la ordenación nos quedará este otro array:

![ud05_array_04.png](/img/user/adjuntos/1DAM_Programacion/Unidad_05/ud05_array_04.png)

Del mismo modo, se pueden ordenar los elementos con **cualquier otro criterio**: de mayor a menor, primero los pares y luego los impares, o cualquier otro que nos resulte útil para resolver un problema. 

**Métodos de ordenación** de arrays hay **muchos**, desde los más simples (e ineficientes) hasta los más elaborados, y constituyen un área de estudio muy interesante dentro de la algorítmica.  

En la sección de actividades volveremos sobre este asunto, pero ahora mostraremos **tres métodos de ordenación** muy populares:

* El **método de la burbuja** (o de **intercambio directo**), un método sencillo de entender pero bastante lento.

* El **método de selección directa**, otro método simple e ineficiente.

* El **método rápido** o ***quicksort***, un algoritmo elegante y recursivo que ordena arrays con asombrosa rapidez. 

Podríamos explicar ahora cómo funciona cada método mediante una larga parrafada, pero probablemente no se entendería gran cosa y los algoritmos son mucho más informativos por sí mismos. De modo que estudia los tres algoritmos detenidamente para intentar comprenderlos (o, al menos, los dos primeros). Dibuja en un papel un array desordenado de pocos elementos y haz un traceo (o ejecución “a dedo”) de cada método de ordenación para comprender cómo actúa. A estas alturas del curso, deberías ser capaz de entender el funcionamiento del método de la burbuja y el de selección directa. Es posible que el método rápido no puedas comprenderlo hasta el final del curso, ya que utiliza conceptos más avanzados, como la recursividad, y además se trata de un algoritmo que no es trivial en absoluto. 

> [!info] Nota 
> `LONGITUD_array` es una constante que se supone definida en alguna otra parte del programa.

```java
// Ordenación por INTERCAMBIO DIRECTO (burbuja)  
void ordenaarray(int v[]) {
    int i, j, elem;
    for (i = 1; i < LONGITUD_array; i++) {
        for (j = LONGITUD_array - 1; j >=i; j--) {
            if (v[j-1] > v[j]) {
                elem = v[j-1];
                v[j-1] = v[j];
                v[j] = elem;
            }
        }
    }
}
```


```java
// Ordenación por SELECCIÓN DIRECTA   
void ordenaarray(int v[])   
{
    int i, j, minimo, posicion_minimo;
    for (i = 0; i < LONGITUD_array; i++) {
        minimo = v[i];
        posicion_minimo = i;
        for (j=i; j < LONGITUD_array; j++) {
            if (v[j] < minimo) {
                minimo = v[j];
                posicion_minimo = j;
            }  
        }  
        v[posicion_minimo] = v[i];   
        v[i] = minimo;   
    }  
}
```

```java
/*
 Ordenación rápida (QUICKSORT)   
 NOTA: en esta implementación, por simplicidad, suponemos que el array v  
 es un atributo de clase.
 */
void ordena_array(int iz, int de)   
{   
    int i, j, x, w;   
    
    i = iz;   
    j = de;   
    x = v[(iz + de) / 2];   
    do {   
        while (v[i] < x) i++;   
        while (x < v[j]) j--;   
    
        if (i <= j) {
            w = v[i];
            v[i] = v[j];
            v[j] = w;
            i++;
            j--;
        }
    } while (i <= j);   

    w = v[i];   
    v[i] = v[de];   
    v[de] = w;   

    if (iz < j) ordena_array(iz, j);   
    if (i < de) ordena_array(i, de);  
}
```

### 2.2.4. Búsqueda en arrays unidimensionales

En los arrays, como en todas las estructuras de datos que contienen muchos datos en su interior, también es habitual encontrarse con la operación de **búsqueda**. 

La operación de búsqueda consiste en, dado un array y dado un dato cualquiera, determinar si el dato está en alguna posición del array y, si es necesario, averiguar cuál es esa posición. 

La operación de búsqueda puede llegar a ser muy lenta (con el método de ***búsqueda secuencial***, que enseguida veremos), por lo que si en un programa tenemos que realizar búsquedas en arrays grandes repetidas veces, debemos pensar el modo de lograr que las búsquedas sean más rápidas. Por fortuna, existe una forma muy simple de hacer una búsqueda en un array de manera tremendamente rápida (con el método llamado de ***búsqueda binaria***, que también veremos). Pero esta forma tiene un problema: para que funcione, el array debe estar previamente *ordenado*. El proceso de ordenación, como acabamos de ver, es lento y costoso, pero, a cambio, obtendremos unos tiempos de búsqueda notablemente mejores. 

Resumiendo, si necesitamos hacer búsquedas de datos en arrays unidimensionales en algún programa:

* Si las **búsquedas** se realizan **pocas veces**, o bien los arrays son pequeños, optaremos por la *búsqueda secuencial*, que no necesita ordenar previamente el array.

* Si las búsquedas se realizan **muchas veces y los arrays son de gran tamaño**, optaremos por la *búsqueda binaria*, pero antes debemos ordenar el array con alguno de los métodos que hemos estudiado en la sección anterior.

#### Búsqueda secuencial

Consiste, simplemente, en **recorrer el array** desde el primer elemento hasta el último. Si encontramos el dato buscado, podemos interrumpir la búsqueda. Si no, continuaremos hasta el final del array. 

Esta es una posible implementación en C:

```c   
/*
 Búsqueda secuencial
 Buscamos el elemento “dato” en el array “v”
 Devolvemos la posición donde está “dato” o, si no lo encontramos, -1  
 */  
int buscar(int v[], int dato) {  
  int i = 0;   
  int x = -1;   
    
  while ((i < LONGITUD_array) && (x == -1))   
  {   
    if (v[i] == dato)	// ¡Lo hemos encontrado!   
      x = i;		    // Anotamos en x la posición   
    i++;   
  }   
  return x;   
} 
```

#### Búsqueda binaria 

Para que esta búsqueda funcione, el array debe estar previamente **ordenado**, como ya hemos aclarado. El método consiste en lo siguiente: 

* Supongamos que v es el array y que contiene N elementos. Llamaremos **`iz`** a la posición del elemento izquierdo del array (inicialmente, `iz = 0`). Llamaremos **`de`** a la posición del elemento derecho del array (inicialmente, `de = N - 1`)

* Tomamos un `x` igual al punto medio entre `iz` y `de`, es decir, `x = (iz / de) / 2`

* Miramos el elemento `v[x]`. Si es el dato que buscábamos, ya hemos terminado. Si no, pueden ocurrir dos cosas:

  1. Que `v[x]` sea *mayor* que el dato que buscábamos. En ese caso, y dado que el array está ordenado, continuamos la búsqueda *a la izquierda* de `x`, haciendo que `de = x`.

  2. Que `v[x]` sea *menor* que el dato que buscábamos. En ese caso, continuamos la búsqueda *a la derecha* de `x`, haciendo `iz = x`. 

* Repetimos desde el paso 2 hasta que encontremos el elemento buscado o hasta que `iz = de` (lo que significará que el elemento no está en el array) 

He aquí una implementación en Java:

```java   
/*
 Búsqueda binaria
 Buscamos el elemento “busc” en el array “v”, que debe estar ordenado
 Devolvemos la posición donde está “busc” o, si no lo encontramos, -1  
 */  
void buscar_binario(int v[], int busc) {  
    int iz, de, mitad, encontrado;   
    // Iniciamos una búsqueda binaria   
    encontrado = 0;   
    iz = 0;   
    de = LONGITUD_array – 1;   
    while ((iz < de - 1) && (encontrado == 0)) {
        mitad = iz + ((de - iz) / 2); // Calculamos la posición "mitad"   
        if (v[mitad] == busc) // ¡Lo hemos encontrado!   
            encontrado = 1;   
        if (v[mitad] > busc)  // Seguimos buscando en la mitad izquierda  
            de = mitad;   
        if (v[mitad] < busc)  // Seguimos buscando en la mitad derecha  
            iz = mitad;  
    }

    if (encontrado == 1)  
        return mitad;
    else
        return -1;   
}
```

El algoritmo de búsqueda es más complejo, como puede verse, pero los tiempos de búsqueda con el método binario son mucho más pequeños. Para un array de N elementos, el método secuencial necesita un promedio de `N/2` pasos para localizar el elemento buscado, mientras que el método binario tarda una media de log2 N pasos. ¿Qué no parece muy impresionante? Fíjate en estos datos:

1. Si el array es *pequeño* (por ejemplo, `N = 10`):
    1. La búsqueda secuencial necesita una media de 5 pasos.
    2. La búsqueda binaria necesita una media de 3 pasos. 

3. Si el array es *mediano* (por ejemplo, N = 100):
    1. La búsqueda secuencial necesita una media de 50 pasos.
    2. La búsqueda binaria necesita una media de 6 ó 7 pasos. 

4. Si el array es *grande* (por ejemplo, N = 1000), la mejora de tiempo empieza a ser notable: 
    1. La búsqueda secuencial necesita una media de 500 pasos.
    2. La búsqueda binaria necesita una media de… ¡10 pasos!

5. Si el array es *muy grande* (por ejemplo, N = 100.000), la mejora de tiempo es aún mayor:
    1. La búsqueda secuencial necesita una media de 50.000 pasos.
    2. La búsqueda binaria necesita una media de sólo 16 pasos.

La mejora en el tiempo de búsqueda es, por lo tanto, mayor cuanto mayor es el array. Por eso dijimos que **la búsqueda binaria se emplea cuando los arrays son muy grandes**. 

## 2.3. Arrays como parámetros

Para **pasar un array como parámetro** a un método, en la llamada a la función se escribe simplemente el **nombre** del array. Recuerda que los arrays son objetos, y que los objetos, en Java, se pasan como **direcciones de memoria**. 

El hecho de que a la función se le pase la dirección del array y no sus valores provoca un efecto importante: que **los arrays siempre pueden modificarse en el interior del método y esa modificación afecta al exterior**. Esta discusión la mantuvimos en el tema 2 (sección "paso de parámetros"), así que revísala si no lo tienes claro, porque es un asunto importante. Esto mismo también sucede con los arrays multidimensionales que veremos más adelante.  

Repetimos: si algún elemento del array se modifica en un método, también será modificado en el método desde el que fue pasado. 

Por ejemplo, supongamos que **serie** es un array de 15 números enteros. Para pasarlo como parámetro a un método llamado **metodo1()** escribiríamos simplemente esto:

```java
int serie[] = new int[15];  
metodo1(serie);
```

En cuanto a la **definición del método**, la declaración de un parámetro que en realidad es un array se hace así:

```java
void metodo1 (int serie[]);
```

 
 ### Ejemplo
 Un programa que sirve para leer 50 números por teclado, y calcular la suma, la media y la desviación típica de todos los valores. La desviación es una magnitud estadística que se calcula restando cada valor del valor medio, y calculando la media de todas esas diferencias. 

Observa el siguiente programa de ejemplo detenidamente, prestando sobre todo atención al uso de los arrays unidimensionales y a **cómo se pasan como parámetros**.  

Los números de la serie se almacenarán en un array float de 50 posiciones llamado valores. La introducción de datos en el array se hace en el método introducirValores(). Recuerda que, al modificar el array dentro del método, también se modificará en el método que lo llamó.  

Después, se invoca a 3 métodos que calculan las tres magnitudes.

```java
class Estadisticas {
    public static void main(String[] args) {  
        float valores[] = new float[50];   
        float suma, media, desviacion;   
        introducirValores(valores);   
        suma = calcularSuma(valores);   
        media = calcularMedia(valores, suma);   
        desviacion = calcularDesviacion(valores, media);   
        System.out.println("La suma es " + suma);   
        System.out.println("La media es " + media);   
        System.out.println("La desviación es " + desviacion);   
    }
    
    /*
     Lee 50 números y los almacena en el array N pasado
     por variable
     */  
    private void introducir_valores(float n[]) {   
        int i;
        for (i = 1; i <= 49; i++) {
            printf("Introduzca el valor nº %d: ", i);   
            n = Integer.parseInt(System.console().readLine());   
        }
    }
    
    /*
     Devuelve la suma todos los elementos del array N
     */   
    private float calcularSuma(float n[50]) {   
        int i;   
        float suma;   
        suma = 0;   
        for (i = 1; i <= 49; i++)   
            suma = suma + n[i];
        return suma;   
    }

    /*
     Devuelve el valor medio de los elementos del array N.
     Necesita conocer lasuma de los elementos para calcular
     la media
     */
    private float calcularMedia(float N[50], float suma) {
        int i;   
        float media;   
        media = suma / 50;   
        return media;   
    }

    /*
     Calcula la desviación típica de los elementos del array N.
     Necesita conocer la media para hacer los cálculos
     */   
    private float calcularDesviacion(float n[50], float media) {  
        int i;   
        float diferencias;   
        diferencias = 0;   
        for (i = 1; i <= 49; i++)   
            diferencias = diferencias + abs(N[i] – media);
            
        diferencias = diferencias / 50;
        return diferencias;   
    }
}
```

### 2.3.1. Funciones variádicas

Como ya hemos visto, un array es en definitiva un objeto. Es decir, es un tipo de dato **no primitivo**.

Por tanto, puede enviarse a una función o método de un objeto para operar con/sobre él. El ejemplo más palpable lo encontramos en cualquier `main`:

```java
...  
public static void main(String[] varargs) {  
...
```

Si lanzamos nuestra aplicación desde la terminal (o línea de comando si estamos en Windows), este array de cadenas de texto recogería esos valores. Definiendo este sencillo programa:

```java
public class Ejemplo {
    ...  
    public static void main(String[] varargs) {  
        if (varargs != null && varargs.length > 0) {  
            System.out.println("Se han enviado los siguientes valores:");
            for(int i = 0; i < varargs.length; i++) {  
                System.out.println(varargs[i]);  
            }
        }
        else {  
            System.out.println("No se han enviado valores al programa.");  
        }
    }
...
```

Se puede ejecutar así desde el terminal:

```bash
$ > java Ejemplo 1 2 3 4 casa coche
```

El resultado de esta ejecución mostrará en pantalla el siguiente resultado:

```bash
Se han enviado los siguientes valores:  
1  
2  
3  
4  
casa  
coche
```

Este caso venía dado en cualquier main que se definía en nuestro código. Pero podemos definir nuestros propios métodos con arrays como parámetros:

```java
...  
public static void main(String[] varargs) {  
    int[] temperaturasDia = {21, 21, 23, 24, 25, 25, 24, 22, 21, 21, 19, 19};  
    int[] temperaturasTemprano = {21, 21, 23};

    System.out.println("Temperatura durante el día: ");  
    mostrarDatos(temperaturasDia);

    System.out.println("---------------------------------------");  
    System.out.println("Temperatura de primeras horas de la mañana: ");  
    mostrarDatos(temperaturasTemprano);  
}

public static void mostrarDatos(int[] temps) {  
    for(int i = 0; i < temps.length; i++) {  
        System.out.println("Temperatura a las " + i + " horas: " + temps[i]);  
    }  
}  
...
```

Lo que realmente se pasa como argumento es la referencia del objeto, con todo lo que ello supone. Esto ya se ha visto en unidades anteriores por lo que no vamos a volver a desarrollarlo. En su lugar, vamos a ver **otras formas de enviar listas de datos** como parámetros.

Volvamos al ejemplo anterior. Cuando pasamos un array como parámetro contamos con la **ventaja de enviar en una sola variable un conjunto de datos**, un array que puede tener **uno o cientos de valores** (dependiendo del tamaño del array). Esto es muy útil en determinadas ocasiones, por supuesto. Y es fácil de hacer ya que sólo hemos de **crear un array** y **enviarlo** al método. En el ejemplo anterior, por ejemplo, podemos ver las siguientes salidas para distintos vectores:

```bash
Temperatura durante el día:  
Temperatura a las 0 horas: 21  
Temperatura a las 1 horas: 21  
Temperatura a las 2 horas: 23  
Temperatura a las 3 horas: 24  
Temperatura a las 4 horas: 25  
Temperatura a las 5 horas: 25  
Temperatura a las 6 horas: 24  
Temperatura a las 7 horas: 22  
Temperatura a las 8 horas: 21  
Temperatura a las 9 horas: 21  
Temperatura a las 10 horas: 19  
Temperatura a las 11 horas: 19  
---------------------------------------  
Temperatura de primeras horas de la mañana:  
Temperatura a las 0 horas: 21  
Temperatura a las 1 horas: 21  
Temperatura a las 2 horas: 23
```

Pero supongamos que ese método se va a usar en distintos contextos dentro de nuestra aplicación y en algunos de ellos sólo se enviará un sólo valor. ¿Tendríamos que crear un array para un sólo valor…? Pues si, no es disparatado. Pero ¿no se podría enviar sólo ese valor sin tanta parafernalia?

Esto es posible gracias a las **funciones variádicas**[^2].

Las funciones o métodos variádicos permiten indicar el envío de un **número indeterminado de parámetros del mismo tipo**. Esto se hace en la definición del parámetro, añadiendo tres puntos seguidos tras el tipo de dato.

Vamos a verlo refactorizando el código anterior:

```java
...
public static void main(String[] varargs) {  
    System.out.println("Temperatura durante el día: ");  
    mostrarDatos(21, 21, 23, 24, 25, 25, 24, 22, 21, 21, 19, 19);

    System.out.println("---------------------------------------");  
    System.out.println("Temperatura de primeras horas de la mañana: ");  
    mostrarDatos(21, 21, 23);  
}

public static void mostrarDatos(int... temps) {  
    for(int i = 0; i < temps.length; i++) {  
        System.out.println("Temperatura a las " + i + " horas: " + temps[i]);  
    }  
}  
...
```

En la definición hemos indicado que el método admite una lista indeterminada de datos de tipo **int** (`int...`) que se representa con el parámetro **temps**. Esta forma de definir el parámetro nos dice que podemos enviar un nº variable de enteros, como se ve en el main. En un caso introducimos 12 enteros y en otro sólo 3. Pero **el cuerpo del método mostrarDatos se mantiene intacto**. Esto se debe a que **internamente un parámetro variádico es un array**, pero puede expresarse de distintas maneras. Es decir, que un método variádico admite distintas formas de enviar los datos:

1. Como un conjunto de parámetros (ejemplo anterior).  
2. Como un array de valores del mismo tipo.

```java
...
public static void main(String[] varargs) {  
    int[] temperaturasTemprano = {21, 21, 23};

    System.out.println("Temperatura durante el día: ");  
    mostrarDatos(21, 21, 23, 24, 25, 25, 24, 22, 21, 21, 19, 19);

    System.out.println("---------------------------------------");  
    System.out.println("Temperatura de primeras horas de la mañana: ");  
    mostrarDatos(temperaturasTemprano);  
}

public static void mostrarDatos(int... temps) {  
    for(int i = 0; i < temps.length; i++) {  
        System.out.println("Temperatura a las " + i + " horas: " + temps[i]);  
    }  
}  
...
```

Un método variádico no tiene que ser *puramente variádico*. Es decir, que admite un sólo parámetro que además es el variádico. Puede admitir varios, aunque **el variádico debe ser el último** por motivos obvios. Por ejemplo:

```java
...  
public static void main(String[] varargs) {  
    String nombre = "Anselmo";  
    int edad = 23;  
    int[] notasEstudiante = {9, 10, 9, 10, 10, 10};

    printDatosEstudiante(nombre, edad, notasEstudiante);  
}

public static void printDatosEstudiante(String nomb, int e, int... notas) {  
    System.out.println("Estudiante: " + nomb);  
    System.out.println("Edad: " + e);  
    for(int i = 0; i < notas.length; i++) {  
        System.out.println("- " + notas[i]);  
    }  
}  
...
```

El compilador sabe que el segundo parámetro, un entero, corresponde a la edad y que a partir de ahí el resto son notas del estudiante. Si cambiamos el orden...

```java
...
// ❌ Error!
public static void printDatosEstudiante(String nomb, int... notas, int e) {  
...
```

¿Cómo saber cuándo acaban las notas y se llega a la edad? Todos son números enteros, sería imposible. Por eso es importante que **el parámetro variádico vaya al final**.


## 2.4. Métodos para arrays unidimensionales

Los arrays unidimensionales, como objetos que son, disponen de varios métodos muy útiles que facilitan el trabajo con ellos. Por ejemplo, los heredados de la clase **`Object`**:

* **`equals()`**: permite discernir si dos referencias son el mismo objeto.
* **`clone()`**: permite duplicar el array en profundidad. 

En la [[1DAM_Programación/Unidades/Unidad 4 - POO. Clases\|Unidad 4]] hablábamos de las peculiaridades y limitaciones de estos dos métodos, y de cómo a veces es conveniente sobrescribirlos. Pues bien, el método clone() para arrays unidimensionales está sobrescrito, y produce una copia en profundidad del array original. Por lo tanto, el array clonado tiene un contenido idéntico al original, pero está alojado en otra zona de la memoria y tienen vidas separadas. *Son arrays unidimensionales de igual contenido pero distinta referencia*. 

Eso significa que, en el ejemplo siguiente, aunque los 3 arrays unidimensionales `v1`, `v2` y `v3` contienen los mismos valores, `v1.equals(v2)` devolverá `false` y `v1.equals(v3)` devolverá `true`:

```java
byte[] v1 = {1, 2, 3};   
byte[] v2 = (byte[]) v1.clone();   
byte[] v3 = v1;
```

Además, los arrays unidimensionales en Java tienen otros métodos propios. Citamos a continuación los más usuales:

* **`length`**: devuelve el número de elementos del array. ¡Cuidado! No es un método, sino un atributo (no lleva paréntesis)

* **`sort()`**: permite ordenar el array por casi cualquier criterio. Se puede seleccionar el rango de ordenación (para no ordenar todo el array, solo una parte) y el método.

* **`fill()`**: para rellenar de valores el array.

* **`binarySearch()`**: realiza una búsqueda binaria. 

Como ves, los chicos de Sun Microsystems pensaron en todo para hacer la vida del programador más sencilla. Puedes encontrar información detallada de estos métodos y otros en el sitio oficial de Oracle: http://docs.oracle.com/javase/8/docs/api/index.html

## 2.5. Representación interna de los arrays unidimensionales

Finalizaremos la sección sobre arrays unidimensionales hablando de cómo se almacenan en la memoria del ordenador. Es importante tener una idea clara porque muchas de las cosas que suceden con los arrays unidimensionales se explican fácilmente a partir de su disposición en memoria. 

En la memoria del ordenador, todos **los elementos de los arrays unidimensionales se almacenan en posiciones de memoria consecutivas**. 

Por ejemplo, si **v1** es un array de **10 números de tipo byte** (cada número de dicho tipo ocupa **1 byte** de memoria), el compilador asignará un espacio de memoria al elemento 0. Imaginemos que dicho espacio de memoria se ubica en la **dirección 2000**. Entonces, el resto de elementos del array ocuparán la posición 2001, la 2002, la 2003, … hasta la 2009 (ver figura) 

Por otro lado, si un array **v2** consta de 50 **números de tipo short**, y suponemos que los datos de este tipo ocupan **2 bytes**, si el primer elemento tiene asignada la **posición 2000**, el siguiente estará en la posición 2002, el siguiente en la 2004, etc. 

¿Qué ocurre si se intenta acceder a un elemento del array **más allá de su límite**? Dicho de otro modo, si tenemos un array de 10 elementos, ¿qué pasa si intentamos utilizar el elemento undécimo? Lógicamente, que estaremos **invadiendo el espacio de direcciones que hay más allá del límite del array**: la dirección 2010 y siguientes en el caso del array v1, y la 2020 y siguientes en el caso del array v2. Esas direcciones pertenecerán a otras variables o, lo que es peor, a algún fragmento de código. 

La JVM, durante la ejecución, comprobará que no intentemos acceder más allá del límite del array (ni por arriba, ni por abajo). Si lo hacemos, obtendremos un error de ejecución que es deseable evitar a toda costa. Esto se puede conseguir encerrando las operaciones sobre arrays unidimensionales en bloques `try-catch` y capturando las posibles excepciones, o bien programando las rutinas de acceso a arrays unidimensionales con el debido cuidado. Un enfoque mixto, utilizando ambas técnicas, es sin duda el más adecuado.

*Ejemplo de asignación de memoria a dos arrays unidimensionales. Los elementos de v1 ocupan 1 byte y, los de v2, 2 bytes cada uno.*

| Dirección | array v1 | array v2 |
| :---: | :---: | :---: |
| 2000 | v1[0] | v2[0] |
| 2001 | v1[1] | v2[0] |
| 2002 | v1[2] | v2[1] |
| 2003 | v1[3] | v2[1] |
| 2004 | v1[4] | v2[2] |
| 2005 | v1[5] | v2[2] |
| 2006 | v1[6] | v2[3] |
| 2007 | v1[7] | v2[3] |
| 2008 | v1[8] | v2[4] |
| 2009 | v1[9] | v2[4] |
| 2010 |  | v2[5] |
| 2011 |  | v2[5] |
| 2012 |  | v2[6] |
| 2013 |  | v2[6] |
| 2014 |  | v2[7] |
| 2015 |  | v2[7] |
| 2016 |  | v2[8] |
| 2017 |  | v2[8] |
| 2018 |  | v2[9] |
| 2019 |  | v2[9] |
| . . . | . . . | . . . |



[^1]:  Algunos autores prefieren llamar **tablas** a los arrays. En latinoamérica, es frecuente usar la bastante discutible castellanización **arreglos**.

[^2]:  **Varargs**. (2025, July 15). Oracle.com. https://docs.oracle.com/javase/8/docs/technotes/guides/language/varargs.html


# 3. Arrays bidimensionales (matrices)

Una **matriz, tabla o array bidimensional**, como un array, es una colección de elementos individuales, todos del mismo tipo, agrupados bajo el mismo identificador. La diferencia con el array es que, en el momento de declararlo y de acceder a cada elemento individual, debemos utilizar **dos índices** en lugar de uno:

```java
int[][] matriz = new int[4][4];
```

Tenemos aquí una variable compleja llamada matriz que no consta de 4 elementos enteros, sino de 16, es decir, 4x4. Podemos representar gráficamente la matriz como una **tabla**:

![ud05_matriz_01.png](/img/user/adjuntos/1DAM_Programacion/Unidad_05/ud05_matriz_01.png)

Cada casilla de la tabla o matriz es identificable mediante una pareja de índices. Normalmente, el primero de los índices se refiere a la **fila**, y el segundo, a la **columna**. Por ejemplo, si hacemos estas asignaciones:

```java
matriz[0][0] = 5;  
matriz[1][0] = 1;  
matriz[3][2] = 13;
```

…el estado en el que quedará la matriz será el siguiente:

![ud05_matriz_02.png](/img/user/adjuntos/1DAM_Programacion/Unidad_05/ud05_matriz_02.png)

Por descontado, los dos índices de la matriz pueden ser diferentes, obteniéndose tablas que son más anchas que altas o más altas que anchas. 

Una matriz es realmente un array de arrays unidimensionales, así que la salida por pantalla de las siguientes instrucciones será, respectivamente, 4 y 4. El primer 4 se refiere al número de filas de la matriz, y, el segundo, al número de columnas de la primera fila: 

```java
System.out.println(matriz.length);  
System.out.println(matriz[0].length);
```

Por lo demás, las matrices se utilizan exactamente igual que los arrays unidimensionales. A modo de ejemplo, este sería el código para **inicializar una matriz** de 5x10 enteros con todos sus elementos a 0. Observa cómo se usan los **dos bucles anidados** para acceder a todos los elementos:

```java
int m[][] = new int[5][10];
int i, j;

for (i = 0; i <= 4; i++) {
    for (j = 0; j <= 9; j++) {
        m[i][j] = 0;
    }
}
```
 

## 3.1. Arrays de múltiples dimensiones

Del mismo modo que a los arrays unidimensionales se les puede añadir un segundo índice, obteniendo las matrices, se puede generalizar esta práctica, dando lugar a **arrays multidimensionales**. Por ejemplo, el siguiente es un array de cinco dimensiones compuesto de números enteros:

```java
int ejemplo[][][][] = new int[10][4][5][7];
```

Estos arrays no se pueden representar gráficamente (aunque con los de tres dimensiones se puede intentar dibujar un cubo), pero su utilización es idéntica a la de los arrays de una o dos dimensiones.


# 4. Cadenas o strings

Si los arrays unidimensionales son el *number one* de las estructuras de almacenamiento, los arrays unidimensionales de caracteres, más conocidos como cadenas o *strings*, son el no-va-más dentro de los arrays unidimensionales. Tanto es así que reciben un nombre y un tratamiento diferenciado.

El uso de cadenas de caracteres es universal en cualquier clase de programa. Simplemente, no puedes escribir un programa para uso de seres humanos que no utilice cadenas de caracteres. Así que vamos a por ellas.

## 4.1. Declaración y manipulación de cadenas

Como hemos dicho, los **arrays unidimensionales** cuyos elementos son caracteres se denominan **cadenas de caracteres** o, simplemente, cadenas (*strings*). Por lo tanto, una cadena de caracteres se declara así:

```java
char cadena[] = new char[50]; /* Cadena de 50 caracteres */
```

Como son arrays unidimensionales, todo lo que hemos dicho hasta ahora sobre arrays unidimensionales es aplicable a las cadenas. 

Las cadenas pueden manipularse elemento por elemento, como cualquier array. Por ejemplo:  

```java
char cadena[] = new char[50];  
cadena[0] = 'H';  
cadena[1] = 'o';  
cadena[2] = 'l';  
cadena[3] = 'a';
```

Las cadenas deben tener, después de su último carácter válido, un carácter especial llamado **nulo**. Este carácter marca el final de la cadena. El carácter nulo se simboliza con el código **\0**. Por lo tanto, en el ejemplo anterior habría que agregar la siguiente línea para que la cadena estuviera completa:  

```java
cadena[4] = '\0';
```

Todas las cadenas deben terminar en un **carácter nulo**. De lo contrario, podemos tener problemas al imprimirlas en la pantalla o al realizar con ellas cualquier otro proceso. En consecuencia, en una cadena definida como la anterior, de 50 caracteres, en realidad sólo tienen cabida 49, ya que siempre hay que reservar una posición para el carácter nulo. 

Esto del carácter nulo puede llegar a ser un incordio. Además, con las cadenas nos gusta hacer cosas que no hacemos con los arrays unidimensionales. Por ejemplo, poner todas las letras en mayúscula (o en minúscula), eliminar espacios, buscar un texto dentro de otro, y mil cosas más. Cosas que no tienen sentido con un array de enteros o de cualquier otra cosa. 

Es por eso que, nuevamente, los chicos y chicas de Sun Microsystems acuden en nuestra ayuda: os presentamos la clase `String`. 

## 4.2. La clase String

Aunque es posible manipular cadenas como simples arrays unidimensionales de caracteres, es mucho más cómodo hacerlo mediante la clase `String`, perteneciente al paquete `java.lang`. 

Para empezar, la clase `String` nos ofrece todos estos cómodos y útiles constructores para cadenas:

```java
String cad1 = "Hola";  
String cad2 = new String("Mundo");  
String cad3 = new String(cad2);
```

Todos los constructores se ocupan de manejar el carácter nulo sin que nosotros tengamos que saber ni siquiera que existe, faltaría más. 

> [!note] Nota
> Recuerda que en la [[1DAM_Programación/Unidades/Unidad 3 - POO. Los objetos\|unidad 3]], en el apartado [[1DAM_Programación/Unidad 03/3. Ejemplos de la API - Math y String\|3. Ejemplos de la API - Math y String]], comentamos algunos de los métodos más habituales de la clase `String`.

* **`length()`**: muestra la longitud de la cadena, sin contar el nulo. Es decir, el número de caracteres útiles reales.

* **`concat(String s)`**: concatena (une) una cadena con otra.

* **`compareTo(String s)`**: compara una cadena con otra. Devuelve un número entero con el número de diferencias alfabéticas encontradas. Si este número es 0, significa que las cadenas son idénticas.

* **`equals()`**: este es un viejo conocido. Devolverá true si las cadenas son iguales y false en caso contrario[^1].

* **`trim()`**: elimina los espacios en blanco que pudieran existir al principio y al final.

* **`toLowerCase()`**: convierte a minúscula.

* **`toUpperCase()`**: convierte a mayúscula.

* **`replace(char c, char newc)`**: reemplaza cada ocurrencia del carácter `c` por `newc`.

* **`substring(int i, int f)`**: devuelve un nuevo `String` que será la subcadena que comienza en el carácter número `i` y termina en el `f` de la cadena original.

* **`charAt(int i)`**: devuelve un `String` con el carácter que ocupa la posición `i` de la cadena.

* **`indexOf(char c)`**: devuelve la posición en la que se encuentra el carácter c por primera vez. Si el carácter no está en la cadena, devuelve -1.

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

## 4.3. La clase StringBuffer

Los métodos de la clase `String` no modifican el `String` con el que trabajan, sino que devuelven un nuevo `String` que puede asignarse a otra variable si necesitamos conservarlo para usarlo después. Por ejemplo:

```java
String cad2 = cad1.substring(5, 10);
```

Si no asignamos el resultado de `substring()` a `cad2`, el valor se perderá. Por eso se dice que la clase String es **inmutable**. Es decir, cada vez que hacemos esto:  

```java
cadena = cadena + "otra cosa"
```


Java no modifica la cadena original, sino que **crea una nueva en memoria** y borra la anterior. En un bucle de 10.000 repeticiones, alguien maldeciría a quien programó eso (y con razón).

Por eso existen las clases [**`StringBuilder`**](https://docs.oracle.com/javase/8/docs/api/java/lang/StringBuilder.html) y, si quieres hacer operaciones *thread-safe* (esto se estudiará en el siguiente curso), la clase [**`StringBuffer`**](https://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html). Ambas clases crean cadenas de texto **mutables**, es decir, que pueden cambiar de tamaño sin crear objetos nuevos.

En dichas clases, a diferencia del String, los métodos **actúan directamente sobre el propio string**, modificándolo. Son métodos, por tanto, destructivos, porque alteran el contenido del string. 

`StringBuilder` y `StringBuffer` no pueden recibir directamente una cadena cuando se instancian. Deben hacerlo de la forma estándar:

```java
StringBuilder texto1 = new StringBuilder("asdf");
StringBuffer texto2 = new StringBuffer("asdf");
```

En cuanto a los métodos, vamos a centrarnos en los más habituales y comunes para ambas clases:

* **`append(argumento)`**: añade el argumento al final de la cadena. El argumento puede ser un int, long, float, double, boolean, char, char[], String u Object. Da igual. Se lo traga y lo añade como puede.

* **`capacity()`**: devuelve la capacidad máxima del string (que será 16 como mínimo, aunque hayamos especificado menos)

* **`charAt(int i)`**: devuelve el carácter situado en la posición i.

* **`delete(int i, int f)`**: elimina los caracteres entre las posiciones i y f.

* **`insert(int pos, argumento)`**: inserta el argumento en la posición especificada.

* **`length()`**: devuelve el número de caracteres del string.

* **`replace(int i, int f, String s)`**: reemplaza los caracteres entre las posiciones `i` y `f` por el string `s`.

* **`reverse()`**: invierte la cadena.

* **`setChar(int i, char c)`**: reemplaza el carácter de la posición `i`.

* **`substring(int i, int f)`**: devuelve el string que empieza en la posición `i` y termina en la posición `f`.

## 4.4. Trocear un String

### 4.4.1. La clase StringTokenizer

Mencionamos por último otra clase relacionada con las cadenas para ilustrar hasta qué punto la biblioteca de clases de Java es completa. Se trata de `StringTokenizer`. 

Esta clase permite dividir una cadena en elementos independientes, siempre que éstos estén separados por algún carácter particular. Este carácter puede ser un espacio en blanco, un retorno de carro (\r), un salto de línea (\n), un avance de página (\f) o un tabulador (\t). También puede servir cualquier otro carácter separador, pero en ese caso hay que indicarlo en el constructor. 

La clase `StringTokenizer` está en el paquete `java.util`. Aquí puedes ver un pequeño ejemplo:

```java
import java.util.StringTokenizer;  

StringTokenizer str;  
str = new StringTokenizer("Vamos con afán todos a la vez");  
System.out.println("La cadena str tiene "  
  + str.countTokens()  
  + " elementos, y son:"  
);

while (str.hasMoreTokens()) {  
  System.out.println(str.nextToken());  
}
```


La salida por pantalla será:

```
La cadena str tiene 7 elementos, y son:  
Vamos  
con  
afán  
todos  
a  
la  
vez
```

Esta clase ya ha sido declarada como **_legacy_** y está en desuso, aunque sigue siendo **útil cuando el texto a trocear sea de gran tamaño**, ya que aún sigue siendo más rápido.

### 4.4.2. Método `split()`

La clase String tiene entre sus métodos uno que permite trocearla, devolviendo un array con todos esos trozos. Hablamos del método String.**`split()`**. Veamos cómo funciona:

```java
String cadenaNombres = "Pedro,Pablo,María,Anselmo,Benito";
String[] nombres = cadenaNombres.split(",");

for (String nombre : nombres) {
    System.out.println(nombre);
}
```

Para trocear la cadena original `cadenaNombres` hemos indicado al método split que lo haga usando el separador `","`. De esa forma, tenemos el array:

![ud05_split_01.png](/img/user/adjuntos/1DAM_Programacion/Unidad_05/ud05_split_01.png)

[^1]:  Una duda habitual es: ¿y si comparo cadenas con \==? Pues bien, el operador de comparación se limitará a mirar las referencias o posiciones de memoria de los objetos String. Es decir, devolverá true solo si ambas cadenas son el mismo objeto, no si su contenido es el mismo.

> [!example] Material de apoyo 
> * [[1DAM_Programación/Unidad 05-Estructuras de almacenamiento#^9004f7\|Referencias - String]]


# 5. Expresiones regulares

Una **expresión regular** (conocida como `RegEx` o `RegExp`) es una secuencia de caracteres que forma un patrón de búsqueda.

Se utilizan principalmente para la validación de formatos (emails, DNI, teléfonos) y para la búsqueda y sustitución avanzada de texto dentro de cadenas. En Java, las expresiones regulares están integradas en la propia clase **`String`** (se usan en métodos como `split()`, `matches()`, `replaceAll()`) y en el paquete especializado **java.util.regex**.

Para comprender mejor las explicaciones, vamos a usar el método **`String.matches(regexp)`**. Este método comprueba que la cadena de texto cumple el patrón que se introduce como argumento, devolviendo `true` si sigue el patrón o `false` si no lo encuentra.

Para construir patrones, utilizamos una combinación de **caracteres literales** y **metacaracteres**. Cada uno de los siguientes símbolos puede identificar un carácter según los siguientes patrones:

| Símbolo | Significado |
| ----- | :---- |
| **`.`** | Representa **cualquier** carácter individual (excepto salto de línea). |
| **`\d`** | Un dígito numérico. Una expresión equivalente sería **\[0-9\]**. |
| **`\D`** | Cualquier carácter que **no** sea un dígito. |
| **`\w`** | Un carácter que puede ser una letra (mayúscula o minúscula), un número o un guión bajo (\_). |
| **`\W`** | Un carácter que **no** sea uno de los identificados por **\w**: puntos, comas, espacios, etc. |
| **`\s`** | Un espacio en blanco, un espacio de tabulador o un salto de línea. |

> [!info] Nota
> En Java, la barra invertida es un carácter de escape. Para usar `\d`, debemos escribirlo como `"\\d"` en nuestro código.

Veamos algunos ejemplos:

```java
public static void** main(String[] args) {  
   String numero1 = "4";
   String numero2 = "44";  
   String letra1 = "a";  
   String letra2 = "Aa";  
   String signoPuntuacion1 = ",";  
   String signoPuntuacion2 = ".";  
   String espacios1 = " ";  
   String espacios2 = "  ";  
   String retornoCarro = "\n";  
   String tabulacion1 = "\t";

   System.out.println(numero1.matches("."));  // true
   System.out.println(letra1.matches("."));  // true
   System.out.println(signoPuntuacion1.matches("."));  // true
   System.out.println(espacios1.matches("."));  // true
   System.out.println(retornoCarro.matches("."));  // false
   System.out.println("---------------");

   System.out.println(numero1.matches("\\d"));  // true
   System.out.println(numero2.matches("\\d"));  // false
   System.out.println(letra1.matches("\\d"));  // false
   System.out.println(espacios1.matches("\\d"));  // false
   System.out.println("---------------");

   System.out.println(numero1.matches("\\D"));  // false
   System.out.println(numero2.matches("\\D"));  // false
   System.out.println(letra1.matches("\\D"));  // true
   System.out.println(espacios1.matches("\\D"));  // true
   System.out.println("---------------");

   System.out.println(numero1.matches("\\w"));  // true
   System.out.println(letra1.matches("\\w"));  // true
   System.out.println(espacios1.matches("\\w"));  // false
   System.out.println(signoPuntuacion1.matches("\\w"));  // false
   System.out.println("---------------");

   System.out.println(numero1.matches("\\W"));  // false
   System.out.println(letra1.matches("\\W"));  // false
   System.out.println(espacios1.matches("\\W"));  // true
   System.out.println(signoPuntuacion1.matches("\\W"));  // true
   System.out.println("---------------");

   System.out.println(espacios1.matches("\\s"));  // true
   System.out.println(tabulacion1.matches("\\s"));  // true
   System.out.println(numero1.matches("\\s"));  // false
   System.out.println(letra1.matches("\\s"));  // false
   System.out.println(espacios2.matches("\\s"));  // false
   System.out.println(signoPuntuacion1.matches("\\s"));  // false
}
```

Nótese que en algunos casos el resultado es confuso. Por ejemplo:

```java
System.out.println(numero2.matches("\\d"));  // false
```

Pero si numero2 contiene un número, ¿por qué el resultado es false? Porque el valor de numero2 es 44. Por tanto, **no es un dígito** sino dos. Y el patrón **`"\\d"`** comprueba **un sólo carácter**.

Entonces, si queremos comprobar si el texto contiene **veinte dígitos**... ¿Realmente tenemos que poner esta expresión regular?

```
"\\d\\d\\d\\d\\d\\d\\d\\d\\d\\d\\d\\d\\d\\d\\d\\d\\d\\d\\d\\d"
```

Por supuesto que no. Y es que además de los patrones, podemos usar **cuantificadores** que nos ayudan a especificar en una expresión regular la cantidad de veces que puede ocurrir uno de los patrones anteriores. Estos cuantificadores son:

| Cuantificador | Significado |
| :---: | ----- |
| **`*`** | Cero o más veces. |
| **`+`** | Una o más veces. |
| **`?`** | Cero o una vez. Es decir, el elemento es **opcional**: puede aparecer o no. |
| **`{n}`** | Exactamente `n` veces. |
| **`{n, m}`** | Entre `n` y `m` veces. |

Retomando el ejemplo anterior:

```java
System.out.println(numero2.matches("\\d\*")); // true, ya que hay cero o más
System.out.println(numero2.matches("\\d+")); // true, ya que hay uno o más
System.out.println(numero2.matches("\\d?")); // false, ya que hay más de uno
System.out.println(numero2.matches("\\d{1}")); // false, ya que hay más de uno
System.out.println(numero2.matches("\\d{2}")); // true, ya que hay 2 exactos
System.out.println(numero2.matches("\\d{1,2}")); // true, ya que hay entre 1 y 2
```

También será necesario en ocasiones indicar una posición donde buscar un patrón. Para ello se usan **anclas**:

| Anclas | Significado |
| :---: | ----- |
| **`^`** | Indica el inicio de la cadena. |
| **`$`** | Indica el final de la cadena. |
| **\|** | Operador "OR". Ejemplo: (jpg|png) |

Veamos ejemplos:

```java
String id = "4";

System.out.println(id.matches("^\\d.*")); // true
System.out.println(id.matches("^\\d.+")); // false
System.out.println(id.matches("^\\d?+")); // true
```


ℹ️ El texto de id comienza por un dígito (**`^\\d`**). Después de ese dígito, no hay nada.

```java
String fichero1 = "java";  
String fichero2 = "class";

System.out.println(fichero1.matches("java|c|py")); // true*  
System.out.println(fichero2.matches("java|c|py")); // false*

```

También se pueden definir **grupos de caracteres** **permitidos o no** usando corchetes []:  

```java
String letra = "b";  
String palabra = "bcDf";  
String digito = "6";  
String numero = "2346";

// [aeiou] = cualquiera de esas letras*  
boolean esVocal = letra.matches("[aeiou]"); // false

// [^aeiou] = cualquiera que no sea una de esas letras
boolean esConsonante = letra.matches("[^aeiou]"); // true

// [a-z] = cualquier letra de la a a la z (minúscula)
boolean esMinuscula = letra.matches("[a-z]"); // true
esMinuscula = palabra.matches("[a-z]*"); // false

// [A-Z] = cualquier letra de la A a la Z (mayúscula)
boolean esMayuscula = letra.matches("[A-Z]"); // false
boolean esMayOMinuscula = palabra.matches("[a-zA-Z]*"); // true

// [0-9] = cualquier dígito del 0 al 9 (equivale a \d)
boolean esDigito = digito.matches("[0-9]"); // true
esDigito = letra.matches("[0-9]"); // false
```

Las expresiones regulares o `RegExp` aparecen como parámetros admitidos en varios métodos de `String`:

- [**matches**](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html#matches-java.lang.String-)(String regex)

- [**replaceAll**](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html#replaceAll-java.lang.String-java.lang.String-)(String regex, String replacement)

- [**replaceFirst**](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html#replaceFirst-java.lang.String-java.lang.String-)(String regex, String replacement)

- [**split**](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html#split-java.lang.String-)(String regex)

En [**matches**](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html#matches-java.lang.String-)(String regex), como ya hemos visto, simplemente comprueba si el patrón indicado en regex se encuentra en el String. Los otros métodos realizan operaciones en base a dichos patrones:

```java
int numDigitosAOfuscar = 5;  
String dni = "12345678X";  
String patronDni = "^\\d{8}\[A-Z]";  
String patronOfuscarDni1 = "^\\d{" + numDigitosAOfuscar + "}";  
String patronOfuscarDni2 = "\\d{4}(\[A-Z])";

String charOfuscador1 = "\*".repeat(numDigitosAOfuscar); // = ****
String charOfuscador2 = "-".repeat(numDigitosAOfuscar);  // = -----

boolean esDni = dni.matches(patronDni);  
System.out.println("Es DNI correcto: " + esDni);  
System.out.println(  
        "DNI ofuscado (primeros 5 dígitos con *): "  
        + dni.replaceAll(patronOfuscarDni1, charOfuscador1)); // *****678X

System.out.println(  
        "DNI ofuscado (primeros 5 dígitos con -): "  
        + dni.replaceAll(patronOfuscarDni1, charOfuscador2)); // -----678X

System.out.println(  
        "DNI ofuscado (últimos 4 dígitos): "  
        + dni.replaceAll(patronOfuscarDni2, "****$1")); // 1234****X
```

Además de la clase `String` hay otras clases específicas en el paquete `java.util.regex` para tratar expresiones regulares: [**Pattern**](https://docs.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html) y [**Matcher**](https://docs.oracle.com/javase/8/docs/api/java/util/regex/Matcher.html). Con ellas se pueden realizar más operaciones que con String. Por ejemplo, extraer todas las ocurrencias en un texto. Veámoslo con el siguiente ejemplo, donde vamos a extraer los números de teléfono de un texto:

```java
import java.util.regex.Matcher;  
import java.util.regex.Pattern;

public class EjemploRegEx {  
    public static void main(String[] args) {  
        String texto = "Llama al 912344556 o al móvil 600111222";  
          
        // Los teléfonos tendrán 9 dígitos. Ese será su patrón
        Pattern patron = Pattern.compile("\\d{9}");  
        Matcher buscador = patron.matcher(texto);  
          
        while (buscador.find()) {  
            System.out.println("Teléfono encontrado: " + buscador.group());  
        }  
    }  
}
```

Otro ejemplo habitual es el de validar una dirección de correo electrónico. Para ello vamos a usar un patrón mucho más sencillo del que realmente debería usarse:

```java
^[\\w.-]+@[\\w.-]+\\.[a-z]{2,8}$
```

Desgranemos este patrón para ver qué se valida:

1. `^` : el patrón empieza aquí.
2. `[\\w.-]+` : uno o más caracteres, puntos o guiones.
3. `@` : debe contener una arroba.
4. `\\.` : es literalmente un punto (escapado).
5. `[a-z]{2,8}` : extensión de 2 a 8 letras minúsculas.
6. `$` : el patrón termina aquí.

> [!example] Material de apoyo 
> [[1DAM_Programación/Unidad 05-Estructuras de almacenamiento#^59502e\|Referencias - Expresiones regulares]]


# 6. Arrays de objetos

Una extensión natural de todo lo visto hasta ahora son los arrays de objetos. Se trata de arrays unidimensionales, matrices o arrays de cualquier dimensión cuyos elementos no son tipos primitivos, sino clases. Por ejemplo, Strings. 

Es un caso obvio de lo-junto-todo-para-obtener-algo-más-grande que deberías estar preparado/a para utilizar en este momento. Te mostramos a continuación un pequeño ejemplo. Trata de averiguar lo que hace antes de leer la solución más abajo.

```java
public class Test {  
    private static String[] lista;  
    final static int POS = 10; // Número de posiciones del array

    public static void main(String[] args) {  
        lista = new String[POS];  
        for (int i = 0; i < POS; i++) {  
            String ln = System.console().readLine();  
            lista[i] = ln.toString();  
        }  
        muestra();  
    }

    public static void muestra() {  
        for (int i = 0; i < POS; i++)  
            System.out.print(lista[i] + " ");  
    }  
}
```

> [!success]- Solución 
> Esta clase crea un array de 10 strings y pide al usuario que teclee 10 cadenas para rellenar el array. Posteriormente se muestra el contenido de los 10 strings por pantalla.


# 7. Colecciones y listas


## 7.1. `ArrayList` y `Vector` vs arrays convencionales

Las **listas** son estructuras de datos similares a los arrays, pero más complejas. Los arrays se acceden mediante un índice numérico y las listas pueden accederse así o por otros métodos. Los elementos de los arrays se ordenan consecutivamente en memoria, mientras que los de las listas pueden estar separados. Hay algunas otras diferencias, pero, en general, resultan ser estructuras similares. 

[**`ArrayList`**](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html) y [**`Vector`**](https://docs.oracle.com/javase/8/docs/api/java/util/Vector.html) son dos implementaciones de la interfaz [**List**](https://docs.oracle.com/javase/8/docs/api/java/util/List.html) en la API de Java. Son dos clases, por tanto, muy similares. `Vector` es ligeramente más lenta pero también más segura (lanza más tipos de excepción y es **_thread-safe_**[^1]), pero si no estás usando hilos lo más normal es usar `ArrayList`. Cualquiera de ellas es más lenta para operar con los datos que un array convencional de los que hemos visto en las secciones anteriores. 

De ahora en adelante nos referiremos a `ArrayList`, pero casi todo lo que digamos es aplicable también a `Vector`. 

Estas clases tienen sobre los arrays convencionales dos grandes **ventajas**:

* Proporcionan un elevado número de **métodos para simplificar las tareas habituales** con estas estructuras: construcción, ordenación, búsqueda, etc.

* Permiten que **el array crezca "dinámicamente"**, es decir, en tiempo de ejecución. Pero cuidado: la operación de crecimiento dinámico es bastante costosa en términos de tiempo de ejecución.

  Esto se debe a que los `ArrayList` se implementan, en realidad, **a partir de arrays** a los que, como sabemos, hay que asignar un tamaño determinado. Lo que hace `ArrayList` es crear de forma transparente un **array de 10 elementos** y, en caso de que sea necesario más espacio, crea un nuevo array más grande, **copiando** los elementos que ya existan al nuevo array. Esto se repite cada vez que se rebasa el tamaño actual del [**`ArrayList`**](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html).

## 7.2. Cómo crear un ArrayList

El ArrayList echa por tierra gran parte de la teoría clásica sobre estructuras de datos, ya que no es ni un array ni una lista, sino algo aún más grande y complejo. 

Para empezar, un ArrayList puede contener datos de diferente tipo, como en este ejemplo:

```java
ArrayList array = new ArrayList();  
array.add("Buenos días");  
array.add(13);  
array.add(0.5);  
array.add('a');
```


Como puede verse, este `ArrayList` se crea vacío y luego se añaden cuatro elementos diferentes (un `String`, un `integer`, un `double` y un `char`[^2]) 

Pero también puede crearse un `ArrayList` para almacenar datos del mismo tipo. En ese caso, se declara así:

```java
ArrayList<Integer> listaNumeros = new ArrayList<Integer>();
```

La variable `listaNumeros` contendrá números enteros. Observa que hemos usado el tipo `Integer` en lugar de int. Un ArrayList puede contener cualquier cosa, **excepto tipos primitivos**. 

## 7.3. Algunos métodos útiles de `ArrayList`

Una vez que tenemos el `ArrayList` creado, es muy fácil usarlo gracias a sus métodos. Es una estructura de datos que aúna potencia y facilidad de uso, y por eso se explica su enorme éxito entre los programadores de Java. 

Los que hay a continuación son los métodos más habituales, pero hay muchos otros que puedes consultar en la API de Java:

* `size()`: devuelve el tamaño actual del array.

* `add(X)`: añade el objeto `X`.

* `add(posicion, X)`: añade el objeto X en la posición indicada.

* `get(posicion)`: devuelve el objeto que hay almacenado en la `posición` indicada.

* `remove(posicion)`: elimina el objeto que hay almacenado en la `posición` indicada.

* `remove(X)`: busca el objeto `X` en el array y lo elimina (solo elimina la primera ocurrencia). Devuelve `true` si tiene éxito o `false` si el objeto no existe.

* `contains(X)`: devuelve true si el array contiene el objeto `X`.

* `indexOf(X)`: devuelve la posición del objeto `X`. Si no existe en el array, devuelve -1.

* `clear()`: borra todos los objetos del array.

* `set(posicion, X)`: sustituye el objeto que haya en la posición indicada por el objeto `X`. 

Por ejemplo, conociendo los métodos anteriores es muy fácil hacer un recorrido por un `ArrayList`:

```java
ArrayList<Integer> miArray = new ArrayList<Integer>(); 

// Este bucle inicializa el array  
for(int i = 0; i < 1000; i++) {
    miArray.add((int)(Math.random() * 500));
}

// Este bucle muestra el contenido del array en consola  
for(int i = 0; i < array.size(); i++){  
    System.out.println(miArray.get(i));  
}
```

## 7.4. Otras colecciones en Java

Pues sí: hay vida más allá del `ArrayList`. Es una estructura muy útil, pero no la única. 

El término "**colecciones**" en Java hace referencia a aquellas clases pensadas para almacenar muchos objetos estructurados de algún modo. Es similar a lo que en programación clásica se llamaba "estructuras de datos", solo que aplicado a objetos.

> [!note] Nota
> Oficialmente, las colecciones son aquellas clases que implementan la interfaz [**Collection**](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html). Están pensadas para mantener una lista o conjunto de objetos de cualquier clase.

Así pues, los arrays convencionales son colecciones, y también lo son los [**ArrayList**](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html) o los objetos de la clase [**Vector**](https://docs.oracle.com/javase/8/docs/api/java/util/Vector.html). Pero Java dispone de un gran número (enorme, en realidad) de otras clases que pueden calificarse como colecciones. No vamos a verlas todas, como es lógico, pero sí a mencionarlas para que te suenen y puedas utilizarlas, recurriendo a la API, si llega el momento. 

Ten en cuenta que muchas de estas colecciones tienen un propósito muy específico. Es decir, su aplicabilidad es más baja que la de una clase tan genérica como [**ArrayList**](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html), porque se ajustan a cierto tipo de problemas muy concretos. Pero, cuando surge un problema de esos, contar con la colección que le sienta como un guante es una gran ventaja. 

**Tipos de colecciones en Java**:

* **Listas**: son colecciones ordenadas (lo que en otros lenguajes se llama genéricamente array). Los objetos pueden estar repetidos en la secuencia y pueden accederse de forma aleatoria o secuencial. Aquí entrarían los **arrays** clásicos, y también **`ArrayList`** y **`Vector`**.

* **Sets** o conjuntos: son colecciones donde, además, los objetos **no pueden repetirse** (solo puede haber una existencia de cada uno). Algunas clases de este tipo son [**HashSet**](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html) (colección no ordenada pero campeona del mundo en velocidad), [**LinkedHashSet**](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedHashSet.html) (como la anterior, pero ordenada y más lenta) o [**TreeSet**](https://docs.oracle.com/javase/8/docs/api/java/util/TreeSet.html) (árbol binario equilibrado, una estructura con superpoderes mágicos en las búsquedas de información).

* **Maps**: son colecciones ordenadas **según una clave**. Asocian cada posición a una clave. Se parecen a los arrays asociativos de otros lenguajes, pero son más genéricos. Algunas clases son [**HashMap**](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html), [**LinkedHashMap**](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedHashMap.html) y [**TreeMap**](https://docs.oracle.com/javase/8/docs/api/java/util/TreeMap.html), con los mismos significados que los sets que mencionamos en el epígrafe anterior.

* **Colas y pilas**: son colecciones sin acceso aleatorio, sino que la entrada y salida de objetos debe hacerse en orden FIFO o LIFO (v. módulo de Sistemas Informáticos para más información). 

Veamos cómo funcionan algunas de ellas.

### 7.4.1. Set

Como hemos dicho antes, [**Set**](https://docs.oracle.com/javase/8/docs/api/java/util/Set.html) representa un conjunto de datos con la peculiaridad de que no se repiten. Puede enfocarse desde el punto de vista matemático en el que un conjunto contiene varios elementos distintos entre sí. Aunque coloquialmente podemos compararlo con un álbum de cromos, que no tiene dos cromos iguales. Esa **es la condición que impone el álbum**, que no tiene dos huecos para dos cromos iguales. 

**Set** pertenece al paquete java.util.Set y realmente es un **interfaz**. Como conjunto de datos, **implícitamente no tiene un orden** como los arrays o ArrayList. Es decir, no hay un primer y último elemento, aunque alguna de las clases que implementan este Set sí que mantiene un orden: [**LinkedHashSet**](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedHashSet.html).

Los métodos más habituales en cualquier [**Set**](https://docs.oracle.com/javase/8/docs/api/java/util/Set.html) son los siguientes, pero hay muchos otros que puedes consultar en la API de Java:

* `size()`: devuelve el tamaño actual del conjunto.

* `add(X)`: añade el objeto X.

* `addAll(colección de X)`: añade otra colección de objetos X. Recordemos que una colección es cualquier estructura que implemente la interfaz [**Collection**](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html) (puede ser un [**ArrayList**](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html), un [**LinkedList**](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedList.html), otro [**Set**](https://docs.oracle.com/javase/8/docs/api/java/util/Set.html), etc). Este método nos permite hacer la operación de **unión** de dos conjuntos de datos.

* `removeAll(colección de X)`: elimina de nuestro conjunto aquellos elementos que se encuentran en la colección que se le pasa como parámetros. Este método nos permite hacer la operación de **diferencia** entre conjuntos de datos.

* `retainAll(colección de X)`: elimina de nuestro conjunto aquellos elementos que no se encuentran en la colección que se le pasa como parámetros. Este método nos permite hacer la operación de **intersección** entre conjuntos de datos.

* `clear()`: borra todos los objetos del conjunto.

* `contains(X)`: devuelve true si el conjunto contiene el objeto X.

* `remove(X)`: elimina el objeto X del conjunto.

* `isEmpty()`: devuelve true si el conjunto está vacío.

Veamos cómo declarar un set muy habitual, el [**HashSet**](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html): 

```java
import java.util.HashSet;

public class EjemploSet {  
    public static void main(String[] args) {
        // declaración de tipo estático  
        Set<String> nombres = new HashSet<>();
        
        // declaración de tipo dinámico
        HashSet<String> apellidos = new HashSet<>();  
    }  
}
```

En el ejemplo anterior se ven dos formas: la primera indicando [**Set**](https://docs.oracle.com/javase/8/docs/api/java/util/Set.html) en la declaración del objeto nombres y en la segunda indicando [**HashSet**](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html) como tipo de dato para apellidos.

Ambas formas son válidas, pero hay una diferencia sutil:

* `Set<String> nombres = new HashSet<>();`
  Esta forma de declarar objetos se conoce como **declaración de tipo estático**, donde declaramos el objeto indicando que su tipo de datos es **una interfaz** en lugar de la clase [**HashSet**](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html).

  > [!warning] Importante 
  > Es decir, creamos el objeto nombres que usará la estructura de un [**HashSet**](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html) para guardar datos, pero sólo podrá usar las funcionalidades firmadas en el contrato de la interfaz [**Set**](https://docs.oracle.com/javase/8/docs/api/java/util/Set.html).

  Esto es útil porque da uniformidad al código y permite cambiar la estructura de datos con facilidad. Así, si en lugar de un en un sólo lugar [**HashSet**](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html) queremos cambiar a un [**LinkedHashSet**](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedHashSet.html) sólo hay que hacer este cambio:

  `Set<String> nombres = new LinkedHashSet<>();`

  El resto del código, que usa sólo los métodos de [**Set**](https://docs.oracle.com/javase/8/docs/api/java/util/Set.html), funcionará correctamente.  
  <br>
  
* `HashSet<String> apellidos = new HashSet<>();`
  En esta ocasión se hace una **declaración de tipo dinámico** para el objeto apellidos como un [**HashSet**](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html) porque queremos usar funcionalidades de esa clase que [**Set**](https://docs.oracle.com/javase/8/docs/api/java/util/Set.html) no incluye. Por ejemplo, el método .clone().

Y ahora le añadimos elementos:

```java
import java.util.HashSet;

public class EjemploSet {  
    public static void main(String[] args) {  
        Set<String> nombres = new HashSet<>();  
        nombres.add("Pepe");  
        nombres.add("Anselmo");  
        nombres.add("Onofrio");  
        nombres.add("Pepe"); // Ya estaba, por lo que se ignora

        System.out.println(nombres);  
    }  
}
```

El resultado mostrará por consola lo siguiente, donde puede verse que no hay repeticiones (a pesar de haberlo intentando):

```
[Pepe, Anselmo, Onofrio]
```

> [!note] Nota 
> En los [**Set**](https://docs.oracle.com/javase/8/docs/api/java/util/Set.html), si se detecta que se va a introducir un elemento que ya existe en el conjunto, simplemente **se ignora**.

Veamos un ejemplo de uso de algunos de esos métodos:

```java
import java.util.HashSet;  
import java.util.Set;  
import java.util.Arrays;  
import java.util.List;

public class EjemploSet {  
    public static void main(String[] args) {  
        ...  
        // Conjunto de invitados del novio  
        Set<String> invitadosNovio = new HashSet<>();  
        invitadosNovio.add("Pedro");  
        invitadosNovio.add("Lucía");  
        invitadosNovio.add("Andrés");

        // Lista de invitados de la novia (List implementa Collection)  
        List<String> invitadosNovia = Arrays.asList("Andrés", "María", "Sonia");

        System.out.println("Invitados Novio: " + invitadosNovio);  
        System.out.println("Invitados Novia: " + invitadosNovia);

        // Añadimos a lista de ella a la de él usando addAll.  
        boolean cambio = invitadosNovio.addAll(invitadosNovia);

        System.out.println("\n¿Se añadieron nuevos invitados?: " + cambio);  
        System.out.println("Lista final única: " + invitadosNovio);

        // Conjunto de invitados de los padres de ambos  
        Set<String> invitadosSuegros = new HashSet<>();  
        invitadosSuegros.add("Pedro");  
        invitadosSuegros.add("Lucía");

        // Quitamos a los invitados de los suegros, que no caen bien a nadie  
        cambio = invitadosNovio.removeAll(invitadosSuegros);  
    }  
}
```

> [!important] Importante
> Revisa el código anterior y comprueba qué ocurre en cada paso (al ejecutar `addAll`, `removeAll`, etc.). 

### 7.4.2. Map

La interfaz [**Map**](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html) es un conjunto (un [**Set**](https://docs.oracle.com/javase/8/docs/api/java/util/Set.html)) que contiene **entradas** o **`entries`**[^3]. Cada **`entry`** es un par Clave-Valor (`Key-Value`). Su comportamiento es similar al `Set` ya que **no mantiene un orden** (como ocurre con [**HashMap**](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html), salvo en estructuras específicas como [**LinkedHashMap**](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedHashMap.html) y [**TreeMap**](https://docs.oracle.com/javase/8/docs/api/java/util/TreeMap.html)) y **no permite repeticiones**.

Si observamos la referencia de la API, vemos lo siguiente:

**Interface Map<K,V>**

Ahí es donde vemos reflejada la unidad mínima de información de un [Map](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html): la ***entrada***. El genérico `<K, V>` hace referencia a los objetos **K**ey y **V**alue respectivamente. Su funcionamiento es como el de un **diccionario** (de hecho se le llama así en algunas ocasiones). En un diccionario, cuando queremos saber el significado de una palabra, buscamos por dicha palabra que es la clave (`Key`). Cuando la encontramos, obtenemos el significado asociado a ella. Ese es su valor (`Value`).

Los [Map](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html) funcionan así. Y cuando hablamos de que no se permiten repeticiones, nos referimos concretamente a que **no puede haber dos *entradas* con la misma clave**.

> [!example] Ejemplo 
> Supongamos un carrito de la compra de cualquier web o app. Cuando añadimos productos al carrito pueden ocurrir dos cosas:
> 1. Si el producto no estaba previamente, se añade y se le asocia una cantidad de productos (uno en este caso).
> 2. Si ya estaba en el carrito, la cantidad de dicho producto se incrementa en uno.
> 
> En cualquier caso, al desplegar nuestro carrito nunca encontramos que tenemos 2 productos del mismo tipo, uno tras otro. Encontramos ese mismo producto y su cantidad (2 en este caso).
> 
> Por tanto ese carrito sería del tipo **`Map<Producto, Integer>`**, donde la clave es el objeto de tipo `Producto` que hemos seleccionado y su valor (la cantidad de ese producto) es un número entero.

Veamos cómo funcionan algunos de los métodos de esta curiosa estructura:

* `clear()`: borra todas las entradas o pares clave-valor del mapa.
<br>
* `size()`: devuelve el número de entradas que contiene el mapa.
<br>
* `get(K clave)`: devuelve el valor de la clave introducida, es decir, un objeto de tipo V. Si no encuentra ninguna coincidencia, devuelve null.
<br>

* `put(clave u objeto de tipo K, valor u objeto de tipo V)`: añade una nueva entrada clave-valor (<K,V>) al mapa.
  > [!warning] Cuidado 
  > Si ya existe una entrada con la clave introducida, la reemplazará por esta nueva.

* `putAll(Map mapa)`: hace un **put(K, V)** de cada entrada del Map pasado por argumento.
<br>

* `putIfAbsent(K clave, V valor)`: es similar a **put(K, V)**, pero añade esta entrada sólo si dicha clave no se encuentra en el mapa. En ese caso devuelve nulo. Pero si K existía previamente en el mapa, no añade la entrada y devuelve el objeto V de su valor asociado.
<br>

* `getOrDefault(K clave, V valorPorDefecto)`: hace lo mismo que el anterior, pero si no se encuentra ninguna entrada con esa clave, devuelve el objeto V que hemos introducido como valor por defecto. Esto garantiza que el resultado no sea nulo.
<br>

* `isEmpty()`: devuelve true si no hay entradas en el mapa.
<br>

* `containsKey(K clave)`: devuelve true si existe una entrada cuya clave sea el mismo objeto que el introducido como argumento.
  > [!warning] Importante 
  > La comparación del objeto pasado por parámetro con cada una de las claves del mapa se hace atendiendo al método **`equals`** y **`hashCode`** de dicho objeto. Es decir, si tenemos un Map cuya clave sean objetos de tipo Persona, se debe haber implementado en dicha clase ambos métodos para poder buscar y comparar correctamente.
  > 
  > Esto es extensible al **resto de estructuras de datos**, tanto estáticas como dinámicas.

* `containsValue(V valor)`: devuelve true si existe al menos una entrada cuyo valor sea el mismo objeto que el introducido como argumento.
<br>

* `entrySet()`: devuelve un conjunto (Set) con las entradas del mapa.
<br>

* `keySet()`: devuelve un Set con las claves (K) del mapa.
<br>

* `remove(K clave)`: elimina la entrada cuya clave sea igual al objeto K introducido como argumento y devuelve su valor V.
<br>

* `remove(K clave, V valor)`: hace lo mismo que **remove**(objeto K) pero sólo si el valor V es el mismo.
<br>

* `replace(K clave, V valor)`: si la clave K está en el mapa, la cambia por esta nueva entrada.  Devuelve el valor anterior que tuviera K. 
<br>

* `replace(K clave, V valorActual, V nuevoValor)`: similar al anterior. Si la clave K está en el mapa y tiene el valor indicado en valorActual, lo cambia por el nuevoValor.
<br>

Veamos un ejemplo que aclare su funcionamiento con un carrito de la compra:

```java
public class Carrito {  
    public static void main(String[] args) {  
        // La clave será el nombre del producto y el valor la cantidad.  
        Map<String, Integer> carrito = new HashMap<>();

        // Agregamos elementos al carrito:  
        carrito.put("Bicicleta", 1);  
        carrito.put("Pendrive", 6);  
        carrito.put("Cargador", 2);

        // Mostrar el contenido del carrito  
        System.out.println("Carrito: " + edades);  
        // Carrito: {Bicicleta=1, Pendrive=6, Cargador=2}

        // ⚠️ Al añadir la misma clave con otro valor, sobreescribimos:  
        carrito.put("Pendrive", 8);

        // Mostrar el contenido del carrito  
        System.out.println("Carrito: " + edades);  
        // Carrito: {Bicicleta=1, Pendrive=8, Cargador=2}  
     }  
}
```

## 7.5. Iteradores

En muchos <abbr title="Lenguajes Orientados a Objetos">LOO</abbr> existen unos objetos especiales llamados **iteradores**. Son objetos pensados para **recorrer una colección de datos** (del tipo que sean: Maps, Sets, ArrayLists, etc.) de forma **sencilla** y, sobre todo, **independiente** de la estructura y del tipo de objetos que almacene.

En Java esos iteradores obedecen a la interfaz [**Iterator**](https://docs.oracle.com/javase/8/docs/api/java/util/Iterator.html) y cada estructura de datos tiene algún método que devuelve un objeto de este tipo. Si vemos la documentación de referencia observamos que tiene cuatro métodos. Esto es porque, aunque muy versátil, tiene la limitación de recorrer cualquier estructura en **una sola dirección**. Solo puede avanzar (de ahí los métodos next() y hasNext()). Esto puede solventarse con sub-iteradores (heredan de [**Iterator**](https://docs.oracle.com/javase/8/docs/api/java/util/Iterator.html)) como es el caso de [**ListIterator**](https://docs.oracle.com/javase/8/docs/api/java/util/ListIterator.html), pero se aplican a estructuras más específicas.

Por otro lado, es más fiable en operaciones como el borrado de elementos de una colección mientras se recorre. Si intentamos borrar un elemento usando el for estándar o el for-each, acabaremos teniendo algún problema.

Los iteradores pueden usarse con muchas clases de Java (genéricamente, con clases "contenedoras" de objetos). En concreto, con todas las que implementen el interfaz [**Iterable**](https://docs.oracle.com/javase/8/docs/api/java/lang/Iterable.html). Eso incluye clases conocidas para nosotros (como ArrayList, Vector, TreeSet, HashSet, etc.).

Los métodos que vamos a utilizar son:

* **`hasNext()`**: devuelve true si aún quedan objetos por recorrer en la estructura. 

* **`next()`**: devuelve el siguiente objeto. 

* **`remove()`**: elimina el objeto devuelto por next().

Para usar un iterador para recorrer un ArrayList basta con crear dicho iterador en el método iterator() del ArrayList. Si además queremos borrar elementos de él:

```java
public class BorrarSuspensos {  
    public static void main(String[] args) {  
        List<Integer> notas = new ArrayList<>();  
        notas.add(8);  
        notas.add(3);  
        notas.add(10);  
        notas.add(4);  
        notas.add(6);

        System.out.println("Notas originales: " + notas);

        // Obtenemos el iterator de la lista  
        Iterator<Integer> it = notas.iterator();

        // Recorremos la lista mientras haya elementos (hasNext)  
        while (it.hasNext()) {  
            // Obtenemos el elemento (next)  
            Integer nota = it.next();  
              
            if (nota < 5) {  
                // Borramos de forma segura (remove)  
                it.remove();   
                System.out.println("Borrando un " + nota + " por suspenso.");  
            }  
        }

        System.out.println("Notas finales (aprobados): " + notas);  
    }  
}
```

> [!question] ¿Cómo lo harías? 🤔
> Cambia la declaración del `ArrayList` por esta línea y vuelve a ejecutar el código:
> ```java
> Set<Integer> notas = new HashSet<>();
> ```
> Intenta replicar este mismo código sin iterador, usando un bucle `for` o `for-each` y comprueba qué ocurre.

En conclusión, el iterador es recomendable para **borrar elementos** de una estructura **de forma segura** o para **recorrer de la misma forma estructuras de datos muy diferentes**, o estructuras personalizadas muy complejas o incluso versiones que ya huelen a rancio.

> [!example] Material de apoyo 
> * [[1DAM_Programación/Unidad 05-Estructuras de almacenamiento#^8503c9\|Referencias - Set]]
> * [[1DAM_Programación/Unidad 05-Estructuras de almacenamiento#^5b166b\|Referencias - Map]]
> * [[1DAM_Programación/Unidad 05-Estructuras de almacenamiento#^12e4ba\|Referencias - Iteradores]]

[^1]:  Cuando una estructura de datos es *thread-safe* significa que muchos hilos de ejecución pueden acceder a ella sin entorpecerse entre sí. Esto se estudiará más a fondo en 2º DAM, en el módulo de Programación de Servicios y Procesos (PSP).

[^2]:  Los tipos primitivos se convierten automáticamente a sus wrappers Integer, Double o Char al insertarlos en el ArrayList. Para más información sobre wrappers, véase la unidad 8.

[^3]:  Estas entradas obedecen a la interfaz [**Map.Entry**](https://docs.oracle.com/javase/8/docs/api/java/util/Map.Entry.html)


# 8. Comparar objetos

## 8.1. Interfaz `Comparable`
Tenemos claro cómo comparar dos números. Quizá no tan claro cómo se comparan dos textos (aunque ya se ha explicado en varias ocasiones) pero **se reduce nuevamente a comparar números**.

En las estructuras anteriores hemos visto algunas que ordenan los datos de forma automática. Tal es el caso del `TreeSet`, que aunque vaya en contra de la definición intrínseca de un `Set` (conjunto de elementos que no siguen un orden), los ordena de forma automática conforme van entrando.

Pero ¿qué ocurre si introducimos objetos de alguna de nuestras clases? En un alarde de originalidad, supongamos que tenemos la clase `Persona` con los atributos nombre y edad. Si instanciamos varios objetos de esta clase e intentamos añadirlos a un `TreeSet`, saltará una excepción con mensajes muy confusos. Entre todos ellos se puede leer la palabra Comparable. Esto significa que las estructuras de datos que ordenan sus objetos lo hacen comparando unos con otros. Para ello, debemos ser capaces de comparar dichos objetos y decidir cuál es mayor o menor. Esto se consigue con el método **`compareTo`** de la interfaz [**Comparable**](https://docs.oracle.com/javase/8/docs/api/java/lang/Comparable.html).

**`Comparable`** es una interfaz que, si la implementamos en alguna de nuestras clases, nos obliga a definir al menos el método **`compareTo`**. Este método lo tienen casi todas las clases de la API de Java y sirve para comparar dos objetos cualesquiera. Devuelve un valor entero, de forma que:

* Si es **negativo** (< 0), el objeto que llama al método `compareTo` es menor que el objeto con el que se compara.  
* Si es **cero** ( = 0), ambos objetos son "iguales".  
* Y si es **positivo** (> 0), ocurre lo opuesto que en el negativo.

Así **el programador decide cómo comparar dos objetos** de la misma forma que decide cuándo son iguales con `equals`.

Veámoslo más claramente con este ejemplo:  

```java
public static void main(String[] args) {  
	Integer n1 = 5;  
	Integer n2 = 9;  
	int comparacion = n1.compareTo(n2);  
	  
	if (comparacion < 0) {  
		System.out.println(n1 + " es menor que " + n2);  
	}  
	else if (comparacion == 0) {  
		System.out.println(n1 + " es igual que " + n2);  
	}  
	else {  
		System.out.println(n1 + " es mayor que " + n2);  
	}  
}
```


Es fácil comparar dos números. Veamos cómo hacerlo con objetos de tipo **Persona**. Para ello, esta clase implementará **Comparable**:

```java
public class Persona implements Comparable {
    private String nombre;  
    private int edad;

    public Persona(String nombre, int edad) {  
        this.nombre = nombre;  
        this.edad = edad;  
    }
    
    public int compareTo(Persona p) {  
        if (this.edad > p.edad) return 1;  
        if (this.edad < p.edad) return -1;  
          
        return 0;          
    }  
}
```

Podemos afinar más aún el método **compareTo** de la siguiente manera:

```java
public int compareTo(Persona p) {  
	return this.edad - p.edad;          
}
```

Haz las cuentas. Verás como funciona.

En cualquier caso, en la actualidad se recomienda hacer uso de los métodos ya implementados para cada objeto. Y aunque int es un tipo de dato primitivo, no lo es su wrapper Integer:  

```java
public int compareTo(Persona p) {  
	return Integer.compare(this.edad, p.edad);          
}
```

> [!warning] Importante 
> Es importante el orden de los factores a comparar.

Con esta variación, podemos ya introducir objetos `Persona` en un `TreeSet` o cualquier otra estructura que necesite comparar sus objetos para ordenarlos adecuadamente.

### 8.1.1. Orden inverso

Un detalle importante es que con una pequeña modificación, podemos hacer que la ordenación se haga a la inversa. Es decir, de mayor a menor. ¿Cómo? Cambiando el orden de los factores.

```java
public int compareTo(Persona p) {  
	return Integer.compare(p.edad, this.edad);          
}
```

O si lo hacemos manualmente:  

```java
public int compareTo(Persona p) {  
	return p.edad - this.edad;          
}
```

La ordenación se hace siempre siguiendo el resultado de `compareTo`, que es:

* `compareTo < 0`, `this` es menor que el objeto pasado por argumento.

* `compareTo = 0`, `this` es igual al objeto pasado por argumento.

* `compareTo > 0`, `this` es mayor que el objeto pasado por argumento.

Si invertimos el orden, **provocamos la inversión de la ordenación por completo**.

> [!question] ¿Y si necesitamos más de un criterio de comparación? 🤔
> Supongamos que la clase `Persona` implementa la interfaz `Comparable` e indicamos que lo haga por su edad. Así, al comparar dos personas diremos que una es mayor que otra porque tiene más años. Es la comparación natural que hemos establecido.
> 
> Pero ¿qué ocurre si necesitamos comparar dos personas por otros criterios? Esto es posible con la interfaz `Comparator`, que veremos más adelante.

> [!example] Material de apoyo 
> * [[1DAM_Programación/Unidad 05-Estructuras de almacenamiento#^f0b9bb\|Referencias - Interfaz Comparable]]

# 9. Clases y métodos con tipos genéricos

En Java, se pueden definir clases, interfaces y funciones que manejen o devuelvan **tipos genéricos**, es decir, que **una misma clase** (o interfaz, o función) **puede gestionar de la misma forma objetos diferentes**.

## 9.1. Clases con genéricos

Supongamos que queremos hacer tres clases para fabricar tres productos distintos: `FabricaCoches`, `FabricaZapatos` y `FabricaAspiradoras`. **Todas tendrán las mismas propiedades** (una lista de productos que fabrican, que serán de objetos `Coche`, `Zapato` y `Aspiradora` respectivamente) **y los mismos métodos**, que admitirán en sus parámetros sus respectivos objetos.

Claramente **estaríamos repitiendo código** salvo por el tipo de producto. Y ya sabemos lo que supone repetir código: no es buena idea. Lo ideal sería tener una colsa clase `Fabrica` que pudiese instanciarse para manejar cada una un producto distinto ¿Entonces cómo lo hacemos? Podríamos definir las propiedades y los argumentos de tipo `Object`, que admite lo que le echemos. Pero luego tendríamos que ir comprobando en cada método si ese `Object` es una instancia de `Coche`, de `Zapato` o de `Aspiradora`. Vamos, ¡un engorro!

Ya que el código sería igual en las tres fábricas salvo por el tipo de objeto que maneja cada una, ¿y si pudiéramos crear una clase `Fabrica` que contenga todos los miembros que estas tres fábricas y usamos un comodín para el tipo de producto? ¡Pues **eso es un genérico**!

Los tipos genéricos se indican con los símbolos `<` y `>`. Por ejemplo:

```java
public class Ejemplo<T> {  
    private T valor;
    
    public Ejemplo(T valor) {  
        this.valor = valor;  
    }
    
    public T getValor() {  
        return valor;  
    }
    
    public void setValor(T valor) {  
        this.valor = valor;  
    }  
}
```

La clase `Ejemplo` implementa un constructor, un `getter` y un `setter`, y contiene un atributo `private` llamado `valor`. ¿Te has fijado en el tipo de datos de `valor`? ¡Exacto! No tiene ningún tipo de datos conocido. Lo hemos declarado como **tipo `T`**.

Ahora fíjate en la declaración de la clase: **`public class Ejemplo<T>`**. Esa `T` en la expresión diamante `< >` indica que esta clase utilizará un tipo genérico, que llamaremos `T`, y que **puede ser sustituido por cualquier otro tipo** de datos real en el momento de instanciar un objeto de tipo **`Ejemplo`**. Esto se haría así:

```java
Ejemplo<Integer> e1 = new Ejemplo<>(10);
Ejemplo<String> e2 = new Ejemplo<>("Hola");
```

En las dos líneas anteriores hemos creado dos objetos de tipo `Ejemplo`, sustituyendo la `T` por `Integer` y  `String` respectivamente. De esa forma indicamos que en `e1` la propiedad `valor` es de  tipo `Integer` y admite valores de tipo `Integer` en el constructor y el setter `setValor`.  Para `e2` hacemos lo mismo, pero el tipo es `String`.  Es decir, el primero trabajará con enteros y el segundo con cadenas. **¡Y eso que son de la misma clase!**

Observa, además, que el valor que pasamos como parámetro en el constructor coincide con el del tipo con el que hemos construido la clase. Si no, provocaríamos un error de ejecución. Fíjate también en que, para los tipos primitivos, tenemos que usar su *wrapper* (`Integer` en lugar de `int`) para este tipo de construcciones.

Ya has estado usando tipos genéricos, aunque sin saber lo que eran, en algunas clases típicas del API de Java. Por ejemplo, `ArrayList`. ¿No es verdad que has visto estas declaraciones a veces?

```java
ArrayList<Integer> a1 = new ArrayList<>();
ArrayList<String> a2 = new ArrayList<>();
```

Ahí lo tienes: dos `ArrayList`, solo que se construye con enteros y otro con cadenas, exactamente igual que nuestra clase de ejemplo.

## 9.2. Funciones con genéricos

Los tipos genéricos se pueden usar en otros contextos, como en la declaración de interfaces o incluso de métodos. Fíjate en este último caso:
{ #0599d8}


```java
public static <T> void imprimir(T valor) {
    System.out.println(valor);
}
```

Aquí estamos definiendo un método llamado `imprimir()` que va a usar un tipo genérico que hemos denominado, de nuevo, `T`. Por eso aparece `<T>` entre `static` y `void`. A partir de ahí, podemos usar la letra `T` como sustituto de un tipo cualquiera en el código del método.

Para invocar al método, basta con poner cualquier variable como parámetro actual, y la `T` tomará el tipo de datos de esa variable. Por ejemplo, si llamamos al método `imprimir()` así:

```java
imprimir("Hola");   // T = String  
imprimir(10);       // T = Integer
```

...tenemos que, en la primera llamada, el tipo `T` se convertirá automáticamente en `String`, puesto que el dato que hemos pasado como parámetro es un `String`; mientras que, en la segunda llamada, el tipo `T` será `Integer`.

Veamos otro ejemplo más ilustrativo. Para empezar, definimos la jerarquía de clases:

```java
class Ordenador {
    private String nombre;
    public Ordenador(String nombre) { this.nombre = nombre; }
    public String getNombre() { return nombre; }
    @Override
    public String toString() { return "Ordenador: " + nombre; }
}

class Portatil extends Ordenador {
    private double peso;
    public Portatil(String nombre, double peso) {
        super(nombre);
        this.peso = peso;
    }
    @Override
    public String toString() {
        return "Portatil: " + getNombre() + " (Peso: " + peso + ")";
    }
}

class Sobremesa extends Ordenador {
    private String placaBase;
    public Sobremesa(String nombre, String placaBase) {
        super(nombre);
        this.placaBase = placaBase;
    }
    @Override
    public String toString() {
        return "Sobremesa: " + getNombre() + " (Placa base: " + placaBase + ")";
    }
}
```

Ahora definimos una clase **`Almacen`** para cualquier elemento que queramos introducir. Es decir, una clase genérica:

```java
class Almacen<T> {
    private T objeto;
    
    public void guardar(T objeto) { this.objeto = objeto; }
    public T recuperar() { return objeto; }
}

public class Main {
    public static void main(String[] args) {
        // Uso de la clase genérica con Portatil
        Almacen<Portatil> almacenPortatil = new Almacen<>();
        almacenPortatil.guardar(new Portatil("MSI Cyborg 17", 2.5));
        
        // No es necesario casting, el compilador sabe que es un Portatil
        Portatil e = almacenPortatil.recuperar();
        System.out.println(e);


        // Uso de la clase genérica con Sobremesa
        Almacen<Sobremesa> almacenSobremesa = new Almacen<>();
        almacenSobremesa.guardar(
            new Sobremesa("PcCom Ready", "ASUS PRIME B550M-A/CSM"));
        System.out.println(almacenSobremesa.recuperar());
        
        // Esto aporta algo de seguridad:
        // almacenPortatil.guardar(new Ordenador("Asus ExpertCenter P500"));
        // El almacén de portátiles no admite cualquier Ordenador, sólo portátiles
    }
}
```

> [!question] ¿Cómo lo harías? 🤔
> La clase `Almacen` del ejemplo anterior **admite solo un objeto**. Modifica el código para que **pueda almacenar varios objetos** (un array, una lista... tú eliges) y que los métodos se adapten a esta estructura de datos.
> Así, el método `guardar` añadirá el objeto a dicha estructura, mientras que el método `recuperar` lo devuelva y lo elimine de la estructura que hayas seleccionado. Eso si, tú decides qué objeto devuelve.
> En cualquier caso, **puedes añadir otros métodos que creas convenientes** para que tu almacén sea funcional y ayude a gestionar su contenido con los métodos que creas necesarios.

## 9.3. Restricciones

En el ejemplo anterior, el `Ejemplo<T>` podía guardar absolutamente cualquier cosa (un `String`, un `Integer` o incluso una clase tan disparatada e inusual como `Persona`...).

Pero en muchos de nuestros desarrollos hemos de acotar esos tipos de datos, ya que no podremos realizar operaciones concretas con culturizar de ellos. Por ejemplo, si queremos una clase que solo acepte objetos de tipo `Persona` o de sus subclases `Empleado` y `Cliente` para poder usar sus métodos (como, por ejemplo, `getNombre()`), tenemos que decirle a esa clase genérica que no puede aceptar cualquier tipo de dato.

Aquí es donde entras las **restricciones** (***bounds*** para los amigos angloparlantes):

* **Tipos restringidos**, como es el caso que vamos a ver a continuación para el ejemplo que estamos explicando en el párrafo anterior.

  Se utiliza al definir el genérico de una clase para obligar a aceptar clases de una jerarquía concreta para poder usar sus métodos comunes en todos ellos. Por ejemplo, el consabido `getNombre()` que está presente en `Persona` y, por herencia, en sus subclases `Empleado` y `Cliente`.

* El **comodín con límite superior**, también conocido como **comodín de salida**, usado generalmente para indicar que un parámetro pueda ser leído como cualquier subclase (`Empleado` o `Cliente`) y tratado como su superclase (`Persona`).

* **Genéricos aplicados a interfaces**, para definir un comportamiento común (como un `Validador<T>`) que se implemente de forma distinta para cada clase (de una forma para `Empleado` y de otra diferente para `Cliente`).

### 9.3.1. Tipos restringidos

Hasta ahora, cuando usábamos `<T>`, esa `T` podía ser cualquier cosa: un `String`, un `Integer` o una `Persona`. El problema es que al admitir cualquier cosa, no podemos usar métodos específicos de esas clases dentro de la clase genérica. Por ejemplo, si intentamos hacer `T.getNombre()`, Java no sabe si `T` tiene ese método, porque `T` podría ser un número `String`, un `Integer` o vaya usted a saber.

Aquí es donde entran en juego los **tipos restringidos** (*bounded type parameters*). Para restringir qué clases aceptamos y cuáles no usamos la palabra clave **`extends`**. Así, al declarar `<T extends Persona>`, le estamos diciendo a Java que `T` puede ser cualquier tipo, **siempre y cuando** **sea una `Persona` o herede de ella**.

De esta forma podemos usar todos los métodos de `Persona` dentro de tu clase genérica, además de aplicar un filtro de seguridad, evitando que alguien intente usar nuestra clase genérica con tipos que no tienen sentido (como por ejemplo, una `Empresa<Double>)`.

Veámoslo con este ejemplo, empezando por establecer la jerarquía de clases:

```java
class Persona {
    private String nombre;
    public Persona(String nombre) { this.nombre = nombre; }
    public String getNombre() { return nombre; }
    @Override
    public String toString() { return "Persona: " + nombre; }
}

class Empleado extends Persona {
    private String puesto;
    public Empleado(String nombre, String puesto) {
        super(nombre);
        this.puesto = puesto;
    }
    @Override
    public String toString() {
        return "Empleado: " + getNombre() + " (Puesto: " + puesto + ")";
    }
}

class Cliente extends Persona {
    private int idCliente;
    public Cliente(String nombre, int idCliente) {
        super(nombre);
        this.idCliente = idCliente;
    }
    @Override
    public String toString() {
        return "Cliente: " + getNombre() + " (ID: " + idCliente + ")";
    }
}
```

Supongamos que queremos una clase que gestione una oficina, un club, etc. y que admita solamente clientes o empleados (objetos que hereden de `Persona`):

```java
// Solo acepta tipos que sean una Persona o alguna de sus subclases:
// Empleado o Cliente
public class Registro<T extends Persona> {
    private List<T> sujetos;

    public Registro(List<T> sujetos) {
        this.sujetos = sujetos;
    }

    public Registro() {
        sujetos = new ArrayList<T>();
    }

    public void add(T sujeto) {
        if (sujeto != null) sujetos.add(sujeto);
    }

    /**
     * Gracias a 'extends Persona' podemos usar getNombre() en cualquier T
     * ya que T va a ser de tipo Persona, es decir, Persona, Empleado o
     * Cliente.
     */
    public void imprimirRegistro() {
        System.out.println("LISTA DEL REGISTRO DE PERSONAS");
        for(T sujeto : sujetos) {
           System.out.println(sujeto.getNombre());
        }
    }
}

// Probémoslo:
public class Main {
    public static void main(String[] args) {
        Registro<Persona> registro = new Registro<>();

        // Introducimos cualquier Persona (Cliente, Empleado o incluso Persona):
        registro.add(new Persona("Anselmo Persona Persona"));
        registro.add(new Empleado("Genara Persona Empleada", "Supervisora"));
        registro.add(new Cliente("Federico Persona Cliente", 334));

        registro.imprimirRegistro();
    }
}
```

E imprime por pantalla lo siguiente:

```
LISTA DEL REGISTRO DE PERSONAS
Anselmo Persona Persona
Genara Persona Empleada
Federico Persona Cliente
```

### 9.3.2. Comodín con límite superior (de salida)

Veamos otro ejemplo con productos financieros. La jerarquía de clases sería la siguiente:

```java
abstract class ProductoFinanciero {
    private String titular;
    protected double saldo;
    
    public ProductoFinanciero(String titular, double saldo) {
        this.titular = titular;
        this.saldo = saldo;
    }
    
    // Cada producto hará el cálculo a su manera:
    public abstract double calcularInteres();


    public String getTitular() {
        return titular;
    }
}

class Cuenta extends ProductoFinanciero {
    public Cuenta(String titular, double saldo) {
        super(titular, saldo);
    }
    
    @Override
    public double calcularInteres() {
        return saldo * 0.01;  // 1% interés
    }
}

class FondoInversion extends ProductoFinanciero {
    public FondoInversion(String titular, double saldo) {
        super(titular, saldo);
    }
    
    @Override
    public double calcularInteres() {
        return saldo * 0.05;  // 5% interés
    }
}
```

Es importante tener claro que una **`Cuenta`** sea un **`ProductoFinanciero`**, una **`List<Cuenta>` no es una `List<ProductoFinanciero>`**. Esto se llama **invarianza** y suele generar confusión. Si intentamos pasar una lista de cuentas a un método que espera una lista de productos financieros, el compilador suele quejarse.

Aquí es donde entra el comodín de salida: **`<? extends ProductoFinanciero>`**, donde "**`?`**" es el comodín o *wildcard*.

Este comodín le dice a Java que acepta una lista de cualquier cosa que sea `ProductoFinanciero` o una de sus subclases. Se conoce como comodín **de salida** porque es muy útil cuando queremos sacar datos de una estructura.

Veamos esto con un ejemplo en el que vamos a implementar un procesador de auditoría. El banco nos ha pedido un método que sume el saldo total de cualquier grupo de productos, ya sean solo cuentas, solo depósitos o una mezcla.

```java
class Auditor {
    /**
     * Este método usa el comodín <? extends ProductoFinanciero>,
     * que permite recibir List<Cuenta>, List<Deposito>,
     * List<FondoInversion> o incluso List<ProductoFinanciero>.
     */
    public static double calcularSaldoTotal(
            List<? extends ProductoFinanciero> productos) {

        double total = 0;
        for (ProductoFinanciero p : productos) {
            // Podemos leer porque Java garantiza que cualquier elemento 
            // de la lista es, como mínimo, un ProductoFinanciero.
            total += p.saldo;
        }
        return total;
    }
}
```

Probémoslo introduciendo listas de distintos productos financieros:

```java
public class Main {
    public static void main(String[] args) {
        List<Cuenta> listaCuentas = new ArrayList<>();
        listaCuentas.add(new Cuenta("Juan", 1000));
        listaCuentas.add(new Cuenta("Maria", 2000));

        List<FondoInversion> listaFondos = new ArrayList<>();
        listaFondos.add(new FondoInversion("Pedro", 5000));

        // El método admite cualquiera de las estructuras de datos:
        double saldoCuentas = Auditor.calcularSaldoTotal(listaCuentas);
        double saldoFondos = Auditor.calcularSaldoTotal(listaFondos);

        System.out.println("Total en cuentas: " + saldoCuentas + "€");
        System.out.println("Total en fondos: " + saldoFondos + "€");
    }
}
```

> [!warning] Importante 
> Hay una **regla de oro** que debemos tener en cuenta sobre `<? extends T>`: **podemos leer**, pero **no podemos escribir**.

Si dentro del método `calcularSaldoTotal` intentamos hacer lo siguiente:

```java
productos.add(new Cuenta("Nuevo", 100)); // ERROR
```

Saldrá un error de compilación. Esto se debe a que cuando usamos `List<? extends ProductoFinanciero>`, el compilador interpreta que esa lista es de un **tipo específico pero desconocido** que hereda de `ProductoFinanciero`. Veámoslo más claramente en el siguiente escenario:

```java
List<Cuenta> misCuentas = new ArrayList<>();

// Llamamos a un método que usa el wildcard
metodoConWildcard(misCuentas);

public void metodoConWildcard(List<? extends ProductoFinanciero> lista) {
    // Java no puede permitir esto...
    lista.add(new FondoInversion("Inversión Arriesgada", 5000)); // ❌ ERROR
}
```

El método no sabe qué hay realmente en la lista. El parámetro `List<? extends ProductoFinanciero>` dice que puede recibir una `List<Cuenta>`, una `List<FondoInversion>` o una `List<Deposito>`, pero **no una lista de productos mezclados**. Si se permitiera, Java estaría rompiendo la integridad de la lista que se le ha pasado (`misCuentas`) y al volver al código principal e intentar leer `misCuentas`, nos encontraríamos con un `FondoInversion`... Esto provocaría una **`ClassCastException`** al intentar usarlo.

## 9.4. Genéricos aplicados a interfaces

En el mundo bancario hay acciones que se repiten para todos los productos, pero se ejecutan de forma **distinta**. Por ejemplo, todos los productos deben poder validarse (comprobar si el saldo es positivo, si el titular es correcto, etc.) o exportarse a un formato de informe.

Si creamos una **interfaz genérica**, definimos un **contrato estándar** que puede adaptarse a cualquier tipo de dato. Supongamos que necesitamos un sistema para validar si una operación financiera es legal o posible. Para ello definimos una interfaz **`Validador<T>`**.:

```java
interface Validador<T> {
    boolean esValido(T producto);
}
```

```java
// Validación para Cuentas –> T se convierte en Cuenta
class ValidadorCuenta implements Validador<Cuenta> {
    @Override
    public boolean esValido(Cuenta c) {
        // Una cuenta es válida si tiene saldo positivo
        return c.saldo >= 0;
    }
}

// Validación para Fondos –> T se convierte en FondoInversion
class ValidadorFondo implements Validador<FondoInversion> {
    @Override
    public boolean esValido(FondoInversion f) {
        // Un fondo solo es válido si tiene más de 500€ (mínimo de inversión)
        return f.saldo >= 500;
    }
}
```

Si a estas alturas te ha pasado por la cabeza eso de “¿Para qué complicarse tanto la vida? ¿Por qué no usamos un `Object`, que es genérico, y ya está?”, resetea... Si la interfaz fuera **`esValido(Object obj)`**, dentro de `ValidadorCuenta` tendríamos que hacer un casting: `Cuenta c = (Cuenta) obj;`.

Esto es **peligroso** porque si alguien pasa por error un `FondoInversion` a ese método, el programa explotaría en tiempo de ejecución.

Con la **interfaz genérica**, el compilador **nos obliga a usar el tipo correcto**. ¡Así no te equivocarás nunca! Aunque decir eso en programación es arriesgarse demasiado...

> [!example] Material de apoyo 
> * [[1DAM_Programación/Unidad 05-Estructuras de almacenamiento#^7bbd3a\|Referencias - Tipos genéricos]]


# 10. Enumerados

La mayoría de los lenguajes de programación contemplan una estructura de datos donde almacenar un **conjunto de ==constantes estáticas== relacionadas entre sí**. Ese conjunto se conoce como **enumerado** o **`enum`**. 

Descompongamos la frase anterior: 

1. **“Conjunto de constantes estáticas…”**: se crean listas de constantes estáticas. Es decir, que una vez instanciado un enum, en memoria existirá **una y sólo una** copia de ese conjunto de constantes. 

2. **“...relacionadas entre sí”**: esto último se refiere a la finalidad que cada programador le da a ese conjunto de constantes. Si vas a usar varias constantes y las vas a meter en el mismo saco (un enum) lo normal es que ese saco sea para una finalidad concreta (días de la semana, estados de un pedido, estaciones o meses del año, etc.). 

   ¿Se pueden agrupar en un enum constantes que no tengan nada que ver unas con otras? Si, pero no es muy recomendable de cara a la organización del código. 

Veamos un ejemplo para entenderlo mejor. El más habitual es el de los días de la semana. Supongamos que tenemos un método que admite como parámetro de entrada una cadena de texto con el nombre de uno de los días de la semana: "lunes", "martes", "miércoles", "jueves", "viernes", "sábado" y/o "domingo". 

Dicho método indicará si el día es o no laborable: 

```java
public class Main {  
    final static String LUNES = "lunes";  
    final static String MARTES = "martes";  
    final static String MIERCOLES = "miércoles";  
    final static String JUEVES = "jueves";  
    final static String VIERNES = "viernes";  
    final static String SABADO = "sábado";  
    final static String DOMINGO = "domingo";

    public static void esLaborable(String dia) {  
        if (dia.toLowerCase().equals(LUNES)  
            || dia.equalsIgnoreCase(MARTES)  
            || ...  
            || dia.equalsIgnoreCase(VIERNES)) {  
            
            System.out.println(dia + " es laborable");
        }  
        else if (dia.equalsIgnoreCase(SABADO)  
            || dia.equalsIgnoreCase(DOMINGO)) {  
            
            System.out.println(dia + " NO es laborable");
        }  
        else {  
            System.out.println(dia + " NO ES UN DÍA VÁLIDO!!");
        }  
    }

    public static void main(String[] args) {  
        esLaborable("lunes");  
        esLaborable("LUNES");  
        esLaborable("miercoles");  
        esLaborable("SÁBADO");  
        esLaborable("sábado");  
        esLaborable("miÉRCOles");  
        esLaborable("domingo");  
        esLaborable("morcilla");  
        esLaborable("María");  
    }
}
```


Al ejecutarlo, el programa mostrará lo siguiente por consola: 

```bash
lunes es laborable  
LUNES es laborable  
miercoles NO ES UN DÍA VÁLIDO!!    // ya que no incluye la tilde  
SÁBADO NO es laborable  
sábado NO es laborable  
miÉRCOles es laborable  
domingo NO es laborable  
morcilla NO ES UN DÍA VÁLIDO!!  
María NO ES UN DÍA VÁLIDO!!
```

Al revisar el código del método **`esLaborable(String dia)`** vemos que hay que hacer muchas validaciones para comprobar si el día introducido es o no un día válido y, en base a eso, mostrar uno u otro mensaje. Y aunque se ha cuidado la validación con un `equalsIgnoreCase` para comprobar la igualdad con uno de los días registrados en las constantes, esto sigue siendo un **proceso de validación muy costoso** y propenso a errores:

¿Y si en lugar de siete posibles valores tuviésemos muchos más? ¿O si cada día admitiese varios valores (con o sin acentos)? ¿Y si olvidamos poner uno de los `if` y no validamos alguno de los valores? No hay que hacer un gran esfuerzo para comprender que esta forma de trabajar entraña más inconvenientes que ventajas.  Vamos a intentar mejorar esta situación usando **enumerados**. 

Los `enum` disponen de métodos estáticos predefinidos que pueden resultar muy útiles. Estos son algunos de ellos:

* **`values()`**: devuelve un array con todos los valores del `enum`. Como array que es, ya conocemos las distintas formas de recorrerlo.

* **`ordinal()`**: devuelve la posición de un valor del `enum` (la primera posición es 0). 

* **`toString()`**: devuelve el valor de un `enum` convertido en un `String` de caracteres.

* **`valueOf()`**: devuelve el valor asociado a un elemento cuyo nombre se facilita como un `String`.

En los próximos apartados veremos el uso de algunos de ellos.

## 10.1. Creación de enumerados.

En el mundo de la programación, a menudo nos encontramos con situaciones en las que una variable solo puede tener un número **limitado** y **predefinido** de valores. Por ejemplo, los días de la semana (lunes, martes...), las estaciones del año (verano, otoño...) o el estado de un pedido (pendiente, enviado, entregado...). 

Como hemos dicho antes, un enum es un conjunto de constantes estáticas relacionadas entre sí. Es decir, intrínsecamente, cada constante es **final** y **static**. 

Vamos a **declarar** uno para el ejemplo anterior: 

```java
// DiaSemana.java
public enum DiaSemana {  
    LUNES,  
    MARTES,  
    MIERCOLES,  
    JUEVES,  
    VIERNES,  
    SABADO,  
    DOMINGO;  
}
```

Como vemos, la declaración es muy similar a la de una clase salvo por la palabra enum. Eso es porque internamente enum equivale a una clase con condiciones concretas (estáticos, finales…). Como las clases, los enum son en última instancia un tipo de dato creado por el programador. 

Podemos usarlo directamente: 

```java
System.out.println(DiaSemana.MIERCOLES);
```

O crear variables de ese tipo de dato (`DiaSemana`) en concreto:

```java
DiaSemana hoy = DiaSemana.MIERCOLES;  
System.out.println(hoy);
```

En ambos casos, la salida por consola será la siguiente:

```
MIERCOLES
```

A primera vista podríamos pensar que el valor de la constante `MIERCOLES` es la cadena de texto `MIERCOLES`, pero **la constante no tiene ningún valor** de tipo primitivo (texto, entero, etc.). Es más, no puede tenerlo porque esa y **todas las constantes** del enum realmente **son objetos** de “la clase” (el enum) `DiaSemana`. Esto despista bastante, pero se aclarará más adelante.

Por lo pronto veamos cómo refactorizar el código anterior usando este enum:

```java
public class Main {
    public static void esLaborable(DiaSemana dia) {  
        if (dia.equals(SABADO) || dia.equals(DOMINGO)) {  
            System.out.println(dia + " NO es laborable");  
        }
        else {  
            System.out.println(dia + " es laborable");  
        }
    }
    
    public static void main(String[] args) {  
        esLaborable(DiaSemana.LUNES);  
        esLaborable("LUNES");            // ERROR DE COMPILACIÓN  
        esLaborable(DiaSemana.MIERCOLES);  
        esLaborable(DiaSemana.SABADO);  
        esLaborable("domingo");          // ERROR DE COMPILACIÓN  
        esLaborable("morcilla");         // ERROR DE COMPILACIÓN  
        esLaborable("María");            // ERROR DE COMPILACIÓN  
    }  
}
```

En el código anterior podemos apreciar varias cosas:

1. El parámetro de entrada del método ha cambiado de **tipo**. Ahora es de tipo `DiaSemana`. Es decir, sólo admite valores de ese enumerado.

2. El bloque de código del método se ha reducido considerablemente y es mucho más claro. Ahora no es necesario validar si es uno de los días de la semana. Lo es y punto.

Así **se garantiza que sólo se pueden introducir valores válidos** por parámetro. Por eso se usa el término **_type-safe_** (que podría traducirse como tipo de dato seguro) con los enumerados.

## 10.2. Las constantes son objetos.

Pero si las constantes no tienen valores, ¿para qué sirven?

Los enumerados son muy útiles para controlar determinados comportamientos en un programa. Por ejemplo, podemos asignar constantes de un enum a distintos controles de un menú de la interfaz. De esa forma no tenemos que estar validando (primero) si la opción elegida es correcta y (segundo) testeando la opción para que realice una determinada acción.

Pero en ocasiones se necesita asociar valores a esas constantes. Por ejemplo, supongamos que nuestro programa tiene asignado para cada día de la semana un número de horas de ejercicio físico.

Si no usamos enumerados la solución habitual sería hacer una matriz o dos arrays del mismo tamaño:

```java
...  
String[] = {"lunes", ..., "domingo"};  
int[] horasEjercicio = {1, 0, 2, ..., 0};  
...
```


Funcionalmente es correcto y con un mismo índice (el 0, por ejemplo) sabemos el día de la semana (lunes) y las horas de ejercicio para ese día (una en este caso). Pero mantenemos dos estructuras, con todo lo que ello conlleva en el resto de código. 

¿Y si además decimos que queremos asociar más valores a cada constante? Por ejemplo, el nombre largo, la abreviatura y un valor lógico (booleano) que indique si ese día se trabaja o no. En tal caso tendríamos que declarar 4 arrays, uno para cada dato. Esto se complica… además de que realmente quien sabe la relación de todos estos entre sí es el programador. Y es posible que el “yo futuro” de ese programador revise el código dentro de un año y no tenga claro qué hizo el otro programador “yo pasado”. 

Una de las máximas de la POO es que los datos y las funcionalidades que se pueden hacer con ellos estén estrechamente relacionados y encapsulados en objetos. Pues bien, **las constantes de los enumerados son objetos** y nos permiten hacer lo anterior de forma sencilla:

```java
public enum DiaSemana {
    LUNES("lunes", "L", true, 1),       // Instancia de LUNES  
    MARTES("martes", "M", false, 0),    // Instancia de MARTES  
    MIERCOLES("miércoles", "X", true, 2),  
    JUEVES("jueves", "J", true, 1),  
    VIERNES("viernes", "V", false, 0),  
    SABADO("sábado", "S", true, 1),  
    DOMINGO("domingo", "D", false, 0);

    // Atributos de instancia para cada constante:  
    private final String nombre;  
    private final String abreviatura;  
    private final boolean estudiar;  
    private final int horasEntrenamiento;

    // Constructor privado para inicializar los atributos  
    private DiaSemana(String nombre,  
                      String abreviatura,  
                      boolean estudiar,  
                      int horasEntrenamiento) {  
        this.nombre = nombre;  
        this.abreviatura = abreviatura;  
        this.estudiar = estudiar;  
        this.horasEntrenamiento = horasEntrenamiento;  
    }

    // Métodos para obtener los valores de los atributos  
    public String getNombre() {  
        return nombre;  
    }

    public String getAbreviatura() {  
        return abreviatura;  
    }

    public boolean getEstudiar() {  
        return estudiar;  
    }

    public int getHorasEntrenamiento() {  
        return horasEntrenamiento;  
    }  
}
```


Si nos fijamos bien, estamos implementando algo muy parecido a una clase donde:

* Declaramos los atributos (`nombre`, `abreviatura`, `estudiar` y `horasEntrenamiento`). En este caso son constantes (`final`).

* Definimos el constructor típico de inicialización de los valores de los atributos.

* Definimos también los `getters` para esos atributos.

Pero hay algo diferente: las **constantes** propias del enumerado. A cada constante se le añade un paréntesis con varios valores. ¿Qué son?

Unos párrafos antes hemos aseverado que **las constantes de los enumerados son objetos**. Esto explicaría por qué cada una de ellas no tiene un valor de tipo primitivo y también lo que vemos en el código anterior:

```java
...  
    LUNES("lunes", "L", true, 1),  
    MARTES("martes", "M", false, 0),  
    MIERCOLES("miércoles", "X", true, 2),  
    JUEVES("jueves", "J", true, 1),  
...
```

Lo que estamos viendo aquí es la forma de **instanciar cada constante**. En otras palabras, cada constante de tipo **DiaSemana** está ejecutando el constructor y pasándole los valores de los atributos. Así, a la constante LUNES se le pasa el nombre “lunes”, la abreviatura “L”, etc.

Si queremos obtener cualquier valor de una constante, usaremos el *getter* correspondiente:  

```java
...  
    System.out.println(DiaSemana.LUNES.getNombre());  
    System.out.println(DiaSemana.MARTES.getNombre());  
...
```

Es importante tener clara esta nomenclatura, que no es otra que la de cualquier objeto con miembros públicos y, como en este caso, estáticos:  

```java
...  
    DiaSemana.LUNES  // Hacer referencia a la constante LUNES.  
    LUNES            // ❌ Error, ya que no se sabe de dónde sale el  
                     // identificador LUNES.  
...
```


Cada objeto tiene sus métodos:

```java
...  
    DiaSemana.LUNES.getNombre();  // Ejecutar getter del objeto LUNES.  
    LUNES.getNombre();            // ❌ Error, ya que no existe el objeto LUNES
                                  // salvo en DiaSemana.
...
```

Otra ventaja de los enumerados es que la **lista de constant** puede recuperarse como un array que nos devuelve el método **`.values()`** propio de los enumerados. Así:  

```java
...  
    System.out.println(DiaSemana.values()[0].getNombre());        // "lunes"  
    System.out.println(DiaSemana.values()[0].getAbreviatura());    // "L"  
    System.out.println(DiaSemana.values()[1].getNombre());        // "martes"

    for (int i = 0; i < DiaSemana.values().length; i++) {  
      System.out.println(DiaSemana.values()[i].getNombre());  
    }  
      
    // Otra alternativa:  
    for (DiaSemana dia : DiaSemana.values()) {  
      System.out.println(dia.getNombre());  
    }

...
```


Donde **`DiaSemana.values()[0]`** devuelve la constante (u objeto de tipo `DiaSemana`) **`LUNES`**.

## 10.3. Funcionalidades

Ya ha quedado claro que un enumerado es un conjunto de constantes relacionadas entre sí. El enum encapsula atributos, métodos y las propias constantes como un array de objetos del tipo de ese mismo enum. Esta frase habría sido difícil de digerir unos cuantos párrafos antes…

Si un enum puede aglutinar un conjunto de constantes con una relación, ¿por qué no puede hacer lo mismo con acciones asociadas a dichas constantes?

Veámoslo con otro ejemplo: las figuras geométricas.

```java
public enum FiguraGeometrica {  
   CIRCUNFERENCIA,  
   CUADRADO,  
   RECTANGULO,  
   TRIANGULO;  
}
```

Este enum es muy básico y por lo pronto nos serviría para operaciones **_type-safe_** y poco más. Si quisiéramos que se hiciesen operaciones como **calcular el área** de cada figura podríamos hacer un método que admitiese como parámetro uno de tipo `FiguraGeometrica`:

```java
...  
    public double calcularArea(FiguraGeometrica figura) {  
        switch (figura) {  
            case CIRCUNFERENCIA:  
                // Pedir por pantalla el radio de la circunferencia.      
                return 3.14 * radio * radio;  
            case CUADRADO:  
                // Pedir por pantalla el lado del cuadrado.      
                return lado * lado;  
            case RECTANGULO:  
                // Pedir por pantalla la base y altura del rectángulo.  
                return base * altura;  
            ...  
        }  
    }  
...
```

Como cada figura requiere datos distintos para hacer el cálculo, hay que pedir expresamente esos datos en cada caso.

Pero lo ideal es que, ya que el enumerado contiene las figuras geométricas, **también debería contener las operaciones relacionadas** como esta. Y aquí viene el problema: ¿hay que hacer un método para calcular el área de cada figura geométrica? ¿O mejor un sólo método que comprueba qué figura es y haga el cálculo pertinente?

Si hiciésemos un método para el área de cada figura:

```java
public enum FiguraGeometrica {  
   CIRCUNFERENCIA,  
   CUADRADO,  
   RECTANGULO,  
   TRIANGULO;

   public double calcularAreaCircunferencia() {  
     // Pedir por pantalla el radio de la circunferencia.  
     return 3.14 * radio;  
   }

   public double calcularAreaCuadrado() {  
     // Pedir por pantalla el lado del cuadrado.  
     return lado * lado;  
   }

   public double calcularAreaRectangulo() {  
     // Pedir por pantalla la base y altura del rectángulo.  
     return base * altura;  
   }

   public double calcularAreaTriangulo() {  
     // Pedir por pantalla la base y altura del triángulo.  
     return base * altura / 2;  
   }  
}
```


Esta implementación no es la más adecuada (de hecho es errónea) por varios motivos:

* Si quisiéramos añadir otras figuras geométricas, tendríamos también que añadir sus correspondientes métodos para calcular el área correspondiente.

* En resumen, esto **está mal**.

Está mal porque, como repetimos insistentemente, cada constante es un objeto y, por tanto, **encapsula todo lo que hay dentro del enumerado**. Es decir, que con el código anterior se podría hacer lo siguiente:

```java
...  
  public static void main(String[] argos) {  
    double area = FiguraGeometrica.CIRCUNFERENCIA.calcularAreaCircunferencia();  
    ...  
    area = FiguraGeometrica.CIRCUNFERENCIA.calcularAreaCuadrado(); // ❌ MAL!!
    ...  
    area = FiguraGeometrica.CIRCUNFERENCIA.calcularAreaRectangulo(); // ❌ MAL!!
    ...  
  }  
...
```

Y esto no es correcto, ya que la circunferencia no debería dejar ejecutar métodos como `calcularAreaCuadrado()` o  `calcularAreaRectangulo()`.

Por tanto, lo mejor es la segunda opción: un sólo método que comprueba qué figura es y haga el cálculo pertinente.

```java
public enum FiguraGeometrica {  
    CIRCUNFERENCIA,  
    CUADRADO,  
    RECTANGULO,  
    TRIANGULO;

    public double calcularArea() {  
        switch (this) {  
            case CIRCUNFERENCIA:  
                // Pedir por pantalla el radio de la circunferencia.  
                return 3.14 * radio;  
            case CUADRADO:  
                // Pedir por pantalla el lado del cuadrado.  
                return lado * lado;  
            case RECTANGULO:  
                // Pedir por pantalla la base y altura del rectángulo.  
                return base * altura;  
            case TRIANGULO:  
                // Pedir por pantalla la base y altura del rectángulo.  
                return base * altura / 2;  
        }  
    }  
}
```

¡Vaya! Parece que ahora tenemos otro elemento extraño. ¿Qué hace ese **`this`** en el `switch`?

Recordemos que cada constante es un objeto que se ha creado lanzando el constructor del enumerado. Como en nuestro ejemplo no hay constructor, entendemos que se ha ejecutado el constructor por defecto.

Si queremos calcular el área de cada figura:  

```java
...  
  public static void main(String[] argos) {  
    double area = FiguraGeometrica.CUADRADO.calcularArea();  
    System.out.println("El área del cuadrado es: " + area);

    area = FiguraGeometrica.TRIANGULO.calcularArea();  
    System.out.println("El área del triángulo es: " + area);

    area = FiguraGeometrica.RECTANGULO.calcularArea();  
    System.out.println("El área del rectángulo es: " + area);  
  }  
...
```

Vemos que estamos llamando al mismo método `calcularArea()` del enumerado para distintas figuras geométricas. Al ejecutarse para cada objeto o constante, this identifica en cada caso de cuál se trata.

Por ejemplo, en:

```java
...  
    double area = FiguraGeometrica.CUADRADO.calcularArea();  
...
```

El método `calcularArea()` se está ejecutando en el objeto `CUADRADO`. Por tanto, `this == CUADRADO`.

Pero volvemos a uno de los problemas iniciales: el tamaño de ese método. Si hay muchas figuras geométricas o si el código a ejecutar para cada una de ellas supone muchas líneas de código, el switch se hace demasiado largo y puede dificultar su mantenimiento.

Además, en la POO lo más conveniente es que cada objeto asuma sólo la responsabilidad propia de su naturaleza. Que cada figura se ocupe de calcular su propia área de forma independiente al resto. Veamos cómo.

> [!warning] Aviso 
> Lo que viene ahora es una mezcla de conceptos que ya se han visto. Aún así no te tires de los pelos si no entran a la primera. Se explicarán a modo de repaso.

Los enumerados permiten declarar métodos abstractos. La pregunta es, ¿y qué subclase va a implementar eso si estamos en un enumerado?

Como siempre, veámoslo con un ejemplo. En este caso, un enumerado de operaciones aritméticas:

```java
public enum OperacionAritmetica {  
    SUMA("+"),  
    RESTA("-"),  
    MULTIPLICACION("*"),  
    DIVISION("/");

    private final String simbolo;

    private OperacionAritmetica(String simbolo) {  
        this.simbolo = simbolo;  
    }

    public String getSimbolo() {  
        return simbolo;  
    }

    public double ejecutar(double x, double y) {  
        switch (this) {  
            case SUMA:  
                return x + y;  
            case RESTA:  
                return x - y;  
            case MULTIPLICACION:  
                return x * y;  
            default:  
                return x / y;    // habría que controlar que y != 0  
        }  
    }  
}
```


Todas estas operaciones admiten dos operandos (dos sumandos, minuendo y sustraendo, dos factores o el dividendo y divisor respectivamente). Vemos que **todas las constantes** (**SUMA**, **RESTA…**) pueden **ejecutar la misma operación** (método ejecutar) y para cada una devolverá el valor adecuado.

Vamos a separar estas operaciones para que cada una se implemente en la figura correspondiente. Para ello, ponemos el método `ejecutar(double x, double y)` como abstracto, vaciando su cuerpo.

Al hacerlo, el compilador exige lo propio en estos casos: que ese método **se implemente para cada objeto** del enumerado. Es importante leerlo en el orden indicado por los pasos 1 y 2:

```java
public enum OperacionAritmetica {  
    // Paso 2. Cada constante implementa el método abstracto 'ejecutar'  
    SUMA {  
        @Override  
        public double ejecutar(double x, double y) {  
            return x + y;  
        }  
    },  
    RESTA {  
        @Override  
        public double ejecutar(double x, double y) {  
            return x - y;  
        }  
    },  
    MULTIPLICACION {  
        @Override  
        public double ejecutar(double x, double y) {  
            return x * y;  
        }  
    },  
    DIVISION {  
        @Override  
        public double ejecutar(double x, double y) {  
            if (y == 0) {  
                throw new IllegalArgumentException("División por cero!");  
            }  
            return x / y;  
        }  
    };  
    ...  
    // constructor, atributos...  
    ...

    // Paso 1. Declarar el método abstracto que cada constante debe implementar  
    public abstract double ejecutar(double x, double y);  
}
```

Vemos que cada constante implementa entre llaves el método ejecutar. De esta forma cada objeto asume sus propia funcionalidad sin mezclarla con la del resto.

Si probamos este código:

```java
public class Calculadora {
	public static void main(String[] args) {  
		double a = 10.0;  
		double b = 5.0;
	
		// Llamamos al método 'ejecutar' de cada constante  
		System.out.println("Resultado de la suma: "  
			+ OperacionAritmetica.SUMA.ejecutar(a, b));
		
		System.out.println("Resultado de la resta: "  
			+ OperacionAritmetica.RESTA.ejecutar(a, b));
		
		System.out.println("Resultado de la multiplicacion: "  
			+ OperacionAritmetica.MULTIPLICACION.ejecutar(a, b));
		
		System.out.println("Resultado de la division: "  
			+ OperacionAritmetica.DIVISION.ejecutar(a, b));  
			  
		// Ejemplo con un bucle  
		System.out.println("\n--- Iterando sobre las operaciones ---");  
		for (OperacionAritmetica op : OperacionAritmetica.values()) {  
			System.out.println(a  
				+ " " + op.getSimbolo() + " "  
				+ b + " = "  
				+ op.ejecutar(a, b));  
		}  
	}  
}
```


El resultado que devuelve sería: 

```
10.0 + 5.0 = 15.0  
10.0 - 5.0 = 5.0  
10.0 * 5.0 = 50.0  
10.0 / 5.0 = 2.0
```

Y por qué hacerlo así. Por el **principio de responsabilidad única** o <abbr title="Single Responsibility Principle">SRP</abbr>. Cada objeto debe ser responsable de sus funciones y principios básicos. Nada más.

En conclusión, los enumerados pueden ser un poderoso aliado si queremos mantener un **conjunto de valores concretos**, sin el riesgo de recibir datos inesperados (**_type-safe_**) y que ofrezcan funcionalidades propias de su naturaleza.

Esto mismo se puede hacer con clases estáticas, por supuesto. Aunque con una clase estática trasladamos los problemas indicados anteriormente de un sitio a otro.

En cualquier caso es importante tener en cuenta que **los enumerados no son bases de datos pequeñitas**. Sólo deben usarse para datos que no cambien (o lo hagan muy poco). Por ejemplo, son útiles para conjuntos de parámetros de uso interno para nuestra aplicación, opciones de la interfaz de usuario, etc.

> [!example] Material de apoyo 
> * [[1DAM_Programación/Unidad 05-Estructuras de almacenamiento#^e57eec\|Referencias - Enumerados]]


# 11. Hemos aprendido...

En este tema hemos visto la diferencia entre **estructuras de datos estáticas y dinámicas**. En las estáticas, hemos profundizado con bastante detalle en los **arrays clásicos** (que en Java, por supuesto, son objetos), debido a que son estructuras muy útiles en una enorme variedad de circunstancias, y a que te las vas a encontrar en prácticamente cualquier lenguaje de programación con el que trabajes en el futuro, de modo que es buena idea aprender a manipularlos con soltura: hacer **búsquedas, ordenaciones, recorridos**, etc.

Hemos profundizado en los **`String`**, que ya eran unos viejos amigos desde la [[1DAM_Programación/Unidades/Unidad 1 - Introducción a la programación con Java\|Unidad 1]]. Hemos entrado más en profundidad en las funcionalidades que ofrecen y cómo usar **expresiones regulares** para tratar textos de forma rápida y eficiente usando un patrón de búsqueda.

También hemos hablado de las **colecciones** de Java, como las que implementan **`List`** (como `ArrayList` y su hermana `Vector`), con las que podemos hacer lo mismo que con cualquier array convencional, pero contando con la inestimable ayuda de su infinidad de métodos útiles. También los **`Set`** o conjuntos para asegurarnos de que los elementos de nuestra colección no se repiten.

Además hemos visto los **`Map`**, conocidos como mapas o diccionarios, que nos permiten organizar conjuntos de pares de objetos clave-valor.

Hemos aprendido a hacer que los objetos de nuestras clases puedan compararse usando la interfaz **`Comparable`** para saber cuál es mayor según nuestro criterio.

Hemos descubierto los encantos de los **enumerados**, que nos permiten crear funcionalidades **_type-safe_** y organizar datos y funcionalidades de constantes en ellos.

Y todo ello haciendo uso de los conocimientos aprendidos en unidades anteriores.

Por último, hemos aprendido a construir archivos JAR (ver [[1DAM_Programación/Unidad 05/Apéndice - los ficheros JAR\|Apéndice]]) para empaquetar y distribuir nuestras aplicaciones Java.

# Apéndice - los ficheros JAR

Los programas que hemos hecho hasta ahora han sido pequeños tirando a minúsculos, pero, cuando una aplicación crece, el número de ficheros fuente que necesita empieza a dispararse inquietantemente. Entonces trasladar todo ese código fuente de una máquina a otra puede ser un problema. 

Para solucionarlo se crearon los archivos **<abbr title="Java ARchive">JAR</abbr>**. Son, simple y llanamente, archivos comprimidos, como los ZIP o los RAR, que incorporan en sus tripas todos los ficheros `.java`, `.class`, la estructura de directorios y cuantas cosas haya en tu carpeta de trabajo. 

Vamos a ver cómo se trabaja con los ficheros JAR desde una consola de texto. Por supuesto, los IDE incorporan herramientas para obviar todos estos farragosos comandos, pero recuerda: no siempre tendrás disponible un IDE y, además... ¡puedes fardar mucho más si lo haces desde la consola\! 

## Crear un JAR

Para crear un fichero `hola.jar` que contenga el archivo `holamundo.class`, escribimos:

```bash
$ jar cfv hola.jar holamundo.class
```

Y, si queremos incluir todos los ficheros del directorio (y, si hay subdirectorios, se añadirán también):

```bash
$ jar cfv hola.jar *
```

## Agregar ficheros a un JAR

Para agregar, digamos, un `adiosmundo.class` a un fichero `hola.jar` que ya existe, se usa el mismo comando que antes:

```bash
$ jar cfv hola.jar adiosmundo.class
```


## Ver el contenido de un JAR

Esto mostrará la lista de archivos contenidos en un JAR:

```bash
$ jar tfv hola.jar
```


## Extraer los ficheros de un JAR

Esto extraerá todos los ficheros:

```bash
$ jar xfv hola.jar
```

Y esto extraerá solo el fichero holamundo.class:

```bash
$ jar xfv hola.jar holamundo.class
```

## Ejecutar la aplicación contenida en un JAR

Pues sí. Si tienes una aplicación completa en un JAR, puedes ejecutarla sin necesidad de extraerla, así:

```bash
$ java -cp hola.jar clasemain
```

> [!question] ¿Cómo lo harías? 🤔
> ¿Cómo harías todo esto a través de tu IDE? Busca la forma de realizar estas operaciones desde Netbeans, IntelliJ, Eclipse, etc.



# Referencias

## String
{ #9004f7}


### Aula Informática - Introducción a la clase String

> Aula Informática. (2022a, abril 5). _Programación Java - Introducción a la clase String_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=1P5MzFLgd7Q

### Aula Informática - Ejercicios estructuras secuenciales IV - String

> Aula Informática. (2022a, abril 5). _Programación Java - Ejercicios estructuras secuenciales IV - String_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=UQlHEikWuiM

### Aula Informática - Ejercicios extra VII - Cadenas de texto

> Aula Informática. (2022c, abril 21). _Programación Java - Ejercicios extra VII - Cadenas de texto_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=BLEwa6tzL2E

## Expresiones regulares
{ #59502e}


### Aula Informática - Expresiones Regulares

> Aula Informática. (2022, 18 agosto). _Programación Java - Expresiones Regulares_ [Vídeo]. YouTube. https://www.youtube.com/watch?v=n7leNDm7D5g*

## Funciones variádicas

### Baeldung.com - Varargs in Java

* ***Varargs in Java***. (s/f). Baeldung.com. Recuperado el 15 de septiembre de 2025, de https://www.baeldung.com/java-varargs

### Aula en la nube - JAVA: VarargS

> Aula en la nube. (2022, 11 diciembre). ***JAVA: VarargS*** ☕ DAM - DAW [Vídeo]. YouTube. https://www.youtube.com/watch?v=8nBfF4pQKLY

### makigas - Fundamentos de Java: funciones variádicas

> makigas. (2023, 13 julio). ***Fundamentos de Java: funciones variádicas*** [Vídeo]. YouTube. https://www.youtube.com/watch?v=DnJYwavcRAY

## Estructuras de datos

> Torti Code. (2026, 17 abril). ***Las 8 Estructuras de Datos que TODO Programador Usa (Pero Nadie Explica Bien)*** [Vídeo]. YouTube. https://www.youtube.com/watch?v=9ifwAPFxpu0

### Set
{ #8503c9}


#### Aula en la nube - JAVA: Set y HashSet

> Aula en la nube. (2023d, marzo 25). ***JAVA: Set y HashSet*** ☕ DAM - DAW [Vídeo]. YouTube. https://www.youtube.com/watch?v=Yzs5MGu_lJY

#### Aula en la nube - JAVA: HashSet + equals + hashCode

> Aula en la nube. (2023e, marzo 26). ***JAVA: HashSet + equals + hashCode*** ☕ DAM - DAW [Vídeo]. YouTube. https://www.youtube.com/watch?v=8Vq04jsVaRo

#### Aula en la nube - JAVA: TreeSet

> Aula en la nube. (2023f, marzo 27). ***JAVA: TreeSet*** ☕ DAM - DAW [Vídeo]. YouTube. https://www.youtube.com/watch?v=tfeQrUH7L4k

#### Aula en la nube - JAVA: TreeSet avanzado

> Aula en la nube. (2023g, marzo 28). ***JAVA: TreeSet avanzado*** ☕ DAM - DAW [Vídeo]. YouTube. https://www.youtube.com/watch?v=UPYECuGiePc

### Map
{ #5b166b}


#### Aula en la nube - JAVA: Interface Map

> Aula en la nube. (2023h, marzo 30). ***JAVA: Interface Map*** ☕ DAM - DAW [Vídeo]. YouTube. https://www.youtube.com/watch?v=PQcBEX5M23c

#### Aula en la nube - JAVA: HashMap

> Aula en la nube. (2023i, abril 2). ***JAVA: HashMap*** ☕ DAM - DAW [Vídeo]. YouTube. https://www.youtube.com/watch?v=eplBXJarh1A

#### Aula en la nube - JAVA: TreeMap

> Aula en la nube. (2023j, abril 4). ***JAVA: TreeMap*** ☕ DAM - DAW [Vídeo]. YouTube. https://www.youtube.com/watch?v=unbN9nF-ifE

#### Aula en la nube - JAVA: TreeMap anidado

* 🎦 Aula en la nube. (2023k, abril 10). ***JAVA: TreeMap anidado*** ☕ DAM - DAW [Vídeo]. YouTube. https://www.youtube.com/watch?v=H3_Wuis_Ipg

## Iteradores
{ #12e4ba}


### Aula en la nube - JAVA: Iterable e Iterator

> Aula en la nube. (2023a, marzo 10). ***JAVA: Iterable e Iterator*** ☕ DAM - DAW [Vídeo]. YouTube. https://www.youtube.com/watch?v=zBE4fx9QyoY

### Aula en la nube - JAVA: TreeMap avanzado

> Aula en la nube. (2023l, abril 15). ***JAVA: TreeMap avanzado*** ☕ DAM - DAW [Vídeo]. YouTube. https://www.youtube.com/watch?v=Q4s1RMSXzX8

## Interfaz Comparable
{ #f0b9bb}


### Aula en la nube - JAVA: Interface Comparable

> Aula en la nube. (2023, 15 marzo). ***JAVA: Interface Comparable*** ☕ DAM - DAW [Vídeo]. YouTube. https://www.youtube.com/watch?v=R_gV5wpBwNQ

## Tipos genéricos
{ #7bbd3a}


### Makigas - Genéricos en Java

* Makigas. (2025, 5 noviembre). **Genéricos en Java** – makigas. [Genéricos en Java](https://www.makigas.es/series/genericos-en-java)

## Enumerados
{ #e57eec}


### Aula en la nube - JAVA: Tipos enumerados

> Aula en la nube. (2023a, febrero 22). ***JAVA: Tipos enumerados*** ☕ DAM - DAW [Vídeo]. YouTube. https://www.youtube.com/watch?v=AkjbCun5kA8

