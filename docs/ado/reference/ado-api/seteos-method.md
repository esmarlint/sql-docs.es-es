---
title: Método SetEOS | Documentos de Microsoft
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
- _Stream::raw_SetEOS
- _Stream::SetEOS
helpviewer_keywords:
- SetEOS method [ADO]
ms.assetid: 707c18ca-6a56-4970-bbd6-ae1fb86a0b8a
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8821b58e5e111ad879c34f0d3d8177404945a72f
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35281614"
---
# <a name="seteos-method"></a>SetEOS (método)
Establece la posición que es el final de la secuencia.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Stream.SetEOS  
```  
  
## <a name="remarks"></a>Notas  
 **SetEOS** actualiza el valor de la [sobrecargas eléctricas](../../../ado/reference/ado-api/eos-property.md) propiedad realizando actual [posición](../../../ado/reference/ado-api/position-property-ado.md) el final de la secuencia. Se truncan los bytes o caracteres que siguen a la posición actual.  
  
 Dado que [escribir](../../../ado/reference/ado-api/write-method.md), [WriteText](../../../ado/reference/ado-api/writetext-method.md), y [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md) no se truncan los valores adicionales existente **flujo** objetos, se pueden truncar estos bytes o caracteres estableciendo la nueva posición final de secuencia con **SetEOS**.  
  
> [!CAUTION]
>  Si establece **sobrecargas eléctricas** a una posición anterior al final real de la secuencia, se perderán todos los datos después de la nueva **sobrecargas eléctricas** posición.  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto de secuencia (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
