# Entendiendo a python en JN

¿Qué es PIP?

PIP es un administrador de paquetes para paquetes Python, o módulos si lo desea.

* ¿Qué es un paquete? Un paquete contiene todos los archivos que necesita para un **módulo**. Los _módulos_ son bibliotecas de código Python que puedes incluir en tu proyecto.

***

Encontrar paquetes Encuentre más paquetes en [https://pypi.org/](https://pypi.org/).

***

#### Manejo de Archivos <a href="#manejo-de-archivos" id="manejo-de-archivos"></a>

La función clave para trabajar con archivos en Python es la función **open().**

* The open() function takes two parameters; filename, and mode.
* Hay cuatro métodos (modos) diferentes para abrir un archivo: ||| |:-|:-| |**"r"**| Leer - Valor predeterminado. Abre un archivo para su lectura, error si el archivo no existe| |**"a"**| Apundar - Abre un archivo para añadirlo, crea el archivo si no existe| |**"w"**| Escribir - Abre un archivo para escribir, crea el archivo si no existe| |**"x"**| Crear - Crea el archivo especificado, devuelve un error si el archivo existe| |**"t"**| Texto - Valor predeterminado. Modo de texto| |**"b"**| Binario - Modo binario (por ejemplo, imágenes)|

***

sintaxis

***

f = open("Crcfile.txt") --> para abrir un archivo f = open("Crcfile.txt", "rt") --> abre el archivo y se especifica la naturaleza del mismo, los codigos son iguales en este caso no es necesario especificar ya que es el "default" del sistema.

#### Herramientas de manejos de datos en Jupyter Notebook[¶](broken-reference) <a href="#herramientas-de-manejos-de-datos-en-jupyter-notebook" id="herramientas-de-manejos-de-datos-en-jupyter-notebook"></a>

dentro del entorno de JN tenemos muchas herramientas de analisis que nos permitiran la manipulacion de datos en tiempo real asi como el analisis de los mismos con un par de lienas de codigo.

A diferencia de Ms Excel este no es visual es decir no podras ver el contenido de cada celda ano ser que sea llamda para visualoizarse, estos conceptos los veremos mas adelante duarante el desarrollo del curso.

{% hint style="info" %}
los programas o aplicaciones que trabajan junto a JN, son llamadas _Librerias_, estas son los que procesan o realizan los trabajos, algunas de estas se encuentran precargadas en el ambiente de Jupiter otras por el contrario hay que instalarlas o llamarlas para que generen valor en el documento, cada una de ellas tiene su propia sintaxis.
{% endhint %}

<figure><img src="../../.gitbook/assets/1. librerias.png" alt=""><figcaption></figcaption></figure>

**Librerias para manejo de Datos en Python y jupyter Notebook**[**¶**](broken-reference)

***

* NumPy:

***

Es la librería fundamental para computación numérica en Python. Proporciona objetos de arreglos multidimensionales, diversas funciones matemáticas y herramientas para trabajar con estos arreglos.

***

* Pandas:

***

Construido sobre NumPy, Pandas ofrece estructuras de datos de alto nivel como Series y DataFrames, que facilitan el análisis y manipulación de datos. Permite cargar datos desde diversos formatos (CSV, Excel, bases de datos), realizar limpieza, transformación, y análisis exploratorio de datos.

***

**librerias para Visualización:**[**¶**](broken-reference)

***

* Matplotlib:

***

Es la biblioteca de visualización más utilizada en Python. Ofrece una amplia variedad de gráficos y personalizaciones para visualizar datos de manera efectiva.

***

* Seaborn:

***

Construido sobre Matplotlib, Seaborn proporciona una interfaz de alto nivel para crear gráficos estadísticos atractivos y informativos.

***

* Plotly:

***

Crea gráficos interactivos que se pueden exportar a diferentes formatos y compartir en línea.

***

* Otras Herramientas Útiles:

***

* SQLAlchemy: Permite conectar Jupyter Notebook a diversas bases de datos relacionales y ejecutar consultas SQL.
* Xarray: Extensión de Pandas para trabajar con datos multidimensionales, como datos climáticos o imágenes.
* NetworkX: Para el análisis de redes.

***

#### Python desde jupyter notebook y MySQL[¶](broken-reference) <a href="#python-desde-jupyter-notebook-y-mysql" id="python-desde-jupyter-notebook-y-mysql"></a>

**Instalacion de los paquetes de MySQL**[**¶**](broken-reference)

Para ejecutar SQL directamente en un cuaderno de Jupyter, necesitaremos dos cosas:

1. Un conector o controlador para interactuar con la base de datos (como sqlite3, psycopg2, etc.).
2. Una extensión de Jupyter que nos permita ejecutar SQL en las celdas.

***

* Paquetes necesarios:

***

1. ipython-sql: Extensión para ejecutar SQL en Jupyter.

Un controlador para la base de datos que estés utilizando.

Si, por ejemplo, usas **SQLite**, el paquete sqlite3 ya está integrado en Python.

Si usas PostgreSQL, necesitarás psycopg2.

**diferencia entre SQLite y SQLAlchemy**[**¶**](broken-reference)

1. SQLite:

**Motor de base de datos:** SQLite es un sistema de gestión de bases de datos relacional (SGBDR) ligero y embebido. Esto significa que es una base de datos completa en sí misma, almacenada en un único archivo.

**Funcionalidad:** Permite crear, modificar y consultar bases de datos, pero su interfaz es a nivel de SQL. Es decir, interactúas directamente con la base de datos a través de comandos SQL.

**Uso común:** Ideal para proyectos pequeños, aplicaciones de escritorio, prototipos y cualquier situación en la que necesites una base de datos simple y ligera. Limitaciones: Al ser embebido, tiene ciertas limitaciones en términos de concurrencia y escalabilidad comparado con otros SGBDR.

2. SQLAlchemy:

_SQLAlchemy es una poderosa biblioteca de Python para trabajar con bases de datos relacionales utilizando SQL. Ofrece una abstracción de alto nivel llamada ORM (Object Relational Mapping) que permite interactuar con las bases de datos usando objetos Python. También puedes utilizarlo a nivel de SQL puro sin el ORM, lo que lo convierte en una opción flexible para trabajar con bases de datos_

**ORM (Object-Relational Mapper):** SQLAlchemy es una biblioteca de Python que actúa como un puente entre tu código Python y la base de datos. Te permite interactuar con la base de datos utilizando objetos de Python, lo que simplifica la programación.

**Abstracción:** SQLAlchemy te abstrae de los detalles específicos de la base de datos subyacente. Esto significa que puedes cambiar de SQLite a PostgreSQL o MySQL sin modificar mucho tu código.

**Funcionalidad:** Además de ejecutar consultas SQL, SQLAlchemy ofrece características avanzadas como mapeo objeto-relacional, migraciones, y optimización de consultas.

**Uso común:** Ideal para proyectos de mayor envergadura donde necesitas una mayor flexibilidad y control sobre la interacción con la base de datos.

**Instalar el Administrador de Mysql**[**¶**](broken-reference)

para efectos de conocer el entorno de Mysql debemos buscar e instalar Mysql workbench

**Workbennch:** Es una herramienta gráfica que facilita la interacción con bases de datos SQL.

[https://www.mysql.com/products/workbench/](https://www.mysql.com/products/workbench/)

donde debemos seleccionar la version que se acomode a nuestro sistema operativo, en este caso, este curso fue realizado con una Mac M1, asique la version que se utilizara para explicacion sera orientada a Mac, no obstante pueden existir algunas variaciones minimas, pero no sera el problema.

MySQL es un sistema de gestión de bases de datos relacionales (SGBDR) muy popular, conocido por su rendimiento, flexibilidad y comunidad activa. Workbench es una herramienta gráfica que facilita la interacción con bases de datos MySQL, permitiendo crear bases de datos, tablas, ejecutar consultas y visualizar los resultados de forma intuitiva.

**Conceptos Básicos de SQL**

SELECT: Se utiliza para seleccionar datos de una o más tablas. FROM: Especifica la tabla de la que se extraerán los datos. WHERE: Filtra los resultados según una condición. INSERT INTO: Inserta nuevos registros en una tabla. UPDATE: Actualiza los valores de registros existentes. DELETE: Elimina registros de una tabla.

**Tarea del modulo 0:**[**¶**](broken-reference)

1. instala el server y el workbench de MYSQL en tu maquina.
2. anota con cautela la contraseña de tu Server.
3. instala el ambiente de workbench y crea una base de datos

puedes apoyarte con IA para esta tarea.

**Pasos para instalacion de MySQL, Workbench y mi primetra tabla**[**¶**](broken-reference)

***

1. Descarga de MySQL y Workbench

***

Visita la página oficial de MySQL: [https://www.mysql.com](https://www.mysql.com/) Selecciona tu sistema operativo: Haz clic en el botón correspondiente a tu sistema operativo (Windows, macOS o Linux). Descarga los instaladores: Descarga tanto el instalador de MySQL Server como el de MySQL Workbench.

***

2. Instalación de MySQL Server

***

Ejecuta el instalador: Haz doble clic en el archivo descargado. Sigue las instrucciones: Sigue las instrucciones del asistente de instalación, aceptando los términos y condiciones y seleccionando las opciones por defecto en la mayoría de los casos. Establece una contraseña: Durante la instalación, se te pedirá que establezcas una contraseña para el usuario root de MySQL. Anota esta contraseña ya que la necesitarás para conectarte a la base de datos.

***

3. Instalación de MySQL Workbench

***

Ejecuta el instalador: Haz doble clic en el archivo descargado. Sigue las instrucciones: Al igual que con MySQL Server, sigue las instrucciones del asistente de instalación.

***

4. Conexión a MySQL Workbench

***

* Inicia Workbench: Una vez instalada, abre la aplicación MySQL Workbench.
* Crea una nueva conexión: Haz clic en el icono "+" en la sección "MySQL Connections".
* Configura la conexión:
* Name: Asigna un nombre a tu conexión (por ejemplo, "MiPrimeraBaseDeDatos").
* Host: Normalmente es "localhost".
* User: "root" (el usuario por defecto).
* Password: Introduce la contraseña que estableciste durante la instalación de MySQL Server.
* Port: Por lo general, es "3306".
* Prueba la conexión: Haz clic en "Test Connection". Si todo está correcto, se establecerá la conexión.

***

5. Creación de una Base de Datos

***

* Expanda la conexión: Haz clic en el signo "+" junto al nombre de tu conexión para expandirla.
* Crea una nueva base de datos: Haz clic derecho en el nombre de tu conexión y selecciona "Create Database".
* Asigna un nombre: Escribe un nombre para tu base de datos (por ejemplo, "mydb").
* Ejecuta la creación: Haz clic en "OK".

***

6. Creación de una Tabla

***

Selecciona la base de datos: Haz clic en el nombre de la base de datos que acabas de crear. Crea una nueva tabla: Haz clic derecho y selecciona "Create Table".

* Define los campos:

1. Nombre del campo: Escribe un nombre descriptivo (por ejemplo, "id", "nombre", "edad").
2. Tipo de dato: Selecciona el tipo de dato adecuado (int, varchar, etc.).
3. Longitud: Especifica la longitud máxima para los campos de tipo texto.

* Clave primaria: Indica cuál es la clave primaria de la tabla (un campo único que identifica cada registro).

Ejecuta la creación: Haz clic en "OK".

***

7. Insertar Datos

***

Escribe una consulta SQL: En la pestaña "SQL", escribe una consulta como esta para insertar datos:

"INSERT INTO mi\_tabla (id, nombre, edad) VALUES (1, 'Juan', 30);" (sin comillas)

8. Ejecuta la Consulta: en el signo de rayo (:9)
