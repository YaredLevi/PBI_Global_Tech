# Diccionario de Datos 

## Calendar

| Columna       | Descripción                                                  |
| ------------- | ------------------------------------------------------------ |
| DateInt       | Fecha en formato entero (ddmmyyyy, los datos comienzan en 01-01-2011 y termina en 31-12-2013) |
| DateKey       | Clave primaria de fecha                                      |
| DayOfMonth    | Día del mes (1–31)                                           |
| DayOfWeekName | Nombre del día de la semana                                  |
| MonthName     | Nombre del mes                                               |
| MonthOfYear   | Número del mes (1–12)                                        |
| QuarterOfYear | Número de trimestre (1–4, por cada año, el primer trimestre empieza en enero y finaliza el 4 trimestre el ultimo día de diciembre) |
| Year          | Año calendario                                               |

## Channel

| Columna     | Descripción                                         |
| ----------- | --------------------------------------------------- |
| ChannelKey  | Clave primaria del canal de ventas                  |
| ChannelName | Nombre del canal (Store, Online, Reseller, Catalog) |

## Geography

| Columna           | Descripción                                                  |
| ----------------- | ------------------------------------------------------------ |
| GeographyKey      | Clave primaria de la geografía                               |
| ContinentName     | Nombre del continente                                        |
| GeographyType     | Tipo de geografía (City, Continent, Country/Región, State/Provice) |
| RegionCountryName | Nombre de país, región o ciudad                              |

## Product

| Columna               | Descripción                          |
| --------------------- | ------------------------------------ |
| ProductKey            | Clave primaria del producto          |
| BrandName             | Marca del producto                   |
| ClassName             | Clase a la que pertenece el producto |
| Manufacturer          | Marca o fabricante                   |
| ProductDescription    | Descripción del producto             |
| ProductName           | Nombre del producto                  |
| ProductSubcategoryKey | Clave de subcategoría                |
| UnitCost              | Costo unitario de adquisición        |
| UnitPrice             | Precio unitario de venta             |

## ProductSubcategory

| Columna               | Descripción                                                  |
| --------------------- | ------------------------------------------------------------ |
| ProductSubcategoryKey | Clave primaria de subcategoría                               |
| ProductCategoryKey    | Clave de categoría principal                                 |
| ProductSubcategory    | Nombre de la subcategoría de producto (Refrigerators, Microwaves, Water Heaters, Coffee Machines, Lamps, Air Conditioners, Fans, MP4&MP3, Recorder, Radio, Recording Pen, Headphones, Bluetooth Headphones, Speakers, Audio Accessories, Televisions, VCD & DVD, Home Theater System, Car Video, TV & Video Accessories, Laptops, Netbooks, Desktops, Monitors, Projectors & Screens, Printers, Scanners & Fax, Computer Setup & Service, Computers Accessories, Digital Cameras, Digital SLR Cameras, Film Cameras, Camcorders, Cameras & Camcorders Accessories, Home & Office Phones, Touch Screen Phones, Smart phones & PDAs, Cell phones Accessories, Music CD, Movie DVD, Audio Books, Boxed Games, Download Games, Games Accessories, Washers & Dryers) |

## ProductCategory

| Columna            | Descripción                                                  |
| ------------------ | ------------------------------------------------------------ |
| ProductCategoryKey | Clave primaria de la categoría                               |
| ProductCategory    | Nombre de la categoría (Audio, TV and Video, Computers, Cameras and camcorders, Cell phones, Music Movies and Audio Books, Games and Toys, Home Appliances) |

## Promotion

| Columna         | Descripción                                                  |
| --------------- | ------------------------------------------------------------ |
| PromotionKey    | Clave primaria de la promoción                               |
| DiscountPercent | Porcentaje de descuento aplicado (0, 0.05, 0.1, 0.2, 0.15, 0.07) |
| EndDate         | Fecha final de la promoción                                  |
| PromotionLabel  | Etiqueta descriptiva de la promo                             |
| PromotionName   | Nombre de la promoción (No Discount, North America Spring Promotion, North America Back-to-School Promotion, North America Holiday Promotion, Asian Holiday Promotion, Asian Spring Promotion, Asian Summer Promotion, European Spring Promotion, European Back-to-Scholl Promotion, European Holiday Promotion) |
| StartDate       | Fecha inicial de la promoción                                |

## Sales

| Columna          | Descripción                         |
| ---------------- | ----------------------------------- |
| SalesKey         | Clave primaria de la venta          |
| ChannelKey       | Clave de canal de venta             |
| DateKey          | Clave de fecha de la transacción    |
| DiscountAmount   | Monto de descuento aplicado         |
| DiscountQuantity | Cantidad de productos con descuento |
| ProductKey       | Clave del producto vendido          |
| PromotionKey     | Clave de la promoción aplicada      |
| ReturnAmount     | Monto de devoluciones               |
| ReturnQuantity   | Cantidad de productos devueltos     |
| SalesAmount      | Monto neto vendido                  |
| SalesQuantity    | Número de unidades vendidas         |
| StoreKey         | Clave identificadora de la tienda   |
| TotalCost        | Costo total de productos vendidos   |
| UnitCost         | Costo unitario del producto         |
| UnitPrice        | Precio unitario vendido             |

## SecurityUsers

| Columna      | Descripción                                               |
| ------------ | --------------------------------------------------------- |
| UserEmail    | Correo electrónico del usuario (identificador único)      |
| Cargo        | Cargo o rol del usuario en la organización                |
| Country      | País al que tiene acceso el usuario                       |
| StoreOrState | Tienda o estado específico al que tiene acceso el usuario |
| Channel      | Canal de ventas al que tiene acceso el usuario            |

> **Nota:** Esta tabla la cree solamente para poder filtrar la información para demostrar que manejo conceptos de filtro de seguridad en Power BI, como no tenemos una tabla de usuarios (empleados) como para filtrar.

## Stores

| Columna         | Descripción                                       |
| --------------- | ------------------------------------------------- |
| StoreKey        | Clave primaria de la tienda                       |
| CloseReason     | Motivo de cierre (vacío, store, relocation)       |
| EmployeeCount   | Número de empleados                               |
| GeographyKey    | Clave geográfica (localización de la tienda)      |
| SellingAreaSize | Superficie de ventas en m²                        |
| Status          | Estado de la tienda (on, off)                     |
| StoreName       | Nombre de la tienda                               |
| StoreType       | Tipo de tienda (Catalog, Online, Reseller, Store) |
