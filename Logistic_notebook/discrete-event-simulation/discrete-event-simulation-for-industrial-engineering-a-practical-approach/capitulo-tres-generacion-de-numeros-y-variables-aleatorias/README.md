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

#### **Independence Tests**

These tests verify whether the generated numbers are independent of each other (that is, whether the value of one number does not influence the value of the following numbers).

1. **Runs Test:** A "run" is a subsequence of observations with a common property.
1. For example, an upward run is a sequence of numbers where each is greater than the previous one. The total number of runs in the sequence is analyzed. If there are too many or too few runs compared to what would be expected from a truly independent sequence, the hypothesis of independence is rejected.
2. **Autocorrelation Test:** This test measures the linear correlation between numbers separated by a certain "lag" (lag) $$k$$ in the sequence. The lag k autocorrelation, $$ρ_k$$​, estimates the correlation between $$U_i$$​ and $$U_i+k$$​. For an independent sequence, all autocorrelations (for $$k≥1$$) are expected to be close to zero. A test statistic (based on the Normal approximation for $$ρ^​k$$​ when N is large) is constructed to check whether $$ρ_k$$​ is significantly different from zero.

{% hint style="warning" %}
It is important to note that a generator must pass a diverse and rigorous set of these statistical tests before being considered acceptable for use in serious simulation studies. The fact that a sequence passes a test does not guarantee that it is "perfect," only that no evidence against the assumption of uniformity or independence has been found under that particular test.
{% endhint %}

***

#### Random Variable Generation Methods.

Once a reliable source of pseudorandom numbers $$U_i∼U(0,1)$$ is available, the next step is to transform these uniform numbers into realizations of random variables that follow the specific probability distributions (Exponential, Normal, Poisson, etc.) that have been identified as models for the uncertain components of the system under study.

There are several methods for performing this transformation.

**Inverse Transform Method (ITM)**

This is the most fundamental method and, when applicable, often the most efficient and straightforward.

1. **Principle** It is based on the fact that if X is a random variable with a continuous and strictly increasing cumulative distribution function (CDF) $$F(x)$$, and U is a random variable $$U(0,1)$$, then the random variable $$Y=F−1(U)$$ has the same distribution as X. Here, $$F−1(u)$$ is the inverse function of the CDF, defined as the value y such that $$F(y)=u$$.
1. **Algorithm for Continuous VAs:**

Generate a number $$u∼U(0,1)$$.

1. Compute $$x=F−1(u)$$. This x is the desired observation from the CDF. X.
2. **Application to Discrete A.V.:**

If X is discrete with $$MPF\ p(xj​)$$ and $$FDA F(xj​)=P(X≤xj​)$$, then $$u∼U(0,1)$$ is generated and the value _xj​_ is searched for such that $$F(xj−1​)<u≤F(xj​)\ (where\ F(x0​)=0)$$. Then _x&#x6A;_&#x200B; is the generated observation. This can be implemented using a sequential or more efficient search.

* **Direct Application Examples, where F−1(u) has closed form:**
* **Uniform Continuous U(a,b):** $$F(x)=(x−a)/(b−a)$$. Inverting, $$x=a+(b−a)u$$.
* **Exponential (mean** $$μ=1/λ$$**):** $$F(x)=1−e−λx$$. Inverting, $$x=−(1/λ)ln(1−u)$$. Since if $$u∼U(0,1)$$, then $$1−u∼U(0,1)$$, one can use $$x=−(1/λ)ln(u)$$ equivalently.
* **Triangular:** The CDF is piecewise linear, and its inverse can also be found analytically piecewise.
* **Weibull:** $$F(x)=1−e−(x/α)β$$. Inverting, $$x=α(−ln(1−u))1/β$$.

<details>

<summary><strong>Advantages:</strong></summary>

It is exact if $$F−1(u)$$ can be calculated precisely. It is intuitive. It preserves monotonicity (if $$u1​<u2$$​, then $$F−1(u1​)≤F−1(u2​)$$), which is useful for some variance reduction techniques.

</details>

<details>

<summary><strong>Disadvantages:</strong></summary>

The function $$F−1(u)$$ does not always have a simple analytic or closed-form expression

(e.g., for the Normal, Gamma, Beta, Binomial, and Poisson distributions with large parameters). In these cases, numerical approximations or alternative methods are required.

</details>

***

#### Acceptance-Rejection (A-R) Method.

This is a general method that can be used when the ITM is difficult or inefficient to apply.

Suppose we want to generate a VA X with PDF $$f(x)$$. We choose another "majority" PDF $$g(x)$$ (from which it is easy to generate variables, for example, using ITM) and a constant $$c≥1$$ such that $$f(x)≤c⋅g(x)$$ for all x where $$f(x)>0$$. The idea is to generate a candidate Y from $$g(y)$$, and then "accept" it as a realization of X with probability $$f(Y)/(c⋅g(Y))$$.

**General Algorithm.**

1. Generate a candidate Y from the distribution with PDF $$g(y)$$.

2. Generate a number $$U∼U(0,1)$$ (independent of Y).
3. If $$U≤c⋅g(Y)f(Y)$$​, then accept $$X=Y$$.
4. Otherwise, reject Y and return to step 1.

**Efficiency.**

The probability of acceptance at each iteration is 1/c. Therefore, we want c to be as close to 1 as possible, which means the "envelope" function $$c⋅g(x)$$ should be as close to f(x) as possible.

The expected number of iterations to generate an observation is c.

**Uses**

Useful for distributions such as the Normal, using a Normal PDF as the major factor for one side, and exponentials for the tails, as in the Ziggurat, Gamma, and Beta algorithms, where the MTI is not straightforward.

#### Box-Muller Method for the Normal Distribution

This is a specific and elegant method for generating pairs of independent standard normal random variables $$Z1​,Z2​∼N(0,1)$$ from two independent random numbers $$U1​,U2​∼U(0,1)$$.

$$
Z_1=\sqrt(−2lnU_1 ). cos(2πU_2)
$$

$$
Z_2=\sqrt(−2lnU_1 ). sin(2πU_2)
$$

To generate a variable $$X∼N(μ,σ2)$$, first generate $$Z_1\ or\ Z_2$$ and then transform it: $$X=μ+σZ_1$$.

**Polar Variant (Marsaglia-Bray):** There is a modification that avoids the direct use of trigonometric functions, using an acceptance-rejection method to generate points within a unit circle, which can be computationally more efficient on some architectures.

**Generation for Empirical Distributions**

When a set of observed data $$x_1,…,x_N$$ from a real system is available, and a theoretical distribution that fits them well cannot be found (or one is unwilling to assume one), the empirical distribution can be used.

1. **For Discrete Data:** If there are k distinct values ​​v1​,…,vk​ with relative frequencies p1​,…,pk​, the MTI for discrete data is applied.
2. **For Continuous Data:** A stepwise empirical CDF can be constructed (if the data are used directly) or a piecewise linear CDF (if the data are grouped into a histogram and interpolated). Then, the MTI is applied.

#### Special Techniques

{% tabs %}
{% tab title="Composition" %}
is used to generate random variables when a complex distribution can be expressed as a weighted combination of several simpler distributions. Basically, if a random variable ( X ) is known to have a distribution function that is a mixture of ( k ) different distributions with associated probabilities ( $$p_1, p_2, \ldots, p_k$$) (where ( $$\sum_{i=1}^k p_i = 1 )$$), the composition technique allows its simulation as follows:

1. ( i ) is chosen with probability ( p\_i ).
2. A random variable ( X\_i ) is generated from the ( i )th distribution.

The generated variable ($$X = X_i$$) then follows the desired distribution, combining the characteristics of the different participating distributions according to the specified weights.
{% endtab %}

{% tab title="Convulsion" %}
The convolution technique is used to generate random variables that are the sum of other independent random variables. It is particularly useful when a random variable ($$Z$$) is known to be the sum of other $$(X_1, X_2, \ldots, X_n)$$ that follow known distributions. /

To simulate (Z) using convolution:

1. Generate (n) independent random variables $$X_1, X_2, \ldots, X_n$$ following their respective distributions.
2. Calculate ($$Z = X_1 + X_2 + \ldots + X_n$$).

The result is that ( Z ) follows the distribution resulting from the sum of the distributions of ( $$X_1, X_2, \ldots, X_n$$ ).

The rejection technique is used to generate a random variable from a complex distribution when it is difficult to sample directly. A density function ( $$g(x)$$) is required that is greater than or equal to the desired function $$f(x)$$ for all possible values ​​of ( X ). The procedure is:

1. Choose ( $$X$$ ) such that it follows the distribution of ( $$g(x)$$ ).
2. Generate a uniform random number ( $$U$$ ) between 0 and 1.
3. Accept ( $$X$$ ) if ( $$U \leq \frac{f(X)}{cg(X)}$$ ), where ( $$c$$ ) is a constant such that ( $$cg(x) \geq f(x)$$ ) for all ( $$x$$ ).

Repeat the process until an ( $$X$$ ) is accepted, ensuring that it follows the ( $$f(x)$$ ) distribution.
\\
{% endtab %}
{% endtabs %}


***

* **Recommended Reading:**
1. Law, A. M. (2015). _Simulation Modeling and Analysis_ (5th ed.). McGraw-Hill Education. (Chapters on random number generation and random variables).
2. Banks, J., Carson, J. S., II, Nelson, B. L., & Nicol, D. M. (2010). _Discrete-Event System Simulation_ (5th ed.). Prentice Hall. (Chapters on random numbers and random variable generation).
3. Leemis, L. M., & Park, S. K. (2006). _Discrete-Event Simulation: A First Course_. (Chapters 2, 6, 7).
4. Hillier, F. S., & Lieberman, G. J. (2010). _Introduction to Operations Research_ (9th ed.). McGraw-Hill. (Chapter 20 on Simulation, sections 20.3, 20.4).
5. Cassandras, C. G., & Lafortune, S. (2008). _Introduction to Discrete Event Systems_ (2nd ed.). Springer. (Section 10.5 on Random Variable Generation).
