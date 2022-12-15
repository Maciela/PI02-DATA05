# <h1 align="center">**`Proyecto Individual 2`**

¡Bienvenidos!
Este es el segundo proyecto individual de la etapa de LABS de Henry.En está instancia se puso a prueba nuestras habilidades en el desarrolo de modelos de Machine Learning.
Iniciaré presentado la situación problema que se planteó, así como los criterios de evaluación:

## **Descripción del problema**

Se nos solicitó un modelo de machine learning, para poder si un paciente tendrá una estancia hospitalaria prolongada o no. Para ello nos diponibilizaron un dataset llamado 'hospitalizaciones_train.csv' , el cual recaba una muestra histórica de sus pacientes. Se define que un paciente posee estancia hospitalaria prolongada si ha estado hospitalizado más de 8 días

## **Criterio de evaluación**

La solución propuesta debe incluir los siguientes ítems, por cada uno cumplido sumará 1 punto, siendo 1 la nota mínima y 5 la nota máxima:

- Entrenamiento y predicción utilizando un Modelo de Machine Learning adecuado al problema (clasificación o regresión).
- Análisis exploratorio de los datos (EDA).
- División de dataset en train y test utilizando train_test_split, CV, KFold o similares.
- Utilización de Pipelines en la producción del modelo.
- Comentarios y redacción con la fundamentación de la solución propuesta, escrita en Markdown en el Jupyter Notebook (.ipynb) o bien en un documento aparte.

## **Descripción de la solución propuesta**

Para resolver al problema, decidí utilizar modelos de machine learning de **clasificación** .

Este repositorio consta de dos datasets:

- El dataset **hospitalizaciones_train.csv** que utilicé en el entreamiento del modelo; para ello tuve que realizar primero el análisis exploratorio de los datos y preprocesamiento. En esta instacia se observó que era conveniente tranformar los datos en variables del tipo categóricas, utilizando LabelEncoder. Luego, para la selección de features utilicé la clase SelectKBest de la librería Scikit-learn, aquí obtuve tres carácteristicas: 'Age','gender','Admission_Deposit', además consideré conveniente utilizar también las columnas 'Type of Admission', 'Severity of Illness', 'health_conditions' , ya que si bien presentan correlaciones menores, en la realidad podrían ser factores que contribuyan a la decisión de la cantidad días que será internado el paciente y por tanto su estadía sea prolongada o no. De este modo obtuve un dataframe con los seis features mencionados(df_entrenamiento). Por último cree dos pipelines, uno correspondiente al modelo de Regresión Logística y otro de Árbol de Decisión.

- El dataset **hospitalizaciones_test.csv**, es el que utilicé para realizar la predicción solicitada. Para ello, utilicé el LabelEncoder sobre los features de interes, obteniendo así un dataframe con las columnas [ 'Age' ,'gender', 'Type of Admission', 'Severity of Illness', 'health_conditions','Admission_Deposit'] , dicho dataframe se denomina df_validacion.

Para decidir que modelo era el adecuado se utilizaron las siguientes métricas:
-Accuracy
-Recall

Finalmente, y como restultado del flujo de trabajo, el modelo que sea adecua al problema es el modelo de Árbol de Decisión.

Por último, generé un archivo .csv sólo con las predicciones, que tiene una sola columna llamada 'pred'.
