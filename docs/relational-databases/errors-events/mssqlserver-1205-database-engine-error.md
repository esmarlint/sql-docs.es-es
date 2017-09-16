---
title: MSSQLSERVER_1205 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 1205 (Database Engine error)
ms.assetid: 9fe3f67c-df3c-4642-a3a4-ccc0e138b632
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: afbc0f15e52f470d88514a4e3cf865447a4a64fd
ms.contentlocale: es-es
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver1205"></a>MSSQLSERVER_1205
  
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|1205|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|LK_VICTIM|  
|Texto del mensaje|La transacción (Id. de proceso %d) quedó en interbloqueo en %.*ls recursos con otro proceso y fue elegida como sujeto del interbloqueo. Vuelva a ejecutar la transacción.|  
  
## <a name="explanation"></a>Explicación  
El acceso a los recursos se realiza en un orden conflictivo en transacciones independientes, lo que causa un interbloqueo. Por ejemplo:  
  
-   Transaction1 actualiza **Table1.Row1**, mientras que Transaction2 actualiza **Table2.Row2**.  
  
-   Transaction1 intenta actualizar **Table2.Row2**, pero se bloquea porque todavía no se ha confirmado Transaction2.  
  
-   Transaction2 ahora intenta actualizar **Table1.Row1**, pero se bloquea porque no se ha confirmado Transaction1.  
  
-   Se produce un interbloqueo porque Transacción1 está esperando a que Transacción2 finalice, pero Transacción2 está esperando a que finalice Transacción1.  
  
El sistema detectará este interbloqueo y elegirá una de las transacciones implicadas como "víctima". Emitirá este mensaje y la transacción de la víctima se revertirá.  
  
## <a name="user-action"></a>Acción del usuario  
Ejecute de nuevo la transacción. También puede revisar la aplicación para evitar los interbloqueos. La transacción elegida como víctima se puede volver a intentar y probablemente se realizará correctamente, en función de qué operaciones se estén ejecutando simultáneamente.  
  
Para evitar la aparición de interbloqueos, considere la posibilidad de hacer que todas las transacciones accedan a las filas en el mismo orden (**Table1**, seguida de **Table2**); de esta forma, aunque se puedan producir bloqueos, no se generarán interbloqueos.  
  
