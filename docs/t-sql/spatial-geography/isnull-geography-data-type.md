---
title: IsNull (tipo de datos geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- IsNull (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- IsNull method
ms.assetid: c031074f-bfda-4584-a3bf-4e7c324f237f
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 855b5f4f94c48dc0010075372439b4266b8c5b26
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36243577"
---
# <a name="isnull-geography-data-type"></a>IsNull (tipo de datos geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Propiedad que especifica si la instancia de **geography** es NULL. Devuelve 'TRUE' si la instancia es NULL; en caso contrario, devuelve 0.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
.IsNull  
```  
  
## <a name="return-types"></a>Tipos devueltos  
 Tipo de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **bit**  
  
 Tipo de CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Notas  
 `IsNull` se puede usar para comprobar si una instancia de **geography** es NULL. Esto puede producir resultados un tanto confusos, devolviendo 0 si la instancia no es NULL y NULL si la instancia es NULL.  
  
 Este método lo usa principalmente la infraestructura [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; se recomienda usar el predicado IS NULL de T-SQL para comprobar si una instancia de **geography** es NULL. Para más información sobre el predicado IS NULL de T-SQL, vea [IS NULL &#40;Transact-SQL&#41;](../../t-sql/queries/is-null-transact-sql.md).  
  
## <a name="examples"></a>Ejemplos  
  
## <a name="see-also"></a>Ver también  
 [Métodos extendidos en instancias de geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
