---
title: "Referencia t&#233;cnica del algoritmo de regresi&#243;n log&#237;stica de Microsoft | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "regresión logística [Analysis Services]"
  - "MAXIMUM_INPUT_ATTRIBUTES, parámetro"
  - "HOLDOUT_PERCENTAGE, parámetro"
  - "MAXIMUM_OUTPUT_ATTRIBUTES, parámetro"
  - "MAXIMUM_STATES, parámetro"
  - "SAMPLE_SIZE, parámetro"
  - "algoritmos de regresión [Analysis Services]"
  - "HOLDOUT_SEED, parámetro"
ms.assetid: cf32f1f3-153e-476f-91a4-bb834ec7c88d
caps.latest.revision: 17
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 17
---
# Referencia t&#233;cnica del algoritmo de regresi&#243;n log&#237;stica de Microsoft
  El algoritmo de regresión logística de [!INCLUDE[msCoName](../../includes/msconame-md.md)] es una variación del algoritmo de red neuronal de [!INCLUDE[msCoName](../../includes/msconame-md.md)], donde el parámetro *HIDDEN_NODE_RATIO* se establece en 0. Este valor creará un modelo de red neuronal que no contenga un nivel oculto y que, por consiguiente, sea equivalente a la regresión logística.  
  
## Implementación del algoritmo de regresión logística de Microsoft  
 Supongamos que la columna de predicción solo contiene dos estados, pero que aun así desea realizar un análisis de regresión, relacionando las columnas de entrada con la probabilidad de que la columna de predicción contenga un estado específico. El siguiente diagrama muestra los resultados que obtendrá si asigna 1 y 0 a los estados de la columna de predicción, calcula la probabilidad de que la columna contenga un estado específico y realiza una regresión lineal en una variable de entrada.  
  
 ![Datos con modelo incorrecto creado con regresión linear](../../analysis-services/data-mining/media/logistic-linear-regression.gif "Datos con modelo incorrecto creado con regresión linear")  
  
 El eje x contiene los valores de una columna de entrada. El eje y contiene las probabilidades de que la columna de predicción tenga un estado o el otro. El problema que puede surgir es que la regresión lineal no limite la columna a los valores 0 y 1, a pesar de que son los valores máximo y mínimo de la columna. Una forma de resolver el problema es llevar a cabo una regresión logística. En vez de crear una línea recta, el análisis de regresión logística crea una curva con forma de "S" que contiene las restricciones máxima y mínima. Por ejemplo, el siguiente diagrama muestra los resultados que se obtienen si lleva a cabo una regresión logística con los mismos datos utilizados en el ejemplo anterior.  
  
 ![Datos con modelo creado con regresión logística](../../analysis-services/data-mining/media/logistic-regression.gif "Datos con modelo creado con regresión logística")  
  
 Observe cómo la curva nunca sobrepasa el valor 1 o disminuye por debajo de 0. Puede utilizar la regresión logística para describir qué columnas de entrada son importantes para determinar el estado de la columna de predicción.  
  
### Selección de características  
 Todos los algoritmos de minería de datos de Analysis Services utilizan automáticamente la selección de características para mejorar el análisis y reducir la carga de procesamiento. El método utilizado para la selección de características en un modelo de regresión logística depende del tipo de datos del atributo. Dado que la regresión logística se basa en el algoritmo de red neuronal de Microsoft, utiliza un subconjunto de los métodos de selección de características que se aplican a las redes neuronales. Para más información, vea [Selección de características &#40;minería de datos&#41;](../../analysis-services/data-mining/feature-selection-data-mining.md).  
  
### Entradas de puntuación  
 La*puntuación* en el contexto de un modelo de red neuronal o de regresión logística implica el proceso de convertir los valores que están presentes en los datos en un conjunto de valores que utilizan la misma escala y, por consiguiente, se pueden comparar entre sí. Por ejemplo, suponga que las entradas para los ingresos abarcan de 0 a 100.000 mientras que las entradas para [Número de hijos] abarcan de 0 a 5. Este proceso de conversión permite comparar la importancia de cada entrada sin tener en cuenta la diferencia en los valores.  
  
 Para cada estado que aparece en el conjunto de entrenamiento, el modelo genera una entrada. Para las entradas discretas o de datos discretos, se crea una entrada adicional para representar el estado Missing, si aparece al menos una vez en el conjunto de entrenamiento. En las entradas continuas, se crean al menos dos nodos de entrada: uno para los valores Missing, si están presentes en los datos de entrenamiento, y una entrada para todos los valores existentes o no nulos. Cada entrada se escala a un formato numérico mediante el método de normalización de puntuación-z, `(x – μ)\StdDev`.  
  
 Durante la normalización de puntuación-z, la media (μ) y la desviación estándar se obtienen sobre el conjunto de entrenamiento completo.  
  
 **Valores continuos**  
  
 El valor está presente: `(X – μ)/σ ` (X es el valor real que se va a codificar)  
  
 El valor está ausente: `-   μ/σ ` (mu negativo dividido por sigma)  
  
 **Valores discretos**  
  
 `μ = p`  (la probabilidad anterior de un estado)  
  
 StdDev  `= sqrt(p\(1-p))`  
  
 El valor está presente: `\(1 – μ)/σ` (uno menos mu dividido por sigma)  
  
 El valor está ausente: `(– μ)/σ` (mu negativo dividido por sigma)  
  
### Descripción de los coeficientes de regresión logística  
 Hay varios métodos en la literatura estadística para realizar la regresión logística, pero una parte importante de todos ellos consiste en evaluar el ajuste del modelo. Se han propuesto diversas estadísticas fáciles de ajustar, entre ellas el cociente de probabilidades y los patrones de covariable. La explicación de cómo medir el ajuste de un modelo escapa del ámbito de este tema; sin embargo, puede recuperar el valor de los coeficientes en el modelo y utilizarlos para diseñar sus propias medidas de ajuste.  
  
> [!NOTE]  
>  Los coeficientes que se crean como parte de un modelo de regresión logística no representan el cociente de probabilidades y no se deberían interpretar como tal.  
  
 Los coeficientes para cada nodo del grafo del modelo representan una suma ponderada de las entradas a ese nodo. En un modelo de regresión logística, el nivel oculto está vacío; por consiguiente, solamente hay un conjunto de coeficientes, que se almacena en los nodos de salida. Puede recuperar los valores de los coeficientes utilizando la consulta siguiente:  
  
```  
SELECT FLATTENED [NODE_UNIQUE NAME],  
(SELECT ATTRIBUTE_NAME< ATTRIBUTE_VALUE  
FROM NODE_DISTRIBUTION) AS t  
FROM <model name>.CONTENT  
WHERE NODE_TYPE = 23  
```  
  
 Para cada valor de salida, esta consulta devuelve los coeficientes y un identificador que señala al nodo de entrada relacionado. También devuelve una fila que contiene el valor de la salida y la intersección. Cada entrada X tiene su propio coeficiente (Ci), pero la tabla anidada también contiene un coeficiente "libre" (Co), calculado según la fórmula siguiente:  
  
 `F(X) = X1*C1 + X2*C2 + … +Xn*Cn + X0`  
  
 Activación: `exp(F(X)) / (1 + exp(F(X)) )`  
  
 Para más información, vea [Ejemplos de consultas de modelos de regresión logística](../../analysis-services/data-mining/logistic-regression-model-query-examples.md).  
  
## Personalizar el algoritmo de regresión logística  
 El algoritmo de regresión logística de [!INCLUDE[msCoName](../../includes/msconame-md.md)] admite varios parámetros que influyen en el comportamiento, el rendimiento y la precisión del modelo de minería de datos resultante. También puede modificar el comportamiento del modelo estableciendo marcas de modelado en las columnas que se usan como entrada.  
  
### Establecer parámetros del algoritmo  
 En la tabla siguiente se describen los parámetros que se pueden utilizar con el algoritmo de regresión logística de Microsoft.  
  
 HOLDOUT_PERCENTAGE  
 Especifica el porcentaje de casos en los datos de entrenamiento que se usan para calcular el error de exclusión. HOLDOUT_PERCENTAGE se utiliza como parte de los criterios de detención durante el entrenamiento del modelo de minería de datos.  
  
 El valor predeterminado es 30.  
  
 HOLDOUT_SEED  
 Especifica un número que se utiliza para inicializar el generador pseudoaleatorio cuando se determinan aleatoriamente los datos de exclusión. Si HOLDOUT_SEED se establece en 0, el algoritmo genera la inicialización basada en el nombre del modelo de minería de datos, para garantizar que el contenido del modelo sigue siendo el mismo durante el nuevo procesamiento.  
  
 El valor predeterminado es 0.  
  
 MAXIMUM_INPUT_ATTRIBUTES  
 Define el número de atributos de entrada que el algoritmo puede controlar antes de invocar la selección de características. Establezca este valor en 0 para desactivar la selección de características.  
  
 El valor predeterminado es 255.  
  
 MAXIMUM_OUTPUT_ATTRIBUTES  
 Define el número de atributos de salida que el algoritmo puede controlar antes de invocar la selección de características. Establezca este valor en 0 para desactivar la selección de características.  
  
 El valor predeterminado es 255.  
  
 MAXIMUM_STATES  
 Especifica el número máximo de estados de atributo que admite el algoritmo. Si el número de estados que tiene un atributo es mayor que el número máximo de estados, el algoritmo utiliza los estados más conocidos del atributo y pasa por alto los estados restantes.  
  
 El valor predeterminado es 100.  
  
 SAMPLE_SIZE  
 Especifica el número de casos que se van a usar para realizar el entrenamiento del modelo. El proveedor de algoritmos usa el valor menor entre este número o el porcentaje del total de los casos que no están incluidos en el porcentaje de datos de exclusión según se especifica en el parámetro HOLDOUT_PERCENTAGE.  
  
 En otras palabras, si HOLDOUT_PERCENTAGE está establecido en 30, el algoritmo usará el valor de este parámetro o un valor que sea igual al 70 por ciento del número total de casos, el que sea menor.  
  
 El valor predeterminado es 10000.  
  
### Marcas de modelado  
 El algoritmo de regresión logística de [!INCLUDE[msCoName](../../includes/msconame-md.md)] admite las siguientes marcas de modelado.  
  
 NOT NULL  
 Indica que la columna no puede contener un valor NULL. Se producirá un error si Analysis Services encuentra un valor NULL durante el entrenamiento del modelo.  
  
 Se aplica a las columnas de la estructura de minería de datos.  
  
 MODEL_EXISTENCE_ONLY  
 Significa que la columna se tratará como si tuviera dos estados posibles: **Missing** y **Existing**. Un valor NULL es un valor ausente.  
  
 Se aplica a la columna del modelo de minería de datos.  
  
## Requisitos  
 Un modelo de regresión logística debe contener una columna de clave, columnas de entrada y al menos una columna de predicción.  
  
### Columnas de entrada y de predicción  
 El algoritmo de regresión logística de [!INCLUDE[msCoName](../../includes/msconame-md.md)] admite los tipos de contenido de columna de entrada, tipos de contenido de columna de predicción y marcas de modelado específicos que se enumeran en la siguiente tabla. Para más información sobre lo que significan los tipos de contenido cuando se usan en un modelo de minería de datos, vea [Tipos de contenido &#40;minería de datos&#41;](../../analysis-services/data-mining/content-types-data-mining.md).  
  
|Columna|Tipos de contenido|  
|------------|-------------------|  
|Atributo de entrada|Continuo, discreto, de datos discretos, clave, tabla|  
|Atributo de predicción|Continuo, discreto, de datos discretos|  
  
## Vea también  
 [Algoritmo de regresión logística de Microsoft](../../analysis-services/data-mining/microsoft-logistic-regression-algorithm.md)   
 [Ejemplos de consultas de modelos de regresión lineal](../../analysis-services/data-mining/linear-regression-model-query-examples.md)   
 [Contenido del modelo de minería de datos para los modelos de regresión logística &#40;Analysis Services - Minería de datos&#41;](../../analysis-services/data-mining/mining model content for logistic regression models.md)   
 [Algoritmo de red neuronal de Microsoft](../../analysis-services/data-mining/microsoft-neural-network-algorithm.md)  
  
  