---
title: "Administraci&#243;n y mantenimiento de la instancia de cl&#250;ster de conmutaci&#243;n por error | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "cuentas de usuario [SQL Server], clústeres de conmutación"
  - "clústeres [SQL Server], mantener"
  - "nodos [Clústeres de conmutación por error]"
  - "clústeres de conmutación por error [SQL Server], mantener"
  - "agregar nodos"
  - "servidores virtuales [SQL Server], quitar nodos"
  - "instancia en clúster de SQL Server"
  - "nodos [Clústeres de conmutación por error], quitar"
  - "nodos [Clústeres de conmutación por error], agregar"
  - "cuentas de servicio [SQL Server]"
  - "quitar nodos"
  - "servidores virtuales [SQL Server], agregar nodos"
ms.assetid: 2d5c63e9-8061-45c3-94db-8dd3100b8a91
caps.latest.revision: 35
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 35
---
# Administraci&#243;n y mantenimiento de la instancia de cl&#250;ster de conmutaci&#243;n por error
  Las tareas de mantenimiento, como agregar o quitar nodos de una instancia de clúster de conmutación por error (FCI) AlwaysOn existente, se llevan a cabo mediante el programa de instalación de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Otras tareas de administración, como cambiar el recurso de dirección IP o recuperarse de determinados escenarios de la FCI, se llevan a cabo con el complemento Administrador de clústeres de conmutación por error, que es el complemento de administración del servicio de clústeres de conmutación por error de Windows Server (WSFC).  
  
## Realizar el mantenimiento de una instancia de clúster de conmutación por error  
 Después de instalar una FCI, puede cambiarla o repararla con el programa de instalación de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Por ejemplo, puede agregar nodos adicionales a una FCI, ejecutar una FCI como instancia independiente o quitar un nodo de la configuración de una FCI.  
  
### Agregar un nodo a una instancia en clúster de conmutación por error existente  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ofrece la posibilidad de mantener una FCI existente. Si elige esta opción, puede agregar otros nodos a la FCI ejecutando el programa de instalación de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en el equipo al que desea agregar la FCI. Para obtener más información, vea [Crear un nuevo clúster de conmutación por error de SQL Server &#40;programa de instalación&#41;](../../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md) y [Agregar o quitar nodos en un clúster de conmutación por error de SQL Server &#40;programa de instalación&#41;](../../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
### Quitar un nodo de una instancia en clúster de conmutación por error existente  
 Puede quitar un nodo de una FCI ejecutando el programa de instalación de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en el equipo en el que desea reducir la FCI. Cada nodo de una FCI se considera un par sin dependencias de otros nodos de la FCI, así que puede quitar cualquier nodo. Un nodo dañado no tiene que estar disponible para poder quitarlo y el proceso de eliminación no desinstala los binarios de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] del nodo no disponible. Los nodos quitados se pueden volver a agregar a una FCI en cualquier momento. Para obtener más información, vea [Agregar o quitar nodos en un clúster de conmutación por error de SQL Server &#40;programa de instalación&#41;](../../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
### Cambiar cuentas de servicio  
 No debe cambiar las contraseñas de ninguna de las cuentas de servicio de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cuando un nodo de FCI está inactivo o sin conexión. Si tiene que hacerlo, debe restablecer de nuevo la contraseña mediante el Administrador de configuración de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cuando todos los nodos vuelvan a estar en línea.  
  
 Si la cuenta de servicio de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] no es de un administrador de un clúster, no se pueden eliminar los recursos administrativos compartidos de ninguno de los nodos del clúster. Los recursos administrativos compartidos de un clúster deben estar disponibles para que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] funcione.  
  
> [!IMPORTANT]  
>  No utilice la misma cuenta para la cuenta de servicio de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] y la cuenta de servicio de WSFC. Si la contraseña cambia en la cuenta de servicio de WSFC, la instalación de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] no será satisfactoria.  
  
 En [!INCLUDE[nextref_longhorn](../../../includes/nextref-longhorn-md.md)], se usan SID de servicio para las cuentas de servicio de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Para obtener más información, vea [Configurar los permisos y las cuentas de servicio de Windows](../../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
## Administrar una instancia de clúster de conmutación por error  
  
|Descripción de la tarea|Vínculo de tema|  
|----------------------|----------------|  
|Describe cómo agregar dependencias a un recurso de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|[Agregar dependencias a un recurso de SQL Server](../../../sql-server/failover-clusters/windows/add-dependencies-to-a-sql-server-resource.md)|  
|Kerberos es un protocolo de autenticación de red diseñado para proporcionar una autenticación firme para aplicaciones cliente/servidor. Kerberos ofrece una base para la interoperabilidad y ayuda a mejorar la seguridad de la autenticación de red de toda una empresa. Se puede usar la autenticación Kerberos con instancias independientes de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] o con FCI AlwaysOn.|[Registrar un nombre de entidad de seguridad de servicio para las conexiones con Kerberos](../../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md).|  
|Proporciona vínculos a contenido que describe cómo habilitar la autenticación Kerberos||  
|Describe el procedimiento que se usa para recuperarse de un error de clúster de conmutación por error de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|[Recuperarse de un error en una instancia de clúster de conmutación por error](../../../sql-server/failover-clusters/windows/recover-from-failover-cluster-instance-failure.md)|  
|Describe el procedimiento que se usa para cambiar el recurso de dirección IP de una instancia de clúster de conmutación por error de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|[Cambiar la dirección IP de una instancia de clúster de conmutación por error](../../../sql-server/failover-clusters/windows/change-the-ip-address-of-a-failover-cluster-instance.md)|  
  
## Vea también  
 [Configurar los valores de la propiedad HealthCheckTimeout](../../../sql-server/failover-clusters/windows/configure-healthchecktimeout-property-settings.md)   
 [Configurar los valores de la propiedad FailureConditionLevel](../../../sql-server/failover-clusters/windows/configure-failureconditionlevel-property-settings.md)   
 [Ver y leer el registro de diagnósticos de la instancia de clúster de conmutación por error](../../../sql-server/failover-clusters/windows/view-and-read-failover-cluster-instance-diagnostics-log.md)  
  
  