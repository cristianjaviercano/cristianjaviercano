---
hidden: true
---

# Block of Exercises Chapter 2.1

In this section, we will delve into the problems presented in chapter two of the content. We will analyze the key concepts, providing a detailed understanding and addressing possible solutions \[...]

***

### Exercises 2.1. Probability

For each of the following problems, the student must:

1. **Identify and describe the Sample Space (S)** as a set.
2. **Construct a Tree Diagram** that represents the experiment and its possible final outcomes.
3. **Generate a Random Sample** of 1000 observations from this experiment using **Python** or **Excel**. If Python is used, a simple script is expected to simulate the experiment and store the result\[...]

<details>

<summary>Exercise 2.1.1</summary>

A fair coin is tossed **three consecutive times**. The sequence of heads (H) and tails (T) is recorded.

</details>

<details>

<summary>Exercise 2.1.2</summary>

A quality inspector randomly selects **two items** from a production line. Each item can be categorized as **Acceptable (A)**, **Defective (D)**, **Requires Adjustment (R)**, or **Rework (W)**.

</details>

<details>

<summary>Exercise 2.1.3</summary>

An engineering company is evaluating the success of its Research and Development (R\&D) projects. A project can have **Technical Success (TS)** or **Technical Failure (TF)**. Additionally, \[...]

</details>

<details>

<summary>Exercise 2.1.4</summary>

In a warehouse, the inventory level of a product is monitored (high (H), medium (M), low (L)) and the daily demand for that product (high (D\_H), low (D\_L)). The inventory status and demand are observe\[...]

</details>

<details>

<summary>Exercise 2.1.5</summary>

A project team must be formed with two members selected from a group of candidates consisting of **an engineer (E)**, **an economist (Ec)**, and **a designer (D)**. The two members are selected \[...]

</details>

<details>

<summary>Exercise 2.1.6</summary>

Let’s consider the results of the first inspection as initial categories: **D** (defective), **M** (minor defects), and **A** (acceptable). If it is 'M', a second inspection classifies according to \[...]

</details>

<details>

<summary>Exercise 2.1.7</summary>

A software test yields two possible results: **Pass (P)** or **Fail (F)**. If it fails, the failure can be classified as **Critical (C)** or **Non-Critical (NC)**. A test is performed on a \[...]

</details>

<details>

<summary>Exercise 2.1.8</summary>

An investor is considering an investment in a startup. The first decision is whether to **Invest (I)** or **Not Invest (NI)**. If they decide to invest, the startup can have **Success (S)** or \*\*Failu\[...]

</details>

<details>

<summary>Exercise 2.1.9</summary>

A student applies for admission to a university. The first stage is **Document Review (DR)**, which can result in **Approved (A\_DR)** or **Rejected (R\_DR)**. If approved, they move on to \[...]

</details>

<details>

<summary>Exercise 2.1.10</summary>

The performance of a machine on a production line is monitored. The machine can be **Operational (O)** or **Non-Operational (NO)**. If it is Operational, it can produce with \*\*High Efficiency (HE)\[...]

</details>

***

### Exercise Block 2.2

<details>

<summary><strong>Problem 1: Monitoring Process Parameters</strong></summary>

In an industrial process, two critical parameters are monitored to ensure product quality: **temperature (T)** and **pressure (P)**. The process is considered **under control** if \[...]

A product is randomly selected and the status of its parameters is recorded.

1. **Sample Space (S):** Define the sample space representing the possible combinations of temperature and pressure states (e.g., (T\_opt, P\_opt)).
2. **Events:**
   * **Event A**: Temperature is within the optimal range.
   * **Event B**: Pressure is within the optimal range.
3. **Intersection:**
   * Describe the **event A∩B** (the intersection of A and B) in words.
   * List the elements of **A∩B** as a subset of S.
   * What does this event mean in the context of the problem?

</details>

<details>

<summary><strong>Problem 2: Rolling Two Dice</strong></summary>

**Two fair six-sided dice** (one red and one blue) are rolled simultaneously and the result of the upper face of each die is recorded.

1. **Sample Space (S):** Define the sample space of this experiment as the set of ordered pairs (result red die, result blue die). It is not necessary to list all 36 elements\[...]
2. **Events:**
   * **Event X**: The sum of the numbers on the two dice is 7.
   * **Event Y**: The number on the red die is greater than 4.
3. **Intersection:**
   * Describe **event X∩Y** in words.
   * List the elements of **X∩Y** as a subset of S.

</details>

<details>

<summary><strong>Problem 3: Software Preference Survey</strong></summary>

An engineering company conducts a survey among its employees about their preferred software for data analysis. Employees may prefer **Python (P)**, **R (R)**, **both**, or **none**.

1. **Sample Space (S):** Define the sample space representing the possible employee preferences.
2. **Events:**
   * **Event M**: The employee prefers Python.
   * **Event N**: The employee prefers R.
3. **Intersection:**
   * Describe **event M∩N** in words.
   * List the elements of **M∩N** as a subset of S.
   * What implication does this event have for software use in the company?

</details>

<details>

<summary><strong>Problem 4: Security Audit Results</strong></summary>

In an IT security audit, a system is classified according to two criteria: whether it presents **critical vulnerabilities (CV)** and whether it has suffered **security breaches (SB)** in the past year\[...]

A system is randomly selected for the audit.

1. **Sample Space (S):** Define the sample space of the possible combinations of audit results (e.g., (CV, SB)).
2. **Events:**
   * **Event G**: The system does not present critical vulnerabilities.
   * **Event H**: The system has suffered security breaches.
3. **Disjunction:**
   * Determine whether **events G and H are disjoint**. Justify your answer based on your set definitions.
   * Describe **G∩H**.

</details>

<details>

<summary><strong>Problem 6: Classification of Defects in a Product</strong></summary>

In the final inspection of a product, the types of defects found are recorded. Possible defects are: **scratches (S)**, **dents (D)**, and **electronic failures (EF)**. A product may \[...]

A product is randomly selected from the production line.

1. **Sample Space (S):** List a sample space that represents whether a product has each type of defect or not (e.g., (No S, No D, No EF), (S, No D, No EF), etc.). Consider that e\[...]
2. **Events:**
   * **Event J**: The product has at least one scratch.
   * **Event K**: The product has only dents (and no other defect).
   * **Event L**: The product has no defect.
3. **Disjunction:**
   * Are **events K and L disjoint**? Justify your answer and describe their intersection.
   * Are **events J and L disjoint**? Justify your answer and describe their intersection.

</details>

<details>

<summary>Problem 7: Management of Multiple Projects</summary>

An engineering company manages **three different projects** simultaneously: Project Alpha (α), Project Beta (β), and Project Gamma (γ). At the end of each quarter, each project is evaluated as e\[...]

A project manager is interested in analyzing the quarterly results of these three projects. The result of each project is recorded.

**Requirements:**

1. **Sample Space (S):**
   * Define the sample space (S) representing all possible combined outcomes of the three projects at the end of the quarter. The elements of S must be ordered tuples (result α, result β, result γ\[...]
   * Describe S as a set.
2. **Definition of Events as Sets:** Describe the following events as subsets of S:
   * **Event A**: At least two projects result in Success.
   * **Event B**: Project Alpha results in Success and Project Beta in Failure.
   * **Event C**: All projects have the same result (all Success or all Failure).
   * **Event D**: Only one project results in Success.
3.  **Intersection Analysis:** For the following pairs of events, do the following:

    * Describe the **intersection** in words.
    * List the elements of the intersection as a subset of S.
    * Determine if the events are **mutually exclusive (disjoint)**. Justify your answer.

    a) **A∩B** b) **B∩C** c) **C∩D**

</details>

***

### Exercise Block 2.3

For each of the following problems, the student must:

1. **Identify and describe the Sample Space (S)** as a set.
2. **Define the given Events** as subsets of S.
3. **Describe in words** the requested set operations.
4. **List the resulting elements** of each requested set operation.
5. **Construct a Venn Diagram** illustrating the involved sets and the region representing the requested operation.
6. **Plot the Venn Diagram in Python** using an appropriate library (such as `matplotlib_venn` or a simple representation with `matplotlib` if the former is not available).

<details>

<summary>2.3.1 Customer Preferences on a Streaming Service</summary>

A video streaming company classifies its customers according to their preference for three content genres: **Movies (M)**, **TV Series (S)**, and **Documentaries (D)**. A customer may pr\[...]

* **Sample Space (S):** Define the sample space representing all possible combinations of preferences. For example, a customer who prefers only movies could be (M,Sc,Dc), where Sc and Dc indicate no p\[...]
* **Events:**
  * **Event A**: The customer prefers Movies.
  * **Event B**: The customer prefers TV Series.
  * **Event C**: The customer prefers Documentaries.
* **Set Operations:** a) **A∩B∩C**: Describe in words, list the elements, and plot the Venn Diagram. b) **(A∪B)∩C**: Describe in words, list the elements, and plot the Venn Diagram.

</details>

<details>

<summary>2.3.2 Evaluation of Work Teams’ Performance</summary>

In a consulting firm, a work team is evaluated on three performance criteria: **Productivity (P)**, **Quality of Work (Q)**, and **Timeliness (T)**. For each criteri\[...]

* **Sample Space (S):** Define the sample space. Use notation similar to problem 1 (e.g., (P, Q, T) for Satisfactory in all three).
* **Events:**
  * **Event X**: The team has Satisfactory performance in Productivity.
  * **Event Y**: The team has Satisfactory performance in Quality of Work.
  * **Event Z**: The team has Satisfactory performance in Timeliness.
* **Set Operations:** a) **X∪Y∪Z**: Describe in words, list the elements, and plot the Venn Diagram. b) **(X∩Y)∪Zc**: Describe in words, list the elements, and plot the Venn Diagram.

</details>

<details>

<summary>2.3.3: Fault Detection in a Complex System</summary>

A complex electronic system consists of three independent subsystems: Subsystem 1 (S1), Subsystem 2 (S2), and Subsystem 3 (S3). It is recorded whether each subsystem has a **failure (F)** or is \*\*oper\[...]

* **Sample Space (S):** Define the sample space. Use notation like (F, O, F) to indicate Failure in S1, Operational in S2, Failure in S3.
* **Events:**
  * **Event E1**: Subsystem 1 has a failure.
  * **Event E2**: Subsystem 2 has a failure.
  * **Event E3**: Subsystem 3 has a failure.
* **Set Operations:** a) **(E1∪E2)∪E3**: Describe in words, list the elements, and plot the Venn Diagram. b) **E1∩(E2c∪E3)**: Describe in words, list the elements, and plot the Venn Diagram.

</details>

#### VENN Diagram in Python

```python
from matplotlib_venn import venn3, venn3_circles
import matplotlib.pyplot as plt

plt.figure(figsize=(8, 8))
venn = venn3(subsets=(1, 1, 1, 1, 1, 1, 1), set_labels=('Movies (A)', 'Series (B)', 'Documentaries (C)')) # These are arbitrary values for visualization
# To shade the intersection A ∩ B ∩ C, use the '111' index
venn.get_patch_by_id('111').set_color('blue') # Color the intersection
venn.get_patch_by_id('111').set_alpha(0.4) # Adjust transparency

plt.title("Venn Diagram: Intersection A $\\cap$ B $\\cap$ C")
plt.show()

# For other operations, adjust the subsets parameters and the patch IDs to color.
# The patch IDs in venn3 are:
# '100': only A
# '010': only B
# '001': only C
# '110': A ∩ B (not C)
# '101': A ∩ C (not B)
# '011': B ∩ C (not A)
# '111': A ∩ B ∩ C
# '000': Complement of the union (outside all circles)
```

***

{% hint style="info" %}
for more exercises, see pages 42 to 44 of the book "Estadística y Probabilidad para Ingenieros."
{% endhint %}

***

<details>

<summary>Exercise 2.4.1 Conditional Probability</summary>

Suppose we have a sample space S consisting of the adult population of a small town that meets the requirements to obtain a university degree. We classify them according to \[...]

<table><thead><tr><th></th><th data-type="number">Employed</th><th data-type="number">Unemployed</th><th data-type="number">Total</th></tr></thead><tbody><tr><td>Man</td><td>460</td><td>40</td><td>null</td></tr></tbody></table>

</details>
