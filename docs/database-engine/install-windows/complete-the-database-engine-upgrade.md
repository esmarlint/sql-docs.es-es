---
title: "Completar la actualización del motor de base de datos | Microsoft Docs"
ms.custom: 
ms.date: 07/21/2017
ms.prod:
- sql-server-2016
- sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f08087e-e532-416c-8caa-e0ec88c57596
caps.latest.revision: 10
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 581e8cd7a43dd1e4c878cc56b49644e51d7a3a79
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="complete-the-database-engine-upgrade"></a>Completar la actualización motor de base de datos

Una vez completada la actualización a SQL Server, hay algunos pasos más que hay que realizar. Entre ellas, figuran:  
  
Después de actualizar el [!INCLUDE[ssDE](../../includes/ssde-md.md)], complete las siguientes tareas:  
  
- **Haga una copia de seguridad de las bases de datos:** haga una copia de seguridad completa de cada base de datos.  

- **Habilite nuevas características:** en SQL Server 2016 y SQL Server 2017, algunos cambios solo se habilitan una vez que el nivel de DATABASE_COMPATIBILITY de una base de datos se ha cambiado a 130 o superior.  Para obtener más información y para ver el flujo de trabajo recomendado, vea [Cambiar el modo de compatibilidad de la base de datos y usar el almacén de consultas](../../database-engine/install-windows/change-the-database-compatibility-mode-and-use-the-query-store.md).  
  
- **Integration Services:**  
  
     Migre los paquetes de Integration Services al formato [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Para obtener más información, consulte [Upgrade Integration Services Packages](../../integration-services/install-windows/upgrade-integration-services-packages.md).  
  
- **Reporting Services:** para una nueva actualización de instalación, restaure las claves de cifrado de Reporting Services. Para obtener más información, vea [Hacer copia de seguridad y restaurar claves de cifrado de Reporting Services](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).  
  
- **Master Data Services:** actualice el esquema de base de datos MDS y cree la aplicación web de SQL Server 2017. Para obtener más información, vea [Actualizar Master Data Services](../../database-engine/install-windows/upgrade-master-data-services.md).  
  
- **Data Quality Services:** actualice el esquema de base de datos DQS y compruebe la actualización del esquema de base de datos DQS. Para obtener más información, vea [Actualizar Data Quality Services](../../database-engine/install-windows/upgrade-data-quality-services.md).  
  
- **Búsqueda de texto completo:** vuelva a rellenar los catálogos de texto completo para garantizar la coherencia semántica de los resultados de las consultas. Para obtener más información, vea [Rellenar índices de texto completo](../../relational-databases/search/populate-full-text-indexes.md).  
  
