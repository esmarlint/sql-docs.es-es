---
title: "Cambiar el tiempo de espera de la sesi&#243;n en una r&#233;plica de disponibilidad (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Grupos de disponibilidad [SQL Server], configurar"
  - "Grupos de disponibilidad [SQL Server], tiempo de espera de la sesión"
  - "tiempo de espera de la sesión [SQL Server]"
ms.assetid: e23c6e06-1cd1-4d4a-9bc2-e3e06ab2933d
caps.latest.revision: 26
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 26
---
# Cambiar el tiempo de espera de la sesi&#243;n en una r&#233;plica de disponibilidad (SQL Server)
  En este tema se describe cómo configurar el período de tiempo de espera de la sesión de una réplica de disponibilidad de AlwaysOn usando [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] o PowerShell en [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. El período de tiempo de espera de la sesión es una propiedad de réplica que controla el número de segundos (en segundos) que una réplica de disponibilidad espera una respuesta de ping de una réplica conectada antes de determinar que la conexión ha sufrido un error. De forma predeterminada, una réplica espera 10 segundos la respuesta de un ping. Esta propiedad de réplica solamente se aplica a la conexión entre una réplica secundaria dada y la réplica principal del grupo de disponibilidad. Para obtener más información sobre el período de tiempo de espera de sesión, vea [Información general de los grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).  
  
-   **Antes de empezar:**  
  
     [Requisitos previos](#Prerequisites)  
  
     [Recomendaciones](#Recommendations)  
  
     [Seguridad](#Security)  
  
-   **Para cambiar el período de tiempo de espera de la sesión, utilizando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="Prerequisites"></a> Requisitos previos  
  
-   Debe estar conectado a la instancia del servidor que hospeda la réplica principal.  
  
###  <a name="Recommendations"></a> Recomendaciones  
 Es recomendable que mantenga el período de espera en 10 segundos o más. Si establece el valor en menos de 10 segundos, existe la posibilidad de que un sistema sobrecargado no reciba los PING y declare un error falso.  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 Se requiere el permiso ALTER AVAILABILITY GROUP en el grupo de disponibilidad, el permiso CONTROL AVAILABILITY GROUP, el permiso ALTER ANY AVAILABILITY GROUP o el permiso CONTROL SERVER.  
  
##  <a name="SSMSProcedure"></a> Usar SQL Server Management Studio  
 **Para cambiar el período de tiempo de espera de la sesión para una réplica de disponibilidad**  
  
1.  En el Explorador de objetos, conéctese a la instancia del servidor que hospeda la réplica principal y expanda el árbol.  
  
2.  Expanda los nodos **Alta disponibilidad de AlwaysOn** y **Grupos de disponibilidad**.  
  
3.  Haga clic en el grupo de disponibilidad cuya réplica de disponibilidad desea configurar.  
  
4.  Haga clic con el botón derecho en la réplica que vaya a configurar y haga clic en **Propiedades**.  
  
5.  En el cuadro de diálogo **Propiedades de réplica de disponibilidad**, use el campo **Tiempo de espera de sesión (segundos)** para cambiar el número de segundos del período de tiempo de espera de la sesión en la réplica.  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
 **Para cambiar el período de tiempo de espera de la sesión para una réplica de disponibilidad**  
  
1.  Conéctese a la instancia del servidor que hospeda la réplica principal.  
  
2.  Use la instrucción [ALTER AVAILABILITY GROUP](../../../t-sql/statements/alter-availability-group-transact-sql.md) del siguiente modo:  
  
     ALTER AVAILABILITY GROUP *group_name*  
  
     MODIFY REPLICA ON '*instance_name*' WITH ( SESSION_TIMEOUT =*seconds* )  
  
     donde *group_name* es el nombre del grupo de disponibilidad, *instance_name* es el nombre de la instancia del servidor que hospeda la réplica de disponibilidad que se va a modificar y *seconds* especifica el número mínimo de segundos que la réplica debe esperar antes de la aplicación del registro a las bases de datos cuando actúa como una réplica secundaria. El valor predeterminado es 0 segundos, lo que indica que no hay ningún retraso de aplicación.  
  
     En el ejemplo siguiente, escrito en la réplica principal del grupo de disponibilidad `AccountsAG`, se cambia el valor de tiempo de espera de la sesión a `15` segundos para la réplica que se encuentra en la instancia del servidor `INSTANCE09`.  
  
    ```  
    ALTER AVAILABILITY GROUP AccountsAG   
       MODIFY REPLICA ON 'INSTANCE09' WITH (SESSION_TIMEOUT = 15);  
    ```  
  
##  <a name="PowerShellProcedure"></a> Usar PowerShell  
 **Para cambiar el período de tiempo de espera de la sesión para una réplica de disponibilidad**  
  
1.  Cambie el directorio (**cd**) a la instancia del servidor que hospeda la réplica principal.  
  
2.  Use el cmdlet **Set-SqlAvailabilityReplica** con el parámetro **SessionTimeout** para cambiar el número de segundos del período de tiempo de espera de sesión en una réplica de disponibilidad especificada.  
  
     Por ejemplo, el comando siguiente establece el tiempo de espera de la sesión en 15 segundos.  
  
    ```  
    Set-SqlAvailabilityReplica –SessionTimeout 15 `   
    -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  Para ver la sintaxis de un cmdlet, use el cmdlet **Get-Help** en el entorno de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Para más información, consulte [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md).  
  
 **Para configurar y usar el proveedor de SQL Server PowerShell**  
  
-   [Proveedor de PowerShell de SQL Server](../../../relational-databases/scripting/sql-server-powershell-provider.md)  
  
## Vea también  
 [Información general de los grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  