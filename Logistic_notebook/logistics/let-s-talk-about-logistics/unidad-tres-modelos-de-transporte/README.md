# Unit Three: Transport Models

With an underdeveloped transportation system, market size is limited to the areas immediately surrounding the production point.&#x20;

Unless production costs are extremely low compared to those of a second production point (i.e., the difference in production costs offsets the transportation costs of serving the second market), there is likely to be little competition. However, with improvements in the transportation system, reduced costs for products in distant markets can be competitive with other products sold in the same markets.&#x20;

In addition to fostering direct competition, low-cost, high-quality transportation also fosters an indirect form of competition by making goods available in a market that would normally be unable to afford the transportation cost. Sales may actually be increased by penetrating markets not normally available for certain products. Goods from a foreign region have a stabilizing effect on the prices of all similar goods in the market. (Ronald Ballou)

***

### Transport Costing

The price (cost) of the transportation service for a consignee will simply be the liner rate for the movement of goods and any ancillary or terminal charges for additional services provided. In the case of contract service, the rate charged for the movement of goods between two points plus any additional charges, such as picking up the goods at the origin, delivery at the destination, insurance, or preparing the goods for shipment, will constitute the total cost of the service. When the consignee owns the service (for example, a fleet of trucks), the cost of the service will be an allocation of the relevant costs to a particular shipment. Relevant costs include items such as fuel, labor, maintenance, equipment depreciation, and administrative costs.

***

### SIMPLE SERVICE OPTIONS

The simple service options for transportation include various modes of transport that cater to different needs:

* **Rail**: Often used for transporting heavy goods over long distances. It is cost-effective and energy-efficient, suitable for bulk shipments.
* **Truck**: Provides door-to-door service and is versatile. Ideal for short-haul and last-mile deliveries, offering flexibility in routes and schedules.
* **Plane**: The fastest mode of transport, best for high-value or time-sensitive goods. Air transport ensures quick delivery over long distances but at a higher cost.
* **Ship**: Suitable for international trade, particularly for bulky and non-perishable goods. Although slower than air, it is economical for large volumes.
* **Pipelines**: Used for transporting liquids and gases over long distances. Pipelines offer a continuous flow and are cost-effective once established.

### INTERMODAL SERVICES.

### Flatbed Trailers

Top-of-Flatbed Trailer (TOPC), or piggyback trailer, refers to the transport of trailers on railroad platforms, generally over longer distances than trucks. TOPC combines the convenience and flexibility of trucking with the long-haul economy of rail.

### Standard Container Loading 

Under a TOFC agreement, the entire trailer is transported on a railroad bed. However, the trailer can also be viewed in two forms: 1) as a container or box in which the cargo is packed; and 2) as the trailer chassis. In a truck-rail intermodal service, it is possible to transport only the container, thus saving the deadweight of the structure and wheels. This service is called container-on-bed (COFC).

***

### TRANSPORTATION COST CHARACTERISTICS

The price that the logistics manager must pay for transportation services depends on the cost characteristics of each type of service. Because each service has different cost characteristics, under a given set of circumstances, there will be potential price advantages that cannot be effectively matched by other services.

### Variable and Fixed Costs

A transportation service incurs various costs, such as labor, fuel, maintenance, terminals, roads, administration, and others. The mix of costs can be arbitrarily divided into those that vary with services or volume (variable costs) and those that do not (fixed costs). Naturally, all costs are variable if a sufficiently long time and large enough volume are considered. However, for transportation pricing purposes, it is useful to consider costs that are constant during the carrier's "normal" operating volume as fixed. All other costs are treated as variable.

***

## Transport modeling

<img src="../../../.gitbook/assets/file.excalidraw.svg" alt="" class="gitbook-drawing">

The network shown represents the problem. There are "m" origins and "n" destinations, each represented by a node. The arcs represent the routes connecting the origins to the destinations. The arc (i, j) connecting origin i to destination j carries two pieces of information,&#x20;

the transportation cost per unit, cij, and the quantity transported, xij. The quantity supplied at origin i is ai, and the quantity demanded at destination j is bj. The objective of the model is to minimize the total transportation cost while satisfying the supply and demand constraints.

Example (taha book - page 175)

MG Auto has three plants in Los Angeles, Detroit, and New Orleans, and two major distribution centers in Denver and Miami. The quarterly capacities of the three plants are 1,000, 1,500, and 1,200 cars, and the demand of the two distribution centers during the same period is 2,300 and 1,400 cars. The distance in miles between the plants and distribution centers is shown in the table.

|             | Miles graph data |       |
| ----------- | ---------------- | ----- |
|             | Denver           | Miami |
| LA          | 1000             | 2690  |
| Detroit     | 1250             | 1350  |
| New Orleans | 1275             | 850   |

The trucking company charges 8 cents per mile per car. shows the transportation costs per car on the different routes, rounded to the nearest dollar.

|             | Cost Dat |       |
| ----------- | -------- | ----- |
|             | Denver   | Miami |
| LA          | 80       | 215   |
| Detroit     | 100      | 108   |
| New Orleans | 102      | 68    |

***

$$
\text{Minimizar z} =  Z_{min}= 80x_{11} + 215x_{12} + 100x_{21} + 108x_{22} + 102x_{31} + 68x_{32}
$$

Sa:

$$
x_{11} + x_{12} = 1000 (Los Ángeles)\\ 
x_{21} + x_{22} = 1500 (Detroit)\\
+ x_{31} + x_{32} = 1200 (Nueva Orléans)\\
x_{11} + x_{21} + x_{31} = 2300 (Denver)\\
x_{12} + x_{22} + x_{32} = 1400 (Miami)\\
x_{ij} \forall\ i= 1, 2, 3, j= 1, 2
$$

{% hint style="warning" %}
**Balancing the transportation model**. The transportation table representation assumes that the model is balanced, that is, that total demand equals total supply. If the model is unbalanced, we can add a dummy origin or destination to restore balance.
{% endhint %}

## Instructions for Using the PuLP Library

The PuLP library is a powerful tool for linear programming in Python. Here we provide a step-by-step guide to using this library effectively.

### Installing PuLP

Before you start using PuLP, you first need to install it. You can do this easily using pip. Open a terminal and type the following command:

```bash
pip install pulp
```

### Creating a Problem

To define a linear programming problem, you must start by importing the library and creating an `LpProblem` object. This object represents your problem.

```python
from pulp import LpProblem, LpMaximize

# Creating a Maximization Problem
problem = LpProblem("My_Problem", LpMaximize)
```

### Declaring Variables

Next, define the decision variables that will be used in your model. Pulp provides the `LpVariable` class for this purpose.

```python
from pulp import LpVariable

# Create a continuous decision variable
x = LpVariable('x', lowBound=0)
y = LpVariable('y', lowBound=0)
```

### Defining the Objective Function

The objective function is the mathematical function you need to maximize or minimize. You can define it using the variables you created.

```python
# Defining the objective function
problem += 3*x + 2*y, "Objective_Function"
```

#### Adding Constraints

Constraints are added to the problem using common mathematical operators. These limit the possible values of the variables.

```python
# Add constraints
problem += (2*x + y <= 20), "Constraint_1"
problem += (4*x - 5*y >= -10), "Constraint_2"
```

#### Problem Solving

With the objective function and constraints defined, the next step is to solve the problem. PuLP can use different solvers, but the default solver is usually sufficient for most cases.

```python
problem.solve()
```

#### Print Results

Once the problem is solved, you can access the results, such as the optimal value of the objective function and the decision variables.

```python
# Display problem status
print("Status:", LpStatus[problem.status])

# Display the optimal value of the variables
for variable in problem.variables():
print(f"{variable.name} = {variable.varValue}")

# Optimal value of the objective function
print("Optimal value: ", value(problem.objective))
```

{% hint style="info" %}
The PuLP library is a versatile tool for solving linear programming problems in Python. It allows for rapid implementation and simplifies the complexity of modeling optimization problems. With the steps described above, you can begin exploring its capabilities and applying linear programming to your projects.
{% endhint %}

This library will be used to solve transportation problems.

For more information about this library, please visit: [https://pypi.org/project/PuLP/](https://pypi.org/project/PuLP/)

1. Install the library: _“pip install pulp”_

#### Import:

* import pulp

1. Create the problem: To create the problem, we must define the variable that will store the problem, for example, "prob." # Create the problem with the command _"pulp.LpProblem"_, where we will assign a name and the type of problem we are facing: - Minimization: pulp.LpMinimize - Maximization: pulp.LpMaximize

with the syntax: **prob = pulp.LpProblem("Task Assignment", pulp.LpMinimize)**

#### Creating the Model Variables:

Variables are the basis of optimization problems, and depending on the type of problem you are solving, they can take on different categories (typologies), such as continuous, integer, or binary variables.

* To create a variable in PuLP, use the LpVariable class, which requires at least a name as an argument and can include constraints such as its type (binary, continuous, integer) and limits on its values. The basic way to define a variable is:

x = LpVariable('x')

Variables can contain model-specific data or simply be empty for use by the model.

#### Defining Variables

Examples of Variables

1. costs = \[\[10, 2, 20], \[12, 7, 15], \[8, 12, 5]]
2. workers = range(3)
3. tasks = range(3)
4. x = pulp.LpVariable.dicts(“x”, \[(i, j) for i in workers for j in tasks], cat=’Binary’)
5. Continuous Variables

These are variables that can take any value within a range, whether positive, negative, or unbounded. This is the default category when the type is not specified.

_**x= LpVariable('x')**_

#### With Bounds

The value of a continuous variable can be restricted to a given interval (for example, between a minimum and maximum value).

* x = LpVariable('x', lowBound=0, upBound=10)
* \\\[0\<X\_i<10\\]

lowBound and upBound are the attributes that define the limits of variables, meaning they also serve as constraints where

* x = LpVariable('x', lowBound=0)
* \\\[X\_{i,j}\ge0\\]

#### Integer Variables

Integer variables can only take whole numeric values within a specific range.

* y = LpVariable('y', lowBound=0, upBound=5, cat='Integer')

In this case, the variable type is specified with the "cat" attribute, which specifies the typology, in this case "integer".

#### Binary Variables

Binary variables are a special case of integer variables, as they can only take the values 0 or 1. This type of variable is useful when modeling binary decisions (yes/no, true/false) in problems such as project selection or resource allocation, which are very common in transportation methods and advanced programming.

* z = LpVariable('z', cat='Binary')

When modeling this type of variable, the decision it entails must be taken into account. That is, it will be 1 if a given condition is met, or 0 if it is not. This way, we can control the system and its logic.

* Summary of Pulp variable arguments:

1. **lowBound:** Defines the variable's lower bound (the smallest value it can take). If not specified, the default is None (no lower bound).
2. **upBound:** Defines the variable's upper bound (the largest value it can take). If not specified, the default is None (no upper bound).
3. **cat:** This argument defines the variable's category (type):

* _'Continuous':_ Continuous variables (default).
* _'Integer':_ Variables that can only take integer values.
* _'Binary':_ Binary variables (which only take the values 0 or 1).

***

### Define the objective function:

Before proceeding with Python programming, it is recommended that the exercise or system be defined in this way, as this makes development easier. When entering the system's objective function, it must already be defined and known according to the nature of the system being investigated. In this case, we will use the following function:

$$
3x_1+2x_2+x_3
$$

* `problem += 3 * x1 + 2 * x2 + x3,` “Objective Function”

Note the name of the variable that encloses the problem: “problem.”

#### Let's add the system's constraints:

`problem += x1 + x2 + x3 <= 2,`

“Constraint 1” `problem += x1 + x2 >= 1`,

“Restriction 2”

In this case, the restrictions are preceded by the symbols $$\(\le\) and \(\ge\)$$

Note that we do not define the “non-negativity” restriction since the variables, when defined and bounded, include the values on which they can operate.

#### We solve:

Use the solve() method to solve the optimization problem. PuLP uses a built-in solver by default, but you can specify one if you prefer.

* problem.solve()

#### Display the result:

Finally, we must specify to the machine that we want to see the results. These can be displayed as flat values, or we can use other libraries such as pandas, mathplotlib, etc., to display these results. However, for these, we would have to define the variables and store the data as required.

print(“Status:”, pulp.LpStatus\[problem.status])

print(“Value of x1:”, x1.varValue) print(“Value of x2:”, x2.varValue) print(“Value of x3:”, x3.varValue)

print(“Optimal value of the objective function:”, pulp.value(problem.objective))

### Definition of the Transportation Model[#](broken-reference/)

Transportation is the backbone of logistics, enabling the flow of goods and services through the supply chain. Its efficiency directly impacts costs, customer satisfaction, and the competitiveness of companies.

There are different modes of transportation, such as land, sea, air, and rail, each with characteristics that make them ideal for certain types of cargo and distances. Choosing the right mode is crucial to optimizing logistics.

In addition to the modes, modes of transportation must be considered, which refer to the way transportation is organized, such as unimodal (a single mode of transportation), multimodal (a combination of modes of transportation), and intermodal (a combination of modes with a single cargo unit).

A logistics model that has gained popularity is cross-docking, which seeks to minimize storage time and streamline distribution.

* Examples

1. Ocean Freight: Ideal for large volumes and long distances, such as the transport of raw materials or manufactured goods between continents.
2. Air Freight: Recommended for perishable or high-value products that require rapid delivery, such as flowers or electronic devices.
3. Cross-docking: A distribution center receives products from different suppliers, consolidates them, and ships them immediately to customers, reducing storage costs and delivery times.

### Key Decision Variables[#](broken-reference/)

When evaluating transportation options, it is essential to consider the following variables:

* Cost: Includes freight, insurance, taxes, and other expenses associated with transportation.
* Time: Refers to the total transit time, from pickup to final delivery.
* Capacity: Refers to the amount of cargo that the chosen mode can carry.
* Reliability: Refers to the probability that the cargo will arrive at its destination on time and under the agreed conditions.

### Graphical Representation of Transportation Models in Linear Programming

A transportation model can be represented graphically using a network of nodes and arcs, similar to a flowchart.

1. Nodes: These represent the origin and destination points of the goods.

* Origin nodes: These indicate the locations from which the goods originate (factories, warehouses, etc.).
* Destination nodes: These represent the locations where the goods must arrive (customers, distribution centers, etc.). Arcs: These are the connections between nodes and symbolize the available transportation routes.

2. Arcs

* Each arc is associated with a transportation cost, which can represent the distance, travel time, or monetary cost of transportation between two nodes. The capacity of each arc can be indicated, which represents the maximum amount of goods that can be transported along that route.

In Python, we have libraries for modeling these diagrams, for example

* graphviz

More information can be found at [https://graphviz.org](https://graphviz.org/)

### Leveling Principle:

In linear programming logistics models, the leveling principle refers to the need to balance supply and demand in the model. This means that the total amount of goods or products shipped from the origins must equal the total amount of goods or products received at the destinations.

When to Use Dummy Elements?

Dummy elements are used when supply and demand are not balanced in the transportation model. A dummy origin or destination is introduced to absorb excess supply or demand, respectively.

1. **Excess Supply:** If total supply is greater than total demand, a dummy destination is created. Transportation costs to this dummy destination are set to zero, as it does not represent a real destination.
2. **Excess Demand:** If total demand is greater than total supply, a dummy origin is created. Transportation costs from this dummy origin are set to zero.

#### Transportation Problem Example Using Pulp[#](broken-reference/)

Imagine a transportation problem with two origins (O1 and O2) and three destinations (D1, D2, and D3). The supply at O1 is 100 units, and the demand at O2 is 150 units. The demand at D1 is 80 units, the demand at D2 is 100 units, and the demand at D3 is 70 units.

In this case, the total supply (250 units) is greater than the total demand (250 units). To level the model, a fictitious destination (DF) with a demand of 0 units is introduced. The transportation costs from O1 and O2 to DF are set to zero.

```python
import pulp

# Create the problem
prob = pulp.LpProblem("Transportation Problem", pulp.LpMinimize)

# Define the origins and destinations
origins = ["O1", "O2"]
destinations = ["D1", "D2", "D3", "DF"] # DF is the fictitious destination

# Supply for each origin
supply = {"O1": 100, "O2": 150}

# Demand for each destination
demand = {"D1": 80, "D2": 100, "D3": 70, "DF": 0}

# Transportation costs (must be defined according to the problem)
costs = {
("O1", "D1"): 10,
("O1", "D2"): 2,
("O1", "D3"): 20,
("O1", "DF"): 0, # Zero cost for the fictitious destination
("O2", "D1"): 12,
("O2", "D2"): 7,
("O2", "D3"): 15,
("O2", "DF"): 0, # Zero cost for the fictitious destination
}

# Decision variables
routes = [(o, d) for o in origins for d in destinations]
x = pulp.LpVariable.dicts("route", routes, lowBound=0, cat='Integer')

# Objective function: Minimize total transportation cost
prob += pulp.lpSum([x[r] * costs[r] for r in routes])

# Constraints
# 1. Respect the offer of each origin
for o in origins:
probab += pulp.lpSum([x[(o, d)] for d in destinations]) <= supply[o]

# 2. Satisfy the demand for each destination
for d in destinations:
prob += pulp.lpSum([x[(o, d)] for o in origins]) >= demand[d]

# Solve the problem
prob.solve()

# Print the results
print("Status:", pulp.LpStatus[prob.status])
for v in prob.variables():
if v.varValue > 0:
print(v.name, "=", v.varValue)

print("Total cost =", pulp.value(prob.objective))
```

The values remaining in the fictitious elements in the solution to a transportation problem represent the difference between supply and demand.

1. **Fictitious Destination:** If in the optimal solution there is a positive value on a route to the fictitious destination, it means there is excess supply at the corresponding origin. The value indicates the number of units that are not shipped to any real destination.
2. **Fictitious Origin:** If in the optimal solution there is a positive value on a route from the fictitious origin, it means there is excess demand at the corresponding destination. The value indicates the number of demand units that cannot be satisfied with the available supply.

### **Definition of the Transportation Model:**[#](broken-reference/)

It involves finding a minimum-cost plan for transporting a good from multiple origins to multiple destinations. This model can be extended to solve numerous non-transportation applications within problems such as inventory control, cash flow, and resource allocation.

Transport Algorithm is an adaptation of the Simplex method applied to the particular case or structure of the associated Linear Programming model. Although the model for this problem can be solved using the Simplex method, its special structure makes it possible to use a special procedure.

```python
import networkx as nx
import matplotlib.pyplot as plt

# Create a directed graph
G = nx.DiGraph()

# Define the sources and destinations
sources = ['P_1', 'P_2', 'P_3', 'P_4']
destinations = ['C_1', 'C_2', 'C_3', 'C_4']

# Add nodes to the graph with the bipartite property
G.add_nodes_from(sources, bipartite=0) # Assign bipartite=0 to the sources
G.add_nodes_from(destinations, bipartite=1) # Assign bipartite=1 to the destinations

# Add edges from each source to each destination
for source in sources:
for destination in destinations:
G.add_edge(source, destination)

# Bipartite positioning
pos = {}
# Sources on the left
pos.update((n, (0, i)) for i, n in enumerate(sources))
# Destinations on the right
pos.update((n, (1, i)) for i, n in enumerate(destinations))

# Draw the graph with nodes and edges
nx.draw(G, pos, with_labels=True, node_size=3000, node_color='skyblue', font_size=12, font_weight='bold', arrows=True)
plt.title("Transportation Network: Sources on the left and Destinations on the right")
plt.show()
```

```python
import networkx as nx
import matplotlib.pyplot as plt
# directed graph
G = nx.DiGraph()
# Define sources and destinations
sources = ['P_1', 'P_2', 'P_3', 'P_4']
destinations = ['C_1', 'C_2', 'C_3', 'C_4']
# Define transportation costs (e.g., distances or costs)
costs = {
('P_1', 'C_1'): 4, ('P_1', 'C_2'): 2, ('P_1', 'C_3'): 5, ('P_1', 'C_4'): 7,
('P_2', 'C_1'): 3, ('P_2', 'C_2'): 6, ('P_2', 'C_3'): 1, ('P_2', 'C_4'): 4,
('P_3', 'C_1'): 7, ('P_3', 'C_2'): 3, ('P_3', 'C_3'): 6, ('P_3', 'C_4'): 5,
('P_4', 'C_1'): 4, ('P_4', 'C_2'): 5, ('P_4', 'C_3'): 3, ('P_4', 'C_4'): 2
}
# Add edges to the graph with costs as weight attributes
for (source, destination), cost in costs.items():
G.add_edge(source, destination, weight=cost)

# Bipartite positioning so that sources are on the right and destinations are on the left
pos = {}
# Sources on the right (x=1)
pos.update((source, (0, i)) for i, source in enumerate(sources))
# Destinations on the left (x=0)
pos.update((destination, (1, i)) for i, destination in enumerate(destinations))

# Draw the graph
plt.figure(figsize=(8, 6)) # Adjust the graph size
nx.draw(G, pos, with_labels=True, node_size=3000, node_color='skyblue', font_size=12, font_weight='bold', arrows=True)

# Add labels with edge weights
labels = nx.get_edge_attributes(G, 'weight')
nx.draw_networkx_edge_labels(G, pos, edge_labels=labels)

# Display the graph
plt.title("Transportation Network: Sources and Destinations with Costs" Transport")
plt.show()
```

1- To solve these optimization problems, we will use the pulp library.

* You must install it since it doesn't come pre-installed in COlab.
* [https://www.youtube.com/watch?v=Dq59G8Uf-\_o](https://www.youtube.com/watch?v=Dq59G8Uf-_o)
* [https://pypi.org/project/PuLP/](https://pypi.org/project/PuLP/)
