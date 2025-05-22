# Unidad Dos: Modelos de inventarios

{% hint style="info" %}
Los modelos de inventario son fundamentales en la logística ya que permiten gestionar eficientemente los niveles de stock. Mediante la aplicación de estos modelos, se puede minimizar el costo total de inventario, balancear el suministro con la demanda, y mejorar el servicio al cliente reduciendo tiempos de entrega y evitando desabastecimientos. Asimismo, facilitan la planificación y la toma de decisiones estratégicas en la cadena de suministro, optimizando el flujo de bienes y mejorando la competitividad de la empresa.
{% endhint %}

En general, la complejidad de los modelos de inventario depende de si la demanda es determinística o probabilística. Dentro de ambas categorías, la demanda puede variar, o no, con el tiempo. el patrón de la demanda en un modelo de inventario puede asumir uno de cuatro tipos:

1. Determinístico y constante(estático)con el tiempo.
2. Determinístico y variable (dinámico) con el tiempo.
3. Probabilístico y estacionario a lo largo del tiempo.
4. Probabilístico y no estacionario a lo largo del tiempo.

Esta clasificación supone la disponibilidad de datos confiables para pronosticar la futura demanda.

En función del desarrollo de modelos de inventario, la primera categoría es la más sencilla analíticamente, y la cuarta es la más compleja. Por otra parte, la primera categoría es la menos probable que ocurra en la práctica, y la cuarta es la más prevalente.

### Definicion de modelos de inventario

los modelos de inventario son modelos estadisticos y ecuaciones matematicas que conjugadas intentan o logran predecir el comportamiento de la demanda en sistemas productivos o de servicio,, para garantizar la disponibilidad de los bienes suminsitrados ya sea en la cade logistica interna o externa segun sea el caso.

hay tipos de modelos que abarcan los inventarios desde los mas sencillos como el EOQ. econocmic orden quantity hasta los modelos mas complejos como los modelos de punto de reorden y los modelos de revision continua de inventario.

### Google colab y los modelos de inventarios:[#](broken-reference)

para trabajar con los modelos de inventarios lo que debemos hacer es

1. identificar las librerias que usaremos en este caso usaremos:

* pandas
* numpy
* mathplotlib

### Modelo general de Inventario[#](broken-reference)

Las grandes pregiuntas que pretende suplir el modelo de inventario es ¿Cuando pedir?¿cuanto pedir?, esto nos lleva a evaluar todos los aspectos del inventario y segun los autores encontramos la siguiente ecuacion que encierra el modelo general de inventario:

```latex
$$
[\text{Costo Total de Inventario} = \text{Costo de Compra} + \text{Costo de Preparación} + \text{Costo de Almacenamiento} + \text{Costo de Faltante}]
$$
```

```markdown
$$
\[\left(\genfrac{}{}{0pt}{}{costo\ total}{de\ inventario}\right) =\left(\genfrac{}{}{0pt}{}{costo\ de}{compra}\right)+\left(\genfrac{}{}{0pt}{}{costo\ de}{preparacion}\right)+\left(\genfrac{}{}{0pt}{}{costo\ de}{almacenamiento}\right)+\left(\genfrac{}{}{0pt}{}{costo\ de}{faltante}\right)\]
$$
```

1. \\(costo\ de\ compra\\): es el precio por unidad del articulo
2. \\(costo\ de\ preparacion\\): es el costo fijo incurrido en el momento de colocar un pedido, es independiente del costo del articulo y la cantidad pedida
3. \\(costo\ de\ almacenamiento\\): tambien conocido como mantenimiento o holding cost en ingles, son los costos asociados al manejo y mantenimiento en bodega del articulo, corresponde al interes por el capital o valor del articulo.
4. \\(costo\ de\ faltante\\): es la penalizacion que se incurre cuando se terminan las existencias del inventario, es la perdida potencial de ingresos producto de la no venta, y un costo subjetivo asociado es la perdida de la confianza o del cliente mismo.

### empezaremos por el modelo EOQ tambien llamado modelos estaticos.[#](broken-reference)

* **el modelo eoq o cantidad optima de pedido:** (EOQ clasico)

es uno de los modelos mas comunes y mayor utilizados ya qu eeste modelo tiene encuenta los costos por pedido y amacenamiento del mismo. es decir que cuanto mas se compre mayor es el descuento pero mayor sera el costo de mantener, el objetivo principal de este modelo es encontrar el punto de equilibrio donde los costos se manejen de la mejor forma posible segun los requeirmientos de la demanda.

\\\[EOQ = \sqrt{\frac{2\*costo\ de\ ordenar\*Demanda}{costo\ de\ almacenamiento\}}\\]

*   **EOQ con demanda Desconocida:**

    se considera la demanda del producto como incierta o desconocida y se utliza un enfoque de nivel de servicio para mantener el nivel optimo de inventario, siendo el nivel de servicio pa probahbilidad de que el inventario este disponible cuando sea requerido, el objetivo principal es encontrar la cantidad optima de inventario que maximice el nivel de servicio mientras se minimizan los costos totales de inventario.

#### Palabras y nomeclaturas[#](broken-reference)

* \\(D= Demanda\\)
* \\(t\_0=Duracion\ del\ ciclo\ de\ pedido\\)
* \\(ROQ = Reorder\ Quantity\\)
* \\(ROL = Reorder\ Level\\)
* \\(Q = cantidad\ optima\ de\ pedido\\)
* \\(t\_0 = \frac{Q}{D}\ unidades\ de\ tiempo\\)
* \\(K = costo\ de\ Preparacion\ (costo\ de\ un\ pedido)\\)
* \\(h = costo\ de\ Almacenamiento\\)
* \\(L= lead\ Time\\)

en general:

\\\[Q= \sqrt{\frac{2(K)(D)}{h\}}\\]

\\(Entonces:\ la\ politica\ de\ inventario\ teoricamente\ sería\ las\ cantidades\ Q\ en\ cada\ "y"\\)

### tiempo de entrega:[#](broken-reference)

cuando existe un pedido con un tiempo de entrega estipulado positivo se llamara “L” (lead time), en estos casos debemos tener en cuenta las relaciones del ROL y ROQ correspondientes ya que estos variaran el comportamiento del inventario segun su naturaleza de abastecimiento o lead time. se debera evidenciar las duraciones del lead time vs el tiempo de ciclo del inventario, ya que el lead time generalmente debera ser menor que el tiempo de ciclo de lo contrario habra que tomar otras medidas para controlar el inventario.

ejemplo:

se define el tiempo efectivo de la siguiente forma:

\\\[L\_e = L - nt\_0\\]

### ROL/ROQ , Lead time y Safety stock en los modelos de inventarios Deterministicos.[#](broken-reference)

* Los supuestos del modelo Eoq se enumeran de la siguiente forma:

1. **Demanda constante:** Se asume que la demanda del producto es constante a lo largo del tiempo, lo que implica que no hay fluctuaciones estacionales o cambios en la demanda.
2. **Tasa de producción o suministro constante:** Se supone que el suministro o producción del inventario es instantáneo y constante. Es decir, cada vez que se realiza un pedido, este llega de inmediato y reabastece completamente el inventario.
3. **Tiempo de entrega conocido y constante:** El tiempo que toma recibir un pedido después de realizarlo es conocido y no varía.
4. **Costo de pedido constante:** El costo asociado a realizar un pedido es fijo, independientemente del tamaño del pedido.
5. **Costo de almacenamiento constante:** El costo de mantener una unidad en inventario es constante y no varía con el tiempo o la cantidad de inventario.

no obstante existen otras variaciones del Modelo que implican una espera en el tiempo de ciclo del pedido, lo que obliga a tomar decisiones en tiempo real, como por ejemplo el _lead time_ de un proveedor, explico, si un proveedor toma su tiempo para entregar el pedido al cliente, este debe mantener una reserva o saber en que momento preciso realizar la orden con el fin de que una vez que este llegue no le afecte el conotrol de inventario o incurra en faltantes, a ese tiempo de ciclo entre el pedido y la recepcion teniendo encuenta el tiempo del cliente se le conoce como **Lead time** mientras que el _nivel de inventario_ donde se debe pedir se conoce como ROL; de igual forma la cantidad a pedir en ese momento se conoce como ROQ.

#### Conceptualizando:[#](broken-reference)

1. ROQ: es la cantidad de unidades que se debe pedir una vez el ROL sea alcanzado.
2. ROL: es el nivel de inventario medido en unidades que funciona como detonante del pedido
3. LT: lead time, es el tiempo que se demora en llegar un pedido desde el momento de su realizacion
4. SStock: safety stock, es el nivel de inventario de seguridad que se necesita para soportanr la variabilidad de LT del proveedor \\(P\_i\\)

### Modelo de EOQ en python[#](broken-reference)

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
```

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

def eoq(costo_producto, costo_orden, costo_almacenamiento, demanda_anual):
    q = np.sqrt((2 * costo_orden * demanda_anual) / costo_almacenamiento)
    tiempo_entre_pedidos = q / demanda_anual
    costo_total = (costo_producto * demanda_anual) + (costo_orden * demanda_anual / q) + (costo_almacenamiento * q / 2)
    return q, tiempo_entre_pedidos, costo_total

# Pedir al usuario que ingrese los valores de los parámetros del inventario
costo_producto = float(input("Ingrese el costo del producto por unidad: "))
costo_orden = float(input("Ingrese el costo por orden: "))
costo_almacenamiento = float(input("Ingrese el costo de almacenamiento por unidad por año: "))
demanda_anual = np.arange(10, 1000, 10)

# Calcular el EOQ para cada valor de la demanda anual
q_values = [eoq(costo_producto, costo_orden, costo_almacenamiento, d)[0] for d in demanda_anual]
costo_total_values = [eoq(costo_producto, costo_orden, costo_almacenamiento, d)[2] for d in demanda_anual]

# Graficar el costo total como una función de la demanda anual
fig, ax1 = plt.subplots()

color = 'tab:red'
ax1.set_xlabel('Demanda anual')
ax1.set_ylabel('Cantidad óptima de inventario', color=color)
ax1.plot(demanda_anual, q_values, color=color)
ax1.tick_params(axis='y', labelcolor=color)

ax2 = ax1.twinx()

color = 'tab:blue'
ax2.set_ylabel('Costo total de inventario', color=color)
ax2.plot(demanda_anual, costo_total_values, color=color)
ax2.tick_params(axis='y', labelcolor=color)

fig.tight_layout()
plt.show()
```

```python
import numpy as np
import matplotlib.pyplot as plt

def costo_total(D, h, s, Q):
   
    return (D/Q)*s + (Q/2)*h

def graficar_eoq(D, h, s):
    
    # Rango de valores para Q
    Q = np.linspace(1, 100, 100)

    # Calcular costos
    costo_mant = (Q/2)*h
    costo_ped = (D/Q)*s
    costo_total_anual = costo_total(D, h, s, Q)

    # Crear la figura
    plt.figure(figsize=(5, 3))

    # Graficar costos
    plt.plot(Q, costo_mant, label='Costo de mantenimiento')
    plt.plot(Q, costo_ped, label='Costo de pedido')
    plt.plot(Q, costo_total_anual, label='Costo total')

    # Encontrar el punto mínimo del costo total (Q óptimo)
    Q_optimo = np.sqrt(2*D*s/h)
    plt.axvline(x=Q_optimo, color='red', linestyle='--', label='Q óptimo')

    # Etiquetas y leyenda
    plt.xlabel('Tamaño del lote (Q)')
    plt.ylabel('Costo')
    plt.title('Modelo EOQ')
    plt.legend()

    # Mostrar la gráfica
    plt.grid(True)
    plt.show()

# Ejemplo de uso
demanda_anual = 100
costo_mantener = 7
costo_pedido = 2
graficar_eoq(demanda_anual, costo_mantener, costo_pedido)
```

### Ejemplo numero uno:[#](broken-reference)

La empresa IND sas tiene una demanda diaria de 100 unidades, y el costo en que se incurren dichos pedidos es de 100 Cop se estima que el almacenqamiento de cada uno de los elementos es de $0.01 Cop Diarios los pedidos se demoran 12 dias en ser entregados, debemos determinar la politica optima de invenario que nos permita mantener el mejor invetario posible. entonces:

* \\(D= 100\ nunidades\ diarias\\)
* \\(K= 100\\)$ por pedido
* \\(h=0.02\\). unidades por día
* \\(L= 12\ dias\\)

```python
import math

def eoq(demand, ordering_cost, holding_cost):
    """Calcula la cantidad óptima de pedido (EOQ) dado la demanda anual,
       el costo de ordenar y el costo de mantenimiento de inventario."""
    eoq = math.sqrt((2 * demand * ordering_cost) / holding_cost)
    return eoq

def total_inventory_cost(demand, ordering_cost, holding_cost, eoq):
    """Calcula el costo total de inventario dado la demanda anual,
       el costo de ordenar, el costo de mantenimiento de inventario y el EOQ."""
    total_cost = (demand * ordering_cost / eoq) + (eoq / 2 * holding_cost)
    return total_cost

# Pide al usuario los datos del inventario
demand = float(input("Ingrese la demanda correspondiente: "))
ordering_cost = float(input("Ingrese el costo de ordenar: "))
holding_cost = float(input("Ingrese el costo de mantener una unidad en inventario: "))

# Calcula la EOQ y el costo total de inventario
eoq_value = eoq(demand, ordering_cost, holding_cost)
total_cost = total_inventory_cost(demand, ordering_cost, holding_cost, eoq_value)

# Imprime los resultados
print("EOQ: ", eoq_value)
print("Costo total de inventario: ", total_cost)
```

{% hint style="info" %}
#### Intentemos graficar el comportamiento de un Articulo de Inventario en el tiempo usando colab
{% endhint %}

En el siguiente ejercicio se pretende generar el comportamiento del inventario a lo largo del periodo \\(t\_0\\), para posteriormente graficarlo.

se podran variar cantidades de productos

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

```python
def calcular_q(demanda, holding_cost, costo_pedido):

    q = np.sqrt((2 * demanda * costo_pedido) / holding_cost)
    return q

def simular_inventario(demanda, q, tiempo_simulacion):
    inventario = []
    nivel_actual = q
    for _ in range(tiempo_simulacion):
        nivel_actual -= demanda
        if nivel_actual <= 0:
            nivel_actual = q
        inventario.append(nivel_actual)
    return inventario


# Solicitar datos al usuario
demanda_anual = float(input("Ingrese la demanda anual: "))
holding_cost = float(input("Ingrese el costo de mantener una unidad en inventario: "))
costo_pedido = float(input("Ingrese el costo de realizar un pedido: "))

# Calcular Q
q_optimo = calcular_q(demanda_anual, holding_cost, costo_pedido)
print("El tamaño del lote óptimo es:", q_optimo)

# Simulación y visualización
demanda_diaria = demanda_anual / 365
tiempo_simulacion = 365
niveles_inventario = simular_inventario(demanda_diaria, q_optimo, tiempo_simulacion)

# Graficar
plt.plot(niveles_inventario)
plt.xlabel("Tiempo (días)")
plt.ylabel("Nivel de inventario")
plt.title("Comportamiento del inventario")
plt.show()
```

{% hint style="info" %}
### Ejercicios de Practica del modelo de inventario



Vamos a poner en practica la teoria descrita en el cuaderno anterior

* debera realizar los siguientes ejercicios a mano en una hoja limpia con su calculadora
* Realizara los siguientes ejercicios usando google colab como se describe en el documento.
{% endhint %}



### Ejercicios EOQ

#### Ejercicio Numero 1[#](broken-reference)

La empresa Industrial.inc, es una empresa qu se dedica a la fabricacion de tornillos autoperforantes para la industria del aluminio. esta desea reducir sus costos de inventarios mediante la determinacion del numero de tornillos que debe obtener en cada una de las ordenes

* la demanda es de 10000
* el pedido tiene un costo asociado de $1000
* el costo de mantener tiene un valor asociado de $1,50 un/año.
* el año tiene 250 dias laborales

usted debera calcular

* a)Numero optimo de Orden \\((q)\\)
* b)Numero de ordenes por año
* c)Tiempo de ciclo, tiempo esperado entre ordenes.

#### Ejercicio Numero 2[#](broken-reference)

LA empresa [Amigos.sa](http://amigos.sa/), comercializa articulos para el hogar, con una demanda anual de 1000 unidades, si el costo para colocar un pedido es de $10usd,$ el costo de almacenamiento unitario anual de cada articulo es de $2,5 Usd, la empresa opera 365 dias, siete dias a la semana, un costo de venta de 15 dolares por articulo, determine la politica optima de inventario para este problema.

#### Ejercicio Numero 3[#](broken-reference)

Una compañia de trasporte, de vans para servicio escolar consume gasolina a una tasa de 8.200 galones por mes, la gasolina cuesta 12.000 Cop. y tiene un costo de pedido 6.000 Cop el costo de mantener el inventario es de 2000 Cop por galon.

* determine cuando y cuanto se debe ordenar, si se desea minimizar el coste total
* suponga que se permiten roturas de stock (stock ruptures) con una penalizacion de 1.500 cop por galon mensual
* suponga que el costo de la gasolina desciende a 8.000 cop por galon si se compran por lo menos 10.000 galones, como afectaria el costo teniendo en cuenta la penalizacion anterior.
* suponga que el costo de la gasolina seria de 7.000 Cop por galon si el costo de lote minimo es de 12.000 galones, teniendo en cuenta la penalizacion anterior.
* ¿sera necesario un invenytario inicial para solucionar el problema?, sustente tecnicamente su respuesta.

#### Ejercicio Numero 4[#](broken-reference)

Una empresa dedicada a la imopresion y comercializacion de libros esta haciendo una compra mensual, para esto realizo un estudio del comportamiento del mercado en el insumo mas importante de su empresa el papel especial con que imprimen sus libros. en los ultimos 12 meses el comportamiento de su demanda fue de:

\\(Demanda = \[10 -11-10-9-10-11-9-10,5-10-9-9-11,5]\\) tonelas por mes se estima el precio de compra se mantendra en Cop $3,400.000 por tonelada su costo de pedido es de COP $350.000, la politica de la compañia dice que el se le cargara un 15% al manejo de los inventarios mas Cop $60.000 por manejo de bodegaje, calcular:

* el modelo optimo para manejar este imventario
* si el proveedor ofrece darnos un descuento del 10% por compras superiores a 30 toneladas y otro proveedor un descuento del 11% por compras superiores a 60 toneladas, como cambiaria mi politica de inventario en cada uno de los escenaros?
* si adicional al descuento logramos hacer un acuerdo con una bodega externa donde el almacenamiento de este se reduce al 9% con una capacidad maxima de 35 toneladas, como cambiaria nuestra politica?

#### Ejercicio Numero 5[#](broken-reference)

Cantidad ec.onómica de pedido La demanda de computadoras Deskpro en Best Buy es de 1,000 unidades por mes. Best Buy incu- rre en costos fijos de colocación del pedido, transporte y recepción de 4,000 dólares cada vez que ‘se coloca un pedido. Cada computadora le cuesta 500 dólares y el minorista tiene un costo de mantener inventario de 20%. Evalúe el número de computadoras que el gerente de la tienda debe ordenar en cada lote de reabastecimiento.

#### Ejercicio Numero 6[#](broken-reference)

Abc company have two item \\(X\_1\\) and \\(X\_2\\) for stockin into theirs warehouse, the Demand for each one of the items is:

* \\(D\_1 = 10000u/y\\) and \\(D\_2=12000u/y\\).
* the holdig cost for each one of them is \\(13%\\) and the costo is \\(C\_1=5000cop\\) And \\(C\_2=7000Cop\\)

the two items have the same supplier so they sahre the operation costing \\(6000cop\\) by S

* need to find the total cost of the operation
* if the supplier takes 3 days of delay how would it be modelated
* ROL
* ROQ

#### Ejercicio Numero 7[#](broken-reference)

Water testing at the Central Park reservoir requires a chemical reagent that costs 500usd per gallon. Use is constant at 1/3 gallon per week. Carrying cost rate is considered to be 12% per year, and the cost of an order is 125usd. What is the optimal order quantity for the reagent?

#### Ejercicio Numero 8[#](broken-reference)

Continuing with the information about the Central Park reservoir given in Problem 1, the city could make this reagent at the rate of 1/8 gallon per day, at a cost of $300 per gallon. The setup cost is 150usd. Use a 7-day week. Compare using the EOQ and the EPQ systems. What course of action do you recommend?

#### Ejercicio de inventario con modelamiento matematico en python[#](broken-reference)

la empresa **XYZ** posee Tres clientes y cuatro proveedores, la empresa manufactura dos productos \\(X\_1\\) y \\(X\_2\\) donde para el producto \\(X\_1\\) es necesario dos unidades de \\(MP\_1\\) y una unidad de \\(MP\_2\\); mientras que es Producto \\(X\_2\\) necesita una unidad de \\(MP\_1\\) y tres unidades de \\(MP\_2\\), el costo de almacenamiento del producto terminado de \\(X\_1\\) y \\(X\_2\\) es de 0,5 COP/Un y 0,8 COP/Un Respectivamente; el costo de pedir \\(X\_1\\) y \\(X\_2\\) es de 1,2 Cop/un y 0,8Cop/Un Respectivamente, cabe mencionar que al pedir un producto se responde desde los proveedores con los componentes respectivos de cada uno \\(MP\_i\\)

la tabla de **costos** de \\(MP\_i\\) esta dada de la siguiente forma:

| Proveedor  | \\(Rm\_1\\) | \\(Rm\_2\\) |
| ---------- | ----------- | ----------- |
| \\(S\_1\\) | 90          | 75          |
| \\(S\_2\\) | 50          | 65          |
| \\(S\_3\\) | 65          | 25          |
| \\(S\_4\\) | 70          | 50          |

* La Demanda del sistema esta dada de la siguiente forma:

| Cliente    | \\(X\_1\\) | \\(X\_2\\) |
| ---------- | ---------- | ---------- |
| \\(C\_1\\) | 500        | 250        |
| \\(C\_2\\) | 450        | 300        |
| \\(C\_3\\) | 250        | 300        |

* se asume que el sistema esta balanceado y que los proveedores pueden suplir la demanda en la totalidad de lo que se requiera.

encuentre:

1. el costo minimo del sistema para suplir con la demanda.
2. los costos asociados al sistema segun el modelo POQ
3. si los proveedores tienen un lead time de:

| PROVEEDOR  | LEAD TIME |
| ---------- | --------- |
| \\(S\_1\\) | 2         |
| \\(S\_2\\) | 4         |
| \\(S\_3\\) | 2         |
| \\(S\_4\\) | 5         |

Calcule los ROL y ROQ de cada uno de los productos, con base en su Bill of material.

4. calcule la tasa de demanda (descuento) \\(d\\) y teniendo en cuenta, una tasa de produccion de \\(x\_1 = 80 un/dia\\) y \\(x\_2 = 60 un/dia\\) calcule el lote economico optimo. y el tamaño de la bodega que deberia tener la empresa.

**Agreguemos el costo total del inventario y grafiquemoslo**[**#**](broken-reference)

```python
# Datos para la prueba de escritorio
D = 100000
h = 30000
S = 14000
periodo = 365
lead_time = 2

# Calcular el Q óptimo y el inventario inicial
Q_opt = ((2 * D * S) / h)**0.5
inventario_inicial = round(Q_opt)


# Crear una tabla para almacenar el inventario
inventario = pd.DataFrame(columns=["Dia", "Inventario_inicial", "Nivel_Inventario", "Pedido", "Demanda", "Inventario_Final"])

# Inicializar la tabla con el día cero
inventario_cero = round(Q_opt)
inventario = inventario.append({"Dia": 0,
                                "Inventario_inicial": 0,
                                "Nivel_Inventario": 0,
                                "Pedido": 0,
                                "Demanda": 0,
                                "Inventario_Final": inventario_cero},
                               ignore_index=True)

# Llenar la tabla con la lógica que definimos
for dia in range(1, periodo+1):
    # Calcular la demanda para el día actual
    demanda = round(np.random.normal(D/periodo, 0.1*D/periodo))

    # Calcular el nivel de inventario y el pedido
    if dia == 1:
        inventario_inicial = inventario_cero
    else:
        inventario_inicial = inventario["Inventario_Final"].iloc[dia-1]

    nivel_inventario = inventario_inicial - demanda
    if nivel_inventario < 0:
        nivel_inventario = 0
        pedido = round(Q_opt) - nivel_inventario
    else:
        pedido = 0

    # Actualizar el inventario final
    inventario_final = nivel_inventario + pedido

    # Agregar una fila a la tabla
    inventario = inventario.append({"Dia": dia,
                                    "Inventario_inicial": inventario_inicial,
                                    "Nivel_Inventario": nivel_inventario,
                                    "Pedido": pedido,
                                    "Demanda": demanda,
                                    "Inventario_Final": inventario_final},
                                    ignore_index=True)


# definimos el costo total del inventario

total_cost = (D * S / Q_opt) + (Q_opt / 2 * h)


#para exportar el archivo .csv de la base de datos generada elimine el numeral del sigiuiente codigo
#el archivo se generara en esta hoja de colab debera descargarla
#inventario.to_csv("tabla_inventario_crc.csv", index=False)

print("el Q optimo de este ejemplo es:", round(Q_opt))
print("el costo total del inventario es:", total_cost)

# Imprimir la tabla
print(inventario)

# Graficar el nivel de inventario


plt.figure(figsize=(40,10))
plt.plot(inventario["Dia"], inventario["Nivel_Inventario"])
plt.xlabel("Dias")
plt.ylabel("Nivel de Inventario")
plt.show()
```

### EPQ Model[#](broken-reference)

The economic production quantity (EPQ) model (also known as the economic lot size (ELS) model) is used in manufacturing situations where inventory increases at a finite rate and depends on the production rate and the usage rate of the item under consideration. In addition to the variables (D, S, H, Q, and C) defined earlier, we define two more variables: p = production rate per day (daily production rate) and d = demand rate per day (daily demand rate). The values of p and d must be in the same time unit. For example, these values could be weekly rates instead of daily rates. However, daily rates are most common. Q in this case is the production quantity (rather than order quantity) to be made in one lot and S is the cost of setting up the machine to produce that one lot. Therefore, S is called the setup cost per set up (rather than order cost per order).

<pre class="language-latex"><code class="lang-latex"><strong>$$\[ Q_{epq}=\sqrt{\left(\frac{2DS}{h\left(1-\frac{d}{q}\right)}\right)} \]$$
</strong></code></pre>

#### Ejemplo EPQ

hallemos:

1. Demandan anual = 50.000 Unidades
2. setup cost = $25 usd
3. costo de mantener = $5 usd
4. _tasa de produccion (p)_ = 500 un/dia
5. Dias laborales = 250 dias

entonces resolvemos:

desconocemos _d_, pero esta puede ser calculada por medio de los dias laborales y demanda anual.

\\\[ d = \frac{50.000}{250} = 200 un \\]

Usando la formula de _EPQ_ obtenemos:

\\\[ Q\_{epq} = \sqrt{\frac{2\*50,000\*25}{5\*(1-\frac{200}{250})\}} = 912.87 \\]

tambien podemos calcular el nivel de inventario maximo (\\(I\_{max})\\)

\\\[ I\_{max}=Q \* \left(1-\frac{d}{p}\right) \\]

Reemplazando:

\\\[ I\_{max}=912.87\*\left(1-\frac{200}{500}\right) = 547.72 un \\]
