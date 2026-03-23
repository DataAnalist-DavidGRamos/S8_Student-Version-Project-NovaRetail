# 🛒 NovaRetail+ Customer Behavior Analytics

![Data Science](https://img.shields.io/badge/Data%20Science-Analysis-blue)
![Python](https://img.shields.io/badge/Python-3.x-yellow)
![Libraries](https://img.shields.io/badge/Libraries-Pandas%20%7C%20Seaborn%20%7C%20Scipy-orange)

## 📌 Resumen del Proyecto

Este proyecto consiste en un **análisis correlacional exploratorio** de la base de datos de clientes de **NovaRetail+**, una plataforma de comercio electrónico líder en Latinoamérica con millones de usuarios activos. 

El equipo de *Crecimiento y Retención* necesita comprender el comportamiento de compra de los usuarios al cierre del año 2024. El objetivo principal es responder a la siguiente pregunta de negocio:
> **¿Qué factores del comportamiento del cliente están más fuertemente asociados con el ingreso anual generado?**

A través de un análisis forense de los datos utilizando Python, identificamos patrones demográficos y transaccionales para generar propuestas de valor que mejoren la tasa de conversión y prevengan el abandono (churn).

## 🗂️ Estructura del Dataset

El conjunto de datos (`novaretail_comportamiento_clientes_2024.csv`) consta de **15,000 registros** y 12 columnas:
- `id_cliente`: Identificador único.
- `edad`, `nivel_ingreso`: Perfil demográfico.
- `visitas_mes`, `compras_mes`: Hábitos de tráfico y transacción.
- `gasto_publicidad_dirigida`: Inversión en marketing por usuario.
- `satisfaccion`: Calificación (1 a 5).
- `miembro_premium`, `abandono`: Variables binarias sobre el estatus del usuario.
- `tipo_dispositivo`, `region`: Variables categóricas que brindan contexto tecnológico y territorial.
- **`ingreso_anual` (Variable Objetivo):** Impacto monetario del cliente.

## 🔬 Metodología y Herramientas Estadísticas

Con una rigurosa sujeción a las matemáticas subyacentes, evitamos asumir causalidad y nos enfocamos en medir la magnitud de asociación utilizando librerías oficiales (`scipy.stats`, `pandas`, `numpy`):

1. **Variables Numéricas Continuas:** 
   - **Coeficiente de Pearson** y **Spearman** (para detectar relaciones estrictamente lineales vs monotónicas en métricas como `visitas_mes` o `compras_mes`).
2. **Variables Categóricas Nominales:** 
   - **V de Cramér**, extrayendo la matriz de confusión (Crosstab) y utilizando el valor $\chi^2$ (Chi-cuadrado) (`chi2_contingency`) para medir la asociación territorial y de dispositivos.
3. **Variables Mixtas (Binaria vs Continua):**
   - **Coeficiente de Correlación Punto-biserial** (`pointbiserialr` de `scipy.stats`), una aproximación premium para entender el impacto exacto del estatus `Premium` o `Abandono` sobre el volumen de `ingreso_anual`.

## 🚀 Principales Hallazgos (Business Insights)

* **🔄 Recurrencia Transaccional:** Existe una correlación de casi el 0.97 entre `compras_mes` y el ingreso anual, consolidando a la recurrencia como el pilar fundamental del e-commerce.
* **📱 Dominio Móvil:** El ~65% de la base transacciona vía dispositivos móviles, sugiriendo una prioridad inmediata en UI/UX mobile-first.
* **📢 Efecto Embudo Publicitario:** El `gasto_publicidad_dirigida` correlaciona en 0.58 con `visitas_mes`, demostrando ser una fuerza de tracción valiosa, pero apenas un 0.20 final con `ingreso_anual` (baja fuerza de cierre de venta inherente).
* **📉 Perfil de Abandono (Churn):** Sorpresivamente, el ~15% de usuarios que nos abandonan presentaban un volumen de compras y engagement *ligeramente superior* (~+2%) a la media retenida. El churn de NovaRetail+ castiga a "power users", lo que levanta alertas rojas sobre fricciones post-compra operativas o de atención.

## 🛠️ Cómo Visualizar

Puedes observar el código paso a paso y la interpretación de cada celda abriendo el archivo oficial:
[📔 **S8_Student Version-Project-NovaRetail.ipynb**](./S8_Student%20Version-Project-NovaRetail.ipynb)
*(Asegúrate de visualizarlo desde un renderizador compatible o localmente en Jupyter Notebook / VS Code).*

---
> **_"Fiel al análisis de datos, ausente de fantasmas y con rigor científico."_**
