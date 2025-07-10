# Chapter Two: Fundamentals of Probability and Statistics for Simulation

### Chapter Objectives:

1. Apply basic concepts of probability theory to model uncertainty in industrial engineering systems.
2. Distinguish between discrete and continuous random variables, and describe their fundamental properties.
3. Use and interpret probability mass functions (PMF), probability density functions (PDF), and cumulative distribution functions (CDF).
4. Calculate and interpret the expected value, variance, and other descriptive measures of random variables.
5. Identify the most common probability distributions (Bernoulli, Binomial, Poisson, Geometric, Uniform, Exponential, Normal, Triangular, Gamma, Weibull, Lognormal) and select the most appropriate one to model random phenomena in logistics and production.
6. Understand the statement and practical implications of the Central Limit Theorem (CLT).
7. Describe the process of parameter estimation from sample data and the need to perform goodness-of-fit tests.

***

## Basic Concepts of Probability

Industrial engineering deals with systems that operate under uncertainty. _Product demand fluctuates, production times vary, machines fail unexpectedly._ **Probability** is the branch of mathematics that provides the language and tools to quantify and analyze this uncertainty. A solid understanding of its principles is therefore an indispensable prerequisite for stochastic simulation.

{% tabs %}
{% tab title="Sample Space (Ω)" %}
_It is the set of all possible outcomes of a random experiment._ For example, if a manufactured part is inspected, the sample space could be {defective, not defective}. If the cycle time of a product is measured, the sample space could be all positive real numbers.

{% hint style="info" %}
Montgomery, D. C., & Runger, G. C. (2018). Applied Statistics and Probability for Engineers (7th ed.). Wiley.
{% endhint %}
{% endtab %}

{% tab title="Event (E)" %}
An event is any subset of the sample space; that is, a collection of one or more possible outcomes.

For example,

* That a part is "defective" is an event.
* That the cycle time is "less than 10 minutes" is another event.
{% endtab %}

{% tab title="Axioms of Probability" %}
The probability of an event A, denoted as P(A), is a number between 0 and 1 that satisfies three basic axioms:

$$
0≤P(A)≤1\   \text{for any event A}
$$

$$
P(Ω)=1\ \text{(the probability that some outcome in the sample space occurs is 1)}
$$

$$
If\ A_1​,A_2​,…,A_n​\ \text{are mutually exclusive events, then} \\P(A_1​∪A_2​∪…∪A_n​)=P(A_1​)+P(A2_​)+…+P(A_n​)
$$
{% endtab %}

{% tab title="Conditional Probability" %}
The probability that event A occurs, given that another event B has already occurred, is called conditional probability and is denoted $$P(A|B)$$.

It is calculated as,

$$P(A|B)=\frac{P(A∩B)}{P(B)}$$

As long as $$P(B)>0.1$$ This concept is vital for modeling dependencies in systems, such as the probability that a machine fails given that it has been operating for a certain time.
{% endtab %}

{% tab title="Independence of Events" %}
Two events A and B are independent if the occurrence of one does not affect the probability of occurrence of the other.

Formally, A and B are independent if $$P(A∩B)=P(A)P(B)$$, which implies that $$P(A|B)=P(A)\ and\ P(B|A)=P(B)$$.

_The assumption of independence_, when valid, greatly simplifies modeling. However, _**assuming it incorrectly**_ can lead to erroneous models.

For example, the failures of two machines may not be independent if they share a common power source.
{% endtab %}

{% tab title="Bayes" %}
Allows updating the probability of an event based on new evidence. Although its direct application in generating simulation inputs is not as frequent as other concepts, it is a fundamental tool in statistical inference and decision-making under uncertainty.
{% endtab %}
{% endtabs %}

{% hint style="info" %}
The foundation of stochastic simulation lies in the ability to numerically represent uncertainty. Production and logistics processes are full of variability. - CRC -
{% endhint %}

[Probability theory](https://www.probabilidadyestadistica.net/teoria-de-la-probabilidad/) provides the _conceptual framework_ for describing these phenomena. Concepts such as event independence are crucial; for example, when modeling a system with multiple machines, it is important to determine if the failure of one machine is independent of failures of another. If they are not (perhaps due to widespread poor maintenance or power fluctuations), the model must capture this dependence, often through conditional probabilities.

***

> #### Example of Probability Using the Dartboard Exercise
>
> There is a square board with an inscribed circle. The circle has a radius _r_ and, since it is perfectly inscribed, the side of the square is _2r_. Darts are thrown at the square randomly, meaning each point inside the square has the same probability of being hit.
>
> _The goal is to determine the probability that a dart that lands inside the square also lands inside the circle._
>
> $$P(A)= \frac{ \text{Measure of the total sample space}}{ \text{Measure of the favorable outcome space}}$$
>
> For this problem:
>
> * The **total sample space (S)** is all possible points where the dart can land, i.e., the area of the square.
> * The **favorable event (E)** is that the dart lands inside the circle, which corresponds to the area of the circle.
>
> **Area of the Circle** $$(A_\text{circle})$$: The area of a circle is calculated with the formula $$A=\pi r^2$$.
>
> For r=1, the area is: $$A_{\text{circle}} = \pi (1)^2 = \pi$$
>
> **Area of the Square** $$(A_\text{square})$$: If the circle of radius 1 is centered and concentric with the square, the side of the square _(l)_ equals the diameter of the circle, i.e., l=2r. For r=1, the side of the square is l=2(1)=2. The area of the square is calculated as&#x20;
>
> $$A=l^2. \ A_{\text{square}} = (2)^2 = 4$$
>
> **Calculation of Probability**: The probability that the dart lands inside the circle is the ratio of the two areas.
>
> $$P(\text{Dart in circle}) = \frac{A_{\text{circle}}}{A_{\text{square}}} = \frac{\pi}{4}$$
>
> Numerically, this is approximately:
>
> $$\frac{\pi}{4} \approx \frac{3.14159}{4} \approx 0.7854$$ This means there is approximately a **78.54%** probability that the dart lands inside the circle.

### Theorem of Mutually Exclusive Events

{% hint style="warning" %}
From a statistical perspective, two or more events are considered **mutually exclusive** if the occurrence of one makes it impossible for any of the others to occur at the same time. In set theory terms, this means that the intersection of these events is the empty set.
{% endhint %}

_The theorem of mutually exclusive events_ states that two events cannot occur simultaneously. In other words, if one event happens, the other cannot. Mathematically, two events A and B are mutually exclusive if their intersection is empty, that is,

$$A \cap B = \emptyset$$.

> **Example:**
>
> Imagine rolling a six-sided die. Define the following events:
>
> * Event A: rolling an even number (2, 4, 6)
> * Event B: rolling an odd number (1, 3, 5)
>
> Clearly, a number cannot be even and odd at the same time. Therefore, A and B are mutually exclusive events.
>
> **Property**
>
> For mutually exclusive events, the probability that any of them occurs is the sum of their individual probabilities: $$P(A \cup B) = P(A) + P(B)$$

In the context of _discrete-event simulation_, the concept of mutually exclusive events is fundamental for modeling **decision points, branching, and entity routing**. When an entity (a customer, product, document) reaches a point in the process where it must follow one of several possible paths, these paths represent mutually exclusive events. The entity cannot take two paths at once.

This logic is implemented in _AnyLogic_ mainly through the **`SelectOutput`** block from the Process Modeling Library (PML).

* **Practical Implementation**: A `SelectOutput` block has one input and multiple outputs. An arriving entity is routed to **one and only one** of these outputs, making the choice of each route a mutually exclusive event.

This routing can be defined in two main ways:

1. **Probabilistic Routing**: The block can be set to route entities based on probabilities. For example, 50% of entities go to output 1, 30% to output 2, and 20% to output 3. The sum of probabilities must be 1, ensuring each entity takes exactly one route.
2. **Conditional Routing**: The route selection is based on a boolean condition (true/false). For example: `IF (entity.type == "Urgent") THEN Output1 ELSE Output2`. The condition `entity.type == "Urgent"` can only be true or false for a given entity, never both. Therefore, taking Output 1 and taking Output 2 are mutually exclusive events.

> #### Shoe Factory Example:
>
> Consider the "Shoe Factory" case.
>
> **Process Description**: The document states that, in the first stage, the cutting process depends on the shoe type. 50% of units are **Type 1**, 30% are **Type 2**, and 20% are **Type 3**.
>
> **Event Analysis**: A shoe unit arriving at the cutting station cannot be both Type 1 and Type 2 at the same time. Therefore, the events "the unit is Type 1", "the unit is Type 2", and "the unit is Type 3" are **mutually exclusive**.
>
> **Implementation in AnyLogic**: To model this system, a `Source` block is used to generate shoe pairs' arrivals, immediately followed by a `SelectOutput` block. This `SelectOutput` is configured with three outputs, each connected to a different cutting process, and with probabilities of 0.5, 0.3, and 0.2, respectively.

***

### Random Variables: Discrete and Continuous

A random variable (RV) is a function that assigns a numeric value to each possible outcome of a random experiment. Instead of working with qualitative events, random variables allow us to quantify outcomes and apply mathematical and statistical tools.

{% tabs %}
{% tab title="Discrete Random Variables" %}
An RV is discrete if the set of values it can take is finite or countably infinite (that is, can be counted, like the integers).

Examples in Industrial Engineering:

* Number of customer arrivals at a service system in an hour.
* Number of defective items in a production lot.
* Number of trucks waiting to load at a dock.
* Number of units demanded of a product in a day.
{% endtab %}

{% tab title="Continuous Random Variables" %}
An RV is continuous if it can take any value within an interval (or union of intervals) of real numbers. Between any two possible values, there is always an infinite number of other possible values.

Examples in Industrial Engineering:

* Time between consecutive order arrivals at a warehouse.
* Service time of an operation on a machine.
* Weight or dimension of a manufactured part.
* Time until equipment failure.
{% endtab %}
{% endtabs %}

***

**Definitions: Probability, Density, and Cumulative Distribution Functions**

**Probability Density Function (PDF):** Describes the probability that a _continuous random variable_ takes a value within a specific range, where the area under the curve equals the probability.

The probability density function (PDF): The probability that X is between values a and b is the integral of the PDF from a to b:

$$P(a \leq X \leq b) = \int_{a}^{b} f(x) \, dx$$

> **Example:**
>
> If X is a continuous random variable with PDF $$f(x) = \frac{1}{2}$$ for $$0 \leq x \leq 2$$, and zero elsewhere, the probability that X is between 0.5 and 1.5 is calculated as:
>
> $$P(0.5 \leq X \leq 1.5) = \int_{0.5}^{1.5} \frac{1}{2} \, dx = \left[\frac{1}{2}x\right]_{0.5}^{1.5} = \frac{1}{2}(1.5) - \frac{1}{2}(0.5) = 0.5$$
>
> Therefore, the probability that X is between 0.5 and 1.5 is 0.5.

**Cumulative Distribution Function (CDF):** Provides the probability that a random variable, discrete or continuous, is less than or equal to a specific value, representing the sum or integration of values up to that point.

> **Example: Rolling a Die**
>
> Consider a simple experiment: rolling a standard six-sided die.
>
> * **Discrete Random Variable (X)**: The result of the roll, which can take discrete values {1,2,3,4,5,6}.
> * **Probability Density Function (pdf)**: For a fair die, each result has the same probability of occurring.
>
> $$p(x)=P(X=x)= \frac{1}{6} ,\quad \text{for } x=\{1,2,3,4,5,6\}$$
>
> **Calculation of the Cumulative Distribution Function (CDF)**
>
> The CDF, denoted as F(x), gives us the probability that the outcome of the roll is **less than or equal to** a specific value x. It is calculated by summing the probabilities of all outcomes up to that value.
>
> * **Probability of getting a 1 or less:** $$F(1)=P(X≤1)=P(X=1)=\frac{1}{6}$$
> * **Probability of getting a 2 or less:** $$F(2)=P(X≤2)=P(X=1)+P(X=2)=\frac{1}{6}+\frac{1}{6}=\frac{2}{6}$$
> * **Probability of getting a 3 or less:** $$F(3)=P(X≤3)=P(X=1)+P(X=2)+P(X=3)=\frac{1}{6}+\frac{1}{6}+\frac{1}{6}=\frac{3}{6}$$

<table><thead><tr><th>Resultado de x_i</th><th width="177.18359375">Probabilidad individual</th><th>Prob Acumulada</th></tr></thead><tbody><tr><td>1</td><td><span class="math">\frac{1}{6}</span></td><td><span class="math">\frac{1}{6}</span></td></tr><tr><td>2</td><td><span class="math">\frac{1}{6}</span></td><td><span class="math">\frac{2}{6}</span></td></tr><tr><td>3</td><td><span class="math">\frac{1}{6}</span></td><td><span class="math">\frac{3}{6}</span></td></tr><tr><td>4</td><td><span class="math">\frac{1}{6}</span></td><td><span class="math">\frac{4}{6}</span></td></tr><tr><td>5</td><td><span class="math">\frac{1}{6}</span></td><td><span class="math">\frac{5}{6}</span></td></tr><tr><td>6</td><td><span class="math">\frac{1}{6}</span></td><td>1</td></tr></tbody></table>

{% hint style="warning" %}
Once we have identified a random variable, we need a way to describe the probability that it takes different values or ranges of values. This is achieved through specific functions.
{% endhint %}

#### For Discrete Random Variables, Probability Mass Function (PMF)

The PMF of a discrete random variable X, denoted as $$p(x)$$ or $$P(X=x)$$, specifies the probability that X takes exactly the value x.

* **Properties:**
  1. $$0 \leq p(x) \leq 1$$ for all x.
  2. $$\sum_{\text{all } x} p(x) = 1$$ (the sum of the probabilities of all possible values is 1).
* **Example:**
  * If X is the result of rolling a fair die, $$p(x)=1/6$$ for $$x \in \{1,2,3,4,5,6\}$$, and $$p(x)=0$$ for any other x.
* The formula for the PMF is:

$$
P(X=k) =   {n \choose k}  \cdot p^k (1-p)^{n-k}
$$

Where:

* n is the number of trials (sample size).
* k is the number of successes (defective components).
* p is the probability of success in a single trial.
* $${n\choose k} = \frac{n!}{k!(n-k)!}$$ is the binomial coefficient, which counts the number of ways to choose k elements from a set of n.

> **Practical Example: Quality Inspection in a Production Lot**
>
> **Scenario:** An industrial engineer is supervising an electronic components production line. On average, 5% of the components produced are defective. The engineer randomly takes a sample of **10 components** from a large batch for a quality inspection.
>
> The interest is in the number of defective components found in that sample.
>
> **Random Variable:** Define the discrete random variable X as: X = "the number of defective components in the sample of 10".
>
> The possible values X can take are {0,1,2,3,4,5,6,7,8,9,10}.
>
> _Solution: In an Excel sheet, replace the values and plot the results._> ![](<../../../.gitbook/assets/Captura de pantalla 2025-06-11 a la(s) 5.46.30 p.m..png>)

#### For Continuous Random Variables: Probability Density Function (PDF)

For a continuous random variable X, the PDF, denoted as $$f(x)$$, does **not** give the probability that X is equal to a specific value — _this probability is always zero for continuous random variables_. Instead, the area under the curve of $$f(x)$$ over an interval \[a,b] represents the probability that X falls within that interval:

$$
P(a \leq X \leq b) = \int_a^b f(x) dx
$$

**Properties:**

1. $$f(x) \geq 0$$ for all x.
2. $$\int_{-\infty}^{\infty} f(x) dx = 1$$ (the total area under the density curve is 1).

#### Cumulative Distribution Function (CDF)

The CDF, denoted as $$F(x)$$, applies to both discrete and continuous random variables. It defines the probability that the random variable X takes a value less than or equal to x, $$F(x) = P(X \leq x)$$.

* **For Discrete Random Variables:** $$F(x) = \sum_{k \leq x} p(k)$$
* **For Continuous Random Variables:** $$F(x) = \int_{-\infty}^x f(t) dt$$
* **General Properties:**
  1. $$0 \leq F(x) \leq 1$$
  2. F(x) is a non-decreasing function (that is, if $$a < b$$, then $$F(a) \leq F(b)$$).
  3. $$\lim_{x \to -\infty} F(x) = 0$$ and $$\lim_{x \to \infty} F(x) = 1$$
* **Usefulness:** The CDF is very useful for calculating interval probabilities: $$P(a < X \leq b) = F(b) - F(a)$$

{% hint style="info" %}
The CDF plays a particularly important role in simulation, as it is the basis of the inverse transform method, a fundamental technique for generating random observations from a specific probability distribution using uniform random numbers.
{% endhint %}

{% hint style="danger" %}
This concept, which will be explored in detail in Chapter 3, highlights the importance of understanding the CDF.
{% endhint %}

***

### Expected Value, Variance, and Other Measures

To summarize the characteristics of a probability distribution and its associated random variable, various numerical measures are used.

The most important are _expected value and variance_.

{% tabs %}
{% tab title="Expected Value" %}
The expected value of a random variable X, denoted as $$E[X]$$ or $$\mu_X$$, represents the average value X would take if the random experiment were repeated a very large number of times. It is a measure of the central tendency of the distribution.

* For discrete X with PMF $$p(x):\quad E[X] = \sum_{\text{all }x} x \cdot p(x)$$
* For continuous X with PDF $$f(x):\quad E[X] = \int_{-\infty}^{\infty} x f(x) dx$$

Properties of Expected Value (if a and b are constants):

* $$E[a] = a$$
* $$E[aX] = aE[X]$$
* $$E[aX + b] = aE[X] + b$$
* $$E[X + Y] = E[X] + E[Y]$$ (for any random variables X and Y)
* $$E[g(X)] = \sum_x g(x)p(x)$$ or $$E[g(X)] = \int_{-\infty}^{\infty} g(x)f(x)dx$$
{% endtab %}

{% tab title="Variance" %}
The variance of a random variable X, denoted as $$Var(X)$$ or $$\sigma^2_X$$, measures the dispersion or variability of the values of X around its mean $$E[X]$$. A small variance indicates that the values of X tend to be close to the mean, while a large variance indicates that the values are more spread out.

$$
Var(X) = E[(X - E[X])^2] = E[X^2] - (E[X])^2
$$

**Properties of Variance:** If a and b are constants:

* $$Var(a) = 0$$
* $$Var(aX) = a^2 Var(X)$$
* $$Var(aX + b) = a^2 Var(X)$$
* If X and Y are independent: $$Var(X + Y) = Var(X) + Var(Y)$$
{% endtab %}

{% tab title="Standard Deviation" %}
The standard deviation, denoted as $$\sigma_X$$ or $$SD(X)$$, is the positive square root of the variance: $$\sigma_X = \sqrt{Var(X)}$$. It is expressed in the same units as the random variable X, making it easier to interpret as a typical measure of dispersion around the mean.

**Other Moments and Measures**

**Moments:** $$E[X^k]$$ is the k-th moment of X about the origin.

$$E[(X-\mu)^k]$$ is the k-th central moment.

The mean is the first moment about the origin, and the variance is the second central moment.

**Coefficient of Variation (CV)**

A relative measure of dispersion, defined as:

$$CV(X) = \frac{\sigma_X}{|E[X]|}, \quad \text{for } E[X] \neq 0$$

It is useful for comparing the variability of random variables with different means.
{% endtab %}
{% endtabs %}

These descriptive measures are fundamental in simulation for **two main reasons**:

<details>

<summary>1. Input Modeling</summary>

When selecting probability distributions for a model's input variables (e.g., service times, demand), their parameters are often directly related to the mean, variance, or other measures (e.g., the exponential distribution is defined by its mean, the normal by its mean and standard deviation).

</details>

<details>

<summary>2. Output Analysis</summary>

Performance metrics estimated from simulation runs are often expected values (e.g., average queue time, average resource utilization) and measures of their variability (e.g., cycle time variance, standard deviation of profit).

</details>

***

### Common Probability Distributions and Their Application in Industrial Engineering

Choosing an appropriate probability distribution to represent a random phenomenon is a critical step in building a valid simulation model. Below are some of the most commonly used distributions in industrial engineering, logistics, and production, along with their characteristics and typical applications.

| Distribution      | Type       | Key Parameters                            | Mean              | Variance                         | Common Applications in IE (Logistics/Production)                           |
| ----------------- | ---------- | ----------------------------------------- | ----------------- | -------------------------------- | -------------------------------------------------------------------------- |
| **Bernoulli**     | Discrete   | p (prob. of success)                      | p                 | p(1-p)                           | Defective/non-defective part, machine up/down.                             |
| **Binomial**      | Discrete   | n (trials), p                             | np                | np(1-p)                          | Number of defectives in a lot, number of customers buying a product.       |
| **Poisson**       | Discrete   | λ (mean rate)                             | λ                 | λ                                | Arrivals/hour, failures/day, defects/unit.                                 |
| **Geometric**     | Discrete   | p (prob. of success)                      | 1/p               | (1-p)/p²                         | Number of inspections until first defect.                                  |
| **Uniform Disc.** | Discrete   | a, b (min, max) or N values               | (a+b)/2           | ((b-a+1)²-1)/12                  | Random selection among N equally likely options.                           |
| **Uniform Cont.** | Continuous | a, b (min, max)                           | (a+b)/2           | (b-a)²/12                        | Uncertainty with only known limits, process times with no more info.       |
| **Exponential**   | Continuous | λ (rate) or μ=1/λ (mean)                  | 1/λ               | 1/λ²                             | Interarrival times (Poisson), service times, life of non-aging components. |
| **Normal**        | Continuous | μ (mean), σ (std. dev.)                   | μ                 | σ²                               | Part dimensions, errors, sums of RVs (CLT), task durations.                |
| **Triangular**    | Continuous | a (min), b (max), c (mode)                | (a+b+c)/3         | (a²+b²+c²-ab-ac-bc)/18           | Activity durations (PERT), process times with limited data.                |
| **Erlang**        | Continuous | k (shape), λ (rate)                       | k/λ               | k/λ²                             | Sum of k exponentials, repair times in phases.                             |
| **Weibull**       | Continuous | α (scale), β (shape)                      | αΓ(1+1/β)         | α²\[Γ(1+2/β)-(Γ(1+1/β))²]        | Failure times (wear-out, infant mortality, constant rate).                 |
| **Lognormal**     | Continuous | μₗₙ (mean of lnX), σₗₙ (std. dev. of lnX) | exp(μₗₙ + σₗₙ²/2) | exp(2μₗₙ + σₗₙ²) (exp(σₗₙ²) - 1) | Repair times, some multiplicative processes.                               |

### Central Limit Theorem (CLT)

The Central Limit Theorem (CLT) is one of the most important and remarkable results in probability theory and statistics, with profound implications for simulation.

> The Central Limit Theorem (CLT) states that, given a sufficiently large sample of independent and identically distributed random variables, the distribution of the sum or sample mean will approximate a normal distribution, regardless of the original distribution of the variables. This means that even if the individual data are not normally distributed, their mean will tend to follow a normal distribution as the sample size increases. This enables statistical inference and the use of techniques such as confidence intervals and hypothesis testing.

Formally, if we have a sequence of random variables:

$$
X_1, X_2, \ldots, X_n
$$

that are independent and identically distributed, with finite mean μ and finite variance $$\sigma^2$$, then as n (the number of variables) becomes large, the distribution of the sum

$$
S_n = X_1 + X_2 + \ldots + X_n
$$

approaches a normal distribution. More formally, the standardized variable

$$
Z_n = \frac{(S_n - n\mu)}{(\sigma \sqrt{n})} = \left(\frac{\overline{X_n} - \mu}{\frac{\sigma}{\sqrt{n}}} \right)
$$

converges in distribution to a standard normal variable N(0,1) as $$n \to \infty$$.

***

### Importance of the CLT in Simulation

{% tabs %}
{% tab title="Justification for Using the Normal Distribution" %}
Many phenomena in industrial engineering, such as the total time to complete a product that passes through multiple processing stages, can be considered as the sum of individual activity durations. Even if the individual activity times are not normally distributed, their sum (if there are enough activities and they are approximately independent) will tend to be normally distributed thanks to the CLT. This justifies the use of the normal distribution as a model for many aggregated quantities in systems.
{% endtab %}

{% tab title="Simulation Output Analysis" %}
In simulation, we are often interested in estimating the mean of a performance metric (e.g., the average customer waiting time). This is done by running the simulation multiple times (replications) and calculating the average of the metric obtained in each replication. If the number of replications is sufficiently large, the CLT implies that the distribution of this sample mean will be approximately normal. This property is fundamental for constructing confidence intervals for the true mean of the performance metric, which is essential for quantifying the precision of simulation-based estimates.
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
The CLT is powerful because it applies regardless of the original distribution of the $X\_i$ (as long as they have finite mean and variance). It is the bridge that connects the individual distributions of the random components of a system with the aggregate or average behavior of the system, which is frequently the focus of analysis in a simulation study.
{% endhint %}

***

### Parameter Estimation and Goodness-of-Fit Tests

#### What is a Goodness-of-Fit Test?

A goodness-of-fit test is a statistical tool used to determine how well a set of data fits an expected theoretical distribution. It evaluates how likely it is that an observed sample was generated from a population that follows a specific distribution.

#### What Is It For?

The goodness-of-fit test is mainly used to:

1. **Validate Statistical Models**: Helps verify if the chosen statistical model is appropriate for the data.
2. **Compare Distributions**: Allows comparing the theoretical distribution with the observed distribution.
3. **Decision Making**: Facilitates decisions in fields such as process quality, as understanding the data distribution can lead to better adjustments and solutions.

#### How Is It Used?

1. **Select the Theoretical Distribution**: Choose the distribution that best describes the data (e.g., Normal, Binomial, Poisson, etc.).
2. **Perform the Statistical Test**: Use tests such as Chi-square, Kolmogorov-Smirnov, or Anderson-Darling.
3. **Interpret the Results**: Analyze the p-value of the test to determine whether to reject or not the null hypothesis that the data follow the selected theoretical distribution.

{% hint style="warning" %}
This analysis is crucial in simulation studies, as it ensures that the results obtained are truly representative of the expected behavior under the assumed theoretical model. -crc-
{% endhint %}

***

#### Parameter Estimation

Once a candidate family of distributions has been selected (based on system knowledge and/or a preliminary analysis of the data, such as histograms), the next step is to estimate the parameters of that distribution using the available sample data

(e.g., observed service times, historical demands).

The most common methods include:

{% tabs %}
{% tab title="Method of Moments" %}
_Equates the sample moments_ (e.g., sample mean, sample variance) with the theoretical moments of the distribution (which are functions of the parameters) and solves the resulting system of equations for the parameters.

It is conceptually simple but not always the most efficient.
{% endtab %}

{% tab title="Maximum Likelihood Estimation (MLE)" %}
Finds the parameter values that maximize the likelihood of having observed the given data sample. MLE estimators usually have good statistical properties (consistency, asymptotic efficiency, asymptotic normality) and are widely used.

For many common distributions, there are closed-form formulas for MLE estimators; for others, numerical methods are required.
{% endtab %}
{% endtabs %}

***

#### Goodness-of-Fit Tests

After selecting a distribution and estimating its parameters, [_**it is crucial to formally assess how well that fitted theoretical distribution agrees with the observed empirical data**_](#user-content-fn-1)[^1]. Goodness-of-fit tests quantify this agreement.

**Hypotheses:**

* Null Hypothesis $$(H_0)$$: The observed data come from the specified theoretical distribution.
* Alternative Hypothesis $$(H_1)$$: The observed data do not come from the specified theoretical distribution.

**Chi-square ($\chi^2$) Test:**

1. Applicable to both discrete and continuous data

{% hint style="warning" %}
the latter must be grouped into intervals or "bins".
{% endhint %}

2. Compares the observed frequencies $$(O_i)$$ in each category or interval with the expected frequencies $$(E_i)$$ under the null hypothesis.
3. The test statistic is $$\chi^2 = \sum (O_i - E_i)^2 / E_i$$.
4. If the value of the statistic is large (exceeding a critical value from the _Chi-square_ distribution with certain degrees of freedom, or if the p-value is small), we reject $$H_0$$, concluding that the theoretical distribution is not a good fit.

**Kolmogorov-Smirnov (K-S) Test:**

1. Mainly for _**continuous data**_ (though there are adaptations for discrete).
2. Compares the empirical cumulative distribution function $$(F_e(x))$$, built from the data, with the theoretical CDF $$(F_t(x))$$ of the hypothesized distribution.
3. The test statistic is $$D = \max_x |F_e(x) - F_t(x)|$$, the maximum absolute vertical difference between the two CDFs.
4. If D is large (exceeding a critical value, or if the p-value is small), we reject $$H_0$$. It is more sensitive to differences in shape, median, or spread than the Chi-square test.

**Interpretation of the p-value**

A small p-value (typically < 0.05 or < 0.10) indicates that there is enough evidence to reject the null hypothesis, suggesting that the chosen distribution does not fit the data well. A large p-value does not "prove" that $$H_0$$ is true, only that _**there is not enough evidence to reject it.**_

{% hint style="warning" %}
_Input modeling is an iterative step._ If a distribution does not pass goodness-of-fit tests, another family of distributions should be considered, or the empirical distribution derived from the data may be used directly if the sample size is sufficiently large. The accuracy of the overall simulation model depends largely on the accuracy of its input models; hence the saying: **"garbage in, garbage out" (GIGO) - crc-**
{% endhint %}

***

### Bibliography

1. Montgomery, D. C., & Runger, G. C. (2018). _Applied Statistics and Probability for Engineers_ (7th ed.). Wiley.
2. Walpole, R. E., Myers, R. H., Myers, S. L., & Ye, K. E. (2017). _Probability and Statistics for Engineering and the Sciences_ (9th ed.). Pearson Education.
3. Ross, S. M. (2014). _Introduction to Probability Models_ (11th ed.). Academic Press.
4. Leemis, L. M., & Park, S. K. (2006). _Discrete-Event Simulation: A First Course_. (Chapters 6, 7, and 9)
5. Winston, W. L. (2005). _Operations Research: Applications and Algorithms_. (Chapter 12)
6. Hillier, F. S., & Lieberman, G. J. (2010). _Introduction to Operations Research_. (Probability and statistics chapters)

[^1]: Note, important!!
