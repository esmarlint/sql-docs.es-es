---
title: La autenticación de modo de SharePoint de Reporting Services | Microsoft Docs
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
- Upgrade SharePoint Mode [Reporting Services]
- SharePoint integration
- SharePoint Mode
ms.assetid: 2c19794a-dd55-4fe5-b901-6dd93e9f6beb
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 704d104b8834675f7511c952db7fafb9fcccafd3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37247815"
---
# <a name="reporting-services-sharepoint-mode-authentication"></a>Autenticación del modo de SharePoint de Reporting Services
  Use la página **Autenticación del modo de SharePoint de Reporting Services** del Asistente para la instalación de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para especificar las credenciales de la cuenta de servicio que se usa en la instalación actual de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Las credenciales se usarán para crear un nuevo grupo de aplicaciones de SharePoint. Además, se creará una nueva aplicación de servicio de SharePoint para [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . El nombre de la aplicación de servicio contendrá el nombre de la instancia anterior de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
## <a name="options"></a>Opciones  
  
-   La opción **Nombre de la cuenta del grupo de aplicaciones SSRS** es de solo lectura. El valor se rellena automáticamente con el valor actual de la instalación de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] existente que va a actualizar.  
  
-   La opción **Contraseña de la cuenta del grupo de aplicaciones SSRS** estará deshabilitada si la cuenta del grupo de aplicaciones no requiere una contraseña. Por ejemplo, “NT Authority\NetworkSerivce”. Si la cuenta del grupo de aplicaciones requiere una contraseña, no podrá continuar con la actualización hasta que escriba la contraseña correcta.  
  
 Para obtener más información, consulte [actualizar y migrar Reporting Services](http://go.microsoft.com/fwlink/?LinkID=245628) (http://go.microsoft.com/fwlink/?LinkID=245628).  
  
## <a name="see-also"></a>Vea también  
 [Actualizar y migrar Reporting Services](http://go.microsoft.com/fwlink/?LinkID=245628)  
  
  
