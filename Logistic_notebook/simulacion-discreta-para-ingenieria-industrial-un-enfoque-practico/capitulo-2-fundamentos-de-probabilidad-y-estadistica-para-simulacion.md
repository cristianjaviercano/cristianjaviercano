# Capítulo 2: Fundamentos de Probabilidad y Estadística para Simulación

### Objetivos del Capítulo:

1. Aplicar los conceptos básicos de la teoría de la probabilidad para modelar la incertidumbre en sistemas de ingeniería industrial.
2. Distinguir entre variables aleatorias discretas y continuas, y describir sus propiedades fundamentales.
3. Utilizar e interpretar funciones de masa de probabilidad (FMP), funciones de densidad de probabilidad (FDP) y funciones de distribución acumulada (FDA).
4. Calcular e interpretar el valor esperado, la varianza y otras medidas descriptivas de variables aleatorias.
5. Identificar las distribuciones de probabilidad más comunes (Bernoulli, Binomial, Poisson, Geométrica, Uniforme, Exponencial, Normal, Triangular, Gamma, Weibull, Lognormal) y seleccionar la más adecuada para modelar fenómenos aleatorios en logística y producción.
6. Comprender el enunciado y las implicaciones prácticas del Teorema del Límite Central (TLC).
7. Describir el proceso de estimación de parámetros de una distribución a partir de datos muestrales y la necesidad de realizar pruebas de bondad de ajuste.

***

## Conceptos básicos de probabilidad

La ingeniería industrial trata con sistemas que operan bajo condiciones de incertidumbre. _La demanda de productos fluctúa, los tiempos de producción varían, las máquinas fallan inesperadamente._ **La probabilidad** es la rama de las matemáticas que nos proporciona el lenguaje y las herramientas para cuantificar y analizar esta incertidumbre. Una comprensión sólida de sus principios es, por lo tanto, un prerrequisito indispensable para la simulación estocástica.

{% tabs %}
{% tab title="Espacio Muestral (Ω)" %}


_Es el conjunto de todos los resultados posibles de un experimento aleatorio_. Por ejemplo, si se inspecciona una pieza manufacturada, el espacio muestral podría ser {defectuosa, no defectuosa}. Si se mide el tiempo de ciclo de un producto, el espacio muestral podría ser todos los números reales positivos.

{% hint style="info" %}
Montgomery, D. C., & Runger, G. C. (2018). Applied Statistics and Probability for Engineers (7th ed.). Wiley.
{% endhint %}
{% endtab %}

{% tab title="Evento (E)" %}
Un evento es cualquier subconjunto del espacio muestral; es decir, una colección de uno o más resultados posibles.&#x20;

Por ejemplo,&#x20;

* Que una pieza sea "defectuosa" es un evento.&#x20;
* Que el tiempo de ciclo sea "menor a 10 minutos" es otro evento.
{% endtab %}

{% tab title="Axiomas de Probabilidad" %}
La probabilidad de un evento A, denotada como P(A), es un número entre 0 y 1 que satisface tres axiomas básicos:

$$
0≤P(A)≤1\   \text{para cualquier evento A}
$$

$$
P(Ω)=1\ \text{(la probabilidad de que ocurra algún resultado del espacio muestral es 1)}
$$

$$
Si\ A_1​,A_2​,…,A_n​\ \text{son eventos mutuamente excluyentes, entonces} \\P(A_1​∪A_2​∪…∪A_n​)=P(A_1​)+P(A2_​)+…+P(A_n​)
$$


{% endtab %}

{% tab title="Probabilidad Condicional" %}
La probabilidad de que ocurra un evento A, dado que otro evento B ya ha ocurrido, se llama probabilidad condicional y se denota $$P(A∣B)$$.&#x20;

Se calcula como,&#x20;

$$P(A∣B)=\frac{P(A∩B)}{P(B)}$$&#x20;

Siempre que $$P(B)>0.1$$ Este concepto es vital para modelar dependencias en los sistemas, como la probabilidad de que una máquina falle dado que ha estado operando por un cierto tiempo.
{% endtab %}

{% tab title="Independencia de Eventos" %}
Dos eventos A y B son independientes si la ocurrencia de uno no afecta la probabilidad de ocurrencia del otro.&#x20;

Formalmente, A y B son independientes si $$P(A∩B)=P(A)P(B)$$, lo que implica que $$P(A∣B)=P(A)\ y\ P(B∣A)=P(B)$$.&#x20;

_La suposición de independencia_, cuando es válida, simplifica enormemente el modelado. Sin embargo, _**asumirla incorrectamente**_ puede llevar a modelos erróneos.&#x20;

Por ejemplo, las fallas de dos máquinas pueden no ser independientes si comparten una fuente de energía común.
{% endtab %}

{% tab title="Teorema de Bayes" %}
Permite actualizar la probabilidad de un evento basándose en nueva evidencia. Aunque su aplicación directa en la generación de entradas para simulación no es tan frecuente como otros conceptos, es una herramienta fundamental en la inferencia estadística y la toma de decisiones bajo incertidumbre.
{% endtab %}
{% endtabs %}

{% hint style="info" %}
La base de la simulación estocástica radica en la capacidad de representar numéricamente la incertidumbre. Los procesos de producción y logística están repletos de variabilidad - CRC-
{% endhint %}

La [teoría de la probabilidad ](https://www.probabilidadyestadistica.net/teoria-de-la-probabilidad/)ofrece el _marco conceptual_ para describir estos fenómenos. Conceptos como la independencia de eventos son cruciales; por ejemplo, al modelar un sistema con múltiples máquinas, es importante determinar si las fallas de una máquina son independientes de las fallas de otra. Si no lo son (quizás debido a un mantenimiento deficiente generalizado o a fluctuaciones de energía), el modelo debe capturar esta dependencia, a menudo a través de probabilidades condicionales.

***

### Variables aleatorias: discretas y continuas

Una variable aleatoria (VA) es una función que asigna un valor numérico a cada resultado posible de un experimento aleatorio. En lugar de trabajar con los eventos cualitativos, las variables aleatorias nos permiten cuantificar los resultados y aplicar herramientas matemáticas y estadísticas.&#x20;

{% tabs %}
{% tab title="Variables Aleatorias Discretas" %}
Una V.A. es discreta si el conjunto de valores que puede tomar es finito o infinito numerable (es decir, se pueden contar, como los números enteros).1

Ejemplos en Ingeniería Industrial:

* Número de llegadas de clientes a un sistema de servicio en una hora.
* Número de piezas defectuosas en un lote de producción.
* Número de camiones esperando para cargar en un muelle.
* Cantidad de unidades demandadas de un producto en un día.
{% endtab %}

{% tab title="Variables Aleatorias Continuas" %}
Una V.A. es continua si puede tomar cualquier valor dentro de un intervalo (o unión de intervalos) de números reales.1 Entre dos valores cualesquiera que pueda tomar, siempre existe un número infinito de otros posibles valores.

Ejemplos en Ingeniería Industrial:

* Tiempo entre llegadas consecutivas de pedidos a un almacén.
* Tiempo de servicio de una operación en una máquina.
* Peso o dimensión de una pieza manufacturada.
* Tiempo hasta la falla de un equipo.
{% endtab %}
{% endtabs %}

***

**Funciones de probabilidad, densidad y distribución acumulada.**

Una vez que hemos identificado una variable aleatoria, necesitamos una forma de describir la probabilidad de que tome diferentes valores o rangos de valores. Esto se logra mediante funciones específicas.

#### Para Variables Aleatorias Discretas, Función de Masa de Probabilidad (FMP o PMF, por sus siglas en inglés)

La FMP de una V.A. discreta X, denotada como $$p(x) o P(X=x)$$, especifica la probabilidad de que X tome exactamente el valor x

* **Propiedades:**
  1. $$0≤p(x)≤1$$ para todo x.
  2. $$∑_{todo x}​p(x)=1$$ (la suma de las probabilidades de todos los posibles valores es 1).
* **Ejemplo:** Si X es el resultado de lanzar un dado equilibrado, $$p(x)=1/6$$ para $$x∈{1,2,3,4,5,6},\ y\ p(x)=0$$ para cualquier otro x.

#### Para Variables Aleatorias Continuas: Función de Densidad de Probabilidad (FDP o PDF, por sus siglas en inglés)

Para una VA. continua X, la FDP, denotada como $$f(x)$$, no da la probabilidad de que X sea igual a un valor específico _**"esta probabilidad es siempre cero para VA. continuas"**_. En cambio, el área bajo la curva de  $$f(x)$$ sobre un intervalo \[a,b] representa la probabilidad de que X caiga en ese intervalo:&#x20;

$$
P(a≤X≤b)=∫_a^bf(x)dx.
$$

**Propiedades:**

1. $$f(x)≥0$$ para todo x.
2. $$∫_{−∞}^∞​f(x)dx=1$$ (el área total bajo la curva de densidad es 1).

#### Función de Distribución Acumulada (FDA o CDF, por sus siglas en inglés)

La FDA, denotada como $$f(x)$$, es aplicable tanto a V.A. discretas como continuas. Define la probabilidad de que la variable aleatoria X tome un valor menor o igual a x, $$F(x)=P(X≤x)$$.

* **Para V.A. Discretas:** $$F(x)=∑_{k≤x}​p(k).$$
* **Para V.A. Continuas:** $$F(x)=∫_{−∞}^x​f(t)dt.$$
* **Propiedades Generales:**
  1. $$0≤F(x)≤1.$$
  2. F(x) es una función no decreciente (es decir, si $$a<b$$, entonces $$F(a)≤F(b)$$).
  3. $$lim_{x→−∞}​F(x)=0\ y\ lim_{x→∞​}F(x)=1.$$
* **Utilidad:** La FDA es muy útil para calcular probabilidades de intervalos $$P(a<X≤b)=F(b)−F(a)$$

{% hint style="info" %}
La FDA juega un papel particularmente importante en la simulación, ya que es la base del método de la transformada inversa, una técnica fundamental para generar observaciones aleatorias de una distribución de probabilidad específica a partir de números aleatorios uniformes
{% endhint %}

Si U es un número aleatorio generado de una distribución Uniforme (0,1), entonces $$X=F−1(U)$$ (donde F−1 es la función inversa de la FDA) será una observación de la variable aleatoria X con FDA F(x).&#x20;

{% hint style="danger" %}
Este concepto, que se explorará en detalle en el Capítulo 3, subraya la importancia de comprender la FDA
{% endhint %}

***

### Valor esperado, varianza y otras medidas

Para resumir las características de una distribución de probabilidad y de la variable aleatoria que sigue, se utilizan diversas medidas numéricas.&#x20;

Las más importantes son el _valor esperado y la varianza_.

{% tabs %}
{% tab title="Valor esperado" %}


El valor esperado de una variable aleatoria X, denotado como $$E[X]$$ o $$μX​$$, representa el valor promedio que tomaría X si el experimento aleatorio se repitiera un número muy grande de veces. Es una medida de la tendencia central de la distribución.1

* Para VA Discreta X con FMP $$p(x): E[X]=∑_{todo x}​x⋅p(x)$$.
* Para VA Continua X con FDP $$f(x): E[X]=∫_{−∞}^∞​x⋅f(x)dx$$

Propiedades del Valor Esperado: Si a y b son constantes:

* $$E[a]=a$$
* $$E[aX]=aE[X]$$
* $$E[aX+b]=aE[X]+b$$
* $$E[X+Y]=E[X]+E[Y] \text{(para cualesquiera V.A. X e Y)}$$
* $$E[g(X)]=∑_x​g(x)p(x)\ o\ E[g(X)]=∫_{−∞}^∞​g(x)f(x)dx.$$
{% endtab %}

{% tab title="Varianza" %}
La varianza de una variable aleatoria X, denotada como $$Var(X)\ o\ σ_2^x$$, mide la dispersión o variabilidad de los valores de X alrededor de su media $$E[X]$$. Una varianza pequeña indica que los valores de X tienden a estar cerca de la media, mientras que una varianza grande indica que los valores están más dispersos.

$$
Var(X)=E[(X−E[X]) ^2 ]=E[X ^2 ]−(E[X]) ^2
$$

**Propiedades de la Varianza:** Si a y b son constantes

* $$Var(a)=0$$
* $$Var(aX)=a^2Var(X)$$
* $$Var(aX+b)=a^2Var(X)$$
* Si X e Y son independientes: $$Var(X+Y)=Var(X)+Var(Y)$$.
{% endtab %}
{% endtabs %}

\
