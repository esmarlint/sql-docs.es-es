---
title: El estado de sincronización de datos de bases de datos de disponibilidad no es correcto | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.agdashboard.arp3datasynchealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 4fd003e7-808e-4b0e-b28a-47d9f2616f06
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: erikre
ms.openlocfilehash: d8c98abcd48d9e1e703bd4e5ca73d62239727671
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34770181"
---
# <a name="data-synchronization-state-of-availability-database-is-not-healthy"></a>El estado de sincronización de datos de bases de datos de disponibilidad no está en buen estado
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="introduction"></a>Introducción  
  
|||  
|-|-|  
|**Nombre de directiva**|Estado de sincronización de datos de la base de datos de disponibilidad|  
|**Problema**|El estado de sincronización de datos de las bases de datos de disponibilidad no es correcto|  
|**Categoría**|**Advertencia**|  
|**Faceta**|Base de datos de disponibilidad|  
  
## <a name="description"></a>Descripción  
 Esta directiva acumula el estado de sincronización de datos de todas las bases de datos de disponibilidad (también conocidas como "réplicas de base de datos") en la réplica de disponibilidad. La directiva está en mal estado cuando alguna réplica de la base de datos no está en el estado esperado de sincronización de datos. De lo contrario, la directiva está en un estado correcto.  
  
> [!NOTE]  
>  Para esta versión de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], la información sobre las posibles causas y soluciones se encuentra en el artículo [El estado de sincronización de datos de alguna base de datos de disponibilidad no está en buen estado](http://go.microsoft.com/fwlink/p/?LinkId=220858) en TechNet Wiki.  
  
## <a name="possible-causes"></a>Posibles causas  
 El estado de sincronización de datos de esta base de datos de disponibilidad no es correcto. En una réplica de disponibilidad de confirmación asincrónica, cada base de datos de disponibilidad debe estar en el estado SYNCHRONIZING. En una réplica de confirmación sincrónica, cada base de datos de disponibilidad debe estar en el estado SYNCHRONIZED.  
  
## <a name="possible-solution"></a>Solución posible  
 Use la directiva de réplica de base de datos para buscar la réplica de base de datos que está en un estado incorrecto de sincronización de datos y, a continuación, resuelva el problema en la réplica de base de datos.  
  
## <a name="see-also"></a>Ver también  
 [Información general de los grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](~/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Usar el Panel de AlwaysOn &#40;SQL Server Management Studio&#41;](~/database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  


