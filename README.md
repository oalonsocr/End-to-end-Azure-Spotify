# Plataforma End-to-End de Datos en Azure (Spotify)

## 📌 Descripción General
Este proyecto implementa una **arquitectura end-to-end de ingeniería de datos en Azure**, utilizando datos de Spotify como caso de estudio.

El objetivo es construir una plataforma moderna basada en **Lakehouse**, cubriendo todo el ciclo de vida del dato: desde la ingesta hasta el consumo analítico, aplicando buenas prácticas de **escalabilidad, gobernanza y optimización de costos**.

---

## 🏗️ Arquitectura

### Tecnologías Utilizadas
- Azure Data Factory
- Azure Data Lake Storage Gen2
- Azure Databricks (PySpark, Delta Lake, Unity Catalog)
- Delta Live Tables (DLT)
- Azure Synapse Analytics (Serverless SQL Pool)

### Arquitectura Medallion
- **Bronze**: Ingesta de datos crudos mediante Azure Data Factory  
- **Silver**: Transformación y limpieza usando Databricks Structured Streaming  
- **Gold**: Tablas analíticas finales implementadas con Delta Live Tables  

📊 Diagrama de arquitectura:

<img width="1050" height="495" alt="end_to_end_project" src="https://github.com/user-attachments/assets/bbcf2c64-a563-45b9-87da-ec7bbf2ac646" />


---

## 🔄 Flujo de Datos

1. Azure Data Factory ingiere datos crudos hacia ADLS Gen2 (capa Bronze)
2. Databricks procesa datos Bronze y genera tablas Silver mediante streaming
3. Delta Live Tables transforma Silver en tablas Gold optimizadas
4. Azure Synapse Analytics consulta las tablas Gold directamente sobre Delta Lake


---

## 📂 Estructura del Repositorio

<img width="415" height="86" alt="image" src="https://github.com/user-attachments/assets/949110f2-f2ca-4de0-b38e-fdfa669b7538" />


---

## ⚙️ Despliegue en Databricks

El proyecto utiliza **Databricks Asset Bundles** para gestionar los entornos de despliegue.

```bash
databricks bundle validate
databricks bundle deploy --target prod 
```

Entornos

dev: entorno de desarrollo individual

prod: entorno productivo aislado


---

## ⚙️ Despliegue en Databricks

El proyecto utiliza **Databricks Asset Bundles** para gestionar los entornos de despliegue.

```bash
databricks bundle validate
databricks bundle deploy --target prod
```

Entornos

dev: entorno de desarrollo individual

prod: entorno productivo aislado

---

🔐 Seguridad y Gobernanza

- Autenticación basada en Azure Active Directory
- Gobernanza de datos mediante Unity Catalog
- Acceso a datos gestionado con Managed Identity
- Control de esquemas y versionado con Delta Lake

---

💰 Optimización de Costos

- Uso de Azure Synapse Serverless (pago por consulta)
- Almacenamiento en Delta Lake sin duplicación de datos
- Exposición de datos mediante vistas

---

🚀 Posibles Mejoras

- Integración CI/CD con GitHub Actions
- Reglas de calidad de datos en Delta Live Tables
- Seguridad a nivel de filas (RLS)
- Optimización avanzada de consultas analíticas

---
👤 Autor

Omar Alonso Cuadros Román
Ingeniero de Datos | Azure | Databricks
