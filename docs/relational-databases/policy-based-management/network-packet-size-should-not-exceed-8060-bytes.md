---
title: El tamaño de paquete de red no debería superar 8060 bytes | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 86db5da1-afe4-4fbb-8bf8-33cedc7e4361
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3a79cd7cd9047b93e154bf63bad5b4968a62ff9b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32952800"
---
# <a name="network-packet-size-should-not-exceed-8060-bytes"></a>El tamaño de paquete de red no debería superar 8060 bytes
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Si el valor especificado para sp_configure 'network packet size' o si el tamaño de paquete de red de cualquier usuario registrado es mayor que 8060 bytes, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] realiza diferentes operaciones de asignación de memoria. Esto puede producir un aumento en el espacio de direcciones virtuales de proceso que no se reserva para el grupo de búferes.  
  
## <a name="best-practices-recommendations"></a>Prácticas recomendadas  
 El tamaño de paquete de red no debería superar 8060 bytes.  
  
## <a name="for-more-information"></a>Para obtener más información  
 [Artículo 903002 de Microsoft Knowledge Base](http://go.microsoft.com/fwlink/?linkid=117749)  
  
## <a name="see-also"></a>Ver también  
 [Supervisar y aplicar las prácticas recomendadas usando la administración basada en directivas](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
