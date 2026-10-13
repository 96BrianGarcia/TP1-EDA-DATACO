# TP N°1 – Análisis exploratorio de datos (EDA) con DataCo Smart Supply Chain
Fecha: 13/10/2026
Autor: BRIAN GARCIA


## Objetivo del trabajo

Realizar un análisis exploratorio de datos (EDA) sobre operaciones de una cadena de suministro, con foco en las demoras en la entrega: cuántos pedidos llegan tarde, qué factores se asocian con esas demoras y cómo se relacionan con la rentabilidad.

Preguntas / hipótesis que guían el análisis:

1. ¿Qué proporción de las entregas es tardía? Una parte importante de los pedidos llega tarde.
2. El modo de envío influye en las demoras. Algunos modos de envío tienen más entregas tardías que otros.
3. Los días reales de envío superan a los programados. Hay una diferencia entre lo prometido y lo cumplido.
4. Las demoras no son iguales en todos los mercados. Algunas regiones tienen más entregas tardías.
5. Las entregas tardías afectan la rentabilidad. Los pedidos tardíos tienen distinta ganancia que los que llegan a tiempo.

## Contexto del dataset

- Nombre: DataCo Smart Supply Chain for Big Data Analysis
- Contenido: registros de pedidos de una cadena de suministro con productos de indumentaria, deportes y suministros electrónicos. Incluye datos del pedido, el cliente, el producto, el envío, la entrega y resultados financieros.
- Tamaño original: 180.519 filas y 53 columnas. Tras la limpieza: 180.519 filas y 38 columnas.
- Unidad de análisis: cada fila es un ítem de pedido. Las 180.519 filas corresponden a 65.752 pedidos distintos (`Order Id`).
- Fuente original: Constante, F., Silva, F., Pereira, A. (2019). *DataCo Smart Supply Chain for Big Data Analysis*. Mendeley Data. https://data.mendeley.com/datasets/8gx2fvg2k6/1
- Descarga (Kaggle): https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis


## Diccionario de datos

Variables utilizadas en el análisis. 

| Variable | Descripción | Tipo 

| Order Id | Identificador único del pedido. Un pedido puede tener varios ítems | Identificador 
| Order Item Id | Identificador único de cada ítem de pedido | Identificador 
| order date (DateOrders) | Fecha y hora en que se realizó el pedido | Fecha 
| Days for shipping (real) | Días que tardó realmente el envío del pedido | Numérica 
| Days for shipment (scheduled) | Días programados (prometidos) para la entrega | Numérica 
| Delivery Status | Estado de la entrega: `Advance shipping` (adelantada), `Shipping on time` (a tiempo), `Late delivery` (tardía) y `Shipping canceled` (cancelada) | Categórica 
| Late_delivery_risk | Indica si el envío llegó tarde: 1 = tardío, 0 = no tardío.| Categórica binaria  
| Shipping Mode | Modo de envío: `Standard Class`, `Second Class`, `First Class` y `Same Day` | Categórica 
| Market | Mercado de destino: `Africa`, `Europe`, `LATAM`, `Pacific Asia` y `USCA` | Categórica 
| Order Item Discount | Valor del descuento aplicado al ítem | Numérica continua 
| Order Item Total | Monto total del ítem | Numérica continua 
| Benefit per order | Ganancia (o pérdida si es negativa) del ítem | Numérica continua 

## Metodología aplicada

 Carga de datos con pandas.
 Revisión general: dimensiones, tipos de datos, nulos y duplicados.
 Limpieza: eliminación de columnas vacías, identificadores, datos personales y variables sin valor para el análisis.
 Revisión de valores atípicos (por ejemplo, en la ganancia por pedido).
 Análisis univariado y bivariado con gráficos de matplotlib.
 Análisis de demoras por modo de envío, mercado y región.
 Análisis de rentabilidad.
 Conclusiones.

Herramientas: Python 3, pandas, numpy, matplotlib y Jupyter Notebook.

## Conclusiones y hallazgos relevantes

1. Proporción de entregas tardías: el 54,8% de los pedidos llega tarde. El 23,0% se adelanta, el 17,8% llega a tiempo y el 4,3% se cancela.
2. El modo de envio es el factor principal. El porcentaje de pedidos tardíos va de 38,1% (Standard Class) a 95,3% (First Class); Second Class llega a 76,7% y Same Day a 46,1%.
3. First Class promete 1 día y tarda 2; Second Class promete 2 y tarda 4; Same Day promete 0 y tarda 0,48 en promedio. Standard Class cumple en promedio (4 y 4). Las demoras se deben a plazos prometidos demasiado cortos más que a envíos lentos.
4. El porcentaje de pedidos tardíos es casi igual en todos los mercados, entre 54,1% y 55,3%.
5. La ganancia por ítem es casi igual con y sin retraso. El descuento promedio también y el monto por ítem tiene la misma mediana en ambos grupos. El 18,7% de los ítems genera pérdida.







