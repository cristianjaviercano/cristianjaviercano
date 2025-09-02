# Unit two: inventory desitions

{% hint style="info" %}
Inventory models are essential in logistics because they allow for efficient management of stock levels. By applying these models, total inventory costs can be minimized, supply and demand can be balanced, and customer service can be improved by reducing delivery times and avoiding stockouts. They also facilitate planning and strategic decision-making in the supply chain, optimizing the flow of goods and improving the company's competitiveness.
{% endhint %}

In general, the complexity of inventory models depends on whether demand is deterministic or probabilistic. Within both categories, demand may or may not vary over time. The demand pattern in an inventory model can take one of four types:

1. Deterministic and constant (static) over time.
2. Deterministic and variable (dynamic) over time.
3. Probabilistic and stationary over time.
4. Probabilistic and non-stationary over time.

This classification assumes the availability of reliable data to forecast future demand.

Based on the development of inventory models, the first category is the simplest analytically, and the fourth is the most complex. On the other hand, the first category is the least likely to occur in practice, and the fourth is the most prevalent.

### Definition of Inventory Models

Inventory models are statistical models and mathematical equations that, when combined, attempt or succeed in predicting demand behavior in production or service systems to ensure the availability of supplied goods, whether in the internal or external logistics chain, as the case may be.

There are types of models that cover inventories, from the simplest, such as the EOQ (economic order quantity) model, to the most complex, such as reorder point models and continuous inventory review models.

### Google Collab and Inventory Models: [#](broken-reference/)

To work with inventory models, what we must do is

1. Identify the libraries we will use. In this case, we will use:

* pandas
* numpy
* mathplotlib

### General Inventory Model [#](broken-reference/)

The main questions that the inventory model aims to address are: When to order? How much to order? This leads us to evaluate all aspects of the inventory. According to the authors, we find the following equation that encompasses the general inventory model:

$$
[\text{Total Inventory Cost} = \text{Purchase Cost} + \text{Preparation Cost} + \text{Holding Cost} + \text{Shortage Cost}]
$$

To represent the mathematical equation for the total inventory cost in the context of the EOQ model, we use the Formula:

$$
CT = \frac{D}{Q} \cdot S + \frac{Q}{2} \cdot H + D \cdot C
$$

Where:

* (CT) is the total cost.
* (D) is the annual demand.
* (Q) is the order quantity (lot size).
* (S) is the cost per order.
* (H) is the storage cost per unit.
* (C) is the purchasing cost per unit.

### We'll start with the EOQ model, also called static models.

* **The EOQ model or optimal order quantity** (classic EOQ)

This is one of the most common and widely used models, as it takes into account order and storage costs. This means that the more you buy, the greater the discount, but the higher the maintenance cost. The main objective of this model is to find the break-even point where costs are best managed according to demand requirements.

$$
EOQ = \sqrt{\frac{2*ordering cost*Demand}{carrying cost}}\
$$

$$
Q= \sqrt{\frac{2(K)(D)}{h}}\
$$

* **EOQ with Unknown Demand:**

Product demand is considered uncertain or unknown, and a service level approach is used to maintain the optimal inventory level. The service level is the probability that the inventory will be available when required. The main objective is to find the optimal amount of inventory that maximizes the service level while minimizing total inventory costs.

$$
EOQ = \sqrt{\frac{2KD}{h} + \left(\frac{Z \sigma_d \sqrt{L}}{h}\right)^2}
$$

Where:

* Z is the value of the normal distribution that corresponds to the desired service level.
* $$\sigma_d\$$ is the standard deviation of demand during the lead time.
* L is the lead time.

#### Words and nomenclatures[#](broken-reference/)

* D = Demand
* $$t_0$$ = Order cycle time
* ROQ = Reorder Quantity
* ROL = Reorder Level
* Q = Optimal Order Quantity
* $$t_0 = \frac{Q}{D}$$ units of time or supply cycles
* K = Order Preparation Cost
* h = Storage Cost
* L = Lead Time

{% hint style="info" %}
In general, this set of equations and initiatives allows us to define what is known as the **inventory policy** in a warehousing operation.
{% endhint %}

### Inventory Policy Definition

The inventory policy in a management system is defined by considering several key elements such as EOQ (Economic Order Quantity), ROL (Reorder Level), ROQ (Reorder Quantity), and random demand:

* **EOQ (Optimal Order Quantity):** This is the quantity that minimizes total inventory costs, including order preparation costs and storage costs. It is used to determine the optimal order size.
* **ROL (Reorder Level):** This is the point at which a new order must be generated to avoid inventory shortages, calculated based on the lead time and expected demand during that period.
* **ROQ (Reorder Quantity):** This is the quantity to be ordered each time the ROL is reached. This quantity can be adjusted based on demand variability and delivery time.
* **Random Demand:** This requires dynamic adjustments to ROL and ROQ, as it is important to account for variations in demand to avoid shortages or excess inventory.

{% hint style="info" %}
An effective inventory policy must be flexible and adapt to variations in demand, delivery times, and other factors that may affect inventory. Continuous evaluation and adjustment of the EOQ, ROL, and ROQ variables allows for maintaining an optimal balance between costs and availability.
{% endhint %}

### Lead time:

When an order has a positive stipulated lead time, it will be called "L" (lead time). In these cases, we must take into account the corresponding ROL and ROQ ratios, since these will vary the inventory behavior depending on its supply nature or lead time. The lead time versus inventory cycle time should be shown, since lead time should generally be less than cycle time; otherwise, other measures will have to be taken to control inventory.

Example:

Effective lead time is defined as follows:

$$
L_e = L - nt_0\
$$

### ROQ, Lead Time, and Safety Stock in Deterministic Inventory Models.[#](broken-reference/)

* The assumptions of the EoQ model are listed as follows:

1. **Constant Demand:** Demand for the product is assumed to be constant over time, implying no seasonal fluctuations or changes in demand.
2. **Constant Supply or Production Rate:** Inventory supply or production is assumed to be instantaneous and constant. That is, each time an order is placed, it arrives immediately and completely replenishes inventory.
3. **Known and Constant Lead Time:** The time it takes to receive an order after it is placed is known and does not vary.
4. **Constant Ordering Cost:** The cost associated with placing an order is fixed, regardless of the order size.
5. **Constant Carrying Cost:** The cost of holding a unit in inventory is constant and does not vary over time or with the amount of inventory.

However, there are other variations of the Model that involve a delay in the order cycle time, which requires real-time decisions. For example, a supplier's lead time. I explain that if a supplier takes their time delivering the order to the customer, the customer must maintain a reserve or know the exact time to place the order so that once it arrives, it does not affect inventory control or incur shortages. This cycle time between the order and receipt, taking into account customer time, is known as **Lead Time**, while the inventory level at which the order must be ordered is known as ROL; likewise, the quantity to be ordered at that time is known as ROQ.

#### Conceptualizing:

1. ROQ: is the quantity of units that must be ordered once the ROQ is reached.
2. ROL: inventory level measured in units that triggers the order.
3. LT: lead time, the time it takes for an order to arrive from the moment it is placed.
4. SStock: safety stock, the level of safety stock needed to withstand the supplier's LT variability (P\_i\_i).

### EOQ Model in Python

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
```

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

def eoq(product_cost, order_cost, storage_cost, annual_demand):
q = np.sqrt((2 * order_cost * annual_demand) / storage_cost)
time_between_orders = q / annual_demand
total_cost = (product_cost * annual_demand) + (order_cost * annual_demand / q) + (storage_cost * q / 2)
return q, time_between_orders, total_cost

# Prompt the user to enter inventory parameter values
product_cost = float(input("Enter the product cost per unit: "))
order_cost = float(input("Enter the cost per order: "))
storage_cost = float(input("Enter the storage cost per unit per year: "))
annual_demand = np. arange(10, 1000, 10)

# Calculate the EOQ for each annual demand value
q_values = [eoq(product_cost, order_cost, storage_cost, d)[0] for d in annual_demand]
total_cost_values = [eoq(product_cost, order_cost, storage_cost, d)[2] for d in annual_demand]

# Plot total cost as a function of annual demand
fig, ax1 = plt.subplots()

color = 'tab:red'
ax1.set_xlabel('Annual Demand')
ax1.set_ylabel('Optimal Inventory Quantity', color=color)
ax1.plot(annual_demand, q_values, color=color)
ax1.tick_params(axis='y', labelcolor=color)

ax2 = ax1.twinx()

color = 'tab:blue'
ax2.set_ylabel('Total Inventory Cost', color=color)
ax2.plot(annual_demand, total_cost_values, color=color)
ax2.tick_params(axis='y', labelcolor=color)

fig.tight_layout()
plt.show()
```

```python
import numpy as np
import matplotlib.pyplot as plt

def total_cost(D, h, s, Q):

return (D/Q)*s + (Q/2)*h

def graph_eoq(D, h, s):

# Range of values for Q
Q = np.linspace(1, 100, 100)

# Calculate costs
maint_cost = (Q/2)*h
ped_cost = (D/Q)*s
annual_total_cost = total_cost(D, h, s, Q)

# Create the figure
plt.figure(figsize=(5, 3))

# Graph costs
plt.plot(Q, maint_cost, label='Maintenance Cost')
plt.plot(Q, ed_cost, label='Ordering Cost')
plt.plot(Q, total_annual_cost, label='Total Cost')

# Find the minimum total cost point (optimal Q)
Q_optimum = np.sqrt(2*D*s/h)
plt.axvline(x=Q_optimum, color='red', linestyle='--', label='Optimal Q')

# Labels and Legend
plt.xlabel('Lot Size (Q)')
plt.ylabel('Cost')
plt.title('EOQ Model')
plt.legend()

# Show the graph
plt.grid(True)
plt.show()

# Usage Example
annual_demand = 100
holding_cost = 7
order_cost = 2
graph_eoq(annual_demand, holding_cost, order_cost)
```

### ROQ, Lead Time, and Safety Stock in Deterministic Inventory Models.

* The assumptions of the EoQ model are listed as follows:

1. **Constant Demand:** Demand for the product is assumed to be constant over time, implying no seasonal fluctuations or changes in demand.
2. **Constant Supply or Production Rate:** Inventory supply or production is assumed to be instantaneous and constant. That is, each time an order is placed, it arrives immediately and completely replenishes inventory.
3. **Known and Constant Lead Time:** The time it takes to receive an order after it is placed is known and does not vary.
4. **Constant Ordering Cost:** The cost associated with placing an order is fixed, regardless of the order size.
5. **Constant Carrying Cost:** The cost of holding a unit in inventory is constant and does not vary over time or with the amount of inventory.

However, there are other variations of the Model that involve a delay in the order cycle time, which requires real-time decisions. For example, a supplier's lead time. I explain that if a supplier takes their time delivering the order to the customer, the customer must maintain a reserve or know the exact time to place the order so that once it arrives, it does not affect inventory control or incur shortages. This cycle time between the order and receipt, taking into account customer time, is known as **Lead Time**, while the inventory level at which the order must be ordered is known as ROL; likewise, the quantity to be ordered at that time is known as ROQ.

#### Conceptualizing:&#x20;

1. ROQ: is the quantity of units that must be ordered once the ROQ is reached.
2. ROL: inventory level measured in units that triggers the order.
3. LT: lead time, the time it takes for an order to arrive from the moment it is placed.
4. SStock: safety stock, the level of safety stock needed to withstand the supplier's LT variability (P\_i\_i).

### EOQ Model in Python

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
```

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

def eoq(product_cost, order_cost, storage_cost, annual_demand):
q = np.sqrt((2 * order_cost * annual_demand) / storage_cost)
time_between_orders = q / annual_demand
total_cost = (product_cost * annual_demand) + (order_cost * annual_demand / q) + (storage_cost * q / 2)
return q, time_between_orders, total_cost

# Prompt the user to enter inventory parameter values
product_cost = float(input("Enter the product cost per unit: "))
order_cost = float(input("Enter the cost per order: "))
storage_cost = float(input("Enter the storage cost per unit per year: "))
annual_demand = np. arange(10, 1000, 10)

# Calculate the EOQ for each annual demand value
q_values = [eoq(product_cost, order_cost, storage_cost, d)[0] for d in annual_demand]
total_cost_values = [eoq(product_cost, order_cost, storage_cost, d)[2] for d in annual_demand]

# Plot total cost as a function of annual demand
fig, ax1 = plt.subplots()

color = 'tab:red'
ax1.set_xlabel('Annual Demand')
ax1.set_ylabel('Optimal Inventory Quantity', color=color)
ax1.plot(annual_demand, q_values, color=color)
ax1.tick_params(axis='y', labelcolor=color)

ax2 = ax1.twinx()

color = 'tab:blue'
ax2.set_ylabel('Total Inventory Cost', color=color)
ax2.plot(annual_demand, total_cost_values, color=color)
ax2.tick_params(axis='y', labelcolor=color)

fig.tight_layout()
plt.show()
```

````python
import numpy as np
import matplotlib.pyplot as plt

def total_cost(D, h, s, Q):

return (D/Q)*s + (Q/2)*h

def graph_eoq(D, h, s):

# Range of values for Q
Q = np.linspace(1, 100, 100)

# Calculate costs
maint_cost = (Q/2)*h
ped_cost = (D/Q)*s
annual_total_cost = total_cost(D, h, s, Q)

# Create the figure
plt.figure(figsize=(5, 3))

# Graph costs
plt.plot(Q, maint_cost, label='Maintenance Cost')
plt.plot(Q, ed_cost, label='Ordering Cost')
plt.plot(Q, total_annual_cost, label='Total Cost')

# Find the minimum total cost point (optimal Q)
Q_optimum = np.sqrt(2*D*s/h)
plt.axvline(x=Q_optimum, color='red', linestyle='--', label='Optimal Q')

# Labels and Legend
plt.xlabel('Lot Size (Q)')
plt.ylabel('Cost')
plt.title('EOQ Model')
plt.legend()

# Show the graph
plt.grid(True)
plt.show()

# Usage Example
annual_demand = 100
holding_cost = 7
order_cost = 2
graph_eoq(annual_demand, holding_cost, order_cost)



### EOQ Exercises

#### Exercise 1[#](broken-reference)

Industrial.inc. is a company dedicated to the manufacture of self-drilling screws for the aluminum industry. It wishes to reduce its inventory costs by determining the number of screws it should obtain in each order.

* Demand is 10,000
* The order has an associated cost of $1,000
* Holding cost is $1.50 per year.
* The year has 250 business days.

You must calculate:

* a) Optimal Order Number \\((q)\\)
* b) Number of orders per year
* c) Cycle time, the expected time between orders.

#### Exercise 2[#](broken-reference)

The company [Amigos.sa](http://amigos.sa/) sells household goods, with an annual demand of 1,000 units. If the cost to place an order is $10 USD, the annual unit storage cost for each item is $2.5 USD. The company operates 365 days a week, seven days a week, and has a cost of sale of $15 USD per item, determine the optimal inventory policy for this problem.

#### Exercise 3[#](broken-reference)

A school van transportation company consumes gasoline at a rate of 8,200 gallons per month. Gasoline costs 12,000 COP and has an ordering cost of 6,000 COP. The inventory holding cost is 2,000 COP per gallon.

* Determine when and how much should be ordered if total costs are to be minimized.
* Assume stockouts are allowed with a penalty of 1,500 COP per gallon per month.
* Assume the cost of gasoline drops to 8,000 COP per gallon if at least 10,000 gallons are purchased. How would this affect the cost, taking into account the previous penalty?
* Assume the cost of gasoline would be 7,000 COP per gallon if the minimum batch cost is 12,000 gallons, taking into account the previous penalty.
* Will an initial inventory be necessary to solve the problem? Provide technical support for your answer.

#### Exercise Number 4[#](broken-reference)

A company dedicated to the printing and marketing of books is making a monthly purchase. To do this, they conducted a market study on the company's most important input: the special paper used to print their books. Over the last 12 months, your demand behavior was:

(Demand = [10 -11-10-9-10-11-9-10.5-10-9-9-11.5]) tons per month. The purchase price is estimated to remain at COP $3,400,000 per ton. Your ordering cost is COP $350,000. Company policy states that a 15% charge will be made for inventory management plus COP $60,000 for warehouse management. Calculate:

* The optimal model for managing this inventory
* If the supplier offers to give us a 10% discount for purchases over 30 tons and another supplier offers an 11% discount for purchases over 60 tons, how would my inventory policy change in each of the scenarios?
* If, in addition to the discount, we reach an agreement with an external warehouse where storage is reduced by 9% with a maximum capacity of 35 tons, how would our policy change?

#### Exercise 5[#](broken-reference)

Economic Order Quantity The demand for Deskpro computers at Best Buy is 1,000 units per month. Best Buy incurs fixed ordering, transportation, and receiving costs of $4,000 each time an order is placed. Each computer costs $500, and the retailer has an inventory holding cost of 20%. Evaluate the number of computers the store manager should order in each replenishment batch.

#### Exercise Number 6[#](broken-reference)

Abc company have two item X\_1 and X\_2 for stockin into their warehouse, the Demand for each one of the items is:

D\_1 = 10000u&#x20;

D\_2 = 12000u

The holding cost for each one of them is 13% and the cost is C\_1 = 5000cop And C\_2 = 7000Cop

the two items have the same supplier so they save the operation costing \\(6000cop\\) by S

* need to find the total cost of the operation
* if the supplier takes 3 days of delay how would it be modeled
* ROLE
*ROQ


#### Ejercicio Numero 7[#](broken-reference)

Water testing at the Central Park reservoir requires a chemical reagent that costs 500usd per gallon. Use is constant at 1/3 gallon per week. Carrying cost rate is considered to be 12% per year, and the cost of an order is 125usd. What is the optimal order quantity for the reagent?

#### Ejercicio Numero 8[#](broken-reference)

Continuing with the information about the Central Park reservoir given in Problem 1, the city could make this reagent at the rate of 1/8 gallon per day, at a cost of $300 per gallon. The setup cost is 150usd. Use a 7-day week. Compare using the EOQ and the EPQ systems. What course of action do you recommend?

#### Inventory Exercise with Mathematical Modeling in Python[#](broken-reference)

Company **XYZ** has three customers and four suppliers. The company manufactures two products, X\_1 and X\_2. Product X\_1 requires two units of MP\_1 and one unit of MP\_2. Product X\_2 requires one unit of MP\_1 and three units of MP\_2. The storage cost for finished products X\_1 and X\_2 is 0.5 COP/unit and 0.8 COP/unit, respectively. The cost of ordering X\_1 and X\_2 is 1.2 COP/unit and 0.8 COP/unit, respectively. It is worth mentioning that when ordering a product, suppliers respond with the respective components for each MP\_i.

The **cost** table for MP\_i is given as follows:

| Supplier | Rm\_1 | Rm\_2 |
| --------- | ----- | ----- |
| S\_1 | 90 | 75 |
| S\_2 | 50 | 65 |
| S\_3 | 65 | 25 |
| S\_4 | 70 | 50 |

* The system demand is given as follows:

| Customer | X\_1 | X\_2 |
| ------- | ---- | ---- |
| C\_1 | 500 | 250 |
| C\_2 | 450 | 300 |
| C\_3 | 250 | 300 |

* It is assumed that the system is balanced and that suppliers can supply the demand in full.

Find:

1. The minimum system cost to supply the demand.

2. The costs associated with the system according to the POQ model.
3. If the suppliers have a lead time of:

| SUPPLIER | LEAD TIME |
| --------- | --------- |
| S\_1 | 2 |
| S\_2 | 4 |
| S\_3 | 2 |
| S\_4 | 5 |

Calculate the ROL and ROQ for each product, based on their Bill of Material.

4. Calculate the demand rate (discount) \\(d\\). Taking into account a production rate of x\_1 = 80 units/day and x\_2 = 60 units/day, calculate the optimal economic batch size and the warehouse size the company should have.

**Let's add the total inventory cost and graph it**[**#**](broken-reference)

```python
# Data for the desktop test
D = 100,000
h = 30,000
S = 14,000
period = 365
lead_time = 2

# Calculate optimal Q and initial inventory
Q_opt = ((2 * D * S) / h)**0.5
initial_inventory = round(Q_opt)

# Create a table to store the inventory
inventory = pd.DataFrame(columns=["Day", "Initial_Inventory", "Inventory_Level", "Order", "Demand", "Ending_Inventory"])

# Initialize the table with day zero
inventory_zero = round(Q_opt)
inventory = inventory.append({"Day": 0,
"Initial_Inventory": 0,
"Inventory_Level": 0,
"Order": 0,
"Demand": 0,
"Ending_Inventory": zero_inventory},
ignore_index=True)

# Fill the table with the logic we defined
for day in range(1, period+1):
# Calculate demand for the current day
demand = round(np. random. normal(D/period, 0.1*D/period))

# Calculate inventory level and order
if day == 1:
starting_inventory = zero_inventory
else:
starting_inventory = inventory["Ending_Inventory"].iloc[day-1]

inventory_level = starting_inventory - demand
if inventory_level < 0:
inventory_level = 0
order = round(Q_opt) - inventory_level
else:
order = 0

# Update ending inventory
ending_inventory = inventory_level + order

# Add a row to the table
inventory = inventory. append({"Day": day,
"Starting_Inventory": starting_inventory,
"Inventory_Level": inventory_level,
"Order": order,
"Demand": demand,
"Ending_Inventory": ending_inventory},
ignore_index=True)

# define the total inventory cost

total_cost = (D * S / Q_opt) + (Q_opt / 2 * h)

# to export the .csv file from the generated database, remove the numeral from the following code
# the file will be generated in this spreadsheet; you must download it
#inventory.to_csv("table_inventory_crc.csv", index=False)

print("The optimal Q for this example is:", round(Q_opt))
print("The total inventory cost is:", total_cost)

# Print the table
print(inventory)

# Graph the inventory level

plt.figure(figsize=(40,10))
plt.plot(inventory["Day"], inventory["Inventory_Level"])
plt.xlabel("Days")
plt.ylabel("Inventory Level")
plt.show()
````

### EPQ Model[#](broken-reference/)

The economic production quantity (EPQ) model (also known as the economic lot size (ELS) model) is used in manufacturing situations where inventory increases at a finite rate and depends on the production rate and the usage rate of the item under consideration. In addition to the variables (D, S, H, Q, and C) defined earlier, we define two more variables: p = production rate per day (daily production rate) and d = demand rate per day (daily demand rate). The values of p and d must be in the same time unit. For example, these values could be weekly rates instead of daily rates. However, daily rates are most common. Q in this case is the production quantity (rather than order quantity) to be made in one lot and S is the cost of setting up the machine to produce that one lot. Therefore, S is called the setup cost per set up (rather than order cost per order).

$$
Q_{epq}=\sqrt{\left(\frac{2DS}{h\left(1-\frac{d}{q}\right)}\right)}
$$

#### EPQ Example

Let's find:

1. Annual demand = 50,000 units
2. Setup cost = $25 USD
3. Maintenance cost = $5 USD
4. Production rate (p) = 500 units/day
5. Working days = 250 days

So we solve:

We don't know _d_, but it can be calculated using the working days and annual demand.

$$
d = \frac{50,000}{250} = 200 un
$$

Using the _EPQ_ formula, we get:

$$
Q_{epq} = \sqrt{\frac{2*50,000*25}{5*(1-\frac{200}{250})}} = 912.87
$$

We can also calculate the maximum inventory level (\\(I\_{max})\\)

$$
I_{max}=Q * \left(1-\frac{d}{p}\right)
$$

Substituting:

$$
I_{max}=912.87*\left(1-\frac{200}{500}\right) = 547.72 un
$$
