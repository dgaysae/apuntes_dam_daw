---
{"dg-publish":true,"dg-permalink":"/apuntes/2-dam-pmdm/unidad-08-mvvm/","permalink":"/apuntes/2-dam-pmdm/unidad-08-mvvm/","dg-note-properties":{"modulo":"[[Módulos/PMDM]]","libro":"[[Libros/PMDM (2º DAM)]]"}}
---


```table-of-contents
maxLevel: 3
```

---

# 1. MVVM

**MVVM (Model-View-ViewModel)** es un patrón de arquitectura de software recomendado por Google para el desarrollo de aplicaciones en Android. Su objetivo principal es la **separación de responsabilidades**, permitiendo desacoplar la interfaz de usuario (UI) de la lógica de negocio y el acceso a los datos.

![ud08_pmdm_01.webp](/img/user/adjuntos/2DAM_PMDM/Unidad_08/ud08_pmdm_01.webp)

```
    +-------------------+
    |    VISTA (UI)     |  <--- Activity / Fragment / Jetpack Compose
    +-------------------+
              |  Observa estado / Envía eventos
              v
    +-------------------+
    |    VIEWMODEL      |  <--- Lógica de presentación (Sobrevive a rotaciones)
    +-------------------+
              |  Solicita datos / Procesa lógica
              v
    +-------------------+
    |      MODELO       |  <--- Lógica de negocio, Repositorios, Room, Retrofit
    +-------------------+
```

## View

La vista es la capa con la que interactúa el usuario (`Activities`, `Fragments` o `composables` de Jetpack Compose). Esta capa es la responsable de (además de mostrar la interfaz gráfica al usuario) capturar los eventos del usuario en su interacción con dicha interfaz: pulsar un botón, introducir texto, hacer scroll, etc.

> [!warning] Cuidado
> Es indispensable que cada capa del patrón asuma **su responsabilidad  y solo la suya**.

En el caso de la vista, no debe contener lógica de negocio, cálculos ni llamadas a bases de datos o APIs. Solo debe mostrar datos y notificar eventos al `ViewModel`.
    

## ViewModel

Esta capa actúa como **puente** entre la Vista y el Modelo. Su labor principal es solicitar datos al modelo cuando es necesario y preparar y mostrar los datos necesarios para la Vista, a la vez que gestiona la lógica de presentación.

> [!info] 
> Una de las cualiades del `ViewModel` es que sobrevive a situaciones como la rotación de pantalla. Es decir, si el usuario gira el dispositivo, el `ViewModel` no tiene que volver a pedir los datos a la red o BD para recargarlos en la vista.
    

## Model

Esta capa gestiona la lógica de negocio y los datos de la aplicación. Abstrae las fuentes de datos. Incluye las entidades de datos, los datos locales (Room, DataStore) y las llamadas a servicios externos (como las APIs REST con Retrofit).

Es recomendable implementarlo siguiendo el patrón **`Repository`** como punto único de entrada a los datos.

## Comunicación entre capas

La comunicación en MVVM sigue el principio de **flujo de datos unidireccional o UDF** (*Unidirectional Data Flow*):

1. **Usuario interactúa con la Vista:** Por ejemplo, pulsa el botón "Cargar usuarios".
    
2. **La Vista notifica al `ViewModel`:** Ejecuta un método del `ViewModel` (ej. `viewModel.onLoadUsersClicked()`).
    
3. **El `ViewModel` solicita datos al Modelo:** Llama al Repositorio o caso de uso.
    
4. **El `ViewModel` actualiza su estado expuesto:** Modifica un flujo de datos observable (`StateFlow` o `LiveData`).
    
5. **La Vista reacciona automáticamente:** La Vista está "escuchando" o "observando" ese estado y redibuja la UI cuando los datos cambian.

## Ventajas de usar MVVM

Como ocurría con el MVC, la separación del código en capas con responsabilidades muy marcadas ayuda a organizar el código de forma que resulta más fácil de mantener y escalar.

Además, como la lógica de negocio está ubicada en el `ViewModel` se puede probar mediante tests unitarios sin necesidad de levantar otros componentes de Android.

También, como hemos dicho antes, resuelve el problema clásico de pérdida de datos al rotar la pantalla o cambiar la configuración del dispositivo.

Esta separación favorece también la reutilización de componentes visuales, por supuesto, ya que no están acoplados a un código de acceso a datos o de lógica de negocio.

# 2. Configuración del proyecto

## 1. Fichero gradle (app)

Habilitamos el binding:

```kotlin
buildFeatures {
    viewBinding = true
}
```

Y añadimos las dependencias:

* `androidx.lifecycle:lifecycle-viewmodel-ktx:2.8.7`
  Ayuda a implementar la arquitectura MVVM. Esta librería es la que provee la clase **ViewModel**, que es la capa intermedia entre la vista (Activity o Fragment) y el modelo de datos. Se encarga de conectar la vista con el modelo y de manejar la lógica de presentación

* `androidx.lifecycle:lifecycle-livedata-ktx:2.8.7`  
  **LiveData** es un componente clave del ViewModel. Permite que la Vista se suscriba a los cambios en el Modelo de datos. Cuando el modelo cambia, LiveData notifica automáticamente a la Vista para que se actualice, utilizando el patrón Observer.

* `androidx.fragment:fragment-ktx:1.8.5`
* `androidx.activity:activity-ktx:1.10.0`

## 2. Habilitamos el binding

Habilitamos el binding en el main activity:

```kotlin
class MainActivity : AppCompatActivity() {
    private lateinit var binding : ActivityMainBinding
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        binding = ActivityMainBinding.inflate(layoutInflater)
        enableEdgeToEdge()
        setContentView(binding.root)
        ViewCompat.setOnApplyWindowInsetsListener(binding.main) { v, insets ->
           val systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars())
            v.setPadding(systemBars.left,
                        systemBars.top,
                        systemBars.right,
                        systemBars.bottom)
            insets
        }
    }
}
```

## 3. Creamos el Model

Creamos el paquete model y en él metemos Data Class + Provider:

```kotlin
data class QuoteModel(val quote: String, val author: String)

class QuoteProvider {
    companion object {
        fun getRandomQuote(): QuoteModel {
            val index = quote.indices.random()
            return quote[index]
        }
        
        private val quote = listOf<QuoteModel>(
            QuoteModel("Esta es la cita 1","fulanito 1"),
            QuoteModel("Esta es la cita 2","fulanito 2"),
            QuoteModel("Esta es la cita 3","fulanito 3"),
            QuoteModel("Esta es la cita 4","fulanito 4"),
            QuoteModel("Esta es la cita 5","fulanito 5"),
            QuoteModel("Esta es la cita 6","fulanito 6"),
            QuoteModel("Esta es la cita 7","fulanito 7"),
            QuoteModel("Esta es la cita 8","fulanito 8"),
            QuoteModel("Esta es la cita 9","fulanito 9")
        )
    }
}
```

## 4. Creamos el ViewModel

Creamos el paquete `viewmodel` y en él la clase `QuoteViewModel` que extiende de `ViewModel()` para convertirse en la capa viewmodel.

En él hemos de implementar nuestro **`livedata`** al que se suscribirá nuestra vista (nuestro activity). De esta forma, si hay un cambio en el modelo, la vista se actualizará automáticamente sin que haya que indicárselo.

```kotlin
class QuoteViewModel : ViewModel() {
    val quoteModel = MutableLiveData<QuoteModel>()
    
    fun randomQuote() {
        quoteModel.postValue(QuoteProvider.getRandomQuote())
    }
}
```

En esta clase creamos nuestra propiedad livedata que contendrá objetos del tipo implementado en nuestro ORM.

Con el método postValue de nuestro livedata se avisa a la vista (activity) de que hay algún cambio y, de esa forma, la activity hará lo que tenga que hacer…

## 5. Creamos la View

Creamos el paquete view y metemos el `MainActivity` en él.

En esta parte vamos a conectar esta vista al viewmodel. Para ello creamos la propiedad:

```kotlin
class MainActivity : AppCompatActivity() {
    private lateinit var binding : ActivityMainBinding
    private val quoteViewModel : QuoteViewModel by viewModels()
    
    override fun onCreate(...
```

La librería viewmodel proporciona la función **`by viewModels()`** que simplifica la conexión del `ViewModel` a la vista (`Activity` o `Fragment`), haciendo que la lógica y la conexión sean más manejables.

En el `onCreate` vamos a suscribir la vista al livedata. Para ello añadimos un ***observer*** que vigila la propiedad quoteModel (que es un livedata) añadimos el código:

```kotlin
override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)
    binding = ActivityMainBinding.inflate(layoutInflater)
    enableEdgeToEdge()
    setContentView(binding.root)
    ViewCompat.setOnApplyWindowInsetsListener(binding.main) {v, insets ->
       ...
    }
    
    quoteViewModel.quoteModel.observe(this, Observer {
        binding.tvQuote.text = it.quote
        binding.tvAuthor.text = it.author
    })
}
```

Y luego:

```kotlin
override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)
    ...
    
    quoteViewModel.quoteModel.observe(this, Observer {
        binding.tvQuote.text = it.quote
        binding.tvAuthor.text = it.author
    })
    
    binding.main.setOnClickListener { quoteViewModel.randomQuote() }
}
```

# 3. Referencias

## Referencias documentales

* Aris. (2023, 15 enero). ***MVVM en Android con Kotlin, LiveData y View Binding*** – Android Architecture Components. Curso Kotlin Para ANDROID. [MVVM en Android con Kotlin, LiveData y View Binding - Android Architecture Components](https://cursokotlin.com/mvvm-en-android-con-kotlin-livedata-y-view-binding-android-architecture-components/)

* Refactoring.Guru. (2026, 1 enero). ***Observer***. https://refactoring.guru/design-patterns/observer

* DevExpert - ***Programación Android y Kotlin. (2024, 15 febrero). Qué son los Patrones de Presentación: MVC, MVP, MVVM ¿Son Arquitecturas de Software?*** [Vídeo]. YouTube. https://www.youtube.com/watch?v=S3h-u4M1q3w

* Zuev, A. (2024, 6 noviembre). ***Patrón MVVM en SwiftUI*** - Adictos al trabajo. Adictos Al Trabajo. https://adictosaltrabajo.com/2020/06/05/patron-mvvm-en-swiftui/

* Casero, A. (2024, 15 marzo). ***¿Qué es el patrón Observer y cómo se usa?*** KeepCoding Bootcamps. https://keepcoding.io/blog/patron-observer-y-como-se-usa/

* Observer. (s. f.). https://refactoring.guru/es/design-patterns/observer

* Gustavo. (2019, 20 junio). ***Patrón de diseño Observer en Java***. Home. https://gustavopeiretti.com/patron-de-diseno-observer-en-java/

* 🎦 [2022] ***Arquitecturas Android (MVVM, MVP, MVC..) - Tutoriales Android Studio***. (s. f.). YouTube. https://youtube.com/playlist?list=PL8ie04dqq7_MvhtWlcIFS9L3_4EWatd-V&si=OodNc_7rPUpCFx2H
