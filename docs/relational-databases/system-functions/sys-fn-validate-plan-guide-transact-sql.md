---
title: Sys.fn_validate_plan_guide (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.fn_validate_plan_guide
- sys.fn_validate_plan_guide_TSQL
- fn_validate_plan_guide
- fn_validate_plan_guide_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_validate_plan_guide function
- sys.fn_validate_plan_guide function
ms.assetid: 3af8b47a-936d-4411-91d1-d2d16dda5623
caps.latest.revision: 19
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 6b941fabfd4ebbd3ca41375622bf682f12b0fc26
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236206"
---
# <a name="sysfnvalidateplanguide-transact-sql"></a>sys.fn_validate_plan_guide (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Comprueba la validez de la guía de plan especificada. La función sys.fn_validate_plan_guide devuelve el primer mensaje de error encontrado cuando la guía de plan se aplica a su consulta. Se devuelve un conjunto de filas vacío cuando la guía de plan es válida. Las guías de plan pueden volverse no válidas una vez realizados los cambios en el diseño físico de la base de datos. Por ejemplo, si una guía de plan especifica un índice determinado y se quita después dicho índice, la consulta ya no podrá utilizar la guía de plan.  
  
 Al validar una guía de plan, es posible determinar si el optimizador puede utilizar la guía sin ninguna modificación. En función de los resultados de la función, puede decidir quitar la guía de plan y reajustar la consulta o modificar el diseño de la base de datos, por ejemplo, recreando el índice especificado en la guía de plan.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
sys.fn_validate_plan_guide ( plan_guide_id )  
```  
  
## <a name="arguments"></a>Argumentos  
 *plan_guide_id*  
 Es el identificador de la Guía de plan como se notifica en el [sys.plan_guides](../../relational-databases/system-catalog-views/sys-plan-guides-transact-sql.md) vista de catálogo. *plan_guide_id* es **int** no tiene ningún valor predeterminado.  
  
## <a name="table-returned"></a>Tabla devuelta  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|msgnum|**int**|Id. del mensaje de error.|  
|severity|**tinyint**|Nivel de gravedad del mensaje, entre 1 y 25.|  
|state|**smallint**|Número de estado del error que indica el punto dentro del código donde se produjo el error.|  
|message|**nvarchar(2048)**|Texto del mensaje del error.|  
  
## <a name="permissions"></a>Permissions  
 Las guías de plan de ámbito OBJECT requieren el permiso VIEW DEFINITION o ALTER en el objeto al que se hace referencia y permisos para compilar la consulta o lote proporcionado en la guía de plan. Por ejemplo, si un lote contiene las instrucciones SELECT, se requieren los permisos SELECT en los objetos a los que se hace referencia.  
  
 Las guías de plan de ámbito SQL o TEMPLATE requieren el permiso ALTER en la base de datos y permisos para compilar la consulta o lote proporcionado en la guía de plan. Por ejemplo, si un lote contiene las instrucciones SELECT, se requieren los permisos SELECT en los objetos a los que se hace referencia.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-validating-all-plan-guides-in-a-database"></a>A. Validar todas las guías de plan en una base de datos  
 El ejemplo siguiente comprueba la validez de todas las guías de plan en la base de datos actual. Si se devuelve un conjunto de resultados vacío, todas las guías de plan son válidas.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT plan_guide_id, msgnum, severity, state, message  
FROM sys.plan_guides  
CROSS APPLY fn_validate_plan_guide(plan_guide_id);  
GO  
```  
  
### <a name="b-testing-plan-guide-validation-before-implementing-a-change-to-the-database"></a>B. Validar la guía de plan de prueba antes de implementar un cambio en la base de datos  
 El ejemplo siguiente utiliza una transacción explícita para quitar un índice. El `sys.fn_validate_plan_guide` se ejecuta la función para determinar si esta acción invalidará cualquier guía de plan en la base de datos. En función de los resultados de la función, se confirma la instrucción `DROP INDEX` o se revierte la transacción y no se quita el índice.  
  
```sql  
USE AdventureWorks2012;  
GO  
BEGIN TRANSACTION;  
DROP INDEX IX_SalesOrderHeader_CustomerID ON Sales.SalesOrderHeader;  
-- Check for invalid plan guides.  
IF EXISTS (SELECT plan_guide_id, msgnum, severity, state, message  
           FROM sys.plan_guides  
           CROSS APPLY sys.fn_validate_plan_guide(plan_guide_id))  
    ROLLBACK TRANSACTION;  
ELSE  
    COMMIT TRANSACTION;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [Guías de plan](../../relational-databases/performance/plan-guides.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
  
