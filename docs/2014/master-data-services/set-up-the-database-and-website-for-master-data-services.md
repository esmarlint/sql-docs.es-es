---
title: Configurar la base de datos y el sitio Web de Master Data Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.general.f1
ms.assetid: d50863e7-50d9-4ab8-aabb-fd68e2d132a1
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fe3be8de50ad6752f5edb4f1ea888c172338aaa2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37322375"
---
# <a name="set-up-the-database-and-website-for-master-data-services"></a>Configurar la base de datos y el sitio web para Master Data Services
  Use la [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] para configurar la base de datos y el sitio Web para [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS)  
  
 Para configurar la base de datos y el sitio web, realice las tareas siguientes.  
  
1.  Crear una base de datos mediante el **configuración de la base de datos** página [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].  
  
     Para obtener información, consulte [página de configuración de la base de datos &#40;Administrador de configuración de Master Data Services&#41; ](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md) y [Asistente para crear base de datos &#40;Administrador de configuración de Master Data Services&#41; ](../../2014/master-data-services/create-database-wizard-master-data-services-configuration-manager.md).  
  
2.  Crear un nuevo sitio Web, seleccione el sitio Web predeterminado o seleccione otro sitio Web existente, mediante el **configuración Web** página [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]. Luego, asocie la base de datos de MDS a la aplicación web que seleccione o cree.  
  
     Para obtener información, consulte [página configuración Web &#40;Administrador de configuración de Master Data Services&#41; ](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) y [cuadro de diálogo Crear sitio Web &#40;Administrador de configuración de Master Data Services&#41; ](../../2014/master-data-services/create-website-dialog-box-master-data-services-configuration-manager.md).  
  
3.  (Opcional) Habilitar la integración con Data Quality Services mediante el **configuración Web** página [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].  
  
     Para obtener más información, consulte [página configuración Web &#40;Administrador de configuración de Master Data Services&#41; ](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) y [habilitar la integración de Data Quality Services con Master Data Services](install-windows/enable-data-quality-services-integration-with-master-data-services.md).  
  
 También puede usar [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] para especificar la configuración para las aplicaciones web y servicios asociados a la base de datos MDS. Por ejemplo, puede especificar la frecuencia con la que se cargan los datos o con la que se envían correos electrónico de validación. Para obtener más información, vea [Configuración del sistema &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).  
  
## <a name="see-also"></a>Vea también  
 [Base de datos de Master Data Services](../../2014/master-data-services/master-data-services-database.md)   
 [Aplicación web Master Data Manager](../../2014/master-data-services/master-data-manager-web-application.md)  
  
  
