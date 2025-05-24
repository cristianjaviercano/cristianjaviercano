---
icon: arrow-progress
---

# Logistic Notebook

***



### Unidad Cuatro: Modelos de Localizacion[#](broken-reference)

***



### Unidad Cinco: supply chain models and methods.[#](broken-reference)

### concepto fubdamental[#](broken-reference)

Imagina la cadena de suministro como un río que desde la fuente (proveedores de materias primas) hasta el mar (cliente final), el producto fluye a través de diversos canales. Un modelo de cadena de suministro es una representación simplificada de este flujo, que nos permite analizar y optimizar su funcionamiento.

donde podemos gestionar aspecto basicos y complejos del sistema tales como:

1. Toma de decisiones: Los modelos nos ayudan a evaluar diferentes escenarios y tomar decisiones estratégicas, como dónde ubicar almacenes, cómo gestionar el inventario o qué rutas de transporte utilizar.
2. Optimización de costos: Al identificar ineficiencias en la cadena de suministro, podemos reducir costos y aumentar la rentabilidad.
3. Mejora de la eficiencia: Los modelos nos permiten simular diferentes procesos y encontrar la forma más eficiente de operar.
4. Gestión de riesgos: Podemos evaluar el impacto de posibles perturbaciones, como desastres naturales o cambios en la demanda, y desarrollar planes de contingencia.

#### Tipos de modelos de cadena de suministro:[#](broken-reference)

Existen diversos tipos de modelos, cada uno con sus propias características y aplicaciones:

1. Modelos continuos: Asumen que la demanda y la producción son constantes en el tiempo.
2. Modelos ágiles: Se adaptan rápidamente a los cambios en la demanda y el entorno.
3. Modelos rápidos: Priorizan la velocidad de entrega y la respuesta a las necesidades del cliente.
4. Modelos configurados a medida: Se diseñan específicamente para una empresa o industria en particular.

#### Herraientas para contruccion de cadenas logisticas:[#](broken-reference)

1. Software de simulación: - AnyLogic: Ofrece una gran flexibilidad para modelar sistemas complejos, incluyendo cadenas de suministro. Permite crear modelos 3D y realizar simulaciones detalladas. - Simio: Es otra opción popular, con una interfaz intuitiva y una amplia biblioteca de componentes. - Arena: Destaca por su capacidad para modelar sistemas discretos y continuos, lo que lo hace adecuado para una variedad de aplicaciones. - Flexym: sofhware de simulacion destacado por su interfaz grafica y sencillez de implementacion , solo para windows.
2. Hojas de cálculo: - Excel: Aunque más básico, puede ser útil para construir modelos sencillos y realizar análisis de sensibilidad.
3. Lenguajes de programación: - Python: Con bibliotecas como Pyomo y SimPy, permite crear modelos personalizados y complejos.
4. Software de optimización: - CPLEX: Se utiliza para resolver problemas de optimización matemática, como la minimización de costos o la maximización de beneficios.

**Pasos para construir un modelo de cadena de suministro:**[**#**](broken-reference)

1. Definición del problema:

* Identificar el objetivo del modelo (reducir costos, mejorar el servicio al cliente, etc.).
* Definir las variables clave (demanda, inventario, tiempo de entrega, etc.).
* Establecer los límites y restricciones del sistema.

2. Recopilación de datos:

* Obtener datos históricos sobre la demanda, los costos, los tiempos de ciclo, etc.
* Verificar la calidad y la consistencia de los datos.

3. Diseño del modelo:

* Seleccionar la herramienta de modelado adecuada.
* Definir la estructura del modelo (componentes, relaciones, flujos).
* Implementar las ecuaciones y lógica del modelo.

4. Validación del modelo:

* Comparar los resultados del modelo con los datos históricos.
* Ajustar el modelo si es necesario.

5. Análisis y simulación:

* Realizar diferentes escenarios para evaluar el impacto de diferentes decisiones.
* Identificar los cuellos de botella y las áreas de mejora.

6. Implementación:

* Comunicar los resultados del modelo a los tomadores de decisiones.
* Desarrollar un plan de implementación para los cambios recomendados.

### Construccion de una cadena usando python:[#](broken-reference)

Vamos a usar python como plataforma de medicion de una cadena de abastecimiento por medio del uso de la libreria _simpy_

### Unidad Seis: Diseño y medicion de la cadena logistica[#](broken-reference)

`Supply Chain Optimization Design and Management_ Advances and Intelligent Methods Premier Reference Source`

***

Se ha utilizado una amplia gama de metodologías para resolver este problema de optimización. Sin embargo, los métodos matemáticos tradicionales han demostrado ser insuficientes para abordar los requisitos derivados del desarrollo de la competencia en el mercado (Silva et al. 2003). Las técnicas inteligentes inspiradas en la naturaleza se consideran bastante eficientes en el manejo de problemas NP-difíciles (es decir, problemas de optimización en los que no se puede encontrar el óptimo en tiempo polinomial). La principal característica de estos métodos es la imitación de la forma en que funcionan y evolucionan los sistemas naturales para hacer frente a situaciones del mundo real (Vassiliadis y Dounias 2009). Por ejemplo, las colonias de hormigas naturales cooperan para encontrar una fuente de alimento de alta calidad, una bandada de pájaros implementa un esquema de comunicación indirecta con el objetivo de encontrar la dirección óptima, etc. Algunos ejemplos de algoritmos inspirados en la naturaleza son los siguientes:

1. Ant Colony Optimization (ACO)
2. Particle Swarm Optimization (PSO)
3. Genetic Algorithms
4. Genetic Programming
5. Memetic Algorithms
6. Artificial Immune Systems
7. DNA Computing

### Deficiones[#](broken-reference)

Para arrojar algo de luz sobre los conceptos básicos de la gestión de la cadena de suministro, es conveniente presentar las funciones principales de una cadena de suministro simplificada (Silva et al. 2009). El enfoque de modelado consta de tres partes, la logística, el suministro y el sistema de distribución, a saber.

1. **Sistema logístico**: recibe pedidos de los clientes y realiza pedidos a los proveedores en lo que a materia prima se refiere. Los materiales comprados se utilizarán en el proceso de fabricación.
2. **Sistema de abastecimiento:** consiste en una red de diferentes proveedores o fabricantes, cada uno de los cuales se ocupa de producir el componente de producto solicitado para el sistema logístico. En este caso, la minimización del tiempo total de tardanza, como se define arriba, puede considerarse como la función objetivo. El problema de la oferta puede pensarse como un problema de optimización de la programación.
3. **Sistema de distribución:** entrega los productos completos a los clientes correspondientes. Los clientes pueden ser descritos por su ubicación geográfica. Un modelo simple y realista del problema de la distribución es el problema de las rutas de los vehículos (o, a veces, el problema del viajante de comercio). Este es un problema de minimización que considera el costo de transporte de la flota de vehículos disponibles. Para este tipo de problema, una restricción común es que cada cliente es visitado por un vehículo y todos los clientes deben estar satisfechos.

### aproximacion de la medicion de la cadena de suministro con la Planificación de producción agregada[#](broken-reference)

* La literatura sobre planificación y control de la producción está llena de modelos y algoritmos para encontrar planes eficientes para la mayoría de los tipos de industrias. En este capítulo, presentamos algunos de los enfoques más exitosos del problema general.

Una técnica particularmente efectiva para obtener planes de producción robustos y eficientes se basa en el principio de descomposición, también conocido como “divide y vencerás”.

Para encontrar el plan óptimo en un horizonte de tiempo, el tiempo mismo se descompone en dos o más niveles de granularidad, formando una jerarquía:

* en el nivel agregado, un período de tiempo puede comprender un mes o un trimestre, y el problema de planificación de la producción agregada es para decidir qué producir para una serie de próximos períodos, dado un pronóstico agregado, así como la capacidad esperada de las líneas de producción durante estos períodos.

Estos planes de producción son particularmente útiles para las decisiones de personal, incluidas las decisiones sobre posibles horas extra que la empresa debería usar en un período agregado determinado, así como las decisiones sobre nuevas contrataciones/despidos o horarios de trabajo flexibles. También son útiles para determinar si se necesita una expansión o, en raras ocasiones, una contracción de la capacidad disponible. Luego, una vez que se determina un plan de producción agregado, el problema de planeación de producción de nivel más fino se convierte en el problema de calcular el plan óptimo para cada plan de producción de nivel más fino.

Comenzamos nuestra discusión sobre la planificación de la producción agregada con el ejemplo más simple posible.

1. Considere un pronóstico de demanda mensual \\(d\_i i=1 . . . N\\) para N períodos, para una compañía imaginaria que produce un solo producto, y considere el problema de construir inventarios de productos terminados durante cada período para que se pueda satisfacer la demanda mensual, manteniendo niveles mínimos de inventarios, evitando así la acumulación de costos:

* de mantenimiento
* de inventario
* de costos de oportunidad,
* riesgo de obsolescencia del inventario
* riesgo de daños en el inventario debido a desastres naturales.
* otro tipo

Si no se toman en cuenta las limitaciones de capacidad, entonces la política óptima es producir todo a tiempo, en un tiempo just in time (JIT), ya que hay suficiente capacidad para satisfacer cualquier nivel de demanda en cualquier período. Sin embargo, cuando la capacidad no es suficiente para satisfacer la demanda durante las temporadas altas, como suele ser el caso, los inventarios deben construirse con anticipación, obviamente lo más tarde posible, para evitar la acumulación de costos de inventario. El siguiente programa lineal (LP) determina la solución óptima para nuestro primer problema de planificación de la producción.

\\\[\begin{split} \text{min} \sum\_{i=1}^{N}h\_i \\\ \ restricciones: h\_i=h\_{i-1}+x\_i-d\_i,\ i=1,...,N\\\ 0 \leq x\_i\leq c,\ i=1,...,N\\\ 0 \leq h\_i,\ i=1,...,N\\\ h\_0 = I\_0 \end{split}\\]

Las variables de decisión x representan la producción de cada período, mientras que las variables h representan el inventario al final de cada período. Al principio, asumimos una acumulación de inventario existente de \\(I\_o\\) unidades.

### Modelos especiales[#](broken-reference)

#### Modelo Interactivo EOQ[#](broken-reference)

```
!pip install ipywidgets
!pip install matplotlib
```

```
import numpy as np
import matplotlib.pyplot as plt
import ipywidgets as widgets
from IPython.display import display

# Función para calcular la EOQ
def eoq(demand, order_cost, holding_cost):
    return np.sqrt((2 * demand * order_cost) / holding_cost)

# Función para calcular los costos totales
def total_cost(order_quantity, demand, order_cost, holding_cost):
    return (order_cost * demand / order_quantity) + (holding_cost * order_quantity / 2)

# Función para actualizar el gráfico basado en los widgets
def update_plot(demand, order_cost, holding_cost):
    order_quantities = np.linspace(1, 2 * demand, 500)
    costs = total_cost(order_quantities, demand, order_cost, holding_cost)

    q_optimal = eoq(demand, order_cost, holding_cost)

    plt.figure(figsize=(12, 6))

    # Graficar costos totales
    plt.plot(order_quantities, costs, label='Costo Total', color='blue')
    plt.axvline(x=q_optimal, color='r', linestyle='--', label=f'EOQ: {q_optimal:.2f}')

    # Graficar costos de pedido
    cost_ordering = order_cost * demand / order_quantities
    plt.plot(order_quantities, cost_ordering, label='Costo de Pedido', color='green', linestyle='--')

    # Graficar costos de almacenamiento
    cost_holding = holding_cost * order_quantities / 2
    plt.plot(order_quantities, cost_holding, label='Costo de Almacenamiento', color='orange', linestyle='--')

    plt.xlabel('Cantidad de Pedido')
    plt.ylabel('Costo')
    plt.title('Modelo EOQ Interactivo')
    plt.legend()
    plt.grid(True)
    plt.show()

# Widgets para los parámetros
demand_widget = widgets.FloatSlider(value=20, min=10, max=1000, step=10, description='Demanda Anual:')
order_cost_widget = widgets.FloatSlider(value=10, min=10, max=200, step=10, description='Costo de Pedido:')
holding_cost_widget = widgets.FloatSlider(value=2, min=0.5, max=200, step=0.5, description='Costo de Almacenamiento:')

# Enlazar widgets con la función de actualización
ui = widgets.VBox([demand_widget, order_cost_widget, holding_cost_widget])
out = widgets.interactive_output(update_plot, {
    'demand': demand_widget,
    'order_cost': order_cost_widget,
    'holding_cost': holding_cost_widget
})

display(ui, out)
```

los modelos interactivos nos ayudan a entender la logica de las cosas, intenta modificando cada uno de los datos, tambien podemos usar elementos propios de python para hacer comparaciones por ejemplo:

* el siguiente codigo toma los valores de Demanda, h y S, y realiza la adicion de una unidad a la variable s 10 veces, con el fin de verificar el comportamiento de Q en este cambio. de esta manera podemos verificar la afectacion de \\(S\\) a \\(Q\\)

```
import math

def eoq(demand, order_cost, holding_cost, s_value):
    eoq = math.sqrt((2 * demand * order_cost) / (holding_cost * s_value))
    return eoq

demand = float(input("Ingrese la demanda anual: "))
order_cost = float(input("Ingrese el costo de pedido: "))
holding_cost = float(input("Ingrese el costo de almacenamiento: "))

for i in range(10):
    s_value = (order_cost + i) + 1  # El valor de S cambiará en cada iteración
    eoq_value = eoq(demand, order_cost, holding_cost, s_value)
    print("Para S = {}, EOQ: {}".format(s_value, eoq_value))
```

```
Ingrese la demanda anual: 100
Ingrese el costo de pedido: 02
Ingrese el costo de almacenamiento: 5
Para S = 3.0, EOQ: 5.163977794943222
Para S = 4.0, EOQ: 4.47213595499958
Para S = 5.0, EOQ: 4.0
Para S = 6.0, EOQ: 3.6514837167011076
Para S = 7.0, EOQ: 3.3806170189140663
Para S = 8.0, EOQ: 3.1622776601683795
Para S = 9.0, EOQ: 2.9814239699997196
Para S = 10.0, EOQ: 2.8284271247461903
Para S = 11.0, EOQ: 2.696799449852968
Para S = 12.0, EOQ: 2.581988897471611
```

#### modelo interactivo POQ - python[#](broken-reference)

```
import ipywidgets as widgets
from IPython.display import display
import matplotlib.pyplot as plt
import numpy as np

def calcular_epq(demanda, costo_preparacion, costo_almacenamiento, tasa_produccion):
  return np.sqrt((2 * demanda * costo_preparacion) / costo_almacenamiento * (tasa_produccion / (tasa_produccion - demanda)))

# detalles de los wiggets
demanda_widget = widgets.IntSlider(value=1000, min=100, max=5000, step=100, description='Demanda:')
costo_preparacion_widget = widgets.IntSlider(value=100, min=10, max=500, step=10, description='Costo Preparación:')
costo_almacenamiento_widget = widgets.FloatSlider(value=0.5, min=0.1, max=2.0, step=0.1, description='Costo Almacenamiento:')
tasa_produccion_widget = widgets.IntSlider(value=6000, min=1000, max=10000, step=100, description='Tasa Producción:')

def actualizar_grafico(demanda, costo_preparacion, costo_almacenamiento, tasa_produccion):
  epq_valor = calcular_epq(demanda, costo_preparacion, costo_almacenamiento, tasa_produccion)
  print(f'EPQ: {epq_valor:.2f}')

  # Datos
  tiempo_ciclo = epq_valor / demanda
  tiempo_produccion = epq_valor / tasa_produccion
  tiempo = np.linspace(0, tiempo_ciclo, 100)
  inventario = np.where(tiempo <= tiempo_produccion,
                       tasa_produccion * tiempo - demanda * tiempo,
                       epq_valor - demanda * tiempo)

  # Grafica
  plt.figure(figsize=(8, 6))
  plt.plot(tiempo, inventario)
  plt.xlabel('Tiempo')
  plt.ylabel('Inventario')
  plt.title('Modelo EPQ')
  plt.grid(True)
  plt.show()

widgets.interact(actualizar_grafico,
                 demanda=demanda_widget,
                 costo_preparacion=costo_preparacion_widget,
                 costo_almacenamiento=costo_almacenamiento_widget,
                 tasa_produccion=tasa_produccion_widget);
```

#### Modelo de asignacion de rutas aleatorias[#](broken-reference)

```
import random
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Solicitar el número de nodos
num_nodos = int(input("Ingrese el número de nodos: "))

# Generar posiciones aleatorias para cada nodo
posiciones = {i: (random.random(), random.random()) for i in range(num_nodos)}

# Calcular la matriz de distancias
matriz_distancias = np.zeros((num_nodos, num_nodos))
for i in range(num_nodos):
    for j in range(i + 1, num_nodos):
        distancia = np.sqrt((posiciones[i][0] - posiciones[j][0])**2 + (posiciones[i][1] - posiciones[j][1])**2)
        matriz_distancias[i, j] = round(distancia, 1)
        matriz_distancias[j, i] = round(distancia, 1)

# Mostrar la matriz de distancias como una tabla
df_distancias = pd.DataFrame(matriz_distancias)
print(df_distancias)

# Graficar las posiciones de los nodos
x = [pos[0] for pos in posiciones.values()]
y = [pos[1] for pos in posiciones.values()]
plt.scatter(x, y)
plt.xlabel("Eje X")
plt.ylabel("Eje Y")
plt.title("Posiciones de los Nodos")
plt.show()
```

```
Ingrese el número de nodos: 10
     0    1    2    3    4    5    6    7    8    9
0  0.0  0.3  0.6  0.5  0.4  0.3  0.3  0.3  0.3  0.4
1  0.3  0.0  0.7  0.7  0.5  0.1  0.2  0.4  0.6  0.7
2  0.6  0.7  0.0  0.5  0.3  0.7  0.9  0.4  0.6  0.5
3  0.5  0.7  0.5  0.0  0.3  0.7  0.7  0.5  0.2  0.1
4  0.4  0.5  0.3  0.3  0.0  0.5  0.6  0.2  0.3  0.3
5  0.3  0.1  0.7  0.7  0.5  0.0  0.3  0.3  0.6  0.7
6  0.3  0.2  0.9  0.7  0.6  0.3  0.0  0.5  0.5  0.7
7  0.3  0.4  0.4  0.5  0.2  0.3  0.5  0.0  0.4  0.4
8  0.3  0.6  0.6  0.2  0.3  0.6  0.5  0.4  0.0  0.2
9  0.4  0.7  0.5  0.1  0.3  0.7  0.7  0.4  0.2  0.0
```
