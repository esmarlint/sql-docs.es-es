---
title: Importar las directivas a una sola instancia | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: bc5bcd87-663f-41d9-bb7b-b3e083cd63df
caps.latest.revision: 8
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 4c45508880948c3ce1cb4814eca918278a66aacb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37177152"
---
# <a name="import-the-policies-to-a-single-instance"></a>Importar las directivas a una instancia única
  En esta tarea, importará las directivas de prácticas recomendadas que desea programar en la administración basada en directivas en una única instancia de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="prerequisites"></a>Requisitos previos  
 Debe realizar este procedimiento en un servidor que ejecute [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] o una versión posterior.  
  
### <a name="import-the-best-practices-policies-for-the-database-engine"></a>Importar las directivas de prácticas recomendadas para el Motor de base de datos  
  
1.  Inicie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]y después conéctese a [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
2.  En el Explorador de objetos, expanda **Administración**y, a continuación, expanda **Administración de directivas**.  
  
3.  Haga clic con el botón secundario en **Directivas**y, a continuación, haga clic en **Importar directiva**.  
  
4.  En el cuadro de diálogo **Importar** , junto al cuadro **Archivos para importar** , haga clic en el botón de puntos suspensivos (**...**).  
  
5.  En la lista **Buscar en** , busque la carpeta siguiente, que contiene las directivas de prácticas recomendadas:  
  
     **C:\Program archivos (x86) \Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**  
  
    > [!NOTE]  
    >  La ruta de acceso puede variar según dónde instalara los archivos de programa de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , si ejecuta un sistema operativo de 32 bits o de 64 bits y el identificador de idioma.  
  
6.  En el cuadro de diálogo **Seleccionar directiva** , seleccione uno o más archivos de directivas.  
  
     Para seleccionar archivos no consecutivos, haga clic en uno, mantenga presionada la tecla CTRL y, a continuación, haga clic en cada archivo adicional. Para seleccionar archivos consecutivos, haga clic en el primero de la secuencia, mantenga presionada la tecla MAYÚS y, a continuación, haga clic en el último archivo.  
  
7.  Cuando termine de seleccionar los archivos, haga clic en **Abrir**.  
  
8.  En el cuadro de diálogo **Importar** , asegúrese de que la lista **Estado de directiva** está establecida en **Conservar el estado de las directivas al importar** (el valor predeterminado) y, a continuación, haga clic en **Aceptar**.  
  
     Las directivas se importan en el nodo **Directivas** en **Administración de directivas**. De forma predeterminada, las directivas importadas se establecen en el modo de evaluación "A petición".  
  
## <a name="next-steps"></a>Pasos siguientes  
 [Programar las directivas](../../2014/tutorials/schedule-the-policies.md)  
  
  
