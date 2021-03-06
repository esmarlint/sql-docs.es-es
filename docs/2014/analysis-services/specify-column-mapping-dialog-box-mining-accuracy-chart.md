---
title: Especifique (gráfico de precisión de minería de datos) del cuadro de diálogo de asignación de columnas | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.coltotablecolmapping.f1
ms.assetid: 68e9e2d2-173f-4363-a515-fc60bfee3af0
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2ed607ca38d0cfda0aee7a3b5d8ebbd683570676
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37306535"
---
# <a name="specify-column-mapping-dialog-box-mining-accuracy-chart"></a>Cuadro de diálogo Especificar asignación de columna (gráfico de precisión de minería de datos) 
  Utilice la pestaña **Especificar asignación de columnas** para seleccionar las tablas de un origen de datos externo y asignar las columnas a un modelo de minería de datos. Después puede utilizar los datos externos para probar la exactitud de un modelo de minería y mostrar los resultados en el gráfico de precisión.  
  
 **Para obtener más información:** [Prueba y validación &#40;minería de datos&#41;](data-mining/testing-and-validation-data-mining.md).  
  
## <a name="options"></a>Opciones  
 **Estructura de minería de datos**  
 Muestra la estructura de minería de datos seleccionada que contiene el modelo que probará.  
  
 **Seleccionar estructura**  
 Haga clic para abrir el cuadro de diálogo **Seleccionar estructura de minería de datos** y seleccione una estructura de minería de datos diferente.  
  
 **Seleccione las tablas de entrada**  
 Muestra las tablas de entrada seleccionadas que se usan para generar el gráfico de elevación. Seleccione la tabla que contiene los datos de prueba que va a utilizar para probar la precisión de los modelos.  
  
> [!NOTE]  
>  Si el panel no contiene ninguna tabla, haga clic en **Seleccionar tabla de casos** para agregar las tablas de una vista del origen de datos.  
  
 **Quitar tabla**  
 Quita la tabla seleccionada. Este botón está deshabilitado si no se ha seleccionado una tabla o si no se muestra ninguna tabla en la lista **Seleccionar tabla(s) de entrada** .  
  
 **Seleccionar tabla de casos**  
 Haga clic para abrir el cuadro de diálogo **Seleccionar tabla** y seleccione una vista del origen de datos.  
  
 **Nota** : este botón solo aparece si no se ha seleccionado una tabla de casos. Para habilitar el botón de modo que pueda seleccionar una tabla de casos diferente, borre la lista seleccionando todas las tablas existentes y haciendo clic en **Quitar tabla**.  
  
 **Seleccionar tabla anidada**  
 Abre el cuadro de diálogo **Seleccionar tabla** . Este botón solo aparece si se ha seleccionado una tabla de casos. Este botón se deshabilita si la estructura de minería de datos asociada no contiene una tabla anidada.  
  
 **Modificar combinación**  
 Abre el cuadro de diálogo **Especificar combinación anidada** . Este botón solo está activo si se ha seleccionado una tabla anidada.  
  
## <a name="see-also"></a>Vea también  
 [Pruebas y validación tareas y procedimientos &#40;minería de datos&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md)   
 [Diseñador gráfico de precisión de minería de datos &#40;minería de datos&#41;](mining-accuracy-chart-designer-data-mining.md)  
  
  
