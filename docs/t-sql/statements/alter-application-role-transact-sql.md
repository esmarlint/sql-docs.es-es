---
title: "MODIFICAR el rol de aplicación (Transact-SQL) | Documentos de Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_APPLICATION_ROLE_TSQL
- ALTER APPLICATION ROLE
dev_langs:
- TSQL
helpviewer_keywords:
- modifying application roles
- passwords [SQL Server], application roles
- ALTER APPLICATION ROLE statement
- application roles [SQL Server], modifying
ms.assetid: c6cd5d0f-18f4-49be-b161-64d9c5569086
caps.latest.revision: 46
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d5205897f64dfb05d8903ed2f4197f35bd722224
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="alter-application-role-transact-sql"></a>ALTER APPLICATION ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Esta instrucción cambia el nombre, la contraseña o el esquema predeterminado de un rol de aplicación.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
ALTER APPLICATION ROLE application_role_name   
    WITH <set_item> [ ,...n ]  
  
<set_item> ::=   
    NAME = new_application_role_name   
    | PASSWORD = 'password'  
    | DEFAULT_SCHEMA = schema_name  
```  
  
## <a name="arguments"></a>Argumentos  
 *application_role_name*  
 Nombre del rol de aplicación que va a modificarse.  
  
 NOMBRE =*new_application_role_name*  
 Especifica el nuevo nombre del rol de aplicación. Ninguna entidad de seguridad de la base de datos debe utilizar este nombre.  
  
 CONTRASEÑA ='*contraseña*'  
 Especifica la contraseña del rol de aplicación. *contraseña* debe cumplir los requisitos de directiva de contraseñas de Windows del equipo que ejecuta la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Debe utilizar siempre contraseñas seguras.  
  
 DEFAULT_SCHEMA =*schema_name*  
 Especifica el primer esquema donde buscará el servidor cuando resuelva los nombres de objetos. *schema_name* puede ser un esquema que no existe en la base de datos.  
  
## <a name="remarks"></a>Comentarios  
 Si el nombre del rol de aplicación nuevo ya existe en la base de datos, la instrucción producirá un error. Cuando se modifica el nombre, la contraseña o el esquema predeterminado de un rol de aplicación, no se cambia el identificador asociado al rol.  
  
> [!IMPORTANT]  
>  La directiva de expiración de contraseñas no se aplica a las contraseñas de rol de aplicación. Por esta razón, debe extremar las precauciones y seleccionar contraseñas seguras. Las aplicaciones que invocan roles de aplicación deben almacenar sus propias contraseñas.  
  
 Los roles de aplicación se pueden ver en la vista de catálogo sys.database_principals.  
  
> [!CAUTION]  
>  En [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]el comportamiento de los esquemas cambió el comportamiento en las versiones anteriores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si en el código se supone que los esquemas son equivalentes a usuarios de base de datos, los resultados obtenidos podrían ser incorrectos. Las vistas de catálogo antiguas, incluida sysobjects, no deben usarse en una base de datos en la que se haya usado alguna de las siguientes instrucciones DDL: CREATE SCHEMA, ALTER SCHEMA, DROP SCHEMA, CREATE USER, ALTER USER, DROP USER, CREATE ROLE, ALTER ROLE, DROP ROLE, CREATE APPROLE, ALTER APPROLE, DROP APPROLE, ALTER AUTHORIZATION. En una base de datos en la que se ha usado alguna de estas instrucciones, deben usarse las nuevas vistas de catálogo. En las nuevas vistas de catálogo se tiene en cuenta la separación de entidades de seguridad y esquemas que se establece en [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Para obtener más información sobre las vistas de catálogo, vea [Vistas de catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Requiere el permiso ALTER ANY APPLICATION ROLE en la base de datos. Para cambiar el esquema predeterminado, el usuario también tiene que cambiar el permiso en el rol de aplicación. Un rol de aplicación puede alterar su propio esquema predeterminado, pero no su nombre ni su contraseña.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-changing-the-name-of-application-role"></a>A. Cambiar el nombre de un rol de aplicación  
 En el ejemplo siguiente, se cambia el nombre del rol de aplicación de `weekly_receipts` a `receipts_ledger`.  
  
```  
USE AdventureWorks2012;  
CREATE APPLICATION ROLE weekly_receipts   
    WITH PASSWORD = '987Gbv8$76sPYY5m23' ,   
    DEFAULT_SCHEMA = Sales;  
GO  
ALTER APPLICATION ROLE weekly_receipts   
    WITH NAME = receipts_ledger;  
GO  
```  
  
### <a name="b-changing-the-password-of-application-role"></a>B. Cambiar la contraseña de un rol de aplicación  
 En el ejemplo siguiente, se cambia la contraseña del rol de aplicación `receipts_ledger`.  
  
```  
ALTER APPLICATION ROLE receipts_ledger   
    WITH PASSWORD = '897yUUbv867y$200nk2i';  
GO  
```  
  
### <a name="c-changing-the-name-password-and-default-schema"></a>C. Cambiar el nombre, la contraseña y el esquema predeterminado  
 En el ejemplo siguiente, se cambia el nombre, la contraseña y el esquema predeterminado del rol de aplicación `receipts_ledger` en la misma operación.  
  
```  
ALTER APPLICATION ROLE receipts_ledger   
    WITH NAME = weekly_ledger,   
    PASSWORD = '897yUUbv77bsrEE00nk2i',   
    DEFAULT_SCHEMA = Production;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [Roles de aplicación](../../relational-databases/security/authentication-access/application-roles.md)   
 [Crear rol de aplicación &#40; Transact-SQL &#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [DROP APPLICATION ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-application-role-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  