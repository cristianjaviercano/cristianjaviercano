---
icon: chart-area
---

# Distribuciones de probabilidad.

## DISTRIBUCION DE BERNOULLI

#### 1. Defunicion de la DB

> La **distribución de Bernoulli** es la distribución de probabilidad discreta más fundamental. Describe un experimento o ensayo que tiene únicamente **dos resultados posibles**, los cuales son mutuamente excluyentes. Estos resultados se denominan genéricamente:

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

> La **distribución Binomial** es una distribución de probabilidad discreta que describe el **número de éxitos** en una secuencia de **n ensayos de Bernoulli** independientes entre sí.

Para que una variable aleatoria siga una distribución Binomial, el experimento debe cumplir con las siguientes condiciones fundamentales:

1. El experimento consiste en una secuencia de n ensayos idénticos y fijos.
2. Cada ensayo tiene únicamente dos resultados posibles: "éxito" o "fracaso".
3. La probabilidad de éxito, denotada por p, es constante en cada uno de los ensayos. La probabilidad de fracaso es, por lo tanto, 1−p.
4. Los ensayos son estadísticamente independientes, lo que significa que el resultado de un ensayo no afecta el resultado de ningún otro.

Esta distribución está definida por dos parámetros: **n** (el número de ensayos) y **p** (la probabilidad de éxito).

***

### **2. ¿Cómo y Cuándo se Usa?**

Se utiliza para modelar el número de veces que ocurre un evento de interés en un número fijo de intentos. Es una de las distribuciones más utilizadas en control de calidad, genética, finanzas y ciencias sociales.

Algunos ejemplos de su aplicación son:

* En **control de calidad**: Calcular la probabilidad de encontrar exactamente k piezas defectuosas en un lote de n unidades extraídas de una línea de producción.
* En **medicina**: Determinar la probabilidad de que k pacientes de un grupo de n respondan positivamente a un tratamiento.
* En **marketing**: Estimar la probabilidad de que k clientes de un grupo de n que recibieron una promoción, realicen una compra.
* En **juegos de azar**: Calcular la probabilidad de obtener exactamente k "caras" al lanzar una moneda n veces.

***

### **3. Forma Algebraica**

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

### **4. Forma en Excel**

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

### **5. Forma de Usarla en Simulación (AnyLogic)**

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

***

## DISTRIBUCION DE POISSON

### **1. Definición**

> La **distribución de Poisson** es una distribución de probabilidad discreta que expresa la probabilidad de que un número determinado de eventos ocurra en un **intervalo fijo de tiempo o espacio**. La condición fundamental es que estos eventos deben ocurrir con una tasa media conocida y de forma independiente al tiempo transcurrido desde el último evento.

A diferencia de la distribución Binomial que cuenta éxitos en un número fijo de ensayos (n), la distribución de Poisson cuenta el número de ocurrencias en un continuo (como tiempo o área). Está definida por un único parámetro:

* **λ (lambda)**: La tasa media de ocurrencia de los eventos en el intervalo especificado.

***

### **2. ¿Cómo y Cuándo se Usa?**

> Es una de las distribuciones más importantes en la investigación de operaciones y la ingeniería, especialmente en la **Teoría de Colas**. Se utiliza para modelar eventos que se consideran "raros" o aleatorios en un intervalo.

Algunos ejemplos de su aplicación son:

* El número de llamadas telefónicas que llegan a un conmutador en un intervalo de una hora.
* El número de defectos o imperfecciones por metro cuadrado en una lámina de acero.
* El número de clientes que llegan a un banco o a una caja de supermercado por minuto.
* El número de averías de una máquina en un día de operación.

Su uso más común en simulación es para modelar **procesos de llegada**.

***

### **3. Forma Algebraica**

Sea X la variable aleatoria que representa el número de ocurrencias de un evento en un intervalo. La **Función de Masa de Probabilidad (fmp)** de la distribución de Poisson es:

$$
f(k;λ)=P(X=k)=\frac{λ^ke^{−λ}}{k!}​
$$

donde:

* k es el número de ocurrencias, y puede tomar valores enteros no negativos {0,1,2,...}.
* λ es la tasa media de ocurrencias por intervalo.
* e es la base del logaritmo natural (aproximadamente 2.71828...).

Una propiedad única y fundamental de la distribución de Poisson es que su valor esperado y su varianza son iguales a su parámetro λ.

* **Valor Esperado (Media)**: $$E[X]=λ$$
* **Varianza**: $$Var(X)=λ$$

***

**4. Forma en Excel**

Excel tiene una función específica para la distribución de Poisson: `POISSON.DIST` (o `POISSON` en versiones en español).

La sintaxis es: `POISSON.DIST(x; media; acumulado)`

* **`x`**: El número de eventos, k, para el que se quiere calcular la probabilidad.
* **`media`**: La tasa media de ocurrencia, λ.
* **`acumulado`**:
  * **`FALSO`**: Calcula la probabilidad de tener _exactamente_ k eventos (P(X=k)).
  * **`VERDADERO`**: Calcula la probabilidad de tener _hasta_ k eventos (P(X≤k)), correspondiente a la FDA.

**Ejemplo:** Los clientes llegan a una caja a una tasa media de 15 por hora (λ=15). ¿Cuál es la probabilidad de que lleguen exactamente 10 clientes en una hora (k=10)? `=POISSON.DIST(10; 15; FALSO)` devuelve `0.0486` (un 4.86%).

***

**5. Forma de Usarla en Simulación (AnyLogic)**

Este es un punto crucial y a menudo confuso. En la simulación de eventos discretos, rara vez se usa la distribución de Poisson directamente para generar llegadas, porque los modelos no avanzan en intervalos de tiempo fijos, sino de un evento al siguiente.

Lo que se modela es el **tiempo entre eventos sucesivos**. Existe una relación fundamental entre la distribución de Poisson y la Exponencial:

> Si el **número de eventos** en un intervalo de tiempo sigue una distribución de Poisson con tasa media λ, entonces el **tiempo entre cada evento sucesivo** sigue una **distribución Exponencial** con un tiempo medio de λ1​.

Por lo tanto, para modelar un **proceso de llegadas de Poisson** en AnyLogic, se utiliza la distribución Exponencial en el bloque `Source`:

*   **Implementación**: En un bloque `Source`, para modelar llegadas Poisson con una tasa λ, en el campo **Tiempo entre llegadas (Interarrival time)**, se debe usar la función:Java

    ```
    exponential(1.0 / lambda)
    ```

**Uso directo de `poisson()` en AnyLogic:**

AnyLogic sí tiene una función `poisson(lambda)`, pero no se usa para el tiempo entre llegadas. Se usa cuando se necesita generar un número entero que representa una cantidad.

**Ejemplo de uso:**

* **Para llegadas**: Un taller recibe trabajos de reparación según un proceso de Poisson con una media de 2 trabajos por hora (λ=2). En el bloque `Source` se configuraría: `Tiempo entre llegadas` = `exponential(1.0 / 2)` horas.
* **Para cantidades**: Un camión llega a un almacén una vez al día. El número de paquetes que descarga sigue una distribución de Poisson con media de 30 paquetes. Para generar cuántas entidades "paquete" crear, se usaría: `int n_paquetes = poisson(30);`.

***

## **Distribución Geométrica**

***

### **1. Definición**

> La **distribución Geométrica** es una distribución de probabilidad discreta que modela el número de **ensayos de Bernoulli** independientes y sucesivos que son necesarios hasta que se observa el **primer "éxito"**.

Al igual que la distribución Binomial, se basa en un proceso de Bernoulli, por lo que debe cumplir con las siguientes condiciones:

1. Cada ensayo tiene únicamente dos resultados posibles: "éxito" o "fracaso".
2. La probabilidad de éxito, p, es constante en cada ensayo.
3. Los ensayos son estadísticamente independientes.

La diferencia clave con la distribución Binomial es que la Geométrica no tiene un número fijo de ensayos (n). El experimento continúa hasta que se alcanza el primer éxito. El parámetro que la define es únicamente **p**, la probabilidad de éxito.

***

### **2. ¿Cómo y Cuándo se Usa?**

Se utiliza para modelar situaciones de "espera para el primer evento" en un contexto de ensayos discretos e independientes. Es particularmente útil en áreas de control de calidad, fiabilidad y análisis de procesos.

Algunos ejemplos de su aplicación son:

* En **manufactura**: Para determinar el número de piezas que se deben inspeccionar hasta encontrar la primera unidad defectuosa.
* En **telecomunicaciones**: El número de veces que debe retransmitirse un paquete de datos hasta que se reciba sin errores.
* En **ventas**: El número de clientes potenciales que un vendedor debe contactar hasta lograr la primera venta.
* En **juegos de azar**: El número de veces que se debe lanzar un dado hasta que aparezca por primera vez un "6".

***

### **3. Forma Algebraica**

Existen dos variantes comunes de la distribución geométrica. La más utilizada en textos como el de Taha modela el número de fracasos _antes_ del primer éxito.

Sea X la variable aleatoria que representa el **número de fracasos** antes de que ocurra el primer éxito. La **Función de Masa de Probabilidad (fmp)** es:

$$f(k;p)=P(X=k)=(1−p)^kp\ para\ k=\{0,1,2,...\}$$

donde:

* k es el número de fracasos.
* p es la probabilidad de éxito.
* (1−p) es la probabilidad de fracaso.

Las principales medidas estadísticas para esta forma son:

* **Valor Esperado (Media)**: $$E[X]=\frac {1−p​}{p}.$$
  * ​ (el número esperado de fracasos antes del primer éxito).
* **Varianza**: $$Var(X)=\frac {1−p​}{p^2}.$$

_(Nota: La otra variante define la variable aleatoria como el número total de ensayos, k′, para lograr el primer éxito. En ese caso,_ $$P(X=k′)=(1−p)^{k′−1}p\ para\ k′=1,2,...$$_, y su media es 1/p.)_

***

### **4. Forma en Excel**

Aunque algunas versiones recientes de Excel incluyen `GEOM.DIST`, la función más compatible y universal es `NEGBINOM.DIST` (o `DISTR.NEGBINOM` en español), ya que la distribución Geométrica es un caso especial de la Binomial Negativa donde el número de éxitos deseado es 1.

La sintaxis es: `DISTR.NEGBINOM(núm_fracaso; núm_éxito; prob_éxito; acumulado)`

Para simular un ensayo Geométrico:

* `núm_fracaso`: El valor de k (el número de fracasos).
* `núm_éxito`: Siempre será **1**.
* `prob_éxito`: La probabilidad de éxito, **p**.
* `acumulado`: Siempre será **FALSO**.

**Ejemplo:** Un jugador de baloncesto tiene una probabilidad de encestar un tiro libre de 0.8 (p=0.8). ¿Cuál es la probabilidad de que falle exactamente 2 veces (k=2) antes de su primer acierto? `=DISTR.NEGBINOM(2; 1; 0.8; FALSO)` devuelve `0.032` (un 3.2%).

***

### **5. Forma de Usarla en Simulación (AnyLogic)**

En simulación, la distribución Geométrica es útil para modelar el número de intentos necesarios para que una acción aleatoria tenga éxito.

**En AnyLogic**, se puede obtener una muestra directamente con la función:

```java
geometric(p)
```

Esta función simula ensayos de Bernoulli con una probabilidad de éxito `p` y devuelve un valor entero que representa el **número total de ensayos realizados hasta obtener el primer éxito**. Es importante notar que el valor devuelto por `geometric(p)` es siempre ≥1 (corresponde a la segunda variante algebraica mencionada en la nota).

**Ejemplo de uso:** Un sistema de software realiza una verificación de seguridad que tiene una probabilidad de éxito del 95% (p=0.95) en cada intento. Para simular cuántos intentos se requieren hasta que la verificación pase, se usaría el siguiente código:

```java
int numeroDeIntentos = geometric(0.95);
```

La variable `numeroDeIntentos` contendrá un entero (1, 2, 3, etc.) que puede usarse para calcular el tiempo total consumido por el proceso de verificación.

***

De acuerdo, exploremos la **distribución Uniforme**, una de las más intuitivas y fundamentales. Es importante diferenciar sus dos variantes: la discreta y la continua.



## **Distribución Uniforme Discreta**

***

### **1. Definición**

> La **distribución Uniforme Discreta** describe un experimento donde hay un **número finito de resultados posibles y cada uno de ellos es igualmente probable**. Es la formalización matemática de un resultado puramente aleatorio dentro de un conjunto de opciones contables.

Está definida por el número de resultados posibles, n.

### **2. ¿Cómo y Cuándo se Usa?**

Se utiliza para modelar situaciones donde cada resultado discreto tiene la misma oportunidad de ocurrir.

* **Juegos de Azar**: El resultado de lanzar un dado no cargado, donde cada cara (1,2,3,4,5,6) tiene la misma probabilidad.
* **Muestreo**: Seleccionar una carta al azar de una baraja bien mezclada.
* **Computación**: Generar un número entero aleatorio dentro de un rango específico.

### **3. Forma Algebraica**

Sea X una variable aleatoria que puede tomar n valores distintos {x\_1​,x\_2​,...,x\_n​}. La **Función de Masa de Probabilidad (fmp)** es: $$P(X=x_i​)=\frac{1}{n}$$​,para cada i=1,2,...,n

Si los resultados son enteros consecutivos en un rango de a a b, entonces n = b−a+1.

* **Valor Esperado (Media)**: $$E[X]=\frac {a+b​}{2}$$
* **Varianza**: $$Var(X)=\frac{(b−a+1)^2−1}{12}​$$

### **4. Forma en Excel**

Excel no tiene una función específica para calcular la probabilidad (ya que es simplemente 1/n), pero sí para generar una muestra aleatoria de esta distribución:

`ALEATORIO.ENTRE(inferior; superior)` o `RANDBETWEEN(bottom, top)`

Esta función devuelve un número entero aleatorio entre los valores `inferior` y `superior` (ambos incluidos), donde cada entero tiene la misma probabilidad.

**Ejemplo:** Para simular el lanzamiento de un dado de 6 caras: `=ALEATORIO.ENTRE(1; 6)`

### **5. Forma de Usarla en Simulación (AnyLogic)**

En AnyLogic, se utiliza para seleccionar un resultado entero aleatorio de un rango donde todas las opciones son igualmente probables.

La función es:

Java

```
uniform_discrete(min, max)
```

Devuelve un número entero aleatorio entre `min` y `max`, inclusive.

**Ejemplo de uso:** Si un proceso de ensamble requiere seleccionar al azar uno de cuatro tipos de tornillos (numerados del 1 al 4), se puede usar `uniform_discrete(1, 4)` para determinar qué tipo de tornillo (`entidad`) se debe generar o tomar de un inventario.

***

## **Distribución Uniforme Continua**

***

### **1. Definición**

> La **distribución Uniforme Continua** describe una variable aleatoria que puede tomar **cualquier valor dentro de un intervalo \[a,b] con la misma probabilidad**. La probabilidad de que la variable caiga en cualquier sub-intervalo de una longitud determinada es la misma, sin importar la ubicación de ese sub-intervalo dentro de \[a,b].

Está definida por dos parámetros: **a** (el valor mínimo) y **b** (el valor máximo).

### **2. ¿Cómo y Cuándo se Usa?**

Es muy utilizada en simulación, especialmente cuando se conoce el rango de un proceso (mínimo y máximo) pero no se tiene información suficiente para justificar otra distribución. Es la distribución que representa la **máxima incertidumbre** dentro de un rango conocido.

* **Modelado de Tiempos de Operación**: El tiempo para realizar una tarea manual puede variar entre 5 y 10 minutos, pero no hay un valor que sea más probable que otro.
* **Estimaciones Iniciales**: Cuando no hay datos históricos, los expertos suelen proporcionar un rango "pesimista-optimista", que se modela bien con una distribución uniforme.

### **3. Forma Algebraica**

Sea X una variable aleatoria continua en el intervalo \[a,b].

* **Función de Densidad de Probabilidad (fdp)**:  $$f(x) = \begin{cases}   \frac{1}{b-a} & \text{para } a \leq x \leq b \\   0 & \text{en otro caso} \end{cases}$$​
* **Función de Distribución Acumulada (FDA)**: $$f(x) = \frac {x-a}{b-a}$$  para  $$a \le x \le b$$
* **Valor Esperado (Media)**: $$E[X]=2a+b​$$
* **Varianza**: $$Var(X)=\frac {(b−a)^2​}{12}$$

### **4. Forma en Excel**

Para generar una muestra de esta distribución, se utiliza la función `ALEATORIO()` (o `RAND()`), que devuelve un número decimal entre 0 y 1, y se escala al intervalo deseado \[a,b].

La fórmula es: `= a + (b-a) * ALEATORIO()`

**Ejemplo:** Para generar un tiempo de servicio que varía uniformemente entre 5 y 10 minutos: `= 5 + (10-5) * ALEATORIO()`

**5. Forma de Usarla en Simulación (AnyLogic)**

AnyLogic proporciona una función directa para muestrear de esta distribución, la cual es una de las más usadas para modelar tiempos de proceso.

La función es:

```java
uniform(min, max)
```

Devuelve un número de punto flotante (decimal) aleatorio uniformemente distribuido entre `min` y `max`.

**Ejemplo de uso:** En el caso de estudio de la "Fábrica de calzado", el tiempo de operación para el corte **Tipo 2** se distribuye uniformemente entre 45 y 60 segundos. En el bloque `Service` o `Delay` que modela esta operación, en el campo **Tiempo de servicio (Service time)**, se escribiría: `uniform(45, 60)` y se especificarían los segundos como unidad de tiempo.

***

## **Distribución Exponencial**

***

### **1. Definición**

> La **distribución Exponencial** es una distribución de probabilidad continua que describe el **tiempo que transcurre entre dos eventos sucesivos** de un proceso de Poisson. Si la llegada de eventos sigue una distribución de Poisson con una tasa media λ, el tiempo entre esas llegadas sigue una distribución Exponencial.

Está definida por un único parámetro:

* **λ (lambda)**: La **tasa media de ocurrencia** de los eventos por unidad de tiempo.

Una característica fundamental y única de esta distribución es su **propiedad de falta de memoria** (memoryless property). Esto significa que la probabilidad de que un evento ocurra en un futuro cercano es completamente independiente del tiempo que ya ha transcurrido. Por ejemplo, si el tiempo de vida de un componente sigue una distribución exponencial, la probabilidad de que falle en la próxima hora es la misma sin importar si ha estado funcionando por 10 horas o por 1000 horas.

***

### **2. ¿Cómo y Cuándo se Usa?**

Es la distribución por excelencia para modelar el tiempo entre eventos aleatorios e independientes en un proceso.

* **Teoría de Colas**: Es la distribución más común para modelar tanto los **tiempos entre llegadas** de clientes como los **tiempos de servicio**. El modelo de colas más básico, M/M/1, asume que ambas variables son exponenciales.
* **Ingeniería de Fiabilidad**: Se usa para modelar el **tiempo hasta la falla** de componentes que no sufren de desgaste por envejecimiento (la tasa de falla es constante).
* **Física**: Modela la desintegración radiactiva.

***

### **3. Forma Algebraica**

Sea T la variable aleatoria continua que representa el tiempo entre eventos.

* **Función de Densidad de Probabilidad (fdp)**: $$f(t)=λ^{e−λ}t,\ para t≥0$$
* **Función de Distribución Acumulada (FDA)**: $$F(t)=P(T≤t)=1−e^{−λt}$$
* **Valor Esperado (Media)**: El tiempo medio entre eventos. $$E[T]=\frac{1}{λ}$$​
* **Varianza**: $$Var(T)=(\frac{1}{λ}​)^2$$

Es crucial notar la relación inversa entre el parámetro λ y la media: si la tasa de llegada es de 10 clientes por hora (λ=10), el tiempo medio entre llegadas es de 1/10 de hora (6 minutos).

***

#### **4. Forma en Excel**

Excel tiene una función directa para la distribución exponencial: `EXPON.DIST` (o `DISTR.EXPON` en versiones en español).

La sintaxis es: `DISTR.EXPON(x; lambda; acumulado)`

* **`x`**: El valor del tiempo, t, que se quiere evaluar.
* **`lambda`**: La tasa de ocurrencia, λ.
* **`acumulado`**:
  * **`FALSO`**: Calcula el valor de la función de densidad, f(t).
  * **`VERDADERO`**: Calcula la probabilidad acumulada, F(t)=P(T≤t).

**Ejemplo:** Si los clientes llegan a un banco a una tasa de 20 por hora (λ=20), ¿cuál es la probabilidad de que el próximo cliente llegue en los próximos 3 minutos (0.05 horas)? `=DISTR.EXPON(0.05; 20; VERDADERO)` devuelve `0.632` (un 63.2%).

***

### **5. Forma de Usarla en Simulación (AnyLogic)**

Esta es la distribución más utilizada en los bloques `Source` de AnyLogic para modelar la llegada aleatoria de entidades (proceso de Poisson).

**En AnyLogic**, la función es:

```java
exponential(mean)
```

**¡Atención!** Este es un punto crítico. La función `exponential()` de AnyLogic **no toma la tasa λ como argumento**. En su lugar, toma el **tiempo medio entre eventos**, que es 1/λ.

**Ejemplo de uso:**

* **Llegadas**: Para modelar un proceso de llegadas de Poisson con una tasa media de 10 clientes por hora (λ=10), el tiempo medio entre llegadas es 1/10=0.1 horas. Por lo tanto, en el bloque `Source`, en el campo **Tiempo entre llegadas (Interarrival time)** se escribiría: `exponential(0.1)` y se asegurarían de que las unidades del modelo estén en horas. Una forma más segura es escribir `exponential(1.0 / 10.0)`.
* **Tiempo de Servicio**: Si el tiempo de servicio para un cliente es exponencial con una duración media de 12 minutos, en el campo de tiempo de servicio de un bloque `Service` se escribiría: `exponential(12)` (con las unidades del modelo en minutos).

***

## **Distribución Normal**

***

### **1. Definición**

La **distribución Normal**, también conocida como la **distribución Gaussiana** o **Campana de Gauss**, es la distribución de probabilidad continua más importante en toda la estadística y la ingeniería.

Se caracteriza por su forma de campana, simétrica respecto a su valor central. Queda completamente definida por dos parámetros:

* **μ (mu)**: La **media**, que representa el valor esperado y el centro de la distribución. Es el punto más alto de la campana.
* **σ (sigma)**: La **desviación estándar**, que mide la dispersión de los datos. Un valor de σ pequeño indica que los datos están muy concentrados alrededor de la media (una campana alta y estrecha), mientras que un valor grande indica mayor dispersión (una campana más ancha y plana).

***

### **2. ¿Cómo y Cuándo se Usa?**

Su aplicabilidad es vasta porque muchos fenómenos naturales y procesos de ingeniería tienden a seguir su patrón. La razón teórica de su prevalencia se debe al **Teorema del Límite Central**, que establece que la suma o el promedio de un gran número de variables aleatorias independientes tiende a distribuirse normalmente, sin importar la distribución original de dichas variables.

Se utiliza para modelar:

* **Características Físicas**: Estatura y peso de una población, dimensiones de piezas en un proceso de manufactura (ej. diámetro de un tornillo).
* **Errores de Medición**: Los errores aleatorios en experimentos científicos suelen agruparse alrededor de cero siguiendo una distribución normal.
* **Procesos Financieros**: Los rendimientos diarios de activos financieros a menudo se modelan con esta distribución.
* **Tiempos de Proceso**: Tiempos de operación que tienden a agruparse alrededor de un valor promedio, con desviaciones simétricas.

***

### **3. Forma Algebraica**

Sea X una variable aleatoria continua.

* **Función de Densidad de Probabilidad (fdp)**: $$F(x)=\frac{1}{σ \sqrt{2π}​}e^{-\frac{1}{2} \left(\frac{(x−μ​)}{σ }\right)^2},\ para\ −∞<x<∞$$
* **Función de Distribución Acumulada (FDA)**: La integral de esta función no tiene una forma cerrada simple, por lo que su cálculo se realiza numéricamente o mediante el uso de tablas estadísticas estandarizadas.
* **Valor Esperado (Media)**: $$E[X]=μ$$
* **Varianza**: $$f(x) = x * e^{2 pi i \xi x}$$

Para calcular probabilidades, se estandariza la variable X a una variable Z que sigue una distribución normal estándar (N con μ=0 y σ=1): Z=σX−μ​ Luego, se utilizan tablas o software para encontrar las probabilidades asociadas a Z.

***

### **4. Forma en Excel**

Excel proporciona funciones directas para la distribución Normal, siendo la más común `NORM.DIST` (o `DISTR.NORM` en español).

La sintaxis es: `DISTR.NORM(x; media; desv_estándar; acumulado)`

* **`x`**: El valor de la variable aleatoria.
* **`media`**: La media de la distribución, μ.
* **`desv_estándar`**: La desviación estándar, σ.
* **`acumulado`**:
  * **`VERDADERO`**: Calcula la FDA, P(X≤x). Este es el uso más habitual.
  * **`FALSO`**: Calcula el valor de la función de densidad, f(x).

**Ejemplo:** En un proceso de llenado, el volumen de una botella sigue una distribución N(500,5) ml. ¿Cuál es la probabilidad de que una botella contenga 498 ml o menos? `=DISTR.NORM(498; 500; 5; VERDADERO)` devuelve `0.3446` (un 34.46%).

***

**5. Forma de Usarla en Simulación (AnyLogic)**

En simulación, la distribución Normal es excelente para modelar tiempos de proceso o características de productos que tienen un valor objetivo claro, con variaciones aleatorias simétricas a su alrededor.

**En AnyLogic**, la función es:

```java
normal(mean, stdDev)
```

* **`mean`**: La media de la distribución, μ.
* **`stdDev`**: La desviación estándar, σ.

**Ejemplo de uso:** Recordando el caso de la "Fábrica de calzado", el tiempo de ensamble (Estación 2) se distribuye normalmente con una media de 3 minutos y una desviación estándar de 1 minuto. En el bloque `Service` que modela esta estación, se escribiría: `normal(3, 1)` y se seleccionarían los minutos como unidad.

**Advertencia Importante en Simulación:** Como ya experimentaste, la distribución Normal teóricamente puede generar valores negativos. Al modelar variables físicas como el tiempo o las dimensiones (que no pueden ser negativas), es una práctica de ingeniería indispensable **truncar la distribución** para evitar errores en tiempo de ejecución. La forma correcta de hacerlo es:

```java
max(0, normal(mean, stdDev))
```

Este comando asegura que si la función `normal()` devuelve un valor negativo, el sistema utilizará `0` en su lugar, manteniendo la integridad del modelo.
