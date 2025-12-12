# Reporte Global Tech - Power BI

![Dashboard Preview](PaginasReporte/Global/Logo.png)

---
**👉 [Ver Presentación del Análisis de Ventas](PaginasReporte/)** (Grabación de la presentación del análisis en proceso)

## 👨‍💻 Sobre Este Proyecto

Este es un **proyecto de Business Intelligence y Análisis de Datos** desarrollado para demostrar habilidades técnicas y de comunicación en el ciclo casi completo de un proyecto de BI: desde el análisis del modelado de datos hasta presentación ejecutiva de hallazgos.

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
de acceso público y diseñado para aprendizaje de Power BI y análisis de datos.

### ⚠️ Nota Importante sobre el Archivo

El archivo `.pbix` descargable de Microsoft no incluye:
- **NO incluye la fuente de datos original** (según advertencia oficial)
- El modelo usa llaves naturales de negocio **en lugar de llaves subrrogadas**
- **Granularidad de Cabecera ("Una fila por recibo/transacción individual")** (Creo que Microsoft lo hizo para simplificar el modelo para aprendizaje de Power BI, enfocándose en visualizaciones y DAX en lugar de modelado transaccional complejo, también comprendo que en un entorno empresarial real)

| Análisis Imposible        | Razón                                                                                   |
| ------------------------- | --------------------------------------------------------------------------------------- |
| Market Basket Analysis    | No puedes saber qué productos se compraron juntos insightsthroughdata​                  |
| Ticket Promedio Real      | Cada "ticket" solo tiene 1 producto, distorsionando métricas                            |
| Cross-selling             | Imposible analizar combinaciones de productos en la misma compra                        |
| Productos Complementarios | No hay forma de identificar patrones de compra simultánea                               |
| Secuencia de Compra       | No puedes analizar el orden de selección dentro de una transacción insightsthroughdata​ |

### 🔍 Validación de Calidad de Datos: Error Detectado en el Dataset

Durante el análisis exploratorio, identifiqué una **inconsistencia en el modelo de datos** que afecta el análisis de promociones, lo solucioné:

 [Ver imagen del error](Documentacion)

#### Descripción del Problema

**Error detectado:** Registros con `PromotionKey` asignado pero sin descuento aplicado.

### 🔒 Row-Level Security: Relación Circular

El modelo incluye una relación circular entre `SecurityUsers`, `Geography` y `Channel`. 
Esto es una **decisión técnica necesaria** para implementar RLS multi-dimensional entendiendo que esta practica es un antipatrón.

 [Ver modelo semántico](Documentacion)

**Contexto:** El dataset no incluye tabla de usuarios. Para simular acceso segmentado por región y canal, creé tabla puente `SecurityUsers` que debe conectarse con ambas dimensiones, generando circularidad inevitable.


### 🎯 Por Qué Enfoqué el Análisis en Tienda de Texas

Decidí **limitar el análisis a una Tienda de Texas** por dos razones:

1. **Demostrar Row-Level Security (RLS):** Simula un escenario real donde diferentes gerentes regionales solo pueden acceder a datos de su territorio
2. **Storytelling más enfocado:** Un análisis regional permite narrativa más específica y recomendaciones accionables vs análisis global genérico
