---
description: >-
  understands that Queueing Theory is a fundamental analytical discipline within
  Operations Research. It provides a mathematical framework for analyzing
  systems where customers or items arrive.
icon: colon
---

# Queueing theory - Analytical models

{% hint style="info" %}
The basic process assumed by most models is that customers want a service
{% endhint %}

## Queueing theory

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

<img src="../../../.gitbook/assets/file.excalidraw (2) (1) (1) (1).svg" alt="Sistema de colas conceptual" class="gitbook-drawing">

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

The M/G/K case is a complex solving scenario, and is virtualy imposible to capture thise detail in an **analithycal solution, in this case we use symiulation aproach.**

<figure><img src="../../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

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

<img src="../../../.gitbook/assets/file.excalidraw (1) (1) (1) (1) (1) (1) (1) (1).svg" alt="Sistema de colas Basico" class="gitbook-drawing">

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

***

## Example of Queuing Theory

### **Example One: M/M/1 - Basic**

Suppose a M/M/1 queuing system where customers arrive at a rate of $$\lambda = 4$$ customers per hour and are served at a rate of $$\mu = 5$$ customers per hour. Calculate the average queue size and average wait time in the system.

**Solution:**

1. et's calculate the system utilization $$\rho$$:\
   $$\rho = \frac{\lambda}{\mu} = \frac{4}{5} = 0.8$$
2. Average queue size $$L_q$$:\
   $$L_q = \frac{\rho^2}{1 - \rho} = \frac{0.8^2}{1 - 0.8} = \frac{0.64}{0.2} = 3.2$$
3. Average waiting time in the system $$W$$\
   $$W = \frac{1}{\mu - \lambda} = \frac{1}{5 - 4} = 1 \text{ hora}$$

Therefore, the average queue size is 3.2 customers, and the average wait time in the system is 1 hour.

### Example 2: System with multiple servers

Consider a system with N servers, where the client arrival rate is $$\lambda$$ and each server serves at a rate of $$\mu$$.

1. system utilization $$\rho$$**:**\
   $$[ \rho = \frac{\lambda}{N \cdot \mu} ]$$
2. Probability that a customer will wait $$P_w$$**:**\
   When system utilization is high $$\rho \approx 1$$, It's more likely that there will be customers waiting. This can be calculated using the Erlang B or C formula, depending on the model chosen.
3. Average tail size $$L_q$$**:**\
   $$[ L_q = \frac{(\frac{\lambda}{\mu})^N (\rho)}{N! (1-\rho)^2} \times P_0 ]$$\
   Where  $$P_0$$ is the probability that there are no customers in the system.
4. Average waiting time in the systema $$W$$**:**\
   $$[ W = \frac{L}{\lambda} ]$$\
   Where ( L ) is the average number of customers in the system, which can be calculated as $$L = L_q + \frac{\lambda}{\mu}$$.

### Queuing System in a Restaurant

In a restaurant, the queuing system can be modeled similarly to a multi-server system, where each server acts as a server capable of handling multiple customers at once.

* Customers and Waiters: Customers arrive at the restaurant and form a queue if all the waiters are busy. The customer arrival rate is symbolized by $$\lambda$$, and each waiter has a service charge $$\mu$$, which indicates the speed at which you can serve customers.
* Utilization: As in the theoretical model, the utilization of each waiter, $$ho$$, it´s calculated as $$ho = \frac{\lambda}{N \cdot \mu}$$ where N is the number of waiters.
* Probability of Waiting: During peak hours, when utilization is high ($$ho \approx 1$$), Customers may have to wait before being served.
* Queue Size and Wait Time: Following the formulas mentioned above, you can calculate the average queue size and the average time a customer waits in the system.

### Example three: A Restaurant with 3 Servers

Suppose a restaurant has 3 servers available to serve customers. The average customer arrival rate at the restaurant is 15 customers per hour. ($$\lambda = 15$$), and each server can attend to one customer in an average of 20 minutes, meaning the service rate per server is 3 customers per hour ($$\mu = 3$$).

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

### Queueing Theory In Inventory System

This analogy allows for the application of queueing models to analyze and optimize various aspects of inventory systems, particularly those characterized by **stochastic demand** and **variable lead times**.

#### The Analogy in the system

* **"Customers" or "Entities":** In inventory systems, these are often **demand requests** for items.
* **"Servers":** The **inventory itself** acts as the server. When an item is in stock, it "serves" the demand immediately. If an item is out of stock, demand "waits" (is backordered) or is "lost."
* **"Queue":**
  * **Positive Inventory:** Can be seen as a "queue" of available items waiting for demand to "arrive."
  * **Backorders/Shortages:** Represent a "queue" of unfulfilled demand waiting for new inventory to "arrive" (from production or replenishment).
* **"Arrival Rate" (λ):** The **demand rate** for items.
* **"Service Rate" (μ):** The rate at which inventory is replenished or available for consumption. This might be related to production capacity or supplier lead times.
* **"Service Time":** The time it takes to "serve" a demand once an item is available. If an item is in stock, this time is effectively zero. If there's a backlog, it's the time until replenishment.

#### Applications of Queueing Theory in Inventory Systems

1. **Modeling Demand and Lead Times:** Queueing theory provides frameworks to model stochastic demand patterns (e.g., Poisson arrivals for independent demands) and variable lead times (e.g., exponential or Erlang distributions for replenishment times).
2. **Analyzing Stockout Probabilities and Backlogs:** By treating unsatisfied demand as a queue, one can use queueing models to:
   * Estimate the probability of a stockout.
   * Calculate the average number of backordered items (average queue length of unfulfilled demand, Lq​).
   * Determine the average time a backorder remains unfulfilled (average waiting time for backorders, Wq​).
3. **Optimizing Reorder Points and Safety Stock:** Understanding the queueing dynamics helps in setting appropriate reorder points and safety stock levels. A higher safety stock reduces the "queue" of unfulfilled demand (backorders) and decreases the probability of stockouts, but increases holding costs. Queueing models can help find the balance.
4. **Evaluating Replenishment Policies:** Different inventory replenishment policies (e.g., continuous review, periodic review) can be analyzed as different "service mechanisms" or "queue disciplines" for satisfying demand.
5. **Perishable Inventory:** For perishable goods, queueing concepts can model items "waiting" to be sold before they expire, with "spoilage" analogous to entities leaving the system without service.

To illustrate the use of queueing theory in inventory management, let's consider a simple example of an inventory system where demand arrivals follow a Poisson process and replenishment times are exponentially distributed.

Imagine a retailer managing an inventory with the following characteristics:

* The demand arrival rate is
  * $$\lambda = 5\text{ unidades/día}$$.
* The Supply rate is:
  * &#x20;$$\mu = 8\text{ unidades/día}$$.

### Calculation of System Metrics

1. **Expected Inventory Level:** This is based on calculating the average number of units in inventory, considering arrival and service rates. It's generally assumed that the inventory operates under an **(s,Q) control policy**, where s is the reorder point and Q is the order quantity.

so we proceed to calculate the system as h\_0

$$ho = \frac{\lambda}{\mu} = \frac{5}{8} = 0.625$$

This indicates that the system is busy **62.5% of the time**, suggesting a **low probability of a stockout** as long as the inventory is consistently replenished. The exact probability of a stockout and the inventory level are further derived using specific queueing theory methods, such as approaching the system as an **M/M/1 or M/M/c model**, depending on the configuration.

***

### Example of Inventory Level Calculation

Suppose an inventory management system with the following characteristics:

* **Arrival rate (λ):** 5 units per hour
* **Service rate (μ):** 8 units per hour
* **Reorder point (s):** 10 units
* **Order quantity (Q):** 20 units

To calculate the expected inventory level, we first determine the system utilization as shown previously:

$$ho = \frac{\lambda}{\mu} = \frac{5}{8} = 0.625$$

With this utilization, and assuming an M/M/1 type model, we can calculate the **average number of units in inventory** using the formula for the work-in-process level in a queueing system:

$$L = \frac{\lambda}{\mu - \lambda} = \frac{5}{8-5} = \frac{5}{3} \approx 1.67 \text{ unidades}$$

This result indicates that, on average, there are approximately **1.67 units in inventory** while the system places orders whenever it falls below the reorder point.

To calculate the **probability of a stockout** in an M/M/1 system, the formula for the probability of no units being available is used, which is equal to the probability that the system is empty. This probability is given by:

$$P_0 = 1 - \frac{\lambda}{\mu} = 1 - 0.625 = 0.375$$

Therefore, there is a **37.5% probability** that the inventory will be empty at any given time.

