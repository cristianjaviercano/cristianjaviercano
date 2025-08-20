---
description: >-
  The objective of these models is not only to minimize costs (as in the classic
  EOQ), but also to achieve a desired Service Level. The service level is the
  probability of not having a shortage.
---

# EOQ Variants

### Incoming Processes in a Warehouse or Inventory System 

Facilities, such as warehouses and storage facilities, are the "where" of the supply chain, the points from or to which inventory is transported, and where it can be transformed or stored. In a warehousing system, there are two main functions: possession (storage) and materials handling. Materials handling encompasses activities such as loading and unloading, movement of products within the warehouse, and order picking.

\
A logistics information system, which includes subsystems such as the warehouse management system (WMS), is fundamental to these operations. The WMS monitors product levels at each stock location in the warehouse and can suggest reorder quantities and times, as well as transmit requests to purchasing departments or suppliers.

***

### EOQ with Shortages and/or Safety Stock (Probabilistic Model)

\
the classic EOQ models assume certain demand and lead times. In reality, uncertainty exists, leading to the need to maintain safety stock to cover demand or supply variability during the lead time. Average inventory is the sum of cycle inventory (Q/2) and safety stock (SS).

\
The appropriate level of safety stock is determined by demand uncertainty, replenishment lead times, lead time variability, and desired product availability. If any of these factors increase, safety stock will also increase.

#### Calculation.

Safety stock $$S_s$$ is commonly calculated as $$S_s = z * σL$$, where z is a safety factor (related to the desired service level, usually obtained from a normal distribution) and $$σL$$ is the standard deviation of demand during the lead time.

***

### EOQ with Variable Demand

{% hint style="warning" %}
This scenario occurs when we know our supplier's lead time, but our customers' demand fluctuates.
{% endhint %}

context:  "PharmaDistribución" distributes a popular painkiller. They want to ensure a **95%** service level to avoid failing pharmacies.

#### Data:

1. Average daily demand $$d$$: 100 boxes.
2. Standard deviation of daily demand $$σ_d$$: 20 boxes (this measures variability).
3. Supplier lead time $$Lt$$: 4 days (constant).
4. Ordering cost (S): $75 per order.
5. Annual demand (D): $$100\  \text{boxes/day} * 365 \text{days} = 36,500 \text{boxes}.$$
6. Maintenance cost (h): $2 per box per year.

_<mark style="color:$success;">**Desired Service Level: 95% (This corresponds to a Z value of 1.65 in the standard normal distribution table).**</mark>_

**Objective: Determine the order quantity (EOQ) and the time to order (ROP).**

#### **Step 1:**&#x20;

Calculate the Order Quantity (Q\*) For the "how much to order," we continue to use the classic EOQ formula, as it represents the economic lot size based on average costs.&#x20;

$$
Q* = \sqrt{\left(\frac{2DS}{h}\right)} = \sqrt{\frac{2 * 36,500 * 75 }{2}} = \sqrt{2,737,500} = 1,655\ \text{boxes}
$$

#### Step 2:&#x20;

{% hint style="danger" %}
One might mistakenly think, "If the standard deviation for one day is 20 boxes, then for 4 days the deviation will be 20 \* 4 = 80 boxes." This is incorrect.

The reason is a fundamental statistical principle: standard deviations cannot be added directly over time, but variances can.

* The standard deviation (σ) measures the dispersion of the data.
* The variance (σ²) is simply the squared standard deviation.
{% endhint %}

_Calculate the Safety Stock_ $$s_s$$ We need to protect ourselves from demand variability during the lead time.

First, we calculate the **standard deviation** of demand during lead time&#x20;

$$
σ_dLt = σ_d * \sqrt{L} = 20 * \sqrt{4} = 20 * 2 = 40 \text{boxes}
$$

Now, we calculate the safety stock:&#x20;

$$
S_s = Z * σ_dLT = 1.65 * 40 = 66\  \text{boxes}
$$

### Step 3:&#x20;

Calculate the Reorder Point (ROP/L)

Average demand during lead time&#x20;

$$
d * L = 100\ \text{boxes/day} * 4\ \text{days} = 400\ \text{boxes}.
$$

$$
ROL = (\text{Average demand during lead time}) + S_s = 400 + 66 = 466\ \text{boxes}
$$

**Explanation and Final Policy:**&#x20;

The inventory policy for "PharmaDistribución" should be Placing an order for 1,655 boxes every time the inventory level drops to 466 boxes.

Of those 466 boxes, 400 are intended to cover expected demand while the order arrives, and the additional 66 boxes are the safety cushion that gives them 95% confidence that stock will not run out even if demand fluctuates more than normal.

***

### EOQ with Variable Lead Time&#x20;

{% hint style="info" %}
This scenario is common when working with international suppliers or complex supply chains, where lead times are uncertain.
{% endhint %}

A bicycle assembly company imports frames from abroad. Demand is fairly stable, but shipping times can vary greatly.

1. Daily demand (d): 10 frames (constant).
2. Average lead time (L): 20 days.
3. Standard deviation of lead time $$σ_L$$: 3 days.
4. Desired Service Level: 98% (Corresponds to a Z value of 2.05).
5. Other data (D, S, H) are the same for calculating EOQ.

#### Determine safety stock and reorder point.

#### Step 1:&#x20;

Calculate Safety Stock (SS) The formula changes slightly, as the uncertainty is in time, not demand.&#x20;

$$
SS = Z * d * σ_L = 2.05 * 10\ \text{marks/day} * 3\ \text{days} = 61.5 ≈ 62\  \text{marks}
$$

### Step 2&#x20;

Calculate the Reorder Point (ROP)

Average demand during the lead time&#x20;

$$
d * L = 10 * 20 = 200 marks.
$$

ROP = (Average demand during lead time) + SS = 200 + 62 = 262 marks

#### Explanation and Final Policy.

{% hint style="success" %}
The company must place a new order for marks every time its inventory reaches 262 units. This level ensures that, even if the supplier takes 3 standard deviations longer than normal, the company will have enough marks to continue operating with a 98% probability.
{% endhint %}
