---
title: "Validar gu&#237;as de planes tras una actualizaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-plan-guides"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "guías de plan [SQL Server], validar después de actualizar"
ms.assetid: a55ebd88-6f58-454d-b1c4-991b88add522
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# Validar gu&#237;as de planes tras una actualizaci&#243;n
  Se recomienda volver a evaluar y probar las definiciones de guías de plan al actualizar la aplicación a una nueva versión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Los requisitos de optimización del rendimiento y el comportamiento de la coincidencia de las guías de plan pueden cambiar. Aunque una guía de plan no válida no hará que una consulta provoque un error, el plan se compilada sin utilizar la guía de plan y posiblemente no sea la mejor opción. Después de actualizar una base de datos a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], es recomendable que realice las tareas siguientes:  
  
-   Valide las guías de plan existentes con la función [sys.fn_validate_plan_guide](../../relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql.md).  
  
-   Utilice eventos extendido para supervisar los planes equivocados durante un cierto período de tiempo con el evento [Guía de plan incorrecta](../../relational-databases/event-classes/plan-guide-unsuccessful-event-class.md) .  
  
  