# CEIA_project


Este repositorio contiene el código correspondiente al proyecto final de la Especialización en inteligencia artificial (CEIA) de la Universidad de Buenos Aires (UBA).

En el mismo se aborda el problema de modelar un equipo de extracción de aceite vegetal para evaluar si es posible hacer una estimación puntual del contenido de materia grasa teniendo como variables de entrada distintos datos de sensores de campo. Otro objetivo importante del proyecto es conocer mejor el comportamiento del proceso a partir del análisis de datos.

Inicialmente el trabajo se divide en 4 etapas:
* **Import data**: El objetivo de esta etapa es desarrollar una cadena de procesamiento de datos que reciba los archivos entregados por el sistema de control, y sea capaz de estructurarlos de manera que faciliten el análisis y procesamiento posterior.
se realiza la importación de datos provenientes de un sistema SCADA y se estructuran para poder trabajar luego. Se alinean los timestamps, corrigen nombres de las features, se agrupan en un solo formato todos los chunks de datos.
<p align="center">
<img src="https://github.com/AlexBarria/CEIA_project/blob/main/Images/pipeline_import_data.PNG" width="425" height="145">
</p>
<p align="center">Figura 1: pipeline para la importación de datos</h1>

* **Data processing**: se realiza un análisis exploratorio de los datos, detección de outliers, evaluación de correlaciones y normalización de los datos.
<p align="center">
<img src="https://github.com/AlexBarria/CEIA_project/blob/main/Images/corr_matrix_test_init.png" width="425" height="380">
</p>
<p align="center">Figura 2: matriz de correlación (Pearson) de los datos</h1>

<p align="center">
<img src="https://github.com/AlexBarria/CEIA_project/blob/main/Images/mi_scores_test_init.png" width="450" height="350">
</p>
<p align="center">Figura 3: criterio de la información mutua con respecto a la variable que se intenta predecir</h1>

<p align="center">
<img src="https://github.com/AlexBarria/CEIA_project/blob/main/Images/distribuciones_iniciales.png" width="450" height="350">
</p>
<p align="center">Figura 4: distribuciones originales de los datos</h1>

<p align="center">
<img src="https://github.com/AlexBarria/CEIA_project/blob/main/Images/OL_vel_ext.png" width="500" height="150">
</p>
<p align="center">Figura 5: detección de outliers en la variable velocidad_extractor</h1>

<p align="center">
<img src="https://github.com/AlexBarria/CEIA_project/blob/main/Images/Concentraciones_3T_PGSM.png" width="350" height="350">
</p>
<p align="center">Figura 6: análisis de concentraciones dentro del extractor</h1>

* **Feature selection**: se seleccionan las features que mayor información aportan a distintos modelos, para seleccionar las variables se utiliza el criterio de la información mutua y análisis de correlaciones. También se utilizaron métoso de selección como RFE y SFS. En base a los resultados se armá el dataset final para entrenar los modelos de Machine learning y Deep learning.

* **Model selection**: en esta sección comenzamos a trabajar con los datos procesados provenientes de la etapa anterior para seleccionar el modelo que mejor performa sobre los datos. Fue probado un modelo de cada familia, considerando: support vector machine, random forest, XGBoost y redes neuronales MLP. Fue realizada una breve búsqueda de hiperparámetros utilizando GridSearch.

<p align="center">
<img src="https://github.com/AlexBarria/CEIA_project/blob/main/Images/validation_scores.png" width="450" height="350">
</p>
<p align="center">Figura 7: métricas sobre el set de validación</h1>

<p align="center">
<img src="https://github.com/AlexBarria/CEIA_project/blob/main/Images/validation_scores_FT.png" width="450" height="150">
</p>
<p align="center">Figura 8: métricas sobre el set de validación luego del fine tuning</h1>

<p align="center">
<img src="https://github.com/AlexBarria/CEIA_project/blob/main/Images/validation_scores_horiz_temp.png" width="450" height="150">
</p>
<p align="center">Figura 9: métricas obtenidas para distintos ohorizontes temporales</h1>

<p align="center">
<img src="https://github.com/AlexBarria/CEIA_project/blob/main/Images/test_scores.png" width="450" height="350">
</p>
<p align="center">Figura 10: métricas obtenidas sobre el set de test</h1>

**Ajuste de hiperparámetros utilizando OPTUNA**:
En base al análisis realizado se decidió utilizar un modelo de la familia XGBOOST. Para realizar el ajuste fino de los hiperparámetros se utilizó el framework OPTUNA, el cual aportó explicabilidad al impacto de cada hiparparámetro en la performance del modelo.

A continuación se pueden ver algunas imágenes obtenidas durante el ajuste fino de hiperparámetros.

<p align="center">
<img src="https://github.com/AlexBarria/CEIA_project/blob/main/Images/PARALLEL_COORD.png" width="800" height="350">
</p>
<p align="center">Figura 11: gráfico de coordenadas paralelas</h1>

<p align="center">
<img src="https://github.com/AlexBarria/CEIA_project/blob/main/Images/OPT_HIST.png" width="800" height="350">
</p>
<p align="center">Figura 12: historial de optimización de HPs</h1>

<p align="center">
<img src="https://github.com/AlexBarria/CEIA_project/blob/main/Images/HP_IMPORT.png" width="800" height="350">
</p>
<p align="center">Figura 13: importancia de los HPs para el modelo desarrollado</h1>

<p align="center">
<img src="https://github.com/AlexBarria/CEIA_project/blob/main/Images/CONTOUR.png" width="800" height="350">
</p>
<p align="center">Figura 14: gráfico de contorno para un subconjunto en particular de HPs</h1>

**Prueba en el conjunto de test**:

Finalmente, con el modelo obtenido luego del ajuste fino de hiperparámetros, se realizó una prueba sobre el conjunto de test.

<p align="center">
<img src="https://github.com/AlexBarria/CEIA_project/blob/main/Images/PRED.png" width="800" height="350">
</p>
<p align="center">Figura 15: predicciones sobre el conjunto de test</h1>




