# 14\_Week\_14\_Technology\_Valuation

## 🎯 Session Objectives

* **Understand** the methodologies used to determine how much a technology is worth.
* **Calculate** a basic financial projection for your technology-based company.
* **Apply** Net Present Value (NPV) concepts to a tech project.

***

## 🧠 Theoretical Content

### 1. Why Value Technology?

To get funding (from investors, banks, or Minciencias), you must answer: "How much money do you need, and what is the projected return on that investment?"

```mermaid
flowchart LR
    A["Invested Capital (Seed)"] --> B["R&D & Prototyping"]
    B --> C["Market Launch"]
    C --> D["Revenue Generation"]
    D --> E["Return on Investment (ROI)"]
    
    style A fill:#e1bee7
    style E fill:#c8e6c9,stroke:#43a047,stroke-width:2px
```

### 2. Valuation Methods

There are three standard ways to value an intangible asset (like a new software or a patent):

1. **Cost Approach**: How much did it cost to build? (Hours of Python coding + Arduino parts). _This is the minimum baseline._
2. **Market Approach**: What are similar startups or technologies selling for? (Using benchmarking from Week 3).
3. **Income Approach (DCF - Discounted Cash Flow)**: Projecting future revenues and discounting them to today's value (NPV). _This is the most common for investors._

### 3. The Income Approach (Simplified)

To use the income approach, you must project your business model into the future (usually 3-5 years).

```mermaid
math
    NPV = \sum_{t=1}^{n} \frac{CashFlow_t}{(1 + DiscountRate)^t} - InitialInvestment
```

* **Initial Investment**: The cost to finish TRL 9 and launch.
* **Cashflows**: Expected sales minus expected operational costs (Cloud servers, maintenance).
* **Discount Rate**: The risk factor. High risk tech uses a high discount rate (usually 20-40%).

***

## 🛠️ Class Activity: Projected Cash Flow

**Goal**: Create a 3-year cash flow projection for your project.

{% stepper %}
{% step %}
### Estimate Initial Costs (Year 0)

What do you need to launch a beta product to the market? (Patenting fees, server setup, manufacturing 10 units).
{% endstep %}

{% step %}
### Project Sales (Years 1-3)

Based on your Lean Canvas pricing, how many units/subscriptions will you realistically sell?
{% endstep %}

{% step %}
### Calculate NPV

Use Excel or Google Sheets to calculate the Net Present Value. Is the project financially viable?
{% endstep %}
{% endstepper %}

| Concept                | Year 0   | Year 1  | Year 2   | Year 3   |
| ---------------------- | -------- | ------- | -------- | -------- |
| Revenues               | $0       | $50,000 | $150,000 | $300,000 |
| Costs (Servers, parts) | $10,000  | $20,000 | $60,000  | $100,000 |
| Net Cash Flow          | -$10,000 | $30,000 | $90,000  | $200,000 |

***

## 📚 Assignments

* **Financial Model**: Submit a clean, standardized 3-year Excel projection for your project.
* **Review Minciencias MGA**: Look up the "Metodología General Ajustada" format used in Colombia for public tech funding.
