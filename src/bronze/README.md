# Capa Bronze – Ingesta de Datos Crudos

La capa **Bronze** es responsable de la **ingesta de datos en su forma original** desde las fuentes de origen hacia el Data Lake, sin aplicar transformaciones de negocio.

El objetivo principal de esta capa es:
- Preservar los datos tal como llegan desde la fuente
- Permitir reprocesamientos en caso de cambios aguas abajo
- Mantener trazabilidad del origen de los datos

---

## 🛠️ Implementación

La capa Bronze está implementada utilizando **Azure Data Factory (ADF)**.

Las responsabilidades de los pipelines de ADF incluyen:
- Extraer datos desde la fuente de origen
- Almacenar los datos crudos en **Azure Data Lake Storage Gen2**
- Orquestar la ejecución y manejar reintentos básicos
- Registrar la ejecución para monitoreo

---

## 📥 Fuentes de Datos
- Eventos de streaming / datos de Spotify
- Datos ingeridos en formato crudo 

---

## 📦 Almacenamiento
- **Cuenta de almacenamiento**: Azure Data Lake Storage Gen2  
- **Contenedor**: bronze  
- **Formato**: datos crudos (sin transformación)  
- **Particionado**: por fecha de ingesta

---

## 🔐 Gobierno de Datos
- No se realizan limpiezas ni enriquecimientos
- No se eliminan registros
- La gestión de retención se maneja a nivel de almacenamiento

---

## 📊 Visualización del Pipeline

A continuación se muestra el pipeline de Azure Data Factory utilizado para la ingesta de datos:


<img width="976" height="438" alt="bronze_layer" src="https://github.com/user-attachments/assets/634e990a-a232-4b52-bd3a-ece53b10240b" />




## 🧭 Consumo Aguas Abajo
Los datos almacenados en la capa Bronze son consumidos por procesos de **Databricks Structured Streaming** en la capa Silver.
