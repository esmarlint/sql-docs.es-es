---
title: Buscar InfoObject | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7f4c132-a5ec-49d8-a964-45775432731f
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f25c00406ce375a2a7a380859ca0eaa5031b54d3
ms.contentlocale: es-es
ms.lasthandoff: 08/03/2017

---
# <a name="look-up-infoobject"></a>Buscar InfoObject
  Use el cuadro de diálogo **Buscar InfoObject** para buscar un InfoObject que se haya definido en el sistema de SAP Netweaver BW. Cuando aparezca la lista de InfoObjects disponibles, seleccione el InfoObject que desee y el destino de SAP BW rellenará las opciones asociadas a los valores necesarios.  
  
 El destino de SAP BW de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW usa el cuadro de diálogo **Buscar InfoObject** . Para obtener más información acerca del destino de SAP BW, vea [SAP BW Destination](../../integration-services/data-flow/sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  La documentación de Microsoft Connector 1.1 for SAP BW da por supuesto que se está familiarizado con el entorno SAP Netweaver BW. Para obtener más información acerca de SAP Netweaver BW, o sobre cómo configurar los objetos y los procesos de SAP Netweaver BW, vea la documentación de SAP.  
  
 **Para abrir el cuadro de diálogo Buscar InfoObject**  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], abra el paquete de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] que contiene el destino SAP BW.  
  
2.  En la pestaña **Flujo de datos** , haga doble clic en el destino de SAP BW.  
  
3.  En **Editor de destino SAP BW**, haga clic en **Administrador de conexiones** para abrir la página **Administrador de conexiones** del editor.  
  
4.  En la página **Administrador de conexiones** , en el cuadro del grupo **Crear objetos de SAP BW** , seleccione una de las siguientes opciones:  
  
    1.  Seleccione **InfoCube**. A continuación, haga clic en **Crear**. En el cuadro de diálogo **Crear InfoCube para datos de transacción** , haga clic en **Buscar** en la columna **IObject** para una de las filas de la lista. Cada fila representa una columna en el flujo de datos del paquete.  
  
    2.  Seleccione **InfoSource**. A continuación, haga clic en **Crear**. En el cuadro de diálogo **Crear InfoSource** , seleccione **Datos de transacción**. En el cuadro de diálogo **Crear InfoSource para datos de transacción** , haga clic en **Buscar** en la columna **IObject** para una de las filas de la lista. Cada fila representa una columna en el flujo de datos del paquete.  
  
    3.  Seleccione **InfoSource**. A continuación, haga clic en **Crear**. En el cuadro de diálogo **Crear InfoSource** , seleccione **Datos maestros**. En el cuadro de diálogo **Crear InfoSource para datos maestros** , haga clic en **Buscar**.  
  
 También puede abrir el cuadro de diálogo **Buscar InfoObject** si hace clic en **Agregar** en la sección **Atributos** del cuadro de diálogo **Crear nuevo InfoObject** .  
  
## <a name="lookup-options"></a>Opciones de búsqueda  
 En los cuadros de texto de los campos de búsqueda, puede filtrar los resultados mediante el carácter comodín de asterisco (*) o mediante una cadena parcial en combinación con el carácter comodín de asterisco. Sin embargo, si deja de un campo de búsqueda vacío, el proceso de búsqueda solamente se corresponderá con cadenas vacías en ese campo.  
  
 **Características**  
 Permite buscar InfoObjects que representan características.  
  
 **Unidades**  
 Permite buscar InfoObjects que representan unidades.  
  
 **Cifras clave**  
 Permite buscar InfoObjects que representan cifras clave.  
  
 **Características de tiempo**  
 Permite buscar InfoObjects que representan características de tiempo.  
  
 **Nombre**  
 Permite escribir el nombre del InfoObject que desea buscar o un nombre parcial con el carácter comodín de asterisco (*). O bien, use el carácter comodín de asterisco por sí solo para incluir todos los InfoObjects.  
  
 **Description**  
 Escriba la descripción o una descripción parcial con el carácter comodín de asterisco (*). O bien, use el carácter comodín de asterisco por sí solo para incluir todos los InfoObjects independientemente de la descripción.  
  
 **Buscar**  
 Busque InfoObjects coincidentes que se hayan definido en el sistema SAP Netweaver BW.  
  
## <a name="lookup-results"></a>Buscar resultados  
 Después de hacer clic en el botón Buscar, aparece una lista de InfoObjects del sistema SAP Netweaver BW en una tabla con los siguientes encabezados de columna.  
  
 **InfoObject**  
 Permite mostrar el nombre del InfoObject que se haya definido en el sistema de SAP Netweaver BW.  
  
 **Texto (corto)**  
 Permite mostrar el texto breve que está asociado al InfoObject.  
  
 Cuando aparezca la lista de InfoObjects disponibles, seleccione el InfoObject que desee y el destino rellenará las opciones asociadas a los valores necesarios.  
  
## <a name="see-also"></a>Vea también  
 [Crear InfoCube para datos de transacción](../../integration-services/data-flow/create-infocube-for-transaction-data.md)   
 [Crear InfoSource](../../integration-services/data-flow/create-infosource.md)   
 [Crear InfoSource para datos de transacción](../../integration-services/data-flow/create-infosource-for-transaction-data.md)   
 [Crear InfoSource para datos maestros](../../integration-services/data-flow/create-infosource-for-master-data.md)   
 [Crear nuevo InfoObject](../../integration-services/data-flow/create-new-infoobject.md)   
 [Editor de destino de SAP BW &#40;Página Administrador de conexiones&#41;](../../integration-services/data-flow/sap-bw-destination-editor-connection-manager-page.md)   
 [Ayuda F1 de Microsoft Connector 1.1 for SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  