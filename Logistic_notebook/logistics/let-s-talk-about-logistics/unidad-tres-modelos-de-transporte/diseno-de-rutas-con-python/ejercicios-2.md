# TSP problem

#### Traveling Salesman Problem (TSP)

The Traveling Salesman Problem (TSP) is a classic optimization problem focused on finding the shortest possible route for a traveler to visit a set of cities and return to the origin city. The key characteristics of TSP include:

1. **Unique Tour:**\
   Each city must be visited exactly once.

TSP is commonly used in logistics, manufacturing, and transportation to optimize travel routes and reduce costs.

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

#### Referencias para mayor información.

* Laporte, G. (1992). The vehicle routing problem: An overview of exact and approximate algorithms. _European Journal of Operational Research_, _59_(2), 345-358.
* Toth, P., & Vigo, D. (2014). _Vehicle Routing: Problems, Methods, and Applications_. Society for Industrial and Applied Mathematics.
* Chopra, S., & Meindl, P. (2019). _Supply Chain Management: Strategy, Planning, and Operation_ (7th ed.). Pearson.

#### Ejercicios Varios

3. En **el ejemplo 1**, suponer que la capacidad de la planta de Detroit es 1300 automóviles (en lugar de 1500). La oferta total (3700 autos) es menor que la demanda total (4300 autos), lo que quiere decir que no será satisfecha parte de la demanda en Denver y Miami. Como la demanda es mayor que la oferta se agrega una fuente _(planta) ficticia_ con una capacidad de 200 automóviles ( 3700  3500) para **balancear** el modelo de transporte. En este caso, el costo de transporte por unidad, desde la planta ficticia a los dos destinos es cero, porque no existe esa fábrica. El costo de transporte por unidad desde la fuente ficticia a los destinos puede asumir también valores positivos. _Por ejemplo,_ para asegurar que Miami recibe toda su demanda, se asignará un costo (penalización) alto de transporte por unidad al elemento cero, desde la fuente ficticia hasta Miami.
   1. Resuelva este modelo usando simplex a mano y luego en Colab, compare los resultados.
   2. Describa el codigo usado.
4. Una tienda produce tres productos diferentes. Los productos se envían a tres almacenes. Los costos de envío por unidad, la oferta y la demanda de cada centro de distribución se muestran en las tablas a continuación. Determine la cantidad de productos que se deben enviar de la fábrica a cada centro de distribución para minimizar los costos de envío.

|          | Almacén A | Almacén B | Almacén C | Oferta |
| -------- | --------- | --------- | --------- | ------ |
| Tienda 1 | $10       | $8        | $7        | 200    |
| Tienda 2 | $5        | $12       | $6        | 300    |
| Tienda 3 | $4        | $7        | $11       | 400    |
| Demanda  | 150       | 250       | 200       |        |

5. Una empresa tiene tres tiendas en ciudades diferentes y dos almacenes en otras ciudades diferentes. Cada tienda oferta productos diferentes. Los costos de envío por unidad, la capacidad de producción y la demanda de cada almacén se muestran en las tablas a continuación. Determine la cantidad de productos que se deben enviar a los almacenes para satisfacer la demanda y minimizar los costos de envío.

|          | Almacén A | Almacén B | Almacén C | Almacén D | Oferta |
| -------- | --------- | --------- | --------- | --------- | ------ |
| Tienda 1 | $4        | $6        | $9        | $5        | 300    |
| Tienda 2 | $7        | $3        | $5        | $8        | 400    |
| Tienda 3 | $2        | $5        | $11       | $7        | 500    |
| Demanda  | 400       | 400       | 300       | 300       |        |

6. Una empresa tiene tres tiendas y cuatro almacenes. Los costos de envío por unidad, la capacidad de producción y la demanda de cada almacén se muestran en las tablas a continuación. Determine la cantidad de productos que se deben enviar de las fábricas a los almacenes para satisfacer la demanda de cada almacén y minimizar los costos de envío.

|          | Almacén A | Almacén B | Almacén C | Almacén D | Almacén E | Oferta |
| -------- | --------- | --------- | --------- | --------- | --------- | ------ |
| Tienda 1 | $6        | $8        | $10       | $9        | $7        | 500    |
| Tienda 2 | $5        | $11       | $7        | $4        | $3        | 400    |
| Tienda 3 | $12       | $9        | $3        | $8        | $6        | 300    |
| Demanda  | 300       | 400       | 400       | 200       | 400       |        |

```
    1. Formule el modelo de programación lineal teorico y algebraico.
    2. Formule este problema como un problema de transporte mediante la construcción de la tabla de parámetros apropiada.
    3. Obtenga una solución óptima para este problema.
    4. realice el ejercicio en colab y dinamicelo diferemtes valores
```

7. Tres ciudades se abastecen de electricidad de tres centrales eléctricas con capacidades de 25, 40 y 30 megawatts (MW). Las demandas máximas en las tres ciudades se estiman en 30, 35 y 25 MW. El precio por MW en las tres ciudades se muestra en la tabla

| Plantas\Ciudad | C\_1 | C\_2 | C\_3 |
| -------------- | ---- | ---- | ---- |
| P\_1           | 600  | 700  | 400  |
| P\_2           | 320  | 300  | 350  |
| P\_3           | 500  | 480  | 450  |

Durante el mes de agosto hay un aumento de 20% en la demanda de cada ciudad, que se puede satisfacer comprando electricidad a otra red, a una tasa elevada de $1000 por MW. Sin embargo, la red no está conectada con la ciudad 3. La empresa eléctrica desea determinar el plan más económico para distribuir y comprar la energía adicional.

```
1. Formule el problema como un modelo de transporte. en COlab usando latex.
2. Resuelva el problema con COLAB y determine un plan óptimo de distribución para la empresa eléctrica.
3. Determine el costo de la electricidad adicional comprada por cada una de las tres ciudades.
```

8. La Compañía ABC tiene tres plantas de producción de Productos para bebés que deben distribuirse a cuatro centros de distribución. Las plantas 1, 2 y 3 producen 12, 17 y 11 cargamentos por mes, respectivamente. Cada centro de distribución necesita recibir 10 cargamentos por mes. En la siguiente tabla se da la distancia de cada planta a su respectivo centro de distribución:

|          | CEDI 1 | CEDI 2 | CEDI 3 | CEDI 4 |
| -------- | ------ | ------ | ------ | ------ |
| planta 1 | 800    | 13000  | 400    | 700    |
| planta 2 | 1100   | 14000  | 600    | 1000   |
| planta 3 | 600    | 1200   | 800    | 900    |

* El costo del flete de cada embarque es de $100 más 0.50 centavos por milla.

¿Cuánto se debería embarcar a cada centro de distribución para minimizar el costo total del envío?

```
1. Formule el problema como uno de transporte mediante la elaboración de una tabla de parámetros apropiada.
2. Trace la representación de red de este problema.
3. Obtenga una solución óptima.
```

9. Tom desearía comprar exactamente 3 litros de cerveza casera hoy y al menos 4 litros mañana. Dick quiere vender un máximo de 5 litros en total a un precio de 3.00usd por litro hoy y de 2.70Usd por litro mañana. Harry está dispuesto a vender un máximo de 4 litros en total, a un precio de 2.90Usd por litro hoy y 2.80Usd por litro mañana.

Tom quiere saber cuánto debe comprar a cada uno para minimizar su costo y a la vez cumplir con los requisitos mínimos para satisfacer su sed.

```
    1. Formule el modelo de programación lineal teorico y algebraico.
    2. Formule este problema como un problema de transporte mediante la construcción de la tabla de parámetros apropiada.
    3. Obtenga una solución óptima para este problema. \
```

10. La corporación Versatech producirá tres productos nuevos. En este momento, cinco de sus plantas tienen exceso de capacidad de producción. El costo unitario respectivo de fabricación del primer producto será de 41usd, 39usd, 42usd, 38usd y 39usd en las plantas 1, 2, 3, 4 y 5, El costo unitario de fabricación del segundo producto será de 55usd, 51usd, 56usd, 52usd y 53usd en las plantas respectivas 1, 2, 3, 4 y 5; y para el tercer producto será de 48usd, 45usd y 50usd en las plantas respectivas 1, 2 y 3, pero las plantas 4 y 5 no pueden fabricar este producto. Los pronósticos de ventas indican que la producción diaria debe ser de 700, 1 000 y 900 unidades de los productos 1, 2 y 3, respectivamente. \\
11. Las plantas 1, 2, 3, 4 y 5 tienen capacidades para producir 400, 600, 400, 600 y 1 000 unidades diarias, sin importar el producto o combinación de productos. Suponga que cualquier planta que tiene capacidad y posibilidad de fabricarlos podrá producir cualquier cantidad de productos y con cualquier combinación. La administración desea asignar los nuevos productos a las plantas con el mínimo costo total de fabricación.
    1. Formule este problema como un problema de transporte mediante la construcción de la tabla de parámetros apropiada.
    2. Obtenga una solución óptima para este problema.
    3. realice este ejercicio en el entorno de google colab en latex y codigo \\
12. La empresa XYZ produce 2 productos \\(X\_1\\) y \\(X\_2\\) en dos plantas diferentes \\(Pl\_1\\) y \\(Pl\_2\\) cada uno de los productos necesita de diferentes Materias primas para ser elaborado segun la siguiente tabla:

|      | Mp1 | Mp2 | Mp3 | Tiempo de Prod     |
| ---- | --- | --- | --- | ------------------ |
| X\_1 | 2   | 3   | 1   | $$4\frac{min}{u}$$ |
| X\_2 | 3   | 1   | 0   | $$3\frac{min}{u}$$ |

La empresa cuenta son 5 proveedores

|      | Mp\_1 | Mp\_2 | Mp\_3 |
| ---- | ----- | ----- | ----- |
| S\_1 | 1000  | 800   | 1000  |
| S\_2 | 4000  | 2000  | -     |
| S\_3 | -     | 9000  | 2000  |
| S\_4 | 5000  | 3000  | 900   |
| S\_5 | 2000  | 4000  | 1000  |

costos por ser enviadas las unidades (u/usd)

|      | CtMp\_1 | CtMp\_2 | CtMp\_3 |
| ---- | ------- | ------- | ------- |
| S\_1 | 2       | 2       | 3       |
| S\_2 | 2       | 2,5     | -       |
| S\_3 | -       | 3       | 1       |
| S\_4 | 4       | 2       | 4       |
| S\_5 | 2       | 2,2     | 2       |

Costo fijo por proveedor:

|      | Costo fijo |
| ---- | ---------- |
| S\_1 | 90 usd     |
| S\_2 | 110 usd    |
| S\_3 | 85 usd     |
| S\_4 | 97 usd     |
| S\_5 | 60 usd     |

|      | Costo variable |
| ---- | -------------- |
| S\_1 | 0,5 usd        |
| S\_2 | 0,8 usd        |
| S\_3 | 0,7 usd        |
| S\_4 | 0,2 usd        |
| S\_5 | 0,6 usd        |

Distancia de las plantas a los prioveedores

|      | Plp\_1 | Plp\_2 |
| ---- | ------ | ------ |
| S\_1 | 70     | 92     |
| S\_2 | 67     | 92     |
| S\_3 | 85     | 83     |
| S\_4 | 70     | 72     |
| S\_5 | 90     | 94     |

1. encuentre el modelo optimo para reducir lso costos y suplir con la demanda
2. debe nivelar el sistema por medio del hallazgo de las unidades de demanda de acuerdo con las capacidades del sistema
3. realice este ejercicio en google colab y modele su respuesta

```
1. encuentre el modelo optimo que minimice el costo del sistema
2. nivele el sistema con base en la oferta
3. realice este ejercicio en google colab
```

### Ejercicio numero 6 del libro hamndy taha - investigacion de operaciones capituo 5

Tres ciudades abastecen de electricidad de ytres centrales electricas con capacidades de 25, 40 y 30 megawatts. las demandas maximas en las tres ciudades se estiman en 30, 35 y 25 megawatts, el precio por megawatts en las tres ciudades se muestra en la siguiente tabla.

Tabla uno.

|        |     | Ciudad |     |
| ------ | --- | ------ | --- |
| Planta | 1   | 2      | 3   |
| 1      | 600 | 700    | 400 |
| 2      | 320 | 300    | 350 |
| 3      | 500 | 480    | 450 |

* Durante el mes de Agosto hay un aumento del 20% en la demanda de cada ciudad, que se puede satisfacer comprando electricidad a otra Red, a una tasa elevada de 100usd/watts, sin embargo la red no esta conectada con la ciudad 3, la empresa electrica desea determinar el plan mas econominco para distribuir y comprar la energia adicional.

1. formule el problema como un modelo de transporte
2. resuelva el problema y determine un plan optimo de distribucion para la empresa
3. deterine el costo de la electricidad comprada por cada una de las ciudades.

***
