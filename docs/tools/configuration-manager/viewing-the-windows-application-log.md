---
title: Ver el registro de aplicación Windows | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- application logs [SQL Server]
- Windows application logs [SQL Server]
- viewing Windows application logs
- errors [SQL Server], logs
- system logs [SQL Server]
- security logs [SQL Server]
- displaying Windows application logs
- logs [SQL Server], Windows application logs
ms.assetid: f9853b74-7db7-47cc-b957-e49ed5bc0a1a
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0275da15c00b2b3d12515a1422b299e017e67345
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "33068312"
---
# <a name="viewing-the-windows-application-log"></a>Ver el registro de la aplicación Windows
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Cuando se configura [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para utilizar el registro de la aplicación de Microsoft Windows, cada sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] escribe eventos nuevos en dicho registro. A diferencia del registro de errores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , no se crea un nuevo registro de aplicación cada vez que se inicia una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Para ver y administrar el registro de la aplicación Windows, utilice el Visor de eventos de Windows o el Visor de registros de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Con el Visor de eventos se pueden ver tres registros.  
  
|Tipo de registro de Windows|Description|  
|----------------------|-----------------|  
|Registro del sistema|Registra los eventos registrados por los componentes del sistema operativo Windows. Por ejemplo, el error al cargar un controlador u otro componente del sistema durante el inicio se graba en el registro del sistema.|  
|Registro de seguridad|Registra eventos de seguridad, como los errores en intentos de inicios de sesión. Esto ayuda a realizar un seguimiento de los cambios en el sistema de seguridad y a identificar las posibles infracciones en la seguridad. Por ejemplo, los intentos de iniciar una sesión en el sistema se pueden grabar en este registro, según la configuración de auditorías del Administrador de usuarios.<br /><br /> Solo los miembros del rol fijo de servidor **sysadmin** pueden ver el registro de seguridad.|  
|Registro de la aplicación|Graba los eventos registrados por las aplicaciones. Por ejemplo, una aplicación de bases de datos puede registrar un error en un archivo en el registro de aplicación.|  
  
 Para obtener más información acerca de cómo utilizar el Visor de eventos, administrar el registro de la aplicación y entender la información que contiene, vea la documentación de Windows.  
  
 **Para ver el registro de aplicación Windows**  
  
 [Ver el registro de aplicación de Windows &#40;Windows&#41;](../../relational-databases/performance/view-the-windows-application-log-windows-10.md)  
  
  
