---
description: >-
  Modeling and Analysis of a Discrete Production System with Multiple Products
  and Shared Resources.
icon: pie
---

# DC Bakery

This time, we will address discrete event simulation by building a model for a bakery.

**Title:** Modeling and Analysis of a Discrete Production System with Multiple Products and Shared Resources.

**Author:** Cristian J. Cano, M.Sc. | Darwin Ramos, M.Sc.

**Company Under Study:** DC Cakes

**Date:** June 2025

**Case:** The company **DC Cakes** specializes in the production of two pastry items: **Alfajores** and **Cakes**. To optimize its efficiency, the company uses pre-processed inputs (cookies and pre-made doughs). The production system is characterized by a complex flow where both products compete for shared resources, such as ovens and the packaging station, and follow differentiated routes at certain stages of the process. The system operates under a maximum production capacity constraint (WIP - Work In Process). The objective of this study is to develop a discrete event simulation model to replicate the current production system, identify bottlenecks, and evaluate the potential impact of capacity investments.

***

**Problem Statement:**

You have been hired as process engineers by **DC Cakes**. Management has observed that daily production is not meeting expected targets and suspects that there are bottlenecks in the system, but is unclear about where they are or what the most effective investment would be to resolve them.

The challenge is to build a discrete event simulation model in **AnyLogic** that faithfully replicates the DC Cakes production system. The ultimate objective is to identify the main bottleneck in the system and propose a quantifiable improvement, evaluating its impact on total production.

<details>

<summary><strong>Alfajor Process</strong></summary>

The flow for alfajor production is as follows:

1. **Supply and Capacity Control**: The process begins with a batch of X **cookies**. These always enter the main production system.
2. **Quality Control (Cookie)**: Once inside the system, the cookie passes through a quality control station dedicated to this input, with its own processing time.
3. **Shaping**: The cookie is shaped according to the alfajor specifications.
4. **First Baking**: The product enters the queue at the **Baking** station. This is the first station where it competes for a shared resource (the oven) with the cakes.
5. **Manjar Application**: After baking, it moves to the station where the manjar is added. This is another station with shared resources. At this point, the product could be reclassified internally (e.g., from "cookie" to "cookie with caramel").
6. **Second Baking**: After applying caramel, the product **returns to the oven queue** for a second baking process, likely to seal the product.
7. **Packaging**: Once the second baking is complete, the finished alfajor moves to the packaging line, which is the last shared resource in the system. The time for this process follows an exponential distribution.
8. **System Output**: Once packaged, the final product leaves the system and is counted as finished production ('Sink').

</details>

<details>

<summary><strong>Cake Process</strong></summary>

The cake production flow follows a different route in the initial stages:

1. **Supply and Capacity Control**: The process begins with a batch of Y **units of dough**.
2. **Quality Control (Dough)**: The dough enters its own quality control line, which is separate from the cookie line and has its own processing time.
3. **Kneading**: It must be processed at the **Kneading** station. This is a station dedicated solely to this product.
4. **Shaping**: After kneading, the dough is shaped.
5. **First Baking**: The shaped cake enters the shared queue at the **Baking** station.
6. **Flavoring**: It moves to the shared flavoring station.
7. **Second Baking**: Like the alfajor, the manjar cake **returns to the oven queue** for its second baking.
8. **Packaging**: The finished product heads to the final packaging station.
9. **System Exit**: Once packaged, the cake exits the system ('Sink').

</details>

**Production System Details**

* **Products and Entities:** A `Product` agent type must be created with a `product_type` parameter (e.g., 1 for Alfajor, 2 for Queque). Products change state and type as they progress (e.g., a cookie becomes a "cookie with caramel"). **Process Flow and Stations:**

1. **Arrival of Inputs**: At the beginning of each day (simulation starts at t=0), **150 units** of cookies (Mp1) and 9**0 units** of dough arrive. (Mp2)
2. **Quality Control**: Separate processes for cookies and dough. Triangular Cookie Quality (2, 5, 9) Triangular Dough Quality (3, 6, 9)
3. **Kneading**: Exclusively for doughs. Triangular kneading time (22, 30, 32)
4. **Shaping**: To give the final shape to the products. Shaping for triangular Alfajor (9, 10, 11) Shaping for triangular dough (12, 13, 14)
5. **Baking**: A resource shared by both products. Baking for triangular Alfajor (2, 15, 28) Baking for triangular Cake (13, 16, 19)
6. **Manjar Application**: A station shared by both products. Triangular alfajor (7, 9, 13) Triangular cake (8, 10, 14)
7. **Conditional Logic**: After applying caramel, the product returns to the oven queue for a second baking.
8. **Packaging**: Shared final station. Exponential (1.0/5) for each product

**Process Time Distributions:** **Quality Control**: Triangular Distribution\*\* **Baking**: Triangular Distribution\*\* **Applying Caramel**: Triangular Distribution\*\* **Packaging**: The process time follows an Exponential distribution with an average of 5 minutes per product.

**System Constraints:**

The entire system has a maximum capacity of 100 products (WIP). New raw materials must wait in a supply queue if the system is full. This must be modeled using the `RestrictedAreaStart` and `RestrictedAreaEnd` blocks.

* The simulation must run for a total of **7200 minutes** (equivalent to 5 days of production).

***

**Phases for Solving the Challenge**

1. **Phase ZERO**: Process Visualization

Build the theoretical model of the process, using flowcharts or any graphical tool that allows you to visualize the process.

2. **Phase 1: Construction of the Base Model**

Create the `Product` agent with its respective parameters.

Model the process flow using the PML library blocks: `Source`, `Queue`, `Service`, `SelectOutput` for logical decisions, and `RestrictedAreaStart/End` for the WIP restriction. Configure each service block (`Service`) with the specified resources and time allocations.

3. **Phase 2: Verification and Validation**

Run the model and verify that the entity flow is correct (cakes are kneaded, alfajores are not, etc.). Ensure that the 100-unit restriction in the system is working correctly. Validate that the total number of output products plus those left in process equals the number of inputs.

4. **Phase 3: Bottleneck Analysis and Identification**

Run the simulation for 7,200 minutes. Analyze the results: Identify the workstation with the **longest queue** and the **longest average wait time**. Review the **utilization** of all resources (dough mixer, oven, deli station, packaging machine). The resource with the utilization closest to 100% is likely the bottleneck.

5. **Phase 4: Improvement Proposal and Evaluation** Based on your analysis, formulate a hypothesis. For example: "The oven is the main bottleneck in the system."

**Improvement Proposal**: Management is considering purchasing a second oven. Modify your model to reflect this improvement, increasing the oven's Resource Pool capacity to **2**. Run the new scenario and compare the results with the baseline model.

6. **Phase 5: Presentation of Results (Technical Report)**

* Prepare a report of no more than 2 pages containing:
* A brief description of the model built.
* A clear identification of the bottleneck, supported by data (queue length, utilization).
* A comparative table of KPIs (Total Production of Alfajores and Queques, Average Cycle Time) between the **base scenario** and the

**scenario with the improvement**.

* A final recommendation for the management of **Pasteles CRC**, indicating whether the investment in a second oven is justifiable or not based on the simulation results.
