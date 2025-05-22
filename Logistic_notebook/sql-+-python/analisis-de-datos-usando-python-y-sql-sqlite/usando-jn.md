# Usando JN

## Guía para Empezar a Usar Jupyter Notebook desde Google Colab

Google Colab es una plataforma que permite usar Jupyter Notebooks en la nube. A continuación se muestra cómo comenzar:

### Celda de Texto

Para agregar una celda de texto:

1. Haz clic en "+ Texto".
2. Escribe tu contenido usando [Markdown](https://colab.research.google.com/notebooks/markdown_guide.ipynb).

Ejemplo de texto en Markdown:

```
# Encabezado Nivel 1
## Encabezado Nivel 2

Texto normal **negrita** *cursiva*.
```

### Celda de Código

Para insertar una celda de código:

1. Haz clic en "+ Código".
2. Introduce tu script en Python dentro de la celda.

Ejemplo básico en una celda de código:

```python
print("Hola, Google Colab!")
```

### Instalación de Librerías

Para instalar librerías usando `pip`, usa:

```python
!pip install nombre_de_la_libreria
```

Ejemplo:

```python
!pip install numpy
```

Este comando descarga e instala la biblioteca `numpy` en tu entorno de Colab.

### Importar Librerías

Para importarlas en tu código:

```python
import numpy as np
```

{% hint style="info" %}
Ahora, estás listo para comenzar a trabajar en tu proyecto de Colab.
{% endhint %}

## ¿Qué es PIP?

PIP es un administrador de paquetes para paquetes Python, o módulos si lo desea.

> ¿Qué es un paquete?\
> Un paquete contiene todos los archivos que necesita para un **módulo**.\
> Los _módulos_ son bibliotecas de código Python que puedes incluir en tu proyecto.

***

Encontrar paquetes\
Encuentre más paquetes en [https://pypi.org/.](https://pypi.org/)

***

#### Manejo de Archivos:

La función clave para trabajar con archivos en Python es la función **open().**

The open() function takes two parameters; filename, and mode.

```latex
// Some code
|||
|:-|:-|
|"r"| Leer - Valor predeterminado. Abre un archivo para su lectura, error si el archivo no existe|
|"a"| Apundar - Abre un archivo para añadirlo, crea el archivo si no existe|
|"w"| Escribir - Abre un archivo para escribir, crea el archivo si no existe|
|"x"| Crear - Crea el archivo especificado, devuelve un error si el archivo existe|
|"t"| Texto - Valor predeterminado. Modo de texto|
|"b"| Binario - Modo binario (por ejemplo, imágenes)|
```

Hay cuatro métodos (modos) diferentes para abrir un archivo:\


***

sintaxis

***

f = open("Crcfile.txt") --> para abrir un archivo\
f = open("Crcfile.txt", "rt") --> abre el archivo y se especifica la naturaleza del mismo, los codigos son iguales en este caso no es necesario especificar ya que es el "default" del sistema.
