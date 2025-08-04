---
icon: sack-dollar
---

# Quantity Discount Model

### Quantity Discount Model in EOQ

The quantity discount model applied to EOQ (Economic Order Quantity) incorporates discounts on unit prices as order volume increases. This modifies the traditional EOQ calculation, which seeks to minimize total costs associated with inventory, including ordering and carrying costs.

#### Key Concepts

* **EOQ (Economic Order Quantity):** The optimal order quantity that minimizes total inventory costs.
* **Quantity Discount:** A reduction in the unit price of a product when purchasing in large volumes.
* **Total Cost:** Includes ordering costs, carrying costs, and the cost of purchased products.

#### EOQ Formula Adjusted with Discounts

To apply the discount model, the EOQ is first calculated for each quantity price level. The total costs for each scenario are then evaluated, and the lowest is selected.

```
Basic EOQ:
```

$$
EOQ = \sqrt{\frac{2DS}{H}}
$$

Where:

* ( D ) = Annual demand.
* ( S ) = Cost per order.
* ( H ) = Inventory holding cost per unit per year.
* **Adjusted Calculation:**

1. Calculate the EOQ for each possible discount price.
2. Evaluate whether the calculated EOQ falls within the range of quantities that qualify for the discount.
3. Calculate the total cost for the calculated EOQ and compare it to the costs for the subsequent discounted levels.

#### Example

Suppose you have the following information:

* Annual demand (D): 1,000 units
* Cost per order (S): $50
* Holding cost per unit (H): $2
* Price per unit without discount: $100
* Quantity discount:

* 100-199 units: $95 per unit
* 200+ units: $90 per unit

**Step 1:** Calculate the EOQ without discounts.

$$
EOQ = \sqrt{\frac{2 \times 1000 \times 50}{2}} = 100
$$

* **Step 2:** Evaluate each discount level.
* **100-199 units: ($95 per unit):**
* Check if the EOQ falls within this range. We calculate total costs for various quantities and identify the minimum.
* **200+ units: ($90 per unit):**

* Recalculate the applicable EOQ and estimate total costs.

Finally, select the order quantity that results in the lowest total cost, considering discounted prices.
