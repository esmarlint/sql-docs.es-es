---
title: Almacenamiento de dimensiones | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], storage
- storing data [Analysis Services]
- storage [Analysis Services], dimensions
- relational OLAP
- multidimensional OLAP
- MOLAP
- storing data [Analysis Services], dimensions
- ROLAP
ms.assetid: 8d74b932-2174-4e1f-8414-636455880b6a
caps.latest.revision: 30
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6462ebf90b7783260f7027d82b26be117ea0b5ce
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37153116"
---
# <a name="dimension-storage"></a>Almacenamiento de dimensiones
  Las dimensiones en [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] admiten dos modos de almacenamiento:  
  
-   OLAP relacional (ROLAP)  
  
-   OLAP multidimensional (MOLAP)  
  
 El modo de almacenamiento determina la ubicación y la forma de los datos de una dimensión. El modo de almacenamiento predeterminado para las dimensiones es MOLAP. **Temas relacionados:**[procesamiento y modos de almacenamiento de partición](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
## <a name="molap"></a>MOLAP  
 Los datos de una dimensión que utiliza MOLAP se almacenan en una estructura multidimensional en la instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Esta estructura multidimensional se crea y se llena al procesarse la dimensión. Las dimensiones MOLAP proporcionan un mejor rendimiento de las consultas que las dimensiones ROLAP.  
  
## <a name="rolap"></a>ROLAP  
 Los datos de una dimensión que utiliza ROLAP se almacenan en las tablas utilizadas para definir la dimensión. Se puede utilizar el modo de almacenamiento ROLAP para admitir grandes dimensiones sin duplicar grandes cantidades de datos, pero a expensas del rendimiento de las consultas. Puesto que la dimensión depende directamente de las tablas de la vista del origen de datos utilizadas para definir la dimensión, el modo de almacenamiento ROLAP también admite OLAP en tiempo real.  
  
> [!IMPORTANT]  
>  Si una dimensión utiliza el modo de almacenamiento ROLAP y la dimensión se incluye en un cubo que use el almacenamiento MOLAP, el cubo deberá procesarse de inmediato si se realiza algún cambio en el esquema de su tabla de origen. Si no se hace de esta manera, pueden producirse resultados incoherentes al realizar consultas al cubo. **Tema relacionado:**[automatizar Analysis Services Administrative Tasks with SSIS](../instances/automate-analysis-services-administrative-tasks-with-ssis.md).  
  
## <a name="see-also"></a>Vea también  
 [Procesamiento y modos de almacenamiento de particiones](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
  
