# Chapter Three: Number Generation and Random Variables

## Chapter Three: Generation of Random Numbers and Random Variables

### Chapter Objectives

1. Explain the importance of random number generation in stochastic simulation.
2. Describe the characteristics and requirements of a good pseudo-random number generator (PRNG).
3. Understand the basic algorithms for generating uniform random numbers (linear congruential generator).
4. Apply transformation techniques to generate random variables with specific probability distributions from uniform random numbers.
5. Analyze and validate the quality of sequences of random numbers and random variables generated.
6. Use software tools and libraries (such as Excel, Python, AnyLogic) to generate and test random numbers and random variables.

***

{% hint style="warning" %}
Random number generation is fundamental to process simulation, as it allows for modeling the uncertainty and variability inherent in complex systems. High-quality random numbers ensure realistic and accurate simulations, which is crucial for analysis, prediction, and decision-making in fields such as engineering, economics, and computer science. For this reason, the use of efficient pseudorandom number generators and validating their suitability through statistical testing are essential pillars of any simulation environment. -crc-
{% endhint %}

### Introduction

In stochastic simulation, random numbers and random variables are fundamental building blocks. Through them, we can model uncertainty, variability, and chance events that occur in real systems—such as arrival times, service times, demand, machine failures, and more.

However, computers are deterministic machines; they cannot generate truly random numbers, but only **pseudo-random numbers**—sequences that "appear" random but are produced by mathematical algorithms.

**A solid understanding of random number and random variable generation is essential** for building valid and reliable simulation models.

***

### 1. Pseudo-Random Number Generators (PRNGs)

#### What Are Pseudo-Random Numbers?

* A **pseudo-random number** is a value produced by a deterministic algorithm that simulates randomness.
* In simulation, we usually require random numbers uniformly distributed between 0 and 1 (Uniform\[0,1]).
* These numbers serve as a basis for generating random variables with any distribution.

#### Requirements for a Good PRNG

A good random number generator should:

1. Produce numbers uniformly distributed in the interval \[0,1].
2. Have a long period before repeating the sequence.
3. Be computationally efficient (fast).
4. Be reproducible (the same seed produces the same sequence).
5. Pass statistical tests for independence and randomness.

#### Linear Congruential Generator (LCG)

One of the most common and oldest algorithms for generating pseudo-random numbers.

The LCG is defined by the recurrence:

$$
X_{n+1} = (a X_n + c) \mod m
$$

where:

* X\_0 is the seed (initial value),
* a is the multiplier,
* c is the increment,
* m is the modulus.

The normalized random number is:

$$
U_n = \frac{X_n}{m}
$$

**Example**

Let $$a = 5, c = 1, m = 16, X_0 = 7$$

Compute the first four random numbers:

* $$X_1 = (5*7 + 1) \mod 16 = 36 \mod 16 = 4, U_1 = 4/16 = 0.25$$
* $$X_2 = (5*4 + 1) \mod 16 = 21 \mod 16 = 5, U_2 = 5/16 = 0.3125$$
* $$X_3 = (5*5 + 1) \mod 16 = 26 \mod 16 = 10, U_3 = 10/16 = 0.625$$
* $$X_4 = (5*10 + 1) \mod 16 = 51 \mod 16 = 3, U_4 = 3/16 = 0.1875$$

**Parameters in Practice**

* The choice of parameters a, c, and m is critical for the quality of the generator.
* In practice, well-tested generators are used (e.g., Mersenne Twister in Python).

***

### 2. Statistical Tests for Random Numbers

To ensure the quality of the numbers generated, several statistical tests are used:

* **Uniformity Test**: Checks whether the numbers are uniformly distributed in \[0,1].
* **Independence Test**: Checks for correlations or patterns between numbers.
* **Runs Test**: Detects long sequences of increasing or decreasing numbers.
* **Chi-Square Test**: Compares observed frequencies with expected frequencies.
* **Kolmogorov-Smirnov Test**: Compares the empirical distribution with the uniform distribution.

> In simulation, it is recommended to use established libraries (e.g., NumPy, random in Python) rather than building your own generators.

***

### 3. Generation of Random Variables

The goal is to generate random variables with a specific distribution (e.g., Exponential, Normal, Poisson) from uniform random numbers.

#### General Steps

1. Generate a uniform random number U in \[0,1].
2. Transform U using a method appropriate for the desired distribution.

#### Methods for Generating Random Variables

**a) Inverse Transform Method**

If $F(x)$ is the cumulative distribution function (CDF) of the desired distribution and $U$ is Uniform\[0,1], then:

$$
X = F^{-1}(U)
$$

will have the desired distribution.

*   **Example:** For the Exponential distribution with mean $1/\lambda$:

    $$
    F(x) = 1 - e^{-\lambda x} \implies x = -\frac{1}{\lambda} \ln(1 - U)
    $$

**b) Acceptance-Rejection Method**

* Used when the inverse CDF is not easily obtainable.
* Involves generating candidate values and accepting or rejecting them according to a rule.

**c) Other Methods**

* **Box-Muller Method** for generating Normal random variables.
* **Composition and convolution** when dealing with sums of random variables.

***

### 4. Generation in Excel, Python, and AnyLogic

#### Excel

* `RAND()`: Generates Uniform\[0,1].
* `RANDBETWEEN(a,b)`: Generates random integers between a and b.
* Use formulas to transform to other distributions.

#### Python

* `random.random()`: Uniform\[0,1].
* `numpy.random`: Library with generators for many distributions (normal, exponential, Poisson, etc.)
* `scipy.stats`: Advanced random variable generation and statistical tests.

#### AnyLogic

* Built-in functions: `uniform()`, `exponential()`, `normal()`, `poisson()`, etc.
* Can specify parameters and use in models directly.

***

### 5. Validation and Analysis of Generated Variables

* Always check that the generated data matches the expected theoretical distribution.
* Use histograms, summary statistics, and formal statistical tests.
* In simulation, the accuracy of random variable generation directly affects the quality of results.

***

## Step By Step Guide

#### Pseudorandom number generation: Lehmer's method.

Stochastic simulation, which is at the core of modeling most industrial engineering systems, is fundamentally based on the ability to generate sequences of numbers that behave as if they were realizations of uniformly distributed random variables in the interval (0,1). These numbers, commonly denoted as

$$U_i∼U(0,1)$$

They are the basic ingredient for later generating random variables from more complex distributions (Exponential, Normal, Poisson, etc.) that represent the various uncertain phenomena in a system.

**Pseudo-Random vs. Truly Random Numbers**

Computers are deterministic machines. Therefore, they cannot generate truly random numbers in the strict sense.

Instead, they use mathematical algorithms to produce sequences of numbers that appear random and that pass various statistical tests of randomness.

These are called **pseudo-random numbers**. The desirable properties of a sequence of pseudo-random numbers.

{% tabs %}
{% tab title="Uniformity" %}
The numbers should be uniformly distributed over the interval (0,1)
{% endtab %}

{% tab title="Independence" %}
Each generated number should be independent of the previous numbers in the sequence.
{% endtab %}

{% tab title="Long Period" %}
The sequence will eventually repeat (it is periodic). The period (length of the sequence before it begins to repeat) should be as long as possible, ideally much longer than the number of random numbers needed for any simulation.
{% endtab %}

{% tab title="Reproducibility" %}
Given the same initial seed, the generator must produce exactly the same sequence of numbers. This is crucial for model debugging and for comparing different system configurations under the same random conditions.
{% endtab %}

{% tab title="Computational Efficiency" %}
The algorithm must be fast at generating numbers, as a simulation may require millions of them.
{% endtab %}

{% tab title="Portability" %}
The generator must produce the same (or statistically equivalent) results on different computing platforms.
{% endtab %}
{% endtabs %}

#### Linear Congruential Generators (LCGs)

Linear Congruential Generators are a class of algorithms for generating pseudorandom numbers. They operate using a linear recurrence relation. The general formula for a LCG is:

$$
[ X_{i+1} = (aX_i + c) \mod m ]
$$

where:

* $$X_i$$ is the i-th integer in the sequence.
* $$X_o$$ is the seed or initial value.
* a is the multiplier.
* c is the increment.
* m is the modulus.

{% hint style="info" %}
The parameters $$a, c, m, and X_0$$ are non-negative integers. The term $$mod\ m$$ means the remainder of dividing $$(aX_i+c)$$ by m. The pseudorandom numbers $$U_i$$ in (0,1) are obtained as $$U_i=X_i/m.$$
{% endhint %}

**Example**

Consider the following values:

* ( a = 5 )
* ( c = 3 )
* ( m = 16 )
* Seed $$(( X_0 )) = 7$$

The sequence can be generated as follows:

1. $$( X_1 = (5 \times 7 + 3) \mod 16 = 38 \mod 16 = 6 )$$
2. $$( X_2 = (5 \times 6 + 3) \mod 16 = 33 \mod 16 = 1 )$$
3. $$( X_3 = (5 \times 1 + 3) \mod 16 = 8 \mod 16 = 8 )$$

We repeat this process to generate more numbers. This method is simple and efficient, but the choice of ( a ), ( c ), and ( m ) is crucial to obtain good randomness and a long period.

**Lehmer's Method (Multiplicative Congruential Generator)**

**Lehmer's Method**

Lehmer's Method, also known as the Multiplicative Congruential Generator, is an algorithm for generating pseudorandom numbers through a recursive relation of the form:

$$
[ X_{n+1} = (a \times X_n) \mod m ]
$$

where:

* a is the multiplier,
* m is the modulus,
* $$X_0$$ is the initial seed of the generator.

This method is a variant of the linear congruential generator, but does not include the constant increment term ( c ). The values ​​of ( a ) and ( m ) are carefully chosen to maximize the period length and the quality of the randomness.

**Example**

Suppose ( a = 7 ), ( m = 31 ), and the initial seed ( $$X_0 = 3$$ ).

1. We calculate the first number in the sequence:

$$[ X_1 = (7 \times 3) \mod 31 = 21 ]$$ 2. We calculate the second number:

$$[ X_2 = (7 \times 21) \mod 31 = 23 ]$$ 3. We calculate the third number:

$$[ X_3 = (7 \times 23) \mod 31 = 6 ]$$

We can continue this process to generate more numbers in the sequence.

_**Parameter Choice:**_

The quality of the Lehmer generator depends critically on the choice of $$m, a, and X_0​.$$

1. **Modulus m:** Must be a large prime number. A common choice, especially on 32-bit machines, is $$m = 2^{31} − 1$$, which is a Mersenne prime.
2. **Multiplier a:** Must be carefully chosen to ensure a full (or nearly full) period and good statistical properties. A full period for a multiplicative generator with prime modulo m is $$m−1$$, which means that the sequence $$X_1​,X_2​,…,X_{m−1}$$​ contains all integers from 1 to m−1 exactly once, in some order.
3. Extensive research has been done to find _"good"_ multipliers. For example, for $$m=2^{31}−1$$, a commonly cited multiplier is $$a=7^5=16807$$, although others such as $$a=48271$$ have also been proposed for their good properties and implementation efficiency.

* **Seed** $$X_0$$**​:** Must be an integer between 1 and m−1. Different seeds will produce different (albeit related) sequences.
* **Implementation:** One challenge in the implementation is to calculate $$aX_i$$​ without overflowing if the product exceeds the computer's maximum integer representation capacity, before taking the modulo m.

Generating $$U(0,1)$$ numbers is the first critical step. The quality of these numbers directly impacts the validity of the entire simulation study.

{% hint style="danger" %}
If the base generator is flawed (e.g., it's not uniform, or the numbers are not independent), then the random variables generated from it will also be flawed, and the simulation results will be unreliable, no matter how sophisticated the rest of the model is.
{% endhint %}

***

#### Randomness and Independence Tests

Since pseudorandom number generators are deterministic algorithms, it is crucial to subject their output sequences to rigorous statistical tests to assess whether they behave sufficiently similarly to truly random and independent sequences from a distribution. U(1,0)

{% hint style="warning" %}
No generator is perfect, and no test can "prove" that a generator is good; rather, tests can reveal whether a generator is "bad" by failing to meet certain statistical criteria.
{% endhint %}

The two fundamental properties that we want to evaluate are **uniformity** and **independence**.

**Uniformity Tests**

{% tabs %}
{% tab title="Chi-square Test (χ2)" %}
It is a statistical tool used to assess uniformity in a sequence of pseudorandom numbers. It involves comparing the observed frequencies of numbers in different intervals with the expected frequencies, which allows us to determine whether the numbers are uniformly distributed.

1. The interval (0,1) is divided into k subintervals of equal length (1/k).
2. A sample of N random numbers $$U_i$$​ is generated.
3. The number of observations $$(O_j​)$$ that fall within each subinterval j is counted.
4. Under the null hypothesis of uniformity, the expected frequency $$(E_j​)$$ for each subinterval is $$N/k.$$
5. The test statistic is calculated: $$X_0^2​=∑_{j=1}^k \frac{​(Oj​−Ej​)^2}{Ej}​.$$
6. This statistic is compared to a critical value from the Chi-square distribution with k−1 degrees of freedom and a significance level α (e.g., 0.05). If $$χ_0^2$$​ is greater than the critical value (or if the p-value is less than α), the uniformity hypothesis is rejected.

***
{% endtab %}

{% tab title="Kolmogorov-Smirnov (K-S) Test" %}
1. Sort the N generated numbers $$U(1)​≤U(2)​≤…≤U(N)$$​.
2. Calculate the empirical cumulative distribution function (CDF) $$F_e​(x)=(number\ of\ U_i​≤x)/N$$.
3. For a U(0,1) distribution, the theoretical CDF is $$F_t​(x)=x\ for\ 0≤x≤1$$.
4. The K-S test statistic is the maximum absolute vertical difference between $$F_e​(x)\ and\ F_t​(x): D_N​=max_{0≤x≤1}​∣F_e​(x)−F_t​(x)∣$$. In practice, it is calculated as

$$
D_N = \max\left\{ \max_{1 \le j \le N} \left( \frac{j}{N} - U_{(j)} \right), \max_{1 \le j \le N} \left( U_{(j)} - \frac{j-1}{N} \right) \right\}
$$

1. $$D_N​$$ is compared to a critical value of the Kolmogorov-Smirnov distribution for sample size N and significance level α. _**If**_ $$D_N$$_**​ is greater than the critical value, the uniformity hypothesis is rejected.**_
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Chi-square Example" %}
Let's imagine we have collected $$n=100$$ observations of a continuous variable and we want to verify whether these data can be modeled by a normal distribution.

**1. Estimate Parameters and Define Intervals**

First, we need the mean and standard deviation of our sample. Suppose for our data:

* Sample mean $$(\bar{x}) = 50$$
* Sample standard deviation $$(s) = 10$$

Next, we divide the data range into k intervals. It is crucial that the expected frequency for each interval $$(E_i)$$ be sufficiently large, typically $$E_i \ge 5$$. For this example, we will select k=5 intervals.

The interval boundaries are defined and then standardized (converted to Z scores) using $$\bar{x} \ y\ s$$:clap:

| Interval (Original Data) | Límit Z (Estandarizated)           |
| ------------------------ | ---------------------------------- |
| X < 40                   | $$Z < (40-50)/10 = -1.0$$          |
| $$40 \le X < 45$$        | $$-1.0 \le Z < (45-50)/10 = -0.5$$ |
| $$45 \le X < 55$$        | $$-0.5 \le Z < (55-50)/10 = 0.5$$  |
| $$55 \le X < 60$$        | $$0.5 \le Z < (60-50)/10 = 1.0$$   |
| $$X \ge 60$$             | $$Z \ge 1.0$$                      |

**2. Calculate Observed Frequencies (O\_i)**

We count the number of data in our sample that fall within each of the defined intervals:

| Interval          | Observed Frecuence (O\_i) |
| ----------------- | ------------------------- |
| X < 40            | 18                        |
| $$40 \le X < 45$$ | 15                        |
| $$45 \le X < 55$$ | 36                        |
| $$55 \le X < 60$$ | 13                        |
| $$X \ge 60$$      | 18                        |
| **Total**         | **100**                   |

**3. Calculate Expected Frequencies (E\_i)**

For each interval, we determine the probability that a value from a standard normal distribution falls within its Z limits. We then multiply this probability by the total sample size (n=100) to obtain E\_i.

| Interval          | Límit Z               | P(Interval) (Prob. Normal Stándar)      | E\_i = n . P(Interval})      |
| ----------------- | --------------------- | --------------------------------------- | ---------------------------- |
| X < 40            | $$Z < -1.0$$          | $$P(Z < -1.0) \approx 0.1587$$          | $$100 \cdot 0.1587 = 15.87$$ |
| $$40 \le X < 45$$ | $$-1.0 \le Z < -0.5$$ | $$P(-1.0 \le Z < -0.5) \approx 0.1498$$ | $$100 \cdot 0.1498 = 14.98$$ |
| $$45 \le X < 55$$ | $$-0.5 \le Z < 0.5$$  | $$P(-0.5 \le Z < 0.5) \approx 0.3829$$  | $$100 \cdot 0.3829 = 38.29$$ |
| $$55 \le X < 60$$ | $$0.5 \le Z < 1.0$$   | $$P(0.5 \le Z < 1.0) \approx 0.1498$$   | $$100 \cdot 0.1498 = 14.98$$ |
| $$X \ge 60$$      | $$Z \ge 1.0$$         | $$P(Z \ge 1.0) \approx 0.1587$$         | $$100 \cdot 0.1587 = 15.87$$ |
| **Total**         |                       | $$\approx 1.0$$                         | $$\approx 100$$              |

{% hint style="warning" %}
The probabilities $$P(\text{Interval})$$ are obtained from a standard normal distribution table (Z-table) or using statistical software.\_
{% endhint %}

**4. Calculate the** $$\chi^2$$ **Statistic**

We use the observed (O\_i) and expected (E\_i) frequencies to calculate the $$\chi^2$$ statistic

| Interval          | O\_i | E\_i  | O\_i - E\_i | (O\_i - E\_i)^2 | (O\_i - E\_i)^2 / E\_i    |
| ----------------- | ---- | ----- | ----------- | --------------- | ------------------------- |
| $$X < 40$$        | 18   | 15.87 | 2.13        | 4.5369          | $$\approx 0.2859$$        |
| $$40 \le X < 45$$ | 15   | 14.98 | 0.02        | 0.0004          | $$\approx 0.00002$$       |
| $$45 \le X < 55$$ | 36   | 38.29 | -2.29       | 5.2441          | $$\approx 0.1369$$        |
| $$55 \le X < 60$$ | 13   | 14.98 | -1.98       | 3.9204          | $$\approx 0.2617$$        |
| $$X \ge 60$$      | 18   | 15.87 | 2.13        | 4.5369          | $$\approx 0.2859$$        |
| **Total**         |      |       |             |                 | $$\chi^2 \approx 0.9704$$ |

The calculated value of the statistic is $$\chi^2_{calculated} \approx 0.9704$$.

**5. Determine Degrees of Freedom (df)**

The degrees of freedom for this test are calculated as:

$$
gl = k - 1 - m
$$

Where:

* k = number of intervals (5 in our example).
* m = number of distribution parameters estimated from the sample. For a normal distribution, we estimate the mean and standard deviation, so m = 2.

So, $$df = 5 - 1 - 2 = 2$$

**6. Making a Statistical Decision**

1. We choose a significance level, typically $$\alpha = 0.05$$.
2. We look for the critical value of $$\chi^2$$ in a Chi-square distribution table (or using software) for $$df=2\ and\ \alpha=0.05$$.\
   The value $$\chi^2_{critical}(2, 0.05)$$ is approximately 5.991.

**Decision Rule:**

* If $$\chi^2_{calculated} > \chi^2_{critical}$$, we reject H\_0.
* If $$\chi^2_{calculated} \le \chi^2_{critical}$$, we fail to reject H\_0.

In our example: $$0.9704 \le 5.991.$$

**7. Conclusion**

Since the calculated value of $$\chi^2 (0.9704)$$ is less than the critical value (5.991) for a significance level of 0.05, we fail to reject the null hypothesis (H\_0).

This means that we do not have sufficient statistical evidence to conclude that the sample data do not follow a normal distribution.

***
{% endtab %}

{% tab title="K-S Test Example" %}
### Kolmogorov-Smirnov (KS) Normality Test

***

**Hypothesis**

* $$H_0$$: The data follow a normal distribution.
* $$H_1$$: The data do not follow a normal distribution.

***

**Test Statistic (D)**

The Kolmogorov-Smirnov test statistic, D, is the maximum absolute difference between the sample CDF $$S_n(x)$$ and the theoretical CDF of the normal distribution F(x):

$$
D = \sup_x |S_n(x) - F(x)|
$$

For practical calculations with an ordered sample $$x_{(1)}, x_{(2)}, \ldots, x_{(n)}$$:\
First, $$D^+\ and\ D^-$$ are calculated:

$$D^+ = \max_{1 \le i \le n} \left( \frac{i}{n} - F(x_{(i)}) \right)$$

$$
D^- = \max_{1 \le i \le n} \left( F(x_{(i)}) - \frac{i-1}{n} \right)
$$

Then, the statistic D is the maximum of these two values:

$$
D = \max(D^+, D^-)
$$

Where:

* n is the sample size. \* $$x_{(i)}$$ is the ith smallest value in the sample (ordered data).
* $$S_n(x_{(i)}) = i/n$$ is the value of the ECDF at $$x_{(i)}$$
* $$F(x_{(i)})$$ is the value of the theoretical CDF of the normal distribution evaluated at $$x_{(i)}$$, using the specified mean $$(\mu)$$ and standard deviation $$(\sigma)$$ (or estimated from the sample for the Lilliefors test).

***

**Step-by-Step Example**

Suppose we have a small sample of n = 5 observations: $$X = {10, 12, 15, 16, 20}$$. We want to test whether they come from a normal distribution.

**Steps:**

1. **Sort the Data:**\
   The data are already sorted: $$x_{(1)}=10, x_{(2)}=12, x_{(3)}=15, x_{(4)}=16, x_{(5)}=20$$.
2. **Estimate Normal Distribution Parameters (for Lilliefors test):**\
   We calculate the sample mean $$(\bar{x})$$ and the sample standard deviation (s).
3. $$\bar{x} = (10+12+15+16+20)/5 = 73/5 = 14.6$$
4. $$s = \sqrt{\frac{\sum (x_i - \bar{x})^2}{n-1}} = \sqrt{\frac{(10-14.6)^2 + (12-14.6)^2 + (15-14.6)^2 + (16-14.6)^2 + (20-14.6)^2}{4}}$$
5. $$s = \sqrt{\frac{(-4.6)^2 + (-2.6)^2 + (0.4)^2 + (1.4)^2 + (5.4)^2}{4}} = \sqrt{\frac{21.16 + 6.76 + 0.16 + 1.96 + 29.16}{4}} = \sqrt{\frac{59.2}{4}} = \sqrt{14.8} \approx 3.847$$
6.  **Calculate** $$F(x_{(i)}), S_n(x_{(i)})$$ **and the differences:**\
    For each $$x_{(i)}$$, we calculate $$F(x_{(i)})$$ using the one-normal CDF with $$\mu=14.6$$ and $$\sigma=3.847$$. This involves standardizing each $$x_{(i)}$$ to $$z_{(i)} = (x_{(i)} - \bar{x})/s$$ and then finding $$P(Z \le z_{(i)})$$

    |  i  | x\_(i) |    z\_(i) = x\_(i)-14.6)/3.847$    | $F(x\_{(i)}) = P(Z \le z\_{(i)})$ | S\_n(x\_(i)) = i/n | $\frac{i-1}{n}$ | $D\_i^+ = \frac{i}{n} - F(x\_{(i)})$ | $D\_i^- = F(x\_{(i)}) - \frac{i-1}{n}$ |
    | :-: | :----: | :--------------------------------: | :-------------------------------: | :----------------: | :-------------: | :----------------------------------: | :------------------------------------: |
    |  1  |   10   | $$(10-14.6)/3.847 \approx -1.196$$ |         $$\approx 0.1159$$        |      1/5 = 0.2     |    0/5 = 0.0    |         0.2 - 0.1159 = 0.0841        |          0.1159 - 0.0 = 0.1159         |
    |  2  |   12   | $$(12-14.6)/3.847 \approx -0.676$$ |         $$\approx 0.2495$$        |      2/5 = 0.4     |    1/5 = 0.2    |         0.4 - 0.2495 = 0.1505        |          0.2495 - 0.2 = 0.0495         |
    |  3  |   15   |  $$(15-14.6)/3.847 \approx 0.104$$ |         $$\approx 0.5414$$        |      3/5 = 0.6     |    2/5 = 0.4    |         0.6 - 0.5414 = 0.0586        |          0.5414 - 0.4 = 0.1414         |
    |  4  |   16   |  $$(16-14.6)/3.847 \approx 0.364$$ |         $$\approx 0.6420$$        |      4/5 = 0.8     |    3/5 = 0.6    |         0.8 - 0.6420 = 0.1580        |          0.6420 - 0.6 = 0.0420         |
    |  5  |   20   |  $$(20-14.6)/3.847 \approx 1.404$$ |         $$\approx 0.9198$$        |      5/5 = 1.0     |    4/5 = 0.8    |         1.0 - 0.9198 = 0.0802        |          0.9198 - 0.8 = 0.1198         |
7.  **Calcular el Estadístico D:**\
    $$D^+ = \max(0.0841, 0.1505, 0.0586, 0.1580, 0.0802) = 0.1580$$\
    $$D^- = \max(0.1159, 0.0495, 0.1414, 0.0420, 0.1198) = 0.1414$$

    $$D = \max(D^+, D^-) = \max(0.1580, 0.1414) = 0.1580$$
8. **Tomar una Decisión Estadística:**
   * Se elige un nivel de significancia $$\alpha$$ (ej., $$\alpha = 0.05$$).
   * El valor $$D_{calculado} = 0.1580$$ se compara con un valor crítico $$D_{critico}$$. Para la prueba de Lilliefors, ya que $$\mu\ y\ \sigma$$ fueron estimados, los valores críticos son diferentes de la prueba KS estándar y dependen de n.
   * Por ejemplo, para n=5 y $$\alpha=0.05$$, el valor crítico de Lilliefors es aproximadamente 0.337.
   * **Regla de decisión:** Si $$D_{calculado} > D_{critico}$$, se rechaza H\_0. De lo contrario, no se rechaza H\_0.
   * En nuestro ejemplo: 0.1580 < 0.337.
9. **Conclusión:**\
   Como $$D_{calculado}$$ (0.1580) es menor que el valor crítico de Lilliefors (0.337) para $$\alpha=0.05$$, no rechazamos la hipótesis nula (H\_0). Concluimos que no hay evidencia suficiente para afirmar que los datos no siguen una distribución normal.

***

**Consideraciones Adicionales**

{% hint style="info" %}
La prueba de Kolmogorov-Smirnov es generalmente más potente que la prueba $$\chi^2$$ para probar la normalidad de datos continuos, especialmente con muestras pequeñas.

Cuando los parámetros de la distribución normal (media y/o desviación estándar) se estiman a partir de la muestra, es crucial utilizar los valores críticos de la **prueba de Lilliefors**, no los de la prueba KS estándar, ya que estos últimos serían demasiado conservadores, llevarían a no rechazar H\_0 con demasiada frecuencia.

La prueba es sensible a desviaciones en el centro, las colas y la forma de la distribución.
{% endhint %}

***
{% endtab %}
{% endtabs %}

***

#### **Pruebas de Independencia**

Estas pruebas verifican si los números generados son independientes entre sí (es decir, si el valor de un número no influye en el valor de los siguientes).

1. **Prueba de Rachas (Runs Test):** Una "racha" es una subsecuencia de observaciones con una propiedad común.
   1. Por ejemplo, una racha ascendente es una secuencia de números donde cada uno es mayor que el anterior. Se analiza el número total de rachas en la secuencia. Si hay demasiadas o muy pocas rachas en comparación con lo que se esperaría de una secuencia verdaderamente independiente, se rechaza la hipótesis de independencia.
2. **Prueba de Autocorrelación:** Mide la correlación lineal entre números separados por un cierto "retraso" (lag) $$k$$ en la secuencia. La autocorrelación de lag k, $$ρ_k$$​, estima la correlación entre $$U_i$$​ y $$U_i+k$$​. Para una secuencia independiente, se espera que todas las autocorrelaciones (para $$k≥1$$) sean cercanas a cero. Se construye un estadístico de prueba (basado en la aproximación Normal para $$ρ^​k$$​ cuando N es grande) para verificar si $$ρ_k$$​ es significativamente diferente de cero.

{% hint style="warning" %}
Es importante destacar que un generador debe pasar un conjunto diverso y riguroso de estas pruebas estadísticas antes de ser considerado aceptable para su uso en estudios de simulación serios. El hecho de que una secuencia pase una prueba no garantiza que sea "perfecta", solo que no se ha encontrado evidencia en contra de la hipótesis de uniformidad o independencia bajo esa prueba particular.
{% endhint %}

***

#### Métodos de generación de variables aleatorias.

Una vez que se dispone de una fuente fiable de números pseudoaleatorios $$U_i∼U(0,1)$$, el siguiente paso es transformar estos números uniformes en realizaciones de variables aleatorias que sigan las distribuciones de probabilidad específicas (Exponencial, Normal, Poisson, etc.) que se han identificado como modelos para los componentes inciertos del sistema bajo estudio.

Existen varios métodos para realizar esta transformación.

**Método de la Transformada Inversa (MTI)**

Este es el método más fundamental y, cuando es aplicable, a menudo el más eficiente y directo

1. **Principio** Se basa en el hecho de que si X es una variable aleatoria con función de distribución acumulada (FDA) continua y estrictamente creciente $$F(x)$$, y U es una variable aleatoria $$U(0,1)$$, entonces la variable aleatoria $$Y=F−1(U)$$ tiene la misma distribución que X. Aquí, $$F−1(u)$$ es la función inversa de la FDA, definida como el valor y tal que $$F(y)=u$$.
   1.  **Algoritmo para V.A. Continuas:**

       Generar un número $$u∼U(0,1)$$.

       1. Calcular $$x=F−1(u)$$. Este x es la observación deseada de la V.A. X.
   2.  **Aplicación a V.A. Discretas:**

       Si X es discreta con $$FMP\ p(xj​)$$ y $$FDA F(xj​)=P(X≤xj​)$$, se genera $$u∼U(0,1)$$ y se busca el valor _xj​_ tal que $$F(xj−1​)<u≤F(xj​)\ (donde\ F(x0​)=0)$$. Entonces _x&#x6A;_&#x200B; es la observación generada. Esto se puede implementar mediante una búsqueda secuencial o más eficiente.

* **Ejemplos de Aplicación Directa, donde F−1(u) tiene forma cerrada:**
  * **Uniforme Continua U(a,b):** $$F(x)=(x−a)/(b−a)$$. Invirtiendo, $$x=a+(b−a)u$$.
  * **Exponencial (media** $$μ=1/λ$$**):** $$F(x)=1−e−λx$$. Invirtiendo, $$x=−(1/λ)ln(1−u)$$. Dado que si $$u∼U(0,1)$$, entonces $$1−u∼U(0,1)$$, se puede usar $$x=−(1/λ)ln(u)$$ de forma equivalente.
  * **Triangular:** La FDA es lineal por tramos, y su inversa también se puede encontrar analíticamente por tramos.
  * **Weibull:** $$F(x)=1−e−(x/α)β$$. Invirtiendo, $$x=α(−ln(1−u))1/β$$.

<details>

<summary><strong>Ventajas:</strong></summary>

Es exacto si $$F−1(u)$$ se puede calcular con precisión. Es intuitivo. Preserva la monotonicidad (si $$u1​<u2$$​, entonces $$F−1(u1​)≤F−1(u2​)$$), lo cual es útil para algunas técnicas de reducción de varianza.

</details>

<details>

<summary><strong>Desventajas:</strong></summary>

La función $$F−1(u)$$ no siempre tiene una expresión analítica simple o de forma cerrada

(ej. para las distribuciones Normal, Gamma, Beta, Binomial, Poisson con parámetros grandes). En estos casos, se requieren aproximaciones numéricas o métodos alternativos.

</details>

***

#### Método de Aceptación-Rechazo (A-R).

Este es un método general que se puede utilizar cuando el MTI es difícil o ineficiente de aplicar

Supongamos que queremos generar una V.A. X con FDP $$f(x)$$. Se elige otra FDP "mayorante" $$g(x)$$ (de la cual sea fácil generar variables, por ejemplo, usando MTI) y una constante $$c≥1$$ tal que $$f(x)≤c⋅g(x)$$ para todo x donde $$f(x)>0$$. La idea es generar un candidato Y a partir de $$g(y)$$, y luego "aceptarlo" como una realización de X con una probabilidad $$f(Y)/(c⋅g(Y))$$.

**Algoritmo General.**

1. Generar un candidato Y a partir de la distribución con FDP $$g(y)$$.
2. Generar un número $$U∼U(0,1)$$ (independiente de Y).
3. Si $$U≤c⋅g(Y)f(Y)$$​, entonces aceptar $$X=Y$$.
4. Si no, rechazar Y y volver al paso 1.

**Eficiencia.**

La probabilidad de aceptación en cada iteración es 1/c. Por lo tanto, se desea que c sea lo más cercano a 1 posible, lo que significa que la función "envolvente" $$c⋅g(x)$$ debe ser lo más ajustada posible a f(x).

El número esperado de iteraciones para generar una observación es c

**Usos**

Útil para distribuciones como la Normal, usando una FDP Normal como mayorante para una parte, y exponenciales para las colas, como en el algoritmo Ziggurat, Gamma y Beta, donde el MTI no es directo.

#### Método de Box-Muller para la Distribución Normal

Este es un método específico y elegante para generar _pares_ de variables aleatorias Normales estándar $$Z1​,Z2​∼N(0,1)$$ independientes, a partir de dos números aleatorios $$U1​,U2​∼U(0,1)$$ independientes.

$$
Z_1=\sqrt(−2lnU_1 ). cos(2πU_2)
$$

$$
Z_2=\sqrt(−2lnU_1 ). sen(2πU_2)
$$

Para generar una variable $$X∼N(μ,σ2)$$, se genera primero $$Z_1\ o\ Z_2$$ y luego se transforma: $$X=μ+σZ_1$$.

**Variante Polar (Marsaglia-Bray):** Existe una modificación que evita el uso directo de funciones trigonométricas, utilizando un método de aceptación-rechazo para generar puntos dentro de un círculo unitario, lo que puede ser computacionalmente más eficiente en algunas arquitecturas.

**Generación para Distribuciones Empíricas**

Cuando se dispone de un conjunto de datos observados $$x_1,…,x_N$$. de un sistema real, y no se encuentra una distribución teórica que se ajuste bien a ellos (o no se desea asumir una), se puede utilizar la distribución empírica

1. **Para Datos Discretos:** Si hay k valores distintos v1​,…,vk​ con frecuencias relativas p1​,…,pk​, se aplica el MTI para discretas.
2. **Para Datos Continuos:** Se puede construir una FDA empírica escalonada (si se usan los datos directamente) o una FDA lineal por tramos (si los datos se agrupan en un histograma y se interpola). Luego se aplica el MTI

#### Técnicas Especiales

{% tabs %}
{% tab title="Composicion" %}
se utiliza para generar variables aleatorias cuando una distribución compleja puede ser expresada como una combinación ponderada de varias distribuciones más simples. Básicamente, si se conoce que una variable aleatoria ( X ) tiene una función de distribución que es una mezcla de ( k ) distribuciones diferentes con probabilidades asociadas ( $$p_1, p_2, \ldots, p_k$$) (donde ( $$\sum_{i=1}^k p_i = 1 )$$), la técnica de composición permite su simulación de la siguiente manera:

1. Se elige ( i ) con probabilidad ( p\_i ).
2. Se genera una variable aleatoria ( X\_i ) de la ( i )-ésima distribución.

La variable generada ( $$X = X_i$$ ) entonces sigue la distribución deseada, combinando las características de las diferentes distribuciones participantes de acuerdo con los pesos especificados.
{% endtab %}

{% tab title="Convulsion" %}
La técnica de convolución se utiliza para generar variables aleatorias que son la suma de otras variables aleatorias independientes. Es particularmente útil cuando se conoce que una variable aleatoria ( $$Z$$ ) es la suma de otras $$( X_1, X_2, \ldots, X_n )$$ que siguen distribuciones conocidas. /

Para simular ( Z ) usando convolución:

1. Generar ( n ) variables aleatorias independientes $$X_1, X_2, \ldots, X_n$$ siguiendo sus respectivas distribuciones.
2. Calcular ( $$Z = X_1 + X_2 + \ldots + X_n$$ ).

El resultado es que ( Z ) sigue la distribución resultante de la suma de las distribuciones de ( $$X_1, X_2, \ldots, X_n$$ ).

La técnica de rechazo se usa para generar una variable aleatoria de una distribución compleja cuando es difícil de muestrear directamente. Se requiere una función de densidad ( $$g(x)$$) que sea mayor o igual a la función deseada $$f(x)$$ para todos los valores posibles de ( X ). El procedimiento es:

1. Elegir ( $$X$$ ) tal que siga la distribución de ( $$g(x)$$ ).
2. Generar un número aleatorio ( $$U$$ ) uniforme entre 0 y 1.
3. Aceptar ( $$X$$ ) si ( $$U \leq \frac{f(X)}{cg(X)}$$ ), donde ( $$c$$ ) es una constante tal que ( $$cg(x) \geq f(x)$$ ) para todos ( $$x$$ ).

Repetir el proceso hasta aceptar un ( $$X$$ ), garantizando que sigue la distribución ( $$f(x)$$ ).\\
{% endtab %}
{% endtabs %}

***

* **Bibliografía Recomendada:**
  1. Law, A. M. (2015). _Simulation Modeling and Analysis_ (5th ed.). McGraw-Hill Education. (Capítulos sobre generación de números aleatorios y variables aleatorias).
  2. Banks, J., Carson, J. S., II, Nelson, B. L., & Nicol, D. M. (2010). _Discrete-Event System Simulation_ (5th ed.). Prentice Hall. (Capítulos sobre números aleatorios y generación de variables aleatorias).
  3. Leemis, L. M., & Park, S. K. (2006). _Discrete-Event Simulation: A First Course_. (Capítulos 2, 6, 7).
  4. Hillier, F. S., & Lieberman, G. J. (2010). _Introducción a la Investigación de Operaciones_ (9th ed.). McGraw-Hill. (Capítulo 20 sobre Simulación, secciones 20.3, 20.4).
  5. Cassandras, C. G., & Lafortune, S. (2008). _Introduction to Discrete Event Systems_ (2nd ed.). Springer. (Sección 10.5 sobre Generación de Variables Aleatorias).
