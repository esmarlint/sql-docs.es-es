---
title: "Establecer la opci&#243;n de configuraci&#243;n del servidor Espera de consulta | Microsoft Docs"
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
  - "consultas [SQL Server], tiempo de espera agotado"
  - "tiempo [SQL Server], tiempo de espera de consulta"
  - "query wait, opción [SQL Server]"
ms.assetid: 0fc4aa01-65a3-4a33-9ef4-caca41add238
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# Establecer la opci&#243;n de configuraci&#243;n del servidor Espera de consulta
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  En este tema se describe cómo establecer la opción de configuración del servidor **Espera de consulta** en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Las consultas que utilizan mucha memoria (como las relativas a operaciones de ordenación y aplicación del algoritmo de hash) se colocan en cola cuando la memoria disponible para ejecutarlas es insuficiente. La opción **Espera de consulta** especifica el tiempo en segundos (de 0 a 2147483647) que una consulta espera para usar los recursos antes de que se agote el tiempo de espera. El valor predeterminado para esta opción es -1. Esto significa que el tiempo de espera se calcula como 25 veces el costo estimado de la consulta.  
  
> [!IMPORTANT]  
>  Una transacción que contiene la consulta en espera puede retener bloqueos mientras la consulta espera para utilizar la memoria. En situaciones poco habituales, es posible que se produzca un interbloqueo no detectable. Al disminuir el tiempo de espera de la consulta, disminuye la probabilidad de que se produzcan estos interbloqueos. Finalmente, se terminará una consulta en espera y se liberarán los bloqueos de la transacción. No obstante, el aumento del tiempo de espera máximo puede aumentar el tiempo para que la consulta se termine. Se recomienda no realizar cambios en esta opción.  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Recomendaciones](#Recommendations)  
  
     [Seguridad](#Security)  
  
-   **Para configurar la opción Espera de consulta, utilizando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Seguimiento:**  [después de configurar la opción Espera de consulta](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="Recommendations"></a> Recomendaciones  
  
-   Esta opción es avanzada y solo debe cambiarla un administrador de base de datos con experiencia o un técnico de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con la titulación apropiada.  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 De forma predeterminada, todos los usuarios tienen permisos de ejecución en **sp_configure** sin ningún parámetro o solo con el primero. Para ejecutar **sp_configure** con ambos parámetros y cambiar una opción de configuración, o para ejecutar la instrucción RECONFIGURE, un usuario debe tener el permiso ALTER SETTINGS en el servidor. Los roles fijos de servidor **sysadmin** y **serveradmin** tienen el permiso ALTER SETTINGS de forma implícita.  
  
##  <a name="SSMSProcedure"></a> Usar SQL Server Management Studio  
  
#### Para configurar la opción query wait  
  
1.  En el Explorador de objetos, haga clic con el botón derecho en un servidor y seleccione **Propiedades**.  
  
2.  Haga clic en el nodo **Avanzado** .  
  
3.  En **Paralelismo**, escriba el valor que desee para la opción **Espera de consulta** .  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
  
#### Para configurar la opción query wait  
  
1.  Conéctese con el [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**. Este ejemplo muestra cómo usar [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) para establecer el valor de la opción `query wait` en `7500` segundos.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'query wait', 7500 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 Para obtener más información, vea [Opciones de configuración de servidor &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Seguimiento: Después de configurar la opción Espera de consulta  
 La configuración surte efecto inmediatamente, sin necesidad de reiniciar el servidor.  
  
## Vea también  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Opciones de configuración de servidor &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  