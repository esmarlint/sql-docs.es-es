---
title: Ver la definición de tabla | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- showing table properties
- displaying table properties
- tables [SQL Server], properties
- viewing table properties
ms.assetid: 1865fb7c-f480-4100-9007-df5364cd002a
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7b41275480fb2ae4adcc6f5e92c7e5c41ce9137f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37290343"
---
# <a name="view-the-table-definition"></a>Vea la definición de tabla
  Puede mostrar las propiedades de una tabla en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Seguridad](#Security)  
  
-   **Para mostrar las propiedades de la tabla con:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de empezar  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permissions  
 Solamente puede ver las propiedades de una tabla si es propietario de la tabla o tiene concedidos permisos para esa tabla.  
  
##  <a name="SSMSProcedure"></a> Usar SQL Server Management Studio  
  
#### <a name="to-show-table-properties-in-the-properties-window"></a>Para mostrar las propiedades de la tabla en la ventana Propiedades  
  
1.  En el Explorador de objetos, seleccione la tabla cuyas propiedades desea mostrar.  
  
2.  Haga clic con el botón secundario en la tabla y elija **Propiedades** en el menú contextual. Para obtener más información, consulte [Table Properties](table-properties-ssms.md).  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
  
#### <a name="to-show-table-properties"></a>Para mostrar las propiedades de una tabla  
  
1.  En el **Explorador de objetos**, conéctese a una instancia del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En la barra de Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**. El ejemplo devuelve todas las columnas de la vista de catálogo `sys.tables` para el objeto especificado.  
  
    ```  
    SELECT * FROM sys.tables  
    WHERE object_id = 1973582069;  
  
    ```  
  
 Para obtener más información, vea [sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql).  
  
###  <a name="TsqlExample"></a>  
