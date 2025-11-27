# 📊 Methodology Comparison - Comparación de Métodos Multivariados

## Introducción

Este documento presenta una comparación sistemática de los tres métodos de análisis multivariado aplicados en el portafolio, utilizando el formato de tabla comparativa especificado en la rúbrica del curso.

---

## 📋 Tabla Comparativa de Métodos

| Aspecto | Factor Analysis | Discriminant Analysis | Cluster Analysis |
|---------|-----------------|----------------------|------------------|
| **Tipo de aprendizaje** | No supervisado | Supervisado | No supervisado |
| **Objetivo principal** | Reducción de dimensionalidad | Clasificación | Segmentación |
| **Input requerido** | Variables continuas (correlacionadas) | Variable categórica + predictores continuos | Variables continuas |
| **Output principal** | Factores latentes (scores factoriales) | Funciones discriminantes (probabilidades de clase) | Grupos/clusters (asignación de membresía) |
| **Caso de uso ideal** | Simplificar encuestas, crear índices compuestos, identificar dimensiones subyacentes de constructos | Predecir categorías de riesgo, clasificar clientes en segmentos conocidos, scoring crediticio | Descubrir segmentos de mercado, agrupar productos similares, identificar patrones de comportamiento |
| **Limitaciones** | Requiere correlaciones significativas entre variables; interpretación subjetiva de factores; no funciona bien con pocas observaciones | Asume normalidad multivariante; LDA asume covarianzas iguales; sensible a outliers | Número de clusters es subjetivo; sensible a escala de variables; K-means asume clusters esféricos |

---

## 📐 Detalles por Método

### Factor Analysis (Análisis Factorial)

#### Características
| Elemento | Descripción |
|----------|-------------|
| **Naturaleza** | Técnica de reducción de dimensionalidad |
| **Supervisión** | No supervisado (sin variable objetivo) |
| **Pregunta que responde** | "¿Qué estructura latente subyace a mis variables observadas?" |

#### Variantes Principales
| Variante | Objetivo | Cuándo usar |
|----------|----------|-------------|
| **EFA (Exploratorio)** | Descubrir factores | Cuando no sabes la estructura |
| **CFA (Confirmatorio)** | Validar estructura | Cuando tienes hipótesis de estructura |
| **PCA** | Maximizar varianza | Cuando solo quieres reducir dimensiones |

#### Métricas de Evaluación
- **KMO**: > 0.6 (idealmente > 0.8)
- **Bartlett**: p < 0.05
- **Varianza explicada**: > 60%
- **Comunalidades**: > 0.4
- **Cargas factoriales**: > |0.4|

#### Caso del Portafolio
- **Aplicación**: Satisfacción del cliente
- **Resultado**: 23 variables → 5 factores (KMO = 0.92)

---

### Discriminant Analysis (Análisis Discriminante)

#### Características
| Elemento | Descripción |
|----------|-------------|
| **Naturaleza** | Técnica de clasificación supervisada |
| **Supervisión** | Supervisado (requiere variable objetivo categórica) |
| **Pregunta que responde** | "¿A qué grupo pertenece una nueva observación?" |

#### Variantes Principales
| Variante | Supuesto de covarianzas | Frontera de decisión |
|----------|------------------------|---------------------|
| **LDA (Lineal)** | Iguales entre clases | Lineal |
| **QDA (Cuadrático)** | Diferentes entre clases | Cuadrática |

#### Métricas de Evaluación
- **Accuracy**: Proporción de correctos
- **Precision**: TP / (TP + FP)
- **Recall**: TP / (TP + FN)
- **F1-Score**: Media armónica
- **AUC-ROC**: Área bajo curva

#### Caso del Portafolio
- **Aplicación**: Riesgo crediticio LendSmart
- **Resultado**: LDA seleccionado (AUC = 1.000)

---

### Cluster Analysis (Análisis de Clusters)

#### Características
| Elemento | Descripción |
|----------|-------------|
| **Naturaleza** | Técnica de segmentación no supervisada |
| **Supervisión** | No supervisado (sin categorías predefinidas) |
| **Pregunta que responde** | "¿Cuántos grupos naturales existen y quién pertenece a cada uno?" |

#### Algoritmos Principales
| Algoritmo | Tipo | Requiere k | Maneja outliers |
|-----------|------|-----------|-----------------|
| **K-Means** | Partición | Sí | No |
| **Jerárquico** | Aglomerativo | No | Parcial |
| **DBSCAN** | Densidad | No | Sí |
| **GMM** | Probabilístico | Sí | Parcial |

#### Métricas de Evaluación
- **Silhouette Score**: [-1, 1], mayor = mejor
- **Inercia (SSW)**: Menor = mejor
- **Calinski-Harabasz**: Mayor = mejor
- **Davies-Bouldin**: Menor = mejor

#### Caso del Portafolio
- **Aplicación**: Segmentación MegaMart
- **Resultado**: 5 clusters de clientes identificados

---

## 🔄 Matriz de Decisión: ¿Cuál Método Usar?

| Si necesitas... | Usa... | Porque... |
|-----------------|--------|-----------|
| Simplificar muchas variables correlacionadas | **Factor Analysis** | Reduce dimensionalidad identificando estructura latente |
| Predecir a qué categoría pertenece un caso nuevo | **Discriminant Analysis** | Clasificación supervisada con interpretabilidad |
| Descubrir grupos naturales sin categorías previas | **Cluster Analysis** | Segmentación no supervisada |
| Entender qué variables son más importantes para separar grupos | **Discriminant Analysis** | Los coeficientes indican importancia |
| Crear un índice o score compuesto | **Factor Analysis** | Los scores factoriales combinan variables |
| Asignar nuevos clientes a segmentos existentes | **Discriminant Analysis** (después de Clusters) | Clasifica en grupos ya definidos |

---

## 🔗 Complementariedad de Métodos

### Combinaciones Útiles

```
┌─────────────────────────────────────────────────────────────────┐
│                    FLUJOS DE TRABAJO                            │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  FLUJO 1: FA → Clusters                                         │
│  ───────────────────────                                        │
│  Paso 1: Reducir variables a factores                           │
│  Paso 2: Usar scores factoriales para clustering                │
│  Beneficio: Clusters más estables y menos ruido                 │
│                                                                 │
│  FLUJO 2: Clusters → Discriminante                              │
│  ──────────────────────────────────                             │
│  Paso 1: Descubrir segmentos con clustering                     │
│  Paso 2: Entrenar discriminante con clusters como target        │
│  Beneficio: Clasificar nuevos casos en segmentos existentes     │
│                                                                 │
│  FLUJO 3: FA → Discriminante                                    │
│  ───────────────────────────                                    │
│  Paso 1: Extraer factores de variables predictoras              │
│  Paso 2: Usar factores como predictores en discriminante        │
│  Beneficio: Reducir multicolinealidad, mejorar interpretación   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📊 Comparación de Supuestos

| Supuesto | Factor Analysis | Discriminant Analysis | Cluster Analysis |
|----------|-----------------|----------------------|------------------|
| **Normalidad multivariante** | Deseable | Requerido (especialmente QDA) | No requerido |
| **Correlaciones entre variables** | Requerido (KMO > 0.6) | No requerido | No requerido |
| **Homogeneidad de covarianzas** | No aplica | Requerido para LDA | No aplica |
| **Escala de variables** | Recomendado estandarizar | Recomendado estandarizar | Obligatorio estandarizar |
| **Tamaño muestral mínimo** | 5-10 obs por variable | 20+ por grupo | Depende del algoritmo |
| **Outliers** | Moderadamente sensible | Sensible | Muy sensible (K-means) |

---

## 📈 Comparación de Outputs

| Aspecto | Factor Analysis | Discriminant Analysis | Cluster Analysis |
|---------|-----------------|----------------------|------------------|
| **Output numérico principal** | Cargas factoriales, scores | Probabilidades de clase, coeficientes | Asignación de cluster, centroides |
| **Output visual típico** | Scree plot, matriz de cargas | ROC curve, matriz de confusión | Scatter plot de clusters, dendrograma |
| **Interpretación directa** | "Esta variable pertenece a este factor" | "Esta observación tiene X% de ser clase A" | "Esta observación pertenece al cluster K" |
| **Uso para predicción** | Indirecto (a través de scores) | Directo | Indirecto (asignar al centroide más cercano) |

---

## 🎓 Resumen Ejecutivo

| Método | Una línea resumen |
|--------|-------------------|
| **Factor Analysis** | Simplifica la complejidad encontrando las dimensiones ocultas detrás de muchas variables |
| **Discriminant Analysis** | Predice categorías y explica qué variables hacen la diferencia entre grupos |
| **Cluster Analysis** | Descubre grupos naturales de observaciones similares sin etiquetas previas |

---

## 📚 Referencias

- Hair, J. F., Black, W. C., Babin, B. J., & Anderson, R. E. (2019). *Multivariate Data Analysis* (8th ed.)
- James, G., Witten, D., Hastie, T., & Tibshirani, R. (2021). *An Introduction to Statistical Learning* (2nd ed.)
- Scikit-learn Documentation: https://scikit-learn.org/stable/
- Factor Analyzer Documentation: https://factor-analyzer.readthedocs.io/

---

*Última actualización: Noviembre 2025*
