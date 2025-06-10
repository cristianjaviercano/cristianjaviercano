# Capitulo cero: introduccion a los conceptos de simulacion

<img src="../../.gitbook/assets/file.excalidraw (1) (1) (1).svg" alt="Unrapido vistazo al mundo e la simulacion" class="gitbook-drawing">

Bienvenido al fascinante mundo de la simulación de eventos discretos, una disciplina que se ha convertido en una herramienta indispensable en el arsenal del ingeniero industrial moderno. En una era caracterizada por la creciente complejidad de los sistemas productivos, logísticos y de servicios, la capacidad de modelar, analizar y optimizar estos sistemas es más crucial que nunca. La investigación de operaciones (IO), en general, ha demostrado ser un motor tecnológico fundamental para el éxito de innumerables organizaciones a nivel mundial , y dentro de este campo, la simulación emerge como una de sus técnicas más versátiles y poderosas. Empresas líderes, como Federal Express, han integrado la IO en el núcleo de sus procesos de toma de decisiones estratégicas, logrando optimizar desde la inversión en equipos hasta la estructura de sus complejas rutas logísticas.

La simulación de eventos discretos es una actividad inherentemente multidisciplinaria, con profundas raíces en la ingeniería industrial, la investigación de operaciones, la informática y la estadística. A lo largo de estas páginas, se explorará cómo la simulación permite trascender las limitaciones de los métodos puramente analíticos, ofreciendo un laboratorio virtual donde es posible experimentar con ideas innovadoras, evaluar el impacto de cambios y tomar decisiones informadas sin incurrir en los costos o riesgos asociados a la experimentación en el mundo real.

> La simulacion es una representacion de la realidad misma, donde las varables y los parametros son los protagonistas del sistema, a medida que se agreguen mas variables y parametros estos sistemas se vuelven mas complejos - crc

### Objetivos del curso:

1. **Comprender los principios fundamentales de la simulación:** Se sentarán las bases conceptuales que sustentan la disciplina.
2. **Aprender a modelar sistemas:** Se desarrollará la capacidad de abstraer la realidad en modelos manejables que capturen la esencia de los sistemas bajo estudio.
3. **Dominar técnicas de simulación de Montecarlo utilizando Excel:** Se explorará cómo una herramienta tan accesible como Excel puede ser utilizada para análisis de riesgo y escenarios
4. **Desarrollar modelos de simulación de eventos discretos utilizando SimPy (Python):** Se introducirá la programación de simulaciones, ofreciendo flexibilidad y potencia para modelos personalizados.
5. **Adquirir habilidades en el uso de software especializado como AnyLogic:** Se explorarán las capacidades de una herramienta de simulación de vanguardia para el modelado de sistemas complejos en producción y logística.
6. **Analizar e interpretar resultados de simulación para la toma de decisiones informadas:** Se enfatizará que la simulación no termina con la ejecución del modelo, sino con la extracción de conocimiento útil.

La metodología de aprendizaje propuesta combina la exposición teórica rigurosa con una fuerte orientación práctica. Cada capítulo incluirá definiciones claras, ejemplos resueltos paso a paso, ejercicios diseñados para reforzar los conceptos y, fundamentalmente, aplicaciones directas a problemas típicos de la ingeniería industrial, especialmente en las áreas de logística y producción. Se espera que el lector no solo aprenda "sobre" simulación, sino que aprenda "a hacer" simulación.

> los sistemas industriales y logísticos modernos son intrínsecamente complejos, dinámicos y estocásticos.

{% hint style="success" %}
la simulación no es simplemente una técnica más; es una forma de pensar, una metodología para la experimentación virtual y un pilar para la mejora continua en la ingeniería industrial
{% endhint %}

***

### Cuando la simulacion es una herramienta util?

**Cuándo NO usar la Simulación de Software Especializado**

El uso de software especializado para simular la realidad tiene tanto ventajas como desventajas. Aunque estas herramientas son reconocidas y aceptadas dentro de la industria por autores como Naylor et al. (1996) y Shannon (1998), no siempre representan la mejor solución. A continuación, exploraremos situaciones en las que no es recomendable utilizar simulaciones:

1. **Complejidad y Tiempo**: Algunos aspectos de la simulación pueden ser excesivamente complicados y consumir mucho tiempo, dificultando su implementación.
2. **Coste**: La inversión en software especializado puede ser elevada, lo que no siempre justifica su uso frente a soluciones más simples y económicas.
3. **Relevancia y Necesidad**: En ocasiones, la complejidad de los problemas no justifica el uso de simulación si existen métodos más directos para resolverlos.
4. **Precisión de Datos**: Si los datos disponibles no son fiables o precisos, la eficacia de la simulación se ve comprometida.

Evaluar cuidadosamente estas condiciones puede ayudar a determinar cuándo es mejor evitar el uso de simulaciones y optar por enfoques alternativos.

{% hint style="info" %}
La Simulacion NO de be ser usada, si el PROBLEMA SE SOLUCIONA CON SENTIDO COMÚN"
{% endhint %}

para todos los demas contextos la sumulacion de eventos discretos en este caso es bienvenida.

> Banks and Gibsoon (1997)

***

### Caracterizacion de un modelo de simulacion

<img src="../../.gitbook/assets/file.excalidraw (6).svg" alt="" class="gitbook-drawing">

