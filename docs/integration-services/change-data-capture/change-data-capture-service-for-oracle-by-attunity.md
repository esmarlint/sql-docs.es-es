---
title: "Servicio de captura de datos modificados para Oracle de Attunity | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 22ec8a5c-9550-4d38-8a4a-485ec3e53ea8
caps.latest.revision: 21
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 21
---
# Servicio de captura de datos modificados para Oracle de Attunity
  El servicio CDC para Oracle es un servicio de Windows que examina los registros de transacciones de Oracle y captura los cambios a las tablas de Oracle deseadas en tablas de cambios de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Las tablas de cambios de SQL donde se almacenan los cambios capturados de Oracle son el mismo tipo de tablas de cambios empleadas en la característica de captura de datos modificados nativa de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Esto hace que el uso de estos cambios sea tan sencillo como el de los cambios realizados a las bases de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## Installation  
 El servicio y el diseñador de captura de datos modificados para Oracle de Attunity de Microsoft® para Microsoft SQL Server® 2016 forman parte del Feature Pack de SQL Server 2016. Descargue los componentes del Feature Pack, en la [página web de SQL Server 2016 Feature Pack](http://go.microsoft.com/fwlink/?LinkId=746297).  
  
 El servicio CDC para Oracle se puede instalar en cualquier equipo compatible con Windows que tenga acceso a las bases de datos de origen de Oracle que se van a capturar y a la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de destino donde reside la base de datos CDC de destino. El servicio CDC no necesita ninguna instalación local de la base de datos de Oracle ni de la base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , solo sus clientes compatibles. Para obtener información acerca de dónde instalar los componentes de base de datos necesarios, vea **Requisitos previos de la base de datos** en este tema.  
  
 La instalación del servicio CDC de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para Oracle coloca la interfaz de usuario de configuración del servicio y el programa de servicio en la ubicación seleccionada. El servicio CDC para Oracle se configura de forma independiente mediante la Consola de configuración del servicio CDC de Oracle. Para obtener más información acerca de cómo configurar el servicio CDC de Oracle, vea [Change Data Capture Service for Oracle by Attunity F1 Help](../../integration-services/change-data-capture/change-data-capture-service-for-oracle-by-attunity-f1-help.md).  
  
 El servicio CDC para Oracle se puede instalar en cualquier equipo compatible con Windows donde esté instalado [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client; no es necesario instalarlo en el mismo equipo donde está instalado [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de destino.  
  
## Entornos de Windows admitidos  
 El Servicio de captura de datos modificados para Oracle de Attunity se puede ejecutar en los entornos de Windows siguientes:  
  
-   Windows Vista con Service Pack 2  
  
-   Windows 7  
  
-   Windows 8 y 8.1  
  
-   Windows 10  
  
-   Windows Server 2008 R2  
  
-   Windows Server 2008 con Service Pack 2  
  
-   Windows Server 2012  
  
## Requisitos previos de la base de datos  
 Para trabajar con el servicio CDC para Oracle debe instalar el software de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client Oracle. Se trata de un requisito previo que se debe obtener de Oracle e instalar antes de instalar el servicio CDC de Oracle. Además, debe instalar el cliente ODBC de SQL Server mediante el programa de instalación de SQL Server.  
  
 El servicio CDC para Oracle admite las versiones siguientes:  
  
### Base de datos de Oracle de origen  
  
-   Oracle Database 11x, cualquier versión  
  
-   Oracle Database 10x, cualquier versión  
  
-   Versión 2 de la base de datos 10g de Oracle: 10.2.0.1-10.2.0.5 (revisión de abril de 2010)  
  
-   Versión 1 de la base de datos 11g de Oracle: 11.1.0.6-11.1.0.7 (revisión de septiembre de 2008)  
  
-   Versión 2 de la base de datos 11g de Oracle: 11.2.0.1-11.2.0.3 (revisión de septiembre de 2011)  

-   Oracle Database 12C en instalación clásica. (La instalación de tipo multiinquilino no es compatible).  
  
### Base de datos de SQL Server de destino  
 Para obtener una lista de las características admitidas por las ediciones de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vea [Características compatibles con las ediciones de SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md).  
  
## Ejecutar el programa de instalación  
 Para instalar el servicio CDC para Oracle, abra el asistente para la instalación para la plataforma Windows que esté usando (32 o 64 bits) y siga las instrucciones de la pantalla.  
  
## Desinstalar el servicio de captura de datos modificados para Oracle de Attunity  
 La desinstalación del servicio CDC para Oracle se realiza mediante Panel de control, Programas y características.  
  
 Al desinstalar el servicio CDC no se eliminan las bases de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creadas. Para quitar completamente la herramienta, debe quitar la base de datos MSXDBCDC y las bases de datos CDC específicas que se crearon en la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de destino con la que trabajó.  
  
 Si desinstala el software del servicio CDC de un equipo y lo instala en otro equipo, solo tiene que proporcionar las definiciones siguientes:  
  
-   Cuenta de servicio  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Cadena de conexión y credenciales  
  
-   La contraseña maestra  
  
 Todas las demás definiciones están almacenadas en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y están disponibles de la instalación anterior en el otro equipo.  
  
## En esta documentación  
  
-   [Servicio de captura de datos modificados para Oracle de Attunity (Arquitectura del sistema)](../../integration-services/change-data-capture/change-data-capture-service-for-oracle-by-attunity-system-architecture.md)  
  
-   [El servicio CDC de Oracle](../../integration-services/change-data-capture/the-oracle-cdc-service.md)  
  
-   [Servicio de captura de datos modificados para Oracle de Attunity (Ayuda de F1)](../../integration-services/change-data-capture/change-data-capture-service-for-oracle-by-attunity-f1-help.md)  
  
-   [Servicio de captura de datos modificados para Oracle de Attunity (Guía de procedimientos)](../../integration-services/change-data-capture/change-data-capture-service-for-oracle-by-attunity-how-to-guide.md)  
  
## Vea también  
 [Trabajar con el servicio CDC de Oracle](../../integration-services/change-data-capture/working-with-the-oracle-cdc-service.md)  
  
  