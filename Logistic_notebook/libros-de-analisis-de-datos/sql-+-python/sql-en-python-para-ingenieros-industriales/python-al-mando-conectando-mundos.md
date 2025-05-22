# Python al Mando - Conectando Mundos

Python se ha convertido en una herramienta indispensable para el análisis de datos en la ingeniería industrial gracias a su simplicidad y su potente ecosistema de bibliotecas. Aquí exploraremos cómo Python se conecta a bases de datos y los entornos de trabajo más comunes.

### ¿Por qué Python para el Análisis de Datos Industriales?

* **Sintaxis Sencilla y Legible:** Fácil de aprender y usar.
* **Ecosistema Poderoso:** Bibliotecas especializadas como:
  * **Pandas:** Manipulación y análisis de datos tabulares.
  * **NumPy:** Cálculo numérico.
  * **Matplotlib/Seaborn:** Visualización de datos.
  * **Scikit-learn:** Machine Learning (mantenimiento predictivo, control de calidad).
* **Versatilidad:** Desde simples scripts hasta aplicaciones complejas.

### Python + SQL: Conexión a Bases de Datos Relacionales

Python te permite ejecutar queries SQL y traer los resultados a tu entorno de análisis.

**Bibliotecas Comunes (Drivers):** \`sqlite3\`, \`psycopg2\` (PostgreSQL), \`mysql.connector\` (MySQL), \`pyodbc\`.

#### Flujo Básico de Trabajo:

1. **Importar** la biblioteca.
2. **Conectar** a la base de datos (cadena de conexión).
3. Crear un **Cursor**.
4. **Ejecutar** consulta SQL.
5. **Recuperar** resultados (ej: \`fetchall()\`, o cargar a Pandas con \`pd.read\_sql\_query()\`).
6. **Cerrar** la conexión.

Ejemplo de código:

```python
import sqlite3
import pandas as pd

# Conectar a la base de datos (o crearla si no existe)
conn = sqlite3.connect('mi_base_industrial.db')

# Ejemplo: Crear una tabla e insertar datos (esto se haría una vez)
# conn.execute('''CREATE TABLE IF NOT EXISTS Sensores (
#                    id INTEGER PRIMARY KEY, timestamp TEXT, temperatura REAL)''')
# conn.execute("INSERT INTO Sensores (timestamp, temperatura) VALUES ('2024-05-21 10:00', 25.5)")
# conn.commit() # Guardar cambios

# Consultar datos y cargarlos en un DataFrame de Pandas
query = "SELECT timestamp, temperatura FROM Sensores WHERE temperatura > 20;"
df_sensores = pd.read_sql_query(query, conn)

print(df_sensores.head())

# Cerrar la conexión
conn.close()
```

### Python + NoSQL: Un Vistazo

Cada tipo de base de datos NoSQL tiene su propia forma de interactuar y su biblioteca Python específica.

**Ejemplo con MongoDB y \`pymongo\`:**

* Conectar al servidor MongoDB.
* Seleccionar la base de datos y la "colección".
* Usar métodos como \`find()\`, \`insert\_one()\`, \`update\_many()\`.
* Las "consultas" se hacen a menudo con diccionarios Python.

```mongodb
# from pymongo import MongoClient
# client = MongoClient('mongodb://localhost:27017/')
# db = client['base_iot']
# coleccion_sensores = db['lecturas_temperatura']
# for lectura in coleccion_sensores.find({'valor': {'$gt': 30}}):
#     print(lectura)
```

### Entornos de Trabajo del Ingeniero de Datos

#### Jupyter Notebook / JupyterLab:

**Ideal para:** Exploración interactiva, prototipado rápido, documentación (código, texto, visualizaciones).

**Ventajas:** Visualización inmediata, fácil de compartir, excelente para aprender.

#### Visual Studio Code (VS Code):

**Ideal para:** Scripts robustos, proyectos grandes, automatización.

**Ventajas:** Potente editor, depuración, Git, terminal. Extensiones para BD.

Ambos son excelentes y pueden usarse de forma complementaria.
