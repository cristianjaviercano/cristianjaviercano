# Some Exercises

### Context

The Cano company is dedicated to the distribution of food products in a specific region. It has 5 suppliers and 9 customers who must be served with certain demands and supply limitations.

### Logical Diagram of the Problem

1. Suppliers: P1, P2, P3, P4, P5
2. Customers: C1, C2, C3, C4, C5, C6, C7, C8, C9
3. Variables:
   * Supply from each supplier
   * Demand from each customer
4. Transportation costs between each supplier and customer
5. Objective: Minimize the total transportation cost

### Question to Solve

How can the Cano company minimize the total transportation cost when distributing its products from suppliers to customers while satisfying customer demands and respecting supplier limitations?

### Additional Data

| Supplier | Supply (units) |
| -------- | -------------- |
| P1       | 100            |
| P2       | 200            |
| P3       | 150            |
| P4       | 180            |
| P5       | 170            |

| Customer | Demand (units) |
| -------- | -------------- |
| C1       | 60             |
| C2       | 80             |
| C3       | 90             |
| C4       | 70             |
| C5       | 110            |
| C6       | 100            |
| C7       | 50             |
| C8       | 75             |
| C9       | 55             |

| Supplier/Customer | C1 | C2 | C3 | C4 | C5 | C6 | C7 | C8 | C9 |
| ----------------- | -- | -- | -- | -- | -- | -- | -- | -- | -- |
| P1                | 4  | 6  | 8  | 5  | 9  | 7  | 3  | 5  | 6  |
| P2                | 5  | 3  | 6  | 4  | 2  | 3  | 5  | 9  | 7  |
| P3                | 8  | 7  | 4  | 3  | 6  | 5  | 2  | 6  | 4  |
| P4                | 7  | 4  | 5  | 6  | 3  | 7  | 4  | 2  | 8  |
| P5                | 6  | 5  | 7  | 9  | 8  | 6  | 3  | 4  | 5  |

> #### Invitation:
>
> We invite students to design a solution for this problem using Python, employing the PuLP library to model and solve the transportation problem.

***

### Exercise Number 2

### Exercise Design: Capacitated Vehicle Routing Problem (CVRP)

### Exercise: Capacitated Vehicle Routing Problem (CVRP)

#### Problem Context

A logistics company has a fleet of trucks for distributing products to its customers. Each truck has a maximum load capacity and must visit multiple customers to fulfill their demands.

#### Problem Data

* **Customers**:

| Customer | Demand (units) |
| -------- | -------------- |
| C1       | 10             |
| C2       | 15             |
| C3       | 20             |
| C4       | 10             |
| C5       | 25             |

* **Trucks**:
  * Truck 1: Capacity 30 units
  * Truck 2: Capacity 40 units
* **Transportation Costs**: The cost matrix indicates the cost of transporting units between the warehouse and the customers, and between the customers themselves.

| Origin/Destination | Warehouse | C1 | C2 | C3 | C4 | C5 |
| ------------------ | --------- | -- | -- | -- | -- | -- |
| Warehouse          | 0         | 4  | 6  | 8  | 5  | 7  |
| C1                 | 4         | 0  | 2  | 4  | 3  | 6  |
| C2                 | 6         | 2  | 0  | 2  | 5  | 3  |
| C3                 | 8         | 4  | 2  | 0  | 3  | 4  |
| C4                 | 5         | 3  | 5  | 3  | 0  | 7  |
| C5                 | 7         | 6  | 3  | 4  | 7  | 0  |

#### Challenge

Model and solve this routing problem using the PuLP library in Python. The objective is to find the optimal route for each truck, minimizing the total transportation cost while respecting the load capacities and demands.
