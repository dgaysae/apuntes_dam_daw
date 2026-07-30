---
{"dg-publish":true,"permalink":"/1-dam-ed/unidad-02-requisitos/requisitos-funcionales-y-no-funcionales/","tags":["ingeniería_sw"],"dg-note-properties":{"unidad":"[[Unidad 2 - Ingeniería del software]]","descripcion":"...","orden":1,"tags":["ingeniería_sw"]}}
---


```table-of-contents
```

---

# 1. Requisitos funcionales

Los requisitos funcionales de un software se suelen registrar en la matriz de trazabilidad de requisitos y en la especificación de requisitos de software, este último, documenta las operaciones y actividades que el sistema debe poder desempeñar.

Entre los posibles requisitos funcionales de un sistema, se incluyen:

* Descripciones de los datos a ser ingresados en el sistema.

* Descripciones de las operaciones a ser realizadas por cada pantalla.

* Descripción de los flujos de trabajo realizados por el sistema.

* Descripción de los reportes del sistema y otras salidas.

* Definición de quién puede ingresar datos en el sistema.

Como el sistema cumplirá los reglamentos y regulaciones de sector o generales que le sean aplicables.

Al igual que otros tipos de requisitos de software, como por ejemplo los requisitos no funcionales, los requisitos funcionales se pueden clasificar según su finalidad, como por ejemplo requisitos de negocio, requisitos originados en aspectos regulatorios, de seguridad, entre otros.

Los requisitos funcionales deben redactarse de tal forma que el lector pueda entender el funcionamiento del sistema sin tener conocimientos técnicos particulares de su funcionamiento.

Lo importante es definir una forma **estándar** para expresar los requisitos y ser consistente con la misma en todos los documentos.

Asimismo, los requisitos funcionales no necesariamente tienen que definirse en forma de narrativas escritas, sino que también pueden utilizarse **diagramas** o **flujos de procesos**, los cuales se incluyen en la especificación funcional del software o sistema a desarrollar.

Para identificar y documentar los requisitos funcionales de software se siguen dos pasos.

En primer lugar se aplican técnicas de levantamiento de requisitos, tales como la **observación**, **entrevistas**, etc. El resultado del levantamiento de requisitos se documenta en el documento de requisitos de software.

Entre los posibles requisitos funcionales de un sistema, se incluyen:

* Descripciones de los datos a ser ingresados en el sistema.

* Descripciones de las operaciones a ser realizadas por cada pantalla.

* Descripción de los flujos de trabajo realizados por el sistema.

* Descripción de los reportes del sistema y otras salidas.

* Definición de quién puede ingresar datos en el sistema.

* Como el sistema cumplirá los reglamentos y regulaciones de sector o generales que le sean aplicables.

A continuación te presentamos los ejemplos de requisitos funcionales, clasificados por distintas áreas.

## 1.1. Ejemplos de requisitos funcionales

### 1.1.1. Requisitos de proceso o área de negocio

* El sistema enviará un correo electrónico cuando se registre alguna de las siguientes transacciones: pedido de venta de cliente, despacho de mercancía al cliente, emisión de factura a cliente y registro de pago de cliente.

* Se permitirá el registro de pedidos de compra con datos obligatorios incompletos, los cuales podrán completarse posteriormente modificando el pedido. Antes de poder aprobarse los datos del pedido deben estar completos.

* Al aprobar un pedido, la solicitud pasará al siguiente paso del flujo de trabajo (workflow) de aprobación configurado en el sistema.

* El sistema permitirá a los usuarios autorizados el ingresar planes y cronogramas de proyecto.

* El sistema permitirá aprobar, cambiar o actualizar planes y cronogramas de proyecto.

* El sistema permitirá el envío automatizado de cartas de entrega de órdenes directamente al almacén.

* A cada orden se le asignará un identificador único, que será utilizado para identificarla en todos los procesos subsecuentes que se realicen sobre esta.

* Al ingresar órdenes de entrega, toda orden de entrega estará asociada a un pedido de venta.

* La facturación de pedidos de venta se realizará en lotes, por medio de una pantalla de pedidos pendientes de facturación, la cual mostrará los pedidos no facturados. Una vez facturados los pedidos no se mostrarán en esta lista.

* El sistema también permitirá el registro de facturas manuales no asociadas a pedidos, sin embargo, estas requerirán autorización por parte del grupo de Gerentes antes de ser contabilizadas.

* El proceso de compras en el sistema abarcará los siguientes pasos y transacciones: Ingreso de la requisición, emisión de la solicitud de cotización y emisión de la orden de compra.

* Los elementos de la solicitud de cotización serán los mismos de la requisición asociada, al igual que los de la orden de compra. El sistema permitirá la emisión de solicitudes de cotización y órdenes de compra parciales.

* La contabilización de transacciones de facturas de venta y facturas de compra podrá configurarse para realizarse de forma automatizada a su registro, o manualmente en lotes (Proceso Batch).

* El software debe poder emitir los siguientes estados financieros: Balance general, Estado de ganancias y pérdidas, Estado de flujos de efectivo. Además, debe poder emitir un listado de mayor general y mayor analítico.

* Los pedidos de compra que excedan los montos establecidos en el flujo de liberaciones de pedidos configurados, deberán pasar por las aprobaciones establecidas en dicho flujo de aprobación.

### 1.1.2. Requisitos de interfaz gráfica

* La solución validará automáticamente el cliente asociado a una orden con el sistema de gestión de contactos.

* El campo de monto acepta únicamente valores numéricos con dos decimales.

* El campo fecha de transacción acepta únicamente fechas anteriores al día de hoy (día actual).

* El campo nombre acepta caracteres alfabéticos únicamente.

* El campo dirección acepta caracteres alfabéticos, numéricos y especiales.

* El campo país consistirá en una lista de preselección. El país asociado a una dirección debe ser previamente registrado en el sistema.

* El campo estado, provincia o departamento consistirá en una lista de preselección. A los usuarios se les presentará únicamente los estados asociados al país seleccionado previamente. El departamento o provincia a seleccionar deberá ser registrado en la funcionalidad correspondiente.

* El campo material de elemento de la pantalla de requisiciones de compra será una lista de preselección, que mostrará únicamente los materiales registrados en el maestro de materiales.

* El campo fecha contable acepta únicamente fechas que correspondan con periodos contables que estén abiertos en el sistema.

* La pantalla de registro de pago puede imprimir los datos en pantalla a la impresora.

* Se mostrará el nombre, tamaño total, espacio disponible y formato de un pen drive o flash drive conectado al puerto USB del computador.

### 1.1.3. Requisitos legales o regulatorios

* El sistema controlará el acceso y lo permitirá solamente a usuarios autorizados.

* La base de datos será implementada con trazas de auditoría.

* Las hojas de cálculo asegurarán los datos usando firmas electrónicas.

* El sistema permitirá elaborar y emitir el reporte regulatorio XX, según los requisitos establecidos en el reglamento y ley aplicable.

* Los libros de venta y de compras serán emitidos en el formato establecido por las autoridades tributarias de dicha materia.

### 1.1.4. Requisitos de seguridad

* El sistema controlará el acceso y lo permitirá solamente a usuarios autorizados. Los usuarios deben ingresar al sistema con un nombre de usuario y contraseña.

* El sistema enviará una alerta al administrador del sistema cuando ocurra alguno de los siguientes eventos: Registro de nueva cuenta, ingreso al sistema por parte del cliente, 2 o más intentos fallidos en el ingreso de la contraseña de usuario y cambio de contraseña de usuario.

* Los integrantes del grupo de usuarios de analistas pueden ingresar solicitudes pero no pueden aprobarlas o borrarlas.

* Los integrantes del grupo de usuarios de gerentes pueden ingresar y aprobar solicitudes, pero no pueden borrarlas.

* Los integrantes del grupo de usuario de administradores no pueden ingresar o aprobar solicitudes, pero si pueden borrarlas.

* Cualquier intercambio de datos vía internet que realice el software se realizará por medio del protocolo encriptado https.

### 1.1.5. Requisitos de interfaces externas (Hardware y Software)

* El software podrá ser utilizado en los sistemas operativos Windows, Linux y OSX.

* La aplicación debe poder utilizarse sin necesidad de instalar ningún software adicional además de un navegador web.

* La aplicación debe poder utilizarse con los navegadores web Chrome, Firefox e Internet Explorer.

# 2. Requisitos no funcionales

Los requisitos no funcionales representan características generales y restricciones de la aplicación o sistema que se esté desarrollando.

Suelen presentar dificultades en su definición dado que su conformidad o no conformidad podría ser sujeto de libre interpretación, por lo cual es recomendable acompañar su definición con criterios de aceptación que se puedan medir.

Entre los ejemplos de requisitos no funcionales presentados, tenemos los referidos a atributos como la eficiencia, seguridad, dependencia y usabilidad del sistema. También presentamos ejemplos de requisitos no funcionales organizacionales y externos.

En un primer nivel, los requisitos no funcionales pueden clasificarse en requisitos de producto, organizacionales y externos, tal como te mostramos en el artículo sobre clasificación de los requisitos no funcionales.

En un segundo nivel, los requisitos de producto pueden clasificarse en requisitos de usabilidad, eficiencia, dependencia y seguridad. A su vez, los requisitos organizacionales pueden clasificarse en requisitos de entorno, organizacionales y de desarrollo. Asimismo, los requisitos externos pueden clasificarse en requisitos regulatorios, éticos y legislativos.

Cuando se realizan las fases de levantamiento y análisis de requisitos, los requisitos no funcionales se pueden registrar en un documento de requisitos de software.

Los requisitos no funcionales suelen expresarse de una manera general y sin hacer referencia a ningún módulo, transacción o característica del sistema, ya que al hacerlo pasarían a ser requisitos funcionales.

Los requisitos no funcionales pueden a su vez derivar en requisitos funcionales, tomando como ejemplo el anterior:

El sistema incluirá un procedimiento de autorización de usuarios, en el cual los usuarios deben identificarse usando un nombre de usuario y contraseña. Sólo los usuarios autorizados de esta forma podrán acceder a los datos del sistema.

Escrito de esta forma, el requerimiento pasa a ser funcional.

## 2.1. Ejemplos de requisitos no funcionales

### 2.1.1. Requisitos de producto

#### Eficiencia

* El sistema debe ser capaz de procesar N transacciones por segundo. Esto se medirá por medio de la herramienta SoapUI aplicada al Software Testing de servicios web.

* Toda funcionalidad del sistema y transacción de negocio debe responder al usuario en menos de 5 segundos.

* El sistema debe ser capaz de operar adecuadamente con hasta 100.000 usuarios con sesiones concurrentes.

* Los datos modificados en la base de datos deben ser actualizados para todos los usuarios que acceden en menos de 2 segundos.

#### Seguridad lógica y de datos

* Los permisos de acceso al sistema podrán ser cambiados solamente por el administrador de acceso a datos.

* El nuevo sistema debe desarrollarse aplicando patrones y recomendaciones de programación que incrementen la seguridad de datos.

* Los permisos de acceso al sistema podrán ser cambiados solamente por el administrador de acceso a datos.

* El nuevo sistema debe desarrollarse aplicando patrones y recomendaciones de programación que incrementen la seguridad de datos.

#### Seguridad industrial

* El sistema no continuará operando si la temperatura externa es menor a 4 grados Celsius.

* El sistema no continuará operando en caso de fuego. (Ej. Un ascensor).

#### Usabilidad

* El tiempo de aprendizaje del sistema por un usuario deberá ser menor a 4 horas.

* La tasa de errores cometidos por el usuario deberá ser menor del 1% de las transacciones totales ejecutadas en el sistema.

* El sistema debe contar con manuales de usuario estructurados adecuadamente.

* El sistema debe proporcionar mensajes de error que sean informativos y orientados al usuario final.

* El sistema debe contar con un módulo de ayuda en línea.

* La aplicación web debe poseer un diseño “Responsive” a fin de garantizar la adecuada visualización en múltiples computadores personales, dispositivos tableta y teléfonos inteligentes.

* El sistema debe poseer interfaces gráficas bien formadas.

#### Dependencia

* El sistema debe tener una disponibilidad del 99,99% de las veces que un usuario intente acceder a él.

* El tiempo para iniciar o reiniciar el sistema no podrá ser mayor a 5 minutos.

* La tasa de tiempos de falla del sistema no podrá ser mayor al 0,5% del tiempo de operación total.

* El promedio de duración de fallas no podrá ser mayor a 15 minutos.

* La probabilidad de falla del Sistema no podrá ser mayor a 0,05.

#### Otros ejemplos de requisitos de producto

* El sistema será desarrollado para las plataformas PC y Macintosh.

* La aplicación debe ser compatible con todas las versiones de Windows, desde Windows 95\.

* La aplicación deberá consumir menos de 500 Mb de memoria RAM.

* La aplicación no podrá ocupar más de 2 GB de espacio en disco.

* La nueva aplicación debe manejar fuentes del alfabeto en Inglés, Idiomas latinos (Español, Frances, Portugués, Italiano), Arábico y Chino.

* La interfaz de usuario será implementada para navegadores web únicamente con HTML5 y JavaScript.

  2. ### Requisitos organizacionales {#requisitos-organizacionales}

* El procedimiento de desarrollo de software a usar debe estar definido explícitamente (en manuales de procedimientos) y debe cumplir con los estándares ISO 9000\.

* La metodología de desarrollo de software será Behaviour Driven Development (BDD) apoyada en Cucumber.

* El sistema debe ser desarrollado utilizando las herramientas CASE XYZ.

* El proceso de desarrollo se gestionará por medio de una determinada herramienta web para gestionar el proceso de desarrollo de software.

* Debe especificarse un plan de recuperación ante desastres para el sistema a ser desarrollado.

* Cada dos semanas deberán producirse reportes gerenciales en los cuales se muestre el esfuerzo invertido en cada uno de los componentes del nuevo sistema.

* Las pruebas de software se gestionarán con una herramienta de gestión de software testing.

* Las pruebas de software se ejecutarán utilizando Selenium y Ruby como herramienta y lenguaje Scripting para automatización de software testing.

  3. ### Requisitos externos {#requisitos-externos}

* Sistemas de datos médicos: El nuevo sistema y sus procedimientos de mantenimiento de datos deben cumplir con las leyes y reglamentos de protección de datos médicos.

* El nuevo sistema se acogerá a las reglas de las licencias generales públicas (GNU), es decir será gratuito, código abierto en el que cualquiera podrá cambiar el software, sin patentes y sin garantías.

* Las páginas web a ser desarrolladas deben cumplir con la ley de tratamiento en condiciones de igualdad para personas con discapacidad.

* El sistema no revelará a sus operadores otros datos personales de los clientes distintos a nombres y números de referencia.

# Referencias

* Tech, M. (2025, 11 mayo). ***Requerimientos Funcionales y No Funcionales: qué son, en qué se diferencian y por qué son clave en el diseño de software***. Mentores Tech. https://www.mentorestech.com/resource-blog-content/requerimientos-funcionales-y-no-funcionales-que-son-en-que-se-diferencian-y-por-que-son-clave-en-el-diseno-de-software

---

<p><span>🏠 <strong>Unidad:</strong> <a data-tooltip-position="top" aria-label="1DAM_ED/Unidades/Unidad 2 - Ingeniería del software.md" data-href="1DAM_ED/Unidades/Unidad 2 - Ingeniería del software.md" href="1DAM_ED/Unidades/Unidad 2 - Ingeniería del software.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 2 - Ingeniería del software</a> | <strong>Siguiente:</strong> <a data-tooltip-position="top" aria-label="1DAM_ED/Unidad 02/2. Análisis.md" data-href="1DAM_ED/Unidad 02/2. Análisis.md" href="1DAM_ED/Unidad 02/2. Análisis.md" class="internal-link" target="_blank" rel="noopener nofollow">2. Análisis</a> ➡️</span></p>