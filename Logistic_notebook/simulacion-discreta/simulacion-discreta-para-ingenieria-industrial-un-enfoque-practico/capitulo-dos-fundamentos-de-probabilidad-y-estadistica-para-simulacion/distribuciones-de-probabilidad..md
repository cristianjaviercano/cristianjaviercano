---
hidden: true
icon: chart-area
---

# Distribuciones de probabilidad.

### Distribucion de bernoulli

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

