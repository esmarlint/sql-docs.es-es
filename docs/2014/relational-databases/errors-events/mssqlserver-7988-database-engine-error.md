---
title: MSSQLSERVER_7988 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 7988 (Database Engine error)
ms.assetid: 29b967b8-de30-4618-99a8-8b1155e69026
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c9f8d0effc6bc7345553ac67f33a1de2588af441
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420314"
---
# <a name="mssqlserver7988"></a>MSSQLSERVER_7988
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|7988|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|DBCC2_PRE_CHECKS_CHAIN_LOOP_DETECTED|  
|Texto del mensaje|Comprobaciones previas de tabla del sistema: Id. de objeto O_ID. Se detectó un bucle en una cadena de datos en P_ID. Instrucción de comprobación terminada debido a un error irreparable.|  
  
## <a name="explanation"></a>Explicación  
 La primera fase de DBCC CHECKDB es hacer comprobaciones básicas en las páginas de datos de las tablas críticas del sistema. Si se encuentra algún error, no puede repararse; por tanto, DBCC CHECKDB termina inmediatamente. Se ha detectado un bucle de vinculación de páginas en la página *P_ID*. Un bucle de vinculación de páginas se produce cuando los punteros de página siguiente de una página vuelven finalmente a la página.  
  
## <a name="user-action"></a>Acción del usuario  
  
### <a name="look-for-hardware-failure"></a>Busque un error de hardware  
 Ejecute un diagnóstico de hardware y corrija cualquier problema. Examine también los registros del sistema y de aplicación de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows así como el registro de errores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para ver si el error se produjo como resultado de un error de hardware. Arregle cualquier problema relacionado con el hardware que encuentre en estos registros.  
  
 Si sigue teniendo problemas de datos dañados, intente intercambiar diferentes componentes de hardware para aislar el problema. Asegúrese de que el sistema no tiene habilitada la memoria caché de escritura en el controlador de disco. Si cree que el problema se debe a la caché de escritura, póngase en contacto con su proveedor de hardware.  
  
 Finalmente, puede resultarle útil cambiar a un nuevo sistema de hardware. Este cambio puede incluir volver a formatear las unidades de disco y volver a instalar el sistema operativo.  
  
### <a name="restore-from-backup"></a>Restaure mediante la copia de seguridad  
 Si el problema no está relacionado con el hardware y tiene una copia de seguridad limpia disponible, úsela para restaurar la base de datos.  
  
### <a name="run-dbcc-checkdb"></a>Ejecute DBCC CHECKDB  
 No aplicable. Este error no puede repararse automáticamente. Si no puede restaurar la base de datos a partir de una copia de seguridad, póngase en contacto con el Servicio de atención al cliente y soporte técnico (CSS) de [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
  
