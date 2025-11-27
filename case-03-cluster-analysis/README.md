# Caso 3: Análisis de Clusters - Segmentación de Clientes MegaMart# 📊 MegaMart Customer Segmentation Project



## 👥 AutoresAnálisis, segmentación y estrategias accionables basadas en datos de

- **Aquiba Samuel Benarroch Serfaty** - A01784240clientes

- **Edgar Samuel Oropeza García** - A01660110

- **Uziel Heredia Estrada** - A01667072## 📌 Descripción General



---Este repositorio contiene el proyecto completo de segmentación de

clientes para **MegaMart**, cuyo objetivo es mejorar la efectividad de

## 1. 🏢 Contexto del Negociolas campañas de marketing mediante personalización. A partir de un

dataset de **3,000 clientes** con métricas de comportamiento, se

### Descripción del Cliente y Problemadesarrolló un análisis end-to-end: carga de datos, preprocesamiento,

**MegaMart** es una cadena de retail que ejecutaba **campañas de marketing genéricas** sin diferenciar entre tipos de clientes. Este enfoque resultaba en:modelado, clustering, visualización y recomendaciones estratégicas.



- Baja efectividad de campañas (mensajes no personalizados)## 🗂️ Contenido del Repositorio

- Altas tasas de churn sin identificar clientes en riesgo

- Desperdicio de presupuesto de marketing    📁 megamart-segmentation/

- Incapacidad de identificar clientes de alto valor para retención    │

    ├── MegaMart_Segmentation.ipynb        # Notebook principal con todo el análisis

### Importancia Estratégica del Análisis    ├── retail_customer_data.csv           # Dataset utilizado (3,000 clientes)

| Aspecto | Impacto |    │

|---------|---------|    ├── Presentación Customer Segmentation Project.pdf   # Presentación ejecutiva

| **Personalización** | Diseñar campañas específicas por tipo de cliente |    ├── Resumen_Ejecutivo_MegaMart.pdf                  # Resumen ejecutivo del estudio

| **Retención** | Identificar segmentos en riesgo de abandono |    │

| **Optimización de recursos** | Asignar presupuesto según valor del segmento |    └── README.md                           # Documentación del repositorio

| **Customer Lifetime Value** | Maximizar valor de clientes de alto potencial |

## 🎯 Objetivo del Proyecto

---

MegaMart ejecutaba campañas de marketing genéricas sin diferenciar

## 2. 🔬 Metodologíaclientes, lo que afectaba negativamente la retención, el engagement y la

eficiencia del presupuesto.\

### Método Multivariado AplicadoEl propósito del proyecto fue **identificar segmentos de clientes

**Análisis de Clusters** utilizando:accionables** para personalizar campañas, aumentar la retención y

- Algoritmo principal: **K-Means**optimizar decisiones comerciales.

- Selección de k: **Método del codo** + **Silhouette Score**

- Preprocesamiento: Estandarización de variables## 🔍 Metodología



### Justificación de la Elección### 1. Exploración de Datos

| Criterio | Justificación |

|----------|---------------|Variables incluidas: - Frecuencia de compra - Gasto total - Tamaño

| **Tipo de problema** | Segmentación sin variable objetivo predefinida |promedio del carrito - Recencia - Actividad digital - Devoluciones -

| **Objetivo** | Descubrir grupos naturales de clientes similares |Antigüedad

| **Naturaleza de datos** | Variables de comportamiento continuas |

| **Escalabilidad** | K-Means eficiente para 3,000+ observaciones |### 2. Preprocesamiento

| **Alternativas consideradas** | Clustering jerárquico (menos escalable), DBSCAN (parámetros sensibles) |

-   Limpieza

### Herramientas y Librerías Utilizadas-   Estandarización

```python-   Análisis de correlaciones

# Core-   Opcional: reducción de dimensionalidad (PCA)

Python 3.x

NumPy, Pandas### 3. Modelado de Segmentación



# Clustering-   K-Means como modelo principal

sklearn.cluster.KMeans-   Métrica silhouette para determinar número óptimo de clusters

sklearn.preprocessing.StandardScaler-   Interpretación de patrones de comportamiento

sklearn.metrics.silhouette_score

### 4. Identificación de Segmentos

# Reducción dimensional (visualización)

sklearn.decomposition.PCALos clusters se interpretan como perfiles reales de negocio.



# Visualización### 5. Recomendaciones Estratégicas

Matplotlib, Seaborn

```Para cada segmento, se diseñan estrategias de marketing y crecimiento.



---## 🧩 Segmentos Identificados



## 3. 📊 Datos1.  **High-Value Loyalists (17.4%)**

2.  **Low-Spend & Low-Engagement Buyers (23.1%)**

### Descripción del Dataset3.  **High Basket Explorers (14.3%)**

| Característica | Valor |4.  **Mid-Frequency, High Email Responders (19.9%)**

|----------------|-------|5.  **New & Low-Activity Customers (25.3%)**

| **Archivo** | `retail_customer_data.csv` |

| **Observaciones** | 3,000 clientes |## 📈 Estrategias Recomendadas

| **Variables** | Métricas de comportamiento de compra |

| **Período** | Datos históricos de transacciones |### High-Value Loyalists



### Variables Clave-   Programas VIP

-   Recomendaciones personalizadas

| Variable | Descripción | Tipo |-   Envíos gratuitos o garantías extendidas

|----------|-------------|------|

| `purchase_frequency` | Frecuencia de compra | Numérica |### Low-Spend & Low-Engagement Buyers

| `total_spend` | Gasto total acumulado | Numérica |

| `avg_basket_size` | Tamaño promedio del carrito | Numérica |-   Campañas simples de activación

| `recency` | Días desde última compra | Numérica |-   Mejoras en la experiencia de compra

| `digital_activity` | Nivel de actividad digital | Numérica |-   A/B testing

| `return_rate` | Tasa de devoluciones | Numérica |

| `customer_tenure` | Antigüedad como cliente | Numérica |### High Basket Explorers



### 📖 Link al Diccionario de Datos-   Mejor información de producto

Ver descripción completa en el notebook: [`MegaMart_Segmentation.ipynb`](./MegaMart_Segmentation.ipynb)-   Bundles y promociones

-   Seguimiento post-compra

---

### Mid-Frequency, High Email Responders

## 4. 🎯 Hallazgos Principales

-   Email marketing segmentado

### Hallazgos Clave-   Ofertas por volumen

-   Cross-selling digital

1. **📊 Se identificaron 5 segmentos distintivos** de clientes con perfiles comportamentales únicos

### New & Low-Activity Customers

2. **🏆 Segmento más valioso**: "High-Value Loyalists" (17.4%)

   - Alta frecuencia, alto gasto, baja recencia-   Secuencia de bienvenida

   - Prioridad para programas de retención VIP-   Cupones de reactivación

-   Campañas de remarketing

3. **⚠️ Segmento en riesgo**: "New & Low-Activity Customers" (25.3%)

   - Mayor proporción de clientes## 📉 Impacto Esperado

   - Requiere campañas de activación inmediata

-   Reducción del churn: **20--25%**

4. **📧 Oportunidad de email marketing**: "Mid-Frequency, High Email Responders" (19.9%)-   Aumento del engagement digital: **30--40%**

   - Alta respuesta a comunicaciones digitales-   Reducción de devoluciones: **10--15%**

   - Canal preferido para engagement-   Uso más eficiente del presupuesto de marketing



5. **🔄 Patrón de devoluciones**: "High Basket Explorers" (14.3%)## ▶️ Cómo Reproducir el Proyecto

   - Compras grandes pero con alta tasa de devolución

   - Necesitan mejor información de producto### 1. Clonar el repositorio



### Segmentos Identificados    git clone https://github.com/tu-usuario/tu-repo.git

    cd tu-repo

| Segmento | % Base | Características Clave |

|----------|--------|----------------------|### 2. Crear entorno virtual

| **High-Value Loyalists** | 17.4% | Alta frecuencia, alto gasto, clientes fieles |

| **Low-Spend & Low-Engagement** | 23.1% | Bajo gasto, poca interacción |    python -m venv env

| **High Basket Explorers** | 14.3% | Compras grandes, alta devolución |    source env/bin/activate  # Mac/Linux

| **Mid-Frequency Email Responders** | 19.9% | Responden bien a email marketing |    env\Scripts\activate     # Windows

| **New & Low-Activity** | 25.3% | Nuevos o inactivos, en riesgo de churn |

### 3. Instalar dependencias

### Visualización Destacada

    pip install -r requirements.txt

*Visualización de clusters en espacio PCA y perfiles radiales disponibles en el notebook.*

### 4. Ejecutar el notebook

### Métricas de Performance del Modelo

Abrir:

| Métrica | Valor | Interpretación |

|---------|-------|----------------|    MegaMart_Segmentation.ipynb

| **Número óptimo de clusters** | 5 | Determinado por elbow + silhouette |

| **Silhouette Score** | >0.3 | Separación aceptable entre clusters |## 📄 Archivos del Proyecto

| **Inercia** | Reducción significativa | Clusters compactos internamente |

| **Interpretabilidad** | Alta | Perfiles de negocio claramente diferenciados |-   Notebook de análisis

-   Resumen ejecutivo

----   Presentación ejecutiva

-   Dataset

## 5. 💼 Recomendaciones de Negocio

## 👨‍💻 Equipo de Proyecto

### Recomendaciones Accionables

-   Uziel Heredia Estrada\

| # | Recomendación | Segmento Target |-   Edgar Samuel Oropeza García\

|---|---------------|-----------------|-   Aquiba Samuel Benarroch Serfaty

| 1 | **Implementar programa VIP exclusivo** - Beneficios premium, acceso anticipado a ofertas, envío gratuito y atención personalizada para maximizar retención. | High-Value Loyalists |

| 2 | **Campaña de reactivación con incentivos** - Secuencia de emails con cupones progresivos y ofertas limitadas para recuperar clientes inactivos. | New & Low-Activity |## 🔗 Recursos Adicionales

| 3 | **Optimizar experiencia de producto** - Mejorar descripciones, fotos y guías de tallas para reducir devoluciones. Ofrecer bundles curados. | High Basket Explorers |

Video del proyecto: https://enlace-video.com

### Impacto Esperado

| Área | Impacto Proyectado |
|------|-------------------|
| **Reducción de churn** | 20-25% al intervenir en segmentos de riesgo |
| **Engagement digital** | +30-40% en segmento de email responders |
| **Reducción de devoluciones** | 10-15% en High Basket Explorers |
| **Eficiencia de marketing** | +25% ROI al personalizar por segmento |

### Próximos Pasos

1. **Corto plazo (1-2 meses)**
   - Implementar etiquetado de clientes por segmento en CRM
   - Diseñar campañas piloto para cada segmento
   
2. **Mediano plazo (3-6 meses)**
   - Medir impacto de campañas segmentadas vs. genéricas (A/B test)
   - Crear dashboards de monitoreo por segmento
   - Automatizar asignación de nuevos clientes a segmentos
   
3. **Largo plazo (6-12 meses)**
   - Evolución dinámica de segmentos (re-clustering periódico)
   - Integrar con modelo predictivo de churn
   - Desarrollar Customer Lifetime Value por segmento

---

## 📎 Recursos y Entregables

| Recurso | Link |
|---------|------|
| **Notebook principal** | [`MegaMart_Segmentation.ipynb`](./MegaMart_Segmentation.ipynb) |
| **Dataset** | [`retail_customer_data.csv`](./retail_customer_data.csv) |
| **Resumen Ejecutivo** | [`Resumen_Ejecutivo_MegaMart.pdf`](./Resumen_Ejecutivo_MegaMart.pdf) |
| **Presentación** | [`Presentación Customer Segmentation Project.pdf`](./Presentación%20Customer%20Segmentation%20Project.pdf) |

---

*Proyecto desarrollado para el curso MA2003B - Análisis Multivariado | Noviembre 2025*
