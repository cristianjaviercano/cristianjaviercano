# The Classic Economic Order Quantity (EOQ)

EOQ model is a cornerstone of inventory management. Its main objective is to determine the optimal order quantity for an item, minimizing the total cost associated with inventory. The model seeks the perfect balance between two conflicting types of costs:&#x20;

1. Setup (or ordering) costs: These are the fixed costs incurred each time an order is placed, regardless of the order size.&#x20;
2. Carrying (or storage) costs: These are the costs of maintaining a unit in inventory for a given period of time.&#x20;

These include capital costs, storage, insurance, etc. If you order very large batches, the cost of holding inventory increases, but you order less frequently, lowering the setup cost. If you order small batches, you maintain little inventory, but the setup cost increases due to the frequency of orders.&#x20;

The EOQ finds the exact point where the sum of both costs is minimum. Assumptions of the Classical Model For the classic formula to work, the model is based on several assumptions:

1. Demand is deterministic and occurs at a constant rate.
2. Inventory replenishment is instantaneous (the entire batch arrives at a single moment).
3. Product shortages or shortages are not allowed.&#x20;

The formula for calculating the optimal batch is:&#x20;

$$
Q = √(2DS / H)
$$

Where:&#x20;

Q\* = Optimal order quantity.&#x20;

D = Demand rate (units per year).&#x20;

S = Setup or ordering cost (per order).&#x20;

H = Inventory carrying cost (per unit per year).

Common Variants of the EOQ Model The classic model is an excellent starting point, but operational reality is often more complex. Therefore, there are several variants that adapt to different scenarios:

1. **EOQ with Quantity Discounts** This is one of the most widely used models. It considers situations where the supplier offers a lower unit price if the order size exceeds a certain quantity. Here, the purchase cost of the product becomes a relevant variable. To find the optimal quantity, the total cost (including the product acquisition cost) must be calculated for each price level and compared to determine whether taking advantage of the discount is economically advantageous.
2. **EPQ (Economic Production Quantity)** This model is ideal for companies that produce their own components rather than purchasing them from a supplier. The key difference is that inventory is not replenished instantly, but rather accumulates as it is produced, at the same time as it is consumed. This changes the way carrying costs are calculated.
3. **EOQ with Planned Shortages (Backorders)** Sometimes, allowing for controlled shortages can be a cost-cutting strategy, especially if inventory holding costs are very high and customers are willing to wait. This model introduces a new cost: the cost per shortage, and calculates an optimal order quantity that minimizes the sum of setup, maintenance, and shortage costs.
4. **Dynamic EOQ Models** These models are used when demand, although known, varies over time (is not constant). They are applied over finite planning horizons and are reviewed periodically. Unlike traditional EOQ, a single order quantity is not sought, but rather an ordering plan over several periods to minimize total costs.
5. **Probabilistic EOQ Models** When demand or delivery times are uncertain (probabilistic), deterministic models are not sufficient. These more advanced models introduce the concept of safety stock to protect against variability and minimize the likelihood of running out of stock.
