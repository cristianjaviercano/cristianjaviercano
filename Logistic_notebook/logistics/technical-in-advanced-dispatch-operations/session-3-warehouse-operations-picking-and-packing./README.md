---
description: >-
  This session transitions from order preparation to physical execution within
  the warehouse. It explores the foundational principles of warehouse layout and
  inventory placement, followed by an analysis
---

# Session 3: Warehouse Operations - Picking and Packing.

## Competency 5: Inventory and Warehouse Layout

A warehouse's physical configuration and the logic governing inventory placement are fundamental drivers of its efficiency. This competency examines the strategic design of warehouse spaces and systems for locating inventory to support fluid operational flow.

### **The Modern Warehouse: Zones & Material Flow**

A warehouse is not a monolithic storage space but a system of interconnected zones, each with a specific function. The layout dictates the flow of goods and people, and an optimized design minimizes travel and congestion.

#### Primary Zones:

* Receiving: Where inbound goods are unloaded, inspected for quality and quantity, and identified.
* Storage: The area for holding inventory. This is often subdivided into Bulk Storage (for palletized reserve inventory) and a Forward-Pick Area (for active, ready-to-pick inventory, often in smaller units like cases or eaches).
* Picking: The zone where order fulfillment occurs. This is where the majority of labor activity is concentrated.
* Packing & Consolidation: Where items for an order are grouped, checked for accuracy, packed into shipping cartons, and labeled.
* Staging & Shipping: Where completed orders are accumulated (staged) by destination or carrier and loaded onto outbound vehicles.
* Material Flow: The path goods follow through these zones should be logical and unidirectional to the greatest extent possible, commonly in a "U-shape" or "I-shape" (straight-through) flow path to prevent backtracking and bottlenecks.

<figure><img src="../../../.gitbook/assets/BA6E0094-238A-430A-848B-F7E195FD5D22.png" alt="" width="375"><figcaption></figcaption></figure>

{% hint style="danger" %}
The design of a warehouse layout is a classic problem in facility planning. The objective is to arrange departments or zones to minimize the total material handling cost, which is often a function of the distance traveled and the frequency of trips between zones (Tompkins et al., 2010). Poor flow can dramatically reduce the overall throughput capacity of the entire system.
{% endhint %}

***

### **Inventory Location Systems**

The method used to assign inventory to storage locations has significant implications for space utilization and picking efficiency.

* Fixed (or Dedicated) Location Storage: Each Stock Keeping Unit (SKU) is assigned a permanent, fixed storage location.
* Pros: Simple to manage, pickers quickly learn locations, and no sophisticated system is needed to locate stock.
* Cons: Highly inefficient use of space. The location must be sized to hold the maximum anticipated inventory of its SKU, leading to significant empty space (low cube utilization) when inventory levels are average or low.
* Random (or Chaotic) Location Storage: Incoming SKUs are stored in any available location of the appropriate size.
* Pros: Extremely high space utilization (often >90%) as it eliminates the reserved empty space of fixed systems.
* Cons: It is entirely dependent on a robust Warehouse Management System (WMS) to track the location of every item. Losing the WMS means losing the inventory.

{% hint style="success" %}
Most modern operations use a hybrid approach. Fast-moving items (A-items) may be given dedicated locations in a forward-pick area for efficiency, while slower-moving items (B and C-items) are stored randomly in a bulk area to maximize space utilization.\

{% endhint %}

<img src="../../../.gitbook/assets/file.excalidraw (2).svg" alt="" class="gitbook-drawing">

***

### **Theoretical Model: ABC Analysis**

ABC analysis is a method of inventory categorization that applies the Pareto principle to segment items based on their significance. The principle suggests that a small percentage of items typically account for a large percentage of overall value or activity.

**Classification:**

* A-Items: The most significant items, typically representing the top 70-80% of annual consumption value or pick frequency, but only constituting 10-20% of total SKUs.
* B-Items: Items of moderate significance, representing the next 15-25% of value/frequency from 30% of SKUs.
* C-Items: The least significant items, representing the final 5% of value/frequency but making up 50% or more of total SKUs.
* Mathematical Foundation: The analysis is performed by calculating the annual consumption value for each SKU (Annual Demand × Item Cost). The SKUs are then ranked in descending order by this value. The cumulative percentage of total SKUs and total value is calculated to determine the A, B, and C cutoff points.

{% hint style="danger" %}
_While classic ABC analysis uses consumption value,_ in a fulfillment context, it is often more powerful to classify items based on pick frequency or sales velocity. This directly aligns the classification with the labor-intensive picking process, ensuring that the most frequently touched items receive preferential treatment in slotting.
{% endhint %}

<img src="../../../.gitbook/assets/file.excalidraw (1) (1) (1).svg" alt="" class="gitbook-drawing">

***

### **Slotting Strategy: The Application of ABC**

Slotting is the strategic placement of inventory within the picking area to minimize handling costs, primarily by reducing picker travel distance. It is the direct physical application of the ABC classification.

* _**Golden Zone Slotting:**_ A-items (the most frequently picked) should be slotted in the most accessible and ergonomically favorable locations—typically between a picker's waist and shoulders (the "golden zone")—and closest to the start of the pick path or nearest to the packing area.
* _**C-Item Placement:**_ C-items (the slowest movers) can be placed in less convenient locations, such as on the bottom or top shelves, or in aisles further away from the shipping dock.

**Other Slotting Considerations:**

* _**Product Correlation**_: Items that are frequently ordered together should be slotted near each other to enable more efficient multi-item picks.
* _**Physical Characteristics:**_ Heavy or bulky items should be placed on lower shelves to reduce picking effort and risk of injury. Small items should be stored in high-density bins to conserve space.

***

## Competency 6: Picking Strategies and Optimization
