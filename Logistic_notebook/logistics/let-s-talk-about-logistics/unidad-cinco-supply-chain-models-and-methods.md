# Unit five: supply chain models and methods

md\_doc = """

## Unit Five: Supply Chain Models and Methods

This unit covers various models and methods for managing supply chains, focusing on maximizing efficiency, reducing costs, and mitigating risks. We will learn how these tools help us make better decisions and strengthen our competitive advantages.

#### Fundamental Concept

> Imagine the supply chain as a river flowing from the source (raw material suppliers) to the sea (final customer); the product travels through various channels. A supply chain model allows us to map and optimize this flow, identifying the best routes and minimizing obstacles.

**Decision making is based on information collected throughout the supply chain, allowing us to select the best model and tools for each case.**

**Types of Supply Chain Models**

There are several types of models, each with its own characteristics and applications:

1. Continuous Models: Assume that demand and production are constant over time.
2. Agile Models: Adapt quickly to changes in demand and the environment.
3. Fast Models: Prioritize delivery speed and responsiveness to customer needs.
4. Custom-Configured Models: Designed specifically for a particular company or industry.

**Tools for Building Logistics Chains**

1. Simulation Software:
   * AnyLogic: Offers great flexibility for modeling complex systems, including supply chains. Enables creating 3D models and conducting detailed simulations.
2. Spreadsheets:
   * Excel: While more basic, it can be useful for building simple models and performing sensitivity analyses.
3. Programming Languages:
   * Python: With libraries like Pyomo and SimPy, you can create custom and complex models.
4. Optimization Software:
   * CPLEX: Used to solve mathematical optimization problems, such as minimizing costs or maximizing profits.

**Steps for Building a Supply Chain Model:**

1. Defining the Problem:
   * Identify the model’s objective (reduce costs, improve customer service, etc.).
   * Define key variables (demand, inventory, delivery time, etc.).
   * Set system boundaries and constraints.
2. Data Collection:
   * Obtain historical data on demand, costs, cycle times, etc.
   * Verify data quality and consistency.
3. Model Design:
   * Select the appropriate modeling tool.
   * Define the model structure (components, relationships, flows).
   * Implement the model’s equations and logic.
4. Model Validation:
   * Compare model results with historical data.
   * Adjust the model if necessary.
5. Analysis and Simulation:
   * Run different scenarios to evaluate the impact of decisions.
   * Identify bottlenecks and areas for improvement.
6. Implementation:
   * Communicate model results to decision-makers.
   * Develop an implementation plan for recommended changes.

#### Building a Supply Chain Using Python

We will use Python as a platform to measure a supply chain using the _simpy_ library.

## Unit Six: Design and Measurement of the Logistics Chain

`Supply Chain Optimization Design and Management_ Advances and Intelligent Methods Premier Reference Source`

***

A wide range of methodologies have been used to solve this optimization problem. However, traditional mathematical methods have proven insufficient to address the complexity and uncertainty of modern supply chains. For this reason, advanced intelligent methods are currently used, such as:

1. Ant Colony Optimization (ACO)
2. Particle Swarm Optimization (PSO)
3. Genetic Algorithms
4. Genetic Programming
5. Memetic Algorithms
6. Artificial Immune Systems
7. DNA Computing

#### Definitions

To clarify the basic concepts of supply chain management, it’s helpful to present the main functions of a simplified supply chain (Silva et al.):

1. **Logistics System:** Receives orders from customers and places orders to suppliers for raw materials. Purchased materials are used in the manufacturing process and then sent to the distribution system.
2. **Supply System:** Consists of a network of different suppliers or manufacturers, each responsible for producing the requested product component for the logistics system.
3. **Distribution System:** Delivers complete products to the corresponding customers, who can be described by their geographic location. A simple, realistic model for logistics distribution considers grouping customers by region.

#### Supply Chain Measurement Approach with Aggregate Production Planning

_The literature on production planning and control is full of models and algorithms to find efficient plans for most types of industries. In this chapter, we focus on those designed for robust and efficient aggregate production planning._

A particularly effective technique for obtaining robust and efficient production plans is based on the decomposition principle, also known as “divide and conquer.”

To find the optimal plan over a time horizon, time itself is decomposed into two or more levels of granularity, forming a hierarchy:

* At the aggregate level, a period may comprise a month or a quarter, and the aggregate production planning problem is to decide what to produce for a series of products or product families.

These production plans are especially useful for staffing decisions, including possible overtime the company should use in an aggregate period.

We begin our discussion of aggregate production planning with the simplest possible example.

1. Consider a monthly demand forecast $$d_i, \ i=1 ... N$$ for N periods, for an imaginary company that produces a single product. The problem is to build inventory to meet demand, considering:
   * Maintenance
   * Inventory
   * Opportunity costs
   * Risk of inventory obsolescence
   * Risk of inventory damage due to natural disasters
   * Other types

If capacity constraints are not considered, the optimal policy is to produce everything just-in-time (JIT), as there is enough capacity to meet demand when needed.

$$
\begin{split} \text{min} \sum_{i=1}^{N}h_i \\ \text{constraints:} \\ h_i=h_{i-1}+x_i-d_i,\ i=1,...,N\\ 0 \leq x_i\leq c,\ i=1,...,N\\ 0 \leq h_i,\ i=1,...,N\\ h_0 = I_0 \end{split}
$$

The decision variables x represent the production in each period, while h represent the inventory at the end of each period. Initially, we assume an initial accumulation of inventory.

#### Special Models

**Interactive EOQ Model**

```python
!pip install ipywidgets
!pip install matplotlib
```

```python
import numpy as np
import matplotlib.pyplot as plt
import ipywidgets as widgets
from IPython.display import display

# EOQ calculation function
def eoq(demand, order_cost, holding_cost):
    return np.sqrt((2 * demand * order_cost) / holding_cost)

# Total cost calculation function
def total_cost(order_quantity, demand, order_cost, holding_cost):
    return (order_cost * demand / order_quantity) + (holding_cost * order_quantity / 2)

# Update plot based on widgets
def update_plot(demand, order_cost, holding_cost):
    order_quantities = np.linspace(1, 2 * demand, 500)
    costs = total_cost(order_quantities, demand, order_cost, holding_cost)

    q_optimal = eoq(demand, order_cost, holding_cost)

    plt.figure(figsize=(12, 6))

    # Plot total costs
    plt.plot(order_quantities, costs, label='Total Cost', color='blue')
    plt.axvline(x=q_optimal, color='r', linestyle='--', label=f'EOQ: {q_optimal:.2f}')

    # Plot ordering costs
    cost_ordering = order_cost * demand / order_quantities
    plt.plot(order_quantities, cost_ordering, label='Ordering Cost', color='green', linestyle='--')

    # Plot holding costs
    cost_holding = holding_cost * order_quantities / 2
    plt.plot(order_quantities, cost_holding, label='Holding Cost', color='orange', linestyle='--')

    plt.xlabel('Order Quantity')
    plt.ylabel('Cost')
    plt.title('Interactive EOQ Model')
    plt.legend()
    plt.grid(True)
    plt.show()

# Widgets for parameters
demand_widget = widgets.FloatSlider(value=20, min=10, max=1000, step=10, description='Annual Demand:')
order_cost_widget = widgets.FloatSlider(value=10, min=10, max=200, step=10, description='Order Cost:')
holding_cost_widget = widgets.FloatSlider(value=2, min=0.5, max=200, step=0.5, description='Holding Cost:')

# Link widgets with update function
ui = widgets.VBox([demand_widget, order_cost_widget, holding_cost_widget])
out = widgets.interactive_output(update_plot, {
    'demand': demand_widget,
    'order_cost': order_cost_widget,
    'holding_cost': holding_cost_widget
})

display(ui, out)
```

Interactive models help us understand the logic behind things. Try modifying each data point; we can also use Python’s own elements for comparisons, e.g., the following code takes the Demand, h, and S values and adds one unit to the s variable ten times to verify Q’s behavior. In this way, you can analyze the effect of changing S on the EOQ.

```
import math

def eoq(demand, order_cost, holding_cost, s_value):
    eoq = math.sqrt((2 * demand * order_cost) / (holding_cost * s_value))
    return eoq

demand = float(input("Enter annual demand: "))
order_cost = float(input("Enter order cost: "))
holding_cost = float(input("Enter holding cost: "))

for i in range(10):
    s_value = (order_cost + i) + 1  # S value changes each iteration
    eoq_value = eoq(demand, order_cost, holding_cost, s_value)
    print(f"For S = {s_value}, EOQ: {eoq_value}")

Enter annual demand: 100
Enter order cost: 02
Enter holding cost: 5
For S = 3.0, EOQ: 5.163977794943222
For S = 4.0, EOQ: 4.47213595499958
For S = 5.0, EOQ: 4.0
For S = 6.0, EOQ: 3.6514837167011076
For S = 7.0, EOQ: 3.3806170189140663
For S = 8.0, EOQ: 3.1622776601683795
For S = 9.0, EOQ: 2.9814239699997196
For S = 10.0, EOQ: 2.8284271247461903
For S = 11.0, EOQ: 2.696799449852968
For S = 12.0, EOQ: 2.581988897471611
```

#### Interactive POQ Model - Python

```
import ipywidgets as widgets
from IPython.display import display
import matplotlib.pyplot as plt
import numpy as np

def calculate_epq(demand, setup_cost, holding_cost, production_rate):
    return np.sqrt((2 * demand * setup_cost) / holding_cost * (production_rate / (production_rate - demand)))

# Widget details
demand_widget = widgets.IntSlider(value=1000, min=100, max=5000, step=100, description='Demand:')
setup_cost_widget = widgets.IntSlider(value=100, min=10, max=500, step=10, description='Setup Cost:')
holding_cost_widget = widgets.FloatSlider(value=0.5, min=0.1, max=2.0, step=0.1, description='Holding Cost:')
production_rate_widget = widgets.IntSlider(value=6000, min=1000, max=10000, step=100, description='Production Rate:')

def update_graph(demand, setup_cost, holding_cost, production_rate):
    epq_value = calculate_epq(demand, setup_cost, holding_cost, production_rate)
    print(f'EPQ: {epq_value:.2f}')

    # Data
    cycle_time = epq_value / demand
    production_time = epq_value / production_rate
    time = np.linspace(0, cycle_time, 100)
    inventory = np.where(time <= production_time,
                         production_rate * time - demand * time,
                         epq_value - demand * time)

    # Plot
    plt.figure(figsize=(8, 6))
    plt.plot(time, inventory)
    plt.xlabel('Time')
    plt.ylabel('Inventory')
    plt.title('EPQ Model')
    plt.grid(True)
    plt.show()

widgets.interact(update_graph,
                 demand=demand_widget,
                 setup_cost=setup_cost_widget,
                 holding_cost=holding_cost_widget,
                 production_rate=production_rate_widget);
```

#### Random Route Assignment Model

```
import random
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Request number of nodes
num_nodes = int(input("Enter the number of nodes: "))

# Generate random positions for each node
positions = {i: (random.random(), random.random()) for i in range(num_nodes)}

# Calculate distance matrix
distance_matrix = np.zeros((num_nodes, num_nodes))
for i in range(num_nodes):
    for j in range(i + 1, num_nodes):
        distance = np.sqrt((positions[i][0] - positions[j][0])**2 + (positions[i][1] - positions[j][1])**2)
        distance_matrix[i, j] = round(distance, 1)
        distance_matrix[j, i] = round(distance, 1)

# Show distance matrix as a table
df_distances = pd.DataFrame(distance_matrix)
print(df_distances)

# Plot node positions
x = [pos[0] for pos in positions.values()]
y = [pos[1] for pos in positions.values()]
plt.scatter(x, y)
plt.xlabel("X Axis")
plt.ylabel("Y Axis")
plt.title("Node Positions")
plt.show()
```

```
Enter the number of nodes: 10
     0    1    2    3    4    5    6    7    8    9
0  0.0  0.3  0.6  0.5  0.4  0.3  0.3  0.3  0.3  0.4
1  0.3  0.0  0.7  0.7  0.5  0.1  0.2  0.4  0.6  0.7
2  0.6  0.7  0.0  0.5  0.3  0.7  0.9  0.4  0.6  0.5
3  0.5  0.7  0.5  0.0  0.3  0.7  0.7  0.5  0.2  0.1
4  0.4  0.5  0.3  0.3  0.0  0.5  0.6  0.2  0.3  0.3
5  0.3  0.1  0.7  0.7  0.5  0.0  0.3  0.3  0.6  0.7
6  0.3  0.2  0.9  0.7  0.6  0.3  0.0  0.5  0.5  0.7
7  0.3  0.4  0.4  0.5  0.2  0.3  0.5  0.0  0.4  0.4
8  0.3  0.6  0.6  0.2  0.3  0.6  0.5  0.4  0.0  0.2
9  0.4  0.7  0.5  0.1  0.3  0.7  0.7  0.4  0.2  0.0
```

"""

You can copy and paste this string directly into your Python script or notebook. If you want this pushed to your repository, just let me know!
