# 🛒 Análisis de Base de Datos E-Commerce | SQL y Análisis de Negocio

### Transformando datos en decisiones estratégicas

[![SQL](https://img.shields.io/badge/SQL-SQLite-07405E?style=for-the-badge\&logo=sqlite\&logoColor=white)](https://www.sqlite.org/)
[![Python](https://img.shields.io/badge/Python-Análisis_de_Datos-3776AB?style=for-the-badge\&logo=python\&logoColor=white)](https://www.python.org/)
[![Google Colab](https://img.shields.io/badge/Google_Colab-Notebook-F9AB00?style=for-the-badge\&logo=googlecolab\&logoColor=white)](https://colab.research.google.com/)

Proyecto de análisis de datos orientado a comprender el desempeño comercial de una empresa de comercio electrónico mediante consultas SQL, análisis de ventas, evaluación del comportamiento de los clientes y revisión de inventario.

📓 **[Abrir proyecto en Google Colab](https://colab.research.google.com/github/sergioingmeca-cyber/E-Commerce-Database-Project/blob/main/E_Commerce_Database_Project.ipynb)** | 💻 **[Ver repositorio en GitHub](https://github.com/sergioingmeca-cyber/E-Commerce-Database-Project)**

---

## 🎯 1. Problema de negocio

Una empresa de comercio electrónico necesita comprender qué factores impulsan sus ingresos, cuáles son los productos y categorías con mejor desempeño, qué clientes generan mayor valor y dónde existen oportunidades para mejorar la gestión del inventario.

El reto consiste en transformar los datos transaccionales almacenados en una base de datos relacional en información útil para la toma de decisiones comerciales.

**Objetivo del proyecto:** utilizar SQL para explorar la base de datos, calcular indicadores clave de desempeño (KPI), identificar productos y clientes destacados, evaluar la tasa de recompra y proponer acciones orientadas a mejorar los resultados del negocio.

## 🗂️ 2. Descripción de los datos

El proyecto utiliza una base de datos SQLite denominada `store.db`, organizada en cinco tablas principales.

| Tabla         | Descripción                                                |
| ------------- | ---------------------------------------------------------- |
| `customers`   | Información de los clientes, ubicación y fecha de registro |
| `orders`      | Identificadores de pedidos, clientes, fechas y estados     |
| `order_items` | Productos comprados, cantidades y precios unitarios        |
| `products`    | Nombres de productos, categorías, precios y existencias    |
| `categories`  | Nombres e identificadores de las categorías de productos   |

### Dimensión de la base de datos

| Indicador            | Registros |
| -------------------- | --------: |
| Clientes registrados |       200 |
| Pedidos              |       800 |
| Líneas de pedido     |     2.456 |
| Productos            |        70 |
| Categorías           |         7 |
| Clientes con compras |       197 |

Las tablas se relacionaron mediante sus identificadores para consolidar la información transaccional y calcular indicadores comerciales.

## 🔎 3. Preguntas de negocio

El análisis se desarrolló para responder las siguientes preguntas:

* ¿Cómo evolucionan los ingresos mensuales?
* ¿Qué categorías generan mayores ingresos?
* ¿Qué productos tienen el mayor y menor ingreso por ventas?
* ¿Quiénes son los clientes de mayor valor?
* ¿Cuál es la tasa de recompra de los clientes?
* ¿Qué productos tienen menores niveles de inventario?
* ¿Cuáles son los tres productos con mayores ingresos dentro de cada categoría?
* ¿Qué porcentaje de los ingresos representa cada cliente?

## 🧠 4. Técnicas SQL aplicadas

El proyecto demuestra el uso de consultas SQL para resolver preguntas reales de negocio.

### Exploración de datos

* Identificación de las tablas disponibles mediante `sqlite_master`.
* Exploración de la estructura y el contenido de las tablas.
* Identificación de relaciones entre clientes, pedidos, productos y categorías.

### Agregación de datos

* `SUM()` para calcular ingresos y unidades vendidas.
* `COUNT()` y `COUNT(DISTINCT ...)` para contar pedidos, clientes y productos.
* `GROUP BY` para agrupar resultados por mes, categoría, producto y cliente.
* `ORDER BY` y `LIMIT` para identificar productos con mayor y menor facturación.

### Combinación de tablas

Uso de `JOIN` para relacionar varias tablas y enriquecer el análisis. Por ejemplo, se conectaron los detalles de los pedidos con las tablas de productos y categorías para calcular los ingresos por categoría.

### Expresiones de tabla comunes (CTE)

Uso de `WITH` para organizar consultas complejas en pasos más claros, especialmente en el análisis de ingresos por cliente y la clasificación de productos.

### Funciones de ventana

* `RANK()` para clasificar productos dentro de cada categoría.
* `SUM() OVER()` para calcular la participación porcentual de los clientes sobre los ingresos totales.

### Funciones de fecha y tratamiento de valores nulos

* `STRFTIME()` para agrupar los ingresos por año y mes.
* `COALESCE()` para manejar valores nulos en las cantidades y los precios unitarios.

### Integración con Python

Uso de `sqlite3` para conectar con la base de datos y de `pandas` para ejecutar consultas SQL y visualizar los resultados en Google Colab.

## 📊 5. Principales resultados

### 5.1. Evolución de los ingresos

* **Ingresos totales:** $875.798,71.
* **Promedio mensual reportado:** $35.031,95.
* **Mes con mayores ingresos:** junio de 2025, con $64.571,88.
* **Mes con menores ingresos:** julio de 2024, con $10.835,49.

Los ingresos presentan variaciones importantes a lo largo del periodo analizado. Junio de 2025 registra el mejor desempeño mensual, mientras que julio de 2024 presenta la menor facturación.

**Oportunidad de negocio:** investigar los factores asociados a los meses de mayor y menor desempeño para mejorar la planificación comercial.

### 5.2. Ingresos por categoría

| Categoría              |    Ingresos |
| ---------------------- | ----------: |
| Home & Kitchen         | $137.363,66 |
| Sports & Outdoors      | $135.881,01 |
| Toys & Games           | $132.302,32 |
| Clothing               | $126.662,31 |
| Beauty & Personal Care | $118.815,98 |
| Electronics            | $117.818,16 |
| Books                  | $106.955,27 |

**Hallazgo:** Home & Kitchen es la categoría con mayores ingresos, mientras que Books presenta la menor facturación.

Estos resultados representan ingresos por ventas, no rentabilidad neta. Para determinar qué categoría genera mayor beneficio, sería necesario incorporar información sobre costos y márgenes.

### 5.3. Productos con mayores ingresos

| Posición | Producto        |   Ingresos |
| -------: | --------------- | ---------: |
|        1 | Yoga Mat        | $35.373,00 |
|        2 | Building Blocks | $29.079,63 |
|        3 | Monitor         | $28.971,80 |
|        4 | Keyboard        | $27.712,45 |
|        5 | Lamp            | $26.686,22 |

**Hallazgo:** Yoga Mat lidera la generación de ingresos entre los productos analizados y también registra el mayor número de unidades vendidas, con 130 unidades.

### 5.4. Productos con menores ingresos

| Producto  |  Ingresos |
| --------- | --------: |
| Charger   |   $506,60 |
| RC Car    |   $776,05 |
| Guidebook | $1.051,39 |
| Comic     | $1.624,52 |
| Art Set   | $1.828,60 |

Charger presenta los menores ingresos. Este resultado permite identificar un producto cuyo desempeño merece una revisión adicional antes de tomar decisiones sobre precios, promociones o permanencia en el catálogo.

### 5.5. Clientes de mayor valor

| Cliente       | Ingresos acumulados | Participación |
| ------------- | ------------------: | ------------: |
| Beth Daniels  |          $13.802,34 |        1,58 % |
| Mark Brown    |          $13.711,83 |        1,57 % |
| Barbara Parks |          $12.076,32 |        1,38 % |
| Donald Shah   |           $9.985,81 |        1,14 % |
| Anita Baxter  |           $9.784,54 |        1,12 % |

**Hallazgo:** Beth Daniels es la cliente con mayores ingresos acumulados, seguida de cerca por Mark Brown.

El cálculo de participación permite medir cuánto aporta cada cliente a los ingresos totales e identificar oportunidades para desarrollar estrategias de fidelización.

### 5.6. Tasa de recompra

| Indicador                       |  Resultado |
| ------------------------------- | ---------: |
| Clientes que realizaron compras |        197 |
| Clientes recurrentes            |        184 |
| Clientes con una sola compra    |         13 |
| **Tasa de recompra**            | **93,4 %** |

La tasa de recompra se calculó como el porcentaje de clientes compradores que realizaron al menos dos pedidos diferentes.

El resultado refleja una elevada proporción de clientes recurrentes dentro de los datos analizados. Para comprender mejor la retención, sería conveniente complementar este indicador con la frecuencia de compra y el tiempo transcurrido entre pedidos.

### 5.7. Análisis de inventario

| Producto          | Existencias |
| ----------------- | ----------: |
| Poetry Collection |           3 |
| Coffee Maker      |           9 |
| Comic             |          10 |
| Jacket            |         500 |

Poetry Collection, Coffee Maker y Comic presentan los niveles de inventario más bajos. Por otro lado, Jacket registra las mayores existencias entre los productos analizados.

**Oportunidad de negocio:** contrastar las existencias con la velocidad de venta, los tiempos de reposición y la demanda esperada para identificar posibles riesgos de desabastecimiento o exceso de inventario.

## 💡 6. Recomendaciones de negocio

### 1. Mejorar la planificación de ventas

Analizar los meses con variaciones significativas en los ingresos e identificar posibles patrones estacionales para planificar campañas y disponibilidad de productos.

### 2. Optimizar el desempeño por categoría

Profundizar en los factores que explican el buen desempeño de Home & Kitchen y evaluar oportunidades para mejorar la facturación de Books. Incorporar costos y márgenes antes de concluir cuál es la categoría más rentable.

### 3. Fortalecer la estrategia de productos

Mantener seguimiento sobre productos destacados como Yoga Mat e investigar el bajo desempeño de Charger para determinar si se justifican acciones comerciales.

### 4. Desarrollar estrategias de fidelización

Identificar clientes de alto valor y diseñar acciones de fidelización. Complementar los ingresos acumulados con métricas de frecuencia y recencia para comprender mejor el comportamiento de compra.

### 5. Optimizar la gestión del inventario

Revisar los niveles de existencias de Poetry Collection, Coffee Maker y Comic, teniendo en cuenta la demanda y los tiempos de reposición. Establecer niveles mínimos de inventario según el comportamiento de las ventas.

## ⚙️ 7. Flujo de trabajo

```text
Base de datos SQLite
        ↓
Exploración de tablas
        ↓
Relación de datos mediante JOIN
        ↓
Cálculo de ingresos e indicadores
        ↓
Análisis por mes, categoría,
producto y cliente
        ↓
CTE y funciones de ventana
        ↓
Identificación de hallazgos
        ↓
Recomendaciones de negocio
```

## 🛠️ 8. Herramientas y habilidades

**Herramientas utilizadas**

* SQL
* SQLite
* Python
* pandas
* sqlite3
* Google Colab

**Habilidades técnicas**

* Consulta y exploración de bases de datos relacionales.
* Unión de múltiples tablas.
* Agregación y agrupación de información.
* Expresiones de tabla comunes (CTE).
* Funciones de ventana y clasificación.
* Análisis temporal.
* Tratamiento de valores nulos.
* Cálculo de indicadores clave de desempeño (KPI).
* Análisis de ventas, clientes e inventario.

**Habilidades de negocio**

* Definición de problemas de negocio.
* Análisis del desempeño comercial.
* Identificación de clientes de mayor valor.
* Evaluación del comportamiento de recompra.
* Interpretación de resultados.
* Formulación de recomendaciones basadas en datos.

## 🏁 9. Conclusión

Este proyecto demuestra cómo SQL permite transformar datos relacionales de comercio electrónico en información relevante para la toma de decisiones.

Mediante consultas, uniones de tablas, agregaciones, CTE y funciones de ventana, fue posible identificar categorías con mayores ingresos, productos destacados, clientes de alto valor, comportamiento de recompra y oportunidades para mejorar la gestión del inventario.

El proyecto refleja una habilidad fundamental para un analista de datos: **conectar las herramientas técnicas con preguntas de negocio y convertir los resultados del análisis en recomendaciones accionables.**

---

## 👨‍💻 Sobre mí

**Sergio Iván Ramírez Moreno**
Analista de Datos en formación | Ingeniero Mecánico | Especialista en Gerencia de Proyectos

Estoy desarrollando mi portafolio mediante proyectos prácticos enfocados en SQL, Python, análisis de datos e inteligencia de negocios, con el objetivo de apoyar la toma de decisiones basada en evidencia.

* **GitHub:** [sergioingmeca-cyber](https://github.com/sergioingmeca-cyber)
* **LinkedIn:** [Sergio Ramírez](https://www.linkedin.com/in/sergio-ramirez-b72744343/)
* **Portafolio:** [Mi portafolio como analista de datos](https://sergioingmeca-cyber.github.io/portafolio/)

¡Gracias por visitar mi proyecto!
