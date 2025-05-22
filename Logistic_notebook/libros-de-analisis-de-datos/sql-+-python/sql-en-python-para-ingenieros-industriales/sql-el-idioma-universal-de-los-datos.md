# SQL - El Idioma Universal de los Datos

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
