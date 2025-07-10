---
icon: boot-heeled
---

# DC Footwear Manufacturing

**1. Objectives**

* [ ] Model a two-stage production process with stochastic arrivals and service times.
* [ ] Implement probabilistic routing logic for different product types.
* [ ] Set up and run a simulation experiment for a finite number of products.
* [ ] Measure and analyze key performance indicators: average time in system and average waiting time.

**2. System Analysis**

Before modeling, it is crucial to define the system components based on the "Shoe Factory" case description.

* **Entities**: Pairs of shoes.
* **Process**: A two-stage flow: Cutting (Station 1) and Assembly (Station 2).
* **Arrivals**: The pairs of shoes arrive at Station 1 with an interarrival time that follows a **Normal** distribution with a mean of 1.5 minutes (90 seconds) and a standard deviation of 20 seconds.
* **Resources**:
* Cutting Machine (Station 1): 1 unit.
* Assembly Machine (Station 2): 1 unit.
* **Flow Logic**:
* At Station 1 (Cutting), there are 3 types of cutting with different probabilities and operation times.
* **50%** are **Type 1** (fixed time).
* **30%** are **Type 2** (uniform time).
* **20%** are **Type 3** (normal time).
* **End of Simulation**:&#x20;

The model must stop after processing **100 pairs of shoes**, or one unit of responsible time.
