---
description: se define la simulación y su contexto en la ingeniería industrial
---

# Capitulo uno: Introducción a la Simulación en Ingeniería Industrial

<img src="../.gitbook/assets/file.excalidraw (2).svg" alt="" class="gitbook-drawing">

### Objetivos del capitulo

{% stepper %}
{% step %}
Definir con precisión los conceptos de sistema, modelo y simulación en el contexto de la ingeniería industrial
{% endstep %}

{% step %}
Describir el proceso de modelado, explicando la importancia de la abstracción y la simplificación
{% endstep %}

{% step %}
Clasificar los modelos según diferentes criterios (físicos, matemáticos; analíticos, de simulación; estáticos/dinámicos; deterministas/estocásticos; continuos/discretos)
{% endstep %}

{% step %}
Identificar los conceptos clave de la simulación de eventos discretos: entidades, atributos, actividades, eventos, estado del sistema y reloj de simulación.
{% endstep %}

{% step %}
Argumentar sobre las ventajas y desventajas de utilizar la simulación como herramienta de análisis.
{% endstep %}

{% step %}
Enumerar y describir los pasos metodológicos involucrados en un estudio de simulación, destacando la importancia de la verificación y la validación.
{% endstep %}

{% step %}
Reconocer aplicaciones relevantes de la simulación en los campos de la ingeniería industrial, la logística y la producción.
{% endstep %}
{% endstepper %}

### ¿Qué es la simulación? Definiciones: sistema, modelo, simulación

{% hint style="warning" %}
Para comprender la simulación, es esencial primero definir los conceptos fundamentales sobre los que se construye
{% endhint %}

<img src="../.gitbook/assets/file.excalidraw (3).svg" alt="Relacion entre los elementos fundamentales de la simulacion" class="gitbook-drawing">

{% tabs %}
{% tab title="Sistema" %}
En el ámbito de la ingeniería y las ciencias, un **sistema** se define como un conjunto de elementos o componentes que interactúan entre sí para lograr un objetivo común o desempeñar una función específica.&#x20;

Estos componentes pueden ser físicos (máquinas, personas, materiales) o lógicos (información, reglas de decisión).&#x20;

Desde la perspectiva del modelado y la simulación, un sistema es cualquier porción de la realidad que se aísla para su estudio, ya sea un entorno real o uno virtual que se desea analizar.&#x20;

Ejemplos de sistemas en ingeniería industrial son vastos y variados: una línea de ensamblaje en una fábrica, un centro de distribución logístico, el flujo de pacientes en un hospital, una cadena de suministro completa, o incluso un proceso de toma de decisiones gerenciales.&#x20;

La característica distintiva es la interdependencia de sus partes y su comportamiento emergente como un todo&#x20;

{% hint style="success" %}
Hillier, F. S., & Lieberman, G. J. (2010). _Introducción a la Investigación de Operaciones_ (9th ed.). McGraw-Hill. (Capítulo 20 sobre Simulación, secciones 20.3, 20.4)
{% endhint %}
{% endtab %}

{% tab title="Modelo" %}
Dado que los sistemas reales suelen ser demasiado complejos para ser estudiados directamente en su totalidad, se recurre a la creación de **modelos**.&#x20;

_Un modelo es una representación simplificada y abstracta de un sistema, construida con un propósito específico_. **No es una réplica exacta de la realidad, sino una aproximación que captura los aspectos esenciales del sistema relevantes para el problema que se investiga**.&#x20;

Como se indica, _"el modelo es siempre menos complejo que el sistema original"_. El propósito del modelo guía las simplificaciones y abstracciones que se realizan. Por ejemplo, para estudiar el flujo de producción en una fábrica, un modelo podría representar las máquinas y los buffers, pero ignorar detalles como la temperatura ambiente o el color de las máquinas, si estos no son relevantes para el objetivo del estudio

{% hint style="success" %}
Cassandras, C. G., & Lafortune, S. (2008). Introduction to Discrete Event Systems (2nd ed.). Springer.
{% endhint %}
{% endtab %}

{% tab title="Simulacion" %}
La **simulación** es el proceso de diseñar un modelo de un sistema real y llevar a cabo experimentos con este modelo con el fin de entender el comportamiento del sistema o evaluar diversas estrategias para su operación.&#x20;

En esencia, _**la simulación imita el funcionamiento de un sistema a lo largo del tiempo**_, generando una historia artificial de su evolución. Esta historia se utiliza luego para extraer conclusiones sobre las características operativas del sistema real.&#x20;

Cuando los modelos matemáticos de un sistema son demasiado complejos para ser resueltos por métodos analíticos (es decir, mediante fórmulas exactas), la simulación, que es un experimento numérico realizado sobre el modelo, se convierte en una herramienta indispensable.&#x20;

Un modelo de simulación de eventos discretos, por ejemplo, es inherentemente estocástico (incorpora aleatoriedad) y dinámico (evoluciona con el tiempo), y su característica principal es que las variables que describen el estado del sistema cambian de valor únicamente en instantes discretos de tiempo, conocidos como "eventos"

{% hint style="success" %}
Law, A. M. (2015). Simulation Modeling and Analysis (5th ed.). McGraw-Hill Education.
{% endhint %}
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
El proceso de simulación no es simplemente "ejecutar un programa". Comienza con una comprensión profunda del sistema real y una definición clara de los objetivos del estudio.
{% endhint %}
