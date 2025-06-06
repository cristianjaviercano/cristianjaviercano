---
hidden: true
---

# Bloque de Ejercicios Capitulo 2.1

En esta sección, profundizaremos en los problemas planteados en el capítulo dos del contenido. Analizaremos los conceptos clave, brindando una comprensión detallada y abordando posibles soluciones y enfoques críticos para resolver los desafíos presentados.

***

### Ejercicios 2.1. probabilidad

Para cada uno de los siguientes problemas, el estudiante deberá:

1. **Identificar y describir el Espacio Muestral (S)** en forma de conjunto.
2. **Construir un Diagrama de Árbol** que represente el experimento y sus posibles resultados finales.
3. **Generar una Muestra Aleatoria** de 1000 observaciones de este experimento utilizando **Python** o **Excel**. Si se utiliza Python, se espera un script sencillo que simule el experimento y almacene los resultados. Si se utiliza Excel, se deben describir las funciones y la metodología empleada.

<details>

<summary>Ejercicio 2.1.1</summary>

Se lanza una moneda justa **tres veces consecutivas**. Se registra la secuencia de caras (C) y sellos (S).

</details>

<details>

<summary>Ejercicio 2.1.2</summary>

Un inspector de calidad selecciona **dos artículos al azar** de una línea de producción. Cada artículo puede ser categorizado como **Aceptable (A)**, **Defectuoso (D)**, **Requiere Ajuste (R)** o **Descontinuado (X)**. Se registra el estado de cada

</details>

<details>

<summary>Ejercicio 2.1.3</summary>

Una empresa de ingeniería está evaluando el éxito de sus proyectos de Investigación y Desarrollo (I+D). Un proyecto puede tener **Éxito Técnico (ET)** o **Fallo Técnico (FT)**. Adicionalmente, puede resultar en un **Beneficio Económico (BE)** o una **Pérdida Económica (PE)**. Se considera un proyecto de I+D y se registran ambos resultados.

</details>

<details>

<summary>Ejercicio 2.1.4</summary>

En un almacén, se monitorea el nivel de inventario de un producto (alto (H), medio (M), bajo (B)) y la demanda diaria de ese producto (alta (D\_A), baja (D\_B)). Se observa el estado del inventario y la demanda un día particular.

</details>

<details>

<summary>Ejercicio 2.1.5</summary>

Un equipo de proyecto debe formarse con dos miembros seleccionados de un grupo de candidatos que consta de **un ingeniero (I)**, **un economista (E)** y **un diseñador (D)**. Los dos miembros se seleccionan aleatoriamente, **sin reemplazo**, y el orden de selección importa.

</details>

<details>

<summary>Ejercicio 2.1.6</summary>

Consideremos los resultados de la primera inspección como categorías iniciales: **D** (defectuoso), **M** (con defectos menores), y **A** (aceptable). Si es 'M', una segunda inspección clasifica como **A'** (aceptable después de ajuste) o **D'** (definitivamente defectuoso).

</details>

<details>

<summary>Ejercicio 2.1.7</summary>

Una prueba de software arroja dos posibles resultados: **Pasa (P)** o **Falla (F)**. Si falla, el fallo puede ser clasificado como **Crítico (C)** o **No Crítico (NC)**. Se realiza una prueba a una nueva versión del software y se registra su resultado.

</details>

<details>

<summary>Ejercicio 2.1.8</summary>

Un inversor considera una inversión en una _startup_. La primera decisión es si **Invertir (I)** o **No Invertir (NI)**. Si decide invertir, la _startup_ puede tener **Éxito (E)** o **Fallo (F)** en el mercado. Si tiene éxito, el inversor obtiene una **Gran Ganancia (GG)** o una **Pequeña Ganancia (PG)**. Si falla, solo puede haber una **Pérdida (P)**. Si decide no invertir, su resultado es **Sin Ganancia ni Pérdida (SGNP)**

</details>

<details>

<summary>Ejercicio 2.1.9</summary>

Un estudiante solicita admisión a una universidad. La primera etapa es la **Revisión de Documentos (RD)**, cuyo resultado puede ser **Aprobado (A\_RD)** o **Rechazado (R\_RD)**. Si es aprobado, pasa a la **Entrevista Personal (EP)**, donde puede ser **Aceptado (A\_EP)** o **Rechazado (R\_EP)**.

</details>

<details>

<summary>Ejercicio 2.1.10</summary>

Se monitorea el rendimiento de una máquina en una línea de producción. La máquina puede estar **Operativa (O)** o **Inoperativa (I)**. Si está Operativa, puede producir con **Alta Eficiencia (AE)** o **Baja Eficiencia (BE)**. Si está Inoperativa, se clasifica si la falla es **Menor (FM)** o **Mayor (FMy)**.

</details>

***

### Bloque de ejercicios 2.2

<details>

<summary><strong>Problema 1: Monitoreo de Parámetros de Proceso</strong></summary>

En un proceso industrial, se monitorean dos parámetros críticos para asegurar la calidad de un producto: la **temperatura (T)** y la **presión (P)**. Se considera que el proceso está **bajo control (C)** si la temperatura está dentro del rango óptimo y la presión está dentro del rango óptimo. Si cualquiera de los parámetros está fuera de rango, se considera **fuera de control (FC)**.

Se selecciona un producto al azar y se registra el estado de sus parámetros.

1. **Espacio Muestral (S):** Defina el espacio muestral que represente las combinaciones posibles de los estados de temperatura y presión (e.g., (T\_opt, P\_opt)).
2. **Eventos:**
   * **Evento A**: La temperatura está dentro del rango óptimo.
   * **Evento B**: La presión está dentro del rango óptimo.
3. **Intersección:**
   * Describa el **evento A∩B** (la intersección de A y B) en palabras.
   * Enumere los elementos de **A∩B** como un subconjunto de S.
   * ¿Qué significa este evento en el contexto del problema?

</details>

<details>

<summary><strong>Problema 2: Lanzamiento de Dos Dados</strong></summary>

Se lanzan simultáneamente **dos dados justos de seis caras** (uno rojo y uno azul) y se registra el resultado de la cara superior de cada dado.

1. **Espacio Muestral (S):** Defina el espacio muestral de este experimento como el conjunto de pares ordenados (resultado dado rojo, resultado dado azul). No es necesario listar todos los 36 elementos, pero sí cómo se conformaría el conjunto.
2. **Eventos:**
   * **Evento X**: La suma de los números de los dos dados es 7.
   * **Evento Y**: El número del dado rojo es mayor que 4.
3. **Intersección:**
   * Describa el **evento X∩Y** en palabras.
   * Enumere los elementos de **X∩Y** como un subconjunto de S.

</details>

<details>

<summary><strong>Problema 3: Encuesta de Preferencias de Software</strong></summary>

Una empresa de ingeniería realiza una encuesta a sus empleados sobre su preferencia de software para análisis de datos. Los empleados pueden preferir **Python (P)**, **R (R)**, **ambos**, o **ninguno**. Se selecciona a un empleado al azar.

1. **Espacio Muestral (S):** Defina el espacio muestral que representa las posibles preferencias del empleado.
2. **Eventos:**
   * **Evento M**: El empleado prefiere Python.
   * **Evento N**: El empleado prefiere R.
3. **Intersección:**
   * Describa el **evento M∩N** en palabras.
   * Enumere los elementos de **M∩N** como un subconjunto de S.
   * ¿Qué implicación tiene este evento para el uso de software en la empresa?

</details>

<details>

<summary><strong>Problema 4: Resultados de una Auditoría de Seguridad</strong></summary>

En una auditoría de seguridad informática, se clasifica un sistema en función de dos criterios: si presenta **vulnerabilidades críticas (VC)** y si ha sufrido **brechas de seguridad (BS)** en el último año. Un sistema puede tener vulnerabilidades críticas o no (VCc), y puede haber sufrido brechas o no (BSc).

Se selecciona un sistema al azar para la auditoría.

1. **Espacio Muestral (S):** Defina el espacio muestral de las posibles combinaciones de resultados de la auditoría (e.g., (VC, BS)).
2. **Eventos:**
   * **Evento G**: El sistema no presenta vulnerabilidades críticas.
   * **Evento H**: El sistema ha sufrido brechas de seguridad.
3. **Disjunción:**
   * Determine si los **eventos G y H son disjuntos**. Justifique su respuesta basándose en su definición de conjuntos.
   * Describa **G∩H**.

</details>

<details>

<summary><strong>Problema 6: Clasificación de Defectos en un Producto</strong></summary>

En la inspección final de un producto, se registran los tipos de defectos encontrados. Los posibles defectos son: **rayones (R)**, **abolladuras (A)**, y **fallas electrónicas (FE)**. Un producto puede tener uno o más de estos defectos, o ninguno.

Se selecciona un producto al azar de la línea de producción.

1. **Espacio Muestral (S):** Enumere un espacio muestral que represente si un producto tiene o no cada uno de los tipos de defectos (e.g., (No R, No A, No FE), (R, No A, No FE), etc.). Considere que el producto puede no tener ningún defecto.
2. **Eventos:**
   * **Evento J**: El producto tiene al menos un rayón.
   * **Evento K**: El producto tiene solo abolladuras (y ningún otro defecto).
   * **Evento L**: El producto no tiene ningún defecto.
3. **Disjunción:**
   * ¿Son los **eventos K y L disjuntos**? Justifique su respuesta y describa su intersección.
   * ¿Son los **eventos J y L disjuntos**? Justifique su respuesta y describa su intersección.

</details>

<details>

<summary>Problema 7: Gestión de Proyectos Múltiples</summary>

Una empresa de ingeniería gestiona simultáneamente **tres proyectos distintos**: el Proyecto Alfa (α), el Proyecto Beta (β) y el Proyecto Gamma (γ). Al final de cada trimestre, cada proyecto es evaluado y clasificado en una de dos categorías mutuamente excluyentes: **Éxito (E)** o **Fallo (F)**.

Un gerente de proyectos está interesado en analizar los resultados trimestrales de estos tres proyectos. Se registra el resultado de cada proyecto.

#### Requerimientos:

1. **Espacio Muestral (S):**
   * Defina el espacio muestral (S) que represente todos los posibles resultados combinados de los tres proyectos al final del trimestre. Los elementos de S deben ser tuplas ordenadas (resultado α, resultado β, resultado γ).
   * Describa S en forma de conjunto.
2. **Definición de Eventos en Forma de Conjunto:** Describa los siguientes eventos como subconjuntos de S:
   * **Evento A**: Al menos dos de los proyectos resultan en Éxito.
   * **Evento B**: El Proyecto Alfa resulta en Éxito y el Proyecto Beta resulta en Fallo.
   * **Evento C**: Todos los proyectos tienen el mismo resultado (todos Éxito o todos Fallo).
   * **Evento D**: Solo uno de los proyectos resulta en Éxito.
3.  **Análisis de Intersecciones:** Para los siguientes pares de eventos, realice lo siguiente:

    * Describa la **intersección** en palabras.
    * Liste los elementos de la intersección como un subconjunto de S.
    * Determine si los eventos son **mutuamente excluyentes (disjuntos)**. Justifique su respuesta.

    a) **A∩B** b) **B∩C** c) **C∩D**

</details>

***

### Bloque de ejercicios 2.3

Para cada uno de los siguientes problemas, el estudiante deberá:

1. **Identificar y describir el Espacio Muestral (S)** en forma de conjunto.
2. **Definir los Eventos** dados como subconjuntos de S.
3. **Describir en palabras** las operaciones de conjuntos solicitadas.
4. **Enumerar los elementos** resultantes de cada operación de conjuntos solicitada.
5. **Construir un Diagrama de Venn** que ilustre los conjuntos involucrados y la región que representa la operación solicitada.
6. **Graficar el Diagrama de Venn en Python** utilizando una librería adecuada (como `matplotlib_venn` o `matplotlib` para una representación simple si la primera no está disponible).

<details>

<summary>2.3.1 Preferencias de Clientes en un Servicio de Streaming</summary>

Una compañía de streaming de video clasifica a sus clientes según su preferencia por tres géneros de contenido: **Películas (P)**, **Series de TV (S)** y **Documentales (D)**. Un cliente puede preferir uno, dos, los tres o ninguno de estos géneros. Se selecciona un cliente al azar y se registran sus preferencias.

* **Espacio Muestral (S):** Defina el espacio muestral que represente todas las posibles combinaciones de preferencias. Por ejemplo, un cliente que prefiere solo películas podría ser (P,Sc,Dc), donde Sc y Dc significan "no series" y "no documentales", respectivamente. Se pueden usar 0s y 1s para representar "no prefiere" y "prefiere" (ej. (1,0,0) para solo Películas).
* **Eventos:**
  * **Evento A**: El cliente prefiere Películas.
  * **Evento B**: El cliente prefiere Series de TV.
  * **Evento C**: El cliente prefiere Documentales.
* **Operaciones con Conjuntos:** a) **A∩B∩C**: Describa en palabras, enumere los elementos y grafique el Diagrama de Venn. b) **(A∪B)∩C**: Describa en palabras, enumere los elementos y grafique el Diagrama de Venn. c) **Ac∩Bc∩Cc**: Describa en palabras, enumere los elementos y grafique el Diagrama de Venn.

</details>

<details>

<summary>2.3.2 Evaluación de Desempeño de Equipos de Trabajo</summary>

En una empresa de consultoría, un equipo de trabajo es evaluado en tres criterios de desempeño: **Productividad (P)**, **Calidad del Trabajo (C)** y **Cumplimiento de Plazos (T)**. Para cada criterio, el equipo puede ser calificado como "Satisfactorio" (indicado por el criterio) o "No Satisfactorio" (indicado por el complemento del criterio, e.g., Pc). Se evalúa un equipo al azar.

* **Espacio Muestral (S):** Defina el espacio muestral. Utilice una notación similar al problema 1 (ej. (P, C, T) para Satisfactorio en los tres).
* **Eventos:**
  * **Evento X**: El equipo tiene desempeño Satisfactorio en Productividad.
  * **Evento Y**: El equipo tiene desempeño Satisfactorio en Calidad del Trabajo.
  * **Evento Z**: El equipo tiene desempeño Satisfactorio en Cumplimiento de Plazos.
* **Operaciones con Conjuntos:** a) **X∪Y∪Z**: Describa en palabras, enumere los elementos y grafique el Diagrama de Venn. b) **(X∩Y)∪Zc**: Describa en palabras, enumere los elementos y grafique el Diagrama de Venn. c) **(XΔY)∩Z**: (Diferencia simétrica de X e Y, interceptado con Z) Describa en palabras, enumere los elementos y grafique el Diagrama de Venn.

</details>

<details>

<summary>2.3.3: Detección de Fallas en un Sistema Complejo</summary>

Un sistema electrónico complejo consta de tres subsistemas independientes: Subsistema 1 (S1), Subsistema 2 (S2) y Subsistema 3 (S3). Se registra si cada subsistema tiene una **falla (F)** o está **operativo (O)**. Se observa el estado de los tres subsistemas.

* **Espacio Muestral (S):** Defina el espacio muestral. Utilice una notación como (F, O, F) para indicar Falla en S1, Operativo en S2, Falla en S3.
* **Eventos:**
  * **Evento E1​**: El Subsistema 1 tiene una falla.
  * **Evento E2​**: El Subsistema 2 tiene una falla.
  * **Evento E3​**: El Subsistema 3 tiene una falla.
* **Operaciones con Conjuntos:** a) **(E1​∪E2​)∪E3​**: Describa en palabras, enumere los elementos y grafique el Diagrama de Venn. b) **E1​∩(E2c​∪E3​)**: Describa en palabras, enumere los elementos y grafique el Diagrama de Venn. c) **(E1​∩E2c​)∩E3c​**: Describa en palabras, enumere los elementos y grafique el Diagrama de Venn.

</details>

#### Diagrama de VENN en python

```python
from matplotlib_venn import venn3, venn3_circles
import matplotlib.pyplot as plt

plt.figure(figsize=(8, 8))
venn = venn3(subsets=(1, 1, 1, 1, 1, 1, 1), set_labels=('Películas (A)', 'Series (B)', 'Documentales (C)')) # Estos son valores arbitrarios para la visualización
# Para sombrear la intersección A ∩ B ∩ C, se usa el índice '111'
venn.get_patch_by_id('111').set_color('blue') # Colorea la intersección
venn.get_patch_by_id('111').set_alpha(0.4) # Ajusta la transparencia

plt.title("Diagrama de Venn: Intersección A $\\cap$ B $\\cap$ C")
plt.show()

# Para otras operaciones, se ajustarían los parámetros subsets y los IDs de los parches a colorear.
# Los IDs de los parches en venn3 son:
# '100': solo A
# '010': solo B
# '001': solo C
# '110': A ∩ B (sin C)
# '101': A ∩ C (sin B)
# '011': B ∩ C (sin A)
# '111': A ∩ B ∩ C
# '000': Complemento de la unión (fuera de todos los círculos)
```

***

{% hint style="info" %}
para mas ejercicios busca la pagina 42 a la 44 del. libro estadistica y probalblidad para ingenieros.
{% endhint %}

***

<details>

<summary>Ejercicio 2.4.1 Probabilidad condicional</summary>

suponga que tenemos un espacio muestral S constituido por la poblacion adulta de una pequeña poblacion que cumple con los requisitos para obetener un titulo universitario, los vamos a clasificar deacuerdo a su genero y situacion laboral

<table><thead><tr><th></th><th data-type="number">Empleado</th><th data-type="number">Desempleado</th><th data-type="number">Total</th></tr></thead><tbody><tr><td>Hombre</td><td>460</td><td>40</td><td>500</td></tr><tr><td>Mujer</td><td>140</td><td>260</td><td>400</td></tr><tr><td>Total</td><td>600</td><td>300</td><td>900</td></tr></tbody></table>

se selecciona al azae uno de estos individuos par que realice un viaje por el pais: nos interesan los siguientes eventos.

1. M = se elige un hombre

2) E = el elegido tiene empleo

</details>

<details>

<summary>Ejercicio 2.4.2 El aereopuerto</summary>

La probabilidad de que un vuelo programado normalemte salga a tiempo es P(D) = 0,83 y la probabilidad de que llegue a tiempo es P(A)=0,82 y la probabilidad de que salga y llegue a tiempo es $$P(D∩A) = 0,78$$, calcule la probabilidad de que:

1. llege a tiempo, dado que salio a tiempo
2. salio a tiempo, dado que llego a tiempo
3. &#x20;llego a tiempo pero salga retrazado&#x20;

</details>

<details>

<summary>Ejercicio 2.4.3 bolsa de pelotas</summary>

Una bolsa contiene 4 bolas blancas y 3 negras, y una segunda bolsa contiene 3 blancas y 5 negras, se saca una bola de la primera bolsa y se coloca sin verla en la segunda bolsa

¿Cual es la probabilidad de que ahora saque una pelota negra de la segunda bolsa?

</details>
