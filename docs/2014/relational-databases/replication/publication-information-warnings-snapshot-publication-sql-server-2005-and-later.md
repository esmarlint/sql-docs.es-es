---
title: Información de publicación, advertencias (publicación de instantáneas, SQL Server 2005 y versiones posterior) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rep.monitor.publicationinfo.warningsandagents.snapshot.f1
ms.assetid: 7aa2eb52-b6b7-4dd3-8483-8ef00d9f0435
caps.latest.revision: 25
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 2418d56bb4f3363c83f1e22f1b79d0907b55414f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36200513"
---
# <a name="publication-information-warnings-snapshot-publication-sql-server-2005-and-later"></a>Información de publicación, Advertencias (Publicación de instantáneas, SQL Server 2005 y posteriores)
  La pestaña **Advertencias** está disponible para los distribuidores que ejecutan [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] y versiones posteriores. La pestaña **Advertencias** permite realizar las siguientes tareas para la publicación seleccionada:  
  
-   Habilitar advertencias.  
  
-   Especificar umbrales asociados con las advertencias.  
  
-   Definir alertas asociadas con advertencias.  
  
## <a name="warnings-thresholds-and-alerts"></a>Advertencias, umbrales y alertas  
 De forma predeterminada, el Monitor de replicación muestra advertencias de suscripciones no inicializadas: se muestra el estado **Suscripción no inicializada** como una advertencia en la columna **Estado** de las páginas que incluyen información de la suscripción. En las publicaciones de instantáneas también puede especificar que la expiración inminente de la suscripción genere una advertencia si configura la opción **Advertir si una suscripción expirará dentro del umbral**. Si se alcanza o se supera el umbral especificado, se muestra el estado de la suscripción como **Con expiración en breve/Expirado** (a menos que tenga que mostrarse un problema con una prioridad superior).  
  
 Además de mostrar una advertencia en el Monitor de replicación, llegar a un umbral también puede desencadenar una alerta. Para definir alertas, haga clic en **Configurar alertas** y proporcione información en el cuadro de diálogo **Configurar alertas de replicación** .  
  
## <a name="options"></a>Opciones  
 **Habilitado**  
 Seleccione esta opción si desea habilitar una advertencia y especificar un umbral asociado.  
  
 **Advertencia**  
 Descripción de la advertencia asociada al umbral.  
  
 **Umbral**  
 Permite especificar un valor para el umbral.  
  
 **Configurar alertas**  
 Seleccione una fila en la cuadrícula **Advertencias** y haga clic en **Configurar alertas** para abrir el cuadro de diálogo **Configurar alertas de replicación** . El cuadro de diálogo permite definir una alerta que se asociará al umbral y la advertencia seleccionados.  
  
 **Descartar cambios**  
 Haga clic para descartar los cambios realizados en las advertencias y los umbrales.  
  
> [!NOTE]  
>  Hacer clic en **Descartar cambios** no afecta a las alertas definidas en el cuadro de diálogo **Configurar alertas de replicación** .  
  
 **Guardar cambios**  
 Haga clic para guardar los cambios realizados en las advertencias y los umbrales.  
  
## <a name="see-also"></a>Vea también  
 [Iniciar el Monitor de replicación](monitor/start-the-replication-monitor.md)   
 [Ver información y realizar tareas para una publicación &#40;Monitor de replicación&#41;](monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)   
 [Supervisar la replicación](monitoring-replication.md)  
  
  