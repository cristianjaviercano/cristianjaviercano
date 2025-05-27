# Modelo de Transbordo

#### Explicación del Modelo de Transbordo o Cross Docking

El modelo de transbordo, también conocido como cross docking, es una metodología logística donde los productos se trasladan directamente desde el proveedor hasta el cliente final con la mínima manipulación y almacenamiento. Este modelo implica el uso de centros de distribución, también llamados nodos intermedios, donde los productos que llegan son clasificadas y redirigidos rápidamente sin necesidad de almacenarlos por un largo periodo.

La ventaja principal del cross docking es la eficiencia en la cadena de suministro, reduciendo costos de almacenamiento y acelerando los tiempos de envío al cliente final. En el escenario típico, los productos llegan a un centro de transbordo y se transfieren directamente a un vehículo de salida que se dirige al destino final, lo cual requiere una coordinación precisa pero proporciona un flujo eficiente y continuo de mercancías.

***

{% hint style="info" %}
En el modelo de transbordo o Cross docking se inicia con el supuesto que el hecho de pasar por nodos intermedios supone un ahorro al sistema, mientras que el modelo general de transporte solo supone entregas directas.
{% endhint %}

Ejemplo:

donde fabricas de producto X  P\_1 y P\_2 en asocian con tres agencias D\_1, D\_2 y D\_3 a travez de dos centros de distribicion T\_1  y T\_2

1. genere el modelo de red de este apartado a mano y en colab. usando Graphviz

```python
from IPython.display import Image
Image(filename='/content/drive/MyDrive/Libros academicos en colab/1. Logistica/Imagen 16-03-23 a las 1.26 p.m..jpeg')
```

La oferta de las plantas son como se muestran en la&#x20;

```latex
Demanda en los P_n
- P_1 = 1000 Un  
- P_2 = 1200 Un 
```

```latex
Demanda en los D_n 
- D_1 = 800
- D_2 = 900  
- D_3 = 500
```

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

```python
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

