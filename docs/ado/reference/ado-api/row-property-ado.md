---
title: Fila (propiedad, ADO) | Documentos de Microsoft
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
- ADORecordConstruction::PutRow
- ADORecordConstruction::GetRow
- ADORecordConstruction::get_Row
- ADORecordConstruction::Row
- ADORecordConstruction::put_Row
helpviewer_keywords:
- Row property [ADO]
ms.assetid: 21019d89-2dd1-4a26-ac6f-384b81d66949
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4de19beeb853abb0a6bdc4d517332a812fa43c0e
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35281324"
---
# <a name="row-property-ado"></a>Propiedad de las filas (ADO)
Obtiene o establece OLE DB **fila** objeto desde o en un [Interfaz ADORecordConstruction](../../../ado/reference/ado-api/adorecordconstruction-interface.md) objeto. Cuando usas **put_Row** para establecer un **fila** objeto, una fila se convierte en ADO **registro** objeto.  
  
## <a name="readwritesyntax"></a>Lectura/escritura. Sintaxis  
  
```  
HRESULT get_Row([out, retval] IUnknown** ppRow);  
HRESULT put_Row([in] IUnknown* pRow);  
```  
  
## <a name="parameters"></a>Parámetros  
 *ppRow*  
 Puntero a OLE DB **fila** objeto.  
  
 *PRow*  
 OLE DB **fila** objeto.  
  
## <a name="return-values"></a>Valores devueltos  
 Este método de propiedad devuelve los valores HRESULT estándar, incluidos S_OK y E_FAIL.  
  
## <a name="applies-to"></a>Se aplica a  
 [Interfaz ADORecordConstruction](../../../ado/reference/ado-api/adorecordconstruction-interface.md)
