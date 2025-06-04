---
description: >-
  esta seccion exploraremos los diferentes tipos de datos que podemos encontrar
  en la naturaleza y que nos rodean, ademas de que estamos interactuando con
  ellos todo el tiempo.
icon: leaf-heart
---

# La Naturaleza de los Datos

***

> los datos se enmarcan en el fenomeno del cual son detectados para esto, lo primero es definir el tipo de fenomeno que se esta observando, y el tipo de herramienta de medicion que se debera utilizar para la captura de los mismos.

> el fenomeno de la naturaleza encierra infinidades de datos que pueden ser leidos, la limitacion se ecnuentra en la forma y el tipo de mediciones asi como la capacidad de procesamiento del sistema en funcion de estos datos, es por esto que los fenomenos observados son modelados para relaizar, imitaciones del mismo, tan sencillos o complejos como el investigador considere y sea pertinenre para el estudio.

### tipos de datos en la naturaleza.[¶](broken-reference) <a href="#tipos-de-datos-en-la-naturaleza" id="tipos-de-datos-en-la-naturaleza"></a>

> Los datos son la materia prima de la información. Son observaciones o mediciones de fenómenos del mundo real, que pueden ser cuantificados o cualificados.

***

## **Tipos de Datos en la Naturaleza**[**¶**](broken-reference)

***

* **Continuos:** Pueden tomar cualquier valor dentro de un rango. Ejemplos: altura, peso, temperatura.
* **Discretos:** Valores enteros que representan conteos. Ejemplos: número de hijos, cantidad de carros.
* **Datos Cuantitativos:** Expresan cantidades o magnitudes, medibles numéricamente.
* **Ordinales:** Tienen un orden natural, pero las diferencias entre categorías no son uniformes. Ejemplos: nivel de educación (primaria, secundaria, universitaria), escala de Likert (muy de acuerdo, de acuerdo, neutral, en desacuerdo, muy en desacuerdo).
* **Nominales:** No poseen un orden intrínseco. Ejemplos: color de ojos, género, tipo de sangre.
* **Datos Cualitativos:** Describen cualidades o características y no se miden numéricamente.

### **Manejo de Datos en Python: Tipologías de Datos**

Python ofrece una variedad de tipos de datos para representar información de manera eficiente. A continuación, te presento un cuadro comparativo:

<table data-view="cards"><thead><tr><th>-</th><th>-</th><th>-</th></tr></thead><tbody><tr><td>Int</td><td>Números enteros</td><td>42, -10, 0</td></tr><tr><td>float</td><td>Números de punto flotante</td><td>3.14, -2.5, 1.0e-8</td></tr><tr><td>str</td><td>Cadenas de texto</td><td>"Hola mundo", 'Python'</td></tr><tr><td>bool</td><td>Valores booleanos</td><td>True, False</td></tr><tr><td>list</td><td>Colecciones ordenadas y mutables</td><td>[1, 2, 3], ["manzana", "banana"]</td></tr><tr><td>tuple</td><td>Colecciones ordenadas e inmutables</td><td>(1, 2, 3), ("manzana", "banana")</td></tr><tr><td>set</td><td>Colecciones no ordenadas de elementos únicos</td><td>{1, 2, 3}, {"manzana", "banana"}</td></tr><tr><td>dict</td><td>Colecciones de pares clave-valor</td><td>{"nombre": "Juan", "edad": 30}</td></tr></tbody></table>

> Obteniendo el tipo de datos: Puede obtener el tipo de datos de cualquier objeto usando la función \*\*type():

```python
y = 10
print(type(y))
```

{% tabs %}
{% tab title="Ejercicio Uno: intenta averiguar la tipologia de los siguientes datos usando Google colab en tu navegador:" %}
| Example                                      | Data Type  |
| -------------------------------------------- | ---------- |
| x = "Hello World"                            | str        |
| x = 20                                       | int        |
| x = 20.5                                     | float      |
| x = 1j                                       | complex    |
| x = \["apple", "banana", "cherry"]           | list       |
| x = ("apple", "banana", "cherry")            | tuple      |
| x = range(6)                                 | range      |
| x = {"name" : "John", "age" : 36}            | dict       |
| x = {"apple", "banana", "cherry"}            | set        |
| x = frozenset({"apple", "banana", "cherry"}) | frozenset  |
| x = True                                     | bool       |
| x = b"Hello"                                 | bytes      |
| x = bytearray(5)                             | bytearray  |
| x = memoryview(bytes(5))                     | memoryview |
| x = None                                     | NoneType   |
{% endtab %}

{% tab title="Ejercicios sencillo 1" %}
**Comprobar par o impar:**\
Escribe un programa que determine si un número dado es par o impar.

```python
numero = int(input("Introduce un número: "))
if numero % 2 == 0:
    print("El número es par")
else:
    print("El número es impar")
3
```
{% endtab %}

{% tab title="Ejercicio Sencillo 2" %}


**Contador de vocales:**\
Crea un programa que cuente cuántas vocales hay en una frase dada por el usuario.

```python
frase = input("Introduce una frase: ")
vocales = "aeiouAEIOU"
contador = sum(1 for letra in frase if letra in vocales)
print("Número de vocales en la frase:", contador)
```
{% endtab %}
{% endtabs %}

