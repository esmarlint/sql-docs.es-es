---
title: LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c178a308-8d99-47fc-8a49-5a480dc592f6
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 96b4deb3bf0c7d660779781f9d76aac785ca12ca
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415134"
---
# <a name="localdberrorinstancefolderpathtoolong"></a>LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|260|  
|Origen del evento|SQL Server Local Database Runtime 12.0|  
|Componente|API de Local Database Runtime|  
|Texto del mensaje|La longitud de la ruta de acceso completa de la carpeta de la instancia de Local Database es mayor que MAX_PATH. La instancia debe almacenarse en la carpeta: %%LOCALAPPDATA%%\Microsoft\Microsoft SQL Server Local DB\Instances\\< nombre de instancia\>.|  
  
## <a name="explanation"></a>Explicación  
 La ruta de acceso donde la instancia debe almacenarse es mayor que MAX_PATH.  
  
## <a name="user-action"></a>Acción del usuario  
 Cree una nueva ruta de acceso que sea menor que MAX_PATH.  
  
  
