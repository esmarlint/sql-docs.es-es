---
title: Modo asincrónico y SQLCancel | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client|ODBC
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- asynchronous operations [SQL Server Native Client]
- SQLCancel function
- SQLSetConnectAttr function
- SQL Server Native Client, asynchronous operations
- ODBC functions
- ODBC applications, asynchronous operations
- SQL Server Native Client ODBC driver, asynchronous mode
ms.assetid: f31702a2-df76-4589-ac3b-da5412c03dc2
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b81d9c0716a0bda54bdeab3c7d2b347a505e0ce2
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37409154"
---
# <a name="creating-a-driver-application---asynchronous-mode-and-sqlcancel"></a>Crear una aplicación de controlador: modo asincrónico y SQLCancel
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Algunas funciones ODBC pueden operar de forma sincrónica o asincrónica. La aplicación puede habilitar las operaciones asincrónicas para un identificador de instrucción o un identificador de conexión. Si la opción está establecida para un identificador de conexión, afectará a todos los identificadores de instrucción del identificador de conexión. La aplicación utiliza las instrucciones siguientes para habilitar o deshabilitar las operaciones asincrónicas:  
  
```  
SQLSetConnectAttr(hdbc, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
SQLSetConnectAttr(hdbc, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_OFF, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_OFF, SQL_IS_INTEGER);  
```  
  
 Cuando una aplicación llama a una función ODBC en modo sincrónico, el controlador no devuelve el control a la aplicación hasta que se notifique que el servidor ha completado el comando.  
  
 Cuando funciona en modo asincrónico, el controlador devuelve inmediatamente el control a la aplicación, incluso antes de enviar el comando al servidor. El controlador establece el código de retorno en SQL_STILL_EXECUTING. A continuación, la aplicación realiza las demás tareas.  
  
 Cuando la aplicación comprueba que el comando ha finalizado, realiza la misma llamada de función con los mismos parámetros al controlador. Si el controlador aún no ha recibido una respuesta del servidor, devolverá de nuevo SQL_STILL_EXECUTING. La aplicación debe comprobar periódicamente el comando hasta que el código de retorno sea distinto de SQL_STILL_EXECUTING. Cuando la aplicación obtiene otro código de retorno, incluso SQL_ERROR, puede determinar que el comando ha finalizado.  
  
 A veces un comando tarda mucho tiempo en completarse. Si la aplicación necesita cancelar el comando sin esperar una respuesta, puede hacerlo mediante una llamada a **SQLCancel** con la misma instrucción controlar que el comando pendiente. Esta es la única vez **SQLCancel** debe usarse. Algunos programadores utilizan **SQLCancel** cuando han procesado parte a través de un resultado de establecer y desea cancelar el resto del conjunto de resultados. [SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md) o [SQLCloseCursor](../../../relational-databases/native-client-odbc-api/sqlclosecursor.md) debe usarse para cancelar el resto de un conjunto de resultados pendiente no **SQLCancel**.  
  
## <a name="see-also"></a>Vea también  
 [Crear una aplicación de controlador ODBC de SQL Server Native Client](../../../relational-databases/native-client/odbc/creating-a-driver-application.md)  
  
  
