---
title: sp_deletepeerrequesthistory (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_deletepeerrequesthistory
- sp_deletepeerrequesthistory_TSQL
helpviewer_keywords: sp_deletepeerrequesthistory
ms.assetid: 63a4ec6e-ce79-4bf1-9d37-5ac88f8d6beb
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9deb92cbdc9eff3e54efb1b37d18abc7bfc01252
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="spdeletepeerrequesthistory-transact-sql"></a>sp_deletepeerrequesthistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elimina el historial relacionado con una solicitud de estado de publicación, que incluye el historial de solicitudes ([MSpeer_request &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/mspeer-request-transact-sql.md)), así como el historial de respuestas ([MSpeer_response &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/mspeer-response-transact-sql.md)). Este procedimiento almacenado se ejecuta en la base de datos de publicación en un publicador que participa en una topología de replicación punto a punto. Para obtener más información, consulte [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_deletepeerrequesthistory [ @publication = ] 'publication'  
    [ , [ @request_id = ] request_id ]  
    [ , [ @cutoff_date = ] cutoff_date ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@publication=** ] **'***publicación***'**  
 Nombre de la publicación para la que se realizó la solicitud de estado. *publicación* es **sysname**, no tiene ningún valor predeterminado.  
  
 [  **@request_id=** ] *request_id*  
 Especifica una solicitud de estado individual para que se eliminen todas las respuestas a esta solicitud. *request_id* es **int**, su valor predeterminado es null.  
  
 [  **@cutoff_date=** ] *cutoff_date*  
 Especifica una fecha límite, antes de la cual se eliminan todos los registros de repuestas. *cutoff_date* es **datetime**, su valor predeterminado es null.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 **sp_deletepeerrequesthistory** se utiliza en una topología de replicación transaccional punto a punto. Para obtener más información, consulte [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 Al ejecutar **sp_deletepeerrequesthistory**, ya sea *request_id* o *cutoff_date* debe especificarse.  
  
## <a name="permissions"></a>Permissions  
 Solo los miembros de la **sysadmin** rol fijo de servidor o **db_owner** rol fijo de base de datos puede ejecutar **sp_deletepeerrequesthistory**.  
  
## <a name="see-also"></a>Vea también  
 [sp_helppeerrequests &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helppeerrequests-transact-sql.md)   
 [sp_helppeerresponses &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md)   
 [sp_requestpeerresponse &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md)  
  
  