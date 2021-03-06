---
title: Sys.dm_exec_procedure_stats (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/10/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_procedure_stats_TSQL
- dm_exec_procedure_stats_TSQL
- dm_exec_procedure_stats
- sys.dm_exec_procedure_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_procedure_stats dynamic management view
ms.assetid: ab8ddde8-1cea-4b41-a7e4-697e6ddd785a
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 0a2aadbc591400d899791759d25e8174104fd1d1
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2018
ms.locfileid: "34466841"
---
# <a name="sysdmexecprocedurestats-transact-sql"></a>sys.dm_exec_procedure_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Devuelve estadísticas de rendimiento de agregado para los procedimientos almacenados en memoria caché. La vista devuelve una fila por cada procedimiento almacenado en memoria caché y la vigencia de la fila corresponde al tiempo que el procedimiento almacenado permanece en memoria caché. Cuando se quita un procedimiento almacenado de la memoria caché, la fila correspondiente se elimina de esta vista. En ese momento, se provoca un evento de seguimiento de SQL de estadísticas de rendimiento similar a **sys.dm_exec_query_stats**.  
  
 En [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], las vistas de administración dinámica no pueden exponer información que impactaría a la contención de la base de datos ni acerca de otras bases de datos a las que el usuario tenga acceso. Para evitar exponer esta información, cada fila que contiene datos que no pertenecen al inquilino conectado se filtra.  
  
> [!NOTE]
> Una consulta inicial de **sys.dm_exec_procedure_stats** podría producir resultados imprecisos si hay una carga de trabajo ejecutándose actualmente en el servidor. Pueden determinarse resultados más precisos volviendo a ejecutar la consulta.  
  
> [!NOTE]
> Para llamar a esta desde [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], use el nombre **sys.dm_pdw_nodes_exec_procedure_stats**.  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Identificador de base de datos en el que el procedimiento almacenado reside.|  
|**object_id**|**int**|Número de identificación de objeto del procedimiento almacenado.|  
|**Tipo**|**char(2)**|Tipo del objeto:<br /><br /> P = Procedimiento almacenado de SQL<br /><br /> PC = Procedimiento almacenado de ensamblado (CLR)<br /><br /> X = Procedimiento almacenado extendido|  
|**type_desc**|**nvarchar(60)**|Descripción del tipo de objeto:<br /><br /> SQL_STORED_PROCEDURE<br /><br /> CLR_STORED_PROCEDURE<br /><br /> EXTENDED_STORED_PROCEDURE|  
|**sql_handle**|**varbinary(64)**|Esto puede usarse para poner en correlación con las consultas en **sys.dm_exec_query_stats** que se ejecutaron desde dentro de este procedimiento almacenado.|  
|**plan_handle**|**varbinary(64)**|Identificador del plan en memoria. Este identificador es transitorio y permanece constante solo mientras el plan permanece en la memoria caché. Este valor se puede usar con el **sys.dm_exec_cached_plans** vista de administración dinámica.<br /><br /> Será siempre 0x000 cuando un procedimiento almacenado nativo consulte una tabla optimizada para memoria.|  
|**cached_time**|**datetime**|Momento en el que el procedimiento almacenado se agregó a la caché.|  
|**last_execution_time**|**datetime**|Hora en que se ejecutó el procedimiento almacenado por última vez.|  
|**execution_count**|**bigint**|El número de veces que se ha ejecutado el procedimiento almacenado desde que se compiló por última vez.|  
|**total_worker_time**|**bigint**|La cantidad total de tiempo de CPU, en microsegundos, consumido por las ejecuciones de este procedimiento almacenado desde que se compiló.<br /><br /> Para los procedimientos almacenados compilados de forma nativa, **total_worker_time** puede no ser exacto si varias ejecuciones tardan menos de 1 milisegundo.|  
|**last_worker_time**|**bigint**|Tiempo de CPU, en microsegundos, consumido la última vez que se ejecutó el procedimiento almacenado. <sup>1</sup>|  
|**min_worker_time**|**bigint**|El tiempo de CPU mínimo, en microsegundos, que este procedimiento almacenado ha consumido alguna vez durante una ejecución. <sup>1</sup>|  
|**max_worker_time**|**bigint**|El tiempo de CPU máximo, en microsegundos, que este procedimiento almacenado ha consumido alguna vez durante una ejecución. <sup>1</sup>|  
|**total_physical_reads**|**bigint**|El número total de lecturas físicas realizadas por las ejecuciones de este procedimiento almacenado desde que se compiló.<br /><br /> Será siempre 0 al consultar una tabla optimizada para memoria.|  
|**last_physical_reads**|**bigint**|El número de lecturas físicas realizadas la última vez que se ejecutó el procedimiento almacenado.<br /><br /> Será siempre 0 al consultar una tabla optimizada para memoria.|  
|**min_physical_reads**|**bigint**|El número mínimo de lecturas físicas que este procedimiento almacenado se ha realizado durante una ejecución.<br /><br /> Será siempre 0 al consultar una tabla optimizada para memoria.|  
|**max_physical_reads**|**bigint**|El número máximo de lecturas físicas que este procedimiento almacenado se ha realizado durante una ejecución.<br /><br /> Será siempre 0 al consultar una tabla optimizada para memoria.|  
|**total_logical_writes**|**bigint**|El número total de lecturas lógicas realizadas por las ejecuciones de este procedimiento almacenado desde que se compiló.<br /><br /> Será siempre 0 al consultar una tabla optimizada para memoria.|  
|**last_logical_writes**|**bigint**|El número de páginas del grupo de búferes desfasadas la última vez que se ejecutó el plan. Si una página ya está desfasada (modificada) no se cuenta ninguna escritura.<br /><br /> Será siempre 0 al consultar una tabla optimizada para memoria.|  
|**min_logical_writes**|**bigint**|El número mínimo de escrituras lógicas que este procedimiento almacenado se ha realizado durante una ejecución.<br /><br /> Será siempre 0 al consultar una tabla optimizada para memoria.|  
|**max_logical_writes**|**bigint**|El número máximo de escrituras lógicas que este procedimiento almacenado se ha realizado durante una ejecución.<br /><br /> Será siempre 0 al consultar una tabla optimizada para memoria.|  
|**total_logical_reads**|**bigint**|El número total de lecturas lógicas realizadas por las ejecuciones de este procedimiento almacenado desde que se compiló.<br /><br /> Será siempre 0 al consultar una tabla optimizada para memoria.|  
|**last_logical_reads**|**bigint**|El número de lecturas lógicas realizadas la última vez que se ejecutó el procedimiento almacenado.<br /><br /> Será siempre 0 al consultar una tabla optimizada para memoria.|  
|**min_logical_reads**|**bigint**|El número mínimo de lecturas lógicas que este procedimiento almacenado se ha realizado durante una ejecución.<br /><br /> Será siempre 0 al consultar una tabla optimizada para memoria.|  
|**max_logical_reads**|**bigint**|El número máximo de lecturas lógicas que este procedimiento almacenado se ha realizado durante una ejecución.<br /><br /> Será siempre 0 al consultar una tabla optimizada para memoria.|  
|**total_elapsed_time**|**bigint**|El tiempo total transcurrido, en microsegundos, hasta las ejecuciones completadas de este procedimiento almacenado.|  
|**last_elapsed_time**|**bigint**|Tiempo transcurrido, en microsegundos, hasta la ejecución completada más recientemente de este procedimiento almacenado.|  
|**min_elapsed_time**|**bigint**|El tiempo mínimo transcurrido, en microsegundos, para cualquier ejecución completada de este procedimiento almacenado.|  
|**max_elapsed_time**|**bigint**|El tiempo máximo transcurrido, en microsegundos, para cualquier ejecución completada de este procedimiento almacenado.|  
|**total_spills**|**bigint**|El número total de páginas derramado mediante la ejecución de este procedimiento almacenado desde que se compiló.<br /><br /> **Se aplica a**: a partir de [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**last_spills**|**bigint**|El número de páginas derramado la última vez que se ejecutó el procedimiento almacenado.<br /><br /> **Se aplica a**: a partir de [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**min_spills**|**bigint**|El número mínimo de páginas que este procedimiento almacenado ha derramado alguna vez durante una ejecución.<br /><br /> **Se aplica a**: a partir de [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**max_spills**|**bigint**|El número máximo de páginas que este procedimiento almacenado ha derramado alguna vez durante una ejecución.<br /><br /> **Se aplica a**: a partir de [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**pdw_node_id**|**int**|El identificador para el nodo que se encuentra en esta distribución.<br /><br />**Se aplica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]|  
  
 <sup>1</sup> para los procedimientos almacenados compilados de forma nativa cuando se habilita la recopilación de estadísticas, el tiempo de trabajo se recopila en milisegundos. Si la consulta se ejecuta en menos de un milisegundo, el valor será 0.  
  
## <a name="permissions"></a>Permissions  

En [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requiere `VIEW SERVER STATE` permiso.   
En [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], requiere el `VIEW DATABASE STATE` permiso en la base de datos.   
   
## <a name="remarks"></a>Comentarios  
 Las estadísticas en la vista se actualizan cuando una ejecución del procedimiento almacenado se completa.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se devuelve información acerca de los diez procedimientos almacenados identificados con el mayor promedio de tiempo transcurrido.  
  
```sql  
SELECT TOP 10 d.object_id, d.database_id, OBJECT_NAME(object_id, database_id) 'proc name',   
    d.cached_time, d.last_execution_time, d.total_elapsed_time,  
    d.total_elapsed_time/d.execution_count AS [avg_elapsed_time],  
    d.last_elapsed_time, d.execution_count  
FROM sys.dm_exec_procedure_stats AS d  
ORDER BY [total_worker_time] DESC;  
```  
  
## <a name="see-also"></a>Vea también  
[Vistas de administración dinámica y funciones relacionadas con ejecuciones &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
[sys.dm_exec_sql_text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
[sys.dm_exec_query_plan &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)    
[sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)    
[sys.dm_exec_trigger_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)    
[sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)    
  
  


