---
title: Opciones de atributos históricos (Asistente para dimensiones de variación lenta) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.histattriboption.f1
ms.assetid: a176ec66-ec39-4c99-99d1-c1afa8450e1e
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7f9b7b2819eec76f3ccc913debea3773cad0b9e4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37328085"
---
# <a name="historical-attribute-options-slowly-changing-dimension-wizard"></a>Opciones de atributos históricos (Asistente para dimensiones variables)
  Utilice el cuadro de diálogo **Opciones de atributos históricos** para mostrar los atributos históricos por fechas de inicio y finalización, o bien para registrar atributos históricos en una columna creada especialmente con este fin.  
  
 Para obtener más información acerca de este asistente, vea [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Opciones  
 **Utilice una única columna para mostrar los registros actual y expirado**  
 Si decide utilizar una sola columna para registrar el estado de los atributos históricos, dispone de las siguientes opciones:  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Columna para indicar el registro actual**|Seleccione una columna donde se va a indicar el registro actual.|  
|**Valor actual**|Utilice **True** o **Current** para indicar si el registro es actual.|  
|**Valor de expiración**|Utilice **False** o **Expired** para indicar si el registro es un valor histórico.|  
  
 **Utilice las fechas inicial y final para identificar los registros actual y expirado**  
 La tabla de dimensiones de esta opción debe incluir una columna de fecha. Si decide mostrar los atributos históricos por fechas de inicio y finalización, dispone de las siguientes opciones:  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Columna de fecha inicial**|Seleccione en la tabla de dimensiones la columna que contiene la fecha inicial.|  
|**Columna de fecha final**|Seleccione en la tabla de dimensiones la columna que contiene la fecha final.|  
|**Variable para establecer valores de fecha**|Seleccione una variable de fecha de la lista.|  
  
## <a name="see-also"></a>Vea también  
 [Configuración de salidas con el Asistente para dimensiones de variación lenta](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
