---
hidden: true
icon: rectangles-mixed
---

# Exercises Chapter One

1. Systems Identification.&#x20;
   1. Select three systems from your everyday environment (e.g., a university cafeteria, the course registration process, your city's public transportation system). For each:&#x20;
      1. Describe its main components.&#x20;
      2. Identify the key inputs and outputs.&#x20;
      3. Propose two different objectives that could justify a simulation study for that system.
2. Abstraction and Simplification: Consider a pizza production system in a busy restaurant. Describe how you would model this system with two different levels of abstraction:&#x20;
   1. Level 1 (High): Focused on daily capacity and overall order flow.&#x20;
   2. Level 2 (Detailed): Focused on the movement of each pizza, oven usage, and staff allocation.&#x20;
      1. Justify the simplifications made at each level. Logically diagram the results in Anylogic/flexym.
3. Model Classification For the following industrial engineering scenarios, classify the most appropriate model type (static/dynamic, deterministic/stochastic, continuous/discrete) and justify your answer:&#x20;
   1. Determine the optimal number of units of a product to order for a single sales period, with uncertain demand.&#x20;
   2. Analyze the heat flow through the wall of an industrial furnace over time.&#x20;
   3. Schedule the sequence of jobs on a machine to minimize total completion time, assuming fixed process times.&#x20;
   4. Evaluate the performance of a call center where call arrivals and handling times vary.
4. SED Components Possible entities.&#x20;
   1. Attributes relevant to a "car" entity.&#x20;
   2. Main activities.&#x20;
   3. Key events occurring in the system.&#x20;
   4. Variables that would define the system state.

***

### Discussion Questions

1. In what situations do you think an analytical (exact mathematical) model would be preferable to a simulation model, and vice versa? Provide examples.
2. Discuss the potential pitfalls of making decisions based on a simulation model that has not been adequately validated. What might be the consequences in a production environment?
3. How does the process of verifying a simulation model relate to software quality principles and good programming practices?
4. If a simulation model is a simplification of reality, how can we trust its results to make decisions about the real system?

***

### [Digital Chapter One Quizz](https://forms.office.com/r/TgMZHF6w0C)

***

## Queuing Theory Exercise

#### **Problem 1:**

A coffee shop has a single server serving customers. The time between customer arrivals follows an exponential distribution with a mean rate of 10 customers per hour, and the service time for each customer also follows an exponential distribution with a mean rate of 12 customers per hour. Based on this information:

Queuing System Diagram:

* Use a diagram to represent the queuing system, identifying the server, arrival, and customer service.\
  Use the formulas in the (M/M/1) model to solve for these metrics.

#### **Problem 2:**

In another section of the cafeteria, a different queuing system has been implemented. This new system has two servers serving customers. The time between customer arrivals follows an exponential distribution with a mean rate of 8 customers per hour, while each server has a service rate of 10 customers per hour. Based on this information:

Queuing System Diagram:

* Use a diagram to represent this new queuing system, highlighting the two servers, the arrival of customers, and the service process.

Use the formulas in the (M/M/2) model to calculate system metrics such as the probability that a customer will have to wait and the average time in the system.

#### **Problem 3:**

An inventory system has been designed in which orders arrive continuously and are fulfilled under a periodic review policy. The order arrival rate follows a Poisson distribution with a mean of 5 orders per day. The lead time to replenish inventory has a mean of 2 days and follows an exponential distribution. Based on this information:

Inventory System Diagram:

* Draw a diagram representing the order flow and replenishment process.

Use relevant formulas to calculate system metrics such as expected inventory level and stockout probability.

#### Problem 4:

Juan and Pedro are two hairdressers who operate independently. They have two chairs for clients waiting for their cut, because the number of clients in the system varies between 0 and 4, for n = 1, 2, 3, 4, the probability of. $$P_n$$ that there are exactly n clients in the system is:

$$
P_0 = \frac{1}{16}, P_1 = \frac{4}{16}, P_2 = \frac{6}{16},P_3 = \frac{4}{16},P_4 = \frac{1}{16}.
$$

1. Calculate L and how would you explain it to the hairdressers?
2. For each possible value of the number of customers in the system, specify how many customers are in the queue, and how would you explain it to the hairdressers?
3. Given that an average of 4 customers arrive per hour and are waiting for a cut, determine W and Wq. Describe the results in terms the hairdressers understand.
4. Assuming both are equally fast in the hairdressing service, what is the expected duration of the cut?
