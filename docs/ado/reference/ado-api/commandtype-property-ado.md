---
title: La propiedad CommandType (ADO) | Documentos de Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::CommandType
helpviewer_keywords:
- CommandType property [ADO]
ms.assetid: ca44809c-8647-48b6-a7fb-0be70a02f53e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 015ad28b7cffbb97c14c8ac9b5b287a36f14b2f9
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35276894"
---
# <a name="commandtype-property-ado"></a>Propiedad CommandType (ADO)
Indica el tipo de un [comando](../../../ado/reference/ado-api/command-object-ado.md) objeto.  
  
## <a name="settings-and-return-values"></a>Configuración y valores devueltos  
 Establece o devuelve uno o varios [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) valores.  
  
> [!NOTE]
>  No utilice la **CommandTypeEnum** valores de **adCmdFile** o **adCmdTableDirect** con **CommandType**. Estos valores sólo pueden utilizarse como opciones con el [abiertos](../../../ado/reference/ado-api/open-method-ado-recordset.md) y [Requery](../../../ado/reference/ado-api/requery-method.md) métodos de un [conjunto de registros](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="remarks"></a>Notas  
 Use la **CommandType** propiedad para optimizar la evaluación de la [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) propiedad.  
  
 Si el **CommandType** valor de la propiedad se establece en el valor predeterminado, **adCmdUnknown**, puede experimentar una disminución del rendimiento porque ADO debe realizar llamadas al proveedor para determinar si el  **CommandText** propiedad es una instrucción SQL, un procedimiento almacenado o un nombre de tabla. Si sabe qué tipo de comando que está utilizando, al establecer el **CommandType** propiedad indica a ADO que vaya directamente al código pertinente. Si el **CommandType** propiedad no coincide con el tipo de comando en el **CommandText** propiedad, se produce un error al llamar a la [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) método.  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Vea también  
 [ActiveConnection, CommandText, CommandTimeout, CommandType, tamaño y ejemplo de propiedades de dirección (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, tamaño y ejemplo de propiedades de dirección (VC ++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, tamaño y ejemplo de propiedades de dirección (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
