---
title: Cambios substanciales de SQL Server Reporting Services en SQL Server 2016 | Microsoft Docs
ms.date: 07/02/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: reporting-services
ms.reviewer: ''
ms.suite: pro-bi
ms.custom: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Me.Value references
- Reporting Services, backward compatibility
- breaking changes [Reporting Services]
ms.assetid: 39c7aafd-dcb9-4317-b8f7-d15828eb4f9a
caps.latest.revision: 121
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: f034cad035750603705d17e31becdc8496b99893
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "33014612"
---
# <a name="breaking-changes-in-sql-server-reporting-services-in-sql-server-2016"></a>Cambios substanciales de SQL Server Reporting Services en SQL Server 2016

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016](../includes/ssrs-appliesto-2016.md)] [!INCLUDE [ssrs-appliesto-not-2017](../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../includes/ssrs-previous-versions.md)]

En este tema se describen los principales cambios realizados en [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Estos cambios pueden provocar errores en las aplicaciones, en los scripts o en las funcionalidades basados en versiones anteriores de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Podría encontrarlos al actualizar, o en scripts o informes personalizados.

## <a name="security-extensions"></a>Extensiones de seguridad

Las extensiones de seguridad personalizadas necesitan alguna modificación para funcionar con el nuevo [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]. Las extensiones de seguridad necesitan usar la interfaz IAuthenticationExtension2.

## <a name="wmi-provider"></a>Proveedor WMI

La aplicación [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] cambia su nombre de "ReportManager" a "ReportServerWebApp".

## <a name="next-steps"></a>Pasos siguientes

[Cambios de comportamiento de SQL Server Reporting Services en SQL Server 2016](../reporting-services/behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)  
[Novedades de Reporting Services (SSRS)](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md)   
[Características en desuso de SQL Server Reporting Services en SQL Server 2016](../reporting-services/deprecated-features-in-sql-server-reporting-services-ssrs.md)    
[Funcionalidad de SQL Server Reporting Services descontinuada en SQL Server 2016](../reporting-services/discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  

¿Tiene alguna pregunta más? [Puede plantear sus dudas en el foro de Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
