---
title: Función Min (Generador de informes y SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: aa1ee96f-9fc4-4775-b9d4-c6187dc37e27
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: e63241cfc502fc5b052af3b726b3f3b302a2587f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37266661"
---
# <a name="min-function-report-builder-and-ssrs"></a>Función Min (Generador de informes y SSRS)
  Devuelve el valor mínimo de todos los valores numéricos no NULL especificados por la expresión, en el contexto del ámbito especificado.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Min(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *expression*  
 (`Variant`) Expresión en la que se va a realizar la agregación.  
  
 *ámbito*  
 (`String`) Opcional. Nombre de un conjunto de datos, un grupo o una región de datos que contiene los elementos de informe a los que se va a aplicar la función de agregado. Si no se especifica el parámetro *scope* , se usa el ámbito actual.  
  
 *recursivos*  
 (**Tipo enumerado**) Opcional. `Simple` (valor predeterminado) o `RdlRecursive`. Especifica si se debe realizar la agregación de forma recursiva.  
  
## <a name="return-type"></a>Tipo devuelto  
 Lo determina el tipo al que pertenece la expresión.  
  
## <a name="remarks"></a>Notas  
 El conjunto de datos especificado en la expresión debe tener el mismo tipo de datos. Para convertir datos de varios tipos de datos numéricos al mismo tipo de datos, use funciones de conversión como `CInt`, `CDbl` o `CDec`. Para obtener más información, vea [Funciones de conversión de tipos](http://go.microsoft.com/fwlink/?LinkId=96142).  
  
 El valor de *scope* debe ser una constante de cadena y no puede ser una expresión. Para los agregados exteriores o los que no especifican a otros agregados, *scope* debe hacer referencia al ámbito actual o a un ámbito de contenido. Para los agregados de agregados, los agregados anidados pueden especificar un ámbito secundario.  
  
 *Expression* puede contener las llamadas a las funciones de agregados anidados con las siguientes excepciones y condiciones:  
  
-   *Scope* , para los agregados anidados, debe ser igual que el ámbito del agregado exterior, o ser contenido por él. Para todos los ámbitos distintos de la expresión, un ámbito debe estar en una relación secundaria con respecto a todos los otros ámbitos.  
  
-   *Scope* , para los agregados anidados, no puede ser el nombre de un conjunto de datos.  
  
-   *Expresión* no puede contener `First`, `Last`, `Previous`, o `RunningValue` funciones.  
  
-   *Expression* no debe contener a los agregados anidados que especifican *recursive*.  
  
 Para más información, vea [Funciones del generador de informes - referencia de funciones de agregado &#40;Generador de informes y SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) y [Ámbito de expresión para los totales, agregados y colecciones integradas &#40;Generador de informes y SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Para más información sobre los agregados recursivos, vea [Crear un grupo de jerarquía recursiva &#40;Generador de informes y SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo de código proporciona el total más bajo del ámbito actual.  
  
```  
=Min(Fields!OrderTotal.Value)  
```  
  
## <a name="see-also"></a>Vea también  
 [Usar expresiones en informes &#40;generador de informes y SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Ejemplos de expresiones &#40;Generador de informes y SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Tipos de datos en expresiones &#40;Generador de informes y SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Ámbito de expresión para totales, agregados y colecciones integradas &#40;generador de informes y SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
