---
title: Configurar un servidor para que escuche en una canalización alternativa (Administrador de configuración de SQL Server) | Documentos de Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Named Pipes [SQL Server], configuring
- listening [SQL Server], pipes
- pipes [SQL Server], alternate
- alternate pipes [SQL Server]
ms.assetid: 914f7491-e2be-4b0d-b3aa-fe5409cdbafa
caps.latest.revision: 27
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 495f91088627399e207adaecf9a5d0dc27a02944
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36198739"
---
# <a name="configure-a-server-to-listen-on-an-alternate-pipe-sql-server-configuration-manager"></a>Configurar un servidor para escuchar en una canalización alternativa (Administrador de configuración de SQL Server)
  En este tema se describe cómo configurar un servidor para que escuche en una canalización alternativa en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante el Administrador de configuración de SQL Server. De forma predeterminada, la instancia predeterminada de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] escucha en la canalización con nombre \\\\.\pipe\sql\query. Las instancias con nombre de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] y [!INCLUDE[ssEW](../../includes/ssew-md.md)] escuchan en otras canalizaciones.  
  
 Hay tres formas de conectarse a una canalización con nombre específica con una aplicación cliente:  
  
-   Ejecutar el servicio Explorador de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en el servidor.  
  
-   Crear un alias en el cliente, especificando la canalización con nombre.  
  
-   Programar el cliente para conectarse mediante una cadena de conexión personalizada.  
  
##  <a name="SSMSProcedure"></a> Usar el Administrador de configuración de SQL Server  
  
#### <a name="to-configure-the-named-pipe-used-by-the-sql-server-database-engine"></a>Para configurar la canalización con nombre utilizada por el Motor de base de datos de SQL Server  
  
1.  En el panel de la consola del Administrador de configuración de SQL Server, expanda **Configuración de red de SQL Server** y, luego, haga clic en **Protocolos de** *\<nombre de instancia>*.  
  
2.  En el panel de detalles, haga clic con el botón derecho en **Canalizaciones con nombre**y, después, haga clic en **Propiedades**.  
  
3.  En la pestaña **Protocolo** , en el cuadro **Nombre de canalización** , escriba la canalización en la que desea que escuche [!INCLUDE[ssDE](../../includes/ssde-md.md)] y, a continuación, haga clic en **Aceptar**.  
  
4.  En el panel de la consola, haga clic en **Servicios de SQL Server**.  
  
5.  En el panel de detalles, haga clic con el botón derecho en **SQL Server (**\<nombre de instancia>**)** y, después, haga clic en **Reiniciar** para detener y reiniciar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Cuando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] está escuchando en una canalización alternativa, hay tres formas de conectarse a una canalización con nombre específica con una aplicación cliente:  
  
-   Ejecutar el servicio Explorador de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en el servidor.  
  
-   Crear un alias en el cliente, especificando la canalización con nombre.  
  
-   Programar el cliente para conectarse mediante una cadena de conexión personalizada.  
  
## <a name="see-also"></a>Vea también  
 [Crear o eliminar un alias de servidor para que lo utilice un cliente &#40;Administrador de configuración de SQL Server&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md)   
 [Configuración de red del servidor](server-network-configuration.md)  
  
  