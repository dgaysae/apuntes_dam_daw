---
{"dg-publish":true,"permalink":"/2-dam-pmdm/unidad-01-introduccion-a-kotlin/","dg-note-properties":{"modulo":"[[Módulos/PMDM]]","libro":"[[Apuntes/PMDM (2º DAM)]]"}}
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


# 1. Variables y constantes

Kotlin permite declarar variables[^1] usando las siguientes palabras reservadas:

## 1.1. `var` - variables

**`var`**, o *variable*, declara las variables tal y como las conocemos. Es decir, son **variables mutables**, a las que se les pueden reasignar valores a lo largo del código. En otras palabras, las variables de toda la vida:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     var nombre = "Pepe"
>     var numero = 5
>     nombre = "Jose"
>     numero = 5
> }
> ```

<iframe src="https://pl.kotl.in/zbUjmHiRG" width="560" height="250"></iframe>

Acostumbrados a Java, hay algo que chirría, ¿no? En ninguno de los casos anteriores se indica el **tipo de dato** de cada variable. Esto no quiere decir que no tengan tipo. Es más, Kotlin tiene **tipado estático**, es decir, que cada variable tiene un **tipo de dato asociado que no cambia**:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     var nombre = "Pepe"	// String
>     var numero = 5		// Int
> 
>     nombre = 4.5	// Error, porque nombre es de tipo String.
>     numero = 5.0	// Error, porque numero es de tipo Int.
> }
> ```

<iframe src="https://pl.kotl.in/OuO_FjpTr" width="560" height="250"></iframe>

> [!info] Para más información... 
> Puedes consultar los **tipos de datos que maneja Kotlin** en la [documentación oficial][kotlin_tipos], aunque los veremos en el apartado [[2DAM_PMDM/Unidad 01/3. Tipos de datos\|3. Tipos de datos]].


## 1.2. `val` - constantes en tiempo de ejecución

**`val`**, o *value*, permite declarar **variables inmutables**. Lo que conocemos como **constantes**:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val nombre = "Pepe"
>     val numero = 5
>     nombre = "Jose"	// Error, porque nombre es inmutable.
>     numero = 5	     // Error, porque numero es inmutable.
> }
> ```

<iframe src="https://pl.kotl.in/KBoUBiMkh" width="560" height="250"></iframe>

Que sean constantes en **tiempo de ejecución** significa que **toman el valor cuando se ejecuta la aplicación**. Dicho de otra forma, admiten **valores constantes** (como los del ejemplo), o el **resultado de una expresión** (ya sea una fórmula o el resultado de una función, que se obtendrá al ejecutar el código).

## 1.3. `const val` - constantes en tiempo de compilación

En Kotlin, las constantes en tiempo de compilación son **valores conocidos antes de que el programa se ejecute**.

Se definen añadiendo `const` a la declaración de la siguiente forma: **`const val`**:

```kotlin
// Equivalente a "public static final int" en Java
const val MAX_USUARIOS = 100
const val RUTA_BASE = "/api/v1"

class Sesion {
    fun permitirAcceso(intentos: Int): Boolean {
        return intentos < MAX_USUARIOS
    }
}
```

Lo habitual es declararlas **dentro del `companion object`** o **en un archivo `.kt`**. Esto **optimiza el rendimiento**, ya que evita llamadas a métodos getter.

La diferencia entre una constante en tiempo de ejecución (`val`) y otra en tiempo de compilación (`const val`) es que en la primera el valor se calcula o se asigna **en el momento exacto en que el código se ejecuta**. En cambio, el valor de una constante en tiempo de compilación debe conocerse **antes de la ejecución**. Por tanto, a una constante `val` podemos asignarle un **valor constante o una expresión**, pero a una constante `const val` solo se le puede asignar un **valor constante**.

> [!abstract]- Código 
> ```kotlin
> import java.time.LocalTime
> 
> // 1. CONSTANTE EN TIEMPO DE COMPILACIÓN (const val)
> // El valor se define antes de que la aplicación corra. No puede cambiar nunca.
> const val TOTAL_INTENTOS_MAXIMOS = 3
> const val URL_SERVIDOR_API = "https://ejemplo.com"
> 
> fun main() {
>     println("--- Datos fijos desde el inicio ---")
>     println("Intentos permitidos: $TOTAL_INTENTOS_MAXIMOS")
>     println("Conectando a: $URL_SERVIDOR_API")
>     
>     println("\n--- Datos calculados al ejecutar ---")
>     simularInicioDeSesion("usuario_demo")
> }
> fun simularInicioDeSesion(usuario: String) {
>     // 2. CONSTANTE EN TIEMPO DE EJECUCIÓN (val)
>     // El valor exacto depende de las condiciones del momento en que se ejecuta 
>     // la línea.
>     val horaDeAcceso: LocalTime = LocalTime.now()
>     // Cambia según el momento exacto en que corras el código
>     
>     val idDeSesionUnico: String = java.util.UUID.randomUUID().toString()
>     // Genera un ID distinto en cada ejecución
>     
>     println("Usuario: $usuario")
>     println("Hora exacta de ingreso: $horaDeAcceso")
>     println("ID único de esta sesión: $idDeSesionUnico")
> }
> ```

<iframe src="https://pl.kotl.in/kfK4qYgUy" width="560" height="620"></iframe>


> [!warning] Recuerda 
> Hay que ser coherente al añadir como propiedad de una clase una constante en tiempo de compilación.
> Si no tiene sentido que esa constante esté en esa clase ni en ninguna otra, **se puede ubicar en un fichero `.kt`** junto a otras constantes (p.e. en un fichero `Utiles.kt`):
> ```kotlin
> // Fichero Utiles.kt
> const val URL_SERVIDOR_API = "https://api.ejemplo.com"
> const val TOTAL_INTENTOS_MAXIMOS = 3
> ```



[kotlin_tipos]: https://kotlinlang.org/docs/types-overview.html



[^1]:  Basic syntax | Kotlin. (s. f.-b). Kotlin Help. https://kotlinlang.org/docs/basic-syntax.html#variables

# 2. Inferencia de tipos

En los casos anteriores hemos declarado variables sin indicar en ningún caso su tipo. Esto se debe a que las variables **asumen** el tipo de dato del valor que se les asigna. A esto se le conoce como **inferencia de tipo** de dato. En el ejemplo anterior se indican algunos tipos de datos inferidos en los comentarios:

```kotlin
var nombre = "Pepe"		// String
var entero = 5			// Int
val esCierto = true		// Boolean
```

También es posible **declarar una variable sin inicializar**. En este caso se ha de indicar qué tipo de dato va a almacenar, ya que las variables **deben tener asociado un tipo de dato** en el momento en el que se declaran:

```kotlin
var nombre: String
var numero: Int
. . .
nombre = "Jose"
numero = 5
```



# 3. Tipos de datos


En Kotlin **no existen tipos de datos primitivos**, como ocurre en Java. Es decir, el **`int`** de Java no se encuentra en Kotlin.

Esto se debe a que **todo** en Kotlin **es un objeto**, **incluyendo los tipos de datos primitivos**:

```kotlin
var nombre = "Pepe"       // String
val enteroLargo = 123456L // Long
val decimalDouble = 1.32  // Double
val decimalFloat = 5.5F   // Float
var entero = 5            // Int
val hexadecimal = 0xAB    // Int
val binary = 0b01010101   // Int
```

Por tanto, el tipo de dato de una variable determina los métodos y operaciones que se pueden realizar con ella.

Los tipos de datos básicos que maneja Kotlin son: **strings, enteros, decimales** y **booleanos**.

A partir de estos tipos de datos podemos construir tipos de datos más complejos (como veremos más adelante).

> [!info] ¿Cómo identificar el tipo de dato?
> Para ver el tipo de dato de una variable, se puede usar la propiedad abstracta [**simpleName**][kotlin_simpleName] de la siguiente manera: 
> ```kotlin
> variable::class.simpleName
> ```

## 3.1. String

Las cadenas en Kotlin se representan con el tipo **`String`** y son **inmutables**.

Se expresan entre comillas dobles (`"`)

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     var nombre = "Pepe"		// String
>     println(nombre::class.simpleName)
> }
> ```

<iframe src="https://pl.kotl.in/-sWYmo3zO" width="560" height="200"></iframe>

Un `String` sigue siendo una secuencia de caracteres, al igual que en Java, por lo que Kotlin permite recorrerla carácter a carácter de forma sencilla:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     var nombre = "Pepe"
>     for (caracter in nombre ) {
>         println(caracter)
>     }
> }
> ```

<iframe src="https://pl.kotl.in/IXV1Y8vGn" width="560" height="220"></iframe>

Que sea inmutable significa al asignarle un valor, **no se pueden cambiar**. Si se reasigna otra cadena a una variable String, la cadena anterior se **desreferencia** y el ***garbage collector*** se encargará de eliminarla.

Esto también implica que cualquier método que ejecute, no cambiará el valor de la cadena. En su lugar creará otra cadena en memoria con el resultado de dicho método:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     var nombre = "Pepe"
>     
>     println(nombre.uppercase())	// el resultado no se guarda en nombre
>     println(nombre)	
> }
> ```

<iframe src="https://pl.kotl.in/_KFV5WmM7" width="560" height="220"></iframe>

Puedes concatenar cadenas usando el operador **`+`**, pero es preferible usar plantillas de cadenas o cadenas multilínea. Para hacer cadenas mutables, al igual que en Java, podemos usar la clase [**StringBuilder**][kotlin_StringBuilder].

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     var nombre = "Pepe"
>     
>     println("Buenos días, " + nombre)	// 👍
>     println("Buenos días, $nombre")		// 👍👍👍👍
> }
> ```

<iframe src="https://pl.kotl.in/v3KGXhXV_" width="560" height="220"></iframe>

* Cuando usamos el operador **`+`** con cadenas de texto hablamos de “**concatenación”**.
* Cuando usamos plantillas para referenciar a una variable, hablamos de “**expansión de variables”**. Las plantillas, también llamadas [***String Templates***][kotlin_StringTemplates], son muy útiles, ya que no solo nos permiten llamar al valor de una variable sino que también es posible usarlas para **evaluar expresiones.** 

**Para evaluar** una expresión con una plantilla debemos rodearla entre llaves (**${expresión}**).

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val uno = 1
>     val dos = 2
>     
>     println("La suma de $uno y $dos es ${uno + dos}")
> }
> ```

<iframe src="https://pl.kotl.in/NLkeEpy64" width="560" height="160"></iframe>

### Literales de Cadenas

Kotlin tiene [**cadenas de escape**][kotlin_EscapedString] (es decir, "comandos" o caracteres que hacen algo en el texto) y [**cadenas multilínea**][kotlin_cadenasMultilinea] (delimitadas por triple comillas).

* Cadenas ***de escape***: contienen caracteres especiales que implican una acción: retorno de carro, tabulador, etc.

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val saludo = "Hola, Pepe!\nCómo ha ido el día?"
>     
>     println(saludo)
> }
> ```

<iframe src="https://pl.kotl.in/zq-KIgScH" width="560" height="180"></iframe>

* Cadenas **multilínea**: permite escribir un texto sin necesidad de usar caracteres *escapados*. Para ello, dicha cadena se delimita por triples comillas dobles.

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val saludo = """Hola, Pepe!
>     Cómo ha ido el día?"""		// no necesita \n
>     
>     println(saludo)
> }
> ```

<iframe src="https://pl.kotl.in/n0196Hyk-" width="560" height="180"></iframe>

  Un método muy útil para evitar problemas de formato con las cadenas multilínea es **`.trimIndent()`**, que permite eliminar todos los espacios en blanco al principio de cada línea del `String`. De esta forma se puede escribir el literal de forma más legible sin que eso afecte a lo que se muestra por pantalla.

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val saludo = """
>             Hola, Pepe!
>             Cómo ha ido el día?
>              """.trimIndent()    //Ignora espacios 
>     
>     println(saludo)
> }
> ```

<iframe src="https://pl.kotl.in/ocvq4CrgT" width="560" height="180"></iframe>

### Operaciones básicas de String

Existen muchas semejanzas con Java en algunas de las funcionalidades que ofrece la clase `String`:

```kotlin
fun main() {
    val nombre = "Anselmo"

    // ************************************
    // Longitud de la cadena
    // ************************************
    println("Longitud de la cadena -------------")
    println("La longitud de $nombre es ${nombre.length}")

    // ************************************
    // Extracción de subcadenas
    // ************************************
    println("Extracción de subcadenas -------------")
    println(nombre.substring(1, 7))  // nselm
    println(nombre.substring(2))  // selmo

    // ************************************
    // Sustituir caracter o subcadena en una cadena
    // ************************************
    println("Sustituir caracter o subcadena en una cadena -------------")
    println(nombre.replace("Ans", "T"))  // Telmo

    // ************************************
    // Cambiar a mayúsculas/minúsculas
    // ************************************
    println("Cambiar a mayúsculas/minúsculas -------------")
    println(nombre.uppercase())  // ANSELMO
    println(nombre.lowercase())  // anselmo

    // ************************************
    // Inspeccionar contenido de la cadena
    // ************************************
    println("Inspeccionar contenido de la cadena -------------")
    println(nombre.contains("a"))  // false
    println(nombre.contains("A"))  // true

    println("Esto es un ejemplo".startsWith("Esto"))  // true

    println("www.iescelia.org".endsWith(".com"))  // false

    // ************************************
    // Dividir una cadena con un split
    // ************************************
    println("Dividir una cadena con un split -------------")
    val nombres = "Telmo, Merche, Alberto, Isabel, Manu, José Luis"
    println(nombres.split(", "))
    // [Telmo, Merche, Alberto, Isabel, Manu, José Luis]

    // ************************************
    // Comparación de cadenas
    // ************************************
    println("Comparación de cadenas -------------")
    println(nombre.compareTo("anselmo"))  // valor negativo
    println("anselmo".compareTo(nombre))  // valor positivo
    println(nombre.compareTo("Anselmo"))  // 0, ya que son iguales

    // Eliminar espacios:
    println("Eliminar espacios -------------")
    val cadenaConEspacios = "   Hola, mundo!   "
    println("---$cadenaConEspacios---")          // ---   Hola, mundo!   ---
    println("---${cadenaConEspacios.trim()}---") // ---Hola, mundo!---
}
```

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val nombre = "Anselmo"
>     
>     // ************************************
>     // Longitud de la cadena
>     // ************************************
>     println("Longitud de la cadena -------------")
>     println("La longitud de $nombre es ${nombre.length}")
>     
>     // ************************************
>     // Extracción de subcadenas
>     // ************************************
>     println("Extracción de subcadenas -------------")
>     println(nombre.substring(1, 7))  // nselm
>     println(nombre.substring(2))  // selmo
>     
>     // ************************************
>     // Sustituir caracter o subcadena en una cadena
>     // ************************************
>     println("Sustituir caracter o subcadena en una cadena -------------")
>     println(nombre.replace("Ans", "T"))  // Telmo
>     
>     // ***********************************
>     // Cambiar a mayúsculas/minúsculas
>     // ************************************
>     println("Cambiar a mayúsculas/minúsculas -------------")
>     println(nombre.uppercase())  // ANSELMO
>     println(nombre.lowercase())  // anselmo
>     
>     // ************************************
>     // Inspeccionar contenido de la cadena
>     // ************************************
>     println("Inspeccionar contenido de la cadena -------------")
>     println(nombre.contains("a"))  // false
>     println(nombre.contains("A"))  // true
>     
>     println("Esto es un ejemplo".startsWith("Esto"))  // true
>     
>     println("www.iescelia.org".endsWith(".com"))  // false
>     
>     // ************************************
>     // Dividir una cadena con un split
>     // ************************************
>     println("Dividir una cadena con un split -------------")
>     val nombres = "Telmo, Merche, Alberto, Isabel, Manu, José Luis"
>     println(nombres.split(", "))
>     // [Telmo, Merche, Alberto, Isabel, Manu, José Luis]
>     
>     // ************************************
>     // Comparación de cadenas
>     // ************************************
>     println("Comparación de cadenas -------------")
>     println(nombre.compareTo("anselmo"))  // valor negativo
>     println("anselmo".compareTo(nombre))  // valor positivo
>     println(nombre.compareTo("Anselmo"))  // 0, ya que son iguales
>     
>     // Eliminar espacios:
>     println("Eliminar espacios -------------")
>     val cadenaConEspacios = "   Hola, mundo!   "
>     println("---$cadenaConEspacios---")          // ---   Hola, mundo!   ---
>     println("---${cadenaConEspacios.trim()}---") // ---Hola, mundo!---
> }
> ```

<iframe src="https://pl.kotl.in/oUuZrfB8R" width="560" height="1250"></iframe>

Kotlin plantea, en cambio, otras operaciones de forma **más sencilla**.

Por ejemplo, en lugar del `.charAt(int indice)` de Java, Kotlin permite acceder al carácter de una posición indicando el índice como en un array:

```kotlin
// ************************************
// Dividir una cadena con distintas líneas en un array
// (mismo efecto que split)
// ************************************
val nombre = "Telmo"
println(nombre[0])  // T
println(nombre[1])  // e
println(nombre[2])  // l
println(nombre[3])  // m
println(nombre[4])  // o
```

O iterar la cadena con un for-each:

```kotlin
val nombre = "Telmo"

for (letra in nombre) {
    println(letra)
}
```

> [!info] 
> Esto último en Java tendríamos que hacerlo convirtiendo `nombre` en un array de `char`.

Por ejemplo, si tenemos una cadena dividida en líneas (`\n`), podemos hacer un split por líneas usando el método `.lines()`:

```kotlin
// ************************************
// Dividir una cadena con distintas líneas en un array
// (mismo efecto que split)
// ************************************
val nombres = "Telmo\nMerche\nAlberto\nIsabel\nManu\nJosé Luis"
println(nombres.lines())
// [Telmo, Merche, Alberto, Isabel, Manu, José Luis]
```

Pero la más llamativa, la que tantos problemas suele dar en Java, es la **compboración de igualdad de cadenas**. Mientras que en Java hay que usar el método `.equals()` para ver si dos cadenas son iguales, **¡ en Kotlin se puede usar el comparador \=\= !**

```kotlin
val nombre = "Telmo"
println(nombre == "Juan")  // false
println(nombre == "Telmo") // true
```

> [!info]  
> El operador \=\= hace una **[[2DAM_PMDM/Unidad 01/6. Comparadores estructurales y referenciales#Comparadores estructurales\|comparación estructural]]**, que estudiaremos más adelante.

### Formato de String

La función [**`String.format()`**][kotlin_StringFormat] permite formatear cadenas con especificadores de formato, similar a Java. Esta función acepta una cadena de formato (con *placeholders*) y uno o más argumentos. La cadena de formato contiene un **marcador de posición** o ***placeholder*** (indicado por **`%`**) para un argumento específico, seguido de especificadores de formato.

Estos especificadores de formato son instrucciones de formateo para el argumento correspondiente, y están compuestos por:

* ***Flags***: opciones de alineación y formato.

* ***Width*** (ancho): longitud mínima del resultado.

* ***Precision*** (precisión): número de decimales o caracteres a mostrar.

* ***Conversion type*** (tipo de conversión): especifica el tipo de dato (entero, flotante, cadena, etc.).

Algunos especificadores comunes incluyen:

* `%d` para enteros.

* `%f` para números de punto flotante.

* `%s` para cadenas.

También puedes usar la sintaxis **`argument_index$`** para referenciar el mismo argumento varias veces en diferentes formatos dentro de la misma cadena.

> [!info]  
> Puedes consultar la **lista completa de especificadores de formato**, en la [documentación de la clase `Formatter` de Java][kotlin_Formater].

Ejemplos:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     /*
>      Formatea un nº entero añadiendo 0 a la izquierda hasta
>      llegar a los 7 caracteres de longitud
>      */
>     val integerNumber = String.format("%07d", 31416)
>     println(integerNumber)
>     
>      /*
>      Formatea un número decimal para mostrar un signo '+'
>      y 4 decimales (redondeando).
>      */
>      val floatNumber = String.format("%+.4f", 3.141592)
>      println(floatNumber)
>     
>      /*
>      Formatea dos cadenas en mayúsculas, cada una ocupando un
>      marcador de posición.
>      */
>      val helloString = String.format("%S %S", "hello", "world")
>      println(helloString)
>
>      /*
>      Mete el número negativo entre paréntesis y luego lo repite.
>      */
>      val negativeNumberInParentheses =
>          String.format("%(d means %1\$d", -31416)
>      println(negativeNumberInParentheses)
> }
> ```

<iframe src="https://pl.kotl.in/fzwcNuEd9" width="560" height="680"></iframe>


## 3.2. Números

> [!info] Números en Kotlin
> Puedes ampliar este apartado consultando la documentación oficial de [**Numbers**][kotlin_Numbers].

### Enteros

Para los números enteros, existen cuatro tipos con diferentes tamaños y rangos de valores:

| Tipo | Tamaño (bits) | Valor mínimo | Valor máximo |
| :---: | :---: | ----- | ----- |
| **Byte** | 8 | -128 | 127 |
| **Short** | 16 | -32,768 | 32,767 |
| **`Int`** | 32 | -2,147,483,648 (-2<sup>31</sup>) | 2,147,483,647 (2<sup>31</sup> - 1) |
| **Long** | 64 | -9,223,372,036,854,775,808 (-2<sup>63</sup>) | 9,223,372,036,854,775,807 (2<sup>63</sup> - 1) |

Cuando se inicializa una variable sin especificar explícitamente el tipo, el compilador **infiere** automáticamente el tipo más pequeño que pueda representar el valor, comenzando desde **`Int`**. Si el valor excede el rango de **`Int`**, el tipo será **Long**. Para especificar un valor como **Long**, añade el sufijo **L** al valor.

```kotlin
val one = 1                     // Int
val threeBillion = 3000000000   // Long
val oneLong = 1L                // Long 
val oneByte: Byte = 1 
```

> [!info] Enteros sin signo
> Dentro de los enteros, Kotlin también proporciona los tipos de [**enteros sin signo**][kotlin_Enteros_sin_signo].

### Reales

Kotlin también proporciona los tipos de números reales `Float` y `Double`, que cumplen con el estándar **IEEE 754**.

| Tipo | Tamaño (bits) | Bits significativos | Bits de exponente | Dígitos decimales |
| :---: | :---: | :---: | :---: | :---: |
| **`Float`** | 32 | 24 | 8 | 6-7 |
| **`Double`** | 64 | 53 | 11 | 15-16 |

Puedes inicializar variables de tipo `Float` y `Double` con números que tengan una parte fraccionaria separada por un punto (`.`). El compilador infiere el tipo `Double` para estos valores:

```kotlin
val pi = 3.14        // Double  
val oneDouble = 1.0  // Double 
```

Para especificar explícitamente un valor como `Float`, añade el sufijo f o F. Si el número tiene más de 6-7 dígitos decimales, será redondeado:

```kotlin
val e = 2.7182818284        // Double  
val eFloat = 2.7182818284f  // Float, valor real: 2.7182817 
```

### Conversión de tipos numéricos

En Kotlin, **no hay conversiones automáticas** entre tipos numéricos más pequeños y más grandes. Por ejemplo, si una función admite como parámetro un `Double`, no podremos invocarla con argumentos de tipo `Int` o `Double`:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     fun printDouble(d: Double) {
>         print(d)
>     }
>     
>     val i = 1
>     val d = 1.0
>     val f = 1.0f
>     
>     printDouble(d)
>     // printDouble(i) // Error: Type mismatch
>     // printDouble(f) // Error: Type mismatch 
> }
> ```

<iframe src="https://pl.kotl.in/Jq46ZaBRY" width="560" height="320"></iframe>

Todos los tipos numéricos soportan conversiones a otros tipos mediante funciones como

* `toByte()`: `Byte`
* `toShort()`: `Short`
* `toInt()`: `Int`
* `toLong()`: `Long`
* `toFloat()`: `Float`
* `toDouble()`: `Double`

### Operaciones con números

Kotlin soporta las operaciones aritméticas estándar: `+`, `-`, `*`, `/`, `%`. Estas operaciones están **sobrecargadas** para realizar automáticamente las conversiones necesarias:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     println(1 + 2)
>     println(2_500_000_000L - 1L)
>     println(3.14 * 2.71)
>     println(10.0 / 3)
> }
> ```

<iframe src="https://pl.kotl.in/KtbtErfG2" width="560" height="250"></iframe>

> [!info]  
> La segunda línea del ejemplo anterior usa `_` intercalados con el número. No te preocupes, solo son separadores de miles. Puedes verlo en el apartado [[2DAM_PMDM/Unidad 01/3. Tipos de datos#Uso de guiones bajos para mejorar la legibilidad\|Uso de guiones bajos para mejorar la legibilidad]] más adelante.

Para obtener divisiones precisas entre enteros, convierte explícitamente uno de los operandos a un tipo decimal:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val x = 5 / 2.toDouble()
>     println(x == 2.5)
> }
> ```

<iframe src="https://pl.kotl.in/YT4qq3J-H" width="560" height="250"></iframe>


### Constantes literales en números

En Kotlin, puedes usar diferentes tipos de constantes literales para números integrales y de punto flotante.

### Constantes literales para valores enteros

* **Decimales**: se escriben directamente como números.
  ```kotlin
  val decimalValue = 123
  ```

* **Long**: se identifican con una **`L`** al final del número.
  ```kotlin
  val longValue = 123L
  ```

* **Hexadecimales**: se prefijan con **`0x`** o **`0X`**.
  ```kotlin
  val hexValue = 0x0F
  ```

* **Binarios**: se prefijan con **`0b`** o **`0B`**.
  ```kotlin
  val binaryValue = 0b00001011
  ```

> [!warning] ¡Ojo! 
> Los octales no están soportados en Kotlin

### Constantes literales para valores de punto flotante

* **`Double`**: es el tipo predeterminado para valores con parte decimal o en **notación científica**.
  ```kotlin
  val doubleValue = 123.5
  val scientificDouble = 123.5e10 // Notación científica
  ```

* **`Float`**: se identifican con un sufijo **`f`** o **`F`**.
  ```kotlin
  val floatValue = 123.5f
  ```

### Uso de guiones bajos para mejorar la legibilidad

Puedes usar guiones bajos (**`_`**) en números para hacerlos más legibles. Esto no afecta al valor numérico.

```kotlin
val oneMillion = 1_000_000
val creditCardNumber = 1234_5678_9012_3456L
val socialSecurityNumber = 999_99_9999L
val hexBytes = 0xFF_EC_DE_5E
val bytes = 0b11010010_01101001_10010100_10010010
```


### Constantes literales para enteros sin signo

Kotlin también admite constantes literales específicas para enteros sin signo.

> [!info] Para más información... 
> ...consulta la documentación oficial para [tipos enteros sin signo][kotlin_literales_nteros_sin_signo].

## 3.3. Lógicos

> [!info] Boolean en Kotlin
> Puedes ampliar este apartado consultando la documentación oficial de [**Boolean**][kotlin_boolean].

Un objeto booleano puede representar dos valores **`true`** y **`false`**. Recuerda que a diferencia de Java, **`Boolean`** no puede ser nulo. Su contraparte **`nullable`** es **`Boolean`**.

> [!info] ¡No ocupan un bit!
> En la JVM, los objetos `Boolean` que se guardan como el primitivo `boolean` **ocupan 1 byte**.

### Operaciones con booleanos

| Operación | Operador | Lógica |
| :---: | :---: | :---: |
| Disyunción | \|\| | OR |
| Conjunción | `&&` | AND |
| Negación | `!` | NOT |

> [!info] Operadores vagos 
> Los operadores booleanos funcionan de forma "perezosa" en todos los lenguajes de programación.
> Esto quiere decir que si el primer operando es `true`, `||` no evaluará el segundo operando. Si el primer operando es `false`, `&&` no evaluará el segundo operando.

## 3.4. Caracteres

Los caracteres en Kotlin son representados con el tipo **`Char`** y sus literales pueden ir entre comillas simples **'C'**. Aunque normalmente los literales de caracteres suelen ser de un único carácter, también podemos encontrar secuencias escapadas de Unicode entre comillas simples cumpliendo con la misma función.

> [!info]  
> En la JVM los objetos de tipo `Char` se guardan como el primitivo `char`, representando un carácter Unicode de **16 bits**.

Los caracteres especiales pueden ser escapados con una barra invertida \\.

* `\t` - Tabulación  
* `\b` - Barra de retroceso  
* `\n` - Nueva línea  
* `\r` - Retorno de carro  
* `\'` - Comilla simple  
* `\"` - Comilla doble  
* `\\` - Barra invertida  
* `\$` - Signo de dólar

También es posible codificar los caracteres utilizando una secuencia escapada de Unicode:

```kotlin
println('\uFF00')
```

## 3.5. Arrays

Los arrays son **estructuras estáticas** de datos que se almacenan en **posiciones contiguas** en la memoria principal (RAM).

Son estáticas porque no pueden/deben cambiar su tamaño durante la ejecución del programa. Por ejemplo, una nueva posición en el array debería ubicarse al final de la estructura, en la última posición adyacente a la de la última que haya en ese momento. El problema es que **no se puede saber** si dicha posición estará ocupada por otros datos de ese u otros programas.

> [!info]  Array vs ArrayList
> Es importante tener clara la diferencia entre un `Array` (estático) y un `ArrayList` (dinámico... aunque con trampa). En [este vídeo](https://www.youtube.com/watch?v=VHhc-ndfI-Y) de nuestro amigo [Brais Moure][web_brais_moure], a la hora de definir un array, realmente está declarando un `ArrayList`. Cuidado con estos despistes...

#### Crear arrays

Podemos crear un array de varias formas.

* Con la function **`arrayOf()`**:
> [!abstract]- Código 
> ```kotlin
> fun main() {
>     var arrayCorto = arrayOf(1, 2, 3)
>     println(arrayCorto.joinToString())
>      /*
>      * ...
>      * Si necesitamos un array más grande
>      * ...
>      */
>      arrayCorto = arrayOf(1, 2, 3, 4, 5, 6)
>      /*
>      * El array anterior (1, 2, 3) queda desreferenciado
>      * en memoria hasta que el garbage collector se
>      * ocupe de él.
>      */
>      println(arrayCorto.joinToString())
> }
> ```
  
  <iframe src="https://pl.kotl.in/85X2ums9_" width="560" height="400"></iframe>

* A partir de un [[2DAM_PMDM/Unidad 01/10. Rangos\|rango]]:  

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val arrayNotasExamen = arrayOf(1..6)
>     println(arrayNotasExamen::class.simpleName)
>     println(arrayNotasExamen.joinToString())
> }
> ```
  
  <iframe src="https://pl.kotl.in/pLrzhdgmX" width="560" height="200"></iframe>

* Con el constructor **`Array`**, indicando el **tipo de los datos** que guarda (entre `< >` del genérico), el **tamaño inicial** (entre paréntesis) y **un valor inicial** (entre llaves) para todos los elementos:


> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val arrayNotasExamen = Array<Int>(6){10}
>     println(arrayNotasExamen.joinToString())
> }
> ```
  
  <iframe src="https://pl.kotl.in/boGVIqEDT" width="560" height="200"></iframe>

* Con el constructor **`Array`**, indicando el **tamaño inicial** (entre paréntesis) y **una función** que genera cada elemento del array indicando su índice:


> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val arrayNumeros = Array(10, { i -> i + 10 })
>     println(arrayNumeros::class.simpleName)
>     println(arrayNumeros.joinToString())
>     
>     val arrayTextos = Array(10, { i -> (i + 10).toString() })
>     println(arrayTextos::class.simpleName)
>     println(arrayTextos.joinToString())
> }
> ```
  
  <iframe src="https://pl.kotl.in/KPxkKs-50" width="560" height="320"></iframe>

Internamente, Kotlin usa clases para abstraer arrays de distintos tipos de datos para evitar el ***boxing-unboxing***[^2] de sus elementos y convertirlos en datos primitivos, que son los que finalmente usará la JVM. Estas clases son: [ByteArray][kotlin_ByteArray], [CharArray][kotlin_CharArray], [ShortArray][kotlin_ShortArray], [IntArray][kotlin_IntArray], [LongArray][kotlin_LongArray], [BooleanArray][kotlin_BooleanArray], [FloatArray][kotlin_FloatArray] y [DoubleArray][kotlin_DoubleArray].

> [!info] Recomendación 
> En la [documentación oficial][kotlin_arrays] se recomienda **limitar el uso de arrays a situaciones muy específicas**.
> 
> En Kotlin se aconseja usar colecciones en lugar de arrays. El motivo es que los arrays son estructuras estáticas de datos, es decir, que son inmutables y no cambian durante la ejecución del programa. Al igual que el `String`, si se necesita otro array de distinto tamaño al establecido inicialmente, hay que crearlo en memoria y *desreferenciar* al anterior.
> 
> Por eso es preferible utilizar [colecciones][kotlin_collections].

#### Acceso y modificación

Leer o modificar los elementos de un array se hace de forma similar a Java:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val arrayNumeros = Array(10, { i -> i + 10 })
>     println(arrayNumeros.joinToString())
>     
>     println(arrayNumeros[5])
>     arrayNumeros[5] = 0
>     println(arrayNumeros.joinToString())
> }
> ```
> 
<iframe src="https://pl.kotl.in/TFI9HDiQe" width="560" height="320"></iframe>

Aunque lo veremos en los [[2DAM_PMDM/Unidad 01/10. Rangos\|rangos]], se puede usar el operador **`in`** para comprobar si un elemento está incluido en un array:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     var arrayCorto = arrayOf(1, 24, 3)
>     println(24 in arrayCorto)
> }
> ```

<iframe src="https://pl.kotl.in/r0AsZ5VSj" width="560" height="250"></iframe>

Podemos recorrer un array de distintas formas:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val arrayNumeros = Array(10, { i -> i + 10 })
>     // Elemento a elemento del array
>     for (numero in arrayNumeros)
>         println(numero)
>     
>     println("-------------------------------")
>     // A través de su RANGO DE ÍNDICES
>     for (indice in arrayNumeros.indices) {
>         //println(arrayNumeros[indice])
>         println(arrayNumeros.get(indice))
>     }
>     
>     println("-------------------------------")
>     // A través de los índices hasta el último
>     for (indice in 0 .. arrayNumeros.size - 1) {
>         println(arrayNumeros[indice])
>         //println(arrayNumeros.get(indice))
>     }
> }
> ```

<iframe src="https://pl.kotl.in/WVa7aLIUx" width="560" height="250"></iframe>

## 3.6. Matrices

Como ya vimos en Java, **una matriz es un array de arrays**. Es decir, un array que en cada una de sus posiciones almacena otro array[^3]. Aunque para verlo de forma más intuitiva lo resumimos diciendo que se representa como una tabla de datos.

Podemos crear una matriz de diferentes formas:

* Mediante el uso del **`arrayOf()`**:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     //Creación de matriz a partir de arrayOf()
>     var matrizForma1 = arrayOf(
>         arrayOf(1,2,3),
>         arrayOf(4,5,6),
>         arrayOf(7,8,9))
>     /*
>      * Creación de matriz a partir de un arrayOf(), y
>      * dentro con constructores inicializándolos a 0
>      */
>     var matrizForma2 = arrayOf(
>         Array<Int> (3) { 0 },
>         Array<Int> (3) { 0 },
>         Array<Int>(3) { 0 })
>         
>     /*
>      * También mencionar que puede ser todo tipo de variables
>      * (String, Int, Double, etc,...)
>      */
>     //Imprimir la primera matriz
>     for (row in matrizForma1) {
>         println(row.contentToString())
>     }
>     
>     println("\n")
>     
>     //Imprimir la segunda matriz
>     for (row in matrizForma2) {
>         println(row.contentToString())
>     }
> }
> ```

<iframe src="https://pl.kotl.in/RecBrRnbB" width="560" height="690"></iframe>

* Podemos utilizar **`Array()`** de forma genérica para facilitar la construcción de matrices. Si creamos una función auxiliar facilitaremos bastante la creación de matrices de distintos tipos:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val matrizStrings = crearMatriz(3, 3, "*")
>     //Podemos acceder al valor de la matriz y modificarlo/Imprimirlo
>     
>     matrizStrings[1][1] = "-"
>     // Recorrer y mostrar la matriz de Strings
>     for (fila in matrizStrings) {
>         for (elemento in fila) {
>             print(elemento)
>         }
>         println()
>     }
> }
> fun crearMatriz(
>         filas: Int,
>         columnas: Int,
>         valorInicial: String): Array<Array<String>>
> {
>     return Array(filas) { Array(columnas) { valorInicial } }
> }
> ```

<iframe src="https://pl.kotl.in/moMBGShXp" width="680" height="380"></iframe>

¡Ojo! Con el bucle de arriba recorreremos los elementos de la matriz usando `for-each` de Kotlin, pero… ¿Y si queremos acceder a los índices para modificar el valor de los elementos, igual que hacíamos en Java? Para ello podemos acceder a la propiedad **`indices`**, presente en las colecciones:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val matrizStrings = crearMatriz(3, 3, "*")
>     //Podemos acceder al valor de la matriz y modificarlo/Imprimirlo
>     
>     matrizStrings[1][1] = "-"
>     // Recorrer y mostrar la matriz de Strings usando los índices
>     for (i in matrizStrings.indices) {
>         for (j in matrizStrings[i].indices) {
>             println("matrizStrings[$i][$j] = ${matrizStrings[i][j]}")
>         }
>     }
> }
> fun crearMatriz(
>         filas: Int,
>         columnas: Int,
>         valorInicial: String): Array<Array<String>>
> {
>     return Array(filas) { Array(columnas) { valorInicial } }
> }
> ```

<iframe src="https://pl.kotl.in/lI4GeSwBx" width="680" height="480"></iframe>

Observa que aunque hemos declarado la matriz como inmutable con un **`val`**, podemos modificar su contenido. Esto es porque la **referencia en memoria no cambia**, ya que **NO reasignamos** en ningún momento la variable.

* En muchas ocasiones es necesario hacer una **matriz que sea irregular**, para ello, lo más sencillo sería hacer lo siguiente 

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     //Creación de matriz irregular
>     val matriz = arrayOf(
>         arrayOf(1, 2, 3),
>         arrayOf(4, 5),
>         arrayOf(6, 7, 8, 9))
>     
>     //Imprimir la matriz
>     for (row in matriz) {
>         println(row.contentToString())
>     }
> }
> ```

<iframe src="https://pl.kotl.in/MnTSXOUx3" width="600" height="250"></iframe>

* Es importante también mencionar que podremos hacer **matrices de más de dos dimensiones o multidimensionales**. Este es un ejemplo de una matriz de tres dimensiones.

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     //Creación de matriz 3 dimensiones, inicializada a 0
>     val matrizTresDimensiones = Array(3) { Array(3) { Array<Int>(3) { 0 } } }
>     
>     //Imprimir la matriz
>     for (row in matrizTresDimensiones) {
>         println(row.contentDeepToString())
>     }
> }
> ```

<iframe src="https://pl.kotl.in/ZEyi7fIyW" width="600" height="250"></iframe>

> [!question] ¿Sabías que ...? 
> Para poder visualizar una matriz en consola, es recomendable usar el método **`contentToString()`**. Pero **con más de 2 dimensiones** sólo mostrarán las direcciones de memoria en cada caso. Para estos últimos, el método **`contentDeepToString()`** que permite ver la matriz en su totalidad:
> ```kotlin
>     for (fila in matriz) {
>         println(fila.contentToString())
>     }
> ```

### Comparar arrays

Para comparar los elementos que contienen dos arrays (en el mismo orden) usaremos los métodos **`contentEquals()`** y **`contentDeepEquals()`**.

#### `contentEquals()`

Permite comprobar si dos arrays son **estructuralmente iguales**, esto es, que tengan tanto el **mismo tamaño**, como que sus elementos aparezcan en la **misma posición** y que **sean iguales**. Obviamente devuelve un valor lógico.

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val array = arrayOf("manzanas", "naranjas", "limon")
>     
>     //mismo tamaño, mismos elementos
>     println(array.contentEquals(arrayOf("manzanas", "naranjas", "limon")))
>     // true
>     
>     //diferente tamaño
>     println(array.contentEquals(arrayOf("apples", "oranges")))
>     // false
>     
>     //los elementos están intercambiados
>     println(array.contentEquals(arrayOf("manzanas", "limon", "naranjas")))
>     // false
> }
> ```

<iframe src="https://pl.kotl.in/ZWrtZg2p9" width="560" height="350"></iframe>

#### `contentDeepEquals()`

Para comparar si son estructuralmente iguales de forma profunda, esto es, que tengan el **mismo tamaño** y que los arrays que contienen en cada posición son iguales (ver [[2DAM_PMDM/Unidad 01/3. Tipos de datos#`contentEquals()`\|3. Tipos de datos#`contentEquals()`]]. Como puede deducirse, también devuelve `true` o `false`.

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val primerArray = arrayOf(intArrayOf(1, 0),
>                               intArrayOf(0, 1))
>     
>     val segundaArray = arrayOf(intArrayOf(1, 0),
>                               intArrayOf(0, -1))
>     // Los elementos de la posición [1][1] no son iguales
>     println(primerArray.contentDeepEquals(segundaArray))
>     // false
>     
>     segundaArray[1][1] = 1
>     println(primerArray.contentDeepEquals(segundaArray))
>     // true
> }
> ```

<iframe src="https://pl.kotl.in/O6mvA93Nz" width="560" height="350"></iframe>

> [!waning] Importante 
> En el caso de los arrays, los operadores de comparación **\=\=** y **!=** comprueban si ambas variables hacen referencia al mismo array (a la misma posición de memoria). Es decir, el contenido de dos arrays **no debe compararse con estos operadores**.




[kotlin_StringOperations]: https://kotlinlang.org/docs/strings.html#basic-string-operations
[kotlin_simpleName]: https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.reflect/-k-class/simple-name.html
[kotlin_StringBuilder]: https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.text/-string-builder/
[kotlin_StringTemplates]: https://kotlinlang.org/docs/strings.html#string-templates
[kotlin_EscapedString]: https://kotlinlang.org/docs/strings.html#escaped-strings
[kotlin_cadenasMultilinea]: https://kotlinlang.org/docs/strings.html#multiline-strings
[kotlin_StringFormat]: https://kotlinlang.org/docs/strings.html#string-formatting
[kotlin_Formater]: https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Formatter.html
[kotlin_Numbers]: https://kotlinlang.org/docs/numbers.html
[kotlin_Enteros_sin_signo]: https://kotlinlang.org/docs/unsigned-integer-types.html
[kotlin_literales_nteros_sin_signo]: https://kotlinlang.org/docs/unsigned-integer-types.html
[kotlin_boolean]: https://kotlinlang.org/docs/booleans.html
[web_brais_moure]: https://mouredev.com/brais-moure/
[kotlin_ByteArray]: https://kotlinlang.org/api/core/kotlin-stdlib/kotlin/-byte-array/
[kotlin_CharArray]: https://kotlinlang.org/api/core/kotlin-stdlib/kotlin/-char-array/
[kotlin_ShortArray]: https://kotlinlang.org/api/core/kotlin-stdlib/kotlin/-short-array/
[kotlin_IntArray]: https://kotlinlang.org/api/core/kotlin-stdlib/kotlin/-int-array/
[kotlin_LongArray]: https://kotlinlang.org/api/core/kotlin-stdlib/kotlin/-long-array/
[kotlin_BooleanArray]: https://kotlinlang.org/api/core/kotlin-stdlib/kotlin/-boolean-array/
[kotlin_FloatArray]: https://kotlinlang.org/api/core/kotlin-stdlib/kotlin/-float-array/
[kotlin_DoubleArray]: https://kotlinlang.org/api/core/kotlin-stdlib/kotlin/-double-array/
[kotlin_arrays]: https://kotlinlang.org/docs/arrays.html
[kotlin_collections]: https://kotlinlang.org/docs/collections-overview.html



[^2]:  Caules, C. Á. (2025, 15 junio). _Java Boxing y sus curiosidades_. Arquitectura Java. https://www.arquitecturajava.com/java-boxing-y-sus-curiosidades/

[^3]:  ***Nested Arrays*** | Kotlin. (s. f.). Kotlin Help. https://kotlinlang.org/docs/arrays.html#nested-arrays


[^9]:  Basic syntax | Kotlin. (s. f.-c). Basic Sintax. ***Ranges***. [https://kotlinlang.org/docs/basic-syntax.html#ranges](https://kotlinlang.org/docs/basic-syntax.html#ranges)

[^10]:  Idioms. (2024, September 25). Kotlin. Retrieved October 3, 2024, from [https://kotlinlang.org/docs/idioms.html#iterate-over-a-range](https://kotlinlang.org/docs/idioms.html#iterate-over-a-range)

[^11]:  MoureDev by Brais Moure. (2019b, agosto 8). KOTLIN: ***Curso ANDROID desde CERO - SENTENCIA WHEN - Lección 4 [2020] | Español*** | MoureDev [Vídeo]. YouTube. [https://www.youtube.com/watch?v=ufsrPf7vao4](https://www.youtube.com/watch?v=ufsrPf7vao4)

[^12]:  Conditions and loops | Kotlin. (s. f.). Kotlin Help. [https://kotlinlang.org/docs/control-flow.html#for-loops](https://kotlinlang.org/docs/control-flow.html#for-loops)

[^13]:  Conditions and loops | Kotlin. (s. f.-b). Kotlin Help. [https://kotlinlang.org/docs/control-flow.html#while-loops](https://kotlinlang.org/docs/control-flow.html#while-loops)

[^14]:  Conditions and loops | Kotlin. (s. f.-b). Kotlin Help. [https://kotlinlang.org/docs/control-flow.html#while-loops](https://kotlinlang.org/docs/control-flow.html#while-loops)

[^15]:  Anncode, & Anncode. (2023, 21 septiembre). ***Constructor Primario y Secundario en Kotlin - anncode***. anncode - [Android Native, Kotlin, Geek & Teacher]. [https://anahisalgado.com/multiples-constructores-en-kotlin-guia-de-constructores-con-ejemplos-practicos/](https://anahisalgado.com/multiples-constructores-en-kotlin-guia-de-constructores-con-ejemplos-practicos/)

[^16]:  Properties | Kotlin. (s. f.). Kotlin Help. [https://kotlinlang.org/docs/properties.html#getters-and-setters](https://kotlinlang.org/docs/properties.html#getters-and-setters)

[^17]:  Revelo, J. (2021, 25 agosto). Clases en Kotlin - develou. Develou. [https://www.develou.com/clases-en-kotlin/](https://www.develou.com/clases-en-kotlin/)

[^18]:  Inheritance | Kotlin. (s. f.). Kotlin Help. [https://kotlinlang.org/docs/inheritance.html](https://kotlinlang.org/docs/inheritance.html)

[^19]:  Type aliases | Kotlin. (s. f.). Kotlin Help. [https://kotlinlang.org/docs/type-aliases.html](https://kotlinlang.org/docs/type-aliases.html)


# 4. static en Kotlin

En Kotlin, el término **`static` no existe**. Pero el concepto sí y se expresa con **`companion object`**.

Los miembros dentro del bloque del `companion object` se comportan como miembros estáticos de Java:

> [!abstract]- Código 
> ```kotlin
> class MiClase {
>     companion object {
>         val MI_CONSTANTE = "Hola"
>         var contador = 0
>         fun saludar() {
>             println("Hola desde un método estático")
>         }
>     }
> }
> fun main() {
>     // Se accede directamente por el nombre de la clase
>     println(MiClase.MI_CONSTANTE)
>     MiClase.saludar()
> }
> ```

<iframe src="https://pl.kotl.in/gICSPrDVO" width="560" height="450"></iframe>


# 5. object

En Kotlin, la palabra clave `object` se utiliza para **declarar una clase y crear una instancia de ella al mismo tiempo**. Se usa principalmente en tres escenarios:

## Declaraciones de objetos - Singleton

Es la forma nativa de crear un **Singleton**, una única instancia de una clase en toda la aplicación. Aunque intentemos instanciar ese mismo objeto muchas veces en el código, se garantiza que solo habrá una única instancia del objeto en nuestra aplicación. Algo parecido a un elemento `static` en Java.

La instancia se crea automáticamente de forma perezosa (_lazy_) la primera vez que se accede a ella. Puede tener propiedades, funciones, e incluso heredar de otras clases o interfaces.

> [!info]  
> Ya lo veremos en el módulo de PSP, pero estos objetos se pueden usar de forma segura con hilos (_thread-safe_).

```kotlin
object NetworkConfig {
	const val BASE_URL = "https://ejemplo.com"
	var timeout = 30

	fun logConfig() {
		println("URL: $BASE_URL, Timeout: $timeout")
	}
}

// Uso directo (no se usa la palabra 'new' ni constructor)
NetworkConfig.logConfig()
```

## Companion objects

Ya lo hemos visto en el [[2DAM_PMDM/Unidad 01/4. static en Kotlin\|apartado anterior]]. Se usa dentro de una clase para definir miembros que están ligados a la clase en sí, no a sus instancias. El equivalente a los miembros **`static`** de Java, vamos.

Hay que tener en cuenta que :
- Solo puede haber un `companion object` por clase.
- Se inicializa cuando se carga la clase contenedora.
- Es ideal para definir constantes, métodos utilitarios o implementar el patrón _Factory_.

```kotlin
class User private constructor(val id: Int) {
	companion object {
		const val MAX_USERS = 100

		// Función Factory
		fun createAdmin(): User {
			return User(0)
		}
	}
}

// Uso directo desde la clase
val max = User.MAX_USERS
val admin = User.createAdmin()
```

## Expresiones de objeto (Clases anónimas)

Se utiliza para crear **instancias de clases anónimas** sobre la marcha, modificando ligeramente una clase existente o implementando una interfaz sin declarar una subclase con nombre.

Se evalúan y ejecutan inmediatamente donde se usan. Pueden acceder y modificar variables del bloque local que las rodea y, a diferencia de Java, no necesitan ser `final`.

```kotlin
interface OnClickListener {
	fun onClick()
}

// Creación de una clase anónima que implementa la interfaz
val botonBorrador = object : OnClickListener {
	override fun onClick() {
		println("Elemento eliminado")
	}
}
```


# 6. Comparadores estructurales y referenciales

Los operadores en Kotlin son los habituales en otro lenguajes: aritméticos y lógicos.

No hay mucho más que añadir, salvo una peculiaridad en el caso de los operadores de comparación **\=\=** y **\=\=\=**:

## Comparadores estructurales

Compara la **estructura de dos objetos** y el **contenido** para ver si son iguales o no. 

Ya conocemos algunos de Java:

\=\= - **igualdad estructural**  
Compara la **estructura de dos objetos** y el **contenido** para ver si son iguales. Esto lo hace llamando a la función `equals()` del objeto.  
  
El operador **!=**, por tanto, el el de **desigualdad estructural**.

## Comparadores referenciales

Comprueban si dos variables apuntan o no al **mismo objeto** en la memoria RAM.

Así, la **igualdad referencial** (\=\=\=) indicará si dos objetos son literalmente el mismo mientras que la **desigualdad referencial** (!\=\=) indica lo contrario.

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val p1 = Persona("Ana")
>     val p2 = Persona("Ana")
>     val p3 = p1 // Apunta a la misma dirección de memoria que p1
>     
>     // COMPARACIÓN ESTRUCTURAL (==)
>     println(p1 == p2)  // true  -> Tienen el mismo contenido
>     
>     // COMPARACIÓN REFERENCIAL (===)
>     println(p1 === p2) // false -> Son objetos distintos en memoria
>     println(p1 === p3) // true  -> Apuntan exactamente al mismo objeto
>     
>     // DESIGUALDAD REFERENCIAL (!==)
>     println(p1 !== p2) // true  -> Es verdad que están en lugares distintos
>     println(p1 !== p3) // false -> Es falso, porque son el mismo objeto
> }
> ```

<iframe src="https://pl.kotl.in/2EfDbqy6I" width="560" height="250"></iframe>

# 7. Collections

En Java estudiamos estructuras de datos como **listas** (**`List`**), **conjuntos** (**`Set`**) o **mapas/diccionarios** (**`Map`**). Kotlin también las contempla.

> [!warning] Recuerda... 
> Recordemos que las colecciones usan **genéricos** para establecer el tipo de datos que van a almacenar.

La diferencia con Java es que en Kotlin, al declarar cualquier colección, **hay que indicar si queremos que sea mutable**.

Una **colección**[^4] es un grupo de un número variable de elementos que tienen un significado común. A diferencia de Java, Kotlin duplica la jerarquía de sus colecciones en **dos tipos de interfaces**:

* **Inmutables** (solo lectura): se puede acceder a sus datos (leer, iterar, buscar), pero no modificarlos.
{ #27e072}

* **Mutables:** extienden las anteriores añadiendo operaciones de escritura (`add`, `remove`, `update`). Es decir, permite modificar la colección y sus elementos.

> [!question] ¿Cómo lo harías? 🤔
> ¿Cómo declararías una colección mutable: con `val` o con `var`?
> Explica el porqué de tu respuesta y constrástala con el resto de la clase.
> 
> **Pista**: por seguridad, se recomienda usar `val`.

Todas las colecciones están incluidas en el paquete [**kotlin.collections**][kotlin_collections].

## List

Es una colección **ordenada** que permite acceder a sus elementos mediante un **índice entero**.

Podemos introducir cualquier valor acorde a su tipo de dato (recuerda que se declara con genéricos) y **permite elementos duplicados** e incluso **valores nulos**.

A la hora de comparar dos listas (ver [[2DAM_PMDM/Unidad 01/6. Comparadores estructurales y referenciales\|6. Comparadores estructurales y referenciales]]), se consideran estructuralmente iguales (\=\=) si tienen el **mismo tamaño** y los **mismos elementos** en las **mismas posiciones**.

A diferencia de Java, Kotlin permite declarar listas de [[2DAM_PMDM/Unidad 01/7. Collections#^27e072\|dos formas]] (mutables e inmutables) con métodos muy similares, sin especificar una estructura concreta.

### List inmutables

Se crean con la función [**`listOf()`**][kotlin_listOf], que admite como parámetros los elementos que conformarán la lista.

```kotlin
fun main() {
    val lista = listOf("Ana", "Juan", "Pedro")
    
    print(lista[0])
    lista[0] = "Pepa"  // ❌ Error, no se pueden modificar elementos
    print(lista[0])
}
```

Al ser inmutable **no permite modificar sus elementos** (como se indica en el código anterior. Tampoco ofrece métodos como `add` o `remove`.

Existe otro método en el paquete [**kotlin.collections**][kotlin_collections] que permite crear una **lista inmutable vacía**:

```kotlin
val listaVacia: List<String> = emptyList()
```

Pero ¿para qué diantre sirve una lista vacía que es inmutable? Si no la podemos modificar para añadir elementos, ¿de qué nos sirve?

Muy sencillo: para evitar el `null`.

Observa el siguiente ejemplo: 

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
>     val resultados = mutableListOf<String>()
>     for (usuario in usuarios) {
>         if (usuario == nombre) resultados.add(usuario)
>     }
>     
>     // Si la lista está vacía, devuelve emptyList() de forma segura
>     if (resultados.isEmpty())
>         return emptyList()
>     else
>         return resultados
> }
> 
> ```

<iframe src="https://pl.kotl.in/5JfLBrHpf" width="600" height="650"></iframe>

El método `buscarUsuariosPorNombre` devuelve siempre una lista. Incluso cuando no hay elementos que devolver, devuelve una **lista vacía**. Esta lista vacía es una lista estática, por lo que no se crea un puntero por cada lista vacía que se genere. **Todas las listas vacías apuntan al mismo sitio**. Esto supone un ahorro de memoria considerable.

Además, al evitar el `null`, no hay que hacer validación alguna y **podemos usar la función en cualquier expresión** (en el bucle en este caso) **sin miedo a que nuestro programa se rompa**.

### List mutables

Si una lista inmutable se creaba con `listOf()`, una mutable se hará mediante `mutableListOf`.

```kotlin
fun main() {
    val lista = mutableListOf("Ana", "Juan", "Pedro")
    
    print(lista[0])
    lista[0] = "Pepa"  // ✅ Es mutable! se pueden modificar sus elementos
    print(lista[0])
}
```

En la declaración anterior se crea **por defecto un `ArrayList`**.

Al igual que con las listas inmutables, podemos crear **listas mutables vacías**:

```kotlin
val lista: mutableListOf<String>()
```

Realmente se crea una lista mutable sin elementos.

Al crear una lista mutable podemos indicarle varios datos, como el tamaño y el valor inicial de sus elementos:

```kotlin
// Lista que reserva 5 posiciones para cadenas de texto:
val listaNombres = ArrayList<String>(5)

// Lista que reserva 10 posiciones para cadenas y las inicializa todas a null
val lista = MutableList<String?>(10) { null }

// Lista que reserva 20 posiciones para enteros y los inicializa todos a 0
val lista = MutableList<Int?>(10) { 0 }

// Podemos usar expresiones lambda para inicializar la lista.
// Lista para 5 enteros donde cada elemento es el doble de su índice
val listaConInit = MutableList(5) { index -> index * 2 } // [0, 2, 4, 6, 8]

```



## Set

Los conjuntos son colecciones de **elementos únicos**. Es decir, **no permite elementos repetidos**.

Tampoco suelen estar ordenadas (aunque hay excepciones como el `LinkedHashSet`), por lo que no hay índice del que tirar para acceder a sus elementos.

Permite el valor `null`, pero solo uno ya que de otra forma tendría elementos repetidos.

> [!warning] ¿Cómo impide el `Set` que se repitan elementos? 
> Si creamos un conjunto de objetos `Persona`, por ejemplo, esa clase debe tener implementados los métodos **`equals`y `hashCode`**.
> Así, al añadir un elemento al conjunto, se va comparando con cada uno de los elementos incluidos en él mediante estos métodos.

Si comparamos dos conjuntos de forma estructural (\=\=), se consideran iguales si tienen el **mismo tamaño** y contienen los **mismos elementos**, sin importar el orden.

### Set inmutables

Similar a la declaración de listas:

```kotlin
val frutas = setOf("Manzana", "Banana", "Naranja")
```

Y también para los vacíos:

```kotlin
val setVacio: Set<String> = emptySet()
```

En ninguno de los casos se pueden modificar el propio conjunto ni sus elementos.

### Set mutables

Cualquiera de estas dos declaraciones...

```kotlin
val setMutable = mutableSetOf(1, 2, 3)
val linkedSet = linkedSetOf("A", "B", "C")

// Con el constructor de LinkedHashSet:
val linkedSet2 = LinkedHashSet<Int>()
```

... crea por debajo un **[`LinkedHashSet`][kotlin_LinkedHashSet]** por defecto. El  `LinkedHashSet` organiza los elementos por **orden de inserción**. Aquí vemos que, contra la naturaleza de un `Set`, el `LinkedHashSet` marca un orden en el conjunto.

También tenemos el `HashSet` que es el **más rápido** y consume menos memoria, pero sin orden garantizado.

> [!example] Actividad propuesta 🏗️
> Averigua y razona por qué la estructura `LinkedHashSet` tiene un orden cuando los `Set`, por definición, no lo tienen.

La otra estructura, el **`HashSet`** se declara de varias formas:

```kotlin
val setHash = hashSetOf(10, 20, 30)

// Con el constructor de HashSet:
val setHash2 = HashSet<String>(100) // Capacidad inicial de 100 elementos
```

Si queremos usar el **`TreeSet`** de Java para ordenar sus elementos de forma natural, podemos declararlo así:

```kotlin
val setOrdenado = sortedSetOf(5, 1, 8, 3)
// Internamente se guarda como [1, 3, 5, 8]
```

## Map

Al igual que en Java, el `Map` no es **formalmente una colección**. En Kotlin, `Map` no hereda de la interfaz `Collection`, aunque suele ser tratada como tal.

El mapa, también conocido como **diccionario**, almacena elementos como **pares clave-valor** (`key-value`).

Las claves son **únicas**; no se pueden repetir como ocurre con las palabras de un diccionario. No ocurre lo mismo con los valores.

De forma parecida al `Set`, dos mapas son **estructuralmente iguales** (\=\=) si, independientemente de su orden, ambos contienen los mismos pares clave-valor.

### Map inmutables

Para asociar una clave con su valor se usa la función `to`

```kotlin
val capitales = mapOf("España" to "Madrid", "Francia" to "París")
```

O dejarlo vacío:

```kotlin
val mapaVacio: Map<String, Int> = emptyMap()
```


### Map mutables

#### Ordenados
Si queremos crear un `Map` **ordenado por el orden de inserción** de sus elementos, podemos usar las funciones `mutableMapOf` o `linkedMapOf`, se crea por defecto un `LinkedHashMap`:

```kotlin
val usuario = mutableMapOf("id" to 1, "nombre" to "Ana")
val ordenadoPorInsercion = linkedMapOf("A" to 1, "B" to 2)
```

O podemos **ordenarlos por las claves**:

```kotlin
val agenda = sortedMapOf("Carlos" to 123, "Ana" to 456)
// "Ana" será el primer elemento
```

#### No (necesariamente) ordenados
Pero si el orden no es prioritario para nuestra solución, podemos usar la estructura [`HashMap`][kotlin_HashMap], mucho más rápida:

```kotlin
val stock = hashMapOf("Manzanas" to 50, "Plátanos" to 30)
```

#### Constructores explícitos

Los casos anteriores, ordenados o no, se pueden declarar usando los constructores específicos de la estructura que escojamos:

```kotlin
val miHashMap = HashMap<String, String>(50) // Capacidad inicial de 50 entradas val miLinkedHashMap = LinkedHashMap<Int, Boolean>()
```


## ArrayDeque

Kotlin incorpora **[`ArrayDeque<T>`][kotlin_ArrayDeque_overview]**, una **cola de doble extremo** que permite añadir o eliminar elementos tanto al principio como al final y de forma muy eficiente.

Internamente almacena los datos en un array, redimensionándolo según se amplíe o disminuya el número de elementos.

A diferencia de las colecciones anteriores, el paquete [**kotlin.collections**][kotlin_collections] no ofrece funciones que creen dicha estructura. Se declara e instancia usando su constructor:

```kotlin
// ArrayDeque vacío:
val colaDoble = ArrayDeque<String>()

// Creado a partir de una colección
val datosIniciales = listOf(10, 20, 30)
val miCola = ArrayDeque(datosIniciales)

// ArrayDeque con una logitud determinada:
val colaDoble2 = ArrayDeque<String>(20)
```

> [!info] Importante 
> El último ejemplo (declararlo con una longitud inicial) es muy útil **si se conoce de antemano el tamaño** del `ArrayDeque`, ya que al reducir el número de operaciones de redimensionamiento del array interno, el rendimiento mejora sensiblemente.

Los métodos son muy similares a los de una pila y una cola. Consulta la [documentación de referencia][kotlin_ArrayDeque] para ampliar información.

Amplía esta información con la documentación oficial o artículos de interés como este:

* Andzevičius, D. (2024, 19 marzo). *ArrayDeque in Kotlin*. baeldung.com. https://www.baeldung.com/kotlin/arraydeque


## Ejemplo

> [!abstract]- Código 
> ```kotlin
> data class Alumno(val nombre: String, val edad: Int)
> fun main() {
>     // ==========================================
>     // 1. EJEMPLO DE LIST (Listas)
>     // ==========================================
>     println("--- EJEMPLO DE LIST ---")
>     // Lista de solo lectura (permite duplicados)
>     val listaAlumnos = listOf("Ana", "Pedro", "Ana") 
>     println("Lista original: $listaAlumnos")
>     println("Primer elemento (índice 0): ${listaAlumnos[0]}")
>     
>     // Lista mutable (permite añadir/eliminar y cambia su tamaño)
>     val listaMutable = mutableListOf("Juan", "María")
>     listaMutable.add("Sofía")       // Añade al final
>     listaMutable.removeAt(1)       // Elimina a "María" (índice 1)
>     println("Lista mutable modificada: $listaMutable\n")
>     
>     // ==========================================
>     // 2. EJEMPLO DE SET (Conjuntos)
>     // ==========================================
>     println("--- EJEMPLO DE SET ---")
>     // Set de solo lectura (elimina duplicados automáticamente)
>     val setIds = setOf(101, 102, 101, 103) 
>     println("Set (sin duplicados): $setIds") // Imprime: [101, 102, 103]
>     println("¿Existe el ID 102?: ${setIds.contains(102)}")
>     
>     // Set mutable
>     val setMutable = mutableSetOf("Kotlin", "Java")
>     setMutable.add("Python")
>     setMutable.add("Java") // No se añadirá porque ya existe
>     println("Set mutable modificado: $setMutable\n")
>     
>     // ==========================================
>     // 3. EJEMPLO DE MAP (Mapas / Diccionarios)
>     // ==========================================
>     println("--- EJEMPLO DE MAP ---")
>     // Map de solo lectura (Clave única -> Valor)
>     val mapaAsignaturas = mapOf(
>         "PROG" to "Programación",
>         "ED" to "Entornos de Desarrollo",
>         "BD" to "Bases de Datos"
>     )
>     println("Nombre de la asignatura PROG: ${mapaAsignaturas["PROG"]}")
>     
>     // Map mutable
>     val mapaNotas = mutableMapOf("Ana" to 8.5, "Pedro" to 6.0)
>     mapaNotas["Sofía"] = 9.2 // Añade un nuevo par clave-valor
>     mapaNotas["Pedro"] = 7.0 // Actualiza el valor de una clave existente
>     println("Mapa de notas actualizado: $mapaNotas")
> }
> ```

<iframe src="https://pl.kotl.in/NcmcRYU-A" width="560" height="950"></iframe>




[kotlin_collections]: https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.collections/
[kotlin_collections_overview]: https://kotlinlang.org/docs/collections-overview.html
[kotlin_LinkedHashSet]: https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.collections/-linked-hash-set/
[kotlin_HashMap]: https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.collections/-hash-map/
[kotlin_ArrayDeque]: https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.collections/-array-deque/
[kotlin_ArrayDeque_overview]: https://kotlinlang.org/docs/collections-overview.html#arraydeque
[kotlin_listOf]: https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.collections/list-of.html



[^4]:  _Collections overview | Kotlin_. (s. f.). Kotlin Help. https://kotlinlang.org/docs/collections-overview.html


# 8. Null Safety

¿Qué es la seguridad de nulos o ***Null Safety***[^5]?

El valor nulo (`null`) está extendido en todos (o casi todos) los lenguajes de programación. Se usa para indicar la **ausencia de un valor**. **La nada** en términos de datos digitales.

En Java, si se intenta operar sobre un elemento nulo sin comprobarlo previamente, salta una excepción de puntero nulo ([**NullPointerException**](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/NullPointerException.html)).

```java
public class Main
{
	public static void main(String[] args) {
		System.out.println(upperCase("Hello World"));
		
		System.out.println(upperCase(null));  // Lanza la excepción
	}
	
	public static String upperCase(String texto) {
	    /*
	    si texto=null
	    
	    return null.toUppercase()
	    
	    no puede ejecutarse porque null no tiene métodos
	    */
		return texto.toUpperCase();
	}
}
```

Si el código no atrapa esta excepción, el programa detiene su ejecución de forma inmediata (*crash*).

Kotlin, por defecto, **no admite valores nulos**. No podemos declarar una variable sin inicializar e intentar usarla, ya que el compilador lanzaría un error. Es decir, **Kotlin comprueba los nulos en tiempo de compilación**. No da la opción a ejecutarlo.

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     var nombre = "Pepe"
>     nombre = null // ❌ ERROR! de compilación
> }
> ```

<iframe src="https://pl.kotl.in/Zs1fv3NlQ" width="560" height="250"></iframe>

Para empezar, ninguna variable admite el valor `null`, tal y como se hacía en Java. En este ejemplo, se está intentando asignar `null` a una variable de tipo `String`. Kotlin por tanto espera una cadena de texto, no un nulo.

Si se quiere indicar que una variable **podría ser nula** (*nulleable*) hay que expresarlo en su tipo con el operador **`?`**:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     var nombre: String? = "Pepe"
>     println(nombre)
>     
>     nombre = null
>     println(nombre)
> }
> ```

<iframe src="https://pl.kotl.in/HkaNhlE0x" width="560" height="250"></iframe>

En el ejemplo anterior estamos diciendo que `nombre` es *nullable*, es decir, que puede contener un `String` o un `null`.

¿Es esto recomendable? **Absolutamente no**. Entonces, ¿por qué lo hacemos? Porque **Kotlin obliga a inicializar cualquier variable que declaremos**. Si hiciéramos esto:

```kotlin
fun main() {
    var nombre: String
    
    println(nombre) // ❌ ERROR! Kotlin indica que debemos inicializarla
}
```

Esto ocurre cuando aún no tenemos el valor que vamos a asignar a dicha variable.

## 8.1. Operador seguro (?.)

Kotlin usa el **operador seguro `?.`** en variables *nulleables* para permitir acceder a sus miembros (propiedades y métodos) de forma segura. Si el valor es nulo, la expresión completa se evalúa a **`null`**:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val cadena: String? = null
>     val longitud: Int? = cadena?.length
>     
>     println(longitud)
> }
> ```

<iframe src="https://pl.kotl.in/cEW1nRrB9" width="560" height="200"></iframe>

En este caso inicializamos `cadena` a `null`. Esto obliga a que `longitud` sea también *nullable*, ya que se forma a partir de un *nullable*. Aquí podemos ver que `?.` devuelve el valor entero con la longitud de la cadena o `null`.

Los *nullable* son, en realidad, un **tipo de dato especial en Kotlin**: admite valores de tipo de datos indicado (`String`, `Int`, `Boolean`, etc.) además de `null`. 

Así, las **colecciones** pueden admitir en su genérico correspondiente un *nullable*:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     /*
>      1. Una lista con elementos que PUEDEN ser nulos (String?)
>     */
>     val listaConNulos: List<String?> = listOf("Manzana", null,
>                                               "Plátano", null,
>                                               "Naranja")
>     for (fruta in listaConNulos) {
>         /*
>          Kotlin obliga a usar el operador '?' porque el
>          elemento puede ser nulo
>          */ 
>         println(fruta?.uppercase())
>     }
>     
>     /*
>      1. UNA LISTA ENTERA que PUEDE ser nula (List<String>?)
>     */
>     var listaCompletaNula: List<String>? = null
>     
>         /*
>             La siguiente línea daría un error de compilación, ya que
>             listaCompletaNula es nula y sería como intentar lo siguiente:
>             
>             null.add("Hola")
>         */
>         listaCompletaNula.add("Hola")
>         // ❌ ERROR! null no tiene métodos, por tanto no puede
>         // ejecutar .add("Hola")
>     
>     // Para añadirle elementos, hemos de crearla (que deje de apuntar
>     // a null)
>     listaCompletaNula = listOf("Perro", "Gato")
>     println("Tamaño de la lista ahora: ${listaCompletaNula.size}")
> }
> ```

<iframe src="https://pl.kotl.in/S9UhStT1z" width="560" height="640"></iframe>

Tal y como se indica en el código, la línea:

```kotlin
listaCompletaNula.add("Hola")
```

fallará porque `listaCompletaNula` es nulo, y si sustituimos la variable por `null` en esa expresión, comprendemos claramente que `null` no tiene métodos y, por tanto, no puede ejecutarse.

> [!info] Comenta esa línea... 
> ...  y vuelve a ejecutar el código. A ver qué pasa.

> [!question] ¿Qué ocurre cuando...? 🤔
> ¿... se declara una lista de la siguiente forma?
> ```kotlin
> var listaChunga: List<String?>? = null
> ```

## 8.2. Operador Elvis (?:)

El **operador Elvis `?:`** proporciona un valor por defecto en caso de que el valor a la izquierda sea nulo:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val nombre = "Pepe"
>     val apellido1: String? = null
>     
>     println(concatenar(nombre, apellido1))
> }
> fun concatenar(nombre: String, apellido: String?): String {
>     return nombre + " " + (apellido ?: "Expósito")
> }
> ```

<iframe src="https://pl.kotl.in/hj2d-T7S9" width="560" height="230"></iframe>

En nuestro ejemplo, en la función `concatenar`, si el argumento `apellido` entra con el valor `null`, el operador Elvis garantiza que se usará por defecto el apellido "Expósito".

Veamos otro ejemplo:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     var cadena: String? = null
>     var longitud = longitudCadenaConElvis(cadena)
>     
>     println("CON el operador Elvis ------------------")
>     println(longitud)
>     
>     longitud = longitudCadenaSinElvis(cadena)
>     
>     println("SIN el operador Elvis ------------------")
>     println(longitud)
> }
> 
> fun longitudCadenaSinElvis(cadena: String?): Int {
>     if (cadena != null)
>         return cadena.length
>     else
>         return 0
> }
> 
> /**
>  * Si el parámetro de entrada es nulo, devuelve 0.
>  * En otro caso, retorna su longitud.
>  */
> fun longitudCadena(cadena: String?): Int {
>     return cadena?.length ?: 0
> }
> ```

<iframe src="https://pl.kotl.in/YUnoEIat7" width="560" height="590"></iframe>

El uso es intuitivo para las colecciones:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     /*
>      1. Una lista que contiene elementos que PUEDEN ser
>         nulos (String?)
>     */
>     val listaConNulos: List<String?> = listOf("Manzana", null,
>                                               "Plátano", null,
>                                               "Naranja")
>     for (fruta in listaConNulos) {
>         /*
>          El operador Elvis nos permite sustituir null por
>          un valor por defecto (Falta una fruta aquí):
>          */ 
>         println(fruta?.uppercase() ?: "Falta una fruta aquí")
>     }
>     
>     /*
>      Si quisiéramos eliminar los nulos, en lugar de hacer un
>      bucle que filtre los valores no nulos en otra lista, podemos
>      usar el método .filterNotNull()
>     */
>     val listaLimpia: List<String> = listaConNulos.filterNotNull()
>     println("\nLista filtrada sin nulos: $listaLimpia")
>     
>     /*
>      2. UNA LISTA ENTERA que PUEDE ser nula (List<String>?)
>     */
>     var listaCompletaNula: List<String>? = null
>     
>     println("\n--- Procesando la lista entera nula ---")
>     /*
>      Con el operador '?' evitamos que el programa crashee si
>      la lista es nula.
>      El operador Elvis nos permite sustituir null por
>      un valor por defecto (0):
>     */
>     println("Tamaño de la lista: ${listaCompletaNula?.size ?: 0}")
>     
>     // Para añadirle elementos, hemos de crearla (que deje de apuntar
>     // a null)
>     listaCompletaNula = listOf("Perro", "Gato")
>     println("Tamaño de la lista ahora: ${listaCompletaNula.size}")
> }
> ```

<iframe src="https://pl.kotl.in/qAnOHGhak" width="700" height="790"></iframe>


## 8.3. Operador de no nulidad (\!\!)

El **operador de no nulidad \!\!** indica que la variable a la que acompaña **no es nula**. En otra palabras, que no es *nullable*:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     // Assigns a nullable string to a variable
>     val b: String? = "Kotlin"
>     // Treats b as non-null and accesses its length
>     val l = b!!.length
>     println(l)  // 6
> }
> ```

<iframe src="https://pl.kotl.in/GlwgYHBeE" width="560" height="230"></iframe>

Visto así, este operador no tiene mucho sentido. Estamos viendo claramente que `b` no es nulo (contiene la cadena "Kotlin"). Además, si en lugar de inicializarlo con este texto, lo inicializo a `null`:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     // Assigns null to a nullable variable
>     val b: String? = null
>     // Treats b as non-null and tries to access its length
>     val l = b!!.length  // ❌ ERROR! NullPointerException
>     println(l)
> }
> ```

<iframe src="https://pl.kotl.in/l99-hJD77" width="560" height="250"></iframe>

Entonces ¿para qué sirve este operador? Para que en aquellos casos donde tengamos claro que una variable no sea nula podamos operar con ella sin tener en cuenta `null`. Es decir, ningún operador más del *null safety*, ninguna validación... 

## 8.4. Función `let`

La función `let` se usa con *nullables* para garantizar la ejecución de un bloque de código sólo si dicho *nullables* no es nulo:

> [!abstract]- Código 
> ```kotlin
> /**
>  * Si el camión tiene mercancías cargadas, irá cargado.
>  */
> fun main() {
>     val camion: String? = "Tomates de Almería"
>     
>     camion?.let {
>         println("El camión está cargado cargado")
>     }
> }
> ```

<iframe src="https://pl.kotl.in/c0tFRzn_Y" width="560" height="250"></iframe>

Si en el código anterior pones a `null` la variable `camion`, ¿qué ocurriría? Que `let` no ejecutaría el bloque de código donde indica que el camión está cargado.

> [!todo] El `let` es un `if (variable != null)` 
> Podemos decir que `let` es como un `if` que se ejecuta solo cuando la variable *nullable* a la que acompaña no es nula.

¿Existe entonces un `else` para `let`? Sí, el `run` junto con el operador Elvis:

> [!abstract]- Código 
> ```kotlin
> /**
>  * Si el camión tiene mercancías cargadas, irá cargado.
>  * Si no, irá vacío.
>  */
> fun main() {
>     // Comenta una y descomenta la otra para ver el resultado:
>     val camion: String? = null
>     //val camion: String? = "mercancia cargada en el camion"
>     
>     println(camion?.length)
>     
>     val contenedor = camion?.let {
>         "cargado"
>     } ?:run {
>         "vacío"
>     }
>     println(contenedor)
> }
> ```

<iframe src="https://pl.kotl.in/KJ4nSFu96" width="560" height="400"></iframe>


[^5]: Kotlin. (s. f.). *Null safety* | Kotlin Help. https://kotlinlang.org/docs/null-safety.html


# 9. lateinit

Teniendo en cuenta lo visto en [[2DAM_PMDM/Unidad 01/8. Null Safety\|8. Null Safety]], hay que hacer un inciso con respecto a algunas reglas que se inculcaron en la era dorada de la programación estructurada y parte de la era de la POO:

> [!info] El inciso... 
> **Ni las variables deben declararse al principio del bloque de código ni deben cambiar de valor** (en la medida de lo posible).
> 
> Ambos consejos son aplicables en el contexto actual de cualquier lenguaje. Dicho de otra forma, siempre que puedas[^6]:
> 
> * **Declara una variable en el momento de asignarle un valor** justo cuando vayas a usarla. Aunque no lo creas, esto aclara mucho el código ya que no hay que buscar dónde se ha declarado cada variable y qué se ha hecho con ella hasta llegar al punto del código que nos interesa.
> * **Procura** (si es posible) **que sea una constante** (`val`). Una variable que cambia de valor con frecuencia puede dificultar la detección de errores y el mantenimiento.

Si no tenemos más remedio que declarar una variable sin conocer aún su valor, lo más sensato es declarar la variable indicando que la inicializaremos más tarde. Esto lo conseguimos con `lateinit`:

```kotlin
fun main() {
    lateinit var nombre: String
    ...
}
```

Esto puede que no tenga sentido si lo miramos desde la perspectiva que hemos usado en Java, pero volvemos a insistir en que **Kotlin no admite nulos**.

El problema del `lateinit` es que le estamos diciendo a Kotlin que nos deje declarar la variable sin inicializar y sin hacerla *nullable* porque nosotros **nos comprometemos a darle un valor**.

Aquí el compilador de Kotlin se fiará y nos dirá: "¡Todo tuyo! Espero que sepas lo que haces". Y esa expresión de desconfianza está justificada porque, ¿y si se nos olvida asignarle un valor, como habíamos prometido? Antes de realizar cualquier operación con esa variable podemos comprobar si se ha inicializado usando la siguiente expresión lógica:

```kotlin
::variable.isInitialized
```

Veamos todo esto en el siguiente código:

```kotlin
class DatabaseService {
    /*
    Declaramos la propiedad "connectionString" sin inicializarla, ya que
    su valor depende de los datos que se envíen en el método "configurar"
    */
    lateinit var connectionString: String

    fun configurar(host: RegiónHost, puerto: Int) {
        // Inicializamos la variable más tarde, fuera del constructor
        this.connectionString = "postgresql://$host:$puerto/basedatos"
    }

    fun conectar() {
        // Comprobamos si la variable ya fue inicializada
        if (::connectionString.isInitialized) {
            println("Conectando a: $connectionString")
        } else {
            println("No se ha configurado la conexión.")
        }
    }
}

data class RegiónHost(val nombre: String) {
    override fun toString() = nombre
}

fun main() {
    val servicio = DatabaseService()
    
    /*
    Si llamamos a "conectar()" aquí, entraría al 'else' o lanzaría
    error si no validamos.
    */ 
    servicio.conectar()

    // Inicializamos la propiedad
    servicio.configurar(RegiónHost("localhost"), 5432)
    
    // Ahora ya podemos usarla con seguridad
    servicio.conectar()
}
```

Y a estas alturas podrías pensar: ¿Y si inicializo `connectionString` con la cadena vacía `""` y acabamos antes? Una vez más volvemos al pensamiento "*Java like*", que no es que esté mal, pero que Kotlin intenta mejorar.

La cadena vacía `""` te **obliga a hacer más validaciones**, ya que se admite como valor a nivel del compilador (al fin y al cabo es una cadena válida en el sentido estricto) pero no a nivel de lógica. Esa cadena vacía, en este ejemplo, **no es una cadena de conexión válida**.

Si olvidamos llamar a `configurar()`, el método `conectar()` intentará conectarse a la dirección `""`. El programa fallará más tarde con un error confuso de red (_"No se puede conectar a "" "_) mientras que **el error real**, olvidar configurar el servicio, **queda oculto**.

Con `lateinit` el programa *crashea* de momento donde debe: en la línea donde intentamos usar la variable. Y el mensaje no da pie a interpretaciones erróneas: _"No se ha configurado la conexión"_ porque no se ha inicializado ese atributo. En definitiva, la depuración es más fácil.



[^6]: Blé, C. (s. f.). _Null, un viejo enemigo del lado oscuro_. Lean Mind. https://leanmind.es/es/blog/evitar-null-tambien-en-kotlin


# 10. Rangos

Un rango **no es un tipo de dato** como tal. Se trata de una forma de representar un intervalo indicando un **valor inicial** y **otro final**.

En matemáticas se usan los corchetes `[ ]` y los parémtesis `( )` para expresar los límites de un rango de datos. Los corchetes significan que los valores están incluidos en el rango y los paréntesis que no:

```
(1, 9) --> números del 1 al 9 sin incluir ni el 1 ni el 9
[1, 9) --> números del 1 al 9 sin incluir ni el 9
(1, 9] --> números del 1 al 9 sin incluir ni el 1
[1, 9] --> números del 1 al 9, ambos incluidos.
```

En Kotlin tenemos los **rangos cerrados** (incluyen los valores de los extremos) y **abiertos solo por la derecha** (no incluyen el último).

## 10.1. Rangos ascendentes

Un rango ascendente es aquel cuyo primer valor es el menor del rango y su valor final es el mayor.

### Operador `..`

Son aquellos que incluyen los valores de los extremos (inicial y final).

Se puede definir un rango estableciendo ambos valores y separándolos con el **operador `..`**:
{ #840e9f}


> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val numeros = 3..7
>     println(numeros)
>     
>     println("Recorremos los números del rango:")
>     for (numero in numeros)
>         println(numero)
>     print("De qué clase sale este rango? ")
>     println(numeros::class.simpleName)
> }
> ```

<iframe src="https://pl.kotl.in/Xq-S3DNs_" width="560" height="350"></iframe>

> [!info]  
> Se puede definir un intervalo con cualquier tipo que sea **comparable** (números, letras, etc.).

Hagámoslo ahora con letras:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val abecedarioMinusculas = "a".."z"
>     println(abecedarioMinusculas)
>     
>     for (letra in abecedarioMinusculas) // ❌ ERROR!
>         println(letra)
>     
>     println(abecedarioMinusculas::class.simpleName)
> }
> ```

<iframe src="https://pl.kotl.in/CuzAZq-VF" width="560" height="250"></iframe>

Aunque efectivamente las letras son comparables, estrictamente hablando, **no hemos hecho un rango de letras**, sino de cadenas donde hemos dicho que hay una serie de cadenas que empiezan por `"a"` y terminan por `"z"`. Pero no son caracteres (`Char`), por lo que no sabemos si después de la `"a"` va una cadena  `"b"` o la  `"aa"`. Dicho de otra forma, aunque las cadenas son comparables, no hay una secuencia clara de cadenas que sigan un orden natural.

Si en el código anterior sustituyes el rango de cadenas `"a".."z"` por el rango de caracteres `'a'..'z'` el código funcionará correctamente.

> [!question] ¿Cómo lo harías? 🤔
> Busca otras formas de hacer el recorrido con bucle dejando el rango de cadenas.
> A ver qué sale.

La función **`rangeTo()`** hace lo mismo que `..`. De hecho, `..` llama a la función `rangeTo()`. Ésta se aplica al cualquier elemento comparable que queramos establecer como el primero del rango y admite como parámetro el último:

```kotlin
// Esto:
val numeros = 3.rangeTo(7)  // 3, 4, 5, 6, 7

// Es lo mismo que esto otro:
val numeros = 3..7  // 3, 4, 5, 6, 7
```

### Rangos abiertos por la derecha

Como se indicaba al principio de este apartado, el rango abierto por la derecha **incluye el valor inicial y excluye el final**.

Se puede crear mediante el operador **`..<`** o las funciones **`until`** y **`rangeUntil`**. Veámoslo creando el mismo rango de distintas formas en el siguiente ejemplo:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     var numero = 7
>     
>     println("Forma 1: con el operador ..<")
>     if (numero in 3..<7) {  // 3, 4, 5, 6
>         println("$numero está en el rango")
>     }
>     else {
>         println("$numero no está en el rango")
>     }
>     
>     println("\nForma 2: con el método until")
>     if (numero in 3 until 7) {  // 3, 4, 5, 6
>         println("$numero está en el rango")
>     }
>     else {
>         println("$numero no está en el rango")
>     }
>     
>     println("\nForma 3: con el método until")
>     numero = 4
>     if (numero in 3.until(7)) {  // 3, 4, 5, 6
>         println("$numero está en el rango")
>     }
>     else {
>         println("$numero no está en el rango")
>     }
>     
>     println("\nForma 4: con el método rangeUntil")
>     numero = 7
>     if (numero in 3.rangeUntil(7)) {  // 3, 4, 5, 6
>         println("$numero está en el rango")
>     }
>     else {
>         println("$numero no está en el rango")
>     }
> }
> ```

<iframe src="https://pl.kotl.in/U7puDmPAC" width="560" height="650"></iframe>


## 10.2. Operador `in`

Se trata de un operador binario (admite dos operandos, uno a cada lado, como los operadores aritméticos) que indica si el `valor` está en el `rango`. Puede usarse de esta forma:

```kotlin
valor in rango   // valor está DENTRO de rango
valor !in rango  // valor está FUERA de rango
```

O con la función `contains`:

```kotlin
rango.contains(valor)     // valor está DENTRO de rango
!rango.contains(valor)    // valor está FUERA de rango
```

Para comprobarlo, juega con el siguiente ejemplo:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val num = 6
>     val numeros = 3..7
>     
>     println("Forma 1: operador in:")
>     print("$num está en el rango $numeros? ")
>     println(num in numeros)  // true
>     
>     print("$num está fuera del rango $numeros? ")
>     println(num !in numeros)  // false
>     
>     println("\nForma 2: funcion contains:")
>     print("$num está en el rango $numeros? ")
>     println(numeros.contains(num))  // true
>     
>     print("$num está fuera del rango $numeros? ")
>     println(!numeros.contains(num))  // false
> }
> ```

<iframe src="https://pl.kotl.in/ynamo-AvU" width="560" height="450"></iframe>


> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val numeros = 3..7
>     println(numeros)
>     
>     val buscar1 = 2
>     val buscar2 = 12
>     val buscar3 = 5
>         
>     println("Rango: $numeros")
>         
>     print("El número $buscar1 está en el rango $numeros ? ")
>     println(buscar1 in numeros)
>     
>     if (buscar2 in numeros) println("El número $buscar2 está en el rango")
>     else println("El número $buscar2 NO está en el rango")
>     
>     println("El número $buscar3 ${if (buscar3 !in numeros) "NO está" else "está" } en el rango")
> }
> ```

<iframe src="https://pl.kotl.in/MBYfw6n50" width="560" height="350"></iframe>

## 10.3. Rangos descendentes

Es importante entender que, aunque Kotlin infiere muchas cosas, **no es consciente de que un rango sea decreciente**. Si no lo crees, prueba a cambiar el orden del [[2DAM_PMDM/Unidad 01/10. Rangos#^840e9f\|ejemplo anterior]] a `7..3` y verás que ni siquiera el `5` está dentro de ese rango. Al hacerlo, Kotlin ve un **rango vacío**.

Para que entienda que el rango es decreciente, hay que indicarlo de alguna forma. Veamos varias de ellas para el [[2DAM_PMDM/Unidad 01/10. Rangos#^840e9f\|ejemplo anterior]]:

```kotlin
// Esto:
val numeros = 7.downTo(3)  // 7, 6, 5, 4, 3
for (i in numeros) {
	//...
}
// Es lo mismo que esto otro:
val numeros = (3..7).reversed()  // 7, 6, 5, 4, 3
for (i in numeros) {
	//...
}
// O podemos crear el rango en el mismo bucle:
for (i in 7 downTo 3) {
	//...
}
```

Vemos que se puede usar la función **`reversed()`** sobre el rango o bien el aplicar la función **`downTo`**.

## 10.4. step

Por defecto, los rangos de Kotlin avanzan **de uno en uno**. El método `step` define el **tamaño del salto** entre los elementos de un rango o progresión.

Así, el salto establecido por defecto se `step = 1`, pero con el método `step` podemos  cambiarlo.

En el siguiente ejemplo indicamos que vamos a recorrer el rango de dos en dos. Así, el método `step` se puede usar de dos formas:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     println("Forma 1: indicándolo en el propio bucle:")
>     println("Impares del 1 al 9:")
>     for (i in 1..10 step 2) {
>         print("$i ")
>     }
>     print("\n".repeat(2))
>     println("Forma 2: generando otro rango con dicho salto:")
>     val impares = (1..10).step(2)
>     for (i in impares) {
>         print("$i ")
>     }
> }
> ```

<iframe src="https://pl.kotl.in/C8nGK_bXO" width="560" height="350"></iframe>

Este método, y prácticamente todos ellos, se pueden combinar con los anteriores:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     for (i in 8 downTo 0 step 2) print(i)
>     // 86420
>     
>     print("\n".repeat(2))
>     
>     val paresDesdendentes = 8.downTo(0).step(2)
>     for (i in paresDesdendentes) print(i)
>     // 86420
> }
> ```

<iframe src="https://pl.kotl.in/E-bALvEmN" width="560" height="250"></iframe>

## 10.5. Buenas prácticas

### Ahorro de memoria

El uso más recomendado para los rangos es no guardarlos en variables si es posible. De esa forma se ahorra espacio en memoria.

La naturaleza de los rangos es o bien recorrer un conjunto ordenado de elementos o comprobar si un elemento está dentro de unos límites. Para ambos casos, lo recomendable es hacer el rango en la misma condición a evaluar:

```kotlin
fun main() {
    val sueldo = 1656.78
    if (sueldo in 1000.0..2000.0) {
        println("Estás en la media")
    }
    
    for (num in (2..20).step(2)) {
        println(num)
    }
    
    for (i in 7 downTo 3) {
        //...
    }
}

```

### Listas de elementos

El uso más habitual es para gestionar listas de elementos (arrays, listas, sets, etc.).

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val frutas = listOf("Manzana", "Pera", "Plátano")
>     
>     println("Recorre la lista de principio a fin:")
>     for (i in 0 until frutas.size) {
>         println("Índice $i: ${frutas[i]}")
>     }
>     
>     println("\nRecorre la lista de fin a principio:")
>     for (i in 0.rangeUntil(frutas.size).reversed()) {
>         println("Índice $i: ${frutas[i]}")
>     }
>     
>     println("\nIgual que el anterior, de fin a principio:")
>     for (i in (frutas.size - 1) downTo 0) {
>         println("Índice $i: ${frutas[i]}")
>     }
> }
> ```

<iframe src="https://pl.kotl.in/7xXdeAl_7" width="560" height="350"></iframe>

Resumiendo, estas son algunas de las formas con las que podríamos iterar un rango:

```kotlin
for (i in 1..100) { ... }       // final cerrado: Incluye el 100
for (i in 1..<100) { ... }      // final abierto: No incluye el 100
for (i in 1+1..<100) { ... }    //final y principio cerrados
for (x in 2..10 step 2) { ... } //ascendente con paso 2
for (x in 10 downTo 1) { ... }  //descendente
(1..10).forEach { ... }         //de forma declarativa
```

Puedes consultar más formas de usar los rangos en arrays en la documentación oficial[^7].

[^7]:  ***Arrays from Ranges***. (2017, 1 noviembre). Kotlin Discussions. https://discuss.kotlinlang.org/t/arrays-from-ranges/5216



# 11. Control de flujo

Como ya sabemos de otros lenguajes de programación (como Java), podemos controlar la ejecución de determinados bloques de código para que se ejecuten o no dependiendo de alguna/s condición/es (sentencias condicionales) o que se repitan varias veces (bucles), etc.

> [!info] Interesante 
> Algo importante a remarcar es que las clásicas sentencias de control condicionales pueden usarse como expresiones (es decir, sentencias que **devuelve un resultado**).



## 11.1. Condicionales

### if - else if - else

El clásico **`if`** funciona en Kotlin como en otros lenguajes, pero puede ampliarse su uso de varias formas:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val a = 3
>     val b = 78
>     var valorMaximo = 0
>     
>     println("Opción 1:")
>     if (a > b)
>         valorMaximo = a
>     else
>         valorMaximo = b
>     println("El máximo es $valorMaximo")
>     
>     // Lo anterior, en una sola línea:
>     println("Opción 2:")
>     valorMaximo = if (a > b) a else b
>     println("El máximo es $valorMaximo")
>     
>     // Lo anterior, en bloques de código:
>     println("Opción 3:")
>     valorMaximo = if (a > b) {
>         println("El máximo es $a")
>         a
>     } else {
>         println("El máximo es $b")
>         b
>     }
> }
> ```

<iframe src="https://pl.kotl.in/CfaYA5h7G" width="560" height="550"></iframe>

La primera es la más conocida. La hemos usado mucho en Java.

La segunda y la tercera funcionan como una expresión. Según el resultado de la condición, se asigna un valor u otro a la variable `valorMaximo`.

> [!warning] Cuidado 
> Cuando se usa el **`if` como una expresión**, el `else` es **obligatorio** para garantizar que dicha expresión devuelve un valor.
> 
> Podemos verlo en el ejemplo anterior, las opciones 2 y 3. Para probarlo, quita el `else` a ver qué ocurre.
{ #7e7e7e}


> [!info] Kotlin no tiene operador ternario `? :` 
> El funcionamiento del **`if` como expresión** es tan versátil que Kotlin no necesita usar el operador ternario `?`, por lo que **no lo tiene implementado**.

### when

`when`[^8] equivale al `switch` de Java. Por tanto, permite mostrar de forma más sencilla la evaluación de varias condiciones, en lugar de usar una cascada de sentencias “if - else if - else”:  

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val posicion = 3
>     
>     when (posicion) {
>         1 -> print("Medalla de ORO")
>         2 -> print("Medalla de PLATA")
>         3 -> print("Medalla de BRONCE")
>         else -> {
>             print("No obtiene medalla")
>         }
>     }
> }
> ```

<iframe src="https://pl.kotl.in/eErL-b8Fq" width="560" height="300"></iframe>

Permite usar expresiones en las ramas de condiciones:  

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val posicion = 3
>     
>     when (posicion) {
>         posicion < 0 -> print("No puede haber posiciones negativas")
>         posicion == 1 -> print("Medalla de ORO")
>         posicion == 2 -> print("Medalla de PLATA")
>         posicion == 3 -> print("Medalla de BRONCE")
>         else -> {
>             print("No obtiene medalla")
>         }
>     }
> }
> ```

<iframe src="https://pl.kotl.in/yyG5GFgjP" width="560" height="300"></iframe>

Como indicamos al principio, `when` también puede tratarse como una expresión. En el siguiente ejemplo vemos cómo el resultado de un `when` se asigna a la variable `medalla`:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val posicion = 3
>     
>     val medalla = when (posicion) {
>         1 -> "ORO"
>         2 -> "PLATA"
>         3 -> "BRONCE"
>         else -> "-"
>     }
>     
>     println(medalla)
> }
> ```

<iframe src="https://pl.kotl.in/ipcJCYwYv" width="560" height="300"></iframe>

> [!warning] Cuidado 
> Con el `when` ocurre lo mismo que con el **`if` [[2DAM_PMDM/Unidad 01/11. Control de flujo#^7e7e7e\|cuando se usa como una expresión]]**: debe incluir **obligatoriamente** el `else` para que la expresión siempre devuelva un valor.

Por supuesto, `when` admite la combinación de varios valores en una misma rama de condición. En el siguiente ejemplo vemos cómo se evalúan los valores 1, 2 y 3 en una sola rama:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val posicion = 33
>     val mensaje = when (posicion) {
>         1, 2, 3 -> "Ha ganado medalla!"
>         else -> "Lo sentimos mucho. Que no decaiga el ánimo!"
>     }
>     println(mensaje)
> }
> ```

<iframe src="https://pl.kotl.in/Zn6un7R1p" width="560" height="250"></iframe>

Podemos usar **rangos**:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val delUnoAlDiez = 1..10
>     
>     val numero1 = 8
>     var mensaje = when (numero1) {
>         in delUnoAlDiez -> "Está entre los 10 primeros!"
>         else -> "No está en la mejor clasificación."
>     }
>     println("Posición $numero1 - $mensaje")
>     
>     // Otra forma
>     val numero2 = 88
>     mensaje = when (numero2) {
>         !in delUnoAlDiez -> "No está en la mejor clasificación."
>         else -> "Está entre los 10 primeros!"
>     }
>     println("\nPosición $numero2 - $mensaje")
> }
> ```

<iframe src="https://pl.kotl.in/IE-PyX2i0" width="560" height="450"></iframe>

También se puede utilizar el operador **`is`** para ejecutar determinadas acciones según el tipo de dato:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val nombre1 = "Pepe"
>     val nombre2 = "Ana"
>     val numero = 10
>     var empiezaPorAOEsDiez = hasPrefix(nombre1)
>     
>     println(empiezaPorAOEsDiez)
>     
>     empiezaPorAOEsDiez = hasPrefix(nombre2)
>     println(empiezaPorAOEsDiez)
>     
>     empiezaPorAOEsDiez = hasPrefix(numero)
>     println(empiezaPorAOEsDiez)
> }
> fun hasPrefix(x: Any) = when(x) {
>     is String -> x.startsWith("A")
>     is Int -> x == 10
>     else -> false
> }
> ```

<iframe src="https://pl.kotl.in/d0IAl6ZVq" width="560" height="430"></iframe>

¿Nos hemos pasado un poco con este último ejemplo? ¿La función `hasPrefix` se escribe de forma muy rara? No te agobies, cuando veamos las funciones la entenderás perfectamente.

## 11.2. Bucles

Los bucles son similares a Java, al igual que las [expresiones para interrumpirlos](https://kotlinlang.org/docs/returns.html).

Los bucles son estructuras de control fundamentales en la programación que nos permiten ejecutar una serie de instrucciones repetidamente mientras se cumpla una determinada condición. En Kotlin, al igual que en Java, los tipos más comunes de bucles son:

* For  
* While  
* Do-While

Muchas veces para modificar el flujo de ejecución usaremos las conocidas expresiones:

* **`break`**: termina inmediatamente la ejecución de las instrucciones dentro del bucle, saltando a la siguiente línea después del bucle.  
* **`continue`**: salta el código que haya dentro del cuerpo del bucle a la siguiente iteración.

### for

El bucle `for`[^9] se utiliza cuando se conoce de antemano el número de iteraciones.

Lo habitual es hacerlo [[2DAM_PMDM/Unidad 01/10. Rangos#Listas de elementos\|con rangos]], como hemos visto en apartados anteriores.

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     println("Recorrer un rango numérico:")
>     
>     for (numero in 1..10) println(numero)
>     
>     println("---------------------")
>     println("Recorrer un rango numérico (excluyendo el final)")
>     
>     for (numero in 1 until 10) println(numero)
>     
>     println("---------------------")
>     println("Recorrer un rango numérico de 3 en 3:")
>     
>     for (numero in 1..30 step 3) println(numero)
>     
>     println("---------------------")
>     println("Recorrer el rango numérico en orden descendente (1):")
>     
>     for (numero in 10 downTo 1) println(numero)
>     
>     println("---------------------")
>     println("Recorrer el rango numérico en orden descendente (2):")
>     
>     for (numero in (1..10).reversed()) println(numero)
>     
>     println("---------------------")
>     println("Recorrer el rango numérico en orden descendente de 2 en 2:")
>     
>     for (numero in (1..10).reversed() step 2) println(numero)
> }
> ```

<iframe src="https://pl.kotl.in/WZQrEIaFU" width="560" height="750"></iframe>

Para recorrer un array, por ejemplo, de la forma clásica (por sus índices):

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val array = arrayOf("a", "b", "c")
>     
>     for (i in array.indices) {
>         println(array[i])
>     }
> }
> ```

<iframe src="https://pl.kotl.in/vgpXrz312" width="560" height="220"></iframe>

O usando una tupla (índice, valor):

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     val array = arrayOf("a", "b", "c")
>     
>     for ((index, value) in array.withIndex()) {
>         println("El elemento en la posicion $index es $value")
>     }
> }
> ```

<iframe src="https://pl.kotl.in/HXy0k3chi" width="560" height="250"></iframe>

> [!info]  
> Investiga cómo funciona `withIndex()` para entender mejor el ejemplo anterior.

### while, do-while

El `while`[^10] y el `do-while` se ejecutan mientras la condición que evalúan sea verdadera. La diferencia (recuerda) es que el `do-while` se ejecutaba al menos una vez, pero el `while` podría no ejecutarse ninguna si la condición no se cumple:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     var x = 7
>     
>     while (x > 0){
>         println(x)
>         x--
>     }
> }
> ```

<iframe src="https://pl.kotl.in/nG6FERQwa" width="560" height="250"></iframe>

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     var x: Int = 0
>     
>     do {
>         println(x)
>         x++
>     } while(x < 10)
> }
> ```

<iframe src="https://pl.kotl.in/lypOJ7d1T" width="560" height="250"></iframe>

Los ejemplos de la web oficial son más bonicos:

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     var carsInGarage = 0
>     val maxCapacity = 3
>     
>     while (carsInGarage < maxCapacity) {
>         println("Car entered. Cars now in garage: ${++carsInGarage}")
>     }
>     // Car entered. Cars now in garage: 1
>     // Car entered. Cars now in garage: 2
>     // Car entered. Cars now in garage: 3
>     
>     println("Garage is full!")
>     // Garage is full!
> }
> ```

<iframe src="https://pl.kotl.in/jEZZTU0Wa" width="560" height="300"></iframe>

> [!abstract]- Código 
> ```kotlin
> fun main() {
>     var roll: Int
>     
>     do {
>         roll = Random.nextInt(1, 7)
>         println("Rolled a $roll")
>     } while (roll != 6)
>     // Rolled a 2
>     // Rolled a 6
>     
>     println("Got a 6! Game over.")
>     // Got a 6! Game over.
> }
> ```

<iframe src="https://pl.kotl.in/jEZZTU0Wa" width="560" height="300"></iframe>

[^8]:  MoureDev by Brais Moure. (2019b, agosto 8). KOTLIN: ***Curso ANDROID desde CERO \- SENTENCIA WHEN \- Lección 4 \[2020\] | Español*** | MoureDev \[Vídeo\]. YouTube. [https://www.youtube.com/watch?v=ufsrPf7vao4](https://www.youtube.com/watch?v=ufsrPf7vao4)

[^9]:  Conditions and loops | Kotlin. (s. f.). Kotlin Help. https://kotlinlang.org/docs/control-flow.html#for-loops

[^10]:  Conditions and loops | Kotlin. (s. f.-b). Kotlin Help. https://kotlinlang.org/docs/control-flow.html#while-loops


# 12. Funciones

Una función es un conjunto de instrucciones que realizan una tarea específica y se encuentran empaquetadas como una unidad en un bloque de código.

En Kotlin se afirma que las funciones son “[ciudadanos de primera clase](https://en.wikipedia.org/wiki/First-class_function)”, lo que permite **tratarlas como objetos** que pueden ser almacenados en variables, **pasarlas como argumentos a otras funciones** y **devolverlas como resultado de funciones**, dándoles una flexibilidad y expresividad funcional que facilita la creación de código modular y reutilizable.

Las funciones pueden funcionar como métodos dentro de una clase o de forma independiente, en un fichero Kotlin (`.kt`) de funciones.

Para declarar funciones en Kotlin, usamos la palabra reservada **`fun`**. Veamos una función en Java y su equivalente en Kotlin:

Java:

```java
public int dobleDe(int x) {
    return 2 * x;
}
```

Kotlin:
```kotlin
fun dobleDe(x: Int): Int {
    return 2 * x
}
```

![ud01_pmdm_01_fun.png](/img/user/adjuntos/2DAM_PMDM/Unidad_01/ud01_pmdm_01_fun.png)

Como puede observarse, no hay un modificador de acceso (`public`, `private`, etc.). Esto es porque en Kotlin **todas las funciones son públicas por defecto**.

Si una función no devuelve ningún valor, en Kotlin devolverá el objeto **`Unit`**. Veamos otro ejemplo tanto en Java como Kotlin:

Java:

```java
public void imprimirMensaje(String mensaje) {
    System.out.println(mensaje);
}
```

Kotlin:
```kotlin
fun imprimirMensaje(mensaje: String): Unit {
    println(mensaje)   
}
```

**`Unit`** es similar al **void en Java**, salvo que a diferencia de este último no es una palabra reservada, sino **un tipo de dato más**. Tiene una única instancia, pero instancia al fin y al cabo. Esto significa que podemos tratarlo como un objeto y devolverlo explícitamente, algo que igual ahora no te dice mucho, pero te resultará útil más adelante cuando comprendas cómo utilizar funciones de orden superior.

Lo habitual es que `Unit` esté implícito y no sea necesario indicarlo:

```kotlin
fun imprimirMensaje(mensaje: String) {
    println(mensaje)   
}
```

## 12.1. Funciones como expresión

Si declaramos una función que retorna una única expresión, podemos expresarla de forma más sencilla ahorrándonos las llaves (`{}`) y la palabra reservada **`return`** y sustituirlo por un **`=`**. Las siguientes funciones son totalmente equivalentes:

```kotlin
//Forma tradicional
fun double(x: Int): Int {
    return x * 2
}

//Como expresión con tipo
fun double(x: Int): Int = x * 2
```

Si ádemás el **tipo de retorno** pueda ser inferido por el compilador, también podemos obviarlo:

```kotlin
//Como expresión con tipo inferido
fun double(x: Int) = x * 2
```

## 12.2. Parámetros

Los parámetros se definen como cualquier variable en Kotlin, y se separan mediante comas:

```kotlin
fun potencia(base: Int, exponente: Int) { /*...*/ }

fun areaRectangulo(
    base: Int,
    altura: Int
) { /*...*/ }
```

### Valores por defecto

En ocasiones enviamos a algunas funciones el mismo valor con mucha frecuencia. Por ejemplo, para calcular calcular el precio total (incluyendo el IVA, que en la actualidad suele ser el **21%**):

> [!abstract]- Código 
> ```kotlin
> fun calcularPrecioFinal(
>     precioBase: Double,
>     porcentajeIva: Double = 21.0,
> ): Double {
>     val impuesto = precioBase * (porcentajeIva / 100)
>     return precioBase + impuesto
> }
> 
> fun main() {
>     // Usa el valor por defecto
>     val precioNormal = calcularPrecioFinal(100.0)
>     println("Precio con IVA estándar (21%): €$precioNormal")
>     // Resultado: 121.0
>     
>     // Sobrescre el valor por defecto
>     val precioReducido = calcularPrecioFinal(100.0, 10.0)
>     println("Precio con IVA reducido (10%): €$precioReducido")
>     // Resultado: 110.0
> }
> ```

<iframe src="https://pl.kotl.in/vIMqQlEDV" width="560" height="410"></iframe>

> [!warning] Recuerda 
> Los parámetros **sin valor por defecto** son **OBLIGATORIOS**.
> Los parámetros **con valor por defecto** son **OPCIONALES**.

> [!abstract]- Código 
> ```kotlin
> fun saludo(
>     nombre: String,
>     mensaje: String = "Hola",
> ) {
>     println("$mensaje, $nombre")
> }
> 
> fun main() {
>     // Si queremos enviar solo el saludo, y lo hacemos así...
>     saludo("Saludos!")
>     // estaremos dando a entender a la función que "Saludos!"
>     saludo("Anselmo", "Saludos!")
>     
>     /*
>      * Los parámetros sin valor por defecto son OBLIGATORIOS.
>      * Los parámetros con valor por defecto son OPCIONALES.
>      */
>      saludo(mensaje = "Hello!")  // ❌ Error! Falta el parámetro nombre
> }
> ```

<iframe src="https://pl.kotl.in/iIwnPaGx9" width="600" height="400"></iframe>

Hay que tener **cuidado con el orden en que se ponen los parametros** si hay algunos con valores por defecto. Si hay parámetros con valores por defecto antes que sin ellos, ¿cómo haces para obviar el valor por defecto?

```kotlin
fun saludo(
    mensaje: String = "Hola",
    nombre: String,
) {
    println("$mensaje, $nombre")
}

fun main() {
    saludo("Pepe") // ❌ Error! Falta el parámetro nombre
}
```

En estos casos hay que **nombrar el parámetro**:

```kotlin
fun saludo(
    mensaje: String = "Hola",
    nombre: String,
) {
    println("$mensaje, $nombre")
}

fun main() {
    saludo(nombre = "Pepe") // 👍
}
```

De esta forma incluso se pueden enviar los parámetros en distintos orden:

> [!abstract]- Código 
> ```kotlin
> fun saludo(
>     mensaje: String = "Hola",
>     nombre: String,
>     desearBuenDia: Boolean = true,
>     saludosAFamilia: Boolean = true,
> ) {
>     println("$mensaje, $nombre")
>     if (desearBuenDia) println("Espero que tengas un buen día!")
>     if (saludosAFamilia) println("Manda saludos a tu familia!")
> }
> 
> fun main() {
>     // La forma habitual:
>     saludo(
>         "Buenos días",
>         "Pepe",
>         true,
>         false,
>     )
>     println()
>     // Nombrando parámetros (orden distinto):
>     saludo(
>         desearBuenDia = false,
>         saludosAFamilia = true,
>         nombre = "Telmo",
>     )
> }
> ```

<iframe src="https://pl.kotl.in/po_9VeeFe" width="560" height="550"></iframe>

### vararg

Si queremos hacer una función pero no conocemos de antemano el número de parámetros, o éste es cambiante, podemos usar parámetros `vararg`, que es equivalente a las [[1DAM_Programación/Unidad 05/2. Arrays unidimensionales (vectores)#2.3.1. Funciones variádicas\|funciones variádicas]] en Java.

De hecho ya los has usado, aunque no te hayas dado cuenta. Por ejemplo, cuando creamos colecciones con [`listOf`][kotlin_listof], podemos introducir el número de elementos que nos plazca. Y si ves la [definición][kotlin_listof] de esta función:

```kotlin
fun <T> listOf(vararg elements: T): List<T>
```

¡Ahí lo tenemos! El parámetro `elements` es un `vararg`.

La palabra clave `vararg` (**var**iable **arg**uments) indica que el parámetro acepta un **número indeterminado** de valores separados por comas. Se explica mejor con un ejemplo:

> [!abstract]- Código 
> ```kotlin
> fun media(vararg numeros: Int): Double {
>     if (numeros.isEmpty()) return 0.0
>     return numeros.sum().toDouble() / numeros.size
> }
> 
> fun main() {
>     // Pasamos distintas cantidades de números:
>     val media1 = media(10, 20, 30)       // Resultado: 20.0
>     val media2 = media(5, 5, 10, 10, 15) // Resultado: 9.0
>     val media3 = media()                 // Resultado: 0.0
>     
>     println("Media 1: $media1")
>     println("Media 2: $media2")
>     println("Media 3: $media3")
> }
> ```

<iframe src="https://pl.kotl.in/KiQfiy2DM" width="560" height="330"></iframe>

En el código anterior queremos calcular la media de los números que nos pasen, que no sabemos cuántos serán. A priori podríamos sobrecargar la función para distintos números de parámetros: `media(a, b)`,  `media(a, b, c)`, etc., pero ¿cuántas funciones tendríamos para hacer la misma tarea? Con `vararg` evitamos todo esto. 

Al igual que en Java, el parámetro `vararg` se comporta como un **[Array][kotlin_array]**. Por eso en el ejemplo anterior podemos usar funciones como `.isEmpty()`, `.sum()` y `.size`.

Si queremos **pasar directamente un array**, hay dos diferencias con respecto a Java que debemos tener en cuenta:

1. Si vamos a introducir datos básicos (`Int`, `Double`, etc.), debemos crear un array específico (`intArrayOf`, `doubleArrayOf`...).
   Si intentamos introducir un array creado con `arrayOf`, como veremos en el siguiente ejemplo, dará un error.
2. **Es necesario usar el operador `*`** para descomponer el array en elementos individuales.

> [!abstract]- Código 
> ```kotlin
> fun media(vararg numeros: Int): Double {
>     if (numeros.isEmpty()) return 0.0
>     return numeros.sum().toDouble() / numeros.size
> }
> 
> fun main() {
>     val listaNumeros1 = arrayOf(10, 20, 30)
>     val listaNumeros2 = intArrayOf(4, 5, 6, 7)
>     
>     val media1 = media(*listaNumeros1) // ❌ Error! Estamos pasando un Array<Int>
>     val media2 = media(*listaNumeros2) // Resultado: 5.5
>     
>     println("Media 1: $media1")
>     println("Media 2: $media2")
> }
> ```

<iframe src="https://pl.kotl.in/ZeZO4CB5A" width="560" height="330"></iframe>

Al ejecutar el código anterior debe dar el siguiente error:

```
❌ Argument type mismatch: actual type is 'Array<Int>', but 'IntArray' was expected.
```

¿Y qué mas da? Ambos son arrays de enteros, ¿no? Si y no. En Kotlin, `IntArray` y `Array<Int>` son tipos de datos totalmente diferentes y **no son intercambiables**:

* `Array<Int>` equivale a un **array de objetos `Integer`** en Java (`Integer[]`).  
  Este es el array que genera la función `arrayOf(a, b, c)`.
* `IntArray`, en cambio, es lo mismo que un **array de `int`** (`int[]`) y que está generado por la función `intArrayOf(a, b...)` y que es el que admite `vararg: Int`.

> [!info]- Para saber más...  
> Cuando definimos la función como `fun media(vararg numeros: Int)`, Kotlin optimiza el código convirtiendo ese `vararg` en un `int[]` de Java para evitar el coste de memoria de los objetos. Por eso, al pasarle un `Array<Int>` creado con `arrayOf` (un `Integer[]` de Java), el compilador se queja porque no puede meter objetos `Integer` (que son más pesados que los datos primitivos) dentro de una estructura optimizada para elementos primitivos.

> [!warning] En conclusión 
> Si en lugar de pasar parámetros sueltos a un parámetros `vararg` le **enviamos un array de datos primitivos**, debemos:
> 1. Enviar un array del tipo de dato específico  ([`intArrayOf`][kotlin_intArrayOf], [`doubleArrayOf`][kotlin_doubleArrayOf], [`charArrayOf`][kotlin_charArrayOf], etc.).
> 2. Usar el operador `*`.

### Funciones con genéricos

¿Recuerdas cuando vimos los [[1DAM_Programación/Unidad 05/9. Clases y métodos con tipos genéricos#^0599d8\|genéricos en los métodos de Java]]?

En Kotlin es muy similar. Veamos la comparación entre ambas:

Java:

```java
public static <T> void imprimir(T valor) {
    System.out.println(valor);
}
```

Kotlin:

```kotlin
fun <T> imprimir(valor: T) { println(valor) } 
```


> [!abstract]- Código 
> ```kotlin
> fun <T> imprimir(valor: T) { println(valor) } 
> 
> fun main() {
>     imprimir(7)
>     imprimir("Hola, clase!")
>     imprimir(true)
> }
> ```

<iframe src="https://pl.kotl.in/l2OBvVqb_" width="560" height="250"></iframe>

# Referencias

Para más información, visita la web [oficial de referencia][kotlin_funciones].

[kotlin_array]: https://kotlinlang.org/docs/arrays.html
[kotlin_listof]: https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.collections/list-of.html
[kotlin_intArrayOf]: https://kotlinlang.org/api/core/kotlin-stdlib/kotlin/int-array-of.html
[kotlin_doubleArrayOf]: https://kotlinlang.org/api/core/kotlin-stdlib/kotlin/double-array-of.html
[kotlin_charArrayOf]: https://kotlinlang.org/api/core/kotlin-stdlib/kotlin/char-array-of.html
[kotlin_funciones]: https://kotlinlang.org/docs/functions.html
