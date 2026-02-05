# Exercises TSP in logistics

{% file src="../../../../.gitbook/assets/CEDI.xlsx" %}

### Problem 1

Consider the problem of a paint manufacturing company, Rainbow, that produces batches of white (W), yellow (Y), black (B), and red (R) paint. The production facilities must be cleaned between batches of different colors. The goal is to determine the sequence of colors that minimizes the total cleaning time.

### Nodes<br>

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

Decision Variables: $$x_{ij} = 1$$ if paint $$j$$ follows paint $$i$$, and 0 otherwise.&#x20;

For example,&#x20;

$$x_{12} = 1$$ if after White, cleaning is done for Yellow.&#x20;

Objective Function: Minimize total cleaning time:&#x20;

$$\text{Min } Z = 10x_{12} + 17x_{13} + 15x_{14} + 20x_{21} + 19x_{23} + 18x_{24} + 50x_{31} + 44x_{32} + 22x_{34} + 45x_{41} + 40x_{42} + 20x_{43}$$&#x20;

Entry/Exit Constraints (n = 4 colors):

1. Each color is entered exactly once:&#x20;
   1. $$x_{21} + x_{31} + x_{41} = 1$$ (to White)
   2. $$x_{12} + x_{32} + x_{42} = 1$$ (to Yellow)&#x20;
   3. $$x_{13} + x_{23} + x_{43} = 1$$ (to Black)&#x20;
   4. $$x_{14} + x_{24} + x_{34} = 1$$ (to Red)
2. Each city is exited exactly once:&#x20;
   1. $$x_{12} + x_{13} + x_{14} = 1$$ (from White)&#x20;
   2. $$x_{21} + x_{23} + x_{24} = 1$$ (from Yellow)&#x20;
   3. $$x_{31} + x_{32} + x_{34} = 1$$ (from Black)&#x20;
   4. $$x_{41} + x_{42} + x_{43} = 1$$ (from Red)
3.  Subtour Elimination Constraints (with n=4):&#x20;

    1. For $$n=4$$, the general constraint is&#x20;

    $$u_i - u_j + 4 \cdot x_{ij} \leq 3$$

    1. These constraints apply for $$i, j \in {2, 3, 4}$$ (nodes Yellow, Black, Red), with $$i \neq j$$ excluding the origin city (City 1, White) from the variables $$u_i$$ and $$u_j$$ The possible pairs $$(i,j)$$ are: (2,3), (2,4), (3,2), (3,4), (4,2), (4,3).
4. Some examples of these constraints would be:&#x20;
   1. For i=2 (Yellow), j=3 (Black): $$u_2 - u_3 + 4 \cdot x_{23} \leq 3$$
   2. For i=2 (Yellow), j=4 (Red): $$u_2 - u_4 + 4 \cdot x_{24} \leq 3$$
   3. For i=3 (Black), j=2 (Yellow): $$u_3 - u_2 + 4 \cdot x_{32} \leq 3$$
   4. For i=3 (Black), j=4 (Red):  $$u_3 - u_4 + 4 \cdot x_{34} \leq 3$$
   5. For i=4 (Red), j=2 (Yellow): $$u_4 - u_2 + 4 \cdot x_{42} \leq 3$$
   6. For i=4 (Red), j=3 (Black): $$u_4 - u_3 + 4 \cdot x_{43} \leq 3$$

{% hint style="warning" %}
These constraints ensure that no cycles are formed between a subset of the Yellow, Black, and Red cities.
{% endhint %}

#### Binary Variables:&#x20;

$$x_{ij} \in {0, 1} \forall i, j.$$&#x20;

The variables u\_i are typically non-negative integers, with a possible range $$1 \leq u_i \leq n$$.&#x20;

For small problems like this 4-node example, all possible optimal routes can be enumerated. In this case, the number of tours is **(n-1)! = (4-1)! = 3! = 6** tours.&#x20;

Evaluating these six, the optimal solution is the W-Y-B-R-W (White-Yellow-Black-Red-White) tour with a total cleaning time of 10 + 19 + 22 + 45 = 96 minutes.

***

### Problem 2 CEDI

Donwload the file [here](https://docs.google.com/document/d/1CKqM2KUIYtqgXxTRkCnF-pKacDv0o8u_DtXqiDEQ7uE/edit?usp=sharing)
