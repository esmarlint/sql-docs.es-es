---
title: Componentes de controlador OLE DB para SQL Server | Documentos de Microsoft
description: Componentes de controlador OLE DB para SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], components
- components [OLE DB Driver for SQL Server]
- MSOLEDBSQL, about OLE DB Driver for SQL Server
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 78b72796de5aa4ac2fb9bc0793f98365b7d8281e
ms.sourcegitcommit: 354ed9c8fac7014adb0d752518a91d8c86cdce81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/14/2018
ms.locfileid: "35611690"
---
# <a name="components-of-ole-db-driver-for-sql-server"></a>Componentes de controlador OLE DB para SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Controlador de OLE DB para SQL Server contiene los siguientes componentes:  

|Componente|Descripción|  
|---------------|-----------------|  
|msoledbsql.dll|El archivo de biblioteca de vínculos dinámicos (DLL) que contiene todo el controlador OLE DB para la funcionalidad de SQL Server.|  
|msoledbsqlr.rll|El archivo de recursos asociado para el controlador OLE DB para la biblioteca de SQL Server.|   
|msoledbsql.h|El controlador OLE DB para el archivo de encabezado de SQL Server que contiene todas las definiciones nuevas necesarias para poder usar el controlador OLE DB para SQL Server. Este archivo de encabezado reemplaza el archivo de encabezado sqloledb.h.<br /><br /> Nota: Puede hacer referencia a msoledbsql.h y sqloledb.h en el mismo programa siempre que sqloledb.h se defina en primer lugar.|  
|msoledbsql.lib|El archivo de biblioteca necesario para directamente llamada la [OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) función a la que pertenece el controlador OLE DB para SQL Server.<br /><br /> Nota: Si se hace referencia al archivo msoledbsql.lib en el código de programación, tiene que asegurarse de que el archivo msoledbsql.dll está en la ruta del sistema y en la ruta de acceso de sistema de los usuarios que utilizan la aplicación.|  

## <a name="see-also"></a>Vea también  
 [Compilación de aplicaciones con el controlador OLE DB para SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
