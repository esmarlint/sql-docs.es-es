---
title: ¿Qué es un bloqueo? | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], locking
- locks [ADO], about locking
ms.assetid: f8989555-28c6-4c17-9bf8-7f44a8a5c407
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 396faecd122eef7ad6e40f790252a0902a508ba8
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35273294"
---
# <a name="what-is-a-lock"></a>¿Qué es un bloqueo?
El bloqueo es el proceso mediante el cual un DBMS restringe el acceso a una fila en un entorno multiusuario. Cuando una fila o columna está bloqueada en modo exclusivo, no se permiten otros usuarios para tener acceso a los datos bloqueados hasta que se libere el bloqueo. Esto garantiza que dos usuarios no puedan actualizar simultáneamente la misma columna de una fila.  
  
 Bloqueos pueden resultar muy caras desde la perspectiva del recurso y deben usarse solo cuando sea necesario para conservar la integridad de los datos. En una base de datos donde cientos o miles de usuarios podrían estar intentando obtener acceso a un registro cada segundo, como una base de datos conectada a Internet: uso de bloqueos innecesarios podría reducir el rendimiento de la aplicación.  
  
 Puede controlar cómo el origen de datos y la biblioteca de cursores ADO administran la simultaneidad eligiendo la opción de bloqueo correspondiente.  
  
 Establecer el **LockType** propiedad antes de abrir un **Recordset** para especificar el tipo de bloqueo que el proveedor debe usar al abrirlo. Lea la propiedad para devolver el tipo de bloqueo en uso en un formato de archivo **Recordset** objeto.  
  
 Los proveedores podrían no admitir todos los tipos de bloqueo. Si un proveedor no admite solicitado **LockType** establecer, sustituirá por otro tipo de bloqueo. Para determinar la funcionalidad de bloqueo real disponible en un **Recordset** objeto, utilice la [admite](../../../ado/reference/ado-api/supports-method.md) método con **adUpdate** y **adUpdateBatch**.  
  
 El **adLockPessimistic** configuración no se admite si el [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) propiedad está establecida en **adUseClient.** Si se establece un valor no admitido, no se producirá ningún error; admite la más parecida **LockType** se utilizará en su lugar.  
  
 El **LockType** propiedad es de lectura y escritura cuando el **Recordset** está cerrado y de solo lectura cuando se abre.  
  
 Esta sección contiene los temas siguientes.  
  
-   [Tipos de bloqueos](../../../ado/guide/data/types-of-locks.md)
