# SQL - Universal Data language

SQL (Structured Query Language) is the standard language for interacting with relational databases. This section details the essential commands every industrial engineer should know to efficiently extract and manipulate operational data.

SQL allows you to:

* **Consult (Read):** Extract the
* **Manipulate (Write):** Insert, update, and delete data
* **Define (Create):** Structure the database (create tables)

For the industrial engineer, mastering SQL queries is essential for accessing the operational Data

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
