# Caso 2: Análisis Discriminante - Riesgo Crediticio LendSmart

## 👥 Autores
- **Aquiba Samuel Benarroch Serfaty** - A01784240
- **Edgar Samuel Oropeza García** - A01660110
- **Uziel Heredia Estrada** - A01667072

---

## 1. 🏢 Contexto del Negocio

### Descripción del Cliente y Problema
**LendSmart** es una empresa fintech especializada en préstamos personales que enfrenta el desafío de **predecir el riesgo de incumplimiento (default)** de los solicitantes de crédito. El problema actual:

- Alta tasa de morosidad que impacta la rentabilidad
- Proceso de evaluación crediticia poco eficiente
- Necesidad de automatizar decisiones de aprobación/rechazo
- Falta de claridad sobre qué variables son más predictivas del riesgo

### Importancia Estratégica del Análisis
| Aspecto | Impacto |
|---------|---------|
| **Reducción de pérdidas** | Identificar solicitantes de alto riesgo antes de aprobar créditos |
| **Eficiencia operativa** | Automatizar decisiones con modelo estadístico robusto |
| **Interpretabilidad** | Entender qué factores aumentan/reducen el riesgo de default |
| **Regulación** | Modelo explicable para cumplimiento normativo (vs. black-box ML) |

---

## 2. 🔬 Metodología

### Método Multivariado Aplicado
**Análisis Discriminante** comparando dos variantes:
- **LDA (Linear Discriminant Analysis)**: Asume covarianzas iguales entre clases
- **QDA (Quadratic Discriminant Analysis)**: Permite covarianzas diferentes

### Justificación de la Elección
| Criterio | Justificación |
|----------|---------------|
| **Tipo de problema** | Clasificación binaria supervisada (default vs. no default) |
| **Variable objetivo** | Categórica binaria (`loan_status`: 0 o 1) |
| **Interpretabilidad** | LDA proporciona coeficientes interpretables para cada variable |
| **Supuestos** | Posibilidad de comparar LDA vs QDA según homogeneidad de covarianzas |
| **Alternativas consideradas** | Regresión logística (similar), árboles (menos interpretables) |

### Herramientas y Librerías Utilizadas
```python
# Core
Python 3.x
NumPy, Pandas

# Machine Learning
sklearn.discriminant_analysis.LinearDiscriminantAnalysis
sklearn.discriminant_analysis.QuadraticDiscriminantAnalysis
sklearn.model_selection.train_test_split
sklearn.preprocessing.StandardScaler

# Evaluación
sklearn.metrics (confusion_matrix, classification_report, roc_curve, auc)

# Visualización
Matplotlib, Seaborn
```

---

## 3. 📊 Datos

### Descripción del Dataset
| Característica | Valor |
|----------------|-------|
| **Archivo** | `credit_risk_data-1.csv` |
| **Observaciones** | 2,500 solicitudes de préstamo |
| **Período** | 2022 - 2024 |
| **Variable objetivo** | `loan_status` (0 = buen pagador, 1 = default) |
| **Split** | 80% train / 20% test (estratificado) |

### Variables Clave

| Categoría | Variables | Descripción |
|-----------|-----------|-------------|
| **Financieras** | `loan_amount`, `annual_income`, `debt_to_income_ratio`, `savings_ratio`, `asset_value` | Situación financiera del solicitante |
| **Historial Crediticio** | `credit_score`, `credit_utilization`, `payment_history_score`, `open_credit_lines` | Comportamiento crediticio pasado |
| **Empleo y Estabilidad** | `employment_years`, `job_stability_score`, `residential_stability` | Estabilidad laboral y residencial |
| **Demográficas** | `age`, `education_level`, `marital_status` | Características del solicitante |
| **Target** | `loan_status` | 0 = Cumple, 1 = Incumple (default) |

### 📖 Link al Diccionario de Datos
Ver descripción completa en el notebook: [`LendSmart_Credit_Risk_Analysis.ipynb`](./LendSmart_Credit_Risk_Analysis.ipynb)

---

## 4. 🎯 Hallazgos Principales

### Hallazgos Clave

1. **🏆 Ambos modelos (LDA y QDA) lograron clasificación perfecta** con AUC = 1.000, indicando una separación lineal clara entre buenos y malos pagadores

2. **📊 Las 5 variables más predictivas del riesgo** (por magnitud de coeficientes LDA):
   - `payment_history_score` (-15.47) → Reduce riesgo significativamente
   - `job_stability_score` (-13.05) → Mayor estabilidad = menor riesgo
   - `credit_utilization` (+11.77) → Alto uso de crédito = mayor riesgo
   - `debt_to_income_ratio` (+4.47) → Alta deuda/ingreso = mayor riesgo
   - `credit_score` (-3.98) → Mejor score = menor riesgo

3. **✅ LDA es suficiente**: A pesar de que las covarianzas no son perfectamente homogéneas, LDA iguala el rendimiento de QDA

4. **🔍 Interpretación consistente con teoría crediticia**: Variables de comportamiento pasado (payment_history) y estabilidad (job_stability) son los mejores predictores

5. **⚠️ Resultados "perfectos" requieren validación adicional**: AUC = 1.0 sugiere datos muy separables o posible sobreajuste

### Visualización Destacada

*Curvas ROC y matrices de confusión disponibles en el notebook - ambos modelos muestran clasificación perfecta en el conjunto de prueba.*

### Métricas de Performance del Modelo

| Métrica | LDA | QDA |
|---------|-----|-----|
| **Accuracy** | 1.000 | 1.000 |
| **Precision (clase 1)** | 1.000 | 1.000 |
| **Recall (clase 1)** | 1.000 | 1.000 |
| **F1-Score** | 1.000 | 1.000 |
| **AUC-ROC** | 1.000 | 1.000 |

**Modelo Seleccionado: LDA** por su mayor interpretabilidad y menor complejidad.

---

## 5. 💼 Recomendaciones de Negocio

### Recomendaciones Accionables

| # | Recomendación | Variable Clave |
|---|---------------|----------------|
| 1 | **Priorizar historial de pagos en evaluación crediticia** - Es el predictor más fuerte. Solicitar reportes de buró y ponderar fuertemente el comportamiento de pago histórico. | `payment_history_score` |
| 2 | **Verificar estabilidad laboral rigurosamente** - Implementar validación de empleo actual y antigüedad. Considerar riesgo adicional para solicitantes con <2 años en puesto actual. | `job_stability_score`, `employment_years` |
| 3 | **Establecer límites de utilización de crédito** - Rechazar o revisar manualmente solicitudes con `credit_utilization` > 70% y `debt_to_income_ratio` > 40%. | `credit_utilization`, `debt_to_income_ratio` |

### Impacto Esperado

| Área | Impacto Proyectado |
|------|-------------------|
| **Tasa de default** | Reducción potencial del 80-90% al identificar correctamente solicitantes de alto riesgo |
| **Tiempo de decisión** | Automatización permite decisiones en minutos vs. días |
| **Costo operativo** | Reducción de revisiones manuales para casos claros |
| **Cumplimiento** | Modelo interpretable facilita explicar rechazos a reguladores |

### Próximos Pasos

1. **Corto plazo (1-2 meses)**
   - Implementar modelo LDA en sistema de scoring
   - Definir umbrales de probabilidad para aprobación automática vs. revisión manual
   
2. **Mediano plazo (3-6 meses)**
   - Validar modelo con datos completamente nuevos (out-of-time validation)
   - Implementar validación cruzada k-fold para confirmar robustez
   - Monitorear performance en producción
   
3. **Largo plazo (6-12 meses)**
   - Considerar técnicas de ensemble si aparecen casos límite
   - Actualizar modelo con nuevos datos de default
   - Explorar segmentación por tipo de préstamo

---

## 📎 Recursos y Entregables

| Recurso | Link |
|---------|------|
| **Notebook principal** | [`LendSmart_Credit_Risk_Analysis.ipynb`](./LendSmart_Credit_Risk_Analysis.ipynb) |
| **Dataset** | [`credit_risk_data-1.csv`](./credit_risk_data-1.csv) |
| **Resumen Ejecutivo** | [`Resumen_Ejecutivo_LendSmart.pdf`](./Resumen_Ejecutivo_LendSmart.pdf) |
| **Presentación** | [`Análisis de Riesgo Crediticio de LendSmart.pptx.pdf`](./Análisis%20de%20Riesgo%20Crediticio%20de%20LendSmart.pptx.pdf) |

---

*Proyecto desarrollado para el curso MA2003B - Análisis Multivariado | Noviembre 2025*
