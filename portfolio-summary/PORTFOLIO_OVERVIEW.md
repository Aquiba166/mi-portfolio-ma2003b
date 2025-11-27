# 📊 Portfolio Overview - Análisis Multivariado MA2003B

## Resumen Integrador

Este documento integra los tres casos de estudio del portafolio, explicando cómo se relacionan los métodos multivariados entre sí y cuándo utilizar cada técnica.

---

## 👥 Autores

- **Aquiba Samuel Benarroch Serfaty** - A01784240
- **Edgar Samuel Oropeza García** - A01660110
- **Uziel Heredia Estrada** - A01667072

**Curso:** MA2003B - Análisis Multivariado  
**Período:** Semestre Agosto-Diciembre 2025

---

## 🔗 ¿Cómo se Relacionan los Tres Métodos Entre Sí?

Los tres métodos multivariados aplicados en este portafolio forman un **ecosistema complementario** para el análisis de datos empresariales:

### Relación Conceptual

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                        ANÁLISIS MULTIVARIADO                                │
│                                                                             │
│   ┌─────────────────┐                           ┌─────────────────┐        │
│   │ ANÁLISIS        │    Reducción de           │ ANÁLISIS        │        │
│   │ FACTORIAL       │    dimensiones para       │ DISCRIMINANTE   │        │
│   │                 │ ─────────────────────────►│                 │        │
│   │ Variables → Factores                        │ Factores → Clasificación │
│   └─────────────────┘                           └─────────────────┘        │
│          │                                              │                  │
│          │ Factores como                                │ Segmentos como   │
│          │ input para                                   │ variable target  │
│          │ segmentación                                 │                  │
│          ▼                                              ▼                  │
│   ┌─────────────────────────────────────────────────────┐                  │
│   │              ANÁLISIS DE CLUSTERS                   │                  │
│   │                                                     │                  │
│   │  Agrupa observaciones sin variable objetivo         │                  │
│   │  Puede usar factores o variables originales         │                  │
│   │  Los clusters pueden ser target para discriminante  │                  │
│   └─────────────────────────────────────────────────────┘                  │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Flujos de Integración

| Flujo | Descripción | Ejemplo |
|-------|-------------|---------|
| **FA → Clusters** | Usar puntajes factoriales como input para clustering | Reducir 23 variables de satisfacción a 5 factores, luego segmentar clientes |
| **FA → Discriminante** | Usar factores como predictores para clasificación | Factores de riesgo para predecir default |
| **Clusters → Discriminante** | Usar clusters como variable objetivo | Segmentar clientes, luego predecir membresía de nuevos clientes |

---

## ❓ ¿Qué Tipos de Preguntas de Negocio Responde Cada Método?

### Análisis Factorial
| Pregunta de Negocio | Aplicación |
|---------------------|------------|
| "¿Cuáles son las dimensiones subyacentes de satisfacción del cliente?" | Identificar factores latentes |
| "¿Cómo puedo simplificar mi encuesta de 30 preguntas?" | Reducir a factores clave |
| "¿Qué aspectos de mi servicio están correlacionados?" | Descubrir estructura de variables |
| "¿Cómo crear un índice compuesto de lealtad?" | Combinar variables en scores |

### Análisis Discriminante
| Pregunta de Negocio | Aplicación |
|---------------------|------------|
| "¿Qué clientes tienen mayor probabilidad de incumplir?" | Clasificar riesgo crediticio |
| "¿Qué variables distinguen a los clientes que renuevan vs. los que cancelan?" | Identificar drivers de churn |
| "¿A qué segmento pertenece un nuevo cliente?" | Asignar a grupos predefinidos |
| "¿Cuáles son los factores que mejor predicen el éxito de un producto?" | Ranking de importancia de variables |

### Análisis de Clusters
| Pregunta de Negocio | Aplicación |
|---------------------|------------|
| "¿Cuántos tipos de clientes tenemos?" | Descubrir segmentos naturales |
| "¿Cómo podemos personalizar nuestro marketing?" | Crear perfiles para targeting |
| "¿Qué productos se compran juntos?" | Agrupar por patrones de consumo |
| "¿Existen grupos de empleados con necesidades similares?" | Segmentar para programas HR |

---

## 🎯 ¿Cuándo Usar Cada Técnica Multivariada?

### Árbol de Decisión para Selección de Método

```
¿Tienes una VARIABLE OBJETIVO que quieres predecir?
│
├── SÍ (Supervisado)
│   │
│   └── ¿La variable objetivo es CATEGÓRICA?
│       │
│       ├── SÍ → ANÁLISIS DISCRIMINANTE
│       │        (LDA si covarianzas homogéneas)
│       │        (QDA si covarianzas diferentes)
│       │
│       └── NO → Regresión (fuera del alcance)
│
└── NO (No Supervisado)
    │
    └── ¿Qué quieres hacer?
        │
        ├── Reducir número de VARIABLES → ANÁLISIS FACTORIAL
        │   • Muchas variables correlacionadas
        │   • Buscar estructura latente
        │   • Crear índices compuestos
        │
        └── Agrupar OBSERVACIONES → ANÁLISIS DE CLUSTERS
            • Segmentar clientes/productos
            • Descubrir grupos naturales
            • No tienes categorías predefinidas
```

### Tabla de Decisión Rápida

| Situación | Método Recomendado | Caso del Portafolio |
|-----------|-------------------|---------------------|
| 23 ítems de encuesta correlacionados | **Análisis Factorial** | Caso 1: Satisfacción |
| Predecir si cliente pagará o no | **Análisis Discriminante** | Caso 2: LendSmart |
| Descubrir tipos de clientes para marketing | **Análisis de Clusters** | Caso 3: MegaMart |
| Simplificar variables antes de segmentar | **FA + Clusters** | Combinación |
| Clasificar nuevos clientes en segmentos existentes | **Clusters + Discriminante** | Combinación |

---

## 🗺️ Mapa Conceptual de Relaciones Entre Métodos

```
                    ┌──────────────────────────────────────────────────────────┐
                    │           MÉTODOS MULTIVARIADOS                          │
                    └──────────────────────────────────────────────────────────┘
                                           │
            ┌──────────────────────────────┼──────────────────────────────┐
            │                              │                              │
            ▼                              ▼                              ▼
┌───────────────────────┐    ┌───────────────────────┐    ┌───────────────────────┐
│   ANÁLISIS FACTORIAL  │    │ ANÁLISIS DISCRIMINANTE│    │  ANÁLISIS DE CLUSTERS │
├───────────────────────┤    ├───────────────────────┤    ├───────────────────────┤
│ • No supervisado      │    │ • Supervisado         │    │ • No supervisado      │
│ • Reduce VARIABLES    │    │ • Clasifica           │    │ • Agrupa OBSERVACIONES│
│ • Output: Factores    │    │ • Output: Predicción  │    │ • Output: Grupos      │
├───────────────────────┤    ├───────────────────────┤    ├───────────────────────┤
│ Caso 1: Satisfacción  │    │ Caso 2: Riesgo Credit.│    │ Caso 3: Segmentación  │
│ 23 vars → 5 factores  │    │ LDA/QDA → AUC=1.0     │    │ 3000 clientes → 5 seg │
└───────────────────────┘    └───────────────────────┘    └───────────────────────┘
            │                              ▲                              │
            │                              │                              │
            └───── Factores como ──────────┘                              │
                   predictores                                            │
            │                                                             │
            └───── Factores como input ───────────────────────────────────┘
                   para clustering

                    ┌──────────────────────────────────────────────────────────┐
                    │  COMPLEMENTARIEDAD: Los métodos se potencian entre sí   │
                    │  • FA simplifica datos para Clusters o Discriminante    │
                    │  • Clusters crea target para Discriminante futuro       │
                    │  • Discriminante clasifica nuevos casos en clusters     │
                    └──────────────────────────────────────────────────────────┘
```

---

## 📋 Resumen de Casos del Portafolio

| Caso | Técnica | Empresa | Problema | Resultado Principal |
|------|---------|---------|----------|---------------------|
| **1** | Análisis Factorial | B2B Services | Simplificar 23 ítems de satisfacción | 5 factores latentes (KMO=0.92) |
| **2** | Análisis Discriminante | LendSmart | Predecir riesgo de default | LDA con AUC=1.0 |
| **3** | Análisis de Clusters | MegaMart | Segmentar clientes para marketing | 5 segmentos accionables |

---

## 🎓 Competencias Demostradas

| Competencia | Evidencia |
|-------------|-----------|
| **Selección de método apropiado** | Justificación clara en cada caso del por qué se eligió cada técnica |
| **Validación de supuestos** | KMO/Bartlett (FA), normalidad/covarianzas (DA), silhouette (Clusters) |
| **Interpretación de resultados** | Traducción de outputs estadísticos a insights de negocio |
| **Recomendaciones accionables** | Estrategias concretas derivadas de cada análisis |
| **Comunicación técnica** | Documentación clara para audiencias técnicas y ejecutivas |

---

## 📚 Referencias

- Hair, J. F., et al. (2019). *Multivariate Data Analysis*
- James, G., et al. (2021). *An Introduction to Statistical Learning*
- Scikit-learn Documentation
- Curso MA2003B - Tecnológico de Monterrey

---

*Última actualización: Noviembre 2025*
