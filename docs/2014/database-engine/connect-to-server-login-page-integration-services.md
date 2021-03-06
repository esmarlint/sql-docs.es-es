---
title: Conectar con el servidor (página Inicio de sesión de Integration Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttodtsserver.login.f1
- sql12.swb.connecttodts.login.f1
ms.assetid: 402c2de4-f4ea-40b0-909f-3ddf3bd59950
caps.latest.revision: 23
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 703a4f062d327da13b1b75d519c70884a9228978
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37241265"
---
# <a name="connect-to-server-login-page-integration-services"></a>Conectar al servidor (página Inicio de sesión de Integration Services)
  Use esta pestaña para ver o especificar las siguientes opciones cuando se conecte a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
## <a name="options"></a>Opciones  
 **Tipo de servidor**  
 Al registrar un servidor desde el Explorador de objetos, seleccione el tipo de servidor al que conectarse: [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services o Integration Services. El resto del cuadro de diálogo muestra simplemente las opciones que se aplican al tipo de servidor seleccionado. Cuando se registra un servidor desde Servidores registrados, el cuadro **Tipo de servidor** es de solo lectura y coincide con el tipo de servidor que se muestra en el componente Servidores registrados. Para registrar un tipo distinto de servidor, seleccione [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services o Integration Services desde la barra de herramientas Servidores registrados antes de comenzar a registrar un servidor nuevo.  
  
 **Nombre del servidor**  
 Seleccione el servidor al que va a conectarse. De forma predeterminada, aparecerá la instancia de servidor a la que se ha conectado por última vez.  
  
> [!NOTE]  
>  No use  *\<servername >*\\*\<instancename >*, ya que [!INCLUDE[ssIS](../includes/ssis-md.md)] no admite varias instancias en un equipo.  
  
 **Autenticación**  
 La autenticación [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows solo está disponible para [!INCLUDE[ssIS](../includes/ssis-md.md)]. Windows permite al usuario conectarse mediante una cuenta de usuario de Windows.  
  
 **Nombre de usuario.**  
 Esta opción no está disponible ya que la autenticación de Windows solo está disponible para [!INCLUDE[ssIS](../includes/ssis-md.md)].  
  
 **Contraseña**  
 Esta opción no está disponible ya que la autenticación de Windows solo está disponible para [!INCLUDE[ssIS](../includes/ssis-md.md)].  
  
 **Recordar contraseña**  
 Esta opción no está disponible ya que la autenticación de Windows solo está disponible para [!INCLUDE[ssIS](../includes/ssis-md.md)].  
  
 **Conectar**  
 Se conecta al servidor seleccionado anteriormente.  
  
 **Opciones**  
 Haga clic aquí para modificar el cuadro de diálogo y ocultar las opciones adicionales de conexión al servidor, como recordar la contraseña.  
  
  
