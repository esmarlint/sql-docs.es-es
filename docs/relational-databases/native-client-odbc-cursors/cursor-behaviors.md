---
title: Comportamientos de cursor | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- version-based optimistic concurrency
- cursors [ODBC], cursor behaviors
- ODBC applications, cursors
- SQL_ATTR_CURSOR_SENSITIVITY option
- SQL_ATTR_CURSOR_SCROLLABLE option
- sensitivity behavior of cursor
- ODBC cursors, cursor behaviors
ms.assetid: 742ddcd2-232b-4aa1-9212-027df120ad35
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: fe80b8d324ff47721a0fb41a60292a867df33cab
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37424534"
---
# <a name="cursor-behaviors"></a>Comportamientos de cursor
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ODBC admite las opciones ISO para especificar el comportamiento de los cursores especificando su capacidad de desplazamiento y sensibilidad. Estos comportamientos se especifican estableciendo las opciones SQL_ATTR_CURSOR_SCROLLABLE y SQL_ATTR_CURSOR_SENSITIVITY en una llamada a [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md). El controlador ODBC de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client implementa estas opciones solicitando cursores de servidor con las siguientes características.  
  
|Valores de comportamiento de cursor|Características de cursor de servidor solicitadas|  
|------------------------------|---------------------------------------------|  
|SQL_SCROLLABLE y SQL_SENSITIVE|Cursor controlado por conjunto de claves y simultaneidad optimista basada en las versiones|  
|SQL_SCROLLABLE y SQL_INSENSITIVE|Cursor estático y simultaneidad de solo lectura|  
|SQL_SCROLLABLE y SQL_UNSPECIFIED|Cursor estático y simultaneidad de solo lectura|  
|SQL_NONSCROLLABLE y SQL_SENSITIVE|Cursor de solo avance y simultaneidad optimista basada en las versiones|  
|SQL_NONSCROLLABLE y SQL_INSENSITIVE|Conjunto de resultados predeterminado (solo avance, solo lectura)|  
|SQL_NONSCROLLABLE y SQL_UNSPECIFIED|Conjunto de resultados predeterminado (solo avance, solo lectura)|  
  
 Simultaneidad optimista basada en la versión requiere un **timestamp** columna en la tabla subyacente. Si se solicita el control de simultaneidad optimista basada en la versión en una tabla que no tiene un **timestamp** columna, el servidor usa valores simultaneidad optimista basada.  
  
## <a name="scrollability"></a>Desplazamiento  
 Si se establece SQL_ATTR_CURSOR_SCROLLABLE como SQL_SCROLLABLE, el cursor admite todos los valores diferentes para el *FetchOrientation* parámetro de [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md). Si SQL_ATTR_CURSOR_SCROLLABLE está establecido en SQL_NONSCROLLABLE, el cursor solo admite un *FetchOrientation* valor de SQL_FETCH_NEXT.  
  
## <a name="sensitivity"></a>Sensibilidad  
 Si SQL_ATTR_CURSOR_SENSITIVITY está establecido en SQL_SENSITIVE, el cursor refleja modificaciones de datos realizadas por el usuario actual o confirmadas por otros usuarios. Si SQL_ATTR_CURSOR_SENSITIVITY está establecido en SQL_INSENSITIVE, el cursor no refleja las modificaciones de datos.  
  
## <a name="see-also"></a>Vea también  
 [Uso de cursores (ODBC)](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md) [propiedades de Cursor](properties/cursor-properties.md) 
  
  
