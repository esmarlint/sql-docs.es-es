---
title: Propiedad DatabaseQueryTimeout (MSReportServer_ConfigurationSetting de WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
api_name:
- DatabaseQueryTimeout Property
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseQueryTimeout property
ms.assetid: 96faed97-9799-4bbf-a66f-fdd532d3eace
caps.latest.revision: 35
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 2cf7248fe0052a23e3ceef2243a4b6b45645402b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37258001"
---
# <a name="databasequerytimeout-property-wmi-msreportserverconfigurationsetting"></a>Propiedad DatabaseQueryTimeout (MSReportServer_ConfigurationSetting de WMI)
  Especifica el número de segundos que deben transcurrir antes de que el servidor de informes asuma un error del comando o que necesita demasiado tiempo para ejecutarse. El servidor de informes ajusta el tiempo de la consulta con respecto al catálogo de SQL, no a un origen de datos para el informe. Lectura/escritura  
  
## <a name="syntax"></a>Sintaxis  
  
```vb  
Public Dim DatabaseQueryTimeout As UInt32  
```  
  
```csharp  
public UInt32 DatabaseQueryTimeout;  
```  
  
## <a name="property-values"></a>Valores de propiedad  
 32 bits sin signo `integer` objeto que representa el número de segundos que se puede ejecutar la consulta.  
  
## <a name="example-code"></a>Código de ejemplo  
 [Clase MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Espacio de nombres:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Miembros MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
