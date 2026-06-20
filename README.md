# Diseño de Base de Datos – Entrega Proyecto Final

## Arquitectura híbrida de datos para Ecommify

Repositorio  correspondiente a la entrega final del proyecto Diseño de Base de Datos.

El proyecto presenta el diseño, implementación, validación y optimización de una arquitectura híbrida de bases de datos para Ecommify, una plataforma de comercio electrónico orientada a productos tecnológicos. La solución combina PostgreSQL/Supabase como motor relacional transaccional y MongoDB Atlas como motor documental para escenarios flexibles, agregados y de alta disponibilidad.

---

## Tabla de contenido

1. Resumen ejecutivo
2. Objetivo del proyecto
3. Alcance funcional y técnico
4. Arquitectura híbrida implementada
5. Tecnologías utilizadas
6. Estructura del repositorio
7. Descripción de carpetas y archivos
8. Requisitos previos
9. Cómo clonar el repositorio
10. Cómo ejecutar los scripts PostgreSQL
11. Cómo ejecutar los scripts MongoDB
12. Cómo ejecutar los notebooks de Colab
13. Resultados principales
14. Análisis PostgreSQL vs MongoDB
15. Análisis CAP aplicado
16. Lecciones aprendidas
17. Recomendaciones estratégicas
18. Consideraciones importantes
19. Autor

---

## Resumen ejecutivo

Ecommify requiere gestionar información transaccional, analítica y documental propia de una plataforma de comercio electrónico. Para responder a estas necesidades, se diseñó una arquitectura híbrida donde cada motor de base de datos cumple un rol especializado:

* PostgreSQL/Supabase se utiliza como núcleo transaccional para pedidos, pagos, clientes, productos base, vendedores, ítems de pedido, reseñas estructuradas y geolocalización.
* MongoDB Atlas se utiliza como capa documental para catálogo extendido, reseñas enriquecidas, perfiles consolidados de cliente, documentos agregados y vistas orientadas a lectura.
* Se implementaron scripts de optimización, particionamiento, validación, consultas críticas y pruebas comparativas.
* Se documentaron decisiones técnicas, trade-offs del Teorema CAP, resultados de rendimiento y recomendaciones de escalamiento.

La arquitectura permite aprovechar las fortalezas de cada tecnología, separando cargas transaccionales, analíticas y documentales, y mejorando el rendimiento, la escalabilidad y la disponibilidad de la solución.

---

## Objetivo del proyecto

Diseñar e implementar una arquitectura híbrida de bases de datos para Ecommify que permita gestionar datos transaccionales y documentales, garantizando:

* Consistencia transaccional.
* Integridad referencial.
* Rendimiento en consultas críticas.
* Escalabilidad ante crecimiento de datos.
* Flexibilidad para información semiestructurada.
* Alta disponibilidad para escenarios documentales.
* Capacidad de análisis sobre datos históricos.

---

## Alcance funcional y técnico

El proyecto cubre los siguientes frentes:

* Diseño de arquitectura híbrida PostgreSQL + MongoDB.
* Modelado relacional para el núcleo transaccional.
* Modelado documental para datos flexibles y agregados.
* Definición de diagramas de arquitectura y modelos ER/documentales.
* Creación de scripts SQL para consultas críticas, índices, particionamiento y validaciones.
* Creación de scripts MongoDB para consultas, inserciones, actualizaciones y agregaciones.
* Validación de rendimiento antes/después mediante consultas críticas.
* Análisis del Teorema CAP por módulo funcional.
* Comparación técnica entre PostgreSQL y MongoDB.
* Documentación ejecutiva y presentación del proyecto.

---

## Arquitectura híbrida implementada

La solución se divide en dos motores principales:

### PostgreSQL / Supabase

PostgreSQL se posiciona como la fuente transaccional confiable del negocio. Es el motor recomendado para:

* Pedidos.
* Pagos.
* Inventario.
* Clientes.
* Productos base.
* Vendedores.
* Ítems de pedido.
* Reseñas estructuradas.
* Geolocalización base.

Su uso se justifica por sus capacidades ACID, integridad referencial, soporte de consultas SQL complejas, particionamiento, índices especializados y validación de planes de ejecución.

### MongoDB Atlas

MongoDB se posiciona como capa documental complementaria. Es el motor recomendado para:

* Catálogo extendido.
* Reseñas enriquecidas.
* Perfiles consolidados de cliente.
* Comportamiento de usuarios.
* Documentos agregados de pedidos.
* Métricas analíticas preprocesadas.
* Logs o eventos de navegación.

Su uso se justifica por la flexibilidad de documentos, facilidad para atributos variables, agregaciones, lecturas rápidas y disponibilidad mediante réplica set.

---

## Tecnologías utilizadas

| Categoría                | Tecnología                                          |
| ------------------------ | --------------------------------------------------- |
| Base de datos relacional | PostgreSQL / Supabase                               |
| Base de datos documental | MongoDB Atlas                                       |
| Lenguaje SQL             | PostgreSQL SQL / PLpgSQL                            |
| Scripts documentales     | JavaScript para MongoDB Shell                       |
| Notebooks                | Google Colab / Jupyter Notebook                     |
| Modelado                 | Diagramas ER y modelo documental                    |
| Análisis de rendimiento  | EXPLAIN, ANALYZE, BUFFERS                           |
| Optimización             | Índices, particionamiento, reescritura de consultas |
| Evidencias               | Imágenes, documento PDF y presentación PDF          |

---

## Estructura del repositorio

```text
Dise-o-de-Base-De-Datos-Entrega-proyecto-Final/
│
├── Arquitectura de la solución/
│   ├── Arquitectura de la solución.png
│   ├── Modelo ER Mongo.png
│   └── Modelo ER Postgresql.png
│
├── Documento del proyecto entregable/
│   └── Entrega Proyecto Final.pdf
│
├── Evidencias Imagenes/
│   ├── Ev1.png
│   ├── Ev2.png
│   ├── Ev3.png
│   ├── Ev4.png
│   ├── Ev5.png
│   ├── Ev6.png
│   ├── Ev7.png
│   ├── Ev8.png
│   ├── Ev9.png
│   └── Ev10.png
│
├── Presentación/
│   └── Presentacion_Entrega Proyecto Final.pdf
│
├── Scripts de la solución/
│   ├── Colab/
│   │   ├── Unidad_5_Act_2.ipynb
│   │   └── Unidad_5_Act_2_1.ipynb
│   │
│   ├── Scripts Mongo/
│   │   ├── ecommify_mongodb_crud_operations.js
│   │   └── mongodb_order_schema.json
│   │
│   └── Scripts Postgresql/
│       ├── 00_all_queries_criticos_optimizados.sql
│       ├── 00_all_queries_criticos_optimizados_explain_analyze.sql
│       ├── 01_create_orders_partitioned_table.sql
│       ├── 02_create_orders_monthly_partitions.sql
│       ├── 03_create_orders_default_partition.sql
│       ├── 04_create_partition_indexes.sql
│       ├── 05_create_future_partitions_function.sql
│       ├── 06_execute_future_partitions_function.sql
│       ├── 07_schedule_future_partitions_pg_cron.sql
│       ├── 08_migrate_orders_to_partitioned.sql
│       ├── 09_validate_migration_counts.sql
│       ├── 10_validate_orders_partitions.sql
│       ├── 11_validate_default_partition.sql
│       ├── 12_validate_distribution_by_partition.sql
│       ├── 13_compare_q03_without_partitioning.sql
│       ├── 14_compare_q03_with_partitioning.sql
│       ├── 15_compare_q04_without_partitioning.sql
│       ├── 16_compare_q04_with_partitioning.sql
│       ├── 17_compare_q05_without_partitioning.sql
│       ├── 18_compare_q05_with_partitioning.sql
│       ├── 19_measure_index_sizes.sql
│       ├── 20_measure_total_index_size.sql
│       ├── 21_rename_orders_after_validation.sql
│       └── create_ecommify_indexes.sql
│
└── README.md
```

---

## Descripción de carpetas y archivos

### Arquitectura de la solución

| Archivo                           | Descripción                                                                                                                                                                                |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Arquitectura de la solución.png` | Diagrama general de la arquitectura híbrida de datos de Ecommify. Representa la separación entre capas de operación, datos relacionales, datos documentales, integración y observabilidad. |
| `Modelo ER Mongo.png`             | Modelo conceptual/documental de MongoDB, mostrando colecciones y relaciones lógicas entre documentos.                                                                                      |
| `Modelo ER Postgresql.png`        | Diagrama entidad-relación del modelo relacional implementado en PostgreSQL. Representa clientes, pedidos, pagos, productos, vendedores, reseñas, ítems de pedido y geolocalización.        |

### Documento del proyecto entregable

| Archivo                      | Descripción                                                                                                                                                                                                                                                                                                    |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Entrega Proyecto Final.pdf` | Documento completo del proyecto. Incluye contexto, objetivos, arquitectura híbrida, matriz de decisión PostgreSQL vs MongoDB, análisis CAP, implementación PostgreSQL, implementación MongoDB, pruebas de rendimiento, resultados, lecciones aprendidas, plan de escalamiento, recomendaciones y conclusiones. |

### Evidencias Imagenes

| Archivo                | Descripción                                                                                                                                              |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Ev1.png` a `Ev10.png` | Evidencias gráficas del proceso de implementación, ejecución de consultas, resultados, diagramas, pruebas o validaciones realizadas durante el proyecto. |

### Presentación

| Archivo                                   | Descripción                                                                                                                                                                                                                                      |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Presentacion_Entrega Proyecto Final.pdf` | Presentación ejecutiva del proyecto final. Resume contexto, objetivos, arquitectura híbrida, decisiones técnicas, resultados de rendimiento, análisis PostgreSQL vs MongoDB, análisis CAP, lecciones aprendidas, recomendaciones y conclusiones. |

### Scripts de la solución / Colab

| Archivo                  | Descripción                                                                                                                             |
| ------------------------ | --------------------------------------------------------------------------------------------------------------------------------------- |
| `Unidad_5_Act_2.ipynb`   | Notebook de apoyo para procesamiento, análisis o validación de datos del proyecto. Puede ejecutarse en Google Colab o Jupyter Notebook. |
| `Unidad_5_Act_2_1.ipynb` | Notebook complementario para análisis, transformación, evidencia o validación adicional del proyecto.                                   |

### Scripts de la solución / Scripts Mongo

| Archivo                               | Descripción                                                                                                                                                   |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `ecommify_mongodb_crud_operations.js` | Script con operaciones MongoDB sobre colecciones como productos, pedidos, clientes y reseñas. Incluye consultas, agregaciones, inserciones y actualizaciones. |
| `mongodb_order_schema.json`           | Ejemplo de documento JSON para representar un pedido en MongoDB, incluyendo información del cliente, estado del pedido, fechas, ítems y pagos embebidos.      |

### Scripts de la solución / Scripts Postgresql

| Archivo                                                   | Descripción                                                                                                                                                                 |
| --------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `00_all_queries_criticos_optimizados.sql`                 | Consultas críticas optimizadas para escenarios de negocio como Order 360, Customer 360, ventas por período, riesgo logístico y entregas.                                    |
| `00_all_queries_criticos_optimizados_explain_analyze.sql` | Versión de consultas críticas con `EXPLAIN ANALYZE` para medir rendimiento y validar planes de ejecución.                                                                   |
| `01_create_orders_partitioned_table.sql`                  | Crea la tabla `orders_partitioned` particionada por rango sobre `order_purchase_timestamp`.                                                                                 |
| `02_create_orders_monthly_partitions.sql`                 | Crea particiones mensuales para la tabla de pedidos.                                                                                                                        |
| `03_create_orders_default_partition.sql`                  | Crea una partición `DEFAULT` para capturar registros fuera de rango.                                                                                                        |
| `04_create_partition_indexes.sql`                         | Crea índices asociados a la tabla particionada y sus patrones de consulta.                                                                                                  |
| `05_create_future_partitions_function.sql`                | Define una función para crear particiones futuras de forma automática.                                                                                                      |
| `06_execute_future_partitions_function.sql`               | Ejecuta la función de creación de particiones futuras.                                                                                                                      |
| `07_schedule_future_partitions_pg_cron.sql`               | Programa la creación automática de particiones mediante `pg_cron`.                                                                                                          |
| `08_migrate_orders_to_partitioned.sql`                    | Migra datos desde la tabla original `orders` hacia la tabla particionada.                                                                                                   |
| `09_validate_migration_counts.sql`                        | Valida conteos entre tabla original y tabla particionada.                                                                                                                   |
| `10_validate_orders_partitions.sql`                       | Valida existencia y estado de las particiones de pedidos.                                                                                                                   |
| `11_validate_default_partition.sql`                       | Revisa si existen registros almacenados en la partición `DEFAULT`.                                                                                                          |
| `12_validate_distribution_by_partition.sql`               | Mide la distribución de registros por partición.                                                                                                                            |
| `13_compare_q03_without_partitioning.sql`                 | Ejecuta comparación de la consulta Q03 sin particionamiento.                                                                                                                |
| `14_compare_q03_with_partitioning.sql`                    | Ejecuta comparación de la consulta Q03 con particionamiento.                                                                                                                |
| `15_compare_q04_without_partitioning.sql`                 | Ejecuta comparación de la consulta Q04 sin particionamiento.                                                                                                                |
| `16_compare_q04_with_partitioning.sql`                    | Ejecuta comparación de la consulta Q04 con particionamiento.                                                                                                                |
| `17_compare_q05_without_partitioning.sql`                 | Ejecuta comparación de la consulta Q05 sin particionamiento.                                                                                                                |
| `18_compare_q05_with_partitioning.sql`                    | Ejecuta comparación de la consulta Q05 con particionamiento.                                                                                                                |
| `19_measure_index_sizes.sql`                              | Mide el tamaño de índices relevantes.                                                                                                                                       |
| `20_measure_total_index_size.sql`                         | Mide el tamaño total ocupado por índices.                                                                                                                                   |
| `21_rename_orders_after_validation.sql`                   | Renombra tablas después de validar correctamente la migración hacia particionamiento. Debe ejecutarse únicamente cuando las validaciones sean exitosas.                     |
| `create_ecommify_indexes.sql`                             | Crea índices principales sobre tablas relacionales como `orders`, `order_items`, `order_payments`, `order_reviews`, `customers`, `products`, `sellers` y `geolocation_raw`. |

---

## Requisitos previos

### PostgreSQL

* PostgreSQL 14 o superior, o una instancia Supabase.
* Cliente SQL como DBeaver, pgAdmin, Supabase SQL Editor o `psql`.
* Esquema de base de datos llamado `ecommify`.
* Tablas base cargadas previamente:

  * `customers`
  * `orders`
  * `order_items`
  * `order_payments`
  * `order_reviews`
  * `products`
  * `sellers`
  * `geolocation_raw`
  * `product_category_name_translation`

### MongoDB

* MongoDB Atlas o MongoDB local.
* MongoDB Shell (`mongosh`) o MongoDB Compass.
* Base de datos sugerida: `EcommifyDB`.
* Colecciones sugeridas:

  * `products`
  * `orders`
  * `customers`
  * `reviews`

### Python / Colab

* Cuenta de Google para ejecutar notebooks en Google Colab.
* Python 3.x si se ejecutan los notebooks localmente.
* Librerías requeridas según las celdas del notebook.

---

## Cómo clonar el repositorio

```bash
git clone https://github.com/romergi1/Dise-o-de-Base-De-Datos-Entrega-proyecto-Final.git
cd Dise-o-de-Base-De-Datos-Entrega-proyecto-Final
```

Verificar estructura:

```bash
ls
```

En Windows PowerShell:

```powershell
dir
```

---

## Cómo ejecutar los scripts PostgreSQL

Los scripts PostgreSQL se encuentran en:

```text
Scripts de la solución/Scripts Postgresql/
```

### Opción 1: DBeaver, pgAdmin o Supabase SQL Editor

1. Abrir la conexión PostgreSQL o Supabase.
2. Confirmar que existe el esquema:

```sql
CREATE SCHEMA IF NOT EXISTS ecommify;
```

3. Confirmar que las tablas base ya están cargadas.
4. Abrir cada archivo `.sql`.
5. Ejecutar los scripts en el orden recomendado.
6. Validar resultados con las consultas de conteo y comparación.

### Opción 2: Terminal con `psql`

Formato general:

```bash
psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "RUTA_DEL_SCRIPT.sql"
```

### Orden recomendado de ejecución PostgreSQL

#### Paso 1: Crear índices generales

```bash
psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "Scripts de la solución/Scripts Postgresql/create_ecommify_indexes.sql"
```

#### Paso 2: Ejecutar consultas críticas optimizadas

```bash
psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "Scripts de la solución/Scripts Postgresql/00_all_queries_criticos_optimizados.sql"
```

#### Paso 3: Ejecutar consultas con análisis de rendimiento

```bash
psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "Scripts de la solución/Scripts Postgresql/00_all_queries_criticos_optimizados_explain_analyze.sql"
```

#### Paso 4: Crear tabla particionada de pedidos

```bash
psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "Scripts de la solución/Scripts Postgresql/01_create_orders_partitioned_table.sql"
```

#### Paso 5: Crear particiones mensuales

```bash
psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "Scripts de la solución/Scripts Postgresql/02_create_orders_monthly_partitions.sql"
```

#### Paso 6: Crear partición DEFAULT

```bash
psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "Scripts de la solución/Scripts Postgresql/03_create_orders_default_partition.sql"
```

#### Paso 7: Crear índices sobre particiones

```bash
psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "Scripts de la solución/Scripts Postgresql/04_create_partition_indexes.sql"
```

#### Paso 8: Crear y ejecutar función de particiones futuras

```bash
psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "Scripts de la solución/Scripts Postgresql/05_create_future_partitions_function.sql"

psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "Scripts de la solución/Scripts Postgresql/06_execute_future_partitions_function.sql"
```

#### Paso 9: Programar particiones futuras con pg_cron

```bash
psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "Scripts de la solución/Scripts Postgresql/07_schedule_future_partitions_pg_cron.sql"
```

Nota: este paso requiere tener habilitada la extensión `pg_cron`. En ambientes administrados como Supabase puede requerir configuración adicional o permisos específicos.

#### Paso 10: Migrar datos a tabla particionada

```bash
psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "Scripts de la solución/Scripts Postgresql/08_migrate_orders_to_partitioned.sql"
```

#### Paso 11: Validar migración y particiones

```bash
psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "Scripts de la solución/Scripts Postgresql/09_validate_migration_counts.sql"

psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "Scripts de la solución/Scripts Postgresql/10_validate_orders_partitions.sql"

psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "Scripts de la solución/Scripts Postgresql/11_validate_default_partition.sql"

psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "Scripts de la solución/Scripts Postgresql/12_validate_distribution_by_partition.sql"
```

#### Paso 12: Comparar rendimiento con y sin particionamiento

```bash
psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "Scripts de la solución/Scripts Postgresql/13_compare_q03_without_partitioning.sql"

psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "Scripts de la solución/Scripts Postgresql/14_compare_q03_with_partitioning.sql"

psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "Scripts de la solución/Scripts Postgresql/15_compare_q04_without_partitioning.sql"

psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "Scripts de la solución/Scripts Postgresql/16_compare_q04_with_partitioning.sql"

psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "Scripts de la solución/Scripts Postgresql/17_compare_q05_without_partitioning.sql"

psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "Scripts de la solución/Scripts Postgresql/18_compare_q05_with_partitioning.sql"
```

#### Paso 13: Medir tamaño de índices

```bash
psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "Scripts de la solución/Scripts Postgresql/19_measure_index_sizes.sql"

psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "Scripts de la solución/Scripts Postgresql/20_measure_total_index_size.sql"
```

#### Paso 14: Renombrar tablas después de validar

```bash
psql "postgresql://USUARIO:PASSWORD@HOST:PUERTO/BASE_DATOS" -v ON_ERROR_STOP=1 -f "Scripts de la solución/Scripts Postgresql/21_rename_orders_after_validation.sql"
```

Importante: este script debe ejecutarse únicamente después de validar que los conteos, distribución y pruebas funcionales sean correctos.

---

## Cómo ejecutar los scripts MongoDB

Los scripts MongoDB se encuentran en:

```text
Scripts de la solución/Scripts Mongo/
```

### Conexión a MongoDB

MongoDB Atlas:

```bash
mongosh "mongodb+srv://USUARIO:PASSWORD@CLUSTER.mongodb.net/EcommifyDB"
```

MongoDB local:

```bash
mongosh "mongodb://localhost:27017/EcommifyDB"
```

### Ejecutar archivo de operaciones CRUD

```bash
mongosh "mongodb+srv://USUARIO:PASSWORD@CLUSTER.mongodb.net/EcommifyDB" "Scripts de la solución/Scripts Mongo/ecommify_mongodb_crud_operations.js"
```

Este archivo contiene ejemplos de:

* Consultas sobre productos.
* Consultas sobre pedidos.
* Agregaciones por categoría.
* Consultas de clientes por ciudad y estado.
* Agregaciones de ventas por mes.
* Consultas de reseñas.
* Inserciones de productos, clientes, pedidos y reseñas.
* Actualizaciones de precio, stock, estado de pedido, ítems y comentarios.

Nota técnica: si el script se ejecuta como archivo completo y el motor reporta error por comentarios con `#`, reemplazar esos comentarios por `//` o ejecutar los bloques manualmente desde MongoDB Compass o `mongosh`.

---

## Cómo ejecutar los notebooks de Colab

Los notebooks están en:

```text
Scripts de la solución/Colab/
```

### Ejecución en Google Colab

1. Ingresar a Google Colab.
2. Seleccionar `File > Upload notebook`.
3. Cargar:

   * `Unidad_5_Act_2.ipynb`
   * `Unidad_5_Act_2_1.ipynb`
4. Ejecutar las celdas en orden.
5. Ajustar rutas de datasets si el notebook usa archivos externos.
6. Validar que las dependencias requeridas estén instaladas.

### Ejecución local con Jupyter

```bash
pip install notebook pandas numpy matplotlib sqlalchemy psycopg2-binary pymongo
jupyter notebook
```

Luego abrir el notebook desde la ruta correspondiente.

---

## Resultados principales

La evaluación de rendimiento demostró mejoras relevantes después de aplicar índices, reescritura de consultas y particionamiento.

| Métrica                              |         Antes |     Después | Mejora |
| ------------------------------------ | ------------: | ----------: | -----: |
| Tiempo total de ejecución PostgreSQL |  2.786,066 ms |  340,828 ms | 87,77% |
| Bloques leídos                       | 1.103 bloques | 123 bloques | 88,85% |

Estos resultados evidencian:

* Menor dependencia de escaneos secuenciales.
* Mejor uso de índices.
* Menor volumen de datos leído.
* Mejor comportamiento de consultas críticas.
* Mayor preparación para crecimiento histórico.

---

## Análisis PostgreSQL vs MongoDB

| Aspecto evaluado           | Motor recomendado | Justificación                                                          |
| -------------------------- | ----------------- | ---------------------------------------------------------------------- |
| Pedidos                    | PostgreSQL        | Requiere consistencia fuerte, trazabilidad e integridad transaccional. |
| Pagos                      | PostgreSQL        | Requiere precisión financiera, conciliación y control de duplicados.   |
| Inventario                 | PostgreSQL        | Debe evitar sobreventa y mantener consistencia del stock.              |
| Clientes                   | PostgreSQL        | Relación directa con pedidos, pagos y análisis transaccional.          |
| Productos base             | PostgreSQL        | Catálogo maestro estructurado e integrado con ítems de pedido.         |
| Catálogo extendido         | MongoDB           | Soporta atributos variables por categoría.                             |
| Reseñas enriquecidas       | MongoDB           | Maneja texto libre, comentarios y estructura flexible.                 |
| Perfiles consolidados      | MongoDB           | Facilita lecturas rápidas y documentos derivados.                      |
| Comportamiento de usuarios | MongoDB           | Permite almacenar eventos semiestructurados de alto volumen.           |
| Analítica preprocesada     | MongoDB           | Útil para dashboards y vistas agregadas.                               |

---

## Análisis CAP aplicado

La solución aplica el Teorema CAP de forma diferenciada por módulo:

| Módulo                     | Motor                | Prioridad CAP                    | Justificación                                                                        |
| -------------------------- | -------------------- | -------------------------------- | ------------------------------------------------------------------------------------ |
| Pedidos                    | PostgreSQL           | CP                               | Se prioriza consistencia y tolerancia a particiones para evitar estados incorrectos. |
| Pagos                      | PostgreSQL           | CP                               | Se prioriza integridad financiera sobre disponibilidad inmediata.                    |
| Inventario                 | PostgreSQL           | CP                               | Se evita vender productos sin disponibilidad real.                                   |
| Clientes                   | PostgreSQL           | CP                               | Se garantiza integridad en relaciones transaccionales.                               |
| Catálogo extendido         | MongoDB              | AP                               | Puede tolerar consistencia eventual y priorizar disponibilidad.                      |
| Reseñas enriquecidas       | MongoDB              | AP                               | No requiere consistencia inmediata.                                                  |
| Comportamiento de usuarios | MongoDB              | AP                               | Se prioriza captura disponible y procesamiento posterior.                            |
| Analítica y reportes       | PostgreSQL + MongoDB | AP para lectura / CP para fuente | Los agregados pueden tener retraso, manteniendo PostgreSQL como fuente confiable.    |
| Sincronización ETL         | Capa intermedia      | CP controlado                    | Debe evitar propagación de datos incompletos o inconsistentes.                       |

---

## Lecciones aprendidas

* No todos los datos requieren el mismo motor de base de datos.
* La consistencia debe priorizarse según la criticidad del proceso de negocio.
* PostgreSQL es más adecuado para transacciones, integridad y consultas relacionales complejas.
* MongoDB aporta valor en escenarios documentales, agregados y lectura flexible.
* El rendimiento depende del diseño físico: índices, particionamiento y planes de ejecución.
* El modelado documental requiere criterio para decidir entre embedding y referencing.
* La sincronización entre motores debe gobernarse con validaciones, trazabilidad e idempotencia.
* El análisis CAP debe hacerse por módulo y no de forma genérica para toda la arquitectura.
* El monitoreo continuo es clave para sostener el rendimiento.
* Las restricciones de free tier obligan a controlar carga, almacenamiento, índices y pruebas.

---

## Recomendaciones estratégicas

1. Mantener PostgreSQL/Supabase como fuente de verdad transaccional.
2. Mantener MongoDB Atlas como capa documental y de lectura flexible.
3. Automatizar la creación de particiones futuras.
4. Monitorear planes de ejecución con `EXPLAIN ANALYZE`.
5. Revisar periódicamente el uso y tamaño de índices.
6. Controlar la partición `DEFAULT` para evitar acumulación de registros fuera de rango.
7. Implementar procesos ETL o eventos para sincronizar PostgreSQL hacia MongoDB.
8. Incorporar observabilidad con métricas de latencia, errores, conexiones, uso de índices y replication lag.
9. Evaluar migración de free tier a planes productivos para soportar mayor concurrencia.
10. Implementar caching, búsqueda especializada y monitoreo centralizado en escenarios productivos.

---

## Consideraciones importantes

* Este repositorio corresponde a una entrega académica.
* Los datasets base no se encuentran documentados como carpeta independiente en la estructura principal del repositorio; por tanto, los scripts asumen que las tablas o colecciones ya fueron cargadas previamente.
* Los scripts deben ejecutarse primero en un ambiente de pruebas.
* Los scripts de renombramiento o migración deben ejecutarse únicamente después de validar conteos y resultados.
* Las credenciales de conexión no deben versionarse en GitHub.
* Para MongoDB Atlas se recomienda usar variables de entorno o mecanismos seguros para administrar cadenas de conexión.
* Para PostgreSQL/Supabase se recomienda validar permisos antes de ejecutar extensiones como `pg_cron`.

---

## Comandos útiles de Git

Actualizar el repositorio local:

```bash
git pull origin main
```

Agregar el README actualizado:

```bash
git add README.md
git commit -m "docs: actualizar README completo del proyecto"
git push origin main
```

Verificar estado:

```bash
git status
```

---

## Autor

Giovani Esteban Romero
Maestría en Arquitectura de Software
Universidad de La Sabana

Proyecto: Diseño de Base de Datos – Entrega Proyecto Final

---

## Estado del proyecto

Proyecto finalizado y documentado como entrega académica, con soporte en:

* Documento técnico final.
* Presentación ejecutiva.
* Diagramas de arquitectura y modelos de datos.
* Evidencias de ejecución.
* Scripts PostgreSQL.
* Scripts MongoDB.
* Notebooks de apoyo.
