---
title: Irrelevantes de texto completo (página General) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftstoplist.general.f1
ms.assetid: 97f8e82d-82ab-4525-91c9-1ee3ae217309
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 2304b2b9a8711210117ffbb2a84abbf167694e71
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37221975"
---
# <a name="new-full-text-stoplist-general-page"></a>Nueva lista de palabras irrelevantes de texto completo (página General)
  Utilice este cuadro de diálogo para crear una lista de palabras irrelevantes de texto completo. Una *lista de palabras irrelevantes* es un conjunto de palabras que se usan habitualmente, denominadas *palabras irrelevantes*, que se omiten de la indización de texto completo para las tablas que utilizan dicha lista. Para obtener más información, vea [Configurar y administrar palabras irrelevantes y listas de palabras irrelevantes para la búsqueda de texto completo](../relational-databases/search/full-text-search.md).  
  
 **Usar SQL Server Management Studio para crear una lista de palabras irrelevantes**  
  
-   [Configurar y administrar palabras irrelevantes y listas de palabras irrelevantes para la búsqueda de texto completo](../relational-databases/search/full-text-search.md)  
  
## <a name="options"></a>Opciones  
 **Nombre de la lista de palabras irrelevantes de texto completo**  
 Escriba el nombre de la lista de palabras irrelevantes de texto completo.  
  
 **Propietario**  
 Especifique el propietario de la lista de palabras irrelevantes de texto completo. Si desea que la propiedad se asigne a usted, es decir, al usuario actual, deje vacío este campo.  
  
 Para especificar un usuario diferente, haga clic en el botón para examinar.  
  
### <a name="create-stoplist-options"></a>Crear opciones de la lista de palabras irrelevantes  
 Haga clic en una de las opciones siguientes de creación:  
  
 **Crear una lista de palabras irrelevantes vacía**  
 La nueva lista de palabras irrelevantes no contendrá ninguna palabra irrelevante.  
  
 **Crear a partir de la lista de palabras irrelevantes del sistema**  
 La nueva lista de palabras irrelevantes se crea a partir de la lista predeterminada que hay en la base de datos [Resource](../relational-databases/databases/resource-database.md).  
  
 **Crear a partir de una lista de palabras irrelevantes de texto completo existente**  
 La nueva lista de palabras irrelevantes se crea copiando una lista existente.  
  
 **Base de datos de origen**  
 Especifica el nombre de la base de datos a la que pertenece la lista de palabras irrelevantes existente. De manera predeterminada, se selecciona la base de datos actual. Si lo desea, seleccione otra base de datos en el cuadro de lista.  
  
 **Lista de palabras irrelevantes de origen**  
 Especifica el nombre de una lista de palabras irrelevantes existente. En la lista de listas de palabras irrelevantes disponibles, seleccione la que desea utilizar como origen. Las listas de palabras irrelevantes disponibles se enumeran en el orden en que aparecen en el Explorador de objetos.  
  
 Si alguno de los idiomas especificados en las palabras irrelevantes de la lista de palabras irrelevantes de origen no está registrado en la base de datos actual, CREATE FULLTEXT STOPLIST crea correctamente la lista, pero se devuelven advertencias y no se agregan las palabras irrelevantes correspondientes.  
  
## <a name="see-also"></a>Vea también  
 [ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)   
 [CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)   
 [DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)   
 [Configurar y administrar palabras irrelevantes y listas de palabras irrelevantes para la búsqueda de texto completo](../relational-databases/search/full-text-search.md)   
 [sys.fulltext_stoplists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)  
  
  
