---
title: Seguridad de objetos de base de datos (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- database [Master Data Services], object security
- security [Master Data Services], database objects
ms.assetid: dd5ba503-7607-45d9-ad0d-909faaade179
caps.latest.revision: 10
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 42f181035f2fffff06540d060ed4a179ab88f806
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2018
ms.locfileid: "35329109"
---
# <a name="database-object-security-master-data-services"></a>Seguridad de objetos de base de datos (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  En la base de datos [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , los datos están almacenados en varias tablas de base de datos y se ven en las vistas. La información que pueda haber protegido en la aplicación web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] está visible para los usuarios con acceso a la base de datos [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
 En concreto, la información del sueldo de los empleados podría estar contenida en un modelo Empleado, o la información financiera de la compañía podría estar en un modelo Cuenta. Puede denegar el acceso a un usuario a estos modelos en la interfaz de usuario de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , pero los usuarios con acceso a la base de datos pueden ver estos datos.  
  
 Puede conceder permisos a los objetos de base de datos para hacer que datos concretos estén disponibles para los usuarios. Para obtener más información sobre cómo conceder permisos, consulte [GRANT &#40;permisos de objeto de Transact-SQL&#41;](../t-sql/statements/grant-object-permissions-transact-sql.md). Para obtener más información acerca de cómo proteger un servidor SQL Server, vea [Securing SQL Server](../relational-databases/security/securing-sql-server.md).  
  
 Las siguientes tareas necesitan acceso a la base de datos de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] :  
  
-   [Almacenar datos de forma provisional](#Staging)  
  
-   [Validar datos según las reglas de negocios](#rules)  
  
-   [Eliminar versiones](#Versions)  
  
-   [Aplicación inmediata de permisos de los miembros de la jerarquía](#Hierarchy)  
  
-   [Configuración del sistema](#SysSettings)  
  
##  <a name="Staging"></a> Almacenar datos de forma provisional  
 En la tabla siguiente, cada elemento protegible tiene "name" como parte del nombre. Indica el nombre de la tabla de ensayo que se especificó cuando se creó una entidad. Para obtener más información, consulte [Información general: importación de datos de tablas &#40;Master Data Services&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)  
  
|Acción|Elementos protegibles|Permisos|  
|------------|----------------|-----------------|  
|Crear, actualizar y eliminar miembros hoja y sus atributos.|stg.name_Leaf|Obligatorio: INSERT<br /><br /> Opcional: SELECT y UPDATE|  
|Cargar datos de la tabla de ensayo Leaf en las tablas adecuadas de la base de datos de MDS.|stg.udp_name_Leaf|Ejecute|  
|Crear, actualizar y eliminar miembros consolidados y sus atributos.|stg.name_Consolidated|Obligatorio: INSERT<br /><br /> Opcional: SELECT y UPDATE|  
|Cargar los datos de la tabla de ensayo Consolidated en las tablas adecuadas de la base de datos de MDS.|stg.udp_name_Consolidated|Ejecute|  
|Mover miembros en una jerarquía explícita.|stg.name_Relationship|Obligatorio: INSERT<br /><br /> Opcional: SELECT y UPDATE|  
|Cargar los datos de la tabla de ensayo Relationship en las tablas adecuadas de la base de datos de MDS.|stg.udp_name_Relationship|Ejecute|  
|Ver los errores producidos cuando se insertaban datos de las tablas de ensayo en tablas de la base de datos de MDS.|stg.udp_name_Relationship|SELECT|  
  
 Para obtener más información, consulte [Información general: importación de datos de tablas &#40;Master Data Services&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md).  
  
##  <a name="rules"></a> Validar datos según las reglas de negocios  
  
|Acción|Elemento protegible|Permisos|  
|------------|---------------|-----------------|  
|Validar una versión de datos según las reglas de negocios|mdm.udpValidateModel|Ejecute|  
  
 Para obtener más información, consulte [Procedimiento almacenado de validación &#40;Master Data Services&#41;](../master-data-services/validation-stored-procedure-master-data-services.md).  
  
##  <a name="Versions"></a> Eliminar versiones  
  
|Acción|Elementos protegibles|Permisos|  
|------------|----------------|-----------------|  
|Determinar el identificador de la versión que desea eliminar|mdm.viw_SYSTEM_SCHEMA_VERSION|SELECT|  
|Eliminar una versión de un modelo|mdm.udpVersionDelete|Ejecute|  
  
 Para obtener más información, consulte [Eliminar una versión &#40;Master Data Services&#41;](../master-data-services/delete-a-version-master-data-services.md).  
  
##  <a name="Hierarchy"></a> Aplicación inmediata de permisos de los miembros de la jerarquía  
  
|Acción|Elementos protegibles|Permisos|  
|------------|----------------|-----------------|  
|Aplicar los permisos de los miembros inmediatamente|mdm.udpSecurityMemberProcessRebuildModel|Ejecute|  
  
 Para obtener más información, consulte [Aplicar inmediatamente los permisos de los miembros &#40;Master Data Services&#41;](../master-data-services/immediately-apply-member-permissions-master-data-services.md).  
  
##  <a name="SysSettings"></a> Configuración del sistema  
 Hay opciones del sistema que puede configurar para controlar el comportamiento en [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Puede ajustar estos valores en [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] o, si tiene el acceso ACTUALIZAR, puede ajustarlos directamente en la tabla de base de datos mdm.tblSystemSetting. Para obtener más información, vea [Configuración del sistema &#40;Master Data Services&#41;](../master-data-services/system-settings-master-data-services.md).  
  
## <a name="see-also"></a>Ver también  
 [Seguridad &#40;Master Data Services&#41;](../master-data-services/security-master-data-services.md)  
  
  
