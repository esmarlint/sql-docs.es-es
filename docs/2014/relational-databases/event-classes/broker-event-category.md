---
title: Categoría de eventos Broker | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Broker event category
- Broker event category [SQL Server]
- event classes [SQL Server], Broker event category
ms.assetid: 470dc93c-0dda-4d89-829b-937738d59b31
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: da45f076ba427f2a0c69b7cf1a335049ce885e24
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37170856"
---
# <a name="broker-event-category"></a>Broker (categoría de eventos)
  La categoría de eventos **Broker** contiene eventos generales de Service Broker.  
  
## <a name="in-this-section"></a>En esta sección  
  
|Tema|Descripción|  
|-----------|-----------------|  
|[Broker:Activation (clase de eventos)](broker-activation-event-class.md)|Evento que se genera cuando un monitor de cola inicia un procedimiento almacenado de activación.|  
|[Broker:Connection (clase de eventos)](broker-connection-event-class.md)|Evento generado para informar del estado de una conexión de transporte administrada por Service Broker.|  
|[Broker:Conversation (clase de eventos)](broker-conversation-event-class.md)|Evento generado para informar sobre el progreso de una conversación.|  
|[Broker:Conversation Group (clase de eventos)](broker-conversation-group-event-class.md)|Evento generado cuando la base de datos crea o quita un grupo de conversación.|  
|[Broker:Corrupted Message (clase de eventos)](broker-corrupted-message-event-class.md)|Evento que se genera para informar de que la base de datos ha recibido un mensaje dañado.|  
|[Broker:Forwarded Message Dropped (clase de eventos)](broker-forwarded-message-dropped-event-class.md)|Evento que se genera cuando SQL Server quita un mensaje de Service Broker que tenía que haberse reenviado.|  
|[Broker:Forwarded Message Sent (clase de eventos)](broker-forwarded-message-sent-event-class.md)|Evento que se genera cuando SQL Server reenvía un mensaje de Service Broker.|  
|[Broker:Message Classify (clase de eventos)](broker-message-classify-event-class.md)|Evento que se genera cuando Service Broker determina el enrutamiento de un mensaje.|  
|[Broker:Message Drop (clase de eventos)](broker-message-drop-event-class.md)|Evento que se genera cuando Service Broker no puede retener un mensaje recibido que debería haberse entregado a un servicio de esta instancia.|  
|[Broker:Remote Message Ack (clase de eventos)](broker-remote-message-ack-event-class.md)|Evento que se genera cuando Service Broker envía o recibe un reconocimiento de mensaje.|  
  
 También se proporcionan dos eventos de auditoría de seguridad para Service Broker. Para obtener más información sobre estos eventos, vea [Clase de eventos Audit Broker Login](audit-broker-login-event-class.md) y [Audit Broker Conversation (clase de eventos)](audit-broker-conversation-event-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Auditoría de seguridad (categoría de eventos)](../../analysis-services/trace-events/security-audit-event-category.md)  
  
  
