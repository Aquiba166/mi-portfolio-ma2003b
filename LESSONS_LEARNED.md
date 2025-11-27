# 📝 Lessons Learned - Reflexiones Críticas del Equipo

## Introducción

Este documento presenta las reflexiones críticas del equipo sobre los desafíos enfrentados, aprendizajes clave y aplicaciones futuras derivadas del desarrollo de los tres casos de estudio del portafolio de Análisis Multivariado.

---

## 👥 Equipo

- **Aquiba Samuel Benarroch Serfaty** - A01784240
- **Edgar Samuel Oropeza García** - A01660110
- **Uziel Heredia Estrada** - A01667072

---

## 🔧 Desafíos Técnicos

### ¿Qué fue difícil y cómo lo superamos?

#### Caso 1: Análisis Factorial

| Desafío | Descripción | Solución Aplicada |
|---------|-------------|-------------------|
| **Selección del número de factores** | El criterio de Kaiser sugirió más factores de los interpretables. El scree plot no era completamente claro. | Combinamos múltiples criterios: Kaiser (eigenvalue > 1), scree plot visual, y porcentaje de varianza explicada (>60%). Validamos que los factores tuvieran interpretación de negocio coherente. |
| **Cargas cruzadas** | Algunas variables cargaban en más de un factor con valores similares. | Aplicamos rotación Varimax y establecimos umbral de |0.4| para asignación. Variables con cargas cruzadas se analizaron conceptualmente. |
| **Instalación de factor_analyzer** | El paquete no estaba en el ambiente por defecto. | Agregamos instrucciones claras de instalación y verificación al inicio del notebook. |

#### Caso 2: Análisis Discriminante

| Desafío | Descripción | Solución Aplicada |
|---------|-------------|-------------------|
| **Resultados "perfectos" (AUC=1.0)** | Ambos modelos lograron clasificación perfecta, lo cual es inusual y sospechoso. | Documentamos que esto puede indicar: (1) datos muy separables, (2) posible data leakage, o (3) necesidad de validación con datos externos. Recomendamos validación out-of-time. |
| **Variables categóricas en LDA/QDA** | Education_level y marital_status requerían codificación numérica. | Aplicamos one-hot encoding con drop_first=True para evitar multicolinealidad. |
| **Verificación de supuestos** | Pruebas formales de normalidad multivariante y homogeneidad de covarianzas son complejas. | Usamos análisis visual (boxplots, histogramas por clase) y discusión teórica de las implicaciones. |

#### Caso 3: Análisis de Clusters

| Desafío | Descripción | Solución Aplicada |
|---------|-------------|-------------------|
| **Determinar número óptimo de k** | El método del codo no siempre muestra un "codo" claro. | Complementamos con análisis de silhouette score para diferentes valores de k. Elegimos k=5 por balance entre métricas y interpretabilidad. |
| **Escalas diferentes de variables** | Variables como total_spend y recency tenían rangos muy distintos. | Estandarización obligatoria (StandardScaler) antes de K-Means para evitar que variables de mayor escala dominen. |
| **Interpretación de centroides** | Los valores estandarizados de centroides no son intuitivos. | Creamos perfiles descriptivos con valores originales y gráficos de radar para comunicar resultados. |

---

## 🔍 Desafíos de Interpretación

### Dificultades para traducir hallazgos estadísticos a insights de negocio

| Área | Dificultad | Estrategia de Comunicación |
|------|------------|---------------------------|
| **Factores latentes** | Explicar a stakeholders que los "factores" no son variables observables directamente, sino constructos estadísticos. | Usamos nombres descriptivos (ej. "Competencia Técnica" en lugar de "Factor 1") y ejemplos concretos de qué variables los componen. |
| **Coeficientes LDA** | El signo y magnitud de coeficientes estandarizados no son intuitivos para audiencias no técnicas. | Creamos rankings simples: "Las 5 variables que más aumentan/reducen el riesgo" con explicación en lenguaje de negocio. |
| **Silhouette score** | Métricas como silhouette (0.3) no significan nada para tomadores de decisiones. | En lugar de reportar métricas, enfocamos en la utilidad: "Los 5 segmentos son claramente distinguibles y permiten estrategias diferenciadas". |
| **Trade-offs estadísticos** | Balancear precisión técnica con simplicidad de mensaje. | Creamos dos versiones de cada resultado: técnica (notebook) y ejecutiva (resumen PDF). |

### Lecciones sobre Comunicación

> "El mejor análisis no tiene valor si no se puede comunicar efectivamente."

1. **Empezar por el "so what"**: ¿Qué puede hacer diferente el negocio con estos resultados?
2. **Visualizaciones > Tablas**: Un buen gráfico comunica más que 10 tablas de números
3. **Evitar jerga**: Traducir términos como "eigenvalue", "silhouette", "covarianza"
4. **Contar una historia**: Los datos deben narrar un problema y su solución

---

## 💡 Aprendizajes Clave

### 3-5 Lecciones Principales del Curso

#### 1. La selección del método depende del problema, no de la técnica
> No elegimos el método porque es "cool" o moderno, sino porque responde a la pregunta de negocio específica.

**Ejemplo aplicado**: En el Caso 2 elegimos Discriminante sobre Regresión Logística porque los coeficientes LDA son más interpretables para entender qué variables separan las clases.

---

#### 2. Los supuestos importan, pero la robustez del método también
> Los métodos multivariados tienen supuestos teóricos (normalidad, homogeneidad de covarianzas) que rara vez se cumplen perfectamente en datos reales.

**Ejemplo aplicado**: LDA asume covarianzas iguales, pero aun sin cumplirse perfectamente, logró el mismo rendimiento que QDA en el Caso 2.

---

#### 3. El preprocesamiento es tan importante como el modelado
> "Garbage in, garbage out" - La calidad del análisis depende de cómo preparamos los datos.

**Ejemplo aplicado**: En el Caso 3, sin estandarización, `total_spend` (valores en miles) habría dominado sobre `recency` (valores en días), produciendo clusters sesgados.

---

#### 4. La interpretabilidad a veces vale más que la precisión
> Un modelo que podemos explicar tiene más valor práctico que una "caja negra" más precisa.

**Ejemplo aplicado**: Preferimos LDA sobre modelos más complejos porque podemos decir exactamente qué variables aumentan el riesgo crediticio y por cuánto.

---

#### 5. Los métodos multivariados se complementan
> No son técnicas aisladas - pueden usarse en secuencia para potenciarse.

**Ejemplo aplicado**: Podríamos usar los factores del Caso 1 como input para segmentación, o los clusters del Caso 3 como variable objetivo para discriminante.

---

## 🚀 Aplicaciones Futuras

### ¿Cómo usaremos estos métodos en nuestra carrera profesional?

| Carrera/Área | Aplicación de Factor Analysis | Aplicación de Discriminante | Aplicación de Clusters |
|--------------|------------------------------|----------------------------|------------------------|
| **Finanzas** | Construir índices de riesgo compuesto | Scoring crediticio, detección de fraude | Segmentación de portafolio de inversiones |
| **Marketing** | Dimensiones de percepción de marca | Predicción de churn/conversión | Segmentación de clientes, buyer personas |
| **Recursos Humanos** | Factores de engagement laboral | Predicción de rotación | Perfiles de empleados, planes de carrera |
| **Operaciones** | Indicadores de eficiencia operativa | Clasificación de proveedores | Agrupación de SKUs para inventario |
| **Consultoría** | Diagnóstico organizacional | Clasificación de riesgo de proyectos | Segmentación de clientes B2B |

### Proyectos Futuros Concretos

1. **Tesis/Capstone**: Integrar los tres métodos en un proyecto de Customer Analytics end-to-end
2. **Prácticas profesionales**: Aplicar segmentación de clientes con datos reales de empresa
3. **Emprendimiento**: Desarrollar herramienta de scoring crediticio para PyMEs
4. **Investigación**: Comparar métodos tradicionales vs. técnicas de ML modernas

---

## 🔄 Reflexiones del Proceso de Equipo

### ¿Qué funcionó bien en nuestro equipo?
- División clara de responsabilidades por caso
- Revisiones cruzadas del código y documentación
- Comunicación constante vía grupo de WhatsApp
- Sesiones de trabajo conjunto para integración

### ¿Qué mejoraríamos en futuros proyectos?
- Comenzar la documentación desde el inicio, no al final
- Establecer estándares de código comunes antes de empezar
- Hacer más pruebas intermedias con el profesor
- Reservar más tiempo para pulir visualizaciones

---

## 💭 Reflexión Final

El desarrollo de este portafolio nos ha enseñado que el análisis multivariado no es solo un conjunto de técnicas estadísticas, sino una forma de **pensar estructuradamente sobre problemas complejos**.

Las lecciones más valiosas trascienden las fórmulas matemáticas:

- **Pensamiento crítico**: Cuestionar resultados, especialmente cuando parecen demasiado buenos
- **Comunicación**: El valor del análisis está en su capacidad de influir decisiones
- **Pragmatismo**: Elegir el método correcto para el problema, no el más sofisticado
- **Humildad**: Reconocer las limitaciones de nuestros modelos y supuestos
- **Colaboración**: Los mejores análisis surgen de perspectivas diversas

> *"La meta no es hacer estadística perfecta, sino tomar mejores decisiones con datos imperfectos."*

---

*Última actualización: Noviembre 2025*
