---
title: "Configurar el almacenamiento de datos del punto de control de la utilidad (utilidad de SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# Configurar el almacenamiento de datos del punto de control de la utilidad (utilidad de SQL Server)
  Los datos que recopilan las instancias administradas de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se almacenan en el almacén de administración de datos de la utilidad (UMDW); el nombre del archivo de este almacén es sysutility_mdw.  
  
 Puede configurar el período para la retención de datos en el almacén de administración de datos de utilidad. Para obtener más información, vea [Administración de la utilidad &#40;Utilidad de SQL Server&#41;](../Topic/Utility%20Administration%20\(SQL%20Server%20Utility\).md).  
  
 Los siguientes valores de configuración no se pueden establecer en esta versión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Nombre de UMDW: Sysutility_mdw.  
  
-   Frecuencia de la carga del conjunto de recopilación: cada 15 minutos.  
  
 El directorio del UMDW se puede configurar: \<unidad del sistema>:\Archivos de programa\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\, donde \<unidad del sistema> normalmente es la unidad C:\. El archivo de registro, Sysutility_mdw_\<GUID>_LOG, se encuentra en el mismo directorio.  
  
> [!NOTE]  
>  La ubicación del archivo del almacén de administración de datos de utilidad se puede cambiar mediante detach/attach o ALTER DATABASE. Recomendamos el uso de ALTER DATABASE. Para obtener más información, vea [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).  
  
## Vea también  
 [Características y tareas de la utilidad de SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  