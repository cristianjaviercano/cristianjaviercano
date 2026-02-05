# TSP problems

### Travelling Salesman Problem (TSP)

The Travelling Salesman Problem (TSP) is a classic optimization problem in computer science and operations research. The goal is to determine the shortest possible route that visits a set of cities, with each city visited exactly once, and then returns to the origin city. TSP is an NP-hard problem, making it computationally challenging as the number of cities increases. Various algorithms, such as dynamic programming, genetic algorithms, and heuristic methods, are employed to find approximate solutions for larger instances.

In a TSP model, the following elements are defined:

"Cities" (Nodes/Vertices): These represent distinct locations that must be visited. In a graph representation, these are the nodes or vertices.

"Distances" (Edges/Routes/Costs): These represent the cost or time associated with traveling directly between two cities. These are often given in a distance matrix, where `dij` is the distance from city `i` to city `j`.&#x20;

Distances can be symmetric (where `dij = dji`) or asymmetric (where `dij ≠ dji`).&#x20;

The goal is to minimize the total length of the round trip.

"Salesman" (Agent/Vehicle): This is the entity that travels between the cities.



The problem's primary goal is to determine a sequence of visits (a "tour" or "Hamiltonian cycle") that starts at an origin city, visits every other city exactly once, and then returns to the origin city, all while minimizing the total accumulated distance or cost.

### Mathematical Model of TSP

The TSP can be formulated as a mixed-integer linear programming (MILP) problem.

Decision Variables:   &#x20;

◦ $$x_ij$$ is a binary variable:       &#x20;

▪ $$x_{ij} = 1$$ if the route is taken from city `i` to city `j`.       &#x20;

▪ $$x_{ij} = 1$$ otherwise.   &#x20;

◦ A high penalty (`M`) is assigned to diagonal elements of the distance matrix to prohibit connecting a city to itself, effectively removing $$x_{ii}$$ from the model.

Objective Function:   &#x20;

◦ Minimize the total cost or distance of the tour: $$Z_{min} = Σ Σ (d_{ij} * x_{ij})$$ for all cities `i` and `j`. Where $$d_{ij}$$ is the cost/distance of traveling from city `i` to city `j`.

• Constraints:   &#x20;

**1. Visit Each City Exactly Once (Inflow):**&#x20;

The salesman must arrive at each city exactly once.&#x20;

$$Σ x_{ij} = 1$$ for each city `j`.   &#x20;

2\. Leave Each City Exactly Once (Outflow):&#x20;

The salesman must depart from each city exactly once.

&#x20;$$Σx_ij = 1$$ for each city `i`.   &#x20;

3\. Subtour Elimination Constraints:&#x20;

These are crucial and complex. Without them, the first two constraints might result in multiple disconnected cycles (subtours) instead of a single, continuous tour that visits all cities.&#x20;

A common way to implement these uses additional variables $$u_i$$ (sequence or flow variables) to ensure a single, continuous tour. One formulation is:&#x20;

$$
u_i - u_j + n * x_{ij} <= n - 1 \ for\  all\ i ≠ j,
$$

where `i` and `j` are not the origin city, and `n` is the total number of cities&#x20;

These ensure that if a path is taken from `i` to `j`, `j` must appear later in the sequence than `i` (except for the return to origin), preventing closed loops among a subset of cities \[.  &#x20;

4\. Binary Variables: $$x_{ij}$$ must be 0 or 1.

Assuming the Traveling Salesman Problem (TSP) formulation where additional variables ( u\_i ) are used to prevent sub-tours, an example of setting these variables could be:



### Applications and Examples of TSP<br>

The versatility of the TSP model allows it to represent various practical situations beyond just a "salesman" visiting "cities". Examples include:

1. Order Picking in a Warehouse:&#x20;
   1. This is a direct application where the "cities" are the locations of items in a warehouse that need to be picked for an order, and the "salesman" is the order picker. The "distances" are the travel times or physical distances between these locations
2. Vehicle Routing Problems (VRP):&#x20;
   1. TSP is a fundamental building block for more complex VRPs, which are often closer to real-world logistics applications. VRPs can include additional constraints such as time windows, multiple depots, vehicle capacities, or pick-up and delivery requirements
3. Scheduling Maintenance Visits:&#x20;
   1. A service center that schedules daily maintenance visits to customers can model this as a TSP. Each customer location is a "city," and the travel time between them is the "distance"
4. Sequencing Production Lots:&#x20;
   1. In a paint production company, if facilities must be cleaned between different paint lots, each color can be a "city," and the cleaning time between two successive colors is the "distance." The goal is to determine the optimal sequence of colors to minimize total cleaning time
5. Automated Guided Vehicles (AGVs):&#x20;
   1. An AGV performing a round trip to deliver mail or parts to departments on a factory floor can use TSP to minimize the total length of its journey, considering horizontal and vertical aisles
6. Drilling Operations:&#x20;
   1. In manufacturing circuit boards, a drilling machine needs to visit a sequence of holes. Each hole is a "city," and the travel time between holes is the "distance." The objective is to find the optimal drilling path to maximize production rate.
7. Waste Collection:&#x20;
   1. The process of collecting waste involves constructing collection routes to minimize costs and ensure efficiency and safety. Each collection point is a "city," and the goal is to optimize the routing of collection vehicles
8. Cutting Stock Problems:&#x20;
   1. Minimizing waste when cutting large sheets of material can be modeled by defining the cuts as "cities" and the resulting waste as "distances"
9. Touring Tourist Sites:&#x20;
   1. A tourist planning to visit multiple sites with a budget for taxi costs can define each site as a "city" and the taxi fare between them as the "distance"
10. Manager Meetings:&#x20;
    1. A manager needing to meet with multiple employees working on shared projects can use TSP to schedule group meetings, defining projects as "cities" and the "traffic" (number of distinct employees entering/leaving the meeting room) when switching projects as the "distance"
11. Surveillance Mission Planning:&#x20;
    1. Planning missions for synthetic aperture radar surveillance can be adapted as a TSP.
12. Precedence-Constrained TSP (PCTSP):&#x20;
    1. This variant applies when certain nodes must be visited before others. Applications include public transport scheduling and circuit board assembly
13. TSP with Time Windows (TSPTW):&#x20;
    1. Here, service at each customer must start within a given time window. Waiting times are generally permitted

### Methods for Solving TSP

These methods guarantee finding the optimal solution but can be computationally intensive:

1. Branch-and-Bound (B\&B):&#x20;
   1. This algorithm explores a search tree by systematically dividing the problem into smaller subproblems (branching) and using lower bounds to prune branches that cannot lead to a better solution than the current best (bounding). The process starts by solving an associated assignment problem to get a lower bound, and if it results in subtours, additional constraints are added
2. Cutting-Plane Algorithm:&#x20;
   1. This method starts by solving a relaxed version of the problem (e.g., as a linear program) and iteratively adds "cuts" (constraints) to eliminate non-integer or subtour solutions, pushing towards an optimal integer solution. The size of the resulting MILP can grow exponentially, making it computationally challenging

### Heuristics and Metaheuristics

These methods aim to find "good" or "high-quality" solutions within a reasonable amount of time, though they do not guarantee optimality. They are particularly useful for larger instances where exact methods are infeasible.

1. Local Search Heuristics: These algorithms start with an initial tour and iteratively make small changes to improve it until no further improvements can be found in the immediate neighborhood, often ending in a local optimum

* _Nearest Neighbor Heuristic:_ Constructs a tour by always moving to the nearest unvisited city from the current city.
* _Inversion Heuristic:_ Improves a tour by reversing a segment of the current tour if it reduces the total length

2. Metaheuristics: These are higher-level strategies designed to escape local optima and explore the search space more effectively

* _Tabu Search:_ Explores the search space by allowing "inferior" moves to avoid local optima and uses a "tabu list" to prevent revisiting recently explored solutions for a certain number of iterations
* _Simulated Annealing:_ Inspired by the annealing process in metallurgy, it accepts worse solutions with a certain probability (which decreases over time, like temperature) to escape local optima
* _Genetic Algorithms:_ Based on biological evolution, these algorithms maintain a population of solutions (tours), apply genetic operators like crossover and mutation to create new solutions, and select the fittest ones over generations

### Using Excel Solver for TSP

Excel Solver can be used to solve optimization problems, including linear and integer programming.&#x20;

For TSP, it can be attractive due to its familiarity \[from previous conversation].\
To set up a TSP model in Excel Solver:

1. Data Setup: Create a matrix of distances/costs between all locations. Also, create a matrix for the binary decision variables (`xij`) where Solver will write the 0s and 1s
2. Objective Function: Use `SUMPRODUCT` to calculate the total cost (sum of `dij * xij`)
3. Constraints:
   1. Ensure each row and column of the `xij` matrix sums to 1 (to ensure each city is entered and left once) \[from previous conversation].   &#x20;
   2. Declare the `xij` variables as binary    &#x20;
   3. The most challenging aspect is implementing the subtour elimination constraints.&#x20;

For small problems (e.g., less than 10-15 cities), these might be added iteratively if subtours are detected. However, for larger problems, this becomes very difficult and often impractical in Excel Solver without significant "ingenuity" or external programming

{% hint style="warning" %}
For larger or more complex TSP instances, specialized optimization software (like AMPL or TORA) or dedicated Excel templates for metaheuristics are generally recommended over Excel Solver for exact solutions
{% endhint %}

#### Example of a TSP Problem

Consider a scenario where a salesperson needs to visit 5 cities: A, B, C, D, and E. The distances between each pair of cities are given in the matrix below:

|   | A  | B  | C  | D  | E  |
| - | -- | -- | -- | -- | -- |
| A | 0  | 10 | 15 | 20 | 25 |
| B | 10 | 0  | 35 | 25 | 30 |
| C | 15 | 35 | 0  | 30 | 15 |
| D | 20 | 25 | 30 | 0  | 20 |
| E | 25 | 30 | 15 | 20 | 0  |

The objective is to find the shortest route, starting and ending at city A, visiting each of the other cities exactly once. A possible solution could be the route A -> B -> D -> E -> C -> A, with a total distance of 95 units. Finding such a solution illustrates the complexity and computational demand typical of TSP scenarios.

***

#### Applying TSP in a Warehouse for Optimizing Forklift Movements

In a warehouse setting, applying the Traveling Salesman Problem (TSP) can significantly improve the efficiency of forklift operations. By optimizing the route for forklifts, it helps reduce travel time and fuel consumption while increasing productivity. Here's a basic approach:

1. **Identify Stops**: Determine all locations (e.g., pick-up, drop-off points) the forklift needs to visit.
2. **Map Distances**: Create a distance matrix similar to the one used in the TSP problem to represent the distances between each pair of locations.
3. **Apply TSP Algorithm**: Use a TSP-solving algorithm (like the nearest neighbor, genetic algorithm, or dynamic programming) to compute the optimal route.
4. **Implement the Route**: Direct forklift operators to follow the optimized route to minimize travel distance and improve efficiency.
5. **Monitor and Adjust**: Continuously monitor the routes and adjust based on real-time data to adapt to changing warehouse conditions.

By integrating TSP solutions for guiding forklifts, warehouses can achieve more streamlined and cost-effective logistics operations.

***

In the context of a DC or warehouse with forklift operations, the elements of the TSP are mapped as follows.

### "Cities" (Nodes/Vertices):&#x20;

_Represent the specific locations within the warehouse that must be visited. This can include:_

1. Stock picking points for orders.
2. Delivery points or packing stations.
3. Storage or replenishment areas.
4. The forklift's base or "depot," where it begins and ends its shift or a task.

### "Distances" (Edges/Routes/Costs):&#x20;

Represent the time or cost associated with direct travel between two locations within the warehouse.&#x20;

These distances can be symmetric (the cost of going from A to B is equal to B to A) or asymmetric (different costs due to one-way aisles, congestion, or internal traffic).<br>

### "Traveling Salesman" (Entity/Vehicle):&#x20;

This is the forklift that performs the route, responsible for picking up and delivering materials.

{% hint style="danger" %}
The objective is to minimize the total travel time (or total cost, which may include fuel, maintenance, or operator time) for the forklift to complete all assigned tasks, visiting each required pick-up/delivery point once and returning to its base.<br>
{% endhint %}

#### Example of TSP in a CEDI with a Forklift<br>

Consider a CEDI where a single forklift is responsible for fulfilling a large order that requires picking items from four different storage locations (L1, L2, L3, L4). The forklift starts its shift from its charging base (B) and must return to it after completing all picks. The goal is to find the most efficient route to minimize the total travel time.

1.  Define the "Cities" (Nodes) &#x20;

    1. B: Forklift Charging Base (Start and End Point)   &#x20;
    2. L1: Picking Location 1   &#x20;
    3. L2: Picking Location 2   &#x20;
    4. L3: Picking Location 3   &#x20;
    5. L4: Picking Location 4


2.  Define the "Distances" (Travel Times in Minutes):&#x20;

    1. The travel time between any two locations is measured in minutes. For simplicity, we assume symmetric travel times (e.g., time from B to L1 is the same as L1 to B)


3. _Self-loops (e.g., B to B) are typically excluded or given a very high penalty, as the forklift must visit distinct locations._
