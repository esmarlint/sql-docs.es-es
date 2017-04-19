---
title: "Configurar las propiedades de un recopilador de datos | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.dc.datacollectionprop.general.f1"
  - "sql13.swb.dc.datacollectionprop.advanced.f1"
ms.assetid: cf98f57d-5a6d-4bc3-bf10-783e460fc63d
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# Configurar las propiedades de un recopilador de datos
  En este tema se describe cómo puede configurar las propiedades de un recopilador de datos.  
  
## Propiedades de Recopilación de datos (pestaña General)  
 Utilice esta página para configurar las opciones para el almacén de administración de datos y especificar dónde se deben almacenar los datos recopilados antes de cargarse en el almacenamiento de datos.  
  
 **Habilitar recopilación de datos**  
 Seleccione esta opción para habilitar la recopilación de datos. Esto tiene el mismo efecto que ejecutar el procedimiento almacenado sp_syscollector_enable_collector. Si se desactiva esta casilla, se deshabilitará la recopilación de datos y tiene el mismo efecto que ejecutar el procedimiento almacenado del sp_syscollector_disable_collector.  
  
 **Server**  
 Muestra el nombre del servidor que hospedará el almacén de administración de datos.  
  
 **Nombre de la base de datos**  
 Muestra el nombre de la base de datos relacional que se utiliza para el almacén de administración de datos.  
  
 **Probar conexión**  
 Pruebe la conexión con el **Servidor** especificado usando la información proporcionada al configurar la recopilación de datos.  
  
 **Directorio de caché**  
 Especifica el directorio del sistema en el que se almacenan los datos recopilados antes de cargarlos en el almacén de administración de datos. Si no se especifica **Directorio de caché** , el recopilador de datos intenta buscar las variables de entorno %TEMP% y %TMP% y utilizar una de estas ubicaciones como la ubicación predeterminada para el almacenamiento temporal. Si no se configuran estas variables de entorno, se produce un error y se le pedirá que cree un directorio de caché.  
  
## Propiedades de Recopilación de datos (pestaña Avanzadas)  
 Utilice esta página para configurar las opciones de reintentos para la conexión con el almacén de administración de datos.  
  
 **Número de reintentos si no se puede realizar la carga**  
 Especifica el número de reintentos de carga en el almacén de administración de datos si no se puede realizar una carga. El valor predeterminado es 1.  
  
## Vea también  
 [Administrar la recopilación de datos](../../relational-databases/data-collection/manage-data-collection.md)   
 [Configurar el almacén de administración de datos &#40;SQL Server Management Studio&#41;](../../relational-databases/data-collection/configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
  