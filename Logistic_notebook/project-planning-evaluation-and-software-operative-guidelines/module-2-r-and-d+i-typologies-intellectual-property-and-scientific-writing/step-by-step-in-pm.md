# step by step in PM

Good project planning must answer five key questions: **What needs to be done?** **How will it be done?** **Who will do it?** **When?** and **How much will it cost?**

## 1. Project Planning Basics

To achieve successful planning, the main steps are:

{% stepper %}
{% step %}
### Define the Scope

Clearly establish the problem to be solved and use a Work Breakdown Structure (WBS) to divide the project into smaller, more manageable tasks.
{% endstep %}

{% step %}
### Create the Schedule

Define the activities, order them in a logical sequence, and estimate how much time each will take.
{% endstep %}

{% step %}
### Assign Resources

Determine the personnel, equipment, and materials needed to execute the tasks.
{% endstep %}

{% step %}
### Estimate the Budget

Calculate the costs associated with each activity and define the total budget.
{% endstep %}

{% step %}
### Analyze Risks

Identify potential issues that could occur during the project and develop a contingency plan ("Plan B") to mitigate them.
{% endstep %}
{% endstepper %}

### Planning Process Diagram

```mermaid
graph TD
    A[Start Project Planning] --> B[Define Scope & WBS]
    B --> C[Create Schedule]
    C --> D[Assign Resources]
    D --> E[Estimate Budget]
    E --> F[Analyze & Mitigate Risks]
    F --> G[Plan Approved]
    
    style A fill:#e0f2fe,stroke:#0284c7
    style G fill:#dcfce7,stroke:#16a34a
```

## 2. Project Formulation Studies

Formulation is the set of activities used to gather and process information. It is specifically composed of four fundamental studies:

{% stepper %}
{% step %}
### Market Study

Analysis of demand, supply, prices, and commercialization to ensure the project has a real space in the market.
{% endstep %}

{% step %}
### Technical Study

Answers how much, where, how, and with what the product or service will be produced (includes size, location, and project engineering).
{% endstep %}

{% step %}
### Organizational Study

Defines the administrative structure, roles, and functions necessary to execute and operate the project.
{% endstep %}

{% step %}
### Legal Study

Establishes the legal framework and regulations that will govern the project across all its stages.
{% endstep %}
{% endstepper %}

### Formulation Studies Diagram

```mermaid
graph TD
    Root[Project Formulation]
    
    Root --> MS[Market Study]
    MS --> MS1[Demand & Supply]
    MS --> MS2[Prices]
    MS --> MS3[Commercialization]
    
    Root --> TS[Technical Study]
    TS --> TS1[Location]
    TS --> TS2[Engineering]
    TS --> TS3[Size & Capacity]
    
    Root --> OS[Organizational Study]
    OS --> OS1[Admin Structure]
    OS --> OS2[Roles & Functions]
    
    Root --> LS[Legal Study]
    LS --> LS1[Legal Framework]
    LS --> LS2[Regulations & Norms]
```

## 3. The Pre-Investment Phase

These stages make up the pre-investment phase of a project and function as a process of "buying certainty", where each step deepens the level of detail to reduce risk before spending money:

{% stepper %}
{% step %}
### Idea

The problem or need is identified, and basic solution alternatives are proposed. Cost and revenue calculations are global and based on experience and existing information.
{% endstep %}

{% step %}
### Profile

A preliminary analysis using secondary information (no field research is done). It serves to discard clearly unviable alternatives.
{% endstep %}

{% step %}
### Pre-feasibility (Preliminary Project)

Deepens the study of the market, technology, and profitability using primary (dynamic) information. Compares viable options and selects the best alternative.
{% endstep %}

{% step %}
### Feasibility

The definitive analysis of the selected option. It deals with finer details, such as written quotes, established contracts, and architectural plans to make the final investment decision.
{% endstep %}

{% step %}
### Design

Once the project is approved, the definitive design (such as detailed engineering) is elaborated to begin material execution.
{% endstep %}
{% endstepper %}

### Pre-Investment Funnel

```mermaid
graph LR
    Idea[1. Idea<br>Basic concepts] --> Profile[2. Profile<br>Secondary info]
    Profile --> Prefeasibility[3. Pre-feasibility<br>Primary info]
    Prefeasibility --> Feasibility[4. Feasibility<br>Final analysis]
    Feasibility --> Design[5. Design<br>Detailed engineering]
    
    style Idea fill:#fef08a,stroke:#ca8a04,stroke-width:2px
    style Design fill:#bbf,stroke:#2563eb,stroke-width:2px
```

## 4. Project Life Cycle: Execution to Evaluation

After pre-investment and design, the project moves into its active phases:

{% stepper %}
{% step %}
### Investment or Execution

In this stage, the project materializes. It involves activities like buying land, building facilities, acquiring machinery, and recruiting and training personnel. This phase concludes with "commissioning" (startup), where installed capacity is tested to ensure the project is fully operational.
{% endstep %}

{% step %}
### Operation

Once installed, the project officially starts. The generation of the good or service intended to solve the original problem or need begins.
{% endstep %}

{% step %}
### Evaluation of Results

After a reasonable time of operation, it is verified whether the project effectively solved the initial problem. This serves to evaluate the real impact (such as job creation or social benefits) and apply corrective measures if things did not go as expected.
{% endstep %}
{% endstepper %}

### Execution and Operation Flow

```mermaid
sequenceDiagram
    participant P as Pre-Investment
    participant E as Execution (Investment)
    participant O as Operation
    participant R as Results Evaluation
    
    P->>E: Handover Approved Design
    note over E: Build, Procure, Train
    E->>E: Commissioning / Startup
    E->>O: Project goes Live
    note over O: Generate Goods/Services
    O->>R: Operating Data
    note over R: Measure Impact, Apply Corrections
```
