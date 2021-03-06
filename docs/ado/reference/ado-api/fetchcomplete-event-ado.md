---
title: Evento FetchComplete (ADO) | Documentos de Microsoft
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
- Recordset::ExecuteComplete
- ExecuteComplete
helpviewer_keywords:
- FetchComplete event [ADO]
ms.assetid: a28d3858-566c-468d-b070-d1de4339fbea
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a6d8024a302d76ad01aa3044c675fc2a42c7c7ed
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35278154"
---
# <a name="fetchcomplete-event-ado"></a>Evento FetchComplete (ADO)
El **FetchComplete** eventos se llama después de recuperar todos los registros en una operación asincrónica prolongada en el [conjunto de registros](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
FetchComplete pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parámetros  
 *pError*  
 Un [Error](../../../ado/reference/ado-api/error-object.md) objeto. Describe el error que se ha producido si el valor de **adStatus** es **adStatusErrorsOccurred**; en caso contrario, no se establece.  
  
 *adStatus*  
 Un [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) valor de estado. Cuando se llama a este evento, este parámetro se establece en **adStatusOK** si la operación que provocó el evento se realizó correctamente, o para **adStatusErrorsOccurred** si la operación produce un error.  
  
 Antes de que se devuelve este evento, establezca este parámetro en **adStatusUnwantedEvent** para impedir notificaciones posteriores.  
  
 *pRecordset*  
 A **Recordset** objeto. El objeto para el que se recuperaron los registros.  
  
## <a name="remarks"></a>Notas  
 Usar **FetchComplete** con Microsoft Visual Basic, Visual Basic 6.0 o posterior es necesario.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de modelo de eventos de ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Conexión ADO y los eventos de conjunto de registros](../../../ado/guide/data/ado-event-handler-summary.md)
