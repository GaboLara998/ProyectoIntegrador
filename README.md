# 🎯 Proyecto Integrador: Detección de Intrusiones en Redes de Comunicación

Este proyecto implementa y evalúa técnicas y algoritmos de aprendizaje automático para la detección de intrusiones en redes de comunicación. Nos enfocamos en una clasificación binaria: Tráfico de tipo Ataque y Tráfico Normal de Red.

## 📂 Estructura del Proyecto

La estructura del repositorio es la siguiente:

- Carpeta `DataSet_UNSW_NB15` con los archivos CSV del conjunto de entrenamiento y conjunto de pruebas:
  - `DataSet_UNSW_NB15/UNSW_NB15_testing-set.csv`
  - `DataSet_UNSW_NB15/UNSW_NB15_training-set.csv`

- Dos archivos en Jupyter Notebook:

  1. 📊 `Analisis_de_DataSet.ipynb` que incluye:
     - **Carga de datos**: Carga del conjunto de datos utilizando métodos como `pd.read_csv`.
     - **Visualización de datos**: Generación de gráficos y visualizaciones para entender mejor la distribución y las características de los datos. Herramientas utilizadas incluyen `matplotlib` y `seaborn`.
     - **Análisis de datos**: Análisis exploratorio de los datos, describiendo las características estadísticas y visualizando las primeras filas del conjunto de datos.

  2. 📝 `ProyectoIntregradorUSFQ.ipynb` que incluye:
     - **Carga de datos**: Se cargan los conjuntos de datos de entrenamiento y prueba desde URLs en GitHub utilizando la función `cargar_datos`, que lee los archivos CSV y los convierte en dataframes de pandas.
     - **Visualización y Análisis de datos**: Se combinan los conjuntos de datos de entrenamiento y prueba en un solo dataframe y se reinicia el índice. Se visualiza la estructura y contenido del dataframe combinado para obtener una visión general de las columnas y tipos de datos.
     - **Eliminación de columnas no necesarias**: Se eliminan las columnas `service`, `proto` y `state`, ya que no son necesarias para el análisis posterior.
     - **Transformación de la columna categórica `attack_cat`**: Se convierte la columna `attack_cat` en códigos numéricos utilizando la función `pd.Categorical().codes`.
     - **Verificación de valores nulos**: Se verifica la presencia de valores nulos en el dataframe y se imprime el conteo de valores nulos por columna.
     - **Eliminación de columnas con alta correlación**: Se calcula la matriz de correlación absoluta del dataframe. Se identifican y eliminan las columnas con una correlación mayor a 0.95 para reducir la multicolinealidad.
     - **Preprocesamiento de datos**: Se identifican las columnas numéricas del dataframe que no incluyen la etiqueta `label`. Se normalizan las columnas numéricas utilizando `MinMaxScaler` para escalar los datos en un rango de 0 a 1.
     - **División del dataset**: Se separan las características (`X`) y las etiquetas (`y`). Se divide el conjunto de datos en entrenamiento (70%) y prueba (30%) utilizando `train_test_split`. Se divide el conjunto de entrenamiento temporal en conjuntos de entrenamiento real y validación (20% del conjunto de entrenamiento).
     - **Visualización de la distribución de las etiquetas**: Se visualiza la distribución de las etiquetas `label` (normal y ataque) utilizando un gráfico de pastel.
     - **Modelado**: Se realiza una búsqueda de hiperparámetros para el modelo de árbol de decisión utilizando `GridSearchCV`. Se entrena el modelo de árbol de decisión con los mejores parámetros encontrados y se imprimen los resultados del modelo. Se visualiza el árbol de decisión resultante utilizando `plot_tree`.
     - **Evaluación de modelos**: Se entrena un modelo de Random Forest y se calculan las métricas de evaluación (precisión, recall, F1, AUC) y la matriz de confusión. Se visualizan las características más importantes del modelo de Random Forest utilizando un gráfico de barras.
     - **Algoritmos adicionales**: Se implementa y evalúa un modelo KNN (vecinos más cercanos), calculando las métricas de evaluación y visualizando la matriz de confusión. Se implementa y evalúa un modelo XGBoost, calculando las métricas de evaluación y visualizando la matriz de confusión. Se implementa y evalúa un modelo SVM (Máquinas de Soporte Vectorial), calculando las métricas de evaluación y visualizando la matriz de confusión.
     - **Evaluaciones con Cross Validation**: Se configuran métricas de evaluación y se utiliza `StratifiedKFold` para realizar validación cruzada con 10 pliegues en los modelos Random Forest, KNN, SVM y XGBoost. Se imprimen los resultados de la validación cruzada para cada modelo, incluyendo precisión, recall, F1 y AUC.
     - **Test estadístico Wilcoxon**: Se realizan pruebas estadísticas de Wilcoxon entre los modelos para comparar sus puntuaciones AUC en los 10 pliegues de validación cruzada. Se imprimen los resultados de las comparaciones, incluyendo los valores p para determinar la significancia estadística de las diferencias entre los modelos.
