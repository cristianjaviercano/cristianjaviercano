# Module 2: R\&D+i Typologies, Intellectual Property, and Scientific Writing

### 1. Typological Distinction: Investment vs. R\&D+i

In the field of Process Engineering, it is imperative to distinguish between a traditional investment project and a Research, Development, and Innovation (R\&D+i) project.

* **Investment Project:** Aims to create or expand installed capacity to produce goods or services using _know&#x6E;_&#x74;echnologies. The risk is primarily commercial or operational.
* **R\&D+i Project:** Aims to generate new knowledge, develop prototypes, or significantly improve processes. The risk is _technological_ and epistemic (Minciencias, 2023).

According to the _Documento de Tipología de Proyectos_ (Version 7) used in the Colombian scientific ecosystem, projects are classified as follows:

#### 1.1 Scientific Research

Systematic creative work undertaken to increase the stock of knowledge.

* **Basic Research:** Theoretical or experimental work without a specific practical application in view.
* **Applied Research:** Original investigation directed towards a specific practical objective (e.g., optimizing a kinetic reaction for a specific polymer).

#### 1.2 Technological Development

The application of research findings to a plan or design for the production of new or substantially improved materials, products, or processes **before** commercial production.

* _Key Deliverables:_ Prototypes, pilot plants, beta versions.

#### 1.3 Innovation

The introduction of a new or significantly improved product (good or service) or process to the market or the organization.

* **Process Innovation:** Implementation of new production or delivery methods (e.g., changing from batch to continuous flow chemistry).
* **Product Innovation:** Introduction of a good/service with significantly improved characteristics.

### 2. Intellectual Property (IP) and Protection Strategy

Intellectual Property refers to the creations of the mind. In engineering, IP protection mechanisms are strategic assets that turn intangible knowledge into a monopoly right.

#### 2.1 Industrial Property (Patents)

A patent is an exclusive right granted for an invention. To be patentable, an invention must meet three rigorous criteria (Superintendencia de Industria y Comercio; WIPO):

1. **Novelty:** The invention must be new worldwide (not part of the "State of the Art").
2. **Inventive Step:** It must not be obvious to a "person skilled in the art" (PHOSITA).
3. **Industrial Application:** It must be capable of being made or used in an industry.

**Types:**

* **Invention Patent:** Protection for 20 years. High inventive step.
* **Utility Model:** Protection for 10 years. Known as "petty patents," applicable to tools or devices with a functional advantage derived from their shape or arrangement.

#### 2.2 The Disclosure Dilemma: Patent vs. Paper

A critical error in R\&D drafting is publishing a scientific article _before_ filing the patent application.

* **Rule:** Public disclosure (article, conference, thesis) destroys **Novelty**.
* **Strategy:** File the patent application first $\rightarrow$ Publish the scientific article second.

### 3. Drafting Technical Documents: Projects, Articles, and Patents

Each document type serves a different purpose and follows a specific structure.

| Feature          | R\&D Project Proposal                                                 | Scientific Article (Paper)                          | Patent Application                                          |
| ---------------- | --------------------------------------------------------------------- | --------------------------------------------------- | ----------------------------------------------------------- |
| **Objective**    | Secure funding and approval for execution.                            | Disseminate knowledge to the scientific community   | Define a legal monopoly over technology                     |
| **Key Audience** | Evaluators, Investors, Managers                                       | Peers, Researchers (Reviewers)                      | Patent Examiners, Lawyers, Competitors                      |
| **Structure**    | Problem $$→$$ Objectives $$→$$ Methodology $$→$$ Budget $$→$$ Impact. | IMRaD (Introduction, Methods, Results, Discussion). | Description $$→$$ Claims (Reivindicaciones) $$→$$ Drawings. |
| **Language**     | Persuasive, future tense ("We will develop...").                      | Descriptive, past tense ("We observed...").         | Legal-technical, broad scope ("A device comprising...")     |

#### 3.1 Drafting the "State of the Art" (Background)

* **In Projects:** Focus on the _gap_ in current knowledge or the _market failure_ that justifies the investment.
* **In Articles:** Focus on the theoretical framework and how this work fills a knowledge gap.
* **In Patents:** Focus on "Prior Art" (Anterioridades) to demonstrate that existing solutions are insufficient or different from the proposed invention.

### 4. Mathematical Modeling: Technology Adoption (Bass Model)

When formulating innovation projects, predicting the speed of market adoption is crucial for financial evaluation. The **Bass Diffusion Model** is the standard differential equation for this purpose.

#### 4.1 Theoretical Formulation

The model assumes adoption is driven by two coefficients:

1. **Innovation (**&#x70;**):** External influence (advertising).
2. **Imitation (**&#x71;**):** Internal influence (word of mouth).

$$
\frac{dN(t)}{dt} = \left[ p + \frac{q}{M} N(t) \right] [M - N(t)]
$$

Where:

* N(t): Cumulative adopters at time t.
* M: Total market potential.

#### 4.2 Python Implementation

```py
import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import odeint

# 1. Define the Differential Equation
def bass_model(N, t, p, q, M):
    """
    dN/dt = Rate of adoption at time t
    p: Innovation coefficient (External)
    q: Imitation coefficient (Internal/Word of Mouth)
    M: Total Market Potential
    """
    dNdt = (p + q * N / M) * (M - N)
    return dNdt

# 2. Simulation Parameters (Scenario: New Bio-reactor Technology)
M = 500         # Total potential industrial clients
p = 0.015       # Slow initial adoption (conservative advertisement)
q = 0.30        # Strong word-of-mouth (industry reputation)
t = np.linspace(0, 15, 100) # 15-year horizon
N0 = 0          # Start from zero

# 3. Solve ODE
solution = odeint(bass_model, N0, t, args=(p, q, M))
cumulative_adopters = solution.flatten()
adoption_rate = np.gradient(cumulative_adopters, t) # Sales per year

# 4. Visualization
plt.figure(figsize=(10, 6))
plt.plot(t, adoption_rate, 'g-', linewidth=2.5, label='Adoption Rate (Sales/Year)')
plt.plot(t, cumulative_adopters, 'b--', linewidth=1.5, label='Cumulative Installed Base')
plt.axvline(x=t[np.argmax(adoption_rate)], color='k', linestyle=':', alpha=0.5, label='Peak Adoption')

plt.title(f'Bass Diffusion Model: Innovation Adoption (p={p}, q={q})')
plt.xlabel('Years')
plt.ylabel('Number of Adopters (Units)')
plt.legend()
plt.grid(True, alpha=0.3)
plt.show()

# Peak Analysis
peak_time = t[np.argmax(adoption_rate)]
print(f"Peak adoption occurs at year: {peak_time:.2f}")

```

**References:**

* Minciencias. (2023). _Documento de Tipología de Proyectos de Carácter Científico, Tecnológico o de Innovación_. Versión 7.
* OECD. (2015). _Frascati Manual 2015: Guidelines for Collecting and Reporting Data on Research and Experimental Development_.
* Superintendencia de Industria y Comercio. (n.d.). _Nuevas Creaciones_.
