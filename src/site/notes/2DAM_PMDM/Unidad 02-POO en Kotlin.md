---
{"dg-publish":true,"permalink":"/2-dam-pmdm/unidad-02-poo-en-kotlin/","dg-note-properties":{"modulo":"[[Módulos/PMDM]]","libro":"[[Apuntes/PMDM (2º DAM)]]"}}
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


# 1. Clases y objetos

Kotlin, al igual que Java, contempla el paradigma de <abbr title="Programación Orientada a Objetos">POO</abbr>. Por tanto, encapsula en objetos tanto su **estado** (valor de las propiedades) como su **funcionalidad** (métodos o funciones). Además incorpora la **programación funcional** de base, lo que ayuda a simplificar el código, evitar errores y facilitar el mantenimiento. Aunque la aplicación de este paradigma lo veremos más tarde.

Aunque la POO es, conceptualmente, la misma que en Java, cambian las formas. Así que ¡manos a la obra!

## 1.1. Declarando clases

A diferencia de Java, Kotlin unifica la **declaración de la clase** con su **constructor principal** en una sola línea. En otras palabras, Kotlin permite declarar una clase y sus propiedades como si fuesen parámetros:

```kotlin
/*
 * Declaración de la clase Persona con las propiedades nombre y edad.
   Al no tener métodos o funciones miembro, no necesita usar las llaves.
 */
class Persona(val nombre: String, var edad: Int)

/*
 * El método "public static void main" que usaba Java para arrancar una
 * aplicación se sustituye por la función main en Kotlin
 */
fun main() {
    var p = Persona("Telmo", 33) // Instancia de un objeto Persona
    println(p.nombre)            // Acceso a sus propiedades
}
```

Observa que a la hora de instanciar objetos (como `p`), **Kotlin no usa la palabra reservada `new`**:
```kotlin
    ...
    var p = Persona("Telmo", 33) // Instancia de un objeto Persona
    ...
```

> [!info]  
> En las primeras versiones de Kotlin el constructor se indicaba con la misma palabra clave. En el caso anterior, sería:
> ```kotlin
> class Persona constructor(val nombre: String, var edad: Int)
> ```
> En la actualidad no es necesario usar la palabra clave `constructor`.

Si escribimos el código anterior **en Java**, quedaría así:

```java
class Persona {
    public final String nombre; 
    public int edad;
    
    public Persona(String nombre, int edad) {
        this.nombre = nombre;
        this.edad = edad;
    }
}

public class Main {
	public static void main(String[] args) {
	    Persona p = new Persona("Telmo", 33);
		System.out.println(p.nombre);
	}
}
```

La economía en línea de código es palpable solo con la clase `Persona`. En Kotlin se implementa en una línea y aquí en 9.

### Constructor principal, propiedades y funciones miembro

En los ejemplos anteriores se ve cómo Kotlin permite definir un **constructor principal** en la cabecera de la clase, de forma similar a como se definen los parámetros de una función. Los parámetros son las **propiedades** de dicha clase que serán visibles desde dicho constructor, donde **`nombre` es una costante** (inmutable) y **`edad` es una variable** (mutable).

> [!warning] Importante 
> Para que los **parámetros del constructor principal** sean propiedades de la clase, **deben llevar la palabra clave `val` o `var`**. De lo contrario, son solo parámetros que no formarán parte del estado de los objetos de esa clase. En tal caso deben asignarse a una propiedad o usarse en alguna función miembro.

Como se puede observar, las propiedades son **públicas por defecto**, al igual que las funciones miembro. Es más, **en Kotlin todo es público mientras no se diga lo contrario**.

Se pueden definir **propiedades dentro de la clase**. Al no estar en el constructor principal, **no son estrictamente necesarias para la instanciación de objetos**. En el siguiente caso, tenemos las propiedades `nombre` y `edad` en el constructor principal y `matriculado` y `expediente` declaradas dentro de la clase:

```kotlin
class Persona(val nombre: String, var edad: Int) {
    var matriculado: Boolean = false
    var expediente: String? = null
}

fun main() {
    val personaFake = Persona()  // ❌ Error! nombre y edad obligatorios
    val p = Persona("Telmo", 33) // Instancia de objeto Persona sin new
    
    // Estado del objeto p:
    println(p.nombre)      // Temo
    println(p.edad)        // 33 
    println(p.matriculado) // false
    println(p.expediente)  // null
}
```

Si queremos que algunas propiedades sean **privadas**, es decir, que sean visibles sólo por la clase e invisible para el resto, se añade el `private` al principio de la declaración:

```kotlin
class Motor {
    // Propiedades privadas
    private val numeroDeSerie: String = "MOT-2026-XYZ"
    private var temperatura: Int = 20

    fun arrancar() {
        // Visibles dentro de la clase
        temperatura = 90
        println("Motor encendido. Número de serie: $numeroDeSerie")
    }

    fun mostrarEstado() {
        // Visible dentro de la clase
        println("Temperatura actual: $temperatura°C")
    }
}

fun main() {
    val miMotor = Motor()
    
    miMotor.arrancar()
    miMotor.mostrarEstado()

    // miMotor.temperatura = 100 
    // ❌ ERROR: No es accesible desde fuera de la clase

    // miMotor.numeroDeSerie = "OTRO-123" 
    // ❌ ERROR: Es privada y además es una constante (val)
}

```

Podemos añadir las **funciones miembro** (**métodos** en Java) que creamos oportunas. Como `printInfo` en el siguiente ejemplo, que hará uso de todas las propiedades: 

```kotlin
class Persona(val nombre: String, var edad: Int) {
    var matriculado: Boolean = false
    var expediente: String? = null
    
    fun printInfo() {
        if (matriculado)
        	println("$nombre, de $edad de edad, tiene la matrícula registrada")
        else
        	println("$nombre, de $edad de edad, no se ha matriculado")
        
        println(expediente?.let {
            "Su expediente: $expediente"
        } ?:run {
            "No hay expediente registrado"
        })
    }
}

fun main() {
    val p = Persona("Telmo", 33)
    p.printInfo()
    println("---------------------------")
    p.expediente = "Expediente de Telmo" // propiedades públicas por defecto
    p.printInfo()
}
```

### Bloque de inicialización - `init`

Ya hemos visto que el **constructor principal** equivale al **constructor estańdar de Java que solo sirve para inicializar las propiedades**. Nada más. Pero ¿y si queremos hacer un constructor más complejo que el anterior, donde haya más lógica, valicaciones de los datos de entrada, etc?

Imaginemos que queremos hacer lo que se hace en este código de Java para validar que la edad no sea negativa:

```java
class Persona {
    public final String nombre; 
    public int edad;
    
    public Persona(String nombre, int edad) {
        this.nombre = nombre;
        this.edad = (edad < 0) ? 0 : edad;  // validamos la edad
    }
}
```

El constructor principal, tal y como está planteado, no puede albergar código. Para darle lógica hay usar el bloque `init`:

```kotlin
class Persona(val nombre: String, var edad: Int) {
    init {
        edad = if (edad < 0) 0 else edad
    }
}
```

El bloque de inicialización **`init` contiene la lógica del constructor principal** y **se ejecuta después de él**. Es decir, primero se inicializan las propiedades indicadas en el constructor principal y después se ejecuta `init`.

> [!question] ¿Cómo lo harías? 🤔
> ¿Cómo harías el ejemplo anterior si pasamos edad como un parámetro, no como una propiedad? Es decir, si:
> ```kotlin
> class Persona(val nombre: String, edad: Int) {
>     ...
> ```
> Si tengo ese parámetro y, dentro de la clase, la propiedad `edad`, ¿cómo distingo una del otro y cómo hago para asignar a la propiedad el valor del parámetro?

Si te fijas, el bloque `init` se ejecuta una sola vez y en el momento de instanciar un objeto. Aquí tenemos un problema. La propiedad `edad` se valida al ejecutar el constructor principal (al instanciar un objeto), pero... ¿y si luego le asigno un valor negativo?

> [!abstract]- Código 
> ```kotlin
> class Persona(val nombre: String, var edad: Int) {
>     init {
>         edad = if (edad < 0) 0 else edad
>     }
> }
> fun main() {
>     val p = Persona("juan", -33)
>     println(p.edad)       // Imprime: 0
>     p.edad = -33
>     println(p.edad)       // Imprime: -33
> }
> ```

<iframe src="https://pl.kotl.in/NyaW1S5yO" width="560" height="450"></iframe>

Pues vaya... parece que el `init` solo sirve para arrancar.  Pero no te agobies, que esto tiene solución.


### `getters` y `setters`

Para resolve el problema anterior es conveniente implementar esas validaciones en el *setter* de la propiedad. En Kotlin podríamos implementar *setters* y *getters*, aunque de forma muy distinta a la de Java. Para el ejemplo anterior, podríamos caer en la tentación de hacer un código ***Java-like*** como el siguiente:

```kotlin
class Persona...    
    // getters
    fun getNombre(): String { return this.nombre }
    fun getEdad(): Int { return this.edad }
    fun getMatriculado(): Boolean { return this.matriculado }
    fun getExpediente(): String { return this.expediente }

    // setters
    fun setNombre(nuevoNombre: String) { this.nombre = nuevoNombre }
    fun setEdad(nuevaEdad: Int) { this.edad = nuevaEdad }
    fun setMatriculado(nuevoMatriculado: Boolean) {
        this.edad = nuevoMatriculado
    }
    fun setExpediente(nuevoExpediente: String) {
        this.expediente = nuevoExpediente
    }
. . .

```

Y esto funciona correctamente, pero **no son los *getters* y *setters* reales**. Son solo **funciones miembro**.

Como las **propiedades** de una clase son **públicas por defecto**, no necesitan ni *setters* ni *getters*. Pero si queremos establecer alguna lógica en ellos, es necesario **declarar la propiedad dentro de la clase** (no en el constructor principal). El motivo es la forma de implementar el *getter* y el*setter*. Por ejemplo, los que Kotlin establece por defecto para cada propiedad equivalen a algo como esto:

```kotlin
/*
 Declaramos la propiedad de la clase dentro de esta, y justo debajo
 escribimos los métodos get() y/o set(value)
*/
var nombre: String = "Pepe"
    get() { // --------- getter
        return field
    }
    set(value) { // ---- setter
        field = value
    }
```

Fíjate bien en la nomenclatura: debajo de la propiedad se crean dos funciones (sin la palabra reservada `fun`): **`get()`** y **`set(value)`**. Esas funciones son respectivamente el *getter* y *setter* **reales** de la propiedad `nombre`. 

Dentro de `get()` se usa la variable **`field`**. Y dentro de `set(value)` se usan `field` y **`value`**:

* `field` representa a la propiedad. Es decir, `field` es literalmente la propiedad `nombre`.
* `value` se refiere al valor que se le asigna a la propiedad.

Si queremos hacer las cosas bien, en ambos casos es obligatorio el uso de `field` en lugar de usar el nombre de la propiedad.

Y ahora viene algo más extraño: **¿cómo se ejecutan?** De forma intuitiva...

> [!abstract]- Código 
> ```kotlin
> class Persona(nombreInicial: String) {
>     var nombre: String = ""
>         set(value) {
>             println("Setter llamado con: $value")
>             field = value.uppercase() // Modifica el texto a mayúsculas
>         }
>     init {
>         // Esta asignación activa el setter personalizado
>         this.nombre = nombreInicial
>     }
> }
> fun main() {
>     val p = Persona("juan") // Imprime: Setter llamado con: juan
>     println(p.nombre)       // Imprime: JUAN
>     p.nombre = "Anselmo"
>     println(p.nombre)       // Imprime: ANSELMO
> }
> ```

<iframe src="https://pl.kotl.in/LvI227Wks" width="560" height="450"></iframe>

En el ejemplo anterior no vemos ningún `p.nombre.get()`. En su lugar, simplemente llamamos a la propiedad `nombre` del objeto `p`:
```kotlin
    ...
    println(p.nombre)
    ...
```

Al hacerlo estamos pidiendo el valor de la propiedad. Es decir, estamos pidiendo que se ejecute el *getter*. Y este se ejecuta siempre. **Siempre**. Incluso cuando no lo definimos, porque todas las propiedades tienen implícitamente un *getter* y un *setter*:

```kotlin
/*
 Si no definimos ni getter ni setter a una propiedad, los tienen
 implementados implícitamente. Aunque no se ven en el código, es
 como si tuvieran estos getter y setter:
*/
var nombre: String = "Pepe"
    get() { // --------- getter estándar
        return field
    }
    set(value) { // ---- setter estándar
        field = value
    }
```

¿Y el *setter*? Si no había llamada explícita para el *getter*, tampoco la hay en este caso.
¡Recuerda! Se entiene de forma intuitiva: si para obtener el valor de una propiedad simplemente la llamo (`p.nombre`) y eso ejecuta su *getter*, para asignarle un valor... pues eso, le asigno el valor `p.nombre = "Anselmo"` e implícitamente se ejecuta su `set("Anselmo")`. **Es la asignación la que lanza el *setter***.

Si ejecutas el código anterior, verás ejecutar `p.nombre = "Anselmo"` y mostrar el valor de nombre inmediatamente después, verás que el *setter* lo ha convertido en `"ANSELMO"` antes de guardarlo en `nombre`.

> [!warning] Importante 
> El `getter` y el `setter` de una propiedad  funcionan de forma distinta en Kotlin, ya que **van asociados directamente a su propiedad**. No son funciones aparte (funciones miembro). Se declaran inmediatamente debajo de la propiedad:
> ```kotlin
> class Clase(val propiedad1: String) {
>     var edad: Int = 0
>         [private] set([value]) {
>             // El setter no admite valores negativos para la propiedad
>             field = if (value < 0) ? 0 else value
>         }
}
> ```

Así que, en caso de establecer *setters* (y/o *getters*), esas propiedades deben declararse **dentro de la clase** y en el bloque `init` se les asignan los valores introducidos como parámetros.

Así, para el ejemplo del apartado anterior, la solución podría ser la siguiente:

> [!abstract]- Código 
> ```kotlin
> class Persona(val nombre: String, edad: Int) {
>     var edad: Int = 0
>         set(value) {
>             field = if (value < 0) 0 else value
>         }
>         
>     init {
>         this.edad = edad // lanza el set de edad
>     }
> }
> fun main() {
>     val p = Persona("juan", -33)  // Lanza el init
>     println(p.edad)       // Imprime: 0
>     p.edad = -33		  // lanza el set de edad
>     println(p.edad)       // Imprime: 0
> }
> ```

<iframe src="https://pl.kotl.in/-ySUZxQ2a" width="560" height="450"></iframe>






[kotlin_tipos]: https://kotlinlang.org/docs/types-overview.html



[^1]:  Basic syntax | Kotlin. (s. f.-b). Kotlin Help. https://kotlinlang.org/docs/basic-syntax.html#variables


# 2. Herencia

En Java se puede declarar una variable indicando como tipo de dato una de las interfaces que implemente. Así parece que el tipo de dato es esa interfaz.

Kotlin ve esto de forma intuitiva (repetimos mucho esta palabra, si). Para indicar qué interfaz implementa una clase se hace de forma similar a como se hace con los tipos de datos:

> [!abstract]- Código 
> ```kotlin
> open class Persona(var nombre:String,
>                    var dni:String,
>                    var edad:Int)
> 
> class Empleado(nombre:String,
>                dni:String,
>                edad:Int,
>                var sueldo: Float): Persona(nombre, dni, edad)
> fun main() {
>     val persona1 = Persona("Anselmo", "88888888X", 32)
>     val empleado1 = Empleado("Pelayo", "11111111A", 41, 1500f)
>     
>     println(persona1.nombre)
>     println(empleado1.nombre)
> }
> ```

<iframe src="https://pl.kotl.in/ayxSOhEyN" width="560" height="450"></iframe>

## Permitir herencia y sobreescritura - `open`

En Kotlin **las clases son finales por defecto, al igual que sus miembros**. Es decir, que por defecto no se puede heredar de una clase ni se pueden sobreescribir sus miembros a menos que se les añada **`open`**.

En el código anterior vemos una primera clase con el modificador `open`, lo que nos da a entender que será la superclase.

La clase `Empleado` hereda de `Persona` porque lo indicamos como si fuera un tipo de dato. Ponemos los dos puntos `:` y después el constructor de la superclase:

```kotlin
class Empleado(nombre:String,
                dni:String,
                edad:Int,
                var sueldo: Float): Persona(nombre, dni, edad)
```

Observa que no hay ni `val` ni `var`, ni en `Persona` ni en `Empleado`. Esto es porque **no estamos creando nuevas propiedades**.  Al omitir `val`/`var`, el parámetro actúa como un argumento normal de una función: llega, se lo entrega al padre y desaparece. En cambio, `sueldo` si es una propiedad nueva y por eso lleva el `var`.

Hay que tener en cuenta varias consideraciones. La primera es que los nombres de la superclase no necesariamente deben coincidir con los originales, pero si deben coincidir los de la subclase con los de la clase que hereda:

```kotlin
open class Persona(var nombre:String,
                   var dni:String,
                   var edad:Int)

class Empleado(n:String,
                id:String,
                age:Int,
                var sueldo: Float): Persona(n, id, age) {
    fun printInfo() {
        println("****************************************************")
        println("**************** DATOS DEL EMPLEADO ****************")
        println("****************************************************")
        println("Nombre: $nombre")
        println("DNI: $dni")
        println("Edad: $edad")
    }                
}
```

> [!warning] ¡Recuerda! 
> Esto **son parámetros, no propiedades**. `Empleado` tiene las propiedades `nombre`, `dni` y `edad` heredadas de `Persona`.

Y, como vemos en el código anterior, **podemos acceder a las propiedades de la superclase desde las subclases**. Recuerda que las propiedades en Kotlin son, por defecto, **públicas y finales**.

Al igual que en Java, al instanciar una subclase se instancia primero la superclase. **Si la subclase tiene constructor primario**, debe llamar al constructor del padre directamente en la declaración de la herencia, tal y como en los ejemplos anteriores.

**Pero si la subclase no tiene constructor primario y  usa constructores secundarios**, se utiliza la palabra clave `super` dentro de cada constructor secundario:

```kotlin
open class Vehiculo(val marca: String)

class Moto : Vehiculo {
    // Constructor secundario
    constructor(marca: String, cilindrada: Int) : super(marca) {
        // Código de inicialización de la moto
    }
}
```

## Sobreescribir miembros - `override`

### Sobreescribir métodos

Por defecto, los miembros de una clase (funciones y propiedades) también están cerradas a modificaciones, aunque la clase sea `open`.

Para que las subclases puedan modificar el comportamiento de esos miembros, tenemos que marcar la función/propiedad como **`open`** en la superclase e indicar en la subclase que ese miembro va a sobreescribir al de la superclase anteponiendo la palabra clave **`override`**:

```kotlin
open class Animal {
    // open para permitir que este método se modifique
    open fun hacerSonido() {
        println("El animal hace un sonido")
    }
}

class Perro : Animal() {
    // Sobrescribimos el comportamiento original
    override fun hacerSonido() {
        println("Guau guau")
    }
}
```

### Sobreescribir métodos

Las propiedades de una superclase se pueden sobreescribir en la subclase para modificar su comportamiento de forma similar usando `override`. Al igual que con los métodos, la propiedad en la superclase debe estar marcada como **`open`**. Entonces podemos volver a declarar dicha propiedad en la subclase añadiendo **`override`**:

```kotlin
open class Vehiculo {
    // Propiedad que puede ser modificada en las subclases
    open val numeroRuedas: Int = 4 
}

class Moto : Vehiculo() {
    // Esta subclase modifica el valor por defecto de la propiedad
    override val numeroRuedas: Int = 2 
}

```

Pero Kotlin, que siempre lo pone fácil,  permite ahorrar código haciendo el `override` directamente en los parámetros del constructor primario:

```kotlin
open class Animal {
    open val tipoDieta: String = "Desconocida"
}

// Sobrescribimos la propiedad 'tipoDieta' en el constructor del hijo
class Leon(override val tipoDieta: String) : Animal()

// Al instanciarlo:
val simba = Leon("Carnívoro") 
```

 Aquí **sí debemos poner `val` o `var`**, porque le estamos diciendo al compilador: _"Oye, bonico. Modifica la propiedad que heredaste de la superclase con este nuevo valor que te voy a pasar"_.

Y aquí hemos de tener en cuenta las siguientes **reglas de compatibilidad**:

- Una propiedad `val` de la superclase se puede sobrescribir como `var` en las subclases, ya que podemos las subclases pueden añadir este nuevo comportamiento que permite modificar dicha propiedad.
- Hacerlo **al revés no está permitido**. Una propiedad `var` de al superclase no puede pasar a ser constante (`val`) en la subclase, ya que rompería el contrato de la superclase. En otras palabras, la superclase espera que se pueda cambiar, pero la subclase lo prohibiría.

---

Con


## Acceso a la superclase - `super`

El hecho de modificar en la subclase un método de la superclase no significa que no podamos usar el de esta última. Podemos hacerlo indicando que se trata del método de la superclase con la palabra clave **`super`**.

```kotlin
class Gato : Animal() {
    override fun hacerSonido() {
        super.hacerSonido()  // Usa la funcionalidad de la superclase
        println("Miau")      // Añade comportamiento particular de esta subclase
    }
}
```

## Clases abstractas

Ya vimos en Java que las **clases abstractas** sirven, en esencia, para no duplicar código, permitiendo que otras clases hereden de ella las propiedades y métodos.

Pues en Kotlin el concepto es el mismo. También se declaran anteponiendo la palabra clave **`abstract`**. Como en Java, estas clases pueden tener **métodos normales** (con su bloque de código) y **métodos abstractos** (pendientes de implementación).

> [!note] Recuerda 
> Los métodos abstractos solo pueden encapsularse en clases abstractas. En el momento que en una clase normal definamos un método como abstracto, el compilador se quejará y nos dirá que para mantenerlo así la clase también debe ser abstracta.

Como hemos dicho antes, las clases abstractas suelen servir de superclases para que otras hereden de ellas. De hecho es la razón de ser de estas clases. Por eso, se puede heredar de ellas por defecto sin indicar nada en ellas. Esto suena raro, pero [[2DAM_PMDM/Unidad 02/2. Herencia#Permitir herencia y sobreescritura - `open`\|en el siguiente apartado]] verás que la herencia en Kotlin necesita  alguna indicación. Por lo pronto, y aunque ahora mismo suene raro, las clases abstractas son  **`open` por defecto:**. No necesitamos escribir `open` ni en la clase abstracta ni en sus miembros abstractos, ya que se asume que están listos para ser heredados y sobrescritos.

### Miembros abstractos

Las propiedades y métodos abstractos son aquellos que **no tienen implementación** (no llevan llaves `{}`) porque están hechos para obligar a las subclases a implementar su lógica. Si la superclase es `Empleado` y tiene un método `calcularIncentivos`, lo mejor es que las subclases `Gerente`, `TechLead`, `Developer` o `Conserje` implementen cada una ese método, que son las que saben cómo hacerlo.

```kotlin
abstract class Personaje(val nombre: String) {

    // Cada subclase debe definir cómo atacar
    abstract fun atacar()

    // Método normal: todas las subclases tienen este mismo comportamiento
    fun recibirDanio(puntos: Int) {
        println("$nombre ha recibido $puntos puntos de daño.")
    }
}

```

### Heredar de clases abstractas

Recordemos que cuando una clase hereda de una clase abstracta, está **obligada** a rellenar el código de todos los métodos y propiedades que se marcaron como `abstract`. Esto lo hace sobreescribiéndolos (`override`):

```kotlin
class Guerrero(nombre: String) : Personaje(nombre) {
    // Debe implementar el método abstracto de al superclase
    override fun atacar() {
        println("$nombre ataca con una espada de acero!")
    }
}

class Mago(nombre: String) : Personaje(nombre) {
    // Debe implementar el método abstracto de al superclase
    override fun atacar() {
        println("$nombre lanza un hechizo de fuego!")
    }
}

fun main() {
    // La siguiente línea provocaría un error
    // val heroe = Personaje("Invalido")
    
    val arturo = Guerrero("Arturo")      //  Correcto
    val merlin = Mago("Merlín")          //  Correcto

    arturo.atacar()        // Imprime: Arturo ataca con una espada de acero!
    merlin.atacar()        // Imprime: Merlín lanza un hechizo de fuego!
    
    arturo.recibirDanio(10) // Imprime: Arturo ha recibido 10 puntos de daño.
}
```

## Clases selladas - `sealed class`

Una `sealed class` representa una jerarquía de herencia restringida. Al marcar una clase como sellada (`sealed`), estamos controlando **qué otras clases pueden heredar de ella**. Todas sus subclases deben estar definidas **en el mismo paquete** y, normalmente, en el mismo archivo.

En una **`sealed class`**, sus subclases pueden ser **tanto objetos únicos ([[2DAM_PMDM/Unidad 01/5. object\|object]]) como clases normales (`class` o `data class`)**, lo que permite que cada estado contenga **datos completamente diferentes**.

Las `sealed classes` se usan habitualmente para modelar el estado de una pantalla que carga datos de internet:

```kotlin
sealed class ResourceState {
    // 1. Un objeto único (no lleva datos, solo indica un estado)
    object Loading : ResourceState()

    // 2. Una data class (lleva una lista de datos si la petición funciona)
    data class Success(val datos: List<String>) : ResourceState()

    // 3. Una clase normal (lleva un mensaje de error y un código HTTP si falla)
    data class Error(val mensaje: String, val codigoHttp: Int) : ResourceState()
}
```

> [!note] Nota 
> Es importante fijarse en que **todas las subclases heredan explícitamente de la clase principal** usando `: ResourceState()`.

## Control de errores con `when`

Al igual que con los enums, el compilador de Kotlin sabe exactamente cuántas subclases tiene una `sealed class`. Al usar `when` como expresión para evaluar una clase sellada, **el compilador obliga a gestionar todos los casos posibles**.

Esto elimina la necesidad de usar un bloque `else` y asegura que, si en el futuro añadimos un nuevo estado (ej. `NoInternet`), el código no compilará hasta que se contemple en el `when`.

```kotlin
fun renderizarPantalla(estado: ResourceState) {
    val mensajeParaUsuario = when (estado) {
        is ResourceState.Loading -> "Cargando datos del servidor... Por favor, espere."
        is ResourceState.Success -> "¡Éxito! Se han cargado ${estado.datos.size} elementos."
        is ResourceState.Error   -> "Error ${estado.codigoHttp}: ${estado.mensaje}"
        // 💡 No necesitas "else". Kotlin sabe que están todos cubiertos.
    }
    println(mensajeParaUsuario)
}
```

> [!note] Nota 
> Usamos la palabra clave **`is`** porque estamos comprobando el **tipo** de la clase (si es de tipo `Success`, `Error`, etc.), a diferencia de los enums donde comprobábamos el valor directamente.

## `sealed class` vs `sealed interface`

En las versiones más actuales de Kotlin, también existen las **`sealed interface`**. Funcionan exactamente igual que las clases selladas, pero con las ventajas de las interfaces:

- No pueden mantener un estado compartido (no tienen constructor con variables).
- Permiten la **herencia múltiple**: una misma clase puede implementar varias `sealed interfaces`.

```kotlin
sealed interface EstadoConectividad {
    object Online : EstadoConectividad
    object Offline : EstadoConectividad
}
```

## Aplicación real en Android (Arquitectura MVVM)

En **Jetpack Compose** o **XML con LiveData/StateFlow**, se pueden ver las clases selladas en todas partes en los _ViewModels_ para gestionar la UI de forma limpia:

```kotlin
// El ViewModel expone este estado a la Vista (Activity/Fragment)
private val _uiState = MutableStateFlow<ResourceState>(ResourceState.Loading)
val uiState = _uiState.asStateFlow()

// En la Vista (Compose), reaccionas al estado de forma reactiva:
when (state) {
    is ResourceState.Loading -> MostrarProgressBar()
    is ResourceState.Success -> MostrarListaCompleta(state.datos)
    is ResourceState.Error   -> MostrarAlertDialog(state.mensaje)
}
```


# 3. Interfaces

La **interface** es un **contrato** que define un conjunto de comportamientos (métodos y propiedades) que una clase **debe implementar**. A diferencia de las clases abstractas, **las interfaces no almacenan estado** (no guardan variables en memoria).

Como podemos ver, conceptualmente es lo mismo que en Java. Permite la **implementación de múltiples interfaces**, al contrario que con la herencia, que en Kotlin también es simple. Pero una clase puede implementar **tantas interfaces como necesite**.

Como en las clases abstractas, son **`open` por defecto** ya que la implementación de interfaces es, a fin de cuentas, una herencia (muy particular). Todos los miembros de una interfaz son abiertos a modificaciones por defecto.

Las interfaces **no tienen constructores**, como ocurría en Java, pero si que **pueden tener lógica por defecto**. En Kotlin, los métodos de una interfaz pueden tener un cuerpo de código predeterminado.

> [!warning] Importante 
> Si la función de una `interface` tiene código, **la clase hija no está obligada a sobrescribirla**.

Se declaran utilizando la palabra clave **`interface`**:

```kotlin
interface Volador {
    val velocidadMaxima: Int // Propiedad abstracta (sin valor inicial)ç
    
    fun despegar() // Método abstracto (sin código)
    
    fun planear() { // Método con comportamiento por defecto
        println("Planeando en el aire...")
    }
}
```

## Implementación de Interfaces

ES similar a la implementación de la herencia (dos puntos `:`). Si una clase implementa varias interfaces, estas se separan por **comas (`,`)**. La diferencia a simple vista con respecto a la herencia es que la interfaces, al no tener constructor, se escriben **sin paréntesis**.

```kotlin
interface Nadador {
    fun nadar()
}

// Pato hereda de una Clase Abstracta (Ave) e implementa dos Interfaces
class Pato(nombre: String) : Ave(nombre), Volador, Nadador {
    
    // Obligatorio definir la propiedad de la interfaz
    override val velocidadMaxima: Int = 50

    // Obligatorio implementar los métodos abstractos
    override fun despegar() {
        println("El pato corre sobre el agua y despega.")
    }

    override fun nadar() {
        println("El pato está nadando en el estanque.")
    }
    
    // 'planear()' no es obligatorio sobrescribirlo porque ya tiene lógica por defecto
}
```

## Polimorfismo - Conflictos de nombres

¿Y si dos interfaces distintas tienen un método con el mismo nombre y cuerpo? En tal caso, Kotlin obliga a sobrescribirlo y resolver la ambigüedad usando `super<NombreInterfaz>`.

```kotlin
interface InterfazA {
    fun saludar() { println("Hola desde A") }
}

interface InterfazB {
    fun saludar() { println("Hola desde B") }
}

class MiClase : InterfazA, InterfazB {
    override fun saludar() {
        super<InterfazA>.saludar() // Llama al método de InterfazA
        super<InterfazB>.saludar() // Llama al método de InterfazB
    }
}
```

Es más, ya sabemos que una clase **puede heredar de otra superclase al mismo tiempo que implementa una o varias interfaces**. Un buen ejemplo es el de la propia [web de documentación de Kotlin](https://kotlinlang.org/docs/inheritance.html#overriding-rules):

```kotlin
open class Rectangle {
    open fun draw() { /* ... */ }
}

interface Polygon {
    fun draw() { /* ... */ } // interface members are 'open' by default
}

class Square() : Rectangle(), Polygon {
    // The compiler requires draw() to be overridden:
    override fun draw() {
        super<Rectangle>.draw() // call to Rectangle.draw()
        super<Polygon>.draw() // call to Polygon.draw()
    }
}
```

# 4. Data classes

Muchas de las clases que necesitamos para nuestros programas tienen el único propósito de **almacenar datos y/o estados** (el clásico [POJO](https://es.wikipedia.org/wiki/Plain_Old_Java_Object) de Java).

En Java, para una clase simple como `Usuario` con tres atributos, necesitas escribir docenas de líneas de código _boilerplate_ (getters, setters, `toString()`, `equals()`, `hashCode()`). En **Kotlin**, una **`data class`** automatiza todo esto y genera estos métodos de forma transparente durante la compilación:

```kotlin
// ¡Et voilá! Una sola línea hace todo el trabajo:
data class Personaje(val id: Int, var nombre: String, val rol: String)
```

> [!warning] Importante 
> Es importante dejar claro que una `data class` es una clase `final` y no puede heredarse de ella.

## Implementación

Para que Kotlin pueda generar toda la magia por debajo, una `data class` debe cumplir algunos requisitos:

- Debe llevar la palabra reservada **`data`** antes de `class`.
- El **constructor principal** debe tener al menos un parámetro.
- Todos los parámetros del constructor principal **deben ser declarados explícitamente como `val` o `var`**.
- No pueden ser clases abstractas, `open`, `sealed` ni `inner`.

### ¿Qué métodos genera Kotlin automáticamente?

Al compilar una `data class`, Kotlin añade por su cuenta los siguientes métodos esenciales:

#### `toString()`

Tanto en Java como en Kotlin, al imprimir un objeto obtenemos una dirección de memoria incomprensible (como `Usuario@65cc4438`). En una `data class`, te devuelve una cadena limpia con los nombres y valores de las propiedades.

```kotlin
val heroe = Personaje(1, "Aragorn", "Guerrero")
println(heroe) 
// Resultado: Personaje(id=1, nombre=Aragorn, rol=Guerrero)
```

#### `equals()` y `hashCode()`

Compara el **contenido** (los datos) de los objetos y no sus referencias de memoria. Así, dos instancias diferentes con los mismos datos serán consideradas iguales.

```kotlin
val heroe1 = Personaje(1, "Legolas", "Arquero")
val heroe2 = Personaje(1, "Legolas", "Arquero")

println(heroe1 == heroe2) // true (En una clase normal sería false)
```

#### `copy()`

En desarrollo móvil y arquitecturas como MVVM (que veremos más adelante), **la inmutabilidad es una buena práctica**. Modificar objetos directamente puede provocar bugs de concurrencia. El método `copy()` permite clonar un objeto entero pero modificando únicamente los atributos que necesites.

```kotlin
val clon = heroe1.copy(nombre = "Thranduil")
// clon tendrá id=1, nombre="Thranduil" y rol="Arquero"
```

> [!warning] Muy importante 
> Podemos excluir propiedades de este tipos de clases, haciendo uso del compilador, que usará sólo aquellos **atributos que se encuentren en el constructor principal** para crear todos estos métodos (`copy`, `equals`, `hashCode`, `toString`, etc.).

<iframe src="https://pl.kotl.in/fboZK7wiH" width="560" height="320"></iframe>

Como puede verse en el código anterior, el color de pelo no afectará a la igualdad entre los dos objetos, porque no se tiene en cuenta.

#### Desestructuradores con `componentN()`

Kotlin genera métodos `component1()`, `component2()`... mapeados según el orden de tus propiedades en el constructor.

```kotlin
data class Persona(val nombre:String, var edad:Int)

fun main(){
    val persona1 = Persona("Anselmo", 30)
        
    //componentN()
    println(persona1.component1())  // Imprime la propiedad 1 = "Anselmo"
    println(persona1.component2())  // Imprime la propiedad 2 = 30
}
```

Esto permite la **declaración desestructurante**, o lo que es lo mismo, que de una tacada y a modo de tupla podamos declarar varias variables de un tirón con la asignación de un objeto:

```kotlin
// Desestructuramos el personaje en 3 variables locales automáticas
val (id, nombre, clase) = heroe1

println("$nombre es un $clase") // Imprime: Legolas es un Arquero
```

Realmente se hace esto:

```kotlin
// El equivalente a la asignación anterior...
val id = heroe1.component1()
val nombre = heroe1.component2()
val clase = heroe1.component3()

println("$nombre es un $clase") // Imprime: Legolas es un Arquero
```

Vamos a cuajar todo esto en el siguiente ejemplo:

<iframe src="https://pl.kotl.in/BAUoJ0l4G" width="560" height="550"></iframe>

## Buenas prácticas

### Usarlas como elementos inmutables

Las `data classes` tienen el objetivo básico de representar una entidad o conjunto de datos extraídos de una fuente de datos cualquiera (un JSON, un registro de base de datos, etc.). La intención no es ir más allá y dotarla de funcionalidades fuera de la responsabilidad de los datos que representa. Por eso, debemos intentar definir los atributos del constructor como `val` siempre que sea posible. Si necesitamos cambiar algo, usamos `.copy()`. Esto evita dolores de cabeza con hilos y estados de la UI. Ya lo verás más adelante, tanto aquí como en el módulo de PSP.

### Implementaciones puntuales

Aunque en la mayoría de las veces las `data class` se definen en una sola línea, podemos añadir funciones secundarias o propiedades que no son necesarias en el constructor. Esto se hace como en cualquier otra clase, entre llaves `{}`.

Pero ¡cuidado! Los métodos que se añaden automáticamente (`equals`, `copy`, etc.) **solo tienen en cuenta lo que hay dentro del constructor principal**.

# 5. Enumerados

Un `enum` es una **clase especial**, un tipo de datos que representa un **conjunto de valores constantes e inmutables** y que, como ya recomendamos en Java, deberían tener relación entre si. Se utiliza cuando conocemos de antemano todos los valores posibles que puede tomar una variable.

En Kotlin, se definen usando dos palabras reservadas juntas: **`enum class`**. Se pueden usar para casos como los siguientes:

- Estados de una petición de red: `LOADING`, `SUCCESS`, `ERROR`.
- Roles de un usuario: `ADMIN`, `PREMIUM`, `GUEST`.
- Tipos de pago: `TARJETA`, `PAYPAL`, `BIZUM`.


```kotlin
enum class EstadoPeticionRed {LOADING, SUCCESS, ERROR}

enum class RolUsuario {ADMIN, PREMIUM, GUEST}

enum class TipoPago {TARJETA, PAYPAL, BIZUM}

enum class EstadoPedido {
    PENDIENTE,
    ENVIADO,
    ENTREGADO,
    CANCELADO
}
```


## Enums con propiedades y métodos

Al igual que en Java, en Kotlin cada constante es una **instancia de la clase** enum. Esto significa que puedes pasarle parámetros a su constructor y asociarles datos o comportamientos.

```kotlin
enum class TipoUsuario(val prioridad: Int, val accesoTotal: Boolean) {
    ADMIN(1, true),
    EDITOR(2, false),
    GUEST(3, false); // ; necesario si después se añaden métodos

    // Podemos añadir funciones dentro del enum
    fun mostrarInfo() = "Rol: $name (Prioridad: $prioridad)"
}
```

## `enum` y `when`

El uso más potente de los enums en Kotlin es combinarlo con la estructura **`when`** (el sustituto mejorado del `switch` de Java).

Al usar `when` como una expresión (para asignar un valor) con un `enum`, **Kotlin obliga a controlar todos los casos posibles**. Si dejamos uno, el compilador dará error, ya que `when` debe dejar forzosamente un valor en la asignación. Esto evita que olvidemos gestionar estados nuevos.

```kotlin
val estadoActual = EstadoPedido.ENVIADO

// El compilador verifica que PENDIENTE, ENVIADO, ENTREGADO y CANCELADO estén cubiertos
val mensajeAlerta = when (estadoActual) {
    EstadoPedido.PENDIENTE -> "El almacén está preparando tu paquete."
    EstadoPedido.ENVIADO   -> "El repartidor está en camino."
    EstadoPedido.ENTREGADO -> "Paquete recibido correctamente."
    EstadoPedido.CANCELADO -> "El pedido ha sido anulado."
    // 💡 ¡No hace falta el "else"! Kotlin ya sabe que no hay más constantes.
}
```

## Propiedades y métodos nativos de los enums

Cada constante de un enum incluye por defecto dos propiedades muy útiles:

- **`name`**, que contiene el nombre de la constante en formato `String`.
- **`ordinal`**, que devuelve la posición de la constante (empezando desde `0`) en el enum.

```kotlin
val miEstado = EstadoPedido.ENTREGADO

println(miEstado.name)    // Imprime: "ENTREGADO"
println(miEstado.ordinal) // Imprime: 2 (PENDIENTE=0, ENVIADO=1, ENTREGADO=2)
```

## Buscar y listar constantes

Con **`entries`** obtenemos una lista con todas las constantes del enum (es la alternativa del viejo `.values()` de Java).

También tenemos el método **`valueOf(String)`**, que convierte un texto en la constante del enum que coincida, lanzando un error si no existe.

```kotlin
// 1. Recorrer todos los valores posibles
for (estado in EstadoPedido.entries) {
    println("Disponible: ${estado.name}")
}

// 2. Convertir un String que viene de una Base de Datos o API a Enum
val estadoDesdeBackend = "CANCELADO"
val estadoEnum = EstadoPedido.valueOf(estadoDesdeBackend) // Devuelve EstadoPedido.CANCELADO
```

## Seriealizar un JSON en un `enum`

Esto ya lo veremos más adelante, cuando ataquemos una API y obtengamos el JSON correspondiente para mostrar datos en nuestras aplicaciones Android. Cuando trabajamos con **Kotlinx Serialization**, podemos serializar y deserializar enums directamente de forma nativa.

Si el JSON devuelve `"ADMIN"`, la librería lo mapeará automáticamente a `TipoUsuario.ADMIN`. ¿Y si el JSON usa minúsculas o códigos extraños? Usamos la anotación `@SerialName`:

```kotlin
import kotlinx.serialization.Serializable
import kotlinx.serialization.SerialName

@Serializable
enum class EstadoSuscripcion {
    @SerialName("active") ACTIVA,
    @SerialName("expired") EXPIRADA,
    @SerialName("pending_payment") PAGO_PENDIENTE
}
```

## ¿Cuándo usamos `enum class` y cuándo `sealed class`?

Las **`enum class`** son las idóneas si las constantes que manejamos son **fijas y no necesitan almacenar datos dinámicos diferentes entre sí** (por ejemplo, todos los usuarios tienen un entero `prioridad`, solo cambia el valor).

Por otra parte, las **`sealed class` (clases selladas)** son recomendables si cada estado necesita **datos completamente distintos**. Por ejemplo: el estado `SUCCESS` necesita una lista de datos de la API, pero el estado `ERROR` necesita un `String` con el mensaje de error y un `Int` con el código HTTP).


# Referencias

* *Inheritance* | Kotlin. (s. f.). Kotlin Help. https://kotlinlang.org/docs/inheritance.html
* *Interfaces* | Kotlin. (s. f.). Kotlin Help. https://kotlinlang.org/docs/interfaces.html
* *Data classes* | Kotlin. (s. f.). Kotlin Help. https://kotlinlang.org/docs/data-classes.html
* *Enum classes* | Kotlin. (s. f.). Kotlin Help. https://kotlinlang.org/docs/enum-classes.html

