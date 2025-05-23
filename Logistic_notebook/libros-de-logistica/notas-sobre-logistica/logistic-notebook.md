---
icon: arrow-progress
---

# Logistic Notebook

### TSP Travel sales man Problem - Problema especial de Rutas[#](broken-reference)

Clásicamente, el problema de TSP tiene que ver con hallar el recorrido más corto (ce- rrado) en una situación de n ciudades, donde cada ciudad es visitada exactamente una vez antes de regresar al punto de partida. El modelo TSP asociado se define por medio de dos datos:

**Pasos:**

* Definición de las ciudades: Se identifican todas las ciudades o puntos que el vendedor debe visitar.
* Cálculo de las distancias: Se determina la distancia entre cada par de ciudades.
* Generación de todas las posibles rutas: Matemáticamente, el número de rutas posibles crece exponencialmente con el número de ciudades, lo que hace que este paso sea computacionalmente costoso para problemas de gran tamaño.
* Evaluación de cada ruta: Se calcula la distancia total de cada ruta.
* Selección de la ruta óptima: Se elige la ruta con la menor distancia total.

#### Problema del Viajero o Agente Viajero (TSP)[#](broken-reference)

El **Problema del Viajero** (TSP por sus siglas en inglés: _Traveling Salesman Problem_) es un problema clásico en optimización combinatoria. El objetivo es encontrar la ruta más corta que permite a un viajero visitar un conjunto de ciudades exactamente una vez y regresar a la ciudad de origen. Este problema pertenece a la clase de problemas NP-difíciles, lo que implica que no se conoce un algoritmo eficiente para resolverlo en todos los casos.

**Definición del Problema**[**#**](broken-reference)

* Sea \\(( G = (V, E) )\\) un grafo completo, donde:
  * \\((V)\\) es el conjunto de vértices o ciudades, \\(V= \left(1, 2, ..., n\right)\\).
  * \\((E)\\) es el conjunto de aristas que conectan cada par de ciudades, con un costo asociado.
* A cada arista \\((i,j) \in E \\), se le asigna un peso \\(d\_{ij}\\), que representa la distancia (o costo) entre las ciudades \\(i\\) y \\(j\\).
* El objetivo es encontrar un ciclo hamiltoniano de costo mínimo, es decir, una ruta que pase por todas las ciudades exactamente una vez y regrese a la ciudad de origen, minimizando el costo total.

**Formulación Matemática del TSP**[**#**](broken-reference)

Sea \\(X\_{ij}\\) una variable binaria que toma el valor:

\\\[\begin{split} x\_{ij} = \begin{cases} 1 & \text{si el viajero toma el camino de la ciudad \\( i \\) a la ciudad \\( j \\)} \\\ 0 & \text{en caso contrario} \end{cases} \end{split}\\]

Entonces, el problema del TSP puede formularse como un problema de **programación lineal entera** de la siguiente manera:

**Función objetivo**[**#**](broken-reference)

Minimizar la suma total de los costos de viaje:

\\\[ \min \sum\_{i=1}^{n} \sum\_{j=1, j \neq i}^{n} d\_{ij} x\_{ij} \\]

**Restricciones**[**#**](broken-reference)

1. **Cada ciudad debe ser visitada exactamente una vez**: $\\( \sum\_{j=1, j \neq i}^{n} x\_{ij} = 1 \quad \forall i \in V \\)\\( \\)\\( \sum\_{i=1, i \neq j}^{n} x\_{ij} = 1 \quad \forall j \in V \\)$
2. **Eliminación de subciclos**: Para garantizar que el ciclo recorra todas las ciudades, es necesario evitar subciclos que no incluyan todas las ciudades: $\\( \sum\_{i, j \in S, i \neq j} x\_{ij} \leq |S| - 1 \quad \forall S \subset V, 2 \leq |S| \leq n-1 \\)\\( Donde \\) S $ es un subconjunto de ciudades.
3. **Variable binaria**: $\\( x\_{ij} \in \\{0, 1\\} \quad \forall i, j \in V \\)$

**Ejemplo Sencillo**[**#**](broken-reference)

Supongamos que tenemos 4 ciudades: A, B, C y D, y las distancias entre ellas están dadas por la siguiente matriz:

|   | A  | B  | C  | D  |
| - | -- | -- | -- | -- |
| A | 0  | 10 | 15 | 20 |
| B | 10 | 0  | 35 | 25 |
| C | 15 | 35 | 0  | 30 |
| D | 20 | 25 | 30 | 0  |

El objetivo es encontrar la ruta más corta que pase por todas las ciudades exactamente una vez y regrese a la ciudad de origen.

**Posibles rutas**[**#**](broken-reference)

Enumeramos algunas de las posibles rutas y calculamos las distancias:

1. **A → B → C → D → A**:\
   $\\( 10 + 35 + 30 + 20 = 95 \\)$
2. **A → B → D → C → A**:\
   $\\( 10 + 25 + 30 + 15 = 80 \quad (\text{ruta óptima}) \\)$
3. **A → C → B → D → A**:\
   $\\( 15 + 35 + 25 + 20 = 95 \\)$
4. **A → C → D → B → A**:\
   $\\( 15 + 30 + 25 + 10 = 80 \\)$

La ruta óptima es **A → B → D → C → A** con un costo total de 80.

**explicacion de la restriccionde los subcilos:**[**#**](broken-reference)

* Eliminación de Subciclos

Cuando se utiliza _programación entera_ para resolver el TSP, un problema común que surge son los **subciclos**. Estos son ciclos que visitan un subconjunto de ciudades sin incluir todas las ciudades, lo cual no es una solución válida. Para evitar estos subciclos, se utilizan restricciones adicionales llamadas _restricciones de eliminación de subciclos._ Una técnica común es agregar una condición que garantice que todas las ciudades estén conectadas en un único ciclo.

En concreto, si usamos una formulación basada en variables binarias, donde \\(x\_{ij} =1\\) si el viajero va de la ciudad \\(i\\) a la ciudad \\(j\\), y \\(X\_{ij}=0\\) si no lo hace, podemos imponer restricciones de subtour eliminations mediante:

Las restricciones de **Miller-Tucker-Zemlin (MTZ)**, que definen variables adicionales asociadas a cada ciudad \\(i\\)

***

* Estas restricciones imponen una relación entre las ciudades visitadas, evitando así que se formen subciclos dentro de un subconjunto de ciudades, garantizando un ciclo completo y válido.

***

* Para evitar estos subciclos, el enfoque MTZ introduce variables auxiliares \\(u\_i\\) que son números asociados a cada ciudad \\(i\\) y que representan el “orden” en el que se visita cada ciudad después de la ciudad de origen (normalmente la ciudad 1). Estas variables garantizan que no se formen subciclos, imponiendo un orden lógico al recorrido.
* definimos. \\(u\_1=1\\)(la ciudad de inicio), y para las demás ciudades \\(u\_i\\) representa el “numero de paso” de las ciudades en el recorrido

El objetivo de las restricciones _MTZ_ es asegurar que si el viajero se desplaza de la ciudad i a la ciudad j, la ciudad j debe ser visitada después de la ciudad i. Esto se puede modelar mediante la siguiente restricción:

\\\[ u\_i - u\_j + n\*x\_{ij} \le n - 1 \ \forall i,j \ (i \ne j) \\]

Donde:

1. \\(u\_i\\) y \\(u\_j\\) son variables auxiliares asociadas a las ciudades \\(i\\) y \\(j\\)
2. \\(n\\) es el número total de ciudades.
3. \\(x\_{ij}\\) es la variable binaria que indica si el viajero se desplaza de \\(i\\) a \\(j\\)

**ejemplo de restriccion de ciclo**[**#**](broken-reference)

supongamos que tenemos 4 ciudades (A,B,C Y D) Y deseamos evitar los subciclos usamos la variable \\(u\_i\\) que representa el orden de la visita.

* \\(u\_A=1\\) (esta es la ciudad de inicio A)
* si \\(X\_{AB}=1\\) (esto indica que hay un viaje de A a B, la restriccion será:

\\\[\begin{split} u\_A - u\_B+ 4\*x\_{AB} \le 3 \\\ 1-u\_B+4\le 3 \\\ u\_B\ge2 \end{split}\\]

Esto quiere decir que B debera ser visitada despues de A

#### Grupo de Ejercicios:[#](broken-reference)

**Ejercicios: Problema del Viajero y Eliminación de Subciclos**[**#**](broken-reference)

**Ejercicio 1: Matriz de distancias y recorrido mínimo**[**#**](broken-reference)

Dada la siguiente matriz de distancias entre 4 ciudades, resuelve el problema del viajero para encontrar el recorrido mínimo que pase por todas las ciudades exactamente una vez y regrese a la ciudad de origen.

objetivo del ejercicio: Debes Enfocarte en resolver el problema del viajero (TSP) utilizando una matriz de distancias y encontrar el recorrido mínimo sin subciclos.

|   | A  | B  | C  | D  |
| - | -- | -- | -- | -- |
| A | 0  | 10 | 15 | 20 |
| B | 10 | 0  | 35 | 25 |
| C | 15 | 35 | 0  | 30 |
| D | 20 | 25 | 30 | 0  |

1. ¿Cuál es el recorrido más corto?
2. ¿Cuál es la distancia total del recorrido?

**Ejercicio 2: Eliminación de subciclos con MTZ**[**#**](broken-reference)

Formule el problema del viajero para el conjunto de 5 ciudades utilizando la formulación de Miller-Tucker-Zemlin (MTZ). Asegúrate de incluir las restricciones para evitar subciclos. Usa las siguientes distancias entre ciudades:

|   | A  | B  | C  | D  | E |
| - | -- | -- | -- | -- | - |
| A | 0  | 12 | 10 | 19 | 8 |
| B | 12 | 0  | 3  | 7  | 2 |
| C | 10 | 3  | 0  | 6  | 4 |
| D | 8  | 2  | 4  | 11 | 0 |

1. Escribe las restricciones para evitar subciclos utilizando las variables \\(u\_i\\) en la formulación MTZ.
2. Resuelve el problema del viajero considerando estas restricciones.

**Ejercicio 3: Identificación de subciclos**[**#**](broken-reference)

Resuelve el problema del viajero para las 4 ciudades (A, B, C, D) con la siguiente matriz de distancias:

|   | A  | B  | C  | D  |
| - | -- | -- | -- | -- |
| A | 0  | 8  | 15 | 10 |
| B | 8  | 0  | 12 | 14 |
| C | 15 | 12 | 0  | 9  |
| D | 10 | 14 | 9  | 0  |

1. Realiza una primera aproximación usando programación entera.
2. Identifica si hay subciclos en tu solución.
3. Aplica las restricciones necesarias para eliminarlos.

**Ejercicio 4: Comparación entre formulaciones**[**#**](broken-reference)

Compara la formulación clásica del TSP con la formulación de Miller-Tucker-Zemlin (MTZ) para el siguiente conjunto de 4 ciudades:

|   | A  | B | C  | D  |
| - | -- | - | -- | -- |
| A | 0  | 9 | 11 | 13 |
| B | 9  | 0 | 6  | 7  |
| C | 11 | 6 | 0  | 8  |
| D | 12 | 7 | 8  | 0  |

1. Formula el problema usando programación lineal entera clásica.
2. Formula el problema usando la técnica MTZ.
3. Resuelve ambas formulaciones y compara los resultados en términos de complejidad y eficiencia.

**Ejercicio 5: Uso de software para resolver el TSP**[**#**](broken-reference)

Usa un software de optimización (por ejemplo, Excel Solver, Python con `PuLP` o cualquier otro) para resolver el siguiente problema del viajero para 5 ciudades:

|   | A  | B  | C | D  | E  |
| - | -- | -- | - | -- | -- |
| A | 0  | 14 | 9 | 7  | 13 |
| B | 14 | 0  | 5 | 12 | 8  |
| C | 9  | 5  | 0 | 15 | 6  |
| D | 13 | 8  | 6 | 10 | 0  |

1. Resuelve el problema usando el software.
2. Asegúrate de que no haya subciclos en la solución.
3. Reporta el recorrido óptimo y la distancia total.

NOTA DEL PROFESOR: estos son ejercicios basicos para afianzar el problema de TSP, no obstante los probelmas pueden tener otras variables de desicion para el sistema como costos \\(C\_{ij}\\) donde entraremos a conocer el costo asociado a cada una de las distancias y recorridos, estos costos pueden estar fijos con recorridos o darse en fuancion de la distacia \\(d\_i\\) es decir que se multiplicaria por el costo unitario de la unidad de distancia para poder entregar el costo al final de la operacion, asi mismo podemos incluir costos fijos, con el fin de generar la alternativa mas economica para el sistema; les dejo un ejemplo.

Ciudades: A, B, C, D, E

* Valor por kilómetro (o unidad de distancia): 5 COP por kilómetro
* Matriz de distancias (en kilómetros):

| A | B  | C  | D  | E  |
| - | -- | -- | -- | -- |
| A | 0  | 10 | 15 | 20 |
| B | 10 | 0  | 35 | 30 |
| C | 15 | 35 | 0  | 25 |
| D | 20 | 30 | 25 | 0  |
| E | 25 | 20 | 30 | 15 |

**Matriz de distancias (en kilómetros)**[**#**](broken-reference)

|   | A  | B  | C  | D  | E  |
| - | -- | -- | -- | -- | -- |
| A | 0  | 10 | 15 | 20 | 25 |
| B | 10 | 0  | 35 | 30 | 20 |
| C | 15 | 35 | 0  | 25 | 30 |
| D | 20 | 30 | 25 | 0  | 15 |
| E | 25 | 20 | 30 | 15 | 0  |

**Matriz de costos (5 Cop/km)**[**#**](broken-reference)

|   | A   | B   | C   | D   | E   |
| - | --- | --- | --- | --- | --- |
| A | 0   | 50  | 75  | 100 | 125 |
| B | 50  | 0   | 175 | 150 | 100 |
| C | 75  | 175 | 0   | 125 | 150 |
| D | 100 | 150 | 125 | 0   | 75  |
| E | 125 | 100 | 150 | 75  | 0   |

#### Bloque de Ejercicios a resolver:[#](broken-reference)

1. Secuenciación de Pinturas en una Planta de Producción

Una compañía fabrica diferentes lotes de pintura en una planta de producción. Cada lote corresponde a un color específico, y el cambio entre un color y otro requiere un tiempo de preparación. Dependiendo de los colores involucrados, los tiempos de preparación pueden variar considerablemente. Una vez completada la secuencia de colores, el ciclo se reinicia en el mismo orden.

El objetivo de la planta es minimizar el tiempo total de preparación por ciclo, seleccionando una secuencia de colores óptima.

Datos:

Los colores de pintura disponibles son:

* Rojo (R)
* Azul (A)
* Verde (V)
* Amarillo (Y)
* Blanco (W)

La siguiente tabla muestra el tiempo de preparación (en minutos) que se requiere para cambiar entre dos colores consecutivos:

|       | R  | A  | V  | Y  | W  |
| ----- | -- | -- | -- | -- | -- |
| **R** | 0  | 5  | 8  | 12 | 7  |
| **A** | 5  | 0  | 10 | 6  | 9  |
| **V** | 8  | 10 | 0  | 7  | 11 |
| **Y** | 12 | 6  | 7  | 0  | 4  |
| **W** | 7  | 9  | 11 | 4  | 0  |

2. Tarjeta de Circuito Integrado

En una planta de producción, se perforan agujeros en tarjetas de circuito idénticas para montar los componentes electrónicos. Las tarjetas son procesadas por un taladro móvil que se desplaza entre los agujeros. El objetivo es encontrar la secuencia óptima de perforación para minimizar el tiempo total de desplazamiento del taladro.

Cada agujero en la tarjeta se representa como un punto, y el desplazamiento entre dos agujeros representa el tiempo o la distancia que el taladro debe recorrer entre los dos puntos.

Datos:

Los agujeros en la tarjeta están ubicados en las siguientes posiciones:

* Agujero 1 (H1)
* Agujero 2 (H2)
* Agujero 3 (H3)
* Agujero 4 (H4)
* Agujero 5 (H5)

La siguiente tabla muestra el **tiempo de desplazamiento (en segundos)** que tarda el taladro en moverse de un agujero a otro:

|        | H1 | H2 | H3 | H4 | H5 |
| ------ | -- | -- | -- | -- | -- |
| **H1** | 0  | 3  | 6  | 9  | 5  |
| **H2** | 3  | 0  | 4  | 8  | 7  |
| **H3** | 6  | 4  | 0  | 3  | 6  |
| **H4** | 9  | 8  | 3  | 0  | 4  |
| **H5** | 5  | 7  | 6  | 4  | 0  |

* Resuelva:

1. **Formulación del problema**: Modela este problema como un _Problema del Agente Viajero (TSP)_, donde cada agujero es una ciudad y el tiempo de desplazamiento entre los agujeros es la distancia entre ciudades.
2. **Determinación de la secuencia óptima**: Utiliza la matriz de tiempos de desplazamiento para encontrar la secuencia óptima en la que el taladro debe moverse para minimizar el tiempo total de perforación.
3. **Aplicación práctica**: Explica cómo la secuencia óptima reduce el tiempo total de operación y mejora la eficiencia en la línea de producción de las tarjetas de circuito, calcule la capacidad de la planta en dos escenarios de secuencia en un tiempo equivalente a un año, de 8 horas diarias de lunes a viernes.
4. **Restricciones adicionales**: Describe cómo manejarías el problema si algunos agujeros debieran ser perforados en un orden específico debido a restricciones técnicas o de diseño.
5. Ejercicio de TSP: Obtención de Imágenes Celestes

La NASA utiliza satélites para capturar imágenes de diversos objetos celestes. El satélite debe reposicionarse entre cada toma de imagen, y el consumo de combustible depende de la distancia entre los objetos. La meta es encontrar la secuencia óptima de toma de imágenes que minimice el consumo total de combustible del satélite.

Cada objeto celeste es considerado como un punto, y el consumo de combustible necesario para moverse de un objeto a otro representa la distancia entre esos puntos.

Datos: Los objetos celestes a fotografiar son:

* Objeto 1 (O1)
* Objeto 2 (O2)
* Objeto 3 (O3)
* Objeto 4 (O4)
* Objeto 5 (O5)

La siguiente tabla muestra el **consumo de combustible (en litros)** que requiere el satélite para reposicionarse entre dos objetos celestes consecutivos:

|        | O1 | O2 | O3 | O4 | O5 |
| ------ | -- | -- | -- | -- | -- |
| **O1** | 0  | 7  | 9  | 8  | 12 |
| **O2** | 7  | 0  | 10 | 6  | 5  |
| **O3** | 9  | 10 | 0  | 4  | 7  |
| **O4** | 8  | 6  | 4  | 0  | 3  |
| **O5** | 12 | 5  | 7  | 3  | 0  |

* Preguntas:

1. **Formulación del problema**: Modela este problema como un _Problema del Agente Viajero (TSP)_, donde cada objeto celeste es una “ciudad” y el consumo de combustible es la “distancia” entre dos objetos consecutivos.
2. **Determinación de la secuencia óptima**: Utiliza la matriz de consumos de combustible para encontrar la secuencia óptima que minimice el consumo total de combustible del satélite.
3. **Aplicación práctica**: Explica cómo la secuencia óptima reduce el consumo de combustible y maximiza la eficiencia de la misión de obtención de imágenes.
4. **Restricciones adicionales**: Si algunos objetos deben fotografiarse en un orden específico, ¿cómo modificarías el modelo para tener en cuenta estas restricciones?
5. Problemas Adicionales

* conjunto de problemas del libro Hamdy A taha 7ma ed - **CONJUNTO DE PROBLEMAS 11.1A pagina 397**

#### Centro de Gravedad - localizacion[#](broken-reference)

El modelo de centro de gravedad es un método más simple y rápido que el TSP, utilizado para determinar la ubicación óptima de una instalación (almacén, fábrica, etc.) considerando la demanda y la distancia a los puntos de demanda.

la pregunta problema es ¿donde ubicaremos la planta o el sitio para la disminucion de costos o distancias?

**Pasos:**

* Identificación de los puntos de demanda: Se localizan todos los puntos donde existe demanda de los productos o servicios (clientes, tiendas, etc.).
* Asignación de pesos: A cada punto de demanda se le asigna un peso que representa la demanda en ese punto.
* Cálculo de las coordenadas del centro de gravedad: Se calculan las coordenadas x e y del centro de gravedad ponderado de todos los puntos de demanda, teniendo en cuenta sus pesos y distancias.
* Ubicación de la instalación: La instalación se ubica en las coordenadas calculadas en el paso anterior.

### VRP. Vehicle Routing Problems[#](broken-reference)

El modelo de transporte VRP (Vehicle Routing Problem) es un problema clásico de optimización combinatoria que se enfoca en la distribución eficiente de productos o servicios desde un conjunto de depósitos a un conjunto de clientes, utilizando una flota de vehículos. El objetivo es minimizar los costos totales, como la distancia recorrida o el tiempo de viaje, cumpliendo con las restricciones de capacidad de los vehículos y las demandas de los clientes. (MEDIORREAL, 2014)

* hace referencia a la asignación adecuada de las rutas de distribución o abastecimiento, a una flota de carros destinada a transportar la mercancía de un punto de depósito a los clientes. Es considerado un problema NP-hard o NP- complejo, ya que el tiempo de solución del algoritmo no se encuentra ligado al tiempo polinomial, por el contrario, tiene un comportamiento de tipo exponencial.

***

#### Modelo Teórico del VRP (vehicle routing problem)[#](broken-reference)

**Datos del Problema:**[**#**](broken-reference)

* \\(N\\): Conjunto de clientes (( N = {1, 2, …, n} )).
* \\(V\\): Conjunto de vehículos (( V = {1, 2, …, m} )).
* \\(q\_i\\): Demanda del cliente \\(i\\).
* \\(c\_{ij}\\): Costo de viajar del cliente \\(i\\) al cliente \\(j\\).
* \\(Q\\): Capacidad máxima de carga de cada vehículo.

**Variables de Decisión:**[**#**](broken-reference)

* \\(x\_{ij}^k\\): Variable binaria que indica si el vehículo \\( k\\) viaja directamente del cliente ( \\(i\\) ) al cliente ( \\(j\\) ).
* \\(u\_i\\): Variable que representa la carga acumulada en el cliente ( i ).

**Función Objetivo:**[**#**](broken-reference)

\\\[ \text{Minimizar } \sum\_{i \in N} \sum\_{j \in N} \sum\_{k \in V} c\_{ij} \cdot x\_{ij}^k \\]

**Restricciones:**[**#**](broken-reference)

1. Cada cliente debe ser visitado exactamente una vez por un vehículo: $\\( \sum\_{j \in N, j \neq i} x\_{ij}^k = 1, \quad \forall i \in N, \forall k \in V \\)$
2. Cada vehículo debe salir de exactamente un depósito y regresar al mismo: $\\( \sum\_{j \in N, j \neq i} x\_{0j}^k = 1, \quad \forall k \in V \\\ \sum\_{i \in N, i \neq j} x\_{ij}^k = 1, \quad \forall k \in V \\)$
3. Capacidad de carga de cada vehículo: $\\( \sum\_{i \in N} q\_i \cdot x\_{ij}^k \leq Q, \quad \forall j \in N, \forall k \in V \\)$
4. Subtours no permitidos: $\\( u\_i - u\_j + Q \cdot x\_{ij}^k \leq Q - q\_j, \quad \forall i, j \in N, j \neq 0, \forall k \in V \\)$

Estas restricciones garantizan que se satisfaga la demanda de todos los clientes, que se respete la capacidad de carga de cada vehículo, y que no se formen subtours en la solución.

#### Ejemplo de VRP Clasico[#](broken-reference)

Supongamos que tenemos una flota de tres vehículos que deben entregar paquetes a cinco clientes. Cada cliente tiene una demanda de paquetes que deben satisfacerse, y cada vehículo tiene una capacidad máxima de carga. El objetivo es planificar las rutas de los vehículos de manera que se minimice la distancia total recorrida y se satisfagan todas las demandas de los clientes.

Datos del Problema:

1. 5 clientes (numerados del 1 al 5).
2. 3 vehículos (numerados del 1 al 3).
3. Demandas de los clientes: \[3, 4, 2, 5, 1].
4. Capacidad de carga de cada vehículo: 7.
5. Distancias entre los clientes (en km):

|       | **1** | **2** | **3** | **4** | **5** |
| ----- | ----- | ----- | ----- | ----- | ----- |
| **1** | 0     | 2     | 3     | 4     | 5     |
| **2** | 2     | 0     | 1     | 2     | 3     |
| **3** | 3     | 1     | 0     | 1     | 2     |
| **4** | 4     | 2     | 1     | 0     | 1     |
| **5** | 5     | 3     | 2     | 1     | 0     |

_Objetivo:_ Minimizar la distancia total recorrida.

* Restricciones:

1. Cada cliente debe ser visitado exactamente una vez por un vehículo.
2. Cada vehículo debe salir de un depósito y regresar al mismo.
3. La capacidad de carga de cada vehículo no debe superarse.
4. No se permiten subtours.

modelos de solucion:

1. ACO: altgoritmo de la colonia de hormiga: Este algoritmo simula el comportamiento de las hormigas para encontrar soluciones aproximadas a problemas de optimización combinatoria, como el VRP.
2. Métodos de Búsqueda Exhaustiva: Estos métodos evalúan todas las posibles combinaciones de rutas de vehículos para encontrar la solución óptima. Esto puede ser práctico para instancias pequeñas del problema, pero se vuelve computacionalmente inviable para instancias más grandes debido a la explosión combinatoria de posibles soluciones.
3. Métodos Heurísticos: Los métodos heurísticos utilizan reglas empíricas o estrategias inteligentes para encontrar soluciones subóptimas en un tiempo razonable. Algunos ejemplos incluyen el algoritmo del vecino más cercano, el algoritmo de inserción más barata y el algoritmo del ahorro de distancia.
4. Métodos Metaheurísticos: Estos son algoritmos de búsqueda de soluciones aproximadas que pueden escapar de óptimos locales y encontrar soluciones de alta calidad en un tiempo razonable. Además de ACO, otros métodos metaheurísticos comunes incluyen el algoritmo genético, la búsqueda tabú, la búsqueda de vecindario variable y el recocido simulado.
5. Programación Lineal Entera (ILP): La formulación del VRP como un problema de programación lineal entera permite utilizar solucionadores de ILP para encontrar la solución óptima. Sin embargo, la complejidad computacional de estos solucionadores puede hacer que este enfoque sea impráctico para instancias grandes.
6. Métodos Basados en Algoritmos de Árbol de Expansión Mínima: Algunos métodos utilizan algoritmos como Prim o Kruskal para construir una ruta inicial y luego aplican heurísticas para mejorarla.

resolviendo en PL

**Variables de Decisión:**

* \\(x\_{ijk}\\): Variable binaria que indica si el vehículo \\(i\\) viaja de cliente \\(j\\) a cliente \\(k\\).
* \\(u\_i\\): Variable que representa el total de carga entregada por el vehículo \\(i\\).

**Función Objetivo:**

* \\( \text{Minimizar} \sum\_{i=1}^{3} \sum\_{j=0}^{5} \sum\_{k=0}^{5} c\_{jk} \cdot x\_{ijk}\\)

**Restricciones:**

1. Cada cliente debe ser visitado exactamente una vez por un vehículo: \$$
2. \sum\_{i=1}^{3} x\_{ijk} = 1, \quad \forall j \in {1, 2, 3, 4, 5}\\
3. \sum\_{j=1}^{5} x\_{i0j} = 1, \quad \forall i \in {1, 2, 3} \$$
4. Cada vehículo debe salir de un depósito y regresar al mismo: \$$
5. \sum\_{j=1}^{5} x\_{ij0} = 1, \quad \forall i \in {1, 2, 3}\\
6. \sum\_{i=1}^{3} x\_{i00} = 1 \$$
7. Capacidad de carga de cada vehículo: $\\( u\_i - u\_j + Q \cdot x\_{ijk} \leq Q - q\_k,\\\ \quad \forall i \in \\{1, 2, 3\\}, \forall j,k \in \\{1, 2, 3, 4, 5\\}, j \neq k \\)$
8. Subtours no permitidos: \$$
9. u\_1 \geq q\_j \cdot x\_{1jk}, \quad \forall j \in {1, 2, 3, 4, 5}\\
10. u\_2 \geq q\_j \cdot x\_{2jk}, \quad \forall j \in {1, 2, 3, 4, 5}\\
11. u\_3 \geq q\_j \cdot x\_{3jk}, \quad \forall j \in {1, 2, 3, 4, 5}\ \$$ **Donde:**

* \\(Q\\) es la capacidad máxima de carga de cada vehículo.
* \\(q\_j\\) es la demanda del cliente \\(j\\).
* \\(c\_{jk}\\) es el costo de viajar del cliente \\(j\\) al cliente \\(k\\).

```
import graphviz

graph = graphviz.Graph(engine='neato')

# Crear grafo
dot = graphviz.Digraph()


# Agregar nodos
dot.node('Planta 1', shape="circle", style="filled", fillcolor="#ADD8E6", fontsize= '10')
dot.node('Planta 2', shape="circle", style="filled", fillcolor="#ADD8E6",fontsize= '10')
dot.node('Planta 3', shape="circle", style="filled", fillcolor="#ADD8E6",fontsize= '10')
dot.node('Ciudad 1', shape="circle", style="filled", fillcolor="#ADD8E6",fontsize= '10')
dot.node('Ciudad 2', shape="circle", style="filled", fillcolor="#ADD8E6",fontsize= '10')
dot.node('Ciudad 3', shape="circle", style="filled", fillcolor="#ADD8E6",fontsize= '10')


# Agregar aristas
dot.edge('Planta 1', 'Ciudad 1', label='600',fontsize= '10')
dot.edge('Planta 1', 'Ciudad 2', label='700',fontsize= '10')
dot.edge('Planta 1', 'Ciudad 3', label='400',fontsize= '10')


dot.edge('Planta 2', 'Ciudad 1', label='320',fontsize= '10')
dot.edge('Planta 2', 'Ciudad 2', label='300',fontsize= '10')
dot.edge('Planta 2', 'Ciudad 3', label='350',fontsize= '10')


dot.edge('Planta 3', 'Ciudad 1', label='500',fontsize= '10')
dot.edge('Planta 3', 'Ciudad 2', label='480',fontsize= '10')
dot.edge('Planta 3', 'Ciudad 3', label='450',fontsize= '10')


# Mostrar grafo
dot
```

```
# Importar la librería PuLP
import pulp

# Crear un problema de minimización
problema = pulp.LpProblem("Problema_Electricidad", pulp.LpMinimize)

# Definir las variables de decisión
x11 = pulp.LpVariable("x11", lowBound=0, cat='Continuous')
x12 = pulp.LpVariable("x12", lowBound=0, cat='Continuous')
x13 = pulp.LpVariable("x13", lowBound=0, cat='Continuous')
x21 = pulp.LpVariable("x21", lowBound=0, cat='Continuous')
x22 = pulp.LpVariable("x22", lowBound=0, cat='Continuous')
x23 = pulp.LpVariable("x23", lowBound=0, cat='Continuous')
x31 = pulp.LpVariable("x31", lowBound=0, cat='Continuous')
x32 = pulp.LpVariable("x32", lowBound=0, cat='Continuous')
x33 = pulp.LpVariable("x33", lowBound=0, cat='Continuous')

# Definir la función objetivo
problema += 600*x11 + 700*x12 + 400*x13 + 320*x21 + 300*x22 + 350*x23 + 500*x31 + 480*x32 + 450*x33 \
            + 1000*0.2*(x11 + x12 + x21 + x22)

# Definir las restricciones
problema += (x11 + x21 + x31 >= 30)
problema += (x12 + x22 + x32 >= 35)
problema += (x13 + x23 >= 25)
problema += (x11 + x12 + x13 <= 25)
problema += (x21 + x22 + x23 <= 40)
problema += (x31 <= 30)

# Resolver el problema
problema.solve()

# Imprimir la solución
print("La solución óptima es:")
print("x11 = ", pulp.value(x11))
print("x12 = ", pulp.value(x12))
print("x13 = ", pulp.value(x13))
print("x21 = ", pulp.value(x21))
print("x22 = ", pulp.value(x22))
print("x23 = ", pulp.value(x23))
print("x31 = ", pulp.value(x31))
print("x32 = ", pulp.value(x32))
print("x33 = ", pulp.value(x33))
print("El costo total es:", pulp.value(problema.objective))
```

***

### El modelo de Transbordo[#](broken-reference)

***

En el modelo de transbordo o Cross docking se inicia con el supuesto que el hecho de pasar por nodos intermedios supone un ahorro al sistema, mientras que el modelo general de transporte solo supone entregas directas.

Ejemplo:

dopn fabricas de producto X \\(P\_1\ y\ P\_2\\) en asocian con tres agencias \\(D\_1, D\_2\ y\ D\_3\\) a travez de dos centros de distribicion \\(T\_1\ y\ T\_2\\)

1. genere el modelo de red de este apartado a mano y en colab. usando Graphviz

```
from IPython.display import Image
Image(filename='/content/drive/MyDrive/Libros academicos en colab/1. Logistica/Imagen 16-03-23 a las 1.26 p.m..jpeg')
```

La oferta de las plantas son como se muestran en la figura:

$

* Demanda\ en\ los\ P\_n \ P\_1 = 1000\ Un \ P\_2 = 1200\ Un \ \\
* Demanda\ en\ los\ D\_n \ D\_1= 800 \ D\_2=900 \ D\_3= 500 \ $

Note que los nodos \\(t\_n\ y\ D\_n\\) funcionan como entrada y salida. a estos se les denomina **Nodos de Transbordo**

* los nodos de oferta pura son los emisores de las unidades
* los nodos de demanda pura son los qu solop reciben unidades
* los nodos de transbordo son los que cumplen estas dos funciones al tiempo. (oferta original + Amortiguador)
* los nodos de demanda pura y transbordo tiene (demanada original + Amrtiguador)

la Cantidad _amortiguador_ debe ser lo suficentemente grande para garantizar toda la oferta o demanda _original_ pase por cualquiera de los nodos de Transbordo siendo \\(B\\) la cantidad deseada de amortiguador. entonces:

B = Oferta(Demanda total) = 1000 + 1200 (ú\ 800 +900+500) = 2200 unidades

con este amortiguador este modelpo se transforma en un modelo original de transporte (…)

A continuacion la respuesta al modelo usando el modelo tradicional de transporte.

| -          | \\(T\_1\\) | \\(T\_2\\) | \\(D\_1\\) | \\(D\_2\\) | \\(D\_3\\) |      |
| ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---- |
| \\(P\_1\\) | 3          | 4          | M          | M          | M          | 1000 |
| \\(P\_2\\) | 2          | 5          | M          | M          | M          | 1200 |
| \\(T\_1\\) | 0          | 7          | 8          | 6          | M          | B    |
| \\(T\_2\\) | M          | 0          | M          | 4          | 9          | B    |
| \\(D\_1\\) | M          | M          | 0          | 5          | M          | B    |
| \\(D\_2\\) | M          | M          | M          | 0          | 3          | B    |

\*\*

#### Ejercicios de Transbordo:[#](broken-reference)

***

1. Formule el modelo correspondiente a los siguinetes diagramas:

```
from IPython.display import Image
Image(filename='/content/drive/MyDrive/Libros academicos en colab/1. Logistica/red2.jpeg',width = 300, height = 200)
```

```
from IPython.display import Image
Image(filename='/content/drive/MyDrive/Libros academicos en colab/1. Logistica/red3.jpeg')
```

2. Construya y optimice el siguiente ejercicio de crossdocking

la empresa Cano.Ltda es una empresa en expansion con un problema de tranbordo clasico, donde usted es contratado como ingeniero de peraciones y se enfrenta a esta desicion, la empresa cuenta con 3 plantas de produccion ubicadas en diferentes puntos de la ciudad, estas abastecen 2 almacenes propios de la compañia (CEDIS), pero debido al cambio en el mercado, el producto debera ser reempacado en bodegas para poder ser llevado a los CEDIS, en este caso contamos con 3 Bodegas que nos prestaran este servicio, estas bodegas tambien son propias.

* construya el diagrama de red y nodos con base en la siguiente informacion: el grafico debera ser visto de izquierda a derecha, donde en la primera parte encontraremos Tres nodos correspondientes a las tres plantas de fabricaciond e la compañia, estod nodos son P\_1, P\_2 y P\_3 estos se comunican por carretera con las Bodegas que hacen el cambio de empaque que se llaman B\_1. B\_2 y B\_3 estas se encuentran en el centro del grafico, las rutas existentes nos obligan a tener la siguente distribucion: la P\_1 solo puede enviar material a B\_1 con una distancia de 20km entre ellas, la P\_2 puede enviar materiales a B\_1, B\_2 y B\_3 con distancias de 10 km, 50 km y 20 km respectivamente, por ultimo P\_3 puede enviar material a B\_3 con una distancia de 15 km; estas tres bodegas pueden enviar material ya procesado a los CEDIS de la sihuiente forma B\_1 puede enviar al CEDI\_1 que esta a una distancia de 10 km, la B\_2 puede enviar a CEDI\_1 y CEDI\_2 que estan a una distacia de 50km y 20 km respectivamente y B\_3 puede enviar al CEDI\_2 que esta a una distancia de 30 km; en algunos casos puede pasar que la capacidad de procesamiento de alguna de las bodegas sea superada y estas puedan ayudarse con otras bodegas, para eso existen rutas de comunicacione entre ellas como son B\_1 esta comunicado con B\_2 a una distancia de 10 km y B\_3 con B\_2 a una distancia de 15 km.

```
import networkx as nx
import matplotlib.pyplot as plt

# Crear un grafo dirigido (ya que las rutas tienen una dirección)
G = nx.DiGraph()

# Agregar nodos
nodos = ['P_1', 'P_2', 'P_3', 'B_1', 'B_2', 'B_3', 'CEDI_1', 'CEDI_2']
G.add_nodes_from(nodos)

# Agregar aristas con distancias (pesos)
aristas = [
    ('P_1', 'B_1', 20),
    ('P_2', 'B_1', 10),
    ('P_2', 'B_2', 50),
    ('P_2', 'B_3', 20),
    ('P_3', 'B_3', 15),
    ('B_1', 'CEDI_1', 10),
    ('B_2', 'CEDI_1', 50),
    ('B_2', 'CEDI_2', 20),
    ('B_3', 'CEDI_2', 30),
    ('B_1', 'B_2', 10),
    ('B_3', 'B_2', 15)
]
G.add_weighted_edges_from(aristas)

# Dibujar el grafo
pos = nx.shell_layout(G)  # Posicionamiento de los nodos
nx.draw(G, pos, with_labels=True, font_weight='bold')
labels = nx.get_edge_attributes(G,'weight')
nx.draw_networkx_edge_labels(G,pos,edge_labels=labels)
plt.show()
```

Matriz de Costos:

| Nodos | 1 | 2 | 3 | 4  | 5  | 6  | 7  | 8  |
| ----- | - | - | - | -- | -- | -- | -- | -- |
| 1     | - | - | - | 20 | -  | -  | -  |    |
| 2     | - | - | - | 10 | 20 | 50 | -  | -  |
| 3     | - | - | - | -  | 15 | -  | -  | -  |
| 4     | - | - | - | -  | 20 | 10 | 10 | -  |
| 5     | - | - | - | -  | -  | 30 |    | 30 |
| 6     | - | - | - | -  | -  | -  | 50 | 20 |
| 7     | - | - | - | -  | -  | -  | -  | -  |
| 8     | - | - | - | -  | -  | -  | -  | -  |

* Costos de produccion:

|   | Costos de produccion |        |
| - | -------------------- | ------ |
| 1 | 400                  | unidad |
| 2 | 450                  | unidad |
| 3 | 470                  | unidad |

1. con base en la matriz de costos hay hacer la matriz de envio, es decir solo con costos.

el modelo contempla que:

1. debe estar nivelado
2. toda la oferta debe pasar por los nodos de mixtos (transbordo)
3. consrtruya la matriz de transbordo

la empresa cano.ltda es una empresa en expansion y en su opercion acaba de firmar unas alienzas con diferentes empresas con el fin de comercializar su producto estrella la empresa posee dos fabricas \\(P\_1\\) y \\(P\_2\\) las cuales tienen una oferta de 1000 unidades y 1200 unidades respectivamente. el grupo ahora cuenta con dos centros de distribucion que llamamos. \\(T\_1\\) y \\(T\_2\\), al final de la cadena se cuenta con tres distribuidores \\(D\_1\\) \\(D\_2\\) y \\(D\_3\\) las cuales tienen una demanada de 800, 900 y 500 respectivamente.

las distancias correspondientes entre cada uno de los actores se da en la siguiente tabla de distancias:

|            | \\(P\_1\\) | \\(P\_2\\) | \\(T\_1\\) | \\(T\_2\\) | \\(D\_1\\) | \\(D\_2\\) | \\(D\_3\\) |
| ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- |
| \\(P\_1\\) | 0          | -          | 3          | 4          | -          | -          | -          |
| \\(P\_2\\) | -          | 0          | 2          | 5          | -          | -          | -          |
| \\(T\_1\\) | -          | -          | 0          | 7          | 8          | 6          | -          |
| \\(T\_2\\) | -          | -          | -          | 0          | -          | 4          | 9          |
| \\(D\_1\\) | -          | -          | -          | -          | 0          | 5          | -          |
| \\(D\_2\\) | -          | -          | -          | -          | -          | 0          | 3          |
| \\(D\_3\\) | -          | -          | -          | -          | -          | -          | 0          |

| Oferta     | qty     |
| ---------- | ------- |
| \\(P\_1\\) | 1000 Un |
| \\(P\_2\\) | 1200 Un |

| Demanda    | qty    |
| ---------- | ------ |
| \\(D\_1\\) | 800 Un |
| \\(D\_2\\) | 900 Un |
| \\(D\_3\\) | 500 Un |

1. Definimos los nodos de Transbordo $\\( T\_1 \ y\ T\_2 \\)$
2. Definimos en “Buffer” del sistema \\(B\_n\\) debe ser lo suficientemente grande para suplir el proceso

\\(B\_n = Oferta - Demanda\\)

3. procedemos a hacer la matriz de transbordo

|            | \\(T\_1\\) | \\(T\_2\\) | \\(D\_1\\) | \\(D\_2\\) | \\(D\_3\\) | Demanda |   |
| ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ------- | - |
| \\(P\_1\\) | 3          | 4          | M          | M          | M          | 1000    |   |
| \\(P\_2\\) | 2          | 5          | M          | M          | M          | 1200    |   |
| \\(T\_1\\) | 0          | 7          | 8          | 6          | M          | B       |   |
| \\(T\_2\\) | M          | 0          | M          | 4          | 9          | B       |   |
| \\(D\_1\\) | M          | M          | 0          | 5          | M          | B       |   |
| \\(D\_2\\) | M          | M          | M          | 0          | 3          | B       |   |
| Oferta     | B          | B          | 800 + B    | 900 + B    | 500        | -       |   |

### Almacenamiento en Bodegas o CEDIS[#](broken-reference)

#### Definiciones:[#](broken-reference)

**Almacenaje y Sistemas de Almacenamiento:**

1. _Almacenaje:_ Es el proceso de guardar y organizar productos o mercancías en un lugar específico, como un almacén o bodega.
2. _Sistemas de Almacenamiento:_ Se refiere a las estructuras y métodos utilizados para almacenar los productos de manera eficiente, como estanterías, paletas, racks, etc.

**Procedimiento de Control y Gestión de Almacenes:**

1. _Control:_ Implica supervisar y monitorear todas las actividades que se realizan dentro del almacén, desde la recepción de mercancías hasta su despacho.
2. _Gestión:_ Se enfoca en planificar, organizar y coordinar los recursos del almacén para optimizar su funcionamiento.

**Procedimiento de Despacho y Devoluciones:**

1. _Despacho:_ Es el proceso de preparar y enviar los productos a los clientes o a otros destinos.
2. _Devoluciones:_ Se refiere a la recepción de productos que son retornados por los clientes, ya sea por defectos, cambios o cancelaciones.

#### Sistemas de Almacenamiento en CEDIS[#](broken-reference)

Los sistemas de almacenamiento en los Centros de Distribución (CEDIS) son cruciales para una gestión eficiente del inventario y un flujo óptimo de productos. Existen diversos sistemas, cada uno con ventajas e inconvenientes según el tipo de producto, espacio disponible y nivel de automatización deseado. Algunos de los más comunes son:

1. Almacenamiento en bloque:

* La mercancía se apila directamente en el suelo, formando bloques compactos.
* Ideal para productos homogéneos y de alta rotación, que no requieren acceso individual.
* Bajo costo de implementación pero puede dificultar el acceso a productos específicos y generar pérdidas por aplastamiento.

2. Estanterías convencionales:

* Sistema versátil y ampliamente utilizado, con estanterías de diferentes alturas y configuraciones.
* Permite el acceso individual a cada paleta y facilita la organización del inventario.
* Costo moderado y adaptable a diferentes tipos de productos, pero puede limitar el uso del espacio vertical.

3. Estanterías compactas (Drive-in / Drive-through):

* Las carretillas elevadoras entran en las estanterías para depositar o retirar las paletas.
* Alta densidad de almacenamiento, ideal para productos con gran volumen y poca rotación.
* Mayor costo de implementación y requiere pasillos más anchos, limitando el número de referencias.

4. Estanterías dinámicas:

* Las paletas se deslizan por gravedad sobre rodillos, siguiendo el principio FIFO (First In, First Out).
* Ideal para productos perecederos o con fecha de caducidad.
* Asegura la rotación del inventario pero tiene un costo elevado y menor capacidad que otros sistemas.

5. Estanterías móviles:

* Se instalan sobre bases móviles que se desplazan sobre raíles, compactando el espacio.
* Optimiza el espacio disponible, ideal para almacenes con espacio limitado.
* Alto costo de implementación y requiere un sistema de control sofisticado.

6. Sistemas automatizados:

* Utilizan transelevadores, robots y sistemas de control para automatizar las operaciones de almacenamiento y recuperación.
* Alta eficiencia y precisión, ideal para grandes volúmenes y alta rotación.
* Requiere una inversión inicial considerable y personal especializado.

7. Carruseles horizontales y verticales:

* Sistemas rotativos que llevan los productos al operario.
* Ideal para piezas pequeñas y medianas, optimizando la preparación de pedidos.
* Costo elevado y capacidad limitada.

#### probelmas de que involucran CEDIS[#](broken-reference)

los problemas a los que nos enfrentamos en centros de distribucion varian segun la seccion donde estos se encuentre,

las partes basicas de un CEDI son:

1. ingreso de mercancia o compras:

en este caso veremos problemas de aprovisionamiento o inventario, donde tendremos que tomar desiciones de cuando, como y donde comprar, asi como en que momento ingresar material a la bodega con el fin de que no se presente cuellos de botella, es decir que la teoria de colas se aplica perfenctamente en esta seccion del CEDI:

* Teoría de Colas: Aplicable para modelar el tiempo de espera y la eficiencia en la recepción de mercancías. Puede optimizar la cantidad de servidores (personal o máquinas) y minimizar el tiempo de procesamiento.
* Optimización de Compras: Modelos de Programación Lineal para decidir qué y cuánto comprar, optimizando el costo en función de la demanda proyectada y la capacidad de almacenamiento.
* Modelos de Abastecimiento Justo a Tiempo (JIT): Reducción de inventarios, asegurando que los suministros lleguen justo cuando se necesitan.
* Sistemas de Almacenamiento ABC: Clasificación de los artículos en A, B y C según su importancia para optimizar el espacio de almacenamiento.
* Modelos de Previsión de la Demanda: Utilizados para anticipar las cantidades necesarias y asegurar un abastecimiento eficiente.

2. en terminos de control de inventario:

* Modelo EOQ (Economic Order Quantity): Programación no lineal para determinar el volumen de pedido óptimo que minimice los costos de pedido y almacenamiento.
* Modelos de Revisión Continua vs Revisión Periódica: Decisiones basadas en puntos de reorden o revisión fija en un intervalo de tiempo.
* Optimización de Niveles de Seguridad: Programación Lineal para calcular los niveles de inventario de seguridad que minimicen la probabilidad de rotura de stock.
* Modelo ABC de Inventarios: Optimización del control de inventarios según el valor y volumen de los artículos.
* Teoría de Juegos en Inventarios: Para prever comportamientos de la competencia y sus efectos sobre la demanda y el inventario.
* Modelos de Descuentos por Cantidad: Programación Lineal aplicada a inventarios para aprovechar economías de escala en las compras.

3. Despachos (Picking y Packing)

* Problema del Empleado de Almacén (Order Picking Problem): Programación Lineal para optimizar las rutas de picking y minimizar el tiempo total recorrido.
* Problema del Bin Packing: Optimización del empaquetado para maximizar el uso del espacio en los contenedores o camiones.
* Modelo de Transporte: Utilizado para minimizar los costos de distribución de los productos desde el centro de distribución a los puntos de destino.
* Optimización de Rutas (VRP - Vehicle Routing Problem): Aplicado en la distribución para optimizar las rutas de entrega, minimizando costos y tiempos de viaje.
* Sistemas de Picking por Zona y Onda: Programación para organizar el picking por zonas del almacén o por olas de pedidos para mejorar la eficiencia.
* Teoría de Cargas Complejas y Consolidación de Pedidos: Modelos de optimización que buscan maximizar la carga de los vehículos de despacho y consolidar pedidos en la menor cantidad de envíos.

cada uno de estos tiene un modelo apropiado que abordaremos mas adelante segun los contenidos actualizados del libro.

#### Modelos para solucionar los problemas de asignacion y transporte[#](broken-reference)

1. _**Asignacion:**_ El método de asignación es una técnica de optimización utilizada para resolver problemas de asignación, que son un caso especial de los problemas de transporte.

**Características:**[**#**](broken-reference)

1. Cada recurso debe ser asignado a una sola tarea.
2. Cada tarea debe ser asignada a un solo recurso.
3. El objetivo es encontrar la asignación óptima que minimice el costo total o maximice el beneficio.

**Pasos del método de asignación:**[**#**](broken-reference)

1. Crear una matriz de costos: Las filas representan los recursos y las columnas representan las tareas. Cada celda contiene el costo de asignar un recurso específico a una tarea específica.
2. Reducir la matriz de costos: Restar el elemento más pequeño de cada fila a todos los elementos de esa fila. Restar el elemento más pequeño de cada columna a todos los elementos de esa columna.
3. Dibujar líneas para cubrir todos los ceros: Se busca cubrir todos los ceros de la matriz con el menor número de líneas horizontales o verticales.
4. Optimizar la asignación: Si el número de líneas es igual al número de filas o columnas, se ha encontrado la solución óptima. Si el número de líneas es menor, se debe
5. realizar una iteración: Encontrar el elemento más pequeño no cubierto por las líneas. Restar este elemento a todos los elementos no cubiertos. Sumar este elemento a todos los elementos cubiertos por dos líneas. Volver al paso 3.
6. Asignar recursos a tareas: Una vez que se ha encontrado la solución óptima, se asignan los recursos a las tareas correspondientes a los ceros en la matriz de costos.

ejemplos de asigancion:

1. El problema consiste en asignar un conjunto de vendedores a un conjunto de rutas, de forma que se minimicen los costos totales asociados con cada asignación, dado que cada vendedor tiene un costo distinto para cada ruta.

tenemos

vendedores: \\(V\_1\\),\\(V\_2\\)y\\(V\_3\\)\
Rutas = \\(R\_1\\), \\(R\_2\\) y \\(R\_3\\) \\

El objetivo es asignar cada vendedor a una ruta de tal manera que se minimicen los costos de asignación. Los costos de asignación están dados en la siguiente tabla:

|            | \\(R\_1\\) | \\(R\_2\\) | \\(R\_3\\) |
| ---------- | ---------- | ---------- | ---------- |
| \\(V\_1\\) | 12         | 15         | 17         |
| \\(V\_2\\) | 10         | 9          | 8          |
| \\(V\_3\\) | 14         | 13         | 11         |

* definimos las Variables

\\(X\_{ij}\\) =. sera la variable de tipo binaria que decidira que vendedor se asigna a cada ruta.

\\(X\_{ij}=\\) \begin{bmatrix} 1 & \text{si el vendedor \\(i\\) es asignado a la ruta \\(j\\)} \ 0 & \text{en caso contrario} \end{bmatrix}

|            | \\(R\_1\\)    | \\(R\_2\\)    | \\(R\_3\\)    |
| ---------- | ------------- | ------------- | ------------- |
| \\(V\_1\\) | \\(X\_{11}\\) | \\(X\_{12}\\) | \\(X\_{13}\\) |
| \\(V\_2\\) | \\(X\_{21}\\) | \\(X\_{22}\\) | \\(X\_{23}\\) |
| \\(V\_3\\) | \\(X\_{31}\\) | \\(X\_{32}\\) | \\(X\_{33}\\) |

* funcion objetivo:

con esta informacion pordemos armar la F.O

\\\[ Z\_{Min}=\sum\_{i}^{n} X\_{ij}\*C\_{ij}\forall i;j \\]

las restricciones, cada vendedor debe ser asigando a una sola ruta y acada ruta un solo vendedor, por esta razon las restricciones seran iguales a 1

\\\[\begin{split} 1.\ X\_{11}+X\_{12}+X\_{13}=1 \\\ 2.\ X\_{21}+X\_{22}+X\_{23}=1 \\\ 3.\ X\_{31}+X\_{32}+X\_{33}=1 \\\ \end{split}\\]

\\\[\begin{split} 1.\ X\_{11}+X\_{21}+X\_{31}=1 \\\ 2.\ X\_{12}+X\_{22}+X\_{32}=1 \\\ 3.\ X\_{13}+X\_{23}+X\_{33}=1 \\\ \end{split}\\]

* todas las varibales deben ser binarias

\\(X\_{ij} \in\left(0,1\right)\\)

***

### Modelo de redes[#](broken-reference)

***

Definicion de redes: las redes son una serie de nodos localizados y enlazados con arcos la notacion para la descripcion de la red es

\\

\\\[\begin{split} (N,A); \\\ donde: \\\ N = Conjunto\ de\ Nodos \\\ A = Conjunto\ de\ Arcos \end{split}\\]

Por ejmplo:

\\\[\begin{split} N = \\{1,2,3,4,5\\} \\\ A = \\{(1,2),(1,3),(2,3),(2,5),(3,4),(3,5),(4,2),(4,5)\\} \end{split}\\]

```
import networkx as nx
import matplotlib.pyplot as plt

G = nx.Graph()
G.add_nodes_from([1, 2, 3, 4, 5])

A = [(1,2),(1,3),(2,3),(2,5),(3,4),(3,5),(4,2),(4,5)]
G.add_edges_from(A)

labels = {1: 'A', 2: 'B', 3: 'C', 4: 'D', 5: 'E'}

pos = nx.spring_layout(G, seed=42)
nx.draw_networkx_nodes(G, pos=pos)
nx.draw_networkx_edges(G, pos=pos)
nx.draw_networkx_labels(G, pos=pos, labels=labels)

plt.show()
```

con cada una de las redes asociadas, se describira algun tipo de flujo, trafico, procesos etc(..) de denomina **arco dirigido u orientado** si permite el flujo positivo y flujo cero en la direccion opuesta.

la **ruta** es la sucesion de arcos distintos que une dos nodos pasando por otros nodos, independientemente de la direcion del flujo de cada arco una **red dirigida** tiene todos sus arcos dirigidos. una ruta forma un **ciclo** si conecta un nodo con sigo mismo, pasando por otros nodos

una **red conectada** es quella en que cada dos nodos distintos estan enlazados almenos con una ruta un **arbol** es una red conectada que puede ser facilmente la red conectada de todos los nodos, donde, no se permiten ciclos un **arbol de expansion** es un arbol que enlaza todos los nodosde la red tambien sin permitir ciclos.

***

Ejercicios:

***

1. grafique a mano y en colab el siguiente modelo \\

\\( 1.1). \\\ N=\\{1,2,3,4,5\\} \\\ A=\\{(1,2),(2,5),(1,3),(3,4),(3,5),(5,1),(4,2)\\} \\)

\\

\\( 1.2). \\\ N=\\{1,2,3,4\\} \\\ A=\\{(1,3),(1,2),(2,3),(2,4),(3,4)\\} \\\ \\)

```
  1. determine:
    - una ruta
    - un ciclo
    - un cilo dirigido
    - un árbol
    - Un árbol de expansion.
```

2. Determine los conjuntos Conjuntos \\(N\\) y \\(A\\) en las redes
3. Trace la Red definida por \\( N=\\{1,2,3,4,5\\} \\\ A=\\{(1,2),(1,5),(2,3)(2,4),(3,5),(3,4),(4,3),(4,6),(5,2),(5,6)\\} \\)
4. se debe transportar en un vehiculo tres productos desde la tienda ABC hasta la cada de doña pepita, para hacer el domicilio que esta solicito a la tienda, pero el domiciliario y su vehiculo no puede trasportar mas de dos elementos a la vez, el domiciliario puede pedir ayuda de sus compañeros, ya que por el tamaño del producto no puede caragar mas de uno a la vez, el maximo de personas incluido el domicialiario es de tres personas, no es recomendable que tengan mas productos que personas en el carro.

* formule el modelo de red para diseñar los viajes del vehiculo de modo que se asegure el domicilo a la casa de doña pepita.

***

### Altogoritmo de Arbol de expansion Minima[#](broken-reference)

***

El altogirtmo de expansion minima enlaza los nodos de una red, en forma directa o indirecta, con la minima longitud posible, de las _ramas_ enlazantes. el uso posible de este altogirtmo es en el diseño de carreteras o rutas entre nodos que unen varias poblaciones. siendo que la ruta diseñada puede pasar entro otras poblaciones o nodos

* el diseño mas economico del sistema sera aquel que minimice la distancia total de caminos creados.

_otra definicion:_ Un árbol de expansión mínimo es un tipo especial de árbol que minimiza las longitudes (o dinero) de los bordes del árbol. Un ejemplo es una compañía de cable que quiere tender línea a múltiples vecindarios; al minimizar la cantidad de cable tendido, la compañía de cable ahorrará dinero.

procedimiento:

\\( Sea\ N=\\{1,2,...n\\}, en\ conjunto\ de \ nodos\ en\ la\ Red. \\\ C\_k=Conjunto\ de\ nodos\ que\ se\ han\ Conectado\ en \ forma\ permanente\ en\ la\ iteracion\ K \\\ \bar{C\_k} = Conjunto\ de\ nodos\ que\ faltan\ por\ conectar. \\)

**Paso Cero:** El conjunto: $\\( C\_0=𝛳\ y \\\ \bar{C\_0} =N \\)$

1. Comenzar con cualquier nodo en el conjunto \\(\bar{C\_0}\\) no conectado e igualas a \\(C\_1=\\{i\\}\\), con lo qie \\(\bar{C\_1}=N-\\{i\\}\\), igualar a \\(K=2\\)
2. **paso general \\(K\ \\)** selecciona un nodo \\(j\\) en el conjunto no conectado \\(\bar{C\_{k-1\}}\\) que produzca el arco mas corto a un nodo, en el conjunto conectado a \\(C\_{k-1}\\) enlazando \\(j\\) en forma permanente con \\(C\_{k-1}\\) y sacarlo de \\(\bar{C\_{k-1\\)\}}$

\\

\\\[ C\_k=C\_{k-1}+\\{j\\}, C\_k = \bar{C\_{k-1\}}-\\{j\\} \\]

\\

* donde los \\(\bar{C\_{k\}}\\) es igual a 0 o vacío, detenerse, o por el contrario igualar \\(K=k+1\\) y repertir el proceso.

***

teniendo el siguiente cuadro:

|       | A | B | C | D | E |
| ----- | - | - | - | - | - |
| **A** | 0 | 1 | 4 | 6 | 2 |
| **B** | 1 | 0 | 2 | - | 2 |
| **C** | 4 | 2 | 0 | 5 | 2 |
| **D** | 6 | - | 5 | 0 | 4 |
| **E** | 2 | 2 | 2 | 4 | 0 |

utilice el altgoritmo de Prim y el de Kruskal y compare

***

#### Modelo Teórico según el Algoritmo de Prim:[#](broken-reference)

Inicialización: Selecciona un nodo arbitrario como raíz del árbol. _Construcción paso a paso:_

1. En cada paso, se agrega la arista más corta que conecta un nodo dentro del árbol con uno fuera del árbol.
2. Selecciona el nodo más cercano al árbol actual y agrega la arista que conecta ese nodo con el árbol.
3. Terminación: Repetir el paso 2 hasta que todos los nodos estén incluidos en el árbol.

#### Modelo Teórico según el Altgoritmo de Kruskal:[#](broken-reference)

Ordenación de aristas: Ordena todas las aristas en orden no decreciente de peso. _Construcción paso a paso:_

1. En cada paso, selecciona la arista más corta que no forme un ciclo con las aristas ya seleccionadas.
2. Agrega esta arista al árbol de expansión mínima.

Terminación: Repetir el paso 2 hasta que se hayan seleccionado \\(n-1\\) aristas donde \\(n\\) es el numero de nodos en el sistema

```
#usaremos en Altgoritmo de PRIMM
import numpy as np

def prim_mst(distancias):
    num_nodos = len(distancias)
    # Inicializar el MST y la lista de nodos visitados
    mst = []
    visitado = [False] * num_nodos
    # Empezar desde el nodo 0
    visitado[0] = True
    # Repetir hasta que todos los nodos estén visitados
    while len(mst) < num_nodos - 1:
        # Encontrar la arista más corta que conecta un nodo visitado con uno no visitado
        min_distancia = float('inf')
        min_i, min_j = None, None
        for i in range(num_nodos):
            if visitado[i]:
                for j in range(num_nodos):
                    if not visitado[j] and distancias[i][j] < min_distancia:
                        min_distancia = distancias[i][j]
                        min_i, min_j = i, j
        # Agregar la arista al MST
        mst.append((min_i, min_j))
        visitado[min_j] = True
    return mst

# Definir la matriz de distancias
distancias = [
    [0, 1, 4, 6, 2],
    [1, 0, 2, float('inf'), 2],
    [4, 2, 0, 5, 2],
    [6, float('inf'), 5, 0, 4],
    [2, 2, 2, 4, 0]
]

# Letras correspondientes a los nodos
nodos_letras = ['A', 'B', 'C', 'D', 'E']

# Ejecutar el algoritmo de Prim
arbol_expansion_minima = prim_mst(distancias)

# Imprimir el MST resultante
print("Árbol de Expansión Mínima:")
for arista in arbol_expansion_minima:
    print(f"Arista: {nodos_letras[arista[0]]} - {nodos_letras[arista[1]]}")
```

```
# Altgoritmo de Kruskal
class UnionFind:
    def __init__(self, n):
        self.parent = list(range(n))
        self.rank = [0] * n

    def find(self, x):
        if self.parent[x] != x:
            self.parent[x] = self.find(self.parent[x])
        return self.parent[x]

    def union(self, x, y):
        root_x = self.find(x)
        root_y = self.find(y)
        if root_x != root_y:
            if self.rank[root_x] < self.rank[root_y]:
                self.parent[root_x] = root_y
            elif self.rank[root_x] > self.rank[root_y]:
                self.parent[root_y] = root_x
            else:
                self.parent[root_y] = root_x
                self.rank[root_x] += 1

def kruskal_mst(distancias, nodos_letras):
    num_nodos = len(distancias)
    aristas = []
    # Construir una lista de aristas (i, j, peso)
    for i in range(num_nodos):
        for j in range(i + 1, num_nodos):
            peso = distancias[i][j]
            aristas.append((i, j, peso))
    # Ordenar las aristas por peso
    aristas.sort(key=lambda x: x[2])
    # Inicializar el MST y el Union-Find
    mst = []
    uf = UnionFind(num_nodos)
    # Construir el MST
    for arista in aristas:
        u, v, peso = arista
        if uf.find(u) != uf.find(v):
            mst.append((u, v))
            uf.union(u, v)
    return mst

# Definir la matriz de distancias
distancias = [
    [0, 1, 4, 6, 2],
    [1, 0, 2, float('inf'), 2],
    [4, 2, 0, 5, 2],
    [6, float('inf'), 5, 0, 4],
    [2, 2, 2, 4, 0]
]

# Letras correspondientes a los nodos
nodos_letras = ['A', 'B', 'C', 'D', 'E']

# Ejecutar el algoritmo de Kruskal
arbol_expansion_minima_kruskal = kruskal_mst(distancias, nodos_letras)

# Imprimir el MST resultante
print("Árbol de Expansión Mínima (Kruskal):")
for arista in arbol_expansion_minima_kruskal:
    print(f"Arista: {nodos_letras[arista[0]]} - {nodos_letras[arista[1]]}")
```

los algoritmos de árbol de expansión mínima, como Prim y Kruskal, tienen una amplia gama de aplicaciones en diferentes campos, como por ejemplo:

1. Redes de Distribución: Planificación de redes de distribución de electricidad, agua, gas, etc.
2. Telecomunicaciones: Diseño de redes de telecomunicaciones para interconectar estaciones base, torres de telefonía, etc.
3. Logística: Optimización de rutas en redes de transporte, como carreteras, ferrocarriles y rutas de envío.
4. Cableado de Computadoras: Diseño de redes de computadoras y cableado para conectar dispositivos en una red local.
5. Construcción de Infraestructura: Planificación de la construcción de carreteras, puentes y otras infraestructuras civiles.
6. Diseño de Circuitos Electrónicos: Diseño de circuitos impresos y conexiones entre componentes electrónicos en placas de circuito.
7. Análisis de Redes Sociales: Identificación de conexiones importantes y relaciones en redes sociales y de colaboración.
8. Biología Molecular: Análisis de interacciones entre proteínas en biología molecular y diseño de rutas metabólicas.
9. Exploración de Recursos Naturales: Planificación de rutas para la exploración y extracción de recursos naturales, como petróleo y minerales.
10. Diseño de Sistemas de Riego: Planificación de sistemas de riego para agricultura y jardinería.

Ejercicio uno:

***

la empresa ABC porvee un servicio de iluminacion a cinco nuevas areas pobladas por proyectos de costruccion, los nodos estan dados por la siguiente red:

\\\[\begin{split} N=\\{1,2,3,4,5\\} \\\ A=\\{(1,2),(1,4),(2,3),(3,4),(1,3),(1,5),(3,6),(4,6),(2,5)\\} \end{split}\\]

\
valores (x10 km)

|   | 1 | 2 | 3 | 4 | 5 | 6  |
| - | - | - | - | - | - | -- |
| 1 | 0 | 1 | 5 | 7 | 9 | -  |
| 2 | 1 | 0 | 6 | - | 3 | -  |
| 3 | - | - | 0 | 5 | - | 10 |
| 4 | - | - | - | 0 | 8 | 3  |
| 5 | - | - | - | - | 0 | -  |
| 6 | - | - | - | - | - | 0  |

***

### Unidad Cuatro: Modelos de Localizacion[#](broken-reference)

***

### Definicion de modelos de localizacion[#](broken-reference)

1. **Modelo de localización de planta:** Este modelo se utiliza para determinar la ubicación óptima de una nueva planta o instalación, teniendo en cuenta factores como la disponibilidad de recursos, la proximidad a los proveedores y los clientes, y los costos de transporte.
2. **Modelo de asignación de instalaciones:** Este modelo se utiliza para determinar la mejor manera de asignar las instalaciones existentes a las diferentes demandas, teniendo en cuenta factores como la capacidad, la disponibilidad de recursos y los costos de transporte.
3. **Modelo de ubicación de almacenes:** Este modelo se utiliza para determinar la ubicación óptima de los almacenes, teniendo en cuenta factores como la demanda, la proximidad a los clientes, los costos de transporte y los costos de mantenimiento del almacén.
4. **Modelo de rutas de distribución:** Este modelo se utiliza para optimizar la ruta de distribución de los productos, teniendo en cuenta factores como la demanda, la ubicación de los clientes, los costos de transporte y la capacidad de los vehículos.

### localización de planta[#](broken-reference)

Según la siguiente tabla de distancias debemos ubicar nuestro CDA (centro de Distribución), mayorista, las demás locaciones son posibles ubicaciones para distribuidores menores también propios.

1. Ubicar el distribuidor mayorista de tal forma que las distancias entre puntos sean lo más cortas posible. (justifique su respuesta) una vez ubicado el mayorista ubique
2. distribuidores menores de tal forma que cubramos la mayoría de las demandas PROMEDIO del año.
3. Evalúe las posibilidades y justifique su respuesta

\ valores (x10 km)

|   | A | B  | C  | D  | E  | F  | G  |
| - | - | -- | -- | -- | -- | -- | -- |
| A | - | 20 | -  | 30 | -  | 80 | -  |
| B | - | 0  | 10 | -  | 10 | -  | -  |
| C | - | -  | 0  | 5  | 5  | -  | -  |
| D | - | -  | -  | 0  | 5  | -  | -  |
| E | - | -  | -  | -  | 0  | 20 | 15 |
| F | - | -  | -  | -  | -  | 0  | 10 |
| G | - | -  | -  | -  | -  | -  | 0  |

|   | Población de clientes | valor m2 |
| - | --------------------- | -------- |
| A | 450                   | 1,2      |
| B | 190                   | 1,3      |
| C | 200                   | 1,2      |
| D | 250                   | 1,6      |
| E | 300                   | 1,6      |
| F | 380                   | 1,8      |
| G | 150                   | 1,1      |

### Metodo grafico de localizacion[#](broken-reference)

El método gráfico de localización de plantas es una técnica utilizada para seleccionar la ubicación óptima de una nueva planta o instalación. El proceso implica el uso de un mapa de la zona para identificar los factores críticos que influyen en la selección de la ubicación, como la disponibilidad de materias primas, la proximidad al mercado, la disponibilidad de mano de obra y la infraestructura existente.

1. Identificación de los factores críticos: El primer paso es identificar los factores críticos que influyen en la ubicación de la planta. Estos factores pueden variar según el tipo de planta y la industria. Por ejemplo, una planta de procesamiento de alimentos puede requerir una ubicación cerca de los campos de cultivo, mientras que una planta de fabricación de alta tecnología puede requerir una ubicación cerca de los centros de investigación y desarrollo.
2. Creación del mapa: Una vez que se han identificado los factores críticos, se crea un mapa de la zona que incluye información detallada sobre la ubicación de estos factores. El mapa también puede incluir información sobre la topografía, las vías de acceso, la disponibilidad de energía y agua, y otros aspectos relevantes.
3. Asignación de pesos a los factores críticos: Una vez que se ha creado el mapa, se asigna un peso a cada uno de los factores críticos en función de su importancia relativa. Esto permite que se le dé una mayor importancia a los factores más críticos en el proceso de toma de decisiones.
4. Análisis de las ubicaciones potenciales: Se identifican las posibles ubicaciones para la nueva planta o instalación y se evalúan en función de los factores críticos y sus respectivos pesos. Se pueden utilizar diferentes métodos para hacer esto, como análisis multicriterio o análisis de distancia.
5. Selección de la ubicación óptima: Finalmente, se selecciona la ubicación óptima en función de los resultados del análisis y se procede a la planificación y construcción de la planta.

#### Ejercicios propuestos:[#](broken-reference)

**Grapich model**[**#**](broken-reference)

| Ciudad     | Costos fijos (M) | Costos Variables |
| ---------- | ---------------- | ---------------- |
| New York   | 150.000.000      | 777.130          |
| Washington | 230.000.000      | 798.090          |
| Bogotá     | 180.000.000      | 573.000          |
| Quito      | 130.000.000      | 630.270          |

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
