# Capitulo Tres: Generación de Números y Variables Aleatorias

### **Objetivos del Capítulo:**

1. Comprender la necesidad y las propiedades deseables de los generadores de números pseudoaleatorios.
2. Describir y aplicar el método de Lehmer (Generador Congruencial Multiplicativo) para la generación de secuencias de números pseudoaleatorios.
3. Conocer los principios de las pruebas estadísticas utilizadas para evaluar la uniformidad e independencia de los generadores de números aleatorios.
4. Aplicar el método de la transformada inversa para generar variables aleatorias a partir de distribuciones discretas y continuas comunes.
5. Entender y aplicar el método de aceptación-rechazo para la generación de variables aleatorias.
6. Utilizar el método de Box-Muller para generar variables aleatorias normales.

***

{% hint style="warning" %}
La generación de números aleatorios es fundamental en la simulación de procesos, ya que permite modelar la incertidumbre y variabilidad inherentes a sistemas complejos. Números aleatorios de alta calidad aseguran que las simulaciones sean realistas y precisas, lo que es crucial para el análisis, predicción y toma de decisiones en ámbitos como la ingeniería, economía y ciencias computacionales. Por este motivo, el uso de generadores de números pseudoaleatorios eficientes y la validación de su idoneidad mediante pruebas estadísticas son pilares esenciales en cualquier entorno de simulación. -crc-
{% endhint %}

### Generación de números pseudoaleatorios: Método de Lehmer.

La simulación estocástica, que es el núcleo de la modelización de la mayoría de los sistemas de ingeniería industrial, se basa fundamentalmente en la capacidad de generar secuencias de números que se comporten como si fueran realizaciones de variables aleatorias uniformemente distribuidas en el intervalo (0,1). Estos números, comúnmente denotados como&#x20;

$$U_i∼U(0,1)$$&#x20;

son el ingrediente básico para luego generar variables aleatorias de distribuciones más complejas _"Exponencial, Normal, Poisson, etc._ que representan los diversos fenómenos inciertos en un sistema.

#### Números Pseudoaleatorios vs. Verdaderamente Aleatorios

_Las computadoras son máquinas deterministas._ Por lo tanto, no pueden generar números verdaderamente aleatorios en el sentido estricto.&#x20;

En su lugar, utilizan algoritmos matemáticos para producir secuencias de números que _parecen_ aleatorios y que pasan diversas pruebas estadísticas de aleatoriedad.&#x20;

Estos se denominan **números pseudoaleatorios**. Las propiedades deseables de una secuencia de números pseudoaleatorios.

{% tabs %}
{% tab title="Uniformidad" %}
Los números deben estar uniformemente distribuidos en el intervalo (0,1)
{% endtab %}

{% tab title="Independencia" %}
Cada número generado debe ser independiente de los números anteriores en la secuencia.
{% endtab %}

{% tab title="Período Largo" %}
La secuencia eventualmente se repetirá (es periódica). El período (longitud de la secuencia antes de que comience a repetirse) debe ser lo más largo posible, idealmente mucho más largo que la cantidad de números aleatorios necesarios para cualquier simulación.
{% endtab %}

{% tab title="Reproducibilidad" %}
Dada la misma semilla inicial, el generador debe producir exactamente la misma secuencia de números. Esto es crucial para la depuración de modelos y para comparar diferentes configuraciones del sistema bajo las mismas condiciones aleatorias
{% endtab %}

{% tab title="Eficiencia Computacional" %}
El algoritmo debe ser rápido para generar números, ya que una simulación puede requerir millones de ellos.
{% endtab %}

{% tab title="Portabilidad" %}
El generador debe producir los mismos resultados (o estadísticamente equivalentes) en diferentes plataformas computacionales.
{% endtab %}
{% endtabs %}

#### Generadores Congruenciales Lineales (GCL)

#### Generadores Congruenciales Lineales (GCL)

Los Generadores Congruenciales Lineales son una clase de algoritmos para generar números pseudoaleatorios. Funcionan utilizando una relación de recurrencia lineal. La fórmula general para un GCL es:

$$
[ X_{i+1} = (aX_i + c) \mod m ]
$$

donde:

* $$X_i$$ es el i-ésimo número entero de la secuencia.
* $$X_o$$ es la semilla o valor inicial.
* a es el multiplicador.
* c es el incremento.
* m es el módulo.

{% hint style="info" %}
Los parámetros $$a,c,m y X_0$$ son enteros no negativos. El término $$mod\ m$$ significa obtener el residuo de la división de $$(aX_i+c)$$ por m. Los números pseudoaleatorios $$U_i$$ en (0,1) se obtienen como $$U_i=X_i/m.$$
{% endhint %}

**Ejemplo**

Consideremos los siguientes valores:

* ( a = 5 )
* ( c = 3 )
* ( m = 16 )
* Semilla $$(( X_0 )) = 7$$

La secuencia puede generarse así:

1. $$( X_1 = (5 \times 7 + 3) \mod 16 = 38 \mod 16 = 6 )$$
2. $$( X_2 = (5 \times 6 + 3) \mod 16 = 33 \mod 16 = 1 )$$
3. $$( X_3 = (5 \times 1 + 3) \mod 16 = 8 \mod 16 = 8 )$$

Repetimos este proceso para generar más números. Este método es simple y eficiente, pero la elección de ( a ), ( c ), y ( m ) es crucial para obtener una buena calidad de aleatoriedad y un largo período.

#### Método de Lehmer (Generador Congruencial Multiplicativo)

#### Método de Lehmer

El Método de Lehmer, también conocido como Generador Congruencial Multiplicativo, es un algoritmo para generar números pseudoaleatorios a través de una relación recursiva de la forma:

$$
[ X_{n+1} = (a \times X_n) \mod m ]
$$

donde:

* a es el multiplicador,
* m es el módulo,
* $$X_0$$ es la semilla inicial del generador.

Este método es una variante del generador congruencial lineal, pero no incluye el término constante de incremento ( c ). El valor de ( a ) y ( m ) son elegidos cuidadosamente para maximizar la longitud del período y la calidad de la aleatoriedad.

#### Ejemplo

Supongamos que ( a = 7 ), ( m = 31 ), y la semilla inicial ( $$X_0 = 3$$ ).

1. Calculamos el primer número en la secuencia:\
   $$[ X_1 = (7 \times 3) \mod 31 = 21 ]$$
2. Calculamos el segundo número:\
   $$[X_2 = (7 \times 21) \mod 31 = 23 ]$$
3. Calculamos el tercer número:\
   $$[ X_3 = (7 \times 23) \mod 31 = 6 ]$$

Podemos continuar este proceso para generar más números en la secuencia.&#x20;

_**Elección de Parámetros:**_&#x20;

La calidad del generador de Lehmer depende críticamente de la elección de $$m, a, y X_0​.$$

1. **Módulo m:** Debe ser un número primo grande. Una elección común, especialmente en máquinas de 32 bits, es $$m = 2^{31} − 1$$, que es un número primo de Mersenne.  &#x20;
2. **Multiplicador a:** Debe elegirse cuidadosamente para asegurar un período completo (o casi completo) y buenas propiedades estadísticas. Un período completo para un generador multiplicativo con módulo primo m es $$m−1$$, lo que significa que la secuencia $$X_1​,X_2​,…,X_{m−1}$$​ contiene todos los enteros desde 1 hasta m−1 exactamente una vez, en algún orden.&#x20;
   1. Se han realizado extensas investigaciones para encontrar _"buenos"_ multiplicadores. Por ejemplo, para $$m=2^{31}−1$$, un multiplicador comúnmente citado es $$a=7^5=16807$$, aunque otros como $$a=48271$$ también se han propuesto por sus buenas propiedades y eficiencia de implementación.  &#x20;

* **Semilla** $$X_0$$**​:** Debe ser un entero entre 1 y m−1. Diferentes semillas producirán diferentes secuencias (aunque relacionadas).
* **Implementación:** Un desafío en la implementación es calcular $$aX_i$$​ sin que ocurra un desbordamiento (overflow) si el producto excede la capacidad máxima de representación de enteros de la computadora, antes de tomar el módulo m.

La generación de números $$U(0,1)$$ es el primer paso fundamental. La calidad de estos números impacta directamente la validez de todo el estudio de simulación.&#x20;

{% hint style="danger" %}
Si el generador base es defectuoso (ej. no es uniforme, o los números no son independientes), entonces las variables aleatorias generadas a partir de él también serán defectuosas, y los resultados de la simulación no serán fiables, sin importar cuán sofisticado sea el resto del modelo
{% endhint %}

### Pruebas de aleatoriedad e independencia

Dado que los generadores de números pseudoaleatorios son algoritmos deterministas, es crucial someter sus secuencias de salida a rigurosas pruebas estadísticas para evaluar si se comportan de manera suficientemente similar a secuencias verdaderamente aleatorias e independientes de una distribución. U(1,0)

{% hint style="warning" %}
Ningún generador es perfecto, y ninguna prueba puede "probar" que un generador es bueno; más bien, las pruebas pueden revelar si un generador es "malo" al no pasar ciertos criterios estadísticos
{% endhint %}

Las dos propiedades fundamentales que se desean evaluar son la **uniformidad** y la **independencia**.

#### Pruebas de Uniformidad

{% tabs %}
{% tab title="Prueba Chi-cuadrado (χ2)" %}
Es una herramienta estadística utilizada para evaluar la uniformidad en una secuencia de números pseudoaleatorios. Consiste en comparar la frecuencia observada de números en diferentes intervalos con las frecuencias esperadas, lo que permite determinar si los números están distribuidos de manera uniforme.

1. Se divide el intervalo (0,1) en k subintervalos de igual longitud (1/k).
2. Se genera una muestra de N números aleatorios $$U_i$$​.
3. Se cuenta el número de observaciones $$(O_j​)$$ que caen en cada subintervalo j.
4. Bajo la hipótesis nula de uniformidad, la frecuencia esperada $$(E_j​)$$ para cada subintervalo es $$N/k.$$
5. Se calcula el estadístico de prueba: $$X_0^2​=∑_{j=1}^k \frac{​(Oj​−Ej​)^2}{Ej}​.$$
6. Este estadístico se compara con un valor crítico de la distribución Chi-cuadrado con k−1 grados de libertad y un nivel de significancia α (ej. 0.05). Si $$χ_0^2$$​ es mayor que el valor crítico (o si el p-value es menor que α), se rechaza la hipótesis de uniformidad.

***
{% endtab %}

{% tab title="Prueba de Kolmogorov-Smirnov (K-S)" %}
1. Se ordenan los N números generados $$U(1)​≤U(2)​≤…≤U(N)$$​.
2. Se calcula la función de distribución acumulada empírica (FDAe) $$F_e​(x)=(número\ de\ U_i​≤x)/N$$.
3. Para una distribución U(0,1), la FDA teórica es $$F_t​(x)=x\ para\ 0≤x≤1$$.
4. El estadístico de prueba K-S es la máxima diferencia vertical absoluta entre $$F_e​(x)\ y\ F_t​(x): D_N​=max_{0≤x≤1}​∣F_e​(x)−F_t​(x)∣$$. En la práctica, se calcula como&#x20;

$$
D_N = \max\left\{ \max_{1 \le j \le N} \left( \frac{j}{N} - U_{(j)} \right), \max_{1 \le j \le N} \left( U_{(j)} - \frac{j-1}{N} \right) \right\}
$$

1. $$D_N​$$ se compara con un valor crítico de la distribución de Kolmogorov-Smirnov para el tamaño de muestra N y nivel de significancia α. _**Si**_ $$D_N$$_**​ es mayor que el valor crítico, se rechaza la hipótesis de uniformidad.**_
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Ejemplo de chi cuadrado" %}
Imaginemos que hemos recolectado $$n=100$$ observaciones de una variable continua y queremos verificar si estos datos pueden ser modelados por una distribución normal.

#### 1. Estimar Parámetros y Definir Intervalos

Primero, necesitamos la media y la desviación estándar de nuestra muestra. Supongamos que para nuestros datos:

* Media muestral $$(\bar{x}) = 50$$
* Desviación estándar muestral $$(s) = 10$$

A continuación, dividimos el rango de los datos en k intervalos. Es crucial que la frecuencia esperada para cada intervalo $$(E_i)$$ sea suficientemente grande, generalmente, $$E_i \ge 5$$. Para este ejemplo, seleccionaremos k=5 intervalos.

Los límites de los intervalos se definen y luego se estandarizan (convierten a puntuaciones Z) usando $$\bar{x} \ y\  s$$:clap:

| Intervalo (Datos Originales) | Límites Z (Estandarizados)         |
| ---------------------------- | ---------------------------------- |
| X < 40                       | $$Z < (40-50)/10 = -1.0$$          |
| $$40 \le X < 45$$            | $$-1.0 \le Z < (45-50)/10 = -0.5$$ |
| $$45 \le X < 55$$            | $$-0.5 \le Z < (55-50)/10 = 0.5$$  |
| $$55 \le X < 60$$            | $$0.5 \le Z < (60-50)/10 = 1.0$$   |
| $$X \ge 60$$                 | $$Z \ge 1.0$$                      |

#### 2. Calcular Frecuencias Observadas (O\_i)

Contamos el número de datos de nuestra muestra que caen dentro de cada uno de los intervalos definidos:

| Intervalo         | Frecuencia Observada (O\_i) |
| ----------------- | --------------------------- |
| X < 40            | 18                          |
| $$40 \le X < 45$$ | 15                          |
| $$45 \le X < 55$$ | 36                          |
| $$55 \le X < 60$$ | 13                          |
| $$X \ge 60$$      | 18                          |
| **Total**         | **100**                     |

#### 3. Calcular Frecuencias Esperadas (E\_i)

Para cada intervalo, determinamos la probabilidad de que un valor de una distribución normal estándar caiga dentro de sus límites Z. Luego, multiplicamos esta probabilidad por el tamaño total de la muestra (n=100) para obtener E\_i.

| Intervalo         | Límites Z             | P(Intervalo) (Prob. Normal Estándar)    | E\_i = n . P(Intervalo})     |
| ----------------- | --------------------- | --------------------------------------- | ---------------------------- |
| X < 40            | $$Z < -1.0$$          | $$P(Z < -1.0) \approx 0.1587$$          | $$100 \cdot 0.1587 = 15.87$$ |
| $$40 \le X < 45$$ | $$-1.0 \le Z < -0.5$$ | $$P(-1.0 \le Z < -0.5) \approx 0.1498$$ | $$100 \cdot 0.1498 = 14.98$$ |
| $$45 \le X < 55$$ | $$-0.5 \le Z < 0.5$$  | $$P(-0.5 \le Z < 0.5) \approx 0.3829$$  | $$100 \cdot 0.3829 = 38.29$$ |
| $$55 \le X < 60$$ | $$0.5 \le Z < 1.0$$   | $$P(0.5 \le Z < 1.0) \approx 0.1498$$   | $$100 \cdot 0.1498 = 14.98$$ |
| $$X \ge 60$$      | $$Z \ge 1.0$$         | $$P(Z \ge 1.0) \approx 0.1587$$         | $$100 \cdot 0.1587 = 15.87$$ |
| **Total**         |                       | $$\approx 1.0$$                         | $$\approx 100$$              |

{% hint style="warning" %}
_Las probabilidades_ $$P(\text{Intervalo})$$ _se obtienen de una tabla de distribución normal estándar (tabla Z) o usando software estadístico._
{% endhint %}

#### 4. Calcular el Estadístico $$\chi^2$$

Utilizamos las frecuencias observadas (O\_i) y esperadas (E\_i) para calcular el estadístico $$\chi^2$$

| Intervalo         | O\_i | E\_i  | O\_i - E\_i | (O\_i - E\_i)^2 | (O\_i - E\_i)^2 / E\_i    |
| ----------------- | ---- | ----- | ----------- | --------------- | ------------------------- |
| $$X < 40$$        | 18   | 15.87 | 2.13        | 4.5369          | $$\approx 0.2859$$        |
| $$40 \le X < 45$$ | 15   | 14.98 | 0.02        | 0.0004          | $$\approx 0.00002$$       |
| $$45 \le X < 55$$ | 36   | 38.29 | -2.29       | 5.2441          | $$\approx 0.1369$$        |
| $$55 \le X < 60$$ | 13   | 14.98 | -1.98       | 3.9204          | $$\approx 0.2617$$        |
| $$X \ge 60$$      | 18   | 15.87 | 2.13        | 4.5369          | $$\approx 0.2859$$        |
| **Total**         |      |       |             |                 | $$\chi^2 \approx 0.9704$$ |

El valor calculado del estadístico es $$\chi^2_{calculado} \approx 0.9704$$.

#### 5. Determinar Grados de Libertad (gl)

Los grados de libertad para esta prueba se calculan como:

$$
gl = k - 1 - m
$$

Donde:

* k = número de intervalos (5 en nuestro ejemplo).
* m = número de parámetros de la distribución que fueron estimados a partir de la muestra. Para una distribución normal, estimamos la media y la desviación estándar, por lo que m=2.

Entonces, $$gl = 5 - 1 - 2 = 2$$

#### 6. Tomar una Decisión Estadística

1. Elegimos un nivel de significancia, comúnmente $$\alpha = 0.05$$.
2. Buscamos el valor crítico de $$\chi^2$$ en una tabla de distribución Chi-cuadrado (o usando software) para $$gl=2\ y\ \alpha=0.05$$.\
   El valor $$\chi^2_{critico}(2, 0.05)$$ es aproximadamente 5.991.

**Regla de decisión:**

* Si $$\chi^2_{calculado} > \chi^2_{critico}$$, rechazamos H\_0.
* Si $$\chi^2_{calculado} \le \chi^2_{critico}$$, no rechazamos H\_0.

En nuestro ejemplo: $$0.9704 \le 5.991.$$

#### 7. Conclusión

Dado que el valor calculado de $$\chi^2 (0.9704)$$ es menor que el valor crítico (5.991) para un nivel de significancia de 0.05, no rechazamos la hipótesis nula (H\_0).&#x20;

Esto significa que no tenemos suficiente evidencia estadística para concluir que los datos de la muestra no siguen una distribución normal.

***
{% endtab %}

{% tab title="Ejemplo de la Prueba K-S" %}
## Prueba de Normalidad de Kolmogorov-Smirnov (KS)

***

#### Hipótesis

* $$H_0$$: Los datos siguen una distribución normal.
* $$H_1$$: Los datos no siguen una distribución normal.

***

#### Estadístico de Prueba (D)

El estadístico de prueba de Kolmogorov-Smirnov, D, es la máxima diferencia absoluta entre la ECDF de la muestra $$S_n(x)$$ y la CDF teórica de la distribución normal F(x):

$$
D = \sup_x |S_n(x) - F(x)|
$$

Para el cálculo práctico con una muestra ordenada $$x_{(1)}, x_{(2)}, \ldots, x_{(n)}$$:\
Primero se calculan $$D^+\ y\ D^-$$:

$$D^+ = \max_{1 \le i \le n} \left( \frac{i}{n} - F(x_{(i)}) \right)$$

$$
D^- = \max_{1 \le i \le n} \left( F(x_{(i)}) - \frac{i-1}{n} \right)
$$

Entonces, el estadístico D es el máximo de estos dos valores:

$$
D = \max(D^+, D^-)
$$

Donde:

* n es el tamaño de la muestra.
* $$x_{(i)}$$ es el i-ésimo valor más pequeño en la muestra (datos ordenados).
* $$S_n(x_{(i)}) = i/n$$ es el valor de la ECDF en $$x_{(i)}$$
* $$F(x_{(i)})$$ es el valor de la CDF teórica de la distribución normal evaluada en $$x_{(i)}$$, utilizando la media $$(\mu)$$ y desviación estándar $$(\sigma)$$ especificadas (o estimadas de la muestra para la prueba de Lilliefors).

***

#### Ejemplo Paso a Paso

Supongamos que tenemos una muestra pequeña de n=5 observaciones: $$X = {10, 12, 15, 16, 20}$$. Queremos probar si provienen de una distribución normal.

**Pasos:**

1. **Ordenar los Datos:**\
   Los datos ya están ordenados: $$x_{(1)}=10, x_{(2)}=12, x_{(3)}=15, x_{(4)}=16, x_{(5)}=20$$.
2. **Estimar Parámetros de la Distribución Normal (para prueba de Lilliefors):**\
   Calculamos la media muestral $$(\bar{x})$$ y la desviación estándar muestral (s).
   * $$\bar{x} = (10+12+15+16+20)/5 = 73/5 = 14.6$$
   * $$s = \sqrt{\frac{\sum (x_i - \bar{x})^2}{n-1}} = \sqrt{\frac{(10-14.6)^2 + (12-14.6)^2 + (15-14.6)^2 + (16-14.6)^2 + (20-14.6)^2}{4}}$$
   * $$s = \sqrt{\frac{(-4.6)^2 + (-2.6)^2 + (0.4)^2 + (1.4)^2 + (5.4)^2}{4}} = \sqrt{\frac{21.16 + 6.76 + 0.16 + 1.96 + 29.16}{4}} = \sqrt{\frac{59.2}{4}} = \sqrt{14.8} \approx 3.847$$
3.  **Calcular** $$F(x_{(i)}), S_n(x_{(i)})$$ **y las diferencias:**\
    Para cada $$x_{(i)}$$, calculamos $$F(x_{(i)})$$ usando la CDF de una normal con $$\mu=14.6$$ y $$\sigma=3.847$$. Esto implica estandarizar cada $$x_{(i)}$$ a $$z_{(i)} = (x_{(i)} - \bar{x})/s$$ y luego encontrar $$P(Z \le z_{(i)})$$

    |  i  | x\_(i) |    z\_(i) = x\_(i)-14.6)/3.847$    | $F(x\_{(i)}) = P(Z \le z\_{(i)})$ | S\_n(x\_(i)) = i/n | $\frac{i-1}{n}$ | $D\_i^+ = \frac{i}{n} - F(x\_{(i)})$ | $D\_i^- = F(x\_{(i)}) - \frac{i-1}{n}$ |
    | :-: | :----: | :--------------------------------: | :-------------------------------: | :----------------: | :-------------: | :----------------------------------: | :------------------------------------: |
    |  1  |   10   | $$(10-14.6)/3.847 \approx -1.196$$ |         $$\approx 0.1159$$        |      1/5 = 0.2     |    0/5 = 0.0    |         0.2 - 0.1159 = 0.0841        |          0.1159 - 0.0 = 0.1159         |
    |  2  |   12   | $$(12-14.6)/3.847 \approx -0.676$$ |         $$\approx 0.2495$$        |      2/5 = 0.4     |    1/5 = 0.2    |         0.4 - 0.2495 = 0.1505        |          0.2495 - 0.2 = 0.0495         |
    |  3  |   15   |  $$(15-14.6)/3.847 \approx 0.104$$ |         $$\approx 0.5414$$        |      3/5 = 0.6     |    2/5 = 0.4    |         0.6 - 0.5414 = 0.0586        |          0.5414 - 0.4 = 0.1414         |
    |  4  |   16   |  $$(16-14.6)/3.847 \approx 0.364$$ |         $$\approx 0.6420$$        |      4/5 = 0.8     |    3/5 = 0.6    |         0.8 - 0.6420 = 0.1580        |          0.6420 - 0.6 = 0.0420         |
    |  5  |   20   |  $$(20-14.6)/3.847 \approx 1.404$$ |         $$\approx 0.9198$$        |      5/5 = 1.0     |    4/5 = 0.8    |         1.0 - 0.9198 = 0.0802        |          0.9198 - 0.8 = 0.1198         |


4.  **Calcular el Estadístico D:**\
    $$D^+ = \max(0.0841, 0.1505, 0.0586, 0.1580, 0.0802) = 0.1580$$\
    $$D^- = \max(0.1159, 0.0495, 0.1414, 0.0420, 0.1198) = 0.1414$$

    $$D = \max(D^+, D^-) = \max(0.1580, 0.1414) = 0.1580$$
5. **Tomar una Decisión Estadística:**
   * Se elige un nivel de significancia $$\alpha$$ (ej., $$\alpha = 0.05$$).
   * El valor $$D_{calculado} = 0.1580$$ se compara con un valor crítico $$D_{critico}$$. Para la prueba de Lilliefors,  ya que $$\mu\ y\ \sigma$$ fueron estimados, los valores críticos son diferentes de la prueba KS estándar y dependen de n.
   * Por ejemplo, para n=5 y $$\alpha=0.05$$, el valor crítico de Lilliefors es aproximadamente 0.337.
   * **Regla de decisión:** Si $$D_{calculado} > D_{critico}$$, se rechaza H\_0. De lo contrario, no se rechaza H\_0.
   * En nuestro ejemplo: 0.1580 < 0.337.
6. **Conclusión:**\
   Como $$D_{calculado}$$ (0.1580) es menor que el valor crítico de Lilliefors (0.337) para $$\alpha=0.05$$, no rechazamos la hipótesis nula (H\_0). Concluimos que no hay evidencia suficiente para afirmar que los datos no siguen una distribución normal.

***

#### Consideraciones Adicionales

{% hint style="info" %}
La prueba de Kolmogorov-Smirnov es generalmente más potente que la prueba $$\chi^2$$ para probar la normalidad de datos continuos, especialmente con muestras pequeñas.

Cuando los parámetros de la distribución normal (media y/o desviación estándar) se estiman a partir de la muestra, es crucial utilizar los valores críticos de la **prueba de Lilliefors**, no los de la prueba KS estándar, ya que estos últimos serían demasiado conservadores, llevarían a no rechazar H\_0 con demasiada frecuencia.

La prueba es sensible a desviaciones en el centro, las colas y la forma de la distribución.
{% endhint %}

***
{% endtab %}
{% endtabs %}

***

### **Pruebas de Independencia**&#x20;

Estas pruebas verifican si los números generados son independientes entre sí (es decir, si el valor de un número no influye en el valor de los siguientes).

1. **Prueba de Rachas (Runs Test):** Una "racha" es una subsecuencia de observaciones con una propiedad común.&#x20;
   1. Por ejemplo, una racha ascendente es una secuencia de números donde cada uno es mayor que el anterior. Se analiza el número total de rachas en la secuencia. Si hay demasiadas o muy pocas rachas en comparación con lo que se esperaría de una secuencia verdaderamente independiente, se rechaza la hipótesis de independencia.  &#x20;
2. **Prueba de Autocorrelación:** Mide la correlación lineal entre números separados por un cierto "retraso" (lag) $$k$$ en la secuencia. La autocorrelación de lag k, $$ρ_k$$​, estima la correlación entre $$U_i$$​ y $$U_i+k$$​. Para una secuencia independiente, se espera que todas las autocorrelaciones (para $$k≥1$$) sean cercanas a cero. Se construye un estadístico de prueba (basado en la aproximación Normal para $$ρ^​k$$​ cuando N es grande) para verificar si $$ρ_k$$​ es significativamente diferente de cero.

{% hint style="warning" %}
Es importante destacar que un generador debe pasar un conjunto diverso y riguroso de estas pruebas estadísticas antes de ser considerado aceptable para su uso en estudios de simulación serios. El hecho de que una secuencia pase una prueba no garantiza que sea "perfecta", solo que no se ha encontrado evidencia en contra de la hipótesis de uniformidad o independencia bajo esa prueba particular.
{% endhint %}

***

### Métodos de generación de variables aleatorias.

Una vez que se dispone de una fuente fiable de números pseudoaleatorios $$U_i∼U(0,1)$$, el siguiente paso es transformar estos números uniformes en realizaciones de variables aleatorias que sigan las distribuciones de probabilidad específicas (Exponencial, Normal, Poisson, etc.) que se han identificado como modelos para los componentes inciertos del sistema bajo estudio.&#x20;

Existen varios métodos para realizar esta transformación.

#### **Método de la Transformada Inversa (MTI)**&#x20;

Este es el método más fundamental y, cuando es aplicable, a menudo el más eficiente y directo

1. **Principio** Se basa en el hecho de que si X es una variable aleatoria con función de distribución acumulada (FDA) continua y estrictamente creciente $$F(x)$$, y U es una variable aleatoria $$U(0,1)$$, entonces la variable aleatoria $$Y=F−1(U)$$ tiene la misma distribución que X. Aquí, $$F−1(u)$$ es la función inversa de la FDA, definida como el valor y tal que $$F(y)=u$$.
   1.  **Algoritmo para V.A. Continuas:**

       Generar un número $$u∼U(0,1)$$.

       1. Calcular $$x=F−1(u)$$. Este x es la observación deseada de la V.A. X.
   2.  **Aplicación a V.A. Discretas:**&#x20;

       Si X es discreta con $$FMP\ p(xj​)$$ y $$FDA F(xj​)=P(X≤xj​)$$, se genera $$u∼U(0,1)$$ y se busca el valor _xj​_ tal que $$F(xj−1​)<u≤F(xj​)\ (donde\ F(x0​)=0)$$. Entonces _x&#x6A;_&#x200B; es la observación generada. Esto se puede implementar mediante una búsqueda secuencial o más eficiente.

*   **Ejemplos de Aplicación Directa, donde F−1(u) tiene forma cerrada:**

    * **Uniforme Continua U(a,b):** $$F(x)=(x−a)/(b−a)$$. Invirtiendo, $$x=a+(b−a)u$$.  &#x20;
    * **Exponencial (media** $$μ=1/λ$$**):** $$F(x)=1−e−λx$$. Invirtiendo, $$x=−(1/λ)ln(1−u)$$. Dado que si $$u∼U(0,1)$$, entonces $$1−u∼U(0,1)$$, se puede usar $$x=−(1/λ)ln(u)$$ de forma equivalente.  &#x20;
    * **Triangular:** La FDA es lineal por tramos, y su inversa también se puede encontrar analíticamente por tramos.  &#x20;
    * **Weibull:** $$F(x)=1−e−(x/α)β$$. Invirtiendo, $$x=α(−ln(1−u))1/β$$.  &#x20;



<details>

<summary><strong>Ventajas:</strong> </summary>

Es exacto si $$F−1(u)$$ se puede calcular con precisión. Es intuitivo. Preserva la monotonicidad (si $$u1​<u2$$​, entonces $$F−1(u1​)≤F−1(u2​)$$), lo cual es útil para algunas técnicas de reducción de varianza.

</details>

<details>

<summary><strong>Desventajas:</strong> </summary>

La función $$F−1(u)$$ no siempre tiene una expresión analítica simple o de forma cerrada&#x20;

(ej. para las distribuciones Normal, Gamma, Beta, Binomial, Poisson con parámetros grandes). En estos casos, se requieren aproximaciones numéricas o métodos alternativos.  &#x20;

</details>

***

### Método de Aceptación-Rechazo (A-R).

Este es un método general que se puede utilizar cuando el MTI es difícil o ineficiente de aplicar

Supongamos que queremos generar una V.A. X con FDP $$f(x)$$. Se elige otra FDP "mayorante" $$g(x)$$ (de la cual sea fácil generar variables, por ejemplo, usando MTI) y una constante $$c≥1$$ tal que $$f(x)≤c⋅g(x)$$ para todo x donde $$f(x)>0$$. La idea es generar un candidato Y a partir de $$g(y)$$, y luego "aceptarlo" como una realización de X con una probabilidad $$f(Y)/(c⋅g(Y))$$.

#### Algoritmo General.

1. Generar un candidato Y a partir de la distribución con FDP $$g(y)$$.
2. Generar un número $$U∼U(0,1)$$ (independiente de Y).
3. Si $$U≤c⋅g(Y)f(Y)$$​, entonces aceptar $$X=Y$$.
4. Si no, rechazar Y y volver al paso 1.

**Eficiencia.**

La probabilidad de aceptación en cada iteración es 1/c. Por lo tanto, se desea que c sea lo más cercano a 1 posible, lo que significa que la función "envolvente" $$c⋅g(x)$$ debe ser lo más ajustada posible a f(x).&#x20;

El número esperado de iteraciones para generar una observación es c

**Usos**

Útil para distribuciones como la Normal, usando una FDP Normal como mayorante para una parte, y exponenciales para las colas, como en el algoritmo Ziggurat, Gamma y Beta, donde el MTI no es directo.

### Método de Box-Muller para la Distribución Normal

Este es un método específico y elegante para generar _pares_ de variables aleatorias Normales estándar $$Z1​,Z2​∼N(0,1)$$ independientes, a partir de dos números aleatorios $$U1​,U2​∼U(0,1)$$ independientes.

$$
Z_1=\s−2lnU1cos(2πU2)Z2= −2lnU1sin(2πU 2)
$$

