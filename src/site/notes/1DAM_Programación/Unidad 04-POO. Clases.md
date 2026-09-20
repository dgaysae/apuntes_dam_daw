---
{"dg-publish":true,"permalink":"/1-dam-programacion/unidad-04-poo-clases/","dg-note-properties":{"unidad":"[[1DAM_Programación/Unidades/Unidad 4 - POO. Clases]]","modulo":"[[Módulos/Programación]]","libro":"[[Apuntes/Programación (1º DAM, 1º DAW)]]"}}
---


```table-of-contents
```

---

[[1DAM_Programación/Unidades/Unidad 4 - POO. Clases#Datos de la unidad\|Unidad 4 - POO. Clases#Datos de la unidad]]

---

# 1. Paquetes

## 1.1 Los paquetes de Java

Los paquetes, como vimos en la [[1DAM_Programación/Unidad 03/6. Paquetes\|unidad 3]], son **agrupaciones de clases**. 

El JDK de Java proporciona todos los paquetes estándar para hacer gran diversidad de tareas (entrada/salida, manejo de ficheros o bases de datos, creación de interfaces gráficos, etc) y, además, podemos usar paquetes de terceras partes o desarrollar los nuestros propios.

Lo lógico es que **las clases de un paquete estén relacionadas de alguna manera**. Por ejemplo, en el paquete estándar `java.io` están todas las clases relativas a la entrada/salida de datos.

Recordemos ahora algunas cosas importantes que ya dijimos sobre los paquetes:

* Un paquete es un **conjunto de clases relacionadas** entre sí.

* Un paquete puede contener **subpaquetes**.

* La estructura de paquetes del JDK es **jerárquica**.

* Para usar una clase de un paquete, tenemos dos modos:
  * Utilizar la ruta entera, como `java.io.File`, cada vez que nos tengamos que referir a la clase `File`.
  
  * Importar el paquete con `import java.io.File`. A partir de entonces,  podemos referirnos a la clase `File` directamente, sin anteponer toda la ruta.
  
* Cuando nos referimos a una clase de un paquete (salvo que se haya importado el paquete) hay que especificar el paquete (y subpaquete si es necesario) al que pertenece. Por ejemplo: `java.io` es un **paquete**, y `java.io.File` se refiere concretamente a la **clase `File` de ese paquete**. 

* Los paquetes **permiten reducir los conflictos con los nombres** puesto que dos clases que se llaman igual, si pertenecen a paquetes distintos, no deberían de dar problemas. 

* Los paquetes **permiten proteger ciertas clases no públicas** al acceso desde fuera del mismo. Esto lo veremos en detalle más adelante, al hablar de visibilidad. 

## 1.2 Cómo crear un paquete

Vamos a ver cómo se crea un paquete mediante un ejemplo muy simple. La idea es reunir en un paquete dos clases y llamarlas desde otro programa para comprobar que todo funciona. 

### Paso 1. Crear un subdirectorio dentro del directorio de trabajo
Lo llamaremos, por ejemplo, `geometria`. Dentro de este subdirectorio crearemos otros, destinados a los subpaquetes de nuestro paquete. Vamos a crear ahora uno llamado `triangulo`. 

Por lo tanto, dentro de tu directorio de trabajo, tienes que crear un subdirectorio Utilidades, y, dentro de éste,  otro llamado prueba.

> [!warning] Importante 
> Es necesario **conservar esta estructura de directorios** para que los paquetes funcionen correctamente.

### Paso 2. Escribir el código de las clases 

En el directorio `geometria/triangulo`, vamos a crear las clases `Equilatero` y `Isosceles`. 

```java
# Equilatero.java
package geometria.triangulo;

import java.io.*;

public class Equilatero {
    public void saludar() {
        System.out.println("Hola, soy un triángulo equilátero");
    }
}
```

```java
# Isosceles.java
package geometria.triangulo;

import java.io.*;

public class Isosceles {
    public void saludar() {
        System.out.println("Hola, soy un triángulo isósceles");
    }
}
```

Observa que la primera línea de ambos archivos señala que estas clases **pertenecen al paquete `geometria.triangulo`**. 
Para hacer uso de estas clases desde una tercera clase que no esté en ese paquete, bastará con escribir algo como esto:

```java
# Test.java
import geometria.triangulo.Equilatero;
import geometria.triangulo.Isosceles;

public class Test {
    public static void main(String[] args) {
        Equilatero e = new Equilatero();
        Isosceles i = new Isosceles();
        e.saludar();
        i.saludar();
    }
}
```

Como podemos apreciar en las dos primeras líneas del código anterior, estamos importando las clases `Equilatero` e `Isosceles` del paquete `geometria.triangulo`. Al hacerlo, podemos usar ambas clases en esta clase `Test`.

También podríamos importar de esta otra manera:

```java
import geometria.triangulo.*;

public class Test {
    public static void main(String[] args) {
        Equilatero e = new Equilatero();
        Isosceles i = new Isosceles();
        e.saludar();
        i.saludar();
    }
}
```

Fíjate en cómo se importa el paquete (el **asterisco** al final indica **“importar TODAS las clases** del paquete `geometria.triangulo`) y cómo, a partir de entonces, puede usarse **cualquier clase del paquete** (como `Equilatero`, `Isosceles` y **cualquier otra** que se encuentre en dicho paquete). 

El código de esta clase `Test` debe estar situado en el directorio de trabajo, no en los subdirectorios del paquete.

### Paso 3. Compilar y probar el paquete 

Una vez creado el código fuente necesario, lo compilaremos, como siempre, con `javac` o con nuestro IDE preferido. Obviamente, la forma de proceder será distinta en cada caso.

> [!note] Te recomendamos... 
> Como siempre, **te recomendamos que hagas la compilación directamente con `javac` desde la línea de comandos las primeras veces**: es la forma **más lenta**, pero también la que te proporciona **mayor control** sobre lo que ocurre y la que te permite comprender bien la forma en la que trabaja el compilador de java.

Para compilar las clases de un paquete desde la consola de texto, debes situarte en el directorio de trabajo (NO en el directorio del paquete, sino más arriba, en el directorio padre). Una vez allí, puedes compilar las clases con:

```bash
~$ javac geometria/triangulo/Equilatero.java
~$ javac geometria/triangulo/Isosceles.java
```

> [!warning] Importante
> No olvides cambiar la barra `/` por `\` en sistemas Windows.

Después de depurar los posibles errores de escritura, ejecutaremos `Test.class` desde la línea de comandos, y el resultado debería ser `"Hola, soy un triángulo equilátero"` seguido de `"Hola, soy un triángulo isósceles"`. 

Si algo falla, asegúrate de tener bien definida la variable `CLASSPATH`, que debe apuntar al directorio donde se encuentra el paquete o, como alternativa, utiliza la opción `-cp` de la línea de comandos al ejecutar el programa con el comando java. Todo esto se explicó en la unidad 2, de modo que es un buen momento para revisarlo si no sabes de qué estamos hablando.

Si vas a compilar el paquete con un IDE, la forma de hacerlo dependerá, lógicamente, del IDE que utilices. Por ejemplo, en **Netbeans**[^1] puedes iniciar un nuevo proyecto. Puede ser “Java Library” si quieres crear solo los paquetes (sin aplicación ejecutable), o una aplicación Java convencional. Luego, al añadir archivos fuente, eliges la opción “Java package”. **Netbeans** se encargará de crear los directorios correspondientes en el lugar correcto, y de indicar el `package` adecuado en el código fuente de cualquier clase que crees dentro del paquete. También se encargará de compilarlo y ejecutarlo todo como es debido.

Aunque estos detalles pueden cambiar, el procedimiento básico será el mismo con cualquier otro IDE. 

[^1]: NetBeans, A. (s. f.). **_Welcome to Apache NetBeans_**. https://netbeans.apache.org/



# 2. Las clases en OOP - divide y vencerás


Las clases son las estructuras que permiten a los programadores hacer razonablemente efectiva la aspiración más deseada de los primeros programadores de los años 50: divide y vencerás.

**_[Divide and Conquer](https://en.wikipedia.org/wiki/Divide_and_conquer)_**, o **DAC**, consiste en dividir un problema complejo en subproblemas, y tratar cada subproblema del mismo modo, es decir, dividiéndolo a su vez en subproblemas. Así sucesivamente hasta que obtengamos problemas lo suficientemente sencillos como para escribir programas que los resuelvan. Si lo piensas un poco, es exactamente así como actuamos en el mundo real cuando un problema supera nuestra capacidad de resolución de una sola vez.

![ud04_dac.png\|Clase vs Objeto](/img/user/adjuntos/1DAM_Programacion/Unidad_04/ud04_dac.png)
> Divide y vencerás (*Divide and Conquer*) - Se divide un problema complejo en varios subproblemas más sencillos, se aúnan las soluciones y con ellas se devuelve la solución final - Figura generada con Gemini

Sí, ya lo sé: sigues sin entender ni papa 😒. Sigue leyendo un poco más y verás como se hace la luz.

## 2.1. Fregonas eléctricas

Imagina a un empresario autónomo que un día tiene la feliz idea de fabricar y vender, digamos, fregonas eléctricas. En realidad son fregonas normales a las que acopla un pequeño motor eléctrico en el garaje de su casa donde ha montado un taller artesanal.

El invento tiene éxito. Después de varios meses anunciándose por las redes sociales y otros barrios de internet, consigue vender unas cuantas unidades y ganar algo de dinero. Decide diversificar su negocio y empieza a fabricar escobas eléctricas, recogedores eléctricos, llaves eléctricas que abren solas las cerraduras y toda clase de artilugios absurdos electrificados.

Pronto el tipo no da a basto con los pedidos y tiene que contratar a varios ayudantes. El taller montado en su garaje se queda pequeño y se trasladan a una nave en un polígono industrial de los que adornan las afueras de nuestras ciudades. La empresa crece, pasa de tres a trescientos trabajadores, hay un departamento de personal, otro de compras, otro de márketing y otro de I+D. El tipo que inventó todo esto ahora viste traje y corbata y trabaja en un despacho en la última planta de un edificio de oficinas elegante en el centro de la ciudad, aunque de vez en cuando le gusta seguir pasando por el taller a ver cómo lo hacen los chicos.

Llegados a este punto, es imposible que nuestro inventor tenga una idea completa de lo que pasa en su empresa. Son trescientos empleados, varios departamentos, tal vez varios talleres repartidos por el mundo (probablemente entre China y Bangladesh). El departamento comercial no sabe exactamente lo que ocurre dentro del departamento de I+D, ni el de I+D lo que ocurre en el de personal, aunque tengan reuniones periódicas.

Saben lo que cada departamento hace, pero no cómo lo hace.

***Ni necesitan saberlo***. Aquí está el meollo del asunto.

Cuando algo se vuelve muy complejo, como esta empresa ficticia que fabricaba fregonas eléctricas, el cerebro humano se ve desbordado. La única forma de abordar estos problemas es dividiéndolos en partes (los departamentos) que se encarguen de resolver una parte del problema (unos calculan las nóminas y buscan a nuevos trabajadores, otros investigan sobre nuevos productos, otros buscan formas de comprar materias primas más baratas y de mejor calidad...). Y cada parte no sabe exactamente cómo lo hacen los demás, ni les importa. Bastantes problemas tienen ellos con lo suyo.

Cada departamento, además, puede ser tan complejo que se tenga que subdividir. Por ejemplo, el departamento de personal puede dividirse en una sección de nóminas, que se encargue de pagar los salarios a los trabajadores y ajustar cuentas con el fisco y la seguridad social, y otra de selección de personal, para buscar a nuevos candidatos a trabajadores. Ambas secciones, aunque trabajan juntas, están solo parcialmente relacionadas, y las personas que trabajan en una pueden tener una idea muy reducida de cómo funciona la otra. La cuestión es que las otras partes funcionan, y con eso basta. Todos cooperan para que la empresa en su conjunto funcione, como los engranajes de un reloj.

Bien, así lo intentan hacer también los programas orientados a objetos. Tome usted un problema muy complicado y no intente resolverlo todo de golpe, por favor. Coja su programa (la empresa fabricante de fregonas) y divídalo en clases (los departamentos), cada una de las cuales haga algunas de las cosas que se necesitan para la solución (fabricar fregonas y otros artilugios eléctricos). Y si esas clases son aún muy complejas, subdivídalas. No tema hacer cuantas subdivisiones necesite.

Las clases colaborarán entre ellas, desde luego. Se enviarán datos, resultados, informes, qué sé yo. Pero ninguna sabrá exactamente cómo funcionan las otras por dentro, ni les hará ninguna falta. Cada una hará su trabajo y producirá sus resultados, y todo ello se fundirá de algún modo para obtener la solución final. Probablemente otra clase (el dueño de la empresa, o el consejo de administración) se encargará de ello.

Existen infinidad de arquitecturas válidas para conseguir el mismo resultado. Pudiera existir un departamento comercial o estar unido al de compras. El departamento de personal podría dividirse en dos departamentos independientes en lugar de tener dos subsecciones. Puede existir un administrador único o un consejo de administración. Todas esas soluciones podrían funcionar, y, en general, no es fácil decidir cuál es la solución óptima, si es que la hay.

Es posible que nuestra empresa necesite varios ejemplares de algún departamento. Por ejemplo, puede usted tener un taller en China, otro en India y otro en Albacete. No importa. Diseñe usted cómo debería ser un taller de fregonas eléctricas y luego cree tantos como necesite. Los planos del taller son las **clases**, y cada taller concreto es un **objeto**.

Las clases, como los talleres, tienen una serie de **atributos** que los describen: su ubicación, su tamaño, el número de trabajadores, y cosas así. Y una serie de cosas que son capaces de hacer como respuesta a las peticiones de otras clases: fabricar mil fregonas más para el mercado asiático, por ejemplo. Estos son los **métodos**.

Así funciona la programación orientada a objetos. Acuérdese de las fregonas eléctricas, por favor, cuando esté diseñando su próximo programa.

## 2.2 Pautas para el diseño de clases

Ya hemos estirado suficientemente nuestro ejemplo de las fregonas eléctricas. Volvamos al mundo real y digamos, más formalmente, que, en la programación orientada a objetos, las clases permiten a los programadores abstraer el problema a resolver, descomponiéndolo en partes más simples que ocultan los datos y la manera en la que estos se manejan para llegar a sus soluciones parciales.  

Las clases suelen proporcionar métodos para acceder a parte de su información interna. Son los llamados **_setters_** y **_getters_**. Por ejemplo, si una clase tiene un atributo llamado `cantidad`, y éste debe poder **consultarse o modificarse desde otras clases**, no es conveniente que ese atributo sea público, sino que la clase debe proporcionar un método `getCantidad()` y otro `setCantidad()` para acceder al mismo.

```java
class Ejemplo {
    private int cantidad;
    
    public int getCantidad() {
        return cantidad;
    }
    
    public void setCantidad(int c) {
        cantidad = c;
    }
}
```

A parte de los `getters` y los `setters`, decidir qué clases son necesarias para resolver un problema, y qué métodos y atributos han de tener, no es tarea fácil. Es una labor que realizan los **analistas** de aplicaciones y requiere, en general, años de experiencia para llegar a dominarse. Para ello se utilizan herramientas como los diagramas de clase o de comportamiento que verás en el módulo de Entornos de Desarrollo, pero no es labor de un programador realizar el diseño de la aplicación, aunque sí debe ser capaz de interpretar el diseño hecho por otros.

Con las aplicaciones pequeñas, como las que vamos a trabajar en los próximos meses, la labor de análisis y diseño se simplifica mucho, pero, aún así, verás que hay veces en las que no resulta trivial decidir qué clases necesita determinado programa. Por ese motivo, vamos a dar ahora una serie de pautas generales para identificar las clases de un sistema, pero solo son eso, pautas. En modo alguno pueden aplicarse irreflexivamente a todos los sistemas, y el número de excepciones es infinito.

- Lee bien la especificación de requisitos. Las **clases** candidatas estarán nombradas en la especificación con **sustantivos**, tales como `Estudiante`, `Profesor` o `Asignatura` (con la primera letra en mayúscula).

- Los **métodos** suelen expresarse con **verbos**. Son las cosas que el sistema "*hace*", y, por lo tanto, se expresan como acciones.  
  Por ejemplo, si la especificación dice que "*el estudiante se matricula de una asignatura*", probablemente la clase `Estudiante` debe tener un método `matricular()`. ¿O encajará mejor en la clase `Asignatura`? Estas son las preguntas que se hace continuamente el analista.

- Los **atributos** o **propiedades** serán también, generalmente, **sustantivos**, pero sin entidad propia. Es decir, estarán **siempre asociados a algo** (su clase). El teléfono o la fecha de nacimiento de un estudiante no son clases, sino atributos de la clase `Estudiante`.

> [!info]  
> Este es un buen punto de partida. En **Entornos de Desarrollo** verás algunas cosas más sobre diseño de software con clases, pero no mucho. Para profundizar en esto, necesitarás cursar una carrera universitaria o forjarte una carrera profesional de muchos años y aprender de los que ya saben.  

## 2.3. Niveles de acceso a los miembros de una clase

En Java hay varios niveles de acceso a los miembros de una clase:

- **Público** (`public`). Se puede acceder a ese miembro desde cualquier otra clase de la aplicación.

- **Privado** (`private`). No se puede acceder a ese miembro desde ninguna otra clase.

- **Protegido** (`protected`). No se puede acceder a ese miembro desde ninguna otra clase, excepto las que pertenezcan al mismo paquete y las subclases, que sí podrán.

- **No especificado**. Si no especificas el nivel de acceso, solo podrán acceder al miembro de la clase las clases del mismo paquete, pero no las subclases.

Cada vez que se declara un miembro de clase (atributo o método), hay que indicar su nivel de acceso . Como hemos visto, no especificar el nivel de acceso también es una forma de hacerlo.

El conjunto de miembros de una clase declarados como públicos y protegidos constituyen su **interfaz**, es decir, es la parte de muestran al resto de la aplicación. Cualquier modificación interna de la clase no debería afectar nunca a su interfaz, de manera que el funcionamiento del resto de la aplicación no se vea alterado porque tengamos que alterar una línea de código de una de las clases.

## 2.4. Niveles de acceso a una clase

También se puede controlar el nivel de acceso a una clase, declarándola como pública o como privada. En el primer caso, cualquier otra clase puede usarla, por ejemplo, para instanciar objetos. En el segundo, sólo podrán hacerlo otras clases de su propio paquete. 

### Clase pública

Puede ser usada por **cualquier otra clase**:

```java
public class unaClase {
    ...
}
```

### Clase no pública

Solo puede ser usada por **clases de su propio paquete**:

```java
class unaClase {
    ...
}
```

## 2.5. Los objetos `this` y `super`

La palabra **`this`** es una palabra reservada de Java. Esto quiere decir que no puedes usarla como identificador de variable, constante, método o clase. 

Y es una palabra reservada porque **el objeto `this` hace referencia al propio objeto** que está ejecutando el código. Es decir, si tenemos una clase naveEspacial e instanciamos cinco objetos de esa clase, tendremos en nuestro programa cinco naves espaciales, cada una con sus atributos y sus métodos. Pues bien, referirnos a `this` dentro del código de la clase es referirnos al objeto concreto, a una de las cinco naves espaciales. 

El objeto `this` se puede emplear para acceder a los atributos y a los métodos del propio objeto, pero casi siempre se omite para ahorrar código. En cambio, algunas veces es necesario usarlo para evitar ambigüedades.  

En el siguiente ejemplo verás cómo usamos `this` una vez sin obligación, solo porque somos así de chulos, y otra vez para resolver una de esas ambigüedades.

```java
class NaveEspacial {  
    private int vidas;
    
    public int getVidas() {
        // Podríamos haber escrito return vidas y no pasaría nada
        return this.vidas; 
    }

    public int setVidas(int vidas) {  
        /*
        Aquí usamos this para distinguir el parámetro "vidas"
        del atributo "vidas"  
        */
        this.vidas = vidas;  
    }  
}
```

El **objeto `super`** es parecido a **`this`**, pero no se refiere al objeto actual, sino a la **superclase o clase madre** del objeto. Veremos más sobre superclases, clases madre y herencia [[1DAM_Programación/Unidad 04/8. Herencia\|más adelante]] en esta unidad. 

## 2.6. La clase `Object`

La clase `Object` es la **raíz de la jerarquía de clases** de Java.  

Esto quiere decir que **cualquier otra clase creada en Java siempre es una subclase de `Object` de algún modo**. Y, por lo tanto, heredará los atributos y métodos de `Object`. Hablaremos más sobre herencia al final del tema, pero es un concepto simple: cuando una clase es la hija de otra, hereda los atributos y métodos de su madre, como en la vida misma. Es decir, dispone de ellos también sin necesidad de volver a escribirlos. 

Pues bien, la clase `Object`, la madre de todas las clases de Java, dispone de varios métodos genéricos muy útiles y los pasa como herencia a todas sus subclases. Es decir, a cualquier otra clase. Esos métodos son: 

* **`clone()`**: para clonar o hacer una copia de un objeto.

  El método `clone()` hace lo que se llama una ***copia superficial***, es decir, hace que los dos objetos, el original y el clonado, referencien a la misma zona de memoria. Así, los cambios en el estado del objeto clonado afectarán al original. Si deseamos un clonado completo, con zonas de memoria diferenciadas (se llama un *copia en profundidad*), debemos *sobreescribir* el método `clone()`. La sobreescritura consiste en desechar el método clone() heredado para establecer uno propio mejor adaptado a la clase que estamos definiendo.

  ```java
  nave1 = new NaveEspacial();
  nave2 = (NaveEspacial) nave1.**clone**();
  ```
  
* **`equals()`**: para comparar dos objetos byte a byte y ver si son iguales.

  El método `equals()` hace una comparación superficial, es decir, mira si los dos objetos comparten la misma zona de memoria. Para hacer una comparación en profundidad, mirando el estado del objeto, *es necesario sobreescribir el método `equals()`*. Es, por lo tanto, un caso parecido al de `clone()`

  ```java
  nave1 = new NaveEspacial();
  nave2 = (NaveEspacial) nave1.clone();
  
  if (nave1.equals(nave2))
      System.out.println("nave1 y nave2 son iguales según equals()");

  ```


* **`toString()`**: devuelve el nombre de la clase a la que pertenece el objeto. 

  En el caso del objeto `nave1` del ejemplo anterior, la llamada a `nave1.toString()` nos devolverá algo parecido a `NaveEspacial@263ac5`. Se trata del nombre de la clase y de la dirección de memoria donde el objeto está alojado. 

* **`finalize()`**: para borrar definitivamente el objeto y liberar los recursos que ocupaba (generalmente, memoria). Es invocado automáticamente por el recolector de basura de la JVM y nosotros no tenemos que hacer nada con él. Véase el apartado sobre destructores al final de este tema para más información.



# 3. ¿De clase o de instancia?


## 3.1. Atributos de clase y variables globales

En Java no existen las variables globales, ese invento demoníaco con el que nos tientan algunos lenguajes de programación prometiéndonos resolver los problemas de forma fácil y cómoda y que acaban siendo como el bloque de hormigón que los gángsters de Chicago ataban al pie de sus víctimas antes de darles una zambullida en las aguas heladas del lago Michigan. 

Una **variable global**, por si alguien tiene curiosidad, es una variable disponible en *todo* el código de la aplicación. Como *cualquiera* puede modificar su valor, basta con que la aplicación crezca lo suficiente para que alguien cometa un error y le asigne un valor incorrecto. Es cuestión de tiempo, antes o después pasará, porque los programadores somos humanos y, como tales, falibles. Y, como la variable es global y, por lo tanto, omnipresente, de pronto todo el programa se desmoronará ante nuestras narices. 

Y ahora, programador pringado, ponte a buscar el error. Tienes un millón de líneas de código y esa puñetera variable puede haber sido modificada de forma incorrecta virtualmente por cualquiera de ellas. Multiplica este problema por N, siendo N el número de variables globales de tu programa, y luego deja caer tu cabeza sobre el teclado. 

Este es el motivo por el que las variables globales ***no deberían ser usadas nunca, jamás, bajo ninguna circunstancia***. Aunque a veces parezcan una solución fácil solo lo son a corto plazo y al final te estallarán en la cara. Y todo, repito, *todo* lo que hagas con variables globales también lo puedes hacer sin ellas. Así que no hay más que hablar. Fin de la historia. 

**En Java no existen variables globales**. Java es un lenguaje serio. Lo más parecido que encontrarás son los **atributos de clase** o **atributos `static`**, que de los dos modos pueden llamarse. Estos funcionan de la siguiente manera: lo declaras como `static`, y luego instancias un objeto de esa clase. El atributo `static` se crea, junto con todos los demás, y se quedan guardaditos dentro de la variable. Luego creas otro objeto de la misma clase, y viene lo raro: el atributo declarado como `static` no se crea, sino que se comparte con el objeto que ya existe. El resto de atributos y métodos sí se crean y se asignan al nuevo objeto, pero el `static` no, ése es compartido por todos los objetos de la misma clase. 

> [!warning] ¡Aviso de peligro! 
> Los atributos `static` se parecen tanto, pero tanto, tanto, a las variables globales, que deberías tener una muy buena excusa para utilizarlos. 

Los atributos normales, es decir, los no `static`, se denominan **atributos de instancia**. Ahí va un ejemplo:

```java
public class NaveEspacial {  
  private static int naves = 0; 	// Atributo de clase
  private int vidas = 0; 		// Atributo de instancia
  . . .  
  NaveEspacial() {  
    naves++;  
    vidas++;  
  }

  public getNaves() { return naves; }  
  public getVidas() { return vidas; }  
}
```

El atributo naves es `static`. Se trata de un contador de objetos, es decir, nos va a llevar la cuenta de cuántos objetos naveEspacial hemos creado. Se incrementará en uno cada vez que se cree una nave (ver constructor), y, como es compartido por todas las naves, irá acumulando el número de objetos creados.  

El atributo vidas, en cambio, es normal. Se le llama **atributo de instancia**. Aunque también se incrementa en el constructor, será un atributo recién creado con el objeto y, por lo tanto, siempre valdrá 0\. 

Por lo tanto, si hacemos esto:

```java
naveEspacial nave1 = new NaveEspacial();  
System.out.println("Nave 1: naves = "  
  + nave1.getNaves()  
  + ", vidas = "  
  + nave1.getVidas()  
);

naveEspacial nave2 = new NaveEspacial();  
System.out.println("Nave 2: naves = "  
  + nave2.getNaves()  
  + ", vidas = "  
  + nave2.getVidas()  
);
```

...deberíamos obtener por pantalla esto:

```bash
Nave1: naves = 1, vidas = 1   
Nave2: naves = 2, vidas = 1
```

## 3.2. Métodos de clase

Del mismo modo que existen los atributos de clase y los atributos de instancia, nos encontraremos con los métodos de clase (métodos `static`) y los métodos de instancia. 

Los métodos de instancia son los normales, lo que hemos estado usando hasta ahora. Los **métodos de clase** o **métodos `static`** son compartidos por toda la clase, es decir, existen aunque no se haya instanciado ningún objeto de la clase. 

**Los métodos `static` tienen dos limitaciones** bastante lógicas si piensas que pueden ejecutarse sin haber instanciado ningún objeto:

* No pueden acceder a `this`

* No pueden acceder a los miembros de instancia (es decir, solo pueden acceder a otros miembros `static`) 

No hace falta que te pongamos ejemplos de métodos `static` en clases de ejemplo como naveEspacial o miNumero, porque ya has usado muchos, a lo mejor sin darte cuenta. 

El caso más claro es main(), más conocido como `public static void main()`, ¿o no te sale esa retahíla de forma automática? Tal vez la primera vez que lo escribiste te preguntaste qué demonios significaba. Ahora lo sabes: public, porque puede invocarse desde cualquier sitio (el IDE, la consola del sistema operativo...), void porque no devuelve valor alguno, y `static` porque puede ejecutarse sin instanciar un objeto de la clase que lo contiene. ¿Quién iba a instanciar el objeto, si el programa empieza precisamente por aquí?

Otros ejemplos son los métodos de la clase `Math` (técnicamente hablando, `java.lang.Math`). Habrás escrito a menudo `Math.random()`, y algunas veces menos `Math.round()` o `Math.pow()`. Pero `Math` no es un objeto, sino una clase. Puedes invocar los métodos `random()` o `round()` a través del nombre de la clase porque son métodos estáticos, y eso evita que tengas que crear un objeto de la clase `Math` antes de poder usarlos. 

Como habrás deducido de todos estos ejemplos, para invocar un método estático no usaremos un objeto, sino el propio nombre de la clase seguido del nombre del método (como en `Math.random()`).



# 4. ¿Por valor o por referencia?

El paso de parámetros, o comunicación de datos del algoritmo invocante al método invocado, puede hacerse mediante dos métodos:

* **Paso de parámetros por valor**, que es la forma más sencilla pero no permite al método devolver resultados en los parámetros.

* **Paso de parámetros por referencia**, que es más complejo pero permite a los métodos devolver resultados en los parámetros. 

Veamos cada método detenidamente. 

## 4.1. Paso de parámetros por valor

Los métodos, como sabes, pueden tener una serie de parámetros en su declaración. Estos parámetros se denominan **parámetros formales**.  

Por ejemplo, un método de una clase llamada miNumero que calcula la potencia de un número elevado a otro podría declararse como:

```java
public static double potencia(double base, double exponente) {  
    return Math.pow(base, exponente);   
}
```

En esta declaración de método, base y exponente son los **parámetros formales**. 

Cuando el método es invocado, se le pasan entre paréntesis los valores de los parámetros. A éstos se les denomina **parámetros actuales**; por ejemplo:

```java
double a = 5.8;   
double b = 3.0;   
double c = miNumero.potencia(a, b);
```

En esta invocación del método potencia(), los parámetros actuales son a y b, es decir, 5.8 y 3.0

Al invocar un método, los parámetros actuales son asignados a los parámetros formales en el mismo orden en el que fueron escritos. Dentro del método, los parámetros se utilizan como variables convencionales. Así, en el ejemplo anterior, dentro del método `potencia()`, el parámetro base es, a todos los efectos, como una variable a la que se hubiera asignado el valor 5.8, mientras que `exponente` es como una variable a la que se hubiera asignado el valor 3.0 

Cuando el subalgoritmo termina de ejecutarse, sus parámetros formales `base` y `exponente` dejan de existir, igual que las variables locales del método, y se devuelve el resultado, que se asigna, en nuestro ejemplo, a la variable `c`. 

## 4.2. Paso de parámetros por referencia

En el paso de parámetros por referencia se produce **una ligadura entre el parámetro actual y el parámetro formal**, de modo que si el parámetro formal se modifica dentro del método, el parámetro actual, propio del método invocador, también será modificado. 

**En Java, el paso por referencia no existe**. ¡Que quede claro\! No te creas lo que dicen por ahí en webs de programación e incluso en algunos libros sesudos. *En Java los argumentos se pasan por valor siempre*. Peeeeeeero cuando el argumento es un objeto en lugar de un tipo primitivo, lo que se pasa por valor es **su referencia**, es decir, la posición que ocupan en memoria, y, por lo tanto, podemos acceder a las tripas del objeto y modificar su contenido desde el método.  

Como si lo hubiéramos pasado por referencia, vamos. 

Míralo en este ejemplo:

```java
class Persona {
    private String nombre;

    public String getNombre() {
        return nombre;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }
}

public class Test {
    public static void main(String[] args) {  
        Persona p = new Persona();   // Creamos un objeto Persona
        p.setNombre("Anselmo");      // Le asignamos un nombre
        System.out.println("El nombre es:" + p.getNombre());
        
        cambiarNombre(p); // Este método recibe el objeto p y le cambia el nombre
        System.out.println("El nombre es:" + p.getNombre());  
    }
    
    private static void cambiarNombre(Persona p) {
        p = new Persona();
        p.setNombre("Santiago");
        System.out.println("El nombre es:" + p.getNombre());
    }  
}
```

La salida por pantalla de este programa será:

```
El nombre es: Anselmo   
El nombre es: Santiago   
El nombre es: Anselmo
```

Esto ocurre porque en `cambiarNombre()` se ha creado un nuevo objeto `Persona` y se ha asignado a `p`. Pero la variable `p` de `main()` no se ve afectada por esto, como sí se vería si estuviera pasada por referencia. Por lo tanto, el paso de parámetros en Java, incluso de objetos complejos, es por valor. 

Si cambiamos el código del método `cambiarNombre()` y lo dejamos así:

```java
...  
private static void cambiarNombre(Persona p) {  
  p.setNombre("Santiago");  
  System.out.println("El nombre es:" + p.getNombre());  
}  
...
```

Tendremos una salida diferente:

```
El nombre es: Anselmo   
El nombre es: Santiago   
El nombre es: Santiago
```

Ahora el paso como parámetro del objeto `p` ha funcionado *como si* estuviese pasado por referencia, es decir, los cambios que se han hecho en el objeto dentro del método se han reflejado en el objeto original del método `main()`, ya que `cambiarNombre()` ha estado actuando sobre la misma región de memoria que `main()`.

> [!abstract] Resumiendo 
> El paso de parámetros en Java es siempre por valor pero al pasar objetos complejos se envía la dirección de memoria del mismo, por lo que, en la práctica, funciona como si fuera paso por referencia y los objetos pueden modificarse en el método que los recibe. Así que, en la práctica, parece un paso de parámetros por referencia, y este es el motivo por el que muchos dicen que, en Java, los tipos primitivos se pasan por valor y los objetos y tipos complejos se pasan por referencia.

## 4.3. Diferencias entre los métodos de paso de parámetros

* **El paso por valor es unidireccional**, es decir, sólo permite transmitir datos del algoritmo principal al método a través de los argumentos. El método, más adelante, podrá devolver datos a través de return, pero eso ya no tiene nada que ver con el paso de los parámetros.

* **El paso por referencia es bidireccional**, es decir, permite que el algoritmo principal y el método intercambien información a través de los parámetros. Hay que tener mucho cuidado con esto porque aumenta el acoplamiento de los métodos. Es decir, si sucede algo incorrecto en uno, puede acabar afectando al funcionamiento del otro.


# 5. Constructores


## 5.1. Constructores

Ya conoces los constructores: esos métodos que se llaman igual que la clase y que **se ejecutan automáticamente al crear un objeto** de esa clase, y que suelen usarse para asignar un valor inicial al estado de la misma (es decir, a sus variables miembro) 

Ahora vamos a citar en algunas peculiaridades adicionales de los constructores: 

* **No pueden ser `static`**. No tendría sentido, puesto que los métodos `static` se ejecutan sin crear objeto alguno, y el constructor se ejecuta precisamente al crear un objeto de la clase. Tampoco pueden ser `abstract`, `final`, `native` o `synchronized`, que son palabrejas que aún no conoces pero que ya irán llegando. En resumen, el constructor no puede llevar ningún modificador. 

* **Suelen ser `public`**. Si son `private`, no se podrán crear objetos desde fuera de la clase, lo cual no tiene sentido (aparentemente)[^1]. Si son protected, solo se podrán crear objetos de la clase desde otras clases del mismo paquete. 

* **Si no se define uno, Java ejecutará el constructor por defecto**, que está heredado de la clase `Object` y asigna valores por defecto a las variables miembro. Estos valores son 0 en caso de atributos numéricos, carácter NUL para los caracteres, cadenas vacías para los strings y valor `null` (nulo) para el resto de objetos.

* **Pueden sobrecargarse**. Esto ya lo hemos experimentado: un constructor puede parametrizarse y otro no. O pueden parametrizarse de distinta manera, inicializando el objeto de modo distinto según cada caso. 

## 5.2. Asignación de objetos

Cuando se asigna un objeto a otro, lo que Java hace realmente es **asignar las direcciones de memoria**. 

Ten siempre presente que un objeto, como cualquier otra variable, es en realidad una referencia a una cierta dirección de memoria donde se almacena la información de esa variable.  

Si una variable `x` es, digamos, un entero de 32 bits, ocupará 4 bytes en la memoria. El sistema le asigna una posición, por ejemplo la `567c8`, y reserva los cuatro bytes siguientes a partir de esa posición para uso y disfrute de esa variable. Así que `x` ocupará las posiciones `567c8`, `567c9`, `567ca` y `567cb`. 

En esos 4 bytes caben exactamente los 32 bits de la variable `x`, por lo que podemos decir que, en realidad, "variable x" es una forma resumida y conveniente de decir "*posiciones de memoria 567c8, 567c9, 567ca y 567cb*". ¡Para un programador sería un follón tener que referirse de este último modo a las variables! 

Cuando asignamos la variable `x` a otra variable entera, llamémosla `y`, lo que Java hace es consultar el valor almacenado en las posiciones de memoria `567c8` y siguientes, y lo copia en las posiciones de la variable `y`, que serán otras diferentes. Lo que ocurre, por lo tanto, es que se asigna el valor de `x` a la variable `y`. 

**Pero con los objetos es distinto**. Como sucedía con el paso de parámetros, cuando se asigna un objeto a otro no se copian sus valores, sino que se asigna la dirección de memoria de un objeto al otro. 

Así, imagina un objeto `p` de tipo `Persona`. Este objeto ocupará más de 32 bits (tiene que almacenar todas sus variables miembro - atributos - y todo su código - métodos -). Supongamos que ocupa 200 bytes, por decir algo, y que el sistema le asigna la dirección 10037. Esto significa que el objeto `p` ocupará la dirección `10037` de memoria y las 199 siguientes, es decir, de la `10037` a la `100ff`. 

![ud04_objeto_en_menoria_01.png](/img/user/adjuntos/1DAM_Programacion/Unidad_04/ud04_objeto_en_menoria_01.png)

Ahora imagina otro objeto de tipo persona llamado `p2`, y que hacemos lo siguiente:

```java
p2 = p;
```

Lo que ocurre tras esta asignación no es que los atributos de `p` se copien uno a uno en `p2`, sino que *la dirección de `p` se copia en `p2`*. Así que no importa cual fuera la dirección de `p2` antes de la asignación, ni los valores de sus atributos. **Todo eso se pierde en el limbo de la memoria**. Ahora `p2` apuntará al mismo lugar que `p`, la dirección `10037`, y, por lo tanto, a todos los efectos, será *igual* que `p`. Los cambios en `p2` se reflejarán en `p`, y viceversa, porque en realidad son el mismo objeto. 

![ud04_objeto_en_menoria_02.png](/img/user/adjuntos/1DAM_Programacion/Unidad_04/ud04_objeto_en_menoria_02.png)

> [!abstract] Resumiendo 
> * En las **asignaciones de tipos de datos simples o primitivos**, **se copia el valor** de una variable en la otra.
> * En las **asignaciones de objetos**, **se copia la referencia** (dirección de memoria) de un objeto en el otro.

Obsérvalo con este ejemplo:

```java
class Persona {
    private String nombre;
    
    public String getNombre() {  
        return nombre;
    }
    
    public void setNombre(String nombre) {  
        this.nombre = nombre;
    }  
} 

public class Test {  
    public static void main(String[] args) {  
        Persona p1 = new Persona();
        Persona p2 = new Persona();
        p1.setNombre("Anselmo");
        p2.setNombre("Santiago");
        System.out.println("El nombre de p1 es:" + p1.getNombre());
        System.out.println("El nombre de p2 es:" + p2.getNombre());
        
        p2 = p1;
        System.out.println("Después de hacer p2 = p1:");
        System.out.println("El nombre de p1 es:" + p1.getNombre());
        System.out.println("El nombre de p2 es:" + p2.getNombre());
        
        p2.setNombre("Ana");
        System.out.println("Después cambiar el nombre de p2:");
        System.out.println("El nombre de p1 es:" + p1.getNombre());
        System.out.println("El nombre de p2 es:" + p2.getNombre());
    }   
}
```

La salida por pantalla de este programa será:

```
El nombre de p1 es: Anselmo  
El nombre de p2 es: Santiago  
Después de hacer p2 = p1:  
El nombre de p1 es: Anselmo  
El nombre de p2 es: Anselmo  
Después de cambiar el nombre de p2:  
El nombre de p1 es: Ana  
El nombre de p2 es: Ana
```

Al asignar `p2 = p1` hemos igualado sus posiciones de memoria, y cualquier cambio en uno implica un cambio en el otro. Desde ese momento, en realidad los dos objetos han pasado a ser el mismo. 

## 5.3. Constructor copia

Pero esta sección iba sobre constructores y destructores, ¿no? ¿Qué tiene que ver la asignación de objetos con los constructores? 

Bien, a veces es posible que, al hacer `p2 = p1` y cosas por el estilo, quieras que, en realidad, los valores de `p1` se copien en `p2`, y no que los dos objetos pasen a ser el mismo, ¿verdad? Vamos, que se comporten igual que las variables simples. 

Para estos casos se utiliza un constructor especial llamado **constructor copia**. Se trata de un constructor que copia los valores de un objeto en otro del mismo tipo. Por lo tanto, el constructor recibirá como parámetro una variable del tipo de su propia clase. 

Vamos a añadir un constructor copia a nuestra clase Persona:

```java
class Persona {  
  private String nombre;

  public Persona (Persona p) { // Constructor copia  
    this.nombre = p.getNombre();
  }

  public String getNombre() {  
    return nombre;
  }

  public void setNombre(String nombre) {  
    this.nombre = nombre;
  }  
}
```

Mira el constructor. Recibe como parámetro otra persona, y obtiene el valor de sus atributos (solo uno, porque nuestra clase solo tiene uno, pero podrían ser más) para asignarlos a sus propios atributos. 

No es difícil imaginarse cómo podríamos ahora copiar los datos de una persona en otra sin igualar los objetos:

```java
public class Test {  
  public static void main(String[] args) {  
    Persona p1 = new Persona();
    Persona p2 = new Persona(p1); // Aquí usamos el constructor copia
    System.out.println("El nombre de p1 es:" + p1.getNombre());
    System.out.println("El nombre de p2 es:" + p2.getNombre());
    
    p2.setNombre("Ana");
    System.out.println("Después cambiar el nombre de p2:");
    System.out.println("El nombre de p1 es:" + p1.getNombre());
    System.out.println("El nombre de p2 es:" + p2.getNombre());
  }   
}
```

La salida ahora demuestra que los objetos `p1` y `p2` siguen siendo independientes a pesar de que al principio compartan los valores de sus atributos:

```
El nombre de p1 es: Anselmo   
El nombre de p2 es: Anselmo   
Después de cambiar el nombre de p2:   
El nombre de p1 es: Anselmo   
El nombre de p2 es: Ana
```

## 5.4. Inicializadores static

Para acabar de complicar la cosa, están los **inicializadores**. 

Los inicializadores no son constructores. No se ejecutan al crear un objeto de la clase, sino que se ejecutan *una y solo una vez*, en la primera ocasión en la que se utiliza la clase. 

Los inicializadores `static` tienen varias limitaciones: 

* No pueden devolver ningún valor. 
* No tienen nombre. No pueden ser invocados. 
* Pueden usar bloques `try-catch` 
* Pueden existir varios, pero siempre se ejecutarán en el orden en el que estén escritos.
* Solo pueden inicializar variables `static` de la clase o invocar métodos `static`. 

¿Y para qué demonios sirve esto? Bueno, es habitual que quieras dar un valor inicial a los atributos static de una clase, ¿no? Con los tipos primitivos eso no es un problema: se le asigna un valor junto a la declaración y listo. Pero con los objetos complejos puede ser más complicado, más que nada porque la asignación puede fallar. 

Es recomendable asignar esos objetos dentro de inicializadores para poder gestionar los errores con bloques `try-catch`.

Por lo demás, vamos a ser sinceros: no es algo que vayas a usar por ahora. Pero están relacionados con los constructores, y éste era el sitio para hablar de ellos, y eso es lo que hemos hecho. 

¿Que aún así quieres ver el aspecto que tiene un inicializador estático? Vale. Aquí lo tienes:

```java
class Ejemplo {  
    static int a;
    int b;
    
    public Ejemplo() {  
        b = a * 2;
        System.out.println("Valor de a: " + a + ". Valor de b: " + b);
    }

    /*
     Este es el inicializador static. Se ejecutará antes de cualquier
     instanciación de la clase Ejemplo y, por tanto, antes que el
     constructor.
     */
    static {
        a = 1;
    }
}
```

## 5.5. Destructores

En Java **no existen los destructores**. Fin de la sección. 

Bueno, explíquemoslo un poco. Los destructores son comunes en otros lenguajes orientados a objetos, en particular en C++. Se encargan de **liberar los recursos** que el objeto está ocupando antes de que éste deje de existir (por ejemplo, cerrar un archivo abierto, o una conexión con una base de datos, un una zona de memoria reservada). Son invocados automáticamente cuando la variable del objeto va a dejar de existir. 

Los destructores, en C++, dejan bajo la responsabilidad del programador la liberación de recursos y los programadores, como todas las personas, a veces somos muy irresponsables. 

En Java existe un mecanismo automático, el **recolector de basura** (*garbage collector*) que se encarga de ir liberando los recursos que ocupaban los objetos que ya no existen, así que, en principio, no hay ninguna necesidad de programar métodos destructores. 

> [!info] Hace años... 
> Existía un "pseudodestructor" en Java. Era el método `finalize()`. Si en tu clase ponías un método `finalize()`, Java lo invocaba cuando el recolector de basura se ponía en marcha. Es decir, que este método **no forzaba la ejecución del recolector de basura**. Sólo lo solicitaba a la JVM.
> El recolector es un proceso automático y, realmente, el programador no tienen ni idea de cuándo va actuar, aunque había una forma de provocarlo:
> ```java
> // Sugerir la ejecución del recolector de basura
> System.runFinalization();
> System.gc();	// gc = Garbage Collector
> ```
> El método `finalize()` fue declarado **obsoleto** (`deprecated`) en Java 9 y pasó al estado de **desaprobación terminal** (`deprecated for removal`) en Java 18.
> 
> Los motivos eran varios y en todos los casos era por degradación del rendimiento:
> - No se garantizaba su ejecución y, si lo hacía, era impredecible.
> - Muchos recursos y streams (gestores de archivos, conexiones a bases de datos, sockets, etc.) podían quedarse abiertos si `finalize()` no se ejecutaba o lo hacía tarde.
> - Y así, un largo etcétera.
> 
> Al eliminar esta opción, se recomendó el uso de otros recursos como el `try-with-resources`, que veremos más adelante.

Así que reafirmamos nuestra afirmación inicial. **En Java no existen los destructores**.


[^1]:  Hay un patrón de diseño que usa constructores privados: el patrón [Singleton](https://refactoring.guru/es/design-patterns/singleton).



# 6. Elementos abstractos y finales


## 6.1. Clases y métodos abstractos

Las clases abstractas son clases **genéricas**. Esto quiere decir que no pueden instanciarse, es decir, no pueden crearse objetos de esa clase. Se usan únicamente para crear clases derivadas a partir de ellas.

Por ejemplo, `Vehículo` puede ser una clase abstracta en una jerarquía de clases. De ella pueden derivar clases más concretas como `Motocicleta`, `Furgoneta` o `Camión`, y de estas últimas sí que se instanciarán los objetos. Pero no tiene sentido crear objetos de tipo `Vehículo`, puesto que faltarán detalles importantes en su implementación debido, precisamente, a que es una clase genérica.

Las **clases abstractas** se usan, por lo tanto, para **representar correctamente jerarquías** entre objetos del mundo real, y **permiten reutilizar gran cantidad de código** de forma comprensible.

Las características de una clase abstracta son:

* No puede instanciarse.
* Puede tener métodos abstractos y no abstractos.
  * Los **métodos no abstractos** son heredados por las clases hijas como en cualquier otra herencia. Estas pueden o no redefinirlos.

  * Los **métodos abstractos** deben ser implementados forzosamente por las clases hijas, a menos que sean también clases abstractas y los sigan declarando como abstractos.

* Si una clase tiene algún método abstracto, entonces la clase también tiene que ser abstracta.

* Los métodos abstractos no pueden ser `static`.

La declaración de una clase o un método abstractos se hace anteponiendo el modificador **`abstract`** a la misma. Por ejemplo:

```java
public abstract class Vehiculo {  
   private int peso;  
   public void setPeso(int p) { peso = p; }    // Método convencional  
   public abstract int getVelocidadMaxima();   // Método abstracto.   
                                               // No se implementa aquí.  
} 
```

## 6.2. Objetos, clases y métodos finales

Un objeto final hace que sea imposible que otro objeto tenga la misma referencia. Por ejemplo, si compilamos este código obtendremos un error en la tercera línea:

```java
final Persona p1 = new Persona();  
Persona p2;  
p2 = p1;
```

Recuerda que hemos usado la palabra final aplicada a variables de tipos primitivos para declararlas como constantes. Más o menos así:

```java
final int PI = 3.141592;
```

Esto hace que la constante `PI` no pueda volver a asignarse a lo largo de su vida en el programa. 

Pues bien, con los objetos finales ocurre algo parecido pero de forma aún más estricta, puesto que ni siquiera pueden ser asignados a otros objetos. Esto ocurre para impedir que el objeto original (`p1` en el ejemplo anterior) pueda ser modificado mediante el segundo objeto (`p2`)

Los objetos finales se usan con propósitos de seguridad (para prevenir modificaciones accidentales en el estado de un objeto) y por eficiencia (al existir una sola instancia de ese objeto, el optimizador de la JVM lo colocará en la memoria RAM y el acceso al mismo será muy rápido)

Los métodos finales son aquellos que no van a modificarse nunca. Es decir, si otra clase los hereda, no podrá modificarlos. Esto se utiliza en aquellos métodos cuyo comportamiento no debería ser alterado por ninguna de las clases descendientes, normalmente por motivos de seguridad y/o de eficiencia. Así prevenimos que una mala práctica de programación pueda hacer que nuestro código deje de funcionar correctamente.

Por último, las clases finales son aquellas que no pueden tener descendencia. Esto tiene importancia en la eficiencia y en la seguridad de nuestra estructura de clases. Por ejemplo, `java.lang.System` es una clase final.



# 7. Interfaces


Una interfaz es **una clase sin código**, es decir, una clase que puede tener atributos y las definiciones de sus métodos, pero sin código dentro de estos. En otras palabras, contiene **métodos abstractos**.

Por ejemplo:

```java
public interface ShapeCalculable {  
   public double area();  
   public double perimetro();  
}
```

> [!info] Nota 
> Aunque en el ejemplo anterior se añade el modificador de acceso `public`, los métodos declarados dentro de un interfaz son, por defecto, **públicos** y **abstractos**. Es decir, que el ejemplo anterior podría escribirse así:
> ```java
> public interface ShapeCalculable {
>     double area();
>     double perimetro();
> }
> ```

Una interfaz por sí misma no sirve para nada. Su utilidad es servir de **molde** para formar otras clases, a pesar de ser totalmente distintas, implementarán el código **cada una a su manera**. Esto es polimorfismo del bueno... Para entenderlo observa estas dos clases:

```java
public class Rectangulo implements ShapeCalculable {
    private double base, altura;

    public Rectangulo (double b, double h) {  
        base = b;  
        altura = h;  
    }

    @Override  
    public double area() {  
        return base * altura;  
    }  
    
    @Override  
    public double perimetro() {  
        return 2 * (base + altura);  
    }
}

public class Circulo implements ShapeCalculable{  
    private double radio;

    public Circulo (double r) {  
        radio = r;  
    }

    @Override  
    public double area() {  
        return Math.PI * Math.pow(radio, 2);  
    }  
    
    @Override  
    public double perimetro() {  
        return 2 * 3.14 * radio;  
    }  
}
```

Si te fijas verás que las clases rectángulo y círculo implementan los dos métodos del interfaz, `area()` y `perimetro()`, y cada una lo hace de un modo distinto. De hecho, en ambos casos se usa la notación **`@Override`** para dejar claro que se están sobreescribiendo (aunque en el interfaz no se hayan implementado).

Podríamos añadir muchas otras clases que usaran la misma interfaz y cada una podría implementar estos métodos de forma diferente. 

Cualquier persona un poco escéptica (y el escepticismo es una cualidad muy necesaria, oiga usted) se preguntaría en este punto: ¿y esto para qué demonios sirve? 

Es una buena pregunta, y tiene una buena respuesta: sirve para **forzar que todas esas clases, por muy distintas que puedan ser, puedan ejecutar los mismos métodos** (insistiendo en que cada una a su manera). En siguientes apartados veremos que este polimorfismo viene muy bien.

Eso si, debe planearse bien ya que una interfaz no debe cambiarse una vez establecida en alguna clase, aunque ésta se rehaga de los pies a la cabeza.

## 7.1. Métodos `default`

Pero si no debemos cambiar una interfaz, ¿eso significa que no puede ampliarse? Nada de eso. Java nos permite definir métodos *a posteriori* usando el modificador **default** (por defecto), que se añade antes del tipo de retorno:

```java
public interface Saludo {  
    default void saludar() {  
        System.out.println("Hola, mundo\!");  
    }  
}
```

Si, este método **default** del interfaz **está implementado** (tiene un cuerpo con funcionalidad). En eso consiste el modificador `default`, en permitir definir métodos ya codificados dentro de el interfaz. Así, las clases que implementan el interfaz pueden usar dichos métodos tal cual, sobreescribirlos (tal y como hacen con los métodos abstractos) o simplemente ignorarlos.

> [!info] Nota 
> Esto nos permite ampliar interfaces añadiendo nuevos métodos sin romper la compatibilidad hacia atrás con las clases existentes que ya la implementan.

> [!warning] Importante 
> Podría darse el caso de que una clase implementase dos o más interfaces que tienen el mismo método `default`, es decir, con el mismo nombre, el mismo tipo de retorno y los mismos parámetros. En tal caso, **la clase está obligada a sobrescribir el método** para resolver el problema. Si no, no dejaría compilarla.

## 7.2. Diferencia entre interfaces y clases abstractas

Según qué casos podríamos ver muchas similitudes entre los interfaces y las clases abstractas. Por ejemplo: 

```java
// Interfaz
public interface ShapeCalculable {  
    public double area();  
    public double perimetro();  
}  
```

```java
// Clase abstracta
public abstract class ShapeCalculable {  
    public abstract double area();  
    public abstract double perimetro();  
}
```

Pero hay que dejar claro que **no son iguales**. Ambas sirven para forzar un interfaz común a todas las clases que heredan de ella (en el caso de las clases abstractas) o que lo implementan (en el caso de los interfaces).

Entonces, ¿cuándo debemos usar una u otra?

Las **clases abstractas** son clases, aunque no puedan instanciarse. Pueden contener código en varios de sus métodos, y los interfaces no (y ahí está la primera gran diferencia). Cualquiera que herede de ellas debe implementar los métodos forzosamente, pero no solo eso, sino que cualquiera que herede de ellas **debe ser un hijo natural**. Es decir, si `Vehiculo` es una clase abstracta, todas las clases que deriven de ella **tienen que ser vehículos**.

Esto con los **interfaces** no ocurre, y es la gran (y sutil) diferencia entre unas y otras. Una interfaz solo define un conjunto de métodos comunes que luego pueden ser implementados por una gran variedad de clases, que **pueden tener mucho o poco que ver entre sí**. Un ejemplo clásico es el interfaz `Drawable` (“dibujable”). Proporciona un método **`draw()`** que hace que el objeto se represente gráficamente en la pantalla. Un interfaz como `Drawable` puede aplicarse a muchas familias de clases:

- Figuras geométricas
- Vehículos
- Vegetales
- Personas
- Etc.

Una figura geométrica y un vehículo no tienen nada que ver: difícilmente podríamos imaginar una estructura de clases en las que unas acaben derivando de otras. Y, sin embargo, todas ellas pueden implementar el interfaz `Drawable`.

Existen otras diferencias aún más sutiles, desde luego. Por ejemplo, como una clase puede implementar varios interfaces a la vez, supone **una especie de herencia múltiple camuflada** (ya que, recuerda, **en Java no está permitida la herencia múltiple**). Pero estas cuestiones son demasiado sutiles para un libro que de introducción como este. Todo llegará a su debido tiempo, y con lo que hemos hablado aquí ya puedes hacer muchas, muchísimas cosas.


# 8. Herencia

La herencia es un poderosísimo modo de **reutilizar código**. Cuando una clase deriva de otra, o extiende de otra o es hija de otra, *hereda* todos sus atributos y métodos. Es decir, hereda datos y código, como en la vida real heredamos los ojos marrones o la tendencia a la calvicie. Una clase derivada, o clase hija o **subclase** puede sobreescribir (el `override` que hemos visto en los interfaces) algunos miembros. También puede sobrecargarlos, todo ello para adaptarlos a sus necesidades o ampliarlos de algún modo.

En otras palabras, la clase madre o **superclase** es una **generalización** y sus **subclases** son **especializaciones** de aquella.

En Java, cada clase solo puede heredar de otra (**herencia simple**). Otros lenguajes, como C++, permiten a cada clase heredar de varias (**herencia múltiple**). La herencia múltiple es más flexible pero presenta algunos problemas serios en los que ahora no vamos a entrar. 

Veamos el mecanismo de herencia replanteando el ejemplo de las figuras del apartado anterior. Ahora, en lugar de una interfaz, usaremos la siguiente como superclase a todas las figuras geométricas. Esta clase contiene los elementos comunes a todas las figuras geométricas que definiremos como subclases de esta:

```java
public class FiguraGeometrica {  
    String color;  
    boolean tieneBorde;

    public void setColor(String s) { color = s; }  
    public String getColor() { return color; }

    public void setBorde(boolean borde) { tieneBorde = borde; }  
    public String getBorde() { return tieneBorde; }  
}
```

Esta clase indica que todas las figuras geométricas que ahora no es un interfaz, sino una clase cien por cien) será la base de nuestras otras clases, ya que todas las subclases que hereden como estas:

```java
public class Rectangulo extends FiguraGeometrica {  
    private double base, altura;  
    public Rectangulo(double b, double h) {  
        base = b;  
        altura = h;  
    }  
    public double area() {  
        return base * altura;  
    }

    public double perimetro() {  
        return 2*(base+altura);  
    }  
}

public class Circulo extends FiguraGeometrica {  
    private double radio;

    public Circulo(double r) {  
        radio = r;  
    }

    public double area() {  
        return 3.14 * radio * radio;  
    }

    public double perimetro() {  
        return 2 * 3.14 * radio;  
    }  
}
```

Las clases rectángulo y círculo son idénticas a las del ejemplo del interfaz, salvo que ahora usan `extends` en lugar de `implements` para indicar que **derivan, extienden o heredan** de `FiguraGeometrica`.

En un diagrama UML básico, esta herencia se expresaría así:

![ud04_uml_herencia.png](/img/user/adjuntos/1DAM_Programacion/Unidad_04/ud04_uml_herencia.png)
> Diagrama UML que muestra cómo `Rectangulo` y `Circulo` heredan de `FiguraGeometrica`.

Esto significa que heredan todos los datos y métodos de `FiguraGeometrica`. Tanto rectángulo como círculo dispondrán de los atributos `color` y `tieneBorde` y podran ejecutar los métodos `getColor()` y `setColor()` definidos en `FiguraGeometrica`. Por lo tanto, podemos hacer algo como esto:

```java
Circulo c = new Circulo(2);  
Rectangulo r = new Rectangulo(4,7);  
c.setColor("Rojo");  
c.setBorde(false);

r.setColor("Verde");  
r.setBorde(true);

System.out.println("El círculo es de color " + c.getColor()); System.out.println("Área del círculo " + c.area());  
if (c.getBorde()) {  
    System.out.println("El círculo tiene borde.");  
}

System.out.println("El rectángulo es de color " + r.getColor()); System.out.println("Área del rectángulo " + r.area());  
if (r.getBorde()) {  
    System.out.println("El rectángulo tiene borde.");  
}
```

Aunque los métodos `setColor()`, `setBorde()`, `getColor()` y `setBorde()` no están definidos en las clases círculo ni rectángulo, **han sido heredados** de su superclase y pueden utilizarse como propios. Así se reutiliza el código de forma simple y elegante, sin necesidad de hacer *copy-paste*.

> [!info] 💡 A propósito 💡 
> Cuando un programador se descubre a sí mismo haciendo *copy-paste*, debería encendérsele la luz de alarma dentro de la cabeza, porque eso significa que **no está aprovechando el mecanismo de herencia** de la <abbr title="Object Oriented Programming">OOP</abbr> y que, por lo tanto, su estructura de clases está probablemente mal planteada.

Por eso definir de forma independiente los métodos `perimetro()` y `area()` no es lo más correcto, ya que podríamos ponerles nombres distintos a las mismas funcionalidades, además de olvidar implementar alguno en una figura que otra. Para tener homogeneidad, lo mejor es añadirlos a la superclase `FiguraGeometrica`. El problema es que la superclase no puede calcular estas medidas ya que no es una figura específica y **no sabe cómo hacerlo** porque no sabe qué figuras se van a implementar.

En estos casos, cuando **todas las subclases** deben tener la responsabilidad de implementar algo pero cada una debe hacerlo de una forma concreta, usamos los **métodos abstractos** de la misma forma que en los interfaces:

```java
public abstract class FiguraGeometrica {  
    String color;  
    boolean tieneBorde;

    public void setColor(String s) { color = s; }  
    public String getColor() { return color; }

    public void setBorde(boolean borde) { tieneBorde = borde; }  
    public String getBorde() { return tieneBorde; }

    public abstract double area();  
    public abstract double perimetro();  
}
```

Se puede observar que aquí se usa el modificador **`abstract`**, que no se usaba en los interfaces, tanto en los métodos como en la clase. El motivo es sencillo: si una clase tiene al menos un método abstracto (definido pero no implementado) la clase no puede instanciarse porque ese método sería un “cuerpo extraño”. Así que **la clase también debe ser abstracta**. Esto significa que **no puede instanciarse ningún objeto a partir de ella**:

```java
FiguraGeometrica figura = new FiguraGeometrica(); // Error de compilación
```

**Las subclases tienen la obligación de implementar estos métodos abstractos** (de la misma forma que ocurría con los interfaces), por lo que es una buena práctica añadir la anotación **`@Override`** en ambos métodos al igual que se hacía con el interfaz.


# 9. Polimorfismo, sobreescritura, sobrecarga


Polimorfismo, sobreescritura y sobrecarga son tres características de la programación orientada a objetos muy relacionadas entre sí. Ya hemos hablado de ellas en anteriores ocasiones de manera informal. Ahora vamos a ampliar estos conceptos.

## 9.1. Más acerca del polimorfismo

El polimorfismo en programación orientada a objetos consiste en que **un mismo elemento puede adquirir varias formas**.

La manera más habitual en la que encontramos el polimorfismo es en los **métodos**. Pueden existir varias versiones del mismo método con distinta forma, esto es: el mismo nombre pero distintos parámetros, o distinto tipo de retorno. El ejemplo más claro puede apreciarse en el constructor de la clase `Persona`:

```java
public Persona();                         // Constructor sin parámetros  
public Persona(String nombre);            // Constructor con 1 parámetro  
public Persona(String nombre, int edad);  // Constructor con 2 parámetros
```

Este tipo de polimorfismo es resuelto por el intérprete **comparando los parámetros formales con los parámetros actuales** que se usan en la llamada al método, y ejecutando la versión del método que se corresponda con la llamada.

Pero hay otra forma de polimorfismo más compleja al tiempo que más potente, y es la que se refiere al **polimorfismo de los objetos pertenecientes a una clase base**. Veámoslo con un ejemplo.

Supongamos que tenemos una jerarquía de clases, como el clásico caso de la clase `Vehículo` de la que deriva la clase `Automóvil`, `Motocicleta`, etc. Imaginemos, además, que de la clase `Automóvil` derivamos la clase `Todoterreno`. Gráficamente lo podemos representar así:

![ud04_uml_herencia_vehiculo_01.png](/img/user/adjuntos/1DAM_Programacion/Unidad_04/ud04_uml_herencia_vehiculo_01.png)

> [!info] Por cierto... 
> Esto, por cierto, es un **diagrama UML de clases**, una de esas herramientas que usan los arquitectos o analistas del software para diseñar las aplicaciones orientadas a objetos. No es nuestro propósito detenernos en esos asuntos pues, como ya hemos dicho varias veces, para comenzar a diseñar programas orientados a objetos muy complejos necesitarías aprender ingeniería del software. Pero el diagrama de clases es tan útil y tan fácil de entender que es buena idea que te familiarices con él, y resulta tan simple que no requiere mucha explicación. Cada clase es un rectángulo, y tiene dentro su nombre, sus atributos y sus métodos. Las flechas indican la herencia.

El código en Java que implementa el diagrama anterior es más o menos así:

```java
class Vehiculo {  
    protected String marca;  
    public void setMarca(String m) { marca = m; }  
    public String getMarca() { return marca; }  
}

class Automovil extends Vehiculo {  
    protected double consumo;   // consumo de combustible cada 100 km  
    public void setConsumo(double c) { consumo = c; }  
    public double getConsumo() { return consumo; }  
}

class Todoterreno extends Automovil {  
    public double getConsumo() { return consumo \* 1.2; }  
}
```

La idea es que los vehículos de tipo `Todoterreno` tendrán un consumo medio cada 100 km. Cuando se comporten como automóviles convencionales (circulando por calles y carreteras), ese será su consumo. Pero cuando circulen por caminos y pistas forestales, su consumo medio habitual se verá incrementado en un 20% (ver clase `Todoterreno`)

Por lo tanto, los vehículos de tipo `Todoterreno` a veces se comportarán como un `Automóvil` y a veces como un `Todoterreno`. **He aquí el polimorfismo de este ejemplo**.

Podemos usar las clases anteriores de este modo:  

```java
Vehiculo v1 = new Automovil();  
v1.setMarca("Seat");  
v1.setConsumo(4.8);   // Dará error al compilar  
Automovil v2 = new Todoterreno();  
v2.setMarca("Toyota");  
v2.setConsumo(7.0);  
System.out.println(v2.getConsumo());
```


En este ejemplo vemos varios aspectos clave del polimorfismo:

- En la línea 1 asignamos un objeto `Automovil` a una variable (`v1`) de tipo `Vehiculo`. Como `Automovil` deriva de `Vehículo`, es posible hacerlo.

- En la línea 3, sin embargo, vemos una limitación de este mecanismo: como `v1` es de tipo `Vehiculo`, no puede resolver la llamada a `setConsumo()`, que es un método de `Automovil`. Se puede arreglar haciendo una conversión explícita:

```java
((Automovil)v1).setConsumo(4.8);
```

Esta conversión hace que, momentáneamente, v1 se comporte como un `Automovil` y no como un `Vehiculo`.

En las siguientes líneas repetimos la idea, pero asignando un `Todoterreno` a una variable `Automovil` (`v2`). La pregunta sería:

> [!question]- ¿qué obtendremos en la última línea? ¿El consumo de un `Automovil` (7.0) o el de un `Todoterreno` (8.4, es decir, un 20% más que el consumo medio)?  
> La respuesta es **8.4**. Y el motivo es que, aunque `v2` es una variable de tipo `Automovil`, está referenciando a un objeto de tipo `Todoterreno`, y el método `getConsumo()` está sobreescrito en esta clase. Por ello, el intérprete de Java preferirá ejecutar el `getConsumo()` de `Todoterreno`.

Sin embargo, sería posible obtener el consumo de `v2` comportándose como un `Automóvil` haciendo una conversión explícita:  

```java
((Automovil)v2).getConsumo();
```

Por lo tanto, el objeto `v1` puede comportarse como un `Vehículo` o como un `Automóvil`, según nos interese. Y el objeto `v2` puede hacerlo como un `Automóvil` o como un `Todoterreno`. Ambos objetos están adquiriendo diferentes formas (polimorfismo) a lo largo de la aplicación.

## 9.2. Vinculación temprana y vinculación tardía

Puede que el polimorfismo de objetos te parezca un follón, y tienes razón: **lo es**. Pero, al mismo tiempo, resulta un mecanismo **muy potente**. Como todos los mecanismos potentes, es fácil que te estalle en las manos si no lo manejas con cautela.

Para tratar de clarificar la forma en la que el intérprete Java decide qué versión de cada método ejecuta en cada caso, hay que tener en cuenta los mecanismos de vinculación que utiliza y cuándo utiliza cada uno. Vincular, en este contexto, se refiere a la forma en la que Java enlaza la llamada a un método con el código concreto de dicho método.

En Java hay dos mecanismos de vinculación: 

* **Vinculación temprana**. Se realiza **en tiempo de compilación**. Es la utilizada con los métodos "normales" y con los sobrecargados.

* **Vinculación tardía**. Se realiza **en tiempo de ejecución**. Es la utilizada con los métodos sobrescritos, excepto los finales.

La vinculación tardía es más lenta y puede producir efectos sorprendentes, pero también es más potente. Es la que ha funcionado en el ejemplo anterior, cuando la variable `v2` de tipo `Automóvil` ha ejecutado un método de la subclase `Todoterreno`. Esto ha ocurrido porque el método en cuestión, `getConsumo()`, estaba sobrescrito en la subclase, y la vinculación tardía ha resuelto, en tiempo de ejecución, que la versión de `getConsumo()` de `Todoterreno` era la que correspondía al objeto.

## 9.3. Más acerca de la sobreescritura de métodos

La **sobrescritura** u ***overriding*** de métodos es fundamental en programación orientada a objetos y, de hecho, la hemos venido practicando desde que trabajamos con herencia.

La sobrescritura nos permite modificar el comportamiento de la clase madre reescribiendo el código de uno o varios métodos de la misma en las clases derivadas. Las únicas condiciones que deben cumplir los métodos sobrescritos son:

* Conservar el mismo nombre.
* Devolver un dato del mismo tipo.
* Mantener los mismos parámetros formales.

Todo ello por pura lógica: si no, no estaríamos redefiniendo un método, sino declarando otro método diferente.

En el apartado anterior sobre sobre polimorfismo puedes ver un ejemplo complejo de sobrescritura (método `getConsumo()` en la clase `Todoterreno`)

## 9.4. Más acerca de la sobrecarga

La **sobrecarga** u **_overloading_** es, en realidad, una de las formas básicas del polimorfismo. Cuando definimos varias versiones del mismo método, con distintos parámetros y/o valores devueltos, se dice que estamos sobrecargando ese método.

Las reglas para hacer correctamente la sobrecarga de métodos son obvias:

* El método sobrecargado debe conservar el nombre pero variar la lista de parámetros formales.
* Los métodos pueden sobrecargarse en la superclase y en las subclases.
* En la sobrecarga pueden utilizarse las mismas excepciones que en el método original o añadir otras.
* En la sobrecarga también puede cambiarse el tipo de retorno o el modificador de acceso.

## 9.5. Conversiones entre objetos

Conversiones explícitas: he aquí otra cosa que hemos utilizado muchas veces de manera informal e intuitiva y que ha llegado el momento de formalizar. Las conversiones, seguro que lo recuerdas, pueden ser de dos tipos: implícitas o explícitas. 

### Conversión implícita

Las **implícitas** eran aquellas que se realizaban automáticamente. En general, en Java están prohibidas, y solo hay algunos casos en los que pueden funcionar sin provocar un error de compilación o de ejecución.

```java
byte a = 1;  
int b = 2;  
int x = a;   // Conversión implícita que funciona  
byte y = b;  // Conversión implícita que falla (un int no “cabe” en un byte)
```

### Conversión explícita

Las **explícitas** son las conversiones que el programador **fuerza utilizando un _casting_** o molde. En tal caso, el compilador mirará para otro lado y supondrá que sabemos lo que hacemos. Forzar una conversión puede dar lugar a efectos indeseados. Como estas conversiones dan mucho más juego, nos vamos a centrar en ellas.

## 9.6. Casting entre tipos primitivos

A lo largo del libro hemos visto muchos ejemplos de conversión de tipos explícita (*casting*) entre tipos primitivos, es decir, de conversión de tipos descrita por el programador. Por ejemplo:

```java
int a = (int)(Math.random() * 100);
```

La única regla es: si conviertes de un tipo de más precisión a otro de menos precisión, perderás información por el camino. En el ejemplo anterior, se convierte de `double` a `int`. ¿Qué información se ha perdido? Los decimales de `double`, por supuesto. En este caso, era justo lo que pretendíamos.

## 9.7. Casting entre objetos

En este capítulo hemos visto (aunque quizá no te hayas percatado) otra aplicación del casting: la que se realiza entre objetos cuando tienen entre si una relación de herencia. Por ejemplo:

```java
((Automovil) v1).setConsumo(4.8);
```

En este ejemplo, `v1` era un objeto de una clase llamada `Vehículo`, que no disponía del método `setConsumo()`, mientras que la clase hija `Automovil` sí que lo tenía. Haciendo la conversión `(Automovil) v1`, conseguíamos acceder al método `setConsumo()` desde un objeto de tipo `Vehículo`.

El casting entre objetos sigue un par de sencillas reglas:

* Si estás usando una clase más específica (más abajo en la jerarquía) para acceder a métodos de clases superiores, no hace falta casting. A esto se le denomina **upcasting** (casting “hacia arriba”)
* Si estás usando una clase más general (más arriba en la jerarquía) para acceder a métodos de clases inferiores, sí debes hacer casting. A esto se le denomina **downcasting** (casting “hacia abajo”)

Un caso habitual de conversión de tipos entre objetos se produce en las llamadas a métodos que aceptan un objeto como parámetro. Supongamos que tenemos un método que acepta un vehículo como parámetro para hacer ciertas operaciones con él. Ese método puede declararse así:

```java
public void miMetodo(Vehiculo v)
```

En tal caso, la variable `v` será un `Vehículo` genérico (parte superior de la jerarquía), y cualquier intento de usar los métodos de `Automóvil`, `Todoterreno` o cualquier otra clase, requerirá un casting.

En cambio, el método también puede declararse así:

```java
public void miMetodo(Automovil a)
```

En este caso, podrán usarse a través del objeto a todos los métodos de `Automovil` y de `Vehiculo` sin necesidad de casting, pero los de `Todoterreno` sí necesitarán conversión explícita, y los de `Bicicleta`, simplemente, no podrán usarse.

> [!question] ¿Qué es mejor, entonces? ¿Usar un parámetro lo más genérico posible, como `Vehículo`, o uno más específico, como `Automóvil`?
> La respuesta, obviamente, depende de lo que estemos programando, pero utilizar una clase muy genérica como Vehículo proporciona al método mucha más flexibilidad, porque puede acceder a cualquier método de cualquier subclase (mediante casting), mientras que utilizar una clase más específica limita los métodos accesibles a los de la rama de la jerarquía en la que se encuentre la clase. 

## 9.8. Más sobre upcasting y downcasting

Upcasting y downcasting son una parte importante de Java. Son mecanismos que nos permiten exprimir al máximo el polimorfismo. Como hemos visto, el upcasting es automático, mientras que el downcasting debe hacerse explícito.

Upcasting y downcasting NO funcionan como las conversiones entre tipos primitivos, y esto es motivo de confusión habitual entre programadores principiantes. Por ello, vamos a insistir en este importante punto planteando otro ejemplo clásico de jerarquía de clases con el que juguetearemos en las siguientes páginas:

Primero de todo, observa que, en la raíz de la jerarquía, está `Object`. Esta clase no suele dibujarse en los diagramas de clase, pero siempre está presente. Simplemente, si creas una clase en Java que no deriva de ninguna otra, Java supondrá que deriva de `Object`. Así que un `Object` es el bisabuelo de un gato.

Consideremos ahora este ejemplo: 

```java
class Animal {  
    int vida = 100;  
}

class Mamifero extends Animal { }

class Gato extends Mamifero { }

class Perro extends Mamifero { }

public class Prueba {  
    public static void main(String[] args) {  
        Gato g = new Gato();  
        System.out.println(g.vida);  
        Perro p = new Perro();  
        System.out.println(p.vida);  
    }  
}
```

Cuando ejecutemos la clase `Test`, obtendremos `100 100` en la consola, porque tanto el perro como el gato heredan la vida de la clase `Animal` (su abuela).

Cuando hacemos un casting no estamos cambiando el objeto, sino sólo etiquetándolo de un modo diferente. Por ejemplo, si hacemos un upcast de `Gato` a `Animal`, el objeto no deja de ser un gato. Todavía es un gato, pero será tratado temporalmente como un `Animal` cualquiera para acceder a los atributos y propiedades de `Animal`.

Aquí tenemos un ejemplo de upcasting:

```java
Gato g = new Gato();  
System.out.println(g);  
Mamifero m = g;    // upcasting  
System.out.println(m);
```


En la pantalla obtendremos algo como esto:

```
Gato@a90653  
Gato@a90653
```

Esto demuestra que el objeto nunca ha dejado de ser un gato. Gato nació y gato morirá, aunque por el camino lo hayamos convertido temporalmente en mamífero (en realidad, nunca ha dejado de serlo). Sin embargo, un gato no puede convertirse en un perro. Ese intento de casting fallará porque no tiene sentido en el mundo real ni tampoco en nuestra jerarquía de objetos (porque consigue representar el mundo real con una aproximación bastante razonable)

El upcasting es automático en Java. No es necesario hacerlo explícito, pero puede hacerse si lo deseamos. Así: 

```java
Mamifero m = (Mamifero)new Gato();

Esto es equivalente a:   
Mamifero m = new Gato();

Pero el downcasting sí debe hacerse explícitamente:  
Gato g1 = new Gato();  
Animal a = g1;       //upcasting automático  
Gato g2 = (Gato) a;  //downcasting manual
```

¿Por qué uno es automático y el otro no? Bueno, el upcasting no puede fallar: un gato siempre es un animal, y puede ser tratado como tal. Pero el downcasting es otra historia. Los perros, como los gatos, son animales, pero un gato no puede ser convertido en perro, ni tampoco al revés. Con el downcasting hay que tener más cuidado, o Java nos tirará a la cara una excepción de conversión de objetos.

### 9.8.1. El operador instanceof

Y aquí llega nuestro aliado definitivo para ayudarnos en todo este lío: un operador llamado **`instanceof`**. 

Este operador nos dice si un objeto es una instancia de una determinada clase. Devuelve true o false. Aquí lo vemos en acción: 

```java
Cat c1 = new Cat();   
Animal a = c1; // upcasting a Animal   
if (a instanceof Cat) { // testeamos si a es un gato   
    System.out.println("¡a es un gato!");   
    System.out.println("Podemos hacer downcasting con tranquilidad");  
    Cat c2 = (Cat)a;   
} 
```


Otra cosa que debes tener en cuenta es que el downcasting no siempre es posible. Por ejemplo, si creas un objeto Mamifero no puedes hacer downcasting a Dog o Cat, porque ambos derivan de Mamifero y podría ser cualquier a de las dos cosas: 

```java
Mamifero m = new Mamifero();   
Cat c = (Cat) m; // Error
```

Este código compila, pero lanzará un error de ejecución del tipo de: `java.lang.ClassCastException: Mamifero cannot be cast to Cat`.

La idea principal que subyace al casting es sencilla: **cada cosa es lo que es**. Por ejemplo, puedes preguntarte: ¿un gato es un mamífero? La respuesta es sí, así que puedes convertir un gato en un mamífero. Y si te preguntas: ¿un mamífero es un gato? La respuesta es que no, no siempre lo es. Así que no puedes convertirlo. Fácil, ¿no? 

Tranquilidad. Veremos más cosas sobre este operador en siguientes apartados.


# 10. Acceso a la superclase

Para acceder a los métodos de una superclase se utiliza la palabra reservada **`super`**. Esta palabra está disponible en cualquier método, excepto en los estáticos. 

`super`, como `this`, es ***una referencia al objeto actual***. Lo que diferencia a `super` de `this` es que ejecutará las versiones de los métodos de la superclase en lugar de los de la clase actual. 

Con `super`, además, se puede acceder a los miembros `protected` de la superclase, pero no a los `private`. Veámoslo con un ejemplo: 

```java
class Vehiculo {   
    protected String marca;   
    public void setMarca(String m) { marca = m; }   
    public String getMarca() { return marca; }   
    public void info() {   
        System.out.println("Soy un vehículo de la marca " + marca);  
    }   
} 

class Bicicleta extends Vehiculo {  
    private int tamRueda; // Tamaño de rueda
    protected String marca;   
    public setMarca(String m1, String m²) {   
        super.marca = m1;   
        this.marca = m2;   
    }   
    public void setTamRueda(double t) { tamRueda = c; }   
    public int getTamRueda() { return tamRueda; }   
    public void info() {   
        super.info();   
        System.out.println(  
            "Soy una bicicleta de marca "  
            + marca  
            + " y tamaño de rueda "  
            + tamRueda  
            + " pulgadas");  
    }   
}
```



En este código, la clase `Bicicleta` deriva de `Vehículo`, pero hemos redefinido el atributo marca y el método `setMarca()`. Observa cómo este método accede al atributo de la clase madre y de la clase actual.  

Ahora invoquemos unos cuantos métodos, a ver qué pasa: 

```java
Bicicleta b = new Bicicleta();   
b.setMarca("BH", "Easymotion");   
b.setTamRueda(28);   
b.info(); 
```

Lo que obtendremos por la pantalla será: 

```
Soy un vehículo de marca BH.   
Soy una bicicleta de marca Easymotion y de tamaño de rueda 28 pulgadas. 
```

Los motivos por los que hemos obtenido esta salida por consola son estos: 

* Primero, el método `setMarca()` estableció el valor de la marca de la superclase en "BH" y el de la clase actual en "Easymotion" 

* Después, el método `info()` invocó en primer lugar al método `info()` de su superclase, que dio lugar a la primera línea ("Soy un vehículo de marca BH"), y después el método imprimió la segunda línea. 

Esta misma forma de proceder puede aplicarse a los constructores. Así, si creamos un constructor para `Vehículo` capaz de recibir la marca, y otro para `Bicicleta` que reciba los nombres de las marcas de la clase madre y la suya propia, podríamos hacer esto: 

```java
class Vehiculo {   
    protected String marca;   
    Vehiculo(String m) { marca = m; }   
    ...   
}   
class Bicicleta {   
    Bicicleta(String m1, String m2) {   
        super(m1);   
        this.marca = m2;   
    }   
    ...   
}
```

Observa como el constructor de `Bicicleta` invoca al constructor de su clase madre con la expresión `super()`. En este caso, `super()` es un método (el constructor de la clase madre) 


# 11. Declaración específica y genérica


## 11.1. Específica

Llegados a este punto hemos de tener claro que podemos ver una clase como un **tipo de dato**. Piénsalo así: una variable se declara indicando su **tipo** y el **identificador** o nombre de la variable. 

```java
int numero = 0;
Circulo c = new Circulo(2);
Rectangulo r = new Rectangulo(4, 7);
```

Por tanto, en el ejemplo anterior, los tipos de datos de las variables `numero`, `c` y `r` son respectivamente `int`, `Circulo` y `Rectangulo`.

Las declaraciones de `c` y `r` son **específicas** ya que para instanciar un objeto de tipo `Circulo` definimos éste como **tipo de la variable** y luego indicamos el **tipo de objeto** también como un `Circulo`:

```java
Circulo c = new Circulo(2);
```

Nada nuevo bajo el sol...

Esto nos permite usar con **`c`** todas las funcionalidades o métodos de un `Circulo` y los heredados de `FiguraGeometrica`.

## 11.2. Genérica

Aunque queda claro cómo definir cualquier objeto, en la herencia pasa algo peculiar. De la misma forma que entre los conocidos de tu familia pueden referirse a ti como “la hija de Pepa” o “Pepa Junior”, en lugar de “Juanita”, en el caso de la herencia pasa algo similar.

Vamos a definir objetos `Circulo` y `Rectangulo` de la siguiente manera:

```java
FiguraGeometrica c = new Circulo(2);  
FiguraGeometrica r = new Rectangulo(4, 7);
```

¡Oh! El compilador no se queja... ¿qué está pasando aquí? Muy sencillo. Como `Circulo` y `Rectangulo` son hijos de `FiguraGeometrica`, pueden declararse con este tipo.

Podemos definir objetos indicando como **tipo de la variable** su superclase (`FiguraGeometrica`), para luego especificar el **tipo de objeto** que realmente son.

Esto se conoce como **declaración genérica** de un objeto. De esta forma estamos tratando a un objeto específico (por ejemplo el `Circulo`) como si fuera uno más genérico (su superclase). Aunque sea un `Circulo`, queremos tratarlo como una `FiguraGeometrica`. Esto afecta a la visibilidad de los métodos de ese objeto. Sólo **podemos acceder a los métodos definidos en `FiguraGeometrica`** salvo que estén sobrescritos en `Circulo`, en cuyo caso se ejecutarán estos últimos.

Esto nos permite tratar **objetos diferentes de la misma manera**:

```java
public class Main {  
   public static void main(String[] args) {  
       Circulo c = new Circulo(2);  
       Rectangulo r = new Rectangulo(4, 7);

       c.setColor("azul");  
       r.setColor("verde");

       mostrarColor(c);  
       mostrarColor(r);  
   }

   public static void mostrarColor(FiguraGeometrica f) {  
       System.out.println("Color de la figura: " + f.getColor());  
   }  
}
```

El método `mostrarColor` se declara de forma genérica el parámetro `f` de tipo `FiguraGeometrica`. Con esto nos permite introducir cualquier objeto que la extienda. 

> [!example] 💡 Prueba lo siguiente 💡 
> Sobreescribe el método `setColor` en las clases `Circulo` y `Rectangulo` para que al color introducido como argumento se le concatene el texto " (Circulo)" y " (Rectangulo)" respectivamente para asignarlo a la propiedad color. Después vuelve a ejecutar el código anterior y verás cómo cambia el resultado.

¡Pero la cosa no acaba aquí! Porque podemos hacer **algo parecido con los interfaces**.

Retomemos el ejemplo del apartado de [[1DAM_Programación/Unidad 04/7. Interfaces\|Interfaces]]:

```java
public interface ShapeCalculable {  
    public double area();  
    public double perimetro();  
}
```

Y supongamos que creamos la siguiente clase que lo implementa:  

```java
public class Cuadrado implements ShapeCalculable {  
    private double lado;

    public Cuadrado(double lado) {  
        this.lado = lado;  
    }

    @Override  
    public double area() {  
        return lado * lado;  
    }

    @Override  
    public double perimetro() {  
        return lado * 4;  
    }

    public double quienSoy() {  
        return "¡Soy un círculo!";  
    }  
}
```

Podemos declarar objetos de tipo `ShapeCalculable`:

```java
ShapeCalculable cuadrado = new Cuadrado(3);  
System.out.println("Área de cuadrado: " + cuadrado.area());  
System.out.println("Perímetro de cuadrado: " + cuadrado.perimetro());
```

Y ahora la pregunta es: ¿se pueden instanciar objetos cuyo tipo sea un interfaz? Obviamente si. Lo que realmente estamos haciendo es decir que **se crea un objeto específico** (`Cuadrado`) **que implementa ese interfaz** (`ShapeCalculable`).

Pero esta forma de declarar un objeto tiene sus cosas... al definir el objeto cuadrado con el tipo `ShapeCalculable`, **limitamos su funcionalidad** a la de dicho interfaz. Es decir, sólo podrá usar los métodos declarados en el interfaz. Ni uno más...

Así, retomando el ejemplo del cuadrado, el IDE nos da un error de compilación si intentamos ejecutar esta línea:

```java
System.out.println(cuadrado.quienSoy());  // ❌ Error de compilación
```

Ya que `quienSoy()` no es un método declarado en el interfaz `ShapeCalculable`.



# 12. ¿De dónde sale este objeto?

Crear o instanciar objetos no es complicado y se puede hacer de varias formas, como ya hemos visto. Y la forma de declararlos determina cómo podemos usarlos.

Al hacer una declaración genérica ganamos flexibilidad a la hora de usar las mismas funcionalidades para distintos de objetos. Observa el método `printDetalles`:

```java
public class Main {
    public static void main(String[] args) {  
        Circulo c = new Circulo(2);  
        Rectangulo r = new Rectangulo(4, 7);

        c.setColor("azul");  
        r.setColor("verde");

        printDetalles(c);  
        printDetalles(r);  
    }

    public static void printDetalles(FiguraGeometrica f) {  
        System.out.println("Color: " + f.getColor());  
        System.out.println("¿Tiene borde? " + f.getBorde());  
        System.out.println("Área: " + f.area());  
        System.out.println("Perímetro: " + f.perimetro());  
    }
}
```

Un mismo método puede ejecutarse para diferentes objetos (`Circulo` y `Rectangulo`) ya que ambos heredan de `FiguraGeometrica` (aunque se hayan declarado de forma específica).

Pero si en algún momento se necesita identificar el tipo específico, ¿cómo podemos averiguarlo...?

## 12.1. instanceof

Este operador se utiliza para verificar si un objeto es una instancia de una clase específica o una subclase de esta. Se expresa de la siguiente manera:

```
objeto1 instanceof objeto2
```

Devuelve un valor booleano indicando si objeto1 es una instancia de objeto2. El resultado será true cuando:

1. `objeto1` sea una instancia específica de `objeto2`.  
  Por ejemplo:

  ```java
  Persona persona1 = new Persona();
  persona1 instanceof Persona;  // devuelve true
  ```

2. `objeto1` sea una instancia de una subclase de `objeto2`.  
  Retomando el ejemplo anterior:
  ```java
  // r es un objeto Rectangulo
  Rectangulo r = new Rectangulo(4, 7);
  r instanceof FiguraGeometrica;  // true, porque r es un objeto Rectangulo
  persona1 instanceof FiguraGeometrica;  // false
  ```
   
3. `objeto1` sea una instancia de un objeto que implementa el interfaz `objeto2`.
  Para entenderlo mejor vamos a hacer más preciso el método del ejemplo anterior, de forma que pueda identificar de qué figura se trata en cada caso:
  ```java
  public class Main {  
      public static void main(String[] args) {  
          Circulo c = new Circulo(2);  
          Rectangulo r = new Rectangulo(4, 7);

          c.setColor("azul");  
          r.setColor("verde");

          mostrarColor(c);
          mostrarColor(r);
          mostrarColor(null);  
      }

      public static void mostrarColor(FiguraGeometrica f) {  
          if (esCirculo(f))  
              System.out.println("Color del círculo: " + f.getColor());  
          else if (esRectangulo(f))  
              System.out.println("Color del rectángulo: " + f.getColor());  
          else  
              System.out.println("Figura no reconocida!");  
      }

      public static boolean esCirculo(FiguraGeometrica f) {  
          return (f instanceof Circulo);  
      }

      public static boolean esRectangulo(FiguraGeometrica f) {  
          return (f instanceof Rectangulo);  
      }
  }
  ```

Al ejecutar este código se imprimirá lo siguiente por consola:

```
Color del círculo: azul  
Color del rectángulo: verde  
Figura no reconocida!
```

¿Qué ha ocurrido con la última línea? Que el operador `instanceof` devuelve `false` si el objeto con el que comparamos es nulo, **ya que null** no es un objeto, **no es una instancia de nada**.

Volvamos ahora al tercer punto de los tres anteriores, donde se indica que también podemos usar `instanceof` para comprobar  si un objeto **implementa una interfaz determinada**:  

```java
Cuadrado cuadrado = new Cuadrado(3);  
cuadrado instanceof ShapeCalculable;  // true
```

Recordemos que la clase `Cuadrado` implementa la interfaz `ShapeCalculable`.

## 12.2. getClass()

Ya hemos vista que `instanceof` nos permite ver de dónde sale un objeto, aunque la información no es exacta ya que puede decir que un objeto puede ser instancia de una clase, una superclase y un interfaz al mismo tiempo.

Si queremos saber solamente la clase específica de la que viene, usaremos el método **`getClass()`**, que compara las clases de forma estricta. Para comparar esta clase específica con otra:

```java
cuadrado.getClass().equals(Cuadrado.class)
```

Donde `.class` obtiene el objeto `Class` correspondiente.

Esta comparación devuelve `true` sólo si el objeto cuadrado es de la clase en concreto (`Cuadrado`), ignorando la herencia o la implementación de interfaces. De esta forma garantizamos de dónde viene.

Tomando los objetos de los ejemplos anteriores, si ejecutamos este código:

```java
System.out.println(cuadrado.getClass().equals(ShapeCalculable.class));  
System.out.println(r.getClass().equals(FiguraGeometrica.class));  
System.out.println(r.getClass().equals(Rectangulo.class));
```

Devolverá:  

```
false  // cuadrado implementa ShapeCalculable, pero es un Cuadrado  
false  // r hereda de FiguraGeometrica, pero es un Rectangulo...  
true   // ...como se puede ver aquí
```

Del objeto `Class` podemos usar el método `getSimpleName()` para obtener un `String` con el nombre de la clase. Así, el ejemplo del apartado anterior podríamos hacerlo de esta otra forma:

```java
public class Main {
    public static void main(String[] args) {  
        Circulo c = new Circulo(2);  
        Rectangulo r = new Rectangulo(4, 7);

        c.setColor("azul");  
        r.setColor("verde");

        mostrarColor(c);  
        mostrarColor(r);  
        mostrarColor(null);  
    }

    public static void mostrarColor(FiguraGeometrica f) {  
        switch (f.getClass().getSimpleName()) {  
            case "Circulo":  
                System.out.print("Color del círculo: " + f.getColor());  
                break;  
            case "Rectangulo":  
                System.out.print("Color del rectángulo: " + f.getColor());  
                break;  
            default:  
                System.out.print("Figura no reconocida!");  
        }  
    }  
}
```



# 13. Herencia vs. Interfaces


La elección entre **usar herencia o interfaces** depende de si se busca reutilizar código o definir un contrato de comportamiento. La herencia modela una relación "es un" (*is-a*), que implica el asumir propiedades y métodos de la superclase, mientras que los interfaces definen una capacidad "puede hacer" (*can-do*).

## 13.1. Herencia

La herencia se utiliza cuando hay una relación estrecha entre clases y se quiere evitar repetir el mismo código (propiedades y métodos) de la implementación de una clase madre en varias clases.

Esto permite la **reutilización de código** ya que las subclases, al heredar miembros de la superclase, no tienen que volver a implementarlos. Así, si la lógica en la superclase (común para todas las subclases) sufre cambios, éstos se reflejan automáticamente en todas las subclases.

Además, con la herencia se puede definir de forma clara una **estructura jerárquica**.

Java permite solamente la **herencia simple**. La herencia múltiple (heredar de varias clases) no está permitida. Aunque esto no tiene porqué ser un problema.

Lo que sí puede serlo es el **acoplamiento fuerte** que conlleva. Esto significa que las subclases dependen directamente de la implementación de la superclase. Si la superclase cambia, puede romper las subclases. Si la superclase se rompe, automáticamente las subclases dejan de funcionar.

Esta rigidez puede ser un problema a medio-largo plazo, ya que cuando un desarrollo evoluciona en el tiempo, se hace cada vez más complicado cambiar la estructura jerárquica de una herencia. 

## 13.2. Interfaces

Los **interfaces** se utilizan para definir un **contrato de comportamiento** que las clases pueden implementar incluso aunque no tengan **nada en común entre ellas**. En otras palabras, se comprometen a implementar (cada una a su manera) determinados métodos. Además, a diferencia de la herencia, una clase **puede implementar varias interfaces** (algo parecido a una especie de herencia múltiple).

¿Y para qué hacemos esto? Para resolver el problema del acoplamiento que provoca la herencia ya que las clases no necesitan conocer la implementación de las otras, solo los métodos que **deben tener implementados**.

Veamos un caso de acoplamiento fuerte en este ejemplo[^1] de un sistema de notificaciones donde la clase principal está fuertemente acoplada a una clase específica de `Email`. 

```java
// Clase de bajo nivel (detalle)
class ServicioEmail {
    void enviarEmail(String msj) {   
        System.out.println("Email: " + msj);   
    }  
}

// Clase de alto nivel (lógica de negocio)
class Notificador {  
    // Este es el problema: Notificador depende directamente de ServicioEmail
    private ServicioEmail email = new ServicioEmail();

    void avisar(String msj) {  
        email.enviarEmail(msj);  
    }  
}
```

Si mañana queremos enviar SMS o notificaciones Push, tenemos que tocar la clase `Notificador` para añadir esa nueva funcionalidad. Estas clases están **fuertemente acopladas** porque `Notificador` **depende** de la implementación del aviso. Esto se conoce como **dependencia** y es característica esencial del acoplamiento fuerte.

Para solucionarlo introducimos una interfaz entre ambas clases (servicio de mensajes y `Notificador`):

```java
interface Mensajero {  
    void enviar(String msj);  
}

class ServicioEmail implements Mensajero {  
    @Override  
    public void enviar(String msj) {   
        System.out.println("Enviando Email: " + msj);   
    }  
}

class ServicioSMS implements Mensajero {  
    @Override  
    public void enviar(String msj) {   
        System.out.println("Enviando SMS: " + msj);   
    }  
}
```

Y ahora, el módulo de alto nivel no es esclavo de una funcionalidad concreta:  

```java
class Notificador {
    private Mensajero mensajero;

    // Inyección de dependencia: el mensajero viene de fuera
    public Notificador(Mensajero mensajero) {
        this.mensajero = mensajero;
    }

    void avisar(String msj) {
        mensajero.enviar(msj);
    }  
}
```

Ahora `Notificador` no sabe (ni le importa) cómo se envía el mensaje, solo sabe que existe un "canal de comunicación" que tiene la funcionalidad de **enviar** un mensaje.

Así podemos cambiar de `Email` a `SMS` (o WhatsApp o cualquier otro medio de comunicación) **sin tocar una sola línea de la lógica de `Notificador`**.

Además hace que el código sea **fácilmente *testeable*** porque en los tests unitarios podemos pasarle un **mock** o simulador de mensajero (que simplemente haga un System.out.println) para probar el Notificador sin enviar correos reales.

> [!info] ℹ️ Nota ℹ️ 
> Esto de los tests se estudia en profundidad en otros módulos, aunque puedes ver algo en la [[1DAM_Programación/Unidades/Unidad 2 - Estructuras de control. Calidad del software\|Unidad 2]], en el apartado de [[1DAM_Programación/Unidad 02/8. Pruebas\|Pruebas]]. Así que es buena idea que vayas aprendiendo a usarlos.

Los interfaces, como hemos podido comprobar, son un claro y significativo ejemplo de **polimorfismo** ya que podemos **tratar de la misma manera a objetos diferentes** que implementan la misma interfaz. 

[^1]:  Ejemplo generado con [Gemini](https://gemini.google.com/).


# 14. Clases anidadas


Para terminar este capítulo, hagamos un breve inciso sobre las **clases anidadas**.

Las clases pueden anidarse, es decir, **pueden definirse unas dentro de otras**.

```java
class Externa {  
    ...  
    class Interna {  
        ...  
    }  
}
```

La clase interna es un **miembro de la clase externa** y, como tal, tendrá acceso a todos sus atributos y métodos, incluso a los privados. Y, como es lógico, podrá ser a su vez `private`, `protected` o `public`.

La clase anidada también puede ser estática o no. **Si es estática no necesita instanciarse**.

La instanciación de una clase anidada necesita la instanciación previa de la clase externa. Por ejemplo:

```java
Externa e = new Externa();  
Interna i = e.new Interna();

```

La anidación de clases, aunque a veces es apropiada, puede dar lugar a situaciones confusas para el programador. **Solo deberían anidarse las clases cuando esté muy claro que esa estructura responde a la lógica del problema** y que la solución obtenida es la más simple posible. Esto sucede, por ejemplo, en clases que van a usarse en un único lugar de todo el sistema.

Las **propiedades de una clase** permiten definir el estado de los objetos instanciados a partir de dicha clase. Esas propiedades pueden ser de cualquier tipo de dato, ya sea **primitivo** (`int`, `boolean`, `double`, etc.) o una **clase** (`String`, `File`, alguna de las clases definidas por nosotros mismos...).

Es lógico pensar que si la clase que define a una o varias de las propiedades de la clase no se van a usar fuera de ella, no tiene sentido crear un nuevo fichero para ella. Por tanto, el lugar donde **definir dicha clase es dentro otra clase**:

```java
class Externa {   
    ...   
    class Interna {   
        ...   
    }   
}
```

De esta forma, la clase interna o contenida es un **miembro** de la clase externa o contenedora y, como tal, tendrá acceso a todos sus atributos y métodos, incluso a los privados. Y como miembro que es, podrá ser a su vez `private`, `protected` o `public`. 

A estas clases internas se les conocen como **clases anidadas**. De esta forma se pueden agrupar clases de forma lógica. El motivo por el que se anidan dentro de otras clases o bloques de código es porque **se usan en un solo lugar**. Así se hace uso de la **encapsulación** y favorece la **legibilidad** del código.

Al estar definidas dentro de otras clases, tienen **acceso a los miembros** de esa clase contenedora. De esta forma se puede crear el tipo de dato que se necesite para un atributo concreto de nuestra clase contenedora. 

Ejemplo:

```java
public class Motor {  
    private int cilindros;

    public Motor(int cilindros) {  
        this.cilindros = cilindros;  
    }

    public class Bujia {  
        public void encender() {  
            System.out.println(  
                "Bujía encendiendo motor de "  
                + cilindros  
                + " cilindros.");  
        }  
    }  
    public Bujia crearBujia() {  
        return new Bujia();  
    }  
}  
```

```java
public class Main {  
    public static void main(String[] args) {  
        Motor motor = new Motor(4);  
        Motor.Bujia bujia = motor.crearBujia();  
        bujia.encender();  
    }  
}
```

En este ejemplo, **`Bujia`** es una clase interna de **`Motor`**. Tiene acceso al atributo **`cilindros`** de la clase **`Motor`** ya que la propiedad **`cilindros`** se ha declarado en la clase contenedora y, por tanto, puede ser usada en toda la clase.

En el siguiente ejemplo se define la clase **`Biblioteca`** con la clase interna **`Libro`** con los atributos **`título`** y **`autor`**, y un método para mostrar la información del libro:

```java
public class Biblioteca {  
    public class Libro {  
        private String titulo;  
        private String autor;

        public Libro(String titulo, String autor) {  
            this.titulo = titulo;  
            this.autor = autor;  
        }

        public void mostrarInformacion() {  
            System.out.println("Título: " + titulo);  
            System.out.println("Autor: " + autor);  
        }  
    }

    public Libro crearLibro(String titulo, String autor) {  
        return new Libro(titulo, autor);  
    }  


    public static void main(String[] args) {  
        Biblioteca biblioteca = new Biblioteca();  
        Biblioteca.Libro libro = biblioteca.crearLibro(  
            "Cien años de soledad",  
            "Gabriel García Márquez");  
        libro.mostrarInformacion();  
    }  
}
```

Obviamente, estas clases internas **no pueden ser clases estáticas** ya que hacen **referencia a miembros de instancia** (propiedades o métodos) de la clase contenedora.

Salvando eso, una clase interna podría perfectamente ser estática. Esto es, que no sería necesario instanciarla

Podemos encontrar distintos tipos de de clases anidadas:

1. **Clases internas (*inner classes*):** no son estáticas y tienen acceso a los miembros de la clase externa.

2. **Clases estáticas anidadas (*static nested classes*):** son estáticas y, por tanto, no tienen acceso directo a los miembros de la clase en la que se encuentran.

3. **Clases locales (*local classes*):** se definen dentro de un bloque de código, como un método.

4. **Clases anónimas (*anonymous classes*):** clases locales sin nombre, útiles para crear implementaciones concisas de interfaces o clases abstractas.

La clase anidada también puede ser estática o no. Si es estática no necesita instanciarse. **La instanciación de una clase anidada necesita la previa instanciación de la clase externa**. Por ejemplo: 

```java
Externa e = new Externa();   
Interna i = e.new Interna(); 
```

La anidación de clases, aunque a veces es apropiada, puede dar lugar a situaciones confusas para el programador. Solo deberían anidarse las clases cuando esté muy claro que esa estructura responde a la lógica del problema y que la solución obtenida es la más simple posible. Esto sucede, por ejemplo, en clases que van a usarse en un único lugar de todo el sistema.

