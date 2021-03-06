---
title: Propiedad de dirección URL (RDS) | Documentos de Microsoft
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: sql
ms.prod_service: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- URL property [ADO]
ms.assetid: 8c56b233-1be8-442c-8d0e-a4c96465bc99
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cb07f83de6f08202b80da6a56bcf781510eb237f
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35288814"
---
# <a name="url-property-rds"></a>Propiedad de dirección URL (RDS)
Indica una cadena que contiene una dirección URL relativa o absoluta.  
  
 Puede establecer la **URL** propiedad en tiempo de diseño en el [DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) del objeto de etiquetas, o en tiempo de ejecución en código de scripting.  
  
> [!IMPORTANT]
>  A partir de Windows 8 y Windows Server 2012, componentes de servidor RDS ya no están incluidos en el sistema operativo Windows (consulte Windows 8 y [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) para obtener más detalles). Componentes de cliente RDS se quitará en una versión futura de Windows. Evite utilizar esta característica en nuevos trabajos de desarrollo y tenga previsto modificar las aplicaciones que actualmente la utilizan. Las aplicaciones que utilizan RDS deben migrar a [servicio de datos de WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Design time: <PARAM NAME="URL" VALUE="Server">  
Run time: DataControl.URL="Server"  
```  
  
#### <a name="parameters"></a>Parámetros  
 *Server*  
 A **cadena** valor que contiene una dirección URL válida.  
  
 *DataControl*  
 Una variable de objeto que representa un **DataControl** objeto.  
  
## <a name="remarks"></a>Notas  
 Normalmente, la dirección URL identifica un archivo de páginas Active Server (.asp) que puede producir y devolver un [conjunto de registros](../../../ado/reference/ado-api/recordset-object-ado.md). Por lo tanto, el usuario puede obtener un **Recordset** sin tener que invocar el lado servidor [DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) ni programar un objeto comercial personalizado.  
  
 Si el **URL** se ha establecido la propiedad, [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) enviará los cambios en la ubicación especificada por la dirección URL.  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de la propiedad de dirección URL (VBScript)](../../../ado/reference/rds-api/url-property-example-vbscript.md)


