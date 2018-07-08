---
title: Derivar valores de columna mediante la transformación Columna derivada | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- columns [Integration Services]
- derived columns
- columns [Integration Services], values
- Derived Column transformation
ms.assetid: 28b07746-fc6f-42b2-b741-9de6fac3f29c
caps.latest.revision: 46
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 569d9edeadfab6f31cf3c4d01bbe57e50c1648fd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36203990"
---
# <a name="derive-column-values-by-using-the-derived-column-transformation"></a>Derivar valores de columna mediante la transformación Columna derivada
  Para agregar y configurar una transformación Columna derivada, el paquete ya debe incluir por lo menos una tarea Flujo de datos y un origen.  
  
 La transformación Columna derivada usa expresiones para actualizar los valores de las columnas existentes o agregar valores a las nuevas. Si se elige agregar valores a columnas nuevas, el cuadro de diálogo **Editor de transformación Columna derivada** evalúa la expresión y define los metadatos de las columnas en función del resultado. Por ejemplo, si una expresión concatena dos columnas (cada una con el tipo de datos DT_WSTR y una longitud de 50) con un espacio entre los dos valores de las columnas, la nueva columna tiene el tipo de datos DT_WSTR y una longitud de 101. El tipo de datos de las columnas nuevas se puede actualizar. El único requisito es que el tipo de datos sea compatible con los datos insertados. Por ejemplo, el cuadro de diálogo **Editor de transformación Columna derivada** genera un error de validación si se asigna un valor de datos a una columna con tipo de datos entero. En función del tipo de datos seleccionado, se puede especificar la longitud, precisión, escala y página de códigos de la columna.  
  
### <a name="to-derive-column-values"></a>Para derivar valores de columna  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], abra el proyecto de [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] que contiene el paquete que desea.  
  
2.  En el Explorador de soluciones, haga doble clic en el paquete para abrirlo.  
  
3.  Haga clic en la pestaña **Flujo de datos** y, a continuación, desde el **cuadro de herramientas**, arrastre la transformación Columna derivada a la superficie de diseño.  
  
4.  Conecte la transformación Columna derivada al flujo de datos arrastrando el conector desde el origen o la transformación anterior a la transformación Columna derivada.  
  
5.  Haga doble clic en la transformación Columna derivada.  
  
6.  En el cuadro de diálogo **Editor de transformación Columna derivada** , genere las expresiones que se usan como condiciones arrastrando variables, columnas, funciones y operadores a la columna **Expresión** en la cuadrícula. Como alternativa, puede escribir la expresión en la columna **Expresión** .  
  
    > [!NOTE]  
    >  Si la expresión no es válida, el texto de la expresión se resalta y la información sobre herramientas de la columna describe los errores.  
  
7.  En la lista **Columna derivada**, seleccione **\<agregar como columna nueva>** para escribir el resultado de evaluación de la expresión en una nueva columna, o seleccione una columna existente para actualizarla con el resultado de la evaluación.  
  
     Si se decide usar una columna nueva, el cuadro de diálogo **Editor de transformación Columna derivada** evalúa la expresión y asigna un tipo de datos a la columna, en función del tipo de datos, la longitud, precisión, escala y página de códigos.  
  
8.  Al utilizar una nueva columna, seleccione un tipo de datos en la lista **Tipo de datos** . Según el tipo de datos seleccionado, actualice opcionalmente los valores en las columnas **Longitud**, **Precisión**, **Escala**y **Página de códigos** . Los metadatos de las columnas existentes no pueden cambiarse.  
  
9. Opcionalmente, modifique los valores de la columna **Nombre de columna derivada** .  
  
10. Para configurar la salida de error, haga clic en **Configurar la salida de errores**. Para más información, vea [Configurar una salida de error en un componente de flujo de datos](../../configure-an-error-output-in-a-data-flow-component.md).  
  
11. Haga clic en **Aceptar**.  
  
12. Para guardar el paquete actualizado, haga clic en **Guardar los elementos seleccionados**, en el menú **Archivo**.  
  
## <a name="see-also"></a>Vea también  
 [Transformación columna derivada](derived-column-transformation.md)   
 [Tipos de datos de Integration Services](../integration-services-data-types.md)   
 [Transformaciones de Integration Services](integration-services-transformations.md)   
 [Rutas de Integration Services](../integration-services-paths.md)   
 [Tarea de flujo de datos] ((.. /.. /Control-Flow/Data-Flow-Task.MD)   
 [Expresiones de Integration Services &#40;SSIS&#41;](../../expressions/integration-services-ssis-expressions.md)  
  
  