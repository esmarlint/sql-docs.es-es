---
title: Informe de evaluación (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Assessment Report dialog box
- Conversion Report dialog box
ms.assetid: ba6f53aa-0049-4c49-8bb8-607a8bfaa737
caps.latest.revision: 14
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 8a268b123663b213f3702dde24eba905e38bf1ac
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2018
ms.locfileid: "38980008"
---
# <a name="assessment-report-accesstosql"></a>Informe de evaluación (AccessToSQL)
La ventana Informe de evaluación muestra los resultados de la conversión de objetos de base de datos a [!INCLUDE[tsql](../../includes/tsql_md.md)] sintaxis, y también puede ayudarle a estimar la complejidad y el costo de los proyectos de migración.  
  
Para crear un informe de evaluación, seleccionar objetos para convertir en el Explorador de metadatos de origen, haga clic en **bases de datos**y, a continuación, seleccione **crear informe**. Este informe también se puede mostrar automáticamente después de convertir los esquemas. Sin embargo, el nombre del informe será el informe de conversión. Para obtener más información, consulte [configuración de proyecto (GUI) (SSMA comunes)](http://msdn.microsoft.com/cf06baf1-8714-48a3-95dc-781f6ca53693).  
  
## <a name="options"></a>Opciones  
**Panel del explorador**  
Contiene una jerarquía de objetos en el informe de evaluación. Expanda las carpetas para ver los subcomponentes y objetos individuales. Al hacer clic en una categoría o un objeto, aparecen las estadísticas de conversión para esa categoría o el objeto en el panel de detalles.  
  
**Panel de detalles**  
Muestra mensajes de las estadísticas o error y advertencia para el objeto seleccionado de conversión. Por ejemplo, si se selecciona la carpeta tablas, el panel de detalles mostrará los números de las claves externas, índices, claves principales y las tablas que se han convertido.  
  
**Panel de mensajes**  
Muestra los errores, advertencias y mensajes de información que se generaron cuando se creó el informe de evaluación. Los mensajes se agrupan por número.  
  
Para ver los detalles del mensaje, haga clic en **errores**, **advertencias**, o **mensajes**y, a continuación, expanda un mensaje. SSMA mostrará la lista de objetos que tienen este error. Haga clic en un objeto para mostrar todos los detalles de conversión para el objeto.  
  
## <a name="see-also"></a>Vea también  
[Reference(Access) de interfaz de usuario](http://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
