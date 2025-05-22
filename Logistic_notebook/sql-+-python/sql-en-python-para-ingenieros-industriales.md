# SQL en Python para Ingenieros Industriales

### Aprende a Usar SQL en Python y Domina Datos como un Experto

Una Charla Esencial para Ingenieros Industriales del Futuro

### El Ingeniero Industrial en la Era de los Datos

"Los datos son el nuevo petróleo" (Clive Humby). Para la Ingeniería Industrial, esto significa una revolución en la optimización de procesos, la toma de decisiones basada en evidencia, la mejora continua y la Industria 4.0.

El ingeniero industrial moderno no solo diseña y gestiona sistemas, sino que también analiza e interpreta la vasta cantidad de datos que estos generan.

**Objetivo Hoy:** Mostrarte cómo SQL y Python son tus aliados estratégicos para convertir datos en decisiones inteligentes y acciones efectivas.

### Agenda de la Sesión

* **El Universo de los Datos:** Bases de Datos Esenciales (Relacionales SQL vs. No Relacionales NoSQL).
* **SQL:** El Idioma Universal para Consultar Datos (Comandos clave para el análisis).
* **Python al Mando:** Conectando Mundos y Potenciando el Análisis (Accediendo a BD, Entornos Jupyter y VS Code).
* **Análisis de Datos Nivel Experto:** SQL + Python en Acción (Casos de uso en Ingeniería Industrial).
* **Conclusión y Tus Próximos Pasos** (Recursos y Q\&A).

### Parte 1: El Universo de los Datos

Esta sección explora los fundamentos de las bases de datos, su importancia crítica para la ingeniería industrial y las diferencias clave entre los modelos relacionales (SQL) y no relacionales (NoSQL), ayudándote a comprender cuándo y por qué elegir cada uno.

### ¿Qué es una Base de Datos?

Un sistema organizado para almacenar, gestionar y recuperar datos de forma eficiente y segura. Piénsalo como el cerebro digital de cualquier operación industrial.

**Importancia Crítica para el Ingeniero Industrial:** Fuente de verdad para la producción, calidad, inventario, mantenimiento, etc. Base para el análisis, la modelización y la simulación.

### Bases de Datos Relacionales (SQL)

Organizan los datos en **tablas** estructuradas (como hojas de cálculo interconectadas).

**Componentes:** Filas (registros), Columnas (atributos), Esquemas.

**Relaciones:** Se establecen mediante **Llaves Primarias** (identificador único por fila) y **Llaves Foráneas** (campos que enlazan tablas).

**Lenguaje:** SQL (Structured Query Language) – El estándar para interactuar con ellas.

#### Ventajas para la Ing. Industrial:

* **Integridad de Datos:** Asegura consistencia y precisión.
* **Estandarización:** Modelo bien definido y maduro.
* **Transaccionalidad (ACID):** Ideal para sistemas críticos (ERP, MES).

**Ejemplos:** MySQL, PostgreSQL, SQL Server, Oracle.

### Bases de Datos No Relacionales (NoSQL)

Ofrecen modelos de datos más flexibles, no limitados a la estructura tabular.

#### Tipos Principales:

* **Documentales (Ej: MongoDB):** Datos en documentos JSON/BSON. Útil para catálogos, configuraciones.
* **Clave-Valor (Ej: Redis):** Pares clave-valor. Ideal para caché, sesiones.
* **Columnares (Ej: Cassandra):** Optimizadas para consultas sobre columnas específicas. Para series temporales (IoT).
* **Grafos (Ej: Neo4j):** Enfocadas en relaciones complejas. Para cadenas de suministro, redes.

#### Ventajas para la Ing. Industrial:

* **Escalabilidad Horizontal:** Manejan grandes volúmenes de datos (Big Data, IoT).
* **Flexibilidad de Esquemas:** Adaptables a datos variados.
* **Rendimiento Específico:** Rápidas para ciertas cargas.

### SQL vs. NoSQL: La Decisión Estratégica

No es una competencia, es complementariedad. La elección depende de las necesidades específicas del proyecto.

#### Usa SQL cuando:

* La integridad de los datos y las relaciones complejas son cruciales.
* Los datos son estructurados y consistentes.
* Necesitas transacciones ACID (Ej: control de inventario).

#### Usa NoSQL cuando:

* Manejas grandes volúmenes de datos diversos (IoT, sensores).
* Necesitas alta velocidad y escalabilidad masiva.
* El esquema de datos es dinámico.

Realidad Industrial: ¡A menudo se utilizan arquitecturas híbridas!

### Parte 2: SQL - El Idioma Universal de los Datos

SQL (Structured Query Language) es el lenguaje estándar para interactuar con bases de datos relacionales. Esta sección detalla los comandos esenciales que todo ingeniero industrial debe conocer para extraer y manipular datos operativos eficazmente.

SQL te permite:

* **Consultar (Leer):** Extraer la información que necesitas.
* **Manipular (Escribir):** Insertar, actualizar y borrar datos.
* **Definir (Crear):** Estructurar la base de datos (crear tablas, etc.).

Para el ingeniero industrial, dominar las consultas SQL es fundamental para acceder a los datos operativos.

### Comandos SQL Clave para el Ingeniero Industrial

SELECT Campos FROM Tabla;

Elige qué columnas quieres ver de qué tabla. Ej: `SELECT NombreProducto, StockActual FROM Inventario;`

WHERE Condicion;

Filtra los resultados. Tu herramienta para encontrar problemas o datos específicos. Ej: `SELECT IDMaquina FROM Sensores WHERE Temperatura > 90;` (Máquinas sobrecalentadas)

JOIN;

Combina datos de múltiples tablas relacionadas. Esencial para una visión integral. Ej: `SELECT O.IDOrden, P.NombreProducto FROM Ordenes O JOIN Productos P ON O.IDProducto = P.IDProducto;`

GROUP BY Campo;

Agrupa filas que tienen los mismos valores en ciertos campos. Se usa con funciones de agregación. Ej: `SELECT LineaProduccion, AVG(Eficiencia) FROM DatosProduccion GROUP BY LineaProduccion;` (Eficiencia promedio por línea)

Funciones de Agregación:

`COUNT()` (contar), `SUM()` (sumar), `AVG()` (promedio), `MAX()` (máximo), `MIN()` (mínimo).

ORDER BY Campo \[ASC|DESC];

Ordena los resultados.

**Enfoque:** Entender \*qué hacen\* estos comandos y \*por qué\* son vitales para extraer insights de los datos de planta, calidad, etc.

### Parte 3: Python al Mando - Conectando Mundos

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

```
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

```
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

### Parte 4: Análisis de Datos Nivel Experto - SQL + Python en Acción

La combinación de SQL para la extracción eficiente de datos y Python (con Pandas) para el análisis avanzado y la visualización, crea una sinergia poderosa. Esta sección presenta casos de uso prácticos en ingeniería industrial donde esta combinación brilla.

### La Sinergia Perfecta

* **SQL:** Extracción eficiente y filtrado de grandes volúmenes de datos desde la fuente.
* **Python (con Pandas):** Limpieza profunda, transformación, análisis estadístico avanzado, modelado predictivo y visualización.

#### Flujo de Trabajo Típico:

1. Definir el Problema.
2. Identificar Datos.
3. Extraer con SQL.
4. Cargar en Python (Pandas).
5. Explorar, Limpiar y Transformar.
6. Analizar y Modelar.
7. Visualizar.
8. Actuar.

### Caso de Uso 1: Análisis de Rendimiento de Producción

**Objetivo:** Identificar cuellos de botella y mejorar la eficiencia (OEE) de una línea de producción.

**Datos Necesarios:** Tiempos de ciclo, unidades producidas/defectuosas, tiempos de parada.

#### Paso 1: Extracción con SQL (Ejemplo conceptual)

```
SELECT 
    p.Fecha, p.IDEstacion, p.TiempoCiclo, p.UnidadesProducidas,
    m.DuracionParada, m.CausaParada
FROM DatosProduccion p
LEFT JOIN DatosParadas m ON p.IDEstacion = m.IDEstacion AND p.Fecha = m.Fecha
WHERE p.Fecha BETWEEN '2024-04-01' AND '2024-04-30';
```

#### Paso 2: Análisis con Python (Pandas)

* Cargar datos en DataFrame.
* Calcular OEE (Disponibilidad \* Rendimiento \* Calidad).
* Identificar estaciones con bajo OEE.
* Analizar causas de parada.
* **Visualizar:** Gráficos de tendencias de OEE, diagramas de Pareto. (Aquí iría un chart container)

Espacio para gráfico de OEE / Pareto de Paradas (Ej: Usando Chart.js)

**Impacto:** Decisiones informadas para mejora, optimizar mantenimiento, reducir tiempos muertos.

### Caso de Uso 2: Optimización de Inventarios

**Objetivo:** Reducir costos de inventario manteniendo un nivel de servicio adecuado.

**Datos Necesarios:** Niveles de stock, historial de demanda, tiempos de entrega.

#### Paso 1: Extracción con SQL (Ejemplo conceptual)

```
SELECT IDProducto, FechaVenta, CantidadVendida
FROM HistorialVentas
WHERE FechaVenta >= DATE_SUB(CURDATE(), INTERVAL 1 YEAR);
```

#### Paso 2: Análisis con Python (Pandas, NumPy)

* Cargar datos en DataFrames.
* Calcular estadísticas de demanda.
* Determinar Puntos de Reorden (ROP) y Stocks de Seguridad.
* (Opcional avanzado): Aplicar modelos de pronóstico de demanda.
* **Visualizar:** Niveles de stock vs. demanda, proyecciones. (Aquí iría un chart container)

Espacio para gráfico de Niveles de Stock / Demanda (Ej: Usando Chart.js)

**Impacto:** Reducción de capital inmovilizado, minimización de obsolescencia, prevención de roturas de stock.

### Importancia del Manejo de Datos para el Ingeniero Industrial

* **Toma de Decisiones Basada en Datos:** De la intuición a la evidencia.
* **Eficiencia Operativa:** Identificar y eliminar desperdicios, optimizar flujos, reducir costos.
* **Mejora de la Calidad:** Monitorear procesos, detectar anomalías, implementar acciones correctivas.
* **Innovación:** Descubrir patrones ocultos, oportunidades de mejora.
* **Competitividad:** Las empresas que utilizan sus datos lideran.

¡Tú, como ingeniero industrial, eres clave en esta transformación digital!

### Conclusión y Próximos Pasos

Hemos recorrido el camino desde los fundamentos de las bases de datos hasta aplicaciones prácticas de SQL y Python en la ingeniería industrial. Ahora es tu turno de tomar estos conocimientos y aplicarlos.

### Resumen Clave

* Las bases de datos (SQL y NoSQL) son fundamentales en la industria.
* SQL es tu herramienta para extraer datos de manera precisa.
* Python, con bibliotecas como Pandas, es tu laboratorio para analizar, modelar y visualizar.
* Jupyter Notebook y VS Code son entornos que facilitan tu trabajo.

El Dúo Dinámico (SQL + Python): Te empodera para pasar de ser un observador de datos a un arquitecto de soluciones basadas en datos.

#### Llamada a la Acción:

* ¡Empieza a explorar! La curva de aprendizaje es accesible.
* Busca pequeños proyectos en tu entorno donde puedas aplicar estos conocimientos.

### Recursos para Seguir Aprendiendo

#### SQL:

* SQLZoo (interactivo)
* W3Schools SQL Tutorial
* Khan Academy - SQL

#### Python para Análisis de Datos:

* Documentación oficial de Pandas, NumPy, Matplotlib.
* Tutoriales en Real Python, DataCamp (cursos introductorios gratuitos), Kaggle Learn.
* Libro: "Python for Data Analysis" de Wes McKinney.

Práctica, Práctica, Práctica: La mejor forma de aprender es haciendo.

### ¡Gracias!

¿Preguntas?
