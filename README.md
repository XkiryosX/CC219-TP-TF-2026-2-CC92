# CC219-TP-TF-2026-2-CC92
## Detección automática de phishing en correos electrónicos en español mediante NLP y Machine Learning

Repositorio académico del curso **Aplicaciones de Data Science (CC219)**.

**Estado actual:** Trabajo Parcial / Hito 1.

## Objetivo

Diseñar un pipeline reproducible de Procesamiento de Lenguaje Natural (NLP) para preparar y representar correos electrónicos en español, con el propósito de entrenar y comparar posteriormente modelos capaces de clasificarlos como **legítimos** o **phishing**.

## Integrantes

- [Nombre integrante 1]
- [Nombre integrante 2]

## Dataset

Se utiliza el dataset **SpaPhish**, compuesto en la versión trabajada por:

- 1,395 correos electrónicos
- 47 variables
- 664 correos legítimos
- 731 correos phishing
- Variable objetivo: `Label`
  - `0`: legítimo
  - `1`: phishing

Principales variables utilizadas:

- `subject`: asunto del correo
- `body`: contenido del correo
- `url_count`: número de URLs
- `attachments_count`: número de archivos adjuntos
- `attachments_total_size`: tamaño total de adjuntos
- `hops_count`: número de saltos de enrutamiento
- `Label`: clase objetivo

### Versiones del dataset

- `data/Spaphish dataset - DiB.csv`: archivo original utilizado en el proyecto.
- `data/Spaphish_dataset_limpio_para_colab.csv`: misma información reserializada en UTF-8-SIG para evitar errores de lectura en Google Colab. Conserva los 1,395 registros y 47 columnas.

## Alcance del Hito 1

En este hito se desarrolla:

1. Descripción y fundamentación del caso de uso.
2. Preguntas de clasificación/predicción.
3. Descripción del conjunto de datos.
4. Análisis exploratorio de datos (EDA).
5. Preprocesamiento y normalización textual.
6. Representación propuesta mediante TF-IDF.
7. Propuesta de algoritmos de clasificación.
8. Definición de métricas para el Hito 2.

La comparación definitiva de modelos, selección del mejor algoritmo y resultados finales se desarrollarán en el Segundo Hito.

## Preguntas del proyecto

1. ¿Es posible clasificar automáticamente un correo electrónico en español como legítimo o phishing utilizando su contenido textual?
2. ¿Qué algoritmo de clasificación supervisada presentará el mejor desempeño para detectar la clase phishing?
3. ¿La incorporación de n-gramas junto con TF-IDF permitirá mejorar la discriminación entre correos legítimos y phishing?

## Preprocesamiento

El notebook desarrolla un pipeline que:

- combina `subject` y `body`;
- trata valores nulos;
- normaliza texto y codificación;
- sustituye URLs por el token `URL`;
- sustituye direcciones de correo por el token `EMAIL`;
- convierte el texto a minúsculas;
- normaliza espacios;
- genera las variables `n_chars` y `n_words`.

La columna preparada para análisis es `text_clean`.

## Representación textual

La línea base propuesta utiliza **TF-IDF (Term Frequency - Inverse Document Frequency)** con unigramas y bigramas.

## Modelos propuestos

Para la fase de modelización se propone comparar:

- Multinomial Naive Bayes
- Bernoulli Naive Bayes
- Regresión Logística
- Random Forest
- SVM lineal / LinearSVC

## Métricas propuestas

- Accuracy
- Precision
- Recall
- F1-score
- Matriz de confusión

Como métricas complementarias se podrán analizar Balanced Accuracy y ROC-AUC.

## Estructura del repositorio

```text
CC219-TP-TF-2026-2-CC92/
├── data/
│   ├── Spaphish dataset - DiB.csv
│   └── Spaphish_dataset_limpio_para_colab.csv
├── code/
│   └── TP_SPAPHISH_Colab_v2.ipynb
├── README.md
├── requirements.txt
├── .gitignore
└── LICENSE
```

## Ejecución en Google Colab

1. Abrir `code/TP_SPAPHISH_Colab_v2.ipynb`.
2. Ejecutar las celdas en orden.
3. Cuando se solicite el dataset, seleccionar `data/Spaphish_dataset_limpio_para_colab.csv`.

## Conclusiones del Hito 1

El análisis preliminar permitió verificar que el dataset presenta una distribución relativamente equilibrada entre correos legítimos y phishing. El EDA también mostró diferencias descriptivas en longitud y metadatos, pero estas no son suficientes por sí solas para establecer reglas deterministas. Por esta razón se propone emplear representación TF-IDF y comparar distintos algoritmos supervisados durante el Segundo Hito.

## Próximos pasos

- Entrenar los modelos propuestos.
- Comparar las métricas obtenidas.
- Analizar falsos positivos y falsos negativos.
- Seleccionar el modelo final.
- Evaluar extensiones modernas del curso, como embeddings o modelos preentrenados.

## Referencias

- SpaPhish / Mendeley Data.
- Materiales del curso Aplicaciones de Data Science - CC219.
- Material de clase sobre NLP, TF-IDF y clasificación.
- Scikit-learn.

## Licencia

El código y la documentación creados por el equipo pueden distribuirse bajo licencia MIT.

El dataset SpaPhish conserva la licencia y las condiciones de atribución establecidas por sus autores y por su fuente original.
