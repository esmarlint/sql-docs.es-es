---
title: 'Paso 6: Desconectar del origen de datos | Documentos de Microsoft'
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
- application process [ODBC], disconnecting from data source
- data sources [ODBC], disconnecting
- disconnecting from data source [ODBC]
ms.assetid: 6ad759ba-4721-4d8f-9b26-de976d4fc1a0
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: db689d042d4dedd12f487933783ad89018433d69
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915010"
---
# <a name="step-6-disconnect-from-the-data-source"></a>Paso 6: Desconectar del origen de datos
El paso final es desconectarse del origen de datos, como se muestra en la siguiente ilustración. En primer lugar, la aplicación libera todos los identificadores de instrucción mediante una llamada a **SQLFreeHandle**. Para obtener más información, consulte [liberar un identificador de instrucciones](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md).  
  
 ![Muestra la desconexión de un origen de datos](../../../odbc/reference/develop-app/media/pr17.gif "pr17")  
  
 A continuación, la aplicación se desconecta del origen de datos con **SQLDisconnect** y libera el identificador de conexión con **SQLFreeHandle**. Para obtener más información, consulte [desconectarse de un origen de datos o el controlador](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
 Por último, la aplicación libera el identificador del entorno con **SQLFreeHandle** y descarga el Administrador de controladores. Para obtener más información, consulte [asignar el entorno de controlar](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).
