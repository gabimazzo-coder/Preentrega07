Análisis de Clientes mediante RFM con Tendencia de Gasto en SQLite y Pandas

Este repositorio contiene un script en Python que implementa una consulta SQL avanzada para calcular las métricas de 
Recency (Recencia), Frequency (Frecuencia) y Monetary (Monetario), añadiendo una métrica personalizada de Tendencia de Gasto
(Trend). El entorno se monta completamente en memoria utilizando sqlite3 y los resultados se procesan con pandas.


Descripción del Proyecto

El código simula una base de datos relacional con información de usuarios y órdenes de compra para realizar un análisis de segmentación de clientes (RFM).
La principal innovación de este script es el cálculo de la tendencia, la cual compara el gasto del último mes activo del usuario contra su promedio histórico
mensual para identificar si está gastando más o menos de lo habitual.

Estructura de Datos Simulada
El script crea y conecta automáticamente una base de datos SQLite en memoria (:memory:) con las siguientes tablas:
• users: Contiene el identificador único de los usuarios (user_id).
• orders: Almacena el historial de compras de los usuarios con las columnas order_id, user_id, order_date y total_amount.


Métricas Calculadas en la Consulta SQL

La consulta utiliza Expresiones de Tabla Comunes (CTEs) y Funciones de Ventana para devolver los siguientes campos por cada usuario:
1. user_id: Identificador único del cliente.
2. recency: Días transcurridos entre la fecha de análisis (2026-10-01) y la última compra del usuario. Si no hay compras, se asigna 999.
3. frequency: Cantidad total de órdenes de compra únicas realizadas.
4. monetary: Suma total del dinero gastado por el cliente.
5. trend: Diferencia entre el gasto del último mes con actividad y el promedio mensual histórico del usuario. Un valor positivo indica incremento en sus compras;
6. un valor negativo indica desaceleración.

7. Requisitos
8. Para ejecutar este script, necesitas tener instalado Python 3 junto con la biblioteca pandas.
