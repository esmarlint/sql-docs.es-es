---
title: "Editor de origen de SAP BW (página de salida de Error) | Documentos de Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.sapbwsource.erroroutput.f1
ms.assetid: b6e23b0c-949a-46d1-8424-4dc3d9035e79
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 00e596fd1c4b200e4f0fe1342fa56a9a3191f991
ms.contentlocale: es-es
ms.lasthandoff: 08/03/2017

---
# <a name="sap-bw-source-editor-error-output-page"></a>Editor de origen de SAP BW (página Salida de error)
  Utilice la página **Salida de error** del **Editor de origen de SAP BW** para seleccionar las opciones de control de errores y para establecer las propiedades en las columnas de salida de errores.  
  
 Para obtener más información sobre el componente de origen de SAP BW de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, vea [Origen de SAP BW](../../integration-services/data-flow/sap-bw-source.md).  
  
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
 Muestra las columnas externas (origen) que se han seleccionado en la página **Columnas** del cuadro de diálogo **Editor de origen de SAP BW** . Para obtener más información sobre este cuadro de diálogo, vea [Editor de origen de SAP BW &#40;página Columnas&#41;](../../integration-services/data-flow/sap-bw-source-editor-columns-page.md).  
  
 **Error**  
 Permite especificar lo que debe hacer el componente de origen de SAP BW cuando se produzca un error: omitir el error, redirigir la fila o hacer que el componente no funcione.  
  
 **Truncamiento**  
 Permite especificar lo que debe hacer el componente de origen de SAP BW cuando se produzca un truncamiento: omitir el error, redirigir la fila o hacer que el componente no funcione.  
  
 **Description**  
 Muestra la descripción del error.  
  
 **Establecer este valor en las celdas seleccionadas**  
 Permite especificar qué debe hacer el componente de origen de SAP BW en todas las celdas seleccionadas cuando se produce un error o un truncamiento: omitir el error, redirigir la fila o hacer que el componente no funcione.  
  
 **Aplicar**  
 Aplica la opción de control de errores a las celdas seleccionadas.  
  
## <a name="see-also"></a>Vea también  
 [Editor de origen de SAP BW &#40;página Administrador de conexiones&#41;](../../integration-services/data-flow/sap-bw-source-editor-connection-manager-page.md)   
 [Editor de origen de SAP BW &#40; Página columnas &#41;](../../integration-services/data-flow/sap-bw-source-editor-columns-page.md)   
 [Editor de origen de SAP BW &#40; Página avanzadas &#41;](../../integration-services/data-flow/sap-bw-source-editor-advanced-page.md)   
 [Ayuda F1 de Microsoft Connector 1.1 for SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  