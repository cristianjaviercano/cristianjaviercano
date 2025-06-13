---
icon: chart-area
---

# Distribuciones de probabilidad.

## DISTRIBUCION DE BERNOULLI

#### 1. Defunicion de la DB

La **distribución de Bernoulli** es la distribución de probabilidad discreta más fundamental. Describe un experimento o ensayo que tiene únicamente **dos resultados posibles**, los cuales son mutuamente excluyentes. Estos resultados se denominan genéricamente:

Matemáticamente.

1. Exito: $$P(X = 1) = p,$$
2. Fracaso $$\quad P(X = 0) = 1-p$$

Un solo experimento de este tipo se conoce como **ensayo de Bernoulli**. Por lo tanto, esta distribución modela el resultado de una única prueba o evento, no de una secuencia de ellos.

#### **2. ¿Cómo y Cuándo se Usa?**

Se utiliza para modelar cualquier situación en la que un evento único tiene un resultado binario. Es la base para distribuciones más complejas como la Binomial y la Geométrica.

Algunos ejemplos de su aplicación son:

* **Lanzamiento de una moneda**: El resultado es cara (éxito) o cruz (fracaso).
* **Inspección de Calidad**: Una pieza manufacturada es conforme (éxito) o defectuosa (fracaso).
* **Resultado de un Examen**: Un estudiante aprueba (éxito) o reprueba (fracaso).
* **Decisión de un Cliente**: Un cliente compra un producto (éxito) o no lo compra (fracaso).

#### **3. Forma Algebraica**

Para formalizarla, se define una variable aleatoria X que puede tomar dos valores:

* X=1 si el resultado es "éxito".
* X=0 si el resultado es "fracaso".

La **Función de Masa de Probabilidad (fmp)** de una variable aleatoria de Bernoulli es:

$$
f(x;p)=P(X=x)=p^x(1−p)^{1−x} \ para\ x∈\{0,1\}
$$

$$
Si\ x=1 (éxito): P(X=1)=p^1(1−p)^{1−1}=p×(1−p)^0=p
$$

$$
Si\ x=0\ (fracaso): P(X=0)=p^0(1−p)^{1−0}=1×(1−p)^1=1−p
$$

Las principales medidas estadísticas son:

* **Valor Esperado (Media)**: $$E[X]=p$$
* **Varianza**: $$Var(X)=p(1−p)$$

#### **4. Forma en Excel**

Excel no posee una función dedicada como `BERNOULLI.DIST`. Sin embargo, un ensayo de Bernoulli es un caso especial de la distribución Binomial donde el número de ensayos es 1 (n=1). Por lo tanto, se utiliza la función `BINOM.DIST` (o `DISTR.BINOM` en versiones en español).

La sintaxis es: `DISTR.BINOM(núm_éxito; ensayos; prob_éxito; acumulado)`

Para simular un ensayo de Bernoulli:

* `núm_éxito`: El resultado que se desea evaluar (1 para éxito, 0 para fracaso).
* `ensayos`: Siempre será **1**.
* `prob_éxito`: La probabilidad de éxito, **p**.
* `acumulado`: Siempre será **FALSO** (para obtener la probabilidad del valor exacto).

**Ejemplo:** Para calcular la probabilidad de que una pieza sea defectuosa (p=0.05), el resultado sería "éxito" si X=1. `=DISTR.BINOM(1; 1; 0.05; FALSO)` devuelve `0.05`.

#### **5. Forma de Usarla en Simulación (AnyLogic)**

En la simulación de sistemas, el ensayo de Bernoulli es crucial para modelar puntos de decisión probabilísticos. La implementación no requiere muestrear de una distribución compleja, sino comparar un número aleatorio con la probabilidad de éxito.

**Lógica de implementación:**

1. Generar un número aleatorio R de una distribución Uniforme(0, 1).
2. Si R≤p, el resultado es "éxito".
3. Si R>p, el resultado es "fracaso".

**En AnyLogic**, esto se simplifica enormemente con la función incorporada:

Java

```java
randomTrue(p)
```

Esta función devuelve el valor booleano `true` (éxito) con una probabilidad `p`, y `false` (fracaso) con una probabilidad `1-p`. Es la implementación directa de un ensayo de Bernoulli.

**Ejemplo de uso:** En un modelo de inspección de calidad, una entidad llega a un bloque `SelectOutput`. En la condición de dicho bloque, se puede escribir `randomTrue(0.98)`. Esto significaría que el 98% de las entidades (los "éxitos") serán enrutadas por la salida `true` (pasan la inspección), mientras que el 2% restante (los "fracasos") serán enviadas por la salida `false` (requieren retrabajo).\


***

## DISTRIBUCION BINOMIAL

### 1. Definicion

La **distribución Binomial** es una distribución de probabilidad discreta que describe el **número de éxitos** en una secuencia de **n ensayos de Bernoulli** independientes entre sí.

Para que una variable aleatoria siga una distribución Binomial, el experimento debe cumplir con las siguientes condiciones fundamentales:

1. El experimento consiste en una secuencia de n ensayos idénticos y fijos.
2. Cada ensayo tiene únicamente dos resultados posibles: "éxito" o "fracaso".
3. La probabilidad de éxito, denotada por p, es constante en cada uno de los ensayos. La probabilidad de fracaso es, por lo tanto, 1−p.
4. Los ensayos son estadísticamente independientes, lo que significa que el resultado de un ensayo no afecta el resultado de ningún otro.

Esta distribución está definida por dos parámetros: **n** (el número de ensayos) y **p** (la probabilidad de éxito).

***

**2. ¿Cómo y Cuándo se Usa?**

Se utiliza para modelar el número de veces que ocurre un evento de interés en un número fijo de intentos. Es una de las distribuciones más utilizadas en control de calidad, genética, finanzas y ciencias sociales.

Algunos ejemplos de su aplicación son:

* En **control de calidad**: Calcular la probabilidad de encontrar exactamente k piezas defectuosas en un lote de n unidades extraídas de una línea de producción.
* En **medicina**: Determinar la probabilidad de que k pacientes de un grupo de n respondan positivamente a un tratamiento.
* En **marketing**: Estimar la probabilidad de que k clientes de un grupo de n que recibieron una promoción, realicen una compra.
* En **juegos de azar**: Calcular la probabilidad de obtener exactamente k "caras" al lanzar una moneda n veces.

***

**3. Forma Algebraica**

Sea X la variable aleatoria que representa el número de éxitos en n ensayos. La **Función de Masa de Probabilidad (fmp)** de la distribución Binomial, que nos da la probabilidad de obtener exactamente k éxitos, es:

$$
f(k;n,p)=P(X=k)={n \choose k}p^k(1−p)^{n−k}
$$

donde:

* k es el número de éxitos, y puede tomar valores {0,1,2,...,n}.
* $${n \choose k}​=\frac{n!}{k!(n−k)!}​$$ es el **coeficiente binomial**, que representa el número de maneras diferentes en que se pueden obtener k éxitos en n ensayos.
* pk es la probabilidad de tener k éxitos.
* $$(1−p)^{n−k}$$ es la probabilidad de tener (n−k) fracasos.

Las principales medidas estadísticas son:

* **Valor Esperado (Media)**: E\[X]=np
* **Varianza**: Var(X)=np(1−p)

***

**4. Forma en Excel**

Excel proporciona una función directa para los cálculos de la distribución Binomial: `BINOM.DIST` (o `DISTR.BINOM` en versiones en español).

La sintaxis es: `DISTR.BINOM(núm_éxito; ensayos; prob_éxito; acumulado)`

* `núm_éxito`: El valor de k para el cual se desea calcular la probabilidad.
* `ensayos`: El número total de ensayos, n.
* `prob_éxito`: La probabilidad de éxito, p.
* `acumulado`:
  * **`FALSO`**: Calcula la probabilidad de tener _exactamente_ k éxitos. (P(X=k)).
  * **`VERDADERO`**: Calcula la probabilidad de tener _hasta_ k éxitos (P(X≤k)), es decir, la Función de Distribución Acumulada (FDA).

**Ejemplo:** En un proceso de manufactura, la probabilidad de que una pieza sea defectuosa es de 0.02 (p=0.02). Si se toma una muestra de 50 piezas (n=50), ¿cuál es la probabilidad de encontrar exactamente 2 piezas defectuosas (k=2)? `=DISTR.BINOM(2; 50; 0.02; FALSO)` devuelve `0.1858` (un 18.58%).

***

**5. Forma de Usarla en Simulación (AnyLogic)**

En simulación, la distribución Binomial se utiliza para determinar el resultado agregado de una serie de eventos binarios sin necesidad de simular cada uno de los n ensayos individualmente.

**En AnyLogic**, se puede obtener una muestra de una distribución binomial directamente con la función:

Java

```java
binomial(n, p)
```

Esta función realiza n ensayos de Bernoulli con una probabilidad de éxito p y devuelve un número entero que representa el **número total de éxitos** obtenidos.

**Ejemplo de uso:** Imaginemos un modelo de un puerto al que llega un buque con un cargamento de 200 contenedores (n=200). Por experiencia, se sabe que la probabilidad de que un contenedor sea seleccionado para una inspección de aduanas es del 15% (p=0.15).

Para determinar cuántos contenedores de ese buque serán inspeccionados, en lugar de simular 200 eventos `randomTrue(0.15)`, se puede usar una sola llamada:

Java

```java
int contenedores_a_inspeccionar = binomial(200, 0.15);
```

La variable `contenedores_a_inspeccionar` contendrá un número entero (por ejemplo, 30), que puede ser usado para dirigir ese número de entidades "contenedor" a una zona de inspección en el modelo.
