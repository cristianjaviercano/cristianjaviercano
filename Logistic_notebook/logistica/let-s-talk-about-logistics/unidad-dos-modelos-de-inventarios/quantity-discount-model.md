---
icon: sack-dollar
---

# Quantity discount Model

### Modelo de Descuento por Cantidad en EOQ

El modelo de descuento por cantidad aplicado al EOQ (Economic Order Quantity) incorpora descuentos en los precios unitarios al aumentar el volumen de pedido. Esto modifica el cálculo tradicional del EOQ, que busca minimizar los costos totales asociados al inventario, incluyendo costos de pedido y de mantenimiento.

#### Conceptos Clave

* **EOQ (Economic Order Quantity):** Es la cantidad óptima de pedido que minimiza los costos totales de inventario.
* **Descuento por Cantidad:** Reducción en el precio unitario de un producto al comprar en grandes volúmenes.
* **Costo Total:** Incluye los costos de pedido, de mantenimiento y el costo de los productos adquiridos.

#### Fórmula EOQ Ajustada con Descuentos

Para aplicar el modelo de descuento, primero se calcula el EOQ para cada nivel de precios por cantidad. Luego se evalúan los costos totales para cada escenario y se selecciona el más bajo.

```
EOQ Básico:
```

$$
EOQ = \sqrt{\frac{2DS}{H}}
$$

Donde:

* ( D ) = Demanda anual.
* ( S ) = Costo por pedido.
* ( H ) = Costo de mantener el inventario por unidad al año.
*   **Cálculo Ajustado:**

    1. Calcular el EOQ para cada posible precio de descuento.
    2. Evaluar si el EOQ calculado cae dentro del rango de cantidades que califican para el descuento.
    3. Calcular el costo total para el EOQ calculado y compararlo con los costos de los niveles siguientes con descuentos.

    #### Ejemplo

    Supongamos que se tiene la siguiente información:

    * Demanda anual (D): 1,000 unidades
    * Costo por pedido (S): $50
    * Costo de mantenimiento por unidad (H): $2
    * Precio por unidad sin descuento: $100
    *   Descuento por cantidades:

        * 100-199 unidades: $95 por unidad
        * 200+ unidades: $90 por unidad

        **Paso 1:** Calcular el EOQ sin descuentos.

$$
EOQ = \sqrt{\frac{2 \times 1000 \times 50}{2}} = 100
$$

* **Paso 2:** Evaluar cada nivel de descuento.
  * **100-199 unidades: ($95 x unidad):**
    * Verificar si el EOQ cae en este rango. Calculamos costos totales para varias cantidades e identificamos el mínimo.
  *   **200+ unidades: ($90 x unidad):**

      * Recalcular EOQ aplicable y estimar costos totales.

      Finalmente, se selecciona la cantidad de pedido que resulta en el costo total más bajo, considerando precios con descuento.
