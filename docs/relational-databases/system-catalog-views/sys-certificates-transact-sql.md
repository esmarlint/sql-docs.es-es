---
title: Sys.Certificates (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- certificates
- certificates_TSQL
- sys.certificates_TSQL
- sys.certificates
dev_langs:
- TSQL
helpviewer_keywords:
- sys.certificates catalog view
ms.assetid: e5046102-a65c-401e-b80d-05636884dec9
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f5aaf349d050b2b1b1d27ae3067f003186c8c6eb
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33180321"
---
# <a name="syscertificates-transact-sql"></a>sys.certificates (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Devuelve una fila por cada certificado en la base de datos.  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|**Nombre**|**sysname**|Nombre del certificado. Es único en la base de datos.|  
|**certificate_id**|**int**|Id. del certificado. Es único en la base de datos.|  
|**principal_id**|**int**|Id. de la entidad de seguridad de la base de datos que posee este certificado.|  
|**pvt_key_encryption_type**|**char(2)**|Indica cómo se ha cifrado la clave privada.<br /><br /> NA = No hay clave privada para el certificado<br /><br /> MK = La clave privada se ha cifrado mediante la clave maestra<br /><br /> PW = La clave privada se ha cifrado mediante una contraseña definida por el usuario<br /><br /> SK = La clave privada se ha cifrado mediante la clave maestra del servicio|  
|**pvt_key_encryption_type_desc**|**nvarchar(60)**|Descripción de cómo se ha cifrado la clave privada.<br /><br /> NO_PRIVATE_KEY<br /><br /> ENCRYPTED_BY_MASTER_KEY<br /><br /> ENCRYPTED_BY_PASSWORD<br /><br /> ENCRYPTED_BY_SERVICE_MASTER_KEY|  
|**is_active_for_begin_dialog**|**bit**|Si el valor es 1, este certificado se utiliza para iniciar diálogos de servicio cifrados.|  
|**issuer_name**|**nvarchar(442)**|Nombre del emisor del certificado.|  
|**cert_serial_number**|**nvarchar(64)**|Número de serie del certificado.|  
|**SID**|**varbinary(85)**|SID (identificador de seguridad) de inicio de sesión para este certificado.|  
|**string_sid**|**nvarchar(128)**|Representación en forma de cadena del SID de inicio de sesión para este certificado.|  
|**Asunto**|**nvarchar(4000)**|Asunto del certificado.|  
|**expiry_date**|**datetime**|Fecha en que expira el certificado.|  
|**start_date**|**datetime**|Fecha en que se valida el certificado.|  
|**Huella digital**|**varbinary(32)**|Hash SHA-1 del certificado. El hash SHA-1 es único globalmente.|  
|**attested_by**|**nvarchar(260)**|Solo para uso del sistema.|  
|pvt_key_last_backup_date|**datetime**|Fecha y hora cuando la clave privada del certificado se exportó por última vez.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Para obtener más información, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vea también  
 [Vistas de catálogo de seguridad &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Vistas de catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Jerarquía de cifrado](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)  
  
  
