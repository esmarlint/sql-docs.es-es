---
title: SERVERPROPERTY devuelve un resultado correcto para la propiedad LCID en SQL Server 2005 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SERVERPROPERTY function
ms.assetid: 833a2fc9-b480-4697-aa7b-9677e78ee0b4
caps.latest.revision: 17
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c9a92dd33ee5693d78b5f55f3bfcbc6edb4a0d8b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37157706"
---
# <a name="serverproperty-returns-correct-result-for-lcid-property-in-sql-server-2005"></a>SERVERPROPERTY devuelve el resultado correcto para la propiedad LCID en SQL Server 2005
  Cuando SERVERPROPERTY('LCID') se ejecuta en servidores de intercalación binaria, la función devuelve un valor de identificador regional de Windows (LCID), independientemente de la intercalación actual del servidor.  
  
> [!NOTE]  
>  Para el caso de los archivos por lotes y archivos de seguimiento que contengan referencias a SERVERPROPERTY ('LCID') y que se ejecuten en otras instancias de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], el Asesor de actualizaciones detectará este cambio de comportamiento solo si el resto de instancias tienen la misma intercalación que la instancia actual de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="corrective-action"></a>Acción correctora  
 Modifique las aplicaciones de forma que SERVERPROPERTY('LCID') devuelva el LCID de Windows que corresponda con la intercalación del servidor.  
  
## <a name="see-also"></a>Vea también  
 [Problemas de actualización de motor de base de datos](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Asesor de actualizaciones de SQL Server 2014 &#91;nuevo&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
