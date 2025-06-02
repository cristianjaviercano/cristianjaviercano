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

{% tab title="Desviación Estándar" %}
La desviación estándar, denotada como  $$σ_x ​$$ o $$DE(X)$$, es la raíz cuadrada positiva de la varianza $$σ_x = \sqrt{Var(X)}$$, Se expresa en las mismas unidades que la variable aleatoria X, lo que facilita su interpretación como una medida de dispersión típica alrededor de la media.

#### Otros Momentos y Medidas ​**Momentos:**

$$E[K^x]$$ es el k-ésimo momento de X alrededor del origen.&#x20;

$$E[(X−μ)^k]$$ es el k-ésimo momento central.&#x20;

La media es el primer momento alrededor del origen, y la varianza es el segundo momento central.

#### Coeficiente de Variación (CV).

Es una medida relativa de dispersión, definida como&#x20;

$$CV(X)=\frac{σ_x}{∣E[X]∣},\ para\ E[X]\ne0$$&#x20;

Es útil para comparar la variabilidad de variables aleatorias con diferentes medias
{% endtab %}
{% endtabs %}

Estas medidas descriptivas son fundamentales en simulación por **dos razones principales**

<details>

<summary> 1. Modelado de Entradas</summary>

Al seleccionar distribuciones de probabilidad para las variables de entrada de un modelo (ej. tiempos de servicio, demanda), sus parámetros a menudo se relacionan directamente con la media, la varianza u otras medidas (ej. la distribución exponencial se define por su media, la normal por su media y desviación estándar).

</details>

<details>

<summary>  2. Análisis de Salidas</summary>

Las métricas de desempeño que se estiman a partir de las corridas de simulación suelen ser valores esperados (ej. tiempo promedio en cola, utilización promedio de un recurso) y medidas de su variabilidad (ej. varianza del tiempo de ciclo, desviación estándar de la ganancia).

</details>

***

### Distribuciones de probabilidad comunes y su aplicación en IInd

La elección de una distribución de probabilidad adecuada para representar un fenómeno aleatorio es un paso crítico en la construcción de un modelo de simulación válido. A continuación, se presentan algunas de las distribuciones más utilizadas en ingeniería industrial, logística y producción, junto con sus características y aplicaciones típicas

<table><thead><tr><th>Distribución</th><th width="92.4609375">Tipo</th><th>Parámetros Clave</th><th width="87.8828125">Media</th><th width="135.92578125">Varianza</th><th width="233.140625">Aplicaciones Comunes en IE (Logística/Producción)</th></tr></thead><tbody><tr><td><strong>Bernoulli</strong></td><td>Discreta</td><td><span class="math">p (prob. \ éxito)</span></td><td>p</td><td><span class="math">p(1-p)</span></td><td>Pieza defectuosa/no defectuosa, máquina operativa/fallada.</td></tr><tr><td><strong>Binomial</strong></td><td>Discreta</td><td>n(ensayos), p</td><td>np</td><td><span class="math">np(1-p)</span></td><td>N° de defectuosos en lote, N° de clientes que compran un producto.</td></tr><tr><td><strong>Poisson</strong></td><td>Discreta</td><td><p><span class="math">\lambda</span></p><p>(tasa media)</p></td><td><span class="math">\lambda</span></td><td><span class="math">\lambda</span></td><td>N° de llegadas/hora, N° de fallas/día, N° de defectos/unidad.</td></tr><tr><td><strong>Geométrica</strong></td><td>Discreta</td><td><span class="math">p</span> (prob. éxito)</td><td>1/p</td><td><span class="math">(1-p)/p^2</span></td><td>N° de inspecciones hasta primer defecto.</td></tr><tr><td><strong>Uniforme Disc.</strong></td><td>Discreta</td><td>a, b (min, max) o N valores</td><td><span class="math">(a+b)/2</span></td><td><span class="math">((b-a+1)^2-1)/12</span></td><td>Selección aleatoria entre N opciones equiprobables.</td></tr><tr><td><strong>Uniforme Cont.</strong></td><td>Continua</td><td>a, b (min, max)</td><td><span class="math">(a+b)/2</span></td><td><span class="math">(b-a)^2/12</span></td><td>Incertidumbre con solo límites conocidos, tiempos de proceso si no hay más info.</td></tr><tr><td><strong>Exponencial</strong></td><td>Continua</td><td><span class="math">\lambda</span> (tasa) o <span class="math">\mu=1/\lambda</span>(media)</td><td><span class="math">1/\lambda</span></td><td><span class="math">1/\lambda^2</span></td><td>Tiempos entre llegadas (Poisson), tiempos de servicio, vida de componentes sin desgaste.</td></tr><tr><td><strong>Normal</strong></td><td>Continua</td><td><p><span class="math">\mu</span></p><p> (media), <span class="math">\sigma</span> (desv. est.)</p></td><td><span class="math">\mu</span></td><td><span class="math">\sigma^2</span></td><td>Dimensiones de piezas, errores, sumas de V.A. (TLC), tiempos de tareas.</td></tr><tr><td><strong>Triangular</strong></td><td>Continua</td><td>a (min), b (max), c (moda)</td><td><span class="math">(a+b+c)/3</span></td><td><span class="math">\frac{a^2+b^2+c^2-ab-ac-bc}{18}</span></td><td>Duración de actividades (PERT), tiempos de proceso con datos limitados.</td></tr><tr><td><strong>Erlang</strong></td><td>Continua</td><td><span class="math">k (forma), \lambda (tasa)</span></td><td><span class="math">k/\lambda</span></td><td><span class="math">k/\lambda^2</span></td><td>Suma de k exponenciales, tiempos de reparación en fases.</td></tr><tr><td><strong>Weibull</strong></td><td>Continua</td><td><span class="math">\alpha (escala), \beta (forma)</span></td><td><span class="math">\alpha\Gamma(1+1/\beta)</span></td><td><span class="math">\alpha^2[\Gamma(1+2/\beta)-(\Gamma(1+1/\beta))^2]</span></td><td>Tiempos de falla (desgaste, mortalidad infantil, constante).</td></tr><tr><td><strong>Lognormal</strong></td><td>Continua</td><td><span class="math">\mu_{\ln} (media de \ln X), \sigma_{\ln} (desv. est. de \ln X)</span></td><td><span class="math">e^{\mu_{\ln} + \sigma_{\ln}^2/2}</span></td><td><span class="math">e^{2\mu_{\ln} + \sigma_{\ln}^2}(e^{\sigma_{\ln}^2} - 1)</span></td><td>Tiempos de reparación, algunos procesos multiplicativos.</td></tr></tbody></table>

### Teorema del Límite Central (TLC)

El Teorema del Límite Central (TLC) es uno de los resultados más importantes y notables en la teoría de la probabilidad y la estadística, con profundas implicaciones para la simulación

> El Teorema del Límite Central (TLC) establece que, dada una muestra suficientemente grande de variables aleatorias independientes e idénticamente distribuidas, la distribución de la suma o promedio muestral se aproximará a una distribución normal, independientemente de la distribución original de las variables. Esto significa que, incluso si los datos individuales no están distribuidos normalmente, su media tenderá a seguir una distribución normal a medida que el tamaño de la muestra aumenta, lo que permite hacer inferencias estadísticas y aplicar técnicas como intervalos de confianza y pruebas de hipótesis.

establece que si se tiene una secuencia de variables aleatorias:

$$
X _1,X_2,…,X_n
$$

que son independientes e idénticamente distribuidas, con una media finita μ y una varianza finita $$σ^2$$, entonces, a medida que n (el número de variables) se vuelve grande, la distribución de la suma.

$$
S 
n
​
 =X 
1
​
 +X 
2
​
 +…+X 
n
​
$$

se aproxima a una distribución normal. Más formalmente, la variable estandarizada

$$Z_n=\frac{(S_n−nμ)}{(σ\sqrt n)} = \left(\frac{\overline{X_n}−μ}{\frac{σ}{\sqrt n}} \right)$$, converge en distribución a una variable aleatoria Normal estándar N(0,1) a medida que $$n→∞$$.  &#x20;

### Importancia del TLC en la simulacion

{% tabs %}
{% tab title="Justificación del Uso de la Distribución Normal" %}
Muchos fenómenos en ingeniería industrial, como el tiempo total para completar un producto que pasa por múltiples etapas de proceso, pueden considerarse como la suma de duraciones de actividades individuales. Incluso si las duraciones de las actividades individuales no siguen una distribución normal, su suma (si hay suficientes actividades y son aproximadamente independientes) tenderá a ser normalmente distribuida gracias al TLC. Esto justifica el uso de la distribución normal como modelo para muchas cantidades agregadas en los sistemas.
{% endtab %}

{% tab title="Análisis de Salidas de Simulación" %}
En la simulación, a menudo se está interesado en estimar la media de una métrica de desempeño (ej. el tiempo promedio de espera de un cliente). Esto se hace ejecutando la simulación múltiples veces (réplicas) y calculando el promedio de la métrica obtenida en cada réplica. Si el número de réplicas es suficientemente grande, el TLC implica que la distribución de esta media muestral será aproximadamente normal. Esta propiedad es fundamental para construir intervalos de confianza para la media verdadera de la métrica de desempeño, lo cual es esencial para cuantificar la precisión de las estimaciones obtenidas por simulación
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
El TLC es poderoso porque se aplica independientemente de la forma de la distribución original de las X\_i (_siempre que tengan media y varianza finitas)_. Es el puente que conecta las distribuciones individuales de los componentes aleatorios de un sistema con el comportamiento agregado o promedio del sistema, que es frecuentemente el foco del análisis en un estudio de simulación
{% endhint %}

### Estimación de parámetros y pruebas de bondad de ajuste

#### Qué es la Prueba de Bondad de Ajuste

La prueba de bondad de ajuste es una herramienta estadística utilizada para determinar qué tan bien un conjunto de datos se ajusta a una distribución teórica esperada. Se evalúa cuán probable es que una muestra observada haya sido generada a partir de una población que se ajusta a una distribución específica.

#### Para qué Sirve

La prueba de bondad de ajuste se utiliza principalmente para:

1. **Validar Modelos Estadísticos**: Ayuda a verificar si el modelo estadístico elegido es adecuado para los datos.
2. **Comparar Distribuciones**: Permite comparar la distribución teórica con la distribución observada.
3. **Toma de Decisiones**: Facilita decisiones en campos como la calidad de procesos, ya que entender la distribución de los datos puede llevar a mejores ajustes y soluciones.

#### Cómo se Usa

1. **Seleccionar la Distribución Teórica**: Elegir la distribución que mejor describe los datos (ej. Normal, Binomial, Poisson, etc.).
2. **Realizar la Prueba Estadística**: Usar pruebas como Chi-cuadrado, Kolmogorov-Smirnov o Anderson-Darling.
3. **Interpretar los Resultados**: Analizar el valor p de la prueba para afirmar si se rechaza o no la hipótesis nula de que los datos siguen la distribución teórica seleccionada.

{% hint style="warning" %}
Este análisis es crucial en estudios de simulación, ya que garantiza que los resultados obtenidos sean realmente representativos del comportamiento esperado bajo el modelo teórico asumido -crc-
{% endhint %}

#### Estimación de Parámetros

Una vez que se ha seleccionado una familia de distribuciones candidata (basada en el conocimiento del sistema y/o un análisis preliminar de los datos, como histogramas), el siguiente paso es estimar los parámetros de esa distribución utilizando los datos muestrales disponibles&#x20;

(ej. tiempos de servicio observados, demandas históricas).&#x20;

Los métodos más comunes incluyen (...)

{% tabs %}
{% tab title="Método de los Momentos" %}
_Iguala los momentos muestrales_ (ej. media muestral, varianza muestral) con los momentos teóricos de la distribución (que son funciones de los parámetros) y resuelve el sistema de ecuaciones resultante para los parámetros.&#x20;

Es conceptualmente simple pero no siempre el más eficiente.
{% endtab %}

{% tab title="Método de Máxima Verosimilitud (Maximum Likelihood Estimation - MLE)" %}
Encuentra los valores de los parámetros que maximizan la probabilidad (o "verosimilitud") de haber observado la muestra de datos dada. Los estimadores MLE suelen tener buenas propiedades estadísticas (consistencia, eficiencia asintótica, normalidad asintótica) y son ampliamente utilizados.&#x20;

Para muchas distribuciones comunes, existen fórmulas cerradas para los estimadores MLE; para otras, se requieren métodos numéricos.
{% endtab %}
{% endtabs %}

#### Pruebas de Bondad de Ajuste (Goodness-of-Fit Tests)

Después de seleccionar una distribución y estimar sus parámetros, [_**es crucial evaluar formalmente qué tan bien esa distribución teórica (ajustada) concuerda con los datos empíricos observados**_](#user-content-fn-1)[^1]. Las pruebas de bondad de ajuste cuantifican esta concordancia.

**Hipótesis:**

* Hipótesis Nula $$(H_0​)$$: Los datos observados provienen de la distribución teórica especificada.
* Hipótesis Alternativa $$(H_1​)$$: Los datos observados no provienen de la distribución teórica especificada.

**Prueba Chi-cuadrado (χ2):**

* Aplicable tanto a datos discretos como continuos&#x20;

{% hint style="warning" %}
estos últimos deben ser agrupados en intervalos o "bins".
{% endhint %}

* Compara las frecuencias observadas $$(O_i​)$$ en cada categoría o intervalo con las frecuencias esperadas $$(E_i​)$$ bajo la hipótesis nula.
* El estadístico de prueba es $$χ^2=∑(O_i​−E_i​)^2/E_i​.$$
* Si el valor del estadístico es grande (superando un valor crítico de la distribución _Chi-cuadrado_ con ciertos grados de libertad, o si el p-value es pequeño), se rechaza $$H_0​$$, concluyendo que la distribución teórica no es un buen ajuste.  &#x20;



[^1]: ojo, importante!!
