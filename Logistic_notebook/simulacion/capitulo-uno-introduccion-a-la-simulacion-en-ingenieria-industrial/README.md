---
description: se define la simulación y su contexto en la ingeniería industrial
---

# Capitulo uno: Introducción a la Simulación en Ingeniería Industrial

<img src="../../.gitbook/assets/file.excalidraw (2).svg" alt="" class="gitbook-drawing">

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

<img src="../../.gitbook/assets/file.excalidraw (3).svg" alt="Relacion entre los elementos fundamentales de la simulacion" class="gitbook-drawing">

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

<details>

<summary></summary>



</details>

<details>

<summary></summary>



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

### Simulacion de Eventos Discretos (SED) Vs. Eventos Continuo (SEC)

Las Dos grandes categorias de la simulacion son de eventos de **tipo discreto y de tipo continuo.**

La SED,&#x20;
