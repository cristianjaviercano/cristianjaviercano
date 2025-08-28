---
hidden: true
---

# Exercises TSP in logistics

{% file src="../../../../.gitbook/assets/CEDI.xlsx" %}

### Problem 1

Consider the problem of a paint manufacturing company, Rainbow, that produces batches of white (W), yellow (Y), black (B), and red (R) paint. The production facilities must be cleaned between batches of different colors. The goal is to determine the sequence of colors that minimizes the total cleaning time.

### Nodes 

* &#x20;W = White&#x20;
* &#x20;Y = Yellow&#x20;
* &#x20;B = Black&#x20;
* &#x20;R = Red&#x20;
* Total number of cities $$n = 4$$.

Distance Matrix $$d_{ij}$$ - Cleaning Times in minutes: ('q' is assigned to prohibit $$x_{ii}$$)

| From / To  | White (1) | Yellow (2) | Black (3) | Red (4) |
| ---------- | --------- | ---------- | --------- | ------- |
| White (1)  | q         | 10         | 17        | 15      |
| Yellow (2) | 20        | q          | 19        | 18      |
| Black (3)  | 50        | 44         | q         | 22      |
| Red (4)    | 45        | 40         | 20        | q       |

Decision Variables: $x\_{ij} = 1$ if paint $j$ follows paint $i$, and $0$ otherwise. For example, $x\_{12} = 1$ if after White, cleaning is done for Yellow. Objective Function: Minimize total cleaning time: $$\text{Min } Z = 10x_{12} + 17x_{13} + 15x_{14} + 20x_{21} + 19x_{23} + 18x_{24} + 50x_{31} + 44x_{32} + 22x_{34} + 45x_{41} + 40x_{42} + 20x_{43}$$ Entry/Exit Constraints ($n = 4$ cities):

1. Each city is entered exactly once: ◦ $x\_{21} + x\_{31} + x\_{41} = 1$ (to White) ◦ $x\_{12} + x\_{32} + x\_{42} = 1$ (to Yellow) ◦ $x\_{13} + x\_{23} + x\_{43} = 1$ (to Black) ◦ $x\_{14} + x\_{24} + x\_{34} = 1$ (to Red)
2. Each city is exited exactly once: ◦ $x\_{12} + x\_{13} + x\_{14} = 1$ (from White) ◦ $x\_{21} + x\_{23} + x\_{24} = 1$ (from Yellow) ◦ $x\_{31} + x\_{32} + x\_{34} = 1$ (from Black) ◦ $x\_{41} + x\_{42} + x\_{43} = 1$ (from Red)
3. Subtour Elimination Constraints (with $n=4$): For $n=4$, the general constraint is $u\_i - u\_j + 4 \cdot x\_{ij} \leq 3$. These constraints apply for $i, j \in {2, 3, 4}$ (cities Yellow, Black, Red), with $i \neq j$, excluding the origin city (City 1, White) from the variables $u\_i$ and $u\_j$. The possible pairs $(i,j)$ are: $(2,3)$, $(2,4)$, $(3,2)$, $(3,4)$, $(4,2)$, $(4,3)$.
4. Some examples of these constraints would be: ◦ For $i=2$ (Yellow), $j=3$ (Black): $u\_2 - u\_3 + 4 \cdot x\_{23} \leq 3$ ◦ For $i=2$ (Yellow), $j=4$ (Red): $u\_2 - u\_4 + 4 \cdot x\_{24} \leq 3$ ◦ For $i=3$ (Black), $j=2$ (Yellow): $u\_3 - u\_2 + 4 \cdot x\_{32} \leq 3$ ◦ For $i=3$ (Black), $j=4$ (Red): $u\_3 - u\_4 + 4 \cdot x\_{34} \leq 3$ ◦ For $i=4$ (Red), $j=2$ (Yellow): $u\_4 - u\_2 + 4 \cdot x\_{42} \leq 3$ ◦ For $i=4$ (Red), $j=3$ (Black): $u\_4 - u\_3 + 4 \cdot x\_{43} \leq 3$
5. These constraints ensure that no cycles are formed between a subset of the Yellow, Black, and Red cities.
6. Binary Variables: $x\_{ij} \in {0, 1}$ for all $i, j$. The variables $u\_i$ are typically non-negative integers, with a possible range $1 \leq u\_i \leq n$. For small problems like this 4-city example, all possible optimal routes can be enumerated. In this case, the number of tours is $(n-1)! = (4-1)! = 3! = 6$ tours. Evaluating these six, the optimal solution is the W-Y-B-R-W (White-Yellow-Black-Red-White) tour with a total cleaning time of $10 + 19 + 22 + 45 = 96$ minutes.
