---
title: Conectar utilizando IPv6 | Documentos de Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Internet Protocol
- IPv4
- IPv6
ms.assetid: 2669098c-f5f1-43da-aec6-e91003ac89f6
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0479ad79093f2de1e9eb0fa6f9ff59db70ec4060
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "33068962"
---
# <a name="connecting-using-ipv6"></a>Conectar utilizando IPv6
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client son totalmente compatibles con el Protocolo de Internet versión 4 (IPv4) y con el Protocolo de Internet versión 6 (IPv6). Cuando Windows se configura con IPv6 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], los componentes reconocen automáticamente la existencia de IPv6. No es necesario realizar ninguna configuración especial de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 La compatibilidad incluye las siguientes cuestiones, aunque no se limita a ellas:  
  
-   [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] y los demás componentes de servidor pueden escuchar en las dos direcciones IPv4 y IPv6 simultáneamente. Cuando están presentes IPv4 e IPv6, puede utilizar el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para configurar [!INCLUDE[ssDE](../../includes/ssde-md.md)] de forma que escuche solo en las direcciones IPv4 o solo en las direcciones IPv6.  
  
-   Cuando se realiza una consulta al servicio Explorador de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que se ejecuta en un equipo que admite IPv4 e IPv6 en una dirección IPv4, responde con una dirección IPv4 y el primer puerto TCP de IPv4 de la lista. Cuando la consulta se realiza en una dirección IPv6, responde con una dirección IPv6 y el primer puerto TCP de IPv6 de la lista. Para evitar incoherencias, se recomienda que las escuchas de IPv4 e IPv6 se configuren de modo que escuchen en el mismo puerto.  
  
-   Herramientas como [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] y el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aceptan los formatos de IPv4 e IPv6 para direcciones IP. En la mayoría de los casos, la cadena de conexión no se tiene que modificar si se especifica \<*nombre_equipo*>\\<*nombre_instancia*> usando el nombre de host del servidor o un nombre de dominio completo (FQDN). Si el servidor tiene IPv4 e IPv6, su nombre de host o FQDN se resolverá en varias direcciones IP, incluidas al menos una dirección IPv4 y varias direcciones IPv6. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client intenta establecer conexiones usando estas direcciones IP en el orden en que las recibe de TCP/IP y usa la primera conexión que se realiza correctamente. Debido a que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client no puede predecir el orden, se debe considerar como orden aleatorio. Las direcciones IPv4 se intentan primero si ambas direcciones IPv4 e IPv6 están presentes. Esta lógica resulta transparente para los usuarios de ODBC, OLE DB y ADO.NET.  
  
    > [!NOTE]  
    >  Si [!INCLUDE[ssDE](../../includes/ssde-md.md)] no está escuchando en IPv4, el intento de conexión de IPv4 debe esperar el período de tiempo de espera antes de intentarlo con la dirección IPv6. Para evitar esto, conéctese directamente a la dirección IP IPv6 o configure un alias en el cliente con la dirección IPv6.  
  
## <a name="see-also"></a>Ver también  
 [Administrador de configuración de SQL Server](../../relational-databases/sql-server-configuration-manager.md)  
  
  
