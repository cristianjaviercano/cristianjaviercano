# The Data´s Universe

This section explores the fundamentals of databases, their critical importance to industrial engineering, and the key differences between relational (SQL) and non-relational (NoSQL) models, helping you understand when and why to choose each.

### What is a Database?

An organized system for efficiently and securely storing, managing, and retrieving data. Think of it as the digital brain of any industrial operation.

**Critical Importance for the Industrial Engineer:** Source of truth for production, quality, inventory, maintenance, etc. Foundation for analysis, modeling, and simulation.

**Language:** SQL (Structured Query Language) – The standard for interacting with them.&#x20;

**Relationships:** Established through&#x20;

**Primary Keys** (unique identifier per row) and **Foreign Keys** (fields linking tables).&#x20;

**Components:** Rows (records), Columns (attributes), Schemas. Organize data into structured **tables** (like interconnected spreadsheets). Relational Databases (SQL)

**Examples:** MySQL, PostgreSQL, SQL Server, Oracle.&#x20;

**Transactionality (ACID):** Ideal for critical systems (ERP, MES).&#x20;

**Standardization:** Well-defined and mature model.&#x20;

**Data Integrity:** Ensures consistency and accuracy. Advantages for Industrial Engineering:

### Non-Relational Databases (No

They provide more adaptable data structures, transcending the limitations of traditional tabular formats. This flexibility allows for the integration and manipulation of complex, varied datasets, which can enhance the analysis and application of information across diverse fields

**Graph Databases (e.g., Neo4j):** Focused on complex relationships, suitable for supply chains and networks.

**Columnar Databases (e.g., Cassandra):** Optimized for queries on specific columns, ideal for time-series data (IoT).

**Key-Value Databases (e.g., Redis):** Store data in key-value pairs, perfect for cache and sessions.

**Document Databases (e.g., MongoDB):** Data stored in JSON/BSON documents, useful for catalogs and configurations.

### Advantages for indutrial engineers

**Specific Performance:** Fast for certain loads.&#x20;

**Schema Flexibility:** Adaptable to varied data.&#x20;

**Horizontal Scalability:** Handle large volumes of data (Big Data, IoT).&#x20;

### SQL vs. NoSQL: The Strategic Decision

It's not competition; it's complementarity. The choice depends on the specific needs of the project.&#x20;

#### Use SQL:

* Data integrity and complex relationships are
* The data are structured and consistent.
* You need ACID transactions (e.g., inventory control).

#### Use No

* You handle large volumes of diverse data (IoT, sensors)
* You need high speed

{% hint style="info" %}
in reality, some times you will need bouth of them!
{% endhint %}
