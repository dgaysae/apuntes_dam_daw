---
{"dg-publish":true,"permalink":"/2-dam-pmdm/unidad-04-estructura-de-un-proyecto/","dg-note-properties":{"modulo":"[[Módulos/PMDM]]","libro":"[[Apuntes/PMDM (2º DAM)]]"}}
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


# 1. Creación de nuevo proyecto

**Actualizado: Abril 2020 (Gómez, S., 2011)**

El ritmo de actualizaciones de [**Android Studio**](https://developer.android.com/studio?hl=es-419) es bastante alto, por lo que algunos detalles de este artículo pueden no ajustarse exactamente a la última versión de la aplicación. Este artículo se encuentra actualizado para la versión de **Android Studio 3.6** 

Seguimos con el Curso de Programación Android. Para empezar a comprender cómo se construye una aplicación Android vamos a crear un nuevo proyecto en Android Studio y echaremos un vistazo a la estructura general del proyecto creado por defecto.

Para crear un nuevo proyecto ejecutaremos Android Studio y desde la pantalla de bienvenida pulsaremos la opción «Start a new Android Studio project» para iniciar el asistente de creación de un nuevo proyecto. 

![ud04_pmdm_01.png](/img/user/adjuntos/2DAM_PMDM/Unidad_04/ud04_pmdm_01.png)

Si ya habíamos abierto anteriormente Android Studio es posible que se abra directamente la aplicación principal en vez de la pantalla de bienvenida. En ese caso accederemos al menú «File / New project…» para crear el nuevo proyecto. 

El asistente de creación del proyecto nos guiará por las distintas opciones de creación y configuración de un nuevo proyecto Android. 

En la primera pantalla del asistente elegiremos el tipo de *actividad* principal de la aplicación. Entenderemos por ahora que una *actividad* es una “ventana” o “pantalla” de la aplicación. Para empezar seleccionaremos *Empty Activity*, que es el tipo más sencillo.

![ud04_pmdm_02.png](/img/user/adjuntos/2DAM_PMDM/Unidad_04/ud04_pmdm_02.png)

En la siguiente pantalla indicaremos, por este orden, el nombre de la aplicación, el paquete java para nuestras clases, y la ruta donde crear el proyecto. Para el segundo de los datos suele utilizarse un valor del tipo *domino.invertido.proyecto*. En mi caso utilizaré por tanto «net.sgoliver.android.holausuario». En tu caso puedes utilizar cualquier otro valor. Adicionalmente tendremos que indicar el lenguaje que utilizaremos para desarrollar (a partir de ahora utilizaré siempre Kotlin) y la API mínima (es decir, la versión mínima de Android) que soportará la aplicación. Como ya indiqué en el capítulo sobre la instalación del entorno de desarrollo, en este curso nos centraremos en Android 8.0 como versión mínima (API 26). Por último, el check de «Use legacy android.support libraries» lo dejaremos deshabilitado.

![ud04_pmdm_03.png](/img/user/adjuntos/2DAM_PMDM/Unidad_04/ud04_pmdm_03.png)

La versión mínima que seleccionemos en la pantalla anterior implica que nuestra aplicación se pueda ejecutar en más o menos dispositivos. De esta forma, cuanto menor sea ésta, a más dispositivos podrá llegar nuestra aplicación, pero más complicado será conseguir que se ejecute correctamente en todas las versiones de Android. Para hacernos una idea del número de dispositivos que cubrimos con cada versión podemos pulsar sobre el enlace «Help me choose», que mostrará el porcentaje de dispositivos que ejecutan actualmente cada versión de Android. Por ejemplo, en el momento de escribir este artículo, si seleccionamos como API mínima la 26 conseguimos cubrir un 60,8% de los dispositivos actuales. Como información adicional, si pulsamos sobre cada versión de Android en esta pantalla podremos ver una lista de las novedades introducidas por dicha versión.

![ud04_pmdm_04.png](/img/user/adjuntos/2DAM_PMDM/Unidad_04/ud04_pmdm_04.png)

Una vez configurado todo pulsamos el botón *Finish* y Android Studio creará por nosotros toda la estructura del proyecto y los elementos indispensables que debe contener. Si todo va bien aparecerá la pantalla principal de Android Studio con el nuevo proyecto creado. 

![ud04_pmdm_05.png](/img/user/adjuntos/2DAM_PMDM/Unidad_04/ud04_pmdm_05.png)

En la parte izquierda, podemos observar todos los elementos creados inicialmente para el nuevo proyecto Android, sin embargo por defecto los vemos de una forma un tanto peculiar que inicialmente puede llevarnos a confusión. Para entender mejor la estructura del proyecto vamos a cambiar momentáneamente la forma en la que Android Studio nos la muestra. Para ello, pulsaremos sobre la lista desplegable situada en la parte superior izquierda, y cambiaremos la vista de proyecto al modo «Project» (en cualquier momento podremos volver al modo «Android» inicial).

![ud04_pmdm_06.png](/img/user/adjuntos/2DAM_PMDM/Unidad_04/ud04_pmdm_06.png)

Con esto, la estructura del proyecto cambia un poco de aspecto y pasa a ser como se observa en la siguiente imagen:

En los siguientes apartados describiremos los elementos principales de esta estructura. 

Lo primero que debemos distinguir son los conceptos de *proyecto* y *módulo*. La entidad *proyecto* es única, y engloba a todos los demás elementos. Dentro de un proyecto podemos incluir varios *módulos*, que pueden representar aplicaciones distintas, versiones diferentes de una misma aplicación, o distintos componentes de un sistema (aplicación móvil, aplicación servidor, librerías, …). En la mayoría de los casos, trabajaremos con un proyecto que contendrá un sólo módulo correspondiente a nuestra aplicación principal. Por ejemplo en este caso que estamos creando tenemos el proyecto «android-hola-usuario» que contiene un solo módulo «app» que contendrá todo el software de la aplicación de ejemplo. 

![ud04_pmdm_07.png](/img/user/adjuntos/2DAM_PMDM/Unidad_04/ud04_pmdm_07.png)

En el siguiente apartado veremos la estructura básica de directorios de un proyecto Android.


# 2. Estructura de directorios

La estructura de directorios que encontramos al crear un nuevo proyecto en Android Studio es la siguiente:

* **`/app/src/main/java`**: contiene todo el **código fuente** de la aplicación
* **`/app/src/main/res/`**: para los **recursos** que usa la aplicación: imágenes, diseños de pantallas, etc.
* Fichero **`AndroidManifest.xml`**: **datos relevantes** del proyecto: cómo se llama, el nombre que aparecerá en el icono de la aplicación, el icono, pantallas que contiene, permisos...
* Fichero **`/app/build.gradle`**: con información necesaria para la **compilación** del proyecto.
* **`/app/libs`**: conjunto de **librerías** que usa el proyecto.



## 2.1. Directorio de código fuente

El directorio **`/app/src/main/java`** contiene todo el código fuente de la aplicación, clases auxiliares, etc. Inicialmente, Android Studio crea por nosotros el código básico de la pantalla (*actividad* o *activity*) principal de la aplicación, que por defecto se llamará **`MainActivity`**, y siempre bajo la estructura del paquete java definido durante la creación del proyecto.

![ud04_pmdm_08.png](/img/user/adjuntos/2DAM_PMDM/Unidad_04/ud04_pmdm_08.png)

## 2.2. Directorio de recursos

La carpeta "res" contiene todos los recursos que la aplicación utilizará: imágenes, diseños de pantallas (layouts), cadenas de texto, colores, estilos, etc.

La organización de los recursos en esta carpeta favorece los siguientes aspectos:

* **Organización**: al separar los recursos de tu código (evitando, entre otras cosas, el *hardcoding*), se mantiene un proyecto limpio y ordenado, facilitando la gestión y el mantenimiento.

* **Reutilización**: se pueden reutilizar los recursos en diferentes partes de tu aplicación, **evitando duplicar código**.

* **Localización**: se pueden crear varias versiones de los recursos en diferentes idiomas, permitiendo que la aplicación se adapte a distintos usuarios.

* **Personalización**: Android utiliza la carpeta "res" para aplicar temas y estilos a tu aplicación, personalizando su apariencia.

Contiene todos los ficheros de recursos necesarios para el proyecto: imágenes, layouts, cadenas de texto, etc. Los diferentes tipos de recursos se pueden distribuir entre las siguientes subcarpetas:

### `/res/drawable/`

Contiene imágenes y otros elementos gráficos usados por la aplicación. Los elementos que aquí se contienen son imágenes vectoriales, que se crean mediante cálculos matemáticas y se pueden redimensionar sin perder calidad en pantallas de distinta resolución. Para poder definir diferentes recursos dependiendo de la resolución y densidad de la pantalla del dispositivo se suele dividir en varias subcarpetas: 
* `/drawable` - recursos independientes de la densidad
* `/drawable-ldpi` (densidad baja)
* `/drawable-mdpi` (densidad media)
* `/drawable-hdpi` (densidad alta)
* `/drawable-xhdpi` (densidad muy alta)
* `/drawable-xxhdpi` (densidad muy muy alta)

### `/res/mipmap/`

Contiene los iconos de lanzamiento de la aplicación (el icono que aparecerá en el menú de aplicaciones del dispositivo) para las distintas densidades de pantalla existentes. Al igual que en el caso de las carpetas /drawable, se dividirá en varias subcarpetas dependiendo de la densidad de pantalla:

* `/mipmap-mdpi`
* `/mipmap-hdpi`
* `/mipmap-xhdpi`
* ...

### `/res/layout/`

Contiene los ficheros de definición XML de las diferentes pantallas de la interfaz gráfica. Para definir distintos layouts dependiendo de la orientación del dispositivo se puede dividir también en subcarpetas:
* `/layout` (vertical)
* `/layout-land` (horizontal)

### `/res/anim/` y/o `/res/animator/`

Contienen la definición de las animaciones[^1] utilizadas por la aplicación.

### `/res/color/`

Contiene ficheros XML de definición de listas de colores según estado.

### `/res/menu/`

Contiene la definición XML de los menús de la aplicación.

### `/res/xml/`

Contiene otros ficheros XML de datos utilizados por la aplicación.

### `/res/raw/`

Contiene recursos adicionales, normalmente en formato distinto a XML, que no se incluyen en el resto de carpetas de recursos.

### `/res/values/`

Contiene otros ficheros XML de recursos de la aplicación, como por ejemplo cadenas de texto (*strings.xml*), estilos (*styles.xml*), colores (*colors.xml*), arrays de valores (*arrays.xml*), tamaños (*dimens.xml*), etc.

Todas las anteriores son carpetas de **posibles recursos** que pueden aparecer en un proyecto Android Según las necesidades, se añadirán o eliminarán según las necesidades del proyecto. 

Como ejemplo, para un proyecto nuevo Android, tendremos por defecto los siguientes recursos para la aplicación:

![ud04_pmdm_09.png](/img/user/adjuntos/2DAM_PMDM/Unidad_04/ud04_pmdm_09.png)

Como se puede observar, existen algunas carpetas en cuyo nombre se incluye un sufijo adicional, como por ejemplo «drawable-**v24**«. Éstos, y otros sufijos, se emplean para definir recursos independientes para determinados dispositivos según sus características. De esta forma, por ejemplo, los recursos incluidos en la carpeta «drawable-**v24**» se aplicarían tan sólo a dispositivos cuya versión de Android sea la 7.0 (API 24) o superior, o por ejemplo los incluidos en una carpeta llamada “values-**w820dp**” se aplicarían sólo a pantallas con más de 820dp de ancho. Al igual que estos sufijos «-w» y «–v» existen otros muchos para referirse a otras características del terminal, puede consultarse la lista completa en la documentación oficial de Android.

Entre los recursos creados por defecto cabe destacar los **layouts**, en nuestro caso sólo tendremos por ahora el llamado `activity_main.xml`, que contienen la definición de la interfaz gráfica de la pantalla principal de la aplicación. Si hacemos doble clic sobre este fichero Android Studio nos mostrará esta interfaz en su editor gráfico, y como podremos comprobar, en principio contiene tan sólo una etiqueta de texto con el mensaje “Hello World!”. 

![ud04_pmdm_10.png](/img/user/adjuntos/2DAM_PMDM/Unidad_04/ud04_pmdm_10.png)

Pulsando sobre los tres botones de la esquina superior derecha (resaltados en rojo en la imagen anterior) podemos alternar entre el editor gráfico (tipo arrastrar-y-soltar), mostrado en la imagen anterior, el editor de código XML, o una vista compartida que permita visualizar ambas cosas de forma simultánea, como en la imagen siguiente:

![ud04_pmdm_11.png](/img/user/adjuntos/2DAM_PMDM/Unidad_04/ud04_pmdm_11.png)

Durante el curso no utilizaremos demasiado el editor gráfico, sino que modificaremos la interfaz de nuestras pantallas manipulando directamente su fichero XML asociado. Esto en principio puede parecer mucho más complicado que utilizar el editor gráfico (no es nada complicado en realidad), pero nos permitirá comprender mucho mejor los elementos que componen la interfaz de nuestras aplicaciones.

**¿Cómo funciona?**

Android utiliza un sistema de identificación único para cada recurso dentro de la carpeta `res`. Estos identificadores se generan automáticamente y se almacenan en un archivo llamado `R.java`. Al referenciar un recurso en tu código, simplemente utilizas el identificador correspondiente.

Ejemplo:

Si tienes una imagen llamada `my_image.png` en la carpeta `mipmap`, puedes referenciarla en tu código de la siguiente manera:

```kotlin
var imageView = findViewById(R.id.myImageView);
imageView.setImageResource(R.mipmap.my_image);
```

## 2.3. AndroidManifest.xml

Contiene la definición en XML de muchos de los aspectos principales de la aplicación, como por ejemplo **su identificación** (nombre, icono, …), **sus componentes** (pantallas, servicios, …), o los **permisos necesarios para su ejecución**. Veremos más adelante más detalles de este fichero.

**Antes de que el sistema operativo Android ejecute una sola línea** de código Kotlin, **lee este archivo** para saber qué contiene la app y qué permisos necesita.

¿Para qué sirve realmente? Las funciones principales de este fichero son:

* **Identificar la aplicación**: define el nombre del paquete (ID único).

* **Declarar los componentes**: todas las Activities, Services o Broadcast Receivers deben estar aquí. Si no están declarados, no existen para el sistema.

* **Gestionar permisos**: aquí solicitamos **acceso a Internet**, a la **cámara**, a la **ubicación**, etc.

* **Requisitos de hw/sw**: define la **versión mínima** de Android soportada o si la app requiere obligatoriamente una cámara con flash.

La estructura básica de este fichero tiene este aspecto:  

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.ies.miaplicacion">

    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.CAMERA" />

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:theme="@style/Theme.MiAplicacion">

        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

        <activity 
            android:name=".ConfiguracionActivity"
            android:label="Ajustes de Usuario" />

    </application>
</manifest>
```

Donde:

* **`<uses-permission>`**  establece los permisos que la app tendrá en el dispositivo. Se colocan fuera de la etiqueta **`<application>`**. El ejemplo de Internet es el más común cuando usamos librerías como **Picasso** para cargar imágenes (como veremos en el tema de **Palette Widgets**.

* **Activity principal**, también conocida como **launcher**. Determina qué Activity se se mostrará cuando se abra la app. El bloque **`<intent-filter>`** dentro de una Activity indica que esa es la pantalla que se abrirá al pulsar el icono de la app en el móvil (`android.intent.category.LAUNCHER`). **Sólo debe haber una** con esta categoría.

* **Registro de nuevas Activities**: cada vez que se crea una nueva Activity (`File > New > Activity`), Android Studio la añadirá automáticamente al manifest. Si la crean a mano, deben recordar **registrarla aquí** o la app se cerrará al intentar abrirla.

### 2.3.1. Configuraciones útiles

Para cambiar algunos de los aspectos visuales o de comportamiento en nuestra app podemos hacer lo siguiente:

* Cambiar el **nombre de la app**: se hace en el atributo **android:label** de la etiqueta **`<application>`**.
  > [!note] 
  > Lo ideal es que apunte a un recurso de texto:
  > ```
  > android:label="@string/nombre_personalizado"
  > ```

* **Forzar la orientación vertical**: si no queremos que la pantalla rote, añadimos este atributo a la `<activity>`:
  ```
  android:screenOrientation="portrait"
  ```

* **Cambiar el icono**: se hace en **`android:icon`**. Si hemos creado un nuevo icono con el **Image Asset Studio**, aquí es donde se vincula:
  ```
  android:icon="@mipmap/mi_nuevo_icono"
  ```

### 2.3.2. Errores comunes

* **`ActivityNotFoundException`**: es el error más típico. Ocurre cuando intentamos lanzar una Activity con un Intent pero **hemos olvidado declararla** en el Manifest.
  > [!note] 
  > Aunque generalmente se hace automáticamente, es conveniente comprobar que cada `Activity` que se crea se registra en el manifest.

* **Permisos olvidados**: cuando lanzamos el emulador y vemos que no cargan las imágenes de Internet, o que no muestra algo que bajamos de la red, la mayoría de las veces es porque falta:
  ```
  <uses-permission android:name="android.permission.INTERNET" />
  ```

* **Mayúsculas/minúsculas**: el atributo `android:name=".MainActivity"` debe coincidir exactamente con el nombre de la clase Kotlin. El **punto inicial** indica que la clase está en el **paquete principal** definido arriba.

## 2.4. Fichero gradle

El fichero **`/app/build.gradle`** contiene información necesaria para la compilación del proyecto, por ejemplo la versión del SDK de Android utilizada para compilar, la mínima versión de Android que soportará la aplicación, referencias a las librerías externas utilizadas, etc. Más adelante veremos también más detalles de este fichero. 

 En un proyecto pueden existir varios ficheros **`build.gradle`**, para definir determinados parámetros a distintos niveles. Por ejemplo, en nuestro proyecto podemos ver que existe un fichero `build.gradle` a nivel de proyecto, y otro a nivel de módulo dentro de la carpeta `/app`. El primero de ellos definirá parámetros globales a todos los módulos del proyecto, y el segundo sólo tendrá efecto para cada módulo en particular. 

## 2.5. Carpeta /app/libs

Puede contener las librerías externas que utilice nuestra aplicación. Normalmente no incluiremos directamente aquí ninguna librería, sino que haremos referencia a ellas en el fichero `build.gradle` descrito en el punto anterior, de forma que entren en el proceso de compilación de nuestra aplicación. Veremos algún ejemplo más adelante. 

Y con esto todos los elementos principales de un proyecto Android. No pierdas de vista este proyecto de ejemplo que hemos creado ya que lo utilizaremos en breve como base para crear nuestra primera aplicación. Pero antes, en el siguiente apartado hablaremos de los componentes software principales con los que podemos construir una aplicación Android.

Recordad que tenéis a vuestra disposición el índice completo de contenidos del Curso de Programación Android desde donde podéis acceder de forma totalmente gratuita a cualquier otro tema que os interese.

# Referencias

* MoureDev by Brais Moure. (2020, 17 enero). ***ANDROID STUDIO: COMO Crear una APP (para Principiantes)*** 📲 \[Tutorial\] \[Vídeo\]. YouTube. [https://www.youtube.com/watch?v=BQaxPwZWboA](https://www.youtube.com/watch?v=BQaxPwZWboA)

* Sgoliver, & Sgoliver. (2014b, diciembre 28). Estructura de un proyecto Android (Android Studio). [sgoliver.net](https://www.sgoliver.net/). [https://www.sgoliver.net/blog/estructura-de-un-proyecto-android-android-studio/](https://www.sgoliver.net/blog/estructura-de-un-proyecto-android-android-studio/)

[^1]:  Animaciones y transiciones. (s. f.). Android Developers. https://developer.android.com/develop/ui/views/animations?hl=es

---

<p><span>🏠 <strong>Unidad:</strong> undefined</span></p>