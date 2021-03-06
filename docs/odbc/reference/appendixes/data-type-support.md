---
title: Compatibilidad con tipos de datos | Documentos de Microsoft
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
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- data types [ODBC], ODBC drivers
- ODBC drivers [ODBC], data types
ms.assetid: 782b4490-372b-4366-aad7-a486fb8a07c8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 820e48a17e397bc9046c8ca431677074e69b8cb2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="data-type-support"></a>Compatibilidad con tipos de datos
Controladores ODBC deben admitir al menos uno de SQL_CHAR y SQL_VARCHAR. Compatibilidad con otros tipos de datos se determina por el nivel de conformidad de del controlador u origen de datos SQL-92. Una aplicación debe llamar a **SQLGetTypeInfo** para determinar los tipos de datos admitidos por el controlador.  
  
 Para obtener más información sobre los tipos de datos, vea [tipos de datos de apéndice D:](../../../odbc/reference/appendixes/appendix-d-data-types.md).
