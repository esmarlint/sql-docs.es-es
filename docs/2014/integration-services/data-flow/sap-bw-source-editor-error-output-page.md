---
title: Editor de origen de SAP BW (página Salida de error) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b6e23b0c-949a-46d1-8424-4dc3d9035e79
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a9406ca3d37cbfa8749a039cdf78bb7020467da5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37280211"
---
# <a name="sap-bw-source-editor-error-output-page"></a>Editor de origen de SAP BW (página Salida de error)
  Utilice la página **Salida de error** del **Editor de origen de SAP BW** para seleccionar las opciones de control de errores y para establecer las propiedades en las columnas de salida de errores.  
  
 Para obtener más información sobre el componente de origen de SAP BW de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, vea [Origen de SAP BW](sap-bw-source.md).  
  
> [!IMPORTANT]  
>  La documentación de Microsoft Connector 1.1 for SAP BW da por supuesto que se está familiarizado con el entorno SAP Netweaver BW. Para obtener más información acerca de SAP Netweaver BW, o sobre cómo configurar los objetos y los procesos de SAP Netweaver BW, vea la documentación de SAP.  
  
> [!IMPORTANT]  
>  La extracción de datos de SAP Netweaver BW requiere una licencia SAP adicional. Póngase en contacto con SAP para comprobar estos requisitos.  
  
 **Para abrir la página Salida de error**  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], abra el paquete de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] que contiene el origen de SAP BW.  
  
2.  En la pestaña **Flujo de datos** , haga doble clic en el origen de SAP BW.  
  
3.  En **Editor de origen de SAP BW**, haga clic en **Salida de error** para abrir la página **Salida de error** del editor.  
  
## <a name="options"></a>Opciones  
  
> [!NOTE]  
>  Si no conoce todos los valores necesarios para configurar el origen, puede que tenga que ponerse en contacto con el administrador de SAP.  
  
 **Entrada o salida**  
 Muestra el nombre del origen de datos.  
  
 **Columna**  
 Muestra las columnas externas (origen) que se han seleccionado en la página **Columnas** del cuadro de diálogo **Editor de origen de SAP BW** . Para obtener más información sobre este cuadro de diálogo, vea [SAP BW Source Editor &#40;Columns Page&#41;](sap-bw-source-editor-columns-page.md).  
  
 **Error**  
 Permite especificar lo que debe hacer el componente de origen de SAP BW cuando se produzca un error: omitir el error, redirigir la fila o hacer que el componente no funcione.  
  
 **Truncamiento**  
 Permite especificar lo que debe hacer el componente de origen de SAP BW cuando se produzca un truncamiento: omitir el error, redirigir la fila o hacer que el componente no funcione.  
  
 **Descripción**  
 Muestra la descripción del error.  
  
 **Establecer este valor en las celdas seleccionadas**  
 Permite especificar qué debe hacer el componente de origen de SAP BW en todas las celdas seleccionadas cuando se produce un error o un truncamiento: omitir el error, redirigir la fila o hacer que el componente no funcione.  
  
 **Aplicar**  
 Aplica la opción de control de errores a las celdas seleccionadas.  
  
## <a name="see-also"></a>Vea también  
 [Editor de origen de SAP BW &#40;página Administrador de conexiones&#41;](sap-bw-source-editor-connection-manager-page.md)   
 [Editor de origen de SAP BW &#40;página columnas&#41;](sap-bw-source-editor-columns-page.md)   
 [Editor de origen de SAP BW &#40;página Opciones avanzadas&#41;](sap-bw-source-editor-advanced-page.md)   
 [Ayuda F1 de Microsoft Connector 1.1 for SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
