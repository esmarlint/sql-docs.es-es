---
title: Sys.fulltext_index_fragments (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fulltext_index_fragments
- sys.fulltext_index_fragments_TSQL
- fulltext_index_fragments_TSQL
- sys.fulltext_index_fragments
dev_langs:
- TSQL
helpviewer_keywords:
- full-text indexes [SQL Server], fragments
- full-text indexes [SQL Server], metadata
- troubleshooting [SQL Server], full-text search
- sys.fulltext_index_fragments catalog view
ms.assetid: a82e5018-5d88-45c0-9a47-c251e17a6cdb
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 18997da5a5eeb691245166be015b0678403b52ff
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33182251"
---
# <a name="sysfulltextindexfragments-transact-sql"></a>sys.fulltext_index_fragments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Un índice de texto completo utiliza tablas internas denominadas *fragmentos de índice de texto completo* para almacenar los datos de índice invertido. Esta vista se puede utilizar para consultar los metadatos sobre estos fragmentos. Esta vista contiene una fila para cada fragmento de índice de texto completo en cada tabla que contiene un índice de texto completo.  
 
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|table_id|**int**|Identificador de objeto de la tabla que contiene el fragmento de índice de texto completo.|  
|fragment_object_id|**int**|Identificador de objeto de la tabla interna asociada al fragmento.|  
|fragment_id|**int**|Identificador lógico del fragmento de índice de texto completo. Es único en todos los fragmentos de esta tabla.|  
|TIMESTAMP|**timestamp**|Marca de tiempo asociada a la creación del fragmento. Las marcas de tiempo de los fragmentos más recientes son mayores que las de los fragmentos anteriores.|  
|data_size|**int**|Tamaño lógico del fragmento en bytes.|  
|row_count|**int**|Número de filas individuales en el fragmento.|  
|status|**int**|Estado del fragmento, uno de los siguientes:<br /><br /> 0 = Creado recientemente y no utilizado todavía.<br /><br /> 1 = Se usa para la inserción durante la mezcla o el rellenado del índice de texto completo. <br /><br /> 4 = Cerrado. Preparado para la consulta.<br /><br /> 6 = Se usa para la entrada de la mezcla y preparado para la consulta.<br /><br /> 8 = Marcado para su eliminación. No se utilizará para el origen de la consulta y la mezcla.<br /><br /> Un estado de 4 ó 6 significa que el fragmento forma parte del índice de texto completo lógico y se pueden consultar; es decir, es un *consultable* fragmento.|  
  
## <a name="remarks"></a>Comentarios  
 La vista de catálogo sys.fulltext_index_fragments se puede utilizar para consultar el número de fragmentos que comprenden un índice de texto completo. Si observa que el rendimiento de la consulta de texto completo es bajo, puede utilizar sys.fulltext_index_fragments para consultar el número de fragmentos consultables (estado = 4 ó 6) en el índice de texto completo, como se explica a continuación:  
  
```  
SELECT table_id, status FROM sys.fulltext_index_fragments  
   WHERE status=4 OR status=6;  
```  
  
 Si hay muchos fragmentos consultables, Microsoft recomienda reorganizar el catálogo de texto completo que contiene el índice de texto completo para mezclar los fragmentos. Para reorganizar del catálogo de texto completo utiliza [ALTER FULLTEXT CATALOG](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md)*catalog_name* REORGANIZAR. Por ejemplo, para reorganizar un catálogo de texto completo denominado `ftCatalog` en la base de datos `AdventureWorks2012`, escriba:  
  
```  
USE AdventureWorks2012;  
GO  
ALTER FULLTEXT CATALOG ftCatalog REORGANIZE;  
GO  
```  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Object Catalog Views &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  (Vistas de catálogo de objetos [Transact-SQL])  
 [Rellenar índices de texto completo](../../relational-databases/search/populate-full-text-indexes.md)  
  
  
