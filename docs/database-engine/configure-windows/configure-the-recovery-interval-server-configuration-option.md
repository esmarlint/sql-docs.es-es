---
title: "Establecer la opci&#243;n de configuraci&#243;n del servidor Intervalo de recuperaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "restaurar intervalo de recuperación [SQL Server]"
  - "puntos de comprobación [SQL Server]"
  - "recovery interval, opción [SQL Server]"
  - "recovery interval, opción predeterminada"
  - "tiempo [SQL Server], intervalo de recuperación"
  - "intervalo de recuperación [SQL Server]"
  - "número máximo de minutos por recuperación de base de datos"
  - "recuperación [SQL Server], recovery interval, opción"
ms.assetid: e4734b3b-8fbe-4b65-9c48-91b5a3dd18e1
caps.latest.revision: 39
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 39
---
# Establecer la opci&#243;n de configuraci&#243;n del servidor Intervalo de recuperaci&#243;n
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  En este tema se describe cómo establecer la opción de configuración del servidor **intervalo de recuperación** en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. La opción de **intervalo de recuperación** define un límite superior para el tiempo que debe tardar la recuperación de cada base de datos. El [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] usa el valor especificado en esta opción para determinar aproximadamente la frecuencia con la que deben emitirse los [puntos de comprobación automáticos](../../relational-databases/logs/database-checkpoints-sql-server.md) en una base de datos determinada.  
  
 El valor de intervalo de recuperación predeterminado es 0, lo que permite que el [!INCLUDE[ssDE](../../includes/ssde-md.md)] configure automáticamente el intervalo de recuperación. Normalmente, el intervalo de recuperación predeterminado tiene como resultado que los puntos de comprobación automáticos se produzcan aproximadamente cada minuto en las bases de datos activas con un tiempo de recuperación inferior a un minuto. Los valores más altos indican el tiempo de recuperación máximo aproximado, en minutos. Por ejemplo, si el intervalo de recuperación se establece en 3, indica un tiempo de recuperación máximo de aproximadamente tres minutos.  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Limitaciones y restricciones](#Restrictions)  
  
     [Recomendaciones](#Recommendations)  
  
     [Seguridad](#Security)  
  
-   **Para establecer la opción de configuración del servidor de intervalo de recuperación, utilizando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Seguimiento:**  [después de configurar la opción de intervalo de recuperación](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="Restrictions"></a> Limitaciones y restricciones  
  
-   El intervalo de recuperación afecta solo a las bases de datos que usan el tiempo de recuperación predeterminado de destino (0). Para invalidar el intervalo de recuperación de servidor en una base de datos, configure un tiempo de recuperación de destino no predeterminado en la base de datos. Para obtener más información, vea [Cambiar el tiempo de recuperación de destino de una base de datos &#40;SQL Server&#41;](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md).  
  
###  <a name="Recommendations"></a> Recomendaciones  
  
-   Esta opción es avanzada y solo debe cambiarla un administrador de base de datos con experiencia o un técnico de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con la titulación apropiada.  
  
-   Normalmente, se recomienda mantener el intervalo de recuperación en 0, a menos que experimente problemas de rendimiento. Si decide aumentar el valor de intervalo de recuperación, es recomendable que lo haga gradualmente en pequeños incrementos y que evalúe el efecto de cada aumento incremental en el rendimiento de la recuperación.  
  
-   Si usa **sp_configure** para cambiar el valor de la opción de **intervalo de recuperación** a más de 60 (minutos), especifique RECONFIGURE WITH OVERRIDE. WITH OVERRIDE deshabilita la comprobación de los valores de configuración (para los valores no válidos o que no se recomiendan).  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 De forma predeterminada, todos los usuarios tienen permisos de ejecución en **sp_configure** sin ningún parámetro o solo con el primero. Para ejecutar **sp_configure** con ambos parámetros y cambiar una opción de configuración, o para ejecutar la instrucción RECONFIGURE, un usuario debe tener el permiso ALTER SETTINGS en el nivel de servidor. Los roles fijos de servidor **sysadmin** y **serveradmin** tienen el permiso ALTER SETTINGS de forma implícita.  
  
##  <a name="SSMSProcedure"></a> Usar SQL Server Management Studio  
 **Para establecer el intervalo de recuperación**  
  
1.  En el Explorador de objetos, haga clic con el botón derecho en una instancia del servidor y seleccione **Propiedades**.  
  
2.  Haga clic en el nodo **Configuración de base de datos** .  
  
3.  En **Recuperación**, en el cuadro **Intervalo de recuperación (min)**, escriba o seleccione un valor entre 0 y 32767 para establecer el tiempo máximo, en minutos, que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] debe emplear en recuperar cada base de datos cuando se inicia. El valor predeterminado es 0, que indica que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lo configura automáticamente. En la práctica, esto significa un tiempo de recuperación inferior a un minuto y un punto de comprobación aproximadamente cada minuto para bases de datos activas.  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
  
#### Para establecer el intervalo de recuperación  
  
1.  Conéctese con el [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**. En este ejemplo se muestra cómo usar [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) para establecer el valor de la opción de `recovery interval` en `3` minutos.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'recovery interval', 3 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 Para obtener más información, vea [Opciones de configuración de servidor &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Seguimiento: Después de configurar la opción de intervalo de recuperación  
 La configuración surte efecto inmediatamente, sin necesidad de reiniciar el servidor.  
  
## Vea también  
 [Cambiar el tiempo de recuperación de destino de una base de datos &#40;SQL Server&#41;](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md)   
 [Puntos de comprobación de base de datos &#40;SQL Server&#41;](../../relational-databases/logs/database-checkpoints-sql-server.md)   
 [Opciones de configuración de servidor &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [show advanced options (opción de configuración del servidor)](../../database-engine/configure-windows/show-advanced-options-server-configuration-option.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)  
  
  