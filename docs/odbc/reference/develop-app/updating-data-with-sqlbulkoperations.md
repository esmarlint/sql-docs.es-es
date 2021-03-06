---
title: Actualizar datos con SQLBulkOperations | Documentos de Microsoft
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
- SQLBulkOperations function [ODBC], updating data
- data updates [ODBC], SQLBulkOperations
- updating data [ODBC], SQLBulkOperations
ms.assetid: 7645a704-341e-4267-adbe-061a9fda225b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6b1acf3d788381f32d892432c0834cc5ee130680
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="updating-data-with-sqlbulkoperations"></a>Actualizar datos con SQLBulkOperations
Las aplicaciones pueden realizar operaciones de actualización, eliminación, fetch o la inserción masiva en la tabla subyacente en el origen de datos con una llamada a **SQLBulkOperations**. Al llamar a **SQLBulkOperations** es una buena alternativa para crear y ejecutar una instrucción SQL. Permite que un controlador ODBC admite actualizaciones por posición incluso cuando el origen de datos no admite las instrucciones SQL posicionadas. Forma parte del paradigma de lograr acceso a la base de datos completa por medio de llamadas a funciones.  
  
 **SQLBulkOperations** opera en el conjunto de filas actual y puede usarse solo después de llamar a **SQLFetch** o **SQLFetchScroll**. La aplicación especifica las filas para actualizar, eliminar o actualizar al almacenar en caché sus marcadores. El controlador recupera los nuevos datos de filas que deben actualizarse o los nuevos datos va a insertar en la tabla subyacente, de los búferes de conjunto de filas.  
  
 El tamaño del conjunto de filas que va a usar **SQLBulkOperations** se establece mediante una llamada a **SQLSetStmtAttr** con una *atributo* argumento de SQL_ATTR_ROW_ARRAY_SIZE. A diferencia de **SQLSetPos**, que utiliza un nuevo tamaño de conjunto de filas solo después de llamar a **SQLFetch** o **SQLFetchScroll**, **SQLBulkOperations** usa la nuevo tamaño de conjunto de filas después de llamar a **SQLSetStmtAttr**.  
  
 Puesto que la mayoría de interacción con bases de datos relacionales se realiza a través de SQL, **SQLBulkOperations** no se admite ampliamente. Sin embargo, un controlador puede fácilmente emular, crear y ejecutar un **actualización**, **eliminar**, o **insertar** instrucción.  
  
 Para determinar qué operaciones **SQLBulkOperation** admite, una aplicación llama **SQLGetInfo** con el SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR _ATTRIBUTES1 o SQL_STATIC_CURSOR_ATTRIBUTES1 opción de información (según el tipo del cursor).  
  
 Esta sección contiene los temas siguientes.  
  
-   [Actualizar las filas por marcador con SQLBulkOperations](../../../odbc/reference/develop-app/updating-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Eliminar filas por marcador con SQLBulkOperations](../../../odbc/reference/develop-app/deleting-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Insertar filas con SQLBulkOperations](../../../odbc/reference/develop-app/inserting-rows-with-sqlbulkoperations.md)  
  
-   [Capturar filas con SQLBulkOperations](../../../odbc/reference/develop-app/fetching-rows-with-sqlbulkoperations.md)
