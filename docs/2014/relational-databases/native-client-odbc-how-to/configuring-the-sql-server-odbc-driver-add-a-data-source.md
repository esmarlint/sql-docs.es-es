---
title: Agregar un origen de datos (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: b4ac6f0e-8e6a-4b1a-9a7e-60e0a69b2180
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8e8d3c51595caa5a65f5ac175bdf16a4333511b5
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37432004"
---
# <a name="add-a-data-source-odbc"></a>Agregar un origen de datos (ODBC)
  Puede agregar un origen de datos con el Administrador de ODBC, mediante programación (utilizando [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)), o mediante la creación de un archivo.  
  
### <a name="to-add-a-data-source-by-using-odbc-administrator"></a>Para agregar un origen de datos mediante el Administrador ODBC  
  
1.  Desde el **Panel de Control**, acceso **herramientas administrativas** y, a continuación, **orígenes de datos (ODBC)**. De modo alternativo, puede invocar odbcad32.exe.  
  
2.  Haga clic en el **DSN de usuario**, **DSN de sistema**, o **DSN de archivo** pestaña y, a continuación, haga clic en **agregar**.  
  
3.  Haga clic en **SQL Server**y, a continuación, haga clic en **finalizar**.  
  
4.  Complete los pasos del Asistente para crear un nuevo origen de datos para SQL Server.  
  
### <a name="to-add-a-data-source-programmatically"></a>Para agregar un origen de datos mediante programación  
  
1.  Llame a [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) con el segundo parámetro establecido en ODBC_ADD_DSN u ODBC_ADD_SYS_DSN.  
  
### <a name="to-add-a-file-data-source"></a>Para agregar un origen de datos de archivo  
  
1.  Llame a [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) con un SAVEFILE = nombre_archivo parámetro en la cadena de conexión. Si la conexión se realiza correctamente, el controlador ODBC crea un origen de datos de archivo con los parámetros de conexión en la ubicación señalada por el parámetro SAVEFILE.  
  
## <a name="see-also"></a>Vea también  
 [Temas de procedimientos de configuración del controlador ODBC de SQL Server](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  
