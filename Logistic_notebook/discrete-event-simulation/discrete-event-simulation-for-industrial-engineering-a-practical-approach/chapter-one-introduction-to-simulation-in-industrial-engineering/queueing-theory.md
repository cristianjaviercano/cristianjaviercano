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

## Server Mechanisms or Service Stations

the different types of mechanisms and how they can be implemented.

{% tabs %}
{% tab title="Unique Server" %}
A **unique server** (also often referred to as a **single server**) describes a service station where there is **only one resource available to process entities at any given time**.

Theoretically, in such a configuration, entities requiring service will form a single queue and wait for this sole server to become available. This is the simplest configuration in queueing theory models.

**Key Characteristics:**

* **Single Channel:** Only one processing unit or individual capable of providing the service.
* **Sequential Processing:** Entities are processed one after another. If an entity arrives while the server is busy, it must wait in a queue.
* **Utilization Sensitivity:** The utilization of a unique server is highly sensitive to fluctuations in arrival rates and service times. Even small increases in demand can lead to significant increases in queue lengths and waiting times if the server's capacity is approached.
{% endtab %}

{% tab title="Multiple Server Mechanisms" %}


As an industrial engineer and researcher, understanding **multiple server mechanisms** is fundamental for analyzing and designing many real-world systems. This configuration involves **two or more identical resources (servers) working in parallel** to provide service to entities from a common queue (Law, 2015; Banks et al., 2010).

The theoretical benefit of multiple servers, compared to a single server with the same total capacity, is often the **reduction in average queue lengths and waiting times**. This is due to the pooling of waiting lines, allowing any free server to pick up the next available entity.

#### Key Characteristics:

* **Parallel Channels:** The system has c servers (c>1) operating simultaneously.
* **Common Queue:** Entities typically form a single waiting line and are dispatched to the first available server. This common queue is generally more efficient than separate queues for each server.
* **Load Balancing:** The system implicitly balances the workload among the available servers.
* **Reduced Waiting:** The probability of an entity having to wait, and the duration of that wait, generally decrease compared to an equivalent single-server system, especially as utilization approaches capacity.
{% endtab %}
{% endtabs %}

<img src="../../../.gitbook/assets/file.excalidraw (1).svg" alt="Sistema de colas Basico" class="gitbook-drawing">

## Service Time Distributions



### Exponential distribution

The **exponential distribution** is a continuous probability distribution that describes the time between events in a Poisson process. It is a key distribution for modeling service time in queueing systems. It is characterized by its **constant rate of occurrence**, meaning that no matter how much time has passed since the last event, the probability of a new event occurring in the next instant is the same. The probability density function of an exponential distribution is expressed as:

$$
f(x; \lambda) = \lambda e^{-\lambda x}
$$

where λ is the occurrence rate and x is time. This **"memoryless" property** makes it very useful in various contexts, such as modeling waiting times in queues and telecommunications systems.



### Degenerate Distribution

The **degenerate distribution** is a probability distribution that **concentrates all its probability at a single point**. In other words, it is a distribution where a random variable always takes the same value with probability 1. If X is a variable with a degenerate distribution at a, it is denoted as: $$X \sim D(a)$$ and defined by:

$$
P(X = a) = 1
$$

This distribution has **no variability**, and therefore, its variance is zero. In practical contexts, it is considered to introduce **no uncertainty or randomness** into modeling scenarios.



### Erlang distribution



The **Erlang distribution** is a special case of the gamma distribution, frequently used in queueing theory and event time modeling. The Erlang distribution is defined by two parameters: an integer k, which indicates the number of identical exponential phases, and a rate parameter λ, which is the rate of each exponential phase. It is denoted as:$$X \sim \text{Erlang}(k, \lambda)$$ nad his density function is:

$$
f(x; k, \lambda) = \frac{\lambda^k x^{k-1} e^{-\lambda x}}{(k-1)!}, \quad x \geq 0
$$

This distribution is characterized by its ability to model processes where multiple independent events are required to occur beforehand.



General Distribution

The **general distribution (G)** refers to a broad class of distributions that do not necessarily conform to a specific shape, such as the normal, exponential, or Erlang distributions. In statistical modeling and queueing theory, it is used to represent processes that have **arbitrary and non-specific characteristics**. The probability density function and exact properties of a general distribution can vary significantly depending on the particular context in which it is applied.

## Queueing Theory Notation

* system status: Number of customers in the system
* Queue length: Number of customers waiting for service.
  * system state _minus_ number of customers being
* Input:
* N(t): Number of customers in the queueing system at time $$t(t \ge 0)$$
* $$P_n(t)$$: Probability that exactly n customers are in the system at time
* s: Númber of servers
* $$\lambda_n$$: Mean arrival rate of new customers when there are n customers in the system.
* $$\mu_n$$ Mean service rate for the entire system when there are n customers in the system.
* When λ\_n is constant for all n, this constant is written as λ.
*   When the _average service rate_ per busy server is constant for all $$n \ge 1$$, this constant is denoted by $$\mu$$.

    * $$\mu_n = s\mu, \text{ when } n\ge s,$$ when servers are busy.
    * $$\frac{1}{\lambda}$$ is the _expected time between arrivals_.
    * $$\frac{1}{\mu},$$ is the expected service time.
    * $$ho = \frac{\lambda}{(s\mu)},$$ is the _utilization factor_ of the service facility, representing the expected fraction of time individual servers are busy, or the fraction of service capacity used by arriving customers.

    When the system is first starting and customers are just entering the system, it is known as the _initial state_. This is a state where the behavior of the system is hard to observe as it stabilizes. Once this initial phase has passed, the system transitions into what is known as a _steady state_, which is the primary focus of queueing theory.

    * $$P_n =$$ probability of having exactly n customers in the system.
    * $$L =$$ the expected number of customers in the system = $$\sum_{n=0}^{\infty}nP_n$$.
    * $$L_q =$$ expected queue length, excluding customers in _service_ mode = $$\sum_{n = s}^{\infty}(n-s)P_n$$.
    * $$W =$$ the waiting time in the system, including service time for each customer $$W = E(W)$$.
    * $$W_q =$$ the waiting time in the system, excluding service time for each customer $$W_q = E(W_q)$$\


### Role of the Exponential Distributionl

The **exponential distribution** is fundamental in queueing theory due to its ability to model situations where events occur continuously and at a constant rate. One of the most important properties of the exponential distribution is its **memoryless property**, meaning that the remaining waiting time for an event is independent of the time already elapsed. This property greatly simplifies the analysis of queueing systems, especially in **M/M/1 models**, where arrivals and service follow a Poisson process and exponential service times, respectively.

The exponential distribution describes the **time between events in a Poisson process**. If events occur at a constant average rate, then the time elapsed between any two consecutive events follows an exponential distribution. Conversely, if inter-event times are exponentially distributed, the number of events occurring in any fixed interval follows a Poisson distribution. This duality is fundamental.

#### Applications.

* **Modeling service times:** In systems where actual service time varies randomly and the average rate is constant.
* **Waiting line analysis:** To determine average waiting times in queueing systems.
* **Network efficiency:** In communication networks, to model packet arrivals and connection durations.

The mathematical simplicity of the exponential distribution allows for efficient calculations and simulations, making it an essential tool for the optimization and design of queueing systems.

### Birth-Death Process

In queueing theory, the **birth-death process** is a type of stochastic process that models systems where arrivals and services can be described by constant rates. These names stem from the analogy with demographic processes: "birth" refers to the arrival of a new customer into the system, while "death" represents a customer's departure after being served.

#### Process Description

* **System State:** The system is in a state determined by the number of customers present.
* **Birth Rate (λ):** The rate at which new customers arrive at the system. In queueing models, this typically follows an exponential distribution.
* **Death Rate (μ):** The rate at which customers complete their service and leave the system. Also often modeled by the exponential distribution.

#### Execution

* **Transitions Between States:** A state change occurs when a customer arrives or leaves.
* **Rate Balance:** In the steady state, the system can achieve an equilibrium where the average birth rate equals the average death rate.

#### Applications

The birth-death process is fundamental in the analysis of M/M/1 queues, helping to calculate metrics such as average queue size and mean waiting time, which are crucial for optimizing the performance of service systems.

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

### Example 3: A Restaurant with 3 Servers

Suppose a restaurant has **3 servers** available to attend to customers. The **average customer arrival rate** at the restaurant is **15 customers per hour**. ($$\lambda = 15$$), and each server can attend to one customer in an average of **20 minutes**, meaning the service rate per server is **3 customers per hou** ($$\mu = 3$$).

Solving:

1.  The utilization of each server is calculated using the formula:

    $$ho = \frac{\lambda}{N \cdot \mu} = \frac{15}{3 \cdot 3} = \frac{15}{9} = \frac{5}{3} \approx 0.56$$

    This indicates that each server is busy approximately **56% of the time**.

Other Server System Calculations

2.  **Queue Waiting Time (Wq​):** This is calculated using Little's Law and the M/M/c model, where Wq​ is the average amount of time a customer waits in the queue before being served.

    To calculate the Queue Waiting Time (Wq​), the formula for M/M/c systems is used.:

$$Wq = \frac{L_q}{\lambda} = \frac{\rho^c \cdot \frac{1}{c!} \cdot \frac{c \cdot \mu}{c \cdot \mu - \lambda} \cdot P_0}{\lambda}$$

Where:

* $$\rho$$ sistem usage
* c Number of servers.
* $$P_0$$ Probability that theres Zero clients in the system.

To calculate $$P_0$$, The probability that there are **0 customers in the system**, the following formula is used in an M/M/c system:

$$
P_0 = \left[ \sum_{n=0}^{c-1} \frac{(\lambda/\mu)^n}{n!} + \frac{(\lambda/\mu)^c}{c!} \cdot \frac{1}{1 - \rho} \right]^{-1}
$$

Where:

* $$\lambda$$ Arriving rate of the customers.
* $$\mu$$ Servers service Rate.
* $$\rho = \frac{\lambda}{c \cdot \mu}$$ System Usage.

This formula helps determine the **probability that the system is empty**, which is crucial for calculating other parameters of the queueing system.

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

