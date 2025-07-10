---
icon: chart-area
---

# Probability Distributions

## BERNOULLI DISTRIBUTION

### 1. Definition

> The **Bernoulli distribution** is the most fundamental discrete probability distribution. It describes an experiment or trial that only has **two possible outcomes**, usually labeled as "success" and "failure".

Mathematically:

1. Success: $$P(X = 1) = p,$$
2. Failure: $$P(X = 0) = 1-p$$

A single experiment of this type is known as a **Bernoulli trial**. This distribution therefore models the outcome of a single trial or event, not a sequence of them.

### 2. How and When Is It Used?

It is used to model any situation in which a single event has a binary outcome. It is the basis for more complex distributions such as the Binomial and Geometric.

Some application examples are:
- **Coin toss**: The result is heads (success) or tails (failure).
- **Quality inspection**: A manufactured part is conforming (success) or defective (failure).
- **Exam result**: A student passes (success) or fails (failure).
- **Customer decision**: A customer buys a product (success) or does not buy it (failure).

### 3. Algebraic Form

To formalize it, a random variable X is defined that can take two values:
- X=1 if the outcome is "success".
- X=0 if the outcome is "failure".

The **Probability Mass Function (pmf)** of a Bernoulli random variable is:

$$
f(x;p)=P(X=x)=p^x(1−p)^{1−x} \quad \text{for}\ x∈\{0,1\}
$$

- If x=1 (success): $$P(X=1)=p^1(1−p)^{1−1}=p(1−p)^0=p$$
- If x=0 (failure): $$P(X=0)=p^0(1−p)^{1−0}=1(1−p)^1=1−p$$

Main statistical measures:
- **Expected Value (Mean)**: $$E[X]=p$$
- **Variance**: $$Var(X)=p(1−p)$$

### 4. In Excel

Excel does not have a dedicated function like `BERNOULLI.DIST`. However, a Bernoulli trial is a special case of the Binomial distribution where the number of trials is 1 (n=1). Therefore, the syntax is:  
`BINOM.DIST(successes; trials; prob_success; cumulative)`

To simulate a Bernoulli trial:
- `successes`: The outcome to evaluate (1 for success, 0 for failure).
- `trials`: Always **1**.
- `prob_success`: Probability of success, **p**.
- `cumulative`: Always **FALSE** (to get the exact value probability).

**Example:** To calculate the probability that a part is defective (p=0.05), the result is "success" if X=1. `=BINOM.DIST(1; 1; 0.05; FALSE)` returns `0.05`.

### 5. How to Use It in Simulation (AnyLogic)

In system simulation, the Bernoulli trial is crucial for modeling probabilistic decision points. The implementation does not require sampling from a complex distribution, but simply:

**Logic:**
1. Generate a random number R from a Uniform(0, 1) distribution.
2. If R≤p, the result is "success".
3. If R>p, the result is "failure".

**In AnyLogic**, this is greatly simplified with the built-in function:

```java
randomTrue(p)
```

This function returns the boolean value `true` (success) with probability `p`, and `false` (failure) with probability `1-p`. It is the direct implementation of a Bernoulli trial.

**Example use:** In a quality inspection model, an entity arrives at a `SelectOutput` block. In the condition of that block, you can write `randomTrue(0.98)`. This would mean...

***

## BINOMIAL DISTRIBUTION

### 1. Definition

> The **Binomial distribution** is a discrete probability distribution that describes the **number of successes** in a sequence of **n independent Bernoulli trials**.

For a random variable to follow a Binomial distribution, the experiment must meet these fundamental conditions:
1. The experiment consists of a sequence of n identical and fixed trials.
2. Each trial only has two possible outcomes: "success" or "failure".
3. The probability of success, denoted by p, is constant in each trial. The probability of failure is 1−p.
4. The trials are statistically independent; the outcome of one does not affect another.

This distribution is defined by two parameters: **n** (number of trials) and **p** (probability of success).

### 2. How and When Is It Used?

It is used to model how many times an event of interest occurs in a fixed number of attempts. It's one of the most widely used distributions in quality control, genetics, finance, etc.

Examples:
- **Quality control**: Probability of finding exactly k defective items in a lot of n units drawn from a production line.
- **Medicine**: Probability that k patients out of n respond positively to a treatment.
- **Marketing**: Probability that k customers out of n who received a promotion make a purchase.
- **Games of chance**: Probability of getting exactly k heads when tossing a coin n times.

### 3. Algebraic Form

Let X be the random variable representing the number of successes in n trials. The **Probability Mass Function (pmf)** of the Binomial distribution is:

$$
f(k;n,p)=P(X=k)={n \choose k}p^k(1−p)^{n−k}
$$

where:
- k is the number of successes, taking values {0,1,2,...,n}
- $${n \choose k} = \frac{n!}{k!(n−k)!}$$ is the binomial coefficient, the number of ways to have k successes in n trials.
- $p^k$ is the probability of k successes.
- $(1−p)^{n−k}$ is the probability of (n−k) failures.

Main statistical measures:
- **Expected Value (Mean)**: $$E[X]=np$$
- **Variance**: $$Var(X)=np(1−p)$$

### 4. In Excel

Excel provides a direct function for Binomial distribution: `BINOM.DIST` (or `DISTR.BINOM` in Spanish).

Syntax: `BINOM.DIST(successes; trials; prob_success; cumulative)`

- `successes`: Value of k for which the probability is calculated.
- `trials`: Total number of trials, n.
- `prob_success`: Probability of success, p.
- `cumulative`:
  - **FALSE**: Calculates probability of exactly k successes (P(X=k)).
  - **TRUE**: Calculates probability of up to k successes (P(X≤k)), i.e., the cumulative distribution function (CDF).

**Example:** In a manufacturing process, if the probability of a defective part is 0.02 (p=0.02) and a sample of 50 parts (n=50) is taken, what's the probability of finding...

### 5. How to Use It in Simulation (AnyLogic)

In simulation, the Binomial distribution is used to determine the aggregate outcome of a series of binary events without simulating each of the n trials individually.

**In AnyLogic**, you can sample from a Binomial distribution directly:

```java
binomial(n, p)
```

This function performs n Bernoulli trials with probability of success p and returns the **total number of successes**.

**Example:** A ship arrives at a port with 200 containers (n=200). If the probability that a container is selected for inspection is 0.15 (p=0.15), instead of simulating 200 `randomTrue(0.15)` events, you can use:

```java
int containers_to_inspect = binomial(200, 0.15);
```

***

## POISSON DISTRIBUTION

### 1. Definition

> The **Poisson distribution** is a discrete probability distribution that expresses the probability of a given number of events occurring in a **fixed interval of time or space**.

Unlike the Binomial, which counts successes in a fixed number of trials (n), Poisson counts the number of occurrences in a continuum (such as time or area).

- **λ (lambda)**: The average rate of occurrence of events in the specified interval.

### 2. How and When Is It Used?

> One of the most important distributions in operations research and engineering, especially in **queueing theory**. Used to model events considered "rare" or that occur randomly in time or space.

Examples:
- Number of phone calls arriving at a switchboard in one hour.
- Number of defects per square meter of steel sheet.
- Number of customers arriving at a bank or checkout per minute.
- Number of machine breakdowns in a day.

Most common use in simulation: modeling **arrival processes**.

### 3. Algebraic Form

Let X be the random variable representing the number of occurrences in an interval. The **Probability Mass Function (pmf)** for Poisson is:

$$
f(k;\lambda)=P(X=k)=\frac{\lambda^k e^{−\lambda}}{k!}
$$

where:
- k is the number of occurrences, taking non-negative integer values {0,1,2,...}
- λ is the average rate per interval.
- e is the base of natural logarithms (about 2.71828...)

Unique property: The expected value and variance are both equal to λ.

- **Expected Value (Mean):** $$E[X]=\lambda$$
- **Variance:** $$Var(X)=\lambda$$

### 4. In Excel

Excel function: `POISSON.DIST` (or `POISSON` in Spanish).

Syntax: `POISSON.DIST(x; mean; cumulative)`

- `x`: Number of events, k.
- `mean`: Mean rate, λ.
- `cumulative`:
  - **FALSE**: Probability of exactly k events (P(X=k)).
  - **TRUE**: Probability of up to k events (P(X≤k)), i.e., CDF.

**Example:** If customers arrive at a checkout at a mean rate of 15 per hour (λ=15), what is the probability that exactly 10 arrive in an hour (k=10)? `=POISSON.DIST(10; 15; FALSE)`

### 5. How to Use It in Simulation (AnyLogic)

In discrete-event simulation, Poisson is rarely used directly for arrivals, because models do not advance in steps of "one arrival". Instead, the **time between successive events** is modeled.

**There is a fundamental relationship between Poisson and Exponential**:
> If the **number of events** in a time interval follows a Poisson distribution with mean rate λ, then the **time between successive events** follows an **Exponential distribution** with mean 1/λ.

To model a **Poisson arrival process** in AnyLogic, use the Exponential distribution in the `Source` block:

```java
exponential(1.0 / lambda)
```

**Direct use of `poisson()` in AnyLogic:**
AnyLogic has a function `poisson(lambda)` for generating an integer count, not for interarrival times.

**Examples:**
- For arrivals: A workshop receives jobs according to a Poisson process with mean 2 per hour (λ=2). In `Source`, set interarrival time: `exponential(0.5)`
- For counts: A truck arrives daily; the number of packages it unloads follows a Poisson distribution with mean 30. Use `poisson(30)` for package count.

***

## GEOMETRIC DISTRIBUTION

### 1. Definition

> The **Geometric distribution** is a discrete probability distribution that models the number of **independent Bernoulli trials** until the first success is observed.

Like Binomial, it's based on Bernoulli trials, so:
1. Each trial has only two outcomes: "success" or "failure".
2. The probability of success, p, is constant in each trial.
3. Trials are statistically independent.
   
Key difference: Geometric does not have a fixed number of trials (n). The experiment continues until the first success.

### 2. How and When Is It Used?

It is used to model "waiting for the first event" situations in discrete, independent trials. Useful in quality control, reliability, and telecommunications.

Examples:
- **Manufacturing**: How many items must be inspected to find the first defective one?
- **Telecommunications**: Number of times a data packet must be retransmitted until received without errors.
- **Sales**: Number of prospects a salesperson must contact before making the first sale.
- **Games of chance**: Number of dice rolls until the first "6" appears.

### 3. Algebraic Form

There are two common variants. The most common models the number of failures _before_ the first success.

Let X be the random variable: **number of failures** before the first success. The **Probability Mass Function (pmf)** is:

$$
f(k;p)=P(X=k)=(1−p)^k\,p\quad \text{for}\ k=0,1,2,\ldots
$$

- k: number of failures.
- p: probability of success.
- (1−p): probability of failure.

Main statistical measures:
- **Expected Value (Mean):** $$E[X]=\frac{1-p}{p}$$ (expected failures before first success)
- **Variance:** $$Var(X)=\frac{1-p}{p^2}$$

_(Note: The other variant defines the variable as the total number of trials, $k'$, to achieve first success.)_

### 4. In Excel

Newer Excel versions include `GEOM.DIST`, but the most compatible universal function is `NEGBINOM.DIST` (or `DISTR.NEGBINOM` in Spanish), as the Geometric distribution is a special case of the Negative Binomial.

Syntax: `NEGBINOM.DIST(num_failures; num_successes; prob_success; cumulative)`

- `num_failures`: k (number of failures)
- `num_successes`: Always **1**
- `prob_success`: Probability of success, **p**
- `cumulative`: Always **FALSE**

**Example:** A basketball player has an 80% chance (p=0.8) of making a free throw. What is the probability of missing exactly 2 times (k=2) before making the first success? `=NEGBINOM.DIST(2; 1; 0.8; FALSE)`

### 5. How to Use It in Simulation (AnyLogic)

In simulation, the Geometric distribution is useful for modeling the number of attempts until a random action succeeds.

**In AnyLogic**, sample directly with:
```java
geometric(p)
```

This simulates Bernoulli trials with probability of success p and returns the **total number of trials until the first success**.

**Example:** If a software check has a 95% chance (p=0.95) of passing each time, simulate how many attempts are needed:

```java
int numAttempts = geometric(0.95);
```

***

## DISCRETE UNIFORM DISTRIBUTION

### 1. Definition

> The **Discrete Uniform Distribution** describes an experiment with a **finite number of possible outcomes, each equally likely**. The mathematical formalization of "pure chance".

Defined by the number of possible outcomes, n.

### 2. How and When Is It Used?

Used for situations where every discrete result has the same chance of occurring.

- **Games of chance**: Rolling a fair die, where each face (1-6) is equally likely.
- **Sampling**: Drawing a card at random from a well-shuffled deck.
- **Computing**: Generating a random integer within a specific range.

### 3. Algebraic Form

Let X be a random variable that can take n distinct values {x₁, x₂, ..., xₙ}. The **pmf** is: $$P(X=x_i) = \frac{1}{n}$$ for each i=1,2,...,n.

If the results are consecutive integers from a to b, n = b−a+1.

- **Expected Value (Mean):** $$E[X]=\frac{a+b}{2}$$
- **Variance:** $$Var(X)=\frac{(b−a+1)^2−1}{12}$$

### 4. In Excel

No specific function for probability (it's just 1/n), but to generate a random sample:

`RANDBETWEEN(bottom, top)` or `ALEATORIO.ENTRE(inferior; superior)` (Spanish)

Returns a random integer between `bottom` and `top` (inclusive), equally likely.

**Example:** To simulate a roll of a 6-sided die: `=RANDBETWEEN(1, 6)`

### 5. How to Use It in Simulation (AnyLogic)

In AnyLogic, to select a random integer result from a range where all are equally likely:

```java
uniform_discrete(min, max)
```

Returns a random integer between `min` and `max`, inclusive.

**Example:** If an assembly process must randomly pick one of four screw types (numbered 1–4): `uniform_discrete(1, 4)`

***

## CONTINUOUS UNIFORM DISTRIBUTION

### 1. Definition

> The **Continuous Uniform Distribution** describes a random variable that can take **any value in an interval [a,b] with equal probability**.

Defined by two parameters: **a** (min value) and **b** (max value).

### 2. How and When Is It Used?

Widely used in simulation, especially when the process range (min and max) is known but there's insufficient info for another distribution.

- **Operation time modeling**: A manual task time varies between 5 and 10 minutes, no value is more likely than another.
- **Initial estimates**: When no historical data, experts usually give a "pessimistic-optimistic" range, which fits a uniform distribution.

### 3. Algebraic Form

Let X be a continuous random variable in [a, b].

- **Probability Density Function (pdf):** $$f(x) = \frac{1}{b-a} \text{ for } a \leq x \leq b; 0 \text{ otherwise}$$
- **Cumulative Distribution Function (CDF):** $$F(x) = \frac{x-a}{b-a} \text{ for } a \leq x \leq b$$
- **Expected Value (Mean):** $$E[X]=\frac{a+b}{2}$$
- **Variance:** $$Var(X)=\frac{(b-a)^2}{12}$$

### 4. In Excel

To generate a sample: use `RAND()`, which returns a decimal between 0 and 1, scaled to [a, b]:

Formula: `=a + (b-a) * RAND()`

**Example:** Generate a service time uniformly between 5 and 10 minutes: `=5 + (10-5) * RAND()`

### 5. How to Use It in Simulation (AnyLogic)

AnyLogic provides a direct function:

```java
uniform(min, max)
```

Returns a floating-point number uniformly distributed between `min` and `max`.

**Example:** For a shoe factory, the operation time for cut Type 2 is uniformly between 45 and 60 seconds: `uniform(45, 60)`

***

## EXPONENTIAL DISTRIBUTION

### 1. Definition

> The **Exponential distribution** is a continuous probability distribution that describes the **time between two successive events** in a Poisson process.

Defined by:
- **λ (lambda)**: **Average event rate** per unit time.

A fundamental property: **memorylessness** (the probability of an event in the future does not depend on how much time has already elapsed).

### 2. How and When Is It Used?

The classic distribution for modeling time between random, independent events.

- **Queueing theory**: Most common for modeling **times between arrivals** and **service times** (e.g., M/M/1 queue).
- **Reliability engineering**: Time until failure of components with no aging (constant failure rate).
- **Physics**: Radioactive decay.

### 3. Algebraic Form

Let T be the continuous random variable for time between events.

- **pdf:** $$f(t)=\lambda e^{−\lambda t},\quad t \geq 0$$
- **CDF:** $$F(t)=P(T\leq t)=1−e^{−\lambda t}$$
- **Expected Value:** $$E[T]=\frac{1}{\lambda}$$
- **Variance:** $$Var(T)=\left(\frac{1}{\lambda}\right)^2$$

### 4. In Excel

Excel function: `EXPON.DIST` (or `DISTR.EXPON` in Spanish).

Syntax: `EXPON.DIST(x; lambda; cumulative)`

- `x`: Time value t.
- `lambda`: Rate λ.
- `cumulative`:
  - **FALSE**: Value of the density function.
  - **TRUE**: Cumulative probability (CDF).

**Example:** Customers arrive at a bank at rate 20 per hour (λ=20). What's the probability the next customer arrives within 3 minutes (0.05 hours)? `=EXPON.DIST(0.05; 20; TRUE)`

### 5. How to Use It in Simulation (AnyLogic)

Most used distribution for modeling random entity arrivals (Poisson process) in AnyLogic `Source` blocks.

**In AnyLogic**, the function is:
```java
exponential(mean)
```

**Note:** `exponential()` in AnyLogic takes the **mean inter-event time**, not λ.

**Example:**
- **Arrivals:** To model a Poisson arrivals process with mean 10 customers/hour (λ=10), the mean time between arrivals is 1/10=0.1 hours. In `Source`, use: `exponential(0.1)`
- **Service Time:** If service time is exponential with mean 12 minutes: `exponential(12)`

***

## NORMAL DISTRIBUTION

### 1. Definition

The **Normal distribution**, also known as the **Gaussian distribution** or **bell curve**, is the most important continuous probability distribution in statistics and engineering.

It is bell-shaped, symmetric about its center. Defined by:
- **μ (mu)**: The **mean**, expected value and center (highest point).
- **σ (sigma)**: The **standard deviation**, measuring dispersion.

### 2. How and When Is It Used?

Widely applicable because many natural phenomena and engineering processes follow its pattern, due to the **Central Limit Theorem**.

Used to model:
- **Physical Characteristics**: Height, weight, part dimensions.
- **Measurement Errors**: Random experimental errors.
- **Financial Processes**: Asset returns.
- **Process Times**: Operation times clustered around an average.

### 3. Algebraic Form

Let X be a continuous random variable.

- **pdf:** $$f(x) = \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^2},\quad -\infty < x < \infty$$
- **CDF:** Integral of the density (no simple closed form; use tables/software).
- **Expected Value:** $$E[X] = \mu$$
- **Variance:** $$Var(X) = \sigma^2$$

For probabilities: standardize X to Z (standard normal): $$Z = \frac{X-\mu}{\sigma}$$

### 4. In Excel

Direct functions: `NORM.DIST` (`DISTR.NORM` in Spanish).

Syntax: `NORM.DIST(x; mean; std_dev; cumulative)`

- `x`: Random variable value.
- `mean`: μ.
- `std_dev`: σ.
- `cumulative`:
  - **TRUE**: CDF (P(X≤x))
  - **FALSE**: Density function

**Example:** In a filling process, bottle volume ~ N(500,5) ml. Probability a bottle contains 498 ml or less: `=NORM.DIST(498; 500; 5; TRUE)`

### 5. How to Use It in Simulation (AnyLogic)

Excellent for modeling process times or product attributes with a clear target value and symmetrical random variation.

**In AnyLogic**:
```java
normal(mean, stdDev)
```

- `mean`: μ.
- `stdDev`: σ.

**Example:** For shoe factory, assembly time (Station 2) is normally distributed with mean 3 min, std dev 1 min: `normal(3, 1)`

**Important Warning:** The Normal distribution can theoretically generate negative values. For physical variables like time, use:
```java
max(0, normal(mean, stdDev))
```
Ensures negative values are replaced with zero.

***

## TRIANGULAR DISTRIBUTION

### 1. Definition

> The **Triangular distribution** is a continuous probability distribution defined by three parameters that determine its triangular shape:
> - **a**: **Minimum** possible value
> - **b**: **Maximum** possible value
> - **c**: **Most likely** value (mode)

Unlike the infinite Normal, the Triangular is defined on finite [a, b], making it practical for bounded phenomena.

### 2. How and When Is It Used?

Ideal when you lack large amounts of historical data but have **expert opinion** (minimum, most likely, maximum).

Common applications:
- **Project Management**: Basis of **PERT** technique for estimating project activity durations.
- **Service/Process Times**: Estimate times for manual operations.
- **Risk Analysis**: Model financial/business variables with subjective estimates.

### 3. Algebraic Form

Let X be a continuous random variable.

- **pdf:** 
  $$
  f(x) = 
    \begin{cases}
      \frac{2(x-a)}{(b-a)(c-a)}, & a \leq x \leq c \\
      \frac{2(b-x)}{(b-a)(b-c)}, & c < x \leq b
    \end{cases}
  $$
- **Expected Value:** $$E[X]=\frac{a+b+c}{3}$$
- **Variance:** $$Var(X)=\frac{a^2+b^2+c^2-ab-ac-bc}{18}$$

### 4. In Excel

No built-in `TRIANG.DIST`. To generate a sample, use the **inverse transform method** with a Uniform(0,1) random number.

**Logic:**
1. Generate a random number R with `RAND()`
2. Calculate threshold $$F_c = (c-a)/(b-a)$$
3. If R < F_c, use formula for ascending ramp.
4. If R ≥ F_c, use formula for descending ramp.

{% hint style="warning" %}
Due to its complexity, this is usually implemented in Excel via macros (VBA) or simulation add-ins, not a direct cell formula.
{% endhint %}

### 5. How to Use It in Simulation (AnyLogic)

The Triangular distribution is widely used in AnyLogic for process times due to the ease of estimating its parameters.

**In AnyLogic**:
```java
triangular(min, mode, max)
```

- `min`: Minimum, a.
- `mode`: Most likely, c.
- `max`: Maximum, b.

**Example:** In Borshchev's AnyLogic book, the time for a process is modeled with `triangular(0.5, 1, 1.5)` seconds (min 0.5, max 1.5, mode 1).

***

## ERLANG DISTRIBUTION

### 1. Definition

> The **Erlang distribution** is a continuous probability distribution describing the **total time until k successive events** occur in a Poisson process.

It can be understood as the **sum (convolution) of k identical, independent exponential variables** with the same mean rate.

Defined by:
- **k**: **Shape parameter**, positive integer (number of exponential events).
- **λ (lambda)**: **Mean event rate** of the underlying Poisson process.

As k increases, the distribution becomes more symmetric, approaching the Normal (Central Limit Theorem).

### 2. How and When Is It Used?

Used to model waiting times or task durations that can be seen as the sum of several sequential, independent phases.

Applications:
- **Queueing Theory**: Service times with several phases (e.g., diagnosis, repair, test).
- **Supply Chain**: Delivery time through k distribution centers or stages.
- **Reliability Engineering**: Time until failure of a system with k sequential backup components.

### 3. Algebraic Form

Let T be the total time to the k-th event.

- **pdf:** $$f(t)=\frac{\lambda^k t^{k−1}e^{−\lambda t}}{(k−1)!},\quad t≥0,\,k=1,2,...$$
- **Expected Value:** $$E[T]=\frac{k}{\lambda}$$
- **Variance:** $$Var(T)=\frac{k}{\lambda^2}$$

### 4. In Excel

No direct `ERLANG.DIST`, but Erlang is a special case of the **Gamma distribution** (shape parameter is integer).

Syntax: `GAMMA.DIST(x; alpha; beta; cumulative)`

- `x`: Total time, t.
- `alpha`: Shape parameter, **k**.
- `beta`: Scale, which is mean time per phase, **1/λ**.
- `cumulative`: `TRUE` for CDF, `FALSE` for pdf.

**Example:** A process has 4 stages (k=4), event rate 2/min (λ=2). Probability process takes 3 min or less: `=GAMMA.DIST(3; 4; 0.5; TRUE)`

### 5. How to Use It in Simulation (AnyLogic)

Useful for process times less variable than the Exponential (whose peak is always at zero), but not as symmetric as Normal.

**In AnyLogic**:
```java
erlang(k, mean)
```
- `k`: Shape parameter, number of stages.
- `mean`: **Total mean time** for the process (k/λ).

**Example:** Assembly process has two sequential phases (k=2), total mean time is 30 min: `erlang(2, 30)` (each phase has mean 15 min).

***

## WEIBULL DISTRIBUTION

### 1. Definition

The **Weibull distribution** is a highly versatile continuous probability distribution. Its main advantage is its ability to model different failure rate behaviors.

Defined by:
- **α (alpha)**: **Shape parameter** (key to the distribution's character)
- **β (beta)**: **Scale parameter** (characteristic life), point where 63.2% of failures have occurred.

### 2. How and When Is It Used?

Classic in **reliability engineering**, **lifetime analysis**, and **warranty management**.

- **α < 1**: Failure rate decreases over time ("infant mortality", early product failures)
- **α = 1**: Constant failure rate. Weibull **reduces to the Exponential**.
- **α > 1**: Failure rate increases over time (wear-out failures in mechanics).

### 3. Algebraic Form

Let T be the time to failure.

- **pdf:** $$f(t) = \frac{\alpha}{\beta} \left( \frac{t}{\beta} \right)^{\alpha-1} e^{-(t/\beta)^\alpha},\quad t \geq 0$$
- **Expected Value:** $$E[T]=\beta\cdot\Gamma(1+1/\alpha)$$
- **Variance:** $$Var(T) = \beta^2 [\Gamma(1+2/\alpha) - (\Gamma(1+1/\alpha))^2]$$

### 4. In Excel

Direct function: `WEIBULL.DIST` (or `DISTR.WEIBULL` in Spanish).

Syntax: `WEIBULL.DIST(x; alpha; beta; cumulative)`

- `x`: Time value, t.
- `alpha`: Shape parameter, α.
- `beta`: Scale parameter, β.
- `cumulative`: `TRUE` for CDF, `FALSE` for pdf.

**Example:** A component has α=2 (wear), β=8000 hours. Probability it fails before 7000 hours: `=WEIBULL.DIST(7000; 2; 8000; TRUE)`

### 5. How to Use It in Simulation (AnyLogic)

Use for process durations or failure times with non-constant failure rates.

**In AnyLogic**:
```java
weibull(shape, scale)
```
- `shape`: α
- `scale`: β

**Example:** For a motor lifetime with α=2.5, β=15000 hours: `weibull(2.5, 15000)`

***

## LOGNORMAL DISTRIBUTION

### 1. Definition

The **Lognormal distribution** is a continuous probability distribution for a variable whose **natural logarithm is normally distributed**. Since the log of a negative number is undefined, it only applies to positive variables.

It is **right-skewed**, ideal for phenomena with many small values and rare large extremes.

### 2. How and When Is It Used?

Applies to variables thought to be the **product of many small, independent factors** (Central Limit Theorem applied multiplicatively).

Examples:
- **Finance**: Stock prices, asset values.
- **Engineering/Medicine**: Repair times, incubation periods, chemical concentrations, particle sizes.

### 3. Algebraic Form

- **pdf:** $$f(x) = \frac{1}{x \sigma_{ln} \sqrt{2\pi}} e^{-\frac{(\ln(x) - \mu_{ln})^2}{2 \sigma_{ln}^2}},\quad x > 0$$
  - _Important_: $$\mu_{ln}$$ and $$\sigma_{ln}$$ are the mean and standard deviation of the **natural logarithm of the variable**, not the variable itself.
- **Expected Value:** $$E[X] = e^{\mu_{ln} + \sigma_{ln}^2 / 2}$$
- **Variance:** $$Var(X) = (e^{\sigma_{ln}^2} - 1) e^{2\mu_{ln} + \sigma_{ln}^2}$$

### 4. In Excel

Direct function: `LOGNORM.DIST` (or `DISTR.LOG.NORM` in Spanish).

Syntax: `LOGNORM.DIST(x; mean; std_dev; cumulative)`

- `x`: Variable value.
- `mean`: Mean of ln(X), i.e., $$\mu_{ln}$$.
- `std_dev`: Std dev of ln(X), i.e., $$\sigma_{ln}$$.
- `cumulative`: `TRUE` for CDF, `FALSE` for pdf.

### 5. How to Use It in Simulation (AnyLogic)

Great for process times that can't be negative and are skewed: most times are short but occasionally there's a long process.

**In AnyLogic**:
```java
lognormal(mean, stdDev)
```
- `mean`: The **mean of the lognormal distribution itself**, E[X].
- `stdDev`: The **std dev of the lognormal distribution**.

**Note:** AnyLogic simplifies usage. No need to calculate $$\mu_{ln}$$ and $$\sigma_{ln}$$ of the log; just provide the observed mean and std dev.

**Example:** If machine diagnostics time has observed mean 45 min and std dev 20 min (and is known to be right-skewed): `lognormal(45, 20)`
