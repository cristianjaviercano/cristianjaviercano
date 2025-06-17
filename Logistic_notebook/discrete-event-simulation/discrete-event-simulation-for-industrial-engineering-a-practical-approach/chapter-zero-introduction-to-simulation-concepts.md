---
description: >-
  For an industrial engineer, this introductory chapter lays the theoretical
  groundwork for understanding simulation. It will define fundamental concepts
  and set the stage for practicalism
---

# Chapter Zero: Introduction to Simulation Concepts

<img src="../../.gitbook/assets/file.excalidraw (1) (1) (1).svg" alt="Unrapido vistazo al mundo e la simulacion" class="gitbook-drawing">

Welcome to the fascinating world of **discrete-event simulation**—a discipline that has become an indispensable tool in the modern industrial engineer's arsenal. In an era characterized by the increasing complexity of production, logistics, and service systems, the ability to model, analyze, and optimize these systems is more crucial than ever.

Operations Research (OR), in general, has proven to be a fundamental technological driver for the success of countless organizations worldwide. Within this field, **simulation** emerges as one of its most versatile and powerful techniques. Leading companies, such as Federal Express, have integrated OR into the core of their strategic decision-making processes, optimizing everything from equipment investment to the structure of their complex logistical routes.

Discrete-event simulation is an inherently **multidisciplinary activity**, with deep roots in industrial engineering, operations research, computer science, and statistics. Throughout these pages, we will explore how simulation allows us to transcend the limitations of purely analytical methods. It offers a **virtual laboratory** where we can experiment with innovative ideas, evaluate the impact of changes, and make informed decisions without incurring the costs or risks associated with real-world experimentation.

> Simulation, in its essence, is the **imitation of the operation of a real-world process or system over time** (Law, 2015). It involves creating a model that captures the key characteristics and behaviors of a system and then running this model to observe its performance under various conditions. This allows for experimentation and analysis without disrupting the actual system, which can be costly, time-consuming, or even dangerous. - Crc

### Course Objectives

This course is designed to equip you with both the theoretical understanding and practical skills necessary to excel in the field of simulation for industrial engineering. By the end of this course, you will be able to:

* **Comprehend the fundamental principles of simulation:** You'll build a strong conceptual foundation for the discipline.
* **Learn to model systems:** You'll develop the ability to abstract real-world complexities into manageable models that capture the essence of the systems under study.
* **Master Monte Carlo simulation techniques using Excel:** You'll explore how an accessible tool like Excel can be leveraged for risk and scenario analysis.
* **Develop discrete-event simulation models using SimPy (Python):** You'll be introduced to programming simulations, offering flexibility and power for customized models.
* **Acquire skills in using specialized software like AnyLogic:** You'll explore the capabilities of a cutting-edge simulation tool for modeling complex systems in production and logistics.
* **Analyze and interpret simulation results for informed decision-making:** We'll emphasize that simulation doesn't end with model execution; it culminates in extracting actionable knowledge.

The proposed learning methodology combines rigorous theoretical exposure with a strong practical orientation. Each chapter will include clear definitions, step-by-step solved examples, exercises designed to reinforce concepts, and, most importantly, direct applications to typical industrial engineering problems, especially in the areas of logistics and production. The aim is for you to not only learn _about_ simulation but to learn _to do_ simulation.

> Modern industrial and logistical systems are **intrinsically complex, dynamic, and stochastic**.

{% hint style="success" %}
la simulaciónSimulation is not merely another technique; it is a **way of thinking**, a **methodology for virtual experimentation**, and a **pillar for continuous improvement in industrial engineering**.
{% endhint %}

***

### When Is Simulation a Useful Tool?

Simulation becomes a powerful and often indispensable tool when dealing with systems characterized by **complexity, dynamism, and stochasticity**. Specifically, its utility is high in scenarios where:

* **Analytical Solutions are Intractable:** Many real-world industrial and logistical systems involve numerous interacting components, probabilistic events (e.g., random arrivals, variable service times), and intricate logical rules. In such cases, obtaining closed-form analytical solutions (e.g., using queuing theory formulas) is often impossible or yields overly simplistic results (Law, 2015).
* **Experimentation in the Real System is Costly or Risky:** Modifying or experimenting directly with an existing system can lead to significant disruptions, high costs, or even safety hazards. Simulation provides a **risk-free virtual laboratory** to test hypotheses, evaluate design changes, and assess operational policies without impacting the actual system (Banks et al., 2010).
* **Time-Dependent Behavior is Crucial:** Systems where the sequence and timing of events are critical to performance (e.g., waiting times, resource utilization over a shift) benefit greatly from simulation, which can capture these dynamic interactions over time.
* **Understanding System Dynamics is Required:** Simulation helps visualize and comprehend the intricate relationships between system components, identifying bottlenecks, points of congestion, and the ripple effects of changes.
* **Evaluating "What-If" Scenarios:** It enables engineers to quickly assess the potential impact of various operational changes, resource additions, or demand fluctuations on key performance indicators before committing resources in the real world.
* **Optimizing Resource Allocation:** Simulation can be used to determine optimal staffing levels, machine configurations, buffer sizes, and inventory policies to maximize throughput or minimize costs.

### When NOT to Use Specialized Simulation Software

While specialized simulation software offers significant advantages in modeling and analysis, there are situations where its application may not be the most efficient or appropriate choice. As Naylor et al. (1996) and Shannon (1998) acknowledge, the decision to employ such tools must weigh their benefits against potential drawbacks. Consider alternative approaches when:

* **Complexity and Time Investment Outweigh Benefits:** If the problem can be solved with simpler analytical models, spreadsheets, or even heuristic approaches, the significant time and effort required for building, verifying, and validating a detailed simulation model may not be justified. For instance, a basic queuing problem with known arrival and service distributions might be sufficiently analyzed using standard queuing theory formulas.
* **High Cost of Software and Training:** Specialized simulation software often entails substantial licensing fees and requires considerable training for users. For one-off, small-scale problems or organizations with limited budgets, the financial investment might not yield a proportional return. In these cases, simpler tools or even custom scripting with general-purpose programming languages (like Python with libraries such as SimPy) might be more cost-effective.
* **Problem Relevance and Necessity are Low:** If the insights gained from simulation are trivial, obvious, or do not significantly impact decision-making, then its use is excessive. The problem's inherent complexity and the value of the potential solution should warrant the simulation effort. For example, if a bottleneck is clearly visible and addressable by simple observation, a full simulation study might be overkill.
* **Data Precision and Availability are Insufficient:** The "garbage in, garbage out" principle applies critically to simulation. If the input data (e.g., arrival rates, service times, breakdown probabilities) are unreliable, incomplete, or highly inaccurate, the simulation results will be misleading and potentially detrimental to decision-making. In such scenarios, efforts should first focus on robust data collection and validation. Without reliable data, even the most sophisticated simulation model will produce questionable outputs.

Carefully evaluating these conditions allows researchers and practitioners to determine when to leverage the powerful capabilities of specialized simulation software and when to opt for alternative, more suitable analytical or empirical approaches.

{% hint style="info" %}
Another crucial scenario where simulation should **not** be used is when the **problem can be solved with common sense**.

* The principle here is to **match the complexity of the solution tool to the complexity of the problem itself**.
{% endhint %}

***

### Characterization of a Simulation Model

<img src="../../.gitbook/assets/file.excalidraw (6).svg" alt="" class="gitbook-drawing">

{% hint style="info" %}
A simulation model, at its core, is a **representation of a real-world system** that captures its essential features and behaviors. The theoretical framework for characterizing these models often distinguishes between several key attributes (Law, 2015; Banks et al., 2010).
{% endhint %}

#### 1. By Type of System Representation

* **Static vs. Dynamic:**
  * **Static Simulation Models:** These models represent a system at a particular point in time or depict a system that does not change over time. They are often used to estimate system performance measures for a given set of inputs. A classic example is **Monte Carlo simulation**, which uses random sampling to estimate properties that depend on random variables.
*   **Dynamic Simulation Models:** These models represent systems that evolve over time. They are designed to study time-dependent behavior and observe how system states change as events occur.

    * **Theoretical Representation:** A dynamic model involves state variables S(t) that change as a function of time, inputs U(t), and system logic L.


*   **Deterministic vs. Stochastic:**

    * **Deterministic Simulation Models:** These models do not contain any random variables. Given a set of inputs, the output will always be the same. They are useful for understanding system logic and identifying cause-and-effect relationships without the noise of variability.
    * **Stochastic Simulation Models:** These models incorporate one or more random variables, meaning that the output of the simulation will vary even if the inputs are identical across different runs. Most real-world industrial and logistical systems exhibit stochastic behavior (e.g., customer inter-arrival times, machine breakdown times), making stochastic simulation crucial for realistic analysis. The use of **probability distributions** (e.g., exponential for inter-arrival times, normal for processing times) is fundamental in these models.
    * **Continuous vs. Discrete-Event:**
      * **Continuous Simulation Models:** As discussed previously, these models track system states that change continuously over time, often described by differential equations. They are suitable for fluid flow, chemical reactions, or population dynamics.
      * **Discrete-Event Simulation (DES) Models:** These models change state only at specific, discrete points in time when an event occurs. They are ideal for systems with distinct entities and queues, such as manufacturing lines, call centers, or supply chains. The core mechanism is the **event calendar**, which manages and executes events in chronological order.



### By Level of Abstraction (Granularity)

The level of detail included in a simulation model is a critical characteristic.

* **High-Level (Aggregate) Models:** These models abstract away many details and focus on the overall behavior of a system. They are useful for strategic planning, initial feasibility studies, or when detailed data is unavailable.
* **Detailed (Disaggregate) Models:** These models include a high degree of fidelity, representing individual entities, resources, and specific operational rules. They are necessary for operational decision-making, fine-tuning processes, or troubleshooting specific bottlenecks. The choice of granularity depends on the study's objectives and the available data.

### By Purpose

While often overlapping, the primary purpose can also characterize a model:

* **Descriptive Models:** Aim to accurately represent an existing system to understand its behavior.
* **Predictive Models:** Used to forecast future system performance under various conditions.
* **Prescriptive (Optimization) Models:** Often used iteratively with optimization techniques to find the best operating policies or system configurations.

#### References

Banks, J., Carson, J. S., Nelson, B. L., & Nicol, D. M. (2010). _Discrete-Event System Simulation_ (5th ed.). Pearson Prentice Hall.

Law, A. M. (2015). _Simulation Modeling and Analysis_ (5th ed.). McGraw-Hill Education.

Naylor, T. H., Balintfy, J. L., Burdick, D. S., & Chu, K. (1996). _Computer Simulation Techniques_. John Wiley & Sons.

Shannon, R. E. (1998). _System Simulation: The Art and Science_. Prentice Hall.
