---
title: Origen OData| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.ODATASOURCE.F1
ms.assetid: cc9003c9-638e-432b-867e-e949d50cec90
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: af382eb9398dc2c8d790f8af1cf72fc89c572959
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37250355"
---
# <a name="odata-source"></a>Origen OData
  Use el componente de origen OData en un paquete SSIS para consumir datos de servicios de Open Data Protocol (OData). El componente admite los protocolos OData v2 y v3, así como los formatos de datos ATOM y JSON.  
  
> [!NOTE]  
>  El origen OData se puede usar para leer listas de SharePoint. Para ver todas las listas en el servidor de SharePoint, use la siguiente dirección URL: http://\<server > / listdata.svc. Para obtener más información sobre las convenciones de direcciones URL de SharePoint, vea [Interfaz de REST de SharePoint Foundation](http://msdn.microsoft.com/library/ff521587.aspx).  
  
## <a name="odata-format"></a>Formato OData  
 La mayoría de los servicios OData devuelven resultados en varios formatos. Puede especificar el formato del conjunto de resultados mediante la opción de consulta $format. Los formatos como JSON y JSON Light son más eficaces que ATOM/XML, y pueden conseguir mejor rendimiento cuando se transfieren grandes cantidades de datos. En la tabla siguiente se muestran resultados de pruebas de ejemplo. Como puede ver, hubo una mejora del rendimiento del 30-53 % al cambiar de ATOM a JSON y del 67 % cuando se cambió de ATOM al nuevo formato JSON Light (disponible en WCF Data Services 5.1).  
  
|||||  
|-|-|-|-|  
|Filas|ATOM|JSON|JSON (Light)|  
|10000|113 segundos|74 segundos|68 segundos|  
|1000000|1110 segundos|853 segundos|665 segundos|  
  
> [!NOTE]  
>  El origen OData de SSIS usa ODataLib 5.5.0 para analizar las fuentes OData y puede leer todos los formatos admitidos por esta biblioteca.  
  
## <a name="in-this-section"></a>En esta sección  
  
-   [Instalar y desinstalar el Componente de origen OData](../install-and-uninstall-odata-source-component.md)  
  
-   [Tutorial: Usar el origen OData &#91;SSIS&#93;](tutorial-using-the-odata-source.md)  
  
-   [Modificar una consulta de origen OData en tiempo de ejecución](modify-odata-source-query-at-runtime.md)  
  
-   [Editor de origen OData &#40;página Conexión&#41;](../odata-source-editor-connection-page.md)  
  
-   [Editor de origen OData &#40;página Columnas&#41;](../odata-source-editor-columns-page.md)  
  
-   [Editor de origen OData &#40;página Salida de error&#41;](../odata-source-editor-error-output-page.md)  
  
-   [Propiedades del origen OData](odata-source-properties.md)  
  
## <a name="see-also"></a>Vea también  
 [Administrador de conexiones OData](../connection-manager/odata-connection-manager.md)  
  
  
