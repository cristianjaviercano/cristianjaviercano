---
icon: boot-heeled
---

# Manufactura de Calzado DC

**1. Objetivos**

* [ ] Modelar un proceso de producción de dos etapas con llegadas y tiempos de servicio estocásticos.
* [ ] Implementar la lógica de enrutamiento probabilístico para diferentes tipos de productos.
* [ ] Configurar y ejecutar un experimento de simulación para un número finito de productos.
* [ ] Medir y analizar los indicadores de rendimiento clave: tiempo promedio en el sistema y tiempo promedio de espera.

**2. Análisis del Sistema**

Antes de modelar, es crucial definir los componentes del sistema basado en la descripción del caso de la "Fábrica de calzado".

* **Entidades**: Pares de zapatos.
* **Proceso**: Un flujo de dos etapas: Corte (Estación 1) y Ensamble (Estación 2).
* **Llegadas**: Los pares de zapatos llegan a la Estación 1 con un tiempo entre llegadas que sigue una distribución **Normal** con una media de 1.5 minutos (90 segundos) y una desviación estándar de 20 segundos.
* **Recursos**:
  * Máquina de Corte (Estación 1): 1 unidad.
  * Máquina de Ensamble (Estación 2): 1 unidad.
* **Lógica de Flujo**:
  * En la Estación 1 (Corte), hay 3 tipos de corte con diferentes probabilidades y tiempos de operación.
  * **50%** son de **Tipo 1** (tiempo fijo).
  * **30%** son de **Tipo 2** (tiempo uniforme).
  * **20%** son de **Tipo 3** (tiempo normal).
* **Fin de la Simulación**:&#x20;

El modelo debe detenerse después de procesar **100 pares de zapatos**. o una unidad e tiempo responsable.
