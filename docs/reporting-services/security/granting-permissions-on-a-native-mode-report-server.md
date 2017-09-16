---
title: Conceder permisos en un servidor de informes de modo nativo | Documentos de Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- roles [Reporting Services], creating
- authorization [Reporting Services]
- server security [Reporting Services]
- role-based security [Reporting Services]
- items [Reporting Services], security
- permissions [Reporting Services], native mode
- published reports [Reporting Services], security
- reports [Reporting Services], security
- report items [Reporting Services], security
- role-based security [Reporting Services], about role-based security
- security [Reporting Services], role-based
ms.assetid: 260dc2e9-546c-4f04-9fa1-977e23c9d68c
caps.latest.revision: 60
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e587f50e041d42bb09d99fa03d4146216883fce6
ms.contentlocale: es-es
ms.lasthandoff: 08/09/2017

---
# <a name="granting-permissions-on-a-native-mode-report-server"></a>Conceder permisos en un servidor de informes en modo nativo
  SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] usa la autorización basada en roles y un subsistema de autenticación para determinar quién puede realizar operaciones y tener acceso a los elementos de un servidor de informes. La autorización basada en roles divide en roles el conjunto de acciones que puede realizar un usuario o un grupo. La autenticación se basa en la autenticación de Windows integrada o en un módulo de autenticación personalizado proporcionado por el usuario. Puede usar los roles predefinidos o los personalizados con cualquier tipo de autenticación.  
  
## <a name="using-roles-to-grant-report-server-access"></a>Usar roles para conceder acceso al servidor de informes  
 Todos los usuarios interactúan con un servidor de informes dentro del contexto de un rol que define un nivel de acceso concreto. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]incluye roles predefinidos que pueden asignar a usuarios y grupos para proporcionar acceso inmediato a un servidor de informes. **Administrador de contenido**, **Publicador**y **Explorador** son ejemplos de roles predefinidos. Cada rol define una recopilación de tareas relacionadas. Por ejemplo, un **publicador** tiene permiso para agregar informes y crear carpetas para almacenar esos informes.  
  
 Las asignaciones de roles normalmente se heredan de un nodo primario, pero se puede anular la herencia de permisos creando una nueva asignación de roles para un elemento determinado. Un usuario que sea miembro del rol **Administrador de contenido** de un informe puede pertenecer al rol **Explorador** de otro informe.  
  
 Para conceder acceso a operaciones y elementos del servidor de informes, siga estas directrices:  
  
1.  Revise los roles predefinidos para determinar si puede utilizarlos tal y como están. Si necesita ajustar las tareas o definir roles adicionales, conviene que lo haga antes de empezar a asignar usuarios a roles específicos. Para obtener más información sobre cada rol, vea [Roles predefinidos](../../reporting-services/security/role-definitions-predefined-roles.md).  
  
2.  Identifique qué usuarios y grupos requieren acceso al servidor de informes y en qué nivel. A la mayoría de los usuarios se les debería asignar el rol **Explorador** o el rol **Generador de informes** . A un pequeño número de usuarios se les debería asignar el rol **Publicador** . A el rol **Administrador de contenido**conviene asignar muy pocos usuarios.  
  
3.  Use el Administrador de informes para asignar roles de la carpeta Inicio (esta es la carpeta de nivel superior en la jerarquía de carpetas del servidor de informes) para cada usuario o grupo que requiera acceso.  
  
4.  En el nivel de sitio, en la página Configuración del sitio del Administrador de informes, cree una asignación de roles de nivel de sistema para cada usuario y grupo empleando los roles predefinidos **Usuario del sistema** y **Administrador del sistema**.  
  
5.  Cree las asignaciones de roles adicionales que necesite para carpetas, informes y otros elementos específicos. No cree un número elevado de asignaciones de roles. Si crea demasiadas, resultará difícil realizar un seguimiento de los distintos niveles de permisos para cada usuario.  
  
> [!NOTE]  
>  Si ha configurado un servidor de informes para que se ejecute en el modo integrado de SharePoint, debe establecer permisos en el sitio de SharePoint para conceder acceso a los elementos del servidor de informes. Para obtener más información, vea [Conceder permisos sobre elementos del servidor de informes en un sitio de SharePoint](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md).  
  
## <a name="who-sets-permissions"></a>Quién establece permisos  
 Inicialmente, solo los usuarios que son miembros del grupo local de administradores pueden tener acceso al servidor de informes. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] está instalado con dos asignaciones de roles predeterminadas que conceden acceso de nivel de elemento y de nivel de sistema para los miembros del grupo local de administradores. Estas asignaciones de roles integradas permiten a los administradores locales administrar los elementos del servidor de informes y conceder a los demás usuarios acceso al servidor de informes. Las asignaciones de roles integradas no se pueden eliminar. Un administrador local siempre tiene permiso para administrar totalmente una instancia del servidor de informes.  
  
 Dado que los permisos totales en un servidor de informes incluyen permisos de nivel de elemento y permisos de nivel de sistema, a un administrador local se le asignan los roles siguientes:  
  
 Antes de poder administrar una instancia del servidor de informes en un equipo local que ejecuta Windows Vista o Windows Server 2008, son necesarios algunos pasos de configuración adicionales. Para obtener más información, vea [Configurar un servidor de informes en modo nativo para la administración local &#40;SSRS&#41;](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
## <a name="how-permissions-are-stored"></a>Cómo se almacenan los permisos  
 Las asignaciones y las definiciones de roles se almacenan en la base de datos del servidor de informes. Si está utilizando varias herramientas cliente o interfaces de programación, todo el acceso estará sujeto a los permisos que se hayan definido para la instancia del servidor de informes en conjunto. Si está configurando varios servidores de informes en una implementación escalada, las asignaciones de roles que define en una instancia se almacenan en una base de datos compartida y las utilizan todas las demás instancias de la misma implementación escalada. Dado que las asignaciones de roles se almacenan junto con los elementos a los que protegen, se puede mover la base de datos a otra instancia del servidor de informes sin perder los permisos definidos.  
  
## <a name="tasks-and-tools-for-managing-permissions"></a>Tareas y herramientas para administrar permisos  
 Use las herramientas siguientes para administrar definiciones y asignaciones de roles.  
  
|Herramienta|Tareas|  
|----------|-----------|  
|Management Studio: se usa para ver, modificar, crear y eliminar definiciones de roles.|[Crear, eliminar o modificar un rol &#40; Management Studio &#41;](../../reporting-services/security/role-definitions-create-delete-or-modify.md)|  
|Administrador de informes: se usa para asignar usuarios y grupos a los roles.|[Conceder acceso de usuario a un servidor de informes &#40; El Administrador de informes &#41;](../../reporting-services/security/grant-user-access-to-a-report-server-report-manager.md)<br /><br /> [Modificar o eliminar una asignación de roles &#40; El Administrador de informes &#41;](../../reporting-services/security/role-assignments-modify-or-delete.md)|  
  
## <a name="see-also"></a>Vea también  
 [Roles predefinidos](../../reporting-services/security/role-definitions-predefined-roles.md)   
 [Conceder permisos sobre elementos de servidor de informes en un sitio de SharePoint](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)   
 [Autenticación con el servidor de informes](../../reporting-services/security/authentication-with-the-report-server.md)   
 [Crear y administrar las asignaciones de roles](../../reporting-services/security/create-and-manage-role-assignments.md)   
 [Seguridad y protección de Reporting Services](../../reporting-services/security/reporting-services-security-and-protection.md)   
 [Administración de contenido de servidor de informes &#40; Modo nativo de SSRS &#41;](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)  
  
  