---
title: Propiedades de Analysis Server (pestaña servicio) | Documentos de Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8dbe4bc5-6aa9-48ee-857e-0b4ea764b9cb
caps.latest.revision: 18
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 081fd98155a51e888215bddc640c19847959f7ad
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36202837"
---
# <a name="analysis-server-properties-service-tab"></a>Propiedades de Analysis Server (pestaña Servicio)
  Este es el servicio [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Este servicio debe estar en ejecución para que [!INCLUDE[ssAS](../../includes/ssas-md.md)] funcione correctamente. Los valores de propiedades en color gris claro no se pueden modificar con esta aplicación.  
  
## <a name="options"></a>Opciones  
 **Ruta de acceso binaria**  
 Muestra la ubicación de los archivos de programa utilizados por el servicio.  
  
 **Control de errores**  
 1 indica `SERVICE_ERROR_NORMAL`. Si el servicio no se inicia al iniciar el equipo, el programa de inicio registra el error y muestra un cuadro de mensaje emergente pero continúa con la operación de inicio. Este valor no puede modificarse.  
  
 **Código de salida**  
 Si se produce un error, el número de error aparece en este cuadro. Utilice este número para solucionar errores buscando el número en [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base o informe del mismo al personal de soporte técnico.  
  
 **Host Name**  
 Muestra el nombre del equipo o clúster que ejecuta [!INCLUDE[ssAS](../../includes/ssas-md.md)].  
  
 **Nombre**  
 Indica el nombre para mostrar del servicio.  
  
 **Id. del proceso**  
 Muestra el número que usa [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows para realizar el seguimiento de los procesos de este programa.  
  
 **Tipo de servicio de SQL**  
 Muestra el tipo de servicio proporcionado a los procesos de llamada. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instala varios servicios.  
  
 **Modo de inicio**  
 Para este servicio se pueden configurar las siguientes opciones:  
  
-   Manual: el servicio no se inicia automáticamente al iniciar el equipo. Debe iniciarlo mediante el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] u otra herramienta.  
  
-   Automático: el servicio intenta iniciarse cuando se inicia el equipo.  
  
-   Deshabilitado: el servicio no se puede iniciar.  
  
 **State**  
 Indica si el servicio está en ejecución, detenido o deshabilitado.  
  
  