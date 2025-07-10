---
hidden: true
---

# Exercise Block Chapter Three

1. **Exercises 3.1**
2. **Lehmer Generator:** Implement a Lehmer generator with m=127, a=30, and $$X_0​=1$$. Generate the first 10 numbers $$X_i​$$ and the corresponding $$U_i$$​. Do you notice any obvious patterns? (Note: This is a small example for illustrative purposes, not a proper generator.)
3. **Uniformity Test (Chi-Square):** Given the following sequence of 20 numbers, supposedly U(0,1): 0.12, 0.87, 0.34, 0.65, 0.05, 0.48, 0.71, 0.92, 0.23, 0.50, 0.78, 0.19, 0.41, 0.99, 0.02, 0.68, 0.29, 0.58, 0.81, 0.38. Perform a Chi-Square test of uniformity using k=5 intervals. Use α=0.05.
4. **Inverse (Exponential) Transform:** Derive the formula for generating exponential random variables with mean μ=10 using the MTI. Generate 3 observations using $$U_1​=0.25,U_2​=0.50,U_3​=0.75$$.
5. **Inverse (Discrete) Transform:** A discrete rv X takes on values ​​1, 2, 3 with probabilities $$P(X=1)=0.3,P(X=2)=0.5,P(X=3)=0.2$$. Describe how you would generate observations of X using ITN. Generate 2 observations using $$U_1​=0.45, U_2​=0.85$$.
6. **Box-Muller:** Using $$U_1​=0.6 and U_2​=0.3$$, generate a pair of standard normal random variables (Z1​,Z2​) using the Box-Muller method. Then, transform Z\_1​ to follow an $$N(50,102)$$ distribution.
7. **Acceptance-Rejection (Conceptual):** Conceptually describe how you could use the Acceptance-Rejection method to generate variables from a PDF $$f(x)=2x$$ for $$0≤x≤1$$ (and 0 otherwise), using a maximizing PDF $$g(x)=1$$ (Uniform(0,1)). What would be the value of c? What would be the probability of acceptance?

* **Discussion Questions:**

1. Why is the term "pseudorandom" used instead of "random" for computer-generated numbers? What are the practical implications of this distinction?
2. What problems might a short-period random number generator cause in a large-scale simulation of a production system?
3. If a sequence of generated numbers passes the Chi-square test for uniformity and the lag-1 autocorrelation test, can you conclude that it is a "good" sequence for any simulation purpose? Why or why not?
4. Compare the inverse transform method and the acceptance-rejection method in terms of their generality, efficiency, and ease of implementation. When would you prefer one over the other?
5. Explain why the reproducibility of a sequence of pseudorandom numbers is a desirable feature in simulation studies.
