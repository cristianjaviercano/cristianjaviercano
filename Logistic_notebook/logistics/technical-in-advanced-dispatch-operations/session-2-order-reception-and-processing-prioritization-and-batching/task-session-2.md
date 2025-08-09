---
hidden: true
---

# Task Session 2

## Task 1: Exception Handling Process Design

{% hint style="danger" %}
This task focuses on Competency 3: Order Ingestion and Validation.
{% endhint %}

**Scenario**

A fulfillment center has just received the following five orders in a data file from a new sales channel. Your WMS has run an initial validation check against the product master file and address database.

| Order ID | Customer Name | Address        | City       | Postal Code | SKU   | Qty | Payment Status |
| -------- | ------------- | -------------- | ---------- | ----------- | ----- | --- | -------------- |
| ORD-101  | A. Garcia     | 123 Main St    | Anytown    | 12345       | SKU-A | 2   | Authorized     |
| ORD-102  | B. Jimenez    | 456 Oak Avenue | Otherville | 9876        | SKU-B | 1   | Authorized     |
| ORD-103  | C. Rojas      | 789 Pine       | Someplace  | 55555       | SKU-X | 3   | Failed         |
| ORD-104  | D. Lopez      | PO Box 1122    | Big City   | 67890       | SKU-C | 1   | Authorized     |
| ORD-105  | E. Perez      | 987 Elm Str.   | Nextown    | 44332       | SKU-D | 5   | Authorized     |

Exportar a Hojas de cálculo

System Information:

* The postal code for "Otherville" should be 5 digits (e.g., 98760).
* SKU-X does not exist in the product master file.
* The system cannot verify "PO Box" addresses for the primary carrier.
* Address normalization rules can automatically correct "Str." to "Street".
* All other data points are considered valid.

**Assignment**

1. Identify and Classify: For each Order ID that has an error, identify the specific validation failure.
2. Propose a Handling Strategy: Based on the concepts of exception handling, describe the most efficient strategy for each failed order (e.g., automated correction, route to manual exception queue, automated customer communication, outright rejection).
3. Justify Your Strategy: Briefly explain the reasoning behind your choice for each, considering factors like cost, speed, and customer experience.
4. Design a Flowchart: Create a simple text-based or conceptual flowchart that outlines the process flow for an incoming order, from initial ingestion through validation and exception handling, leading to a "Ready for Picking" status.

***

#### Task 2: Order Prioritization and Batching Heuristic

{% hint style="danger" %}
This task focuses on Competency 4: Order Prioritization and Batching.
{% endhint %}

**Scenario**

The following six orders have been validated and are now in the "Ready for Picking" queue. The warehouse uses a simple grid layout for its pick locations. The picking process starts at location (0,0). A picking cart has a capacity constraint and can hold a maximum of 3 orders at a time.

Order Queue:

| Order ID | Shipping Method | Items (SKU @ Location)             |
| -------- | --------------- | ---------------------------------- |
| ORD-201  | Standard        | 1x SKU-A @ (1,5)                   |
| ORD-202  | Express         | 1x SKU-B @ (4,2); 1x SKU-C @ (4,4) |
| ORD-203  | Standard        | 1x SKU-D @ (7,1)                   |
| ORD-204  | Standard        | 1x SKU-A @ (1,5); 1x SKU-E @ (2,5) |
| ORD-205  | Express         | 1x SKU-F @ (8,8)                   |
| ORD-206  | Standard        | 1x SKU-C @ (4,4)                   |

Exportar a Hojas de cálculo

**Assignment**

1. Prioritize the Queue: Re-sequence the list of six orders based on their priority. State the clear rule you are applying.
2. Form Picking Batches: Using your prioritized list, apply a simple batching heuristic (e.g., a "seed-based" approach where you select the highest priority order and group it with the 1 or 2 other orders that are geographically closest) to create optimal picking batches. Each batch must respect the 3-order cart capacity constraint.
3. Justify the Batches: For each batch you create, explain your logic. Why were those specific orders grouped together?
4. Estimate Efficiency Gains: Calculate the total travel distance (using Manhattan distance: $$∣x2​−x1​∣+∣y2​−y1​∣$$) for picking all six orders individually versus picking them in the batches you created. This demonstrates the quantitative benefit of your batching strategy.
