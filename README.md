# CEIA_project


Este repositorio contiene el código correspondiente al proyecto final de la Especialización en inteligencia artificial (CEIA) de la Universidad de Buenos Aires (UBA).

En el mismo se aborda el problema de modelar un equipo de extracción de aceite vegetal para evaluar si es posible hacer una estimación puntual del contenido de materia grasa teniendo como variables de entrada distintos datos de sensores de campo. Luego se aborda el problema como uno de series temporales para poder realizar forecasting y predecir valores a distintos horizontes de tiempo.

Inicialmente el trabajo se divide en 4 etapas:
* **Import data**: se realiza la importación de datos provenientes de un sistema SCADA y se estructuran los datos para poder trabajar luego. Se alinean los timestamps, corrigen nombres de las features, se agrupan en un solo formato todos los chunks de datos.

* **Data processing**: se realiza un anális exploratorio de los datos, detección de outliers, se evalúan las correlaciones de los datos y se normalizan los datos.
Esta etapa fue una de las más importantes hasta el momento ya que a partir del análisis de los datos se descubrieron comportamientos del proceso que eran poco conocidos hasta el momento.

* **Feature selection**: se seleccionan las features que mayor información aportan a distintos modelos, se implementa selección recursiva de features (RFE), selección secuencial de features (SFS), entre otros. En base a los resultados se armá el dataset final para entrenar los modelos de Machine learning y Deep learning.

* **Model selection**: aquí se definen las métricas de evaluación para los distintos modelos y se prueba el desempeño de ellos para distintos juegos de hiperparámetros. 


*Los avances que se muestran son preliminares y el proyecto se encuentra en pleno desarrollo*




