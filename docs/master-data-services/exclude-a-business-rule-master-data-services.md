---
title: Excluir una regla de negocios (Master Data Services) | Documentos de Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules [Master Data Services], excluding
ms.assetid: bdbc9df0-23f7-40b9-8aba-4445c1482580
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 264f58554df70d5531cecdaea9bbc94606086e9a
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="exclude-a-business-rule-master-data-services"></a>Excluir una regla de negocios (Master Data Services)
  En [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], excluya una regla de negocios cuando no desee eliminar la regla permanentemente, pero no desee validar los datos con ella.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para realizar este procedimiento:  
  
-   Debe disponer de permiso para tener acceso al área funcional de **Administración del sistema** .  
  
-   Debe ser administrador de modelo. Para obtener más información, vea [Administradores &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-exclude-a-business-rule"></a>Para excluir una regla de negocios  
  
1.  En [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], haga clic en **Administración del sistema**.  
  
2.  En la barra de menús, seleccione **Administrar** y haga clic en **Reglas de negocios**.  
  
3.  En la página **Reglas de negocios** , en la lista desplegable **Modelo** , seleccione un modelo.  
  
4.  En la lista desplegable **Entidad** , seleccione una entidad.  
  
5.  En la lista desplegable **Member Types** (Tipos de miembros), seleccione un tipo de miembro.  
  
6.  En la cuadrícula, seleccione la fila de la regla de negocios que desea excluir y haga clic en **Editar**.  
  
7.  Active la casilla **Excluida** .  
  
8.  Haga clic en **Guardar**.  
  
9. Haga clic en **Publish All**(Publicar todo).  
  
10. En el cuadro de diálogo de confirmación, haga clic en **Aceptar**. El valor de la columna **Business Rule Status** (Estado de regla de negocios) es **Excluida** y la columna **Excluida** es **Sí**.  
  
## <a name="see-also"></a>Vea también  
 [Eliminar una regla de negocios &#40; Master Data Services &#41;](../master-data-services/delete-a-business-rule-master-data-services.md)   
 [Crear y publicar una regla de negocios &#40; Master Data Services &#41;](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)   
 [Las reglas de negocios &#40; Master Data Services &#41;](../master-data-services/business-rules-master-data-services.md)  
  
  