# 08\_Week\_8\_Value\_Engineering

{% hint style="info" %}
Session Objectives

* **Apply** Value Engineering principles to technology design.
* **Analyze** the functions of the prototype vs. its cost.
* **Optimize** materials and processes to reduce costs without sacrificing quality.
{% endhint %}

***

## 🧠 Theoretical Content

### 1. What is Value Engineering (VE)?

Value Engineering is a systematic method to improve the "value" of goods or products and services by examining their function.

* **Value = Function / Cost**
* You can increase Value by improving the Function or reducing the Cost.

```mermaid
math
  Value = \frac{Function}{Cost}
```

```mermaid
flowchart TD
    A["Identify Problem/Product"] --> B["Analyze Functions (What does it do?)"]
    B --> C["Brainstorm Alternatives (Creative Phase)"]
    C --> D["Evaluate Costs of Alternatives"]
    D --> E["Select Best Value Option"]
    E --> F["Implement"]
    
    style A fill:#e1bee7
    style B fill:#bbdefb
    style C fill:#fff9c4
    style D fill:#ffe0b2
    style E fill:#c8e6c9,stroke:#43a047,stroke-width:2px
```

### 2. Functional Analysis (FAST Diagram)

The Function Analysis System Technique (FAST) asks "How?" and "Why?" for every component of your technology.

```mermaid
graph LR
    Why(("WHY? (Left)")) <--> How(("HOW? (Right)"))
    
    A["Improve Process Efficiency"] --- B["Automate Data Collection"]
    B --- C["Install Arduino Sensors"]
    C --- D["Write Python Script to Centralize Data"]
```

If a component costs $100 but does not directly support the primary function (the "Why"), _it must be redesign or eliminated._

### 3. Cost Optimization Strategies

* **Component Standardization**: Using standard off-the-shelf parts (like an ESP32 instead of a custom PCB) during prototyping.
* **Software vs. Hardware**: Can a physical button ($2) be replaced by a software interface on a touchscreen ($0 marginal cost)?
* **Open Source Leverage**: Using Python libraries instead of paying for licensed analytical software.

***

## 🛠️ Class Activity: Technology Unit Cost Analysis

Goal: Calculate and optimize the Bill of Materials (BOM) or Software Stack cost for your MVP.

{% stepper %}
{% step %}
### Current Cost Calculation

List every expected component (sensors, cloud servers API calls, motors, 3D printing filament).
{% endstep %}

{% step %}
### Function Mapping

What specific function does each cost line item serve?
{% endstep %}

{% step %}
### Value Optimization

Identify the top 2 most expensive items. Force your team to brainstorm a cheaper alternative for those items without altering the core function.
{% endstep %}
{% endstepper %}

| Item                    | Cost   | Function         | Alternative                    | Reduced Cost |
| ----------------------- | ------ | ---------------- | ------------------------------ | ------------ |
| Cloud Database (AWS DB) | $50/mo | Store data       | Local SQLite / Free Tier Cloud | $0           |
| Metal Enclosure         | $30    | Protect circuits | 3D Printed PETG                | $5           |

***

## 📚 Assignments

* **Refine the BOM**: Finalize your optimized Bill of Materials.
* **Sprint Continuation**: Proceed with the physical/digital construction of the prototype using the selected and optimized components.
