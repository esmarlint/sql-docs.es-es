---
title: La propiedad CursorLocation (ADO) | Documentos de Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Connection15::CursorLocation
- Recordset15::CursorLocation
helpviewer_keywords:
- CursorLocation property [ADO]
ms.assetid: 39c8d86e-7ee9-4182-be5e-aad5ce952f84
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6679a7a8a83f954039587776e5e668bd5ed05365
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="cursorlocation-property-ado"></a>Propiedad CursorLocation (ADO)
Indica la ubicación del servicio de cursor.  
  
## <a name="settings-and-return-values"></a>Configuración y valores devueltos  
 Establece o devuelve un **largo** valor que se puede establecer en uno de los [CursorLocationEnum](../../../ado/reference/ado-api/cursorlocationenum.md) valores.  
  
## <a name="remarks"></a>Comentarios  
 Esta propiedad le permite elegir entre varias bibliotecas de cursores accesibles para el proveedor. Por lo general, puede elegir entre utilizar una biblioteca de cursores de cliente o una que se encuentra en el servidor.  
  
 Valor de esta propiedad afecta a las conexiones establecidas solo después de que se ha establecido la propiedad. Cambiar el **CursorLocation** propiedad no tiene ningún efecto en las conexiones existentes.  
  
 Los cursores devueltos por el [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) método heredarán este ajuste. **Conjunto de registros** objetos heredarán automáticamente este valor de sus conexiones asociadas.  
  
 Esta propiedad es de lectura/escritura en un [conexión](../../../ado/reference/ado-api/connection-object-ado.md) o un cerrado [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)y de solo lectura en un formato de archivo **conjunto de registros**.  
  
> [!NOTE]
>  **Uso de servicios de datos remoto** cuando se utiliza en un lado del cliente **Recordset** o **conexión** objeto, el **CursorLocation** propiedad solo puede establecerse en **adUseClient**.  
  
## <a name="applies-to"></a>Se aplica a  
  
|||  
|-|-|  
|[Objeto de conexión (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Objeto de conjunto de registros (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>Vea también  
 [Apéndice A: proveedores](../../../ado/guide/appendixes/appendix-a-providers.md)