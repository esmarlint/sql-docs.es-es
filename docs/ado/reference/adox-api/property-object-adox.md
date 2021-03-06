---
title: Objeto de propiedad (ADOX) | Documentos de Microsoft
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
helpviewer_keywords:
- Property object [ADOX]
ms.assetid: 6a56def6-dbe6-4ccc-a491-8d076889f019
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: db31ab407ee6268d14797ea3f50a9056c287f314
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35286880"
---
# <a name="property-object-adox"></a>Objeto de propiedad (ADOX)
Representa una característica de un objeto ADOX.  
  
## <a name="remarks"></a>Notas  
 Objetos ADOX tienen dos tipos de propiedades: integradas y dinámicas.  
  
 Las propiedades integradas son aquellas propiedades disponibles inmediatamente para cualquier objeto nuevo, utilizando la sintaxis MyObject.Property. No aparecen como objetos de propiedad en un objeto [colección de propiedades](../../../ado/reference/ado-api/properties-collection-ado.md), por lo que aunque se pueden cambiar sus valores, no se puede modificar sus características.  
  
 Propiedades dinámicas se definen por el proveedor de datos subyacente y aparecen en la colección de propiedades para el objeto ADOX apropiado.  Pueden hacer referencia a las propiedades dinámicas sólo a través de la colección mediante la sintaxis MyObject.Properties(0) o MyObject.Properties.  
  
 No se puede eliminar cualquier tipo de propiedad.  
  
 Un objeto dinámico Property tiene cuatro propiedades integradas de su propio:  
  
 El [nombre](../../../ado/reference/ado-api/name-property-ado.md) propiedad es una cadena que identifica la propiedad.  
  
 El [tipo](../../../ado/reference/ado-api/type-property-ado.md) propiedad es un entero que especifica el tipo de datos de propiedad.  
  
 El [valor](../../../ado/reference/ado-api/value-property-ado.md) propiedad es una variante que contiene el valor de propiedad. Valor es la propiedad predeterminada para un objeto de propiedad.  
  
 El [atributos](../../../ado/reference/ado-api/attributes-property-ado.md) propiedad es un valor long que indica características de la propiedad específica del proveedor.  
  
 Esta sección contiene el siguiente tema.  
  
-   [Propiedades, métodos y eventos del objeto Property (ADOX)](../../../ado/reference/adox-api/adox-property-object-properties-methods-and-events.md)
