---
title: Asignación de origen y bases de datos de destino (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- database schemas
- mapping, databases
- schemas, mapping to
- schemas, SQL Azure
- schemas, SQL Server
- source database
- target database
ms.assetid: 69bee937-7b2c-49ee-8866-7518c683fad4
caps.latest.revision: 17
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: d0a76c4fdeff8abbe2b5e1ba2bafd615bba4b919
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2018
ms.locfileid: "38980168"
---
# <a name="mapping-source-and-target-databases-accesstosql"></a>Asignación de origen y bases de datos de destino (AccessToSQL)
Cuando se conecta a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, deberá especificar una base de datos de destino para la migración. Si tiene varias bases de datos de Access se puede asignar a varios [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] bases de datos (o esquemas) o a varios esquemas en la base de datos de SQL Azure conectada.  
  
## <a name="sql-server-or-sql-azure-database-schemas"></a>SQL Server o los esquemas de base de datos de SQL Azure  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] las bases de datos usan el concepto de esquemas para separar los objetos dentro de una base de datos en grupos lógicos. Por ejemplo, una base de datos de la biblioteca podría utilizar tres esquemas denominados **libros**, **audio**, y **vídeo** para separar los objetos de audio y vídeo de libro, entre sí. De forma predeterminada, la base de datos se asigna a **maestro** base de datos y **dbo** esquema en [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] y a la base de datos conectada y **dbo** esquema en SQL Azure.  
  
A menos que personalice la asignación entre cada base de datos de Access y la [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de datos y esquema, SSMA migrará todos los esquemas y datos asociados con la base de datos de acceso a la base de datos predeterminado asignado.  
  
## <a name="modifying-the-target-database-and-schema"></a>Modificación de la base de datos de destino y el esquema  
SSMA le permite asignar cada base de datos de Access a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o base de datos de SQL Azure y el esquema. El siguiente procedimiento describe cómo personalizar la asignación de cada base de datos.  
  
**Para modificar la base de datos de destino y el esquema**  
  
1.  En el panel Explorador de metadatos de acceso, seleccione **tengan acceso a metadatos**.  
  
    Asignación de esquema también está disponible cuando se selecciona el **bases de datos** nodo o cualquier base de datos. La lista de asignación de esquema se ha personalizado para el objeto seleccionado.  
  
2.  En el panel derecho, haga clic en el **esquema de asignación** ficha.  
  
    Verá una tabla que contiene el acceso a los nombres de base de datos y su correspondiente ssNoVersion o esquema de Sql Azure. El esquema de destino se indica en una notación de dos partes (database.schema).  
  
3.  Seleccione la fila que contiene la asignación que desea personalizar y, a continuación, haga clic en **modificar**.  
  
4.  En el **elija el esquema de destino** cuadro de diálogo, puede examinar para la base de datos de destino disponibles y el esquema o el tipo de la base de datos y el esquema de nombre en el cuadro de texto en una notación de dos partes (database.schema) y, a continuación, haga clic en **Aceptar**.  
  
**Modos de asignación**  
  
-   Asignar a SQL Server  
  
Base de datos de origen se puede asignar a cualquier base de datos de destino. De forma predeterminada se asigna la base de datos de origen a destino [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de datos con el que se ha conectado con SSMA. Si no existe la base de datos de destino que se está asignando en [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], a continuación, se le pedirá con un mensaje **"la base de datos y/o esquema no existe en el destino [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] metadatos. Se crearán durante la sincronización. ¿Desea continuar?"** Haga clic en Sí. De forma similar, se puede asignar el esquema al esquema que no existe en el destino [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de datos que se creará durante la sincronización.  
  
-   Asignación de SQL Azure  
  
Puede asignar la base de datos de origen al destino conectado [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de datos o al cualquier esquema en el destino conectado [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de datos. Si el esquema de origen se asignan a cualquier esquema que no existe en la base de datos de destino conectados, entonces se le pedirá con un mensaje **"esquema no existe en los metadatos de destino. Se crearán durante la sincronización. ¿Desea continuar? "** Haga clic en Sí.  
  
## <a name="reverting-to-your-initial-database-and-schema"></a>Revertir a la base de datos inicial y el esquema  
Si personaliza la asignación entre una base de datos y un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o base de datos de SQL Azure y el esquema, puede revertir la asignación a la base de datos que especificó cuando conecta a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure.  
  
**Restablecer al esquema y la base de datos predeterminada**  
  
1.  En la pestaña asignación de esquema, seleccione cualquier fila y haga clic en **Restablecer valores predeterminados** para revertir a la base de datos predeterminada y el esquema.  
  
## <a name="next-step"></a>Paso siguiente  
El siguiente paso del proceso de migración es [convertir objetos de base de datos](http://msdn.microsoft.com/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c)  
  
## <a name="see-also"></a>Vea también  
[Migrar bases de datos de Access a SQL Server](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
