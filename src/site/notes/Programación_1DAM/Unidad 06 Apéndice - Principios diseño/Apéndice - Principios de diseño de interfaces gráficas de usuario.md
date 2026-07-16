---
{"dg-publish":true,"permalink":"/programacion-1-dam/unidad-06-apendice-principios-diseno/apendice-principios-de-diseno-de-interfaces-graficas-de-usuario/","tags":["java/swing"],"dg-note-properties":{"unidad":["[[Unidad 6 - Interfaz gráfica de usuario (GUI) - Swing]]","[[Unidad 6 - Interfaz gráfica de usuario (GUI) - JavaFX]]"],"descripcion":"Pongamos en práctica lo visto hasta ahora","orden":10,"tags":["java/swing"]}}
---


```table-of-contents
```

---

Aunque el interfaz gráfico de usuario de una aplicación debe diseñarse de forma específica para las necesidades de esa aplicación, existen algunos principios universales. No son leyes rígidas, pero han sido validados durante décadas por la experiencia en diseño y estudios de usabilidad. Muchos provienen de marcos como las heurísticas de Jakob Nielsen o las leyes de la psicología cognitiva aplicadas al diseño.

Nuestro objetivo no es convertirnos en expertos diseñadores (de hecho, hay gente especializada en ello), pero conviene que los conozcas, aunque sea someramente. En las siguientes páginas te presentamos algunos de ellos en forma de listas de “qué hacer” “qué NO hacer”, que muchas veces resulta más ilustrativo que cualquier norma.

Por favor, tómate estas ideas solo como eso, ideas, no como normas inviolables.

## Cosas que NO se deben hacer

### 1. Sobrecargar el interfaz con demasiados elementos

Un error común en el diseño de interfaces gráficas es incluir demasiados elementos en una misma pantalla, como botones, menús, colores o textos. Esto provoca una sobrecarga cognitiva en el usuario, dificultando que identifique rápidamente lo importante y tome decisiones con facilidad. Un diseño limpio y minimalista permite mejorar la usabilidad, ya que guía la atención hacia las funciones principales y reduce la confusión.

![ud06_swing_ppios_design_01.png](/img/user/attach/Unidad%2006/ud06_swing_ppios_design_01.png)

### 2. Mezclar elementos

Combinar estilos, tipografías, colores o tipos de componentes sin coherencia puede generar una experiencia visual caótica. La falta de consistencia hace que el usuario tenga que reaprender constantemente cómo interactuar con la interfaz. Mantener una línea visual uniforme y patrones claros facilita la navegación y mejora la comprensión del sistema.

![ud06_swing_ppios_design_02.png](/img/user/attach/Unidad%2006/ud06_swing_ppios_design_02.png)

### 3. Usar iconos o botones poco claros

Los iconos o botones ambiguos dificultan la interacción porque el usuario no entiende fácilmente su función. Si un elemento no es intuitivo, obliga a experimentar o cometer errores para descubrir su propósito. Es fundamental utilizar símbolos reconocibles y, cuando sea necesario, acompañarlos de etiquetas que refuercen su significado.

![ud06_swing_ppios_design_03.png](/img/user/attach/Unidad%2006/ud06_swing_ppios_design_03.png)

### 4. Obligar a dar muchos pasos para cada tarea

Cuando una interfaz requiere demasiados pasos para completar una acción, se vuelve ineficiente y frustrante. Los usuarios valoran la rapidez y la simplicidad, por lo que es importante optimizar los flujos de interacción. Reducir el número de acciones necesarias mejora la productividad y la satisfacción general.

![ud06_swing_ppios_design_04.png](/img/user/attach/Unidad%2006/ud06_swing_ppios_design_04.png)

### 5. Olvidar el rendimiento y la velocidad

Un diseño atractivo pierde valor si la interfaz es lenta o presenta retrasos. El rendimiento es clave en la experiencia del usuario, ya que tiempos de carga largos o animaciones pesadas pueden generar abandono. Optimizar recursos y asegurar una respuesta ágil contribuye a una interacción fluida y eficiente.

![ud06_swing_ppios_design_05.png](/img/user/attach/Unidad%2006/ud06_swing_ppios_design_05.png)

## Cosas que SÍ se deben hacer

### 1. Mantener la coherencia visual

Es fundamental que todos los elementos de la interfaz sigan un mismo estilo visual en cuanto a colores, tipografías, iconos y disposición. La coherencia permite que el usuario reconozca patrones y anticipe el comportamiento de los componentes, lo que reduce el esfuerzo cognitivo y mejora la experiencia general. Un diseño consistente transmite además profesionalidad y confianza.

![ud06_swing_ppios_design_06.png](/img/user/attach/Unidad%2006/ud06_swing_ppios_design_06.png)

### 2. Priorizar legibilidad y accesibilidad sobre cualquier otra consideración

El diseño debe garantizar que cualquier usuario pueda leer y comprender la información sin dificultad, independientemente de sus capacidades o del dispositivo que utilice. Esto implica elegir tamaños de texto adecuados, buen contraste de colores y estructuras claras. La accesibilidad no es opcional: mejora la inclusión y beneficia a todos los usuarios al hacer la interfaz más clara y usable.

![ud06_swing_ppios_design_07.png](/img/user/attach/Unidad%2006/ud06_swing_ppios_design_07.png)

### 3. Crear un GUI fácil e intuitivo de usar

Una buena interfaz debe poder utilizarse sin necesidad de instrucciones complejas. La intuición se logra mediante el uso de convenciones conocidas, una organización lógica y una navegación clara. Cuando el usuario entiende rápidamente cómo interactuar con el sistema, se reduce la frustración y aumenta la eficiencia en la realización de tareas.

![ud06_swing_ppios_design_08.png](/img/user/attach/Unidad%2006/ud06_swing_ppios_design_08.png)

### 4. Proporcionar retroalimentación informativa al usuario

Es importante que el sistema informe al usuario sobre lo que está ocurriendo en cada momento, ya sea mediante mensajes, animaciones o cambios visuales. La retroalimentación permite confirmar acciones, prevenir errores y mantener al usuario orientado dentro del sistema. Sin ella, la interacción puede resultar confusa e insegura.

![ud06_swing_ppios_design_09.png](/img/user/attach/Unidad%2006/ud06_swing_ppios_design_09.png)


### 5. Pensar en el tipo de usuario al que te diriges

El diseño debe adaptarse a las características, necesidades y nivel de experiencia del público objetivo. No es lo mismo diseñar para expertos que para principiantes, ni para niños que para adultos. Tener en cuenta al usuario final permite tomar decisiones más acertadas en cuanto a complejidad, lenguaje, funcionalidades y estilo, logrando una interfaz más efectiva y satisfactoria.

![ud06_swing_ppios_design_10.png](/img/user/attach/Unidad%2006/ud06_swing_ppios_design_10.png)

---

<p><span>⬅️ <strong>Anterior:</strong> <a data-tooltip-position="top" aria-label="Programación_1DAM/Unidad 06 Swing/Apéndice - recursos del proyecto.md" data-href="Programación_1DAM/Unidad 06 Swing/Apéndice - recursos del proyecto.md" href="Programación_1DAM/Unidad 06 Swing/Apéndice - recursos del proyecto.md" class="internal-link" target="_blank" rel="noopener nofollow">Apéndice - recursos del proyecto</a> | 🏠 <strong>Unidad:</strong> <a data-tooltip-position="top" aria-label="Programación_1DAM/Unidades/Unidad 6 - Interfaz gráfica de usuario (GUI) - Swing.md" data-href="Programación_1DAM/Unidades/Unidad 6 - Interfaz gráfica de usuario (GUI) - Swing.md" href="Programación_1DAM/Unidades/Unidad 6 - Interfaz gráfica de usuario (GUI) - Swing.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 6 - Interfaz gráfica de usuario (GUI) - Swing</a>,<a data-tooltip-position="top" aria-label="Programación_1DAM/Unidades/Unidad 6 - Interfaz gráfica de usuario (GUI) - JavaFX.md" data-href="Programación_1DAM/Unidades/Unidad 6 - Interfaz gráfica de usuario (GUI) - JavaFX.md" href="Programación_1DAM/Unidades/Unidad 6 - Interfaz gráfica de usuario (GUI) - JavaFX.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 6 - Interfaz gráfica de usuario (GUI) - JavaFX</a></span></p>


