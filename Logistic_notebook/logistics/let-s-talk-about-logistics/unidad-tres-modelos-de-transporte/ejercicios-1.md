# Ejercicios 1

### Contexto

La empresa Cano se dedica a la distribución de productos alimenticios en una región específica. Tiene 5 proveedores y 9 clientes que deben ser atendidos con ciertas demandas y limitaciones de oferta. El objetivo es encontrar la mejor manera de distribuir estos productos para minimizar los costos de transporte.

### Diagrama Lógico del Problema

1. Proveedores: P1, P2, P3, P4, P5
2. Clientes: C1, C2, C3, C4, C5, C6, C7, C8, C9
3. Variables:
   * Oferta de cada proveedor
   * Demanda de cada cliente
4. Costos de transporte entre cada proveedor y cliente
5. Objetivo: Minimizar el costo total de transporte

### Pregunta a Solucionar

¿Cómo puede la empresa Cano minimizar el costo total de transporte al distribuir sus productos desde los proveedores hacia los clientes mientras satisface las demandas de los clientes y respeta las capacidades de los proveedores?

### Datos Adicionales

| Proveedor | Oferta (unidades) |
| --------- | ----------------- |
| P1        | 100               |
| P2        | 200               |
| P3        | 150               |
| P4        | 180               |
| P5        | 170               |

| Cliente | Demanda (unidades) |
| ------- | ------------------ |
| C1      | 60                 |
| C2      | 80                 |
| C3      | 90                 |
| C4      | 70                 |
| C5      | 110                |
| C6      | 100                |
| C7      | 50                 |
| C8      | 75                 |
| C9      | 55                 |

| Proveedor/Cliente | C1 | C2 | C3 | C4 | C5 | C6 | C7 | C8 | C9 |
| ----------------- | -- | -- | -- | -- | -- | -- | -- | -- | -- |
| P1                | 4  | 6  | 8  | 5  | 9  | 7  | 3  | 5  | 6  |
| P2                | 5  | 3  | 6  | 4  | 2  | 3  | 5  | 9  | 7  |
| P3                | 8  | 7  | 4  | 3  | 6  | 5  | 2  | 6  | 4  |
| P4                | 7  | 4  | 5  | 6  | 3  | 7  | 4  | 2  | 8  |
| P5                | 6  | 5  | 7  | 9  | 8  | 6  | 3  | 4  | 5  |

{% hint style="info" %}
### Invitación: Invitamos a los estudiantes a diseñar una solución para este problema usando Python, empleando la librería PuLP para modelar y resolver el problema de transporte.
{% endhint %}

### Ejercicio Numero 2.&#x20;

### Diseño de un ejercicio: Problema de Ruteo de Vehículos Capacitado (VRPC)

### Ejercicio de Problema de Ruteo de Vehículos Capacitado (VRPC)

#### Contexto del Problema

Una empresa de logística cuenta con una flota de camiones para la distribución de productos a sus clientes. Cada camión tiene una capacidad máxima de carga y debe visitar múltiples clientes para entregar los productos demandados. La empresa desea minimizar el costo total de transporte cumpliendo con las restricciones de capacidad de los camiones y las demandas de los clientes.

#### Datos del Problema

*   **Clientes**:

    | Cliente | Demanda (unidades) |
    | ------- | ------------------ |
    | C1      | 10                 |
    | C2      | 15                 |
    | C3      | 20                 |
    | C4      | 10                 |
    | C5      | 25                 |
* **Camiones**:
  * Camión 1: Capacidad 30 unidades
  * Camión 2: Capacidad 40 unidades
*   **Costos de Transporte**:\
    La matriz de costos indica el costo de transportar unidades entre el almacén y los clientes, y entre los propios clientes.

    | Origen/Destino | Almacén | C1 | C2 | C3 | C4 | C5 |
    | -------------- | ------- | -- | -- | -- | -- | -- |
    | Almacén        | 0       | 4  | 6  | 8  | 5  | 7  |
    | C1             | 4       | 0  | 2  | 4  | 3  | 6  |
    | C2             | 6       | 2  | 0  | 2  | 5  | 3  |
    | C3             | 8       | 4  | 2  | 0  | 3  | 4  |
    | C4             | 5       | 3  | 5  | 3  | 0  | 7  |
    | C5             | 7       | 6  | 3  | 4  | 7  | 0  |

#### Desafío

Modela y resuelve este problema de ruteo utilizando la librería PuLP en Python. El objetivo es encontrar la ruta óptima para cada camión minimizando el costo total de transporte, respetando las restricciones de capacidad de los camiones y satisfaciendo las demandas de todos los clientes.
