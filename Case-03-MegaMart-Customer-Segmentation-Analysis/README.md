# 📊 MegaMart Customer Segmentation Project

Análisis, segmentación y estrategias accionables basadas en datos de
clientes

## 📌 Descripción General

Este repositorio contiene el proyecto completo de segmentación de
clientes para **MegaMart**, cuyo objetivo es mejorar la efectividad de
las campañas de marketing mediante personalización. A partir de un
dataset de **3,000 clientes** con métricas de comportamiento, se
desarrolló un análisis end-to-end: carga de datos, preprocesamiento,
modelado, clustering, visualización y recomendaciones estratégicas.

## 🗂️ Contenido del Repositorio

    📁 megamart-segmentation/
    │
    ├── MegaMart_Segmentation.ipynb        # Notebook principal con todo el análisis
    ├── retail_customer_data.csv           # Dataset utilizado (3,000 clientes)
    │
    ├── Presentación Customer Segmentation Project.pdf   # Presentación ejecutiva
    ├── Resumen_Ejecutivo_MegaMart.pdf                  # Resumen ejecutivo del estudio
    │
    └── README.md                           # Documentación del repositorio

## 🎯 Objetivo del Proyecto

MegaMart ejecutaba campañas de marketing genéricas sin diferenciar
clientes, lo que afectaba negativamente la retención, el engagement y la
eficiencia del presupuesto.\
El propósito del proyecto fue **identificar segmentos de clientes
accionables** para personalizar campañas, aumentar la retención y
optimizar decisiones comerciales.

## 🔍 Metodología

### 1. Exploración de Datos

Variables incluidas: - Frecuencia de compra - Gasto total - Tamaño
promedio del carrito - Recencia - Actividad digital - Devoluciones -
Antigüedad

### 2. Preprocesamiento

-   Limpieza
-   Estandarización
-   Análisis de correlaciones
-   Opcional: reducción de dimensionalidad (PCA)

### 3. Modelado de Segmentación

-   K-Means como modelo principal
-   Métrica silhouette para determinar número óptimo de clusters
-   Interpretación de patrones de comportamiento

### 4. Identificación de Segmentos

Los clusters se interpretan como perfiles reales de negocio.

### 5. Recomendaciones Estratégicas

Para cada segmento, se diseñan estrategias de marketing y crecimiento.

## 🧩 Segmentos Identificados

1.  **High-Value Loyalists (17.4%)**
2.  **Low-Spend & Low-Engagement Buyers (23.1%)**
3.  **High Basket Explorers (14.3%)**
4.  **Mid-Frequency, High Email Responders (19.9%)**
5.  **New & Low-Activity Customers (25.3%)**

## 📈 Estrategias Recomendadas

### High-Value Loyalists

-   Programas VIP
-   Recomendaciones personalizadas
-   Envíos gratuitos o garantías extendidas

### Low-Spend & Low-Engagement Buyers

-   Campañas simples de activación
-   Mejoras en la experiencia de compra
-   A/B testing

### High Basket Explorers

-   Mejor información de producto
-   Bundles y promociones
-   Seguimiento post-compra

### Mid-Frequency, High Email Responders

-   Email marketing segmentado
-   Ofertas por volumen
-   Cross-selling digital

### New & Low-Activity Customers

-   Secuencia de bienvenida
-   Cupones de reactivación
-   Campañas de remarketing

## 📉 Impacto Esperado

-   Reducción del churn: **20--25%**
-   Aumento del engagement digital: **30--40%**
-   Reducción de devoluciones: **10--15%**
-   Uso más eficiente del presupuesto de marketing

## ▶️ Cómo Reproducir el Proyecto

### 1. Clonar el repositorio

    git clone https://github.com/tu-usuario/tu-repo.git
    cd tu-repo

### 2. Crear entorno virtual

    python -m venv env
    source env/bin/activate  # Mac/Linux
    env\Scripts\activate     # Windows

### 3. Instalar dependencias

    pip install -r requirements.txt

### 4. Ejecutar el notebook

Abrir:

    MegaMart_Segmentation.ipynb

## 📄 Archivos del Proyecto

-   Notebook de análisis
-   Resumen ejecutivo
-   Presentación ejecutiva
-   Dataset

## 👨‍💻 Equipo de Proyecto

-   Uziel Heredia Estrada\
-   Edgar Samuel Oropeza García\
-   Aquiba Samuel Benarroch Serfaty

## 🔗 Recursos Adicionales

Video del proyecto: https://enlace-video.com
