# Modelo de redes

### Modelo de redes[#](broken-reference)

***

Definicion de redes: las redes son una serie de nodos localizados y enlazados con arcos la notacion para la descripcion de la red es

\\

{% code overflow="wrap" %}
```markdown
\[\begin{split} (N,A); \\ donde: \\ N = Conjunto\ de\ Nodos \\ A = Conjunto\ de\ Arcos \end{split}\]
```
{% endcode %}

Por ejmplo:

\\\[\begin{split} N = \\{1,2,3,4,5\\} \\\ A = \\{(1,2),(1,3),(2,3),(2,5),(3,4),(3,5),(4,2),(4,5)\\} \end{split}\\]

```python
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

```python
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

```python
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
