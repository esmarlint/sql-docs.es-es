---
title: "Definir relaciones normales y propiedades de las relaciones normales | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "atributo de granularidad"
  - "relaciones [Analysis Services], relaciones normales"
ms.assetid: 840280d8-20c3-46c0-99ea-62479469c36b
caps.latest.revision: 9
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 9
---
# Definir relaciones normales y propiedades de las relaciones normales
  Al definir una nueva dimensión de cubo o un nuevo grupo de medida, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] intentará detectar si existe una relación normal y, a continuación, establecerá la configuración de uso de la dimensión en **Normal**. Puede ver o modificar una relación de dimensión normal en la pestaña **Uso de dimensiones** del Diseñador de cubos.  
  
 Al definir la relación de una dimensión de cubo con un grupo de medida, también se especifica el atributo de granularidad de esa relación. El atributo de granularidad define el nivel mínimo de detalle disponible en el cubo para dicha dimensión, que suele ser el atributo clave de la dimensión. Sin embargo, en algunos casos, quizás desee establecer la granularidad de determinada dimensión de cubo de determinado grupo de medida en otra granularidad. Por ejemplo, si utiliza un grupo de medida Sales Quotas o Budget, quizás desee establecer el atributo de granularidad de la dimensión Time en el atributo Month, no en el atributo Day. Al especificar que el atributo de granularidad sea distinto del atributo clave, se debe garantizar que los demás atributos de la dimensión estén directa o indirectamente vinculados a este otro atributo por medio de relaciones de atributo. De lo contrario, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] no podrá agregar los datos correctamente.  
  
  