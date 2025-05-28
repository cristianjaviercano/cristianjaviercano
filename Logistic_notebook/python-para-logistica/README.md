# Python para logistica

### Herramientas de Python para la Gestión de la Cadena de Abastecimiento

Python ofrece una variedad de bibliotecas y herramientas que pueden ser utilizadas para mejorar la gestión de la cadena de abastecimiento:

* **Pandas**: Para el análisis de datos y el manejo de grandes volúmenes de información.
* **NumPy**: Permite manejar operaciones matemáticas y estadísticas eficientemente.
* **SciPy**: Incluye algoritmos y herramientas para optimización y análisis numérico.
* **Matplotlib y Seaborn**: Para la visualización de datos, ayudando en la comprensión de patrones y tendencias.
* **PuLP**: Una biblioteca para modelar problemas de optimización lineal, útil para la planificación de recursos.
* **SupplyChainPy**: Diseñada específicamente para analíticas dentro de la cadena de suministro.
* **NetworkX**: Para el análisis y visualización de redes, útil en la optimización de rutas y logística.

Estas herramientas permiten desde la optimización de inventarios y recursos, hasta la simulación de flujos logísticos y la previsión de demanda, facilitando así la toma de decisiones informadas.

* **SimPy**: Es una biblioteca de simulación basada en procesos, ideal para modelar y simular sistemas logísticos y de cadena de suministro. Permite representar operaciones complejas como líneas de producción, procesos de pedido y distribución, ayudando a identificar cuellos de botella y oportunidades de mejora en tiempo real.

#### Herramientas GIS en Python

Python también ofrece diversas bibliotecas para el análisis Geoespacial (GIS), útiles para la gestión de la cadena de abastecimiento en escenarios que requieren análisis geográficos y de rutas:

* **GDAL/OGR**: Un conjunto de herramientas para leer y escribir formatos de datos geoespaciales.
* **Shapely**: Utilizado para el análisis y manipulación de datos geométricos.
* **GeoPandas**: Extiende las capacidades de Pandas para incluir operaciones geoespaciales.
* **Fiona**: Para leer y escribir archivos de datos geoespaciales en forma fácil.
* **Pyproj**: Utilizada para la transformación de sistemas de coordenadas.

#### Folium

Folium es una biblioteca en Python que facilita la visualización de datos geoespaciales en mapas interactivos. Se integra bien con otras bibliotecas de análisis de datos y es especialmente útil para la creación de mapas choropleth, la representación de ubicaciones de puntos y la visualización de rutas. La biblioteca utiliza Leaflet.js para el manejo de mapas en el navegador, lo que permite una experiencia rica e interactiva para el usuario.

#### Dash

Dash es un potente framework de Python desarrollado por la compañía detrás de Plotly, que permite a los ingenieros crear aplicaciones web interactivas con facilidad. Es especialmente popular para la creación de **dashboards** y **aplicaciones de análisis de datos** en tiempo real, combinando la simplicidad de Python con la capacidad de generar interfaces de usuario personalizables y dinámicas.

_Dash_ se construye sobre una robusta arquitectura que incluye Flask, React.js y Plotly.js, permitiendo la integración de gráficos interactivos, controles de usuario como sliders o botones, y elementos de interfaz de usuario complejos. Esto lo convierte en una opción ideal para la visualización de datos intensiva y la presentación de análisis complejos en navegadores web.

Las aplicaciones desarrolladas con Dash son gratuitas y abiertas, lo que significa que pueden ser compartidas y desplegadas en múltiples plataformas con facilidad. La comunidad de Dash también ofrece numerosos componentes y extensiones que permiten ampliar sus capacidades básicas, como la incorporación de gráficos en 3D, mapas interactivos y mucho más.

#### Motores de Optimización para Programación Lineal en Python

La programación lineal es una técnica para la optimización de un objetivo lineal sujeto a restricciones lineales. En Python, existen varios motores o bibliotecas que facilitan la resolución de problemas de programación lineal:

* **PuLP**: Es una biblioteca de programación lineal fácil de usar y que proporciona una interfaz para definir problemas de optimización y resolverlos utilizando diversos solucionadores.
* **SciPy**: Ofrece el módulo `optimize`, que incluye funciones para resolver problemas de programación lineal.
* **CVXPY**: Es una biblioteca que permite especificar problemas de optimización de manera declarativa y los resuelve usando solucionadores numéricos.
* **Gurobi y CPLEX**: Son solucionadores comerciales altamente eficientes para programación lineal e integra fácilmente con Python a través de sus respectivas APIs.

Estos motores de optimización permiten a los desarrolladores y científicos de datos implementar soluciones rápidas y eficientes para problemas de optimización en sus proyectos.

#### Ejemplo de Problema de Programación Lineal

Supongamos que queremos maximizar el beneficio de vender dos productos, A y B. El producto A genera un beneficio de $40 por unidad y el producto B, $30 por unidad. Las restricciones son:

1. Se pueden producir un máximo de 30 unidades de A por día.
2. Se pueden producir un máximo de 20 unidades de B por día.
3. La producción combinada de A y B no puede exceder 40 unidades por día.

El problema se formula matemáticamente como:

**Maximizar:**\
( Z = 40A + 30B )

**Sujeto a restricciones:**\
( A \leq 30 )\
( B \leq 20 )\
( A + B \leq 40 )\
( A, B \geq 0 )

#### Resolución con Diferentes Motores

**Usando PuLP**

```python
from pulp import LpMaximize, LpProblem, LpVariable

prob = LpProblem("Maximizar_Beneficio", LpMaximize)
A = LpVariable("A", 0, 30)
B = LpVariable("B", 0, 20)

prob += 40 * A + 30 * B
prob += A + B <= 40

prob.solve()
```

**Usando SciPy**

```python
from scipy.optimize import linprog

c = [-40, -30]
A_ub = [[1, 0], [0, 1], [1, 1]]
b_ub = [30, 20, 40]

res = linprog(c, A_ub=A_ub, b_ub=b_ub, bounds=(0, None))
```

**Usando CVXPY**

```python
import cvxpy as cp

A = cp.Variable()
B = cp.Variable()
objective = cp.Maximize(40 * A + 30 * B)
constraints = [A <= 30, B <= 20, A + B <= 40, A >= 0, B >= 0]

prob = cp.Problem(objective, constraints)
prob.solve()
```

**Usando Gurobi**

```python
from gurobipy import Model, GRB

model = Model()
A = model.addVar(name="A", lb=0, ub=30)
B = model.addVar(name="B", lb=0, ub=20)

model.setObjective(40 * A + 30 * B, GRB.MAXIMIZE)
model.addConstr(A + B <= 40)

model.optimize()
```

**Usando CPLEX**

```python
from cplex import Cplex

cplex_problem = Cplex()
cplex_problem.set_problem_type(Cplex.problem_type.LP)
cplex_problem.variables.add(names=["A", "B"], obj=[40, 30], ub=[30, 20], lb=[0, 0])

cplex_problem.linear_constraints.add(
    lin_expr=[[[0, 1], [1, 1]]],
    senses=["L"],
    rhs=[40]
)

cplex_problem.solve()
```

#### Principales Diferencias

* **PuLP**: Interfaz fácil para expresar y resolver problemas, adecuada para principiantes.
* **SciPy**: Parte de una biblioteca científica más amplia, adecuada para optimizaciones más básicas.
* **CVXPY**: Ofrece una API más declarativa, útil para problemas complejos.
* **Gurobi**: Solucionador comercial de alto rendimiento, adecuado para grandes problemas.
* **CPLEX**: Similar a Gurobi, es eficiente y escalable para aplicaciones industriales.

