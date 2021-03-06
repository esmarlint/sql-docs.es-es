---
title: Tarea Ejecutar trabajo del Agente SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqlserveragentjobtask.f1
helpviewer_keywords:
- Execute SQL Server Agent Job task [Integration Services]
- jobs [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 3aa3bc0e-1a1c-452e-81b8-b4e3422ea053
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ead21855d754a9e5b48572e5576b311db5b32983
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37173266"
---
# <a name="execute-sql-server-agent-job-task"></a>Tarea Ejecutar trabajo del Agente SQL Server
  La tarea Ejecutar trabajo del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ejecuta trabajos del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] es un servicio de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows que ejecuta trabajos definidos en una instancia de SQL Server. Puede crear trabajos que ejecuten instrucciones de Transact-SQL y scripts de ActiveX, realizar tareas de mantenimiento de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] y Replicación, o ejecutar paquetes. También puede configurar un trabajo para supervisar [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y activar alertas. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generalmente se utilizan para automatizar tareas que se realizan con frecuencia. Para más información, vea [Implementar trabajos](../../ssms/agent/implement-jobs.md).  
  
 Un paquete puede utilizar la tarea Ejecutar trabajo del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para realizar tareas administrativas relacionadas con componentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Por ejemplo, un trabajo del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] puede ejecutar un procedimiento almacenado del sistema, como **sp_enum_dtspackages** , para obtener una lista de paquetes de una carpeta.  
  
> [!NOTE]  
>  El Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] debe estar ejecutándose para poder ejecutar automáticamente trabajos administrativos locales o multiservidor.  
  
 Esta tarea encapsula el procedimiento del sistema **sp_start_job** y pasa el nombre del trabajo del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] al procedimiento como un argumento. Para obtener más información, vea [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql).  
  
## <a name="configuring-the-execute-sql-server-agent-job-task"></a>Configurar la tarea Ejecutar trabajo del Agente SQL Server  
 Puede establecer propiedades a través del Diseñador [!INCLUDE[ssIS](../../../includes/ssis-md.md)] . Esta tarea se encuentra en la sección **Tareas del plan de mantenimiento** del **Cuadro de herramientas** , en el Diseñador [!INCLUDE[ssIS](../../../includes/ssis-md.md)] .  
  
 Para obtener más información acerca de las propiedades que puede establecer en el Diseñador [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , haga clic en el tema siguiente:  
  
-   [Tarea Ejecutar trabajo del Agente SQL Server &#40;Plan de mantenimiento&#41;](../../relational-databases/maintenance-plans/execute-sql-server-agent-job-task-maintenance-plan.md)  
  
 Para obtener más información sobre cómo establecer estas propiedades en el Diseñador [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , haga clic en el siguiente tema:  
  
-   [Establecer las propiedades de tareas o contenedores](../set-the-properties-of-a-task-or-container.md)  
  
  
