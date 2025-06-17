---
description: >-
  understands that Queueing Theory is a fundamental analytical discipline within
  Operations Research. It provides a mathematical framework for analyzing
  systems where customers or items arrive.
icon: colon
---

# Queueing theory

{% hint style="info" %}
El proceso basico supuesto por la mayoria de los modelos, es que **Los clientes quieren un servicio**
{% endhint %}

### QT.

Queueing theory deals with the mathematical study of waiting lines, or queues. It models the flow of entities through a service system. The theoretical models typically represent a **stochastic process** where random variables govern arrivals and service times. The objective is to analyze performance measures such as average waiting time, average queue length, server utilization, and the probability of a customer having to wait.

**Whay is Qt about?**

At its core, **Queueing Theory** is the mathematical study of waiting lines. Its objective is to **analyze, model, and predict the behavior of systems** where "entities" (such as customers, products, calls, or data) arrive seeking a service but must wait if "servers" (resources like cashiers, machines, operators, or processors) are busy.

The nucleus of any queueing system can be broken down into:

* **Entities:** The elements that flow through the system and demand service.
* **The Queue:** The place where entities wait.
* **The Service Station:** The combination of the queue and the servers providing the service.

### The Analytical Approach and its Limitations

Queueing Theory provides us with a powerful set of **mathematical formulas (analytical solutions)** to calculate key performance indicators:

* **Lq​**: The average number of entities in the queue.
* **Wq​**: The average waiting time in the queue.
* **L**: The average number of entities in the entire system (in queue + in service).
* **W**: The average total time in the system.

For these formulas to work, the system must be classified using a standard notation, such as the **Kendall Notation (A/B/C/D/E)**, which describes the system's characteristics (e.g., arrival type, service type, number of servers).

<details>

<summary>Kendall's Notation</summary>

The **Kendall Notation** is a standardized way to describe queues in waiting line systems and is vital for classifying models within queueing theory. The notation typically takes the form of **A/B/C/D/E**, where:

* **A**: **Inter-arrival time distribution** (e.g., **M** for Markovian/Poisson, **D** for Deterministic, **G** for General).
* **B**: **Service time distribution** (e.g., **M** for Markovian/Exponential, **D** for Deterministic, **G** for General).
* **C**: **Number of servers** (e.g., **1** for a single server, **c** for multiple servers).
* **D**: **Total system capacity** (e.g., can be **∞** for unlimited, or a specific number).
* **E**: **Population size** of customers (e.g., can be **∞** for unlimited, or a finite number).

Properly using this notation helps in quickly identifying the system's characteristics and applying the appropriate analytical formulas.

</details>

However, this is where we encounter the **major limitation of pure theory**: these formulas are only valid under **very strict and simplified assumptions**.

For example, classic formulas assume that arrivals follow a Poisson distribution and service times follow an Exponential distribution (the M/M/1 system, for instance).

**What happens when the real system is more complex?**

* **If service times follow a Normal or Triangular distribution?**
* **If there are multiple steps in the process with different types of resources?**
* **If customers can abandon the queue (renege)?**
* **If there are priorities (VIP customers)?**

In these cases, mathematical solutions become **extremely complex** or, most often, simply **do not exist**.

A utilization factor below 1 indicates that the system has **sufficient capacity** to serve customers.

### Queueing Theory in Practice with AnyLogic

The concepts of Queueing Theory map directly to the blocks of AnyLogic's Process Modeling Library (PML):

* **Entity arrivals** are modeled with the **`Source`** block.
* **The queue** is modeled with the **`Queue`** block (or the internal queue of the `Service` block).
* **Servers** are modeled as **`Resources`** within a **`ResourcePool`**.
* **The service station** is modeled with a **`Service`** block (which combines `Seize`, `Delay`, and `Release`).

### What is an **INPUT** in a system:

The **input** is denoted as the entry of agents into the system. The first characteristic we encounter is **Size**, which is the total number of customers that may require the service offered by the system at a specific moment—in other words, the potential customers.

This input population can be of **finite or infinite size**; some authors also call it of limited or unlimited nature.

The **statistical pattern** by which customers are generated over time must be specified. The most common assumption is that they are generated by a **Poisson distribution**.

<details>

<summary><strong>Poisson distribution</strong></summary>

It's a **discrete probability distribution** that expresses the probability of a given number of events occurring in a fixed interval of time or space. These events must happen with a constant average rate and be independent of one another. The probability formula for exactly k events to occur is:

$$P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}$$

where λ is the average rate of event occurrence and e is the base of the natural logarithm. This distribution is commonly used to model the arrival of entities in systems such as queues or service processes.

</details>

<img src="../../../.gitbook/assets/file.excalidraw (2).svg" alt="Sistema de colas conceptual" class="gitbook-drawing">

## Queue Discipline

The queue discipline refers to the **rule or policy by which entities (customers, jobs, items) are selected from the queue to be served** (Law, 2015; Banks et al., 2010). It dictates the order in which waiting entities receive service and can significantly impact system performance metrics such as individual waiting times, throughput, and fairness.

The theoretical representation of queue discipline is typically a logical rule that prioritizes entities based on their attributes or their arrival sequence.

Here are the most common types of queue disciplines:

#### 1. First-Come, First-Served (FCFS) / First-In, First-Out (FIFO)

* **Description:** This is the most common and intuitive queue discipline. Entities are served in the exact order in which they arrive at the queue.
* **Theoretical Perspective:** If Ai​ is the arrival time of entity i, then entity i will be served before entity j if and only if Ai​\<Aj​.
* **Applications:** Supermarket checkout lines, typical call centers, bank queues.
* **Properties:** Generally considered fair, as it respects the order of arrival.

#### 2. Last-Come, First-Served (LCFS) / Last-In, First-Out (LIFO)

* **Description:** Entities that arrive most recently are served first.
* **Theoretical Perspective:** If Ai​ is the arrival time of entity i, then entity i will be served after entity j if and only if Ai​\<Aj​, assuming both are still in the queue when a server becomes free.
* **Applications:** Less common in customer service but can be found in inventory management (e.g., stacking new items on top of old ones) or certain data processing queues where the newest information is prioritized.
* **Properties:** Can lead to "starvation" of entities that arrive early if the system is continuously busy.

#### 3. Service In Random Order (SIRO)

* **Description:** When a server becomes free, an entity is selected from the queue for service completely at random, without regard to arrival time or any other attribute.
* **Applications:** Rarely seen in explicit customer service but might implicitly occur in chaotic or poorly managed waiting areas. Could be a simplification for certain simulation models where order doesn't strictly matter.
* **Properties:** Offers no explicit fairness and can lead to highly variable waiting times for entities.

#### 4. Priority Queueing

* **Description:** Entities are classified into different priority groups, and those with higher priority are served before those with lower priority. Within the same priority class, another discipline (e.g., FCFS) is often applied. Priority can be **preemptive** (a higher-priority entity can interrupt a lower-priority entity currently in service) or **non-preemptive** (a higher-priority entity waits for the current service to finish, then gets served next).
* **Theoretical Perspective:** Each entity i has an associated priority Pi​. If Pi​>Pj​, entity i is served before entity j, regardless of arrival time.
* **Applications:** Emergency rooms (critical patients get higher priority), manufacturing systems (rush orders, machine repair tasks), network traffic (VoIP data over regular data).
* **Properties:** Improves service for high-priority entities but can significantly increase waiting times for lower-priority ones.

#### 5. Shortest Processing Time (SPT) / Shortest Job First (SJF)

* **Description:** Entities with the shortest estimated service time are selected next from the queue.
* **Applications:** Manufacturing job shops (to reduce average work-in-process and lead times), computer CPU scheduling.
* **Properties:** Tends to minimize the average number of entities in the system and average waiting time. However, longer jobs might experience very long waits or "starvation." This requires knowing or estimating the service time in advance.

#### 6. Longest Processing Time (LPT)

* **Description:** Entities with the longest estimated service time are selected next.
* **Applications:** Less common for reducing waiting times but might be used in specific scheduling contexts (e.g., to clear large jobs first to free up capacity if long jobs block subsequent processes).
* **Properties:** Can maximize the average time in the system and queue for most entities.

#### Importance in Simulation Modeling

The choice and implementation of the correct queue discipline are critical in simulation modeling because:

* It directly impacts the **performance measures** of the system, especially those related to waiting times and throughput.
* It reflects the **operational policies** and fairness criteria of the real system.
* Incorrectly modeling the queue discipline can lead to **invalid simulation results** and misguided decisions.

In simulation software like **AnyLogic**, these disciplines are often pre-built options within queueing blocks or can be customized using programming logic for more complex, user-defined rules.

***

### Mecanismos de Servidores o de Estaciones de Servicio

los diferentes tipos de mecanismos y cómo pueden ser implementados.

{% tabs %}
{% tab title="Unico Servidor" %}
En este sistema, un único servidor gestiona todas las solicitudes de los usuarios. Este método es sumamente simple de implementar y administrar, lo que lo hace muy atractivo para proyectos pequeños o medianos debido a su bajo costo inicial y económico.&#x20;

Sin embargo, presenta ciertas limitaciones significativas si no se maneja adecuadamente el tráfico de solicitudes. A medida que el volumen de tráfico y solicitudes aumenta, el servidor puede fácilmente convertirse en un cuello de botella, afectando negativamente el rendimiento general del sistema.&#x20;

Esto se debe a que la capacidad de procesamiento de un solo servidor es finita y puede llevar a tiempos de respuesta más lentos, especialmente durante períodos de alta demanda. Además, el riesgo de tiempo de inactividad es mayor, ya que si el servidor falla, no hay copias de seguridad inmediatas que tomen su lugar. Es vital evaluar cuidadosamente estas consideraciones antes de optar por un enfoque de servidor único para aplicaciones críticas o de
{% endtab %}

{% tab title="Mecanismos de Servidores Múltiples" %}
En este sistema, un único servidor gestiona todas las solicitudes. Este método es simple de implementar y gestionar, pero puede generar cuellos de botella si el volumen de solicitudes es alto.

**Servidores Paralelos**

Varios servidores trabajan de manera simultánea para repartir la carga de trabajo. Es ideal para servicios con alta demanda, reduciendo tiempos de espera significativamente.

**Servidores en Serie**

Las solicitudes pasan de un servidor a otro en una secuencia predefinida. Este enfoque es útil para procesos que requieren múltiples etapas de atención.

#### Sistemas Distribuidos

Esta estrategia combina múltiples servidores ubicados en diferentes lugares, permitiendo gestionar solicitudes en una amplia área geográfica. Es útil para organizaciones que operan en varias ubicaciones.
{% endtab %}
{% endtabs %}

<img src="../../../.gitbook/assets/file.excalidraw (1).svg" alt="Sistema de colas Basico" class="gitbook-drawing">

### Distribuciones de tiempos de servicio:

* M = Distribucion exponencial

La distribución exponencial es una distribución de probabilidad continua que describe el tiempo entre eventos en un proceso de Poisson. Es una distribución clave para modelar el tiempo de servicio en sistemas de colas. Se caracteriza por su tasa de ocurrencia constante, lo que significa que no importa cuánto tiempo haya pasado desde el último evento, la probabilidad de que ocurra un nuevo evento en el siguiente instante es la misma. La función de densidad de probabilidad de una distribución exponencial se expresa como:

$$
f(x; \lambda) = \lambda e^{-\lambda x}
$$

donde ( \lambda ) es la tasa de ocurrencia y ( x ) es el tiempo. Esta propiedad de "sin memoria" hace que sea muy útil en diversos contextos, como la modelización de tiempos de espera en colas y sistemas de telecomunicaciones.

* D = distribucion degenerada

La **distribución degenerada** es una distribución de probabilidad que concentra toda su probabilidad en un solo punto. En otras palabras, es una distribución donde una variable aleatoria siempre toma el mismo valor con probabilidad 1. Si ( X ) es una variable con distribución degenerada en ( a ), se denota como $$X \sim D(a)$$ y se define por:

$$
P(X = a) = 1
$$

Esta distribución no tiene variabilidad y, por lo tanto, su varianza es cero. En contextos prácticos, se considera que no introduce incertidumbre o aleatoriedad en los escenarios de modelización.

* Distribucion de Erlang

La **distribución de Erlang** es un caso particular de la distribución gamma, utilizada frecuentemente en la teoría de colas y en modelización de tiempo entre eventos. La distribución de Erlang está definida por dos parámetros: un número entero ( k ), que indica el número de fases exponenciales idénticas, y un parámetro de tasa $$\lambda$$ , que es la tasa de cada fase exponencial. Se denota como $$X \sim \text{Erlang}(k, \lambda)$$ y su función de densidad es:

$$
f(x; k, \lambda) = \frac{\lambda^k x^{k-1} e^{-\lambda x}}{(k-1)!}, \quad x \geq 0
$$

Esta distribución se caracteriza por su capacidad de modelar procesos donde se requiere que ocurran múltiples eventos independientes previamente.

* G = Distribucion General

La **distribución general** (G) se refiere a una clase amplia de distribuciones que no se ajustan necesariamente a una forma específica, como las distribuciones normal, exponencial o Erlang. En modelado estadístico y teoría de colas, se utiliza para representar procesos que tienen características arbitrarias y no específicas. La función de densidad de probabilidad y las propiedades exactas de una distribución general pueden variar significativamente dependiendo del contexto particular en el que se aplique.

### Notacion de la teoria de colas

* estado del sistema: Numero de clientes en el sistema
* Longitud de la cola: Numero de clientes que esperan el servicio
  * estado del sistema _menos_ numero de clientes a quienes se les da el servicio.
* N(t): Número de clientes en el sistema de colas en el tiempo $$t(t \ge 0)$$
* $$P_n(t)$$: Probabilidad de que exactamente n clientes esten en el sistema en el tiempo t, dado el número en tiempo 0
* s: Número de servidores
* $$\lambda_n$$: tasa media de llegadas de nuevos clientes cuando hay n clientes en el sistema
* $$\mu_n$$ tasa media de servicio en todo el sistema cuando hay n clientes en el sistema.
* Cuando $$\lambda_n$$  es constante para toda n, esta constante se escribe como  $$\lambda$$,
*   Cuando la _tasa media de servicio_ por servidor ocupado es constante para toda n $$n \ge 1$$, esta constante se escribe como $$\mu$$

    * $$\mu_n = s\mu, cuando\ n\ge s,$$ cuando los servidores estan ocupados
    * $$\frac{1}{\lambda}$$ _tiempo esperado entre llegadas_
    * $$\frac{1}{\mu},$$ tiempo esperado de servicio
    * $$\rho = \frac{\lambda}{(s\mu)},$$ es el _factor de utilizacion_ de la instalacion de servicio, la fraccion esperada de tiempo en que los setvidores individuales están ocupados, es la fraccion de la capacidad usada del servicio por los clientes que llegan.

    Cuando el sistema esta en ejecusion al inicio de este, cuando los clientes apenas estan entrando al sistema se conoce como _estado inicial_ es un estado donde el mismo comportamiento del sistema es dificil de evidenciar ya que se esta estabilizando, una ves relaizado o pasado este fenomeno el sistema entra en lo que se conoce como _estado estable_, esta ultima es el foco de observacion de la teoria de colas.

    * $$P_n =$$ probabilidad de que haya exactamente n clientes en el sistema
    * $$L =$$ número esperado de clientes en el sistema = $$\sum_{n=0}^{\infin}nP_n$$
    * $$L_q =$$longitu esperada de la cola, este excluye a los clientes que estan en el modo _servicio_ = $$\sum_{n = s}^{\infin}(n-s)P_n$$
    * $$W =$$tiempo de espera en el sistema, incluye le tiempo de servicio para cada cliente $$W = E(W)$$
    * $$W_q=$$ tiempo de espera en el sistema, excluye el tiempo de servicio para cada cliente $$W_q = E(W_q)$$

### Papel de la Distribución Exponencial

La **distribución exponencial** es fundamental en la teoría de colas debido a su capacidad para modelar situaciones en las que los eventos ocurren de manera continua y a una tasa constante. Una de las propiedades más importantes de la distribución exponencial es su falta de memoria, lo que significa que el tiempo de espera restante para un evento es independiente del tiempo ya transcurrido. Esta propiedad simplifica en gran medida el análisis de sistemas de colas, especialmente en los modelos **M/M/1**, donde las llegadas y el servicio siguen un proceso de Poisson y tiempos de servicio exponenciales respectivamente.

#### Aplicaciones

* **Modelado de tiempos de servicio**: En sistemas donde el tiempo de servicio real varía de manera aleatoria, y la tasa promedio es constante.
* **Análisis de espera**: Determinar tiempos de espera promedio en sistemas de colas.
* **Eficiencia de la red**: En redes de comunicación para modelar la llegada de paquetes y la duración de las conexiones.

La simplicidad matemática de la distribución exponencial permite realizar cálculos y simulaciones eficientes, siendo una herramienta esencial para la optimización y diseño de sistemas de colas.

#### Proceso de Nacimiento y Muerte

En la teoría de colas, el **proceso de nacimiento y muerte** es un tipo de proceso estocástico que modela sistemas donde las llegadas y servicios pueden ser descritos por tasas constantes. Estos nombres se deben a la analogía con los procesos demográficos: "nacimiento" se refiere a la llegada de un nuevo cliente al sistema, mientras que "muerte" representa la salida de un cliente tras ser atendido.

**Descripción del Proceso**

1. **Estado del sistema**: El sistema se encuentra en un estado determinado por el número de clientes presentes.
2. **Tasa de nacimiento** $$\lambda$$: La tasa a la que nuevos clientes llegan al sistema. En modelos de colas, esta suele seguir la distribución exponencial.
3. **Tasa de muerte** $$\mu$$: La tasa a la que los clientes completan su servicio y dejan el sistema. También modelada a menudo por la distribución exponencial.

**Ejecución**

* **Transiciones entre estados**: Un cambio de estado ocurre cuando un cliente llega o se va.
* **Balance de tasas**: En el estado estacionario, el sistema puede lograr un equilibrio donde la tasa promedio de nacimientos iguala a la tasa promedio de muertes.

#### Aplicaciones

El proceso de nacimiento y muerte es básico en el análisis de colas **M/M/1**, ayudando a calcular métricas como el tamaño promedio de la cola y el tiempo de espera medio, cruciales para optimizar el rendimiento de sistemas de servicio.

#### Ejemplo Uno de Teoría de Colas

**Problema:**

Supongamos un sistema de colas **M/M/1** donde los clientes llegan a una tasa de $$\lambda = 4$$ clientes por hora y son atendidos a una tasa de $$\mu = 5$$ clientes por hora. Calcule el tamaño promedio de la cola y el tiempo de espera promedio en el sistema.

**Solución:**

Primero, calculemos la utilización del sistema ((\rho)):\
$$\rho = \frac{\lambda}{\mu} = \frac{4}{5} = 0.8$$

**Tamaño promedio de la cola ((L\_q)):**\
$$L_q = \frac{\rho^2}{1 - \rho} = \frac{0.8^2}{1 - 0.8} = \frac{0.64}{0.2} = 3.2$$

**Tiempo de espera promedio en el sistema ((W)):**\
$$W = \frac{1}{\mu - \lambda} = \frac{1}{5 - 4} = 1 \text{ hora}$$

Por lo tanto, el tamaño promedio de la cola es de 3.2 clientes, y el tiempo de espera promedio en el sistema es de 1 hora.

#### Ejemplo 2: Sistema con múltiples servidores

Consideremos un sistema con **N** servidores, donde la tasa de llegada de clientes es $$\lambda$$ y cada servidor atiende a una tasa de $$\mu$$.

**Utilización del sistema** $$\rho$$**:**\
$$[ \rho = \frac{\lambda}{N \cdot \mu} ]$$

**Probabilidad de que un cliente espere** $$P_w$$**:**\
Cuando la utilización del sistema es alta $$\rho \approx 1$$, es más probable que haya clientes esperando. Se puede calcular usando la fórmula de Erlang B o C dependiendo del modelo elegido.

**Tamaño promedio de la cola** $$L_q$$**:**\
$$[ L_q = \frac{(\frac{\lambda}{\mu})^N (\rho)}{N! (1-\rho)^2} \times P_0 ]$$\
Donde  $$P_0$$ es la probabilidad de que no haya clientes en el sistema.

**Tiempo de espera promedio en el sistema ((W)):**\
$$[ W = \frac{L}{\lambda} ]$$\
Donde ( L ) es el número promedio de clientes en el sistema, que puede ser calculado como $$L = L_q + \frac{\lambda}{\mu}$$.

#### Sistema de Colas en un Restaurante

En un restaurante, el sistema de colas se puede modelar de manera similar a un sistema de servidores múltiples, donde cada mesero actúa como un servidor capaz de manejar múltiples clientes a la vez.

* **Clientes y Meseros**: Los clientes llegan al restaurante y forman una cola si todos los meseros están ocupados. La tasa de llegada de clientes se simboliza por $$\lambda$$, y cada mesero tiene una tasa de servicio $$\mu$$, que indica la velocidad a la que puede atender a los clientes.
* **Utilización**: Al igual que en el modelo teórico, la utilización de cada mesero, $$ho$$, se calcula como $$ho = \frac{\lambda}{N \cdot \mu}$$ donde **N** es el número de meseros.
* **Probabilidad de Espera**: Durante las horas pico, cuando la utilización es alta ($$ho \approx 1$$), es probable que los clientes tengan que esperar antes de ser atendidos.
* **Tamaño de la Cola y Tiempo de Espera**: Siguiendo las fórmulas mencionadas anteriormente, se puede calcular el tamaño promedio de la cola y el tiempo promedio que un cliente espera en el sistema.

### Ejemplo 3 de un Restaurante con 3 Meseros

Supongamos que un restaurante tiene 3 meseros disponibles para atender a los clientes. La tasa promedio de llegada de clientes al restaurante es de 15 clientes por hora ($$\lambda = 15$$), y cada mesero puede atender a un cliente en un promedio de 20 minutos, es decir, la tasa de servicio por mesero es de 3 clientes por hora ($$\mu = 3$$).



#### Resolución del Problema

1.  **Cálculo de la Utilización**: La utilización de cada mesero se calcula usando la fórmula:

    $$ho = \frac{\lambda}{N \cdot \mu} = \frac{15}{3 \cdot 3} = \frac{15}{9} = \frac{5}{3} \approx 0.56$$

    Esto indica que cada mesero está ocupado aproximadamente un 56% del tiempo.

#### Otros Cálculos del Sistema de Meseros

2. **Tiempo de Espera en Cola (Wq)**: Este se calcula usando la fórmula de Little y el modelo M/M/c, donde Wq es la cantidad promedio de tiempo que un cliente espera en la cola antes de ser atendido.

Para calcular el **Tiempo de Espera en Cola (Wq)**, se utiliza la fórmula para sistemas M/M/c:

$$Wq = \frac{L_q}{\lambda} = \frac{\rho^c \cdot \frac{1}{c!} \cdot \frac{c \cdot \mu}{c \cdot \mu - \lambda} \cdot P_0}{\lambda}$$

donde:

* $$\rho$$ es la utilización del sistema.
* c es el número de meseros.
* $$P_0$$ es la probabilidad de que haya 0 clientes en el sistema.

Para calcular $$P_0$$, que es la probabilidad de que haya 0 clientes en el sistema, se utiliza la siguiente fórmula en un sistema M/M/c:

$$
P_0 = \left[ \sum_{n=0}^{c-1} \frac{(\lambda/\mu)^n}{n!} + \frac{(\lambda/\mu)^c}{c!} \cdot \frac{1}{1 - \rho} \right]^{-1}
$$

donde:

* $$\lambda$$ es la tasa de llegada de clientes.
* $$\mu$$ es la tasa de servicio de los meseros.
* $$\rho = \frac{\lambda}{c \cdot \mu}$$ es la utilización del sistema.

Esta fórmula ayuda a determinar la probabilidad de que el sistema esté vacío, lo cual es crucial para calcular otros parámetros del sistema de colas.

***

### Teoria de colas en sistemas de inventarios

Para ilustrar el uso de la teoría de colas en la gestión de inventarios, consideremos un ejemplo sencillo de un sistema de inventario donde las llegadas de demanda siguen un proceso de Poisson y los tiempos de reposición son exponencialmente distribuidos.

Imaginemos un minorista que gestiona un inventario con las siguientes características:

* La tasa de llegada de demanda es $$\lambda = 5\text{ unidades/día}$$.
* La tasa de suministro o reposición es $$\mu = 8\text{ unidades/día}$$.

#### Cálculo de las métricas del sistema:

1. **Nivel de Inventario Esperado**: Se basa en calcular el número promedio de unidades en inventario considerando las tasas de llegada y servicio. Generalmente se asume que el inventario opera bajo un control $$(s, Q)$$ donde $s$ es el punto de reorden y $Q$ es la cantidad de pedido.

En este contexto, calcularemos la utilización del sistema como:

$$ho = \frac{\lambda}{\mu} = \frac{5}{8} = 0.625$$

Esto indica que el sistema está ocupado el 62.5% del tiempo, sugiriendo una baja probabilidad de ruptura de stock mientras el inventario es repuesto consistentemente. La probabilidad exacta de ruptura de stock y el nivel de inventario se derivan adicionalmente mediante métodos específicos de la teoría de colas, como abordar el sistema como un modelo $$M/M/1$$ o $$M/M/c$$, dependiendo de la configuración.

#### Ejemplo de Cálculo del Nivel de Inventario

Supongamos un sistema de gestión de inventario con las siguientes características:

* **Tasa de llegada** $$\lambda$$**:** 5 unidades por hora
* **Tasa de servicio** $$\mu$$**:** 8 unidades por hora
* **Punto de reorden s:** 10 unidades
* **Cantidad de pedido Q:** 20 unidades

Para calcular el **nivel de inventario esperado**, primero determinamos la **utilización del sistema** como se muestra anteriormente:

$$ho = \frac{\lambda}{\mu} = \frac{5}{8} = 0.625$$

Con esta utilización y asumiendo un modelo de tipo $$M/M/1$$, podemos calcular el _número promedio de unidades en inventario_ utilizando la fórmula del nivel de trabajo en un sistema de colas:

$$L = \frac{\lambda}{\mu - \lambda} = \frac{5}{8-5} = \frac{5}{3} \approx 1.67 \text{ unidades}$$

Este resultado indica que, en promedio, hay aproximadamente 1.67 unidades en inventario mientras el sistema lanza pedidos cada vez que cae por debajo del punto de reorden.

Para calcular la **probabilidad de ruptura de stock** en un sistema $$M/M/1$$, se utiliza la fórmula de la probabilidad de que no haya unidades disponibles, que es igual a la probabilidad de que el sistema esté vacío. Esta probabilidad viene dada por:

$$P_0 = 1 - \frac{\lambda}{\mu} = 1 - 0.625 = 0.375$$

Por lo tanto, hay un 37.5% de probabilidad de que el inventario esté vacío en cualquier momento dado.

