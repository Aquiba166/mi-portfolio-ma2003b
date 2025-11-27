# Caso 1: Análisis Factorial - Satisfacción del Cliente

---

## 👥 Autores

- **Aquiba Samuel Benarroch Serfaty** - A01784240

- **Edgar Samuel Oropeza García** - A01660110

- **Uziel Heredia Estrada** - A01667072



---Este proyecto realiza un Análisis Factorial sobre un conjunto de datos de satisfacción del cliente con el objetivo de:



## 1. 🏢 Contexto del Negocio* Explorar la estructura subyacente de las variables.

* Determinar el número óptimo de factores mediante autovalores y Scree Plot.

### Descripción del Cliente y Problema* Evaluar la idoneidad del dataset con KMO y prueba de Bartlett.

Una empresa de servicios B2B necesita comprender los **factores subyacentes que impulsan la satisfacción de sus clientes empresariales**. Actualmente, la empresa recolecta datos a través de encuestas con 23 ítems de satisfacción, pero la cantidad de variables dificulta:* Extraer factores con método principal y rotación Varimax.

- Identificar qué aspectos priorizar* Interpretar factores y analizar su relación con outcomes del negocio.

- Comunicar resultados de forma clara a la dirección* Generar visualizaciones y conclusiones ejecutivas.

- Diseñar intervenciones focalizadas

---

### Importancia Estratégica del Análisis

| Aspecto | Impacto |## Estructura del Notebook

|---------|---------|

| **Retención de clientes** | Identificar drivers clave de satisfacción para reducir churn |1. EDA inicial del dataset

| **Asignación de recursos** | Focalizar inversiones en los factores más importantes |2. Pruebas de idoneidad (KMO, Bartlett)

| **Simplicidad operativa** | Reducir 23 variables a 5 factores manejables |3. Selección del número de factores (autovalores, varianza, scree plot)

| **Decisiones basadas en datos** | Pasar de intuición a insights cuantificables |4. Extracción y rotación de factores (Varimax)

5. Construcción de puntajes factoriales

---6. Visualizaciones

7. Conclusiones y recomendaciones

## 2. 🔬 Metodología

---

### Método Multivariado Aplicado

**Análisis Factorial Exploratorio (EFA)** con:## Tecnologías y Librerías Utilizadas

- Método de extracción: **Factores Principales**

- Rotación: **Varimax** (ortogonal)```

- Criterios de retención: Kaiser (eigenvalue > 1) + Scree PlotPython 3.x

NumPy

### Justificación de la ElecciónPandas

| Criterio | Justificación |Matplotlib

|----------|---------------|Seaborn

| **Tipo de problema** | Reducción de dimensionalidad con 23 variables correlacionadas |factor_analyzer

| **Objetivo** | Descubrir estructura latente (factores no observables) |```

| **Naturaleza de datos** | Variables continuas (escala 1-7) sin variable objetivo |

| **Alternativas descartadas** | PCA (no identifica factores latentes), Clusters (segmenta observaciones, no variables) |---



### Herramientas y Librerías Utilizadas## Cómo Ejecutar el Proyecto

```python

# Core### 1. Instalar dependencias

Python 3.x

NumPy, Pandas```

pip install numpy pandas matplotlib seaborn factor_analyzer

# Análisis Factorial```

factor_analyzer  # KMO, Bartlett, extracción, rotación

### 2. Ejecutar el notebook

# Visualización

Matplotlib, SeabornAbrir el archivo `.ipynb` usando Jupyter Notebook, JupyterLab o VSCode.



# Estadística---

statsmodels

sklearn.preprocessing.StandardScaler## Dataset

```

Se utiliza un dataset llamado `customer_satisfaction.csv` con variables relacionadas con percepción del cliente.

---Debe agregarse manualmente al proyecto.



## 3. 📊 Datos---



### Descripción del Dataset## Resultados Principales

| Característica | Valor |

|----------------|-------|* Identificación de factores principales de satisfacción.

| **Archivo** | `customer_satisfaction_data.csv` |* Matriz rotada e interpretación clara de cada factor.

| **Observaciones** | ~3,500 respuestas de encuesta |* Visualizaciones para comunicar resultados.

| **Variables de satisfacción** | 23 ítems (escala 1-7) |* Puntajes factoriales para segmentar clientes.

| **Variables outcome** | 5 (NPS, satisfacción general, renovación, etc.) |

| **Missing data** | ~5% (tratado con listwise deletion) |

---

### Variables Clave

## Equipo de Trabajo

#### Variables de Satisfacción (Input para FA)

| Grupo | Variables |**Team:** Equipo 2

|-------|-----------|

| **Técnicas** | `technical_expertise`, `problem_solving`, `innovation_solutions`, `technical_documentation`, `system_integration` |**Members:**

| **Relación** | `account_manager_responsive`, `executive_access`, `trust_reliability`, `long_term_partnership`, `communication_clarity` |

| **Proyecto** | `project_management`, `timeline_adherence`, `budget_control`, `quality_deliverables`, `change_management` |* Aquiba Samuel Benarroch Serfaty — A01784240

| **Valor/Costo** | `cost_transparency`, `value_for_money`, `roi_demonstration`, `competitive_pricing`, `billing_accuracy` |* Edgar Samuel Oropeza García — A01660110

| **Soporte** | `support_responsiveness`, `training_quality`, `documentation_help` |* Uziel Heredia Estrada — A01667072



#### Variables Outcome---

- `overall_satisfaction`, `nps_score`, `renewal_likelihood`, `revenue_growth_pct`, `referrals_generated`

## Recursos y Entregables

### 📖 Link al Diccionario de Datos

Ver sección de variables en el notebook: [`study_case_final.ipynb`](./study_case_final.ipynb)* Video de presentación: [https://youtu.be/1UJ_UAbBss0](https://youtu.be/1UJ_UAbBss0)

* Executive Summary: Disponible en Canvas

---* Dataset: customer_satisfaction.csv



## 4. 🎯 Hallazgos Principales---



### Hallazgos Clave

1. **✅ Datos altamente aptos para FA**: KMO = 0.92 (Excelente) y Test de Bartlett significativo (p < 0.001)

2. **📊 Se identificaron 5 factores latentes** que explican >65% de la varianza total:
   - Factor 1: **Competencia Técnica** (expertise, problem solving, innovación)
   - Factor 2: **Calidad de Relación** (account manager, confianza, comunicación)
   - Factor 3: **Gestión de Proyectos** (timelines, presupuesto, calidad)
   - Factor 4: **Percepción de Valor** (ROI, pricing, transparencia)
   - Factor 5: **Soporte Post-venta** (responsiveness, training, documentación)

3. **🔗 Estructura clara en bloques**: La matriz de correlación muestra agrupaciones naturales que coinciden con los factores extraídos

4. **📈 Factores con alta correlación con outcomes**: Los puntajes factoriales correlacionan significativamente con NPS y probabilidad de renovación

5. **⚖️ Balance de varianza**: Ningún factor domina excesivamente; distribución equilibrada de importancia

### Visualización Destacada

*Scree Plot disponible en el notebook - muestra un "codo" claro después del factor 5, validando la solución de 5 factores.*

### Métricas de Performance del Modelo

| Métrica | Valor | Interpretación |
|---------|-------|----------------|
| **KMO** | 0.92 | Excelente adecuación muestral |
| **Bartlett χ²** | Significativo (p < 0.001) | Variables correlacionadas |
| **Varianza explicada** | >65% | Buena captura de información |
| **Comunalidades** | >0.4 para todas las variables | Factores representan bien a las variables |
| **Cargas factoriales** | >0.5 para ítems principales | Estructura clara y definida |

---

## 5. 💼 Recomendaciones de Negocio

### Recomendaciones Accionables

| # | Recomendación | Factor Relacionado |
|---|---------------|-------------------|
| 1 | **Invertir en capacitación técnica del equipo** - Los clientes valoran altamente la expertise técnica. Implementar certificaciones y desarrollo continuo. | Competencia Técnica |
| 2 | **Fortalecer la figura del Account Manager** - La relación personal es un driver clave. Asegurar continuidad y responsiveness del AM asignado. | Calidad de Relación |
| 3 | **Mejorar transparencia en pricing y ROI** - Desarrollar dashboards de valor entregado y comunicar proactivamente el retorno de inversión. | Percepción de Valor |

### Impacto Esperado

| Área | Impacto Proyectado |
|------|-------------------|
| **Retención** | +10-15% en tasa de renovación al mejorar factores críticos |
| **NPS** | +5-10 puntos al focalizar en los 5 factores identificados |
| **Eficiencia** | Reducción de 23 métricas a 5 KPIs de satisfacción |
| **Decisiones** | Priorización clara de inversiones basada en datos |

### Próximos Pasos

1. **Corto plazo (1-2 meses)**
   - Crear dashboard ejecutivo con los 5 factores
   - Implementar tracking de puntajes factoriales por cliente
   
2. **Mediano plazo (3-6 meses)**
   - Diseñar intervenciones específicas por factor
   - Validar modelo con Análisis Factorial Confirmatorio (CFA)
   
3. **Largo plazo (6-12 meses)**
   - Integrar factores en modelo predictivo de churn
   - Segmentar clientes por perfil factorial (combinar con Clusters)

---

## 📎 Recursos y Entregables

| Recurso | Link |
|---------|------|
| **Notebook principal** | [`study_case_final.ipynb`](./study_case_final.ipynb) |
| **Dataset** | [`customer_satisfaction_data.csv`](./customer_satisfaction_data.csv) |
| **Resumen Ejecutivo** | [`Resumen_Ejecutivo.pdf`](./Resumen_Ejecutivo.pdf) |
| **Video presentación** | [YouTube](https://youtu.be/1UJ_UAbBss0) |

---

*Proyecto desarrollado para el curso MA2003B - Análisis Multivariado | Noviembre 2025*
