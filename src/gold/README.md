# Capa Gold – Modelo Analítico

La capa **Gold** contiene las tablas finales listas para consumo analítico.
En esta capa se aplican las reglas de negocio y se generan estructuras
optimizadas para herramientas de análisis como **Azure Synapse Analytics**
y **Power BI**.

---

## 🎯 Objetivo de la Capa Gold
- Proveer datos confiables y consistentes para analítica
- Aplicar reglas de negocio finales
- Manejar cambios en los datos mediante CDC
- Optimizar el acceso para consultas analíticas

---

## 🛠️ Implementación Técnica

La capa Gold está implementada en **Azure Databricks** utilizando:

- **PySpark**
- **Delta Live Tables (DLT)**
- **Pipelines / Jobs de Databricks** para la orquestación

El procesamiento se basa en datos provenientes de la capa Silver.

---

## 🔄 Flujo de Procesamiento

1. Lectura de tablas Silver mediante streaming
2. Creación de tablas intermedias (staging)
3. Aplicación de reglas de negocio
4. Manejo de cambios con **Change Data Capture (CDC)**
5. Persistencia de tablas Gold en **Delta Lake**

---

## 🧪 Ejemplo de Lógica Implementada

- Uso de `@dlt.table` para definir tablas gestionadas
- Creación de tablas finales mediante `create_auto_cdc_flow`
- Definición de claves primarias y columnas de secuencia
- Almacenamiento como tablas Delta optimizadas

---

## 📦 Almacenamiento

- **Formato**: Delta Lake
- **Ubicación física**: Azure Data Lake Storage Gen2
- **Catálogo**: Unity Catalog
- **Capa**: Gold

Las tablas creadas en esta capa son accesibles directamente
desde **Azure Synapse Analytics (Serverless SQL Pool)**.

---

## 📊 Consumo de Datos

Los datos de la capa Gold son consumidos por:
- Azure Synapse Analytics (consultas SQL serverless), se podria implementar en Power Bi pero
  el objetivo del proyecto solo abarca Azure Synapse Analytics.


Esta capa no está diseñada para transformaciones adicionales,
solo para lectura analítica.

<img width="1298" height="536" alt="synapse_analytics" src="https://github.com/user-attachments/assets/fd09a5a4-fe9e-40c9-b978-bb6f9082ed01" />

---

## 🔐 Gobierno y Calidad de Datos

- Uso de Unity Catalog para gobernanza
- Control de esquema y versionado con Delta Lake
- Trazabilidad desde capas Bronze y Silver

