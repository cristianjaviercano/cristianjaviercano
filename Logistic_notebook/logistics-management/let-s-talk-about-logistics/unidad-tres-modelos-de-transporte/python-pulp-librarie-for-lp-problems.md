# Python Pulp Librarie for LP problems

## Instructions for Using the PuLP Library

The PuLP library is a powerful tool for linear programming in Python. Here we provide a step-by-step guide to using this library effectively.

### Overview of the PuLP Library

PuLP is a Python library for linear programming that simplifies the process of defining and solving optimization problems. It supports a range of solvers and enables modelers to formulate linear problems using a high-level, intuitive syntax. With PuLP, users can set up complex linear algebraic expressions as constraints and objectives, making it an ideal choice for both beginners and advanced users looking to implement optimization strategies within their Python applications.

### Using PuLP in Transportation Problems

The PuLP library can be effectively utilized to solve transportation problems by optimizing the allocation of resources such as goods or services.

### Applications of PuLP

PuLP can be applied in various fields including logistics, supply chain management, and operations research. It is particularly useful for:

* **Transportation Optimization**: Streamlining distribution systems to minimize costs and improve efficiency.
* **Production Planning**: Determining optimal production schedules considering constraints like workforce, raw materials, and machinery capacity.
* **Resource Allocation**: Efficiently distributing resources in sectors such as healthcare, finance, and manufacturing to maximize returns or minimize waste.
* **Blending Problems**: Finding the best mix of ingredients or materials for products while meeting cost and quality requirements.

You can install PuLP on any system that supports Python and has the pip package manager installed. This includes Windows, macOS, and Linux operating systems. Ensure your terminal or command prompt has access to Python and pip to successfully execute the installation command.

### Using PuLP in Google Colab

you can use PuLP in Google Colab. To do so, first ensure that it is installed by running the following command in a code cell:

```python
!pip install pulp
```

This command installs PuLP in your Colab environment, allowing you to proceed with creating and solving linear programming problems.

### Installing PuLP

Before you start using PuLP, you first need to install it. You can do this easily using pip. Open a terminal and type the following command:

```bash
pip install pulp
```

### Creating a Problem

To define a linear programming problem, you must start by importing the library and creating an `LpProblem` object. This object represents your problem.

```python
from pulp import LpProblem, LpMaximize

# Creating a Maximization Problem
problem = LpProblem("My_Problem", LpMaximize)
```

### Declaring Variables

Next, define the decision variables that will be used in your model. Pulp provides the `LpVariable` class for this purpose.

```python
from pulp import LpVariable

# Create a continuous decision variable
x = LpVariable('x', lowBound=0)
y = LpVariable('y', lowBound=0)
```

### Defining the Objective Function

The objective function is the mathematical function you need to maximize or minimize. You can define it using the variables you created.

```python
# Defining the objective function
problem += 3*x + 2*y, "Objective_Function"
```

#### Adding Constraints

Constraints are added to the problem using common mathematical operators. These limit the possible values of the variables.

```python
# Add constraints
problem += (2*x + y <= 20), "Constraint_1"
problem += (4*x - 5*y >= -10), "Constraint_2"
```

#### Problem Solving

With the objective function and constraints defined, the next step is to solve the problem. PuLP can use different solvers, but the default solver is usually sufficient for most cases.

```python
problem.solve()
```

#### Print Results

Once the problem is solved, you can access the results, such as the optimal value of the objective function and the decision variables.

```python
# Display problem status
print("Status:", LpStatus[problem.status])

# Display the optimal value of the variables
for variable in problem.variables():
print(f"{variable.name} = {variable.varValue}")

# Optimal value of the objective function
print("Optimal value: ", value(problem.objective))
```

{% hint style="info" %}
The PuLP library is a versatile tool for solving linear programming problems in Python. It allows for rapid implementation and simplifies the complexity of modeling optimization problems. With the steps described above, you can begin exploring its capabilities and applying linear programming to your projects.
{% endhint %}

This library will be used to solve transportation problems.

For more information about this library, please visit: [https://pypi.org/project/PuLP/](https://pypi.org/project/PuLP/)

1. Install the library: _“pip install pulp”_

#### Import:

* import pulp

1. Create the problem: To create the problem, we must define the variable that will store the problem, for example, "prob." # Create the problem with the command _"pulp.LpProblem"_, where we will assign a name and the type of problem we are facing: - Minimization: pulp.LpMinimize - Maximization: pulp.LpMaximize

with the syntax: **prob = pulp.LpProblem("Task Assignment", pulp.LpMinimize)**

#### Creating the Model Variables:

Variables are the basis of optimization problems, and depending on the type of problem you are solving, they can take on different categories (typologies), such as continuous, integer, or binary variables.

* To create a variable in PuLP, use the LpVariable class, which requires at least a name as an argument and can include constraints such as its type (binary, continuous, integer) and limits on its values. The basic way to define a variable is:

x = LpVariable('x')

Variables can contain model-specific data or simply be empty for use by the model.

#### Defining Variables

Examples of Variables

1. costs = \[\[10, 2, 20], \[12, 7, 15], \[8, 12, 5]]
2. workers = range(3)
3. tasks = range(3)
4. x = pulp.LpVariable.dicts(“x”, \[(i, j) for i in workers for j in tasks], cat=’Binary’)
5. Continuous Variables

These are variables that can take any value within a range, whether positive, negative, or unbounded. This is the default category when the type is not specified.

_**x= LpVariable('x')**_

#### With Bounds

The value of a continuous variable can be restricted to a given interval (for example, between a minimum and maximum value).

* x = LpVariable('x', lowBound=0, upBound=10)
* \\\[0\<X\_i<10\\]

lowBound and upBound are the attributes that define the limits of variables, meaning they also serve as constraints where

* x = LpVariable('x', lowBound=0)
* \\\[X\_{i,j}\ge0\\]

#### Integer Variables

Integer variables can only take whole numeric values within a specific range.

* y = LpVariable('y', lowBound=0, upBound=5, cat='Integer')

In this case, the variable type is specified with the "cat" attribute, which specifies the typology, in this case "integer".

#### Binary Variables

Binary variables are a special case of integer variables, as they can only take the values 0 or 1. This type of variable is useful when modeling binary decisions (yes/no, true/false) in problems such as project selection or resource allocation, which are very common in transportation methods and advanced programming.

* z = LpVariable('z', cat='Binary')

When modeling this type of variable, the decision it entails must be taken into account. That is, it will be 1 if a given condition is met, or 0 if it is not. This way, we can control the system and its logic.

* Summary of Pulp variable arguments:

1. **lowBound:** Defines the variable's lower bound (the smallest value it can take). If not specified, the default is None (no lower bound).
2. **upBound:** Defines the variable's upper bound (the largest value it can take). If not specified, the default is None (no upper bound).
3. **cat:** This argument defines the variable's category (type):

* _'Continuous':_ Continuous variables (default).
* _'Integer':_ Variables that can only take integer values.
* _'Binary':_ Binary variables (which only take the values 0 or 1).

***

### Define the objective function:

Before proceeding with Python programming, it is recommended that the exercise or system be defined in this way, as this makes development easier. When entering the system's objective function, it must already be defined and known according to the nature of the system being investigated. In this case, we will use the following function:

$$
3x_1+2x_2+x_3
$$

* `problem += 3 * x1 + 2 * x2 + x3,` “Objective Function”

Note the name of the variable that encloses the problem: “problem.”

#### Let's add the system's constraints:

`problem += x1 + x2 + x3 <= 2,`

“Constraint 1” `problem += x1 + x2 >= 1`,

“Restriction 2”

In this case, the restrictions are preceded by the symbols $$\(\le\) and \(\ge\)$$

Note that we do not define the “non-negativity” restriction since the variables, when defined and bounded, include the values on which they can operate.

#### We solve:

Use the solve() method to solve the optimization problem. PuLP uses a built-in solver by default, but you can specify one if you prefer.

* problem.solve()

#### Display the result:

Finally, we must specify to the machine that we want to see the results. These can be displayed as flat values, or we can use other libraries such as pandas, mathplotlib, etc., to display these results. However, for these, we would have to define the variables and store the data as required.

print(“Status:”, pulp.LpStatus\[problem.status])

print(“Value of x1:”, x1.varValue) print(“Value of x2:”, x2.varValue) print(“Value of x3:”, x3.varValue)

print(“Optimal value of the objective function:”, pulp.value(problem.objective))
