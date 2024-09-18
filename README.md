# ETL - Extracción, Transformación y Carga :chart_with_upwards_trend: :arrows_counterclockwise:

# Super Store :convenience_store:

Super Store, líder en el sector minorista, se enfrenta al desafío de gestionar grandes volúmenes de datos dispersos. Para mejorar la toma de decisiones, se propone la implementación de un sólido sistema ETL con tablas de hecho y dimensiones. Este proyecto busca crear un sistema integral que extraiga, transforme y cargue datos eficientemente, proporcionando una estructura jerárquica para facilitar el análisis. El objetivo no es solo optimizar el almacenamiento, sino potenciar la capacidad de Super Store para identificar patrones y oportunidades de mercado, adaptándose ágilmente a cambios en la demanda del consumidor.

# Temas :bulb:

- [Introducción](#Introducción)
- [Objetivo](#Objetivo)
- [Procesamiento y análisis](#Procesamiento-y-análisis)
- [Herramientas](#Herramientas)
- [Lenguajes](#Lenguajes)
- [Resultados y Conclusiones](#Resultados-y-Conclusiones)
- [Ficha técnica](/Ficha_técnica/README.md)
- [Google Colab](/Google_Colab/README.md)
- [Dashboard](/Dashboard/README.md)
- [Presentación](/Presentación/README.md)

## Introducción 

ETL se refiere a un proceso de tres fases: Extracción (Extraction), Transformación (Transformation) y Carga (Load). Este proceso se utiliza comúnmente en el ámbito de la gestión y análisis de datos, especialmente en el contexto de data warehouses y business intelligence.

__1. Extracción (Extraction):__ Durante esta fase, los datos se extraen desde una o varias fuentes de datos, que pueden ser bases de datos, archivos planos, servicios web u otras fuentes. La extracción implica recopilar la información necesaria para su posterior procesamiento.

__2. Transformación (Transformation):__ En esta etapa, los datos extraídos se transforman según los requisitos del sistema de destino. Las transformaciones pueden incluir limpieza de datos, conversión de formatos, combinación de datos de múltiples fuentes, filtrado y otras operaciones que aseguran que los datos sean coherentes y útiles para el análisis.

__3. Carga (Load):__ La fase final implica cargar los datos transformados en el sistema de destino, que generalmente es un data warehouse o una base de datos diseñada para el análisis de negocios. Los datos ahora están listos para ser consultados y analizados de manera eficiente.

## Objetivo

A través del proceso ETL (Extract, Transform, Load), construir un sistema tabular que nos permita almacenar datos de manera eficiente y consultar estos datos más fácilmente.

## Procesamiento y análisis

__📥 1. Conectar/importar datos a otras herramientas__
- Se creó el proyecto `proyecto5-etl` y el conjunto de datos `Dataset` en BigQuery.
- Tablas importadas: **superstore**.

__🕵️‍♀️ 2. Valores nulos__
- Identificación de valores nulos utilizando comandos SQL:
  - `COUNTIF`, `IS NULL`, `AS`.

__🗃️ 3. Valores duplicados__
- Identificación de registros duplicados utilizando comando SQL:
  - `COUNT`, `GROUP BY`, `HAVING`.

__📋 4. Datos discrepantes en variables categóricas__
- Identificación de datos discrepantes en variables categóricas mediante comandos SQL:
  - `DISTINCT`, `ORDER BY`.

__📊 5. Datos discrepantes en variables numéricas__
- Identificación de datos discrepantes en variables numéricas utilizando comandos SQL:
  - `COUNT`, `ARRAY_AGG`, `CAST`.

__🔄 6. Comprobar y cambiar tipo de dato__
- Se identificó que las variables `ship_date` y `order_date` tienen el tipo de dato `TIMESTAMP`, es recomendable usar el tipo de dato `DATE`.

__🌐 7. Buscar datos de otras fuentes__
- Se extrajo información de la tabla "multinacional" de Wikipedia utilizando Python en [Google Colab](/Google_Colab/proyecto5_etl.ipynb).

__🛠️ 8. Diseñar estructura de la base de datos (tablas de hechos y dimensiones)__
- Se diseñó un modelo de **esquema estrella** para la base de datos. 
- Clasificación de las variables:
  - **Dimensiones 📏:** Variables que describen atributos contextuales (por ejemplo, productos, clientes, fechas).
  - **Hechos 📊:** Variables que contienen datos cuantitativos o eventos, como ventas, cantidad, y precios.
- Para ver el diseño de la estructura de la base de datos, puedes revisar [Ficha técnica](/Ficha_técnica/tablas.png).
    
__🗄️ 9. Crear estructura de la base de datos (tablas de hechos y dimensiones)__
- Utilizando los comandos `CREATE TABLE`, `SELECT`, `DISTINCT`, `JOIN`, se crearon y llenaron las tablas en BigQuery.
  
- **Tablas de dimensiones** 📐: 
  - `customer_dim`
  - `category_dim`
  - `subcategory_dim`
  - `product_dim`
  - `order_dim`
  - `market_dim`
    
- **Tabla de hechos** 📊: 
  - `sales_superstore`

__⏰ 10. Programar actualizaciones de tablas__

- Se creó un **flujo de actualización** de tablas considerando las relaciones entre las tablas de hechos y dimensiones.
- El objetivo es actualizar los datos de manera eficiente y mantener la **integridad referencial** de las tablas.

__🔗 11. Unir tablas__

- Con los comandos `SELECT`, `LEFT JOIN`, se creó una tabla para el **análisis exploratorio** 📊.
- La tabla se generó a partir de la estructura de tablas de dimensiones y de hechos, seleccionando variables que contienen información relevante.

Para ver más detalles de cada uno de los pasos del procesamiento, puedes revisar [Ficha técnica](/Ficha_técnica/Ficha_técnica.pdf).

__🔍 12. Análisis exploratorio__

- **Agrupar datos**: Según variables categóricas para identificar patrones y tendencias.
- **Visualizar las variables categóricas**: Se crearon gráficos y diagramas para obtener una mejor comprensión de los datos.
- **Aplicar medidas de tendencia central y dispersión**: Se calcularon estadísticas como la media, mediana, rango y desviación estándar.
- **Visualizar distribución**: Se crearon diagramas de dispersión.
- **Visualizar el comportamiento de los datos a lo largo del tiempo**: Se crearon gráficos para observar datos a través de los años.

Para ver más detalles del análisis exploratorio puedes revisar: [Dashboard](/Dashboard/Proyecto5_etl.pdf).

🔗 https://lookerstudio.google.com/reporting/58c871d4-115c-4fec-b35d-976aae6fcd3a 

## Herramientas

* Google BigQuery
* Google Looker Studio
* Google Docs
* Google Slide
* Google Colab

## Lenguajes

* SQL
* Python

## Resultados y Conclusiones

* La creación del **esquema de datos** basado en tablas de hechos y dimensiones permitirá centralizar toda la información relevante de ventas, productos, clientes y mercados en un solo lugar, facilitando el análisis de la información de forma precisa y rápida.

* La __tablas de hechos__ `sales_superstore` almacena grandes volúmenes de datos transaccionales, mientras que las __tablas de dimensiones,__ (`customers_dim`,`products_dim`, `markets_dim`, `order_dim`), contienen información descriptiva. Este diseño permite realizar consultas optimizadas y obtener resultados de manera más eficiente.

* Con el diseño de tablas de hechos y dimensiones, se podrán realizar **análisis a nivel de detalle y en diferentes dimensiones**, como analizar ventas por producto, cliente, segmento, mercado, y período de tiempo.

* La implementación de un **pipeline de actualización** permitirá que las tablas se mantengan actualizadas de manera regular (por ejemplo, diariamente o semanalmente) con la última información, asegurando la disponibilidad de datos recientes para la toma de decisiones.

* El diseño de tablas de hechos y dimensiones sigue un enfoque de **esquema estrella**, donde, la **tabla de hechos**(`sales_superstore`) se conecta con múltiples **tablas de dimensiones** (`customers_dim`, `products_dim`, `orders_dim`, `markets_dim`). Este esquema es ideal para el análisis y la creación de dashboards, ya que permite acceder a los datos de forma simple y rápida.

* La tabla de hechos `sales_superstore` tiene como **clave primaria** el `id_ticket`, lo que garantiza la unicidad de las transacciones. Las **llaves foráneas** conectan la tabla de hechos con las tablas de dimensiones, asegurando que se pueda hacer un análisis detallado utilizando los atributos de las dimensiones.

* El proceso de **ETL** debe estar diseñado para:
    - **Extraer** datos de las fuentes originales.
    - **Transformar** los datos adecuadamente (limpieza, cálculo de indicadores, generación de claves, etc.).
    - **Cargar** los datos en las tablas del esquema estrella.

* El pipeline de actualización debe manejar estos pasos automáticamente, evitando errores manuales y garantizando la integridad de los datos. La implementación del pipeline de actualización permitirá actualizar las tablas de hechos y dimensiones periódicamente, asegurando que los datos reflejen la situación actual del negocio.

Para más detalles sobre las conclusiones y recomendaciones, puedes revisar: [Ficha técnica](/Ficha_técnica/Ficha_técnica) y [Presentación](/Presentación/Presentacion.pdf).

