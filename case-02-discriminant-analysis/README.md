# Caso 2: Análisis de Riesgo Crediticio - LendSmart

## 📋 Descripción del Proyecto

Este proyecto implementa un análisis de riesgo crediticio para **LendSmart**, una empresa fintech, utilizando técnicas de **Análisis Discriminante Lineal (LDA)** y **Análisis Discriminante Cuadrático (QDA)** para predecir el comportamiento de pago de los solicitantes de crédito.

## 👥 Autores

- **Aquiba Samuel Benarroch Serfaty** 
- **Edgar Samuel Oropeza García**
- **Uziel Heredia Estrada**

## 📅 Fecha

Noviembre 2025

## 📁 Estructura del Proyecto

```
case-02-discriminant-analysis/
├── README.md
├── LendSmart_Credit_Risk_Analysis.ipynb    # Notebook principal con el análisis
├── credit_risk_data-1.csv                  # Dataset de riesgo crediticio
├── Análisis de Riesgo Crediticio de LendSmart.pptx.pdf  # Presentación
└── Resumen_Ejecutivo_LendSmart.pdf         # Resumen ejecutivo
```

## 📊 Dataset

El dataset contiene información de **2,500 solicitudes de préstamo** procesadas por LendSmart entre 2022 y 2024.

### Variables Principales

| Categoría | Variables |
|-----------|-----------|
| **Financieras** | `loan_amount`, `annual_income`, `debt_to_income_ratio`, `savings_ratio`, `asset_value` |
| **Historial Crediticio** | `credit_score`, `credit_utilization`, `payment_history_score`, `open_credit_lines` |
| **Empleo y Estabilidad** | `employment_years`, `job_stability_score`, `residential_stability` |
| **Demográficas** | `age`, `education_level`, `marital_status` |
| **Variable Objetivo** | `loan_status` (0 = buen pagador, 1 = default) |

## 🔬 Metodología

### 1. Análisis Exploratorio de Datos (EDA)
- Distribución de la variable objetivo
- Análisis de variables continuas y categóricas por clase
- Matriz de correlación entre variables numéricas

### 2. Preprocesamiento
- One-hot encoding para variables categóricas
- División train/test (80/20) con estratificación
- Estandarización de variables numéricas

### 3. Supuestos Estadísticos
- **Normalidad Multivariante**: Verificación de distribuciones
- **Homogeneidad de Covarianzas**: Análisis de variabilidad por clase

### 4. Modelado
- **LDA (Linear Discriminant Analysis)**: Asume covarianza compartida
- **QDA (Quadratic Discriminant Analysis)**: Permite covarianzas diferentes por clase

### 5. Evaluación
- Matrices de confusión
- Classification Report (Precision, Recall, F1-Score)
- Curvas ROC y AUC

## 📈 Resultados

| Modelo | Accuracy | Recall | Precision | AUC |
|--------|----------|--------|-----------|-----|
| **LDA** | 1.000 | 1.000 | 1.000 | 1.000 |
| **QDA** | 1.000 | 1.000 | 1.000 | 1.000 |

### Variables más Influyentes (LDA)

| Ranking | Variable | Efecto |
|---------|----------|--------|
| 1 | `payment_history_score` | ⬇️ Reduce riesgo |
| 2 | `job_stability_score` | ⬇️ Reduce riesgo |
| 3 | `credit_utilization` | ⬆️ Aumenta riesgo |
| 4 | `debt_to_income_ratio` | ⬆️ Aumenta riesgo |
| 5 | `credit_score` | ⬇️ Reduce riesgo |

## ✅ Conclusión

**Modelo Seleccionado: LDA (Linear Discriminant Analysis)**

**Justificación:**
- Ambos modelos alcanzaron rendimiento perfecto (AUC = 1.000)
- LDA ofrece mayor **interpretabilidad** y **simplicidad**
- Las clases presentan separación lineal clara
- Menor complejidad computacional

## 🛠️ Tecnologías Utilizadas

- **Python 3.x**
- **Pandas** - Manipulación de datos
- **NumPy** - Operaciones numéricas
- **Matplotlib/Seaborn** - Visualización
- **Scikit-learn** - Modelos de Machine Learning
  - `LinearDiscriminantAnalysis`
  - `QuadraticDiscriminantAnalysis`
  - Métricas de evaluación

## 🚀 Cómo Ejecutar

1. Asegúrate de tener Python 3.x instalado
2. Instala las dependencias:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn
   ```
3. Abre el notebook `LendSmart_Credit_Risk_Analysis.ipynb` en Jupyter
4. Ejecuta todas las celdas secuencialmente

## 📚 Referencias

- Análisis Discriminante Lineal y Cuadrático
- Scikit-learn Documentation
- Teoría de Riesgo Crediticio

---

*Proyecto desarrollado para el curso MA2003B - Análisis Multivariado*
