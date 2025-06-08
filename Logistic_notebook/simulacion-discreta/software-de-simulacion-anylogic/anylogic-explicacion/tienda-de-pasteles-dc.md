---
icon: pie
---

# Tienda de Pasteles DC

esta vez abordaremos la simulacion de eventos discretos desde la contruccion de un modelo para una pasteleria.

**Título:** Modelado y Análisis de un Sistema de Producción Discreta con Múltiples Productos y Recursos Compartidos.&#x20;

**Autor:** Ing. Cristian J. Cano, M.Sc. | Ing. Darwin Ramos, M.Sc.&#x20;

**Empresa Objeto de Estudio:** Pasteles DC

**Fecha:** Junio de 2025

**Resumen del Caso:** La empresa **Pasteles DC** se especializa en la producción de dos artículos de repostería: **Alfajores** y **Queques**. Para optimizar su eficiencia, la empresa utiliza insumos pre-procesados (galletas y masas pre-hechas). El sistema de producción se caracteriza por un flujo complejo donde ambos productos compiten por recursos compartidos, como los hornos y la estación de envasado, y siguen rutas diferenciadas en ciertas etapas del proceso. El sistema opera bajo una restricción de capacidad máxima de producción (WIP - Work In Process). El presente estudio tiene como objetivo desarrollar un modelo de simulación de eventos discretos para replicar el sistema de producción actual, identificar cuellos de botella y evaluar el impacto potencial de inversiones en capacidad.

***

**Planteamiento del Problema:**

Ustedes han sido contratados como ingenieros de procesos por **Pasteles DC**. La gerencia ha observado que la producción diaria no alcanza las metas esperadas y sospecha que existen cuellos de botella en el sistema, pero no tienen claro dónde se encuentran ni cuál sería la inversión más efectiva para resolverlos.

El reto consiste en construir un modelo de simulación de eventos discretos en **AnyLogic** que replique fielmente el sistema de producción de Pasteles DC. El objetivo final es identificar el principal cuello de botella del sistema y proponer una mejora cuantificable, evaluando su impacto en la producción total.

**Detalles del Sistema de Producción**

* **Productos y Entidades:**
  * Se debe crear un tipo de agente `Producto` con un parámetro `tipo_producto` (ej. 1 para Alfajor, 2 para Queque).
  * Los productos cambian de estado y tipo a medida que avanzan (ej. una galleta se convierte en "galleta con manjar").
* **Flujo del Proceso y Estaciones:**
  1. **Llegada de Insumos**: Al inicio de cada día (simulación inicia en t=0), llegan **150 unidades** de galletas (Mp1) y 9**0 unidades** de masa. (Mp2)
  2. **Control de Calidad**: Procesos separados para galletas y masas.
  3. **Amasado**: Exclusivo para las masas.
  4. **Moldeado**: Para dar forma final a los productos.
  5. **Horneado**: Recurso compartido por ambos productos.
  6. **Aplicación de Manjar**: Estación compartida por ambos productos.
  7. **Lógica Condicional**: Tras la aplicación de manjar, el producto vuelve a la cola del horno para un segundo horneado.
  8. **Envasado**: Estación final compartida.
* **Distribuciones de Tiempos de Proceso:**
  * **Control de Calidad**: Distribución **Triangular ()**
  * **Horneado**: Distribución **Triangular ()**
  * **Aplicación de Manjar**: Distribución **Triangular. ()**
  * **Envasado**: El tiempo de proceso sigue una distribución **Exponencial** con una media de 5 minutos por producto.
* **Restricciones del Sistema:**
  * El sistema completo tiene una **capacidad máxima de 100 productos** (WIP). Las nuevas materias primas deben esperar en una cola de suministro si el sistema está lleno. Se debe modelar utilizando los bloques `RestrictedAreaStart` y `RestrictedAreaEnd`.
  * La simulación debe correr por un total de **7200 minutos** (equivalente a 5 días de producción).

***

**Fases para la Resolución del Reto**

1. **fase CERO**: Visualizacion del proceso
   * &#x20;Construya el modelo teorico del proceso, usando diagramas de flujo o cualquiuer herramienta grafica que le permita visualizar el proceso.
2. **Fase 1: Construcción del Modelo Base**
   * Cree el agente `Producto` con sus respectivos parámetros.
   * Modele el flujo del proceso utilizando los bloques de la librería PML: `Source`, `Queue`, `Service`, `SelectOutput` para las decisiones lógicas, y `RestrictedAreaStart/End` para la restricción de WIP.
   * Configure cada bloque de servicio (`Service`) con los recursos y las distribuciones de tiempo especificadas.
3. **Fase 2: Verificación y Validación**
   * Ejecute el modelo y verifique que el flujo de entidades es correcto (los queques pasan por amasado, los alfajores no, etc.).
   * Asegúrese de que la restricción de 100 unidades en el sistema funciona correctamente.
   * Valide que el número total de productos de salida más los que quedaron en proceso sea igual al número de insumos que ingresaron.
4. **Fase 3: Análisis e Identificación de Cuellos de Botella**
   * Ejecute la simulación por los 7200 minutos.
   * Analice los resultados: identifique la estación de trabajo que presenta la **cola más larga** y el **mayor tiempo de espera promedio**.
   * Revise la **utilización** de todos los recursos (amasadora, horno, estación de manjar, envasadora). El recurso con la utilización más cercana al 100% es probablemente el cuello de botella.
5. **Fase 4: Propuesta y Evaluación de Mejoras**
   * Con base en su análisis, formule una hipótesis. Por ejemplo: "El horno es el principal cuello de botella del sistema".
   * **Propuesta de Mejora**: La gerencia evalúa comprar un segundo horno. Modifique su modelo para reflejar esta mejora, aumentando la capacidad del `ResourcePool` del horno a **2**.
   * Ejecute el nuevo escenario y compare los resultados con el modelo base.
6. **Fase 5: Presentación de Resultados (Informe Técnico)**
   * Prepare un informe de no más de 2 páginas que contenga:
     * Una breve descripción del modelo construido.
     * La identificación clara del cuello de botella, justificada con datos (longitud de cola, utilización).
     * Una tabla comparativa de KPIs (Producción Total de Alfajores y Queques, Tiempo de Ciclo Promedio) entre el **escenario base** y el **escenario con la mejora**.
     * Una recomendación final para la gerencia de **Pasteles CRC**, indicando si la inversión en un segundo horno es justificable o no según los resultados de la simulación.
