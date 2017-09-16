---
title: Realizar cambios en las tablas seleccionadas para capturar cambios | Documentos de Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- makChanToTab
ms.assetid: a309f82a-c6ef-464d-a6ef-df555bfb609a
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 962b3a3690bd8a0bf62de762509c4398773578ca
ms.contentlocale: es-es
ms.lasthandoff: 08/03/2017

---
# <a name="make-changes-to-the-tables-selected-for-capturing-changes"></a>Realizar cambios en las tablas seleccionadas para capturar cambios
  En este cuadro de diálogo, puede seleccionar determinadas columnas de la tabla seleccionada desde las que se van a capturar datos. También puede editar la información de **Rol de seguridad** y de **Instancia de captura** .  
  
 Puede realizar los cambios siguientes en las tablas seleccionadas para capturar cambios en este cuadro de diálogo.  
  
 **Realizar cambios a las columnas incluidas en la instancia CDC:**  
  
 Realice una o ambas de las acciones siguientes:  
  
-   Active la casilla situada junto a cualquier columna adicional que desee incluir.  
  
-   Desactive la casilla situada junto a cualquier columna que ya no desee incluir.  
  
 **Cambiar el tipo de datos para una columna específica**:  
  
 Puede seleccionar un tipo de datos diferente para una columna determinada. Solo puede cambiar el tipo de datos a uno que sea compatible con el tipo de datos original.  
  
 Para cambiar el tipo de datos, haga clic en la columna **Tipo de datos** y seleccione un tipo de datos diferente. Solo están disponibles los tipos de datos compatibles con el tipo de datos original.  
  
> [!NOTE]  
>  Si no se puede seleccionar ningún tipo de datos adicional, la lista desplegable no estará disponible.  
  
 **Cambiar el rol de seguridad**  
  
 Escriba un nuevo nombre o edite el nombre del rol de acceso de seguridad en el campo **Rol de seguridad** .  
  
 **Cambiar o agregar una instancia de captura**  
  
 En el campo **Instancia de captura** , escriba un nombre para la instancia de captura.  
  
## <a name="see-also"></a>Vea también  
 [Cómo crear la instancia de base de datos de cambios SQL Server](../../integration-services/change-data-capture/how-to-create-the-sql-server-change-database-instance.md)   
 [Seleccione las columnas y tablas de Oracle](../../integration-services/change-data-capture/select-oracle-tables-and-columns.md)  
  
  