---
title: Ver información y realizar tareas para una suscripción (Monitor de replicación) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], viewing information
- subscriptions [SQL Server replication], Replication Monitor tasks
- viewing subscription information
ms.assetid: 54aac83b-6f29-40d7-8901-cf059749867f
caps.latest.revision: 32
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ea071e2023c302d604c7d77f703cdaa050fc1c24
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37150666"
---
# <a name="view-information-and-perform-tasks-for-a-subscription-replication-monitor"></a>Ver información y realizar tareas para una suscripción (Monitor de replicación)
  El Monitor de replicación proporciona las siguientes pestañas que incluyen información acerca de las suscripciones:  
  
-   **Todas las suscripciones**  
  
     En esta pestaña se muestra información acerca de todas las suscripciones de la publicación seleccionada.  
  
-   **Lista de supervisión de suscripciones**  
  
     En esta pestaña se muestra información acerca de las suscripciones de todas las publicaciones disponibles en el publicador seleccionado que tienen errores, advertencias o un rendimiento insuficiente. Esta pestaña no se muestra en los distribuidores que se ejecutan en versiones anteriores de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
 Para obtener más información acerca de las opciones de cada pestaña, haga clic en la pestaña en el panel derecho y, a continuación, haga clic en **Ayuda** en la barra de menús. Para información sobre cómo iniciar el Monitor de replicación, vea [Iniciar el Monitor de replicación](start-the-replication-monitor.md).  
  
### <a name="to-view-information-and-perform-tasks-for-subscriptions-in-the-all-subscriptions-tab"></a>Para ver información y realizar tareas para suscripciones en la pestaña Todas las suscripciones  
  
1.  Expanda un grupo de publicador en el panel izquierdo, expanda un publicador y, a continuación, haga clic en una publicación.  
  
2.  Para ver información acerca de las suscripciones, haga clic en la pestaña **Todas las suscripciones** . Para ver solamente aquellas suscripciones que se encuentren en un estado determinado, por ejemplo sincronizando, seleccione una opción de la lista desplegable **Mostrar** .  
  
3.  Para ver y modificar las propiedades de una suscripción, haga clic con el botón secundario en la suscripción y, a continuación, haga clic en **Propiedades**. En esta pestaña, también puede realizar tareas y tener acceso a información más detallada. Para obtener más información, vea [Ver información y realizar tareas para los agentes asociados a una suscripción &#40;Monitor de replicación&#41;](view-information-and-perform-tasks-for-subscription-agents.md).  
  
### <a name="to-view-information-and-perform-tasks-for-subscriptions-in-the-subscription-watch-list-tab"></a>Para ver información y realizar tareas para suscripciones en la pestaña Lista de supervisión de suscripciones  
  
1.  Expanda un grupo de publicador en el panel izquierdo y, a continuación, haga clic en un publicador.  
  
2.  Para ver información acerca de las suscripciones, haga clic en la pestaña **Lista de supervisión de suscripciones** .  
  
3.  Seleccione el tipo de suscripción que quiere mostrar en la lista desplegable **Mostrar suscripciones \<TipoDeSuscripción>** . Para ver solamente aquellas suscripciones que se encuentren en un estado determinado, por ejemplo sincronizando, seleccione una opción de la lista desplegable **Mostrar** .  
  
4.  Para ver y modificar las propiedades de una suscripción, haga clic con el botón secundario en la suscripción y, a continuación, haga clic en **Propiedades**. En esta pestaña, también puede realizar tareas y tener acceso a información más detallada. Para obtener más información, vea [Ver información y realizar tareas para los agentes asociados a una suscripción &#40;Monitor de replicación&#41;](view-information-and-perform-tasks-for-subscription-agents.md).  
  
## <a name="see-also"></a>Vea también  
 [Ver y modificar las propiedades de una suscripción de inserción](../view-and-modify-push-subscription-properties.md)   
 [View and Modify Pull Subscription Properties](../view-and-modify-pull-subscription-properties.md)  (Ver y modificar las propiedades de una suscripción de extracción)  
 [Supervisar la replicación](../monitoring-replication.md)  
  
  
