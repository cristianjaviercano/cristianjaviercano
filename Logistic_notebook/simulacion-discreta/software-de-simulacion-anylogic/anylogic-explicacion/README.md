# Anylogic explicacion

Aprender a utilizar AnyLogic implica comprender tanto los fundamentos teóricos de la simulación como la aplicación práctica de sus bibliotecas de modelado. AnyLogic es un software de simulación multimétodo que permite a los ingenieros e investigadores crear modelos dinámicos y complejos de una amplia variedad de sistemas. Desarrollado por The AnyLogic Company, cofundada por Andrei Borshchev, se ha establecido como una herramienta líder por su capacidad para combinar diferentes paradigmas de simulación en un solo entorno (Borshchev, 2013).

Este documento servirá como una introducción estructurada al uso de AnyLogic, comenzando con los conceptos fundamentales del modelado, describiendo los principales métodos de simulación que ofrece y concluyendo con una guía práctica para construir un primer modelo, basándose en los textos proporcionados.

#### **Paradigmas de Modelado en AnyLogic**

La principal fortaleza de AnyLogic es su capacidad para integrar tres métodos de simulación fundamentales. La elección del método depende de la naturaleza del sistema y del nivel de abstracción requerido (Borshchev, 2013, p. 1).

1. **Dinámica de Sistemas (System Dynamics - SD)**: Este método, desarrollado por Jay Forrester, opera a un alto nivel de abstracción. Se enfoca en modelar las relaciones causales y los bucles de retroalimentación (feedback loops) entre variables agregadas a lo largo del tiempo. Es ideal para análisis estratégicos de sistemas complejos como mercados, ecosistemas o dinámicas sociales (Borshchev, 2013, pp. 2-3). Matemáticamente, se basa en sistemas de ecuaciones diferenciales (Mahdavi, s.f., p. 8).
2. **Modelado de Eventos Discretos (Discrete-Event Modeling - DEM)**: También conocido como modelado centrado en procesos, este enfoque visualiza el sistema como un flujo de entidades (p. ej., clientes, productos) que atraviesan una secuencia de operaciones o procesos (p. ej., colas, servicios, retrasos). Es el método más utilizado en la industria para modelar sistemas de servicio, manufactura y logística. Los componentes clave son las **entidades**, los **recursos** que las atienden y el **diagrama de flujo** que define el proceso (Borshchev, 2013, pp. 9-10).
3. **Modelado Basado en Agentes (Agent-Based Modeling - ABM)**: Este es un enfoque de abajo hacia arriba (bottom-up) donde el comportamiento global del sistema emerge de las interacciones de un gran número de agentes autónomos e individuales. Cada agente tiene sus propias características y reglas de comportamiento. Es especialmente útil para modelar sistemas con componentes heterogéneos que interactúan en un espacio compartido, como el comportamiento de multitudes, epidemias o redes de consumidores (Mahdavi, s.f., p. 9).

***

### **Bloques de Construcción Fundamentales (PML)**

Basado en Mahdavi (s.f., pp. 138-139), los bloques esenciales son:

* **Source**: Genera entidades (agentes) y las introduce en el proceso a una tasa de llegada definida.
* **Queue**: Almacena entidades que no pueden avanzar, típicamente porque esperan por un recurso.
* **Delay**: Retrasa a una entidad por un tiempo específico, representando la duración de una operación.
* **Service**: Un bloque compuesto que encapsula la lógica de `Seize` (tomar un recurso), `Delay` (tiempo de servicio) y `Release` (liberar el recurso).
* **ResourcePool**: Define un conjunto de recursos (p. ej., personal, maquinaria) que pueden ser utilizados por las entidades.
* **Sink**: Elimina entidades del modelo una vez que han completado el proceso.

<figure><img src="../../../.gitbook/assets/flujomm1.png" alt=""><figcaption></figcaption></figure>

***

### **Construcción de un Modelo de Cola Simple**

Siguiendo la metodología presentada en Mahdavi (s.f., pp. 39-45), se puede construir un modelo básico de un sistema de colas (p. ej., una taquilla).

1. **Crear un nuevo modelo**: En AnyLogic, se inicia un nuevo proyecto, definiendo las unidades de tiempo (p. ej., segundos).
2. **Construir el diagrama de flujo**:
   * Arrastre un bloque **Source** al editor gráfico. En sus propiedades, defina la `Arrival rate` (tasa de llegadas), por ejemplo, 2 por segundo.
   * Arrastre un bloque **Queue**. AnyLogic lo conectará automáticamente al puerto de salida del bloque `Source`. Se puede dejar su capacidad como infinita (`Maximum capacity`).
   * Arrastre un bloque **Delay** después del `Queue`. En sus propiedades, defina el `Delay time`. Este puede ser un valor constante o una distribución de probabilidad, como `triangular(0.5, 1, 1.5)` segundos. La capacidad del `Delay` (por defecto 1) representa el número de servidores.
   * Finalmente, arrastre un bloque **Sink** para terminar el flujo.
3. **Configurar el experimento**:
   * En las propiedades del experimento (`Simulation`), establezca un `Stop time`, por ejemplo, 3600 segundos (1 hora).
   * Para asegurar que cada ejecución produzca resultados diferentes (debido a la aleatoriedad), configure el generador de números aleatorios a `Random seed`.
4. **Ejecutar y analizar**:
   * Al ejecutar el modelo, se puede observar el número de entidades que entran (`in`) y salen (`out`) de cada bloque.
   * El bloque `Queue` mostrará la longitud actual y la longitud promedio (`Length (av)`) de la cola, permitiendo un análisis inicial del rendimiento del sistema.

***

>
>
> #### **Referencias**
>
> * Borshchev, A. (2013). _The Big Book of Simulation Modeling: Multimethod Modeling with AnyLogic 8_. AnyLogic North America.
> * Mahdavi, A. (s.f.). _The Art of Process-Centric Modeling with AnyLogic_. Manuscrito no publicado.

***

### links de consulta:

<details>

<summary>lista de herramientas:</summary>

la lista de herramientas de anylogic esta en linea en el siguiente [link](https://anylogic.help/library-reference-guides/process-modeling-library/pml-blocks.html)

</details>

<details>

<summary>Anylogic cloud tootls bar:<br></summary>

Lista de herramientas para anylogic online ---> [Aqui](https://anylogic.help/cloud/toolbar.html)

</details>
