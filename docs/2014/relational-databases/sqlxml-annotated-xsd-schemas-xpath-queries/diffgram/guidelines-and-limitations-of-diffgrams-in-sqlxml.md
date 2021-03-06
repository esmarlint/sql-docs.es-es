---
title: Instrucciones y limitaciones de DiffGrams en SQLXML | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: cf8689c4-2a63-4d05-b202-21b5ff187d7f
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: dbfbf7661184dce2c1e4ab957622e95361950cb1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37296625"
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a>Instrucciones y limitaciones de DiffGrams en SQLXML
  Recuerde lo siguiente al usar DiffGrams con SQLXML 4.0:  
  
-   Los tipos de objeto binario de gran tamaño (BLOB) como `text/ntext` y las imágenes no se deben usar en el bloque `<diffgr:before>` al trabajar con DiffGrams, porque esto los incluiría para su uso en el control de simultaneidad. Esto puede producir problemas con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] debido a las limitaciones en la comparación para los tipos BLOB. Por ejemplo, la palabra clave LIKE se usa en la cláusula WHERE para comparar entre las columnas del tipo de datos `text`; sin embargo, se producirá un error en las comparaciones en el caso de los tipos BLOB donde el tamaño de los datos supere los 8 K.  
  
-   Los caracteres especiales en los datos `ntext` pueden producir problemas con SQLXML 4.0 debido a las limitaciones en la comparación para los tipos BLOB. Por ejemplo, el uso de "[Serializable]" en el bloque `<diffgr:before>` de un DiffGram cuando se usa en la comprobación de simultaneidad de una columna de tipo `ntext` producirá un error con la descripción de error de SQLOLEDB siguiente:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  
