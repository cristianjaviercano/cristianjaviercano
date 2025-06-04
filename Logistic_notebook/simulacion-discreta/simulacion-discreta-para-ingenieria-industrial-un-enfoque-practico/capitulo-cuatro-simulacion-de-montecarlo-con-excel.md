# Capitulo Cuatro: Simulación de Montecarlo con Excel

Objetivos:

1. Comprender los principios fundamentales y las aplicaciones típicas de la simulación de Montecarlo.
2. Utilizar eficientemente las funciones incorporadas en Microsoft Excel para generar números aleatorios y muestrear de distribuciones de probabilidad comunes.
3. Estructurar e implementar modelos de simulación de Montecarlo en hojas de cálculo de Excel para resolver problemas simples de ingeniería industrial, logística y producción.
4. Realizar análisis estadísticos básicos (media, desviación estándar, histogramas) de los resultados obtenidos de una simulación de Montecarlo en Excel.
5. Evaluar el impacto de la incertidumbre en los parámetros de un modelo y realizar análisis de sensibilidad básicos

***

### **Introducción a la simulación de Montecarlo.**

La simulación de Montecarlo es una técnica computacional que utiliza el muestreo aleatorio para obtener resultados numéricos. Esencialmente, se basa en la idea de repetir un experimento simulado muchas veces, utilizando en cada ocasión valores de entrada generados a partir de sus distribuciones de probabilidad, para luego analizar el conjunto de resultados obtenidos y así entender el comportamiento del sistema o proceso bajo estudio, especialmente en presencia de incertidumbre.  &#x20;

#### **Definición y Principio.**&#x20;

A diferencia de la simulación de eventos discretos que se enfoca en la evolución dinámica de sistemas a lo largo del tiempo, la simulación de Montecarlo se aplica a menudo a modelos estáticos o para evaluar el impacto de la incertidumbre en modelos que de otro modo serían deterministas. El nombre proviene del Casino de Montecarlo, aludiendo al carácter aleatorio inherente al método. La idea central es que, mediante un número suficiente de "experimentos" o "muestras" aleatorias, se puede aproximar la solución de problemas que serían difíciles o imposibles de resolver analíticamente.  &#x20;

### **Pasos Generales de un Estudio Montecarlo:**

1. **Definir el Modelo del Sistema:** Establecer las relaciones matemáticas o lógicas que describen el sistema o problema, identificando las variables de salida de interés (ej. ganancia, costo, tiempo de finalización).
2. **Identificar Entradas Inciertas:** Determinar qué variables de entrada o parámetros del modelo son inciertos y deben ser tratados como variables aleatorias.
3. **Especificar Distribuciones de Probabilidad:** Para cada entrada incierta, seleccionar y parametrizar una distribución de probabilidad adecuada que represente su variabilidad (ej. demanda Normal, duración de actividad Triangular).
4. **Generar Muestras Aleatorias (Replicaciones):** Para cada replicación del modelo:
   * Generar un valor aleatorio para cada variable de entrada incierta a partir de su distribución especificada.
   * Calcular el valor de la(s) variable(s) de salida del modelo utilizando estos valores de entrada generados.
5. **Repetir el Paso 4:** Realizar un gran número de replicaciones (cientos o miles) para obtener una muestra representativa de los posibles resultados de salida.
6. **Analizar Estadísticamente los Resultados:** Calcular estadísticas descriptivas (media, varianza, percentiles), construir histogramas o funciones de distribución empírica para las variables de salida, y estimar probabilidades de interés (ej. probabilidad de que la ganancia exceda un cierto umbral).

### **Aplicaciones Típicas en Ingeniería Industrial:**

* **Análisis de Riesgo en Proyectos e Inversiones:** Evaluar la distribución de posibles resultados financieros (ej. Valor Presente Neto - VPN, Tasa Interna de Retorno - TIR) cuando los flujos de caja o los costos son inciertos.  &#x20;
* **Estimación de Fiabilidad de Sistemas:** Calcular la probabilidad de que un sistema (compuesto por múltiples componentes con probabilidades de falla individuales) funcione correctamente.
* **Problemas de Inventario Simples:** Determinar políticas de pedido óptimas cuando la demanda es incierta (ej. el problema del vendedor de periódicos).  &#x20;
* **Planificación de la Producción bajo Incertidumbre:** Estimar la cantidad de producción necesaria para satisfacer una demanda fluctuante minimizando costos de inventario y faltantes.
* **Análisis de Tolerancias en Manufactura:** Evaluar cómo las variaciones en las dimensiones de las piezas afectan el ensamblaje final.
* **Estimación de Tiempos en Proyectos (PERT Estocástico):** Calcular la distribución del tiempo de finalización de un proyecto cuando las duraciones de las actividades son inciertas.  &#x20;

Excel, aunque no es un software de simulación especializado, es una plataforma muy accesible y ampliamente utilizada. Sus capacidades para generar números aleatorios y realizar cálculos estadísticos lo convierten en una herramienta útil para introducir los conceptos de la simulación de Montecarlo y para realizar análisis de modelos relativamente simples donde la dinámica temporal compleja no es el foco principal. Muchos problemas en ingeniería industrial que involucran incertidumbre en parámetros pueden ser abordados inicialmente con este enfoque antes de recurrir a herramientas más sofisticadas.  &#x20;

***

### **Uso de funciones de Excel para generar aleatoriedad: `ALEATORIO()`, `ALEATORIO.ENTRE()`.**

Microsoft Excel proporciona funciones incorporadas que son fundamentales para generar la aleatoriedad necesaria en las simulaciones de Montecarlo. Las dos funciones básicas son `ALEATORIO()` y `ALEATORIO.ENTRE()`.

* **`ALEATORIO()` (RAND):**
  * **Descripción:** Esta función genera un número real pseudoaleatorio que está uniformemente distribuido en el intervalo mayor o igual a 0 y menor que 1 (es decir, \[0,1)).  &#x20;
  * **Sintaxis:** `ALEATORIO()`
  * **Comportamiento:** Cada vez que la hoja de cálculo se recalcula (ya sea por un cambio en otra celda, al presionar la tecla F9, o al abrir el archivo), la función `ALEATORIO()` devuelve un nuevo número aleatorio. Esta volatilidad es esencial para generar múltiples replicaciones en una simulación de Montecarlo.
  * **Uso Base:** `ALEATORIO()` es la piedra angular para generar variables aleatorias de otras distribuciones mediante el método de la transformada inversa, como se verá en la siguiente sección.
  * **Fijar un Valor:** Si se desea conservar un valor aleatorio específico generado por `ALEATORIO()` sin que cambie con cada recálculo, se puede copiar la celda que contiene la función y luego usar la opción "Pegar Valores" para reemplazar la fórmula por su resultado numérico.  &#x20;
* **`ALEATORIO.ENTRE(inferior, superior)` (RANDBETWEEN):**
  * **Descripción:** Esta función devuelve un número entero pseudoaleatorio que está uniformemente distribuido entre los valores `inferior` y `superior`, ambos inclusive.  &#x20;
  * **Sintaxis:** `ALEATORIO.ENTRE(inferior, superior)`
    * `inferior`: El menor entero que la función puede devolver.
    * `superior`: El mayor entero que la función puede devolver.
  * **Comportamiento:** Al igual que `ALEATORIO()`, esta función es volátil y genera un nuevo entero aleatorio con cada recálculo de la hoja.
  * **Uso Típico:** Útil para modelar situaciones donde los resultados son enteros equiprobables dentro de un rango definido, como el resultado de lanzar un dado (`ALEATORIO.ENTRE(1,6)`), o para seleccionar aleatoriamente un ítem de una lista numerada.

Es importante comprender que tanto `ALEATORIO()` como `ALEATORIO.ENTRE()` generan números a partir de una _distribución uniforme_. Esto significa que cada valor posible dentro de sus respectivos rangos tiene la misma probabilidad de ocurrir. Si se necesita modelar fenómenos que siguen otras distribuciones (Normal, Exponencial, Poisson, etc.), será necesario transformar la salida de `ALEATORIO()` utilizando técnicas como la transformada inversa. Estas dos funciones, aunque simples, son los bloques de construcción esenciales para introducir la incertidumbre en los modelos de Excel y realizar simulaciones de Montecarlo.&#x20;

***

### Implementación de la Transformada Inversa en Excel para distribuciones comunes

El método de la transformada inversa (MTI) es una técnica fundamental para generar variables aleatorias (V.A.) a partir de una distribución de probabilidad específica, utilizando como base números aleatorios uniformemente distribuidos.

1.  Normal $$N(μ,σ2)$$

    1. &#x20;(media μ, desviación estándar σ)
       1. Excel proporciona una función directa para la inversa de la FDA Normal
          1. **Fórmula en Excel:** `=DISTR.NORM.INV(ALEATORIO(), media, desv_est)` o en inglés `=NORM.INV(RAND(), mean, standard_dev)`.  &#x20;
             * Reemplace `media` y `desv_est` con los valores deseados.&#x20;


2. Triangular (mínimo a, moda c, máximo b).

La FDA es $$F(x)$$ = $$\left\{ \begin{matrix} \frac{(x-a)^2}{(b-a)(c-a)}\  si\ a \le x\le c\\ 1- \frac{(b-x)^2}{(b-a)(b-c)}\  si\ c \le x\le b\end{matrix} \right\}$$

La inversa $$F^−1(u)$$ se define por tramos:&#x20;

$$Si\ u≤F(c)=(c−a)/(b−a)$$, entonces $$x=a+\sqrt {u(b−a)(c−a)}$$.&#x20;

$$Si\ u>F(c)$$, entonces $$x=b−\sqrt{(1−u)(b−a)(b−c)}$$



**Fórmula en Excel:**&#x20;

{% hint style="info" %}
**Asumiendo que a,c,b están en las celdas A1, B1, C1 respectivamente**
{% endhint %}

`=SI(ALEATORIO()<=(B1-A1)/(C1-A1), A1+RAIZ(ALEATORIO()*(C1-A1)*(B1-A1)), C1-RAIZ((1-ALEATORIO())*(C1-A1)*(C1-B1)))`&#x20;

_Esta fórmula usa `ALEATORIO()` dos veces, lo que genera dos números aleatorios diferentes. Para usar el mismo número aleatorio U para la condición y el cálculo, U debería generarse en una celda separada y referenciarse._&#x20;

Una mejor implementación sería: Celda D1: `=ALEATORIO()` Celda E1: `=SI(D1<=(B1-A1)/(C1-A1), A1+RAIZ(D1*(C1-A1)*(B1-A1)), C1-RAIZ((1-D1)*(C1-A1)*(C1-B1)))`&#x20;

#### **Bernoulli (probabilidad de éxito p):**

* La V.A. toma valor 1 (éxito) con probabilidad p, y 0 (fracaso) con probabilidad 1−p.
* La FDA es $$F(0)=1−p, F(1)=1.$$
* Si u\<p, X=1. Si u≥p, X=0. (O, más comúnmente, si u\<p, X=1, sino X=0).
* **Fórmula en Excel:** `=SI(ALEATORIO()<p, 1, 0)`
  * Reemplace `p` con la probabilidad de éxito.

**Binomial (n ensayos, probabilidad de éxito p):**

* Excel tiene una función inversa directa.
* **Fórmula en Excel:** `=INV.BINOM(n, p, ALEATORIO())` o en inglés `=BINOM.INV(trials, probability_s, RAND())`.  &#x20;
  * Reemplace `n` y `p` con los parámetros deseados.

