---
title: "Conectarse a un archivo dBASE u otro archivo DBF | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "conectarse a archivos DBF"
  - "archivos dBase"
  - "archivos DBF"
ms.assetid: b0e8c831-9f96-475c-82a4-4f5b02692752
caps.latest.revision: 16
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 16
---
# Conectarse a un archivo dBASE u otro archivo DBF
  Es posible conectarse a un archivo de base de datos de dBASE u otro .DBF en un paquete de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] con un administrador de conexiones OLE DB y seleccionando el proveedor OLE DB para Microsoft Jet 4.0.  
  
> [!NOTE]  
>  El asistente de importación y exportación del servidor SQL en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no es compatible con la ejecución de la importación desde o importación hacia, dBASE o otros archivos DBF. Se puede utilizar Microsoft Access o Microsoft Excel para importar los datos de archivos DBF en una base de datos de Access o en hojas de cálculo de Excel y, a continuación, usar el Asistente para importación y exportación de SQL Server.  
  
### Para configurar un administrador de conexiones para conectarse a un archivo dBASE u otro archivo DBF  
  
1.  Agregue un nuevo administrador de conexiones OLE DB al paquete Para más información, consulte [Add, Delete, or Share a Connection Manager in a Package](../Topic/Add,%20Delete,%20or%20Share%20a%20Connection%20Manager%20in%20a%20Package.md).  
  
2.  En la página **Conexión** del cuadro de diálogo **Administrador de conexiones**, seleccione OLE DB nativo\Proveedor OLE DB de Microsoft Jet 4.0 como el **Proveedor**.  
  
3.  Cuando se trabaja con archivos DBF, la carpeta representa la base de datos, y los archivos DBF individuales representan tablas. Por lo tanto, el cuadro de texto **Nombre de archivo de base de datos** debe contener la ruta de acceso de la carpeta donde reside el archivo DBF, y no el nombre de archivo. Puede escribir o pegar una ruta de acceso a la carpeta, o bien puede utilizar el botón **Examinar** para seleccionar el archivo DBF y, a continuación, quitar el nombre de archivo del final de la ruta de acceso a la carpeta.  
  
4.  En la página **Todo** del cuadro de diálogo **Administrador de conexiones** , escriba el valor **dBASE III**, **dBASE IV**o **dBASE 5.0**, según corresponda, en Propiedades extendidas.  
  
5.  Haga clic en **Probar conexión** para validar los valores especificados. Debería recibir un mensaje que indica que se estableció correctamente la conexión de prueba. Haga clic en **Aceptar** para cerrar el cuadro de mensaje.  
  
6.  Haga clic en **Aceptar** para guardar la configuración del administrador de conexiones.  
  
7.  Para utilizar el administrador de conexiones en el flujo de datos del paquete, seleccione un origen o un destino de OLE DB y configúrelo para usar el administrador de conexiones que creó en los pasos anteriores.  
  
## Vea también  
 [Administrador de conexiones OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md)  
  
  