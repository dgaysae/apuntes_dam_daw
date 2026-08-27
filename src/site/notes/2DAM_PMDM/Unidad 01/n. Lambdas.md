---
{"dg-publish":true,"permalink":"/2-dam-pmdm/unidad-01/n-lambdas/","tags":["kotlin/variables","kotlin/constantes","kotlin/inferencia","kotlin/tipos_de_datos"],"dg-note-properties":{"unidad":"[[2DAM_PMDM/Unidades/Unidad 1 - Introducción a Kotlin]]","descripcion":"Tipos de datos en Kotlin.","orden":3,"tags":["kotlin/variables","kotlin/constantes","kotlin/inferencia","kotlin/tipos_de_datos"]}}
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







## Rehaciendo ejemplos anteriores

Retomando el [[6. Collections#List inmutables|ejemplo]] que usamos para explicar la función `emptyList()`, podemos rehacerlo con expresiones lambda de la forma siguiente:

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

---

<p><span>⬅️ <strong>Anterior:</strong> <a data-tooltip-position="top" aria-label="2DAM_PMDM/Unidad 01/2. Inferencia de tipos.md" data-href="2DAM_PMDM/Unidad 01/2. Inferencia de tipos.md" href="2DAM_PMDM/Unidad 01/2. Inferencia de tipos.md" class="internal-link" target="_blank" rel="noopener nofollow">2. Inferencia de tipos</a> | 🏠 <strong>Unidad:</strong> <a data-tooltip-position="top" aria-label="2DAM_PMDM/Unidades/Unidad 1 - Introducción a Kotlin.md" data-href="2DAM_PMDM/Unidades/Unidad 1 - Introducción a Kotlin.md" href="2DAM_PMDM/Unidades/Unidad 1 - Introducción a Kotlin.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 1 - Introducción a Kotlin</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="2DAM_PMDM/Unidad 01/4. static en Kotlin.md" data-href="2DAM_PMDM/Unidad 01/4. static en Kotlin.md" href="2DAM_PMDM/Unidad 01/4. static en Kotlin.md" class="internal-link" target="_blank" rel="noopener nofollow">4. static en Kotlin</a> ➡️</span></p>