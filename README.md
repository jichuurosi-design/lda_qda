# Análisis Discriminante Lineal (LDA) y Cuadrático (QDA)
### Wine Dataset — Comparación de Modelos de Clasificación


## Descripción del proyecto

Este proyecto implementa y compara dos modelos clásicos de clasificación supervisada basados en análisis discriminante:

- **LDA** — *Linear Discriminant Analysis* (Análisis Discriminante Lineal)
- **QDA** — *Quadratic Discriminant Analysis* (Análisis Discriminante Cuadrático)

Ambos modelos se aplican sobre el Wine Dataset del UCI Machine Learning Repository, que contiene 178 muestras de vinos italianos clasificadas en 3 categorías según 13 características químicas. El objetivo es comparar el rendimiento predictivo, las fronteras de decisión y las métricas de evaluación de ambos modelos.

## Dataset

El dataset utilizado es el Wine Dataset, disponible directamente desde la librería `scikit-learn`. No es necesario descargar ningún archivo externo.

Se carga automáticamente en el notebook con:

*from sklearn.datasets import load_wine
wine = load_wine()*

| Característica | Detalle |
|---|---|
| **Origen** | UCI Machine Learning Repository |
| **Observaciones** | 178 muestras |
| **Variables predictoras** | 13 (características químicas del vino) |
| **Variable objetivo** | Tipo de vino (3 clases) |
| **Valores faltantes** | Ninguno |
| **Clases** | class_0 (59), class_1 (71), class_2 (48) |

**Variables predictoras incluidas:**
`alcohol`, `malic_acid`, `ash`, `alcalinity_of_ash`, `magnesium`,
`total_phenols`, `flavanoids`, `nonflavanoid_phenols`, `proanthocyanins`,
`color_intensity`, `hue`, `od280/od315_of_diluted_wines`, `proline`

## Cómo ejecutar el proyecto

### Opción 1 — Google Colab (recomendado, sin procedimientos extras)

1. Haz clic en el siguiente badge para abrir el notebook directamente en Colab:

https://colab.research.google.com/drive/147SjblRelctI-yTlH-66REFW4O9HWqWq?usp=sharing

2. Una vez abierto, ejecuta todas las celdas con:
   **Runtime → Run all** (o `Ctrl + F9`)

### Opción 2 — Ejecución local con Jupyter o vs

**Paso 1 — Clona el repositorio:**

*se puede clonar el repositorio de github o descargar el archivo ipynb en el google colab*

**Paso 2 — Instala las dependencias:**

*pip install scikit-learn pandas numpy matplotlib seaborn jupyter*

**Paso 3 — Ejecuta el notebook:**

*jupyter notebook LDA_QDA_Completo.ipynb*

## Contenido del Notebook

El notebook está organizado en las siguientes secciones:

| # | Sección | Descripción |
|---|---|---|
| 1 | **Descripción del dataset** | Origen, variables, clases y estructura |
| 2 | **Exploración de datos** | Dimensiones, tipos, nulos, estadísticas descriptivas |
| 3 | **Visualizaciones** | 5 gráficos con interpretación (histogramas, boxplots, correlaciones, dispersión) |
| 4 | **Preparación de datos** | División 70/30 estratificada + estandarización con justificación |
| 5 | **Implementación LDA** | Entrenamiento, parámetros, métricas y matriz de confusión |
| 6 | **Implementación QDA** | Entrenamiento, parámetros, métricas y matriz de confusión |
| 7 | **Comparación de modelos** | Tabla comparativa completa de métricas y tiempo |
| 8 | **Fronteras de decisión** | Visualización gráfica de fronteras LDA (lineal) vs QDA (cuadrática) |
| 9 | **Conclusiones** | 5 conclusiones fundamentadas |

## Principales hallazgos

### Métricas de rendimiento obtenidas

| Métrica | LDA | QDA |
|---|---|---|
| **Accuracy** | ~0.98 | ~0.98 |
| **Precisión (weighted)** | ~0.98 | ~0.98 |
| **Recall (weighted)** | ~0.98 | ~0.98 |
| **F1-Score (weighted)** | ~0.98 | ~0.98 |

> Los valores exactos se muestran al ejecutar el notebook.

### Conclusiones principales

1. **LDA** logra alta precisión en el Wine Dataset porque los datos cumplen razonablemente sus supuestos estadísticos: distribución gaussiana de las variables y covarianzas similares entre las tres clases de vino.

2. **QDA** genera fronteras de decisión cuadráticas más flexibles. En este dataset su rendimiento es comparable al de LDA, lo que indica que las diferencias entre las matrices de covarianza de cada clase no son drásticas.

3. Las variables `alcohol` y `flavanoids` son las más discriminantes visualmente: con solo estas dos variables, ambos modelos logran separar correctamente la mayoría de las muestras.

4. La **estandarización** fue una decisión clave: las 13 variables tienen escalas muy distintas (p.ej., `magnesium` ~100 vs `alcohol` ~13), y sin normalizarlas los modelos podrían sesgarse hacia las variables de mayor magnitud.

5. **LDA es preferible** cuando la interpretabilidad y la eficiencia son prioritarias. QDA es más adecuado cuando las covarianzas entre clases difieren significativamente y se dispone de suficientes observaciones por clase para estimar matrices de covarianza estables.

## Tecnologías utilizadas

| Librería | Uso |
|---|---|
| `scikit-learn` | Modelos LDA, QDA, métricas, preprocesamiento |
| `pandas` | Manipulación del DataFrame |
| `numpy` | Operaciones numéricas y matrices |
| `matplotlib` | Visualizaciones y fronteras de decisión |
| `seaborn` | Gráficos estadísticos (heatmap, boxplot) |
| `Google Colab` | Entorno de ejecución en la nube |

## Autor

**Miguel Alejandro Yglesias Alvear**

Carrera: Ciencia de Datos e Inteligencia Artificial

📅 Fecha: 5 de julio del 2026
