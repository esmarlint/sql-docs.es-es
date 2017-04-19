---
title: "Deshabilitar una restricci&#243;n FOREIGN KEY para la replicaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "restricciones [SQL Server], claves externas"
  - "claves externas [SQL Server], deshabilitar restricciones"
  - "deshabilitar restricciones"
ms.assetid: 4211f2fd-d16a-4081-995c-43f1f0827f0b
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Deshabilitar una restricci&#243;n FOREIGN KEY para la replicaci&#243;n
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Puede deshabilitar las restricciones de clave externa para la replicación en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Esto puede ser útil si se publican datos de una versión anterior de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Si se publica la tabla mediante replicación, se deshabilitan automáticamente las restricciones FOREIGN KEY para las operaciones realizadas por los agentes de replicación. Cuando un agente de replicación realiza una inserción, actualización o eliminación en un suscriptor, no se comprueba la restricción. En cambio, sí se comprueba cuando lo hace un usuario. La restricción se deshabilitará para el agente de replicación porque ya se comprobó en el publicador cuando se insertaron, actualizaron o eliminaron los datos originalmente.  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Seguridad](#Security)  
  
-   **Para deshabilitar una restricción de clave externa para la replicación, use:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 Requiere el permiso ALTER en la tabla.  
  
##  <a name="SSMSProcedure"></a> Usar SQL Server Management Studio  
  
#### Para deshabilitar una restricción FOREIGN KEY para la replicación  
  
1.  En el **Explorador de objetos**, expanda la tabla con la restricción de clave externa que desee modificar y, a continuación, expanda la carpeta **Claves** .  
  
2.  Haga clic con el botón derecho en la restricción de clave externa y, luego, haga clic en **Modificar**.  
  
3.  En el cuadro de diálogo **Relaciones de clave externa** , seleccione el valor **No** para **Exigir para replicación**.  
  
4.  Haga clic en **Cerrar**.  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
  
#### Para deshabilitar una restricción FOREIGN KEY para la replicación  
  
1.  Para realizar esta tarea en [!INCLUDE[tsql](../../includes/tsql-md.md)], quite la restricción de clave externa. Después agregue una nueva restricción de clave externa y especifique la opción NOT FOR REPLICATION.  
  
 Para obtener más información, vea [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md).  
  
###  <a name="TsqlExample"></a>  