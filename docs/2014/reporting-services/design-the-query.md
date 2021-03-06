---
title: Diseñar la consulta | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptwizard.designquery.f1
ms.assetid: 2dad800f-10a1-453c-8761-2935b9826d84
caps.latest.revision: 39
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: be1faf198c38ee9445602aa0e0bcc8ae66b5461a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37270311"
---
# <a name="design-the-query"></a>Diseñar la consulta
  Utilice esta página del Asistente para informes para crear una consulta escribiéndola manualmente, usando el Generador de consultas para crear una consulta de forma interactiva, o importando una consulta de otro informe.  
  
 El tipo de origen de datos seleccionado en la página Seleccionar el origen de datos, una página anterior del Asistente para informes, determina la consulta que se puede escribir en esta página. Por ejemplo, si el tipo de origen de datos es [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], puede escribir instrucciones [!INCLUDE[tsql](../includes/tsql-md.md)] o nombres de procedimientos almacenados. Si el tipo de origen de datos es [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], el panel Consulta está deshabilitado y no puede escribir una consulta directamente. Puede especificar la consulta mediante el Generador de consultas.  
  
## <a name="options"></a>Opciones  
 **Cadena de consulta**  
 Escriba una consulta que recupere los datos que desea utilizar en el informe.  
  
 **Generador de consultas**  
 Haga clic en **Generador de consultas** para abrir un diseñador de consultas para el origen de datos o para importar una consulta de otro informe.  
  
 Para obtener más información acerca de los diseñadores de consultas, vea [Reporting Services Query Designers](../../2014/reporting-services/reporting-services-query-designers.md).  
  
## <a name="example"></a>Ejemplo  
 Para el tipo de origen de datos **Microsoft SQL Server**, la consulta siguiente recupera una lista de apellidos de la [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] base de datos `Person` tabla.  
  
```  
SELECT LastName FROM Person.Person;  
```  
  
 Para el tipo de origen de datos **Microsoft SQL Server**, la siguiente consulta ejecuta el [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] procedimiento almacenado `uspGetEmployeeManagers` para el empleado con identificación de número 1:  
  
```  
EXEC uspgetEmployeeManagers '1';  
```  
  
## <a name="see-also"></a>Vea también  
 [Ayuda del Asistente para informes](../../2014/reporting-services/report-wizard-help.md)   
 [Conjuntos de datos incrustados y compartidos de informe &#40;Generador de informes y SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Agregar datos a un informe &#40;generador de informes y SSRS&#41;](report-data/report-datasets-ssrs.md)  
  
  
