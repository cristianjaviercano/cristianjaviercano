---
icon: timeline-arrow
---

# Chapter Four: Monte Carlo Simulation with Excel

Objectives:

1. Understand the fundamental principles and typical applications of Monte Carlo simulation.
2. Efficiently use the built-in functions in Microsoft Excel to generate random numbers and sample from common probability distributions.
3. Structure and implement Monte Carlo simulation models in Excel spreadsheets to solve simple problems in industrial engineering, logistics, and production.
4. Perform basic statistical analyses (mean, standard deviation, histograms) on the results obtained from a Monte Carlo simulation in Excel.
5. Evaluate the impact of uncertainty on model parameters and perform basic sensitivity analyses.

***

### **Introduction to Monte Carlo Simulation.**

Monte Carlo simulation is a computational technique that uses random sampling to obtain numerical results. Essentially, it is based on the idea of ​​repeating a simulated experiment many times, each time using input values ​​generated from their probability distributions. The set of results obtained is then analyzed to understand the behavior of the system or process under study, especially in the presence of uncertainty.

#### **Definition and Principle.**

Unlike discrete-event simulation, which focuses on the dynamic evolution of systems over time, Monte Carlo simulation is often applied to static models or to assess the impact of uncertainty on otherwise deterministic models. The name comes from the Monte Carlo Casino, alluding to the inherent randomness of the method. The central idea is that, through a sufficient number of random "experiments" or "samples," one can approximate the solution to problems that would be difficult or impossible to solve analytically.

### **General Steps of a Monte Carlo Study:**

1. **Define the System Model:** Establish the mathematical or logical relationships that describe the system or problem, identifying the output variables of interest (e.g., profit, cost, completion time).
2. **Identify Uncertain Inputs:** Determine which input variables or model parameters are uncertain and should be treated as random variables.
3. **Specify Probability Distributions:** For each uncertain input, select and parameterize an appropriate probability distribution that represents its variability (e.g., normal demand, triangular activity duration).
4. **Generate Random Samples (Replications):** For each model replication:
* Generate a random value for each uncertain input variable from its specified distribution.
* Calculate the value of the model's output variable(s) using these generated input values.
5. **Repeat Step 4:** Perform a large number of replications (hundreds or thousands) to obtain a representative sample of possible output outcomes.
6. **Statistically Analyze the Results:** Calculate descriptive statistics (mean, variance, percentiles), construct histograms or empirical distribution functions for the output variables, and estimate probabilities of interest (e.g., the probability that the profit exceeds a certain threshold).

### **Typical Applications in Industrial Engineering:**

* **Project and Investment Risk Analysis:** Evaluate the distribution of possible financial outcomes (e.g., Net Present Value - NPV, Internal Rate of Return - IRR) when cash flows or costs are uncertain.
* **System Reliability Estimation:** Calculate the probability that a system (composed of multiple components with individual probabilities of failure) will function correctly.
* **Simple Inventory Problems:** Determine optimal ordering policies when demand is uncertain (e.g., the newspaper vendor problem).
* **Production Planning under Uncertainty:** Estimate the amount of production needed to meet fluctuating demand while minimizing inventory costs and shortages.
* **Manufacturing Tolerance Analysis:** Evaluate how variations in part dimensions affect final assembly.
* **Project Time Estimating (Stochastic PERT):** Calculate the distribution of project completion times when activity durations are uncertain.

Excel, although not a specialized simulation software, is a very accessible and widely used platform. Its capabilities for generating random numbers and performing statistical calculations make it a useful tool for introducing Monte Carlo simulation concepts and for performing analysis of relatively simple models where complex time dynamics are not the primary focus. Many problems in industrial engineering involving parameter uncertainty can be initially addressed with this approach before turning to more sophisticated tools.

***

### **Using Excel Functions to Generate Randomness: `RAND()`, `RANDBETWEEN()`.**

Microsoft Excel provides built-in functions that are critical for generating the randomness needed in Monte Carlo simulations. The two basic functions are `RAND()` and `RANDBETWEEN()`.

* **`RAND()` (RAND):**
* **Description:** This function generates a pseudo-random real number that is uniformly distributed in the range greater than or equal to 0 and less than 1 (i.e., \[0,1)). &#x20;
* **Syntax:** `RAND()`
* **Behavior:** Each time the worksheet is recalculated (either by a change in another cell, pressing the F9 key, or opening the file), the `RAND()` function returns a new random number. This volatility is essential for generating multiple replications in a Monte Carlo simulation.
* **Base Use:** `RANDBETWEEN()` is the cornerstone for generating random variables from other distributions using the inverse transform method, as will be seen in the next section.
* **Setting a Value:** If you want to retain a specific random value generated by `RANDBETWEEN()` without it changing with each recalculation, you can copy the cell containing the function and then use the "Paste Values" option to replace the formula with its numerical result. &#x20;
* **`RANDBETWEEN(lower, upper)` (RANDBETWEEN):**
* **Description:** This function returns a pseudo-random integer that is uniformly distributed between the `lower` and `upper` values, inclusive. &#x20;
* **Syntax:** `RANDBETWEEN(lower, upper)`
* `lower`: The smallest integer the function can return.
* `upper`: The largest integer the function can return.
* **Behavior:** Like `RANDBETWEEN()`, this function is volatile and generates a new random integer with each recalculation of the spreadsheet.
* **Typical Use:** Useful for modeling situations where outcomes are equally probable integers within a defined range, such as the result of rolling a die (`RANDBETWEEN(1,6)`), or randomly selecting an item from a numbered list.

It is important to understand that both `RANDBETWEEN()` and `RANDBETWEEN()` generate numbers from a _uniform distribution_. This means that each possible value within their respective ranges has the same probability of occurring. If you need to model phenomena that follow other distributions (Normal, Exponential, Poisson, etc.), you will need to transform the output of `RAND()` using techniques such as the inverse transform. These two functions, although simple, are essential building blocks for introducing uncertainty into Excel models and performing Monte Carlo simulations.

***

### Implementing the Inverse Transform in Excel for Common Distributions

The inverse transform method (ITM) is a fundamental technique for generating random variables (RVs) from a specific probability distribution, using uniformly distributed random numbers as a basis.

1. Normal $$N(μ, σ2)$$

1. &#x20;(mean μ, standard deviation σ)
1. Excel provides a direct function for the inverse of the Normal CDF
1. **Excel formula:** `=NORM.INV(RAND(), mean, std_dev)` or `=NORM.INV(RAND(), mean, std_dev)`. &#x20;
* Replace `mean` and `std_dev` with the desired values.&#x20;

2. Triangular (minimum a, mode c, maximum b).

The FDA is $$F(x)$$ = $$\left\{ \begin{matrix} \frac{(x-a)^2}{(b-a)(c-a)}\ si\ a \le x\le c\\ 1- \frac{(b-x)^2}{(b-a)(b-c)}\ si\ c \le x\le b\end{matrix} \right\}$$

The inverse $$F^−1(u)$$ is defined piecewise:&#x20;

$$If\ u≤F(c)=(c−a)/(b−a)$$, then $$x=a+\sqrt {u(b−a)(c−a)}$$.&#x20;

$$If\ u>F(c)$$, then $$x=b−\sqrt{(1−u)(b−a)(b−c)}$$



**Formula in Excel:**&#x20;

{% hint style="info" %}
**Assuming a,c,b are in cells A1, B1, C1 respectively**
{% endhint %}

`=IF(RANDOM()<=(B1-A1)/(C1-A1), A1+ROOT(RANDOM()*(C1-A1)*(B1-A1)), C1-ROOT((1-RANDOM())*(C1-A1)*(C1-B1)))`&#x20;

_This formula uses `RANDOM()` twice, which generates two different random numbers. To use the same random number U for both the condition and the calculation, U should be generated in a separate cell and referenced.

A better implementation would be: Cell D1: `=RAND()` Cell E1: `=IF(D1<=(B1-A1)/(C1-A1), A1+SQRT(D1*(C1-A1)*(B1-A1)), C1-SQRT((1-D1)*(C1-A1)*(C1-B1)))`&#x20;

#### **Bernoulli (probability of success p):**

* The AV takes the value 1 (success) with probability p, and 0 (failure) with probability 1−p.
* The CDF is $$F(0)=1−p, F(1)=1.$$
* If u\<p, X=1. If u ≥ p, X = 0. (Or, more commonly, if u < p, X = 1, otherwise X = 0.)
* **Excel formula:** `=IF(RAND()<p, 1, 0)`
* Replace `p` with the probability of success.

**Binomial (n trials, probability of success p):**

* Excel has a direct inverse function.
* **Excel formula:** `=BINOM.INV(n, p, RAND())` or `=BINOM.INV(trials, probability_s, RAND())`. &#x20;
* Replace `n` and `p` with the desired parameters.

***

### **The Bullseye Problem**

Imagine a square board with a side length of 2 and an area of ​​4 units. Within this square, we inscribe a circle of radius 1, whose area is $$πr2=π$$.

<img src="../../../.gitbook/assets/file.excalidraw (13).svg" alt="Bullseye Problem" class="gitbook-drawing">

If we throw _darts randomly_ at this board, such that each point in the square has the same probability of being hit, the proportion of darts that fall inside the circle relative to the total number of darts thrown will be approximately equal to the **ratio of their areas.**

The method is based on a stochastic experiment. Consider a sample space defined by a square in the Cartesian plane. To simplify the model, this square is usually centered at the origin, with vertices at the points (1, 1), (1, -1), (-1, -1), and (-1, 1). The length of each side is therefore 2 units, and its **total area** $$A_{square} = 4$$ **square units**.

Within this square, a circle is inscribed with center at the origin (0,0) and radius r = 1. The area of ​​this **circle** $$A_{circle}$$ is defined by the formula $$πr2$$**,** which in this case is simply π.

The experiment consists of generating a large number of random points (x,y) that fall uniformly within the boundaries of the square. This means that each point has the same probability of landing anywhere within the square's area.

$$
−1≤x≤1 \ y\ −1≤y≤1
$$

For each generated point, we evaluate whether it falls within the inscribed circle. A point (x,y) is inside the circle if the distance from the origin to that point is less than or equal to the radius of the circle. According to the Pythagorean Theorem, this condition is expressed mathematically as:

$$
x
2
+y
2
≤r
2
$$

Since r=1, the condition simplifies to

$$
x
2
+y
2
≤1
$$

* Theoretically, the probability (P) that a randomly thrown dart will hit inside the circle is the ratio of the area of ​​the circle to the area of ​​the square.

$$
P(inside the circle)= \frac{A_{circle}}{ A_{square}}= \frac{π}{4}
$$

#### **Algebraic Form and Implementation Algorithm**

By algebraically rearranging the above expression to solve for π, we obtain the estimation formula used in the Simulation:

$$
π≈4⋅\frac{N_{total}}{​N_{circle​}}​
$$

* **Initialization**: Define the total number of "darts" to throw $$N_{total}$$​ and initialize a counter for the points inside the circle $$N_{circle}​$$ to zero.
* **Point Generation**: Start a loop that repeats N\_total​ times. In each iteration, generate two random numbers, x and y, from a uniform distribution on the interval \[-1, 1].
* **Condition Evaluation**: For each point (x,y) generated, calculate x2+y2.
* **Counting**: If the evaluation result is less than or equal to 1, increment the counter N\_circle​.
* **Final Estimate**: Once the loop is complete, calculate the approximation of π using the derived formula: $$π_{estimated​} = 4⋅\frac{N_{circle}}{​{N_{total}}}$$​.


<figure><img src="../../../.gitbook/assets/Captura de pantalla 2025-06-10 a la(s) 1.54.58 p.m..png" alt="" width="375"><figcaption></figcaption></figure>

### **Model Logic (Single-Server Queue):**

The simulation clock will advance from client to client. For each client, the following must be determined:

1. When does the client arrive?
2. How long does the client require service?
3. When does the client begin service? This depends on the client's arrival time and when the server becomes available.
4. How long did the client wait in the queue?
5. When does the client end service and leave the system?

The goal is to collect data on system performance (KPIs), such as average wait time, server utilization, and queue length.

#### **Model Implementation in Microsoft Excel**

The spreadsheet will be structured into two sections:

<details>

<summary>Input parameters (probability distributions) </summary>

**Input Parameters and Distributions**

First, probability distributions for interarrival times and service times are defined. This is the core of the Monte Carlo method, where random numbers will be used to sample from these distributions.

<table><thead><tr><th>Time</th><th data-type="number">Probability</th><th data-type="number">Cumulative probability</th><th data-type="number">Range bottom</th></tr></thead><tbody><tr><td>1</td><td>0.25</td><td>0.25</td><td>0</td></tr><tr><td>2</td><td>0.4</td><td>0.65</td><td>0.25< /td></tr><tr><td>3</td><td>0.2</td><td>0.85</td><td>0.65</td></tr><tr><td>4</td><td>0.15</td><td>1</td><td>0.85</td></tr></tbody></table>

</details>

<details>

<summary>The main simulation table.</summary>

<table><thead><tr><th>time MIn</th><th>Probability</th><th>Accumulated</th><th data-type="number">limit bottom</th></tr></thead><tbody><tr><td>2</td><td>0.3</td><td>0.3</td><td>0</td></tr><tr><td>3</td><td>0 .5</td><td>0.8</td><td>0.3</td></tr><tr><td>4</td><td>0.2</td><td>1</td><td>0.8</td></tr></tbody></table>

</details>

{% embed url="https://docs.google.com/spreadsheets/d/18sUk-lkaXOz7nrbjiC0UxqG91DfLOFqM07N6GbR9kAk/edit?usp=sharing" %}
ejercico montecarlo con aleatorios
{% endembed %}
