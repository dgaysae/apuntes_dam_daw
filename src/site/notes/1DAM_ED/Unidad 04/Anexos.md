---
{"dg-publish":true,"permalink":"/1-dam-ed/unidad-04/anexos/","tags":["junit","pruebas","test"],"dg-note-properties":{"unidad":"[[Unidad 4 - Pruebas, optimización y documentación]]","descripcion":"...","orden":13,"tags":["junit","pruebas","test"]}}
---


```table-of-contents
```

---

## Anexo i. Algoritmo adivinador de número

Código Java del algoritmo de [[4. Pruebas de caja blanca - análisis estructural#4.4. Caminos imposibles|camino imposible]]:

```java
public static void main(String[] args) {
   Scanner leerDeTeclado = new Scanner(System.in);
   int numeroSecreto = (new Random()).nextInt(1, 101);
   int intentos = 0;
   int numeroTentativa = 0;
   do {
       System.out.println("Introduzca un número: ");
       numeroTentativa = leerDeTeclado.nextInt();

       if (numeroTentativa < numeroSecreto) {
           System.out.println("Debe ser mayor.");
       }
       else if (numeroTentativa > numeroSecreto) {
           System.out.println("Debe ser menor.");
       }
       intentos++;
   } while (numeroTentativa != numeroSecreto);

   System.out.println("Enhorabuena! Has acertado en " + intentos + " intentos.");
   leerDeTeclado.close();
}
```



---

<p><span>⬅️ <strong>Anterior:</strong> <a data-tooltip-position="top" aria-label="1DAM_ED/Unidad 04/Referencias documentales.md" data-href="1DAM_ED/Unidad 04/Referencias documentales.md" href="1DAM_ED/Unidad 04/Referencias documentales.md" class="internal-link" target="_blank" rel="noopener nofollow">Referencias documentales</a> | 🏠 <strong>Unidad:</strong> <a data-tooltip-position="top" aria-label="1DAM_ED/Unidades/Unidad 4 - Pruebas, optimización y documentación.md" data-href="1DAM_ED/Unidades/Unidad 4 - Pruebas, optimización y documentación.md" href="1DAM_ED/Unidades/Unidad 4 - Pruebas, optimización y documentación.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 4 - Pruebas, optimización y documentación</a></span></p>