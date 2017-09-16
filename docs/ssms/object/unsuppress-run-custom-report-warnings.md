---
title: "Anular la supresión de las advertencias de Ejecutar informe personalizado | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 0deed900-c910-4d12-aac0-6ab9e39eb068
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 20c37528ddb6bc1c93d86135ddcdf1ed0b9e2aa1
ms.contentlocale: es-es
ms.lasthandoff: 06/22/2017

---
# <a name="unsuppress-run-custom-report-warnings"></a>Anular la supresión de las advertencias de Ejecutar informe personalizado
Para los informes personalizados existen dos cuadros de diálogo de advertencia. En este tema se describe cómo anular la supresión de la presentación de estos cuadros en [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
De forma predeterminada, el cuadro de diálogo **Ejecutar informe personalizado** aparece antes de la ejecución de un informe personalizado. Si activa la casilla **No volver a mostrar esta advertencia** , el cuadro de diálogo ya no aparecerá más. De forma predeterminada, el cuadro de diálogo **Ejecutar informe personalizado** también aparece cuando se abre un informe personalizado y, a continuación, se hace clic en un vínculo para abrir otro informe personalizado. Este cuadro de diálogo muestra la ruta completa al archivo de informe detallado personalizado. Si activa la casilla **No volver a mostrar esta advertencia** , el cuadro de diálogo ya no aparecerá más.  
  
## <a name="SSMSProcedure"></a>Usar SQL Server Management Studio  
  
#### <a name="to-unsuppress-the-main-custom-report-warning-dialog-box"></a>Para anular la supresión del cuadro de diálogo de advertencia principal del informe personalizado  
  
1.  Conéctese a \<*Servidor*>\\<*Recurso compartido*>|\<*Unidad*>\Documents and Settings\\<UserProfile>\Application Data\Microsoft\Microsoft SQL Server\130\Tools\Shell\reports.xml.  
  
2.  Haga clic con el botón derecho en **reports.xml**y, luego, haga clic en **Editar**.  
  
3.  Cambie**<SuppressWarning>true\<\/SuppressWarning> a <SuppressWarning>false\<\/SuppressWarning>**.  
  
4.  Reinicie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
#### <a name="to-unsuppress-the-drill-through-custom-report-warning-dialog-box"></a>Para anular la supresión del cuadro de diálogo de advertencia del informe de obtención de detalles personalizado  
  
1.  Conéctese a \<*Servidor*>\\<*Recurso compartido*>|\<*Unidad*>\Documents and Settings\\<UserProfile>\Application Data\Microsoft\Microsoft SQL Server\130\Tools\Shell\reports.xml.  
  
2.  Haga clic con el botón derecho en **reports.xml**y, luego, haga clic en **Editar**.  
  
3.  Cambie **<SuppressDrillthroughWarning>true\<\/SuppressDrillthroughWarning> a <SuppressDrillthroughWarning>false\<\/SuppressDrillthroughWarning>**.  
  
4.  Reinicie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
## <a name="see-also"></a>Vea también  
[Informes personalizados en Management Studio](../../ssms/object/custom-reports-in-management-studio.md)  
[agregar un informe personalizado a Management Studio](../../ssms/object/add-a-custom-report-to-management-studio.md)  
[Usar informes personalizados con las propiedades de nodo del Explorador de objetos](../../ssms/object/use-custom-reports-with-object-explorer-node-properties.md)  
  
