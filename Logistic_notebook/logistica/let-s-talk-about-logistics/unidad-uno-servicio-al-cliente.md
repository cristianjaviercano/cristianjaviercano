# Unidad Uno: Servicio Al Cliente

## Enfoque en el Servicio al Cliente:

#### Qué es el servicio al cliente en el contexto de la logística

En el ámbito de la logística, el servicio al cliente se centra en asegurar que los clientes reciban sus productos de manera efectiva y eficiente. Esto incluye garantizar tiempos de entrega precisos, comunicar cualquier retraso potencial y brindar soluciones rápidas a cualquier problema que pueda surgir durante el proceso de envío. El objetivo es optimizar cada punto de contacto con el cliente para lograr una experiencia satisfactoria que fomente la lealtad y repetición de compras.

#### Cómo Python puede ayudar a medir y mejorar el servicio al cliente

Python es una herramienta poderosa para analizar datos y optimizar procesos en el servicio al cliente. Aquí te mostramos algunas formas en que puede ser útil:

1. **Análisis de datos:** Utiliza bibliotecas como Pandas y NumPy para analizar grandes volúmenes de datos de clientes, identificar patrones y predecir tendencias.

Implementando estas soluciones, las empresas pueden ofrecer un servicio más ágil, confiable y personalizado, logrando así una mejor relación con sus clientes.

{% hint style="info" %}
Definición de servicio al cliente El servicio al cliente se refiere al conjunto de actividades, procesos y estrategias que una empresa o negocio implementa para satisfacer las necesidades y expectativas de sus clientes. Implica brindar asistencia, soporte y una experiencia positiva a los clientes antes, durante y después de una venta o interacción.
{% endhint %}

## Objetivos del SC

{% tabs %}
{% tab title="1" %}
Comprender y atender las necesidades de los clientes de manera efectiva
{% endtab %}

{% tab title="2" %}
Resolver problemas, quejas y consultas de manera oportuna y eficiente
{% endtab %}

{% tab title="3" %}
Crear relaciones duraderas y de confianza con los clientes
{% endtab %}

{% tab title="4" %}
Superar las expectativas de los clientes y generar lealtad hacia la marca
{% endtab %}

{% tab title="5" %}
Diferenciarse de la competencia a través de un servicio excepcional
{% endtab %}
{% endtabs %}

### ¿Cómo se mide la satisfacción del cliente en una empresa?[#](broken-reference)

Métodos para medir la satisfacción del cliente:

1. **Encuestas de satisfacción:** Estas son herramientas directas que permiten a las empresas obtener retroalimentación sobre la experiencia del cliente. Pueden incluir preguntas sobre la calidad del producto, la atención al cliente y la probabilidad de recomendar la empresa a otros.
2. **Análisis de comentarios en redes sociales:** Evaluar las opiniones y comentarios de los clientes en plataformas sociales puede proporcionar una visión clara de su satisfacción. Este método permite identificar tendencias y áreas de mejora.
3. **Índice de quejas y reclamaciones:** El seguimiento del número y la naturaleza de las quejas puede ayudar a las empresas a medir la satisfacción del cliente. Un aumento en las quejas puede indicar problemas en el servicio o el producto.
4. **Grupos de discusión (focus groups):** Reunir a un grupo de clientes para discutir sus experiencias y opiniones sobre un producto o servicio puede ofrecer información valiosa sobre su satisfacción y expectativas.
5. **Tasa de retención y fidelización de clientes:** Medir cuántos clientes regresan para realizar compras repetidas puede ser un indicador directo de su satisfacción. Un alto nivel de retención sugiere que los clientes están contentos con la oferta de la empresa.

[ive consultores](https://iveconsultores.com/satisfaccion-del-cliente/)

### Herramientas Matemáticas para Medir la Satisfacción del Cliente

Para analizar y medir cada uno de los ítems de una encuesta de satisfacción del cliente, las empresas pueden utilizar técnicas matemáticas que proporcionan insights valiosos sobre la experiencia del consumidor. Una de las técnicas más utilizadas es la **regresión lineal múltiple**, que ayuda a entender la relación entre variables y medir su impacto en la satisfacción.

#### Encuesta de Satisfacción

La encuesta de satisfacción es una herramienta fundamental para recopilar datos directos de los clientes. Estas encuestas pueden incluir preguntas sobre varios aspectos del servicio o producto, permitiendo a las empresas capturar las actitudes y percepciones de los clientes sobre su experiencia general.

#### Cómo Formular y Evaluar una Encuesta de Satisfacción al Cliente

Para formular una encuesta de satisfacción al cliente efectiva.

**Definir Objetivos Claros:** Establezca qué aspectos de la satisfacción del cliente desea medir (por ejemplo, calidad del servicio, atención al cliente, etc.).

Evaluar la encuesta implica revisar la calidad de las preguntas y la representatividad de las respuestas, asegurando que las conclusiones obtenidas sean precisas y útiles para la toma de decisiones.

#### Herramientas Estadísticas para Validar Preguntas de Encuestas

Al crear encuestas, es fundamental asegurarse de que las preguntas sean válidas y confiables. Aquí se describen algunas herramientas estadísticas que pueden utilizarse para esta validación:

**Análisis de Fiabilidad (Alfa de Cronbach):** Mide la consistencia interna de las preguntas en la encuesta, asegurando que todas las preguntas que pretenden medir un mismo constructo se correlacionan.

Utilizar estas herramientas garantiza que una encuesta recopila datos significativos y representativos, consecuentemente mejorando la efectividad del análisis de satisfacción del cliente.

Para explicar matemáticamente el **alfa de Cronbach**, consideremos un conjunto de preguntas diseñadas para medir un único constructo. Esta métrica evalúa la consistencia interna y se calcula con la siguiente fórmula:

\
$$[ \alpha = \frac{N \cdot \bar{c}}{\bar{v} + (N - 1) \cdot \bar{c}} ]$$

Donde:

* $$N$$ es el número de elementos (preguntas) en la escala.
* $$\bar{c}$$ es la media de las covarianzas entre los elementos.
* $$\bar{v}$$ es la media de las varianzas de los elementos individuales.

El valor de alfa varía de 0 a 1, donde un valor más alto indica una mayor consistencia interna.

### Regresión Lineal Múltiple

La regresión lineal múltiple es una técnica de análisis estadístico que se utiliza para modelar la relación entre una variable dependiente (por ejemplo, la satisfacción del cliente) y múltiples variables independientes (por ejemplo, la calidad del servicio, la conveniencia de horarios, etc.). Los detalles del uso de la regresión incluyen:

1. **Selección de Variables:** Primero, se identifican todas las variables que pueden afectar la satisfacción del cliente.
2. **Modelado:** Se construye un modelo que cuantifique la relación entre las variables.
3. **Interpretación de Resultados:** Los coeficientes del modelo permiten interpretar el impacto individual de cada variable independiente en la satisfacción del cliente.
4. **Predicción:** Basándose en el modelo construido, la empresa puede hacer predicciones precisas y tomar decisiones informadas para mejorar su oferta.

La combinación de encuestas bien diseñadas y análisis de regresión lineal múltiple proporciona una base sólida para comprender y mejorar la satisfacción del cliente en cualquier empresa.

La fórmula para una regresión lineal múltiple es:

$$
[ Y = \beta_0 + \beta_1X_1 + \beta_2X_2 + \cdots + \beta_nX_n + \varepsilon ]
$$

Donde:

* $$Y$$ es la variable dependiente.
* $$( \beta_0 )$$ es el intercepto del modelo.
* $$( \beta_1, \beta_2, \ldots, \beta_n )$$ son los coeficientes de regresión.
* $$( X_1, X_2, \ldots, X_n )$$ son las variables independientes.
* $$( \varepsilon )$$ es el término de error.

### Veamos un ejemplo.

```python
import pandas as pd
```

{% code overflow="wrap" %}
```python
Bd = pd.read_csv('/Users/CRC/Bd.csv') #puedes usar tu propia base de datos de encuensta de clientes; fuente --> Kaggle.com
```
{% endcode %}

```python
Bd.info()
```

```python
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

```python
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

```python
print(Bd.iloc[:, 24])
```

```python
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

```python
Bd['satisfaction_number'] = Bd.iloc[:, 24].replace({'satisfied': 1, 'neutral or dissatisfied': 0}).astype('int64')
Bd.info()
```

```python
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

```python
new_Bd = Bd.select_dtypes(include=['int64'])
new_Bd.info()
```

```python
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

```python
from sklearn.linear_model import LogisticRegression

X = new_Bd.drop('satisfaction_number', axis=1)  # Features
y = new_Bd['satisfaction_number']  # Target
```

```python
model = LogisticRegression(max_iter=1000)
model.fit(X, y)
```

```
LogisticRegression(max_iter=1000)
```

```python
coefficients = model.coef_
print(coefficients)
```

```python
[[-5.18027052e-05 -1.16258989e-05 -2.80761473e-02  3.95433258e-04
   7.36834576e-02 -7.33795504e-02  2.20575820e-02 -5.02928419e-02
   3.44141436e-02  1.39971393e-01  7.60752048e-02  1.00156931e-01
   6.77428471e-02  6.52574668e-02  3.40855476e-02  4.14320968e-02
   3.04496795e-02  6.91197925e-02 -6.33084903e-03]]
```

```python
intercept = model.intercept_
print(intercept)
```

```python
[-0.01461123]
```

```python
predictions = model.predict(X)
print(predictions)
```

<pre class="language-python"><code class="lang-python"><strong>[1 1 1 ... 0 1 0]
</strong></code></pre>
