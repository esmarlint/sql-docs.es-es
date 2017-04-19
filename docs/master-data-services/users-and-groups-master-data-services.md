---
title: "Usuarios y grupos (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "usuarios [Master Data Services]"
  - "grupos [Master Data Services]"
  - "usuarios [Master Data Services], acerca de los usuarios"
  - "grupos [Master Data Services], acerca de los grupos"
ms.assetid: ed08dd2d-248e-4b68-91d4-e9961cb50eed
caps.latest.revision: 8
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 8
---
# Usuarios y grupos (Master Data Services)
  Para tener acceso a la aplicación web de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] un usuario debe tener una cuenta de dominio de Windows o una cuenta en el equipo servidor donde se instale [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Para conceder acceso a [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] puede:  
  
-   Agregar la cuenta de usuario a un dominio o grupo local y, a continuación, agregar el grupo a la lista de grupos de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
-   Agregar la cuenta de usuario a la lista de usuarios de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
    > [!NOTE]  
    >  Cuando un usuario pertenece a un grupo que tiene acceso a [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], el nombre del usuario se agrega de forma automática a la lista de usuarios la primera vez que el usuario obtiene acceso a [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] o al [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] MDS.  
  
 Para realizar una acción en el área de funcionalidad del **Explorador** de la IU, se debe asignar al grupo o usuario acceso al área funcional del **Explorador** y permiso a los objetos del modelo.  
  
 Si un usuario o grupo necesita tener acceso a otras áreas funcionales, se debe asignar al usuario o grupo acceso al área funcional específica.  
  
## Práctica recomendada  
 Para simplificar la administración, cree grupos y asigne a cada uno permiso a las áreas funcionales y a los objetos de modelo. Puede agregar usuarios a los grupos y quitarlos a continuación sin tener acceso a la interfaz de usuario de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .  
  
 No asigne ningún permiso adicional a ningún usuario individual y no incluya usuarios en varios grupos que tengan acceso a [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]. Además, no use los permisos de miembros de la jerarquía a menos que desee que un grupo tenga limitado el acceso a miembros concretos.  
  
## Vea también  
 [Agregar un usuario &#40;Master Data Services&#41;](../master-data-services/add-a-user-master-data-services.md)   
 [Agregar un grupo &#40;Master Data Services&#41;](../master-data-services/add-a-group-master-data-services.md)   
 [Eliminar usuarios o grupos &#40;Master Data Services&#41;](../master-data-services/delete-users-or-groups-master-data-services.md)   
 [Probar los permisos de un usuario &#40;Master Data Services&#41;](../master-data-services/test-a-user-s-permissions-master-data-services.md)  
  
  