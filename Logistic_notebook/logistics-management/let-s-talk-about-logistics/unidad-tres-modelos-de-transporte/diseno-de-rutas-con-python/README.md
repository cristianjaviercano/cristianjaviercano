# Route Desing Using Python

Linear programming is a mathematical technique used to optimize a linear objective, subject to linear constraints. In route design, it allows you to model and solve problems that seek to minimize costs or total travel time while respecting capacity and time constraints. This technique helps determine the best combination of decision variables such as routes to be taken, number of vehicles, and delivery sequence, ensuring that resources are used efficiently and effectively.

Route optimization represents one of the most common challenges in logistics operations management. Mathematical models provide a systematic framework for addressing these problems, enabling more informed and efficient decision-making. Some of the most commonly used models are described below.

**Programming Model for Solving Routing Problems**

Routing problems are common challenges in transportation and logistics optimization. These problems may involve finding the most efficient route to deliver goods, planning travel itineraries, or minimizing transportation costs. An effective approach to addressing these problems is the use of programming models.

#### Types of Routing Problems

1. **Traveling Salesman Problem (TSP)**: Seeks to determine the shortest route that allows a set of cities to be visited only once and return to the starting point.
2. **Vehicle Routing Problem (VRP)**: Focuses on finding optimal routes for a fleet of vehicles that must meet a series of demands from a central depot.
3. **Delivery and Collection Routing Problems**: Involves not only the delivery of goods but also the collection of products or packaging for recycling.

#### Programming Models Used

**Programming Model for Solving Routing Problems**

Routing problems are common challenges in transportation and logistics optimization. These problems may involve finding the most efficient route to deliver goods, planning travel itineraries, or minimizing transportation costs. An effective approach to addressing these problems is the use of programming models.

#### Types of Routing Problems

1. **Traveling Salesman Problem (TSP)**: Seeks to determine the shortest route that allows a set of cities to be visited only once and return to the starting point.
2. **Vehicle Routing Problem (VRP)**: Focuses on finding optimal routes for a fleet of vehicles that must meet a series of demands from a central depot.
3. **Delivery and Collection Routing Problems**: Involves not only the delivery of goods but also the collection of products or packaging for recycling.

#### Programming Models Used

Programming models for routing problems have a wide range of practical applications, including:

* Route optimization in online shopping delivery services.
* Efficient route planning for public transportation services.
* Distribution logistics management in supply chains.

### Route Design with Python

Route planning focuses on designing optimal routes for delivering products or achieving system objectives, considering:

1. Time
2. Cost
3. Capacity constraints

**Objective of Designing a Route**

The objective can be:

1. Minimize costs
2. Optimize delivery times
3. Improve resource utilization

***

### ROUTE DESIGN USING PYTHON.[#](../../../../logistics/let-s-talk-about-logistics/unidad-tres-modelos-de-transporte/diseno-de-rutas-con-python/broken-reference/)

There are numerous libraries and algorithms available that simplify the route design process in Python. These tools are used to optimize and plan efficient routes in various applications, such as vehicle fleet management, freight delivery, trip planning, and many others.

Notable libraries include NetworkX, which provides data structures and algorithms for graph and network analysis. There is also GeoPandas, which extends Pandas' capabilities by allowing the handling and analysis of geospatial data. Another popular option is OSRM (Open Source Routing Machine), which offers a server and client library for generating routes using OpenStreetMap data.

On the other hand, route optimization algorithms such as Dijkstra's algorithm, the A\* (A-star) algorithm, and metaheuristic optimization algorithms can be used to find optimal routes based on various constraints and costs. These algorithms are essential for applications requiring high efficiency in route planning.

{% hint style="info" %}
The Python ecosystem offers a variety of tools and techniques that allow the problem of route design to be addressed efficiently and effectively, adapting to the specific needs of each application. By leveraging these libraries and algorithms, developers can create advanced solutions in the field of route planning and optimization.
{% endhint %}

{% code overflow="wrap" %}
```markdown
Pulp: A library for solving optimization problems, including TSP and VRP.
```
{% endcode %}

Let's consider an example where we have a problem assigning tasks to workers, where each worker must perform a single task, and each task must be performed by a single worker. The objective function is to minimize the total cost of the assignment.

```python
!pip install Pulp
```

```python
import pulp

# Create the problem
prob = pulp.LpProblem("Task Assignment", pulp.LpMinimize)

# Define the variables
costs = [[10, 2, 20], [12, 7, 15], [8, 12, 5]]
workers = range(3)
tasks = range(3)
x = pulp.LpVariable.dicts("x", [(i, j) for i in workers for j in tasks], cat='Binary')

# Objective function
prob += pulp.lpSum(costs[i][j] * x[(i, j)] for i in workers for j in tasks)

# Constraints
for i in workers:
prob += pulp.lpSum(x[(i, j)] for j in tasks) == 1

for j in tasks:
prob += pulp.lpSum(x[(i, j)] for i in workers) == 1

# Solve the problem
prob.solve()

# Print the results
print("Status:", pulp.LpStatus[prob.status])
for v in prob.variables():
print(v.name, "=", v.varValue)

print("Total cost =", pulp.value(prob.objective))
```

#### Network Analysis Using NetworkX[#](../../../../logistics/let-s-talk-about-logistics/unidad-tres-modelos-de-transporte/diseno-de-rutas-con-python/broken-reference/)

**NetworkX** is a powerful and versatile Python library used for the creation, manipulation, and analysis of complex networks. Designed to facilitate the process of modeling graph structures, NetworkX finds applications in numerous fields such as network science, computational biology, engineering, social sciences, among others.

This library offers functionalities that enable detailed and accurate network analysis, including, but not limited to, finding shortest paths between nodes, which is essential in optimizing routes and transportation networks. Additionally, NetworkX is capable of detecting communities within a network, helping to identify clusters or modules that may represent entities with common characteristics or interests in a social or biological context.

Another notable feature is its ability to calculate various centrality metrics, such as degree, betweenness, and closeness centrality, which are crucial for determining the most influential or critical nodes within the network.

NetworkX's intuitive design and extensive documentation make it ideal for both researchers and practitioners looking to efficiently perform complex network analysis. Additionally, its compatibility with other Python libraries, such as Pandas and Matplotlib, enables seamless integration into broader data science workflows.

**Main Features:**[**#**](../../../../logistics/let-s-talk-about-logistics/unidad-tres-modelos-de-transporte/diseno-de-rutas-con-python/broken-reference/)

1. Graph Creation and Manipulation: Supports various graph types (directed, undirected, multigraphs) and allows adding nodes and edges with attributes.
2. Network Analysis: Provides a wide range of graph theory algorithms for performing structural analysis, such as calculating centralities (degree, betweenness, closeness), detecting connected components, shortest paths, community detection, etc.
3. Graph Types: Supports directed graphs (where connections are directed), undirected graphs, and multigraphs (where there can be multiple edges between two nodes).

```python
!pip install networkx==2.8.8
```

```python
import networkx as nx
import matplotlib.pyplot as plt

# Create a graph
G = nx.Graph()

# Add nodes and edges
G.add_edge(1, 2)
G.add_edge(2, 3)
G.add_edge(3, 4)

# Draw the graph
nx.draw(G, with_labels=True)
plt.show()
```

### Example 1:

MG Auto has three plants: in Los Angeles, Detroit, and New Orleans; and two main distribution centers in Denver and Miami. The capacities of the three plants during the next quarter will be 1,000, 1,500, and 1,200 cars. Quarterly demand at the two distribution centers is 2,300 and 1,400 cars. The mileage between the factories and the distribution centers

* The shipping company charges 8 cents per mile per car. The transportation cost per car, on the different routes, is rounded up to the nearest dollar.

TABLE 1

|             | Denver | Mimami |
| ----------- | ------ | ------ |
| Los Angeles | 1000   | 2690   |
| Detroit     | 1250   | 1350   |
| New Orleans | 1275   | 850    |

TABLE 2

|                | Denver(1) | Mimami(2) |
| -------------- | --------- | --------- |
| Los Angeles(1) | 80        | 215       |
| Detroit(2)     | 100       | 108       |
| New Orleans(3) | 102       | 68        |

**Solving:**

**Decision variables:**

* \\(x\_{ij}\\): Number of cars to be transported from plant \\(i\\) to distribution center \\(j\\).

**Objective function:**

* Minimize the total transportation cost, given by:

\\\[\text{Min } Z = 0.08 \sum\limits\_{i=1}^{3}\sum\limits\_{j=1}^{2}x\_{ij}d\_{ij}\\]

* Where \\(d\_{ij}\\) is the distance in kilometers between plant \\(i\\) and distribution center \\(j\\), according to Table 1.

**Constraints:**

* Plant capacity: $\\(\sum\limits\_{j=1}^{2}x\_{ij} \leq c\_i ∀\ i = 1, 2, 3\\)$
* Where \\(c\_i\\) is the capacity of plant \\(i\\).
* Distribution center demand: $\\(\sum\limits\_{i=1}^{3}x\_{ij} \geq d\_j\ ∀\ j = 1, 2\\)$
* Where \\(d\_j\\) is the demand of distribution center \\(j\\), according to the statement.
* Non-negativity constraints: $\\(x\_{ij} \geq 0\ ∀\ i = 1, 2, 3\ and\ j = 1, 2\\)$
* _Also, the decision variables must be integers, since fractions of cars cannot be transported._

**Solving with Python and the PuLp library:**[**#**](../../../../logistics/let-s-talk-about-logistics/unidad-tres-modelos-de-transporte/diseno-de-rutas-con-python/broken-reference/)

```python
import pulp

# Create a minimization problem
problem = pulp.LpProblem("Transportation", pulp.LpMinimize)

# Create the decision variables
x11 = pulp.LpVariable("Los Angeles to Denver", lowBound=0, cat='Integer')
x12 = pulp.LpVariable("Los Angeles to Miami", lowBound=0, cat='Integer')
x21 = pulp.LpVariable("Detroit to Denver", lowBound=0, cat='Integer')
x22 = pulp.LpVariable("Detroit to Miami", lowBound=0, cat='Integer')
x31 = pulp.LpVariable("New Orleans to Denver", lowBound=0, cat='Integer')
x32 = pulp.LpVariable("New Orleans to Miami", lowBound=0, cat='Integer')

# Define the objective function
problem += 0.08 * (1000*x11 + 2690*x12 + 1250*x21 + 1350*x22 + 1275*x31 + 850*x32)

# Define the supply and demand constraints
problem += x11 + x12 <= 2300, "Supply "Angeles"
problem += x21 + x22 <= 1500, "Detroit Offer"
problem += x31 + x32 <= 2000, "New Orleans Offer"
problem += x11 + x21 + x31 >= 2300, "Denver Lawsuit"
problem += x12 + x22 + x32 >= 1400, "Miami Lawsuit"

# Solve the problem
problem.solve()

# Print the result
print("Status:", pulp.LpStatus[problem.status])
print("Total transportation cost: $", round(pulp.value(problem.objective), 2))

for variable in problem.variables(): 
print(variable.name, "=", variable.varValue)
```

#### Example 2:

In this model, we have three origins (\\(O\_1\\), \\(O\_2\\), and \\(O\_3\\)) and four destinations (\\(D\_1\\), \\(D\_2\\), \\(D\_3\\), and \\(D\_4\\)), and the table shows the transportation costs from each origin to each destination. The objective is to determine the optimal allocation of products to destinations, minimizing the total transportation cost.

| ORIGEN     | \\(D\_1\\) | \\(D\_2\\) | \\(D\_3\\) | \\(D\_4\\) |
| ---------- | ---------- | ---------- | ---------- | ---------- |
| \\(O\_1\\) | 4          | 5          | 2          | 7          |
| \\(O\_2\\) | 3          | 6          | 8          | 2          |
| \\(O\_3\\) | 9          | 4          | 1          | 3          |

**Solving the model:**

The objective function of this model is expressed as:

\begin{equation\*} \text{minimize} Z = \sum\_{i=1}^{3}\sum\_{j=1}^{4}c\_{ij}x\_{ij} \end{equation\*}

Where:

\\(Z\\): represents the total transportation cost.

\\(c\_{ij}\\): is the cost of transporting a unit from origin \\(i\\) to destination \\(j\\).

\\(x\_{ij}\\): is the number of units transported from origin \\(i\\) to destination \\(j\\).

Capacity constraints are expressed as:

```markdown
\begin{align*} \sum_{j=1}^{4} x_{1j} &\leq 60
\sum_{j=1}^{4} x_{2j} &\leq 70
\sum_{j=1}^{4} x_{3j} &\leq 80 \end{align*}
```

**Where:**

The constraint \\(\sum\_{j=1}^{4} x\_{ij} \leq C\_i\\) indicates that the total quantity of products shipped from source \\(i\\) cannot exceed its maximum capacity \\(C\_i\\). Demand constraints are expressed as:

```markdown
\begin{align*} \sum_{i=1}^{3} x_{i1} &\geq 50
\sum_{i=1}^{3} x_{i2} &\geq 70
\sum_{i=1}^{3} x_{i3} &\geq 80
\sum_{i=1}^{3} x_{i4} &\geq 30 \end{align*}
```

**Where:**

* The constraint \\(\sum\_{i=1}^{3} x\_{ij} \geq D\_j\\) indicates that the total quantity of products shipped to destination \\(j\\) must be at least equal to its demand \\(D\_j\\)

```python
import pulp
```

```python
# Define the problem
problem = pulp.LpProblem("Transportation Problem", pulp.LpMinimize)

# Defines the decision variables
origins = ['O1', 'O2', 'O3']
destinations = ['D1', 'D2', 'D3', 'D4']
x = pulp.LpVariable.dicts('shipment', ((o, d) for o in origins for d in destinations), lowBound=0, cat='Integer')

# Defines the objects of the functions
costs = { 
('O1', 'D1'): 4, 
('O1', 'D2'): 5, 
('O1', 'D3'): 2, 
('O1', 'D4'): 7, 
('O2', 'D1'): 3, 
('O2', 'D2'): 6, 
('O2', 'D3'): 8, 
('O2', 'D4'): 2, 
('O3', 'D1'): 9, 
('O3', 'D2'): 4, 
('O3', 'D3'): 1, 
('O3', 'D4'): 3
}
problem += pulp.lpSum([costs[o, d] * x[o, d] for o in origins for d in destinations])

# Define the restrictions
for or in origins: 
problem += pulp.lpSum([x[o, d] for d in destinations]) == 1
for d in destinations: 
problem += pulp.lpSum([x[o, d] for o in origins]) == 1

# solve the problem
problem.solve()

# print the optimal solution
print("Optimal solution:")
for or in origins: 
for d in destinations: 
if x[o, d].value() > 0: 
print(f"Ship {x[o, d].value()} from {o} to {d}")
print(f"Total cost: {pulp.value(problem.objective)}");
```
