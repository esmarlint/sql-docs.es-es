---
title: Sys.dm_tran_current_snapshot (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_tran_current_snapshot_TSQL
- dm_tran_current_snapshot
- dm_tran_current_snapshot_TSQL
- sys.dm_tran_current_snapshot
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_current_snapshot dynamic management view
ms.assetid: 7509d595-c0e1-4237-a5ac-b41ad934544c
caps.latest.revision: 35
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 6f7d32aa395ecb53ae9ccb3fd793fb661af8480b
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2018
ms.locfileid: "34467791"
---
# <a name="sysdmtrancurrentsnapshot-transact-sql"></a>sys.dm_tran_current_snapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Devuelve una tabla virtual que muestra todas las transacciones activas en el momento en que se inicia la transacción de instantáneas actual. Si la transacción actual no es una transacción de instantáneas, esta función no devuelve filas. **Sys.dm_tran_current_snapshot** es similar a **sys.dm_tran_transactions_snapshot**, salvo que **sys.dm_tran_current_snapshot** devuelve solo las transacciones activas de la transacción de instantáneas actual.  
  
> [!NOTE]  
>  Para llamar a esta desde [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], use el nombre **sys.dm_pdw_nodes_tran_current_snapshot**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sys.dm_tran_current_snapshot  
```  
  
## <a name="table-returned"></a>Tabla devuelta  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**transaction_sequence_num**|**bigint**|Número de secuencia de la transacción activa.|  
|pdw_node_id|**int**|**Se aplica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> El identificador para el nodo que se encuentra en esta distribución.|  
  
## <a name="permissions"></a>Permissions

En [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requiere `VIEW SERVER STATE` permiso.   
En [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], requiere el `VIEW DATABASE STATE` permiso en la base de datos.   

## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se utiliza un escenario de prueba con cuatro transacciones simultáneas, identificadas con un número de secuencia de transacción (XSN), que se ejecutan en una base de datos con las opciones ALLOW_SNAPSHOT_ISOLATION y READ_COMMITTED_SNAPSHOT establecidas en ON. Se están ejecutando las siguientes transacciones:  
  
-   XSN-57 es una operación de actualización con aislamiento serializable.  
  
-   XSN-58 es igual que XSN-57.  
  
-   XSN-59 es una operación de selección con aislamiento de instantáneas.  
  
-   XSN-60 es igual que XSN-59.  
  
 La siguiente consulta se ejecuta en el ámbito de XSN-59.  
  
```  
SELECT   
    transaction_sequence_num  
  FROM sys.dm_tran_current_snapshot;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
transaction_sequence_num  
------------------------  
57  
58  
```  
  
 Los resultados muestran que XSN-57 y XSN-58 estaban activas en el momento en que se inició la transacción de instantáneas XSN-59. Este resultado se conserva hasta que finaliza la transacción de instantáneas, incluso después de confirmar o revertir XSN-57 y XSN-58.  
  
 La misma consulta se ejecuta en el ámbito de XSN-60.  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
transaction_sequence_num  
------------------------  
57  
58  
59  
```  
  
 La salida de XSN-60 incluye las mismas transacciones que aparecen para XSN-59, pero también incluye XSN-59, que estaba activa cuando se inició XSN-60.  
  
## <a name="see-also"></a>Vea también  
 [Funciones y vistas de administración dinámica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Funciones y vistas de administración dinámica relacionadas con transacciones &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


