---
description: >-
  This chapter introduces the fundamental concepts of simulation within the
  specific context of industrial engineering.
---

# Chapter One: Introduction to Simulation in Industrial Engineering

<img src="../../../.gitbook/assets/file.excalidraw (6).svg" alt="" class="gitbook-drawing">

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

<img src="../../../.gitbook/assets/file.excalidraw (7).svg" alt="Relacion entre los elementos fundamentales de la simulacion" class="gitbook-drawing">

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
The correct classification of a problem and the required model type is a crucial step, as it guides the selection of the most appropriate simulation methodology (e.g., Monte Carlo, Discrete-Event, System Dynamics)
{% endhint %}

Summarizing the previous information, we can define that while simulation models can be classified into countless types, the important thing is to recognize them by their specifications to be able to select the correct interpretation methodology.

| Characterístics Model | Time         | Randomness    | Change of State | Example in IE                                       | Common Simulation Approach             |
| --------------------- | ------------ | ------------- | --------------- | --------------------------------------------------- | -------------------------------------- |
| Estatic               | Not relevant | Deterministic | Not relevant    | Calculation of fixed cost of a product              | (No simulation required)               |
| Estatic               | Not relevant | Stocástic     | Not relevant    | Investment risk analysis (NPV with uncertain flows) | Montecarlo                             |
| Dinamic               | Relevant     | Deterministic | Continuos       | Drug Decay Model (ODE)                              | Continuous-time simulation (numerical) |
| Dinamic               | Relevant     | Stocástic     | Continuos       | Stock pricing model (stock dif. equ.)               | Continuous Time Simulation (Advanced)  |
| Dinamic               | Relevant     | Deterministic | Discrete        | Fixed production plan with scheduled arrivals       | (Can be analytical or simple SED)      |
| Dinamic               | Relevant     | Stocástic     | Discrete        | Queuing system, faulty production line              | Discrete Event Simulation (DES)        |

### Simulation in Operations Research studies

Simulation plays the same role in many studies as IoT, but while IoT seeks optimization or finding a solution, simulation seeks to describe the environment or system in order to understand its behavior and predict or find those faults or elements that add value to timely decisions.

IO is dedicated to designing a design or procedure for some stochastic system, which can operate probabilistically over time,

When Simulation is required as part of an OR study, it is very common that it contains the same steps, the detailed Simulation Model is necessary to formulate and describe the operation and how it should be simulated.

1. Define the State of the system, such as the number of customers in a queuing system
2. identify possible states
3. identify possible events
4. have a Simulation Clock, which records the time
5. Method to generate events randomly
6. A formula to identify state transitions that generate random events

***

### Simulation of Discrete Events (DES) vs. Continuous Events (CES)

The two major categories of simulation are discrete event and continuous event.

DES is a powerful methodology for modeling systems whose state changes at discrete points in time as a result of the occurrence of certain events. Between one event and the next, the state of the system is assumed to remain constant; that is, "nothing significant happens between events." To build and understand DES models, it is crucial to become familiar with their fundamental components.

<details>

<summary>Entities</summary>

They are dynamic objects that "flow" through the system, requesting services, occupying resources, and triggering events. In industrial engineering contexts, entities can be customers in a bank, parts on a production line, orders in a logistics system, trucks in a transportation network, or even data packets in a communications network.

</details>

<details>

<summary>Attributes</summary>

These are the individual properties or characteristics of entities. Attributes allow differentiation between entities of the same type and can influence their processing within the system. For example, a customer (entity) may have attributes such as "required transaction type" or "arrival time." A part (entity) may have attributes such as "product type," "processing route," or "priority."

</details>

<details>

<summary>Activities (or Delays)</summary>

They represent time-consuming operations or processes within the system. An entity may experience an activity, such as being served by a server, being processed by a machine, or traveling from one point to another. The duration of an activity may be deterministic (fixed) or, more commonly in SED, stochastic (random), modeled by a probability distribution.

</details>

<details>

<summary>Events</summary>

They are instantaneous events that can change the state of the system. Events mark the beginning or end of an activity, or any other significant change. Typical examples include the arrival of an entity to the system (arrival event), the end of service for an entity (end-of-service event), or the failure of a machine (failure event).

</details>

<details>

<summary>System Status</summary>

A set of variables that contain all the information necessary to describe the system at a particular instant. The state of the system must be sufficient to resume the simulation from that point if it were stopped. Examples of state variables include the number of customers waiting in a queue, the status of a server (busy, free, under repair), or the inventory level of a product.

</details>

<details>

<summary>Simulation Clock</summary>

It is a variable that maintains the current value of the simulated time. Unlike real time, the simulation clock does not advance continuously, but rather jumps from one event instant to the next. This mechanism is known as "next-event time advance" and is essential for the efficiency of SED.

</details>

<details>

<summary>Event List or Event Calendar</summary>

It is an essential data structure that stores all future events that have been scheduled to occur. The events in this list are typically ordered chronologically, that is, by their scheduled occurrence time. The simulation clock advances to the time of the most imminent event in this list.

</details>

<details>

<summary>Resources</summary>

These are the system components that provide services or are used by entities. These resources typically have limited capacity (e.g., a finite number of cashiers, machines, operators, or loading docks). Entities often compete for the use of these resources.

</details>

<details>

<summary>Queues</summary>

Queues are places within the system where entities wait when they cannot immediately access a resource or service because it is busy or unavailable. Queues are a natural consequence of resource contention in systems with random arrivals and/or services.

</details>

{% hint style="warning" %}
### The interrelationship of these concepts defines the dynamics of a SED model. Entities arrive, possibly with specific attributes, and request resources to perform activities. If resources are unavailable, entities may wait in queues. The occurrence of events (such as arrivals or activity completions) changes the state of the system.Ventajas y desventajas de la simulación
{% endhint %}

It is a powerful analytical tool, but like any methodology, it has both strengths and weaknesses.

It is crucial for the industrial engineer to understand these characteristics in order to decide when and how to apply simulation effectively.

{% tabs %}
{% tab title="Benefits" %}


1. Complex Systems Analysis: Allows the study of systems whose complexity (large number of variables, nonlinear interactions, stochastic behavior) precludes the use of pure analytical methods. Simulation is especially useful for complex queuing systems where mathematical formulas are limited or nonexistent.1\

2. Safe and Economical Experimentation: Facilitates system experimentation without disrupting real operations, building expensive physical prototypes, or exposing the system to unnecessary risks. Radical changes or extreme conditions can be tested in a controlled virtual environment.1\

3. Alternatives Evaluation ("What-if Analysis"): Allows the comparison of different operating policies, system designs, or investment scenarios before implementation. This helps make more informed decisions and select the most promising options.\

4. Time Compression and Expansion: Long periods of operation (years) can be simulated in a matter of minutes or hours of computing time, or, conversely, short-duration events can be analyzed in great detail. Problem Identification and System Understanding: Helps identify bottlenecks, understand the interdependencies between system components, and visualize overall system dynamics. Building the model itself often leads to a better understanding of the system.\

5. Incorporating Randomness and Uncertainty: Allows for modeling and analyzing the impact of variability inherent in real systems (random arrival times, variable service durations, equipment failures, demand fluctuations).\

6. Communication and Visualization Tool: Simulation models, especially those with graphic animation capabilities, are excellent tools for communicating system operation and study results to different audiences, including management and operating personnel.\

7. Training: Simulators can be used as training tools for operators and decision-makers, allowing them to experience the consequences of their actions in a risk-free environment.
{% endtab %}

{% tab title="Disadvantages" %}


1. Cost and Development Time: Developing a valid and detailed simulation model can be a lengthy and expensive process, requiring specialized personnel, software, and significant computational time. Simulation tends to be a relatively expensive process.1\

2. Outputs as Statistical Estimates: Simulation, especially stochastic simulation, produces estimates of system behavior, not exact or optimal solutions (unless combined with optimization techniques). The results are subject to sampling error and require careful statistical analysis for interpretation.1\

3. Data Intensiveness: The validity of a simulation model depends largely on the quality of the input data used to define probability distributions and system parameters. The "garbage in, garbage out" (GIGO) principle fully applies. Collecting and analyzing this data can be challenging. Complexity in Interpreting&#x20;
4. Results: Interpreting simulation output can be complex and requires a good understanding of statistical methods to avoid erroneous conclusions.\

5. Risk of False Confidence: A simulation model, especially a visually appealing one, can generate a false sense of accuracy or validity if it has not been rigorously verified and validated.\

6. Model Specificity: A simulation model is typically specific to the system and objectives for which it was developed. Generalizing its results to other systems or significantly changing the objectives may require substantial revision or the construction of a new model.
{% endtab %}
{% endtabs %}

***

## Steps in a simulation study.

A simulation study is a structured project that follows a series of methodological steps to ensure that the results are credible and useful for decision-making. Verification and validation are critical components of this process, which are performed iteratively throughout the study lifecycle.

### General Phases of a Simulation Project.

{% stepper %}
{% step %}
Definition of the Problem and Establishment of Objectives and Scope of the Study

This is the initial and possibly most crucial step. It involves clearly understanding the system being studied, the problem to be solved, and the specific objectives pursued with the simulation. What questions is the simulation expected to answer? What performance metrics are important?

{% hint style="warning" %}
A poorly defined problem or ambiguous objectives will inevitably lead to an ineffective simulation study.
{% endhint %}
{% endstep %}

{% step %}
Formulation of the Conceptual Model

Once the objectives have been defined, a conceptual model of the system is developed. This involves identifying the key components of the system, relevant variables, the interactions between them, inputs, outputs, and the level of detail or abstraction necessary to meet the study's objectives.

{% hint style="warning" %}
The hypotheses and simplifications to be made must be established.
{% endhint %}
{% endstep %}

{% step %}
Collection and Analysis of Input Data

Simulation requires data to feed the model. This includes data to estimate system parameters (e.g., machine capacities, number of servers) and to characterize the variability of inputs (e.g., customer interarrival times, service times, equipment failure rates) using probability distributions.

{% hint style="warning" %}
The quality of this data is essential for the validity of the model
{% endhint %}
{% endstep %}

{% step %}
Construction of the Computational Model (Programming)

The conceptual model is translated into a computational model using a specific simulation language (e.g. AnyLogic, Simio), a simulation library in a general-purpose language (e.g. SimPy in Python), or even a spreadsheet for simpler models (e.g. Excel for Monte Carlo).

{% hint style="warning" %}
It is recommended to use linear programming logic and its variants for these cases, to make the mathematical model to understand the logic of the system.
{% endhint %}
{% endstep %}

{% step %}
Verification of the Computational Model

Verification focuses on ensuring that the computational model behaves as the modeler designed it—that is, that the program correctly implements the logic and algorithms of the conceptual and specification model.

{% hint style="warning" %}
The key question is: "Did we build the model (program) correctly?
{% endhint %}

1. Verification Techniques (desktop testing)
   1. Code review (code walkthroughs).
   2. Modular testing (testing individual model components).
   3. Use of traces (following execution step by step for simple input values).
   4. Comparison with known results from simple cases or simplified versions of the model.
   5. Verifying logic under extreme parameter conditions.
   6. Using animation to detect anomalous behavior
{% endstep %}

{% step %}
Model Validation

Validation seeks to determine whether the simulation model is a sufficiently accurate representation of the real system for the purposes of the study.

{% hint style="warning" %}
The key question is: "Do we build the correct model (that represents reality)?"
{% endhint %}

_Validation Techniques:_

1. Comparison of model results with historical data from the real system (if available).
2. Review of the model and its results by experts on the real system.
3. Turing tests: Presenting experts with the results of the model and the real system (without identifying which is which) and seeing if they can distinguish them.
4. Sensitivity analysis: Varying the model's input parameters and checking whether the outputs change in a way that is consistent with the expected behavior of the real system.
5. Checking face validity: Does the model appear reasonable to those familiar with the system?
{% endstep %}

{% step %}
Design of Simulation Experiments

Once the model has been verified and validated, the experiments to be performed are planned. This includes defining the scenarios to be evaluated, the alternatives to be compared, the number of replicates (independent runs) for each scenario, the duration of each replicate, and the length of the warm-up period if steady-state results are sought.
{% endstep %}

{% step %}
Execution of Simulation Runs (Production Runs)

Simulations are run according to the experimental design. It is important to properly manage random number generation to ensure independence between replicates or reproducibility, if necessary.
{% endstep %}

{% step %}
Analysis of Output Results

The data generated by the simulations are analyzed using statistical tools to estimate the performance metrics of interest (e.g., means, variances, percentiles, confidence intervals) and to compare different alternatives or scenarios.
{% endstep %}

{% step %}
Documentation, Presentation of Results and Decision-Making/Implementation

Finally, the entire study is documented, including the model, assumptions, input data, virtual processes, experiments performed, and results obtained. The findings are presented to decision-makers, and if the study warrants it, the recommendations are implemented.
{% endstep %}
{% endstepper %}

{% hint style="danger" %}
It is essential to understand that verification and validation are not activities performed once and for all at the end of model development. They are continuous and iterative processes that must be carried out throughout the entire simulation study lifecycle.\


_**A model that has not been adequately verified and validated lacks credibility, and decisions based on it can be erroneous and costly**_. The involvement of the client or real-system expert is vital throughout the entire process, especially in problem definition, conceptual formulation, and validation. -crc-
{% endhint %}

***

## Applications in industrial engineering, logistics and production

Simulation is an extraordinarily versatile tool that has found a wide range of applications in virtually all areas of industrial engineering, logistics, and production.

Its ability to model the complexity, dynamics, and stochasticity of systems makes it an invaluable tool for analysis, design, and continuous improvement.

{% tabs %}
{% tab title="Manufacturing and Production Systems" %}
* Plant Layout and Design: Evaluate different plant configurations, machinery placement, workstations, and storage areas to optimize material flows, minimize travel distances, reduce bottlenecks, and improve overall efficiency.\

* Production and Assembly Line Analysis: Model production lines to analyze their capacity, identify bottlenecks (a core concept in the Theory of Constraints (TOC 1), determine the optimal size of intermediate buffers, and evaluate the impact of variability on process times and machine failure rates. General Motors, for example, used simulation to significantly increase the throughput of its plants.\

* Production Scheduling and Sequencing: Test different priority rules and sequencing algorithms to minimize cycle times, reduce work in process (WIP), and improve delivery date adherence.1 Swift & Company applied simulation for shift-level scheduling and promise capacity management.\

* Inventory Control (WIP and Raw Materials): Evaluate inventory control policies on the production floor, such as Kanban or CONWIP systems, and determine optimal inventory levels for raw materials and components.1 Samsung Electronics used simulation to reduce cycle times and inventories.\

* Capacity Planning: Determine the requirements for machinery, personnel, and other resources to meet projected demand, and evaluate the impact of investments in new capacity.\

* Material Handling Systems: Design and evaluate the efficiency of internal transportation systems such as automated guided vehicles (AGVs), conveyors, cranes, and robots, considering their speeds, capacities, and control logic.\

* Reliability and Maintenance Modeling: Analyze the impact of equipment failures and maintenance policies (preventive, predictive, corrective) on line availability and total production.\

* Lean/Just-in-Time (JIT) Systems Implementation: Simulate the transition to lean production systems to evaluate their benefits and challenges before full-scale implementation.
{% endtab %}

{% tab title="Logistics and Supply Chains" %}
* Distribution Network Design: Optimize the location and number of warehouses and distribution centers, and define product flow routes to minimize total costs and improve service levels.\

* Warehouse Management: Model a warehouse's internal operations (receiving, storage, picking, packing, shipping) to improve space utilization, optimize operator and equipment routes, and reduce order processing times.\

* Transportation Route Optimization: Evaluate different routing strategies for vehicle fleets, considering factors such as transportation costs, delivery time windows, vehicle capacities, and travel time variability. Yellow Freight System improved its service and performance by interactively optimizing its transportation operations.\

* Supply Chain Inventory Policies: Analyze the impact of different inventory policies (centralized vs. decentralized, security levels) on multiple links in the supply chain, considering demand variability and supplier lead times. IBM applied simulation to optimize its multi-echelon inventory system for service logistics, and Philips Electronics used it to synchronize its chain and mitigate the bullwhip effect.\

* Bullwhip Effect Analysis: Simulate how variations in end-consumer demand amplify up the supply chain, and test strategies to mitigate it. Supply Chain Collaboration and Synchronization: Evaluate the benefits of sharing information and coordinating decisions among different actors in the supply chain.
{% endtab %}

{% tab title="Service Systems" %}
* Queuing Systems Analysis: Modeling and analyzing the performance of systems where customers (or jobs) wait for service, such as in banks, call centers, hospitals, airports, restaurants, and government offices. The objective is often to balance service costs with service quality (wait times).\

  * AT\&T developed a simulation-based system to help its clients design call centers.\

* Staffing Optimization: Determining the optimal number of servers (tellers, agents, doctors, nurses) at different times of the day or week to meet desired service levels at a reasonable cost.\

  * Merrill Lynch used simulation for its pricing and service analysis.\

* Service Process Design and Redesign: Evaluating the impact of changes in process flows, task assignments, or the introduction of new technology on efficiency and customer experience.
{% endtab %}

{% tab title="Project management" %}
* Project Duration and Cost Estimation: Model the duration and cost of project activities as random variables (using distributions such as Triangular or Beta in PERT) to obtain a distribution of the total project duration and cost.\

* Critical Path and Sensitivity Analysis: Identify the most critical activities and analyze how variability in their durations affects the probability of meeting project deadlines.\

* Project Risk Management: Evaluate the impact of potential risks (supplier delays, technical issues, lack of resources) and the effectiveness of contingency plans.
{% endtab %}
{% endtabs %}

The versatility of simulation is such that its application extends to almost any system where dynamics, interaction between components, and uncertainty play an important role.

{% hint style="success" %}
the competitiveness of organizations. The key for the industrial engineer is to learn to identify the characteristics of a problem that make it a candidate for simulation analysis and then translate that problem into a valid and useful model.
{% endhint %}

***

Literature

1. Banks, J., Carson, J. S., II, Nelson, B. L., & Nicol, D. M. (2010). Discrete-Event System Simulation (5th ed.). Prentice Hall.\

2. Law, A. M. (2015). Simulation Modeling and Analysis (5th ed.). McGraw-Hill Education.\

3. Leemis, L. M., & Park, S. K. (2006). Discrete-Event Simulation: A First Course. Prentice Hall.\

4. Hillier, F. S., & Lieberman, G. J. (2010). Introduction to Operations Research (9th ed.). McGraw-Hill. (Chapters on simulation)\

5. Cassandras, C. G., & Lafortune, S. (2008). Introduction to Discrete Event Systems (2nd ed.). Springer.\

6. Urquía Moraleda, A., & Martín Villalba, C. (2016). Simulation and modeling methods. UNED.
