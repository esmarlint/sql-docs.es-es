---
title: "Configurar o cambiar la intercalaci&#243;n del servidor | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "intercalaciones de servidores [SQL Server]"
  - "intercalaciones [SQL Server], servidor"
ms.assetid: 3242deef-6f5f-4051-a121-36b3b4da851d
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# Configurar o cambiar la intercalaci&#243;n del servidor
  La intercalación de servidor actúa como intercalación predeterminada para todas las bases de datos del sistema que se han instalado con la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], así como las bases de datos de usuario recién creadas. La intercalación de servidor se especifica durante la instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Para más información, consulte [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
## Cambiar la intercalación de servidor  
 El cambio de la intercalación predeterminada para una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] puede ser una operación compleja que incluye los siguientes pasos:  
  
-   Asegurarse de que se dispone de toda la información o scripts necesarios para volver a crear las bases de datos de usuario y todos los objetos contenidos en ellas.  
  
-   Exportar todos los datos mediante una herramienta como [bcp Utility](../../tools/bcp-utility.md). Para obtener más información, vea [Importar y exportar datos en bloque &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md).  
  
-   Quitar todas las bases de datos de usuario.  
  
-   Vuelva a generar la base de datos maestra al especificar la nueva intercalación en la propiedad SQLCOLLATION del comando **setup**. Por ejemplo:  
  
    ```  
    Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName   
    /SQLSYSADMINACCOUNTS=accounts /[ SAPWD= StrongPassword ]   
    /SQLCOLLATION=CollationName  
    ```  
  
     Para obtener más información, vea [Volver a generar bases de datos del sistema](../../relational-databases/databases/rebuild-system-databases.md).  
  
-   Crear todas las bases de datos y todos los objetos contenidos en ellas.  
  
-   Importar todos los datos.  
  
> [!NOTE]  
>  En lugar de cambiar la intercalación predeterminada de una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puede especificar una intercalación predeterminada para cada nueva base de datos que cree.  
  
## Vea también  
 [Compatibilidad con la intercalación y Unicode](../../relational-databases/collations/collation-and-unicode-support.md)   
 [Establecer o cambiar la intercalación de base de datos](../../relational-databases/collations/set-or-change-the-database-collation.md)   
 [Establecer o cambiar la intercalación de columnas](../../relational-databases/collations/set-or-change-the-column-collation.md)   
 [Volver a generar bases de datos del sistema](../../relational-databases/databases/rebuild-system-databases.md)  
  
  