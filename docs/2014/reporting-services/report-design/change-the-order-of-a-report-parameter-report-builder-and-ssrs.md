---
title: Cambiar el orden de un parámetro de informe (Generador de informes y SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: abd61e19-dba3-423c-a26c-e8bc43197d3f
caps.latest.revision: 6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 199b83364fceb93e59b9a1b32824166448a4c23f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37191295"
---
# <a name="change-the-order-of-a-report-parameter-report-builder-and-ssrs"></a>Cambiar el orden de un parámetro de informe (Generador de informes y SSRS)
  Cambie el orden de los parámetros de informe cuando tenga un parámetro dependiente que aparece antes que el parámetro del que depende. El orden de los parámetros es importante cuando se tienen parámetros en cascada, o cuando se desea mostrar a los usuarios el valor predeterminado de un parámetro antes de que elijan valores para otros parámetros. Un parámetro de informe dependiente contiene una referencia, ya sea en su consulta de valores predeterminados o en su consulta de valores válidos, a un parámetro de consulta que señala a un parámetro de informe situado después de él en la lista de parámetros del panel Datos de informe.  
  
 El orden en que se muestran los parámetros en la barra de herramientas del visor de informes lo determina el orden de los parámetros en el panel Datos de informe.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-order-of-report-parameters"></a>Para cambiar el orden de los parámetros de informe  
  
1.  En el panel Datos de informe, expanda el nodo Parámetros.  
  
2.  Haga clic en un parámetro y use los botones de flecha arriba y flecha abajo de la barra de herramientas del panel Datos de informe para mover el parámetro hacia arriba o hacia abajo en la lista. La siguiente imagen muestra el panel Datos de informe del Generador del informes.  
  
     ![Panel datos de informe](../media/reportdatapane.png "panel datos de informe")  
  
## <a name="see-also"></a>Vea también  
 [Parámetros de informe &#40;Generador de informes y Diseñador de informes&#41;](report-parameters-report-builder-and-report-designer.md)   
 [Ayuda del Generador de informes para cuadros de diálogo, paneles y asistentes](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Agregar parámetros en cascada a un informe &#40;generador de informes y SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [Tutorial: Agregar un parámetro a un informe &#40;Generador de informes&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Agregar filtros de conjunto de datos, filtros de región de datos y filtros de grupo &#40;Generador de informes y SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Referencias a la colección de parámetros &#40;generador de informes y SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md)  
  
  
