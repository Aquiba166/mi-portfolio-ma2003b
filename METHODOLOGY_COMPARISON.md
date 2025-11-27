# 📊 Methodology Comparison - Comparación de Métodos Multivariados

## Introducción

Este documento presenta una comparación sistemática de las tres técnicas de análisis multivariado aplicadas en el portafolio, destacando sus características, supuestos, aplicaciones y criterios de selección.

---

## 🔄 Visión General de los Métodos

| Aspecto | Análisis Factorial | Análisis Discriminante | Análisis de Clusters |
|---------|---------------------|------------------------|---------------------|
| **Tipo** | Reducción dimensional | Clasificación supervisada | Segmentación no supervisada |
| **Objetivo** | Identificar variables latentes | Predecir categorías | Agrupar observaciones |
| **Variable objetivo** | No aplica | Requerida (categórica) | No aplica |
| **Caso aplicado** | Satisfacción del cliente | Riesgo crediticio | Segmentación retail |

---

## 📐 Análisis Factorial

### Descripción
Técnica que busca reducir la dimensionalidad identificando factores latentes que explican las correlaciones entre variables observadas.

### Variantes
| Variante | Descripción | Uso |
|----------|-------------|-----|
| **EFA** | Exploratorio | Descubrir estructura de factores |
| **CFA** | Confirmatorio | Validar estructura hipotética |
| **PCA** | Componentes principales | Maximizar varianza explicada |

### Supuestos
- ✅ Correlaciones significativas entre variables (KMO > 0.6)
- ✅ Prueba de Bartlett significativa
- ✅ Tamaño de muestra adecuado (n > 5-10 por variable)
- ⚠️ Normalidad multivariante (deseable pero no crítico)

### Métricas de Evaluación
```
┌─────────────────────────────────────────────┐
│ • KMO (Kaiser-Meyer-Olkin): > 0.6          │
│ • Varianza explicada acumulada: > 60%       │
│ • Comunalidades: > 0.4                      │
│ • Cargas factoriales: > |0.4|               │
└─────────────────────────────────────────────┘
```

### Cuándo Usar
- Muchas variables correlacionadas
- Objetivo de simplificar estructura
- Desarrollo de escalas o cuestionarios
- Preprocesamiento para otros análisis

---

## 📊 Análisis Discriminante

### Descripción
Técnica supervisada que encuentra combinaciones lineales de variables que mejor separan grupos predefinidos.

### Variantes Comparadas en el Portafolio

| Característica | LDA | QDA |
|----------------|-----|-----|
| **Frontera de decisión** | Lineal | Cuadrática |
| **Covarianzas** | Asume iguales entre clases | Permite diferentes |
| **Complejidad** | Menor | Mayor |
| **Parámetros** | Menos | Más |
| **Riesgo de sobreajuste** | Menor | Mayor |
| **Interpretabilidad** | Alta | Media |

### Supuestos
- ✅ Variable dependiente categórica
- ✅ Variables independientes continuas (o codificadas)
- ⚠️ Normalidad multivariante por grupo
- ⚠️ Homogeneidad de matrices de covarianza (solo LDA)
- ✅ Independencia de observaciones

### Métricas de Evaluación
```
┌─────────────────────────────────────────────┐
│ • Accuracy: Proporción de correctos         │
│ • Precision: TP / (TP + FP)                 │
│ • Recall: TP / (TP + FN)                    │
│ • F1-Score: Media armónica P y R            │
│ • AUC-ROC: Área bajo curva ROC              │
│ • Matriz de confusión                       │
└─────────────────────────────────────────────┘
```

### Cuándo Usar
- Clasificación con grupos conocidos
- Interpretación de variables discriminantes
- Predicción de membresía de grupo
- Cuando interesa la contribución de cada variable

### Resultado del Caso 2
**Modelo seleccionado: LDA**
- AUC = 1.000 (ambos modelos)
- LDA preferido por simplicidad e interpretabilidad

---

## 🎯 Análisis de Clusters

### Descripción
Técnica no supervisada que agrupa observaciones en clusters basándose en similitud, sin variable objetivo predefinida.

### Algoritmos Principales

| Algoritmo | Descripción | Ventajas | Desventajas |
|-----------|-------------|----------|-------------|
| **K-Means** | Particional basado en centroides | Rápido, escalable | Requiere k, sensible a outliers |
| **Jerárquico** | Aglomerativo/Divisivo | No requiere k, dendrograma | Computacionalmente costoso |
| **DBSCAN** | Basado en densidad | Detecta outliers, formas arbitrarias | Parámetros sensibles |
| **GMM** | Modelos de mezcla gaussiana | Probabilístico, clusters elípticos | Asume normalidad |

### Supuestos
- ⚠️ Escala de variables (estandarización recomendada)
- ⚠️ Métrica de distancia apropiada
- ✅ Clusters "naturales" en los datos

### Métricas de Evaluación

**Internas (sin ground truth):**
```
┌─────────────────────────────────────────────┐
│ • Silhouette Score: [-1, 1], mayor = mejor  │
│ • Índice de Calinski-Harabasz: mayor = mejor│
│ • Índice de Davies-Bouldin: menor = mejor   │
│ • Inercia (SSW): menor = mejor              │
└─────────────────────────────────────────────┘
```

**Métodos para seleccionar k:**
- Método del codo (Elbow)
- Silhouette analysis
- Gap statistic
- Dendrograma (jerárquico)

### Cuándo Usar
- Segmentación de mercado
- Detección de patrones ocultos
- Agrupación de documentos
- Compresión de datos
- Preprocesamiento para análisis supervisado

---

## 🔀 Comparación de Flujos de Trabajo

```
┌──────────────────────────────────────────────────────────────────┐
│                    ANÁLISIS FACTORIAL                            │
│ ┌──────────┐   ┌──────────┐   ┌──────────┐   ┌──────────┐       │
│ │   EDA    │ → │ KMO/     │ → │ Extrac.  │ → │ Rotación │       │
│ │          │   │ Bartlett │   │ Factores │   │ Varimax  │       │
│ └──────────┘   └──────────┘   └──────────┘   └──────────┘       │
└──────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────┐
│                  ANÁLISIS DISCRIMINANTE                          │
│ ┌──────────┐   ┌──────────┐   ┌──────────┐   ┌──────────┐       │
│ │   EDA    │ → │ Train/   │ → │ LDA/QDA  │ → │ Evaluar  │       │
│ │          │   │ Test     │   │ Fit      │   │ Métricas │       │
│ └──────────┘   └──────────┘   └──────────┘   └──────────┘       │
└──────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────┐
│                   ANÁLISIS DE CLUSTERS                           │
│ ┌──────────┐   ┌──────────┐   ┌──────────┐   ┌──────────┐       │
│ │   EDA    │ → │ Estandar │ → │ Elegir k │ → │ Perfilar │       │
│ │          │   │ izar     │   │ Cluster  │   │ Clusters │       │
│ └──────────┘   └──────────┘   └──────────┘   └──────────┘       │
└──────────────────────────────────────────────────────────────────┘
```

---

## 🤔 Guía de Selección de Método

### Diagrama de Decisión

```
¿Tienes variable objetivo categórica?
    │
    ├── SÍ → ¿Quieres clasificar nuevas observaciones?
    │         │
    │         ├── SÍ → ANÁLISIS DISCRIMINANTE
    │         │         • LDA si covarianzas similares
    │         │         • QDA si covarianzas diferentes
    │         │
    │         └── NO → ¿Quieres entender diferencias entre grupos?
    │                   └── SÍ → ANÁLISIS DISCRIMINANTE
    │
    └── NO → ¿Tienes muchas variables correlacionadas?
              │
              ├── SÍ → ¿Quieres reducir dimensionalidad?
              │         │
              │         ├── SÍ → ANÁLISIS FACTORIAL / PCA
              │         │
              │         └── NO → ¿Quieres segmentar observaciones?
              │                   └── SÍ → ANÁLISIS DE CLUSTERS
              │
              └── NO → ¿Quieres encontrar grupos naturales?
                        └── SÍ → ANÁLISIS DE CLUSTERS
```

---

## 📋 Tabla Resumen Comparativa

| Criterio | Factorial | Discriminante | Clusters |
|----------|-----------|---------------|----------|
| **Supervisado** | ❌ | ✅ | ❌ |
| **Objetivo principal** | Reducir variables | Clasificar | Segmentar |
| **Output** | Factores/Componentes | Predicciones | Grupos |
| **Interpretabilidad** | Alta | Alta (LDA) | Media |
| **Validación** | Varianza explicada | Accuracy, AUC | Silhouette |
| **Escalabilidad** | Alta | Alta | Media-Alta |
| **Sensible a outliers** | Media | Baja-Media | Alta (K-means) |

---

## 🎓 Conclusiones

### Complementariedad de Métodos

Los tres métodos no son excluyentes, sino complementarios:

1. **Factorial** puede usarse como preprocesamiento para reducir dimensiones antes de Discriminante o Clusters
2. **Clusters** puede crear una variable objetivo para luego aplicar Discriminante
3. **Discriminante** puede validar clusters encontrados

### Recomendaciones Generales

| Situación | Recomendación |
|-----------|---------------|
| Muchas variables, quiero simplificar | Análisis Factorial |
| Tengo grupos, quiero predecir | Análisis Discriminante |
| No tengo grupos, quiero encontrarlos | Análisis de Clusters |
| Quiero entender qué variables importan | LDA con coeficientes |
| Datos muy asimétricos entre clases | Considerar otras técnicas (árboles, etc.) |

---

## 📚 Referencias

- Hair, J. F., et al. (2019). *Multivariate Data Analysis*
- James, G., et al. (2021). *An Introduction to Statistical Learning*
- Hastie, T., Tibshirani, R., & Friedman, J. (2009). *The Elements of Statistical Learning*
- Scikit-learn User Guide: https://scikit-learn.org/stable/user_guide.html

---

*Última actualización: Noviembre 2025*
