---
hidden: true
icon: rectangles-mixed
---

# Bloque de ejercicios Capitulo Uno

### 1. Identificación de Sistemas.

Seleccione tres sistemas de su entorno cotidiano (ej. una cafetería universitaria, el proceso de inscripción a cursos, el sistema de transporte público de su ciudad). Para cada uno:

1. Describa sus componentes principales.
2. Identifique las entradas y salidas clave.
3. Proponga dos objetivos diferentes que podrían justificar un estudio de simulación para ese sistema.

### 2. Abstracción y Simplificación:&#x20;

Considere un sistema de producción de pizzas en un restaurante concurrido. Describa cómo modelaría este sistema con dos niveles de abstracción diferentes:

1. Nivel 1 (Alto): Enfocado en la capacidad diaria y el flujo general de pedidos.
2. Nivel 2 (Detallado): Enfocado en el movimiento de cada pizza, el uso de hornos y la asignación de personal.
3. Justifique las simplificaciones realizadas en cada nivel.
4. Diagrame los resultados de forma logica en Anylogic/flexym

### 3. Clasificación de Modelos

Para los siguientes escenarios de ingeniería ind, clasifique el tipo de modelo más apropiado (estático/dinámico, determinista/estocástico, continuo/discreto) y justifique su respuesta:

1. Determinar el número óptimo de unidades de un producto a pedir para un único período de venta, con demanda incierta.
2. Analizar el flujo de calor a través de la pared de un horno industrial a lo largo del tiempo.
3. Programar la secuencia de trabajos en una máquina para minimizar el tiempo total de finalización, asumiendo tiempos de proceso fijos.
4. Evaluar el rendimiento de un centro de llamadas donde las llegadas de llamadas y los tiempos de atención son variables.

### 4. Componentes SED

1. Posibles entidades.
2. Atributos relevantes para una entidad "automóvil".
3. Actividades principales.
4. Eventos clave que ocurren en el sistema.
5. Variables que definirían el estado del sistema

***

## Preguntas para Discusión

1. ¿En qué situaciones considera que un modelo analítico (matemático exacto) sería preferible a un modelo de simulación, y viceversa? Proporcione ejemplos.
2. Discuta los peligros potenciales de tomar decisiones basadas en un modelo de simulación que no ha sido adecuadamente validado. ¿Cuáles podrían ser las consecuencias en un entorno de producción?
3. ¿Cómo se relaciona el proceso de verificación de un modelo de simulación con los principios de calidad del software y buenas prácticas de programación?
4. Si un modelo de simulación es una simplificación de la realidad, ¿cómo podemos confiar en sus resultados para tomar decisiones sobre el sistema real?

***

### [Evaluacion de Contenidos del Capitulo Uno](https://forms.office.com/r/TgMZHF6w0C)

***

### Ejercicio de Teoría de Colas

#### **Problema 1:**

Una cafetería cuenta con un único servidor que atiende a los clientes. El tiempo entre la llegada de los clientes sigue una distribución exponencial con una tasa media de 10 clientes por hora, y el tiempo de servicio de cada cliente también sigue una distribución exponencial con una tasa de 12 clientes por hora. Con base en esta información:

**Diagrama del Sistema de Colas:**

* Utilice un diagrama para representar el sistema de colas, identificando el servidor, la llegada y el servicio de los clientes.

Utilice las fórmulas del modelo (M/M/1) para resolver estas métricas.

#### **Problema 2:**

En otra sección de la cafetería, se ha implementado un sistema de colas distinto al anterior. Este nuevo sistema tiene dos servidores que atienden a los clientes. El tiempo entre la llegada de los clientes sigue una distribución exponencial con una tasa media de 8 clientes por hora, mientras que cada servidor tiene una tasa de servicio de 10 clientes por hora. Con base en esta información:

**Diagrama del Sistema de Colas:**

* Use un diagrama para representar este nuevo sistema de colas, destacando los dos servidores, la llegada de los clientes y el proceso de servicio.

Utilice las fórmulas del modelo (M/M/2) para calcular las métricas del sistema, tales como la probabilidad de que un cliente tenga que esperar y el tiempo promedio en el sistema.

#### **Problema 3:**

Se ha diseñado un sistema de inventario en el que los pedidos llegan de manera continua y son atendidos bajo una política de revisión periódica. La tasa de llegada de pedidos sigue una distribución de Poisson con una media de 5 pedidos por día. El tiempo de entrega para reponer el inventario tiene una media de 2 días y sigue una distribución exponencial. Con base en esta información:

**Diagrama del Sistema de Inventario:**

* Dibuje un diagrama que represente el flujo de pedidos y el proceso de reabastecimiento.

Utilice las fórmulas pertinentes para calcular las métricas del sistema, como el nivel de inventario esperado y la probabilidad de ruptura de stock.

#### Problema 4:

Juan y pedro son dos peluqueros que opetran de manera independiente, Tienen dos sillas para clientes que esperan su corte, por que el número de clientes en el sistema varia en 0 y 4, para n = 1, 2, 3, 4, la probabilidad de. $$P_n$$ de que halla exactamente n cllientes en el sistema es:

$$
f(x) = x * e^{2 pi i \xi x}
$$

