---
{"dg-publish":true,"dg-permalink":"/apuntes/1-dam-ed/unidad-02-entornos-de-desarrollo/","permalink":"/apuntes/1-dam-ed/unidad-02-entornos-de-desarrollo/","dg-note-properties":{"unidad":"[[Asignaturas/1DAM_ED/Unidades/Unidad 02/Unidad 02 - Entornos de desarrollo]]","modulo":"[[Módulos/Entornos de desarrollo]]","libro":"[[Libros/Entornos de desarrollo (1º DAM, 1º DAW)]]"}}
---


```table-of-contents
```

---

# 1. El IDE

Los primeros entornos de desarrollo integrados nacieron a principios de los años 70, y se popularizaron en la década de los 90. Tienen el objetivo de ganar fiabilidad y tiempo en los proyectos de software. Proporcionan al programador una serie de componentes con la misma interfaz gráfica, con la consiguiente comodidad, aumento de eficiencia y reducción de tiempo de codificación.

Normalmente, un IDE está dedicado a un determinado lenguaje de programación. No obstante, las últimas versiones de los IDE tienden a ser compatibles con varios lenguajes (por ejemplo: [Eclipse](https://eclipseide.org/), [NetBeans](https://netbeans.apache.org/front/main/index.html), Microsoft Visual Studio, [Visual Studio Code](https://code.visualstudio.com/), etc.) mediante la instalación de plugins adicionales.

En este tema, nuestro interés se centra en conocer los entornos de desarrollo, los tipos, en función de su licencia y del lenguaje de programación hacia el cual están enfocados.

## 1.1. Evolución histórica

En las décadas de utilización de la tarjeta perforada como sistema de almacenamiento el concepto de **Entorno de Desarrollo Integrado** sencillamente no tenía sentido. Los programas estaban escritos con diagramas de flujo y entraban al sistema a través de las **tarjetas perforadas**. Los programas indicaban directamente las operaciones a realizar.

![](https://upload.wikimedia.org/wikipedia/commons/d/d8/IBM1130CopyCard.agr.jpg)
> Tarjeta perforada binaria
> Fuente: https://es.wikipedia.org/wiki/Tarjeta_perforada

Posteriormente, con la evolución de la tecnología y de los lenguajes de programación, eran compilados o interpretados por **línea de comandos**.

![](https://upload.wikimedia.org/wikipedia/commons/3/36/Emacs-linux-console.png)
> Fuente: OMPIRE, CC BY-SA 4.0 <https://creativecommons.org/licenses/by-sa/4.0>, via Wikimedia Commons

El primer lenguaje de programación que utilizó un IDE fue el BASIC (que fue el primero en abandonar también las tarjetas perforadas o las cintas de papel). Este primer IDE estaba basado en consola de comandos exclusivamente (normal por otro lado, si tenemos en cuenta que hasta la década de los 90 no entran en el mercado los sistemas operativos con interfaz gráfica). Sin embargo, el uso que hace de la gestión de archivos, compilación y depuración, es perfectamente compatible con los IDE actuales. 

El primer IDE que se hizo público fue [**Maestro**](https://en.wikipedia.org/wiki/Maestro_I). Nació a principios de los 70 y fue instalado por unos 22.000 programadores en todo el mundo. Lideró este campo durante los años 70 y 80\.

El uso de IDE se afianza en los 90 y hoy en día existen multitud entre los que destacamos:

| Entorno de desarrollo | Lenguajes que soporta | Tipo de licencia |
| :---: | ----- | ----- |
| NetBeans | C/C++, Java, JavaScript, PHP, Python.  | De uso público. |
| Eclipse | Ada, C/C++, Java, JavaScript, PHP.  | De uso público. |
| VS Code | Uso principal: JavaScript, TypeScript y Node.js Compatibilidad: C++, C\#, Java, Python, Go, .NET | De uso público. |
| Microsoft VS | Basic, C/C++, C\#.  | Propietario. |
| C++ Builder | C/C++.  | Propietario. |
| JBuilder | Java.  | Propietario. |

> [!note] Nota 
> No hay unos entornos de desarrollo más importantes que otros. La elección del IDE más adecuado dependerá del lenguaje de programación que vayamos a utilizar para la codificación de las aplicaciones y el tipo de licencia con la que queramos trabajar.

## 1.2. Características

> [!info] 
> Debido a la naturaleza cambiante de estos productos, algunos de los datos indicados pueden estar desactualizados.

* **Licencia**: existen IDEs comerciales (p.ej: Jbuilder, Visual Studio...) y otros libres u open source (Eclipse, NetBeans...)

* **Plataforma**: hay IDEs multiplataforma, es decir, funcionan en distintos sistemas (Windows, Linux y Mac, etc.). NetBeans, Visual Studio Code o IntelliJ IDEA son algunos de ellos.
  Otros, en cambio y siendo una minoría, se limitan a un solo sistema. Es el caso de:
  * [Visual Studio](https://visualstudio.microsoft.com/es/) de Microsoft, que corre solamente en Windows
  * [Gambas](https://gambaswiki.org/website/en/main.html), pensado solo para  Linux.

* **Programación visual**: los IDEs que permiten programación visual están diseñados para generar aplicaciones con interfaz gráfico de usuario (GUI). Otros IDEs no permiten programación visual, aunque también se pueden generar aplicaciones GUI programando el interfaz manualmente (usando las funciones del API correspondiente). Esto último es mucho más lento, pero también más flexible y eficiente.

* **Depurador**: es la herramienta principal de la fase de pruebas. Tiene diferentes funciones que ayudan a localizar errores de ejecución en el código fuente. Más adelante hablaremos de estas funciones.

* **Autocompletar**: es una función que facilita la introducción de código fuente. Completa los nombres de métodos, atributos, variables, subprogramas, etc, en cuanto hemos tecleado las primeras letras.

* **Navegador de clases**: un browser que permite navegar por el árbol de clases para acceder rápidamente al código de cualquiera de ellas.

* **Soporte multilenguaje**: muchos IDEs están diseñados para trabajar con un único lenguaje (p.ej: Gambas o Visual Basic trabajan en Basic), pero otros pueden compilar múltiples lenguajes (p.ej: NetBeans o Eclipse). En ocasiones, es necesario instalar plugins o módulos adicionales para extender la capacidad multilenguaje.

* **Encadenamiento de herramientas**: el proceso de generación de un programa ejecutable suele siempre seguir los mismos pasos (luego los veremos en detalle: edición, compilación, montaje, depuración, ejecución). Algunos programas pueden necesitar más pasos (por ejemplo, edición de sonidos, modelado 3D, combinación de estos recursos con el programa final, etc). Pues bien, los IDE proporcionan mecanismos para encadenar herramientas, pero no todos permiten cadenas de la misma longitud ni complejidad, es decir, no todos disponen de las mismas herramientas.

* **Análisis de rendimiento (*profiling*)**: el profiler es una herramienta que realiza pruebas de rendimiento del programa que estamos ejecutando desde el IDE. Sirve para depurar el programa, pues detecta posibles errores al indicarnos, por ejemplo, si un subprograma está tardando demasiado en responder o si una estructura de datos ha crecido más de lo esperado.

* **Cobertura de código**: como la anterior, es una herramienta para la fase de pruebas. Nos indica qué parte del código fuente estamos probando y qué parte no, de modo que podamos diseñar nuevos juegos de pruebas si aún nos queda alguna parte del programa por probar.

* **Refactorización**: es otra técnica asociada a las pruebas, que permite reorganizar el código fuente sin alterar su funcionamiento. Se utiliza cuando se pretende mejorar el rendimiento de parte del código de un programa.

* **Sistema de control de versiones (CVS)**: ayuda a mantener las versiones anteriores conforme se van haciendo modificaciones en el código, permite consultar los cambios que se han hecho y revertirlos en caso necesario, y facilita la coordinación entre varios desarrolladores.

* **Generador automático de documentación**: genera la documentación del programa en algún formato preestablecido y, a menudo, modificable.


# 2. Estructura de un IDE

Los entornos de desarrollo, ya sean libres o propietarios, están formados por una serie de componentes software que determinan sus funciones:

* **Editor de textos**: resalta y colorea la sintaxis, tiene la función de autocompletar código, ayuda y listado de parámetros de funciones y métodos de clase. Inserción automática de paréntesis, corchetes, tabulaciones y espaciados.

* **Compilador/intérprete**: detecta los errores de sintaxis en tiempo real. Características de refactorización.

* **Depurador**: botón de ejecución y traza, puntos de ruptura y seguimiento de variables. Puede incluir la opción de depurar en servidores remotos.

* **Generador automático de herramientas**: para la visualización, creación y manipulación de componentes visuales y todo un arsenal de asistentes y utilidades de gestión y generación código.

* **Interfaz gráfica**: nos brinda la oportunidad de programar en varios lenguajes con un mismo IDE. Es una interfaz agradable que puede acceder a innumerables bibliotecas y plugins, aumentando las opciones de nuestros programas.

## 2.1. Menús típicos de un IDE

Un IDE tiene, a primera vista, es aspecto un editor de texto con una serie de menús adicionales y paneles. Efectivamente, el IDE incluye un editor de texto específico para programación, pero no se debe olvidar que el editor es sólo una de las aplicaciones integradas dentro del IDE.

Para acceder al **compilador** y al **depurador** suele existir un menú al estilo de cualquier programa habitual. Además, existen otros menús, como es lógico, habrá variaciones de un IDE a otro, en general encontraremos estos menús:

* **Menú Archivo**: Contiene las opciones para abrir y guardar los archivos fuente. Generalmente, los IDE pueden trabajar con diferentes tipos de archivo fuente, y están preparados para abrir ese tipo de archivo. Por ejemplo, un IDE para C/C++ abrirá archivos con extensión .c o .cpp, mientras que otro para Java abrirá archivos con extensión .java

* **Menú Edición**: Tiene las opciones típicas para facilitar la edición de programas, incluyendo las utilísimas funciones de Cortar, Copiar y Pegar que seguro que vas a utilizar con frecuencia. Es muy recomendable que te aprendas los atajos de teclado si aún no los dominas.

* **Menú Buscar**: Opciones para buscar textos en el programa, reemplazarlos por otros, ir a cierta línea, etc. A veces, estas opciones se integran en el menú Edición.

* **Menú Ver**: Tiene opciones para acceder a las distintas ventanas de información del depurador, del compilador, del navegador de archivos o del navegador de clases.

* **Menú Proyecto**: Casi todos los IDEs necesitan crear un proyecto para poder generar un ejecutable. Un proyecto es una colección de archivos y recursos, de los cuales sólo algunos de ellos son los archivos fuente generados por el programador. El resto son archivos necesarios para la correcta compilación y ejecución del programa (p.ej: bibliotecas, formularios, etc). Desde el menú Proyectos se pueden crear proyectos y agregar o eliminar los archivos implicados en el mismo, así como cambiar las propiedades del proyecto.

* **Menú Ejecutar**: Desde aquí se accede al compilador. La opción Compilar produce la compilación y el enlace del código fuente activo en ese momento. La opción Reconstruir recompila todos los archivos que formen parte del proyecto (lo cual puede llevar mucho tiempo si el proyecto es grande) y los vuelve a enlazar, mientras que la opción Compilar sólo compila el archivo activo y los que tengan dependencias con él. 

* **Menú Debug (Depurar)**: Desde aquí también se accede al depurador, que por su importancia explicaremos en la siguiente unidad.

* **Menú Herramientas**: Contiene multitud de opciones de configuración del compilador y del entorno de desarrollo. Son muy diferentes en cada IDE.

* **Menús Ventana y Ayuda**: Son similares a los de otras aplicaciones.

## 2.2. Paneles

Los IDE más complejos disponen de varios paneles donde muestran la información más importante. Algunos paneles habituales son:

* El **panel de edición**. Es el más importante, ya que en él se edita el código fuente. El editor suele colorear las diferentes secciones de código (palabras reservadas, números, cadenas, etc), lo cual facilita la lectura y ayuda a localizar errores de sintaxis.

* El **panel de proyectos**. Permite navegar por los diferentes proyectos existentes, abriéndolos, cerrándolos o cambiando sus propiedades con facilidad.

* El **panel de archivos**. Permite navegar rápidamente por los archivos de un proyecto.

* El **navegador de clases**. Permite navegar por las clases y sus métodos con facilidad, accediendo a cualquier parte del código con un simple clic. Lógicamente, sólo existen en los IDEs para lenguajes orientados a objetos.

* El **panel de salida**. Muestra los mensajes de error del compilador o del enlazador. A veces, también puede mostrar la salida del programa en ejecución.

* El **panel de depuración**. Agrupa las diferentes salidas del depurador: contenido de la pila, contenido de los registros, estado de la memoria, contenido de variables, etc.

* El **panel de diseño de pantallas**. Sólo existe en los IDE orientados a la programación visual. En estos casos, también se incluye un panel de propiedades de cada uno de los objetos del GUI. Generalmente, los paneles se pueden mostrar u ocultar a criterio del programador. Es buena idea disponer de un monitor de generosas proporciones para poder distribuir los paneles por la pantalla dejando una generosa superficie al panel de edición.


# 3. Configuración y personalización de entornos de desarrollo

Una vez tenemos instalado nuestro entorno de desarrollo podemos acceder a personalizar su configuración. Al abrir un proyecto existente, o bien crear un nuevo proyecto, seleccionaremos un desplegable con el nombre de “configuración” desde el que podremos personalizar distintas opciones del proyecto.

Podemos personalizar la configuración del entorno sólo para el proyecto actual, o bien para todos los proyectos, presentes y futuros.

Parámetros configurables del entorno:

* Carpeta o carpetas **donde se alojarán todos los archivos** de los proyectos (es importante la determinación de este parámetro, para tener una estructura de archivos ordenada).

* Carpetas de **almacenamiento de paquetes** fuente y paquetes prueba.

* **Administración** de la plataforma del entorno de desarrollo.

* **Opciones de la compilación** de los programas: compilar al grabar, generar información de depuración.

* **Opciones de de la aplicación**: nombre del archivo empaquetado (con extensión .jar, que es la extensión característica de este tipo de archivos empaquetados) y momento del empaquetado.

* Opciones de **generación de documentación** asociada al proyecto.

* **Descripción de los proyectos**, para una mejor localización de los mismos.

* Opciones globales de **formato del editor**: número de espaciados en las sangrías, color de errores de sintaxis, color de etiquetas, opción de autocompletado de código, propuestas de insertar automáticamente código.

* Opciones de **combinación de teclas** en teclado.

* Etc.

# 4. Módulos, plugins y extensiones

En la mayoría de entornos de desarrollo, podemos hacer uso de módulos y plugins para desarrollar aplicaciones. (Por ejemplo [Eclipse Marketplace](https://marketplace.eclipse.org/) o las [extensiones de Visual Studio Code](https://marketplace.visualstudio.com/vscode)).

Un módulo es un componente software que contiene clases de Java que pueden interactuar con las API del entorno de desarrollo y el manifest file, que es un archivo especial que lo identifica como módulo.

Los módulos se pueden construir y desarrollar de forma independiente. Esto posibilita su reutilización y que las aplicaciones puedan ser construidas a través de la inserción de módulos con finalidades concretas. Por esta misma razón, una aplicación puede ser extendida mediante la adición de módulos nuevos que aumentan su funcionalidad.

Existen en la actualidad multitud de módulos y plugins disponibles para todas las versiones de los entornos de desarrollo más utilizados.

## 4.1. Funcionalidades

Los módulos y plugins disponibles para los entornos de desarrollo, en sus distintas versiones, tienen muchas y muy variadas funciones.

Podemos clasificar las distintas categorías de funcionalidades de módulos y plugins en los siguientes grupos:

* **Construcción de código**: facilitan la labor de programación. (Ej. [Copilot VSCode](https://code.visualstudio.com/docs/copilot/overview)).

* **Bases de datos**: ofrecen nuevas funcionalidades para el mantenimiento de las aplicaciones. (Ej. JPA de Eclipse).

* **Depuradores**: hacen más eficiente la depuración de programas (Java Debugger VSCode).

* **Aplicaciones**: añaden nuevas aplicaciones que nos pueden ser útiles. (JavaFX)

* **Edición**: hacen que los editores sean más precisos y más cómodos para el programador.

* **Documentación de aplicaciones**: para generar documentación de los proyectos en la manera deseada.

* **Interfaz gráfica de usuario**: para mejorar la forma de presentación de diversos aspectos del entorno al usuario.

* **Lenguajes de programación y bibliotecas**: para poder programar bajo un Lenguaje de Programación que, en principio, no soporte la plataforma.

* **Refactorización**: hacer pequeños cambios en el código para aumentar su legibilidad, sin alterar su función.

* **Aplicaciones web**: para introducir aplicaciones web integradas en el entorno.

* **Pruebas**: para incorporar utilidades de pruebas al software.


# 5. Herramientas de construcción (Build Tools) y gestión de dependencias

Hoy en día es habitual usar código de terceros en el desarrollo de cualquier software. Las aplicaciones suelen incluir **bibliotecas, frameworks y módulos externos**. A todo eso se le conoce como **dependencias**, ya que el software que las usa depende de ellas para poder funcionar.

Las **herramientas de construcción (*Build Tools*)** son programas que automatizan el proceso de gestionar estas dependencias, compilar el código fuente, ejecutar pruebas y generar el artefacto final (el ejecutable o paquete):

| Función | Descripción | Importancia |
| ----- | ----- | ----- |
| **Gestión de Dependencias** | Descarga, almacena y enlaza automáticamente las bibliotecas externas requeridas (y sus propias dependencias transitivas). | Elimina la necesidad de descargar JARs o módulos manualmente. |
| **Compilación** | Ejecuta el compilador del lenguaje (ej. Java, Kotlin) sobre el código fuente. | Es el paso más básico para convertir el código legible en código máquina. |
| **Ejecución de Tareas** | Automatiza tareas repetitivas como limpieza de directorios, generación de documentación, ejecución de tests y empaquetamiento. | Ahorra tiempo y asegura la consistencia en el flujo de trabajo. |
| **Generación de Artefactos** | Crea el formato final de distribución (ej. archivo `.jar`, `.war` o paquete `npm`). | El resultado es lo que se entrega al cliente o se despliega en un servidor. |

El IDE (Netbeans, IntelliJ, Eclipse, etc.) se integra directamente con estas herramientas, utilizando sus archivos de configuración para entender la estructura del proyecto.

Por ejemplo, en el ecosistema Java podemos encontrarnos con **Maven** o **Gradle**:

| Herramienta | Archivo de Configuración | Características |
| :---: | ----- | ----- |
| **Maven** | `pom.xml` (formato XML) | Se basa en el principio de **Convención sobre Configuración**. Si sigues la estructura de carpetas estándar de Maven, el archivo de configuración es muy simple. |
| **Gradle** | `build.gradle` (Lenguaje Groovy o Kotlin DSL) | Ofrece mayor flexibilidad y velocidad (gracias al *build cache*). Es la opción por defecto para el desarrollo de Android. |

Veamos un ejemplo de Maven, que es el que se usa en clases de Programación. A continuación tenemos un fragmento del fichero **pom.xml** de Maven donde se indica que el proyecto necesita la biblioteca de pruebas **JUnit 5**:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org..."
         xsi:schemaLocation="http://maven...">
   <modelVersion>4.0.0</modelVersion>
   <groupId>com.dam2.unidad02</groupId>
   <artifactId>Programcion_1DAMB_2024_25</artifactId>
   <version>1.0-SNAPSHOT</version>
   <packaging>jar</packaging>
   <properties>
       <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
       <maven.compiler.release>17</maven.compiler.release>
       <exec.mainClass>com.dam2.unidad02.programcion_1damb_2024_25.Programcion_1DAMB_2024_25</exec.mainClass>
   </properties>
    <dependencies>
        <!-- Dependencia que instalará las librerías de JUnit -->
        <dependency>
            <groupId>org.junit.jupiter</groupId>
            <artifactId>junit-jupiter-engine</artifactId>
            <version>5.10.0</version>
            <scope>test</scope>
        </dependency>
    </dependencies>
</project>
```

> [!example] Actividad propuesta 🏗️
> En el IDE que usamos en clase, añade la parte marcada del código anterior y observa qué ocurre en tu IDE.

En el contexto web, concretamente con JavaScript, se encuentran los gestores de dependencias  npm[^1] y Yarn:

| Herramienta | Archivo de Configuración | Características |
| :---: | ----- | ----- |
| **<abbr title="Node Package Manager">npm</abbr>** | `package.json` | Gestor de dependencias estándar para el ecosistema Node.js y, en general, frontend (React, Vue, Angular). |
| **Yarn** | `package.json` (similar a npm) | Creado por Facebook, es una alternativa más rápida a npm en ciertos escenarios, centrándose en la **seguridad** y el **rendimiento**. |

A continuación se muestra un ejemplo que indica a **npm** qué librerías/frameworks y en qué versiones se van a usar en un proyecto cualquiera. En este caso, se indica la versión de librería React y también scripts de tareas para automatizar el desarrollo en un proyecto que han llamado **mi-app-web**:

```json
{  
    "name": "mi-app-web",  
    "version": "1.0.0",  
    "dependencies": {  
      "react": "^18.3.1",  
      "react-dom": "^18.3.1"  
    },  
    "scripts": {  
      "start": "webpack serve --open",  
      "build": "webpack --mode production",  
      "test": "jest"  
    }  
}
```

En este ejemplo, si se ejecuta desde el terminal el comando **`npm run build`** se le dice al *Build Tool* que ejecute el comando **`webpack --mode production`** definido en el script, automatizando el empaquetado final del código.

[^1]:  En la actualidad npm no es seguro debido a los ataques Shai-Hulud ([[Asignaturas/1DAM_ED/Apuntes/Unidad 02/8. Referencias\|Rodríguez Sánchez, 2025]]).

# 6. Otras herramientas

## 6.1. El terminal y los shells

Aunque los IDE (Entornos de Desarrollo Integrados) centralizan casi todas las tareas de codificación, la interfaz de línea de comandos o **CLI** (*Command Line Interface*) sigue siendo una herramienta esencial e indispensable para el flujo de trabajo profesional.

Un conocimiento sólido del terminal permite gestionar proyectos, automatizar tareas, interactuar con herramientas de build (construcción) y diagnosticar problemas del sistema operativo de manera más rápida y eficiente que a través de interfaces gráficas.

### 6.1.1. ¿Qué es el shell?

El **shell** es el programa que actúa como **intérprete de comandos** entre el usuario y el sistema operativo. Cuando abrimos un terminal o línea de comandos (CLI), en realidad estamos **ejecutando una instancia** de un programa Shell.

Históricamente, los shells más comunes han sido [**cmd.exe**](https://es.wikipedia.org/wiki/S%C3%ADmbolo_del_sistema_de_Windows) (Windows) y [**Bash**](https://www.gnu.org/software/bash/) (Unix/Linux). Sin embargo, el desarrollo moderno ha adoptado shells mucho más potentes y versátiles.

| Shell | Sistema Operativo | Características Clave |
| ----- | ----- | ----- |
| [**Bash**](https://www.gnu.org/software/bash/) (*Bourne-Again Shell*) | Linux, macOS | El estándar histórico. Enfocado a texto. Excelente para *scripting* básico y comandos UNIX tradicionales. |
| [**PowerShell Core**](https://github.com/PowerShell/PowerShell) | Windows, Linux, macOS | **Orientado a objetos**. Permite interactuar con la configuración del sistema de forma muy potente, utilizando ***cmdlets*** (comandos orientados a la acción). **Reemplaza al obsoleto cmd.exe**. |
| [**Zsh**](https://www.zsh.org/) (*Z Shell*) | Linux, macOS | Una extensión de Bash que añade autocompletado avanzado, temas, y gestión de historial más eficiente. Popular con el framework [**Oh My Zsh**](https://ohmyz.sh/). |

### 6.1.2. Herramientas CLI de interés

Además del IDE, a la hora de desarrollar software hoy en día se hace necesario el uso de otras herramientas complementarias fundamentales. Veamos algunas de ellas.

#### Git

Git es uno de los **sistemas de control de versiones** más extendidos en el mundo del desarrollo de software.

El control de versiones permite guardar un **historial de todos los cambios** realizados en un proyecto, de modo que se pueden comparar versiones anteriores o restaurar el estado del código en un momento específico. 

En el caso de Git tenemos un sistema de control de versiones **distribuido** donde cada desarrollador tiene una **copia completa del repositorio** local, lo que permite trabajar sin conexión a Internet y hace que el sistema sea más rápido y fiable, ya que **no hay un único punto central de fallo**.

Git facilita el trabajo en paralelo de un equipo de desarrollo gracias a las ramas (*branches*). Cada desarrollador **puede crear sus propias ramas** para implementar nuevas funciones de forma independiente y **luego fusionar los cambios** en la rama principal. Es decir, se pueden crear **distintos flujos de trabajo en un mismo proyecto**, permitiendo aislar en diferentes ramas los cambios que haga cada programador. 

Git usa un **hash** seguro (SHA1) para verificar la integridad de los archivos y el historial de cambios, haciendo que sea muy difícil modificar o corromper datos sin que Git lo detecte. 

Git suele estar integrado en todos o la gran mayoría de IDEs. Aún así, los comandos ejecutados en CLI son necesarios para tareas avanzadas, resolución de conflictos (merges) complejos y personalización.

Aunque veremos esta herramienta en más profundidad en unidades posteriores, aquí adelantamos algunos comandos básicos de Git:

| Comando | Finalidad | Ejemplo Práctico |
| ----- | ----- | ----- |
| git clone | Descargar un repositorio existente. | git clone https://github.com/proyecto/ejemplo.git |
| git status | Ver el estado actual del área de trabajo. | git status |
| git add | Preparar archivos para el *commit*. | git add . (Añade todos los cambios) |
| git commit | Guardar los cambios con un mensaje. | git commit -m "feat: Se añade login de usuario" |
| git push | Subir los *commits* al repositorio remoto. | git push origin main |

> [!example] Actividad propuesta 🏗️
> Desde tu terminal, comprueba si tienes instalado Git. Puedes hacerlo comprobando su versión:
> ```bash
> ~$ git --version
> git version 2.34.1
> ```
> Si la ejecución anterior es correcta, vamos a probar a clonar un repositorio real. Por ejemplo:
> ```bash
> ~$ git clone https://github.com/dgaysae/Programacion_1DAMB_2024_25.git
> ```

#### Peticiones HTTP

Para probar APIs, diagnosticar problemas de red o descargar recursos se pueden usar herramientas como las siguientes:

| Herramienta | Finalidad | Ejemplo Práctico |
| ----- | ----- | ----- |
| **curl** (Client URL) | Realiza peticiones HTTP, HTTPS, FTP, etc. Es la herramienta de facto para probar servicios web. | `curl -X GET https://api.ejemplo.com/usuarios` |
| **wget** | Utilidad no interactiva para descargar archivos desde la web. Más simple que `curl` para descargas directas. | `wget https://ejemplo.com/instalador.exe` |

> [!note] Nota 
> Existen otras herramientas con interfaz gráfico, como [**Postman**](https://www.postman.com/), que pueden resultar muy útiles para realizar estas pruebas.

#### Manipulación de archivos y texto

Estas herramientas son muy importantes a la hora de hacer búsquedas rápidas en ficheros de log extensos, modificar archivos de configuración o filtrar datos.

| Comando | Finalidad | Ejemplo Práctico |
| ----- | ----- | ----- |
| grep | Busca patrones de texto dentro de archivos. | `grep "ERROR" logs/servidor.log` |
| find | Busca archivos y directorios según criterios. | `find . -name "*.java"` (Busca todos los archivos Java en el directorio actual) |
| cat | Muestra el contenido de un archivo en la salida estándar. | `cat README.md` |
| pipe | **Operador de encadenamiento:** permite que la salida de un comando sea la entrada del siguiente. |  |

Estos comandos pueden combinarse para obtener aún más funcionalidad. Esto se conoce como **encadenamiento de comandos**. El siguiente ejemplo muestra cómo listar todos los archivos JavaScript modificados en los últimos 7 días y contarlos (wc):

```bash
# Busca archivos *.js, filtra por tiempo (7 días), y luego cuenta
# las líneas
find . -name "*.js" -mtime -7 | wc -l
```

#### Automatización con *shell scripting*

El verdadero poder del terminal reside en el *shell scripting*. Consiste en **agrupar una secuencia de comandos** en un solo archivo para ejecutar tareas repetitivas o complejas de forma automática.

Se podrían implementar scripts para:

* Automatizar *builds*, limpiando directorios, compilar, y empaquetar una aplicación.

* Despliegues básicos, copiando archivos a un servidor remoto vía SSH.

* Configurar entornos, descargando dependencias y configurando variables de entorno.

* Gestionar logs, filtrando, rotando y archivando ficheros.

A continuación se muestra un ejemplo práctico de shell script usando Bash. Se trata de un script que simula el proceso de preparación de un entorno antes de compilar un proyecto Java.

Puedes implementarlo en tu Linux y ver cómo funciona. Copia el siguiente código y guárdalo en un fichero **`preparar_proyecto.sh`**.

```bash
#!/bin/bash
# --- Script de Preparación de Entorno para Proyecto ---
# 1. Definición de variables
PROJECT_DIR="mi_aplicacion_java"
BUILD_LOG="build.log"
DATE=$(date +"%Y-%m-%d %H:%M:%S")

echo "[$DATE] Iniciando preparación del entorno..."
echo "----------------------------------------"

# 2. Navegar al directorio del proyecto
if [ -d "$PROJECT_DIR" ]; then
    cd $PROJECT_DIR
    echo "[$DATE] Navegando a $PROJECT_DIR..."
else
    echo "[$DATE] Error: El directorio $PROJECT_DIR no existe."
    exit 1
fi

# 3. Limpiar compilaciones antiguas (simulación de 'make clean' o 'gradle clean')
echo "[$DATE] Limpiando archivos temporales y compilaciones previas..."
rm -rf target/classes 2>/dev/null
echo "[$DATE] Limpieza completada."

# 4. Simulación de ejecución de pruebas y compilación
echo "[$DATE] Ejecutando pruebas unitarias y compilando (Simulación)..."
# En un proyecto real, aquí iría: ./gradlew test | tee $BUILD_LOG
# Usamos 'sleep' para simular el tiempo de ejecución
sleep 2

# 5. Verificación de logs y estado
WARNINGS=$(grep -c "WARNING" $BUILD_LOG 2>/dev/null)

if [ $? -eq 0 ] && [ "$WARNINGS" -eq 0 ]; then
    echo "[$DATE] ** PROCESO FINALIZADO CON ÉXITO **"
else
    echo "[$DATE] Advertencia: Se encontraron $WARNINGS advertencias en el proceso."
fi

# Volver al directorio original
cd ..
echo "----------------------------------------"
echo "[$DATE] Preparación completada."
```

Una vez tengas el fichero, sigue los siguientes pasos para su ejecución:

1. Dale permisos de ejecución:
  ```
  chmod +x preparar_proyecto.sh
  ```
  
2. Ejecuta el script desde el terminal:
  ```
  ./preparar_proyecto.sh
  ```

> [!note] Nota 
> No vamos a profundizar en este tema, ya que se ve con más detalle en el módulo de Sistemas Informáticos.

### 6.1.3. Integración y Entrega Continua (CI/CD)

La **integración continua** o **<abbr title="Continuous Integration">CI</abbr>** y la **entrega continua** o **<abbr title="Continuous Deployment">CD</abbr>** conforman el flujo de trabajo habitual hoy en día.

Una vez que el código se ha escrito, depurado en el IDE y se ha confirmado en Git (mediante commit), el siguiente paso es **asegurar que funciona correctamente y puede ser desplegado a los usuarios finales**. Este proceso se gestiona mediante las prácticas de Integración Continua (CI) y Entrega Continua (CD).

El CI/CD es un conjunto de principios y prácticas que automatizan las etapas de build (construcción), pruebas y despliegue del software.

#### Integración Continua (CI)

La Integración Continua es una práctica de desarrollo que requiere que los desarrolladores **integren código en un repositorio compartido** (como Git) de forma **frecuente**, idealmente varias veces al día.

El principal objetivo de la CI es **detectar lo antes posible los problemas de integración** entre las distintas partes desarrolladas por cada programador.

Cada vez que un desarrollador sube sus cambios al repositorio central (hace un **git push**) se activa automáticamente un **pipeline de CI** que realiza los siguientes pasos:

1. **Build (Compilación):** el código fuente se compila y se convierte en un **artefacto ejecutable** (ej. un archivo JAR, un ejecutable binario, o archivos JavaScript empaquetados).

2. **Pruebas unitarias y de integración:** se ejecutan automáticamente **todos los tests** que han escrito los desarrolladores. Si un sólo test falla, el *build* se marca como fallido.

3. **Análisis estático de código (*code linting*):** se revisa el código en busca de malas prácticas, vulnerabilidades de seguridad o incumplimiento de estándares de estilo (ej. con herramientas como [SonarQube](https://www.sonarsource.com/es/products/sonarqube/) o [ESLint](https://eslint.org/) para JavaScript).

Si el pipeline de CI falla, se avisa inmediatamente al desarrollador para que corrija el error **antes de que el código defectuoso se fusione con la rama principal**.

#### Entrega Continua (CD)

La CD extiende la CI, automatizando el proceso de liberación del software después de que el *build* y las pruebas hayan ido bien. Existen dos variantes:

1. *Continuous Delivery* (Entrega continua)  
   Se prepara el código de forma automática para su liberación o *release*, incluyendo el empaquetado y el despliegue a un **entorno de *Staging*** (preproducción/pruebas). Sin embargo, el **paso final a producción requiere una aprobación o acción manual** por parte de un operador o *manager*.

2. *Continuous Deployment* (Despliegue continuo)  
   Este es el **nivel más alto de automatización**. Si el código pasa todas las pruebas automatizadas (CI) y las pruebas adicionales en *Staging* (ej. pruebas de rendimiento), el cambio **se despliega automáticamente a producción, sin intervención humana**.

#### Herramientas de CI/CD más extendidas

Las herramientas de CI/CD son la infraestructura que aloja y ejecuta los *pipelines* de automatización.

| Herramienta | Plataforma | Tipo |
| ----- | ----- | ----- |
| [**GitHub Actions**](https://github.com/features/actions) | [GitHub](https://github.com/) | Moderno, basado en archivos [YAML](https://www.redhat.com/es/topics/automation/what-is-yaml). Muy popular para proyectos Open Source y medianos. |
| [**GitLab CI**](https://docs.gitlab.com/ci/) | [GitLab](https://gitlab.com/) | Muy integrado con el control de versiones, utiliza también [YAML](https://www.redhat.com/es/topics/automation/what-is-yaml). |
| [**Jenkins**](https://www.jenkins.io/) | Servidor Propio | Clásico, muy potente y configurable, ideal para entornos empresariales grandes y personalizados (aunque requiere más mantenimiento). |

Se puede ver un ejemplo de pipeline de Ci en el **[[Asignaturas/1DAM_ED/Apuntes/Unidad 02/9. Anexos#Anexo i. Pipeline sencillo en GitHub Actions\|anexo i]]**.

### 6.1.4. Cloud IDEs y entornos *contenerizados*

#### IDEs en la nube (Cloud IDEs)

Un IDE en la nube es un entorno de desarrollo completo al que se accede **a través de un navegador web**. La máquina real que ejecuta el código, el sistema operativo, las dependencias y el propio IDE, se encuentra en un servidor remoto.

Hay una tendencia en auge en el desarrollo de software: la **estandarización y portabilidad del entorno de trabajo**.

De esta forma se evita el clásico problema de "en mi máquina funciona...".

Para conseguirlo se combinan dos tecnologías: los **IDEs en la nube** y los **contenedores**.

Con un IDE en la nube el entorno tiene una gran disponibilidad ya que se puede abrir sin instalar nada en una máquina. Esto permite a los programadores codificar desde cualquier dispositivo (incluso una tablet) con solo una conexión a Internet. Además el IDE en la nube puede aprovechar la potencia de servidores remotos con mucha más RAM y CPU que el portátil local del desarrollador.

Obviamente, esto garantiza que todos los miembros del equipo trabajarán con la misma versión de los componentes que forman parte del proyecto.

Al abrir el IDE en la nube ya viene con la configuración necesaria para el proyecto.

Algunos ejemplos de estos IDEs son:

* [**GitHub Codespaces**](https://github.com/features/codespaces): está integrado directamente en [GitHub](https://github.com/). Se activa con un click y usa Visual Studio Code (VS Code) en el navegador.

* [**GitPod**](https://gitpod.io/): es similar a la anterior, pero se puede usar con [GitHub](https://github.com/), [GitLab](https://about.gitlab.com/es/) y [Bitbucket](https://bitbucket.org/).

#### Contenerización de entornos (Docker)

La tecnología subyacente que permite la estandarización de los IDEs en la nube (y la CI/CD) son los **contenedores**, siendo [**Docker**](https://www.docker.com/) el más utilizado.

Un contenedor empaqueta el **código de una aplicación** junto con ***todo*** **lo necesario para que se ejecute**: bibliotecas, variables de entorno y el sistema operativo base.

El mayor desafío en equipos es asegurar la **fidelidad del entorno de desarrollo** con el entorno de producción. Si el código funciona perfectamente en el IDE local pero falla al desplegarse, el entorno de desarrollo no es fiable.

El uso de contenedores resuelve esto creando un recinto **aislado** y **portátil**.

Para facilitar la configuración de entornos de desarrollo basados en contenedores, se utiliza un archivo de configuración llamado **`devcontainer.json`**. Este archivo se puede leer desde muchas herramientas como (VS Code, Codespaces, etc.). Se puede consultar un ejemplo en el **[[Asignaturas/1DAM_ED/Apuntes/Unidad 02/9. Anexos#Anexo ii. Ejemplo de fichero `devcontainer.json`\|anexo ii]]**.



# 7. Entornos de desarrollo en la práctica

En los apartados anteriores hemos visto qué es un IDE, cómo se organiza y qué herramientas lo acompañan. En este apartado lo **ponemos en práctica**: vamos a instalar varios entornos, mantenerlos al día, ampliarlos con extensiones y usarlos para generar ejecutables.

Trabajaremos con tres entornos muy extendidos:

| Entorno | Empresa o comunidad | Licencia | Uso en este apartado |
|---|---|---|---|
| **Visual Studio Code** | Microsoft | Gratuito. Su código base (*Code - OSS*) es libre (MIT); la distribución oficial lleva una licencia propietaria de Microsoft | Editor ligero y multilenguaje |
| **Apache NetBeans** | Fundación Apache | **Libre** (Apache 2.0) | IDE para Java con Maven |
| **IntelliJ IDEA** | JetBrains | **Propietario**, con funciones gratuitas y otras de pago (hay licencias educativas gratuitas) | IDE profesional para Java |

> [!NOTE] Libre no es lo mismo que gratuito
> Un programa **libre** permite usar, estudiar, modificar y redistribuir su código. Un programa **propietario** puede ser gratuito, pero su licencia limita lo que se puede hacer con él. VS Code es un buen ejemplo de la diferencia: su código es libre, pero el instalador que descargamos de Microsoft no lo es. Existe una distribución totalmente libre, [VSCodium](https://vscodium.com/).

> [!WARNING] Versiones
> Los nombres de los menús y de las opciones cambian de una versión a otra. Si no encuentras una opción, búscala con el buscador de los ajustes del IDE o consulta su documentación oficial.

## 7.1. Instalar entornos de desarrollo

Antes de instalar un IDE para Java necesitamos el **JDK** (*Java Development Kit*), que incluye el compilador `javac`. Usaremos una versión **LTS** (de soporte extendido), por ejemplo la de [Eclipse Temurin](https://adoptium.net/).

Una vez instalada, abre una terminal (Linux/MaxOS) o el símbolo del sistema (Windows) y ejecuta estos dos comandos:

```bash
java -version
javac -version
```

Si ambos muestran la versión, el JDK está instalado y en el `PATH`.

### 7.1.1. Formas de instalación

Los IDE se pueden instalar de varias formas. Conviene conocerlas, porque cada una cambia la manera de **actualizar** el programa (ver [[Asignaturas/1DAM_ED/Apuntes/Unidad 02-Entornos de desarrollo#7.2. Configurar las actualizaciones\|#7.2. Configurar las actualizaciones]]):

| Forma | Ejemplo | Quién actualiza el IDE |
|---|---|---|
| **Instalador** descargado de la web oficial | `.exe`, `.dmg`, `.deb`, `.rpm` | El propio IDE, o el gestor de paquetes si es `.deb`/`.rpm` |
| **Gestor de paquetes** del sistema | `zypper`, `apt`, `winget` | El gestor de paquetes |
| **Paquete universal** | Flatpak, Snap | Flatpak o Snap |
| **Gestor del fabricante** | JetBrains Toolbox | La aplicación del fabricante |
| **Versión portable** (archivo comprimido) | `.zip`, `.tar.gz` | Nadie: hay que descargar la nueva versión a mano |

### 7.1.2. Visual Studio Code

1. Descarga el instalador de [code.visualstudio.com](https://code.visualstudio.com/) para tu sistema. En openSUSE, la documentación oficial explica cómo añadir el repositorio de Microsoft e instalarlo con `zypper`.
2. Ábrelo e instala el **Extension Pack for Java** de Microsoft desde la vista de extensiones (`Ctrl+Mayús+X`).
3. Comprueba la instalación creando un archivo `Hola.java` y ejecutándolo con el botón ▷ (*Run*).

### 7.1.3. Apache NetBeans

1. Descarga la última versión de [netbeans.apache.org](https://netbeans.apache.org/front/main/download/). Hay instaladores para Windows, macOS y Linux, y también un archivo `.zip` que no necesita instalación.
2. Durante la instalación, indica la carpeta del JDK si no la detecta sola.
3. Comprueba la instalación con *File → New Project → Java with Maven → Java Application*.

### 7.1.4. IntelliJ IDEA

1. Descarga IntelliJ IDEA de [jetbrains.com/idea](https://www.jetbrains.com/idea/download/), o instala antes **JetBrains Toolbox**, que gestiona la instalación y las actualizaciones de todos los IDE de JetBrains.
2. Al abrirlo por primera vez, acepta la licencia. Si quieres las funciones de pago, puedes solicitar una **licencia educativa** gratuita con el correo del centro.
3. Comprueba la instalación con *New Project → Java*, usando **Maven** como sistema de construcción.

> [!TIP] Instalar varios IDE no es un problema
> Los IDE no interfieren entre sí: cada uno guarda su configuración en su propia carpeta. Lo que comparten es el **JDK**, que se instala una sola vez. Eso sí, cada IDE ocupa espacio y memoria, así que conviene cerrar los que no se estén usando.

## 7.2. Configurar las actualizaciones

Un IDE se actualiza en **dos niveles**: el propio entorno y sus extensiones o *plugins*. Las actualizaciones corrigen errores y fallos de seguridad, pero también pueden cambiar el comportamiento del entorno o romper una extensión. Por eso, en un equipo de trabajo es habitual **controlar cuándo** se actualiza, en lugar de hacerlo siempre de forma automática.

### 7.2.1. Visual Studio Code

En *Archivo → Preferencias → Configuración* (`Ctrl+,`), busca `update`:

| Ajuste | Valores | Qué controla |
|---|---|---|
| `update.mode` | `default`, `start`, `manual`, `none` | Si VS Code busca e instala actualizaciones de forma automática, solo al arrancar, solo cuando se lo pedimos o nunca |
| `extensions.autoUpdate` | Activado, solo las seleccionadas, desactivado | Si las extensiones se actualizan solas |
| `extensions.autoCheckUpdates` | Activado o desactivado | Si comprueba si hay versiones nuevas de las extensiones |

También se pueden editar en el archivo `settings.json`:

```json
{
  "update.mode": "manual",
  "extensions.autoUpdate": false
}
```

> [!NOTE]
> Si VS Code se ha instalado con un gestor de paquetes (`zypper`, Snap…), lo actualiza ese gestor y el ajuste `update.mode` no tiene efecto.

### 7.2.2. Apache NetBeans

1. Abre *Tools → Plugins* y ve a la pestaña ***Settings***.
2. En **Check for updates**, elige la frecuencia (cada inicio, cada día, cada semana… o nunca).
3. En la misma pestaña aparecen los **centros de actualización** (*Update Centers*): las direcciones de donde NetBeans descarga los *plugins*. Se pueden activar, desactivar o añadir otros.
4. En la pestaña ***Updates*** se instalan las actualizaciones pendientes.

### 7.2.3. IntelliJ IDEA

1. Abre *Settings → Appearance & Behavior → System Settings → Updates*.
2. Activa o desactiva la **comprobación automática** de actualizaciones del IDE y de los *plugins*.
3. Elige el **canal** de actualizaciones: estable (*Release*) o de prueba (*Early Access Program*, EAP), con versiones previas que pueden tener errores.

Si se instaló con JetBrains Toolbox, las actualizaciones se configuran desde Toolbox, que permite incluso **volver a una versión anterior** (*rollback*).

## 7.3. Añadir y eliminar módulos y extensiones

En [[Asignaturas/1DAM_ED/Apuntes/Unidad 02/4. Módulos, plugins y extensiones\|4. Módulos, plugins y extensiones]] vimos para qué sirven. Ahora vamos a gestionarlos.

### 7.3.1. Visual Studio Code

| Acción | Cómo |
|---|---|
| **Buscar e instalar** | Vista de extensiones (`Ctrl+Mayús+X`), buscar por nombre y pulsar *Instalar* |
| **Desactivar** | Rueda dentada de la extensión → *Deshabilitar*. Sigue instalada, pero no se carga |
| **Desinstalar** | Rueda dentada → *Desinstalar*. Se borra del equipo |
| **Ver las instaladas** | Filtro `@installed` en el buscador de extensiones |

Desde el terminal también se pueden gestionar, lo que permite **automatizar** la preparación de un equipo:

```bash
code --list-extensions
code --install-extension ms-python.python
code --uninstall-extension ms-python.python
```

### 7.3.2. Apache NetBeans

En *Tools → Plugins*:

- ***Available Plugins***: marcar los *plugins* e instalarlos.
- ***Installed***: marcar uno y pulsar ***Deactivate*** (desactivar) o ***Uninstall*** (desinstalar).

### 7.3.3. IntelliJ IDEA

En *Settings → Plugins*:

- ***Marketplace***: buscar e instalar.
- ***Installed***: desmarcar la casilla de un *plugin* para desactivarlo, o usar su menú para desinstalarlo.

> [!TIP] Desactivar antes que desinstalar
> Si un IDE va lento o falla después de instalar algo, **desactiva** las extensiones sospechosas una a una hasta encontrar la culpable. Así puedes volver a activarla sin tener que reinstalarla ni perder su configuración.

## 7.4. Generar ejecutables de varios lenguajes en un mismo entorno

Un IDE **multilenguaje**, como VS Code, permite trabajar con varios lenguajes en el mismo entorno. Para cada lenguaje hace falta su **extensión** (para editar y depurar) y su **compilador o intérprete** (para ejecutar), que se instalan por separado.

Vamos a generar en VS Code un ejecutable a partir de código en **Java** y otro a partir de código en **C**:

| | Java | C |
|---|---|---|
| Extensión | Extension Pack for Java | C/C++ (Microsoft) |
| Herramienta necesaria | JDK y Maven | Compilador `gcc` |
| Qué se genera | `.jar` (bytecode para la JVM) | Ejecutable nativo del sistema operativo |
| Cómo se genera | `mvn package` | `gcc hola.c -o hola` |
| Cómo se ejecuta | `java -jar target/<proyecto>.jar` | `./hola` |

### 7.4.1. Java con Maven

1. Crea un proyecto con la paleta de comandos (`Ctrl+Mayús+P`) → *Java: Create Java Project* → *Maven*.
2. Escribe un programa sencillo en la clase principal.
3. Abre el terminal integrado (`` Ctrl+` ``) y genera el paquete:

   ```bash
   mvn package
   ```

4. El archivo `.jar` aparece en la carpeta `target/`. Para que `java -jar` sepa qué clase ejecutar, el `pom.xml` debe indicar la **clase principal** en el *manifest* (con el *plugin* `maven-jar-plugin`). Si no, se puede ejecutar con:

   ```bash
   java -cp target/<proyecto>.jar <paquete>.<ClasePrincipal>
   ```

### 7.4.2. C

1. Crea un archivo `hola.c` en otra carpeta del mismo VS Code.
2. Compílalo desde el terminal integrado, o con el botón ▷ de la extensión C/C++, que lanza `gcc` por nosotros:

   ```bash
   gcc hola.c -o hola
   ./hola
   ```

> [!EXAMPLE] Compara los resultados
> El `.jar` funciona en cualquier sistema con una JVM; el ejecutable de C solo en el sistema operativo y el procesador para el que se ha compilado. Es la diferencia entre **código intermedio** y **código nativo** que vimos en la Unidad 01 ([[Asignaturas/1DAM_ED/Apuntes/Unidad 01/10. Codificación#10.5. Máquinas virtuales\|10.5. Máquinas virtuales]]).

## 7.5. Generar ejecutables de un mismo código con varios entornos

Como el proyecto de Java usa **Maven**, su configuración (el `pom.xml`) no depende del IDE. Eso permite abrir **el mismo proyecto** en varios entornos y generar el ejecutable con cualquiera de ellos.

1. Abre en **NetBeans** la carpeta del proyecto creado en VS Code (*File → Open Project*). NetBeans la reconoce como proyecto Maven por el `pom.xml`.
2. Genérala con ***Clean and Build*** (el martillo con la escoba). En la ventana *Output* se ve que NetBeans ejecuta Maven.
3. Ábrelo también en **IntelliJ IDEA** (*File → Open* y elegir el `pom.xml` o la carpeta) y genéralo desde la ventana de herramientas de **Maven**, con *Lifecycle → package*.
4. Ejecuta los tres `.jar` y compara: ¿se comportan igual? ¿Tienen el mismo tamaño?

> [!NOTE] Lo que es del proyecto y lo que es del IDE
> Cada IDE añade al proyecto sus propios archivos de configuración: `.vscode/` (VS Code), `nbactions.xml` (NetBeans) o `.idea/` (IntelliJ). Estos archivos **no deben subirse al repositorio** (se excluyen con `.gitignore`, como veremos en la Unidad 04), para que cada miembro del equipo pueda usar el IDE que prefiera. Lo que se comparte es el código y el `pom.xml`.

> [!TIP] El IDE no es imprescindible
> Los tres IDE generan el `.jar` llamando a Maven. Por eso también se puede generar sin ningún IDE, con `mvn package` desde el terminal. Así es como lo hacen los servidores de **integración continua** (ver [[Asignaturas/1DAM_ED/Apuntes/Unidad 02/6. Otras herramientas#6.1.3. Integración y Entrega Continua (CI/CD)\|6.1.3. Integración y Entrega Continua (CI/CD)]]).

# 8. Referencias

* Java Code Geeks. (2021, 26 mayo). **Java NetBeans IDE Tutorial** \[Vídeo\]. YouTube. [https://www.youtube.com/watch?v=wdpxnKry0ic](https://www.youtube.com/watch?v=wdpxnKry0ic)

* EdTics Academy. (2023, 24 abril). **Introducción a NetBeans IDE para principiantes: Aprender a programar en Java** \[Vídeo\]. YouTube. [https://www.youtube.com/watch?v=SXIOxvxWf7A](https://www.youtube.com/watch?v=SXIOxvxWf7A)

* Rodríguez Sánchez, R. R. S. (2025, 8 octubre). ***Shai‑Hulud: El ataque masivo a npm que sacude la cadena de suministro del software***. S|ngular \- Insights. [https://www.sngular.com/es/insights/417/shai-hulud-el-ataque-masivo-a-npm](https://www.sngular.com/es/insights/417/shai-hulud-el-ataque-masivo-a-npm)

## Depuración

* Charly Cimino. (2023, 16 octubre). **DEBUG 🪲 en Java ☕ con Netbeans👨🏻\_💻 Ejecutá tu CÓDIGO LÍNEA a LÍNEA 🐾** \[Vídeo\]. YouTube. [https://www.youtube.com/watch?v=SMzHetM\_Uj8](https://www.youtube.com/watch?v=SMzHetM_Uj8)

* Programando en JAVA. (2023, 8 diciembre). **DEPURACIÓN (DEBUG) en JAVA con INTELLIJ IDEA \- Tutorial Completo Fácil** \[Vídeo\]. YouTube. [https://www.youtube.com/watch?v=zmhwCK2lG3Y](https://www.youtube.com/watch?v=zmhwCK2lG3Y)

* Aprendo Informática. (2022, 9 junio). **Curso de Java: 71 \- Debug, depuración, como debuggear en visual studio code, Ciclos y Arreglos** \[Vídeo\]. YouTube. [https://www.youtube.com/watch?v=RxGdKF-AmJ4](https://www.youtube.com/watch?v=RxGdKF-AmJ4)

* Kevin De La Coba Malam. (2021, 20 noviembre). **DEBUG JAVA EN VSCODE\!\!\!** \[Vídeo\]. YouTube. [https://www.youtube.com/watch?v=KKQBol95uTg](https://www.youtube.com/watch?v=KKQBol95uTg)

## Control de versiones

* Atlassian. (s. f.-b). ***Qué es Git | Atlassian Git Tutorial***. [https://www.atlassian.com/es/git/tutorials/what-is-git](https://www.atlassian.com/es/git/tutorials/what-is-git)


# 9. Anexos

## Anexo i. Pipeline sencillo en GitHub Actions

Los ***pipelines*** se definen mediante archivos de configuración que indican a la herramienta qué comandos ejecutar y cuándo. A menudo, estos comandos son los mismos *shell scripts* que el desarrollador usaría localmente.

En este caso veamos un ejemplo de un fichero de configuración hecho en yaml:

```yaml
# .github/workflows/node.js.yml
name: Integracion Continua de Node.js

# Desencadenante: Este pipeline se ejecuta cuando se hace push o pull request a la rama 'main'
on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

# Define los trabajos (jobs) que se ejecutarán
jobs:
  build:
    runs-on: ubuntu-latest # Ejecutar en un servidor Linux (Ubuntu)
    steps:
    - uses: actions/checkout@v4 # Paso 1: Descargar el código
    - name: Configurar Node.js 20
      uses: actions/setup-node@v4
      with:
        node-version: '20' # Paso 2: Asegurar la versión correcta del entorno
    - name: Instalar dependencias
      run: npm ci # Paso 3: Usar el gestor de dependencias (npm)
    - name: Ejecutar pruebas unitarias
      run: npm test # Paso 4: ¡El paso de CI más importante!
    - name: Simulación de Entrega
      # Si el paso 'npm test' pasa, este paso se ejecuta.
      run: echo "Build exitoso. Artefacto listo para Entorno de Staging."
```

## Anexo ii. Ejemplo de fichero `devcontainer.json`

`.devcontainer/devcontainer.json`:

```json
{
  // Nombre que se mostrará en el IDE
  "name": "Entorno de Desarrollo Java/Maven",
  
  // Imagen base de Docker que define el S.O. y las herramientas
  "image": "[mcr.microsoft.com/devcontainers/java:21](https://mcr.microsoft.com/devcontainers/java:21)",
  
  // Ajustes de VS Code específicos para este proyecto
  "settings": {
    "java.jdt.ls.vmargs": "-noverify -Xmx1G -Djava.net.useSystemProxies=true"
  },
  
  // Extensiones de VS Code que se instalarán automáticamente en el contenedor
  "customizations": {
    "vscode": {
      "extensions": [
        "vscjava.vscode-java-pack",
        "redhat.vscode-xml"
      ]
    }
  },
  
  // Comando que se ejecuta después de crear el contenedor (ej. instalar dependencias)
  "postCreateCommand": "mvn install"
}
```
