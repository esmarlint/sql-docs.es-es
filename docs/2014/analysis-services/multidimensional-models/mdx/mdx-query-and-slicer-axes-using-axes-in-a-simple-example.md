---
title: Uso de ejes de consulta y segmentador en un ejemplo Simple (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- slicer axis
- query axis [MDX]
ms.assetid: 85bcb26f-5971-4153-b334-61f8d8b475b5
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9b6eb6140795995f2fb035e9972a7c89396fd83a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37197915"
---
# <a name="using-query-and-slicer-axes-in-a-simple-example-mdx"></a>Usar los ejes de consulta y segmentador en un ejemplo simple (MDX)
  En este sencillo ejemplo se ilustran los conceptos en los que se basa la especificación y el uso de los ejes de consulta y segmentador.  
  
## <a name="the-cube"></a>Cubo  
 Un cubo, denominado TestCube, tiene dos dimensiones simples: Route y Time. Cada dimensión solo tiene una jerarquía de usuario, denominadas Route y Time respectivamente. Puesto que las medidas del cubo son parte de la dimensión Measures, este cubo tiene tres dimensiones en total.  
  
## <a name="the-query"></a>Consulta  
 La consulta va a proporcionar una matriz en la que la medida Packages se puede comparar con rutas (routes) y tiempos (times).  
  
 En la siguiente consulta MDX de ejemplo, las jerarquías Route y Time se utilizan como ejes de la consulta y la dimensión Measures como eje segmentador. La función [Members](/sql/mdx/members-set-mdx) indica que MDX usará los miembros de la jerarquía o el nivel para generar un conjunto. El uso de la función `Members` implica que no es necesario especificar explícitamente cada miembro de una jerarquía o un nivel específicos de una consulta MDX.  
  
```  
SELECT  
   { Route.nonground.Members } ON COLUMNS,  
   { Time.[1st half].Members } ON ROWS  
FROM TestCube  
WHERE ( [Measures].[Packages] )  
```  
  
## <a name="the-results"></a>Resultado  
 El resultado es una cuadrícula que identifica el valor de la medida Packages en cada intersección de las dimensiones de eje COLUMNS y ROWS. En la tabla siguiente se muestra el aspecto que tendría la cuadrícula.  
  
||air|sea|  
|-|---------|---------|  
|1st quarter|60|50|  
|2nd quarter|45|45|  
  
## <a name="see-also"></a>Vea también  
 [Especificar el contenido de un eje de consulta &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)   
 [Especificar el contenido de un eje segmentador &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)  
  
  
