---
title: Propiedades de Agente SQL Server (página General) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.general.f1
ms.assetid: b51601e9-5454-43c6-bb5e-24eb2ff043c8
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6a081d0648c322c11b3761fcd06dca43d629785f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37185862"
---
# <a name="sql-server-agent-properties-general-page"></a>Propiedades de Agente SQL Server (página General)
  Utilice esta página para ver y modificar las propiedades generales del servicio del Agente [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="options"></a>Opciones  
 **Estado del servicio**  
 Muestra el estado actual del servicio del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Reiniciar SQL Server si se detiene inesperadamente**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] El Agente reinicia [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se detiene de forma inesperada.  
  
 **Reiniciar el Agente SQL Server automáticamente si se detiene inesperadamente**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] reinicia el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se detiene de forma inesperada.  
  
 **Nombre de archivo**  
 Especifica el nombre de archivo del registro de errores.  
  
 **...**  
 Permite buscar el archivo del registro de errores.  
  
 **Incluir mensajes de seguimiento de ejecución**  
 Incluye mensajes de seguimiento de ejecución en el registro de errores. Los mensajes de seguimiento proporcionan información detallada sobre la operación del Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Por tanto, el archivo de registro requiere más espacio en disco cuando se selecciona esta opción. Solo se debe seleccionar si se intenta solucionar un problema que puede estar relacionado con el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Escribir archivo OEM**  
 Escribe el archivo de registro de errores como un archivo no Unicode. De esta forma, se reduce el espacio en disco que utiliza el archivo de registro. Sin embargo, si se habilita esta opción, puede resultar más difícil leer los mensajes que incluyen datos Unicode.  
  
 **Destinatario de NET SEND**  
 Escribe el nombre de un operador que recibirá una notificación mediante NET SEND de los mensajes que el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] escribe en el archivo de registro.  
  
## <a name="see-also"></a>Vea también  
 [Operadores](operators.md)   
 [Registro de errores del Agente SQL Server](sql-server-agent-error-log.md)  
  
  
