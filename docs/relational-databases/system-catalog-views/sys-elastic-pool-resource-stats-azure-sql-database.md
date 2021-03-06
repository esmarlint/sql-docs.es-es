---
title: Sys.elastic_pool_resource_stats (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 04/06/2018
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- Azure SQL Database
f1_keywords:
- sys.elastic_pool_resource_stats catalog view
helpviewer_keywords:
- sys.elastic_pool_resource_stats_TSQL
- sys.elastic_pool_resource_stats
- elastic_pool_resource_stats_TSQL
- elastic_pool_resource_stats
ms.assetid: f242c1bd-3cc8-4c8b-8aaf-c79b6a8a0329
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: a04b60738a48ddbe09db3eb8d7032d2f08b4ba9c
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "37997987"
---
# <a name="syselasticpoolresourcestats-azure-sql-database"></a>Sys.elastic_pool_resource_stats (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Devuelve estadísticas de uso de recursos de todos los grupos de bases de datos elásticas en un servidor lógico. Para cada grupo de bases de datos elásticas, hay una fila para cada 15 segundos (cuatro filas por minuto) de la ventana de informe. Esto incluye el uso de CPU, E/S, registro, consumo de almacenamiento y simultáneas de solicitudes o sesiones todas las bases de datos en el grupo. Estos datos se conservan durante 14 días. 
  
||  
|-|  
|**Se aplica a**: [!INCLUDE[ssSDS](../../includes/sssds-md.md)] V12.|  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**start_time**|**datetime2**|Hora de UTC que indica el inicio del segundo intervalo de informes 15.|  
|**end_time**|**datetime2**|Hora de UTC que indica el final del segundo intervalo de informes 15.|  
|**elastic_pool_name**|**nvarchar(128)**|Nombre del grupo de bases de datos elásticas.|  
|**avg_cpu_percent**|**decimal(5,2)**|Uso de proceso medio en porcentaje del límite del grupo.|  
|**avg_data_io_percent**|**decimal(5,2)**|Uso de E/S medio en porcentaje basado en el límite del grupo.|  
|**avg_log_write_percent**|**decimal(5,2)**|Promedio de escritura utilización de recursos en porcentaje del límite del grupo.|  
|**avg_storage_percent**|**decimal(5,2)**|Promedio de utilización del almacenamiento en porcentaje del límite del grupo de almacenamiento.|  
|**max_worker_percent**|**decimal(5,2)**|Máximo de trabajos simultáneos (solicitudes) en porcentaje basado en el límite del grupo.|  
|**max_session_percent**|**decimal(5,2)**|Número máximo de sesiones simultáneo en porcentaje basado en el límite del grupo.|  
|**elastic_pool_dtu_limit**|**int**|Máximo de grupo elástico DTU configuración actual de este grupo elástico durante este intervalo.|  
|**elastic_pool_storage_limit_mb**|**bigint**|Límite de almacenamiento máximo del grupo elástico actual configuración para este grupo elástico en megabytes durante este intervalo.|  
  
## <a name="remarks"></a>Notas  
 Esta vista existe en la base de datos maestra del servidor lógico. Debe estar conectado a la base de datos maestra para consultar **sys.elastic_pool_resource_stats**.  
  
## <a name="permissions"></a>Permisos  
 Debe pertenecer a la **dbmanager** rol.  
  
## <a name="examples"></a>Ejemplos  
 El ejemplo siguiente devuelve los datos de utilización de recursos ordenados por la hora más reciente de todos los grupos de bases de datos elásticas en el servidor lógico actual.  
  
```  
SELECT * FROM sys.elastic_pool_resource_stats   
ORDER BY end_time DESC;  
```  
  
 El ejemplo siguiente calcula el consumo medio de porcentaje DTU para un grupo determinado.  
  
```  
SELECT start_time, end_time,      
  (SELECT Max(v)      
FROM (VALUES (avg_cpu_percent), (avg_data_io_percent), (avg_log_write_percent)) AS value(v)) AS [avg_DTU_percent]    
FROM sys.elastic_pool_resource_stats   
WHERE elastic_pool_name = '<your pool name>'   
ORDER BY end_time DESC;  
```  
  
## <a name="see-also"></a>Vea también  
 [Control del crecimiento explosivo con bases de datos elásticas](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/)   
 [Crear y administrar un grupo de bases de datos elásticas de SQL Database (versión preliminar)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/)   
 [Sys.resource_stats &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md)   
 [Sys.dm_db_resource_stats &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md)  
  
  
