---
description: >-
  is a dynamic, typically stochastic, and computational modeling technique used
  to represent systems where changes in state occur only at specific, distinct
  points in time, known as events.
icon: coin-blank
---

# Discrete Event Simulation

**Discrete-event simulation (DES)** is an approach used to model dynamic systems that evolve through a series of events occurring at discrete and irregular points in time.

{% hint style="success" %}
Unlike a continuous process, changes in the system's state only occur at these specific moments when an event takes place, such as a customer's arrival or the completion of a service.
{% endhint %}

This type of simulation is particularly useful for analyzing systems where events are fundamental in determining their behavior, such as production lines, queueing systems, or any operation where the time between events is critical.

Discrete-event simulation models are often **stochastic**, meaning they include uncertainty or random variability. Events change based on random occurrences—these are called **discrete events**. For example, imagine a queueing system where the system's state is the number of customers in it. The events that impact this and change its state are **arrivals** or **departures** from the queue.

On the other hand, in **continuous simulations**, changes in the system's state occur **continuously over time**. For example, imagine an airplane in flight as the system under observation, with its state defined by its position. This position varies along the trajectory throughout the entire observation period. Another example would be chemical processes or reactions where measurements like pressure or other variables must be continuously observed due to their change over time.

### Exercise Number One: The Miami Casino Game

Imagine you've won a competition: an all-expenses-paid trip to a five-star hotel in Miami, Florida, United States. At this hotel, there's a casino where you decide to gamble, but you're not interested in traditional games. So, you opt for a new one with the following rules:

* In each round, an **unbiased coin** is tossed repeatedly until the **difference between the number of heads and tails** that appears reaches **three**.
* If you decide to participate, you must **pay one dollar for each coin toss**. You **cannot abandon the game** until it finishes, or you will incur a penalty.
* You **receive eight dollars at the end of the game**.

This means you win money if the number of tosses is less than eight, but you lose money if the coin is tossed more than eight times.

Let's follow these examples where C **is Heads** and S **is Tails**.

| Resultados  | Lanzamientos | Ganancias   |
| ----------- | ------------ | ----------- |
| CCC         | 3            | Se gana 5   |
| CSCCC       | 5            | Se gana 3   |
| SCCSCSCSSSS | 11           | Se pierde 3 |

Now try to play this game, but first lets make a simualtion in Python in order to know what woukd happen.

```python
import random
# define las variables del codigo.
def simular_juego():
    caras = 0
    sellos = 0
    lanzamientos = 0

    while abs(caras - sellos) < 3:
        lanzamiento = random.choice(['C', 'S'])
        if lanzamiento == 'C':
            caras += 1
        else:
            sellos += 1
        lanzamientos += 1

    # Calcula el resultado financiero
    ganancia = 8 - lanzamientos
    return lanzamientos, ganancia

def simular_varios_juegos(n):
    resultados = [simular_juego() for _ in range(n)]
    for i, (lanzamientos, ganancia) in enumerate(resultados):
        print(f"Juego {i+1}: {lanzamientos} lanzamientos, {'ganó' if ganancia > 0 else 'perdió'} {abs(ganancia)} dólares")

# Simula N juegos, selecciona la cantidad de juegos que deseas evaluar
simular_varios_juegos(10)

```

{% hint style="info" %}
Game 1: 3 tosses, won $5\
Game 2: 3 tosses, won $5\
Game 3: 15 tosses, lost $7\
Game 4: 7 tosses, won $1\
Game 5: 7 tosses, won $1\
Game 6: 3 tosses, won $5\
Game 7: 7 tosses, won $1\
Game 8: 3 tosses, won $5\
Game 9: 5 tosses, won $3\
Game 10: 5 tosses, won $3

-¿are you in?
{% endhint %}

### Now let's try to perform this small Simulation in EXCEL.

We need to generate a sequence of random observations from a **uniform distribution between 0 and 1**. To refer to random observations from a uniform distribution, we will use the **"RAND()"** function.

Where: The probability of getting Heads is ½ and the probability of getting Tails is ½.

$$
P(Caras) = \frac{1}{2} ; P(sellos) = \frac{1}{2}
$$

| Lower bound | Uper bound |   |
| ----------- | ---------- | - |
| 0,0000      | 0,4999     | C |
| 0,5000      | 0,99999    | S |

_We use the formula_

$$= IF(RANDOM \lt 0,5, "Cara", "Sello").$$

You can use other cells where you have the "countif" functions to count the "heads" and "tails," calculating the difference to know when to stop.

{% hint style="success" %}
From the book . Hillier, F. S., & Lieberman, G. J. (2010). IO1 Introduction (9th ed.). McGraw-Hill
{% endhint %}

### Queueing Theory in Simulation: An Illustrative Approach

Let´s consider the  M/M/1 with the fowolling parameters

* Poisson arrivals, exponential service time, and a single server. Where the arrival rate... $$\lambda = 3u/hr \ y \ \mu= 5u/hr$$

The system is straightforward: arriving customers join a queue, are served, and then leave the system. We start the simulation clock at 0, i.e., t=0. We will have a one-hour simulation run, where the current state of the system is:

$$
N(t) = Qty\ of\ Client\ in\ time\ t
$$

The events, as we previously stated in the explanation, that change the system's state are the **arrival** and **departure** of customers from the system.

The state transition formula is:

$$
Reestablecer\ N(t) = \left\{ \begin{aligned}N(t) +1 \text{ arrive in time t } \\ N(t) - 1 \ \text{service completed in time t}\end{aligned} \right\}
$$

### Behavior and Steps to Solve a Problem M/M/1

An M/M/1 system is a basic queuing theory model used to represent a system with arrivals, one service, and a single queue. The system's behavior and the steps required to solve related problems are detailed below:

1. System Definition:
   * Arrivals: Customers arrive following a Poisson process with an arrival rate $$(\lambda)$$, which means that the time between successive arrivals is random and follows an exponential distribution.
   * Service: Service times are also random and follow an exponential distribution with a service rate $$(\mu)$$. There is only one server available to serve customers.
   * Single Queue: The system has a single queue where customers wait their turn to be served. Once served, customers exit the system.

This model refers to the "birth and death" models of queuing theory, generally explained by the M/M/s model. This assumes that arrival times are independent and distributed according to an exponential distribution, a Poisson input process. It is known as the birth and death model when the average arrival rate and the average service rate are constant and independent of the system state. In our case, we have a single server. s = 1, which is easy to express, which would not be the case if s > 1.

the system service rate $$\mu_n$$ It represents the average rate of completed services of the entire queuing system when there are n clients in it; different case when we have multiple servers (s > 1) then $$\mu_n$$ It is not the same as $$\mu$$,&#x20;

$$\mu = n\mu\ \text{when n is} \le s,$$ &#x20;

&#x20;$$\mu = s\mu\ \text{when n is} \ge s,$$

Using these formulas we proceed to calculate the factors $$C_n$$ of the process of birth and death

$$
C_n = \left(\frac{\lambda}{\mu}\right)^n =\rho^n, \ \text{para}\  n=0,1,2,...
$$

therefore,

$$
P_n = \rho^nP_0, \ para\ n=0,1,2,...
$$

Where,

$$
P_0 = \left( \sum_{n=0}^{\infty} \rho^n \right)^{-1}
$$

$$
=1 - \rho.
$$

$$
P_n = (1 - \rho) \rho^n \quad \forall n \in \{0, 1, 2, \ldots\}
$$

### Let's look at an example of this system.

Consider a small bank branch with a single teller. Customers arrive at this branch to be served by the teller. It is assumed that this system can be modeled as an [M/M/1,](https://en.wikipedia.org/wiki/M/M/1_queue) queue

Arrivals (M): Customer arrivals follow a Poisson process with an average rate of λ customers per unit time. This means that the times between successive arrivals are independent and identically distributed (i.i.d.) random variables according to an exponential distribution with mean $$\frac{1}{\lambda}$$

Service (M): Cashier service times follow an exponential distribution with an average service rate of μ customers per unit of time (if the cashier is busy). This means that service duration is a random variable with mean 1/μ.

Server (1): There is only one server (the cashier).

System capacity: Infinite queue capacity is assumed (customers always wait if the cashier is busy).

Queue discipline: Customers are served in order of arrival (FCFS - First Come, First Served).

For this example, we will use the following parameters:\
Average customer arrival rate (λ): 20 customers per hour.\
Average cashier service rate (μ): 25 customers per hour.

{% hint style="warning" %}
It is essential that λ<μ for the system to be stable and not grow indefinitely. In this case, 20<25, so the system is stable.
{% endhint %}

Solving, The main performance measures for a steady-state M/M/1 system are calculated with the following formulas (Gross, Shortle, Thompson, & Harris, 2008)

Server utilization factor (ρ): It is the proportion of time that the server is busy.

$$
ρ=\frac{μ}{λ}
$$

Probability that the system is empty (P0​): Probability that there are no customers in the system (the ATM is idle).

$$
P_0​=(1−ρ)
$$

Probability that there are n customers in the system (Pn​):

$$
P_n=(1−ρ)ρ^n=P_0ρ^n
$$

Average number of customers in the system (L): Includes those in queue and those being served.

$$
L = \frac{ρ}{1−ρ} = \frac{λ}{μ−λ}
$$

Average number of customers in the queue (Lq​):

$$
L = \frac{ρ^2}{1−ρ} = \frac{λ^2}{μ(μ−λ)}
$$

Average time a customer spends in the system (W): Total time from arrival to departure (waiting + service).

$$
W = \frac{L}{\lambda} = \frac{1}{\mu - \lambda}
$$

Average time a customer spends waiting in line (Wq​):

$$
W_q= \frac{\lambda}{\mu(\mu - \lambda)}
$$

It can also be calculated as $$W_q = W - \frac{1}{\mu}$$

{% hint style="info" %}
MINI TASK: Calculate each of the indices and draw your conclusions, also perform a Monte Carlo simulation and these metrics will become your indicators
{% endhint %}
