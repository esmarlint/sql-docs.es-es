---
title: sp_articleview (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_articleview
- sp_articleview_TSQL
helpviewer_keywords:
- sp_articleview
ms.assetid: a3d63fd6-f360-4a2f-8a82-a0dc15f650b3
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 68d7b62faa098eedb77bf1576020f01c090fcbd5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32993392"
---
# <a name="sparticleview-transact-sql"></a>sp_articleview (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea la vista que define el artículo publicado cuando una tabla se filtra horizontal o verticalmente. Esta vista se utiliza como el origen filtrado del esquema y los datos de las tablas de destino. Con este procedimiento almacenado solamente pueden modificarse artículos sin suscripciones. Este procedimiento almacenado se ejecuta en el publicador de la base de datos de publicación.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_articleview [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @view_name = ] 'view_name']  
    [ , [ @filter_clause = ] 'filter_clause']  
    [ , [ @change_active = ] change_active ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @refreshsynctranprocs = ] refreshsynctranprocs ]  
    [ , [ @internal = ] internal ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@publication=**] **'***publicación***'**  
 Es el nombre de la publicación que contiene el artículo. *publicación* es **sysname**, no tiene ningún valor predeterminado.  
  
 [  **@article=**] **'***artículo***'**  
 Es el nombre del artículo. *artículo* es **sysname**, no tiene ningún valor predeterminado.  
  
 [  **@view_name=**] **'***view_name***'**  
 Es el nombre de la vista que define el artículo publicado. *view_name* es **nvarchar (386)**, su valor predeterminado es null.  
  
 [  **@filter_clause=**] **'***filter_clause***'**  
 Es una cláusula de restricción (WHERE) que define un filtro horizontal. Cuando escriba la cláusula de restricción, omita la palabra clave WHERE. *filter_clause* es **ntext**, su valor predeterminado es null.  
  
 [  **@change_active =** ] *change_active*  
 Permite modificar las columnas en publicaciones con suscripciones. *change_active* es un **int**, su valor predeterminado es **0**. Si **0**, no se cambian las columnas. Si **1**, se pueden crear vistas o volverá a crearse en los artículos activos que tienen suscripciones.  
  
 [  **@force_invalidate_snapshot =** ] *force_invalidate_snapshot*  
 Confirma que la acción realizada por este procedimiento almacenado puede invalidar una instantánea existente. *force_invalidate_snapshot* es un **bits**, su valor predeterminado es **0**.  
  
 **0** especifica que los cambios en el artículo no invalidarán la instantánea no es válida. Si el procedimiento almacenado detecta que el cambio requiere una nueva instantánea, se producirá un error y no se realizarán cambios.  
  
 **1** especifica que los cambios en el artículo pueden invalidar la instantánea no es válida y si hay suscripciones existentes que requieran una nueva instantánea, concede permiso para marcar como obsoleta la instantánea existente y generar una nueva.  
  
 [  **@force_reinit_subscription =]** *force_reinit_subscription*  
 Confirma que la acción realizada por este procedimiento almacenado puede requerir que se reinicialicen las suscripciones existentes. *force_reinit_subscription* es un **bits** con un valor predeterminado de **0**.  
  
 **0** especifica que los cambios en el artículo hacen que la suscripción para reinicializarla. Si el procedimiento almacenado detecta que el cambio requiere la reinicialización de suscripciones, se producirá un error y no se realizarán cambios.  
  
 **1** especifica que los cambios en el artículo hace que la suscripción existente que se reinicialicen y concede permiso para que se lleve a cabo la reinicialización.  
  
 [ **@publisher**=] **'***publisher***'**  
 Especifica un no[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] publisher. *Publisher* es **sysname**, su valor predeterminado es null.  
  
> [!NOTE]  
>  *Publisher* no debe usarse al publicar desde una [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher.  
  
 [ **@refreshsynctranprocs** =] *refreshsynctranprocs*  
 Indica si los procedimientos almacenados utilizados para sincronizar la replicación se vuelven a crear automáticamente. *refreshsynctranprocs* es **bits**, su valor predeterminado es 1.  
  
 **1** significa que los procedimientos almacenados se vuelven a creados.  
  
 **0** significa que no se vuelven a creados los procedimientos almacenados.  
  
 [ **@internal**=] *interno*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 **sp_articleview** crea la vista que define el artículo publicado e inserta el Id. de esta vista en el **sync_objid** columna de la [sysarticles &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/sysarticles-transact-sql.md) tabla e inserta el texto de la cláusula de restricción en la **filter_clause** columna. Si se replican todas las columnas y no hay ningún **filter_clause**, el **sync_objid** en el [sysarticles &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/sysarticles-transact-sql.md) tabla está establecida en el identificador de la tabla base y el uso de **sp_articleview** no es necesario.  
  
 Para publicar una tabla filtrada verticalmente (es decir, para filtrar columnas) ejecute primero **sp_addarticle** y no tienen ninguna *sync_object* parámetro, ejecute [sp_articlecolumn &#40;&#41; ](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) una vez para cada columna replicar (definiendo el filtro vertical) y, a continuación, ejecutarse **sp_articleview** para crear la vista que define el artículo publicado.  
  
 Para publicar una tabla filtrada horizontalmente (es decir, para filtrar filas), ejecute [sp_addarticle &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) y no tienen ninguna *filtro* parámetro. Ejecutar [sp_articlefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md), con todos los parámetros, incluido *filter_clause*. A continuación, ejecute **sp_articleview**, con todos los parámetros, incluido el mismo parámetro *filter_clause*.  
  
 Para publicar una tabla filtrada vertical y horizontalmente, ejecute [sp_addarticle &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) y no tienen ninguna *sync_object* o *filtro* parámetros. Ejecutar [sp_articlecolumn &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) una vez para cada columna que se va a replicarse y vuelva a ejecutar [sp_articlefilter &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) y **sp_ articleview**.  
  
 Si el artículo ya tiene una vista que define el artículo publicado, **sp_articleview** quita la vista existente y crea automáticamente una nueva. Si la vista se creó manualmente (**tipo** en [sysarticles &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/sysarticles-transact-sql.md) es **5**), no se quita la vista existente.  
  
 Si crea un procedimiento almacenado de filtro personalizado y una vista que define el artículo publicado manualmente, no podrán ejecutarse **sp_articleview**. En su lugar, proporciónelos como el *filtro* y *sync_object* parámetros [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md), junto con el adecuado *tipo* valor.  
  
## <a name="example"></a>Ejemplo  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-articleview-transact-_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 Solo los miembros de la **sysadmin** rol fijo de servidor o **db_owner** rol fijo de base de datos puede ejecutar **sp_articleview**.  
  
## <a name="see-also"></a>Vea también  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [Definir y modificar un filtro de fila estático](../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)   
 [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articlefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [Procedimientos almacenados de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
