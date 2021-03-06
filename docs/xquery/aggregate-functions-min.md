---
title: Función Min (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- fn:min function
- min function [XQuery]
ms.assetid: db0b7d94-3fa6-488f-96d6-6a9a7d6eda23
caps.latest.revision: 28
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8e5ce4f5ac16b337db62633d8b0a72ca98c708a5
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38051713"
---
# <a name="aggregate-functions---min"></a>Funciones de agregado: min
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Devuelve de una secuencia de valores atómicos, *$arg*, el único elemento cuyo valor es menor que el de todos los demás.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
fn:min($arg as xdt:anyAtomicType*) as xdt:anyAtomicType?  
```  
  
## <a name="arguments"></a>Argumentos  
 *$arg*  
 Secuencia de elementos de los cuales se devolverá el valor mínimo.  
  
## <a name="remarks"></a>Notas  
 Todos los tipos de valores atomizados que se pasan a **min()** deben ser subtipos del mismo tipo base. Tipos base aceptados son los tipos que admiten la **gt** operación. Entre estos tipos se incluyen los tres tipos base numéricos integrados, los tipos base de fecha y hora, xs:string, xs:boolean y xdt:untypedAtomic. Los valores del tipo xdt:untypedAtomic se convierten a xs:double. Si es una combinación de estos tipos, o si se pasan otros valores de otros tipos, se produce un error estático.  
  
 El resultado de **min()** recibe el tipo base de los tipos pasados, como xs: double en el caso de xdt: untypedAtomic. Si la entrada se encuentra estáticamente vacía, se considera implícitamente vacía y se devuelve un error estático.  
  
 El **min()** función devuelve un valor de la secuencia que es menor que cualquier otro en la secuencia de entrada. En el caso de los valores xs:string, se utiliza la intercalación de puntos de código Unicode predeterminada. Si no se puede convertir un valor xdt: untypedAtomic a xs: Double, el valor se omite en la secuencia de entrada *$arg*. Si la entrada es una secuencia vacía calculada dinámicamente, se devolverá la secuencia vacía.  
  
## <a name="examples"></a>Ejemplos  
 En este tema se proporciona ejemplos de XQuery con instancias XML almacenadas en varias **xml** columnas de tipo en la base de datos AdventureWorks.  
  
### <a name="a-using-the-min-xquery-function-to-find-the-work-center-location-that-has-the-fewest-labor-hours"></a>A. Usar la función min() de XQuery para encontrar la ubicación de centro de trabajo con el menor número de horas de trabajo  
 La consulta siguiente recupera todas las ubicaciones de centro de trabajo del proceso de fabricación de un modelo de producto (ProductModelID=7) con el menor número de horas de trabajo (LaborHours). Por lo general, se devuelve una sola ubicación, tal como se muestra a continuación. Si existen varias ubicaciones con el mismo número mínimo de horas de trabajo, se devolverán todas.  
  
```  
select ProductModelID, Name, Instructions.query('  
  declare namespace AWMI=  
    "http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  for   $Location in /AWMI:root/AWMI:Location  
  where $Location/@LaborHours =  
          min( /AWMI:root/AWMI:Location/@LaborHours )  
return  
  <Location WCID=     "{ $Location/@LocationID }"   
              LaborHrs= "{ $Location/@LaborHours }" />  
  ') as Result   
FROM  Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Observe lo siguiente en la consulta anterior:  
  
-   El **espacio de nombres** palabra clave en el prólogo de XQuery define un prefijo de espacio de nombres. A continuación, el prefijo se utiliza en el cuerpo de XQuery.  
  
 El cuerpo de XQuery construye el XML que tiene un \<ubicación > elemento con WCID y **LaborHrs** atributos.  
  
-   Esta consulta también recupera los valores de ProductModelID y de nombres.  
  
 El resultado es el siguiente:  
  
```  
ProductModelID   Name              Result  
---------------  ----------------  ---------------------------------  
7                HL Touring Frame  <Location WCID="45" LaborHrs="0.5"/>   
```  
  
## <a name="implementation-limitations"></a>Limitaciones de la implementación  
 Éstas son las limitaciones:  
  
-   El **min()** función asigna todos los enteros a xs: decimal.  
  
-   El **min()** no se admite la función con valores de tipo xs: Duration.  
  
-   No se admiten las secuencias que mezclan tipos en límites de tipo base.  
  
-   No se admite la opción sintáctica que proporciona una intercalación.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de XQuery con el tipo de datos xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
