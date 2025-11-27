# 📊 Portafolio de Análisis Multivariado - MA2003B

[![Python](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## 🎯 Descripción

Este repositorio contiene el portafolio de proyectos del curso **MA2003B - Análisis Multivariado** del Tecnológico de Monterrey. Incluye tres casos de estudio que aplican técnicas estadísticas avanzadas para resolver problemas empresariales reales.

## � Autores

- **Aquiba Samuel Benarroch Serfaty** 
- **Edgar Samuel Oropeza García**
- **Uziel Heredia Estrada**

Semestre: Agosto - Diciembre 2025

## 📁 Estructura del Repositorio

```
mi-portfolio-ma2003b/
│
├── README.md                      # Este archivo
├── LICENSE                        # Licencia MIT
├── requirements.txt               # Dependencias Python
├── .gitignore                     # Archivos ignorados por Git
│
├── PORTFOLIO_OVERVIEW.md          # Resumen integrador
├── LESSONS_LEARNED.md             # Reflexiones críticas
├── METHODOLOGY_COMPARISON.md      # Comparación de métodos
│
├── case-01-factor-analysis/       # Caso 1: Análisis Factorial
│   ├── README.md
│   ├── study_case_final.ipynb
│   ├── customer_satisfaction_data.csv
│   └── Resumen_Ejecutivo.pdf
│
├── case-02-discriminant-analysis/ # Caso 2: Análisis Discriminante
│   ├── README.md
│   ├── LendSmart_Credit_Risk_Analysis.ipynb
│   ├── credit_risk_data-1.csv
│   ├── Resumen_Ejecutivo_LendSmart.pdf
│   └── Análisis de Riesgo Crediticio de LendSmart.pptx.pdf
│
└── case-03-cluster-analysis/      # Caso 3: Análisis de Clusters
    ├── README.md
    ├── MegaMart_Segmentation.ipynb
    ├── retail_customer_data.csv
    ├── Resumen_Ejecutivo_MegaMart.pdf
    └── Presentación Customer Segmentation Project.pdf
```

## 📋 Casos de Estudio

| Caso | Técnica | Empresa | Objetivo |
|------|---------|---------|----------|
| **01** | Análisis Factorial | - | Identificar dimensiones latentes de satisfacción del cliente |
| **02** | Análisis Discriminante (LDA/QDA) | LendSmart | Predecir riesgo crediticio y comportamiento de pago |
| **03** | Análisis de Clusters | MegaMart | Segmentación de clientes para estrategias de marketing |

## 🚀 Inicio Rápido

### Prerrequisitos

- Python 3.8 o superior
- pip (gestor de paquetes de Python)
- Jupyter Notebook o JupyterLab

### Instalación

1. **Clonar el repositorio**
   ```bash
   git clone https://github.com/Aquiba166/mi-portfolio-ma2003b.git
   cd mi-portfolio-ma2003b
   ```

2. **Crear entorno virtual (recomendado)**
   ```bash
   python -m venv venv
   source venv/bin/activate  # En macOS/Linux
   # o
   .\venv\Scripts\activate   # En Windows
   ```

3. **Instalar dependencias**
   ```bash
   pip install -r requirements.txt
   ```

4. **Iniciar Jupyter**
   ```bash
   jupyter notebook
   ```

5. **Navegar a cualquier caso** y abrir el notebook `.ipynb`

## 🛠️ Tecnologías Utilizadas

| Categoría | Herramientas |
|-----------|--------------|
| **Lenguaje** | Python 3.x |
| **Análisis de Datos** | Pandas, NumPy |
| **Visualización** | Matplotlib, Seaborn |
| **Machine Learning** | Scikit-learn |
| **Estadística** | SciPy, Statsmodels |
| **Entorno** | Jupyter Notebooks |

## 📊 Técnicas Implementadas

- ✅ **Análisis Factorial Exploratorio (EFA)**
- ✅ **Análisis de Componentes Principales (PCA)**
- ✅ **Análisis Discriminante Lineal (LDA)**
- ✅ **Análisis Discriminante Cuadrático (QDA)**
- ✅ **K-Means Clustering**
- ✅ **Clustering Jerárquico**

## 📈 Resultados Destacados

### Caso 2: LendSmart Credit Risk
- **Modelo seleccionado:** LDA
- **AUC:** 1.000
- **Variables clave:** `payment_history_score`, `job_stability_score`, `credit_utilization`

### Caso 3: MegaMart Segmentation
- Identificación de segmentos de clientes distintivos
- Estrategias de marketing personalizadas por segmento

## 📚 Documentación Adicional

- [📋 Portfolio Overview](PORTFOLIO_OVERVIEW.md) - Resumen integrador de los tres casos
- [📝 Lessons Learned](LESSONS_LEARNED.md) - Reflexiones críticas y aprendizajes
- [🔀 Methodology Comparison](METHODOLOGY_COMPARISON.md) - Comparación detallada de técnicas

## 📄 Licencia

Este proyecto está bajo la Licencia MIT - ver el archivo [LICENSE](LICENSE) para más detalles.

## 🙏 Agradecimientos

- Tecnológico de Monterrey
- Profesores del curso MA2003B
- Compañeros de equipo

---

⭐ Si este repositorio te fue útil, ¡considera darle una estrella!

*Última actualización: Noviembre 2025*
