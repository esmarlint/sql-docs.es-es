---
title: Instalación de Microsoft Connector for SAP BW | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3bfb9023-9597-4f59-9085-4b9057e7702e
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cf27a091e8fc6c9b6cc31cb27ff5993c6cf7c268
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2018
ms.locfileid: "35330909"
---
# <a name="installing-the-microsoft-connector-for-sap-bw"></a>Instalación de Microsoft Connector for SAP BW
  [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector for SAP BW para SQL Server 2016 es un componente de SQL Server 2016 Feature Pack. Para instalar Connector for SAP BW y su documentación, descargue y ejecute el instalador desde la [página web de SQL Server 2016 Feature Pack](http://go.microsoft.com/fwlink/?LinkId=746297).  

> [!IMPORTANT]
> Microsoft no prevé proporcionar una versión actualizada del conector de SAP BW. Microsoft no posee el código fuente de los componentes de SAP BW, que fueron desarrollados por terceros, por lo que no puede actualizarlos. Sopese la posibilidad de adquirir los componentes de conectividad de SAP más recientes de un socio de Microsoft ISV, como [Theobald Software](https://theobald-software.com/en/xtract-is-productinfo.html). Los socios de ISV de Microsoft han adaptado sus componentes de conectividad de SAP para SSIS para su instalación en Azure.

> [!IMPORTANT]  
>  La documentación de Microsoft Connector for SAP BW da por supuesto que se está familiarizado con el entorno SAP Netweaver BW. Para obtener más información acerca de SAP Netweaver BW, o sobre cómo configurar los objetos y los procesos de SAP Netweaver BW, vea la documentación de SAP.  
  
> [!IMPORTANT]  
>  La extracción de datos de SAP Netweaver BW requiere una licencia SAP adicional. Póngase en contacto con SAP para comprobar estos requisitos.  
  
## <a name="required-sap-files"></a>Archivos necesarios de SAP  
 Para usar [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector for SAP BW, no es necesario instalar el software SAP Front End (GUI de SAP) en el equipo local.  
  
 Sin embargo, debe copiar el archivo del conector .NET de SAP, librfc32.dll, en la subcarpeta del sistema de la carpeta Windows. (Normalmente, la ubicación de esta carpeta es **C:\Windows\system32**).  
  
## <a name="considerations-for-64-bit-computers"></a>Consideraciones para equipos de 64 bits  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector for SAP BW es totalmente compatible con la versión de 64 bits de [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows. En un equipo de 64 bits, [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector for SAP BW tiene los requisitos adicionales siguientes:  
  
-   Para ejecutar paquetes en modo de 64 bits en cualquier sistema operativo Windows de 64 bits, copie la versión de 64 bits del archivo de la GUI de SAP, librfc32.dll, a la carpeta **system32** de la carpeta Windows. (Normalmente, la ubicación de este archivo es **C:\Windows\system32**).  
  
-   Para ejecutar paquetes en modo de 32 bits en cualquier sistema operativo Windows de 64 bits, copie el archivo de la GUI de SAP, librfc32.dll, a la carpeta **SysWow64** de la carpeta Windows. (Normalmente, la ubicación de esta carpeta es **C:\Windows\SysWow64**).  
  
  
