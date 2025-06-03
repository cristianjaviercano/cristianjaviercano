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

#### 4. Calcular el Estadístico $\chi^2$

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

{% tab title="Tab 2" %}

{% endtab %}
{% endtabs %}







