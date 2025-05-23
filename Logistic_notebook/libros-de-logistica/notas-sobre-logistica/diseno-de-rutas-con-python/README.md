# Diseño de Rutas con Python

La programación lineal es una técnica matemática utilizada para optimizar un objetivo lineal, sujeto a restricciones lineales. En el diseño de rutas, permite modelar y resolver problemas donde se busca minimizar costos o tiempo total de recorrido mientras se respetan las restricciones de capacidad y tiempo. Esta técnica ayuda a determinar la mejor combinación de variables de decisión como rutas a tomar, cantidad de vehículos y secuencia de entregas, garantizando que los recursos se utilicen de manera eficiente y efectiva.

{% hint style="info" %}
La optimización de rutas representa uno de los desafíos más comunes en la gestión de operaciones logísticas. Los modelos matemáticos proporcionan un marco sistemático para abordar estos problemas, permitiendo la toma de decisiones más informadas y eficientes. A continuación, se describen algunos de los modelos más utilizados.
{% endhint %}

**Modelo de Programación para Solucionar Problemas de Rutas**

Los problemas de rutas son desafíos comunes en la optimización del transporte y la logística. Estos problemas pueden involucrar encontrar la ruta más eficiente para entregar bienes, planificar itinerarios de viaje o minimizar costos de transporte. Un enfoque eficaz para abordar estos problemas es el uso de modelos de programación.

#### Tipos de Problemas de Rutas

1. **Problema del Viajante (TSP)**: Busca determinar la ruta más corta que permite visitar un conjunto de ciudades una sola vez y regresar al punto de partida.
2. **Problema de Ruteo de Vehículos (VRP)**: Se centra en encontrar las rutas óptimas para una flota de vehículos que deben satisfacer una serie de demandas desde un depósito central.
3. **Problemas de Ruta de Entrega y Recolección**: Involucran no solo la entrega de bienes, sino también la recolección de productos o envases para su reciclaje.

#### Modelos de Programación Utilizados

1. **Programación Entera**: Utilizada para problemas donde las decisiones son binarias, como visitar o no un nodo.
2. **Programación Lineal**: Permite modelar y resolver problemas con restricciones lineales y variables continuas.
3. **Heurísticas y Metaheurísticas**: Algoritmos como “Ant Colony” o “Genetic Algorithms”, que buscan soluciones aproximadas pero rápidamente.

#### Pasos para Desarrollar un Modelo de Programación

1. **Definición del Problema**: Clarificar los objetivos, restricciones y parámetros del problema de rutas específicos.
2. **Formulación del Modelo**: Traducir el problema en términos matemáticos, definiendo variables, ecuaciones y restricciones.
3. **Selección del Algoritmo**: Elegir el algoritmo de solución más adecuado, considerando el tamaño y la complejidad del problema.
4. **Implementación Computacional**: Usar software de optimización para implementar y probar el modelo.
5. **Análisis de Resultados**: Evaluar las soluciones generadas, ajustando el modelo y parámetros según sea necesario.

#### Aplicaciones Prácticas

Los modelos de programación para problemas de rutas tienen una amplia gama de aplicaciones prácticas, incluyendo:

* Optimización de rutas en servicios de entrega de compra en línea.
* Planificación de rutas eficientes para servicios de transporte público.
* Gestión de la logística de distribución en cadenas de suministro.

### Diseño de rutas con python

La planificación de rutas se enfoca en diseñar recorridos óptimos para la entrega de productos o el logro de los objetivos del sistema considerando.

1. tiempo
2. costo
3. restricciones de capacidad

**Objetivo de diseñar una ruta**

el objetivo puede ser:

1. Minimizar costos
2. Optimizar tiempos de entregas
3. Mejorar la utilizacion de recursos

***

### DISEÑO DE RUTAS UTILIZANDO PYTHON.[#](broken-reference)

Existen numerosas librerías y algoritmos disponibles que simplifican el proceso de diseño de rutas en Python. Estas herramientas se utilizan para optimizar y planificar caminos eficientes en diversas aplicaciones, como son la gestión de flotas de vehículos, la entrega de mercancías, la planificación de viajes y muchas otras más.

Entre las librerías más destacadas se encuentra NetworkX, que proporciona estructuras de datos y algoritmos para el análisis de grafos y redes. También está GeoPandas, que extiende las capacidades de Pandas al permitir el manejo y el análisis de datos geoespaciales. Otra opción popular es OSRM (Open Source Routing Machine), que ofrece un servidor y una biblioteca de cliente para generar rutas utilizando datos de OpenStreetMap.

Por otro lado, se pueden emplear algoritmos de optimización de rutas como el algoritmo de Dijkstra, el algoritmo A\* (A-star) y los algoritmos de optimización metaheurística, que se usan para encontrar rutas óptimas en función de diversas restricciones y costos. Estos algoritmos son fundamentales para aplicaciones donde se requiere una alta eficiencia en la planificación de rutas.

{% hint style="info" %}
El ecosistema de Python ofrece una variedad de herramientas y técnicas que permiten abordar el problema del diseño de rutas de manera eficiente y efectiva, adaptándose a las necesidades específicas de cada aplicación. Al aprovechar estas librerías y algoritmos, los desarrolladores pueden crear soluciones avanzadas en el ámbito de la planificación y optimización de rutas.
{% endhint %}

{% code overflow="wrap" %}
```markdown
Pulp: Una librería para resolver problemas de optimización, incluyendo el TSP y VRP.
```
{% endcode %}

hagamnos el ejemplo donde tenemos un problema de asignación de tareas a trabajadores, donde cada trabajador debe realizar una sola tarea y cada tarea debe ser realizada por un solo trabajador. La función objetivo es minimizar el costo total de la asignación

```python
!pip install Pulp
```

```python
import pulp

# Crear el problema
prob = pulp.LpProblem("Asignacion de Tareas", pulp.LpMinimize)

# Definir las variables
costos = [[10, 2, 20], [12, 7, 15], [8, 12, 5]]
trabajadores = range(3)
tareas = range(3)
x = pulp.LpVariable.dicts("x", [(i, j) for i in trabajadores for j in tareas], cat='Binary')

# Función objetivo
prob += pulp.lpSum(costos[i][j] * x[(i, j)] for i in trabajadores for j in tareas)

# Restricciones
for i in trabajadores:
    prob += pulp.lpSum(x[(i, j)] for j in tareas) == 1

for j in tareas:
    prob += pulp.lpSum(x[(i, j)] for i in trabajadores) == 1

# Resolver el problema
prob.solve()

# Imprimir los resultados
print("Status:", pulp.LpStatus[prob.status])
for v in prob.variables():
    print(v.name, "=", v.varValue)

print("Costo total =", pulp.value(prob.objective))
```

#### Analisis de redes por medio de Networkx[#](broken-reference)

**NetworkX** es una biblioteca poderosa y versátil de Python empleada para la creación, manipulación y análisis de redes complejas. Diseñada para facilitar el proceso de modelar estructuras de grafos, NetworkX encuentra aplicaciones en numerosos campos como la ciencia de redes, biología computacional, ingeniería, ciencias sociales, entre otros.

Esta biblioteca ofrece funcionalidades que permiten un análisis detallado y preciso de las redes, incluyendo, pero no limitándose a, encontrar caminos mínimos entre nodos, lo cual es esencial en la optimización de rutas y redes de transporte. Además, NetworkX es capaz de detectar comunidades dentro de una red, ayudando a identificar agrupaciones o módulos que pueden representar entidades con características o intereses comunes en un contexto social o biológico.

Otra característica destacada es su capacidad para calcular diversas métricas de centralidad, como la centralidad de grado, intermediación y cercanía, que son cruciales para determinar los nodos más influentes o críticos dentro de la red.

El diseño intuitivo y la amplia documentación hacen de NetworkX una herramienta ideal tanto para investigadores como para profesionales que buscan llevar a cabo análisis complejos de redes de manera eficiente. Además, su compatibilidad con otras bibliotecas de Python, como Pandas y Matplotlib, permite una integración fluida en flujos de trabajo más amplios de ciencia de datos.&#x20;

**Características principales:**[**#**](broken-reference)

1. Creación y manipulación de grafos: Soporta varios tipos de grafos (dirigidos, no dirigidos, multigrafos) y permite agregar nodos y aristas con atributos.
2. Análisis de redes: Proporciona una amplia gama de algoritmos de teoría de grafos para realizar análisis estructural, como el cálculo de centralidades (grado, intermediación, cercanía), detección de componentes conectados, caminos mínimos, detección de comunidades, etc.
3. Tipos de grafos: Soporta grafos dirigidos (donde las conexiones tienen dirección), no dirigidos y multigrafos (donde puede haber múltiples aristas entre dos nodos).

```python
!pip install networkx==2.8.8
```

```python
import networkx as nx
import matplotlib.pyplot as plt

# Crear un grafico
G = nx.Graph()

# Agregar nodos y aristas
G.add_edge(1, 2)
G.add_edge(2, 3)
G.add_edge(3, 4)

# Dibujar el grafo
nx.draw(G, with_labels=True)
plt.show()
```

### Ejemplo 1:

MG Auto tiene tres plantas: en Los Ángeles, Detroit y New Orleans; y dos centros principales de distribución en Denver y en Miami. Las capacidades de las tres plantas durante el próximo trimestre serán 1000, 1500 y 1200 autos. Las demandas trimestrales en los dos centros de distribución son 2300 y 1400 autos. El kilometraje entre las fábricas y los centros de distribución

* La empresa transportista cobra 8 centavos por KM y por auto. El costo de transporte por auto, en las distintas rutas y redondeado hasta el $ más próximo

TABLA 1

|             | Denver | Mimami |
| ----------- | ------ | ------ |
| Los Angeles | 1000   | 2690   |
| Detroit     | 1250   | 1350   |
| New Orleans | 1275   | 850    |

TABLA 2

|                | Denver(1) | Mimami(2) |
| -------------- | --------- | --------- |
| Los Angeles(1) | 80        | 215       |
| Detroit(2)     | 100       | 108       |
| New Orleans(3) | 102       | 68        |

**Resolviendo:**

**Variables de decisión:**

* \\(x\_{ij}\\): Cantidad de autos a transportar desde la planta \\(i\\) hasta el centro de distribución \\(j\\).

**Función objetivo:**

* Minimizar el costo total de transporte, dado por:

\\\[\text{Min } Z = 0.08 \sum\limits\_{i=1}^{3}\sum\limits\_{j=1}^{2}x\_{ij}d\_{ij}\\]

* Donde \\(d\_{ij}\\) es la distancia en kilómetros entre la planta \\(i\\) y el centro de distribución \\(j\\), según la tabla 1.

**Restricciones:**

* Capacidad de la planta: $\\(\sum\limits\_{j=1}^{2}x\_{ij} \leq c\_i ∀\ i = 1, 2, 3\\)$
* Donde \\(c\_i\\) es la capacidad de la planta \\(i\\).
* Demanda del centro de distribución: $\\(\sum\limits\_{i=1}^{3}x\_{ij} \geq d\_j\ ∀\ j = 1, 2\\)$
* Donde \\(d\_j\\) es la demanda del centro de distribución \\(j\\), según el enunciado.
* Restricciones de no negatividad: $\\(x\_{ij} \geq 0\ ∀\ i = 1, 2, 3\ y\ j = 1, 2\\)$
* _Además, las variables de decisión deben ser enteras, ya que no se pueden transportar fracciones de autos._

**Resolviendo con Python y la libreria PuLp:**[**#**](broken-reference)

```python
import pulp

# Crear un problema de minimización
problem = pulp.LpProblem("Transporte", pulp.LpMinimize)

# Crear las variables de decisión
x11 = pulp.LpVariable("Los Angeles a Denver", lowBound=0, cat='Integer')
x12 = pulp.LpVariable("Los Angeles a Miami", lowBound=0, cat='Integer')
x21 = pulp.LpVariable("Detroit a Denver", lowBound=0, cat='Integer')
x22 = pulp.LpVariable("Detroit a Miami", lowBound=0, cat='Integer')
x31 = pulp.LpVariable("New Orleans a Denver", lowBound=0, cat='Integer')
x32 = pulp.LpVariable("New Orleans a Miami", lowBound=0, cat='Integer')

# Definir la función objetivo
problem += 0.08 * (1000*x11 + 2690*x12 + 1250*x21 + 1350*x22 + 1275*x31 + 850*x32)

# Definir las restricciones de oferta y demanda
problem += x11 + x12 <= 2300, "Oferta Los Angeles"
problem += x21 + x22 <= 1500, "Oferta Detroit"
problem += x31 + x32 <= 2000, "Oferta New Orleans"
problem += x11 + x21 + x31 >= 2300, "Demanda Denver"
problem += x12 + x22 + x32 >= 1400, "Demanda Miami"

# Resolver el problema
problem.solve()

# Imprimir el resultado
print("Estado:", pulp.LpStatus[problem.status])
print("Costo total de transporte: $", round(pulp.value(problem.objective), 2))

for variable in problem.variables():
    print(variable.name, "=", variable.varValue)
```

#### Ejemplo 2:

En este modelo, tenemos tres orígenes (\\(O\_1\\), \\(O\_2\\) y \\(O\_3\\)) y cuatro destinos (\\(D\_1\\), \\(D\_2\\), \\(D\_3\\) y \\(D\_4\\)), y la tabla muestra los costos de transporte desde cada origen a cada destino. El objetivo es determinar la asignación óptima de los productos a los destinos, minimizando el costo total de transporte.

| ORIGEN     | \\(D\_1\\) | \\(D\_2\\) | \\(D\_3\\) | \\(D\_4\\) |
| ---------- | ---------- | ---------- | ---------- | ---------- |
| \\(O\_1\\) | 4          | 5          | 2          | 7          |
| \\(O\_2\\) | 3          | 6          | 8          | 2          |
| \\(O\_3\\) | 9          | 4          | 1          | 3          |

**Resolviendo el modelo:**

La función objetivo de este modelo se expresa como:

\begin{equation\*} \text{minimizar } Z = \sum\_{i=1}^{3}\sum\_{j=1}^{4}c\_{ij}x\_{ij} \end{equation\*}

Donde:

\\(Z\\): representa el costo total de transporte.

\\(c\_{ij}\\): es el costo de transportar una unidad del origen \\(i\\) al destino \\(j\\).

\\(x\_{ij}\\): es la cantidad de unidades transportadas del origen \\(i\\) al destino \\(j\\).

Las restricciones de capacidad se expresan como:

```markdown
\begin{align*} \sum_{j=1}^{4} x_{1j} &\leq 60
\sum_{j=1}^{4} x_{2j} &\leq 70
\sum_{j=1}^{4} x_{3j} &\leq 80 \end{align*}
```

**Donde:**

La restricción \\(\sum\_{j=1}^{4} x\_{ij} \leq C\_i\\) indica que la cantidad total de productos que se envían desde el origen \\(i\\) no puede superar su capacidad máxima \\(C\_i\\). Las restricciones de demanda se expresan como:

\begin{align\*} \sum\_{i=1}^{3} x\_{i1} &\geq 50\
\sum\_{i=1}^{3} x\_{i2} &\geq 70\
\sum\_{i=1}^{3} x\_{i3} &\geq 80\
\sum\_{i=1}^{3} x\_{i4} &\geq 30 \end{align\*}

**Donde:**

* La restricción \\(\sum\_{i=1}^{3} x\_{ij} \geq D\_j\\) indica que la cantidad total de productos que se envían al destino \\(j\\) debe ser al menos igual a su demanda \\(D\_j\\)

```python
import pulp
```

```python
# Define el problema
problem = pulp.LpProblem("Transportation Problem", pulp.LpMinimize)

# Define las variables de decision
origins = ['O1', 'O2', 'O3']
destinations = ['D1', 'D2', 'D3', 'D4']
x = pulp.LpVariable.dicts('shipment', ((o, d) for o in origins for d in destinations), lowBound=0, cat='Integer')

# Define los objetos de las funciones
costs = {
    ('O1', 'D1'): 4,
    ('O1', 'D2'): 5,
    ('O1', 'D3'): 2,
    ('O1', 'D4'): 7,
    ('O2', 'D1'): 3,
    ('O2', 'D2'): 6,
    ('O2', 'D3'): 8,
    ('O2', 'D4'): 2,
    ('O3', 'D1'): 9,
    ('O3', 'D2'): 4,
    ('O3', 'D3'): 1,
    ('O3', 'D4'): 3
}
problem += pulp.lpSum([costs[o, d] * x[o, d] for o in origins for d in destinations])

# Define las restricciones
for o in origins:
    problem += pulp.lpSum([x[o, d] for d in destinations]) == 1
for d in destinations:
    problem += pulp.lpSum([x[o, d] for o in origins]) == 1

# resuelve el problema
problem.solve()

# imprime la solucion Optima
print("Optimal solution:")
for o in origins:
    for d in destinations:
        if x[o, d].value() > 0:
            print(f"Ship {x[o, d].value()} from {o} to {d}")
print(f"Total cost: {pulp.value(problem.objective)}");
```
