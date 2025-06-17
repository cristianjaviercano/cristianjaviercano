---
description: >-
  This chapter introduces the fundamental concepts of simulation within the
  specific context of industrial engineering.
---

# Chapter One: Introduction to Simulation in Industrial Engineering

<img src="../../../.gitbook/assets/file.excalidraw (2) (1) (1).svg" alt="" class="gitbook-drawing">

### Chapter Objectives: Introduction to Simulation in Industrial Engineering

This chapter aims to establish a robust foundational understanding of simulation, specifically tailored for industrial engineers. Upon successful completion of this chapter, the reader will be able to:

1. **Define with precision the concepts of system, model, and simulation** within the context of industrial engineering. This involves understanding their interrelationships and significance in problem-solving.
2. **Describe the modeling process**, explaining the critical importance of abstraction and simplification in translating real-world complexity into manageable representations.
3. **Classify models according to various criteria**, including physical vs. mathematical; analytical vs. simulation; static vs. dynamic; deterministic vs. stochastic; and continuous vs. discrete. This will provide a structured framework for model selection.
4. **Identify the key concepts of discrete-event simulation**: entities, attributes, activities, events, system state, and the simulation clock. A clear understanding of these elements is fundamental for building and analyzing DES models.
5. **Argue effectively about the advantages and disadvantages** of utilizing simulation as an analytical tool, discerning when it is the most appropriate approach and when alternatives should be considered.
6. **Enumerate and describe the methodological steps** involved in a comprehensive simulation study, emphasizing the crucial roles of model verification and validation in ensuring model accuracy and credibility.
7. **Recognize relevant applications of simulation** across the diverse fields of industrial engineering, logistics, and production, demonstrating its practical utility in optimizing real-world operations.

***

### What is Simulation? Definitions: System, Model, Simulation

{% hint style="warning" %}
To understand the simulation, it is essential first to define the fundamental concepts on which it is built.
{% endhint %}

<img src="../../../.gitbook/assets/file.excalidraw (3).svg" alt="Relacion entre los elementos fundamentales de la simulacion" class="gitbook-drawing">

{% tabs %}
{% tab title="System" %}


A **collection of entities (e.g., people, machines, components) that interact with each other to achieve a logical purpose or objective** (Law, 2015; Banks et al., 2010). A system is bounded, meaning there is a clear distinction between what is inside the system and what is part of its environment. The behavior of the system emerges from the interactions of its components over time.

**Key Characteristics:**

* **Components/Entities:** Distinct parts or elements.
* **Interactions:** Relationships and dependencies between components.
* **Purpose/Objective:** A defined goal or function.
* **Boundary:** A conceptual or physical demarcation separating the system from its environment.
* **Environment:** Everything outside the system that can influence its behavior.

**Examples in Industrial Engineering:**

* **Manufacturing System:** Entities include raw materials, products, machines, operators. Interactions involve processing, material handling, and quality control. Purpose: produce goods.
* **Supply Chain System:** Entities include suppliers, manufacturers, distributors, retailers, and customers. Interactions involve ordering, production, transportation, and inventory management. Purpose: deliver products to customers.
* **Healthcare System (e.g., Emergency Department):** Entities include patients, doctors, nurses, examination rooms, equipment. Interactions involve patient admission, diagnosis, treatment, and discharge. Purpose: provide medical care.

{% hint style="success" %}
Hillier, F. S., & Lieberman, G. J. (2010). _Introducción a la Investigación de Operaciones_ (9th ed.). McGraw-Hill. (Capítulo 20 sobre Simulación, secciones 20.3, 20.4)
{% endhint %}
{% endtab %}

{% tab title="Model" %}


A **model** is an abstraction or representation of a real-world system. Its primary purpose is to capture the essential features and relationships of the system under study, simplifying its complexity to enable analysis, prediction, and understanding (Shannon, 1998).

Theoretically, a model can be conceptualized as a **set of logical and mathematical relationships that describe the behavior of a system or phenomenon** (Law, 2015). It is not the system itself, but a tool used to reason about the system.

**Key Characteristics:**

* **Abstraction:** Focuses on relevant aspects while omitting irrelevant details.
* **Representation:** Translates real-world elements into a formal structure (e.g., equations, flowcharts, code).
* **Purpose-Driven:** Designed with a specific analytical objective in mind. A model's validity is relative to its intended use.

**Types of Models (as per Chapter Objectives):**

* **Physical Models:** Tangible, scaled representations (e.g., miniature factory layout, wind tunnel model).
* **Mathematical Models:** Use symbols and equations to represent relationships. These can be:
  * **Analytical Models:** Provide exact or approximate solutions using mathematical formulas (e.g., queuing theory formulas, linear programming).
  * **Simulation Models:** Imitate the behavior of a system over time, often relying on numerical methods and statistical sampling.

{% hint style="success" %}
Cassandras, C. G., & Lafortune, S. (2008). Introduction to Discrete Event Systems (2nd ed.). Springer.
{% endhint %}
{% endtab %}

{% tab title="Simulation" %}
**The process of designing and developing a computerized model of a real or proposed system for the purpose of conducting numerical experiments to understand, predict, or improve the behavior of the system over time** (Banks et al., 2010).

Alternatively, Law (2015) states that simulation is the **imitation of the operation of a real-world process or system over time**. This involves generating an artificial history of the system and drawing inferences about its operating characteristics.

**Key Aspects:**

* **Computerized Model:** Simulation is almost exclusively performed using software.
* **Numerical Experimentation:** Involves running the model multiple times under different conditions.
* **Dynamic/Time-Based:** Crucially captures how a system evolves over time.
* **"What-If" Analysis:** Enables the evaluation of alternative designs, policies, or scenarios without physical intervention.
* **Stochasticity (often):** Many simulations incorporate random variables to reflect real-world uncertainty, producing probabilistic outputs.

**In essence, simulation allows an industrial engineer to create a "digital twin" or "virtual laboratory" of a system, enabling safe, cost-effective, and rapid experimentation that would be impractical or impossible in the real world.** This makes it an invaluable tool for understanding complex operational dynamics and supporting data-driven decision-making.

{% hint style="success" %}
Law, A. M. (2015). Simulation Modeling and Analysis (5th ed.). McGraw-Hill Education.
{% endhint %}
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
The simulation process involves more than just "running a program." It starts with a thorough understanding of the real system and a clear definition of the study
{% endhint %}

***

### The Modeling Process: Abstraction and Simplification

The development of a simulation model is as much an **art as it is a science**. It involves making crucial decisions about what to include and what to omit—a process guided by the study's objectives and the nature of the system being modeled.

<details>

<summary>Abstraction of the Model</summary>

**Abstraction** involves identifying and capturing the **essence of a system**, while ignoring details considered irrelevant to the study's purpose. It's the process of "rising above" minute details to gain a more general and manageable overview.

* **Theoretical Perspective:** Abstraction involves mapping a complex real-world system S to a simplified representation M such that M captures the critical functional relationships of S relevant to the study's objectives. This can be viewed as identifying the **"first principles"** or dominant mechanisms governing the system's behavior.
* **Practical Application:** If studying a manufacturing line's throughput, an engineer would abstract away details like the color of machines or the specific brand of tools, focusing instead on processing times, machine capacities, breakdown rates, and material flow logic.

**Abstraction** is the conceptual process of identifying the essential characteristics and behaviors of a system while deliberately ignoring irrelevant details. In simulation, this means focusing on the elements and interactions that directly influence the performance measures of interest.

&#x20;

{% hint style="warning" %}
La elección del nivel de abstracción correcto es **crítica**,&#x20;

* Un modelo demasiado abstracto puede no capturar los fenómenos importantes, mientras que uno innecesariamente detallado puede volverse intratable o consumir demasiados recursos computacionales&#x20;

-CRC-
{% endhint %}

</details>

<details>

<summary>Simplification of the Model</summary>



**Simplification** is the practical act of reducing the complexity of the abstracted model to make it tractable for implementation and analysis. This often involves making assumptions, aggregating components, or using statistical distributions to represent variability rather than modeling every individual micro-event.

* **Theoretical Perspective:** Simplification often involves reducing the number of state variables, assuming certain distributions for random inputs, or linearizing non-linear relationships, provided these simplifications do not significantly compromise the **validity** of the model with respect to the study's objectives.

As expressed by the maxim cited, a model should be "as simple as possible, but never simpler." This implies a **delicate balance**. Omitting important characteristics can invalidate the model, while including superfluous details can **obscure the results**, **increase development and execution time**, and **complicate its validation**.

{% hint style="success" %}
Banks, J., Carson, J. S., II, Nelson, B. L., & Nicol, D. M. (2010). Discrete-Event System Simulation (5th ed.)
{% endhint %}

</details>

{% hint style="info" %}
The modeling process is often **iterative**. One can start with a relatively simple model, and as understanding of the system and the model's sensitivity to different factors grows, **more details or complexity can be gradually added where necessary**.
{% endhint %}

The ability to perform appropriate **abstractions** and **simplifications**—without losing the model's essential fidelity to the system and the study's objectives—is one of the most important competencies of a good modeler.

#### Types of Simulation Models that Imitate Reality.

Models can be classified in various ways, which helps in understanding their nature and the appropriate tools for their analysis.

<details>

<summary>Physic Models</summary>

These are **tangible or scaled representations** of the real system. Classic examples include building models used by architects or airplane models in wind tunnels. While useful in certain fields, in the context of simulating industrial engineering systems, the focus is predominantly on **mathematical models**.

</details>

<details>

<summary><strong>Matemathics Models</strong></summary>

These utilize **mathematical language and symbols** (equations, algorithms) to describe the relationships between a system's components and variables. These are the models that are **implemented and analyzed via computer simulation**.

</details>

<details>

<summary><strong>Analithics Models</strong></summary>

These are mathematical models that can be solved using **direct mathematical techniques** to obtain **exact or closed-form solutions**—for example, the solution to a system of linear differential equations or the formula for the average waiting time in an M/M/1 queue.

</details>

<details>

<summary><strong>Simulation Models</strong></summary>

When a mathematical model is too complex for an analytical solution, **simulation** is employed. This involves the **numerical evaluation** of the model through **computerized experimentation** to estimate its behavior.

</details>

<details>

<summary><strong>Static Models</strong></summary>

Time is **not an explicit or significant variable** in the model. They represent the system at a **single point in time** or under **equilibrium conditions**. Monte Carlo simulation, for instance, is often applied to static models to evaluate the impact of input uncertainty on an output of interest.

</details>

<details>

<summary><strong>Dinamic Models</strong></summary>

The **system's state evolves over time**. System variables change as a result of activities or events occurring throughout time. Discrete-event simulation fundamentally deals with **dynamic models**.

</details>

<details>

<summary><strong>Deterministic Models</strong></summary>

No contienen componentes aleatorios. Dada una entrada y un estado inicial, la trayectoria futura del sistema está completamente determinada.

</details>

<details>

<summary>Stochastic (or Probabilistic) Models</summary>

They contain at least one **random component**. Input variables or model parameters are described using **probability distributions**. As a result, the model's output is also random and must be analyzed statistically. Most real-world industrial engineering systems exhibit **stochastic behavior** (variable process times, random customer arrivals, machine failures, etc.), so simulation models are typically stochastic.

</details>

<details>

<summary>Continuous Variable / Continuous Time Models</summary>

State variables can **change continuously over time**. They are often described by differential equations (as in fluid dynamics or projectile motion). Simulating these systems involves **discretizing time** for numerical solutions.

</details>

<details>

<summary>Discrete Variables Models / Discrete Time</summary>

State variables change only at **specific and countable instances in time**. If these instances are uniformly spaced, we refer to them as **discrete-time models**

</details>

<details>

<summary>Discrete-Event Models (DEM)</summary>

These are a particular type of **dynamic and generally stochastic model** where state variables change instantaneously at discrete and irregularly spaced points in time, as a result of the occurrence of "events" (e.g., a customer arrival, a service completion). This is the **primary focus of this course**.

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

###









## Bibliografia

1. Banks, J., Carson, J. S., II, Nelson, B. L., & Nicol, D. M. (2010). Discrete-Event System Simulation (5th ed.). Prentice Hall.
2. Law, A. M. (2015). Simulation Modeling and Analysis (5th ed.). McGraw-Hill Education.
3. Leemis, L. M., & Park, S. K. (2006). Discrete-Event Simulation: A First Course. Prentice Hall.&#x20;
4. Hillier, F. S., & Lieberman, G. J. (2010). Introducción a la Investigación de Operaciones (9th ed.). McGraw-Hill. (Capítulos sobre simulación)&#x20;
5. Cassandras, C. G., & Lafortune, S. (2008). Introduction to Discrete Event Systems (2nd ed.). Springer.
6. Urquía Moraleda, A., & Martín Villalba, C. (2016). Métodos de simulación y modelado. UNED.&#x20;
