---
title: Comando de etiqueta de DELETE | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- DELETE TAG command [ODBC]
ms.assetid: 4f4e1362-a5f3-4b15-8a3c-d4e96605f221
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 28ee28e069ac0e1ef8e22ca2b118e273236e269c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="delete-tag-command"></a>Eliminar etiqueta, comando
Quita una etiqueta o etiquetas de un archivo de índice compuesto (.cdx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
DELETE TAG TagName1 [OF CDXFileName1]  
   [, TagName2 [OF CDXFileName2]] ...  
  Or   
DELETE TAG ALL [OF CDXFileName]  
```  
  
## <a name="arguments"></a>Argumentos  
 *TagName1*OF *CDXFileName1*[, *TagName2*[OF *CDXFileName2*]]...  
 Especifica una etiqueta para quitar de un archivo de índice compuesto. Puede eliminar varias etiquetas con una etiqueta eliminar mediante la inclusión de una lista de nombres de etiqueta separados por comas. Si dos o más etiquetas con el mismo nombre existen en los archivos de índice abierto, puede quitar una etiqueta de un archivo de índice específico mediante la inclusión de *CDXFileName*.  
  
 Todos los [OF *CDXFileName*]  
 Quita todas las etiquetas de un archivo de índice compuesto. Si la tabla actual tiene un archivo de índice compuesto estructural, se quitan todas las etiquetas del archivo de índice, se elimina el archivo de índice desde el disco y se quita la marca en el encabezado de la tabla que indica la presencia de un archivo de índice compuesto estructural asociado. Use todos los datos con OF *CDXFileName* para quitar todas las etiquetas de un archivo de índice compuesta abierto que no sea el archivo de índice compuesto estructural.  
  
## <a name="remarks"></a>Comentarios  
 Archivos de índice compuesto, creados con el índice, contienen etiquetas correspondientes a las entradas de índice. Eliminar etiqueta se utiliza para quitar una etiqueta o etiquetas de archivos de índice compuesto abierto. Puede eliminar sólo las etiquetas de los archivos de índice compuesto abiertos en el área de trabajo actual. Si quita todas las etiquetas de un archivo de índice compuesto, se elimina el archivo desde el disco.  
  
 Visual FoxPro busca primero una etiqueta en el archivo de índice compuesto estructural (si está abierto). Si la etiqueta no se encuentra en el archivo de índice compuesto estructural, Visual FoxPro, a continuación, busca la etiqueta en los demás archivos de índice compuesto abierto.  
  
## <a name="see-also"></a>Vea también  
 [Comando de índice](../../odbc/microsoft/index-command.md)
