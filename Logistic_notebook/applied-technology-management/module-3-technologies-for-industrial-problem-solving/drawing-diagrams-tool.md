---
icon: pen-ruler
---

# Drawing Diagrams tool

[Drawio](https://app.diagrams.net/).com is a free online diagramming application that allows users to create flowcharts, network diagrams, UML diagrams, and more. To use Draw.io:

1. Open the website: [Drawio](https://app.diagrams.net/).com
2. Choose to work offline or connect to your Google Drive, Dropbox, or other storage services to save your diagrams.
3. Select a template or start with a blank canvas.
4. Use the drag-and-drop interface to add shapes, connectors, and labels.
5. Save or export your diagram in various formats like PNG, PDF, or SVG.

<figure><img src="../../.gitbook/assets/Captura de pantalla 2025-08-17 a la(s) 8.13.17 a.m..png" alt="" width="375"><figcaption></figcaption></figure>

***

In order ti create the user interface and all the flow of the Integral solution, need to use some diferents diagramas to explain.

1. **User Flow Diagram with Embedded Wireframes:** This is the main diagram. It maps the user's journey through the application. Each step in the flow would not just be a box with text but a simplified wireframe of the screen.&#x20;
2. **Entity-Relationship Diagram (ERD):** This is the standard for modeling the database structure. Simplified Component Diagram: This diagram shows the logical modules of the backend.
3. **Component Diagram (Simplified):** This diagram illustrates the backend's logical modules.

***

## User Flow Diagram With Embedded Wireframes

A user flow diagram with embedded wireframes is a visual representation that combines both the journey a user takes through an application and sketches or simplified versions of the screens they will encounter. This type of diagram is particularly beneficial for understanding the user experience design and ensuring every screen's purpose is clear.

#### User Interface Flowchart (UI Flow) 

{% hint style="warning" %}
Theoretical Basis: A UI Flowchart is a visual model that represents the navigation path a user follows through the various pages or views of an application. Unlike a process flowchart (which models business logic), a UI Flow diagram focuses on the user experience (UX), showing how interfaces are connected and what actions (clicking buttons, filling out forms) trigger the transition from one screen to another. Its purpose is to define the information architecture and ensure logical and intuitive navigation (Nielsen & Budiu, 2012).
{% endhint %}

### Steps to Create a User Flow Diagram with Embedded Wireframes:

1. **Identify User Tasks:** Determine the primary tasks users need to accomplish within your application.
2. **Define Entry and Exit Points:** Specify where users will start their journey and the potential endpoints based on different paths they may take.
3. **Map Out Key Screens:** Create simplified wireframes for each significant screen or interaction point in the user journey.
4. **Add Annotations:** Include notes or labels on your wireframes to clarify the functionality or purpose of each element.
5. **Link Screens in Sequence:** Use arrows or lines to connect related screens, clearly indicating the flow between them.

By following these steps, you can create a comprehensive user flow diagram that provides clarity and direction for both designers and developers working on the project.

> lets make an example of a inventory store aplication.

To create a solution, first define the main goal of the application to develop the solution app. In this case, we will create an inventory management tool for a retail store that can handle different types of items like food, groceries, beverages, and their expiration dates.

Similar to any inventory system, it includes three main processes and specific KPIs. The primary processes are:

1.  #### Inbound Process

    The inbound process involves the systematic receipt and management of goods and materials arriving at a facility. Key steps include:

    1. **Receiving**: Accept incoming shipments and verify them against purchase orders.
    2. **Inspection**: Check goods for quality and accuracy.
    3. **Unpacking**: Open containers and prepare items for storage.
    4. **Inventory Management**: Update inventory records and organize items in designated storage locations.
    5. **Quality Control**: Conduct thorough checks to ensure products meet standards.
    6. **Documentation**: Maintain accurate records of all inbound activities for auditing and tracking.

    Effective inbound processing ensures smooth operations, accurate inventory levels, and enhanced supply chain efficiency.
2.  **Outbound Process**

    The Outbound Process is a crucial logistics function involving the preparation and transfer of products from a company to its customers or distribution centers. This ensures that products are delivered accurately and on time. The process involves several key steps that must be executed efficiently:

    1. **Order Management**: The process begins with the receipt of customer orders through various channels such as online platforms, emails, or direct sales. This involves managing the order database and prioritizing orders based on various factors like delivery location and urgency.
    2. **Inventory Management**: Inventory levels are checked to ensure the ordered items are in stock. This involves real-time inventory tracking and making adjustments as necessary to minimize delays and meet customer demands.
    3. **Order Picking**: The picking process involves retrieving products from their storage locations based on the order list. Efficient picking strategies like batch picking or zone picking are often employed to optimize time and resources.
    4. **Quality Check**: Before packaging, the products undergo a quality check to confirm that they meet the required standards. Any defective or incorrect items are removed and replaced.
    5. **Packaging**: Products are then securely packaged using appropriate materials to prevent damage during transit. The packaging should also be labeled with necessary information such as addresses, special handling instructions, and barcodes for tracking.
    6. **Labeling**: Correct labeling is essential for ensuring that the products are directed to the right destinations. This includes printing and affixing shipping labels generated via automated systems.
    7. **Shipping**: Once packaged and labeled, the products are prepared for shipment. This involves selecting the most efficient and cost-effective transportation methods based on the destination and delivery schedule.
    8. **Tracking and Documentation**: Tracking systems are utilized to monitor the shipment's progress and communicate its status to customers and stakeholders. Accurate documentation ensures compliance with any regulatory requirements and facilitates smooth customs processing for international shipments.
    9. **Customer Communication**: Keeping customers informed about their order status and delivery timelines is vital. Automated notifications and customer service support play a role in managing expectations and addressing inquiries effectively.
    10. **Review and Feedback**: Continuous review of the outbound process is crucial for identifying areas of improvement. Feedback from customers and performance metrics assist in optimizing procedures and enhancing customer satisfaction.

    Overall, a well-organized and efficient outbound process helps companies maintain high service standards, reduce errors, and achieve customer satisfaction and loyalty.
3.  #### Inventory Management Process

    Effective inventory management is crucial for maintaining optimal stock levels, reducing costs, and ensuring customer satisfaction. The process involves several key steps as outlined below:

    1. **Demand Forecasting**:
       * Use historical sales data and market analysis to predict future inventory requirements.
       * Implement forecasting tools and techniques to increase accuracy.
    2. **Stock Replenishment**:
       * Establish reorder points and stock levels to prevent overstocking or stockouts.
       * Automate the ordering process to streamline replenishment.
    3. **Inventory Tracking**:
       * Utilize inventory management software to monitor stock levels in real-time.
       * Implement barcode or RFID systems for accurate item tracking.
    4. **Storage and Handling**:
       * Organize the warehouse to optimize space and streamline picking processes.
       * Maintain proper storage conditions to preserve product quality.
    5. **Inventory Analysis**:
       * Conduct regular inventory audits and cycle counts to verify stock levels.
       * Analyze turnover rates and adjust inventory practices as needed.
    6. **Supplier and Vendor Management**:
       * Build strong relationships with suppliers to ensure timely delivery of quality products.
       * Negotiate favorable terms and agreements to improve supply chain efficiency.
    7. **Customer Order Fulfillment**:
       * Ensure quick and accurate processing of customer orders.
       * Implement efficient packaging and shipping practices to enhance customer satisfaction.

    By following these steps, businesses can achieve better inventory control, reduce costs, and improve overall efficiency within their supply chain.

#### First step: creates a general flow of the aplication using a whiteboard or a paper.

<img src="../../.gitbook/assets/file.excalidraw (16).svg" alt="" class="gitbook-drawing">

#### Translate it to a drwaing application like Draio.com - UI flow

<figure><img src="../../.gitbook/assets/Captura de pantalla 2025-08-17 a la(s) 9.10.10 a.m..png" alt=""><figcaption></figcaption></figure>

#### The Three Core Transactional Flows:

We will design the diagrams for the following fundamental retail operations:

1. 📦 Goods Receipt (Purchase): The process of adding new stock to the inventory.
2. 🚚 Dispatch (Sale): The process of removing stock from inventory due to a customer sale.
3. 🗑️ Inventory Write-off: The process of removing stock for non-sale reasons (e.g., damaged, expired, or lost goods).

## Entity relation diagram

#### log in page:

### 🖥️ Flow: User Authentication (Log-in Page)

you will learn how to design a complete and logical diagram for a user authentication page. This diagram will serve as a professional blueprint for developing the actual application, detailing the user interface, the logical processes, and the data structure required.

Tool: Draw.io (now diagrams.net)

Objective: To securely authenticate a user's identity before granting access to the main application and to provide a way for new users to register.

This detailed diagram perfectly corresponds to the `login_user` and `register_user` functions and the `login_view` layout we have already developed in the Python code, confirming that our design process is aligned with the implementation.

### Part 1: Designing the User Interface (UI) Wireframe

The first step is to create a visual mockup of what the user will see. This is called a wireframe.

1. Create the Main Container:
   * On the left-side panel, under the "General" shapes, select the Rectangle tool.
   * Drag it onto the canvas and resize it to create a large box that will represent the entire login screen.
   * Double-click the rectangle and title it "Retail Inventory System Login".
2. Add Input Fields:
   * Drag two smaller Rectangle shapes into your main container. These will be the input boxes.
   * Use the Text tool to add labels above these boxes: "USER" and "PASSWORD".
   * To show they are input fields, double-click each box and type "Line 1" or similar placeholder text.
3. Add Action Buttons:
   * From the "General" shapes, select the Button shape (a rounded rectangle).
   * Create two buttons. Label one "Sign in" and the other "Sign up". Place them logically next to the input fields. You can also add a text label like "New around here?" to guide the user.
4. Add a Status Display:
   * Use the Text tool to add a label at the bottom of the container named "Status:". This is where error or success messages will appear.

***

### Part 2: Modeling the Database

Next, we need to define the structure of the data our application will interact with.

1. Create the Database Shape:
   * In the shape search bar, type "Cylinder" and select the database shape. This universally represents a database.
   * Place it on your canvas and label it "BD User" (User Database).
2. Define the Data Fields (Schema):
   * Using the Text tool, list the required data fields inside or next to the cylinder shape. This defines what information we need to store for each user.
     * `ID_user` (A unique identifier for each user)
     * `User_Name`
     * `Password`
     * `Mail` (Email address)

***

#### ## Part 3: Charting the Application Logic

This is the most critical part, where we map out the "thinking process" of our application using a flowchart.

1. Map the "Sign in" (Authentication) Flow:
   * Start with a Parallelogram shape (used for I/O or data entry) and label it "Check in data base". Draw a connector arrow from your "Sign in" button to this shape.
   * Draw an arrow from "Check in data base" to a Diamond shape (used for decisions). Label the diamond "User in data base?".
   * Create two branches from the diamond:
     * "Yes" Branch: Draw an arrow to a Rectangle labeled "status: User registered". This represents a successful login. From here, an arrow should point to a process box showing that the main application screen will open.
     * "No" Branch: Draw an arrow to a Rectangle labeled "status: User Not found". From this box, draw a connector back to the "Status:" label in your UI wireframe to show that an error message is displayed.
2. Map the "Sign up" (Registration) Flow:
   * Start with a Diamond shape labeled "New user?" and connect your "Sign up" button to it.
   * Create a "Yes" branch leading to a Rectangle labeled "open new user information screen". This represents showing a form to the user.
   * From there, an arrow should point to a Rectangle labeled "Storage Information".
   * Finally, draw an arrow from "Storage Information" to a Parallelogram labeled "Write User and Password", which then points to your "BD User" database shape, indicating that the new data is saved.

By completing these three parts, you will have a comprehensive and professional diagram that clearly communicates the visual design, data requirements, and logical flow of a user authentication system.

<figure><img src="../../.gitbook/assets/Captura de pantalla 2025-08-17 a la(s) 2.41.10 p.m..png" alt=""><figcaption></figcaption></figure>

***

## To Select A system Action

### How to Design an Application Landing Page

To design a central dashboard that provides the user with a real-time overview of the most important Key Performance Indicators (KPIs) and serves as the main navigation hub to the system's core modules: Inbound, Outbound, and Inventory.

#### Designing the User Interface (UI) Wireframe

This screen is a combination of data display and navigation. We will use a two-column layout for a clean and organized look.

1. **Create the Main Container:**
   * Draw a large Rectangle to represent the entire page.
   * Use the Text tool to add a header at the top. This should be dynamic, so label it "Welcome, \[User\_Name]!" and another text element for the date.
2. **Design the Navigation Column:**
   * Inside the main container, draw a narrower Rectangle on the left side to act as the navigation panel.
   * Inside this panel, place three large Button shapes, stacked vertically.
     * Label the first button "📦 Inbound".
     * Label the second button "🚚 Outbound".
     * Label the third button "📊 Inventory Management".
3. **Design the KPI Display Column:**
   * On the right side of the main container, create a wider Rectangle for the KPI dashboard.
   * Use the Text tool to create a title for this section: "Key Performance Indicators (KPIs)".
   * Add several smaller boxes to display individual KPIs. These are display-only fields. Label them clearly:
     * Total Inventory Value: (Represents the total cost of all items in stock).
     * Total Units in Stock: (The sum of all quantities).
     * Products Below Reorder Point: (A critical metric for purchasing).
     * Sales Value (Today): (Total revenue for the current day).

<figure><img src="../../.gitbook/assets/Captura de pantalla 2025-08-17 a la(s) 5.58.33 p.m..png" alt=""><figcaption></figcaption></figure>

***

### Inventory Data - Inventory Management

According to your main flowchart, this module is accessed from the landing page and is focused on providing detailed information about the inventory. This is primarily a reporting and analysis screen rather than a transactional one.

{% hint style="success" %}
Here is the detailed guide for designing the "Inventory Data" module diagram in Drawio.com
{% endhint %}

> To design a screen that allows the user to view, search, and filter the complete inventory list. This provides a comprehensive look at stock levels, locations, and associated product details.

### Part 1: Designing the User Interface (UI) Wireframe

This screen needs controls for searching and a main area to display the data table.

1. Create the Main Container and Title:
   * Draw a large Rectangle for the module's screen.
   * Add a title at the top using the Text tool: "📊 Inventory Management".
2. Add Search and Filter Controls:
   * At the top of the container, create a section for controls.
   * Add a Text Input shape and label it "Search by Product Name...". This will be our search bar.
   * Add a Dropdown shape and label it "Filter by Category (Estanteria)". This will allow users to narrow down the view to a specific shelf or category.
   * Add a Button labeled "Apply Filters".
3. Create the Data Display Area:
   * The largest part of the screen will be for displaying the inventory table.
   * Use the Table shape from the "General" library to create a representation of the data grid.
   * Define the column headers in the table: `ProductID`, `NombreProducto`, `Estanteria`, `Cantidad`, `CostoCompra`, `PrecioVenta`.
