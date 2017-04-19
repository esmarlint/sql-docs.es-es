---
title: "Establecer opciones de &#237;ndice | Microsoft Docs"
ms.custom: ""
ms.date: "02/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-indexes"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ALLOW_ROW_LOCKS, opción"
  - "SORT_IN_TEMPDB, opción"
  - "DROP_EXISTING, cláusula"
  - "datos de gran tamaño, índices"
  - "PAD_INDEX"
  - "STATISTICS_NORECOMPUTE"
  - "opción de índice MAXDOP, configuración"
  - "opciones de índice [SQL Server]"
  - "MAXDOP, opción de índice"
  - "IGNORE_DUP_KEY, opción"
  - "ALLOW_PAGE_LOCKS, opción"
  - "ONLINE"
ms.assetid: 7969af33-e94c-41f7-ab89-9d9a2747cd5c
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Establecer opciones de &#237;ndice
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  En este tema se describe cómo modificar las propiedades de un índice en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Limitaciones y restricciones](#Restrictions)  
  
     [Seguridad](#Security)  
  
-   **Para modificar las propiedades de un índice, use:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="Restrictions"></a> Limitaciones y restricciones  
  
-   Las siguientes opciones se aplican inmediatamente al índice mediante la cláusula SET de la instrucción ALTER INDEX: ALLOW_PAGE_LOCKS, ALLOW_ROW_LOCKS, IGNORE_DUP_KEY y STATISTICS_NORECOMPUTE.  
  
-   Las opciones siguientes se pueden establecer cuando se vuelve a generar un índice mediante ALTER INDEX REBUILD o CREATE INDEX WITH DROP_EXISTING: PAD_INDEX, FILLFACTOR, SORT_IN_TEMPDB, IGNORE_DUP_KEY, STATISTICS_NORECOMPUTE, ONLINE, ALLOW_ROW_LOCKS, ALLOW_PAGE_LOCKS, MAXDOP y DROP_EXISTING (solo CREATE INDEX).  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 Requiere el permiso ALTER en la tabla o la vista.  
  
##  <a name="SSMSProcedure"></a> Usar SQL Server Management Studio  
  
#### Para modificar las propiedades de un índice en el Diseñador de tablas  
  
1.  En el Explorador de objetos, haga clic en el signo más para expandir la base de datos que contiene la tabla en la que desea modificar las propiedades de un índice.  
  
2.  Haga clic en el signo más para expandir la carpeta **Tablas** .  
  
3.  Haga clic con el botón derecho en la tabla en la que quiere modificar las propiedades de un índice y seleccione **Diseño**.  
  
4.  En el menú **Diseñador de tablas**, haga clic en **Índices o claves**.  
  
5.  Seleccione el índice que desea modificar. Sus propiedades aparecerán en la cuadrícula principal.  
  
6.  Cambie los valores de una o todas las propiedades para personalizar el índice.  
  
7.  Haga clic en **Cerrar**.  
  
8.  En el menú **Archivo**, seleccione **Guardar***nombre_tabla*.  
  
#### Para modificar las propiedades de un índice en el Explorador de objetos  
  
1.  En el Explorador de objetos, haga clic en el signo más para expandir la base de datos que contiene la tabla en la que desea modificar las propiedades de un índice.  
  
2.  Haga clic en el signo más para expandir la carpeta **Tablas** .  
  
3.  Haga clic en el signo más para expandir la tabla en la que desea modificar las propiedades de un índice.  
  
4.  Haga clic en el signo más para expandir la carpeta **Índices** .  
  
5.  Haga clic con el botón derecho en el índice en el que quiere modificar las propiedades y seleccione **Propiedades**.  
  
6.  Debajo de **Seleccionar una página**, seleccione **Opciones**.  
  
7.  Cambie los valores de una o todas las propiedades para personalizar el índice.  
  
8.  Para agregar, quitar o cambiar la posición de una columna de índice, seleccione la página **General** del cuadro de diálogo **Propiedades del índice:** *nombre_índice*. Para obtener más información, consulte [Index Properties F1 Help](../../relational-databases/indexes/index-properties-f1-help.md).  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
  
#### Para ver las propiedades de todos los índices en una tabla  
  
1.  En el **Explorador de objetos**, conéctese a una instancia del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En la barra de Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT i.name AS index_name,   
        i.type_desc,   
        i.is_unique,   
        ds.type_desc AS filegroup_or_partition_scheme,   
        ds.name AS filegroup_or_partition_scheme_name,   
        i.ignore_dup_key,   
        i.is_primary_key,   
        i.is_unique_constraint,   
        i.fill_factor,   
        i.is_padded,   
        i.is_disabled,   
        i.allow_row_locks,   
        i.allow_page_locks,   
        i.has_filter,   
        i.filter_definition  
    FROM sys.indexes AS i  
       INNER JOIN sys.data_spaces AS ds ON i.data_space_id = ds.data_space_id  
    WHERE is_hypothetical = 0 AND i.index_id <> 0   
       AND i.object_id = OBJECT_ID('HumanResources.Employee');   
    GO  
  
    ```  
  
#### Para establecer las propiedades de un índice  
  
1.  En el **Explorador de objetos**, conéctese a una instancia del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En la barra de Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue los ejemplos siguientes en la ventana de consulta y haga clic en **Ejecutar**.  
  
     [!code-sql[IndexDDL#AlterIndex4](../../relational-databases/indexes/codesnippet/tsql/set-index-options_1.sql)]  
  
     [!code-sql[IndexDDL#AlterIndex2](../../relational-databases/indexes/codesnippet/tsql/set-index-options_2.sql)]  
  
 Para obtener más información, vea [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md).  
  
  