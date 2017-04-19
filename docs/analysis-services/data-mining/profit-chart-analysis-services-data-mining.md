---
title: "Gr&#225;fico de beneficios (Analysis Services - Miner&#237;a de datos) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "precisión, gráficos"
  - "ingresos, estimar"
  - "beneficios, estimar"
  - "gráficos [Analysis Services]"
  - "gráficos de beneficios [Analysis Services]"
ms.assetid: 760ee051-6fd8-48e3-8d2e-82db3ab45e45
caps.latest.revision: 23
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 23
---
# Gr&#225;fico de beneficios (Analysis Services - Miner&#237;a de datos)
  Un gráfico de beneficios muestra la rentabilidad estimada asociada al uso de un modelo de minería de datos. Por ejemplo, suponga que su modelo predice con qué clientes debe ponerse en contacto una compañía en un escenario empresarial. En ese caso, agregaría al gráfico de beneficios información sobre el costo de realizar la campaña de envío de correo directo. Entonces, en el gráfico completo puede ver el beneficio estimado si se dirige correctamente a los clientes en comparación con si se pone en contacto con los clientes de forma aleatoria.  
  
## Crear un gráfico de beneficios  
 Un gráfico de beneficios es similar a un gráfico de mejora respecto al modelo predictivo. Empiece creando un gráfico de elevación y, después, agregue la información de costo y beneficios.  
  
 Para crear un gráfico de beneficios, debe tener un modelo existente.  
  
 En este ejemplo, hemos utilizado el modelo de árbol de decisiones de correo directo. El modelo identifica los clientes que es probable que compren una bicicleta. Puede aplicar el **Gráfico de beneficios** para determinar a cuántos de sus clientes debe dirigirse para maximizar el beneficio.  
  
 Si no tiene el modelo de ejemplo, puede crearlo mediante el [Basic Data Mining Tutorial](../Topic/Basic%20Data%20Mining%20Tutorial.md).  
  
1.  Abra el generador de gráficos de precisión de minería de datos.  
  
    -   En SQL Server Management Studio, haga clic con el botón derecho en el modelo y seleccione **Ver gráfico de elevación**.  
  
    -   En SQL Server Data Tools, abra el proyecto en el que creó el modelo y haga clic en la pestaña **Gráfico de precisión de minería de datos** .  
  
2.  En la pestaña **Selección de entrada** , seleccione el modelo y elija el valor del atributo de predicción.  
  
     En este escenario concreto, solo le interesa la rentabilidad de predecir con precisión un valor: [Bike Buyer] =1.  
  
     Sin embargo, hay otros escenarios en los que también le interesa predecir correctamente los valores false. Por ejemplo, el costo de un falso positivo en una prueba de diagnóstico médica puede ser considerable y es necesario tenerlo en cuenta en la rentabilidad de la predicción, al igual que el costo de los falsos negativos. En esos escenarios, mediría todos los resultados.  
  
3.  Seleccione un conjunto de datos para pruebas. En este ejemplo, seleccione el conjunto de datos de pruebas.  
  
4.  Ahora, haga clic en la pestaña **Gráfico de elevación** .  
  
     Se genera automáticamente un gráfico de elevación.  
  
5.  Para cambiarlo a un gráfico de beneficios, seleccione **Gráfico de beneficios** en la lista **Tipo de gráfico** .  
  
6.  En cuanto elija el gráfico de beneficios como tipo de gráfico, se abre automáticamente el cuadro de diálogo **Configuración del gráfico de beneficios** .  
  
     Este cuadro de diálogo ayuda a especificar los costos y los beneficios asociados con una campaña de envío de correo directo. Para el gráfico que se muestra en estos ejemplos, se usaron los valores siguientes:  
  
    |Configuración|Value|Comentarios|  
    |-------------|-----------|--------------|  
    |**Población**|20,000|Establezca el valor de la población total de destino<br /><br /> La base de datos puede contener muchos clientes, pero para ahorrar gastos de envío elige dirigirse solo a los 20.000 clientes que es más probable que respondan. Para obtener esta lista, ejecute una consulta de predicción y ordénela por el resultado de probabilidad del modelo de predicción.|  
    |**Costo fijo**|500|Especifique el costo de preparar una vez una campaña de envío de correo directo para 20.000 personas. Esto puede incluir la impresión, o el costo de configurar una campaña de correo electrónico.|  
    |**Costo individual**|3|Especifique el costo por unidad de la campaña de envío de correo directo.<br /><br /> Este importe se multiplicará por un número igual o menor que 20.000, según cuántos clientes prediga el modelo que son buenos candidatos.|  
    |**Ingresos por individuo**|400|Escriba un valor que representa la cantidad de beneficios o de ingresos que se pueden esperar de un resultado correcto. En este caso, supondremos que el envío por correo de un catálogo da como resultado la compra de accesorios o bicicletas por un promedio de $400.<br /><br /> Esta cantidad se usará para proyectar la ganancia total asociada a los casos de probabilidad alta.|  
  
7.  Después de haber definido los parámetros necesarios, haga clic en **Aceptar**.  
  
8.  El gráfico se actualiza para mostrar la curva de beneficios.  
  
## Descripción del gráfico de beneficios  
 El diagrama siguiente muestra un gráfico basado en estos parámetros. El eje Y del gráfico representa el beneficio, mientras que el eje X representa el porcentaje de los clientes con los que se ha puesto en contacto a través de la campaña de correo directo.  
  
 Como se puede ver aquí, se puede usar un gráfico de beneficios para comparar varios modelos, siempre y cuando todos ellos predigan el mismo atributo discreto.  
  
 ![un gráfico de beneficios que compara tres modelos](../../analysis-services/data-mining/media/dm14-profitchartupdated.gif "un gráfico de beneficios que compara tres modelos")  
  
 Observe la línea gris vertical del gráfico. A medida que hace clic y arrastra la línea, la información sobre herramientas muestra el porcentaje de la población de destino que se incluye en la curva en ese momento.  
  
 Cada vez que se arrastra la línea, también se actualiza la **Leyenda de minería de datos** para mostrar el valor porcentual, una puntuación de beneficios y la probabilidad de predicción asociada al porcentaje de población en la línea gris vertical.  
  
 Por ejemplo, si utilizara este modelo para decidir a quién va a enviar material promocional, podría decidir dirigirse al 25 % de la población, según las probabilidades de predicción. Sin embargo, el área que hay bajo la curva de beneficios del gráfico es mayor entre el 40 y el 70 por ciento, lo que indica que si se envía el correo a más personas, puede aumentar los ingresos, incluso aunque solo responda un porcentaje global menor.  
  
## Guardar gráficos  
 Al crear un gráfico de precisión o un gráfico de beneficios no se crea ningún objeto en el servidor. En su lugar, se ejecutan consultas en un modelo existente y se representan los resultados en el visor. Si necesita guardar los resultados, debe copiar el gráfico o los resultados a Excel u otro archivo.  
  
## Contenido relacionado  
 Los temas siguientes contienen más información acerca de cómo puede crear y usar gráficos de precisión.  
  
|Temas|Vínculos|  
|------------|-----------|  
|Incluye una visita guiada que explica cómo se crea un gráfico de mejora respecto al modelo predictivo para el modelo de distribución de correo directo.|[Tutorial básico de minería de datos](../Topic/Basic%20Data%20Mining%20Tutorial.md)<br /><br /> [Probar la exactitud con gráficos de mejora respecto al modelo predictivo &#40;Tutorial básico de minería de datos&#41;](../Topic/Testing%20Accuracy%20with%20Lift%20Charts%20\(Basic%20Data%20Mining%20Tutorial\).md)|  
|Explica los tipos de gráficos relacionados.|[Gráfico de mejora respecto al modelo predictivo &#40;Analysis Services - Minería de datos&#41;](../../analysis-services/data-mining/lift-chart-analysis-services-data-mining.md)<br /><br /> [Matriz de clasificación &#40;Analysis Services - Minería de datos&#41;](../../analysis-services/data-mining/classification-matrix-analysis-services-data-mining.md)<br /><br /> [Gráfico de dispersión &#40;Analysis Services - Minería de datos&#41;](../../analysis-services/data-mining/scatter-plot-analysis-services-data-mining.md)|  
|Describe la validación cruzada en los modelos y estructuras de minería de datos.|[Validación cruzada &#40;Analysis Services - Minería de datos&#41;](../../analysis-services/data-mining/cross-validation-analysis-services-data-mining.md)|  
|Describe los pasos necesarios para crear gráficos de mejora respecto al modelo predictivo y otros gráficos de precisión.|[Tareas y procedimientos de prueba y validación &#40;minería de datos&#41;](../../analysis-services/data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md)|  
  
## Vea también  
 [Prueba y validación &#40;minería de datos&#41;](../../analysis-services/data-mining/testing-and-validation-data-mining.md)   
 [Probar la exactitud con gráficos de mejora respecto al modelo predictivo &#40;Tutorial básico de minería de datos&#41;](../Topic/Testing%20Accuracy%20with%20Lift%20Charts%20\(Basic%20Data%20Mining%20Tutorial\).md)  
  
  