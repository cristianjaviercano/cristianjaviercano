# Network Model

### Network Model

***

Definition of networks: networks are a series of located nodes connected by arcs. The notation for describing the network is

$$
\begin{split} (N,A); \\ where: \\ N = Set\ of\ Nodes \\ A = Set\ of\ Arcs \end{split}\
$$

For example:

\\[\begin{split} N = \\{1,2,3,4,5\\} \\\ A = \\{(1,2),(1,3),(2,3),(2,5),(3,4),(3,5),(4,2),(4,5)\\} \end{split}\\]

```python
import networkx as nx
import matplotlib.pyplot as plt

G = nx.Graph()
G.add_nodes_from([1, 2, 3, 4, 5])

A = [(1,2),(1,3),(2,3),(2,5),(3,4),(3,5),(4,2),(4,5)]
G.add_edges_from(A)

labels = {1: 'A', 2: 'B', 3: 'C', 4: 'D', 5: 'E'}

pos = nx.spring_layout(G, seed=42)
nx.draw_networkx_nodes(G, pos=pos)
nx.draw_networkx_edges(G, pos=pos)
nx.draw_networkx_labels(G, pos=pos, labels=labels)

plt.show()
```

With each associated network, some type of flow, traffic, processes, etc., will be described. It is called a directed or oriented arc if it allows positive flow and zero flow in the direction of the arc.

A path is the succession of distinct arcs that connects two nodes passing through other nodes, regardless of the direction of flow of each arc. A directed network has all its arcs directed.

A connected network is one in which every two distinct nodes are connected by at least one path. A tree is a connected network that can easily be the connected network of all nodes, but with no cycles.

***

Exercises:

***

1. Draw by hand and in Colab the following model:
   
$$
N=\{1,2,3,4,5\} \\ A=\{(1,2),(2,5),(1,3),(3,4),(3,5),(5,1),(4,2)\}
$$

$$
N=\{1,2,3,4\} \\ A=\{(1,3),(1,2),(2,3),(2,4),(3,4)\}
$$



```
  1.Determine:
    - a path
    - a cycle
    - a directed cycle
    - a tree
    - A spanning tree..
```

2. Determine the sets (N) and (A) in the networks
3. Draw the network defined by

$$
N=\{1,2,3,4,5\} \\ A=\{(1,2),(1,5),(2,3)(2,4),(3,5),(3,4),(4,3),(4,6),(5,2),(5,6)\}
$$

2. Three products must be transported in a vehicle from the ABC store to Mrs. Pepita’s house to fulfill a delivery requested from the store, but the delivery person and their vehicle cannot repeat the same route.

* Formulate the network model to design the vehicle's trips so that delivery to Mrs. Pepita’s house is ensured.
  
***

### Minimum Spanning Tree Algorithm

***

The minimum spanning algorithm connects the nodes of a network, directly or indirectly, with the minimum possible length of the connecting branches. A possible use of this algorithm is in the design of distribution networks.

The most economical system design will be the one that minimizes the total distance of the created paths.
Another definition: A minimum spanning tree is a special type of tree that minimizes the lengths (or money) of the tree’s edges. An example is a cable company wanting to minimize the cost of connecting homes.

Procedure:

Let $$N=\{1,2,...n\}$$, en conjunto de  nodos en la Red.

$$
C_k=Conjunto\ de\ nodos\ que\ se\ han\ Conectado\ en \ forma\ permanente\ en\ la\ iteracion\ K \\ \bar{C_k} = Conjunto\ de\ nodos\ que\ faltan\ por\ conectar.
$$

**Step Zero: The set:

$$
C_0=𝛳\ y \\ \bar{C_0} =N
$$

1. Start with any node in the set $$\bar{C_0}$$ not yet connected and set $$C_1=\{i\}$$, con lo que $$\bar{C_1}=N-\{i\}$$, igualar a K=2
2. **paso general K,** select a node j in the unconnected set $$\bar{C_{k-1}}$$ that produces the shortest arc to a node in the connected set $$C_{k-1}$$ enlazando j permanently connecting $$C_{k-1}$$ and put it out of $$\bar{C_{k-1}}$$

$$
C_k=C_{k-1}+\{j\}, C_k = \bar{C_{k-1}}-\{j\}
$$

* when $$\bar{C_{k}}$$ is zero or empty, stop; otherwise, set $$K=k+1$$ and repeat the process.

***

Given the following table:

|       | A | B | C | D | E |
| ----- | - | - | - | - | - |
| **A** | 0 | 1 | 4 | 6 | 2 |
| **B** | 1 | 0 | 2 | - | 2 |
| **C** | 4 | 2 | 0 | 5 | 2 |
| **D** | 6 | - | 5 | 0 | 4 |
| **E** | 2 | 2 | 2 | 4 | 0 |

Use Prim’s and Kruskal’s algorithms and compare.

***

#### Theoretical Model According to Prim’s Algorithm:


Initialization: Select an arbitrary node as the root of the tree. Step-by-step construction:

1. At each step, add the shortest edge that connects a node inside the tree with one outside the tree.

2. Select the node closest to the current tree and add the edge connecting that node to the tree.

3. Termination: Repeat step 2 until all nodes are included in the tree.

#### Theoretical Model According to Kruskal’s Algorithm:

Edge ordering: Sort all edges in non-decreasing order of weight. Step-by-step construction:

1. At each step, select the shortest edge that does not form a cycle with the edges already selected.
2. Add this edge to the minimum spanning tree.
3. Termination: Repeat step 2 until (n-1) edges have been selected, where (n) is the number of nodes in the system.

# We will use Prim's Algorithm
import numpy as np

def prim_mst(distances):
    num_nodes = len(distances)
    # Initialize the MST and the visited nodes list
    mst = []
    visited = [False] * num_nodes
    # Start from node 0
    visited[0] = True
    # Repeat until all nodes are visited
    while len(mst) < num_nodes - 1:
        # Find the shortest edge connecting a visited node to an unvisited node
        min_distance = float('inf')
        min_i, min_j = None, None
        for i in range(num_nodes):
            if visited[i]:
                for j in range(num_nodes):
                    if not visited[j] and distances[i][j] < min_distance:
                        min_distance = distances[i][j]
                        min_i, min_j = i, j
        # Add the edge to the MST
        mst.append((min_i, min_j))
        visited[min_j] = True
    return mst

# Define the distance matrix
distances = [
    [0, 1, 4, 6, 2],
    [1, 0, 2, float('inf'), 2],
    [4, 2, 0, 5, 2],
    [6, float('inf'), 5, 0, 4],
    [2, 2, 2, 4, 0]
]

# Letters corresponding to the nodes
node_letters = ['A', 'B', 'C', 'D', 'E']

# Run Prim's algorithm
minimum_spanning_tree = prim_mst(distances)

# Print the resulting MST
print("Minimum Spanning Tree:")
for edge in minimum_spanning_tree:
    print(f"Edge: {node_letters[edge[0]]} - {node_letters[edge[1]]}")```

```python
# Kruskal's Algorithm
class UnionFind:
    def __init__(self, n):
        self.parent = list(range(n))
        self.rank = [0] * n

    def find(self, x):
        if self.parent[x] != x:
            self.parent[x] = self.find(self.parent[x])
        return self.parent[x]

    def union(self, x, y):
        root_x = self.find(x)
        root_y = self.find(y)
        if root_x != root_y:
            if self.rank[root_x] < self.rank[root_y]:
                self.parent[root_x] = root_y
            elif self.rank[root_x] > self.rank[root_y]:
                self.parent[root_y] = root_x
            else:
                self.parent[root_y] = root_x
                self.rank[root_x] += 1

def kruskal_mst(distances, node_letters):
    num_nodes = len(distances)
    edges = []
    # Build a list of edges (i, j, weight)
    for i in range(num_nodes):
        for j in range(i + 1, num_nodes):
            weight = distances[i][j]
            edges.append((i, j, weight))
    # Sort edges by weight
    edges.sort(key=lambda x: x[2])
    # Initialize the MST and Union-Find
    mst = []
    uf = UnionFind(num_nodes)
    # Build the MST
    for edge in edges:
        u, v, weight = edge
        if uf.find(u) != uf.find(v):
            mst.append((u, v))
            uf.union(u, v)
    return mst

# Define the distance matrix
distances = [
    [0, 1, 4, 6, 2],
    [1, 0, 2, float('inf'), 2],
    [4, 2, 0, 5, 2],
    [6, float('inf'), 5, 0, 4],
    [2, 2, 2, 4, 0]
]

# Letters corresponding to the nodes
node_letters = ['A', 'B', 'C', 'D', 'E']

# Run Kruskal's algorithm
minimum_spanning_tree_kruskal = kruskal_mst(distances, node_letters)

# Print the resulting MST
print("Minimum Spanning Tree (Kruskal):")
for edge in minimum_spanning_tree_kruskal:
    print(f"Edge: {node_letters[edge[0]]} - {node_letters[edge[1]]}")


# Imprimir el MST resultante

print("Árbol de Expansión Mínima (Kruskal):")
for arista in arbol_expansion_minima_kruskal:
    print(f"Arista: {nodos_letras[arista[0]]} - {nodos_letras[arista[1]]}")
```

Minimum spanning tree algorithms, such as Prim and Kruskal, have a wide range of applications in different fields, for example:

1. Distribution Networks: Planning networks for electricity, water, gas, etc.
2. Telecommunications: Designing telecommunication networks to interconnect base stations, cell towers, etc.
3. Logistics: Route optimization in transportation networks, such as roads, railways, and shipping routes.
4. Computer Cabling: Designing computer networks and cabling to connect devices in a local network.
5. Infrastructure Construction: Planning the construction of roads, bridges, and other civil infrastructure.
6. Electronic Circuit Design: Designing printed circuits and connections between electronic components on circuit boards.
7. Social Network Analysis: Identifying important connections and relationships in social and collaborative networks.
8. Molecular Biology: Analyzing interactions between proteins in molecular biology and designing metabolic pathways.
9. Natural Resource Exploration: Planning routes for exploration and extraction of natural resources, such as oil and minerals.
10. Irrigation System Design: Planning irrigation systems for agriculture and gardening.
Exercise one:

The company ABC provides lighting service to five new populated areas through construction projects. The nodes are given by the following network:

\[\begin{split} N=\{1,2,3,4,5\} \\ A=\{(1,2),(1,4),(2,3),(3,4),(1,3),(1,5),(3,6),(4,6),(2,5)\} \end{split}\]

Values (x10 km)

|   | 1 | 2 | 3 | 4 | 5 | 6  |
| - | - | - | - | - | - | -- |
| 1 | 0 | 1 | 5 | 7 | 9 | -  |
| 2 | 1 | 0 | 6 | - | 3 | -  |
| 3 | - | - | 0 | 5 | - | 10 |
| 4 | - | - | - | 0 | 8 | 3  |
| 5 | - | - | - | - | 0 | -  |
| 6 | - | - | - | - | - | 0  |

***
