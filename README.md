# EverPeak Retail: Customer Segmentation & Business Architecture Analysis

## 📊 Descripción del Proyecto
Este repositorio contiene el análisis exploratorio, tratamiento avanzado de valores atípicos (outliers) e ingeniería de características (*Feature Engineering*) aplicado al dataset de retail **EverPeak**. El objetivo principal es transformar datos transaccionales crudos en insights accionables y segmentos de clientes estructurados para respaldar la toma de decisiones estratégicas del equipo comercial y financiero.

---

## 🛠️ Estructura del Proyecto
* `notebooks/everpeak_analysis.ipynb`: Notebook principal con el flujo completo de análisis, visualización y segmentación.
* `datasets/`: Contiene los archivos de datos limpios y procesados.
* `README.md`: Documentación oficial del proyecto.

---

## 🔍 Fases Metodológicas del Análisis

### 1. Diagnóstico y Visualización de Datos
Se evaluaron las distribuciones de las variables numéricas clave (`price`, `quantity`, `order_value`, `customer_age`) utilizando histogramas con curvas de densidad (KDE) y diagramas de caja (*boxplots*), identificando asimetrías a la derecha (*right-skewed*) características del sector retail, donde un pequeño porcentaje de transacciones concentra altos volúmenes de compra.

### 2. Tratamiento de Outliers (Winsorización)
* **Decisión de Negocio:** En lugar de eliminar registros extremos (lo que destruiría la visibilidad de los ingresos por clientes de alto valor o *whales*), se aplicó la técnica de **Winsorización** utilizando `np.clip()` al percentil 99. 
* **Impacto:** Esto permitió estabilizar la media y reducir la varianza excesiva para futuros modelos estadísticos, sin perder el valor de las transacciones legítimas de alta gama.

### 3. Feature Engineering (Segmentación de Clientes)
Se diseñaron funciones personalizadas en Python aplicadas fila por fila mediante `.apply(axis=1)` para clasificar la base de datos bajo criterios lógicos de negocio:
* **Segmentación por Gasto y Edad:** Clasificación de clientes en perfiles de valor (`Senior VIP`, `Junior VIP`, `Sr. Medium Value`, `Jr. Medium Value`, `Low Value`).
* **Segmentación por Volumen:** Separación del comportamiento transaccional según el número de unidades adquiridas cruzado con rangos de edad.

---

## 📈 Conclusiones Ejecutivas para el Negocio
1. **Comportamiento Asimétrico:** Las métricas de tendencia central muestran que el análisis basado exclusivamente en promedios puede estar sesgado por las compras de alto valor; el uso de medianas y percentiles ofrece una perspectiva más fiel del cliente típico de EverPeak.
2. **Oportunidades de Retención:** La identificación de segmentos VIP permite diseñar campañas de lealtad personalizadas y optimizar la asignación de recursos comerciales.

---

## 🚀 ¿Cómo reproducir este análisis?
1. Clona este repositorio o descarga el archivo `.ipynb`.
2. Asegúrate de tener instaladas las librerías requeridas en tu entorno de Python:
   ```bash
   pip install pandas numpy matplotlib seaborn
