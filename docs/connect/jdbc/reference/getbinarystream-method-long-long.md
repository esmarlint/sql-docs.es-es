---
title: Método (long, long) getBinaryStream | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 30bc8882-04b4-4efd-95e4-7d3a2a8c1d47
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8edc7822d8f091bb2cecbac4456beeadc11506d7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32830200"
---
# <a name="getbinarystream-method-long-long"></a>Método getBinaryStream (long, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Devuelve un objeto del flujo de entrada que contiene un valor BLOB parcial, para ello utiliza la posición de inicio y la longitud especificadas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public java.io.InputStream getBinaryStream(long pos, long length)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *punto de venta*  
  
 El desplazamiento para el primer byte del valor parcial que se va a recuperar.  
  
 *length*  
  
 La longitud en bytes del valor parcial que se va a recuperar.  
  
## <a name="return-value"></a>Valor devuelto  
 Un flujo de entrada que contiene los datos BLOB.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método getBinaryStream especificado por el método getBinaryStream en la interfaz java.sql.Blob.  
  
## <a name="see-also"></a>Vea también  
 [Métodos SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [Miembros de SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [Clase SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
