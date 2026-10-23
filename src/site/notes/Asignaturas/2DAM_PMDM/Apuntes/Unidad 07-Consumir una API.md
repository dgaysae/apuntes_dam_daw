---
{"dg-publish":true,"dg-permalink":"/apuntes/2-dam-pmdm/unidad-07-consumir-una-api/","permalink":"/apuntes/2-dam-pmdm/unidad-07-consumir-una-api/","dg-note-properties":{"modulo":"[[Módulos/PMDM]]","libro":"[[Libros/PMDM (2º DAM)]]"}}
---


```table-of-contents
maxLevel: 3
```

---

# 1. Ficheros del proyecto

## 1.1. Manifest

Habilitamos permisos a nuestra app para acceso a Internet:

```xml
<uses-permission android:name="android.permission.INTERNET" />
```

## 1.2. Dependencias

Añadimos las dependencias en el fichero graddle de la app.

Para la gestión de imágenes:

* **`com.squareup.picasso:picasso`** (en su última versión)

Para la gestión del consumo de APIs REST usaremos la librería **Retrofit**. Las dependencias de esta librería son las de **Retrofit2**:

* **`com.squareup.retrofit2:retrofit`** (en su última versión)

* **`com.squareup.retrofit2:converter-gson`** (en su última versión)  
  Esta librería nos ayudará a convertir el json de la API en una *data class*.

Será necesario usar hilos (threads) que no congelen la pantalla de la app mientras se descargan los datos de la API. En Android, esos hilos se implementan mediante **corrutinas**:

* **`org.jetbrains.kotlinx:kotlinx-coroutines-android`** (en su última versión)

# 2. Bindings

Para usar el binding hemos de indicarlo en el fichero gradle del módulo:  

```kotlin
buildFeatures {
   viewBinding = true
}
```

Creamos el objeto binding en el main activity:  

```kotlin
class MainActivity : AppCompatActivity() {
    private lateinit var b : ActivityMainBinding  // este es el objeto binding
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        b = ActivityMainBinding.inflate(layoutInflater)
        enableEdgeToEdge()
        setContentView(b.root)
        ViewCompat.setOnApplyWindowInsetsListener(b.main) { v, insets ->
            val systemBars = insets
                    .getInsets(WindowInsetsCompat.Type.systemBars())
            v.setPadding(systemBars.left,
                        systemBars.top,
                        systemBars.right,
                        systemBars.bottom)
            insets
        }
    }
}
```




## 1.1. Manifest

Habilitamos permisos a nuestra app para acceso a Internet:

```xml
<uses-permission android:name="android.permission.INTERNET" />
```

## 1.2. Dependencias

Añadimos las dependencias en el fichero graddle de la app.

Para la gestión de imágenes:

* **`com.squareup.picasso:picasso`** (en su última versión)

Para la gestión del consumo de APIs REST usaremos la librería **Retrofit**. Las dependencias de esta librería son las de **Retrofit2**:

* **`com.squareup.retrofit2:retrofit`** (en su última versión)

* **`com.squareup.retrofit2:converter-gson`** (en su última versión)  
  Esta librería nos ayudará a convertir el json de la API en una *data class*.

Será necesario usar hilos (threads) que no congelen la pantalla de la app mientras se descargan los datos de la API. En Android, esos hilos se implementan mediante **corrutinas**:

* **`org.jetbrains.kotlinx:kotlinx-coroutines-android`** (en su última versión)


# 3. Vista

En el `MainActivity` vamos a hacer una vista sencilla que estará compuesta por un buscador (`SearchView`) y un listado de elementos encontrados en un `RecyclerView`:

```xml
<androidx.appcompat.widget.SearchView
   android:id="@+id/svDogs"
   android:layout_width="match_parent"
   android:layout_height="wrap_content"
   app:layout_constraintBottom_toBottomOf="parent"
   app:layout_constraintEnd_toEndOf="parent"
   app:layout_constraintHorizontal_bias="1.0"
   app:layout_constraintStart_toStartOf="parent"
   app:layout_constraintTop_toTopOf="parent"
   app:layout_constraintVertical_bias="0.0" />

<androidx.recyclerview.widget.RecyclerView
   android:id="@+id/rvDogs"
   android:layout_width="0dp"
   android:layout_height="0dp"
   app:layout_constraintBottom_toBottomOf="parent"
   app:layout_constraintEnd_toEndOf="parent"
   app:layout_constraintStart_toStartOf="parent"
   app:layout_constraintTop_toBottomOf="@+id/svDogs" />
```

Antes de continuar, comprueba que el emulador se abre correctamente. Si te diese un fallo similar a este:

```
Class 'kotlin.Unit' was compiled with an incompatible version of Kotlin. The actual metadata version is 2.1.0, but the compiler version 1.9.0 can read versions up to 2.0.0.

The class is loaded from /home/diego/.gradle/caches/modules-2/files-2.1/org.jetbrains.kotlin/kotlin-stdlib/2.1.0/85f8b81009cda5890e54ba67d64b5e599c645020/kotlin-stdlib-2.1.0.jar!/kotlin/Unit.class

```

Por último, actualiza la versión de Kotlin en el fichero **`libs.versions.toml`**


# 4. Modelo

Con la vista ya hecha, vamos a definir el **modelo de datos** que se acople bien a lo que nos va a devolver la [**API**](https://dog.ceo/dog-api/).

Vamos a atacar a este endpoint:

https://dog.ceo/api/breed/hound/images

Al abrirla en nuestro navegador vemos que nos devuelve dos campos:

* **`message`**: lista de URLs de fotos)  
* **`status`**: es la respuesta a nuestra petición. Indica si la petición se ha hecho correctamente.

![ud07_pmdm_01.png](/img/user/adjuntos/2DAM_PMDM/Unidad_07/ud07_pmdm_01.png)

Esos son los datos que recibimos al lanzar la petición a la API, por lo que haremos un modelo que la representa. Para eso creamos la data class **`DogResponse`** con esos campos:

```kotlin
data class DogResponse(
    var status: String,
    var message: List<String>)
```

Si los nombres de esos campos que nos devuelve la API no son los que queremos usar en nuestro código, podemos cambiarlos **mapeando los nombres de la API con nuestros atributos** de la siguiente manera:

```kotlin
import com.google.gson.annotations.SerializedName

data class DogResponse(
   var status: String,
   @SerializedName("message") var images: List<String>
)
```

Donde los nombres serializados (los de la API) se corresponden como vemos en el código anterior con nuestros atributos.

Ahora creamos una interfaz que defina el método para consumir los datos de la API. En dicha interfaz hemos de especificar:

* El **tipo de petición** que se va a hacer a la API. En nuestro caso, será una consulta de datos, por lo que usaremos el verbo **`GET`**.

* La función que hace la llamada. Es importante que esta función tenga un nombre significativo, acorde a la llamada que hace.

  Como esta función hará la llamada dependiendo de lo que se le pida (nosotros vamos a lanzar la petición para que nos dé imágenes de una raza concreta) debemos meterle como parámetro de entrada qué raza va a ser esa. Eso lo haremos pasándole la URL en cada caso.

  Por otro lado, el resultado de esa llamada será el tipo de dato que hemos definido anteriormente (DogResponse), pero hemos de indicar que venga como respuesta a nuestra petición. Por eso, la función devolverá un **`Response<DogResponse>`**.

Este sería el código resultante: 

```kotlin
import retrofit2.Response
import retrofit2.http.GET
import retrofit2.http.Url

interface APIService {
   @GET
   suspend fun getDogsByBreeds(@Url url : String) : Response<DogResponse>
}
```

El prefijo **`suspend`** se usa porque esta función se ejecutará en una corrutina, en un hilo secundario, por lo que se requiere este sufijo.

# 5. Retrofit

Hemos hecho el diseño del modelo de datos y la interfaz que define el tipo de llamada que vamos a hacer a la API, pero nos falta el objeto Retrofit que ejecute todo.

Para ello vamos a definir una función en el `MainActivity` que genere dicho objeto. Este objeto tendrá:

* La URL del endpoint de la API.  
* El conversor (`converter-gson`) para transformar el json a nuestro modelo de datos.  
* Demás funcionalidades y configuración para hacer estas llamadas.

```kotlin
private fun getRetrofit() : Retrofit {
   return Retrofit
       .Builder()
       .baseUrl("https://dog.ceo/api/breed/")
       .addConverterFactory(GsonConverterFactory.create())
       .build()
}
```

La forma de crear una instancia de Retrofit es mediante un Builder, así que siguiendo el código anterior vemos:

1. Cómo se crea el objeto (Builder() )  
2. La URL base, que será la que hay hasta el dato cambiante, que es la raza. Veámoslo con un ejemplo. Si quiero obtener imágenes de la raza hound, african o cotondetulear usaré la misma URL + raza + images:  
   [https://dog.ceo/api/breed/**hound**/images](https://dog.ceo/api/breed/hound/images)

   [https://dog.ceo/api/breed/**african**/images](https://dog.ceo/api/breed/african/images)

   [https://dog.ceo/api/breed/**cotondetulear**/images](https://dog.ceo/api/breed/cotondetulear/images)

   …

   Es decir, se usa la misma URL base (https://dog.ceo/api/breed/) y luego se añade una u otra raza.

3. Añadimos también el conversor para transformar el json en un objeto como el definido en nuestra data class.

## RecyclerView con datos de la API

Vamos ahora a crear el `RecyclerView` que va a contener los datos. Empezamos por el layout de cada item de la lista. Para ello creamos un nuevo Android Resource File en la carpeta `res/layout` al que llamaremos **`item_dog`**:

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.cardview.widget.CardView xmlns:android="http://schemas.android.com/apk/res/android"
   android:layout_width="match_parent"
   xmlns:app="http://schemas.android.com/apk/res-auto"
   android:layout_height="300dp"
   app:cardCornerRadius="16dp"
   android:layout_margin="8dp">

   <ImageView
       android:id="@+id/ivDog"
       android:layout_width="match_parent"
       android:layout_height="match_parent"
       android:scaleType="centerCrop" />

</androidx.cardview.widget.CardView>
```

Esta vista será de tipo `CardView`, a la que le podemos definir el redondeo de las esquinas (`cardCornerRadius`) y un margen. Contendrá un `ImageView` (`ivDog`).

Después definimos el adapter **`DogAdapter`** para el `RecyclerView`, con la inner class del **`DogViewHolder`**:

```kotlin
class DogAdapter(private val images : List<String>)
        : RecyclerView.Adapter<DogAdapter.DogViewHolder>() {
        
    override fun onCreateViewHolder(
            parent: ViewGroup,
            viewType: Int): DogViewHolder
    {
        val layoutInflater = LayoutInflater.from(parent.context)
        return DogViewHolder(
                layoutInflater
                    .inflate(R.layout.item_dog, parent, false)
        )
    }
    
    override fun getItemCount(): Int = images.size
    
    override fun onBindViewHolder(
            holder: DogViewHolder,
            position: Int)
    {
        val item = images[position]
        holder.bind(item)
    }
    
    class DogViewHolder(view: View)
            : RecyclerView.ViewHolder(view)
    {
        private val b = ItemDogBinding.bind(view)
        
        fun bind(image : String) {
            Picasso
                .get()
                .load(image)
                .into(b.ivDog)
        }
    }
}
```

Ahora iniciamos el RecyclerView en nuestro main activity con la función `initRecyclerView`. Pero antes instanciamos el adapter. También creamos una lista de imágenes vacía, ya que al arrancar la aplicación no tenemos imágenes para cargar en el adapter:

```kotlin
private lateinit var dogAdapter : DogAdapter
private val dogImages = mutableListOf<String>()
. . .
```

Esa lista es mutable porque cambiará cada vez que se reciban datos de la API.

Así, con todo esto, inicializamos el `RecyclerView` con esta función:

```kotlin
private fun initRecyclerView() {
   dogAdapter = DogAdapter(dogImages)
   b.rvDogs.layoutManager = LinearLayoutManager(this)
   b.rvDogs.adapter = dogAdapter
}
```


# 6. Corrutinas

Ya hemos estudiado los hilos (Threads) en el módulo de PSP, por lo que entendemos qué supone lanzar un hilo: ejecutar algo de forma concurrente para no paralizar toda la aplicación en el hilo principal (*main thread*).

Una corrutina es un marco de trabajo para la **ejecución de código de forma asíncrona y no bloqueante**. Es decir, permiten realizar tareas en segundo plano sin detener la interfaz de usuario (UI). Son como "hilos ligeros", pero mucho más eficientes en el uso de memoria.

Para utilizarlas hay que indicarlo en el fichero de configuración de gradle:  

```kotlin
dependencies {
    // Versión estable actual
    implementation("org.jetbrains.kotlinx:kotlinx-coroutines-android:1.7.3")
}
```

La corrutina establece su propio ámbito o *scope* para ejecutar tareas en segundo plano. Es decir, en qué contexto (o hilo) se va a ejecutar cada cosa. Esta **`CoroutineScope`** define el ciclo de vida de la corrutina.

⚠️ Si el *scope* se destruye (por ejemplo, al cerrar una pantalla), **todas sus corrutinas se cancelan automáticamente**.

Para lanzar una corrutina en Android se suele usar **`lifecycleScope`** para Activities/Fragments, aunque existen otras como **`viewModelScope`**.

Para indicar en qué hilo se debe ejecutar la tarea en cuestión se usa **`Dispatchers`**:

* **`Dispatchers.Main`** para tareas que se ejecutarán en el mismo hilo de la interfaz de usuario (p.e. actualizar un TextView, mostrar un Toast).

* **`Dispatchers.IO`** para operaciones de entrada/salida (peticiones a internet, bases de datos). Este es el habitual para realizar tareas pesadas sin bloquear la pantalla.

* **`Dispatchers.Default`** para tareas que requieren mucho uso de CPU (procesamiento de datos complejos).

Veamos un ejemplo práctico simulando una descarga pesada que puede durar varios segundos. Esta tarea actualiza un `ProgressBar` y, al terminar, muestra un mensaje en un `TextView`.

En el Layout (**`activity_main.xml`**) tenemos un `ProgressBar` con id `progressBar` y un `Button` con id `btnCargar` y el código de la activity es el siguiente:  

```kotlin
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import androidx.lifecycle.lifecycleScope
import kotlinx.coroutines.Dispatchers
import kotlinx.coroutines.delay
import kotlinx.coroutines.launch
import kotlinx.coroutines.withContext
import com.example.app.databinding.ActivityMainBinding

class MainActivity : AppCompatActivity() {
    private lateinit var binding: ActivityMainBinding
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        binding = ActivityMainBinding.inflate(layoutInflater)
        setContentView(binding.root)
        
        binding.btnCargar.setOnClickListener {
            // Lanzamos la corrutina vinculada al ciclo de vida
            // de la Activity
            lifecycleScope.launch {
                ejecutarTareaPesada()
            }
        }
    }
    
    // Función de suspensión que simula una tarea en segundo plano
    private suspend fun ejecutarTareaPesada() {
        // Mostramos el progreso (HILO PRINCIPAL)
        binding.progressBar.visibility = android.view.View.VISIBLE
        binding.tvEstado.text = "Descargando datos..."
        
        // Cambiamos al hilo de Entrada/Salida para no
        // bloquear la UI
        withContext(Dispatchers.IO) {
            // Simulamos una espera de 3 segundos
            // (ej. una descarga de red)
            delay(3000) 
        }
        
        // Volvemos automáticamente al hilo Principal
        // al salir de withContext
        binding.progressBar.visibility = android.view.View.GONE
        binding.tvEstado.text = "¡Carga completada con éxito!"
    }
}
```

En el código vemos que **`launch`** inicia la corrutina. La instrucción **`delay`** pausa la ejecución, en este caso de la corrutina, de forma que no paraliza la app. **`withContext`**(`Dispatchers.IO`) establece otro contexto en el que se ejecutará el trabajo pesado. Uno que no sea el hilo principal de la app, para que siga funcionando de forma fluida.

## En nuestro ejemplo

El problema de hacer esta petición tal cual es que la petición se lanza y tarda un tiempo el devolvernos los resultados. Esto implica que en ese tiempo nuestra aplicación se queda atascada y no se puede hacer nada con ella.

Para evitar eso, vamos a lanzar las peticiones a través de un hilo secundario usando **corrutinas**.

Para ello vamos a definir en el MainActivity la función searchByName que lanzará dicha corrutina. La forma de establecer una corrutina es la estándar según la librería que hemos instalado:

```kotlin
    private fun searchByName(query: String) {
        CoroutineScope(Dispatchers.IO).launch {
        
            // Código a ejecutar en segundo plano
            // . . .
            
            runOnUiThread {
                // Código a ejecutar en el hilo principal
                if (llamada.isSuccessful) {
                    // mostrar resultados en RecyclerView
                }
                else {
                    // mostrar error
                }
            }
        }
    }
```

Dentro de la corrutina indicamos qué queremos que se ejecute en segundo plano y qué parte afectará al hilo principal, el de nuestra pantalla (runOnUiThread):

```kotlin
private fun searchByName(query: String) {
    CoroutineScope(Dispatchers.IO).launch {
        val llamada = getRetrofit()
            .create(APIService::class.java)
            .getDogsByBreeds("$query/images")
        val perretes = llamada.body()
        
        runOnUiThread {
            if (llamada.isSuccessful) {
                // mostrar resultados en RecyclerView
            }
            else {
                // mostrar error
            }
        }
    }
}
```

Lo que ejecutaremos será:

1. Creamos el objeto Retrofit, al que le indicamos la  interfaz para definir su funcionamiento. En nuestro caso, le indicamos la interfaz que hemos creado para hacer la petición GET.

2. Con el objeto Retrofit creado, ya puedo obtener la respuesta (Response) a las llamadas que hagamos a la API. Para ello lanzamos la petición getDogsBreeds y le pasamos el resto de la URL que necesitamos para hacer la petición:

   [https://dog.ceo/api/breed/**hound/images**](https://dog.ceo/api/breed/hound/images)

   [https://dog.ceo/api/breed/**african/images**](https://dog.ceo/api/breed/african/images)

   [https://dog.ceo/api/breed/**cotondetulear/images**](https://dog.ceo/api/breed/cotondetulear/images)

   …

   https://dog.ceo/api/breed/**\$query**/images

3. Con esa respuesta (Response):
   - si es correcta mostraremos los resultados (si los hay).
   - si no es correcta mostraremos un error.

## Completar la corrutina

Ahora que tenemos todos los componentes vamos a completar la corrutina:

```kotlin
private fun searchByName(query: String) {
    CoroutineScope(Dispatchers.IO).launch {
        val llamada = getRetrofit()
            .create(APIService::class.java)
            .getDogsByBreeds("$query/images")
        val perretes = llamada.body()
        
        runOnUiThread {
            if (llamada.isSuccessful) {
                val images = perretes?.images ?: emptyList()
                dogImages.clear()
                dogImages.addAll(images)
                dogAdapter.notifyDataSetChanged()
            }
            else {
                Toast.makeText(
                    this@MainActivity,
                    "ERROR! Algo ha fallado...",
                    Toast.LENGTH_SHORT
                    )
                .show()
            }
        }
    }
}
```


# 7. El buscador

Para que el buscador funcione en el MainActivity hemos de indicar a esta clase que implementen el SearchView.OnQueryTextListener:

```kotlin
import androidx.appcompat.widget.SearchView.OnQueryTextListener
...
class MainActivity : AppCompatActivity(), SearchView.OnQueryTextListener {
```

Esto nos obligará a implementar dos métodos:

```kotlin
// Este se ejecuta cuando se lanza la búsqueda
override fun onQueryTextSubmit(p0: String?): Boolean {
    if (!p0.isNullOrBlank()) {
        searchByName(p0.lowercase(Locale.ROOT))
    }
    return true
}

// Este se ejecuta cada vez que se detecta un cambio en el texto
// del buscador. No lo vamos a usar por ahora.
override fun onQueryTextChange(p0: String?): Boolean {
    return true
}
```

# Referencias

* 🎦 Programación Android by AristiDevs. (2021, 18 febrero). ***[Tutorial] RETROFIT 2 en KOTLIN con CORRUTINAS - Consumir API JSON en Android Studio en Español 2022*** [Vídeo]. YouTube. https://www.youtube.com/watch?v=aQP-mUGWh1U

* Aris. (2023, 15 enero). ***Capítulo 20 – Consumiendo APIS con Retrofit 2***. Curso Kotlin Para ANDROID. https://cursokotlin.com/capitulo-20-consumiento-apis-retrofit-2/

* Aris. (2023b, enero 15). ***Tutorial Retrofit 2 en Kotlin con Corrutinas – Consumiendo API [Capítulo 20 v2]***. Curso Kotlin Para ANDROID. https://cursokotlin.com/tutorial-retrofit-2-en-kotlin-con-corrutinas-consumiendo-api-capitulo-20-v2/

* ZuRamos, J. (2022, 13 noviembre). Android: ***Cómo consumir una API y procesar respuestas JSON 🎯 Retrofit***. Programación y Más. https://programacionymas.com/blog/consumir-una-api-usando-retrofit
