---
title: Propiedades de la base de datos (página ChangeTracking) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.changetracking.f1
ms.assetid: 9b929640-bc62-449b-9b06-b5a77b8cf372
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ff372309d1f9f5c7eda982b4c431c24556c6f073
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37225585"
---
# <a name="database-properties-changetracking-page"></a>Propiedades de la base de datos (página ChangeTracking)
  Utilice esta página para ver o modificar la configuración del seguimiento de cambios de la base de datos seleccionada. Para obtener más información sobre las opciones disponibles en esta página, vea [Habilitar y deshabilitar el seguimiento de cambios &#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md).  
  
## <a name="options"></a>Opciones  
 **Seguimiento de los cambios**  
 Utilice esta opción para habilitar o deshabilitar el seguimiento de cambios de la base de datos.  
  
 Para habilitar el seguimiento de cambios, debe tener el permiso para modificar la base de datos.  
  
 Al cambiar el valor a **True** , se establece una opción de base de datos que permite habilitar el seguimiento en tablas individuales.  
  
 También puede configurar el seguimiento de cambios utilizando [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql).  
  
 **Período de retención**  
 Especifica el período mínimo para mantener la información de seguimiento de cambios en la base de datos. Los datos se quitarán solo si el valor **Limpieza automática**es **True**.  
  
 El valor predeterminado es 2.  
  
 **Unidades del período de retención**  
 Especifica las unidades para el valor del Período de retención. Puede seleccionar **Días**, **Horas**o **Minutos**. El valor predeterminado es **Días**.  
  
 El período de retención mínimo es de 1 minuto. No hay ningún período de retención máximo.  
  
 **Limpieza automática**  
 Indica si los datos del seguimiento de cambios se quitan automáticamente después del período de retención especificado.  
  
 Al habilitar la opción **Limpieza automática** , se restablece cualquier período de retención anterior personalizado al valor predeterminado de 2 días.  
  
## <a name="see-also"></a>Vea también  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [CREATE DATABASE &#40;Transact-SQL de SQL Server&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
  
