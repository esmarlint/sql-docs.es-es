---
title: Simultaneidad de cursor (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- concurrency [ODBC]
- cursors [ODBC], concurrency
- ODBC cursors, concurrency
ms.assetid: 68228ece-cbf1-4f19-bfdc-053884c1af48
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 9bc43656728586f30a2fa07e3ab1903ec00dc6d3
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423904"
---
# <a name="cursor-concurrency-odbc"></a>Simultaneidad de cursor (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Las opciones de simultaneidad establecidas por la aplicación afectan a las operaciones del cursor, como los tipos de cursor. Opciones de simultaneidad se establecen mediante la opción SQL_ATTR_CONCURRENCY de [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md). Los tipos de simultaneidad son:  
  
-   Solo lectura (SQL_CONCUR_READONLY)  
  
-   Valores (SQL_CONCUR_VALUES)  
  
-   Versión de fila (SQL_CONCUR_ROWVER)  
  
-   Bloqueo (SQL_CONCUR_LOCK)  
  
## <a name="see-also"></a>Vea también  
 [Propiedades de cursor](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
