---
title: Ejecutar procedimientos | Documentos de Microsoft
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
- SQL statements [ODBC], procedures
- procedures [ODBC], executing
ms.assetid: a75e497a-4661-438a-a10e-f598c65f81be
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d61929c1d2afb756be5157f3378ff0fe6b4d7e95
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910780"
---
# <a name="executing-procedures"></a>Ejecución de procedimientos
ODBC define una secuencia de escape estándar para la ejecución de procedimientos. Para obtener la sintaxis de esta secuencia y un ejemplo de código que lo usa, consulte [las llamadas a procedimiento](../../../odbc/reference/develop-app/procedure-calls.md).  
  
 Para ejecutar un procedimiento, una aplicación realiza las siguientes acciones:  
  
1.  Establece los valores de los parámetros. Para obtener más información, consulte [parámetros de la instrucción](../../../odbc/reference/develop-app/statement-parameters.md), más adelante en esta sección.  
  
2.  Llamadas **SQLExecDirect** y le pasa una cadena que contiene la instrucción SQL que ejecuta el procedimiento. Esta instrucción puede utilizar la secuencia de escape definida por la sintaxis de ODBC o específicos del DBMS; las instrucciones que utilizan la sintaxis específica del DBMS no son interoperables.  
  
3.  Cuando **SQLExecDirect** se llama, el controlador:  
  
    -   Recupera los valores de parámetro actuales y los convierte según sea necesario. Para obtener más información, consulte [parámetros de la instrucción](../../../odbc/reference/develop-app/statement-parameters.md), más adelante en esta sección.  
  
    -   Llama al procedimiento en el origen de datos y envía los valores de parámetro convertido. Cómo el controlador llama al procedimiento es específico del controlador. Por ejemplo, puede modificar la instrucción SQL para usar la gramática SQL del origen de datos y envía esta instrucción para su ejecución, o podría llamar al procedimiento directamente mediante un mecanismo de llamada a procedimiento remoto (RPC) que se define en el protocolo de flujo de datos del DBMS.  
  
    -   Devuelve los valores de parámetros de salida o de cualquier entrada/salida o el valor devuelto del procedimiento, suponiendo que el procedimiento se realiza correctamente. Estos valores no estén disponibles hasta que se han procesado todos los demás resultados (número de filas y conjuntos de resultados) generados por el procedimiento. Si se produce un error en el procedimiento, el controlador devuelve los errores.
