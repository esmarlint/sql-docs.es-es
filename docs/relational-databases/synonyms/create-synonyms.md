---
title: Creación de sinónimos | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.synonym.general.f1
helpviewer_keywords:
- creating synonyms
- synonyms [SQL Server], creating
ms.assetid: fedfa7a5-d0b6-4e2b-90f4-a08122958e33
caps.latest.revision: 7
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 22cf9fe47d80716cdddbf245c9af04ae1aa0b5f5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32971760"
---
# <a name="create-synonyms"></a>Crear sinónimos
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  En este tema se describe cómo crear un sinónimo en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Seguridad](#Security)  
  
-   **Para crear un sinónimo, mediante:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de empezar  
  
###  <a name="Security"></a> Seguridad  
 Para crear un sinónimo en un esquema determinado, el usuario debe tener el permiso CREATE SYNONYM y ser propietario del esquema o tener el permiso ALTER SCHEMA. El permiso CREATE SYNONYM se puede conceder.  
  
####  <a name="Permissions"></a> Permissions  
  
##  <a name="SSMSProcedure"></a> Usar SQL Server Management Studio  
  
#### <a name="to-create-a-synonym"></a>Para crear un sinónimo  
  
1.  En el **Explorador de objetos**, expanda la base de datos donde desea crear la nueva vista.  
  
2.  Haga clic con el botón derecho en la carpeta **Sinónimos** y haga clic en **Nuevo sinónimo…**.  
  
3.  En el cuadro de diálogo **Agregar sinónimo** , escriba la siguiente información.  
  
     **Nombre de sinónimo**  
     Escriba el nombre que desea utilizar para este objeto.  
  
     **Esquema de sinónimos**  
     Escriba el esquema del nuevo nombre que desea utilizar para este objeto.  
  
     **Nombre del servidor**  
     Escriba la instancia de servidor a la que va a conectarse.  
  
     **Nombre de la base de datos**  
     Escriba o seleccione la base de datos que contiene el objeto.  
  
     **Esquema**  
     Escriba o seleccione el esquema al que pertenece el objeto.  
  
     **Tipo de objeto**  
     Seleccione el tipo de objeto.  
  
     **Nombre del objeto**  
     Escriba el nombre del objeto al que hace referencia el sinónimo.  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
  
#### <a name="to-create-a-synonym"></a>Para crear un sinónimo  
  
1.  Conéctese con el [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue los ejemplos siguientes en la ventana de consulta y haga clic en **Ejecutar**.  
  
###  <a name="TsqlExample"></a> Ejemplo (Transact-SQL)  
 En el siguiente ejemplo se crea un sinónimo para una tabla existente en la base de datos de [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . El sinónimo se utiliza en los ejemplos siguientes.  
  
```  
USE tempdb;  
GO  
CREATE SYNONYM MyAddressType  
FOR AdventureWorks2012.Person.AddressType;  
GO  
```  
  
 En el siguiente ejemplo se inserta una fila en la tabla base a la que hace referencia el sinónimo `MyAddressType` .  
  
```  
USE tempdb;  
GO  
INSERT INTO MyAddressType (Name)  
VALUES ('Test');  
GO  
```  
  
 En el siguiente ejemplo se muestra cómo se puede hacer referencia a un sinónimo en SQL dinámica.  
  
```  
USE tempdb;  
GO  
EXECUTE ('SELECT Name FROM MyAddressType');  
GO  
```  
  
  
