---
title: Propiedad OriginalValue (ADO) | Documentos de Microsoft
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
- Field20::OriginalValue
helpviewer_keywords:
- OriginalValue property [ADO]
ms.assetid: 6e33c6ec-14d9-4b1d-ba9b-cb99862e7bac
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5c77c1badaa812efb13767b8f30afa37341bc07c
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35280034"
---
# <a name="originalvalue-property-ado"></a>Propiedad OriginalValue (ADO)
Indica el valor de un [campo](../../../ado/reference/ado-api/field-object.md) que existía en el registro antes de que se realizaron los cambios.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un **Variant** valor que representa el valor de un campo antes de realizar cualquier cambio.  
  
## <a name="remarks"></a>Notas  
 Use la **OriginalValue** propiedad para devolver el valor del campo original de un campo del registro actual.  
  
 En *modo de actualización inmediata* (en el que el proveedor escribe los cambios en el origen de datos subyacente después de llamar a la [actualizar](../../../ado/reference/ado-api/update-method.md) método), el **OriginalValue** devuelve de propiedad el valor del campo que existían antes de cualquier cambio (es decir, desde la última **actualización** llamada al método). Este es el mismo valor que el [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) método se usa para reemplazar la [valor](../../../ado/reference/ado-api/value-property-ado.md) propiedad.  
  
 En *modo de actualización por lotes* (en el que el proveedor almacena varios cambios en caché y los escribe en el origen de datos subyacente sólo cuando se llama a la [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) método), el **OriginalValue** propiedad devuelve el valor del campo que existían antes de cualquier cambio (es decir, desde la última **UpdateBatch** llamada al método). Este es el mismo valor que el [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) método se usa para reemplazar la **valor** propiedad. Cuando esta propiedad se usa con la [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md) propiedad, es posible solucionar conflictos que surgen de las actualizaciones por lotes.  
  
## <a name="record"></a>Grabar  
 Para [registro](../../../ado/reference/ado-api/record-object-ado.md) objetos, el **OriginalValue** propiedad estará vacía para los campos agregados antes de [actualización](../../../ado/reference/ado-api/update-method.md) se llama.  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo OriginalValue y UnderlyingValue propiedades (VB)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [Ejemplo OriginalValue y UnderlyingValue propiedades (VC ++)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [Propiedad UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md)
