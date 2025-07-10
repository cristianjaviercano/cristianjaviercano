---
hidden: true
---

---
description: A comprehensive chapter on hypothesis testing in simulation for industrial engineering, with definitions, logic, tools, examples, exercises, and references.
---

# Hypothesis Testing in Simulation

## 1. Introduction and Definitions

Simulation is a powerful technique in industrial engineering for analyzing complex systems where analytical solutions are difficult or impossible. It allows engineers and decision-makers to model the behavior of real-world systems such as manufacturing lines, supply chains, transportation networks, and service operations under a variety of conditions. By running experiments on these models, practitioners can predict system performance, evaluate proposed changes, and identify potential improvements before implementing them in the real world.

However, simulation outputs are inherently subject to **randomness** and variability, especially when the model incorporates stochastic elements such as random arrivals, service times, or equipment failures. This means that results from a single simulation run might not be representative of the system’s true performance. To obtain meaningful insights, simulations are typically run multiple times (replications), producing sample data that must be analyzed statistically.

When comparing different scenarios or evaluating the impact of a change (for example, adding another server to a queue, changing inventory policies, or modifying process layouts), it is not enough to simply observe an improvement in the simulation output. Random variation might cause apparent differences even when there is no true effect. For this reason, **statistical hypothesis testing** becomes a crucial step in simulation analysis.

**Hypothesis testing** provides a formal, mathematical framework to decide whether observed differences between systems, policies, or configurations are likely due to actual changes or simply random chance. It helps to answer questions like:
- Is the new scheduling policy truly reducing waiting times, or could the observed decrease be random?
- Does a proposed system modification lead to a statistically significant reduction in costs?
- Are two competing suppliers’ delivery performances statistically different?

By applying hypothesis tests to simulation results, industrial engineers can make **data-driven decisions** with confidence, minimizing the risk of implementing costly or ineffective changes. This rigorous approach ensures that any claimed improvements are supported by statistical evidence, not just by chance observations.

### Relevance in Industrial Engineering

- **Decision Making**: Hypothesis testing helps to justify changes in processes, layouts, or resource allocations based on simulation outcomes.
- **Validation and Verification**: Ensures that simulation models accurately represent real systems and that any improvements are statistically meaningful.
- **Performance Comparison**: Allows for rigorous comparison between different scenarios, policies, or configurations.

### Key Terms

| Term                  | Definition                                                                                   |
|-----------------------|----------------------------------------------------------------------------------------------|
| Hypothesis            | A claim or statement about a characteristic of a population or model.                        |
| Null Hypothesis ($H_0$) | The default assumption that there is no effect or difference.                                |
| Alternative Hypothesis ($H_1$) | The claim we test for, stating there is an effect or difference.                     |
| Test Statistic        | A value calculated from sample data used to decide whether to reject $H_0$.                  |
| p-value               | The probability of obtaining a test statistic as extreme as the observed, assuming $H_0$ true.|
| Significance Level ($\alpha$) | The threshold probability for rejecting $H_0$ (commonly 0.05 or 0.01).               |
| Type I Error          | Rejecting $H_0$ when it is actually true (false positive).                                   |
| Type II Error         | Failing to reject $H_0$ when $H_1$ is true (false negative).                                 |
| Power                 | The probability of correctly rejecting $H_0$ when $H_1$ is true.                             |
| Confidence Interval   | A range of values within which the true parameter is likely to fall.                         |

***

## 2. The Main Logic Path for Hypothesis Testing

The process of hypothesis testing in simulation follows these general steps:

1. **State the Hypotheses**  
   - Formulate the null hypothesis ($H_0$) and the alternative hypothesis ($H_1$).
2. **Select the Significance Level ($\alpha$)**  
   - Common choices: 0.05 or 0.01.
3. **Choose the Appropriate Test**  
   - Depends on data type, sample size, and assumptions (e.g., normality).
4. **Collect and Summarize Data**  
   - Run the simulation, collect output data, and compute relevant statistics.
5. **Calculate the Test Statistic**  
   - Use the formula appropriate for the chosen test.
6. **Determine the p-value or Critical Value**  
   - Compare the observed test statistic to theoretical distributions.
7. **Make a Decision**  
   - If p-value < $\alpha$, reject $H_0$; otherwise, do not reject $H_0$.
8. **Draw Conclusions and Interpret Results**  
   - State the practical implications of the findings in the context of the simulation.

> **Tip:** In simulation, it's important to account for random variability by using multiple replications and proper random seeds.

***

## 3. Tools for Hypothesis Testing in Simulation

Below is a table of commonly used hypothesis tests in simulation environments, with their typical use cases:

| Test Name                 | Use Case / Example                                  | When to Use                                         | Example Command (Python/Excel)           |
|---------------------------|-----------------------------------------------------|-----------------------------------------------------|------------------------------------------|
| **t-test**                | Compare means of two systems                        | Data is continuous, samples independent, normality   | `scipy.stats.ttest_ind(A, B)`            |
| **Paired t-test**         | Compare two scenarios on the same system            | Paired data (e.g., before/after), normality         | `scipy.stats.ttest_rel(A, B)`            |
| **ANOVA**                 | Compare means for more than two systems             | More than two groups, normality, equal variances     | `scipy.stats.f_oneway(A, B, C)`          |
| **Mann-Whitney U**        | Non-parametric comparison of two systems            | Data not normal, ordinal/continuous, independent     | `scipy.stats.mannwhitneyu(A, B)`         |
| **Kruskal-Wallis**        | Non-parametric for more than two groups             | Non-normal, more than two groups                    | `scipy.stats.kruskal(A, B, C)`           |
| **Chi-square Test**       | Test for categorical data distributions             | Categorical data, frequency comparison              | `scipy.stats.chisquare(observed, expected)` |
| **Confidence Interval**   | Estimation of mean or other parameter               | Any simulation output                               | `scipy.stats.t.interval(...)`             |
| **Variance Test (F-test)**| Compare variances of two systems                    | Normal data                                         | `scipy.stats.levene(A, B)`                |
| **Proportion Test**       | Compare proportions between systems                 | Binary outcomes                                     | `statsmodels.stats.proportions_ztest`     |

> For Excel, use functions like `T.TEST`, `ANOVA`, or `CHISQ.TEST` as appropriate.

***

## 4. Examples

### Example 1: M/M/1 Queue (Single-Server System)

**Scenario:**  
Suppose a bank simulates two queueing policies and wants to know if the average customer waiting time is significantly reduced by the new policy.

- **$H_0$:** The mean waiting time is the same for both systems.
- **$H_1$:** The mean waiting time is different under the new policy.

**Steps:**
1. Simulate both systems for 30 replications each.
2. Collect the average waiting times for both.
3. Use a two-sample t-test to compare means.

**Python Example:**
```python
from scipy.stats import ttest_ind
# Suppose wait_times_old and wait_times_new are lists of 30 averages each
t_stat, p_value = ttest_ind(wait_times_old, wait_times_new)
if p_value < 0.05:
    print("Reject H0: Significant difference in means.")
else:
    print("Fail to reject H0: No significant difference.")
```

### Example 2: Restaurant Simulation

**Scenario:**  
A restaurant wants to test if a new seating arrangement reduces the average time customers spend in the system.

- **$H_0$:** The mean total time in system is equal for both layouts.
- **$H_1$:** The mean total time in system is less with the new layout.

**Steps:**
1. Simulate both layouts, using paired simulation (same random seeds).
2. Collect paired results for 20 replications.
3. Use a paired t-test.

**Python Example:**
```python
from scipy.stats import ttest_rel
# Suppose times_old and times_new are paired lists of 20 values
t_stat, p_value = ttest_rel(times_old, times_new)
if p_value < 0.05:
    print("Reject H0: New layout reduces time in system.")
else:
    print("Fail to reject H0: No significant reduction.")
```

***

## 5. Exercises and Discussion Questions

### Exercises

1. Simulate an M/M/1 queue under two different arrival rates. Test if the average queue length is significantly different.
2. Compare two inventory policies in a store simulation. Use hypothesis testing to determine if stockouts are reduced.
3. Test if changing the number of servers in a bank reduces customer wait time using ANOVA with three server configurations.
4. Run a simulation of a call center with and without a callback option. Test if customer satisfaction scores differ using a non-parametric test.
5. Simulate a production line. Test if a new scheduling rule reduces the standard deviation of job completion times.
6. Compare the proportion of customers served within 5 minutes in two different restaurant layouts.
7. Using simulation, generate batch data from two machines. Test if their output variance is the same.
8. Simulate a hospital emergency department before and after a process improvement. Test if the mean patient length-of-stay has changed.
9. Run a simulation comparing two inventory reorder points. Test if the mean time between stockouts is different.
10. Create a simulation with a known output. Add noise to the data and verify the power of a hypothesis test by repeating it multiple times.

### Discussion Questions

1. Why is it important to use multiple replications in simulation studies?
2. When might a non-parametric test be preferred over a parametric test in simulation analysis?
3. What is the impact of increasing the number of replications on the power of a test?
4. How can random number seed selection affect hypothesis testing in simulation?
5. What are the risks of Type I and Type II errors in simulation-based decision making?
6. Discuss the limitations of using only the mean as a performance measure in simulation output analysis.
7. When comparing multiple scenarios, why might you need to adjust the significance level (e.g., Bonferroni correction)?
8. How can confidence intervals complement hypothesis tests in simulation?
9. Can hypothesis testing prove that two systems are "the same"? Why or why not?
10. What role does practical significance play versus statistical significance in simulation studies?

***

## 6. Further Reading and References

- Law, A. M., & Kelton, W. D. (2015). **Simulation Modeling and Analysis** (5th ed.). McGraw-Hill.
- Banks, J., Carson, J. S., Nelson, B. L., & Nicol, D. M. (2010). **Discrete-Event System Simulation** (5th ed.). Pearson.
- Kelton, W. D., Sadowski, R. P., & Sturrock, D. T. (2014). **Simulation with Arena** (6th ed.). McGraw-Hill.
- Montgomery, D. C., & Runger, G. C. (2014). **Applied Statistics and Probability for Engineers** (6th ed.). Wiley.
- Pidd, M. (2004). **Computer Simulation in Management Science** (5th ed.). Wiley.
- Banks, J. (2010). **Handbook of Simulation: Principles, Methodology, Advances, Applications, and Practice**. Wiley.

> For more code examples, see documentation for `scipy.stats` (Python) or the Data Analysis Toolpak in Excel.

***
