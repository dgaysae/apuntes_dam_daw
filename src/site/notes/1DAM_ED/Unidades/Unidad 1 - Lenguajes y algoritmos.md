---
{"dg-publish":true,"permalink":"/1-dam-ed/unidades/unidad-1-lenguajes-y-algoritmos/","tags":["java/conceptos_básicos","conceptos_básicos"],"dg-note-properties":{"modulo":"[[Entornos de desarrollo]]","libro":"[[Entornos de desarrollo (1º DAM, 1º DAW)]]","descripcion":"...","orden":1,"tags":["java/conceptos_básicos","conceptos_básicos"]}}
---



<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/1-dam-programacion/unidad-01/1-introduccion/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">





Los ordenadores se han hecho para realizar tareas siguiendo un conjunto de instrucciones finitas. Esto es, un **programa**. Por su naturaleza (electrónica) manejan sólo dos posibles valores:
- **0** cuando no hay señal eléctrica.
- **1** en caso contrario.

Esta unidad de información, que puede tomar dos posibles valores, se conoce como **bit** (_**bi**nary digi**t**_). El ordenador realiza operaciones manejando bits. Esto lo hace sincronizando sus operaciones y los componentes que las realizan mediante un reloj interno que les envía pulsos. Por eso se dice que el ordenador es una **máquina síncrona**.

El ordenador realiza estas tareas cargándolas en la **memoria principal** a la que accede directamente la CPU, tomando las instrucciones a ejecutar y los datos con los que operar.

## 1.1. Programa

Estas tareas están definidas en los distintos **programas**. Un programa es un conjunto de instrucciones ordenadas y comprensibles para un ordenador y de datos que pueden usar esas instrucciones, de manera que cuando se ejecutan en el ordenador se obtiene un resultado.

Cada programa tiene como finalidad resolver un problema realizando alguna tarea concreta:

- Calcular las nóminas de una empresa.
- Navegar por Internet ([Brave](https://brave.com/es/), [Chrome](https://www.google.com/intl/es_es/chrome/), [Firefox](https://www.firefox.com/es-ES/), [Edge](https://www.microsoft.com/es-es/edge/), etc.).
- Enviar correos (Thunderbird, Outlook, etc.).

 En general, para que un programa realice su función, debe **comunicarse** de alguna manera **con el exterior** para recibir datos y devolver reusltados.

Esos datos pueden ser de distinta naturaleza, pero en todos los casos **deben convertirse en datos binarios** para que el ordenador pueda manejarlos.

## 1.2. Algoritmo

Un algoritmo es un **conjunto ordenado y finito de operaciones** que permiten hallar la solución a un problema. La implementación de algoritmos genera programas que puede ejecutar el ordenador y pueden procesar datos para devolver la solución:

![ud01_prog_01_algoritmo.png\|500](/img/user/adjuntos/1DAM_Programacion/Unidad_01/ud01_prog_01_algoritmo.png)

### 1.2.1. Carecterísticas

Un algoritmo **no debe ser ambiguo** en sus resultados, ya que será la base del algoritmo posterior. Para que un algoritmo produzca un resultado en un **tiempo finito**, debe tener las siguientes características:

- **Preciso**: establece el orden en que se realizan los pasos de la operación.
- **Definido**: si se sigue dos o más veces (con los mismos datos), se obtiene siempre el mismo resultado.
- **Finito**: hay un número determinado y finito de pasos.
- **Independiente** del lenguaje de programación en el que se codificará posteriormente.

Veamos un ejemplo de algoritmo implementado en lenguaje natural:

- Inicio.
- Pedir un número N que represente la edad de una persona.
- Si N es **mayor o igual a 18**, la persona **ES MAYOR DE EDAD**.
- Si N es **menor que 18**, la persona **ES MENOR DE EDAD**.
- Fin del programa.

Si te fijas en el algoritmo podrás comprobar que cumple todas las características de un algoritmo.

---

<p><span>🏠 <strong>Unidad:</strong> <a data-tooltip-position="top" aria-label="1DAM_Programación/Unidades/Unidad 1 - Introducción a la programación con Java.md" data-href="1DAM_Programación/Unidades/Unidad 1 - Introducción a la programación con Java.md" href="1DAM_Programación/Unidades/Unidad 1 - Introducción a la programación con Java.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 1 - Introducción a la programación con Java</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="1DAM_Programación/Unidad 01/2. Codificación de la información.md" data-href="1DAM_Programación/Unidad 01/2. Codificación de la información.md" href="1DAM_Programación/Unidad 01/2. Codificación de la información.md" class="internal-link" target="_blank" rel="noopener nofollow">2. Codificación de la información</a> ➡️</span></p>

</div></div>


| File                                                                                  | Descripción                                                                                                                                                              |
| ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [[1DAM_ED/Unidad 01/1. Software y programas\|1. Software y programas]]             | Conceptos básicos como qué es un programa, un algoritmo, cómo se representa la información en un ordenador y los distintos distemas de numeración que se usan para ello. |
| [[1DAM_ED/Unidad 01/2. Relación hardware-software\|2. Relación hardware-software]] | ...                                                                                                                                                                      |
| [[1DAM_ED/Unidad 01/3. Algoritmos\|3. Algoritmos]]                                 | ...                                                                                                                                                                      |
| [[1DAM_ED/Unidad 01/4. Lenguajes de programación\|4. Lenguajes de programación]]   | ...                                                                                                                                                                      |
| [[1DAM_ED/Unidad 01/5. Paradigmas y lenguajes\|5. Paradigmas y lenguajes]]         | ...                                                                                                                                                                      |
| [[1DAM_ED/Unidad 01/Referencias documentales\|Referencias documentales]]           | ...                                                                                                                                                                      |

{ .block-language-dataview}

---

<p><span>🏠 <strong>Libro:</strong> <a data-tooltip-position="top" aria-label="Apuntes/Entornos de desarrollo (1º DAM, 1º DAW).md" data-href="Apuntes/Entornos de desarrollo (1º DAM, 1º DAW).md" href="Apuntes/Entornos de desarrollo (1º DAM, 1º DAW).md" class="internal-link" target="_blank" rel="noopener nofollow">Entornos de desarrollo (1º DAM, 1º DAW)</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="1DAM_ED/Unidades/Unidad 2 - Ingeniería del software.md" data-href="1DAM_ED/Unidades/Unidad 2 - Ingeniería del software.md" href="1DAM_ED/Unidades/Unidad 2 - Ingeniería del software.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 2 - Ingeniería del software</a> ➡️</span></p>
