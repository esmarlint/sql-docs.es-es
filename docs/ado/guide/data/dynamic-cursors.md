---
title: Los cursores dinámicos | Documentos de Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], dynamic
- dynamic cursors [ADO]
ms.assetid: 00460f30-8cf7-494e-82df-41012f40ae51
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ab212d978f38a9e80435d0fae81a6664a8839b56
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35270414"
---
# <a name="dynamic-cursors"></a>Cursores dinámicos
Los cursores dinámicos detectan todos los cambios realizados en las filas del conjunto de resultados, independientemente de si se producen los cambios desde dentro del cursor o por otros usuarios fuera del cursor. Todos los insert, update y las instrucciones delete realizadas por todos los usuarios son visibles a través del cursor. El cursor dinámico puede detectar los cambios realizados a las filas, el orden y los valores del conjunto de resultados una vez que se abre el cursor. Las actualizaciones realizadas fuera del cursor no son visibles hasta que se confirman (a menos que el nivel de aislamiento de transacción de cursor se establece en "sin confirmar").  
  
 Por ejemplo, suponga que un cursor dinámico recupera dos filas y otra aplicación y, a continuación, actualiza una de esas filas y elimina la otra. Si el cursor dinámico, a continuación, captura las filas, no encontrará la fila eliminada, pero se mostrará a los nuevos valores de la fila actualizada.  
  
 El cursor dinámico es una buena opción si la aplicación debe detectar todas las actualizaciones simultáneas realizadas por otros usuarios. Utilice la **adOpenDynamic CursorTypeEnum** para indicar que desea utilizar un cursor dinámico en ADO.  
  
## <a name="see-also"></a>Vea también  
 [Cursores de solo avance](../../../ado/guide/data/forward-only-cursors.md)   
 [Cursores estáticos](../../../ado/guide/data/static-cursors.md)   
 [Cursores KEYSET](../../../ado/guide/data/keyset-cursors.md)
