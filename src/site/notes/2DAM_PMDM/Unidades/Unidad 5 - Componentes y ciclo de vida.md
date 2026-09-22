---
{"dg-publish":true,"permalink":"/2-dam-pmdm/unidades/unidad-5-componentes-y-ciclo-de-vida/","tags":["android/ciclo_de_vida"],"dg-note-properties":{"modulo":"[[Módulos/PMDM]]","libro":"[[Apuntes/PMDM (2º DAM)]]","descripcion":"Fases por las que pasa una app Android desde que se abre. Componentes básicos de una app.","orden":5,"tags":["android/ciclo_de_vida"]}}
---


Los componentes básicos[^1] en una app Android son las ***activities[^7]***, los **servicios[^2]**, los ***broadcast receivers[^3]*** (mediante *Intents[^4]*.) y por último los ***content providers[^5]*** o proveedores de contenido para **compartir información entre distintas aplicaciones**.

Existen otros elementos, como los ***widgets[^6]***, que veremos más adelante.

## Activities

Una **`activity`** o actividad se puede definir como una **pantalla de la app con funcionalidad**.

Hay que tener en cuenta que la pantalla de un dispositivo móvil es mucho más pequeña que la de un ordenador y, por tanto, no caben tantas opciones. Además, un dispositivo móvil está más limitado en recursos (aunque cada vez menos): las memorias, los discos... deben ser de un tamaño minúsculo para que quepan en un aparato tan pequeño. Esto pone más límites que un ordenador.

### Ciclo de vida

Las `activities` nacen y mueren a lo largo de la ejecución de una app siguiendo el siguiente ciclo:

![activity_lifecycle.png](/img/user/adjuntos/2DAM_PMDM/Unidad_05/activity_lifecycle.png)

> *Ciclo de vida de la actividad*. (s. f.). Android Developers. https://developer.android.com/guide/components/activities/activity-lifecycle?hl=es#alc

En él se indican los pasos que sigue una `activity` para arrancar. Estos pasos se ejecutan en los métodos que se indican a continuación y que se ejecutan de forma transparente para el usuario y el programador. Entonces, ¿por qué crear métodos para esto? Porque el programador puede sobreescribirlos y decidir qué hacer en cada uno de estos pasos.

Los primeros métodos del ciclo de vida de la `activity` son:

1. **`onCreate()`** - Este método carga la `activity` (su código y recursos asociados) en memoria.

2. **`onStart()`** - La activity, cargada en memoria en el paso anterior, se empieza a ejecutar. Pero no está disponible aún para el usuario (no es visible).

3. **`onResume()`** - La activity se hace visible para el usuario y le permite interactuar con ella.

A partir de aquí, la `activity` ya está corriendo y puede pasar a uno de los estados determinados por los siguientes métodos.

#### `onPause()`
Si se detecta que otra aplicación más prioritaria que esta `activity` necesita mostrarse al usuario (p.e. una llamada de teléfono), la `activity` que se está ejecutando pasa a estar en pausa. En este "limbo", la `activity` pierde el enfoque principal y deja de estar en primer plano, aunque **todavía puede ser visible** de forma parcial (p.e. si se abre un cuadro de diálogo transparente o en modo multiventana).

En este estado, el usuario no puede interactuar con la interfaz de esta actividad.

En caso de que el programador sobreescriba el `onPause()`, debe hacerlo con cuidado. Hay que tener en cuenta que este método se ejecuta para dar paso a otra `activity` de más prioridad y no debe hacer esperar al usuario.

La ejecución del `onPause()` es la transición a otra pantalla. Es decir, que la otra pantalla se detiene hasta que este método termina. En esta transición se deben pausar o detener elementos pesados que consumen batería o hardware, como animaciones, reproducción de música o sensores (cámara, GPS, etc.).

Lo recomendable es sobreescribir este método si necesitamos guardar datos rápidos de última hora, pausar animaciones o liberar componentes de hardware. Pero si la pantalla es puramente informativa, no es necesario tocar este método.

> [!info] Para sobreescribir este método heredado...
> ... es conveniente llamar al método de la superclase:
> ```kotlin
> super.onPause()
> ```
> Y esto se hace **extensible al resto de métodos del ciclo de vida**.



El `onPause()` se activa cuando se abre una nueva `activity` semitransparente, cuando un diálogo por encima, cuando el usuario cambia a otra aplicación o interactúa en modo multiventana o cuando el sistema operativo (Android) indica que debe entrar en juego otra app más prioritaria (las llamadas de teléfono, por ejemplo).

#### `onStop()`

Este método se ejecuta cuando acaba el `onPause()`.

Aquí la ejecución de nuestra `activity` se detiene y **deja de estar visible** para el usuario. Desde aquí podemos volver a ejecutar la `activity` mediante **`onRestart()`** (si sigue cargada en memoria) o volver a arrancarla llevándola a **`onCreate()`**.

A diferencia de `onPause()`, donde la actividad aún puede verse de fondo, en `onStop()` **la pantalla queda totalmente oculta**.

En este estado donde se recomienda liberar recursos que no se necesitan si el usuario no está viendo la pantalla. Aquí es donde se deben desconectar bases de datos, detener animaciones complejas, pausar animaciones pesadas o cancelar peticiones de red.

En cuanto al guardado de datos pesados para recordar el estado de tu `activity`, solía usarse el `onPause()`. Pero, como indicábamos en el apartado anterior, para agilizar las transiciones entre pantallas, ahora Google recomienda usar `onStop()`. Las operaciones como el guardado de datos pesados en la base de datos local (como Room), por ejemplo, es mejor hacerlas aquí.

En este estado las `activities` siguen manteniéndose en la memoria RAM. Peeeeero si el sistema operativo ve que se queda sin memoria para otras aplicaciones que deben estar en primer plano, puede **matar el proceso** de nuestra aplicación **sin previo aviso**. Por eso se puede ver en el diagrama anterior una flechita al proceso "**App process killed**".

Este método se ejecuta cuando el usuario presiona el botón **Home** (Inicio) para ir al escritorio de su teléfono, cuando se abre una **nueva actividad a pantalla completa** que tapa por completo a la anterior, cuando el usuario abre el menú de **aplicaciones recientes** y cambia a otra app, etc. En definitiva, cuando nuestra `activity` deja de estar visible para el usuario.

#### `onDestroy()`

Esta es la **última etapa** en el ciclo de vida de una `activity` y se ejecuta justo antes de que la actividad sea eliminada por completo de la memoria RAM del dispositivo.

Cuando decimos que se elimina de memoria, recordemos que eso significa que la instancia del objeto de esa `activity` muere y con ella todos los componentes visuales y variables locales vinculados a ella.

En este estado hay que liberar todos aquellos recursos que no se hayan cerrado en `onStop()`, como hilos de ejecución en segundo plano (`threads`) o liberar referencias que podrían causar fugas de memoria (`memory leaks`).

Este método **podría no llegar a ejecutarse** si el sistema operativo se queda sin memoria crítica mientras la app está en segundo plano. En estos casos puede decidir matar el proceso completo de la aplicación. Por eso, **no es el mejor lugar para guardar datos relevantes**. Mejor lo hacemos en el `onStop()`, ¿no?

El `onDestroy()` puede activarse por dos motivos:

1. **Por petición del usuario o del código**: el usuario presiona el botón "Atrás", desliza la app para cerrarla desde el menú de aplicaciones recientes, o nosotros como programador llamamos explícitamente al método `finish()`.
2. **Por cambios de configuración**: esto ocurre de forma automática cuando el usuario **gira la pantalla** (pasa de vertical a horizontal) o cambia el idioma del sistema. En este caso, **Android destruye la actividad actual y crea una completamente nueva** en cuestión de milisegundos para adaptar el diseño. Esto se puede identificar usando el método `isFinishing()`.

### `View`

Esta es la clase madre de la que heredan los distintos elementos visuales en una `activity`: botones, desplegables, etc.

En Android, una **`View`** (Vista) es la clase sobre la que se crean el resto de componentes visuales de la la interfaz de usuario. Es un objeto que **dibuja algo en la pantalla con lo que el usuario puede interactuar**.

Todo lo que el usuario ve y toca en la aplicación (botones, textos, imágenes, campos de formulario) es una `View`.

![different-views-in-one-image.webp](/img/user/adjuntos/2DAM_PMDM/Unidad_05/different-views-in-one-image.webp)
> Mewada, P. (2023, 5 octubre). *View and ViewGroup in Android* - Scaler Topics. Scaler Topics. https://www.scaler.com/topics/view-in-android/


Para entenderlas mejor, el ecosistema de Android las divide en dos grupos:

1. Componentes visuales o *widgets*.
2. Contenedores (`ViewGroup`)

![view-arbol_herencia.png](/img/user/adjuntos/2DAM_PMDM/Unidad_05/view-arbol_herencia.png)

#### Componentes visuales - `Widgets`

Son las vistas individuales con funciones específicas. Por ejemplo:

- **`TextView`** sirve para mostrar texto en la pantalla.
- **`Button`** muestra un botón que ejecuta una acción al ser presionado.
- **`ImageView`** sirve para mostrar fotos, iconos o gráficos.
- **`EditText`** es un campo donde el usuario puede escribir texto.

#### Contenedores - `ViewGroup`

Un `ViewGroup` es, en esencia, un contenedor (layout) que nos permite agrupar varios views en él. Es un tipo especial de `View` que no dibuja nada por sí mismo. Su única función es **contener otras vistas y organizar su posición** en la pantalla (arriba, abajo, en lista, en cuadrícula). De `ViewGroup` cuelgan clases como  `LinearLayout`, `ConstraintLayout` o `RecyclerView` (que estudiaremos más adelante). 

Fíjate en el siguiente pantallazo, donde cada cuadro es un `ViewGroup` que contiene un texto (`TextView`) y una imagen (`ImageView`).:

![viewgroup-app_amazon.jpeg](/img/user/adjuntos/2DAM_PMDM/Unidad_05/viewgroup-app_amazon.jpeg)

> Fuente: Acosta, L. (2022, 19 septiembre). *Cómo descargar, crear una cuenta y comprar desde la aplicación de Amazon Compras en México*. Xataka México. https://www.xataka.com.mx/telecomunicaciones/como-descargar-crear-cuenta-comprar-aplicacion-amazon-compras-mexico

## Referencias

* Aspectos fundamentales de la app. (s. f.). Android Developers. https://developer.android.com/guide/components/fundamentals?hl=es#Components


[^1]:  Aspectos fundamentales de la app. (s. f.). Android Developers.  
    [https://developer.android.com/guide/components/fundamentals?hl=es\#Components](https://developer.android.com/guide/components/fundamentals?hl=es#Components)

[^2]:  Descripción general de los servicios. (s. f.). Android Developers.  
    [https://developer.android.com/develop/background-work/services?hl=es-419](https://developer.android.com/develop/background-work/services?hl=es-419)

[^3]:  Descripción general de las transmisiones. (s. f.). Android Developers.  
    [https://developer.android.com/develop/background-work/background-tasks/broadcasts?hl=es-419](https://developer.android.com/develop/background-work/background-tasks/broadcasts?hl=es-419)

[^4]:  Intents y filtros de intents. (s. f.). Android Developers.  
    [https://developer.android.com/guide/components/intents-filters?hl=es-419](https://developer.android.com/guide/components/intents-filters?hl=es-419)

[^5]:  Conceptos básicos sobre proveedores de contenido. (s. f.). Android Developers.  
    [https://developer.android.com/guide/topics/providers/content-provider-basics?hl=es-419](https://developer.android.com/guide/topics/providers/content-provider-basics?hl=es-419)

[^6]:  Cómo crear un widget simple. (s. f.). Android Developers.  
    [https://developer.android.com/develop/ui/views/appwidgets?hl=es-419\#ProviderBroadcasts](https://developer.android.com/develop/ui/views/appwidgets?hl=es-419#ProviderBroadcasts)

[^7]:  Introducción a las actividades. (s. f.). Android Developers.  
    [https://developer.android.com/guide/components/activities/intro-activities?hl=es](https://developer.android.com/guide/components/activities/intro-activities?hl=es)




---

<p><span>⬅️ <strong>Anterior:</strong> <a data-tooltip-position="top" aria-label="2DAM_PMDM/Unidades/Unidad 4 - Estructura de un proyecto Android.md" data-href="2DAM_PMDM/Unidades/Unidad 4 - Estructura de un proyecto Android.md" href="2DAM_PMDM/Unidades/Unidad 4 - Estructura de un proyecto Android.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 4 - Estructura de un proyecto Android</a> | 🏠 <strong>Libro:</strong> <a data-tooltip-position="top" aria-label="Apuntes/PMDM (2º DAM).md" data-href="Apuntes/PMDM (2º DAM).md" href="Apuntes/PMDM (2º DAM).md" class="internal-link" target="_blank" rel="noopener nofollow">PMDM (2º DAM)</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="2DAM_PMDM/Unidades/Unidad 6 - Comenzamos.md" data-href="2DAM_PMDM/Unidades/Unidad 6 - Comenzamos.md" href="2DAM_PMDM/Unidades/Unidad 6 - Comenzamos.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 6 - Comenzamos</a> ➡️</span></p>
