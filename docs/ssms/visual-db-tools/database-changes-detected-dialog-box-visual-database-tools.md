---
title: Se han detectado cambios en la base de datos (cuadro de diálogo, Visual Database Tools) | Microsoft Docs
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
f1_keywords:
- vdt.dlgbox.schema.databasechangesdetected
- vdtsql.chm:65543
- vdtsql.chm:65554
ms.assetid: 91f13086-371f-46a2-9f46-804c1415f3ed
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7e63f1093a744c56e0900930b54708f15493f89e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "33048312"
---
# <a name="database-changes-detected-dialog-box-visual-database-tools"></a>Se han detectado cambios en la base de datos (cuadro de diálogo, Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Este cuadro de diálogo aparece si intenta guardar un diagrama de base de datos o tablas seleccionadas y alguno de los objetos de la base de datos a los que va a afectar la acción de guardar no está actualizado en la base de datos. Si acepta los cambios mostrados en este cuadro de diálogo, se actualizará la base de datos para que coincida con el diagrama y se sobrescribirán los cambios realizados por otros usuarios.  
  
> [!NOTE]  
> Aunque no se pueden deshacer los cambios realizados en una tabla o un diagrama de base de datos, los cambios no se guardan en la base de datos hasta que se guarde la tabla o el diagrama. Para descartar los cambios no guardados, elija **No** y cierre todos los diagramas abiertos sin guardarlos.  
  
## <a name="options"></a>Opciones  
**Advertir sobre detección de diferencias**  
Especifica si se mostrará este cuadro de diálogo la próxima vez que intente guardar un diagrama de base de datos o las tablas seleccionadas. Si esta opción está activada, el cuadro de diálogo aparecerá cada vez que guarde un diagrama o una tabla que no se haya actualizado aún en la base de datos. Si está desactivada, no se mostrará el cuadro de diálogo. La opción está activada de forma predeterminada. Si desactiva esta opción, podrá volver a activarla en el cuadro de diálogo **Opciones** .  
  
**Sí**  
Actualiza la base de datos con todos los cambios mostrados en la lista.  
  
**No**  
Cancela la acción de guardar.  
  
> [!NOTE]  
> Para actualizar el diagrama de forma que coincida con la base de datos, ciérrelo sin guardar los cambios, haga clic con el botón secundario en el diagrama del Explorador de servidores, haga clic en Actualizar y, a continuación, vuelva a abrir el diagrama.  
  
**Guardar archivo de texto**  
Muestra el cuadro de diálogo **Guardar como** , que permite especificar una ubicación para el archivo de texto que contiene la lista de cambios efectuados en la base de datos.  
  
## <a name="see-also"></a>Ver también  
[Reconciliar un diagrama de base de datos con una base de datos modificada &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/reconcile-a-database-diagram-with-a-modified-database-visual-database-tools.md)  
[Entornos multiusuario &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/multiuser-environments-visual-database-tools.md)  
  
