---
title: Elemento de tabla de esquema (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Table element [DTA]
ms.assetid: a59e8319-05d1-47f3-af39-7d970ab8e7dc
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f58288d90c1a3158f4757856b51b7374ee07f167
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37187762"
---
# <a name="table-element-for-schema-dta"></a>Table (DTA, elemento de Schema)
  Especifica la tabla que se va a optimizar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
<Schema>  
...code removed here...  
    <Table>...</Table>  
```  
  
## <a name="element-attributes"></a>Atributos del elemento  
  
|Attribute|Descripción|  
|---------------|-----------------|  
|`NumberOfRows`|Opcional. Entero que permite simular tablas de diferentes tamaños.|  
  
## <a name="element-characteristics"></a>Características del elemento  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|**Tipo y longitud de los datos**|**string**, entre 1 y 255 caracteres.|  
|**Valor predeterminado**|Ninguno.|  
|**Repetición**|Opcional. Presenta tantas tablas como sea necesario para la carga de trabajo.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elementos|  
|------------------|--------------|  
|**Elemento primario**|[Elemento de esquema de base de datos &#40;DTA&#41;](schema-element-for-database-dta.md)|  
|**Elementos secundarios**|[Nombre de elemento de tabla &#40;DTA&#41;](name-element-for-table-dta.md)|  
  
## <a name="remarks"></a>Notas  
 Si no se especifica un elemento `Table`, el Asistente para la optimización de motor de base de datos asumirá que todas las tablas de la base de datos especificada se pueden optimizar.  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo de uso, vea [Server &#40;DTA, elemento&#41;](server-element-dta.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia del archivo de entrada XML &#40;Asistente para la optimización de motor de base de datos&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
