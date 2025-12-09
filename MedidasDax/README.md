## 📁 Medidas Base

```dax
Total Ventas = SUM(Sales[SalesAmount])
```

Suma total de ventas

```dax
Total Costos = SUM(Sales[TotalCost])
```

Suma total de costos

```dax
Utilidad = [Total Ventas] - [Total Costos]
```

Calcula la utilidad (ventas menos costos)

```dax
Margen de Utilidad % = DIVIDE([Utilidad], [Total Ventas], 0)
```

Porcentaje de utilidad sobre ventas

```dax
Cantidad Total = SUM(Sales[SalesQuantity])
```

Suma de unidades vendidas

```dax
Monto Devoluciones = SUM(Sales[ReturnAmount])
```

Total de devoluciones en dinero

```dax
Tasa de Devolución % = DIVIDE([Monto Devoluciones], [Total Ventas], 0)
```

Porcentaje de devoluciones sobre ventas totales

## 📁 Comparaciones YoY

```dax
Ventas Año Anterior = CALCULATE([Total Ventas], SAMEPERIODLASTYEAR(Calendar[DateKey]))
```

Ventas del mismo período año anterior

```dax
Ventas YoY % = DIVIDE([Total Ventas] - [Ventas Año Anterior], [Ventas Año Anterior], 0)
```

Variación porcentual interanual de ventas

```dax
Utilidad Año Anterior = CALCULATE([Utilidad], SAMEPERIODLASTYEAR(Calendar[DateKey]))
```

Utilidad del mismo período año anterior

```dax
Utilidad YoY % = DIVIDE([Utilidad] - [Utilidad Año Anterior], [Utilidad Año Anterior], 0)
```

Variación porcentual interanual de utilidad

## 📁 Análisis de Promociones

```dax
Ventas con Descuento = 
CALCULATE(
    [Total Ventas],
    Sales[DiscountAmount] > 0
)
```

Ventas generadas con descuentos aplicados

```dax
Ventas sin Descuento = 
CALCULATE(
    [Total Ventas],
    Sales[DiscountAmount] = 0
)
```

Ventas sin descuentos aplicados

```dax
Descuento Promedio % = AVERAGE(Promotion[DiscountPercent])
```

Porcentaje promedio de descuento aplicado

## 📁 Análisis de Rendimiento

```dax
Valor Promedio Transacción = DIVIDE([Total Ventas], [Cantidad Total], 0)
```

Ticket promedio por unidad vendida

```dax
Ventas por Tienda = 
DIVIDE(
    [Total Ventas],
    DISTINCTCOUNT(Sales[StoreKey]),
    0
)
```

Promedio de ventas por tienda

```dax
Cantidad de Transacciones = COUNTROWS(Sales)
```

Número total de transacciones

```dax
Artículos Promedio por Transacción = 
DIVIDE(
    [Cantidad Total],
    [Cantidad de Transacciones],
    0
)
```

Promedio de ítems por transacción

```dax
Puntaje Desempeño Producto = 
VAR RankVentas = RANKX(ALL(Product[ProductName]), [Total Ventas], , DESC)
VAR RankMargen = RANKX(ALL(Product[ProductName]), [Margen de Utilidad %], , DESC)
RETURN 
DIVIDE(RankVentas + RankMargen, 2, 0)
```

Score combinado de ventas y margen

## 📁 Inteligencia Temporal

```dax
Ventas Acumuladas Año = 
TOTALYTD([Total Ventas], Calendar[DateKey])
```

Ventas acumuladas desde inicio de año (YTD)

```dax
Ventas Acumuladas Trimestre = 
TOTALQTD([Total Ventas], Calendar[DateKey])
```

Ventas acumuladas en el trimestre (QTD)

```dax
Ventas Acumuladas Mes = 
TOTALMTD([Total Ventas], Calendar[DateKey])
```

Ventas acumuladas en el mes (MTD)

```dax
Ventas Trimestre Actual = 
CALCULATE(
    [Total Ventas],
    DATESQTD(Calendar[DateKey])
)
```

Ventas del trimestre en curso

```dax
Ventas Mes Anterior = 
CALCULATE(
    [Total Ventas],
    PREVIOUSMONTH(Calendar[DateKey])
)
```

Ventas del mes previo

```dax
Ventas MoM % = 
DIVIDE(
    [Total Ventas] - [Ventas Mes Anterior],
    [Ventas Mes Anterior],
    0
)
```

Variación mes a mes (Month over Month)

```dax
Ventas Promedio Diario = 
DIVIDE(
    [Total Ventas],
    DISTINCTCOUNT(Calendar[DateKey]),
    0
)
```

Promedio de ventas por día

```dax
Pico Ventas Día = 
CALCULATE(
    MAX(Sales[SalesAmount]),
    ALLEXCEPT(Calendar, Calendar[DayOfWeekName])
)
```

Venta máxima por día de la semana

## 📁 Análisis Geográfico

```dax
Ventas por Geografía = 
DIVIDE(
    [Total Ventas],
    DISTINCTCOUNT(Geography[GeographyKey]),
    0
)
```

Promedio de ventas por región

```dax
Cantidad Tiendas = DISTINCTCOUNT(Stores[StoreKey])
```

Número total de tiendas únicas

```dax
Tiendas Activas = 
CALCULATE(
    [Cantidad Tiendas],
    Stores[Status] = "on"
)
```

Tiendas en operación

```dax
Tamaño Promedio Tienda = AVERAGE(Stores[SellingAreaSize])
```

Área promedio de venta por tienda

```dax
Ventas por Metro Cuadrado = 
DIVIDE(
    [Total Ventas],
    SUM(Stores[SellingAreaSize]),
    0
)
```

Productividad por superficie de venta

## 📁 Rankings

```dax
Ranking por Ventas = 
RANKX(
    ALL(Geography[RegionCountryName]),
    [Total Ventas],
    ,
    DESC,
    DENSE
)
```

Posición de ventas por región

## 📁 Medidas Contextuales

```dax
Producto Seleccionado = 
IF(
    HASONEVALUE(Product[ProductName]),
    VALUES(Product[ProductName]),
    "Todos los productos"
)
```

Muestra el producto filtrado o "Todos"

```dax
Región Seleccionada = 
IF(
    HASONEVALUE(Geography[RegionCountryName]),
    VALUES(Geography[RegionCountryName]),
    "Todas las regiones"
)
```

Muestra la región filtrada o "Todas"

```dax
Mix de Productos % = 
DIVIDE(
    [Total Ventas],
    CALCULATE([Total Ventas], ALL(Product)),
    0
)
```

Participación del producto en ventas totales

```dax
Título Drill Through = 
"Análisis Detallado: " & [Producto Seleccionado] & " | " & [Región Seleccionada]
```

Título dinámico para páginas de detalle

## 📁 Análisis Avanzado

```dax
Media Móvil Ventas 3M = 
CALCULATE(
    AVERAGE(Sales[SalesAmount]),
    DATESINPERIOD(
        Calendar[DateKey],
        MAX(Calendar[DateKey]),
        -3,
        MONTH
    )
)
```

Promedio móvil de últimos 3 meses

```dax
Proyección Ventas = 
VAR VentasActuales = [Total Ventas]
VAR CrecimientoPromedio = [Ventas YoY %]
RETURN VentasActuales * (1 + CrecimientoPromedio)
```

Proyección simple basada en tendencia YoY

```dax
Ventas vs Objetivo = 
VAR Objetivo = [Total Ventas] * 1.15
RETURN [Total Ventas] - Objetivo
```

Diferencia entre ventas y objetivo (+15%)

```dax
Ventas vs Promedio Categoría = 
[Total Ventas] - 
CALCULATE(
    AVERAGE(Sales[SalesAmount]),
    ALL(Product[ProductName])
)
```

Comparación con promedio de categoría

## 📁 Títulos Dinámicos

```dax
Título Dinámico Ventas = 
"Total Ventas: " & FORMAT([Total Ventas], "$#,##0") & 
" | YoY: " & FORMAT([Ventas YoY %], "+0.0%;-0.0%;0%")
```

Título con valores formateados de ventas y YoY

## 📁 Formato Condicional

```dax
Color Ventas = 
SWITCH(
    TRUE(),
    [Ventas YoY %] >= 0.10, "#2D8659",
    [Ventas YoY %] >= 0, "#FF8C42",
    "#E63946"
)
```

Asigna color según desempeño YoY (verde/naranja/rojo)

Estas medidas están listas para organizarse en carpetas de visualización en Power BI, facilitando la navegación y mantenimiento de tu modelo semántico.


