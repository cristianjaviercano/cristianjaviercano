---
description: se define la simulación y su contexto en la ingeniería industrial
---

# Capitulo uno: Introducción a la Simulación en Ingeniería Industrial

<img src="../../../.gitbook/assets/file.excalidraw (2).svg" alt="" class="gitbook-drawing">

### Objetivos del capitulo

{% stepper %}
{% step %}
Definir con precisión los conceptos de sistema, modelo y simulación en el contexto de la ingeniería industrial
{% endstep %}

{% step %}
Describir el proceso de modelado, explicando la importancia de la abstracción y la simplificación
{% endstep %}

{% step %}
Clasificar los modelos según diferentes criterios (físicos, matemáticos; analíticos, de simulación; estáticos/dinámicos; deterministas/estocásticos; continuos/discretos)
{% endstep %}

{% step %}
Identificar los conceptos clave de la simulación de eventos discretos: entidades, atributos, actividades, eventos, estado del sistema y reloj de simulación.
{% endstep %}

{% step %}
Argumentar sobre las ventajas y desventajas de utilizar la simulación como herramienta de análisis.
{% endstep %}

{% step %}
Enumerar y describir los pasos metodológicos involucrados en un estudio de simulación, destacando la importancia de la verificación y la validación.
{% endstep %}

{% step %}
Reconocer aplicaciones relevantes de la simulación en los campos de la ingeniería industrial, la logística y la producción.
{% endstep %}
{% endstepper %}

### ¿Qué es la simulación? Definiciones: sistema, modelo, simulación

{% hint style="warning" %}
Para comprender la simulación, es esencial primero definir los conceptos fundamentales sobre los que se construye
{% endhint %}

<img src="../../../.gitbook/assets/file.excalidraw (3).svg" alt="Relacion entre los elementos fundamentales de la simulacion" class="gitbook-drawing">

{% tabs %}
{% tab title="Sistema" %}
En el ámbito de la ingeniería y las ciencias, un **sistema** se define como un conjunto de elementos o componentes que interactúan entre sí para lograr un objetivo común o desempeñar una función específica.&#x20;

Estos componentes pueden ser físicos (máquinas, personas, materiales) o lógicos (información, reglas de decisión).&#x20;

Desde la perspectiva del modelado y la simulación, un sistema es cualquier porción de la realidad que se aísla para su estudio, ya sea un entorno real o uno virtual que se desea analizar.&#x20;

Ejemplos de sistemas en ingeniería industrial son vastos y variados: una línea de ensamblaje en una fábrica, un centro de distribución logístico, el flujo de pacientes en un hospital, una cadena de suministro completa, o incluso un proceso de toma de decisiones gerenciales.&#x20;

La característica distintiva es la interdependencia de sus partes y su comportamiento emergente como un todo&#x20;

{% hint style="success" %}
Hillier, F. S., & Lieberman, G. J. (2010). _Introducción a la Investigación de Operaciones_ (9th ed.). McGraw-Hill. (Capítulo 20 sobre Simulación, secciones 20.3, 20.4)
{% endhint %}
{% endtab %}

{% tab title="Modelo" %}
Dado que los sistemas reales suelen ser demasiado complejos para ser estudiados directamente en su totalidad, se recurre a la creación de **modelos**.&#x20;

_Un modelo es una representación simplificada y abstracta de un sistema, construida con un propósito específico_. **No es una réplica exacta de la realidad, sino una aproximación que captura los aspectos esenciales del sistema relevantes para el problema que se investiga**.&#x20;

Como se indica, _"el modelo es siempre menos complejo que el sistema original"_. El propósito del modelo guía las simplificaciones y abstracciones que se realizan. Por ejemplo, para estudiar el flujo de producción en una fábrica, un modelo podría representar las máquinas y los buffers, pero ignorar detalles como la temperatura ambiente o el color de las máquinas, si estos no son relevantes para el objetivo del estudio

{% hint style="success" %}
Cassandras, C. G., & Lafortune, S. (2008). Introduction to Discrete Event Systems (2nd ed.). Springer.
{% endhint %}
{% endtab %}

{% tab title="Simulacion" %}
La **simulación** es el proceso de diseñar un modelo de un sistema real y llevar a cabo experimentos con este modelo con el fin de entender el comportamiento del sistema o evaluar diversas estrategias para su operación.&#x20;

En esencia, _**la simulación imita el funcionamiento de un sistema a lo largo del tiempo**_, generando una historia artificial de su evolución. Esta historia se utiliza luego para extraer conclusiones sobre las características operativas del sistema real.&#x20;

Cuando los modelos matemáticos de un sistema son demasiado complejos para ser resueltos por métodos analíticos (es decir, mediante fórmulas exactas), la simulación, que es un experimento numérico realizado sobre el modelo, se convierte en una herramienta indispensable.&#x20;

Un modelo de simulación de eventos discretos, por ejemplo, es inherentemente estocástico (incorpora aleatoriedad) y dinámico (evoluciona con el tiempo), y su característica principal es que las variables que describen el estado del sistema cambian de valor únicamente en instantes discretos de tiempo, conocidos como "eventos"

{% hint style="success" %}
Law, A. M. (2015). Simulation Modeling and Analysis (5th ed.). McGraw-Hill Education.
{% endhint %}
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
El proceso de simulación no es simplemente "ejecutar un programa". Comienza con una comprensión profunda del sistema real y una definición clara de los objetivos del estudio.
{% endhint %}

#### El proceso de modelado, Abstracción y simplificación

El desarrollo de un modelo de simulación es tanto un arte como una ciencia. Implica tomar decisiones cruciales sobre qué incluir y qué omitir, un proceso guiado por los objetivos del estudio y la naturaleza del sistema.

<details>

<summary>La Abstraccion de un Fenomeno Observado</summary>

La abstracción consiste en _**identificar y capturar la esencia de un sistema**_, _ignorando los detalles que se consideran irrelevantes para el propósito del estudio._&#x20;

{% hint style="info" %}
Es el proceso de "elevarse" por encima de los detalles minuciosos para obtener una visión más general y manejable.&#x20;
{% endhint %}

En el contexto del modelado, la abstracción permite **"usar cada parte del modelo sin conocer sus detalles internos"**. Los modelos de simulación pueden operar en diferentes niveles de abstracción.&#x20;

Por ejemplo, a un nivel _estratégico alto_, se pueden modelar flujos agregados en una cadena de suministro sin detallar cada camión o producto individual.&#x20;

A un nivel _operativo bajo_, se podría modelar el movimiento preciso de un vehículo guiado automáticamente (AGV) en un almacén, incluyendo sus aceleraciones y desaceleraciones.&#x20;

{% hint style="warning" %}
La elección del nivel de abstracción correcto es **crítica**,&#x20;

* Un modelo demasiado abstracto puede no capturar los fenómenos importantes, mientras que uno innecesariamente detallado puede volverse intratable o consumir demasiados recursos computacionales&#x20;

-CRC-
{% endhint %}

</details>

<details>

<summary>La Simplificación Del Modelo Observado.</summary>

La simplificación va de la mano con la abstracción. Dado que los sistemas reales son inherentemente complejos, cualquier modelo será una simplificación de esa realidad.&#x20;

El objetivo es lograr una _"simplificación válida"_ , es decir, un modelo que sea lo suficientemente simple para ser comprendido, construido y analizado, pero lo suficientemente detallado para representar adecuadamente aquellos aspectos del sistema que son cruciales para los objetivos del estudio.&#x20;

Como lo expresa la máxima citada en , un modelo debe ser "_**tan simple como sea posible, pero nunca más simple"**_. Esto implica un delicado equilibrio.&#x20;

Omitir características importantes puede invalidar el modelo, mientras que incluir detalles superfluos puede oscurecer los resultados, aumentar el tiempo de desarrollo y ejecución, y dificultar la validación del mismo.

{% hint style="success" %}
Banks, J., Carson, J. S., II, Nelson, B. L., & Nicol, D. M. (2010). Discrete-Event System Simulation (5th ed.)
{% endhint %}

</details>

{% hint style="info" %}
El proceso de modelado a menudo es iterativo. Se puede comenzar con un modelo relativamente simple y, a medida que se gana comprensión del sistema y de la sensibilidad del modelo a diferentes factores, se pueden añadir gradualmente más detalles o complejidad donde sea necesario.
{% endhint %}

La habilidad para realizar abstracciones y simplificaciones adecuadas, sin perder la fidelidad esencial del modelo respecto al sistema y los objetivos del estudio, es una de las competencias más importantes de un **buen modelador.**

#### Tipos de Modelos de Simulacion que buscan imitar la Reaidad.

Los modelos pueden clasificarse de diversas maneras, lo que ayuda a entender su naturaleza y las herramientas adecuadas para su análisis

<details>

<summary><strong>Modelos Fisicos</strong></summary>

Son representaciones tangibles o a escala del sistema real. Ejemplos clásicos incluyen maquetas de edificios utilizadas por arquitectos o modelos de aviones en túneles de viento. Aunque útiles en ciertos campos, en el contexto de la simulación de sistemas de ingeniería industrial, el enfoque se centra predominantemente en los modelos matemáticos

</details>

<details>

<summary><strong>Modelos Matemáticos</strong></summary>

Utilizan el lenguaje y los símbolos matemáticos (ecuaciones, algoritmos) para describir las relaciones entre los componentes y las variables de un sistema. Estos son los modelos que se implementan y analizan mediante simulación por computado

</details>

<details>

<summary><strong>Modelos Analíticos</strong></summary>

Son aquellos modelos matemáticos que pueden resolverse mediante técnicas matemáticas directas para obtener soluciones exactas o en forma cerrada&#x20;

por ejemplo, la solución de un sistema de ecuaciones diferenciales lineales o la fórmula para el tiempo de espera promedio en una cola M/M/1&#x20;

</details>

<details>

<summary><strong>Modelos de Simulación</strong></summary>

Cuando un modelo matemático es demasiado complejo para una solución analítica, se recurre a la simulación. Esta implica la evaluación numérica del modelo a través de la experimentación computarizada para estimar su comportamiento

</details>

<details>

<summary><strong>Modelos Estáticos</strong></summary>

El tiempo no es una variable explícita o significativa en el modelo. Representan el sistema en un único punto en el tiempo o bajo condiciones de equilibrio. La simulación de Montecarlo, por ejemplo, a menudo se aplica a modelos estáticos para evaluar el impacto de la incertidumbre en las entradas sobre una salida de interés

</details>

<details>

<summary><strong>Modelos Dinámicos</strong></summary>

El estado del sistema evoluciona con el tiempo. Las variables del sistema cambian como resultado de actividades o eventos que ocurren a lo largo del tiempo. La simulación de eventos discretos se ocupa fundamentalmente de modelos dinámicos

</details>

<details>

<summary><strong>Modelos Deterministas</strong></summary>

No contienen componentes aleatorios. Dada una entrada y un estado inicial, la trayectoria futura del sistema está completamente determinada.

</details>

<details>

<summary><strong>Modelos Estocásticos (o Probabilísticos)</strong></summary>

Contienen al menos un componente aleatorio. Las variables de entrada o los parámetros del modelo se describen mediante distribuciones de probabilidad. Como resultado, la salida del modelo también es aleatoria y debe analizarse estadísticamente. La mayoría de los sistemas de ingeniería industrial reales exhiben comportamiento estocástico (tiempos de proceso variables, llegadas aleatorias de clientes, fallas de máquinas, etc.), por lo que los modelos de simulación suelen ser estocásticos.

</details>

<details>

<summary><strong>Modelos de Variables Continuas / Tiempo Continuo</strong></summary>

Las variables de estado pueden cambiar continuamente a lo largo del tiempo. A menudo se describen mediante ecuaciones diferenciales (como en la dinámica de fluidos o el movimiento de un proyectil). La simulación de estos sistemas implica la discretización del tiempo para su solución numérica

</details>

<details>

<summary><strong>Modelos de Variables Discretas / Tiempo Discreto:</strong></summary>

Las variables de estado cambian solo en instantes específicos y contables de tiempo. Si estos instantes están espaciados uniformemente, se habla de modelos de tiempo discreto (descritos por ecuaciones en diferencias)

</details>

<details>

<summary><strong>Modelos de Eventos Discretos (MED)</strong></summary>

Son un tipo particular de modelo dinámico y generalmente estocástico, donde las variables de estado cambian instantáneamente en puntos discretos e irregularmente espaciados en el tiempo, como resultado de la ocurrencia de "eventos" (ej. llegada de un cliente, finalización de un servicio). Este es el enfoque principal de este curso

</details>

{% hint style="success" %}
La correcta clasificación de un problema y el tipo de modelo necesario es un paso crucial, ya que guía la selección de la metodología de simulación más apropiada (Montecarlo, eventos discretos, dinámica de sistemas, etc.)
{% endhint %}

Resumiendo a informacion anterior podemos definir que los modelos de simulacion si bien se pueden clasificar en un sin numero de tipos, lo importante es reconocerlos con sus especificacione para poder seleccionar la metodologia de interpretacion correcta.

| Característica del Modelo | Tiempo       | Aleatoriedad | Cambio de Estado | Ejemplo en IE                                              | Enfoque de Simulación Común              |
| ------------------------- | ------------ | ------------ | ---------------- | ---------------------------------------------------------- | ---------------------------------------- |
| Estático                  | No relevante | Determinista | No relevante     | Cálculo de costo fijo de un producto                       | (No requiere simulación)                 |
| Estático                  | No relevante | Estocástico  | No relevante     | Análisis de riesgo de inversión (VPN con flujos inciertos) | Montecarlo                               |
| Dinámico                  | Relevante    | Determinista | Continuo         | Modelo de decaimiento de un fármaco (ODE)                  | Simulación de tiempo continuo (numérica) |
| Dinámico                  | Relevante    | Estocástico  | Continuo         | Modelo de precios de acciones (ecu. dif. estoc.)           | Simulación de tiempo continuo (avanzada) |
| Dinámico                  | Relevante    | Determinista | Discreto         | Plan de producción fijo con llegadas programadas           | (Puede ser analítico o SED simple)       |
| Dinámico                  | Relevante    | Estocástico  | Discreto         | Sistema de colas, línea de producción con fallas           | Simulación de Eventos Discretos (SED)    |

#### Simulacion en los estudios de Investigacion de Operaciones

la simulacion tiene el mismo papel en muchos estudios que la IO, pero cuando la IO busca la optimizacion o el hallazgo de una solucion, la simulacion busca el describir el entorno o el sistema con el fin de conocer el comportamiento y predecir o encontrar estas fallas o elementos que dan valor a las decisiones a tiempo.

la IO se dedica a diseñar un diseño o procedimiento para algún sistema estocastico, que pued eoperar de forma probabilistica a travez del tiempo,

Cuando es necesario usar la Simulacion como parte del estudio de IO, es muy comun que contenga los mismos pasos, el **Modelo de Simulacion** detallado es necesario para formular y descrinbir la operacion y como debe simularse.

1. Definir el _Estado del sistema, como el número de clientes en un sistema de colas_
2. _identificar los estados posibles_
3. _identificar los eventos posibles_
4. contar con un Reloj de Simulacion, que registre el tiempo
5. Metodo para  generar **eventos de manera aleatoria**
6. Una formula para identificar las _Transiciones de los estados_ que generen los eventos aleatorios

***

### Simulacion de Eventos Discretos (SED) Vs. Eventos Continuo (SEC)

Las Dos grandes categorias de la simulacion son de eventos de **tipo discreto y de tipo continuo.**

La (SED) es una metodología poderosa para modelar sistemas cuyo estado cambia en puntos discretos en el tiempo como resultado de la ocurrencia de ciertos sucesos o eventos. Entre un evento y el siguiente, se asume que el estado del sistema permanece constante; es decir, _"nada significativo sucede entre eventos"_. Para construir y comprender los modelos SED, es crucial familiarizarse con sus componentes fundamentales.

<details>

<summary>Entidades</summary>

Son los objetos dinámicos que _"fluyen"_ a través del sistema, solicitan servicios, ocupan recursos y desencadenan eventos. En contextos de ingeniería industrial, las entidades pueden ser clientes en un banco, piezas en una línea de producción, pedidos en un sistema logístico, camiones en una red de transporte, o incluso paquetes de datos en una red de comunicación

</details>

<details>

<summary>Atributos</summary>

Son las propiedades o características individuales de las entidades. Los atributos permiten diferenciar entre entidades del mismo tipo y pueden influir en su procesamiento dentro del sistema. Por ejemplo, un cliente (entidad) puede tener atributos como "tipo de transacción requerida" o "tiempo de llegada". Una pieza (entidad) puede tener atributos como "tipo de producto", "ruta de procesamiento" o "prioridad"

</details>

<details>

<summary>Actividades (o Retrasos - Delays)</summary>

Representan operaciones o procesos que consumen tiempo dentro del sistema. Una entidad puede experimentar una actividad, como ser atendida por un servidor, ser procesada por una máquina, o viajar de un punto a otro. La duración de una actividad puede ser determinista (fija) o, más comúnmente en SED, estocástica (aleatoria), modelada por una distribución de probabilidad

</details>

<details>

<summary>Eventos</summary>

Son sucesos instantáneos que pueden cambiar el estado del sistema. Los eventos marcan el inicio o el fin de una actividad, o cualquier otro cambio significativo. Ejemplos típicos incluyen la llegada de una entidad al sistema (evento de llegada), la finalización del servicio de una entidad (evento de fin de servicio), o la falla de una máquina (evento de falla)

</details>

<details>

<summary>Estado del Sistema</summary>

Es un conjunto de variables que contienen toda la información necesaria para describir el sistema en un instante particular. El estado del sistema debe ser suficiente para reanudar la simulación desde ese punto si se detuviera. Ejemplos de variables de estado incluyen el número de clientes esperando en una cola, el estado de un servidor (ocupado, libre, en reparación), o el nivel de inventario de un producto

</details>

<details>

<summary>Reloj de Simulación (Simulation Clock)</summary>

Es una variable que mantiene el valor actual del tiempo simulado. A diferencia del tiempo real, el reloj de simulación no avanza continuamente, sino que salta de un instante de evento al siguiente. Este mecanismo se conoce como "avance del próximo evento" (next-event time advance) y es fundamental para la eficiencia de la SED

</details>

<details>

<summary>Lista de Eventos (Event List o Event Calendar)</summary>

Es una estructura de datos esencial que almacena todos los eventos futuros que han sido programados para ocurrir. Los eventos en esta lista están típicamente ordenados cronológicamente, es decir, por su tiempo de ocurrencia programado. El reloj de simulación avanza al tiempo del evento más inminente en esta lista

</details>

<details>

<summary>Recursos</summary>

Son los componentes del sistema que proporcionan servicio o son utilizados por las entidades. Los recursos suelen tener una capacidad limitada (por ejemplo, un número finito de cajeros, máquinas, operarios, o muelles de carga). Las entidades a menudo compiten por el uso de estos recursos

</details>

<details>

<summary>Colas (Queues)</summary>

Son lugares dentro del sistema donde las entidades esperan cuando no pueden acceder inmediatamente a un recurso o servicio porque este está ocupado o no disponible. Las colas son una consecuencia natural de la contención de recursos en sistemas con llegadas y/o servicios aleatorios

</details>

{% hint style="warning" %}
La interrelación de estos conceptos es lo que define la dinámica de un modelo SED. Las entidades llegan, posiblemente con atributos específicos, y solicitan recursos para realizar actividades. Si los recursos no están disponibles, las entidades pueden esperar en colas. La ocurrencia de eventos (como llegadas o fines de actividad) cambia el estado del sistema
{% endhint %}

### Ventajas y desventajas de la simulación

Es una herramienta analítica de gran alcance, pero como cualquier metodología, presenta tanto fortalezas como debilidades.&#x20;

Es crucial que el ingeniero industrial comprenda estas características para decidir cuándo y cómo aplicar la simulación de manera efectiva.

{% tabs %}
{% tab title="Ventajas" %}


1. **Análisis de Sistemas Complejos**: Permite estudiar sistemas cuya complejidad (gran número de variables, interacciones no lineales, comportamiento estocástico) impide el uso de métodos analíticos puros. La simulación es especialmente útil para sistemas de colas complejos donde las fórmulas matemáticas son limitadas o inexistentes.1
2. **Experimentación Segura y Económica**: Facilita la experimentación con el sistema sin necesidad de interrumpir la operación real, construir costosos prototipos físicos o exponer el sistema a riesgos innecesarios. Se pueden probar cambios radicales o condiciones extremas en un entorno virtual controlado.1
3. **Evaluación de Alternativas ("What-if Analysis")**: Permite comparar diferentes políticas de operación, diseños de sistemas o escenarios de inversión antes de su implementación. Esto ayuda a tomar decisiones más informadas y a seleccionar las opciones más prometedoras.
4. **Compresión y Expansión del Tiempo**: Es posible simular largos períodos de operación (años) en cuestión de minutos u horas de tiempo computacional, o, inversamente, analizar eventos de corta duración con gran detalle.
5. **Identificación de Problemas y Comprensión del Sistema**: Ayuda a identificar cuellos de botella, comprender las interdependencias entre componentes del sistema y visualizar la dinámica general del sistema. La propia construcción del modelo a menudo conduce a una mejor comprensión del sistema.
6. **Incorporación de Aleatoriedad e Incertidumbre:** Permite modelar y analizar el impacto de la variabilidad inherente a los sistemas reales (tiempos de llegada aleatorios, duraciones de servicio variables, fallas de equipos, fluctuaciones de la demanda).
7. **Herramienta de Comunicación y Visualización:** Los modelos de simulación, especialmente aquellos con capacidades de animación gráfica, son excelentes herramientas para comunicar el funcionamiento de un sistema y los resultados de un estudio a diferentes audiencias, incluyendo la gerencia y el personal operativo.1
8. **Entrenamiento:** Los simuladores pueden utilizarse como herramientas de entrenamiento para operadores y tomadores de decisiones, permitiéndoles experimentar las consecuencias de sus acciones en un entorno libre de riesgos.
{% endtab %}

{% tab title="Desventajas" %}


1. **Costo y Tiempo de Desarrollo:** El desarrollo de un modelo de simulación válido y detallado puede ser un proceso largo y costoso, requiriendo personal especializado, software y tiempo computacional significativo. "La simulación tiende a ser un proceso relativamente caro".1
2. **Resultados como Estimaciones Estadísticas:** La simulación, especialmente la estocástica, produce estimaciones del comportamiento del sistema, no soluciones exactas u óptimas (a menos que se combine con técnicas de optimización). Los resultados están sujetos a error muestral y requieren un análisis estadístico cuidadoso para su interpretación.1
3. **Requerimiento Intensivo de Datos:** La validez de un modelo de simulación depende en gran medida de la calidad de los datos de entrada utilizados para definir las distribuciones de probabilidad y los parámetros del sistema. El principio "basura entra, basura sale" (GIGO, Garbage In, Garbage Out) es plenamente aplicable. La recolección y el análisis de estos datos pueden ser un desafío.
4. **Complejidad en la Interpretación de Resultados:** La interpretación de los resultados de salida de una simulación puede ser compleja y requiere un buen entendimiento de los métodos estadísticos para evitar conclusiones erróneas.
5. **Riesgo de Falsa Confianza:** Un modelo de simulación, especialmente si es visualmente atractivo, puede generar una falsa sensación de precisión o validez si no ha sido rigurosamente verificado y validado.
6. **Especificidad del Modelo:** Un modelo de simulación suele ser específico para el sistema y los objetivos para los cuales fue desarrollado. Generalizar sus resultados a otros sistemas o cambiar significativamente los objetivos puede requerir una revisión sustancial o la construcción de un nuevo modelo.
{% endtab %}
{% endtabs %}

***

## Pasos en un estudio de simulación.

Un estudio de simulación es un proyecto estructurado que sigue una serie de pasos metodológicos para asegurar que los resultados sean creíbles y útiles para la toma de decisiones. La verificación y la validación son componentes críticos de este proceso, que se realizan de manera iterativa a lo largo del ciclo de vida del estudio

<figure><img src="../../../.gitbook/assets/Fases Generales de un Proyecto de Simulación - visual selection.png" alt=""><figcaption><p>ciclo de la generacion del modelo de simulacion</p></figcaption></figure>

### Fases Generales de un Proyecto de Simulación.

{% stepper %}
{% step %}
**Definición del Problema y Establecimiento de Objetivos y Alcance del Estudio**

Este es el paso inicial y, posiblemente, el más crucial. Consiste en comprender claramente el sistema a estudiar, el problema que se quiere resolver y los objetivos específicos que se persiguen con la simulación. _¿Qué preguntas se espera que responda la simulación?_ _¿Qué métricas de desempeño son importantes?_&#x20;

{% hint style="warning" %}
_**Un problema mal definido o unos objetivos ambiguos conducirán inevitablemente a un estudio de simulación ineficaz**_
{% endhint %}
{% endstep %}

{% step %}
**Formulación del Modelo Conceptual**

Una vez definidos los objetivos, se desarrolla un modelo conceptual del sistema. Esto implica identificar los componentes clave del sistema, las variables relevantes, las interacciones entre ellas, las entradas, las salidas, y el nivel de detalle o abstracción necesario para cumplir los objetivos del estudio.&#x20;

{% hint style="warning" %}
Se deben establecer las hipótesis y simplificaciones que se realizarán
{% endhint %}
{% endstep %}

{% step %}
**Recolección y Análisis de Datos de Entrada**

La simulación requiere datos para alimentar el modelo. Esto incluye datos para estimar los parámetros del sistema (ej. capacidades de máquinas, número de servidores) y para caracterizar la variabilidad de las entradas (ej. tiempos entre llegadas de clientes, tiempos de servicio, tasas de falla de equipos) mediante distribuciones de probabilidad.

{% hint style="warning" %}
La calidad de estos datos es fundamental para la validez del modelo
{% endhint %}
{% endstep %}

{% step %}
**Construcción del Modelo Computacional (Programación)**

El modelo conceptual se traduce a un modelo computacional utilizando un lenguaje de simulación específico (ej. AnyLogic, Simio), una librería de simulación en un lenguaje de propósito general (ej. SimPy en Python), o incluso una hoja de cálculo para modelos más simples (ej. Excel para Montecarlo)

{% hint style="warning" %}
se recomienda hacer uso de la logica de programacion lineal y sus variantes para estos casos, hacer el modelo matematico paa comprender la logica del sistema
{% endhint %}
{% endstep %}

{% step %}
**Verificación del Modelo Computacional**

La verificación se enfoca en asegurar que el modelo computacional se comporta tal como el modelador lo diseñó, es decir, que el programa implementa correctamente la lógica y los algoritmos del modelo conceptual y de especificación.&#x20;

{% hint style="warning" %}
La pregunta clave es: "¿Construimos el modelo (programa) correctamente?
{% endhint %}

_Técnicas de Verificación, (prueba de escritorio)_

1. Revisión del código (code walkthroughs).
2. Pruebas modulares (probar componentes individuales del modelo).
3. Uso de trazas (seguir la ejecución paso a paso para valores de entrada simples).
4. Comparación con resultados conocidos de casos simples o versiones simplificadas del modelo.
5. Comprobación de la lógica bajo condiciones extremas de los parámetros.
6. Uso de animación para detectar comportamientos anómalos
{% endstep %}

{% step %}
**Validación del Modelo**

La validación busca determinar si el modelo de simulación es una representación suficientemente precisa del sistema real para los propósitos del estudio.&#x20;

{% hint style="warning" %}
La pregunta clave es: "¿Construimos el modelo correcto (que representa la realidad)
{% endhint %}

_Técnicas de Validación:_

1. Comparación de los resultados del modelo con datos históricos del sistema real (si existen).
2. Revisión del modelo y sus resultados por expertos en el sistema real.
3. Pruebas de Turing: presentar a expertos los resultados del modelo y del sistema real (sin identificar cuál es cuál) y ver si pueden distinguirlos.1
4. Análisis de sensibilidad: variar los parámetros de entrada del modelo y verificar si las salidas cambian de una manera que sea consistente con el comportamiento esperado del sistema real.
5. Comprobar la "validez aparente" (face validity): ¿El modelo parece razonable a quienes conocen el sistema?
{% endstep %}

{% step %}
**Diseño de Experimentos de Simulación**

Una vez verificado y validado el modelo, se planifican los experimentos que se realizarán. Esto incluye definir los escenarios a evaluar, las alternativas a comparar, el número de réplicas (corridas independientes) para cada escenario, la duración de cada réplica, y la duración del período de calentamiento (warm-up period) si se buscan resultados de estado estacionario
{% endstep %}

{% step %}
**Ejecución de las Corridas de Simulación (Corridas de Producción)**

Se ejecutan las simulaciones según el diseño experimental. Es importante gestionar adecuadamente la generación de números aleatorios para asegurar la independencia entre réplicas o la reproducibilidad si es necesario.
{% endstep %}

{% step %}
**Análisis de los Resultados de Salida**

Los datos generados por las simulaciones se analizan utilizando herramientas estadísticas para estimar las métricas de desempeño de interés (ej. promedios, varianzas, percentiles, intervalos de confianza) y para comparar las diferentes alternativas o escenarios
{% endstep %}

{% step %}
**Documentación, Presentación de Resultados y Toma de Decisiones/Implementación**

Finalmente, se documenta todo el estudio, incluyendo el modelo, los supuestos, los datos de entrada, los procesos de V\&V, los experimentos realizados y los resultados obtenidos. Los hallazgos se presentan a los tomadores de decisiones, y si el estudio lo justifica, se procede a la implementación de las recomendaciones
{% endstep %}
{% endstepper %}

{% hint style="danger" %}
Es fundamental entender que la verificación y la validación no son actividades que se realizan una única vez al final del desarrollo del modelo. Son procesos continuos e iterativos que deben llevarse a cabo a lo largo de todo el ciclo de vida del estudio de simulación.

Un modelo que no ha sido adecuadamente verificado y validado carece de credibilidad, y las decisiones basadas en él pueden ser erróneas y costosas. La participación del cliente o del experto en el sistema real es vital durante todo el proceso, especialmente en la definición del problema, la formulación conceptual y la validación. -crc-
{% endhint %}

***

### Aplicaciones en ingeniería industrial, logística y producción

La simulación es una herramienta extraordinariamente versátil que ha encontrado una amplia gama de aplicaciones en prácticamente todas las áreas de la ingeniería industrial, la logística y la producción.&#x20;

Su capacidad para modelar la complejidad, la dinámica y la estocasticidad de los sistemas la convierte en un instrumento invaluable para el análisis, diseño y mejora continua.&#x20;

{% tabs %}
{% tab title="Sistemas de Manufactura y Producción" %}
* **Diseño y Distribución de Planta (Layout):** Evaluar diferentes configuraciones de planta, ubicación de maquinaria, estaciones de trabajo y áreas de almacenamiento para optimizar flujos de materiales, minimizar distancias de recorrido, reducir cuellos de botella y mejorar la eficiencia general.
* **Análisis de Líneas de Producción y Ensamblaje:** Modelar líneas de producción para analizar su capacidad, identificar cuellos de botella (un concepto central en la Teoría de Restricciones - TOC 1), determinar el tamaño óptimo de los buffers intermedios, y evaluar el impacto de la variabilidad en los tiempos de proceso y las tasas de falla de las máquinas.1 General Motors, por ejemplo, utilizó la simulación para incrementar significativamente el rendimiento de sus plantas.
* **Programación y Secuenciación de la Producción:** Probar diferentes reglas de prioridad y algoritmos de secuenciación para minimizar tiempos de ciclo, reducir el trabajo en proceso (WIP) y mejorar el cumplimiento de las fechas de entrega.1 Swift & Company aplicó la simulación para la programación a nivel de turno y la gestión de la capacidad de promesa.
* **Control de Inventarios (WIP y Materias Primas):** Evaluar políticas de control de inventario en el piso de producción, como sistemas Kanban o CONWIP, y determinar niveles óptimos de inventario de materias primas y componentes.1 Samsung Electronics utilizó la simulación para reducir tiempos de ciclo e inventarios.
* **Planificación de Capacidad:** Determinar los requerimientos de maquinaria, personal y otros recursos para satisfacer la demanda proyectada, y evaluar el impacto de inversiones en nueva capacidad.
* **Sistemas de Manejo de Materiales:** Diseñar y evaluar la eficiencia de sistemas de transporte interno como vehículos guiados automáticamente (AGVs), bandas transportadoras, grúas y robots, considerando sus velocidades, capacidades y lógicas de control.
* **Modelado de Confiabilidad y Mantenimiento:** Analizar el impacto de las fallas de equipos y las políticas de mantenimiento (preventivo, predictivo, correctivo) sobre la disponibilidad de la línea y la producción total.
* **Implementación de Sistemas Lean/Just-in-Time (JIT):** Simular la transición a sistemas de producción esbelta para evaluar sus beneficios y desafíos antes de la implementación a gran escala.
{% endtab %}

{% tab title="Logística y Cadenas de Suministro" %}
* **Diseño de Redes de Distribución**: Optimizar la ubicación y el número de almacenes y centros de distribución, y definir las rutas de flujo de productos para minimizar costos totales y mejorar los niveles de servicio.
* **Gestión de Almacenes:** Modelar las operaciones internas de un almacén (recepción, almacenamiento, picking, empaque, despacho) para mejorar la utilización del espacio, optimizar los recorridos de los operarios y equipos, y reducir los tiempos de procesamiento de pedidos.
* **Optimización de Rutas de Transporte**: Evaluar diferentes estrategias de ruteo para flotas de vehículos, considerando factores como costos de transporte, ventanas de tiempo de entrega, capacidades de los vehículos y variabilidad en los tiempos de viaje.1 Yellow Freight System mejoró su servicio y rendimiento mediante la optimización interactiva de sus operaciones de transporte.1
* **Políticas de Inventario en la Cadena de Suministro**: Analizar el impacto de diferentes políticas de inventario (centralizado vs. descentralizado, niveles de seguridad) en múltiples eslabones de la cadena de suministro, considerando la variabilidad de la demanda y los tiempos de entrega de los proveedores.1 IBM aplicó la simulación para optimizar su sistema de inventario multi-escalón para la logística de servicios 1, y Philips Electronics la usó para sincronizar su cadena y mitigar el efecto látigo.1
* **Análisis del Efecto Látigo (Bullwhip Effect)**: Simular cómo las variaciones en la demanda del consumidor final se amplifican a medida que se asciende en la cadena de suministro, y probar estrategias para mitigarlo.
* **Colaboración y Sincronización en la Cadena de Suministro:** Evaluar los beneficios de compartir información y coordinar decisiones entre los diferentes actores de la cadena.
{% endtab %}

{% tab title="Sistemas de Servicios" %}
* **Análisis de Sistemas de Colas:** Modelar y analizar el rendimiento de sistemas donde los clientes (o trabajos) esperan por servicio, como en bancos, centros de llamadas (call centers), hospitales, aeropuertos, restaurantes, y oficinas gubernamentales. El objetivo suele ser equilibrar los costos de servicio con la calidad del servicio (tiempos de espera).&#x20;
  * AT\&T desarrolló un sistema basado en simulación para ayudar a sus clientes a diseñar centros de atención telefónica.
* **Optimización de Personal (Staffing)**: Determinar el número óptimo de servidores (cajeros, agentes, médicos, enfermeras) en diferentes momentos del día o semana para cumplir con los niveles de servicio deseados a un costo razonable.&#x20;
  * Merrill Lynch utilizó simulación para su análisis de precios y servicios.

**Diseño y Rediseño de Procesos de Servicio**: Evaluar el impacto de cambios en los flujos de procesos, la asignación de tareas o la introducción de nueva tecnología en la eficiencia y la experiencia del cliente.
{% endtab %}

{% tab title="Gestión de Proyectos" %}
* **Estimación de la Duración y Costo de Proyectos:** Modelar la duración y el costo de las actividades de un proyecto como variables aleatorias (usando distribuciones como la Triangular o Beta en PERT) para obtener una distribución de la duración y el costo total del proyecto.
* **Análisis de Rutas Críticas y Sensibilidad:** Identificar las actividades más críticas y analizar cómo la variabilidad en sus duraciones afecta la probabilidad de cumplir con los plazos del proyecto.
* **Gestión de Riesgos en Proyectos:** Evaluar el impacto de posibles riesgos (retrasos en proveedores, problemas técnicos, falta de recursos) y la efectividad de planes de contingencia.
{% endtab %}
{% endtabs %}

La versatilidad de la simulación es tal que su aplicación se extiende a casi cualquier sistema donde la dinámica, la interacción entre componentes y la incertidumbre juegan un papel importante.

{% hint style="success" %}
la competitividad de las organizaciones. La clave para el ingeniero industrial es aprender a identificar las características de un problema que lo hacen candidato para un análisis por simulación y luego traducir ese problema en un modelo válido y útil
{% endhint %}

***

## Bibliografia

1. Banks, J., Carson, J. S., II, Nelson, B. L., & Nicol, D. M. (2010). Discrete-Event System Simulation (5th ed.). Prentice Hall.
2. Law, A. M. (2015). Simulation Modeling and Analysis (5th ed.). McGraw-Hill Education.
3. Leemis, L. M., & Park, S. K. (2006). Discrete-Event Simulation: A First Course. Prentice Hall.&#x20;
4. Hillier, F. S., & Lieberman, G. J. (2010). Introducción a la Investigación de Operaciones (9th ed.). McGraw-Hill. (Capítulos sobre simulación)&#x20;
5. Cassandras, C. G., & Lafortune, S. (2008). Introduction to Discrete Event Systems (2nd ed.). Springer.
6. Urquía Moraleda, A., & Martín Villalba, C. (2016). Métodos de simulación y modelado. UNED.&#x20;
