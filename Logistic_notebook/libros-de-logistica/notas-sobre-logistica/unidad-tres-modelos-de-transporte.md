# Unidad tres: Modelos de Transporte

### Instrucciones para el Uso de la Librería PuLP

La librería PuLP es una herramienta poderosa para la programación lineal en Python. Aquí te proporcionamos un guía paso a paso para usar esta librería de manera efectiva.

#### Instalación de PuLP

Antes de comenzar a usar PuLP, primero necesitas instalarla. Puedes hacerlo fácilmente utilizando pip. Abre una terminal y escribe el siguiente comando:

```bash
pip install pulp
```

#### Creación de un Problema

Para definir un problema de programación lineal, debes comenzar por importar la librería y crear un objeto `LpProblem`. Este objeto es la representación de tu problema.

```python
from pulp import LpProblem, LpMaximize

# Crear un problema de maximización
problem = LpProblem("Mi_Problema", LpMaximize)
```

#### Declaración de Variables

Luego, define las variables de decisión que serán usadas en tu modelo. PuLP proporciona la clase `LpVariable` para este propósito.

```python
from pulp import LpVariable

# Crear una variable continua de decisión
x = LpVariable('x', lowBound=0)
y = LpVariable('y', lowBound=0)
```

#### Definición de la Función Objetivo

La función objetivo es la función matemática que necesitas maximizar o minimizar. Puedes definirla utilizando las variables creadas.

```python
# Definir la función objetivo
problem += 3*x + 2*y, "Función_Objetivo"
```

#### Agregar Restricciones

Las restricciones del problema se añaden utilizando operadores matemáticos habituales. Estas limitan los valores posibles de las variables.

```python
# Añadir restricciones
problem += (2*x + y <= 20), "Restricción_1"
problem += (4*x - 5*y >= -10), "Restricción_2"
```

#### Resolución del Problema

Con la función objetivo y las restricciones definidas, el siguiente paso es resolver el problema. PuLP puede utilizar diferentes solucionadores, pero el solver predeterminado suele ser suficiente para la mayoría de los casos.

```python
problem.solve()
```

#### Imprimir Resultados

Una vez que el problema es resuelto, puedes acceder a los resultados, como el valor óptimo de la función objetivo y las variables de decisión.

```python
# Mostrar estatus del problema
print("Status:", LpStatus[problem.status])

# Mostrar el valor óptimo de las variables
for variable in problem.variables():
    print(f"{variable.name} = {variable.varValue}")

# Valor óptimo de la función objetivo
print("Valor óptimo: ", value(problem.objective))
```

{% hint style="info" %}
La librería PuLP es una herramienta versátil para resolver problemas de programación lineal en Python. Permite una rápida implementación y simplifica la complejidad de modelar problemas de optimización. Con los pasos descritos anteriormente, puedes comenzar a explorar sus capacidades y aplicar programación lineal a tus proyectos.
{% endhint %}

esta libreria sera usada en la resolucion de problemas de transporte.

para mayor informacion sobre esta libreroa podemos visitar: [https://pypi.org/project/PuLP/](https://pypi.org/project/PuLP/)

1. Instalacion de la libreria: _“pip install pulp”_

importamos:

* import pulp

1. crear el problema: para cerar el problema debemos definir la variable que almacenara el problema, por ejempplo “prob” y #creamos el problema. con el comando _“pulp.LpProblem”_ donde le asignaremos nombre y el tipo de problema al que nos enfrentamos sea - Minimizacion : pulp.LpMinimize - Maximizacion: pulp.LpMaximice

con la sintaxis: **prob = pulp.LpProblem(“Asignacion de Tareas”, pulp.LpMinimize)**

2. Creacion de las Variables del modelo:

las variables son la base de los problemas de optimización, y dependiendo del tipo de problema que estés resolviendo, pueden adoptar diferentes categorías (tipologías), como variables continuas, enteras o binarias.

* Para crear una variable en PuLP, se utiliza la clase LpVariable, que requiere al menos un nombre como argumento, y puede incluir restricciones como su tipo (binaria, continua, entera) y límites en sus valores. La forma básica de definir una variable es:

x = LpVariable(‘x’)

las variables pueden contener datos espcificos del modelo o solo estar vacias para ser usadas por el modelo.

‘#definir las variables

* Ejemplos de variables

1. costos = \[\[10, 2, 20], \[12, 7, 15], \[8, 12, 5]]
2. trabajadores = range(3)
3. tareas = range(3)
4. x = pulp.LpVariable.dicts(“x”, \[(i, j) for i in trabajadores for j in tareas], cat=’Binary’)
5. Variables Continuas

Estas son variables que pueden tomar cualquier valor dentro de un rango, ya sea positivo, negativo o sin límites. Esta es la categoría predeterminada cuando no se especifica el tipo.

\\(x\ =\ LpVariable('x')\\)

2. Con límites

Se puede restringir el valor de una variable continua a un intervalo dado (por ejemplo, entre un valor mínimo y máximo).

* x = LpVariable(‘x’, lowBound=0, upBound=10)
* \\\[0\<X\_i<10\\]

lowBound y upBound son los atributos que definen los limites de las variables, es decir tambien sirven para las restricciones donde

* x = LpVariable(‘x’, lowBound=0)
* \\\[X\_{i,j}\ge0\\]

b) Variables Enteras

Las variables enteras solo pueden tomar valores numéricos enteros dentro de un rango específico.

* y = LpVariable(‘y’, lowBound=0, upBound=5, cat=’Integer’)

en este caso se especifica el tipo de variable con el atributo “cat” donde se especifica la toipologoia en este caso “integer” de Entero.

c) Variables Binarias

Las variables _binarias_ son un caso especial de las variables enteras, ya que solo pueden tomar los valores 0 o 1. Este tipo de variable es útil cuando modelamos decisiones binarias (sí/no, verdadero/falso) en problemas como la selección de proyectos o la asignación de recursos, muy comunes en metodos de trasnporte y programacion avanzada.

* z = LpVariable(‘z’, cat=’Binary’)

cuando se modela este tipo de variables hay que tener en cuenta las desicion que conlleva la misma, es decir, sera 1 si se cumple una condicion dada o sera 0 si no se cumple, de esta forma podemos llevar control del sistema y la logica del mismo.

* resumen de argumentos en variables de Pulp:

1. **lowBound:** Define el límite inferior de la variable (el valor más pequeño que puede tomar). Si no se especifica, el valor predeterminado es None (sin límite inferior).
2. **upBound:** Define el límite superior de la variable (el valor más grande que puede tomar). Si no se especifica, el valor predeterminado es None (sin límite superior).
3. **cat:** Este argumento define la categoría (tipo) de la variable:
   * _‘Continuous’:_ Variables continuas (por defecto).
   * _‘Integer’:_ Variables que solo pueden tomar valores enteros.
   * _‘Binary’:_ Variables binarias (que solo toman los valores 0 o 1).

***

3. Definir la funcion objetivo:

Se recomienda antes de proceder con la programacion en python de que el ejercicio o el sistema este definido de esta forma se hace mas facil el desarrollo del mismo, es decir. cuando se pretenda ingresar la F.O del sistema esta ya debe estar definida y conocida segun la naturaleza del sistema investigado, en este caso usaremos la siguiente funcion:

\\\[3x\_1+2x\_2+x\_3\\]

* problema += 3 \* x1 + 2 \* x2 + x3, “Función Objetivo”

notese el nombre de la variable que encierra el problema “problema”

4. Procedmos a agregar las restricciones del sistema:

problema += x1 + x2 + x3 <= 2, “Restricción 1” problema += x1 + x2 >= 1, “Restricción 2”

en este caso las restricciones van precedidas por los signos \\(\le\\) y \\(\ge\\)

notese que no definimos la restriccion de “no negatividad” ya que las variables al ser definidas y acotadas incluyen los valores donde estas pueden operar.

5. Resilvemos:

Utiliza el método solve() para resolver el problema de optimización. PuLP usa un solver incorporado por defecto, pero puedes especificar uno si prefieres.

* problema.solve()

6. MOstrar el resultado:

por ultimo debemos especificarle a la maquina que deseamos ver los resultados estos pueden ser mostrados como valore splanos o podemos usar otras librerias como pandas mathplotlib, etc, para mostrar estos resultados, pero para estos habria que definir las variables y almacenar los datos segun cada una lo requiera.

print(“Estado:”, pulp.LpStatus\[problema.status])

print(“Valor de x1:”, x1.varValue) print(“Valor de x2:”, x2.varValue) print(“Valor de x3:”, x3.varValue)

print(“Valor óptimo de la función objetivo:”, pulp.value(problema.objective))

### Definicion del modelo de Transporte[#](broken-reference)

El transporte es la columna vertebral de la logística, permitiendo el flujo de bienes y servicios a través de la cadena de suministro. Su eficiencia impacta directamente en los costos, la satisfacción del cliente y la competitividad de las empresas.

Existen diferentes **medios** de transporte, como el terrestre, marítimo, aéreo y ferroviario, cada uno con características que los hacen ideales para ciertos tipos de carga y distancias. La elección del medio adecuado es crucial para optimizar la logística.

Además de los medios, se deben considerar los **modos** de transporte, que se refieren a la forma en que se organiza el transporte, como el transporte unimodal (un solo medio), multimodal (combinación de medios) e intermodal (combinación de medios con una sola unidad de carga).

Un modelo logístico que ha ganado popularidad es el **cross-docking**, que busca minimizar el tiempo de almacenamiento y agilizar la distribución.

* Ejemplos

1. Transporte marítimo: Ideal para grandes volúmenes y largas distancias, como el transporte de materias primas o productos manufacturados entre continentes.
2. Transporte aéreo: Recomendado para productos perecederos o de alto valor que requieren entrega rápida, como flores o dispositivos electrónicos.
3. Cross-docking: Un centro de distribución recibe productos de diferentes proveedores, los consolida y los envía inmediatamente a los clientes, reduciendo costos de almacenamiento y tiempos de entrega.

### Variables de Decisión Clave[#](broken-reference)

Al evaluar las opciones de transporte, es fundamental considerar las siguientes variables:

* Costo: Incluye el precio del flete, seguros, impuestos y otros gastos asociados al transporte.
* Tiempo: Se refiere al tiempo total de tránsito, desde la recolección hasta la entrega final.
* Capacidad: Hace referencia a la cantidad de carga que puede transportar el medio elegido.
* Fiabilidad: Se refiere a la probabilidad de que la carga llegue a destino a tiempo y en las condiciones acordadas.

### Representacion grafica de los modelos de transporte en Progranacion lineal[#](broken-reference)

Un modelo de transporte se puede representar gráficamente mediante una red de nodos y arcos, similar a un diagrama de flujo.

1. Nodos: Representan los puntos de origen y destino de la mercancía.

* Nodos de origen: Indican los lugares de donde sale la mercancía (fábricas, almacenes, etc.).
* Nodos de destino: Representan los lugares a donde debe llegar la mercancía (clientes, centros de distribución, etc.). Arcos: Son las conexiones entre los nodos y simbolizan las rutas de transporte disponibles.

2. Arcos

* Cada arco se asocia con un costo de transporte, que puede representar la distancia, el tiempo de viaje o el costo monetario del transporte entre dos nodos. Se puede indicar la capacidad de cada arco, que representa la cantidad máxima de mercancía que se puede transportar por esa ruta.

en python tenemos librerias para modelar estos diagramas, por ejemplo

* graphviz

se puede ampliar info en [https://graphviz.org](https://graphviz.org/)

### Principio de nivelacion:[#](broken-reference)

En los modelos de logística de programación lineal, el principio de nivelación se refiere a la necesidad de equilibrar la oferta y la demanda en el modelo. Esto significa que la cantidad total de bienes o productos que se envían desde los orígenes debe ser igual a la cantidad total de bienes o productos que se reciben en los destinos.

¿Cuándo usar elementos ficticios?

Los elementos ficticios se utilizan cuando la oferta y la demanda no están equilibradas en el modelo de transporte. Se introduce un origen o destino ficticio para absorber el exceso de oferta o demanda, respectivamente.

1. **Exceso de oferta:** Si la oferta total es mayor que la demanda total, se crea un destino ficticio. Los costos de transporte a este destino ficticio se establecen en cero, ya que no representa un destino real.
2. **Exceso de demanda:** Si la demanda total es mayor que la oferta total, se crea un origen ficticio. Los costos de transporte desde este origen ficticio se establecen en cero.

#### Ejemplo de probelma de trasporte usando Pulp[#](broken-reference)

Imagina un problema de transporte con dos orígenes (O1 y O2) y tres destinos (D1, D2 y D3). La oferta de O1 es 100 unidades y la de O2 es 150 unidades. La demanda de D1 es 80 unidades, la de D2 es 100 unidades y la de D3 es 70 unidades.

En este caso, la oferta total (250 unidades) es mayor que la demanda total (250 unidades). Para nivelar el modelo, se introduce un destino ficticio (DF) con una demanda de 0 unidades. Los costos de transporte desde O1 y O2 a DF se establecen en cero.

```
import pulp

# Crear el problema
prob = pulp.LpProblem("Problema de Transporte", pulp.LpMinimize)

# Definir los orígenes y destinos
origenes = ["O1", "O2"]
destinos = ["D1", "D2", "D3", "DF"] # DF es el destino ficticio

# Oferta de cada origen
oferta = {"O1": 100, "O2": 150}

# Demanda de cada destino
demanda = {"D1": 80, "D2": 100, "D3": 70, "DF": 0}

# Costos de transporte (se deben definir según el problema)
costos = {
    ("O1", "D1"): 10,
    ("O1", "D2"): 2,
    ("O1", "D3"): 20,
    ("O1", "DF"): 0,  # Costo cero para el destino ficticio
    ("O2", "D1"): 12,
    ("O2", "D2"): 7,
    ("O2", "D3"): 15,
    ("O2", "DF"): 0,  # Costo cero para el destino ficticio
}

# Variables de decisión
rutas = [(o, d) for o in origenes for d in destinos]
x = pulp.LpVariable.dicts("ruta", rutas, lowBound=0, cat='Integer')

# Función objetivo: Minimizar el costo total de transporte
prob += pulp.lpSum([x[r] * costos[r] for r in rutas])

# Restricciones
# 1. Respetar la oferta de cada origen
for o in origenes:
    prob += pulp.lpSum([x[(o, d)] for d in destinos]) <= oferta[o]

# 2. Satisfacer la demanda de cada destino
for d in destinos:
    prob += pulp.lpSum([x[(o, d)] for o in origenes]) >= demanda[d]

# Resolver el problema
prob.solve()

# Imprimir los resultados
print("Status:", pulp.LpStatus[prob.status])
for v in prob.variables():
    if v.varValue > 0:
        print(v.name, "=", v.varValue)

print("Costo total =", pulp.value(prob.objective))
```

Los valores que quedan en los elementos ficticios en la solución de un problema de transporte representan la diferencia entre la oferta y la demanda.

1. **Destino ficticio:** Si en la solución óptima hay un valor positivo en una ruta hacia el destino ficticio, significa que hay un exceso de oferta en el origen correspondiente. El valor indica la cantidad de unidades que no se envían a ningún destino real.
2. **Origen ficticio:** Si en la solución óptima hay un valor positivo en una ruta desde el origen ficticio, significa que hay un exceso de demanda en el destino correspondiente. El valor indica la cantidad de unidades de demanda que no se pueden satisfacer con la oferta disponible.

### **Definicion del modelo de Transporte:**[#](broken-reference)

Tiene que ver con encontrar un plan de costo mínimo para transportar una mercancía desde varios orígenes hasta varios destinos. Este modelo se puede extender para resolver numerosas aplicaciones que no se relacionan con el transporte dentro de los problemas de control de inventarios, flujo de efectivo, asignación de recursos.

Algoritmo del Transporte, es una adaptación del método Simplex aplicada al caso o estructura particular del modelo de Programación Lineal asociado. Aunque el modelo de este problema se puede resolver mediante el método Simplex, su estructura especial hace posible el uso de un procedimiento especial

```python
import networkx as nx
import matplotlib.pyplot as plt

# Crear un grafo dirigido
G = nx.DiGraph()

# Definir las fuentes y los destinos
fuentes = ['P_1', 'P_2', 'P_3', 'P_4']
destinos = ['C_1', 'C_2', 'C_3', 'C_4']

# Añadir nodos al grafo con la propiedad bipartita
G.add_nodes_from(fuentes, bipartite=0)  # Asignar bipartite=0 a las fuentes
G.add_nodes_from(destinos, bipartite=1)  # Asignar bipartite=1 a los destinos

# Añadir arcos desde cada fuente a cada destino
for fuente in fuentes:
    for destino in destinos:
        G.add_edge(fuente, destino)

# Posicionamiento bipartito
pos = {}
# Fuentes a la izquierda
pos.update((n, (0, i)) for i, n in enumerate(fuentes))
# Destinos a la derecha
pos.update((n, (1, i)) for i, n in enumerate(destinos))

# Dibujar el grafo con nodos y arcos
nx.draw(G, pos, with_labels=True, node_size=3000, node_color='skyblue', font_size=12, font_weight='bold', arrows=True)
plt.title("Red de Transporte: Fuentes a la izquierda y Destinos a la derecha")
plt.show()
```

```python
import networkx as nx
import matplotlib.pyplot as plt
#grafico dirigido
G = nx.DiGraph()
# Definir las fuentes y los destinos
fuentes = ['P_1', 'P_2', 'P_3', 'P_4']
destinos = ['C_1', 'C_2', 'C_3', 'C_4']
# Definir los costos de transporte (por ejemplo, distancias o costos)
costos = {
    ('P_1', 'C_1'): 4, ('P_1', 'C_2'): 2, ('P_1', 'C_3'): 5, ('P_1', 'C_4'): 7,
    ('P_2', 'C_1'): 3, ('P_2', 'C_2'): 6, ('P_2', 'C_3'): 1, ('P_2', 'C_4'): 4,
    ('P_3', 'C_1'): 7, ('P_3', 'C_2'): 3, ('P_3', 'C_3'): 6, ('P_3', 'C_4'): 5,
    ('P_4', 'C_1'): 4, ('P_4', 'C_2'): 5, ('P_4', 'C_3'): 3, ('P_4', 'C_4'): 2
}
# Añadir aristas al grafo con los costos como atributos de peso
for (fuente, destino), costo in costos.items():
    G.add_edge(fuente, destino, weight=costo)

# Posicionamiento bipartito para que las fuentes estén a la derecha y los destinos a la izquierda
pos = {}
# Fuentes a la derecha (x=1)
pos.update((fuente, (0, i)) for i, fuente in enumerate(fuentes))
# Destinos a la izquierda (x=0)
pos.update((destino, (1, i)) for i, destino in enumerate(destinos))

# Dibujar el grafo
plt.figure(figsize=(8, 6))  # Ajustar el tamaño del gráfico
nx.draw(G, pos, with_labels=True, node_size=3000, node_color='skyblue', font_size=12, font_weight='bold', arrows=True)

# Añadir etiquetas con los pesos de las aristas
labels = nx.get_edge_attributes(G, 'weight')
nx.draw_networkx_edge_labels(G, pos, edge_labels=labels)

# Mostrar el gráfico
plt.title("Red de Transporte: Fuentes y Destinos con Costos de Transporte")
plt.show()
```

1- para resolver estos problemas de optimizacion usaremos la ibreria pulp

* hay que instalarla ya que no viene preinstalada en COlab
* [https://www.youtube.com/watch?v=Dq59G8Uf-\_o](https://www.youtube.com/watch?v=Dq59G8Uf-_o)
* [https://pypi.org/project/PuLP/](https://pypi.org/project/PuLP/)
