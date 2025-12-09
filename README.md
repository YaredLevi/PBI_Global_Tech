# Reporte Global Tech - Power BI

![Dashboard Preview](PaginasReporte/Global/Logo.png)

---
**👉 [Ver Presentación del Análisis de Ventas](PaginasReporte/)**

## 👨‍💻 Sobre Este Proyecto

Este es un **proyecto de Business Intelligence y Análisis de Datos** desarrollado para 
demostrar habilidades técnicas y de comunicación en el ciclo completo de un proyecto 
de BI: desde modelado de datos hasta presentación ejecutiva de hallazgos.

### 🎓 Formación y Habilidades Aplicadas

Este proyecto integra conocimientos adquiridos de tres fuentes principales:

**1. [Data Analyst in Power BI - DataCamp](https://www.datacamp.com/completed/statement-of-accomplishment/track/67244a4f1f0e8b6a2cc36911cef101cd1802ce39)**
- Modelado de datos con Power BI
- DAX 
- Power Query
- Row-Level Security (RLS) para gobernanza de datos
- Gestión de dimensión tiempo y jerarquías
- Interactividad avanzada: drill-through, drill-down, tooltips, marcadores
- Divulgación progresiva de información 
- Tabla de medidas organizada
- Despliegue en Power BI Service

**2. [Google Data Analytics Professional Certificate - Coursera](https://www.coursera.org/account/accomplishments/professional-cert/certificate/SB44E9JQDSIL)**
- Storytelling con datos
- Diseño de visualizaciones efectivas
- Comunicación de hallazgos a stakeholders no técnicos
- Estructura de presentaciones
- Mejores prácticas para dashboards ejecutivos

**3. Formación Universitaria en Ingeniería Informática**
- Fundamentos de bases de datos relacionales
- Modelado de datos y normalización
- Arquitectura de sistemas de información

---

## 📊 Sobre el Archivo .pbix

Este análisis utiliza el dataset oficial de Microsoft 
**["ContosoSalesForPowerBI"](https://www.microsoft.com/en-us/download/details.aspx?id=46801)**, 
de acceso público y diseñado para aprendizaje de Power BI.

### ⚠️ Nota Importante sobre el Archivo

El archivo `.pbix` descargable de Microsoft no incluye:
- **NO incluye la fuente de datos original** (según advertencia oficial)
- El modelo usa llaves naturales de negocio **en lugar de llaves subrrogadas**
- **Sin Tabla Intermedia de Detalle de Venta** (Creo que Microsoft lo hizo para simplificar el modelo para aprendizaje de Power BI, enfocándose en visualizaciones 
y DAX en lugar de modelado transaccional complejo.)


### 🎯 Por Qué Enfoqué el Análisis en Tienda de Texas

Decidí **limitar el análisis a una Tienda de Texas** por dos razones:

1. **Demostrar Row-Level Security (RLS):** Simula un escenario real donde diferentes 
   gerentes regionales solo pueden acceder a datos de su territorio
2. **Storytelling más enfocado:** Un análisis regional permite narrativa más específica 
   y recomendaciones accionables vs análisis global genérico
