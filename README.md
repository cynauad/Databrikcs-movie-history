# Databricks Movie History

Este repositorio contiene un proyecto completo de Databricks para el análisis de datos de películas, implementando una arquitectura de lago de datos (Data Lakehouse) con capas Bronze, Silver y Gold.

## 📋 Descripción del Proyecto

El proyecto demuestra un pipeline completo de ingeniería de datos para procesar y analizar información histórica de películas, incluyendo presupuestos, ingresos, países de producción, compañías, géneros, idiomas y más.

Este proyecto es parte del curso **Master en Azure Databricks & Spark para Data Engineers [A-Z]** de Udemy.

## 📚 Sobre el curso

**Master en Azure Databricks & Spark para Data Engineers [A-Z]** — Udemy

Curso teórico-práctico diseñado para profesionales de datos que desean aprender a procesar, transformar y analizar grandes volúmenes de datos en la nube de Microsoft Azure. A lo largo del curso se exploran la arquitectura de Databricks, su integración con otros servicios de Azure y las mejores prácticas para el manejo de datos a gran escala utilizando Apache Spark.

Entre los principales temas cubiertos se encuentran:

- Procesamiento de datos batch (carga completa e incremental)
- Construcción de pipelines ETL con Apache Spark SQL y PySpark
- Arquitectura Data Lake y Lakehouse con Delta Lake
- Unity Catalog y gestión de seguridad en Databricks
- Orquestación de pipelines con Databricks y Azure Data Factory (ADF)
- Clusters, Notebooks, Pools y Jobs en Azure Databricks
- Conexión de Databricks con Power BI

## 🏗️ Arquitectura

El proyecto sigue la arquitectura Medallion:

- **Bronze Layer**: Datos crudos ingestados directamente desde archivos CSV
- **Silver Layer**: Datos limpios y transformados
- **Gold Layer**: Datos agregados y optimizados para análisis

## 📁 Estructura del Proyecto

```
databricks-course/
├── set-up/                    # Configuración inicial y acceso a Azure Data Lake Storage
│   ├── 01. access_adls_using_access_key.ipynb
│   ├── 02. access_adls_using_token_sas.ipynb
│   ├── 03. access_adls_using_service_principal.ipynb
│   ├── 04. access_adls_using_cluster_scoped.ipynb
│   ├── 05. Explorer_secrets_utility.ipynb
│   ├── 06. access_external_location.ipynb
│   ├── 07. work_with_files.ipynb
│   └── 08. configure_access_adls_gen2.ipynb
├── ingestion/                 # Ingestión de datos desde archivos CSV
│   ├── 00.ingestion_all_notebooks.ipynb
│   ├── 01. ingestion_file_movie.ipynb
│   ├── 02. ingestion_file_language.ipynb
│   ├── 03. ingestion_file_genre.ipynb
│   ├── 04. ingesta_file_country.ipynb
│   ├── 05. ingesta_file_person.ipynb
│   ├── 06. ingesta_file_movie_genre.ipynb
│   ├── 07. ingesta_file_movie_cast.ipynb
│   ├── 08. ingesta_file_language_role.ipynb
│   ├── 09. ingestion_folder_production_company.ipynb
│   ├── 10. ingestion_folder_movie_company.ipynb
│   ├── 11. ingestion_folder_movie_languages.ipynb
│   ├── 12. ingestion_folder_production_country.ipynb
│   └── 13.create_silver_database.ipynb
├── bronze/                    # Creación de tablas en capa Bronze
│   └── 01.create_bronze_tables.ipynb
├── transformation/            # Transformaciones y creación de capas Silver/Gold
│   ├── 01.results_movie_genre_language.ipynb
│   ├── 02.results_country_prod_company.ipynb
│   ├── 03.results_group_movie_genre.ipynb
│   ├── 04.results_group_movie_country.ipynb
│   ├── 05.create_gold_database.ipynb
│   └── 06.results_movie.ipynb
├── analysis/                  # Análisis de datos
│   ├── 01.budget_revenue_country.ipynb
│   ├── 02.budget_revenue_production_country.ipynb
│   ├── 03.budget_revenue_country.ipynb
│   └── 04.budget_revenue_production_country.ipynb
├── demo/                      # Demostraciones de operaciones Spark SQL
│   ├── 01.filter_demo.ipynb
│   ├── 02.join_demo.ipynb
│   ├── 03.aggregation_demo.ipynb
│   ├── 04._sql_temp_view_demo.ipynb
│   ├── 05_.sql_demo.ipynb
│   ├── 06.sql_objects_demo.ipynb
│   ├── 07.sql_dml_demo.ipynb
│   ├── 08.sql_functions_demo.ipynb
│   ├── 09.sql_join_demo.ipynb
│   └── 10.delta_lake_demo.ipynb
├── utils/                     # Utilidades
│   ├── 01.prepare_for_incremental_load.ipynb
│   └── 02.email-error.ipynb
└── includes/                  # Configuraciones y funciones comunes
    ├── commom_functions.ipynb
    └── configuration.ipynb
```

## 🚀 Inicio Rápido

### Prerrequisitos

- Cuenta de Azure con Data Lake Storage Gen2
- Workspace de Databricks
- Cluster de Databricks configurado
- Secrets configurados en Databricks para acceso a ADLS

### Configuración Inicial

1. **Configurar acceso a Azure Data Lake Storage:**
   - Ejecutar los notebooks en `set-up/` según el método de autenticación preferido
   - Configurar secrets en Databricks para las claves de acceso

2. **Configurar rutas de almacenamiento:**
   - Editar `includes/configuration.ipynb` con las rutas correctas de ADLS
   - Crear los contenedores `bronze`, `silver` y `gold` en ADLS

3. **Ejecutar ingestion:**
   - Comenzar con `ingestion/00.ingestion_all_notebooks.ipynb` para procesar todos los archivos
   - O ejecutar individualmente los notebooks de ingestion según sea necesario

### Flujo de Ejecución

1. **Ingestion** → Crear tablas Bronze
2. **Transformación** → Crear bases de datos Silver y Gold
3. **Análisis** → Ejecutar consultas analíticas
4. **Demo** → Explorar funcionalidades de Spark SQL

## 📊 Conjuntos de Datos

El proyecto procesa los siguientes tipos de datos:

- **Películas**: ID, título, presupuesto, ingresos, popularidad, fecha de lanzamiento, duración, calificaciones
- **Países**: Países de producción
- **Compañías**: Compañías productoras
- **Géneros**: Clasificación por género
- **Idiomas**: Idiomas de las películas
- **Reparto**: Actores y roles
- **Relaciones**: Uniones entre películas y otros entidades

## 🔧 Tecnologías Utilizadas

- **Databricks**: Plataforma de análisis de datos
- **Apache Spark**: Procesamiento de datos a gran escala
- **Delta Lake**: Formato de tabla para lakehouse
- **Azure Data Lake Storage Gen2**: Almacenamiento de datos
- **PySpark**: API de Python para Spark
- **Spark SQL**: Consultas SQL sobre DataFrames

## 📈 Análisis Incluidos

- Presupuesto y ingresos por país
- Rendimiento por compañía productora
- Distribución por género y idioma
- Tendencias temporales (2010-2015)
- Estadísticas agregadas por país

## 🎯 Casos de Uso

- Análisis de mercado cinematográfico
- Evaluación de rendimiento de compañías productoras
- Estudios de tendencias por región
- Optimización de presupuestos de producción

## 📝 Notas

- Los notebooks están en español
- Requiere configuración previa de Azure Data Lake Storage
- Incluye manejo de errores y logging por email
- Soporta carga incremental de datos

## 📄 Licencia

Este proyecto es para fines educativos y de demostración.