---
title: "Procedimiento almacenado de validaci&#243;n (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 332d3c86-4440-4f12-a6cb-ffbfbccde52c
caps.latest.revision: 8
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 8
---
# Procedimiento almacenado de validaci&#243;n (Master Data Services)
  En [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], valide una versión para aplicar las reglas de negocios a todos los miembros de la versión del modelo.  
  
 En este tema se explica cómo usar el procedimiento almacenado **mdm.udpValidateModel** para validar datos. Si es administrador de la aplicación web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , puede realizar la validación en la interfaz de usuario en su lugar. Para obtener más información, consulte [Validar una versión con las reglas de negocios &#40;Master Data Services&#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md).  
  
> [!NOTE]  
>  Si invoca la validación antes de que se complete el proceso de almacenamiento provisional, no se validarán los miembros que no se hayan terminado de almacenar.  
  
## Ejemplo  
  
```  
DECLARE @ModelName nVarchar(50) = 'Customer'   
DECLARE @Model_id int   
DECLARE @UserName nvarchar(50)= 'DOMAIN\user_name'   
DECLARE @User_ID int   
DECLARE @Version_ID int   
  
SET @User_ID = (SELECT ID    
                 FROM mdm.tblUser u   
                 WHERE u.UserName = @UserName)   
SET @Model_ID = (SELECT Top 1 Model_ID   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_Name = @ModelName)   
SET @Version_ID = (SELECT MAX(ID)   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_ID = @Model_ID)  
  
EXECUTE mdm.udpValidateModel @User_ID, @Model_ID, @Version_ID, 1  
  
```  
  
## Parámetros  
 Los parámetros de este procedimiento son los siguientes:  
  
|Parámetro|Description|  
|---------------|-----------------|  
|UserID|Id. de usuario.|  
|Model_ID|Identificador del modelo.|  
|Version_ID|Identificador de versión.|  
  
## Vea también  
 [Información general: importación de datos de tablas &#40;Master Data Services&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)   
 [Validar una versión con las reglas de negocios &#40;Master Data Services&#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
  