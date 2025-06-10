---
hidden: true
icon: colon
---

# Teoria de colas

{% hint style="info" %}
El proceso basico supuesto por la mayoria de los modelos, es que **Los clientes quieren un servicio**
{% endhint %}

### Teoria de colas.

**¿Qué es la Teoría de Colas?**

En su esencia, la Teoría de Colas es el **estudio matemático de las líneas de espera**. Su objetivo es analizar, modelar y predecir el comportamiento de sistemas donde las "entidades" (como clientes, productos, llamadas o datos) llegan en busca de un servicio, pero deben esperar si los "servidores" (recursos como cajeros, máquinas, operadores o procesadores) están ocupados.

El núcleo de cualquier sistema de colas se puede descomponer en:

* **Entidades**: Los elementos que fluyen a través del sistema y demandan servicio.
* **La Cola**: El lugar donde las entidades esperan.
* **La Estación de Servicio**: La combinación de la cola y los servidores que prestan el servicio.

### **El Enfoque Analítico y sus Limitaciones**

La Teoría de Colas nos proporciona un poderoso conjunto de **fórmulas matemáticas (soluciones analíticas)** para calcular indicadores de rendimiento clave:

* **Lq**: El número promedio de entidades en la cola.
* **Wq**: El tiempo promedio de espera en la cola.
* **L**: El número promedio de entidades en todo el sistema (en cola + en servicio).
* **W**: El tiempo promedio total en el sistema.

Para que estas fórmulas funcionen, el sistema debe ser clasificado usando una notación estándar, como la **notación de Kendall (A/B/C/D/E)**, que describe las características del sistema (ej. tipo de llegadas, tipo de servicio, número de servidores).

<details>

<summary>Notación de Kendall</summary>

La notación de Kendall es una manera estandarizada de describir colas en sistemas de espera y es vital para clasificar los modelos dentro de la teoría de colas. La notación típicamente tiene la forma de A/B/C/D/E, donde:

* **A**: Distribución del tiempo entre llegadas (ej. M para Poisson).
* **B**: Distribución del tiempo de servicio (ej. M para Exponencial).
* **C**: Número de servidores (por ejemplo, 1 para un solo servidor).
* **D**: Capacidad total del sistema (puede ser ∞ para ilimitada).
* **E**: Tamaño de la población fuente de clientes (puede ser ∞ para ilimitada).

Utilizar correctamente esta notación ayuda a identificar rápidamente las características del sistema y a aplicar las fórmulas analíticas adecuadas.

</details>



Sin embargo, aquí es donde encontramos la gran limitación de la teoría pura: **estas fórmulas solo son válidas bajo supuestos muy estrictos y simplificados**.&#x20;

* Por ejemplo, las fórmulas clásicas asumen que las llegadas siguen una distribución de Poisson y los tiempos de servicio una distribución Exponencial (el sistema M/M/1, por ejemplo).

¿Qué sucede cuando el sistema real es más complejo?

* ¿Si los tiempos de servicio siguen una distribución Normal o Triangular?
* ¿Si hay múltiples pasos en el proceso con diferentes tipos de recursos?
* ¿Si los clientes pueden abandonar la cola (renegar)?
* ¿Si hay prioridades (clientes VIP)?

En estos casos, las soluciones matemáticas se vuelven extremadamente complejas o, la mayoría de las veces, **simplemente no existen**.\
\
Un factor de utilización por debajo de 1 indica que el sistema tiene capacidad suficiente para atender a los clientes.

### **La Teoría de Colas en la Práctica con AnyLogic**

Los conceptos de la Teoría de Colas se mapean directamente a los bloques de la **Process Modeling Library (PML)** de AnyLogic:

* Las **llegadas de entidades** se modelan con el bloque `Source`.
* La **cola** se modela con el bloque `Queue` (o la cola interna del bloque `Service`).
* Los **servidores** se modelan como `Resources` en un `ResourcePool`.
* La **estación de servicio** se modela con un bloque `Service` (que combina `Seize`, `Delay` y `Release`).

### que es una ENTRADA en el sistema:

la entrada se dentoa como el ingreso de los agentes al sistema, la primera caracteristica que encontramos es el _Tamaño, el cual._ es el número total de clientes que pueden requerir el servicio ofrecido por el sistema en un momento específico, en otras palabras los **clientes potenciales**

esta poblacion es la **poblacion de entrada** esta puede ser de tamaño Finito o Infinito, tambien alfgunos autores le llaman de naturaleza _limtadad o ilimitada._

se debe especificar el **patron estadistico mediante el cual se generan los clientes en el tiempo, el** supuesto mas Normal es que se generan  por una distribucion de _poisson\*_,&#x20;

<details>

<summary>La <strong>distribución de Poisson</strong></summary>

Es una distribución de probabilidad discreta que expresa la probabilidad de que un número determinado de eventos ocurra en un intervalo fijo de tiempo o espacio. Estos eventos deben suceder con una tasa promedio constante y ser independientes entre sí. La fórmula de probabilidad para que ocurran exactamente ( k ) eventos es:

$$P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}$$

donde $$\lambda$$  es la tasa promedio de ocurrencia de eventos y ( e ) es la base del logaritmo natural. Esta distribución es comúnmente utilizada para modelar la llegada de entidades en sistemas como colas o procesos de servicio.

</details>

<img src="../../../.gitbook/assets/file.excalidraw (1).svg" alt="Sistema de colas conceptual" class="gitbook-drawing">

### Disciplina de la cola

La _orden_ mencionada se refiere al procedimiento mediante el cual se escoge qué miembros recibirán el servicio específico en cuestión. Este proceso de selección puede estructurarse de diversas maneras, incluyendo pero no limitándose a las siguientes:

1. **Primero en llegar, primero en ser atendido:** Esta metodología asigna servicios siguiendo la secuencia de llegada de los miembros, atendiendo a quienes primero soliciten el servicio antes que a los demás.
2. **Prioridad por niveles de membresía:** En esta modalidad, se da preferencia a aquellos miembros con un nivel de membresía más alto, pudiendo así acceder al servicio antes que otros con niveles inferiores.
3. **Asignación aleatoria:** Los miembros son seleccionados a través de un sistema aleatorio, proporcionando igualdad de oportunidades a todos, sin importar el momento de la solicitud o el nivel de membresía.
4. **Por cita previa:** Los servicios se asignan a los miembros que hayan programado previamente su solicitud, evitando así largas esperas y organizando un flujo más ordenado de atención.

Dependiendo de las necesidades específicas del servicio y de los requisitos organizacionales, se puede optar por uno u otro mecanismo, o incluso por una combinación de varios para optimizar la eficiencia y satisfacción de los miembros.

### Mecanismos de Servidores o de Estaciones de Servicio

los diferentes tipos de mecanismos y cómo pueden ser implementados.

{% tabs %}
{% tab title="Unico Servidor" %}
En este sistema, un único servidor gestiona todas las solicitudes de los usuarios. Este método es sumamente simple de implementar y administrar, lo que lo hace muy atractivo para proyectos pequeños o medianos debido a su bajo costo inicial y económico.&#x20;

Sin embargo, presenta ciertas limitaciones significativas si no se maneja adecuadamente el tráfico de solicitudes. A medida que el volumen de tráfico y solicitudes aumenta, el servidor puede fácilmente convertirse en un cuello de botella, afectando negativamente el rendimiento general del sistema.&#x20;

Esto se debe a que la capacidad de procesamiento de un solo servidor es finita y puede llevar a tiempos de respuesta más lentos, especialmente durante períodos de alta demanda. Además, el riesgo de tiempo de inactividad es mayor, ya que si el servidor falla, no hay copias de seguridad inmediatas que tomen su lugar. Es vital evaluar cuidadosamente estas consideraciones antes de optar por un enfoque de servidor único para aplicaciones críticas o de
{% endtab %}

{% tab title="Mecanismos de Servidores Múltiples" %}
En este sistema, un único servidor gestiona todas las solicitudes. Este método es simple de implementar y gestionar, pero puede generar cuellos de botella si el volumen de solicitudes es alto.

**Servidores Paralelos**

Varios servidores trabajan de manera simultánea para repartir la carga de trabajo. Es ideal para servicios con alta demanda, reduciendo tiempos de espera significativamente.

**Servidores en Serie**

Las solicitudes pasan de un servidor a otro en una secuencia predefinida. Este enfoque es útil para procesos que requieren múltiples etapas de atención.

#### Sistemas Distribuidos

Esta estrategia combina múltiples servidores ubicados en diferentes lugares, permitiendo gestionar solicitudes en una amplia área geográfica. Es útil para organizaciones que operan en varias ubicaciones.
{% endtab %}
{% endtabs %}

<img src="../../../.gitbook/assets/file.excalidraw.svg" alt="Sistema de colas Basico" class="gitbook-drawing">

### Distribuciones de tiempos de servicio:

* M = Distribucion exponencial

La distribución exponencial es una distribución de probabilidad continua que describe el tiempo entre eventos en un proceso de Poisson. Es una distribución clave para modelar el tiempo de servicio en sistemas de colas. Se caracteriza por su tasa de ocurrencia constante, lo que significa que no importa cuánto tiempo haya pasado desde el último evento, la probabilidad de que ocurra un nuevo evento en el siguiente instante es la misma. La función de densidad de probabilidad de una distribución exponencial se expresa como:

$$
f(x; \lambda) = \lambda e^{-\lambda x}
$$

donde ( \lambda ) es la tasa de ocurrencia y ( x ) es el tiempo. Esta propiedad de "sin memoria" hace que sea muy útil en diversos contextos, como la modelización de tiempos de espera en colas y sistemas de telecomunicaciones.

* D = distribucion degenerada

La **distribución degenerada** es una distribución de probabilidad que concentra toda su probabilidad en un solo punto. En otras palabras, es una distribución donde una variable aleatoria siempre toma el mismo valor con probabilidad 1. Si ( X ) es una variable con distribución degenerada en ( a ), se denota como $$X \sim D(a)$$ y se define por:

$$
P(X = a) = 1
$$

Esta distribución no tiene variabilidad y, por lo tanto, su varianza es cero. En contextos prácticos, se considera que no introduce incertidumbre o aleatoriedad en los escenarios de modelización.

* Distribucion de Erlang

La **distribución de Erlang** es un caso particular de la distribución gamma, utilizada frecuentemente en la teoría de colas y en modelización de tiempo entre eventos. La distribución de Erlang está definida por dos parámetros: un número entero ( k ), que indica el número de fases exponenciales idénticas, y un parámetro de tasa $$\lambda$$ , que es la tasa de cada fase exponencial. Se denota como $$X \sim \text{Erlang}(k, \lambda)$$ y su función de densidad es:

$$
f(x; k, \lambda) = \frac{\lambda^k x^{k-1} e^{-\lambda x}}{(k-1)!}, \quad x \geq 0
$$

Esta distribución se caracteriza por su capacidad de modelar procesos donde se requiere que ocurran múltiples eventos independientes previamente.

* G = Distribucion General

La **distribución general** (G) se refiere a una clase amplia de distribuciones que no se ajustan necesariamente a una forma específica, como las distribuciones normal, exponencial o Erlang. En modelado estadístico y teoría de colas, se utiliza para representar procesos que tienen características arbitrarias y no específicas. La función de densidad de probabilidad y las propiedades exactas de una distribución general pueden variar significativamente dependiendo del contexto particular en el que se aplique.

### Notacion de la teoria de colas

* estado del sistema: Numero de clientes en el sistema
* Longitud de la cola: Numero de clientes que esperan el servicio
  * estado del sistema _menos_ numero de clientes a quienes se les da el servicio.
* N(t): Número de clientes en el sistema de colas en el tiempo $$t(t \ge 0)$$
* $$P_n(t)$$: Probabilidad de que exactamente n clientes esten en el sistema en el tiempo t, dado el número en tiempo 0
* s: Número de servidores
* $$\lambda_n$$: tasa media de llegadas de nuevos clientes cuando hay n clientes en el sistema
* $$\mu_n$$ tasa media de servicio en todo el sistema cuando hay n clientes en el sistema.
* Cuando $$\lambda_n$$  es constante para toda n, esta constante se escribe como  $$\lambda$$,
*   Cuando la _tasa media de servicio_ por servidor ocupado es constante para toda n $$n \ge 1$$, esta constante se escribe como $$\mu$$

    * $$\mu_n = s\mu, cuando\ n\ge s,$$ cuando los servidores estan ocupados
    * $$\frac{1}{\lambda}$$ _tiempo esperado entre llegadas_
    * $$\frac{1}{\mu},$$ tiempo esperado de servicio
    * $$\rho = \frac{\lambda}{(s\mu)},$$ es el _factor de utilizacion_ de la instalacion de servicio, la fraccion esperada de tiempo en que los setvidores individuales están ocupados, es la fraccion de la capacidad usada del servicio por los clientes que llegan.

    Cuando el sistema esta en ejecusion al inicio de este, cuando los clientes apenas estan entrando al sistema se conoce como _estado inicial_ es un estado donde el mismo comportamiento del sistema es dificil de evidenciar ya que se esta estabilizando, una ves relaizado o pasado este fenomeno el sistema entra en lo que se conoce como _estado estable_, esta ultima es el foco de observacion de la teoria de colas.

    * $$P_n =$$ probabilidad de que haya exactamente n clientes en el sistema
    * $$L =$$ número esperado de clientes en el sistema = $$\sum_{n=0}^{\infin}nP_n$$
    * $$L_q =$$longitu esperada de la cola, este excluye a los clientes que estan en el modo _servicio_ = $$\sum_{n = s}^{\infin}(n-s)P_n$$
    * $$W =$$tiempo de espera en el sistema, incluye le tiempo de servicio para cada cliente $$W = E(W)$$
    * $$W_q=$$ tiempo de espera en el sistema, excluye el tiempo de servicio para cada cliente $$W_q = E(W_q)$$

### Papel de la Distribución Exponencial

La **distribución exponencial** es fundamental en la teoría de colas debido a su capacidad para modelar situaciones en las que los eventos ocurren de manera continua y a una tasa constante. Una de las propiedades más importantes de la distribución exponencial es su falta de memoria, lo que significa que el tiempo de espera restante para un evento es independiente del tiempo ya transcurrido. Esta propiedad simplifica en gran medida el análisis de sistemas de colas, especialmente en los modelos **M/M/1**, donde las llegadas y el servicio siguen un proceso de Poisson y tiempos de servicio exponenciales respectivamente.

#### Aplicaciones

* **Modelado de tiempos de servicio**: En sistemas donde el tiempo de servicio real varía de manera aleatoria, y la tasa promedio es constante.
* **Análisis de espera**: Determinar tiempos de espera promedio en sistemas de colas.
* **Eficiencia de la red**: En redes de comunicación para modelar la llegada de paquetes y la duración de las conexiones.

La simplicidad matemática de la distribución exponencial permite realizar cálculos y simulaciones eficientes, siendo una herramienta esencial para la optimización y diseño de sistemas de colas.

#### Proceso de Nacimiento y Muerte

En la teoría de colas, el **proceso de nacimiento y muerte** es un tipo de proceso estocástico que modela sistemas donde las llegadas y servicios pueden ser descritos por tasas constantes. Estos nombres se deben a la analogía con los procesos demográficos: "nacimiento" se refiere a la llegada de un nuevo cliente al sistema, mientras que "muerte" representa la salida de un cliente tras ser atendido.

**Descripción del Proceso**

1. **Estado del sistema**: El sistema se encuentra en un estado determinado por el número de clientes presentes.
2. **Tasa de nacimiento ((\lambda))**: La tasa a la que nuevos clientes llegan al sistema. En modelos de colas, esta suele seguir la distribución exponencial.
3. **Tasa de muerte ((\mu))**: La tasa a la que los clientes completan su servicio y dejan el sistema. También modelada a menudo por la distribución exponencial.

**Ejecución**

* **Transiciones entre estados**: Un cambio de estado ocurre cuando un cliente llega o se va.
* **Balance de tasas**: En el estado estacionario, el sistema puede lograr un equilibrio donde la tasa promedio de nacimientos iguala a la tasa promedio de muertes.

#### Aplicaciones

El proceso de nacimiento y muerte es básico en el análisis de colas **M/M/1**, ayudando a calcular métricas como el tamaño promedio de la cola y el tiempo de espera medio, cruciales para optimizar el rendimiento de sistemas de servicio.

####









