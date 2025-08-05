# Transshipment Model

#### Explanation of the Transshipment or Cross Docking Model

The transshipment model, also known as cross docking, is a logistics methodology where products move directly from the supplier to the end customer with minimal handling and storage. This model involves the use of distribution centers, also called intermediate nodes, where incoming products are quickly sorted and rerouted without the need for long-term storage.

The main advantage of cross docking is supply chain efficiency, reducing storage costs and speeding up shipping times to the end customer. In the typical scenario, products arrive at a transshipment center and are transferred directly to an outbound vehicle headed to the final destination, which requires precise coordination but provides an efficient and continuous flow of goods.

***

{% hint style="info" %}
The transshipment or cross-docking model starts with the assumption that passing through intermediate nodes represents savings for the system, while the general transportation model only assumes direct deliveries.
{% endhint %}

Example:

where product X factories P\_1 and P\_2 are associated with three agencies D\_1, D\_2, and D\_3 through two distribution centers T\_1 and T\_2.

1. Generate the network model for this section by hand and in collaboration. using Graphviz

```python
from IPython.display import Image
Image(filename='/content/drive/MyDrive/Academic books in colab/1. Logistics/Image 03-16-23 at 1:26 p.m..jpeg')
```

The supply of plants is as shown in the following table:

```latex
Demand at P_n
- P_1 = 1000 Un
- P_2 = 1200 Un
```

```latex
Demand at D_n
- D_1 = 800
- D_2 = 900
- D_3 = 500
```
Note that nodes \\(t\_n\ and \\ D\_n\\) function as input and output. These are called **Transshipment Nodes**

* Pure supply nodes are the issuers of units
* Pure demand nodes are those that only receive units
* Transshipment nodes are those that fulfill both functions simultaneously. (original supply + Buffer)
* Pure demand and transshipment nodes have (original demand + Buffer)

The Buffer Quantity must be large enough to ensure that all of the original supply or demand passes through any of the Transshipment nodes, with \\(B\\) being the desired buffer quantity. then:

B = Supply (Total Demand) = 1000 + 1200 (or 800 + 900 + 500) = 2200 units

With this buffer, this model transforms into an original transportation model (…)

Below is the response to the model using the traditional transportation model.

| - | \\(T\_1\\) | \\(T\_2\\) | \\(D\_1\\) | \\(D\_2\\) | \\(D\_3\\) | |
| ---------- | ---------- | ---------- | ---------- | ---------- | ---- |
| \\(P\_1\\) | 3 | 4 | M | M | M | 1000 |
| \\(P\_2\\) | 2 | 5 | M | M | M | 1200 |
| \\(T\_1\\) | 0 | 7 | 8 | 6 | M | B |
| \\(T\_2\\) | M | 0 | M | 4 | 9 | B |
| \\(D\_1\\) | M | M | 0 | 5 | M | B |
| \\(D\_2\\) | M | M | M | 0 | 3 | B |

\*\*

#### Crossdocking Exercises:[#](broken-reference)

***

1. Formulate the model corresponding to the following diagrams:

```
from IPython.display import Image
Image(filename='/content/drive/MyDrive/Academic Books in Collab/1. Logistics/network2.jpeg',width = 300, height = 200)
```

```
from IPython.display import Image
Image(filename='/content/drive/MyDrive/Academic Books in Collab/1. Logistics/network3.jpeg')
```

2. Build and optimize the following crossdocking exercise.

Cano. Ltda is a growing company with a classic crossdocking problem. You are hired as an operations engineer and are faced with this decision. The company has three production plants located At different points in the city, these supply two of the company's own warehouses (CEDIS). However, due to market changes, the product must be repackaged in warehouses to be transported to the CEDIS. In this case, we have three warehouses that will provide this service. These warehouses are also our own.

* Build the network and node diagram based on the following information: the graph should be viewed from left to right. In the first part, we find three nodes corresponding to the company's three manufacturing plants. These nodes are P\_1, P\_2, and P\_3. These are connected by road to the warehouses that handle the packaging change, called B\_1. B\_2 and B\_3 are located in the center of the graph, the existing routes force us to have the following distribution: P\_1 can only send material to B\_1 with a distance of 20km between them, P\_2 can send materials to B\_1, B\_2 and B\_3 with distances of 10 km, 50 km and 20 km respectively, finally P\_3 can send material to B\_3 with a distance of 15 km; These three warehouses can send already processed material to the CEDIS in the following way B\_1 can send to CEDI\_1 which is at a distance of 10 km, B\_2 can send to CEDI\_1 and CEDI\_2 which are at a distance of 50km and 20 km respectively and B\_3 can send to CEDI\_2 which is at a distance of 30 km; In some cases, it may happen that the processing capacity of one of the warehouses is exceeded and they can help each other with other warehouses, for this there are communication routes between them, such as B\_1 is connected to B\_2 at a distance of 10 km and B\_3 with B\_2 at a distance of 15 km.

```python
import networkx as nx
import matplotlib.pyplot as plt

# Create a directed graph (since paths have a direction)
G = nx.DiGraph()

# Add nodes
nodes = ['P_1', 'P_2', 'P_3', 'B_1', 'B_2', 'B_3', 'CEDI_1', 'CEDI_2']
G.add_nodes_from(nodes)

# Add edges with distances (weights)
edges = [
('P_1', 'B_1', 20),
('P_2', 'B_1', 10),
('P_2', 'B_2', 50),
('P_2', 'B_3', 20),
('P_3', 'B_3', 15), 
('B_1', 'CEDI_1', 10), 
('B_2', 'CEDI_1', 50), 
('B_2', 'CEDI_2', 20), 
('B_3', 'CEDI_2', 30), 
('B_1', 'B_2', 10), 
('B_3', 'B_2', 15)
]
G.add_weighted_edges_from(edges)

# Draw the graph
pos = nx.shell_layout(G) # Node positioning
nx.draw(G, pos, with_labels=True, font_weight='bold')
labels = nx.get_edge_attributes(G,'weight')
nx.draw_networkx_edge_labels(G,pos,edge_labels=labels)
plt.show()
```

Cost Matrix:

| Nodes | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| ----- | - | - | - | -- | -- | -- | -- | -- |
| 1 | - | - | - | 20 | - | - | - | |
| 2 | - | - | - | 10 | 20 | 50 | - | - |
| 3 | - | - | - | - | 15 | - | - | - |
| 4 | - | - | - | - | 20 | 10 | 10 | - |
| 5 | - | - | - | - | - | 30 | | 30 |
| 6 | - | - | - | - | - | - | 50 | 20 |
| 7 | - | - | - | - | - | - | - | - |
| 8 | - | - | - | - | - | - | - | - |

* Production costs:

| | Production costs | |
| - | -------------------- | ------ |
| 1 | 400 | unit |
| 2 | 450 | unit |
| 3 | 470 | unit |

1. Based on the cost matrix, the shipping matrix must be created, that is, with costs only.

The model considers that:

1. It must be leveled.
2. All supply must pass through the mixed nodes (transshipment).
3. Build the transshipment matrix.

Cano.ltda is a growing company and has just signed alliances with different companies to market its flagship product. The company owns two factories (P1) and (P2), which have a supply of 1,000 units and 1,200 units, respectively. The group now has two distribution centers, which we call T1 and T2. At the end of the chain, there are three distributors (D1), D2, and D3), which have a demand of 800, 900, and 500 units, respectively.

The corresponding distances between each of the actors are given in the following distance table:

| | P\_1 | P\_2 | T\_1 | T\_2 | D\_1 | D\_2 | D\_3 |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| P\_1 | 0 | - | 3 | 4 | - | - | - |
| P\_2 | - | 0 | 2 | 5 | - | - | - |
| T\_1 | - | - | 0 | 7 | 8 | 6 | - |
| T\_2 | - | - | - | 0 | - | 4 | 9 |
| D\_1 | - | - | - | - | 0 | 5 | - |
| D\_2 | - | - | - | - | - | 0 | 3 |
| D\_3 | - | - | - | - | - | - | 0 |

| Supply | qty |
| ------ | ------- |
| P\_1 | 1000 Units |
| P\_2 | 1200 Units |

| Demand | qty |
| ------- | ------ |
| D\_1 | 800 Units |
| D\_2 | 900 Units |
| D\_3 | 500 Units |

1. We define the transshipment nodes T\_1 and T\_2
2. We define the system's "Buffer" B\_n must be large enough to supply the process

$$
B\_n = Supply - Demand
$$

3. We proceed to create the transshipment matrix

| | T\_1 | T\_2 | D\_1 | D\_2 | D\_3 | Demand |
| ------ | ---- | ---- | ------- | ------- | ---- | ------- |
| P\_1 | 3 | 4 | M | M | M | 1000 |
| P\_2 | 2 | 5 | M | M | M | 1200 |
| T\_1 | 0 | 7 | 8 | 6 | M | B |
| T\_2 | M | 0 | M | 4 | 9 | B |
| D\_1 | M | M | 0 | 5 | M | B |
| D\_2 | M | M | M | 0 | 3 | B |
| Offer | B | B | 800+B | 900+B | 500 | - |
