---
title: Editor de origen de CDC (página columnas) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsource.columns.f1
ms.assetid: bcf3030e-98d8-4445-967c-33c3f8ecb4fc
caps.latest.revision: 9
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 12fc9ddc38caa6525138f630dfb51a74c65c38b3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37306091"
---
# <a name="cdc-source-editor-columns-page"></a>Editor de origen de CDC (página Columnas)
  Use la página **Columnas** del cuadro de diálogo **Editor de origen de CDC** para asignar una columna de salida a cada columna externa (origen).  
  
 Para obtener más información acerca del origen de CDC, vea [CDC Source](data-flow/cdc-source.md).  
  
## <a name="task-list"></a>Lista de tareas  
 **Para abrir la página Columnas del Editor de origen de CDC**  
  
1.  En [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], abra el paquete [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] que tiene el origen de CDC.  
  
2.  En la pestaña **Flujo de datos** , haga doble clic en el origen de CDC.  
  
3.  En el **Editor de origen de CDC**, haga clic en **Columnas**.  
  
## <a name="options"></a>Opciones  
 **Columnas externas disponibles**  
 Lista de las columnas externas disponibles en el origen de datos. Esta tabla no se puede usar para agregar o quitar columnas. Seleccione las columnas que se van a usar en el origen. Las columnas seleccionadas se agregan a la lista **Columna externa** en el orden en que se seleccionan.  
  
 **Columna externa**  
 Vista de las columnas externas (origen) en el orden en que se verán cuando configure componentes que usen datos del origen de CDC. Para cambiar este orden, en primer lugar borre las columnas seleccionadas en la lista **Columnas externas disponibles** y, a continuación, seleccione las columnas externas en la lista en un orden diferente. Las columnas seleccionadas se agregan a la lista **Columna externa** en el orden en que las haya seleccionado.  
  
 **Columna de salida**  
 Especifique un nombre único para cada columna de salida. El nombre predeterminado es el nombre de la columna externa (origen) seleccionada; sin embargo, puede elegir cualquier nombre único y descriptivo. El nombre especificado se muestra en el Diseñador de SSIS.  
  
## <a name="see-also"></a>Vea también  
 [Editor de origen de CDC &#40;página Administrador de conexiones&#41;](../../2014/integration-services/cdc-source-editor-connection-manager-page.md)   
 [Editor de origen de CDC &#40;página de salida de Error&#41;](../../2014/integration-services/cdc-source-editor-error-output-page.md)  
  
  
