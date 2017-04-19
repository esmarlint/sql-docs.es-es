---
title: "Quitar grupos de archivos inactivos (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "restauraciones por etapas [SQL Server], grupos de archivos inactivos"
  - "grupos de archivos inactivos"
  - "restaurar grupos de archivos [SQL Server]"
  - "transacciones diferidas"
  - "grupos de archivos [SQL Server], inactivos"
  - "grupos de archivos no restaurados"
ms.assetid: 055f9c6a-5c18-4942-98e7-ec918f0ff975
caps.latest.revision: 27
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 27
---
# Quitar grupos de archivos inactivos (SQL Server)
  En este tema se describe cómo quitar grupos de archivos inactivos en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Limitaciones y restricciones](#Restrictions)  
  
-   [Recomendaciones](#Recommendations)  
  
     [Seguridad](#Security)  
  
-   **Para quitar grupos de archivos inactivos, utilizando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="Restrictions"></a> Limitaciones y restricciones  
  
-   Este tema es pertinente para las bases de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que incluyen varios archivos o grupos de archivos y, en el modelo simple, solo para grupos de archivos de solo lectura.  
  
-   Todos los archivos de un grupo de archivos pasan a estar inactivos cuando se quita un grupo de archivos sin conexión.  
  
###  <a name="Recommendations"></a> Recomendaciones  
  
-   Si no se va a restaurar nunca un grupo de archivos sin restaurar, se puede convertir en *inactivo* quitándolo de la base de datos. El grupo de archivos inactivo no se podrá restaurar nunca en esta base de datos, aunque los metadatos permanecen en ella. Una vez inactivo el grupo de archivos, la base de datos se puede reiniciar y la recuperación hará que la base de datos sea coherente en todos los grupos de archivos restaurados.  
  
     Por ejemplo, establecer un grupo de archivos como inactivo es una opción para resolver transacciones diferidas generadas por un grupo de archivos sin conexión que ya no es necesario en la base de datos. Las transacciones que estaban diferidas porque el grupo de archivos estaba sin conexión salen del estado diferido una vez que el grupo de archivos queda inactivo. Para obtener más información, vea [Transacciones diferidas &#40;SQL Server&#41;](../../relational-databases/backup-restore/deferred-transactions-sql-server.md).  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 Requiere el permiso ALTER en la base de datos.  
  
##  <a name="SSMSProcedure"></a> Usar SQL Server Management Studio  
  
#### Para quitar grupos de archivos inactivos  
  
1.  En el **Explorador de objetos**, conéctese a una instancia del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] y expándala.  
  
2.  Expanda **Bases de datos**, haga clic con el botón derecho en la base de datos de la que quiera eliminar el archivo y, después, haga clic en **Propiedades**.  
  
3.  Seleccione la página **Archivos** .  
  
4.  En la cuadrícula **Archivos de base de datos** , seleccione los archivos que desee eliminar, haga clic en **Quitar**y, a continuación en **Aceptar**.  
  
5.  Seleccione la página **Grupos de archivos** .  
  
6.  En la cuadrícula **Filas** , seleccione el grupo de archivos que desee eliminar, haga clic en **Quitar**y, a continuación, en **Aceptar**.  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
  
#### Para quitar grupos de archivos inactivos  
  
1.  Conéctese con el [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**. (**Nota:** En este ejemplo se supone que ya existen los archivos y el grupo de archivos. Para crear estos objetos, vea el ejemplo B del tema [Opciones File y Filegroup de ALTER DATABASE](../Topic/ALTER%20DATABASE%20File%20and%20Filegroup%20Options%20\(Transact-SQL\).md)). En el primer ejemplo se quitan los archivos `test1dat3` y `test1dat4` del grupo de archivos inactivo utilizando la instrucción `ALTER DATABASE` con la cláusula `REMOVE FILE`. En el segundo ejemplo se quita el grupo de archivos inactivo `Test1FG1` utilizando la cláusula `REMOVE FILEGROUP`.  
  
```tsql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
REMOVE FILE test1dat3 ;  
ALTER DATABASE AdventureWorks2012  
REMOVE FILE test1dat4 ;  
GO  
  
```  
  
```tsql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
REMOVE FILEGROUP Test1FG1 ;  
GO  
  
```  
  
## Vea también  
 [Opciones File y Filegroup de ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20File%20and%20Filegroup%20Options%20\(Transact-SQL\).md)   
 [Transacciones diferidas &#40;SQL Server&#41;](../../relational-databases/backup-restore/deferred-transactions-sql-server.md)   
 [Restauraciones de archivos &#40;modelo de recuperación completa&#41;](../../relational-databases/backup-restore/file-restores-full-recovery-model.md)   
 [Restauraciones de archivos &#40;modelo de recuperación simple&#41;](../../relational-databases/backup-restore/file-restores-simple-recovery-model.md)   
 [Restauración con conexión &#40;SQL Server&#41;](../../relational-databases/backup-restore/online-restore-sql-server.md)   
 [Restaurar páginas &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-pages-sql-server.md)   
 [Restauraciones por etapas &#40;SQL Server&#41;](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)  
  
  