---
title: Valores de HOST_NAME | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.newsubwizard.hostnamevalue.f1
ms.assetid: 21548f08-2910-4a55-baac-b911ba9afaf1
caps.latest.revision: 20
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 86d1b5ed846a55cacd3b7c4959d5eced6985bb72
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37352057"
---
# <a name="hostname-values"></a>Valores de HOST_NAME
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Las publicaciones de combinación con filtros con parámetros utilizan la función SUSER_SNAME() o la función HOST_NAME() para filtrar datos. La función se especifica en el Asistente para nueva publicación o en el cuadro de diálogo **Propiedades de la publicación** .  
  
 De forma predeterminada, la función HOST_NAME() devuelve el nombre del equipo que se conecta al publicador. Cuando se utilizan filtros con parámetros, es normal reemplazar este valor suministrando otro en esta página del asistente. A continuación, la función HOST_NAME() devuelve el valor que se ha especificado en vez del nombre del equipo. Para obtener más información, vea la sección sobre cómo reemplazar el valor de HOST_NAME() de [Filtros de fila con parámetros](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
> [!NOTE]  
>  Si reemplaza HOST_NAME(), todas las llamadas a la función HOST_NAME() devolverán el valor especificado. Asegúrese de que otras aplicaciones no dependen de HOST_NAME() al devolver el nombre del equipo.  
  
## <a name="options"></a>Opciones  
 **Propiedades de la suscripción**  
 Escriba un valor para cada suscriptor en la columna **Valor de HOST_NAME** o acepte el valor predeterminado, que es el nombre del equipo suscriptor.  
  
## <a name="see-also"></a>Ver también  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)  (Ver y modificar las propiedades de una suscripción de extracción)  
 [Ver y modificar las propiedades de una suscripción de inserción](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [HOST_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/host-name-transact-sql.md)   
 [Suscribirse a publicaciones](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
