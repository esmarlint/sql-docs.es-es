---
title: "Establecer la opci&#243;n de configuraci&#243;n del servidor Fecha l&#237;mite de a&#241;o de dos d&#237;gitos | Microsoft Docs"
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
  - "fecha límite de año de dos dígitos (opción)"
  - "años de cuatro dígitos [SQL Server]"
ms.assetid: d94e81b6-f2e6-47ef-b497-ec3d827a1646
caps.latest.revision: 23
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 23
---
# Establecer la opci&#243;n de configuraci&#243;n del servidor Fecha l&#237;mite de a&#241;o de dos d&#237;gitos
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  En este tema se describe cómo configurar la opción de configuración de servidor **fecha límite de año de dos dígitos** en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. La opción de **fecha límite de año de dos dígitos** especifica un número entero entre 1753 y 9999 que representa el año límite para interpretar años de dos dígitos como años de cuatro dígitos. El marco temporal predeterminado para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] es de 1950 a 2049, que indica el año límite 2049. Esto significa que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interpreta un año con dos dígitos igual a 49 como 2049, un año con dos dígitos igual a 50 como 1950 y un año con dos dígitos igual a 99 como 1999. Para mantener la compatibilidad con las versiones anteriores, utilice el valor predeterminado.  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Recomendaciones](#Recommendations)  
  
     [Seguridad](#Security)  
  
-   **Para configurar la opción de fecha límite de año de dos dígitos, use:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Seguimiento:**  [Después de configurar la opción de fecha límite de año de dos dígitos](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="Recommendations"></a> Recomendaciones  
  
-   Esta opción es avanzada y solo debe cambiarla un administrador de base de datos con experiencia o un técnico de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con la titulación apropiada.  
  
-   Los objetos de automatización OLE utilizan 2030 como el año límite de dos dígitos. Puede utilizar la opción de **fecha límite de año de dos dígitos** para que los valores de fecha de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y las aplicaciones cliente sean coherentes. No obstante, para evitar ambigüedades con las fechas, utilice años con cuatro dígitos en los datos.  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 De forma predeterminada, todos los usuarios tienen permisos de ejecución en **sp_configure** sin ningún parámetro o solo con el primero. Para ejecutar **sp_configure** con ambos parámetros y cambiar una opción de configuración, o para ejecutar la instrucción RECONFIGURE, un usuario debe tener el permiso ALTER SETTINGS en el nivel de servidor. Los roles fijos de servidor **sysadmin** y **serveradmin** tienen el permiso ALTER SETTINGS de forma implícita.  
  
##  <a name="SSMSProcedure"></a> Usar SQL Server Management Studio  
  
#### Para configurar la opción de fecha límite de año de dos dígitos  
  
1.  En el Explorador de objetos, haga clic con el botón derecho en un servidor y seleccione **Propiedades**.  
  
2.  Haga clic en el nodo **Configuración adicional del servidor** .  
  
3.  En **Compatibilidad con años de dos dígitos**, en el cuadro **Cuando se escriba un año con dos dígitos**, **debe interpretarse como un año entre** , escriba o seleccione un valor que represente el último año del intervalo de tiempo.  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
  
#### Para configurar la opción de fecha límite de año de dos dígitos  
  
1.  Conéctese con el [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**. En este ejemplo se muestra cómo usar [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) para establecer el valor de la opción de `two digit year cutoff` en `2030`.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'two digit year cutoff', 2030 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 Para obtener más información, vea [Opciones de configuración de servidor &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Seguimiento: Después de configurar la opción de fecha límite de año de dos dígitos  
 La configuración surte efecto inmediatamente, sin necesidad de reiniciar el servidor.  
  
## Vea también  
 [Opciones de configuración de servidor &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)  
  
  