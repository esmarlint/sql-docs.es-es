---
title: Método CopyRecord (ADO) | Documentos de Microsoft
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
- _Record::raw_CopyRecord
- _Record::CopyRecord
helpviewer_keywords:
- CopyRecord method [ADO]
ms.assetid: b9bcf272-3c74-479f-95dd-0229a32e98fc
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7da84b8922306f5aa7c51fa10fe023eec06a5414
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277314"
---
# <a name="copyrecord-method-ado"></a>Método CopyRecord (ADO)
Copia una entidad representada por un [registro](../../../ado/reference/ado-api/record-object-ado.md) a otra ubicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Record.CopyRecord (Source, Destination, UserName, Password, Options, Async)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *Source*  
 Opcional. A **cadena** valor que contiene la dirección URL que especifica la entidad que se va a copiar (por ejemplo, un archivo o directorio). Si *origen* se omite o se especifica una cadena vacía, el archivo o directorio representado por el actual [registro](../../../ado/reference/ado-api/record-object-ado.md) se va a copiar.  
  
 *Destino*  
 Opcional. A **cadena** valor que contiene la dirección URL que especifica la ubicación donde *origen* se va a copiar.  
  
 *UserName*  
 Opcional. A **cadena** valor que contiene el identificador de usuario que, si es necesario, autoriza el acceso a *destino*.  
  
 *Contraseña*  
 Opcional. A **cadena** valor que contiene la contraseña que comprueba si es necesario, *nombre de usuario*.  
  
 *Opciones*  
 Opcional. A [CopyRecordOptionsEnum](../../../ado/reference/ado-api/copyrecordoptionsenum.md) valor que tiene un valor predeterminado de **como**. Especifica el comportamiento de este método.  
  
 *Async*  
 Opcional. A **booleano** valor que, cuando **True**, especifica que esta operación debe ser asincrónica.  
  
## <a name="return-value"></a>Valor devuelto  
 A **cadena** valor que normalmente devuelve el valor de *destino*. Sin embargo, el valor devuelto exacto depende del proveedor.  
  
## <a name="remarks"></a>Notas  
 Los valores de *origen* y *destino* no debe ser idéntico; en caso contrario, se produce un error de tiempo de ejecución. Al menos uno de los nombres de servidor, ruta de acceso o recurso debe ser diferentes.  
  
 Todos los elementos secundarios (por ejemplo, en los subdirectorios) de *origen* son copian de forma recursiva, a menos que **adCopyNonRecursive** se especifica. En una operación recursiva, *destino* no debe ser un subdirectorio de *origen*; en caso contrario, la operación no se completará.  
  
 Este método produce un error si *destino* identifica una entidad existente (por ejemplo, un archivo o directorio), a menos que **adCopyOverWrite** se especifica.  
  
> [!IMPORTANT]
>  Use la **adCopyOverWrite** opción con prudencia. Por ejemplo, especificar esta opción para copiar un archivo en un directorio le *eliminar* el directorio y reemplazarlo con el archivo.  
  
> [!NOTE]
>  Direcciones URL que utilizan el esquema http, se invocarán automáticamente el [proveedor Microsoft OLE DB para Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Para obtener más información, consulte [absoluto y direcciones URL relativas](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)
