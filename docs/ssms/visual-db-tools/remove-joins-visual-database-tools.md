---
title: Quitar combinaciones (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- removing joins
- joins [SQL Server], removing
- deleting joins
ms.assetid: ccc212a1-fd13-48d6-85e5-5ff310c34bbd
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 88b5bc8e83484129cb6d503b2bb1feb226c8cc34
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "33048222"
---
# <a name="remove-joins-visual-database-tools"></a>Quitar combinaciones (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Si no desea que las tablas se combinen mediante una combinación interna o externa, puede quitar la combinación existente entre ellas. Por ejemplo, puede quitar una combinación que el [Diseñador de consultas y vistas](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) haya creado automáticamente entre dos tablas.  
  
> [!NOTE]  
> Cuando se quita una combinación de una consulta, no se modifica la relación subyacente en la base de datos.  
  
Si dos tablas combinadas forman parte de la consulta y quita todas las condiciones de combinación que existen entre ellas, la consulta resultante es el producto de ambas tablas, es decir, una instancia CROSS JOIN.  
  
### <a name="to-remove-a-join"></a>Para quitar una combinación  
  
-   En el [panel Diagrama](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md), seleccione la línea de combinación de la combinación que desea quitar y, a continuación, presione la tecla SUPR. Puede seleccionar y eliminar varias líneas de combinación al mismo tiempo.  
  
El Diseñador de consultas y vistas quita la línea de combinación y modifica la instrucción en el [panel SQL](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md).  
  
## <a name="see-also"></a>Ver también  
[Combinar tablas automáticamente &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/join-tables-automatically-visual-database-tools.md)  
[Combinar tablas manualmente &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/join-tables-manually-visual-database-tools.md)  
[Realizar consultas con combinaciones &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  
