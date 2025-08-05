# TSP problem

#### Traveling Salesman Problem (TSP)

The Traveling Salesman Problem (TSP) is a classic optimization problem focused on finding the shortest possible route for a traveler to visit a set of cities and return to the origin city. The key challenge is:

1. **Unique Tour:**\
   Each city must be visited exactly once.

TSP is commonly used in logistics, manufacturing, and transportation to optimize travel routes and reduce costs.

#### Problem Description

Given a set of cities and the distances between each pair of them, the goal is to find a sequence of visits that minimizes the total distance traveled. This problem can be visualized as a closed circuit:

1. **Unique Route:**\
   Each city must be visited exactly once.
2. **Closed Circuit:**\
   The route must start and end in the same origin city.
3. **Distance Minimization:**\
   The sum of all distances between the visited cities must be as small as possible.

#### Example

Suppose we have five cities: A, B, C, D, and E. The task is to find the route that covers all the cities and returns to the initial city A, so that the sum of the distances between the cities is minimized.

#### Solution Methods

Some methods to solve the traveling salesman problem include:

* **Brute Force:** Evaluates all possible routes and selects the one with the shortest distance. This is practical for a small number of cities due to its factorial complexity.
* **Approximate Algorithms:** Such as ant colony search, genetic algorithms, or simulated annealing, which offer solutions close to optimal in reasonable time for large numbers of cities.
* **Dynamic Programming:** Uses the Held-Karp algorithm, which has a time complexity of 2^n * n^2, more efficient than brute force, though still exponential.

#### Practical Exercise: Solving the Traveler Problem with PuLP

In this exercise, students will use the PuLP library in Python to solve the traveling salesman problem (TSP). Through this exercise, students will model and solve the problem computationally.

**Instructions**

1.  **Introduction to the Problem:**

    Imagine you are a salesperson who must visit the following cities: City1, City2, City3, City4, and City5. The goal is to determine the route that minimizes the total distance traveled when visiting all the cities and returning to the initial city.

**Example Code**

```python
import pulp

# Definition of cities and distance matrix
cities = ['City1', 'City2', 'City3', 'City4', 'City5']
distances = {('City1', 'City2'): 10, ('City1', 'City3'): 15, ...}

# Define the problem
problem = pulp.LpProblem("TSP", pulp.LpMinimize)

# Decision variables
x = pulp.LpVariable.dicts('route', distances, cat='Binary')

# Objective function
problem += pulp.lpSum([distances[i] * x[i] for i in distances])

# Constraints
...

# Solving the problem
problem.solve()

# Results
print(f"Solver status: {pulp.LpStatus[problem.status]}")
print("Optimal route:")
for i in distances:
    if pulp.value(x[i]) == 1:
        print(f"Travel from {i[0]} to {i[1]}")

print(f"Total distance: {pulp.value(problem.objective)}")

Complete the code by implementing the constraints and share your results. This exercise will provide practical experience in combinatorial optimization and its application with computational tools.

***

{% hint style="info" %}

Tips to Implement the Constraints
{% endhint %}

Entry and Exit Constraint:
Each city must have exactly one entry and one exit. To achieve this, make sure that in each city, the sum of incoming and outgoing routes equals 1.

Routing Exercise in a Distribution Center (CEDI)
{% hint style="info" %}

What is a CEDI?
A Distribution Center, known as CEDI, is a logistics facility used by companies for receiving, storing, managing, and distributing products. Its main function is to optimize supply chain processes. {% endhint %}

Context for CRC Companies
In the context of CRC Companies, a routing exercise is proposed for a CEDI handling a single type of product. The company has three forklifts that facilitate the movement of goods within the facility.

The goal of this exercise is to determine the average service time or attention time inside the CEDI. This analysis will help CRC Companies optimize processes and resources, improving the efficiency of the distribution center.

The CEDI will have the following areas and characteristics:

Product: A single type of product.
Forklifts: Three forklifts.
Functional Areas:
Receiving Area (ARM): Location where the product is received.
Inspection Area (AI): Zone for quality and quantity verification of the product.
Forklift Parking Area (APM): Space designated for parking and recharging forklifts.
Dispatch Area (AD): Point where finished products or orders leave.
Storage Area (AA): Area designated for shelves for product storage.
Shelves:
Six shelves in total.
Each shelf will have 12 towers.
Each tower will have 3 levels.
Coordinate Identification: Shelf locations will be identified by coordinates (x, y, z).
II. Student Requirements
The student must complete the following tasks:

1. Warehouse Modeling in Excel and Determination of Coordinates

The first step is to build a warehouse model in a spreadsheet (Excel) to determine the coordinates of each area and each storage location.

General Coordinates: All areas (ARM, AI, APM, AD) will have a z coordinate = 1 meter, assuming their operations occur at ground level.
Storage Coordinates: For locations within the Storage Area (AA), coordinates (x, y) will be the same for a given tower, and the z coordinate will vary depending on the level:
Level 1: z = 1 meter.
Level 2: z = 2 meters.
Level 3: z = 3 meters.
Assume each unit change in z represents 1 meter.
2. Matrix of Possible Routes, Times, and Distances

Once all coordinates are defined, the student must build a matrix of distances and times between all relevant locations within the CEDI.

Euclidean Distance: The three-dimensional Euclidean distance can be used to calculate the distance between two points (x1, y1, z1) and (x2, y2, z2): d = sqrt((x2−x1)^2 + (y2−y1)^2 + (z2−z1)^2)
Average Forklift Speed: Assume an average forklift speed of 10 meters per second.
Time Calculation: The travel time between two points will be calculated as: t = distance / average forklift speed
Route Matrix: A matrix M will be generated where M_ij represents the time or distance traveled from location i to location j.
3. Demand Simulation and Generation of CSV File

Demand for orders and the location of items in the warehouse will be simulated, assuming the warehouse is initially full.

Initial Orders: The number of orders per simulation should be random, ranging from 1 to 5.
Items per Order: Each order will contain a random number of items, between 5 and 20.
Item Location: Each item in an order must be "located" at a specific coordinate within the Storage Area (AA). That is, it is assumed that these items must be picked from their storage location.
CSV File Generation: The simulated demand (orders, items, and their origin coordinates) must be exported to a .csv file. This file will serve as input for the routing model.
4. Formulation of the Vehicle Routing Problem with Capacities (VRPC)

The student must formulate a VRPC model that uses the generated .csv file as input.

Objective: Minimize the total travel time of the forklifts to fulfill the orders.
Decision Variables:
Binary variables indicating whether a forklift visits a location.
Binary variables indicating whether a route between two locations is taken.
Constraints:
Each order must be fulfilled.
Forklifts have limited capacity (for example, in number of items or volume, which the student must define).
Forklifts start and end their route in the Forklift Parking Area (APM).
Each forklift cannot exceed its maximum operation time.
Route continuity constraints.
III. Deliverables
The student must submit a report in PDF format containing:

Detailed explanation of each step taken.
Diagram or representation of the warehouse and its coordinates.
The distance and time matrix.
The logic of demand simulation.
The theoretical and algebraic formulation of the VRPC model, including all assumptions and additional considerations.
Analysis of the results obtained (if the VRPC solution is implemented).
Additionally, the complete code developed in Python using Jupyter Notebook or Google Colab must be attached. The code should include:

Generation of coordinates and the distance/time matrix.
Demand simulation and export to a .csv file.
Implementation of the VRPC model using an optimization library (e.g., PuLP, GurobiPy, OR-Tools).
Additional Considerations for Problem Design
Warehouse Layout: For modeling in Excel, a rectangular or grid layout can be assumed for the warehouse, which facilitates coordinate assignment.
Forklift Capacity: The capacity of the forklifts must be specified. For example, a forklift can transport a maximum of X items per trip.
Picking Strategy: An individual picking strategy per item will be assumed, i.e., each item has a specific location that must be visited.
Loading/Unloading Time: To simplify the initial model, a constant loading/unloading time per item or per order can be assumed, or ignored in a first approximation. The student may choose to include it later.
Operating Hours: Operating hours for the CEDI and forklifts can be established to include in the time constraints.
Traffic/Congestion: For this initial level, congestion in aisles or areas can be omitted, assuming smooth movements. If greater complexity is desired, congestion can be introduced.
This design provides a robust framework for students to apply concepts of facility design, logistics systems modeling, and optimization in a practical setting.

References for Further Information
Laporte, G. (1992). The vehicle routing problem: An overview of exact and approximate algorithms. European Journal of Operational Research, 59(2), 345-358.
Toth, P., & Vigo, D. (2014). Vehicle Routing: Problems, Methods, and Applications. Society for Industrial and Applied Mathematics.
Chopra, S., & Meindl, P. (2019). Supply Chain Management: Strategy, Planning, and Operation (7th ed.). Pearson.


#### Ejercicios Varios

Various Exercises

In example 1, suppose the capacity of the Detroit plant is 1300 cars (instead of 1500). The total supply (3700 cars) is less than the total demand (4300 cars), which means:
Solve this model using simplex by hand and then in Colab, compare the results.
Describe the code used.
A store produces three different products. The products are sent to three warehouses. The shipping costs per unit, supply, and demand for each distribution center are shown in the table:


|          | Store A | Store B | Store C | Offert |
| -------- | --------- | --------- | --------- | ------ |
| Store 1 | $10       | $8        | $7        | 200    |
| Store 2 | $5        | $12       | $6        | 300    |
| Store 3 | $4        | $7        | $11       | 400    |
| Demand  | 150       | 250       | 200       |        |

5. A company has three stores in different cities and two warehouses in other cities. Each store offers different products. The shipping costs per unit, production capacity, and demand for each warehouse are shown in the table:

|          | Warehouse A | Warehouse B | Warehouse C | Warehouse D | Offert |
| -------- | --------- | --------- | --------- | --------- | ------ |
| Store 1 | $4        | $6        | $9        | $5        | 300    |
| Store 2 | $7        | $3        | $5        | $8        | 400    |
| Store 3 | $2        | $5        | $11       | $7        | 500    |
| Demand  | 400       | 400       | 300       | 300       |        |

6. A company has three stores and four warehouses. The shipping costs per unit, production capacity, and demand for each warehouse are shown in the tables below. Determine the optimal shipping and cost:

|          | Wharehouse A | Wharehouse B | Wharehouse C | Wharehouse D | Wharehouse E | Offert|
| -------- | --------- | --------- | --------- | --------- | --------- | ------ |
| Store 1 | $6        | $8        | $10       | $9        | $7        | 500    |
| Store 2 | $5        | $11       | $7        | $4        | $3        | 400    |
| Store 3 | $12       | $9        | $3        | $8        | $6        | 300    |
| Demand  | 300       | 400       | 400       | 200       | 400       |        |

```
   1. Formulate the theoretical and algebraic linear programming model.
    2. Formulate this problem as a transportation problem by constructing the appropriate parameter table.
    3. Get an optimal solution for this problem.
    4. Do the exercise in Colab and vary different values.
```

7. Three cities are supplied with electricity from three power plants with capacities of 25, 40, and 30 megawatts (MW). The maximum demands in the three cities are estimated at 30, 35, and 25 MW. The price per MW supplied from each plant to each city is:

| Plant\City | C\_1 | C\_2 | C\_3 |
| -------------- | ---- | ---- | ---- |
| P\_1           | 600  | 700  | 400  |
| P\_2           | 320  | 300  | 350  |
| P\_3           | 500  | 480  | 450  |

During August, there is a 20% increase in demand for each city, which can be met by purchasing electricity from another network, at a high rate of $1000 per MW. However, the network is not unlimited.

```
1. Formulate the problem as a transportation model. In Colab using latex.
2. Solve the problem with Colab and determine an optimal distribution plan for the power company.
3. Determine the cost of additional electricity purchased by each of the three cities.
```

8. The ABC Company has three baby product manufacturing plants that must be distributed to four distribution centers. Plants 1, 2, and 3 produce 12, 17, and 11 shipments per month, respectively. The shipping costs for each plant to each distribution center are:

|          | CEDI 1 | CEDI 2 | CEDI 3 | CEDI 4 |
| -------- | ------ | ------ | ------ | ------ |
| plant 1 | 800    | 13000  | 400    | 700    |
| plant 2 | 1100   | 14000  | 600    | 1000   |
| plant 3 | 600    | 1200   | 800    | 900    |

* The shipping cost for each shipment is $100 plus $0.50 per mile.
How much should be shipped to each distribution center to minimize the total shipping cost?

```
1. Formulate the problem as a transportation model by preparing the appropriate parameter table.
2. Draw the network representation of this problem.
3. Get an optimal solution.
```

9. Tom wants to buy exactly 3 liters of homemade beer today and at least 4 liters tomorrow. Dick wants to sell a maximum of 5 liters in total at a price of $3.00 per liter today and $2.70 per liter tomorrow.

Tom wants to know how much he should buy from each to minimize his cost and still meet the minimum requirements to satisfy his thirst.

```
   1. Formulate the theoretical and algebraic linear programming model.
    2. Formulate this problem as a transportation problem by constructing the appropriate parameter table.
    3. Get an optimal solution for this problem. \
```

10. Versatech Corporation will produce three new products. At this time, five of its plants have excess production capacity. The respective unit manufacturing cost for the first product at each plant is: \\

11. Plants 1, 2, 3, 4, and 5 have capacities to produce 400, 600, 400, 600, and 1,000 units per day, regardless of the product or product mix. Suppose any plant that has the capacity can manufacture any of the products.

Formulate this problem as a transportation problem by constructing the appropriate parameter table.
Get an optimal solution for this problem.
Do this exercise in Google Colab using latex and code. \\

12. XYZ company produces 2 products \(X_1\) and \(X_2\) in two different plants \(Pl_1\) and \(Pl_2\). Each product requires different raw materials for its production:

|      | Mp1 | Mp2 | Mp3 | Tiempo de Prod     |
| ---- | --- | --- | --- | ------------------ |
| X\_1 | 2   | 3   | 1   | $$4\frac{min}{u}$$ |
| X\_2 | 3   | 1   | 0   | $$3\frac{min}{u}$$ |

The company has 5 suppliers:

|      | Mp\_1 | Mp\_2 | Mp\_3 |
| ---- | ----- | ----- | ----- |
| S\_1 | 1000  | 800   | 1000  |
| S\_2 | 4000  | 2000  | -     |
| S\_3 | -     | 9000  | 2000  |
| S\_4 | 5000  | 3000  | 900   |
| S\_5 | 2000  | 4000  | 1000  |

Shipping costs per unit (u/usd):

|      | CtMp\_1 | CtMp\_2 | CtMp\_3 |
| ---- | ------- | ------- | ------- |
| S\_1 | 2       | 2       | 3       |
| S\_2 | 2       | 2,5     | -       |
| S\_3 | -       | 3       | 1       |
| S\_4 | 4       | 2       | 4       |
| S\_5 | 2       | 2,2     | 2       |

Fixed cost per supplier:

|      | Costo fijo |
| ---- | ---------- |
| S\_1 | 90 usd     |
| S\_2 | 110 usd    |
| S\_3 | 85 usd     |
| S\_4 | 97 usd     |
| S\_5 | 60 usd     |

|      | Costo variable |
| ---- | -------------- |
| S\_1 | 0,5 usd        |
| S\_2 | 0,8 usd        |
| S\_3 | 0,7 usd        |
| S\_4 | 0,2 usd        |
| S\_5 | 0,6 usd        |

Distance from plants to suppliers:

|      | Plp\_1 | Plp\_2 |
| ---- | ------ | ------ |
| S\_1 | 70     | 92     |
| S\_2 | 67     | 92     |
| S\_3 | 85     | 83     |
| S\_4 | 70     | 72     |
| S\_5 | 90     | 94     |

1. Find the optimal model to reduce costs and meet demand.
2. You must balance the system by finding the demand units according to system capacities.
3. Do this exercise in Google Colab and model your answer.

```
1. Find the optimal model that minimizes system cost.
2. Balance the system based on supply.
3. Do this exercise in Google Colab.
```

#### Exercise number 6 from the book "Hamdy Taha - Operations Research Chapter 5"

Three cities are supplied with electricity from three power plants with capacities of 25, 40, and 30 megawatts. The maximum demands in the three cities are estimated at 30, 35, and 25 megawatts. The price per MW supplied from each plant to each city is:



|        |     | Ciudad |     |
| ------ | --- | ------ | --- |
| Planta | 1   | 2      | 3   |
| 1      | 600 | 700    | 400 |
| 2      | 320 | 300    | 350 |
| 3      | 500 | 480    | 450 |

*During August, there is a 20% increase in demand for each city, which can be met by purchasing electricity from another network, at a high rate of $100 per watt, but the network is not unlimited.

1. Formulate the problem as a transportation model.
2. Solve the problem and determine an optimal distribution plan for the company.
3. Determine the cost of electricity purchased by each of the cities.

***
