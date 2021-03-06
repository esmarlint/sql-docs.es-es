---
title: Intercalación (cuadro de diálogo, Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.definecolumncollation
- vdtsql.chm:65561
ms.assetid: e4020f79-7abf-4839-b9b2-984ef7049817
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 59fdbf7a2847b4a033a2f6a22bb056393e24b272
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37218855"
---
# <a name="collation-dialog-box-visual-database-tools"></a>Intercalación (cuadro de diálogo, Visual Database Tools)
  Este cuadro de diálogo permite especificar una secuencia de intercalación para la columna. La secuencia de intercalación de una columna se utiliza en cualquier operación que compare los valores de la columna con otra columna o con valores constantes. También afecta al comportamiento de algunas funciones de cadena, como SUBSTRING y CHARINDEX. Para obtener una lista completa de los efectos del valor de intercalación de una columna, vea la documentación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Este cuadro de diálogo aparece en las situaciones siguientes:  
  
-   Si se escribe un nombre del intercalación no válido en el campo **Intercalación** de la pestaña **Propiedades de columna** .  
  
-   Si se hace clic en el campo **Intercalación** de la pestaña **Propiedades de columna** y, luego, se hace clic en el botón de puntos suspensivos (**...**) que aparece a la derecha del campo.  
  
## <a name="options"></a>Opciones  
 **Intercalación de SQL**  
 Elija una de las secuencias de intercalación que define [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en la lista desplegable.  
  
 **Intercalación de Windows**  
 Elija una de las secuencias de intercalación que define Windows en la lista desplegable.  
  
 **Orden binario**  
 Utilice los códigos binarios de valores de caracteres para la comparación. Si activa esta opción, no estarán disponibles determinadas opciones de comparación alfabética. Por ejemplo, la posibilidad de distinguir entre mayúsculas y minúsculas no estará disponible, puesto que las letras mayúsculas y las minúsculas tienen codificaciones binarias diferentes. Solo se aplica si se selecciona **Intercalación de Windows**.  
  
 **Orden del diccionario**  
 Utilice las opciones de comparación alfabética. Solo se aplica si se selecciona **Intercalación de Windows**. Las opciones de comparación alfabética son:  
  
-   **Distinguir mayúsculas de minúsculas** Seleccione esta opción si desea distinguir las letras mayúsculas de las minúsculas en las comparaciones.  
  
-   **Distinguir acentos** Seleccione esta opción si desea distinguir entre letras acentuadas y no acentuadas en las comparaciones. Si selecciona esta opción, también se distinguirán letras con distintos tipos de acento en las comparaciones.  
  
-   **Distinguir Kana** Seleccione esta opción si desea distinguir entre las sílabas japonesas katakana e hiragana en las comparaciones.  
  
-   **Distinguir ancho** Seleccione esta opción si desea distinguir entre caracteres de ancho medio y completo en las comparaciones.  
  
 **Restaurar valores predeterminados (Botón)**  
 Aplica a la columna la secuencia de intercalación predeterminada para la base de datos.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con columnas en consultas de funciones agregadas &#40;Visual Database Tools&#41;](visual-database-tools.md)  
  
  
