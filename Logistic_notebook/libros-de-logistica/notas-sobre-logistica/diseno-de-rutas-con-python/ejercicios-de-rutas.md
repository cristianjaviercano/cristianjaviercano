# Ejercicios de Rutas

### Ejercicio sobre Ruteo utilizando TSP (Problema del Viajero)

**Descripción del problema:**

### Problema del Viajante

El problema del viajante, también conocido como el problema del vendedor viajero, es un desafío clásico en la optimización combinatoria. Consiste en encontrar el recorrido más corto posible que permita a un viajero visitar una serie de ciudades dispuestas en un grafo completo, de modo que cada ciudad sea visitada exactamente una vez antes de regresar al punto de partida.

#### Descripción del Problema

Dado un conjunto de ciudades y las distancias entre cada par de ellas, se busca una secuencia de visitas que minimice la distancia total recorrida. Este problema se puede visualizar como un circuito hamiltoniano en un grafo ponderado y requiere que el recorrido cumpla con las siguientes condiciones:

1. **Recorrido Único:**\
   Cada ciudad debe ser visitada exactamente una vez.
2. **Circuito Cerrado:**\
   El recorrido debe comenzar y terminar en la misma ciudad de origen.
3. **Minimización de Distancia:**\
   La suma total de las distancias entre las ciudades visitadas debe ser la menor posible.

#### Ejemplo

Supongamos que tenemos cinco ciudades: A, B, C, D y E. La tarea es encontrar el recorrido que cubra todas las ciudades y vuelva a la ciudad inicial A, de manera que la suma de las distancias entre las ciudades sea mínima.

#### Métodos de Solución

Algunos métodos para resolver el problema del viajante incluyen:

* **Fuerza Bruta:** Evalúa todas las posibles rutas y selecciona la de menor distancia. Es práctico para un pequeño número de ciudades debido a su complejidad factorial.
* **Algoritmos Aproximados:** Como la búsqueda de colonia de hormigas, algoritmos genéticos o el algoritmo de recocido simulado, ofrecen soluciones cercanas al óptimo en un tiempo razonable para conjuntos mayores de ciudades.
* **Programación Dinámica:** Utiliza el algoritmo de Held-Karp, que tiene una complejidad temporal de 2^n \* n^2, siendo más eficiente que la fuerza bruta, aunque aún exponencial.

#### Ejercicio Práctico: Resolviendo el Problema del Viajante con PuLP

En este ejercicio, los estudiantes utilizarán la biblioteca PuLP en Python para resolver el problema del viajante (TSP). A través de este ejercicio, los estudiantes modelarán y resolverán el problema utilizando programación lineal entera para encontrar el recorrido óptimo.

**Instrucciones**

1.  **Introducción al Problema:**

    Imagina que eres un vendedor que debe visitar las siguientes ciudades: Ciudad1, Ciudad2, Ciudad3, Ciudad4 y Ciudad5. El objetivo es determinar la ruta que minimiza la distancia total recorrida al visitar cada ciudad exactamente una vez antes de regresar a la ciudad inicial.

**Ejemplo de Código**

```python
import pulp

# Definición de las ciudades y la matriz de distancias
ciudades = ['Ciudad1', 'Ciudad2', 'Ciudad3', 'Ciudad4', 'Ciudad5']
distancias = {('Ciudad1', 'Ciudad2'): 10, ('Ciudad1', 'Ciudad3'): 15, ...}

# Definir el problema
problema = pulp.LpProblem("TSP", pulp.LpMinimize)

# Variables de decisión
x = pulp.LpVariable.dicts('ruta', distancias, cat='Binary')

# Función objetivo
problema += pulp.lpSum([distancias[i] * x[i] for i in distancias])

# Restricciones
...

# Resolviendo el problema
problema.solve()

# Resultado
print(f"Estado del solucionador: {pulp.LpStatus[problema.status]}")
print("Recorrido óptimo:")
for i in distancias:
    if pulp.value(x[i]) == 1:
        print(f"Viajar de {i[0]} a {i[1]}")

print(f"Distancia total: {pulp.value(problema.objective)}")
```

**Completa el código implementando las restricciones y comparte tus resultados. Este ejercicio te brindará experiencia práctica en optimización combinatoria y su aplicación con herramientas computacionales.**

***

{% hint style="info" %}
#### Consejos para Implementar las Restricciones
{% endhint %}

**Restricción de Entrada y Salida:**\
Cada ciudad debe tener exactamente una entrada y una salida. Para ello, asegúrate de que en cada ciudad, la suma de las rutas que entran y las que salen sea igual a 1.

### Ejercicio de Rutas en un CEDI

{% hint style="info" %}
#### ¿Qué es un CEDI?

Un Centro de Distribución, conocido como CEDI, es una instalación logística empleada por las empresas para la recepción, almacenamiento, gestión y distribución de productos. Su principal función es optimizar el flujo de mercancías desde el proveedor hasta el cliente final, asegurando la eficiencia en la cadena de suministro.
{% endhint %}

#### Contextualización para Empresas CRC

En el contexto de Empresas CRC, se plantea un ejercicio de ruteo para un CEDI que maneja un único tipo de producto. La empresa dispone de tres montacargas que facilitan el movimiento de mercancía entre diferentes áreas funcionales, tales como recepción, inspección, almacenamiento, y despacho.

El objetivo de este ejercicio es determinar el tiempo de servicio o el tiempo promedio de atención dentro del CEDI. Este análisis ayudará a Empresas CRC en la optimización de procesos y recursos, mejorando su eficiencia operativa a través de una modelación precisa en Excel del layout y operaciones internas del CEDI.

El CEDI contará con las siguientes áreas y características:

1. **Producto:** Un único tipo de producto.
2. **Montacargas:** Tres montacargas.
3. **Áreas Funcionales:**
   1. **Área de Recepción de Mercancías (ARM):** Ubicación donde se recibe el producto.
   2. **Área de Inspección (AI):** Zona para la verificación de la calidad y cantidad del producto.
   3. **Área de Parqueo de Montacargas (APM):** Espacio designado para el estacionamiento y recarga de los montacargas.
   4. **Área de Despacho (AD):** Punto de salida de los productos terminados o pedidos.
   5. **Área de Almacenamiento (AA):** Zona destinada a las estanterías para el almacenamiento del producto.
4. **Estanterías:**
   * Seis estanterías en total.
   * Cada estantería tendrá 12 torres.
   * Cada torre tendrá 3 niveles.
   * **Identificación de Coordenadas:** Las ubicaciones de las estanterías serán identificadas mediante coordenadas (x,y,z).

#### II. Requerimientos del Estudiante

El estudiante deberá abordar las siguientes tareas:

**1. Modelado de la Bodega en Excel y Determinación de Coordenadas**

El primer paso es construir un modelo de la bodega en una hoja de cálculo (Excel) para determinar las coordenadas de cada área y de cada ubicación de almacenamiento.

* **Coordenadas Generales:** Todas las áreas (ARM, AI, APM, AD) tendrán una coordenada z=1 metro, asumiendo que sus operaciones se realizan a nivel de suelo.
* **Coordenadas de Almacenamiento:** Para las ubicaciones dentro del Área de Almacenamiento (AA), las coordenadas (x,y) serán las mismas para una torre dada, y la coordenada z variará según el nivel:
  * Nivel 1: z=1 metro.
  * Nivel 2: z=2 metros.
  * Nivel 3: z=3 metros.
  * Se asume que cada unidad de cambio en z representa 1 metro.

**2. Matriz de Rutas Posibles, Tiempos y Distancias**

Una vez definidas todas las coordenadas, el estudiante deberá construir una matriz de distancias y tiempos entre todas las ubicaciones relevantes del CEDI.

* **Distancia Euclidiana:** Se puede utilizar la distancia euclidiana tridimensional para calcular la distancia entre dos puntos (x1​,y1​,z1​) y (x2​,y2​,z2​): d=(x2​−x1​)2+(y2​−y1​)2+(z2​−z1​)2​
* **Velocidad Promedio del Montacargas:** Se asume una velocidad promedio de movimiento de los montacargas de 10 metros por segundo.
* **Cálculo del Tiempo:** El tiempo de recorrido entre dos puntos se calculará como: t=Velocidad promedio del montacargasd​
* **Matriz de Rutas:** Se generará una matriz M donde Mij​ represente el tiempo o la distancia de recorrido desde la ubicación i hasta la ubicación j.

**3. Simulación de la Demanda y Generación del Archivo CSV**

Se simulará la demanda de pedidos y la ubicación de los elementos en la bodega, asumiendo que la bodega está inicialmente llena.

* **Pedidos Iniciales:** La cantidad de pedidos por simulación debe ser aleatoria, en un rango de 1 a 5.
* **Elementos por Pedido:** Cada pedido contendrá un número aleatorio de elementos, entre 5 y 20.
* **Localización de Elementos:** Cada elemento en un pedido deberá ser "localizado" en una coordenada específica dentro del Área de Almacenamiento (AA). Es decir, se asumirá que estos elementos deben ser extraídos de estas coordenadas.
* **Generación de Archivo CSV:** La demanda simulada (pedidos, elementos y sus coordenadas de origen) deberá ser exportada a un archivo `.csv`. Este archivo servirá como insumo para el modelo de ruteo de vehículos (VRP).

**4. Planteamiento del Problema de Ruteo de Vehículos con Capacidades (VRPC)**

El estudiante deberá plantear un modelo de VRPC que utilice el archivo `.csv` generado como entrada.

* **Objetivo:** Minimizar el tiempo total de recorrido de los montacargas para satisfacer los pedidos.
* **Variables de Decisión:**
  * Variables binarias que indiquen si un montacargas visita una ubicación.
  * Variables binarias que indiquen si se toma una ruta entre dos ubicaciones.
* **Restricciones:**
  * Cada pedido debe ser atendido.
  * Los montacargas tienen una capacidad limitada (por ejemplo, en número de elementos o volumen, lo cual el estudiante deberá definir).
  * Los montacargas inician y terminan su ruta en el Área de Parqueo de Montacargas (APM).
  * Cada montacargas no puede exceder su tiempo máximo de operación.
  * Las restricciones de continuidad de las rutas.
*   **Formulación Teórica del VRPC (Ejemplo):** Sea V el conjunto de nodos (ubicaciones), K el conjunto de montacargas, cij​ el costo (tiempo o distancia) de ir del nodo i al nodo j, qi​ la demanda del nodo i, y Qk​ la capacidad del montacargas k. Variables de decisión:

    * xijk​∈{0,1}: 1 si el montacargas k viaja del nodo i al nodo j, 0 en caso contrario.
    * uik​: Posición del nodo i en la ruta del montacargas k (para evitar subrutas).

    Objetivo: Minimizar i∈V∑​j∈V∑​k∈K∑​cij​xijk​

    Sujeto a:

    1. Cada cliente (elemento de pedido) debe ser visitado exactamente una vez por un montacargas: j∈V,j=i∑​k∈K∑​xijk​=1∀i∈V∖{0} (donde 0 es el depósito/APM)
    2. Conservación del flujo para cada montacargas: j∈V,j=i∑​xijk​−j∈V,j=i∑​xjik​=0∀i∈V,∀k∈K
    3. Restricción de capacidad para cada montacargas: i∈V∖{0}∑​qi​j∈V,j=i∑​xijk​≤Qk​∀k∈K
    4. Subtour elimination (Miller-Tucker-Zemlin o similar): uik​−ujk​+Nxijk​≤N−1∀i,j∈V∖{0},i=j,∀k∈K
    5. Los montacargas parten del depósito: j∈V∖{0}∑​x0jk​=1∀k∈K
    6. Los montacargas regresan al depósito: i∈V∖{0}∑​xi0k​=1∀k∈K
    7. Dominio de las variables: xijk​∈{0,1}∀i,j∈V,∀k∈K

    El estudiante deberá especificar las consideraciones adicionales para este problema particular, como la capacidad de los montacargas en términos de número de elementos que pueden transportar por viaje, y la definición clara del "depósito" para los montacargas (APM).

#### III. Entregables

El estudiante deberá entregar un informe en formato PDF que contenga:

* Explicación detallada de cada paso realizado.
* Diagrama o representación de la bodega y sus coordenadas.
* La matriz de distancias y tiempos.
* La lógica de la simulación de la demanda.
* El planteamiento teórico y algebraico del modelo VRPC, incluyendo todas las suposiciones y consideraciones adicionales.
* Análisis de los resultados obtenidos (si se llega a implementar la solución del VRPC).

Además, se debe adjuntar el código completo desarrollado en Python utilizando Jupyter Notebook o Google Colab. El código debe incluir:

* Generación de coordenadas y la matriz de distancias/tiempos.
* Simulación de la demanda y exportación al archivo `.csv`.
* La implementación del modelo VRPC utilizando una librería de optimización (ej. `PuLP`, `GurobiPy`, `OR-Tools`).

#### Consideraciones Adicionales para el Diseño del Problema

* **Layout de la Bodega:** Para el modelado en Excel, se puede asumir un layout rectangular o cuadriculado para la bodega, lo que facilita la asignación de coordenadas.
* **Capacidad de los Montacargas:** Se debe especificar la capacidad de los montacargas. Por ejemplo, un montacargas puede transportar un máximo de X elementos por viaje.
* **Estrategia de Recogida:** Se asumirá una estrategia de recogida individual por elemento, es decir, cada elemento tiene una ubicación específica que debe ser visitada.
* **Tiempo de Carga/Descarga:** Para simplificar el modelo inicial, se puede asumir un tiempo de carga/descarga constante por elemento o por pedido, o ignorarlo en una primera aproximación. El estudiante puede decidir si incluirlo.
* **Horarios de Operación:** Se puede establecer un horario de operación para el CEDI y los montacargas para incluir en las restricciones de tiempo.
* **Tráfico/Congestión:** Para este nivel inicial, se puede omitir la consideración de congestión en los pasillos o áreas, asumiendo movimientos fluidos. Si se desea complejizar, se podría introducir penalizaciones.

Este diseño proporciona un marco robusto para que el estudiante aplique conceptos de diseño de instalaciones, modelado de sistemas logísticos y optimización en un entorno práctico.

#### Referencias

* Laporte, G. (1992). The vehicle routing problem: An overview of exact and approximate algorithms. _European Journal of Operational Research_, _59_(2), 345-358.
* Toth, P., & Vigo, D. (2014). _Vehicle Routing: Problems, Methods, and Applications_. Society for Industrial and Applied Mathematics.
* Chopra, S., & Meindl, P. (2019). _Supply Chain Management: Strategy, Planning, and Operation_ (7th ed.). Pearson.
