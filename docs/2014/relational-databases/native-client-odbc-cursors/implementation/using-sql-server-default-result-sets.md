---
title: Uso de conjuntos de resultados predeterminados SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- ODBC cursors, default result sets
- cursors [ODBC], default result sets
- default result sets
- result sets [ODBC], default
- ODBC applications, cursors
ms.assetid: ee1db3e5-60eb-4425-8a6b-977eeced3f98
caps.latest.revision: 35
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7a4ad5f55da7e5188b4555fbbfe3c4a3fabdc3ae
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415017"
---
# <a name="using-sql-server-default-result-sets"></a>Utilizar conjuntos de resultados predeterminados de SQL Server
  Los atributos de cursor ODBC predeterminados son:  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_FORWARD_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_CONCURRENCY, SQL_CONCUR_READ_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 1, SQL_IS_INTEGER);  
```  
  
 Siempre que estos atributos se establecen en sus valores predeterminados, el [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] controlador ODBC de Native Client utiliza un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] conjunto de resultados predeterminado. Los conjuntos de resultados predeterminados se pueden utilizar para cualquier instrucción SQL admitida por [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] y son el método más eficaz de transferir un conjunto de resultados completo al cliente.  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] presentó la compatibilidad para conjuntos de resultados activos múltiples (MARS); las aplicaciones ahora pueden tener más de un conjunto de resultados predeterminado activo por conexión. MARS no está habilitado de forma predeterminada.  
  
 Antes de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], los conjuntos de resultados predeterminados no admitían varias instrucciones activas en la misma conexión. Una vez ejecutada una instrucción SQL en una conexión, el servidor no acepta comandos (excepto una solicitud para cancelar el resto del conjunto de resultados) del cliente en esa conexión hasta que se han procesado todas las filas del conjunto de resultados. Para cancelar el resto del conjunto de resultados procesado parcialmente, llame a [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) o [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) con el *fOption* parámetro establecido en SQL_CLOSE. Para terminar un conjunto de resultados procesado parcialmente y comprobar la presencia de otro conjunto de resultados, llame a [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md). Si una aplicación ODBC intenta ejecutar un comando en un identificador de conexión antes de que se ha procesado completamente el conjunto de resultados predeterminado, la llamada genera SQL_ERROR y una llamada a **SQLGetDiagRec** devuelve:  
  
```  
szSqlState: "HY000", pfNativeError: 0  
szErrorMsg: "[Microsoft][SQL Server Native Client]  
                Connection is busy with results for another hstmt."  
```  
  
## <a name="see-also"></a>Vea también  
 [Cómo se implementan los cursores](how-cursors-are-implemented.md)  
  
  
