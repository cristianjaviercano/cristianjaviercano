# My Jupyter Book

### Logistic management desde python y google colab[#](broken-reference)

***

\\(Docente:\ Cristian\ Javier\ Cano\ M\\)\
\\(msc\ Innovacion\ y\ Desarrollo\\)

### Unidad Cero: Componentes tipicos de la Logistica:[#](broken-reference)

Un sistema logístico típico se compone de varios elementos clave que trabajan en conjunto para garantizar que los productos lleguen al cliente final de manera eficiente y a tiempo. Estos son algunos de los componentes más comunes:

1. **Servicio al cliente:**

Este componente se centra en satisfacer las necesidades y expectativas del cliente. Incluye aspectos como la atención al cliente, la gestión de pedidos, la resolución de problemas y la comunicación efectiva.

2. **Gestión de la demanda:**

Implica predecir y planificar la demanda de productos para asegurar que se tenga el inventario adecuado en el momento adecuado. Se utilizan herramientas como el análisis de datos y la previsión de la demanda.

3. **Procesamiento de pedidos:**

Abarca todas las actividades relacionadas con la recepción, verificación, preparación y envío de los pedidos. La eficiencia en este proceso es fundamental para la satisfacción del cliente.

4. **Gestión de inventario:**

Se encarga de controlar y optimizar los niveles de inventario para minimizar costos y garantizar la disponibilidad de los productos. Incluye el seguimiento del inventario, la gestión de almacenes y la planificación del reabastecimiento.

5. **Transporte:**

Es el componente responsable del movimiento físico de los productos a través de la cadena de suministro. Incluye la selección del medio de transporte adecuado (terrestre, marítimo, aéreo), la planificación de rutas y la gestión de la flota.

6. **Almacenamiento:**

Proporciona el espacio físico para guardar los productos de forma segura y eficiente. Involucra la gestión de almacenes, el control de la ubicación del inventario y la optimización del espacio.

7. **Manejo de materiales:**

Se refiere al movimiento de los productos dentro del almacén, como la recepción, el almacenamiento, la preparación de pedidos y el despacho. Se utilizan equipos y tecnologías como carretillas elevadoras, sistemas de transporte y robots.

8. **Embalaje:**

Protege los productos durante el transporte y el almacenamiento. Incluye la selección de los materiales de embalaje adecuados, el diseño del embalaje y el etiquetado.

9. **Control de calidad:**

Garantiza que los productos cumplan con los estándares de calidad establecidos. Incluye la inspección de los productos, las pruebas de calidad y la gestión de devoluciones.

### Modelos matematicos segun la etapa del proceso logistico[#](broken-reference)

1. **Modelos matemáticos en la etapa de aprovisionamiento:** En esta etapa, los modelos matemáticos más utilizados son los modelos de inventario, que se utilizan para determinar la cantidad óptima de inventario a mantener y cuándo realizar pedidos. También se utilizan modelos de compra óptima y modelos de selección de proveedores para tomar decisiones de compra estratégicas.
2. **Modelos matemáticos en la etapa de producción:** En esta etapa, se utilizan modelos de programación lineal para optimizar la planificación de la producción, incluyendo la asignación de recursos, la programación de la producción y la gestión de la capacidad.
3. **Modelos matemáticos en la etapa de almacenamiento:** En esta etapa, se utilizan modelos de diseño y gestión de almacenes para determinar la ubicación óptima de los almacenes, el tamaño óptimo del almacén y la disposición óptima de los productos en el almacén. También se utilizan modelos de gestión de inventario para optimizar el nivel de inventario en el almacén.
4. **Modelos matemáticos en la etapa de transporte:** En esta etapa, se utilizan modelos de optimización de rutas para determinar la ruta óptima de entrega, la asignación de vehículos y la programación de los horarios de entrega. También se utilizan modelos de asignación de recursos para optimizar la utilización de los recursos de transporte.
5. **Modelos matemáticos en la etapa de distribución:** En esta etapa, se utilizan modelos de optimización de la cadena de suministro para optimizar el flujo de productos y la coordinación entre los diferentes actores de la cadena de suministro. También se utilizan modelos de planificación de la demanda para predecir la demanda futura y tomar decisiones de producción y distribución en consecuencia.

### ¿Cual es la mision de la logistica?:[#](broken-reference)

La misión de la logística puede resumirse en planificar, implementar y controlar el flujo eficiente y efectivo de bienes, servicios e información relacionada desde el punto de origen hasta el punto de consumo para satisfacer las necesidades de los clientes.

_**Esta misión implica:**_

* Entregar el producto adecuado: Asegurar que el producto o servicio correcto llegue al cliente.
* En la cantidad adecuada: Proporcionar la cantidad exacta de producto que el cliente necesita.
* En el lugar adecuado: Hacer llegar el producto al destino correcto.
* En el momento adecuado: Entregar el producto en el tiempo acordado. En las condiciones adecuadas: Asegurar que el producto llegue en perfecto estado.
* Al coste adecuado: Optimizar los costos de la cadena de suministro para ofrecer precios competitivos y rentabilidad.

### Unidad uno: Servicio Al CLiente[#](broken-reference)

***

### Enfoque en el Servicio al Cliente:[#](broken-reference)

* Definir qué es el servicio al cliente en el contexto de la logística.
* Explicar los diferentes aspectos del servicio al cliente, como tiempo de entrega, confiabilidad, comunicación, etc.
* Mostrar cómo Python puede ayudar a medir y mejorar el servicio al cliente.

#### Qué es el servicio al cliente en el contexto de la logística.[#](broken-reference)

Definición de servicio al cliente El servicio al cliente se refiere al conjunto de actividades, procesos y estrategias que una empresa o negocio implementa para satisfacer las necesidades y expectativas de sus clientes. Implica brindar asistencia, soporte y una experiencia positiva a los clientes antes, durante y después de una venta o interacción.

#### Objetivos clave del servicio al cliente[#](broken-reference)

1. Comprender y atender las necesidades de los clientes de manera efectiva
2. Resolver problemas, quejas y consultas de manera oportuna y eficiente
3. Crear relaciones duraderas y de confianza con los clientes
4. Superar las expectativas de los clientes y generar lealtad hacia la marca
5. Diferenciarse de la competencia a través de un servicio excepcional

#### ¿Cómo se mide la satisfacción del cliente en una empresa?[#](broken-reference)

Métodos para medir la satisfacción del cliente:

1. **Encuestas de satisfacción:** Estas son herramientas directas que permiten a las empresas obtener retroalimentación sobre la experiencia del cliente. Pueden incluir preguntas sobre la calidad del producto, la atención al cliente y la probabilidad de recomendar la empresa a otros.
2. **Análisis de comentarios en redes sociales:** Evaluar las opiniones y comentarios de los clientes en plataformas sociales puede proporcionar una visión clara de su satisfacción. Este método permite identificar tendencias y áreas de mejora.
3. **Índice de quejas y reclamaciones:** El seguimiento del número y la naturaleza de las quejas puede ayudar a las empresas a medir la satisfacción del cliente. Un aumento en las quejas puede indicar problemas en el servicio o el producto.
4. **Grupos de discusión (focus groups):** Reunir a un grupo de clientes para discutir sus experiencias y opiniones sobre un producto o servicio puede ofrecer información valiosa sobre su satisfacción y expectativas.
5. **Tasa de retención y fidelización de clientes:** Medir cuántos clientes regresan para realizar compras repetidas puede ser un indicador directo de su satisfacción. Un alto nivel de retención sugiere que los clientes están contentos con la oferta de la empresa.

[ive consultores](https://iveconsultores.com/satisfaccion-del-cliente/)

```
import pandas as pd
```

```
Bd = pd.read_csv('/Users/cristianjaviercanomogollon/Documents/Python_crc/BD_apoyo/Logistica/indice_pasajeros.csv')
```

```
Bd.info()
```

```
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 25976 entries, 0 to 25975
Data columns (total 25 columns):
 #   Column                             Non-Null Count  Dtype  
---  ------                             --------------  -----  
 0   Unnamed: 0                         25976 non-null  int64  
 1   id                                 25976 non-null  int64  
 2   Gender                             25976 non-null  object 
 3   Customer Type                      25976 non-null  object 
 4   Age                                25976 non-null  int64  
 5   Type of Travel                     25976 non-null  object 
 6   Class                              25976 non-null  object 
 7   Flight Distance                    25976 non-null  int64  
 8   Inflight wifi service              25976 non-null  int64  
 9   Departure/Arrival time convenient  25976 non-null  int64  
 10  Ease of Online booking             25976 non-null  int64  
 11  Gate location                      25976 non-null  int64  
 12  Food and drink                     25976 non-null  int64  
 13  Online boarding                    25976 non-null  int64  
 14  Seat comfort                       25976 non-null  int64  
 15  Inflight entertainment             25976 non-null  int64  
 16  On-board service                   25976 non-null  int64  
 17  Leg room service                   25976 non-null  int64  
 18  Baggage handling                   25976 non-null  int64  
 19  Checkin service                    25976 non-null  int64  
 20  Inflight service                   25976 non-null  int64  
 21  Cleanliness                        25976 non-null  int64  
 22  Departure Delay in Minutes         25976 non-null  int64  
 23  Arrival Delay in Minutes           25893 non-null  float64
 24  satisfaction                       25976 non-null  object 
dtypes: float64(1), int64(19), object(5)
memory usage: 5.0+ MB
```

```
Bd.describe()
```

|       | Unnamed: 0   | id            | Age          | Flight Distance | Inflight wifi service | Departure/Arrival time convenient | Ease of Online booking | Gate location | Food and drink | Online boarding | Seat comfort | Inflight entertainment | On-board service | Leg room service | Baggage handling | Checkin service | Inflight service | Cleanliness  | Departure Delay in Minutes | Arrival Delay in Minutes |
| ----- | ------------ | ------------- | ------------ | --------------- | --------------------- | --------------------------------- | ---------------------- | ------------- | -------------- | --------------- | ------------ | ---------------------- | ---------------- | ---------------- | ---------------- | --------------- | ---------------- | ------------ | -------------------------- | ------------------------ |
| count | 25976.000000 | 25976.000000  | 25976.000000 | 25976.000000    | 25976.000000          | 25976.000000                      | 25976.000000           | 25976.000000  | 25976.000000   | 25976.000000    | 25976.000000 | 25976.000000           | 25976.000000     | 25976.000000     | 25976.000000     | 25976.000000    | 25976.000000     | 25976.000000 | 25976.00000                | 25893.000000             |
| mean  | 12987.500000 | 65005.657992  | 39.620958    | 1193.788459     | 2.724746              | 3.046812                          | 2.756775               | 2.977094      | 3.215353       | 3.261665        | 3.449222     | 3.357753               | 3.385664         | 3.350169         | 3.633238         | 3.314175        | 3.649253         | 3.286226     | 14.30609                   | 14.740857                |
| std   | 7498.769632  | 37611.526647  | 15.135685    | 998.683999      | 1.335384              | 1.533371                          | 1.412951               | 1.282133      | 1.331506       | 1.355536        | 1.320090     | 1.338299               | 1.282088         | 1.318862         | 1.176525         | 1.269332        | 1.180681         | 1.319330     | 37.42316                   | 37.517539                |
| min   | 0.000000     | 17.000000     | 7.000000     | 31.000000       | 0.000000              | 0.000000                          | 0.000000               | 1.000000      | 0.000000       | 0.000000        | 1.000000     | 0.000000               | 0.000000         | 0.000000         | 1.000000         | 1.000000        | 0.000000         | 0.000000     | 0.00000                    | 0.000000                 |
| 25%   | 6493.750000  | 32170.500000  | 27.000000    | 414.000000      | 2.000000              | 2.000000                          | 2.000000               | 2.000000      | 2.000000       | 2.000000        | 2.000000     | 2.000000               | 2.000000         | 2.000000         | 3.000000         | 3.000000        | 3.000000         | 2.000000     | 0.00000                    | 0.000000                 |
| 50%   | 12987.500000 | 65319.500000  | 40.000000    | 849.000000      | 3.000000              | 3.000000                          | 3.000000               | 3.000000      | 3.000000       | 4.000000        | 4.000000     | 4.000000               | 4.000000         | 4.000000         | 4.000000         | 3.000000        | 4.000000         | 3.000000     | 0.00000                    | 0.000000                 |
| 75%   | 19481.250000 | 97584.250000  | 51.000000    | 1744.000000     | 4.000000              | 4.000000                          | 4.000000               | 4.000000      | 4.000000       | 4.000000        | 5.000000     | 4.000000               | 4.000000         | 4.000000         | 5.000000         | 4.000000        | 5.000000         | 4.000000     | 12.00000                   | 13.000000                |
| max   | 25975.000000 | 129877.000000 | 85.000000    | 4983.000000     | 5.000000              | 5.000000                          | 5.000000               | 5.000000      | 5.000000       | 5.000000        | 5.000000     | 5.000000               | 5.000000         | 5.000000         | 5.000000         | 5.000000        | 5.000000         | 5.000000     | 1128.00000                 | 1115.000000              |

```
print(Bd.iloc[:, 24])
```

```
0                      satisfied
1                      satisfied
2        neutral or dissatisfied
3                      satisfied
4                      satisfied
                  ...           
25971    neutral or dissatisfied
25972                  satisfied
25973    neutral or dissatisfied
25974                  satisfied
25975    neutral or dissatisfied
Name: satisfaction, Length: 25976, dtype: object
```

```
Bd['satisfaction_number'] = Bd.iloc[:, 24].replace({'satisfied': 1, 'neutral or dissatisfied': 0}).astype('int64')
Bd.info()
```

```
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 25976 entries, 0 to 25975
Data columns (total 26 columns):
 #   Column                             Non-Null Count  Dtype  
---  ------                             --------------  -----  
 0   Unnamed: 0                         25976 non-null  int64  
 1   id                                 25976 non-null  int64  
 2   Gender                             25976 non-null  object 
 3   Customer Type                      25976 non-null  object 
 4   Age                                25976 non-null  int64  
 5   Type of Travel                     25976 non-null  object 
 6   Class                              25976 non-null  object 
 7   Flight Distance                    25976 non-null  int64  
 8   Inflight wifi service              25976 non-null  int64  
 9   Departure/Arrival time convenient  25976 non-null  int64  
 10  Ease of Online booking             25976 non-null  int64  
 11  Gate location                      25976 non-null  int64  
 12  Food and drink                     25976 non-null  int64  
 13  Online boarding                    25976 non-null  int64  
 14  Seat comfort                       25976 non-null  int64  
 15  Inflight entertainment             25976 non-null  int64  
 16  On-board service                   25976 non-null  int64  
 17  Leg room service                   25976 non-null  int64  
 18  Baggage handling                   25976 non-null  int64  
 19  Checkin service                    25976 non-null  int64  
 20  Inflight service                   25976 non-null  int64  
 21  Cleanliness                        25976 non-null  int64  
 22  Departure Delay in Minutes         25976 non-null  int64  
 23  Arrival Delay in Minutes           25893 non-null  float64
 24  satisfaction                       25976 non-null  object 
 25  satisfaction_number                25976 non-null  int64  
dtypes: float64(1), int64(20), object(5)
memory usage: 5.2+ MB
```

```
new_Bd = Bd.select_dtypes(include=['int64'])
new_Bd.info()
```

```
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 25976 entries, 0 to 25975
Data columns (total 20 columns):
 #   Column                             Non-Null Count  Dtype
---  ------                             --------------  -----
 0   Unnamed: 0                         25976 non-null  int64
 1   id                                 25976 non-null  int64
 2   Age                                25976 non-null  int64
 3   Flight Distance                    25976 non-null  int64
 4   Inflight wifi service              25976 non-null  int64
 5   Departure/Arrival time convenient  25976 non-null  int64
 6   Ease of Online booking             25976 non-null  int64
 7   Gate location                      25976 non-null  int64
 8   Food and drink                     25976 non-null  int64
 9   Online boarding                    25976 non-null  int64
 10  Seat comfort                       25976 non-null  int64
 11  Inflight entertainment             25976 non-null  int64
 12  On-board service                   25976 non-null  int64
 13  Leg room service                   25976 non-null  int64
 14  Baggage handling                   25976 non-null  int64
 15  Checkin service                    25976 non-null  int64
 16  Inflight service                   25976 non-null  int64
 17  Cleanliness                        25976 non-null  int64
 18  Departure Delay in Minutes         25976 non-null  int64
 19  satisfaction_number                25976 non-null  int64
dtypes: int64(20)
memory usage: 4.0 MB
```

```
from sklearn.linear_model import LogisticRegression

X = new_Bd.drop('satisfaction_number', axis=1)  # Features
y = new_Bd['satisfaction_number']  # Target
```

```
model = LogisticRegression(max_iter=1000)
model.fit(X, y)
```

```
LogisticRegression(max_iter=1000)
```

In a Jupyter environment, please rerun this cell to show the HTML representation or trust the notebook.\
On GitHub, the HTML representation is unable to render, please try loading this page with nbviewer.org.

```
coefficients = model.coef_
print(coefficients)
```

```
[[-5.18027052e-05 -1.16258989e-05 -2.80761473e-02  3.95433258e-04
   7.36834576e-02 -7.33795504e-02  2.20575820e-02 -5.02928419e-02
   3.44141436e-02  1.39971393e-01  7.60752048e-02  1.00156931e-01
   6.77428471e-02  6.52574668e-02  3.40855476e-02  4.14320968e-02
   3.04496795e-02  6.91197925e-02 -6.33084903e-03]]
```

```
intercept = model.intercept_
print(intercept)
```

```
[-0.01461123]
```

```
predictions = model.predict(X)
print(predictions)
```

```
[1 1 1 ... 0 1 0]
```

### Unidad Dos: Modelos de inventario Deterministicos:[#](broken-reference)

***

En general, la complejidad de los modelos de inventario depende de si la demanda es determinística o probabilística. Dentro de ambas categorías, la demanda puede variar, o no, con el tiempo. el patrón de la demanda en un modelo de inventario puede asumir uno de cuatro tipos:

1. Determinístico y constante(estático)con el tiempo.
2. Determinístico y variable (dinámico) con el tiempo.
3. Probabilístico y estacionario a lo largo del tiempo.
4. Probabilístico y no estacionario a lo largo del tiempo.

Esta clasificación supone la disponibilidad de datos confiables para pronosticar la futura demanda.

En función del desarrollo de modelos de inventario, la primera categoría es la más sencilla analíticamente, y la cuarta es la más compleja. Por otra parte, la primera categoría es la menos probable que ocurra en la práctica, y la cuarta es la más prevalente.

### Definicion de modelos de inventario[#](broken-reference)

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

\\\[\left(\genfrac{}{}{0pt}{}{costo\ total}{de\ inventario}\right) =\left(\genfrac{}{}{0pt}{}{costo\ de}{compra}\right)+\left(\genfrac{}{}{0pt}{}{costo\ de}{preparacion}\right)+\left(\genfrac{}{}{0pt}{}{costo\ de}{almacenamiento}\right)+\left(\genfrac{}{}{0pt}{}{costo\ de}{faltante}\right)\\]

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

```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
```

```
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

```
---------------------------------------------------------------------------
StdinNotImplementedError                  Traceback (most recent call last)
Cell In[14], line 12
      9     return q, tiempo_entre_pedidos, costo_total
     11 # Pedir al usuario que ingrese los valores de los parámetros del inventario
---> 12 costo_producto = float(input("Ingrese el costo del producto por unidad: "))
     13 costo_orden = float(input("Ingrese el costo por orden: "))
     14 costo_almacenamiento = float(input("Ingrese el costo de almacenamiento por unidad por año: "))

File ~/anaconda3/lib/python3.10/site-packages/ipykernel/kernelbase.py:1172, in Kernel.raw_input(self, prompt)
   1165 """Forward raw_input to frontends
   1166 
   1167 Raises
   1168 ------
   1169 StdinNotImplementedError if active frontend doesn't support stdin.
   1170 """
   1171 if not self._allow_stdin:
-> 1172     raise StdinNotImplementedError(
   1173         "raw_input was called, but this frontend does not support input requests."
   1174     )
   1175 return self._input_request(
   1176     str(prompt),
   1177     self._parent_ident["shell"],
   1178     self.get_parent("shell"),
   1179     password=False,
   1180 )

StdinNotImplementedError: raw_input was called, but this frontend does not support input requests.
```

```
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

```
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

#### Intentemos graficar el comportamiento de un Articulo de Inventario en el tiempo usando colab[#](broken-reference)

En el siguiente ejercicio se pretende generar el comportamiento del inventario a lo largo del periodo \\(t\_0\\), para posteriormente graficarlo.

se podran variar cantidades de productos

```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

```
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

### Ejercicios de Practica del modelo de inventario[#](broken-reference)

Vamos a poner en practica la teoria descrita en el cuaderno anterior

* debera realizar los siguientes ejercicios a mano en una hoja limpia con su calculadora
* Realizara los siguientes ejercicios usando google colab como se describe en el documento.

### Ejercicios EOQ[#](broken-reference)

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

```
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

\\\[ Q\_{epq}=\sqrt{\left(\frac{2DS}{h\left(1-\frac{d}{q}\right)}\right)} \\]

#### Ejemplo EPQ[#](broken-reference)

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

#### gestion de inventarios y abastecimiento:[#](broken-reference)

investigar:

1. Inventario ABC
2. Mterial Criticaly
3. Quantity Duiscount Model

### Unidad tres: Modelos de Transporte[#](broken-reference)

### Instrucciones para el uso de la libreria Pulp:[#](broken-reference)

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

```
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

```
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

```
pip install pulp
```

#### Diseño de rutas con python[#](broken-reference)

La planificacion de rutas, centra sus esfuerzos en la planificacion de recorridos optimos para la entrega de productos o el cumplimiento de los objetivos del sistema, teniendo en cunta variables especificas como:

1. tiempo
2. costo
3. restricciones de capacidad

**Objetivo de diseñar una ruta**[**#**](broken-reference)

el objetivo puede ser:

1. Minimizar costos
2. optimizar tiempos de entregas
3. Mejorar la utilizacion de recursos

**Modelos de rutas:**[**#**](broken-reference)

en logistica tenemos modelos varios de rutas, los que modelan ecenarios especificos de la realidad, estos modelos intentan dar respuesta a la realidad con base en las restricciones especificas, los modelos generales son:

1. TSP - travel salesman problem, o problema del agente viajero: Encontrar la ruta más corta que visita todos los puntos de entrega una sola vez y regresa al punto de partida.
2. VRP - Problema de Ruteo de Vehiculos: Asignar una flota de vehículos para atender a un conjunto de clientes, minimizando costos y respetando restricciones de capacidad y tiempo.
3. VRPTW - VRO con ventanas de tiempo: Similar al VRP, pero con la restricción de que cada cliente debe ser atendido dentro de una ventana de tiempo específica.

***

### DISEÑO DE RUTAS UTILIZANDO PYTHON.[#](broken-reference)

Existen librerías y algoritmos que facilitan el diseño de rutas en Python.

```
Pulp: Una librería para resolver problemas de optimización, incluyendo el TSP y VRP.
```

hagamnos el ejemplo donde tenemos un problema de asignación de tareas a trabajadores, donde cada trabajador debe realizar una sola tarea y cada tarea debe ser realizada por un solo trabajador. La función objetivo es minimizar el costo total de la asignación

```
!pip install Pulp
```

```
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

**NetworkX** es una biblioteca de Python que se utiliza para crear, manipular y analizar redes complejas. Es ampliamente usada en el campo de la ciencia de redes, en donde se necesitan realizar análisis detallados de la estructura de grafos, como encontrar caminos mínimos, detectar comunidades, calcular centralidad, entre otros.

**Características principales:**[**#**](broken-reference)

1. Creación y manipulación de grafos: Soporta varios tipos de grafos (dirigidos, no dirigidos, multigrafos) y permite agregar nodos y aristas con atributos.
2. Análisis de redes: Proporciona una amplia gama de algoritmos de teoría de grafos para realizar análisis estructural, como el cálculo de centralidades (grado, intermediación, cercanía), detección de componentes conectados, caminos mínimos, detección de comunidades, etc.
3. Tipos de grafos: Soporta grafos dirigidos (donde las conexiones tienen dirección), no dirigidos y multigrafos (donde puede haber múltiples aristas entre dos nodos).

```
!pip install networkx==2.8.8
```

```
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

#### Ejemplo 1:[#](broken-reference)

**Ejemplo uno:** MG Auto tiene tres plantas: en Los Ángeles, Detroit y New Orleans; y dos centros principales de distribución en Denver y en Miami. Las capacidades de las tres plantas durante el próximo trimestre serán 1000, 1500 y 1200 autos. Las demandas trimestrales en los dos centros de distribución son 2300 y 1400 autos. El kilometraje entre las fábricas y los centros de distribución

* La empresa transportista cobra 8 centavos por KM y por auto. El costo de transporte por auto, en las distintas rutas y redondeado hasta el $ más próximo
* TABLA 1

|             | Denver | Mimami |
| ----------- | ------ | ------ |
| Los Angeles | 1000   | 2690   |
| Detroit     | 1250   | 1350   |
| New Orleans | 1275   | 850    |

* TABLA 2

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

```
# Importar la biblioteca PuLP
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

#### Ejemplo 2:[#](broken-reference)

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

* \\(Z\\): representa el costo total de transporte.
* \\(c\_{ij}\\): es el costo de transportar una unidad del origen \\(i\\) al destino \\(j\\).
* \\(x\_{ij}\\): es la cantidad de unidades transportadas del origen \\(i\\) al destino \\(j\\).

Las restricciones de capacidad se expresan como:

\begin{align\*} \sum\_{j=1}^{4} x\_{1j} &\leq 60\
\sum\_{j=1}^{4} x\_{2j} &\leq 70\
\sum\_{j=1}^{4} x\_{3j} &\leq 80 \end{align\*}

**Donde:**

La restricción \\(\sum\_{j=1}^{4} x\_{ij} \leq C\_i\\) indica que la cantidad total de productos que se envían desde el origen \\(i\\) no puede superar su capacidad máxima \\(C\_i\\). Las restricciones de demanda se expresan como:

\begin{align\*} \sum\_{i=1}^{3} x\_{i1} &\geq 50\
\sum\_{i=1}^{3} x\_{i2} &\geq 70\
\sum\_{i=1}^{3} x\_{i3} &\geq 80\
\sum\_{i=1}^{3} x\_{i4} &\geq 30 \end{align\*}

**Donde:**

* La restricción \\(\sum\_{i=1}^{3} x\_{ij} \geq D\_j\\) indica que la cantidad total de productos que se envían al destino \\(j\\) debe ser al menos igual a su demanda \\(D\_j\\)

```
import pulp
```

```
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

***

#### Ejercicios de la Unidad Tres.[#](broken-reference)

***

1. En **el ejemplo 1**, suponer que la capacidad de la planta de Detroit es 1300 automóviles (en lugar de 1500). La oferta total (3700 autos) es menor que la demanda total (4300 autos), lo que quiere decir que no será satisfecha parte de la demanda en Denver y Miami. Como la demanda es mayor que la oferta se agrega una fuente _(planta) ficticia_ con una capacidad de 200 automóviles ( 3700  3500) para **balancear** el modelo de transporte. En este caso, el costo de transporte por unidad, desde la planta ficticia a los dos destinos es cero, porque no existe esa fábrica. El costo de transporte por unidad desde la fuente ficticia a los destinos puede asumir también valores positivos. _Por ejemplo,_ para asegurar que Miami recibe toda su demanda, se asignará un costo (penalización) alto de transporte por unidad al elemento cero, desde la fuente ficticia hasta Miami.

* resuelva este modelo usando simplex a mano y luego en Colab, compare los resultados.
* Describa el codigo usado.

2. Una tienda produce tres productos diferentes. Los productos se envían a tres almacenes. Los costos de envío por unidad, la oferta y la demanda de cada centro de distribución se muestran en las tablas a continuación. Determine la cantidad de productos que se deben enviar de la fábrica a cada centro de distribución para minimizar los costos de envío.

|          | Almacén A | Almacén B | Almacén C | Oferta |
| -------- | --------- | --------- | --------- | ------ |
| Tienda 1 | $10       | $8        | $7        | 200    |
| Tienda 2 | $5        | $12       | $6        | 300    |
| Tienda 3 | $4        | $7        | $11       | 400    |
| Demanda  | 150       | 250       | 200       |        |

3. Una empresa tiene tres tiendas en ciudades diferentes y dos almacenes en otras ciudades diferentes. Cada tienda oferta productos diferentes. Los costos de envío por unidad, la capacidad de producción y la demanda de cada almacén se muestran en las tablas a continuación. Determine la cantidad de productos que se deben enviar a los almacenes para satisfacer la demanda y minimizar los costos de envío.

|          | Almacén A | Almacén B | Almacén C | Almacén D | Oferta |
| -------- | --------- | --------- | --------- | --------- | ------ |
| Tienda 1 | $4        | $6        | $9        | $5        | 300    |
| Tienda 2 | $7        | $3        | $5        | $8        | 400    |
| Tienda 3 | $2        | $5        | $11       | $7        | 500    |
| Demanda  | 400       | 400       | 300       | 300       |        |

4. Una empresa tiene tres tiendas y cuatro almacenes. Los costos de envío por unidad, la capacidad de producción y la demanda de cada almacén se muestran en las tablas a continuación. Determine la cantidad de productos que se deben enviar de las fábricas a los almacenes para satisfacer la demanda de cada almacén y minimizar los costos de envío.

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

5. Tres ciudades se abastecen de electricidad de tres centrales eléctricas con capacidades de 25, 40 y 30 megawatts (MW). Las demandas máximas en las tres ciudades se estiman en 30, 35 y 25 MW. El precio por MW en las tres ciudades se muestra en la tabla

| Plantas\Ciudad | \\(C\_1\\) | \\(C\_2\\) | \\(C\_3\\) |
| -------------- | ---------- | ---------- | ---------- |
| \\(P\_1\\)     | 600        | 700        | 400        |
| \\(P\_2\\)     | 320        | 300        | 350        |
| \\(P\_3\\)     | 500        | 480        | 450        |

Durante el mes de agosto hay un aumento de 20% en la demanda de cada ciudad, que se puede satisfacer comprando electricidad a otra red, a una tasa elevada de $1000 por MW. Sin embargo, la red no está conectada con la ciudad 3. La empresa eléctrica desea determinar el plan más económico para distribuir y comprar la energía adicional.

```
1. Formule el problema como un modelo de transporte. en COlab usando latex.
2. Resuelva el problema con COLAB y determine un plan óptimo de distribución para la empresa eléctrica.
3. Determine el costo de la electricidad adicional comprada por cada una de las tres ciudades.
```

6. La Compañía ABC tiene tres plantas de producción de Productos para bebés que deben distribuirse a cuatro centros de distribución. Las plantas 1, 2 y 3 producen 12, 17 y 11 cargamentos por mes, respectivamente. Cada centro de distribución necesita recibir 10 cargamentos por mes. En la siguiente tabla se da la distancia de cada planta a su respectivo centro de distribución:

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

7. Tom desearía comprar exactamente 3 litros de cerveza casera hoy y al menos 4 litros mañana. Dick quiere vender un máximo de 5 litros en total a un precio de 3.00usd por litro hoy y de 2.70Usd por litro mañana. Harry está dispuesto a vender un máximo de 4 litros en total, a un precio de 2.90Usd por litro hoy y 2.80Usd por litro mañana.

Tom quiere saber cuánto debe comprar a cada uno para minimizar su costo y a la vez cumplir con los requisitos mínimos para satisfacer su sed.

```
    1. Formule el modelo de programación lineal teorico y algebraico.
    2. Formule este problema como un problema de transporte mediante la construcción de la tabla de parámetros apropiada.
    3. Obtenga una solución óptima para este problema. \
```

8. La corporación Versatech producirá tres productos nuevos. En este momento, cinco de sus plantas tienen exceso de capacidad de producción. El costo unitario respectivo de fabricación del primer producto será de 41usd, 39usd, 42usd, 38usd y 39usd en las plantas 1, 2, 3, 4 y 5, El costo unitario de fabricación del segundo producto será de 55usd, 51usd, 56usd, 52usd y 53usd en las plantas respectivas 1, 2, 3, 4 y 5; y para el tercer producto será de 48usd, 45usd y 50usd en las plantas respectivas 1, 2 y 3, pero las plantas 4 y 5 no pueden fabricar este producto. Los pronósticos de ventas indican que la producción diaria debe ser de 700, 1 000 y 900 unidades de los productos 1, 2 y 3, respectivamente. \\
9. Las plantas 1, 2, 3, 4 y 5 tienen capacidades para producir 400, 600, 400, 600 y 1 000 unidades diarias, sin importar el producto o combinación de productos. Suponga que cualquier planta que tiene capacidad y posibilidad de fabricarlos podrá producir cualquier cantidad de productos y con cualquier combinación. La administración desea asignar los nuevos productos a las plantas con el mínimo costo total de fabricación.
   1. Formule este problema como un problema de transporte mediante la construcción de la tabla de parámetros apropiada.
   2. Obtenga una solución óptima para este problema.
   3. realice este ejercicio en el entorno de google colab en latex y codigo \\
10.
    * la empresa XYZ produce 2 productos \\(X\_1\\) y \\(X\_2\\) en dos plantas diferentes \\(Pl\_1\\) y \\(Pl\_2\\) cada uno de los productos necesita de diferentes Materias primas para ser elaborado segun la siguiente tabla:

|            | Mp1 | Mp2 | Mp3 | Tiempo de Prod       |
| ---------- | --- | --- | --- | -------------------- |
| \\(X\_1\\) | 2   | 3   | 1   | \\(4\frac{min}{u}\\) |
| \\(X\_2\\) | 3   | 1   | 0   | \\(3\frac{min}{u}\\) |

La empresa cuenta son 5 proveedores

|            | \\(Mp\_1\\) | \\(Mp\_2\\) | \\(Mp\_3\\) |
| ---------- | ----------- | ----------- | ----------- |
| \\(S\_1\\) | 1000        | 800         | 1000        |
| \\(S\_2\\) | 4000        | 2000        | -           |
| \\(S\_3\\) | -           | 9000        | 2000        |
| \\(S\_4\\) | 5000        | 3000        | 900         |
| \\(S\_5\\) | 2000        | 4000        | 1000        |

costos por ser enviadas las unidades (u/usd)

|            | \\(CtMp\_1\\) | \\(CtMp\_2\\) | \\(CtMp\_3\\) |
| ---------- | ------------- | ------------- | ------------- |
| \\(S\_1\\) | 2             | 2             | 3             |
| \\(S\_2\\) | 2             | 2,5           | -             |
| \\(S\_3\\) | -             | 3             | 1             |
| \\(S\_4\\) | 4             | 2             | 4             |
| \\(S\_5\\) | 2             | 2,2           | 2             |

Costo fijo por proveedor:

|            | Costo fijo |
| ---------- | ---------- |
| \\(S\_1\\) | 90 usd     |
| \\(S\_2\\) | 110 usd    |
| \\(S\_3\\) | 85 usd     |
| \\(S\_4\\) | 97 usd     |
| \\(S\_5\\) | 60 usd     |

|            | Costo variable |
| ---------- | -------------- |
| \\(S\_1\\) | 0,5 usd        |
| \\(S\_2\\) | 0,8 usd        |
| \\(S\_3\\) | 0,7 usd        |
| \\(S\_4\\) | 0,2 usd        |
| \\(S\_5\\) | 0,6 usd        |

Distancia de las plantas a los prioveedores

|            | \\(Plp\_1\\) | \\(Plp\_2\\) |
| ---------- | ------------ | ------------ |
| \\(S\_1\\) | 70           | 92           |
| \\(S\_2\\) | 67           | 92           |
| \\(S\_3\\) | 85           | 83           |
| \\(S\_4\\) | 70           | 72           |
| \\(S\_5\\) | 90           | 94           |

1. encuentre el modelo optimo para reducir lso costos y suplir con la demanda
2. debe nivelar el sistema por medio del hallazgo de las unidades de demanda de acuerdo con las capacidades del sistema
3. realice este ejercicio en google colab y modele su respuesta

```
1. encuentre el modelo optimo que minimice el costo del sistema
2. nivele el sistema con base en la oferta
3. realice este ejercicio en google colab
```

#### Ejercicio numero 6 del libro hamndy taha - investigacion de operaciones capituo 5[#](broken-reference)

Tres ciudades abastecen de electricidad de ytres centrales electricas con capacidades de 25, 40 y 30 megawatts. las demandas maximas en las tres ciudades se estiman en 30, 35 y 25 megawatts, el precio por megawatts en las tres ciudades se muestra en la siguiente tabla.

* Tabla uno.

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

**RESOLVEMOS**

* Tabla de capacidad vs demanda

|              |     | Ciudad |     |                |
| ------------ | --- | ------ | --- | -------------- |
| Planta       | 1   | 2      | 3   | Capacidad MWts |
| 1            | 600 | 700    | 400 | 30             |
| 2            | 320 | 300    | 350 | 35             |
| 3            | 500 | 480    | 450 | 25             |
| Demanda Mwts | 25  | 40     | 30  | desnivelado    |

Tabla 2 - nivelamos el sistema con un agente ficticio

|              |     | Ciudad |     |         |                |
| ------------ | --- | ------ | --- | ------- | -------------- |
| Planta       | 1   | 2      | 3   | 4(fict) | Capacidad MWts |
| 1            | 600 | 700    | 400 | M       | 30             |
| 2            | 320 | 300    | 350 | M       | 35             |
| 3            | 500 | 480    | 450 | M       | 25             |
| Demanda Mwts | 25  | 40     | 30  | 5       | Nivelado       |

tabla 3 - modelo teorico

|                |                              | Ciudad \\(j\\)             |                            |                            |                |
| -------------- | ---------------------------- | -------------------------- | -------------------------- | -------------------------- | -------------- |
| Planta \\(i\\) | 1                            | 2                          | 3                          | 4(fict)                    | Capacidad MWts |
| 1              | \\(X\_{11}\\)\*\\(C\_{11}\\) | \\(X\_{12}\\)\\(C\_{12}\\) | \\(X\_{13}\\)\\(C\_{13}\\) | \\(X\_{14}\\)\\(C\_{14}\\) | \\(C\_1\\)     |
| 2              | \\(X\_{21}\\)\\(C\_{21}\\)   | \\(X\_{22}\\)\\(C\_{22}\\) | \\(X\_{23}\\)\\(C\_{23}\\) | \\(X\_{24}\\)\\(C\_{24}\\) | \\(C\_2\\)     |
| 3              | \\(X\_{31}\\)\\(C\_{31}\\)   | \\(X\_{32}\\)\\(C\_{32}\\) | \\(X\_{33}\\)\\(C\_{33}\\) | \\(X\_{34}\\)\\(C\_{34}\\) | \\(C\_3\\)     |
| Demanda Mwts   | \\(D\_{1}\\)                 | \\(D\_{2}\\)               | \\(D\_{3}\\)               | \\(D\_{4}\\)               | Nivelado       |

1. Identificacion de variables:

* \\(P\_i\\) = Capacidad de plantas \\(i\\)
* \\(D\_j\\) = Demanda de energia de las Ciudades \\(j\\)
* \\(C\_{ij}\\) = Costo de transferencia de energia de la planta \\(i\\) hasta la ciudad \\(j\\)
* \\(X\_{ij}\\) = Cantidad de Mwts de energia de la planta \\(i\\) a la ciudad \\(j\\)

2. Planteamos el modelo Teorico:

* F.O = Minimizacion de los costos de trasnferencia entre las plantas \\(i\\) y las ciudades \\(j\\)

\\\[Z\_{min} = \sum\_{i = 1}^{i=n}\sum\_{j = 1}^{j=m} (C\_{ij}\*X\_{ij})\\]

* Sujeto a las siguientes restricciones:

1. restriccion de capacidad $\\( 1.\ \sum\_{i}^{n}\sum\_{j}^{m}X\_{ij} ≤ P\_j \ ∀ i={1,2,3}; j={1} \\\ 2.\ \sum\_{i}^{n}\sum\_{j}^{m}X\_{ij} ≤ P\_j \ ∀ i={1,2,3}; j={2} \\\ 3.\ \sum\_{i}^{n}\sum\_{j}^{m}X\_{ij} ≤ P\_j \ ∀ i={1,2,3}; j={3} \\\ 4.\ \sum\_{i}^{n}\sum\_{j}^{m}X\_{ij} ≤ P\_j \ ∀ i={1,2,3}; j={4} \\\ \\)$
2. restriccion de Demanda $\\( 1.\ \sum\_{i}^{n}\sum\_{j}^{m}X\_{ij} \le D\_i \ ∀ i={1}; j={1,2,3,4}\\\ 2.\ \sum\_{i}^{n}\sum\_{j}^{m}X\_{ij} \le D\_i \ ∀ i={2}; j={1,2,3,4}\\\ 3.\ \sum\_{i}^{n}\sum\_{j}^{m}X\_{ij} \le D\_i \ ∀ i={3}; j={1,2,3,4}\\\ \\)$
3. restriccion de no negatividad:

\\\[ 1. X\_{ij} \ge 0 \\]

***

#### Modelo Algebraico[#](broken-reference)

|                |                    | Ciudad \\(j\\)   |                  |                |              |
| -------------- | ------------------ | ---------------- | ---------------- | -------------- | ------------ |
| Planta \\(i\\) | 1                  | 2                | 3                | 4(fict)        | Demanda MWts |
| 1              | \\(X\_{11}\\)\*600 | \\(X\_{12}\\)700 | \\(X\_{13}\\)400 | \\(X\_{14}\\)M | 30           |
| 2              | \\(X\_{21}\\)320   | \\(X\_{22}\\)300 | \\(X\_{23}\\)350 | \\(X\_{24}\\)M | 35           |
| 3              | \\(X\_{31}\\)500   | \\(X\_{32}\\)480 | \\(X\_{33}\\)450 | \\(X\_{34}\\)M | 25           |
| Capacidad Mwts | 25                 | 40               | 30               | 5              | NIvelado     |

**Formulamos la Funcion objetivo**

\\\[ Z\_{min} = X\_{11}\*600 + X\_{12}\*700+ X\_{13}\*400 + X\_{14}\*M + X\_{21}\*320 + X\_{22}\*300 + X\_{23}\*350+ X\_{24}\* M + X\_{31}\*500 + X\_{32}\*480+ X\_{33}\* 450 + X\_{34}\* M \\]

sa:

\\\[\begin{split} 1. X\_{11} + X\_{12}+ X\_{13}+X\_{14} \le 30 \\\ 2. X\_{21} + X\_{22}+ X\_{23}+X\_{24} \le 35 \\\ 3. X\_{31} + X\_{32}+ X\_{33}+X\_{34} \le 25 \\\ 4. X\_{11}+X\_{21}+X\_{31} \le 25 \\\ 5. X\_{12}+X\_{22}+X\_{32} \le 40 \\\ 6. X\_{13}+X\_{23}+X\_{33} \le 30 \\\ 7. X\_{14}+X\_{24}+X\_{34} \le 5\\\ 8. X\_{ij} \ge 0\\\ \end{split}\\]

***

Resolvemos usando el metodo de la esquina nor oeste

***

|           |     |     | ciudad |   |         |
| --------- | --- | --- | ------ | - | ------- |
| Planta    | 1   | 2   | 3      | 4 | Demanda |
| 1         | 600 | 700 | 400    | M |         |
|           |     |     |        |   | 30      |
| 2         | 320 | 300 | 350    | M |         |
|           |     |     |        |   | 35      |
| 3         | 500 | 480 | 450    | M |         |
|           |     |     |        |   | 25      |
| Capacidad | 25  | 40  | 30     | 5 |         |

***

**Solucion a los ejercicios:**[**#**](broken-reference)

***

**Ejercicio numero uno:**[**#**](broken-reference)

```
# Importar la biblioteca PuLP
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
y1 = pulp.LpVariable("Fuente ficticia a Denver", lowBound=0, cat='Integer')
y2 = pulp.LpVariable("Fuente ficticia a Miami", lowBound=0, cat='Integer')


# Definir la función objetivo
problem +=(80*x11 + 215*x12 + 100*x21 + 108*x22 + 102*x31 + 68*x32 + 0*y1 + 0*y2)

# Definir las restricciones de oferta y demanda
problem += x11 + x12 <= 1000, "Oferta Los Angeles"
problem += x21 + x22 <= 1300, "Oferta Detroit"
problem += x31 + x32 <= 1200, "Oferta New Orleans"
problem += y1 + y2 <= 200, "Oferta Fuente Ficticia"
problem += x11 + x21 + x31+ y1 == 2300, "Demanda Denver"
problem += x12 + x22 + x32 + y2 == 1400, "Demanda Miami"

# Resolver el problema utilizando el método simplex
problem.solve()

# Imprimir el resultado
print("Estado:", pulp.LpStatus[problem.status])
print("Costo total de transporte: $", round(pulp.value(problem.objective),2))

for variable in problem.variables():
    print(variable.name, "=", variable.varValue)
```

**Ejercicio Numero Dos**[**#**](broken-reference)

```
import pandas as pd

# Definir los datos como un diccionario
datos = {'-': ['Tienda 1', 'Tienda 2', 'Tienda 3', 'Demanda'],
         'Almacén A': ['10$', '5$', '4$', '150'],
         'Almacén B': ['8$', '12$', '7$', '250'],
         'Almacén C': ['7$', '6$', '11$', '200'],
         'Oferta': ['200', '300', '400', '-']}

# Convertir el diccionario a un objeto DataFrame de pandas
tabla = pd.DataFrame(datos)


# Imprimir la tabla
print(tabla)
```

```
import graphviz

graph = graphviz.Graph(engine='neato')

# Crear grafo
dot = graphviz.Digraph()


# Agregar nodos
dot.node('Tienda 1', shape="circle", style="filled", fillcolor="#ADD8E6", fontsize= '10')
dot.node('Tienda 2', shape="circle", style="filled", fillcolor="#ADD8E6",fontsize= '10')
dot.node('Tienda 3', shape="circle", style="filled", fillcolor="#ADD8E6",fontsize= '10')
dot.node('Almacen A', shape="circle", style="filled", fillcolor="#ADD8E6",fontsize= '10')
dot.node('Almacen B', shape="circle", style="filled", fillcolor="#ADD8E6",fontsize= '10')
dot.node('Almacen C', shape="circle", style="filled", fillcolor="#ADD8E6",fontsize= '10')


# Agregar aristas
dot.edge('Tienda 1', 'Almacen A', label='10$',fontsize= '10')
dot.edge('Tienda 1', 'Almacen B', label='8$',fontsize= '10')
dot.edge('Tienda 1', 'Almacen C', label='7$',fontsize= '10')


dot.edge('Tienda 2', 'Almacen A', label='5$',fontsize= '10')
dot.edge('Tienda 2', 'Almacen B', label='12$',fontsize= '10')
dot.edge('Tienda 2', 'Almacen C', label='6$',fontsize= '10')


dot.edge('Tienda 3', 'Almacen A', label='4$',fontsize= '10')
dot.edge('Tienda 3', 'Almacen B', label='7$',fontsize= '10')
dot.edge('Tienda 3', 'Almacen C', label='11$',fontsize= '10')


# Mostrar grafo
dot
```

```
# Importamos la biblioteca PuLP
import pulp

# Creamos un problema de minimización
problem = pulp.LpProblem("Envío de productos", pulp.LpMinimize)

# Definimos las variables de decisión
x11 = pulp.LpVariable("Costo de productos enviados de la tienda 1 a almacen A", lowBound=0, cat='Integer')
x12 = pulp.LpVariable("Costo de productos enviados de la tienda 1 a almacen B", lowBound=0, cat='Integer')
x13 = pulp.LpVariable("Costo de productos enviados de la tienda 1 a almacen C", lowBound=0, cat='Integer')
x14 = pulp.LpVariable("Costo de productos enviados de la tienda 1 a almacen D Ficticia", lowBound=0, cat='Integer')
x21 = pulp.LpVariable("Costo de productos enviados de la tienda 2 a almacen A", lowBound=0, cat='Integer')
x22 = pulp.LpVariable("Costo de productos enviados de la tienda 2 a almacen B", lowBound=0, cat='Integer')
x23 = pulp.LpVariable("Costo de productos enviados de la tienda 2 a almacen C", lowBound=0, cat='Integer')
x24 = pulp.LpVariable("Costo de productos enviados de la tienda 2 a almacen D Ficticia", lowBound=0, cat='Integer')
x31 = pulp.LpVariable("Costo de productos enviados de la tienda 3 a almacen A ", lowBound=0, cat='Integer')
x32 = pulp.LpVariable("Costo de productos enviados de la tienda 3 a almacen B ", lowBound=0, cat='Integer')
x33 = pulp.LpVariable("Costo de productos enviados de la tienda 3 a almacen C ", lowBound=0, cat='Integer')
x34 = pulp.LpVariable("Costo de productos enviados de la tienda 3 a almacen D Ficticia", lowBound=0, cat='Integer')

# Definimos la función objetivo
problem += 10*x11 + 8*x12 + 7*x13 + 5*x21 + 12*x22 +6*x23 + 4*x31 + 7*x32 + 11*x33, "Costo total de envío"

#Definimos las restricciones de oferta
problem += x11 + x12 + x13 <= 200, "Oferta de la tienda 1"
problem += x21 + x22 + x23 <= 300, "Oferta de la tienda 2"
problem += x31 + x32 + x33 <= 400, "Oferta de la tienda 3"

#Definimos las restricciones de demanda
problem += x11 + x21 + x31 >= 150, "Demanda del almacen A"
problem += x12 + x22 + x32 >= 250, "Demanda del almacen B"
problem += x13 + x23 + x33 >= 200, "Demanda del almacen C"
problem += x14 + x24 + x34 >= 300, "Demanda del almacen D Ficticia"

#Resolvemos el problema
problem.solve()

#Imprimimos el resultado
print("Estado:", pulp.LpStatus[problem.status])
print("Costo total de envío: $", round(pulp.value(problem.objective), 2))

for variable in problem.variables():
    print(variable.name, "=", variable.varValue)
```

**Ejercicio numero Tres**[**#**](broken-reference)

```
import pandas as pd

# Crear diccionario con los datos
datos = {'Almacén A': ['4$', '7$', '2$'],
         'Almacén B': ['6$', '3$', '5$'],
         'Almacén C': ['9$', '5$', '11$'],
         'Almacén D': ['5$', '8$', '7$']}

# Convertir diccionario en dataframe de pandas
df = pd.DataFrame(datos)

# Asignar nombres de las filas y columnas
df.index = ['Tienda 1', 'Tienda 2', 'Tienda 3']
df.columns.name = 'Almacenes'

# Agregar fila y columna de oferta y demanda
df.loc['Demanda'] = ['400', '400', '300', '300']
df['Oferta'] = ['300', '400', '500', '-']

# Imprimir tabla
print(df)
```

```
import graphviz

graph = graphviz.Graph(engine='neato')

# Crear grafo
dot = graphviz.Digraph()


# Agregar nodos
dot.node('Tienda 1', shape="circle", style="filled", fillcolor="#ADD8E6", fontsize= '10')
dot.node('Tienda 2', shape="circle", style="filled", fillcolor="#ADD8E6",fontsize= '10')
dot.node('Tienda 3', shape="circle", style="filled", fillcolor="#ADD8E6",fontsize= '10')
dot.node('Almacen A', shape="circle", style="filled", fillcolor="#ADD8E6",fontsize= '10')
dot.node('Almacen B', shape="circle", style="filled", fillcolor="#ADD8E6",fontsize= '10')
dot.node('Almacen C', shape="circle", style="filled", fillcolor="#ADD8E6",fontsize= '10')
dot.node('Almacen D', shape="circle", style="filled", fillcolor="#ADD8E6",fontsize= '10')

# Agregar aristas
dot.edge('Tienda 1', 'Almacen A', label='4$',fontsize= '10')
dot.edge('Tienda 1', 'Almacen B', label='7$',fontsize= '10')
dot.edge('Tienda 1', 'Almacen C', label='2$',fontsize= '10')
dot.edge('Tienda 1', 'Almacen D', label='5$',fontsize= '10')

dot.edge('Tienda 2', 'Almacen A', label='6$',fontsize= '10')
dot.edge('Tienda 2', 'Almacen B', label='3$',fontsize= '10')
dot.edge('Tienda 2', 'Almacen C', label='5$',fontsize= '10')
dot.edge('Tienda 2', 'Almacen D', label='8$',fontsize= '10')

dot.edge('Tienda 3', 'Almacen A', label='9$',fontsize= '10')
dot.edge('Tienda 3', 'Almacen B', label='5$',fontsize= '10')
dot.edge('Tienda 3', 'Almacen C', label='11$',fontsize= '10')
dot.edge('Tienda 3', 'Almacen D', label='7$',fontsize= '10')

# Mostrar grafo
dot
```

```
# Importamos la biblioteca PuLP
import pulp

# Creamos un problema de minimización
problem = pulp.LpProblem("Envío de productos", pulp.LpMinimize)

# Definimos las variables de decisión
x11 = pulp.LpVariable("tienda 1 a almacen A", lowBound=0, cat='Integer')
x12 = pulp.LpVariable("tienda 1 a almacen B", lowBound=0, cat='Integer')
x13 = pulp.LpVariable("tienda 1 a almacen C", lowBound=0, cat='Integer')
x14 = pulp.LpVariable("tienda 1 a almacen D", lowBound=0, cat='Integer')
x21 = pulp.LpVariable("tienda 2 a almacen A", lowBound=0, cat='Integer')
x22 = pulp.LpVariable("tienda 2 a almacen B", lowBound=0, cat='Integer')
x23 = pulp.LpVariable("tienda 2 a almacen C", lowBound=0, cat='Integer')
x24 = pulp.LpVariable("tienda 2 a almacen D", lowBound=0, cat='Integer')
x31 = pulp.LpVariable("tienda 3 a almacen A", lowBound=0, cat='Integer')
x32 = pulp.LpVariable("tienda 3 a almacen B", lowBound=0, cat='Integer')
x33 = pulp.LpVariable("tienda 3 a almacen C", lowBound=0, cat='Integer')
x34 = pulp.LpVariable("tienda 3 a almacen D", lowBound=0, cat='Integer')
x41 = pulp.LpVariable("tienda 4 Ficticia a almacen A", lowBound=0, cat='Integer')
x42 = pulp.LpVariable("tienda 4 Ficticia a almacen B", lowBound=0, cat='Integer')
x43 = pulp.LpVariable("tienda 4 Ficticia a almacen C", lowBound=0, cat='Integer')
x44 = pulp.LpVariable("tienda 4 Ficticia a almacen D", lowBound=0, cat='Integer')

# Definimos la función objetivo
problem += (4*x11 + 6*x12 + 9*x13 + 5*x14 + 7*x21 + 3*x22 +5*x23 + 8*x24 + 2*x31 + 5*x32 + 11*x33 + 7*x34)

#Definimos las restricciones de oferta
problem += x11 + x12 + x13 + x14 <= 200, "Oferta de la tienda 1"
problem += x21 + x22 + x23 + x24 <= 300, "Oferta de la tienda 2"
problem += x31 + x32 + x33 + x34 <= 400, "Oferta de la tienda 3"
problem += x41 + x42 + x43 + x44 <= 500, "Oferta de la tienda 4 Ficticia"

#Definimos las restricciones de demanda
problem += x11 + x21 + x31 + x41 >= 400, "Demanda del almacen A"
problem += x12 + x22 + x32 + x42 >= 400, "Demanda del almacen B"
problem += x13 + x23 + x33 + x43 >= 300, "Demanda del almacen C"
problem += x14 + x24 + x34 + x44 >= 300, "Demanda del almacen D"

#Resolvemos el problema
problem.solve()

#Imprimimos el resultado
print("Estado:", pulp.LpStatus[problem.status])
print("Costo total de transporte: $", round(pulp.value(problem.objective), 2))

for variable in problem.variables():
    print(variable.name, "=", variable.varValue)
```

**Ejercicio Numero Cuatro**[**#**](broken-reference)

```
datos = [{'Items': 'Tienda 1', 'Almacen A': 6, 'Almacen B': 8, 'Almacen C': 10, 'Almacen D': 9, 'Almacen E': 7, 'Oferta': 500},
         {'Items': 'Tienda 2', 'Almacen A': 5, 'Almacen B': 11, 'Almacen C': 7, 'Almacen D': 4, 'Almacen E': 3,'Oferta': 400},
         {'Items': 'Tienda 3', 'Almacen A': 12, 'Almacen B': 9, 'Almacen C': 3,'Almacen D': 8, 'Almacen E': 6, 'Oferta': 300},
         {'Items': 'Demanda', 'Almacen A': 300, 'Almacen B': 400, 'Almacen C': 408,'Almacen D': 200, 'Almacen E': 400, 'Oferta': 0}]

df_datos = pd.DataFrame(datos)
df_datos = df_datos.set_index('Items' , drop= True)
df_datos
```

```
import graphviz

graph = graphviz.Graph(engine='neato')

# Crear grafo
dot = graphviz.Digraph()


# Agregar nodos
dot.node('Tienda 1', shape="circle", style="filled", fillcolor="#D8BFD8", fontsize= '10')
dot.node('Tienda 2', shape="circle", style="filled", fillcolor="#D8BFD8",fontsize= '10')
dot.node('Tienda 3', shape="circle", style="filled", fillcolor="#D8BFD8",fontsize= '10')
dot.node('Almacen A', shape="circle", style="filled", fillcolor="#D8BFD8",fontsize= '10')
dot.node('Almacen B', shape="circle", style="filled", fillcolor="#D8BFD8",fontsize= '10')
dot.node('Almacen C', shape="circle", style="filled", fillcolor="#D8BFD8",fontsize= '10')
dot.node('Almacen D', shape="circle", style="filled", fillcolor="#D8BFD8",fontsize= '10')
dot.node('Almacen E', shape="circle", style="filled", fillcolor="#D8BFD8",fontsize= '10')

# Agregar aristas
dot.edge('Tienda 1', 'Almacen A', label='6',fontsize= '10')
dot.edge('Tienda 1', 'Almacen B', label='8',fontsize= '10')
dot.edge('Tienda 1', 'Almacen C', label='10',fontsize= '10')
dot.edge('Tienda 1', 'Almacen D', label='9',fontsize= '10')
dot.edge('Tienda 1', 'Almacen E', label='7',fontsize= '10')


dot.edge('Tienda 2', 'Almacen A', label='5',fontsize= '10')
dot.edge('Tienda 2', 'Almacen B', label='11',fontsize= '10')
dot.edge('Tienda 2', 'Almacen C', label='7',fontsize= '10')
dot.edge('Tienda 2', 'Almacen D', label='4',fontsize= '10')
dot.edge('Tienda 2', 'Almacen E', label='3',fontsize= '10')

dot.edge('Tienda 3', 'Almacen A', label='12',fontsize= '10')
dot.edge('Tienda 3', 'Almacen B', label='9',fontsize= '10')
dot.edge('Tienda 3', 'Almacen C', label='3',fontsize= '10')
dot.edge('Tienda 3', 'Almacen D', label='8',fontsize= '10')
dot.edge('Tienda 3', 'Almacen E', label='6',fontsize= '10')

# Mostrar grafo
dot
```

```
import pulp

# Creamos el problema de minimización
prob = pulp.LpProblem("Problema de transporte", pulp.LpMinimize)

# Creamos las variables de decisión
x11 = pulp.LpVariable("tienda 1 a almacen A", lowBound=0, cat='Integer')
x12 = pulp.LpVariable("tienda 1 a almacen B", lowBound=0, cat='Integer')
x13 = pulp.LpVariable("tienda 1 a almacen C", lowBound=0, cat='Integer')
x14 = pulp.LpVariable("tienda 1 a almacen D", lowBound=0, cat='Integer')
x15 = pulp.LpVariable("tienda 1 a almacen E", lowBound=0, cat='Integer')
x21 = pulp.LpVariable("tienda 2 a almacen A", lowBound=0, cat='Integer')
x22 = pulp.LpVariable("tienda 2 a almacen B", lowBound=0, cat='Integer')
x23 = pulp.LpVariable("tienda 2 a almacen C", lowBound=0, cat='Integer')
x24 = pulp.LpVariable("tienda 2 a almacen D", lowBound=0, cat='Integer')
x25 = pulp.LpVariable("tienda 2 a almacen E", lowBound=0, cat='Integer')
x31 = pulp.LpVariable("tienda 3 a almacen A", lowBound=0, cat='Integer')
x32 = pulp.LpVariable("tienda 3 a almacen B", lowBound=0, cat='Integer')
x33 = pulp.LpVariable("tienda 3 a almacen C", lowBound=0, cat='Integer')
x34 = pulp.LpVariable("tienda 3 a almacen D", lowBound=0, cat='Integer')
x35 = pulp.LpVariable("tienda 3 a almacen E", lowBound=0, cat='Integer')
x41 = pulp.LpVariable("tienda 4 Ficticia a almacen A", lowBound=0, cat='Integer')
x42 = pulp.LpVariable("tienda 4 Ficticia a almacen B", lowBound=0, cat='Integer')
x43 = pulp.LpVariable("tienda 4 Ficticia a almacen C", lowBound=0, cat='Integer')
x44 = pulp.LpVariable("tienda 4 Ficticia a almacen D", lowBound=0, cat='Integer')
x45 = pulp.LpVariable("tienda 4 Ficticia a almacen E", lowBound=0, cat='Integer')

# Definimos la función objetivo
prob += (6*x11 + 8*x12 + 10*x13 + 9*x14 + 7*x15 + 5*x21 + 11*x22 + 7*x23 + 4*x24 + 3*x25 + 12*x31 + 9*x32 + 3*x33 + 8*x34 + 6*x35), "Costo total de envío"

# Definimos las restricciones
prob += x11 + x12 + x13 + x14 + x15 <= 500, "Capacidad de producción de tienda 1"
prob += x21 + x22 + x23 + x24 + x25 <= 400, "Capacidad de producción de tienda 2"
prob += x31 + x32 + x33 + x34 + x35 <= 300, "Capacidad de producción de tienda 3"
prob += x41 + x42 + x43 + x44 + x45 <= 500, "Capacidad de producción de tienda 4 Ficticia"

prob += x11 + x21 + x31 + x41 >= 300, "Demanda del almacén A"
prob += x12 + x22 + x32 + x42 >= 400, "Demanda del almacén B"
prob += x13 + x23 + x33 + x43 >= 400, "Demanda del almacén C"
prob += x14 + x24 + x34 + x44 >= 200, "Demanda del almacén D"
prob += x15 + x25 + x35 + x45 >= 400, "Demanda del almacén E"

# Resolvemos el problema
prob.solve()

# Imprimimos la solución
print("Costo total de envío: $", pulp.value(prob.objective))
for v in prob.variables():
    print(v.name, "=", v.varValue)
```

**Ejercicio Numero Cinco**[**#**](broken-reference)

1. Formulación del problema como modelo de transporte:

Variables de decisión: \begin{align\*} x\_{ij}: cantidad \ de \ electricidad \ enviada \ desde\ la \ planta \ i \ a \ la \ ciudad \ j. \end{align\*} Función objetivo:

Minimizar el costo total de distribución y compra de electricidad adicional:

\begin{align\*} \min Z= 600x\_{11} + 320x\_{12} + 500x\_{13}+700x\_{21} + 300x\_{22} + 480x\_{23}+400x\_{31} + 350x\_{32}+450x\_{33} + 1000(0.230x\_{21}+0.235x\_{22} \end{align\*}

Sujeto a:

Restricciones de capacidad de las plantas:

\begin{align\*} x\_{11} + x\_{12} + x\_{13} &\leq 25 \ x\_{21} + x\_{22} + x\_{23} &\leq 40 \ x\_{31} + x\_{32} &\leq 30\
\end{align\*}

Restricciones de demanda de las ciudades (antes del aumento de demanda):

\begin{aligned} x\_{11} + x\_{21} &\leq 30 \ x\_{12} + x\_{22} &\leq 35 \ x\_{13} + x\_{23} &\leq 25 \ \end{aligned}

Restricciones de no-negatividad:

\begin{aligned} x\_{ij} \geq 0 \end{aligned}

Además, debido a que la ciudad 3 no está conectada a la red para comprar electricidad adicional, la restricción de demanda de la ciudad 3 debe ajustarse a la demanda aumentada, es decir, \begin{aligned} x\_{13} + x\_{23} \leq 25 \cdot 1.2 \end{aligned}

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
