---
{"dg-publish":true,"permalink":"/2-dam-pmdm/unidad-03-conceptos-avanzados/","dg-note-properties":{"modulo":"[[Módulos/PMDM]]","libro":"[[Apuntes/PMDM (2º DAM)]]"}}
---


```table-of-contents
```

---


<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



> [!info] Para que practiques desde el principio... 
> Puedes ejecutar el código Kotlin que se muestran a continuación pulsando el botoncito de "Play" en la parte superior derecha de cada código.
> 
> También puedes editar y cambiar el código para hacer pruebas sin irte de aquí.
> 
> En cualquier caso, puedes ir al **[Playground de Kotlin](https://play.kotlinlang.org/)**, el editor de código de Kotlin en la web que te permitirá probar cada uno de los códigos que encontrarás en estas notas.

</div></div>


# 1. Funciones de extensión

Las funciones de extensión en Kotlin permiten **agregar nuevas funcionalidades a clases existentes** sin modificar su código fuente.

Veámoslo con un ejemplo. Supongamos que necesitamos un par de funcionalidades específicas para las cadenas de texto en nuestra aplicación: una eliminará todos los espacios en blanco y la otra pondrá la primera letra de la cadena en mayúscula. Para ello crearemos estas dos funciones o métodos en alguna de las clases:

```kotlin
fun String.sinEspacios(): String {
    return this.replace(" ", "")
}

fun String.primeraMayuscula(): String {
    return this.replaceFirstChar{ it.uppercase() }
}

fun String.esPalindromo(): Boolean {
    return this == this.reversed()
}
```

De esta forma hemos añadido a la clase `String` las funcionalidades **`sinEspacios()`** y **`primeraMayuscula()`** y las puedo usar con cualquier objeto `String`:

```kotlin
...
val quiniela = "          1  x         2 ".sinEspacios()
//quiniela = "1x2"
...
var nombre = "pepe".primeraMayuscula()		// Pepe
...
var palindromo = "opo".esPalindromo()		// true
```

Veamos más ejemplos con otras clases conocidas:

```kotlin
//Crea un rango desde el nº hasta el final indicado:
fun Int.rangeTo(hasta: Int): IntRange {
    return this..hasta
}

//Repite una cadena de texto tantas veces como indique el entero:
fun Int.repetir(cadena: String): String {
    return cadena.repeat(this)
}

//Indica si un nº es par
fun Int.esPar(): Boolean {
    return this % 2 == 0
}

//Invierte el valor booleano
fun Boolean.not(): Boolean {
    return !this
}

// Cómo se usan:
fun main() {
	for (i in 3.rangeTo(12) {
	    . . .
	}
	. . .
	println(3.repetir("textoRepetido "))
	//Imprime: textoRepetido textoRepetido textoRepetido 
	
	. . .
	println(7.esPar())
	//false
	
	. . .
	val esMenor = false
	println(esMenor)        //false
	println(esMenor.not())  //true
}
```

> [!info] Más ejemplos en... 
> Puedes ver más ejemplos de funciones de extensión en:
> 
> Aris. (2023, 15 enero). *Funciones de extensión en Kotlin – Capítulo 36*. Curso Kotlin Para ANDROID. https://cursokotlin.com/funciones-de-extension-en-kotlin-capitulo-36/


## Referencias

* *Extensions* | Kotlin. (s. f.). Kotlin Help. https://kotlinlang.org/docs/extensions.html


# 2. Funciones de orden superior

Las funciones de orden superior son aquellas que cumplen alguna de estas condiciones:

* Reciben otras **funciones como parámetros**.

* Devuelven una **función como resultado**.

En esencia, las funciones de orden superior tratan a las funciones como **ciudadanos de primera clase** (esto lo vamos a escuchar mucho entre influencer y gurús del desarrollo), permitiéndote manipularlas y pasarlas como datos. Esto quiere decir que el lenguaje trata a las funciones con la misma flexibilidad que a cualquier otro tipo de dato (como un `Int`, un `String` o un objeto `Persona` que hayamos creado vaya usted a saber dónde y cuándo).

Hasta hace algunos años, los lenguajes de programación (incluidas algunas versiones de Java un poco viejecillas), una función sólo podía declararse dentro de una clase. En Kotlin, una función puede:

* **Guardarse en una variable**. Se puede asignar a una variable para ejecutarlo más tarde:

  ```kotlin
  val saludo: (String) -> Unit = { nombre ->
      println("¡Hola, $nombre! Bienvenida/o a PMDM.")
  }
  // La ejecutamos usando la variable
  saludo("Ana")  // ¡Hola, Ana! Bienvenida/o a PMDM.
  ```

* **Pasarse como argumento**. Se puede enviar una función como parámetro a otra función (fundamental para los *callbacks* en Android):

  ```kotlin
  fun descargarDatos(url: String, alTerminar: (Boolean) -> Unit) {
      // Simulamos una descarga...
      val exito = true
      // Ejecutamos la función que nos pasaron
      alTerminar(exito)
  }
  // Uso:
  fun main() {
      descargarDatos("google.com", { bien ->
          if (bien) println("¡Descarga completada!")
      })
  }
  ```

* **Devolverse desde otra función**. Una función puede fabricar y devolverte otra función nueva.

## 2.1. Funciones predefinidas

A continuación vemos las funciones de primer orden predefinidos más habituales.

### `map()`
Aplica una transformación a cada elemento de una colección y devuelve una nueva lista con los resultados.

```kotlin
val numeros = listOf(1, 2, 3, 4)
val numerosDobles = numeros.map { n:Int -> n * 2 } // [2, 4, 6, 8]
```

En este ejemplo, `map()` toma una función como argumento (en este caso, `{ it * 2 }`) y la aplica a cada elemento de la lista.

Pero Kotlin es hábil infiriendo tipos de datos, por lo que el ejemplo anterior podría reducirse a:

```kotlin
val numeros = listOf(1, 2, 3, 4)
val numerosDobles = numeros.map { n -> n * 2 } // [2, 4, 6, 8]
```

Además, cuando una función como `{ n -> n * 2 }` tiene un único argumento de entrada (`n`), se puede eliminar la parte izquierda de definición de parámetros y usar it en el cuerpo de la función para referirse a dicho argumento de entrada:

```kotlin
val numeros = listOf(1, 2, 3, 4)
val numerosDobles = numeros.map { it * 2 } // [2, 4, 6, 8]
```

### `filter()`

Filtra los elementos de una colección según una condición.

```kotlin
val numeros = listOf(1, 2, 3, 4, 5)
val numerosPares = numeros.filter { it % 2 == 0 } // [2, 4]
```

Aquí, `filter()` toma una función que devuelve un booleano y filtra los elementos que cumplen la condición.

### `reduce()`
Combina todos los elementos de una colección en un único valor.

```kotlin
val numeros = listOf(1, 2, 3, 4, 5)
val suma = numeros.reduce { acc, element -> acc + element }
println(suma) // Imprime: 15
```
  
`reduce()` toma una función como argumento que tiene dos parámetros:

* **`acc`**: el valor acumulado hasta el momento.

* **`element`**: el elemento actual de la lista.

La función que pasamos a **`reduce()`** suma el elemento actual al valor acumulado.

`reduce()` comienza con el primer elemento como valor acumulado y luego aplica la función a cada elemento sucesivo.

### `forEach()`

Ejecuta una acción para cada elemento de una colección.

```kotlin
val nombres = listOf("Ana", "Pedro", "Laura", "David")
nombres.forEach { nombre ->
  println(nombre)  
}
```

El `forEach()` recorre la lista de **`nombres`** y los imprime línea a línea.

## Referencias

* _Funciones de orden superior con colecciones  |  Android Developers_. (s. f.). Android Developers. https://developer.android.com/codelabs/basic-android-kotlin-compose-higher-order-functions?hl=es-419#0
* _Higher-order functions and lambdas | Kotlin_. (s. f.). Kotlin Help. https://kotlinlang.org/docs/lambdas.html


# 3. Funciones como parámetros

Además de las funciones de orden superior predefinidas vistas en el apartado anterior, podemos definir nuestras propias funciones. Por ejemplo:

```kotlin
fun calcular(num1: Int,
             num2: Int,
             operacion: (Int, Int)->Int
): Int {
    return operacion(num1, num2)
}
```

El último parámetro de la función **`calcular`** es una función llamada **`operacion`** que recibe dos enteros y devuelve un entero. Eso **es lo único que sabemos**, que podremos introducir cualquier función que admita dos enteros como parámetros y devuelva un entero como resultado.

La función **`calcular`** devolverá el resultado que devuelva dicha función, que aún no sabemos cúal es.

Definamos algunas funciones que cumplan con dicha cabecera:

```kotlin
fun sumar(a: Int, b: Int): Int { return a + b }
fun restar(a: Int, b: Int) = a - b
fun multiplicar(a: Int, b: Int): Int { return a * b }
fun dividir(a: Int, b: Int) = if (b != 0) a/b else 0
```

Todas las funciones devuelven el resultado, aunque el “return” se expresa de distintas formas.

Veamos cómo pasar cualquiera de estas funciones como parámetro en la función **calcular**:

```kotlin
val suma = calcular(4, 5, ::sumar)
val resta = calcular(4, 5, ::restar)
val producto = calcular(4, 5, ::multiplicar)
val division = calcular(4, 5, ::dividir)
```

Veamos otro ejemplo, esta vez dentro de la clase `Persona` que hemos definido anteriormente. Añadimos en ella el siguiente método:

```kotlin
class Persona(var nombre: String = "",
              var dni: String? = null,
              var edad: Int = 0) {
    var soltera = true

    fun casarse() {
        this.soltera = false
    }

    fun puedeConducir(conducir: (Int) -> Boolean): Boolean {
        return conducir(edad)
    }
}
```

Ahora imaginemos que definimos fuera de la clase varias funciones que cumplan con esa cabecera (admite un entero como parámetro y devuelve un valor lógico):

```kotlin
fun enFrancia(edad: Int): Boolean {
    return edad >= 19
}
fun enEspana(edad: Int): Boolean {
    return edad >= 18
}
fun enIslandia(edad: Int): Boolean {
    return edad >= 16
}
```

Si tenemos el siguiente objeto `Persona`, podemos comprobar dónde puede o no conducir:

```kotlin
val juanito = Persona("Juanito Pérez", "00000000Z", 16)
...
println(juanito.puedeConducir(::enFrancia))  //false
println(juanito.puedeConducir(::enEspana))   //false
println(juanito.puedeConducir(::enIslandia)) //true
```

¿Y si la clase `Persona` fuera de una librería que no podemos tocar? En tal caso podemos implementar **`puedeConducir`** como una extensión de Persona:  

```kotlin
// En algún lugar de nuestro código:
fun Persona.puedeConducir(conducir: (Int) -> Boolean): Boolean {
    return conducir(edad)
}
```



# 4. Funciones como resultado

También podemos definir el tipo de dato de salida de una función como otra función:

```kotlin
fun crearSaludo(prefijo: String): (String) -> String {
    return { nombre -> "$prefijo $nombre" }
}
```

La función anterior devuelve una función que toma un nombre y devuelve un saludo personalizado.

El prefijo se captura en el momento de llamar a la función:  

```kotlin
val saludoFormal = crearSaludo("Estimado/a")
println(saludoFormal("Ana")) // Imprime: Estimado/a Ana
```

En este caso, la variable `saludoFormal` es de tipo **`(String) -> String`** (una función). Es decir, admite una cadena de texto como parámetro de entrada y devuelve un texto.

# 5. Lambdas

Una **Lambda** es, sencillamente, una **función anónima** (sin nombre) que definimos entre llaves `{ ... }`. Esto se aplica cuando el último argumento es una función. Entonces podemos sacarlo de los paréntesis y ponerlo entre llaves, **aunque sigue siendo un argumento**.

En los apartados anteriores hemos visto cómo una función puede pasarse como parámetro a otra función. De la misma forma, una función puede asignarse a una variable. Hasta ahora hemos usado las variables para almacenar datos de distintos tipos. Pero las variables también pueden almacenar bloques de código. Por ejemplo:  

```kotlin
var imprimirMensaje: (String) -> Unit = { nombre ->
    println("Te damos la bienvenida, $nombre !")
}
imprimirMensaje("Pepe")    // Te damos la bienvenida, Pepe !
```

En estos casos, el tipo de dato se define como una función con esta forma:

```
(tipo dato param1[, tipo dato param2, ...]) -> tipo de dato que devuelve
```

La flecha **`->`** equivale al **`return`** de la función.

En caso de que la función no vaya a devolver ningún dato, se pone el tipo **`Unit`**.

> [!info] Info 
> `Unit` se usa como tipo para indicar que una función no devolverá nada. El equivalente en Java sería el `void`.

Otro ejemplo donde se ve la estructura del tipo de dato función:  

```kotlin
var opAritmetica: (Int, Int) -> Int = { x, y -> x + y }
println(opAritmetica(3, 4))
```

En este caso, la variable sumar almacena un bloque de código (algo entre llaves) correspondiente a una función con dos parámetros enteros de entrada (`x` e `y`) que devuelve la suma entera de ambos.

Al tratarse de una función, podría usarla con la función calcular de ejemplos anteriores:  

```kotlin
var opAritmetica: (Int, Int) -> Int = { x, y -> x + y }
println(calcular(3, 4, opAritmetica))
```

> [!note] Nota 
> Al tratarse de una variable, no hay que referenciarla con **`::`**.

De esta forma, al tratarse de una variable, puede cambiar su valor o, en este caso, su funcionalidad simplemente asignándole otra función:  

```kotlin
var opAritmetica: (Int, Int) -> Int = { x, y -> x + y }
println(calcular(3, 4, opAritmetica))

opAritmetica: (Int, Int) -> Int = { x, y -> x - y }
println(calcular(25, 7, opAritmetica))
```

Si no usamos variables e introducimos directamente el código de la función en el parámetro, decimos que estamos usando una **lambda** o **función anónima** (ya que no tiene nombre):

```kotlin
println(calcular(25, 7, {x: Int, y: Int -> x + y}))
println(calcular(25, 7, {x: Int, y: Int -> x - y}))
```

Si queremos implementar una lambda con más líneas de código en su cuerpo (por ejemplo, una potencia):

```kotlin
println(calcular(2, 8, { base, exp ->
    var producto = 1
    for(i in 1..exp) producto *= base
    producto
}
))
```

En este código vemos cómo indicamos:

* La cabecera (base y exp, que se entiende que son los enteros 2 y 8 respectivamente).

* Definimos el cuerpo de la función y, por último, indicamos el valor pero **sin `return`**, ya que la flecha **`->`** ya equivale al return de la función.

Al implementar esta lambda, el propio editor nos sugiere que la saquemos del paréntesis. Al hacerlo quedaría así:

```kotlin
println(calcular(2, 8)) { base, exp ->
    var producto = 1
    for(i in 1..exp) producto *= base
    producto
}
)   //quitamos un paréntesis, ya que se ha cerrado arriba
```

El sacar la lambda de los paréntesis puede hacer creer que ya no se trata de un parámetro de la función calcular, pero no es así. La lambda **sigue siendo un parámetro** en dicha función.

Esto explica cosas como la declaración de un array de enteros con todos los valores inicializados a un valor. En el siguiente ejemplo, el segundo parámetro del constructor es una lambda:  

```kotlin
val numeros = IntArray(5, {1}) // {1, 1, 1, 1, 1}
//Al ser una lambda, puede sacarse de los paréntesis:
val numeros2 = IntArray(5) {1} // {1, 1, 1, 1, 1}
val numeros3 = IntArray(5) {it} // {0, 1, 2, 3, 4}
```

Es decir, IntArray es una función de orden superior ya que admite funciones como parámetros y cuyo parámetro de entrada (it) es el índice del array. Pero podemos **renombrar** ese parámetro de entrada:  

```kotlin
val numeros3 = IntArray(5) {i -> i * 2} // {0, 2, 4, 6, 8}
```

## Parámetros no utilizados

A veces una lambda recibe varios parámetros pero no se usan todos. Para evitar advertencias del compilador (*warnings* ⚠️), usamos un guión bajo `_` para ignorarlos.

```kotlin
// Supongamos un Map donde la lambda recibe (clave, valor)
mapa.forEach { _, valor -> 
    println("Solo me interesa el valor: $valor") 
}
```


## Niveles de acceso

Como ya sabemos, las variables que se declaren dentro de un bloque de código podrán usarse sólo en ese ámbito (en dicho bloque). Con las lambdas ocurre igual, aunque dentro de una lambda se puede hacer uso de las variables externas declaradas en el mismo ámbito.

Veámoslo con el siguiente ejemplo. Declaramos la siguiente función:

```kotlin
fun recorrerArray(listaNumeros: IntArray, fn: (Int) -> Unit){
    for (numero in listaNumeros)
        fn(numero)
}
```

Podemos llamar a esta función pasándole por parámetro la siguiente lambda:

```kotlin
var suma = 0
var producto = 1
var arrayNumeros = IntArray(5){it}

recorrerArray(arrayNumeros){
    suma += it
    producto *= it
}
```

Como en muchas ocasiones el uso de it puede resultar confuso, podemos renombrar el parámetro de entrada:

```kotlin
...
recorrerArray(arrayNumeros){ numero ->
    suma += numero
    producto *= numero
}
```


## Rehaciendo ejemplos anteriores

Retomando el [[2DAM_PMDM/Unidad 01/7. Collections#List inmutables\|ejemplo]] que usamos para explicar la función `emptyList()`, podemos rehacerlo con expresiones lambda de la forma siguiente:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val nombreABuscar = "Telmo"
>     
>     for (nombre in buscarUsuariosPorNombre(nombreABuscar))
>         println(nombre)
>     
>     println("Hay ${buscarUsuariosPorNombre(nombreABuscar).size} ocurrencias")
> }
> fun buscarUsuariosPorNombre(nombre: String): List<String> {
>     val usuarios = listOf("Telmo", "Ana", "Alberto",
>                         "Carlos", "Mercedes", "Elena",
>                         "Telmo", "Anselmo")
>     
>     // Filtramos la lista original
>     val resultados = usuarios.filter { it.contains(nombre, ignoreCase = true) }
>     
>     // Si la lista está vacía, devuelve emptyList() de forma segura
>     return resultados.ifEmpty { emptyList() }
> }
> 
> ```

<iframe src="https://pl.kotl.in/X-61y2pSV" width="560" height="650"></iframe>


## Referencias

* _Higher-order functions and lambdas | Kotlin_. (s. f.). Kotlin Help. https://kotlinlang.org/docs/lambdas.html

# 6. Typealias

El `typealias` es literalmente el alias de un tipo de dato existente en Kotlin. El `typealias` permite al programador darle un nombre alternativo a un tipo de dato existente para simplificar el código.

Por ejemplo, si se implementa un código donde se evalúan tokens que son guardados como `String`, podemos asignarles un alias que haga más descriptivo ese `String`:

```kotlin
// Alias para un conjunto de nodos de red
typealias OToken = String
...
val tokenCliente: OToken = getTokenFromRequest() // es un String
```

También se usa para simplificar tipos de datos más complejos y extensos de escribir.  

```kotlin
// Alias para un conjunto de nodos de red
typealias NodeSet = Set<Network.Node>
...
val nodos: NodeSet

// Alias para un mapa de archivos
typealias FileTable<K> = MutableMap<K, MutableList<File>>
```

En esa misma línea, las firmas de funciones (el tipo de dato función) pueden hacerse más sencillas.  

```kotlin
// Alias para un manejador de eventos
typealias MyHandler = (Int, String, Any) -> Unit

// Alias para un predicado genérico
typealias Predicate<T> = (T) -> Boolean
```

También se puede usar para hacer referencia a clases anidadas (*nested* e *inner*).

```kotlin
class A {
    inner class Inner
}
class B {
    inner class Inner
}

// Creando alias para clases internas
typealias AInner = A.Inner
typealias BInner = B.Inner
```

> [!note] Nota 
> * Los typealiases no crean tipos de datos. Simplemente permiten llamarlos de otra forma más sencilla.
> * Son equivalentes a sus tipos subyacentes.
> * El compilador de Kotlin los expande automáticamente

```kotlin
// Definición del type alias
typealias Predicate<T> = (T) -> Boolean

// Función que usa el type alias
fun foo(p: Predicate<Int>) = p(42)

fun main() {
    // Uso directo de función lambda
    val f: (Int) -> Boolean = { it > 0 }
    println(foo(f)) // Imprime "true"

    // Usando el type alias
    val p: Predicate<Int> = { it > 0 }
    println(listOf(1, -2).filter(p)) // Imprime "[1]"
}
```


# 7. Fechas

Como ya vimos en Java en el curso anterior, podemos usar las clases **`LocalDate`** y **`LocalDateTime`** del paquete **`java.time`**.

Recordemos su uso con algunos ejemplos:

```kotlin
import java.time.LocalDateTime

fun main() {
    val fechaHoraActual = LocalDateTime.now()
    println(fechaHoraActual)  // 2024-10-13T11:00:39.219977120
}
```

Estos datos son difíciles de interpretar para nosotros, por lo que podemos darles otro formato usando la clase **`DateTimeFormatter`**:  

```kotlin
import java.time.LocalDateTime
import java.time.format.DateTimeFormatter

fun main() {
    val fechaHoraActual = LocalDateTime.now()
    val formatoFecha1 =
    	DateTimeFormatter.ofPattern("EEEE, MMMM dd, yyyy")
    val formatoFecha2 =
    	DateTimeFormatter.ofPattern("dd-MM-yyyy")
    var fechaFormateada = fechaHoraActual.format(formatoFecha1)
    println(fechaFormateada)  // Sunday, October 13, 2024

    fechaFormateada = fechaHoraActual.format(formatoFecha2)
    println(fechaFormateada)  // 13-10-2024
}
```

Lo mismo ocurre con las horas, con la clase **`LocalTime`**:  

```kotlin
import java.time.LocalTime

fun main() {
    val horaActual = LocalTime.now()
    println(horaActual)  // 11:12:16.308689063
}
```

Y aplicando formatos:  

```kotlin
import java.time.LocalTime
import java.time.format.DateTimeFormatter

fun main() {
    val horaActual = LocalTime.now()
    val formato24Horas =
    	DateTimeFormatter.ofPattern("HH:mm:ss")
    val formato12Horas =
    	DateTimeFormatter.ofPattern("hh:mm a")
    var horaFormateada = horaActual.format(formato24Horas)

    println(horaFormateada) // 11:16:48

    horaFormateada = horaActual.format(formato12Horas)
    println(horaFormateada) // 11:16 AM
}
```

