---
title: Conceder acceso a una base de datos | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: t-sql
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
helpviewer_keywords:
- database access
ms.assetid: 686edfe2-3650-48a6-a2da-9d46fa211ad8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 75d4f048573ce60b0be6704196b376c8136aa213
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37424094"
---
# <a name="lesson-2-2---granting-access-to-a-database"></a>Lección 2-2: Conceder acceso a una base de datos
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]
Mary ahora tiene acceso a esta instancia de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], pero no tiene permiso para tener acceso a las bases de datos. Incluso no tiene acceso a su propia base de datos **TestData** hasta que la autorice como usuario de base de datos.  
  
Para conceder acceso a Mary, cambie a la base de datos **TestData** y, a continuación, use la instrucción CREATE USER para asignar su inicio de sesión a un usuario denominado Mary.  
  
### <a name="to-create-a-user-in-a-database"></a>Para crear un usuario en una base de datos  
  
1.  Escriba y ejecute las siguientes instrucciones (reemplace `computer_name` con el nombre de su equipo) para conceder acceso a `Mary` a la base de datos `TestData` .  
  
    ```  
    USE [TestData];  
    GO  
  
    CREATE USER [Mary] FOR LOGIN [computer_name\Mary];  
    GO  
  
    ```  
  
    Ahora, Mary tiene acceso a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] y a la base de datos `TestData` .  
  
## <a name="next-task-in-lesson"></a>Siguiente tarea de la lección  
[Crear vistas y procedimientos almacenados](../t-sql/lesson-2-3-creating-views-and-stored-procedures.md)  
  
  
  
