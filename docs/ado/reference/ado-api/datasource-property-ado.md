---
title: Propiedad de origen de datos (ADO) | Documentos de Microsoft
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
- Recordset20::DataSource
helpviewer_keywords:
- DataSource property [ADO]
ms.assetid: 300a702a-3544-48c5-b759-83b511fe97e0
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5fa4df4252d9970d4ec8ec36500dc5782466c675
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277474"
---
# <a name="datasource-property-ado"></a>Propiedad de origen de datos (ADO)
Indica un objeto que contiene datos que se va a representar como un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objeto.  
  
## <a name="remarks"></a>Notas  
 Esta propiedad se utiliza para crear controles enlazados a datos con el entorno de datos. El entorno de datos mantiene colecciones de datos (orígenes de datos) que contiene objetos con nombre (miembros de datos) que se representarán como un **Recordset** objeto *.*  
  
 El [DataMember](../../../ado/reference/ado-api/datamember-property.md) y **DataSource** propiedades deben utilizarse conjuntamente.  
  
 El objeto al que hace referencia debe implementar la **IDataSource** de interfaz y debe contener un **IRowset** interfaz.  
  
## <a name="usage"></a>Uso  
  
```  
Dim rs as New ADODB.Recordset  
rs.DataMember = "Command"     'Name of the rowset to bind to.  
Set rs.DataSource = myDE      'Name of the object containing an IRowset.  
```  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto de conjunto de registros (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vea también  
 [Propiedad DataMember](../../../ado/reference/ado-api/datamember-property.md)
