---
title: Ejecutar scripts durante la sincronización (programación de la replicación con Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- synchronization [SQL Server replication], scripts
- scripts [SQL Server replication], synchronization and
- sp_addscriptexec
ms.assetid: b58a0877-4e43-4fab-a281-24e6022d3fb1
caps.latest.revision: 33
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d8db9946713312aad619d918b524d858f9b39415
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37298295"
---
# <a name="execute-scripts-during-synchronization-replication-transact-sql-programming"></a>Ejecutar scripts durante la sincronización (programación de la replicación con Transact-SQL)
  La replicación admite la ejecución de script a petición para suscriptores a publicaciones transaccionales y de combinación. Esta funcionalidad copia el script en el directorio de trabajo de la replicación y, a continuación, usa **sqlcmd** para aplicar el script en el suscriptor. De forma predeterminada, si hay un error al aplicar el script para una suscripción a una publicación transaccional, el Agente de distribución se detendrá. Puede especificar que un script [!INCLUDE[tsql](../../includes/tsql-md.md)] se ejecute mediante programación con los procedimientos almacenados de la replicación.  
  
### <a name="to-specify-a-script-to-run-for-all-subscribers-to-a-snapshot-transactional-or-merge-publication"></a>Para especificar que un script se ejecute para todos los suscriptores a una publicación transaccional, de instantáneas o de combinación  
  
1.  Cree y pruebe el script [!INCLUDE[tsql](../../includes/tsql-md.md)] que se ejecutará a petición.  
  
2.  Guarde el archivo de script en una ubicación en la que pueda tener acceso el Agente de instantáneas de la publicación.  
  
3.  En el publicador de la base de datos de publicaciones, ejecute [sp_addscriptexec &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql). Especifique **@publication**, el nombre del archivo de script con la ruta UNC completa creada en el paso 2 para **@scriptfile**y uno de los valores siguientes para **@skiperror**:  
  
    -   **0** - el agente dejará de ejecutar el script si se encuentra un error.  
  
    -   **1** - el agente registrará los errores y continuará ejecutando el script cuando se encuentren errores.  
  
4.  El script especificado se ejecutará en cada suscriptor cuando el agente se vuelva a ejecutar para sincronizar la suscripción.  
  
## <a name="see-also"></a>Vea también  
 [Sincronizar datos](synchronize-data.md)  
  
  
