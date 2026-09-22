---
{"dg-publish":true,"permalink":"/2-dam-pmdm/unidad-06-comenzamos/","dg-note-properties":{"modulo":"[[Módulos/PMDM]]","libro":"[[Apuntes/PMDM (2º DAM)]]"}}
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


# 1. Layouts

En Android, existen varios tipos de *layouts* y todos heredan de la clase [**`ViewGroup`**](https://developer.android.com/reference/android/view/ViewGroup). Por las limitaciones de tiempo nos vamos a centrar en los más habituales.

| Layout | Uso recomendado |
| :---: | ----- |
| [**`FrameLayout`**](https://developer.android.com/reference/android/widget/FrameLayout) | Puede contener un sólo elemento. Suele usarse como capa o pila, poniendo uno sobre otro. El uso habitual es el de contener [**`Fragments`**](https://developer.android.com/guide/fragments?hl=es-419) o imágenes con texto superpuesto. |
| [**`LinearLayout`**](https://developer.android.com/reference/android/widget/LinearLayout) | Estructura muy simple donde los elementos se disponen de forma lineal (uno tras otro), ya sea horizontal o verticalmente. Es útil para listas simples o grupos de botones. Y mediante el atributo `android:weightSum` se puede repartir el espacio proporcionalmente entre todos sus elementos. |
| [**`GridLayout`**](https://developer.android.com/reference/android/widget/GridLayout) | Dispone los elementos en una rejilla o matriz `m x n`. Es útil para pantallas como formularios (con varias columnas), calculadoras, etc. |
| [**`ConstraintLayout`**](https://developer.android.com/reference/androidx/constraintlayout/widget/ConstraintLayout) **👍** | Es el más flexible y eficiente, al tiempo que el más complejo. Utiliza constraints para indicar la disposición de los elementos con respecto a otros elementos o al contenedor. Este layout es el más recomendable y en la actualidad se considera el layout estándar. |
| [**`CoordinatorLayout`**](https://developer.android.com/reference/androidx/coordinatorlayout/widget/CoordinatorLayout) | Viene en la librería [**Material Design**](https://m3.material.io/) y se usa para interacciones complejas en las nuevas interfaces de usuario, como que el botón flotante (FAB) se mueva cuando aparece un aviso o que la barra superior se oculte al hacer scroll. |

> [!warning] Importante 
> En la actualidad, **el anidamiento de layouts penaliza el rendimiento**.
> Antes, al diseñar interfaces complejas, se metían [**`LinearLayouts`**](https://developer.android.com/reference/android/widget/LinearLayout) dentro de otros, y esos a su vez dentro de un [**`RelativeLayout`**](https://developer.android.com/develop/ui/views/layout/relative?hl=es-419).
> 
> En la actualidad, si necesitamos **más de dos niveles de anidamiento**, lo recomendable es usar un solo [**`ConstraintLayout`**](https://developer.android.com/reference/androidx/constraintlayout/widget/ConstraintLayout).


## ConstraintLayout

El [**`ConstraintLayout`**](https://developer.android.com/reference/androidx/constraintlayout/widget/ConstraintLayout) permite disponer los elementos de la interfaz de forma flexible, sin necesidad de anidar otros layouts (lo que mejora drásticamente el rendimiento de la app). Se basa en **restricciones** (*constraints*), que pueden entenderse como unas "gomas elásticas" que sujetan cada elemento en la pantalla.

Para que un elemento esté bien posicionado en un [**`ConstraintLayout`**](https://developer.android.com/reference/androidx/constraintlayout/widget/ConstraintLayout), necesita **al menos una *constraints* horizontal y una vertical**. Si falta alguna, el elemento se desubica al ejecutar la app, generalmente desplazándose a la esquina superior (0, 0).

La forma de darle esas restricciones es mediante los atributos **`layout_constraintTop_toTopOf`**, **`layout_toBottomOf_toBottomOf`**, etc. que permiten su posicionamiento relativo. El formato en el que están escritas estas propiedades indica:

```xml
layout_constraintTop_toTopOf: <parent o id de otro componente>
```

Donde:

* El **`Top`** de "layout_constraint**Top**\_toTopOf" se refiere a la arista (en este caso parte superior) del componente al que estamos aplicando la restricción.

* El **`TopOf`** de "layout_constraintTop\_to**TopOf**" a la arista (en este caso parte superior) del elemento (contenedor u otro elemento de la interfaz) con el que establecer esa restricción.

Una vez que hay una restricción, el **margen** define la distancia fija.

Podemos usar el atributo **`bias`**, que representa el tanto por ciento de inclinación, si queremos modificar la distancia en las restricciones. Por ejemplo, si un botón tiene restricciones a izquierda y derecha, por defecto queda centrado (bias no se muestra como atributo, pero su valor es 50%). Con el **`bias`** podemos "empujarlo" más hacia un lado u otro (ej. 30% - 70%).

**Guidelines**  
Se pueden usar **guidelines** (guías), que son líneas invisibles (verticales u horizontales) que sirven como ancla. Pueden fijarse en **`dp`** o en **`%`** y son muy útiles para dejar un margen lateral en toda la app (generalmente del del 10%).

**Barriers**  
Son líneas invisibles que se mueven según el tamaño del componente más grande de un grupo. Suelen usarse, por ejemplo, con etiquetas de texto que según el idioma pueden cambiar de longitud.

**Chains**  
Permiten agrupar varios elementos para que se repartan el espacio de forma equilibrada (estilo flexbox de CSS).

## Ejemplos prácticos.


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/2-dam-pmdm/unidad-06/30-referencias/#diseno-de-layouts-aristi-devs" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## Diseño de layouts - AristiDevs

<iframe width="560" height="315" src="https://www.youtube.com/embed/videoseries?si=KlZoBOWdwX47puTj&amp;list=PL8ie04dqq7_MGB5vNieT4Fr_fvw5t0nBC" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

> Programación by AristiDevs. ***Diseño de layouts***. (s. f.-b). YouTube. [Playlist](https://youtube.com/playlist?list=PL8ie04dqq7_MGB5vNieT4Fr_fvw5t0nBC&si=Rl4lpH9QWUi8sHRg)


</div></div>


> [!info] Para más ejemplos... 
> Puedes ver más ejemplos prácticos de cómo crear y usar distintos layouts, en las [referencias documentales](#referencias-documentales).


# 2. Palette Texts

La paleta de texto (*Palette Texts*) nos permite definir y gestionar los estilos de texto en la aplicación.

Se trata de un conjunto de estilos predefinidos que se pueden aplicar a los elementos de texto de tu aplicación, como títulos, subtítulos, cuerpos de texto, etc. Estos estilos **se definen en un archivo XML** y se pueden reutilizar en toda tu aplicación.

Para ello existen ficheros XML en la carpeta **`res/values`**, como por ejemplo **`style.xml`**. Veamos el siguiente ejemplo:

```xml
<resources>
    <style name="TextAppearance.MyApp.Title">
        <item name="android:textSize">24sp</item>
        <item name="android:textColor">@color/primary</item>
        <item name="android:fontFamily">@font/my_font</item>
    </style>

    <style name="TextAppearance.MyApp.Body">
        <item name="android:textSize">16sp</item>
        <item name="android:textColor">@color/secondary</item>
    </style>
</resources>
```

En este ejemplo, se definen dos estilos: **TextAppearance.MyApp.Title** y **TextAppearance.MyApp.Body**. Cada estilo especifica propiedades como el **tamaño de fuente**, el **color** y la ***font family***.

Detengámonos un momento aquí para hacer hincapié en la importancia de la extensión de los estilos de base. Aunque técnicamente podríamos poner cualquier nombre a capricho, los nombres como TextAppearance.MyApp.Title siguen esta nomenclatura debido a la **herencia**.

En Android, el uso de puntos  en el nombre describe la herencia implícita. Cuando nombramos a un estilo siguiendo un patrón jerárquico separado por puntos, el estilo "hijo" hereda automáticamente todos los atributos del estilo "padre".

Por ejemplo, partiendo del estilo base:  

```xml
<style name="TextAppearance.MyApp">
    <item name="android:textColor">@color/black</item>
    <item name="android:fontFamily">sans-serif</item>
</style>
```

Hemos creado uno llamado **`TextAppearance.MyApp.Title`**:

```xml
<style name="TextAppearance.MyApp.Title">
    <item name="android:textSize">24sp</item>
    <item name="android:textStyle">bold</item>
</style>
```

Y este nuevo estilo **Title** tendrá **cuatro atributos**: el color y la fuente heredados de **TextAppearance.MyApp** más el tamaño y el estilo de texto añadidos en éste último.

> [!warning] Importante 
> En las versiones más recientes de Android, Google ha estandarizado los nombres de la tipografía para que las apps sean más coherentes. Ya no se recomienda usar nombres a capricho como "SubtituloGrande". Lo mejor es **seguir la escala tipográfica oficial de Material Design 3**, que divide los textos en cinco grupos:
> * **`Display`** (`L`, `M`, `S`): para pantallas grandes o énfasis extremo.
> * **`Headline`** (`L`, `M`, `S`): títulos de secciones.
> * **`Title`** (`L`, `M`, `S`): títulos de tarjetas o diálogos.
> * **`Body`** (`L`, `M`, `S`): el texto principal de la app.
> * **`Label`** (`L`, `M`, `S`): textos de botones, etiquetas de campos, etc.

> [!warning] Importante 
> En algunos ejemplos de los apuntes puede aparecer el nombre **`TextAppearance.AppCompat`**. Esto ha cambiado con **Material Design 3**, por lo que lo ideal es cambiarlo por **`TextAppearance.Material3.TitleLarge`**, etc.

Para aplicar un estilo de texto a un elemento de texto en un archivo de layout XML:  

```xml
<TextView
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Este es un título"
    android:textAppearance="@style/TextAppearance.MyApp.Title" />
```

Y en código:  

```kotlin
val textView: TextView = findViewById(R.id.myTextView)
textView.setTextAppearance(R.style.TextAppearance.MyApp.Body)
```

También es muy útil para el tema de accesibilidad en la app, ya que con una paleta de textos se pueden definir los estilos que cumplan con los **requisitos de accesibilidad** (tamaño mínimo de la fuente, contraste de color, etc.).

## 2.1. TextView

El componente **`TextView`** es uno de los más utilizados en Android para mostrar texto en pantalla.

![ud06_pmdm_01.png](/img/user/adjuntos/2DAM_PMDM/Unidad_06/ud06_pmdm_01.png)

> Fuente: Android - TextView Control. (s. f.). https://www.tutorialspoint.com/android/android_textview_control.htm

La gran cantidad de propiedades nos permite personalizar su apariencia y comportamiento.

Por ejemplo, las propiedades básicas:

* **`text`**: establece el texto que se mostrará en el `TextView`.

* **`textSize`**: define el tamaño del texto, generalmente en sp[^2] (*scaled pixels*).
  > [!info] 
  > Debido a las dimensiones de las pantallas, es recomendable usar **valores pares**.

* **`textColor`**: indica el color del texto.

* **`gravity`**: permite alinear el texto dentro del `TextView` (inicio, centro, fin, etc.).

* **`layout_width`** / **`layout_height`**: definen el ancho y alto del `TextView`. Hay que tener cuidado con valores como **`match_parent`**, que no significa “todo el alto/ancho de la pantalla”, sino el del contenedor donde se encuentra.

Podemos modificar el formato del texto con:

* **`textStyle`**: aplica estilos al texto (normal, negrita, cursiva).

* **`fontFamily`**: establece la familia de fuentes a utilizar. Estas fuentes pueden extraerse de **`res/font`** si se han cargado algunas en sus respectivos ficheros ttf.
  > [!info] 
  > Se pueden agregar *custom fonts* o fuentes propias (ficheros ttf) a un proyecto y utilizarlas en los `TextView`.

* **`letterSpacing`**: ajusta el espaciado entre letras.

* **`lineSpacingExtra`**: añade espacio extra entre líneas.

* **`maxLines`**: limita el número de líneas que se mostrarán.

* **`typeface`**: introduce una fuente de las que Android tiene por defecto.

* **`textAllCaps`**: todo mayúsculas.

* **`textAppearance`**: permite indicar el estilo del `TextView` que se haya definido en la paleta de textos. Por ejemplo: `@style/…Display3`

O el formato visual mediante:

* **`background`**: establece un color o un drawable como fondo.

* **`padding`**: añade espacio entre el borde del `TextView` y su contenido.

* **`drawableLeft`/`Right`/`Top`/`Bottom`**: Agrega imágenes a los lados del texto.

Es posible influir en el comportamiento de un `TextView` a través de:

* **ellipsize**: define cómo se truncará el texto si excede el espacio disponible (cortar, omitir, etc.).

* **singleLine**: fuerza al texto a ocupar una sola línea.

* **clickable**: hace que el `TextView` sea clickeable.

* **linksClickable**: habilita los enlaces dentro del texto.

Veamos esto con un ejemplo:  

```xml
<TextView
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:textSize="24sp"
    
    android:text="Hola, mundo!"
    android:textColor="@color/colorPrimary"
    android:textStyle="bold"
    android:gravity="center" />
```

Este código creará un TextView con el texto "Hola, mundo!" en negrita, centrado y con el color colorPrimary definido en los recursos.

> [!info] 
> Es recomendable usar la unidad **`sp`** para el tamaño de texto, ya que se **escala automáticamente** según las preferencias del usuario.
> La unidad **`dp`** se utiliza para indicar las dimensiones de pantallas, vistas... en general para contenedores de elementos relacionados que se ven afectados por la densidad de pantalla.

## 2.2. EditText

En esta ocasión hablamos del componente **EditText[^3]** que ofrece campos que admiten texto editable. Es decir, texto que **el usuario puede modificar**.

![ud06_pmdm_02.png\|300](/img/user/adjuntos/2DAM_PMDM/Unidad_06/ud06_pmdm_02.png)

El componente **EditText** es fundamental en Android para permitir a los usuarios introducir texto en una aplicación. Al igual que el TextView, cuenta con una amplia variedad de propiedades que permiten personalizar estos campos.

En cuanto a las propiedades **básicas**:

* **`text`**: establece el texto predeterminado que se mostrará en el EditText.

* **`hint`**: muestra un texto de sugerencia cuando el campo está vacío.

* **`textSize`**: define el tamaño del texto.

* **`textColor`**: especifica el color del texto.

* **`inputType`**: indica el tipo de entrada esperado (texto, número, correo electrónico, etc.).

* **`maxLength`**: limita la cantidad máxima de caracteres que el usuario puede ingresar.

Para el **formato** y **apariencia**:

* **`ems`**: establece una anchura fija para el campo.

* **`textStyle`**: aplica estilos al texto (normal, negrita, cursiva).

* **`fontFamily`**: establece la familia de fuentes a utilizar.

* **`background`**: define el fondo del EditText.

* **`padding`**: añade espacio entre el borde y el texto.

* **`drawable`** (`Start` | `Top` | `Bottom` | `End`…): podemos asignar un icono al campo.

* **`drawablePadding`**: para espaciar el icono del borde del campo.

* **`textColor`** / **`textColorHint`**: cambia el color del texto.

Y para indicar ciertos **comportamientos**:

* **`singleLine`**: fuerza al texto a ocupar una sola línea.

* **`maxLines`**: limita el número máximo de líneas.

* **`lines`**: establece el número exacto de líneas.

* **`imeOptions`**: configura las opciones del teclado virtual (buscar, siguiente, etc.).

* **`selectAllOnFocus`**: selecciona todo el texto al obtener el foco.

Propiedades de validación:

* **`inputType`**: además de indicar el tipo de entrada, puede ayudar a validar los datos que se introducen por teclado (por ejemplo, solo números). Es fundamental para indicar el tipo de entrada que se espera en un `EditText`. Esto no solo afecta a la apariencia del teclado virtual, sino que también puede influir en el comportamiento del sistema y en la validación.

  Los valores más comunes de esta propiedad que definen el tipo de campo para introducir datos son:

  * **`text`**: texto sin formato.

  * **`textMultiLine`**: texto de múltiples líneas.

  * **`number`**: números decimales.

  * **`phone`**: número de teléfono.

  * **`email`**: dirección de correo electrónico.

  * **`password`**: contraseña (oculta el texto).

  * **`date`**: fecha.

  * **`datetime`**: fecha y hora.

  Estos tipos pueden combinarse, separándolos con pipes (`|`):
  ```xml
  <EditText
    android:inputType="textPassword|text|number"
    ... />
  ```

* **`digits`**: nos permite introducir una máscara de valores aceptados en el campo. Por ejemplo, “0123456789” haría que sólo se permitiese números.

* **`maxLength`**: limita la cantidad máxima de caracteres.

Veamos algunas de ellas con un ejemplo:  

```xml
<EditText
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:hint="Introduzca su nombre"
    android:inputType="textCapWords"
    android:maxLines="1"   
 />
```

Este código creará un EditText que ocupará **todo el ancho** de su contenedor, con un **texto de sugerencia** "Introduzca su nombre", solo **permitirá una línea** de texto y pondrá en mayúscula la primera letra de cada palabra.

Existen otros componentes como [**`TextInputLayout`**](https://developer.android.com/reference/com/google/android/material/textfield/TextInputLayout), que proporciona funcionalidades adicionales como etiquetas emergentes, validación y ayuda visual.

### 2.2.1. Validaciones en `EditText`

Aunque **`inputType`** ofrece una buena base para la validación, **realmente no valida** que el dato introducido cumpla con el formato de validación deseado. Por tanto, en muchas ocasiones hay que implementar la validación mediante código. Veamos algún ejemplo donde validar varios campos:  

```kotlin
val editTextEmail = findViewById<EditText>(R.id.editTextEmail)
val editTextPassword = findViewById<EditText>(R.id.editTextPassword)

val email = editTextEmail.text.toString()
val password = editTextPassword.text.toString()

if (TextUtils.isEmpty(email)) {
    editTextEmail.error = "El email es obligatorio"
} else if (TextUtils.isEmpty(password)) {
    editTextPassword.error = "La contraseña es obligatoria"
} else {
    // Ambos campos tienen texto, valida el email (por ejemplo)
    if (!android.util.Patterns.EMAIL_ADDRESS.matcher(email).matches()) {
        editTextEmail.error = "El formato del email no es válido"
    } else {
        // Todo correcto
    }
}
```

## 2.3. AutoCompleteTextView

Este componente muestra un campo que sugiere automáticamente opciones a medida que el usuario escribe.

![ud06_pmdm_03.jpg\|300](/img/user/adjuntos/2DAM_PMDM/Unidad_06/ud06_pmdm_03.jpg)

> Fuente: Gharat, A. (2017, 2 octubre). AutoCompleteTextView suggestions repeating. Stack Overflow. https://stackoverflow.com/questions/46520854/autocompletetextview-suggestions-repeating

Es una extensión de `EditText` que muestra un desplegable con sugerencias basadas en una lista de datos.

El **`AutoCompleteTextView`** realmente es un campo de texto editable que, a medida que el usuario escribe, muestra un menú desplegable con sugerencias de texto. Estas sugerencias pueden provenir de distintas fuentes:

* De un **array definido en el código** (poco recomendable):
  ```kotlin
  val provincias = arrayOf(
                "Almería", "Granada", "Málaga", "Jaén",
                "Córdoba", "Sevilla", "Cádiz", "Huelva")
  ```

* De una **lista estática** definida en los recursos (`strings.xml`):
  ```xml
  <resources>
      ...
      <string-array name="provincias">
          <item>Almería</item>
          <item>Granada</item>
          <item>Málaga</item>
          <item>Jaén</item>
          <item>Córdoba</item>
          <item>Sevilla</item>
          <item>Cádiz</item>
          <item>Huelva</item>
      </string-array>
      ...
  </resources>
  ```

* Desde un set de datos devuelto por una base de datos o un servicio web.

Algunas de las propiedades más usadas para este componente son:

| Propiedad | Descripción |
| :---- | :---- |
| `completionThreshold` | Número mínimo de caracteres que el usuario debe escribir antes de que aparezca el menú desplegable. |
| `dropDownHeight` | Altura del menú desplegable. |
| `dropDownWidth` | Ancho del menú desplegable. |
| `adapter` | Un **adaptador** que vincula los datos a mostrar en el menú desplegable con la vista. |

### 2.3.1. Adaptadores

Los adaptadores permiten *mapear* la fuente de datos que queremos asociar al `AutoCompleteTextView` a las vistas que se muestran en el menú desplegable. Android proporciona varios adaptadores predefinidos, como:

#### ArrayAdapter

Para listas simples de cadenas.

Ejemplos de código con un **array definido en el código**:  

```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        // Crear una lista de datos
        val provincias = arrayOf("Almería", "Granada",
                        "Málaga", "Jaén", "Córdoba",
                        "Sevilla", "Cádiz", "Huelva")
        val autoCompleteTextView =
findViewById<AutoCompleteTextView>(R.id.autoCompleteTextView)
        // Crear un adaptador para la lista de datos
        val adapter = ArrayAdapter<String>(this,
                android.R.layout.simple_dropdown_item_1line,
                provincias)
        // Asigna el adaptador al campo
        autoCompleteTextView.setAdapter(adapter)
    }
}
```

Otro ejemplo, esta vez teniendo los **datos parametrizados** en **`strings.xml`** (ver ejemplo de **lista estática**):  

```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Obtener lista de strings de recursos:
        val provincias: Array<String> = resources.
                    getStringArray(R.array.provincias)

        val autoCompleteTextView =
findViewById<AutoCompleteTextView>(R.id.autoCompleteTextView)

        // Crear un adaptador para la lista de datos
        val adapter = ArrayAdapter<String>(this,
                android.R.layout.simple_dropdown_item_1line,
                provincias)

        // Asigna el adaptador al campo
        autoCompleteTextView.setAdapter(adapter)
    }
}
```

#### SimpleCursorAdapter

Para los datos extraídos de bases de datos u otros servicios externos. Esto se verá más adelante.


## 2.4. MultiAutoCompleteTextView

Este componente permite a los usuarios seleccionar múltiples sugerencias de una lista. A diferencia del [[2DAM_PMDM/Unidad 06/2. Palette Texts#2.3. AutoCompleteTextView\|AutoCompleteTextView]], que permite seleccionar una sugerencia sólo una vez, **`MultiAutoCompleteTextView` permite seleccionar varias**, separadas por un delimitador o token definido.

Es similar al componente [[2DAM_PMDM/Unidad 06/2. Palette Texts#2.3. AutoCompleteTextView\|AutoCompleteTextView]]. En ambos campos se pueden introducir varios valores. Es decir, el `AutoCompleteTextView` muestra texto emergente pero, una vez introducido, se puede seguir insertando texto.

La diferencia entre ambos componentes es que `MultiAutoCompleteTextView` permite introducir varios valores, separados por el token que indiquemos, y una vez introducido podamos volver a recibir sugerencias para los siguientes valores que el usuario quiera introducir. Al seleccionar uno de los valores de la lista, se inserta el texto en el campo y se añade el token (coma, punto y coma, etc.) y permite seguir escribiendo y, al mismo tiempo, mostrando sugerencias.

Reutilizando el código anterior, podríamos hacer un campo MultiAutoCompleteTextView que permita incluir varios valores en dicho campo y separados por comas:  

```kotlin
...
    // Obtener lista de strings de recursos:
    val provincias: Array<String> = resources.
                    getStringArray(R.array.provincias)
                    
    val multiAutoCompleteTextView =
        findViewById<MultiAutoCompleteTextView>(
                R.id.multiAutoCompleteTextView
        )
        
    // Crear un adaptador para la lista de datos
    val adapter = ArrayAdapter<String>(this,
                android.R.layout.simple_dropdown_item_1line,
                provincias)
                
    // Asigna el adaptador al campo
    multiAutoCompleteTextView.setAdapter(adapter)
    
    // Indico el separador de valores
    multiAutoCompleteTextView.setTokenizer(
        MultiAutoCompleteTextView.CommaTokenizer()
    )
...
}
```

Al establecer el token estoy indicando al campo que permita añadir varios valores de la lista, separados por comas.


## 2.5. Otros componentes

Existen muchos más componentes, aunque su base es muy similar a la de los elementos que ya hemos visto. En cualquier caso, aquí tienes un vídeo para ver [[2DAM_PMDM/Unidad 06/30. Referencias#Cómo crear selectores para formularios en Android con Kotlin - Garaje de ideas\|cómo crear selectores]] (checkboxes, radiobuttons, etc.).

> [!warning] Importante 
> Es aquí donde ya depende de ti investigar aquellos componentes que quieras usar: busca información, pregunta a [Gemini](https://gemini.google.com/) o cualquier otro motor de IA, etc.

## 2.6. Uso de código

Podemos hacer uso del código para modificar los atributos mencionados en los apartados anteriores. Veamos algunos ejemplos.

### 2.6.1. Texto parametrizado

Una de las cosas que debemos **evitar** es ***hardcodear*** valores en nuestro código, como es el caso de los textos:  

```kotlin
// tvSaludo : TextView
tvSaludo.text = "¡Hola, Anselmo! Hoy es viernes." // ❌ Mal!!!!!
```

Lo mejor es parametrizar el texto en el fichero **`strings.xml`** de la carpeta de recursos (res) y obtenerlo desde cualquier parte del proyecto, ya sea la `activity` (xml) o desde código. Esto permite personalizar mensajes según los datos de tu aplicación, haciendo que tu interfaz de usuario sea más **dinámica**.

El texto parametrizado te permite incluir variables dentro de una cadena en **`strings.xml`**. Estas variables se reemplazarán por valores reales en tiempo de ejecución.

Ejemplo:  

```xml
<resources>
    <string name="hello_world">¡Hola, %1$s! Hoy es %2$s.</string>
</resources>
```

En este ejemplo, **`%1$s`** y **`%2$s`** son parámetros que se reemplazarán por dos cadenas de texto: una para un nombre y otra para un día de la semana, respectivamente.

Para obtener este texto desde Kotlin y reemplazar los parámetros, utilizaremos la función **`getString()`** usando el objeto `R`[^6] y un array de argumentos:  

```kotlin
// Kotlin
val nombre = "Anselmo"
val diaSemana = "viernes"

// tvSaludo : TextView
tvSaludo.text = getString(R.string.hello_world, nombre, diaSemana)
```

La función **`getString(R.string.hello_world, nombre, diaSemana)`** busca la cadena con el ID **`R.string.hello_world`** en **`strings.xml`** y reemplaza los parámetros **`%1$s`** y **`%2$s`** por los respectivos valores de nombre y día.

Cada parámetro (**`%1$s`** y **`%2$s`**) representa:

* **Orden**: el número después del `%` indica la posición del argumento que se va a insertar.

* **Tipo de dato**: el símbolo `$s` después del número indica el tipo de formato (`$s` para cadenas, `$d` para números enteros, `$f` para números reales, etc.).

Ejemplo:  

```xml
<resources>
    <string name="precio">El precio es de %.2f euros.</string>
</resources>
```

Podemos usarlo en nuestro código de la siguiente manera:  

```kotlin
// Kotlin
val precio = 19.99
val mensajePrecio = getString(R.string.precio, precio)
```

> [!note] Recuerda que...
> ...en Java también usamos este formato `%.2f` para indicar que el número real muestre sólo **dos decimales**.







[^2]:  El tamaño de las fuentes se suele expresar con la unidad `sp`. Consultar el artículo:  
    Campos, M. (2016, 4 febrero). *Diferencias entre PX, DP y SP en Android*. OpenWebinars.net. https://openwebinars.net/blog/diferencias-entre-px-dp-y-sp-en-android/

[^3]:  *Introducción a las actividades*. (s. f.). Android Developers. https://developer.android.com/guide/components/activities/intro-activities?hl=es

[^6]:  Recuerda que el objeto `R` representa a los recursos que hay almacenados en la carpeta **`res`** del proyecto.


# 3. Referencias

## API reference

### TextView - Android Developers

* TextView. (s. f.). Android Developers. [https://developer.android.com/reference/android/widget/TextView](https://developer.android.com/reference/android/widget/TextView)

## Webs de desarrolladores

### Diseño de layouts - AristiDevs

<iframe width="560" height="315" src="https://www.youtube.com/embed/videoseries?si=KlZoBOWdwX47puTj&amp;list=PL8ie04dqq7_MGB5vNieT4Fr_fvw5t0nBC" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

> Programación by AristiDevs. ***Diseño de layouts***. (s. f.-b). YouTube. [Playlist](https://youtube.com/playlist?list=PL8ie04dqq7_MGB5vNieT4Fr_fvw5t0nBC&si=Rl4lpH9QWUi8sHRg)

### FrameLayout y LinearLayout en Kotlin (Android Studio) - Garaje de ideas

* Garaje de ideas, Tech. (2022e, septiembre 15). ***FrameLayout y LinearLayout en Kotlin (Android Studio)*** [Vídeo]. YouTube. [FrameLayout y LinearLayout en Kotlin (Android Studio)](https://www.youtube.com/watch?v=kxIjuAcFzTc)

### TextView - Introducción al Desarrollo en Android - Garaje de ideas

* Garaje de ideas, Tech. (2022a, julio 21). ***TextView - Introducción al Desarrollo en Android*** [Vídeo]. YouTube. [TextView - Introducción al Desarrollo en Android](https://www.youtube.com/watch?v=eatNSWR1SBs)

### EditText paso a paso en Android Studio - Garaje de ideas

* Garaje de ideas, Tech. (2022b, julio 28). ***EditText paso a paso en Android Studio*** (Kotlin) [Vídeo]. YouTube. [EditText paso a paso en Android Studio (Kotlin)](https://www.youtube.com/watch?v=H_Vp14ZONa0)

### Cómo crear selectores para formularios en Android con Kotlin - Garaje de ideas

* Garaje de ideas, Tech. (2022d, agosto 30). ***Cómo crear selectores para formularios en Android con Kotlin*** [Vídeo]. YouTube. [Cómo crear selectores para formularios en Android con Kotlin](https://www.youtube.com/watch?v=CKbXXzry1dg)

### Cómo usar Scrollview en Kolin (Android Studio) paso a paso - Garaje de ideas

* Garaje de ideas, Tech. (2022f, septiembre 22). ***Cómo usar Scrollview en Kolin (Android Studio) paso a paso*** [Vídeo]. YouTube. [Cómo usar Scrollview en Kolin (Android Studio) paso a paso](https://www.youtube.com/watch?v=Lcfm1wes-hg)
