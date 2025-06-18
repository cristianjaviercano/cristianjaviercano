---
description: >-
  is a dynamic, typically stochastic, and computational modeling technique used
  to represent systems where changes in state occur only at specific, distinct
  points in time, known as events.
icon: coin-blank
---

# Discrete Event Simulation

**Discrete-event simulation (DES)** is an approach used to model dynamic systems that evolve through a series of events occurring at discrete and irregular points in time.

{% hint style="success" %}
Unlike a continuous process, changes in the system's state only occur at these specific moments when an event takes place, such as a customer's arrival or the completion of a service.
{% endhint %}

This type of simulation is particularly useful for analyzing systems where events are fundamental in determining their behavior, such as production lines, queueing systems, or any operation where the time between events is critical.

Discrete-event simulation models are often **stochastic**, meaning they include uncertainty or random variability. Events change based on random occurrences—these are called **discrete events**. For example, imagine a queueing system where the system's state is the number of customers in it. The events that impact this and change its state are **arrivals** or **departures** from the queue.

On the other hand, in **continuous simulations**, changes in the system's state occur **continuously over time**. For example, imagine an airplane in flight as the system under observation, with its state defined by its position. This position varies along the trajectory throughout the entire observation period. Another example would be chemical processes or reactions where measurements like pressure or other variables must be continuously observed due to their change over time.

### Exercise Number One: The Miami Casino Game

Imagine you've won a competition: an all-expenses-paid trip to a five-star hotel in Miami, Florida, United States. At this hotel, there's a casino where you decide to gamble, but you're not interested in traditional games. So, you opt for a new one with the following rules:

* In each round, an **unbiased coin** is tossed repeatedly until the **difference between the number of heads and tails** that appears reaches **three**.
* If you decide to participate, you must **pay one dollar for each coin toss**. You **cannot abandon the game** until it finishes, or you will incur a penalty.
* You **receive eight dollars at the end of the game**.

This means you win money if the number of tosses is less than eight, but you lose money if the coin is tossed more than eight times.

Let's follow these examples where C **is Heads** and S **is Tails**.

| Resultados  | Lanzamientos | Ganancias   |
| ----------- | ------------ | ----------- |
| CCC         | 3            | Se gana 5   |
| CSCCC       | 5            | Se gana 3   |
| SCCSCSCSSSS | 11           | Se pierde 3 |

Now try to play this game, but first lets make a simualtion in Python in order to know what woukd happen.

```python
import random
# define las variables del codigo.
def simular_juego():
    caras = 0
    sellos = 0
    lanzamientos = 0

    while abs(caras - sellos) < 3:
        lanzamiento = random.choice(['C', 'S'])
        if lanzamiento == 'C':
            caras += 1
        else:
            sellos += 1
        lanzamientos += 1

    # Calcula el resultado financiero
    ganancia = 8 - lanzamientos
    return lanzamientos, ganancia

def simular_varios_juegos(n):
    resultados = [simular_juego() for _ in range(n)]
    for i, (lanzamientos, ganancia) in enumerate(resultados):
        print(f"Juego {i+1}: {lanzamientos} lanzamientos, {'ganó' if ganancia > 0 else 'perdió'} {abs(ganancia)} dólares")

# Simula N juegos, selecciona la cantidad de juegos que deseas evaluar
simular_varios_juegos(10)

```

{% hint style="info" %}
Juego 1: 3 lanzamientos, ganó 5 dólares\
Juego 2: 3 lanzamientos, ganó 5 dólares\
Juego 3: 15 lanzamientos, perdió 7 dólares\
Juego 4: 7 lanzamientos, ganó 1 dólares\
Juego 5: 7 lanzamientos, ganó 1 dólares\
Juego 6: 3 lanzamientos, ganó 5 dólares\
Juego 7: 7 lanzamientos, ganó 1 dólares\
Juego 8: 3 lanzamientos, ganó 5 dólares\
Juego 9: 5 lanzamientos, ganó 3 dólares\
Juego 10: 5 lanzamientos, ganó 3 dólares

-¿are you in?
{% endhint %}

### Now let's try to perform this small Simulation in EXCEL.

We need to generate a sequence of random observations from a **uniform distribution between 0 and 1**. To refer to random observations from a uniform distribution, we will use the **"RAND()"** function.

Where: The probability of getting Heads is ½ and the probability of getting Tails is ½.

$$
P(Caras) = \frac{1}{2} ; P(sellos) = \frac{1}{2}
$$

| Lower bound | Uper bound |   |
| ----------- | ---------- | - |
| 0,0000      | 0,4999     | C |
| 0,5000      | 0,99999    | S |

_We unse the formula_

$$= SI(ALEATORIO NÚMERO \lt 0,5, "Cara", "Cruz").$$

puedes usar otras celdas donde tengas las funciones "contar.si" para contar las "caras" y "sellos" haciendo la diferencia para saber cuando detenerte.

{% hint style="success" %}
juego sacado del libro . Hillier, F. S., & Lieberman, G. J. (2010). Introducción a la Investigación de Operaciones (9th ed.). McGraw-Hill
{% endhint %}

#### Teoria de colas en la simulacion un acercamiento ilustrativo

Consideremos el modelo M/M/1 con los siguientes parametros:

* entradas de poisson, tiempo de servicio exponencial y un solo servidor. donde la tasa de llegada $$\lambda = 3u/hora \ y \ \mu= 5u/hora$$

el sistema es sencillo, los clientes que llegan se unen a  una cola, son atendidos y luego se van del sistema, iniciamos el reloj de la simulacion en 0 es decir. t = 0, tendremos una hora de corrida de la simulacion, donde el estado actual del mismo es:

$$
N(t) = No\ de\ Clientes\ en\ el\ tiempo\ t
$$

los eventos como dijimos anteriormente, en la explicacion, que cambian el estado del sistema es la **llegada** y **Salida** de clientes del sistema.

La formula de transcicion de estado es:

$$
Reestablecer\ N(t) = \left\{ \begin{aligned}N(t) +1 \text{ si una llegada ocurre en el tiempo t } \\ N(t) - 1 \ \text{si un servicio se completa en tiempo t}\end{aligned} \right\}
$$

#### Comportamiento y Pasos para Resolver un Problema M/M/1

Un sistema M/M/1 es un modelo básico de teoría de colas utilizado para representar un sistema con llegadas, un servicio y una sola fila. A continuación se detalla el comportamiento del sistema y los pasos necesarios para resolver problemas relacionados:

1. **Definición del Sistema**:
   * **Llegadas**: Los clientes llegan siguiendo un proceso de Poisson con una tasa de llegada $$(\lambda)$$, lo que significa que el tiempo entre llegadas sucesivas es aleatorio y sigue una distribución exponencial.
   * **Servicio**: Los tiempos de servicio también son aleatorios y siguen una distribución exponencial con una tasa de servicio $$(\mu)$$. Hay un único servidor disponible para atender a los clientes.
   * **Cola Única**: El sistema tiene una sola cola, donde los clientes esperan su turno para ser atendidos. Una vez atendidos, los clientes salen del sistema.

este modelo hace referencia a los modelos de "nacimiento y muerte" de la **teoria de colas** explicado de forma general por el modelo **M/M/s**, este supone que los tiempos de llegadas son independientes y distribuidos deacuerdo con una distribucion exponencial, proceso de entrada de poisson , se le conoce como modelo de nacimiento y muerte cuando la tas ade llegada nedia y la tasa de servicio media son constantes e independientes del estado del sistema.

en nuestro caso tenemos un solo servidor. s =1 , por que lo que es facil expresarla, lo que no seria si s > 1.&#x20;

la **tasa de servicio del sistema** $$\mu_n$$ Representa la tasa media de los servicios terminados de todo el sistema de colas cuando existen n clientes en él; caso diferente cuando tenemos multiples servidores (s > 1) en tonces $$\mu_n$$ no es lo mismo que $$\mu$$,&#x20;

$$\mu = n\mu\ \text{cuando n es} \le s,$$ &#x20;

&#x20;$$\mu = s\mu\ \text{cuando n es} \ge s,$$

usando estas formulas procedemos a calcular los factores $$C_n$$ del proceso de nacimiento y muerte



$$
C_n = \left(\frac{\lambda}{\mu}\right)^n =\rho^n, \ \text{para}\  n=0,1,2,...
$$

por lo tanto,

$$
P_n = \rho^nP_0, \ para\ n=0,1,2,...
$$

Donde

$$
P_0 = \left( \sum_{n=0}^{\infty} \rho^n \right)^{-1}
$$

$$
=1 - \rho.
$$

$$
P_n = (1 - \rho) \rho^n \quad \forall n \in \{0, 1, 2, \ldots\}
$$

#### Hgamos un ejemplo de este sistema

Considérese una sucursal bancaria pequeña que cuenta con un único cajero. Los clientes llegan a esta sucursal para ser atendidos por el cajero. Se asume que este sistema puede ser modelado como una cola [M/M/1,](https://en.wikipedia.org/wiki/M/M/1_queue)

**Llegadas (M):** Las llegadas de clientes siguen un proceso de Poisson con una tasa media de λ clientes por unidad de tiempo. Esto significa que los tiempos entre llegadas sucesivas son variables aleatorias independientes e idénticamente distribuidas (i.i.d.) según una distribución exponencial con media $$\frac{1}{\lambda}$$

**Servicio (M):** Los tiempos de servicio del cajero siguen una distribución exponencial con una tasa media de servicio de μ clientes por unidad de tiempo (si el cajero está ocupado). Esto significa que la duración del servicio es una variable aleatoria con media 1/μ.

**Servidor (1):** Hay un único servidor (el cajero).

**Capacidad del sistema:** Se asume una capacidad infinita para la cola (los clientes siempre esperan si el cajero está ocupado).

**Disciplina de la cola:** Los clientes son atendidos en orden de llegada (FCFS - First Come, First Served).

Para este ejemplo, se utilizaremos los siguientes parámetros:

* Tasa media de llegada de clientes (λ): 20 clientes por hora.
* Tasa media de servicio del cajero (μ): 25 clientes por hora.

{% hint style="warning" %}
Es fundamental que λ<μ para que el sistema sea estable y no crezca indefinidamente. En este caso, 20<25, por lo que el sistema es estable.
{% endhint %}

Solucionando, Las principales medidas de desempeño para un sistema M/M/1 en estado estacionario se calculan con las siguientes fórmulas (Gross, Shortle, Thompson, & Harris, 2008)

**Factor de utilización del servidor (ρ)**: Es la proporción de tiempo que el servidor está ocupado.&#x20;

$$
ρ=\frac{μ}{λ}
$$

**Probabilidad de que el sistema esté vacío (P0​)**: Probabilidad de que no haya clientes en el sistema (el cajero está ocioso).&#x20;

$$
P_0​=(1−ρ)
$$

**Probabilidad de que haya n clientes en el sistema (Pn​)**:

$$
P_n=(1−ρ)ρ^n=P_0ρ^n
$$

**Número promedio de clientes en el sistema (L)**: Incluye los que están en cola y el que está siendo atendido.

$$
L = \frac{ρ}{1−ρ} = \frac{λ}{μ−λ}
$$

**Número promedio de clientes en la cola (Lq​)**:

$$
L = \frac{ρ^2}{1−ρ} = \frac{λ^2}{μ(μ−λ)}
$$

**Tiempo promedio que un cliente pasa en el sistema (W)**: Tiempo total desde la llegada hasta la salida (espera + servicio).

$$
W = \frac{L}{\lambda} = \frac{1}{\mu - \lambda}
$$

**Tiempo promedio que un cliente pasa esperando en la cola (Wq​)**:

$$
W_q= \frac{\lambda}{\mu(\mu - \lambda)}
$$

También se puede calcular como $$W_q = W - \frac{1}{\mu}$$

{% hint style="info" %}
MINI TAREA: Calciula cada uno de los indices y saca tus conclusiones.
{% endhint %}

#### Apliquemos un poco de python al asunto...

```
 Calcula las medidas de desempeño para un sistema de colas M/M/1.

    Argumentos:
        lambda_val (float): Tasa media de llegada de clientes (clientes/unidad de tiempo).
        mu_val (float): Tasa media de servicio (clientes/unidad de tiempo por servidor ocupado).
        n_val (int, optional): Número específico de clientes en el sistema para calcular P_n.
                               Si es None, P_n no se calcula específicamente para un n dado.

    Returns:
        dict: Un diccionario con las medidas de desempeño si el sistema es estable (rho < 1).
              Retorna None si el sistema es inestable (rho >= 1).

```

```python
/def analizar_sistema_MM1(lambda_val, mu_val, n_val=None):
  
    if lambda_val <= 0 or mu_val <= 0:
        print("Error: Las tasas de llegada y servicio deben ser positivas.")
        return None
        
    if lambda_val >= mu_val:
        print(f"Error: El sistema es inestable o está críticamente cargado (lambda >= mu). Rho = {lambda_val/mu_val:.2f}")
        rho = lambda_val / mu_val
        resultados = {
            "lambda": lambda_val,
            "mu": mu_val,
            "rho": rho,
            "estable": False,
            "mensaje": "Sistema inestable o críticamente cargado."
        }
        return resultados

    rho = lambda_val / mu_val
    P0 = 1 - rho
    
    L = rho / (1 - rho)
    Lq = (rho**2) / (1 - rho)
    # Alternativamente: Lq = L - rho
    
    W = L / lambda_val 
    # Alternativamente: W = 1 / (mu_val - lambda_val)
    Wq = Lq / lambda_val
    # Alternativamente: Wq = rho / (mu_val - lambda_val)

    resultados = {
        "lambda": lambda_val,
        "mu": mu_val,
        "rho": rho,
        "P0": P0,
        "L (clientes en sistema)": L,
        "Lq (clientes en cola)": Lq,
        "W (tiempo en sistema)": W,
        "Wq (tiempo en cola)": Wq,
        "estable": True
    }

    if n_val is not None and isinstance(n_val, int) and n_val >= 0:
        Pn = P0 * (rho**n_val)
        resultados[f"P{n_val} (probabilidad de {n_val} clientes)"] = Pn
        
    return resultados

# Aplicación del ejemplo que estamos trabajando
lambda_banco = 20  # clientes por hora
mu_banco = 25    # clientes por hora

# Calcular para n=3 específicamente también
metricas_banco = analizar_sistema_MM1(lambda_banco, mu_banco, n_val=3)

if metricas_banco:
    print("\n--- Resultados del Sistema M/M/1 (Cajero Bancario) ---")
    for medida, valor in metricas_banco.items():
        if isinstance(valor, float):
            print(f"{medida}: {valor:.4f}")
        else:
            print(f"{medida}: {valor}")
    
    # Convertir tiempos a minutos para mejor interpretación
    if metricas_banco["estable"]:
        print(f"\nW (tiempo en sistema en minutos): {metricas_banco['W (tiempo en sistema)'] * 60:.2f} min")
        print(f"Wq (tiempo en cola en minutos): {metricas_banco['Wq (tiempo en cola)'] * 60:.2f} min")
```

{% hint style="info" %}
Mini tarea, abre tu hoja de google colab o VScode e intenta
{% endhint %}
