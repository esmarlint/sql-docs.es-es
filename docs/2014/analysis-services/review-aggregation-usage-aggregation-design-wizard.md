---
title: Revise el uso de agregaciones (Asistente para diseño de agregaciones) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.aggregationdesignwizard.reviewusage.f1
ms.assetid: 107ee872-3df2-4931-b56c-af11e38f6745
caps.latest.revision: 8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1c0027b2bceada8bfe84f0ee835395dd62686d16
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37332817"
---
# <a name="review-aggregation-usage-aggregation-design-wizard"></a>Revisar el uso de agregaciones (Asistente para diseño de agregaciones)
  Utilice la página **Revisar el uso de agregaciones** para configurar el uso de agregaciones.  
  
## <a name="options"></a>Opciones  
 **Default**  
 Seleccione esta opción para establecer como predeterminada la configuración del uso de agregaciones del atributo. Esta configuración permite que el diseñador aplique una regla predeterminada basada en el tipo de atributo y dimensión.  
  
 `Full`  
 Seleccione esta opción para establecer la configuración de uso de agregaciones del atributo `Full`. Con esta configuración es necesario que cada agregación del cubo incluya ese atributo o un atributo relacionado que tenga un valor inferior en la cadena de atributos. El `Full` configuración del uso de agregación debe evitarse cuando un atributo contiene muchos miembros. Cuando la configuración se ha especificado para varios atributos o atributos con varios miembros, es posible que esta configuración impida que se diseñen las agregaciones debido a un tamaño excesivo.  
  
 **Ninguno**  
 Seleccione esta opción para establecer la configuración del uso de agregaciones del atributo en None. Con esta configuración ninguna agregación del cubo puede incluir el atributo.  
  
 `Unrestricted`  
 Seleccione esta opción para establecer la configuración de uso de agregaciones del atributo `Unrestricted`. Esta configuración impide que se coloquen restricciones en el diseñador de agregaciones. Sin embargo, es necesario que el atributo se evalúe para determinar si es un candidato importante de la agregación.  
  
 **Establezca todas en la configuración predeterminada**  
 Seleccione esta opción para establecer como predeterminada la configuración del uso de agregaciones de todos atributos.  
  
## <a name="see-also"></a>Vea también  
 [Ayuda de F1 del Asistente de diseño de agregación](aggregation-design-wizard-f1-help.md)   
 [Asistentes de Analysis Services &#40;datos multidimensionales&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  
