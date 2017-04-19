---
title: "Modificar las cuentas de servicios de controlador y de cliente | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44a73ddb-18ad-415c-bfbe-126ab2e3290b
caps.latest.revision: 29
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 29
---
# Modificar las cuentas de servicios de controlador y de cliente
  En este tema, aprenderá a modificar las cuentas de servicio del cliente y Distributed Replay Controller; y, a continuación, volverá a aplicar las listas de control de acceso (ACL).  
  
### Iniciar o detener los servicios de Distributed Replay utilizando Administración de equipos  
  
1.  En el equipo en el que se instalan los servicios de Distributed Replay, desde el símbolo del sistema, escriba **dcomcnfg**.  
  
2.  Haga doble clic en **Servicios**, desplácese hacia abajo y haga clic con el botón derecho en **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay \<service name>** y, después, haga clic en **Iniciar** o **Detener**.  
  
### Para modificar el servicio Distributed Replay Controller  
  
1.  En el equipo del controlador, detenga el servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller.  
  
2.  En **Servicios**, haga clic con el botón derecho en **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller** y luego seleccione **Propiedades**.  
  
3.  En la ventana **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller** , en la pestaña **Iniciar sesión** , seleccione **Esta cuenta**, escriba la nueva cuenta de inicio de sesión o haga clic en **Examinar** para buscarla y, a continuación, haga clic en **Aceptar**.  
  
     **Importante**: al configurar Distributed Replay Controller, puede especificar una o más cuentas de usuario que se usarán para ejecutar los servicios Distributed Replay Client. La lista siguiente es una relación de las cuentas admitidas:  
  
    -   Cuenta de usuario de dominio  
  
    -   Cuenta de usuario local creada por el usuario  
  
    -   Administrador  
  
    -   Cuenta virtual y MSA (cuenta de servicio administrada)  
  
    -   Servicios de red, servicios locales y sistema  
  
     No se aceptan cuentas de grupo (locales o de dominio) y otras cuentas integradas (como Todos).  
  
4.  Inicie el servicio Distributed Replay Controller.  
  
### Para modificar el servicio Distributed Replay Client  
  
1.  Antes de modificar el servicio Distributed Replay Client, asegúrese de que la cuenta del servicio de cliente que va a cambiar se especificó durante la instalación (en el parámetro CTLRUSERS en el equipo del controlador). Si la cuenta de servicio de cliente que va a cambiar no se especificó durante la configuración, primero debe realizar los siguientes pasos:  
  
    1.  Detenga el servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller.  
  
    2.  En el equipo del controlador en el que esté instalado el servicio del controlador, desde el símbolo del sistema, escriba **dcomcnfg**.  
  
    3.  En la ventana **Servicios de componentes**, vaya a **Raíz de consola -> Servicios de componentes -> Equipos -> Mi PC -> DCOM Config ->DReplayController**.  
  
    4.  Haga clic con el botón derecho en **DReplayController** y luego haga clic en **Propiedades**.  
  
    5.  En la ventana **Propiedades de DReplayController** , en la pestaña **Seguridad** , haga clic en **Editar** en la sección **Permisos de inicio y activación** .  
  
    6.  Conceda a la nueva cuenta de inicio de sesión del servicio de cliente los permisos **Activación local y remota** y, a continuación, haga clic en **Aceptar**.  
  
    7.  Haga clic en **Editar** en la sección **Permisos de acceso** y conceda a la nueva cuenta de inicio de sesión del servicio cliente los permisos **Acceso local y remoto** y, a continuación, haga clic en **Aceptar**.  
  
    8.  Haga clic en **Aceptar** para cerrar la ventana **Propiedades de DReplayController** .  
  
    9. En el equipo del controlador, agregue la cuenta de inicio de sesión de servicio de cliente cambiada al grupo **Usuarios COM distribuidos** .  
  
    10. Inicie el servicio SQL Server Distributed Replay Controller.  
  
2.  Detenga el servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Client.  
  
3.  En la ventana **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Client** , en la pestaña **Iniciar sesión** , seleccione **Esta cuenta**, escriba la nueva cuenta de inicio de sesión o haga clic en **Examinar** para buscarla y, a continuación, haga clic en **Aceptar**.  
  
4.  Inicie el servicio Distributed Replay Client.  
  
  