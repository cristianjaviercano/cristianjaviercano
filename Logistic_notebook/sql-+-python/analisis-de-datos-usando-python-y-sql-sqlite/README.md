---
icon: python
---

# Analisis de Datos usando Python y SQL (SqLite)



### Introduccion a SQL y a las Bases de Datos:[¶](broken-reference) <a href="#introduccion-a-sql-y-a-las-bases-de-datos" id="introduccion-a-sql-y-a-las-bases-de-datos"></a>

***

**SQL (Structured Query Language):**

***

Es un lenguaje estándar para gestionar y manipular bases de datos relacionales. SQL permite realizar tareas como consultar datos, actualizar registros, insertar nuevos datos y eliminar datos existentes.Bases de Datos Relacionales: Son colecciones organizadas de datos que se estructuran en tablas. Cada tabla tiene filas (registros) y columnas (campos).

Las bases de datos relacionales utilizan claves primarias y foráneas para establecer relaciones entre tablas.

Ejemplo de una base de datos simple:

1. Tabla Clientes:

* ID (Clave primaria)
* Nombre
* Email

2. Tabla Pedidos:

* PedidoID (Clave primaria)
* ClienteID (Clave foránea que referencia a Clientes.ID)
* Fecha

***

**Características de SQL**

1. Declarativo: SQL es un lenguaje declarativo, lo que significa que describe qué hacer, no cómo hacerlo.
2. Portabilidad: SQL es compatible con la mayoría de los sistemas de gestión de bases de datos (DBMS) como MySQL, PostgreSQL, Oracle, SQL Server, etc.
3. Estandarización: SQL es un estándar internacional, lo que asegura su consistencia y compatibilidad en diferentes plataformas.

**Usos Comunes de SQL**

1. Consultas de Datos: Recuperar información específica de grandes conjuntos de datos.
2. Gestión de Datos: Insertar, actualizar y eliminar datos de manera eficiente.
3. Análisis de Datos: Realizar cálculos y agregaciones para obtener insights.
4. Seguridad de Datos: Controlar el acceso a los datos mediante permisos y roles.

***

para efectos de este curso utlizameros "Workbench" como plataforma de manipulacion de datos.

**MySQL Workbench**

* es una herramienta visual de diseño y administración de bases de datos para MySQL . Es ampliamente utilizada por desarrolladores y administradores de bases de datos para interactuar con bases de datos MySQL de manera más eficiente.

1. Interfaz Gráfica de Usuario (GUI): Proporciona una interfaz amigable para realizar tareas comunes de administración de bases de datos sin necesidad de usar la línea de comandos.
2. Modelado de Datos: Permite crear modelos de datos visuales, lo que facilita el diseño y la comprensión de la estructura de la base de datos.
3. Desarrollo de SQL: Incluye un editor SQL que permite escribir, ejecutar y depurar consultas SQL . También ofrece resaltado de sintaxis y autocompletado para facilitar la escritura de código.
4. Administración de Servidores: Ofrece herramientas para gestionar usuarios, permisos, y realizar tareas de mantenimiento como copias de seguridad y restauración de bases de datos.
5. Migración de Datos: Facilita la migración de bases de datos desde otros sistemas de gestión de bases de datos a MySQL.
6. Monitoreo de Rendimiento: Proporciona herramientas para monitorear el rendimiento del servidor MySQL y optimizar consultas.
7. Compatibilidad Multiplataforma: Está disponible para Windows, macOS y Linux, lo que permite su uso en diferentes entornos.

### Teoria de Bases de Datos[¶](broken-reference) <a href="#teoria-de-bases-de-datos" id="teoria-de-bases-de-datos"></a>

#### Concepto de base de datos[¶](broken-reference) <a href="#concepto-de-base-de-datos" id="concepto-de-base-de-datos"></a>

***

Concepto uno:

***

Una base de datos es una colección organizada de datos que pueden ser fácilmente accesibles, gestionados y actualizados. Estos datos están estructurados de tal manera que permiten realizar consultas rápidas y precisas sobre grandes volúmenes de información. (crc)

Una base de datos es como una biblioteca organizada y digital. Imaginemos una biblioteca donde cada libro contiene información específica y todos los libros están ordenados de manera que puedas encontrar fácilmente el que buscas. Una base de datos funciona de manera similar, pero en lugar de libros, almacena información digital.

* ¿Para qué sirven las bases de datos?

1. **Almacenar grandes cantidades de información:** Desde datos personales hasta registros de ventas, todo puede ser guardado en una base de datos.
2. **Organizar la información:** Las bases de datos estructuran los datos de manera lógica, lo que facilita encontrar la información que necesitas.
3. **Buscar información rápidamente:** Con una base de datos, puedes encontrar información específica en cuestión de segundos.
4. **Compartir información:** Puedes compartir la información almacenada en una base de datos con otras personas o aplicaciones.

#### ¿Cómo funciona una base de datos?[¶](broken-reference) <a href="#c2-bfc-c3-b3mo-funciona-una-base-de-datos" id="c2-bfc-c3-b3mo-funciona-una-base-de-datos"></a>

* Una base de datos se compone de:

1. **Tablas:** Son como hojas de cálculo donde se almacenan los datos. Cada tabla tiene filas (registros) y columnas (campos).
2. **Registros:** Cada fila representa un elemento de datos, como un cliente o un producto.
3. **Campos:** Cada columna representa un atributo de un elemento de datos, como el nombre, la dirección o el precio.
4. **Relaciones:** Las tablas pueden estar relacionadas entre sí, lo que permite establecer conexiones entre los datos.

#### ¿Cuáles son los tipos de bases de datos?[¶](broken-reference) <a href="#c2-bfcu-c3-a1les-son-los-tipos-de-bases-de-datos" id="c2-bfcu-c3-a1les-son-los-tipos-de-bases-de-datos"></a>

Existen diferentes tipos de bases de datos, cada uno con sus características y usos:

1. **Relacionales:** Las bases de datos relacionales son las más comunes. Se basan en un modelo de datos tabular, donde la información se organiza en tablas (filas y columnas). Las tablas pueden estar relacionadas entre sí mediante _claves primarias y claves foráneas_
2. **No relacionales (NoSQL):** Diseñadas para manejar grandes volúmenes de datos no estructurados o semiestructurados, como texto o datos de redes sociales.
3. **En memoria:** Almacenan los datos en la memoria RAM del servidor, lo que permite un acceso muy rápido.
4. **Distribuidas:** Reparten los datos en múltiples servidores para mejorar el rendimiento y la escalabilidad.

***

definicion:

1. **Clave primaria:** es un campo o conjunto de campos en una tabla que identifica de manera única cada registro dentro de esa tabla. Esto significa que no puede haber dos filas en la misma tabla que tengan el mismo valor para la clave primaria. Las características de una clave primaria son:

* Unicidad: Cada valor de la clave primaria debe ser único para cada registro.
* No nula: No se permite que los valores de la clave primaria sean nulos; cada registro debe tener un valor asignado.
* Inalterabilidad: Idealmente, los valores de la clave primaria no deberían cambiar a lo largo del tiempo, ya que esto podría afectar las relaciones con otras tablas

2. **Clave foranea:** es un campo (o conjunto de campos) en una tabla que se utiliza para crear una relación con otra tabla. Una clave foránea apunta a la clave primaria en otra tabla, estableciendo así una conexión entre los registros de ambas tablas. Las características de una clave foránea son:

* Referencia: La clave foránea debe coincidir con un valor existente en la clave primaria de la tabla relacionada.
* Integridad referencial: Asegura que las relaciones entre las tablas sean coherentes; es decir, no se pueden insertar valores en la clave foránea que no existan como claves primarias en la otra tabla.
* Puede ser nula: A diferencia de la clave primaria, los campos definidos como claves foráneas pueden aceptar valores nulos si no es necesario establecer una relación 45.

***

#### Como Diseñar una Base de Datos.[¶](broken-reference) <a href="#como-dise-c3-b1ar-una-base-de-datos" id="como-dise-c3-b1ar-una-base-de-datos"></a>

1. **analizar el sistema:** se debe analizar el sistema observado para encontrar los elementos claves y los campos que se deben gestionar al interior de la base de datos.

no todos los datos pertenecen a la misma tabla, es posible almacenar diferentes tablas con diferentes tipos de datos y estos se relacionarian entre si, con el fin de hacer l conexion y generar informacion de Valor.

2. **Realizar el esquema de relacion de la base de datos:** las bases de datos relacionadas entre ellas deberan ser graficadas a parte con el fin de manejar una relacion directa, sobre todo, las relaciones funcionales entre los datos. para esto podemos usar herramientas como powerquery de excel o de forma manual papel y lapiz.
3. **Diseñar los campos de las bases de datos**: temar base de datos por base de datos y diseñar los campos de cada una de las bases de datos, para poder ingresar los datos.
4. **Diseñar la base de datos en SQL e ingresar datos**:

en este caso vamos. ahacer uso de la libreria _Pandas_ desde python para importar datos a las tablas, no obstante tenemos otras formas de hacerlo las cuales listamos:

**1. Usar SQL Directamente desde Python**[**¶**](broken-reference)

* _Conectar a la Base de Datos:_

Asegúrate de tener una conexión establecida con tu base de datos usando una librería como pymysql o sqlite3 .

import pymysql

connection = pymysql.connect( host='localhost', --> el nombre del host de tu SQL user='tu\_usuario', --> tu suario password='tu\_contraseña', --> la contraseña de la BD SQL database='nombre\_de\_tu\_base\_de\_datos' --> cnombre de la BD )

* Crear un Cursor:

Utiliza un cursor para ejecutar comandos SQL.

cursor = connection.cursor()

* Insertar Datos:

Usa una sentencia SQL INSERT INTO para agregar datos.

sql = "INSERT INTO Productos (nombre, descripcion, precio, cantidad\_en\_stock, categoria\_id, proveedor\_id) VALUES (%s, %s, %s, %s, %s, %s)" val = ("Producto1", "Descripción del producto", 10.99, 100, 1, 1) cursor.execute(sql, val)

* Confirmar Cambios: Asegúrate de confirmar los cambios para que se guarden en la base de datos.

connection.commit()

* Cerrar Conexión:

Siempre cierra la conexión después de completar las operaciones.

connection.close()

NOTA: esta forma no es tan agil de ingresar datos al sistema, pero es valida.

**2. Usar Pandas para Cargar Datos desde un DataFrame**[**¶**](broken-reference)

1. Importar Librerías:

Asegúrate de tener pandas y SQLAlchemy instalados.

2. Crear un DataFrame:

Crea un DataFrame con los datos que deseas cargar.

data = { 'nombre': \['Producto1', 'Producto2'], 'descripcion': \['Descripción1', 'Descripción2'], 'precio': \[10.99, 20.99], 'cantidad\_en\_stock': \[100, 200], 'categoria\_id': \[1, 2], 'proveedor\_id': \[1, 2] } df = pd.DataFrame(data)

3. Conectar a la Base de Datos:

Usa SQLAlchemy para crear una conexión.

engine = create\_engine('mysql+pymysql://tu\_usuario:tu\_contraseña@localhost/nombre\_de\_tu\_base\_de\_datos')

4. Cargar el DataFrame a la Base de Datos:

Usa el método **to\_sql** de pandas.

'df.to\_sql('Productos', con=engine, if\_exists='append', index=False'

Debemos limpiar la base de datos, por ejemplo los valores de las columnas

* Parental\_Involvement object
* Access\_to\_Resources object
* Extracurricular\_Activities object

son de tipo String, hay que pasarlas a Int o a Bollean para que sea computables con el reto.

para esto haremos una lista de las columnas que deseamos cambiar y definimos los valores para cada uno de los datos

Parental\_Involvement object a Low = 1 Medium =2 High = 3 Access\_to\_Resources object a Low = 1 Medium =2 High = 3 Extracurricular\_Activities object a Yes = 1 No = 0 Motivation\_Level object a Low = 1 Medium =2 High = 3 Internet\_Access object a Yes = 1 No = 0 Family\_Income object a Low = 1 Medium =2 High = 3 Teacher\_Quality object a Low = 1 Medium =2 High = 3 School\_Type object a Public = 1 Private = 2 Peer\_Influence object a Positive = 1 Negative = 2 Neutral = 3 Learning\_Disabilities object a yes = 1 no = 0 Parental\_Education\_Level object a High School = 1 College = 2 Postgraduate = 3 Distance\_from\_Home object a Near = 1 Moderate =2 Far = 3 Gender object a Male = 1 Female = 0

In \[38]:

```
#(EDA)
df.describe()
# Correlasion
corr_matrix = df.corr()
print(corr_matrix)

# Visualizacion
import seaborn as sns
import matplotlib.pyplot as plt

sns.heatmap(corr_matrix, annot=True)
plt.show()


from sklearn.ensemble import RandomForestRegressor

X = df.drop('Exam_Score', axis=1)
y = df['Exam_Score']

model = RandomForestRegressor()
model.fit(X, y)

feature_importances = pd.Series(model.feature_importances_, index=X.columns)
feature_importances.sort_values(ascending=False).plot(kind='barh')
plt.show()
```

```
/var/folders/c5/v7gmryxx5clfs98nnyc30ys00000gn/T/ipykernel_34364/18802199.py:4: FutureWarning: The default value of numeric_only in DataFrame.corr is deprecated. In a future version, it will default to False. Select only valid columns or specify the value of numeric_only to silence this warning.
  corr_matrix = df.corr()
```

```
                   Hours_Studied  Attendance  Sleep_Hours  Previous_Scores  \
Hours_Studied           1.000000   -0.009908     0.010977         0.024846   
Attendance             -0.009908    1.000000    -0.015918        -0.020186   
Sleep_Hours             0.010977   -0.015918     1.000000        -0.021750   
Previous_Scores         0.024846   -0.020186    -0.021750         1.000000   
Tutoring_Sessions      -0.014282    0.014324    -0.012216        -0.013122   
Physical_Activity       0.004624   -0.022435    -0.000378        -0.011274   
Exam_Score              0.445455    0.581072    -0.017022         0.175079   

                   Tutoring_Sessions  Physical_Activity  Exam_Score  
Hours_Studied              -0.014282           0.004624    0.445455  
Attendance                  0.014324          -0.022435    0.581072  
Sleep_Hours                -0.012216          -0.000378   -0.017022  
Previous_Scores            -0.013122          -0.011274    0.175079  
Tutoring_Sessions           1.000000           0.017733    0.156525  
Physical_Activity           0.017733           1.000000    0.027824  
Exam_Score                  0.156525           0.027824    1.000000  
```

```
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
Cell In[38], line 21
     18 y = df['Exam_Score']
     20 model = RandomForestRegressor()
---> 21 model.fit(X, y)
     23 feature_importances = pd.Series(model.feature_importances_, index=X.columns)
     24 feature_importances.sort_values(ascending=False).plot(kind='barh')

File ~/anaconda3/lib/python3.10/site-packages/sklearn/ensemble/_forest.py:345, in BaseForest.fit(self, X, y, sample_weight)
    343 if issparse(y):
    344     raise ValueError("sparse multilabel-indicator for y is not supported.")
--> 345 X, y = self._validate_data(
    346     X, y, multi_output=True, accept_sparse="csc", dtype=DTYPE
    347 )
    348 if sample_weight is not None:
    349     sample_weight = _check_sample_weight(sample_weight, X)

File ~/anaconda3/lib/python3.10/site-packages/sklearn/base.py:565, in BaseEstimator._validate_data(self, X, y, reset, validate_separately, **check_params)
    563         y = check_array(y, input_name="y", **check_y_params)
    564     else:
--> 565         X, y = check_X_y(X, y, **check_params)
    566     out = X, y
    568 if not no_val_X and check_params.get("ensure_2d", True):

File ~/anaconda3/lib/python3.10/site-packages/sklearn/utils/validation.py:1106, in check_X_y(X, y, accept_sparse, accept_large_sparse, dtype, order, copy, force_all_finite, ensure_2d, allow_nd, multi_output, ensure_min_samples, ensure_min_features, y_numeric, estimator)
   1101         estimator_name = _check_estimator_name(estimator)
   1102     raise ValueError(
   1103         f"{estimator_name} requires y to be passed, but the target y is None"
   1104     )
-> 1106 X = check_array(
   1107     X,
   1108     accept_sparse=accept_sparse,
   1109     accept_large_sparse=accept_large_sparse,
   1110     dtype=dtype,
   1111     order=order,
   1112     copy=copy,
   1113     force_all_finite=force_all_finite,
   1114     ensure_2d=ensure_2d,
   1115     allow_nd=allow_nd,
   1116     ensure_min_samples=ensure_min_samples,
   1117     ensure_min_features=ensure_min_features,
   1118     estimator=estimator,
   1119     input_name="X",
   1120 )
   1122 y = _check_y(y, multi_output=multi_output, y_numeric=y_numeric, estimator=estimator)
   1124 check_consistent_length(X, y)

File ~/anaconda3/lib/python3.10/site-packages/sklearn/utils/validation.py:879, in check_array(array, accept_sparse, accept_large_sparse, dtype, order, copy, force_all_finite, ensure_2d, allow_nd, ensure_min_samples, ensure_min_features, estimator, input_name)
    877         array = xp.astype(array, dtype, copy=False)
    878     else:
--> 879         array = _asarray_with_order(array, order=order, dtype=dtype, xp=xp)
    880 except ComplexWarning as complex_warning:
    881     raise ValueError(
    882         "Complex data not supported\n{}\n".format(array)
    883     ) from complex_warning

File ~/anaconda3/lib/python3.10/site-packages/sklearn/utils/_array_api.py:185, in _asarray_with_order(array, dtype, order, copy, xp)
    182     xp, _ = get_namespace(array)
    183 if xp.__name__ in {"numpy", "numpy.array_api"}:
    184     # Use NumPy API to support order
--> 185     array = numpy.asarray(array, order=order, dtype=dtype)
    186     return xp.asarray(array, copy=copy)
    187 else:

File ~/anaconda3/lib/python3.10/site-packages/pandas/core/generic.py:2070, in NDFrame.__array__(self, dtype)
   2069 def __array__(self, dtype: npt.DTypeLike | None = None) -> np.ndarray:
-> 2070     return np.asarray(self._values, dtype=dtype)

ValueError: could not convert string to float: 'Low'
```

### Pasos basicos[¶](broken-reference) <a href="#pasos-basicos" id="pasos-basicos"></a>

leer una tabla en python que tengamos en CSV

import pandas as pd

df = pd.read\_csv('url del archivo y el nomnbre')

print(df.to\_string())

### que es PANDAS:[¶](broken-reference) <a href="#que-es-pandas" id="que-es-pandas"></a>

Pandas es una biblioteca de Python utilizada para trabajar con conjuntos de datos.

Tiene funciones para analizar, limpiar, explorar y manipular datos.

El nombre "Pandas" tiene una referencia tanto a "Panel Data" como a "Python Data Analysis" y fue creado por Wes McKinney en 2008.

### ¿Por qué usar pandas?[¶](broken-reference) <a href="#c2-bfpor-qu-c3-a9-usar-pandas" id="c2-bfpor-qu-c3-a9-usar-pandas"></a>

Pandas nos permite analizar macrodatos y sacar conclusiones basadas en teorías estadísticas.

Los pandas pueden limpiar conjuntos de datos desordenados y hacerlos legibles y relevantes.

Los datos relevantes son muy importantes en la ciencia de datos.

### ¿Qué podemos hacer los pandas?[¶](broken-reference) <a href="#c2-bfqu-c3-a9-podemos-hacer-los-pandas" id="c2-bfqu-c3-a9-podemos-hacer-los-pandas"></a>

Pandas te da respuestas sobre los datos. Como:

¿Hay una correlación entre dos o más columnas? ¿Cuál es el valor promedio? ¿Valor máximo? ¿Valor mínimo? Los pandas también pueden eliminar filas que no son relevantes o que contienen valores incorrectos, como valores vacíos o NULL. Esto se llama limpieza de los datos.

### Analisis estadistico basico para python usando Bases de datos[¶](broken-reference) <a href="#analisis-estadistico-basico-para-python-usando-bases-de-datos" id="analisis-estadistico-basico-para-python-usando-bases-de-datos"></a>

Ahora que podemos importar y leer datos en en eltorno de python vamos a realizar algunas consultas y analisis basicos que nos permitan generar valor, en este caso como trabajaremos con con las bases de datos.

1. haremos un EDA (exploratoru Data Analysis) analisis exploratorio de datos.

El primer paso en cualquier analisis de datos debe ser el EDA, ya que es el que nos muestra el comportamiento y naturaleza de los datos que a los que nos enfrentamos.

este EDA hace parte de la estadistica clasica la cual se ocupa casi que exclusivamente de la inferencia de datos en un conjunto de procedimientos a veces complejo, que nos permite sacar conclusiones de grandes grupos de datos, ya sea analizando el total de los datos observados del fenomeno o a partir de una muestra. de este ejercicio _jhon W turkey_ en su libro "the future of data analisys" \[turkey 1962] propuso por primera vez una nueva discliplina a la que llamo "Data Analisys" o analisis de Datos, donde se centraria mas en el comportamiento de inforacion almacenada en grandes bloques de "bits"

#### Elementos de los datos estructurados:[¶](broken-reference) <a href="#elementos-de-los-datos-estructurados" id="elementos-de-los-datos-estructurados"></a>

si bien ya conocemos que los datos provienen de miuchas fuentes,sensores, eventos, texto, imagenes vieos etc, estos son "vomitados" literalmente al mundo de una manera brusca y constante, gran parte de estos datos no estan estructurados, como por ejemplo las imagenes que son un gran cumulo de pixeles, y cada pixel tiene un elemento RGB, etc.

el gran desafio de la ciencia de datos es la conversion de esos datos no estructurados o grandes volumenes de datos desde un fenomeno observado en informacion valiosa

existen dos tipos de datos estructurados:

* numericos
* categoricos

continuando con la seccion naturaleza de los datos explicamos:

los datos de tipo numerico se presentan en dos modalidades sencillas

* continuos
* discretos

los datos de tipo categoricos, son aquellos que adoptan un conjunto fijo de valores. como por ejemplo: tipos de pantallas = (plasma LCD, led, etc) nombres de estados de USA = (alabama, alaska etc)

por otra parte tenemos los datos **Binarios** los que toiman valores de 0/1 o falso y verdadero.

datos Ordianles: (1,2,3,4,5)

la importancia de reconocer la tipologia de los datos en un analisis de datos se centra en que debemos renconocer la naturlaeza del fenomeno y el tipo de dato que este nos esta arrojando con el find de poder hacer el mejor sistema de procesamiento de datos que podamos. para asi finalmente decidir la forma de vizualizacion de los mismos, para finalmente generar valor.

#### Datos Rectangulares (tablas de datos)[¶](broken-reference) <a href="#datos-rectangulares-tablas-de-datos" id="datos-rectangulares-tablas-de-datos"></a>

El marco de referencia tipica para el analisis de datos en analisis de datos son las tablas estructuradas de forma matricial, como por ejemplo una hoja de calculo o una tabla adscrita a una base de datos.

el termino "rectangular data" es el termino asociado a una matriz bidimensional con \*\*filas que indican los registros y columnas que indican las catacteristicas.

|           |        |          |          |              |
| --------- | ------ | -------- | -------- | ------------ |
| Categoría | Divisa | Vendedor | Duracion | Calificacion |
| musica    | Dólar  | 3249     | 5        | 2,5          |
| musica    | Dólar  | 3250     | 4        | 4,1          |

dentro del entorno de python los llamaremos. "DATA FRAME"

**Marcos de Datos e indices**[**¶**](broken-reference)

las tablas de bases de datos tradicionales tienen una o mas columnas designadas como indices, escencialmente es un numero de filas, con el fin de mejorar sustancialemnte las consultas a las tablas, o bases de datos, en python este trabajo es especializado a la libreria "pandas" donde el objeto central es el DataFrame por defecto. comun mente citado como "df"

#### Estructura de datos NO rectangulares[¶](broken-reference) <a href="#estructura-de-datos-no-rectangulares" id="estructura-de-datos-no-rectangulares"></a>

existen otras estructuras denominadas "no rectangulares" en la ciencia de Datos.

1. los datos de series de tiempo registran condiciones sucesivas de la misma variable. es la materia prima de los metodos de pronosticos estadisticos y analisis de comportamiento se series de tiempo, asi como el continuo registro de una vriable por un sensor en funcion del tiempo.

### Estimacion de la localizacion[¶](broken-reference) <a href="#estimacion-de-la-localizacion" id="estimacion-de-la-localizacion"></a>

los datos rectangulares o estructurados en tablas piueden tener un sin fin de variaciones en su comportamiento es por esto que nos centramos en el EDA en encontrar un Valor tipico para cada caracteristica es decir su tendencia central

1. Media
2. Media ponderada
3. Mediana
4. Percentil
5. Mediana ponderada
6. Media Recortada
7. Robusto o Resistente
8. Atipico

en la medida de lo posible se recomienta empezar por las medias y medianas, no siendo estas la unica opcion, o la mejor, pero si la mas facíl de usar e interpretar, a sabiendas que nos enfrentamos a una serie de datos de la cual desconocemos su naturaleza.

### Estimacion de la Variabilidad[¶](broken-reference) <a href="#estimacion-de-la-variabilidad" id="estimacion-de-la-variabilidad"></a>

una segunda dimension a extraer en un conjunto de datos se denomina la variablidad, tambien conocida como la dispersion, esta mide el grado de agrupacion o dispersion de los valores de los datos, dentro del corazon de las estadistica se encuentra la variablidad, la cual hay que medirla, reducirla, identificar las fuentes de la variabilidad y tomar desiciones con respecto a ellas.

1. Desviaciones
2. Varianza
3. Desviacion estandar
4. desviacion media Absoluta
5. Desviacion Absoluta mediana de la mediana
6. Rango
7. Estadisticos Ordinales
8. Percentil
9. Rango intercuartil

### Exploracion de la distribucion de Datos.[¶](broken-reference) <a href="#exploracion-de-la-distribucion-de-datos" id="exploracion-de-la-distribucion-de-datos"></a>

Se vuelve importante explora como se distribuyen los datos en general:

1. Diagrama de Caja y Bigotes.

Es una representación gráfica que resume la distribución de un conjunto de datos. Muestra de manera visual cinco números clave:

* Mínimo: El valor más pequeño del conjunto de datos.
* Primer cuartil (Q1): Separa el 25% inferior de los datos.
* Mediana (Q2): El valor central de los datos, que divide el conjunto en dos partes iguales.
* Tercer cuartil (Q3): Separa el 75% inferior de los datos.
* Máximo: El valor más grande del conjunto de datos.

La "caja" representa el rango intercuartílico (IQR), es decir, la diferencia entre el tercer y el primer cuartil. Los "bigotes" se extienden desde la caja hasta los valores mínimo y máximo, a menos que haya valores atípicos (outliers), en cuyo caso los bigotes se extienden hasta un valor máximo definido (generalmente 1.5 veces el IQR por encima de Q3 o por debajo de Q1).

* ¿Para qué sirve?
* Visualizar la distribución de los datos: Identificar si los datos están sesgados, si hay valores atípicos, etc.
* Comparar distribuciones: Comparar la distribución de diferentes grupos de datos.
* Detectar valores atípicos: Identificar valores que se encuentran muy alejados del resto de los datos.

#### Exploracion de Datos Binarios y Categoricos[¶](broken-reference) <a href="#exploracion-de-datos-binarios-y-categoricos" id="exploracion-de-datos-binarios-y-categoricos"></a>

en el caso de los datos bianarios y categoricos podemos usar proporciones simples para identificar el comportamiento de los mismos

1. Moda
2. Valor esperado
3. Graficos de Barras
4. Graficos de torta
5. Analisis porcentuales

#### Analisis de correlaciones[¶](broken-reference) <a href="#analisis-de-correlaciones" id="analisis-de-correlaciones"></a>

los analisis de correlacion son analisis que se realizan en tre variables, intentado identificar patrones de pertinencia o dependencia, ya sea ente variables predictorias, o varoibales predictorias y varibale objetivo, partiendo de la premisa de que cada par de datos X y Y estan relacionados de alguna manera ya sea positivamente o negativamente.

1. coeficiente de correlacion
2. Matriz de correlacion
3. Diagrama de dispersion

La correlación es una medida estadística que indica la fuerza y dirección de la relación lineal entre dos variables numéricas. En otras palabras, nos dice si al aumentar una variable, la otra tiende a aumentar (correlación positiva), disminuir (correlación negativa) o si no existe una relación lineal aparente (correlación cercana a cero).

**Elementos clave en el análisis de correlación:**[**¶**](broken-reference)

1. Coeficiente de correlación: Un valor numérico entre -1 y 1 que cuantifica la fuerza y dirección de la relación lineal.

* Cerca de 1: Correlación positiva fuerte.
* Cerca de -1: Correlación negativa fuerte.
* Cerca de 0: No hay correlación lineal.

2. Matriz de correlación: Una tabla que muestra los coeficientes de correlación entre todas las variables numéricas de un conjunto de datos.
3. Diagrama de dispersión: Una gráfica que muestra los puntos de datos para dos variables numéricas, permitiendo visualizar la relación entre ellas.

### Conectividad Google Colab online y CSV.[¶](broken-reference) <a href="#conectividad-google-colab-online-y-csv" id="conectividad-google-colab-online-y-csv"></a>

Si estas trabajando con jupyter notebook de forma offline, es posible la conexion local del servicio MySql - workbench con jupyter notebook pero para aquellas personas que prefieren trabajar en la nube de google drive, es preferible el manejo de datos desde archivos .CSV y Sheets o en su defecti sistemas de BD que permitan esta interfaz como el mismo sistema de google cloud.

ahora explicaremos el paso a paso que se debe llevar para poder generar valor con los datos idependiente del sistema de analisis que se este ejecutando, sumando un componente de machine learning o entrenamiento del proceso para generacion de informacion.

#### Proceso Sistemático de Análisis de Datos y Machine Learning con Python[¶](broken-reference) <a href="#proceso-sistem-c3-a1tico-de-an-c3-a1lisis-de-datos-y-machine-learning-con-python" id="proceso-sistem-c3-a1tico-de-an-c3-a1lisis-de-datos-y-machine-learning-con-python"></a>

A través de este enfoque, se busca proporcionar una guía clara y concisa para aquellos interesados en aplicar técnicas de análisis y aprendizaje automático en sus proyectos.

### Subconsultas y Consultas Multitablas[¶](broken-reference) <a href="#subconsultas-y-consultas-multitablas" id="subconsultas-y-consultas-multitablas"></a>

**¿Qué son las subconsultas y las consultas multitabla?**

1. Subconsultas: Son consultas anidadas dentro de otra consulta. Se utilizan para obtener un conjunto de resultados que luego se utilizan como un valor en la consulta externa.
2. Consultas multitabla: Combinan datos de dos o más tablas en una sola consulta, utilizando diferentes tipos de uniones (JOIN).

***

**Tipos de uniones en consultas multitabla**

1. INNER JOIN: Devuelve los registros que tienen valores coincidentes en las columnas especificadas de ambas tablas.
2. LEFT JOIN: Devuelve todos los registros de la tabla izquierda y los registros coincidentes de la tabla derecha. Si no hay coincidencia, los valores de la tabla derecha serán NULL. &#x20;
3. RIGHT JOIN: Lo contrario de LEFT JOIN. Devuelve todos los registros de la tabla derecha y los registros coincidentes de la tabla izquierda.
4. FULL OUTER JOIN: Devuelve todos los registros cuando hay una coincidencia en alguna de las tablas. &#x20;

Fuente: 1. www.studocu.com 2. www.thedataschools.com

definicion 2: Una subconsulta es una consulta dentro de otra consulta. Se utiliza para realizar operaciones que dependen de los resultados de otra consulta. Aquí tienes un ejemplo básico:

ejemplo:

### Funciones y operadores en SQL[¶](broken-reference) <a href="#funciones-y-operadores-en-sql" id="funciones-y-operadores-en-sql"></a>

Imagina que MySQL es un idioma para hablar con tu base de datos. Al igual que en cualquier idioma, necesitas palabras (operadores) y frases (funciones) para expresar ideas y realizar acciones.

**Operadores:** Son símbolos que realizan operaciones específicas sobre los datos, como sumar, restar, comparar, etc.

**Funciones:** Son como mini-programas predefinidos que realizan tareas más complejas, como calcular la longitud de una cadena, encontrar el valor máximo de una columna, etc.

* Tipos de Operadores

MySQL ofrece una amplia gama de operadores para manipular datos:

1. Aritméticos: +, -, \*, /, % (módulo). Se utilizan para realizar cálculos numéricos.
2. Comparación: =, !=, <, >, <=, >=. Se utilizan para comparar valores.
3. Lógicos: AND, OR, NOT. Se utilizan para combinar condiciones.
4. De conjunto: IN, NOT IN, BETWEEN, LIKE. Se utilizan para comparar valores con conjuntos o patrones.
5. De bits: &, |, ^, \~. Se utilizan para realizar operaciones a nivel de bits.

**Funciones de Agrupamiento y Ventanas**[**¶**](broken-reference)

Funciones de agrupamiento **(GROUP BY):**

Te permiten agrupar filas de una tabla según uno o más valores de columna. Combinadas con funciones de agregación (COUNT, SUM, AVG, etc.), se puede calcular estadísticas para cada grupo.

* Ejemplo:

Obtener el número de pedidos por cliente:

### Conceptos Basicos de Process Mining[¶](broken-reference) <a href="#conceptos-basicos-de-process-mining" id="conceptos-basicos-de-process-mining"></a>

El Process Mining, o minería de procesos, es una técnica que utiliza algoritmos especializados para analizar los datos de registro de eventos y descubrir patrones, tendencias y detalles de cómo se desarrolla un proceso. En otras palabras, es como una "radiografía" de tus procesos de negocio, que te permite ver cómo funcionan realmente y dónde hay oportunidades de mejora.

**Pasos básicos para realizar Process Mining en MySQL Workbench:**[**¶**](broken-reference)

1. Preparación de los datos:

* Estructura de la tabla: Asegúrate de que tus datos de eventos estén almacenados en una tabla con campos como:
* event\_id: Identificador único de cada evento.
* case\_id: Identificador del caso al que pertenece el evento.
* activity: Nombre de la actividad.
* timestamp: Fecha y hora en que ocurrió el evento.
* Otros campos relevantes para tu proceso (usuario, sistema, etc.).
* Limpieza de datos: Verifica que los datos estén completos, consistentes y libres de errores.

2. Consultas SQL:
3. Secuencias de eventos:

Ejemplo: SELECT case\_id, GROUP\_CONCAT(activity ORDER BY timestamp) AS secuencia FROM tabla\_eventos GROUP BY case\_id;

2. Tiempos de ciclo:

Ejemplo: SELECT case\_id, TIMEDIFF(MAX(timestamp), MIN(timestamp)) AS tiempo\_ciclo FROM tabla\_eventos GROUP BY case\_id;

3. Cuellos de botella:

Ejemplo: SELECT activity, COUNT(\*) AS cantidad\_de\_eventos, AVG(TIMEDIFF(end\_timestamp, start\_timestamp)) AS tiempo\_promedio FROM tabla\_eventos GROUP BY activity ORDER BY tiempo\_promedio DESC;

3. Visualización:
4. Exportar resultados: Exporta los resultados de tus consultas a un archivo CSV o una hoja de cálculo. Herramientas de visualización: Utiliza herramientas como Excel, Google Sheets o Power BI para crear gráficos y diagramas que representen tus datos.

### 1. Introduccion A Los Dasboard:[¶](broken-reference) <a href="#id-1.-introduccion-a-los-dasboard" id="id-1.-introduccion-a-los-dasboard"></a>

* Que Es Un Dashboard?

***

es una herramienta visual que permite monitorear, analizar y presentar información clave de manera centralizada, facilitando la toma de decisiones informada. En un contexto de negocios o industrial, un tablero muestra métricas importantes, KPIs (Key Performance Indicators) y otros datos relevantes en tiempo real, organizados en gráficos, tablas, y otros elementos visuales que simplifican la comprensión de la información

***

**Jupyter Notebook:** Esta herramienta es ideal para científicos de datos y analistas debido a su naturaleza interactiva. Permite combinar código (Python), visualizaciones y texto explicativo en un mismo documento. Esto facilita la exploración de datos, el desarrollo de modelos y la creación de prototipos de dashboards.

#### Dashboard en la Gestion de Inventario:[¶](broken-reference) <a href="#dashboard-en-la-gestion-de-inventario" id="dashboard-en-la-gestion-de-inventario"></a>

**Beneficios de los dashboards en la gestión de inventario**

1. Toma de decisiones más rápida: Al tener una visión clara del estado de tu inventario, podrás identificar rápidamente problemas como faltantes de stock, productos obsoletos o sobreproducción.
2. Mejora de la eficiencia: Un dashboard te permite monitorear el rendimiento de tu inventario en tiempo real, lo que te ayudará a optimizar los procesos y reducir costos.
3. Mayor precisión en los pronósticos: Al analizar datos históricos y tendencias, podrás realizar pronósticos más precisos sobre la demanda futura.
4. Mejor colaboración: Un dashboard puede ser compartido con diferentes equipos (compras, ventas, producción) para facilitar la comunicación y la colaboración.

### 2. Construccion de un Dashboard.[¶](broken-reference) <a href="#id-2.-construccion-de-un-dashboard" id="id-2.-construccion-de-un-dashboard"></a>

empezaremos por la instalacion de los elementos necesarios para poder crear el dashboard:

1. instalación de librerías

Si aún no tienes instalado Plotly Dash, podemos comenzar por ahí. Necesitaremos las siguientes librerías:

Dash: La librería principal para crear aplicaciones web interactivas. Plotly: Para generar los gráficos. Dash Core Components: Proporciona componentes HTML para la interfaz de usuario. Dash HTML Components: Define los componentes HTML básicos. Pandas: Para manipular los datos.
