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
{% tab title="Prueba de Chi Cuadrado" %}

{% endtab %}

{% tab title="Prueba de Kolmogorov-Smirnov (K-S)" %}

{% endtab %}
{% endtabs %}

