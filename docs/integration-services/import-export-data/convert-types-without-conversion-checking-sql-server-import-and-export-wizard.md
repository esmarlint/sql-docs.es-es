---
title: "Convertir tipos sin comprobar conversi&#243;n (Asistente para importaci&#243;n y exportaci&#243;n de SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "01/11/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.impexpwizard.nomappingfile.f1"
ms.assetid: 87d9d3e5-477f-4117-a37f-bff53ea3e14d
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 24
---
# Convertir tipos sin comprobar conversi&#243;n (Asistente para importaci&#243;n y exportaci&#243;n de SQL Server)
  Después de seleccionar las tablas y vistas existentes para copiar o revisar la consulta que ha proporcionado, el Asistente para importación y exportación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] puede mostrar **Convertir tipos sin comprobar conversión**. El asistente muestra esta página cuando no puede encontrar uno o varios de los archivos de asignación y de conversión de tipo de datos que necesita para asignar tipos de datos entre el origen y el destino. La página incluye información que le ayudará a comprender qué falta.
  
 Haga clic en **Siguiente** para continuar sin saber si las conversiones de tipos de datos se realizarán correctamente. De lo contrario, haga clic en **Atrás** para cambiar las selecciones o haga clic en **Cancelar** para salir del asistente.
  
 Para obtener información sobre cómo el asistente asigna los tipos de datos de las columnas de origen a las de destino y sobre cómo usa los archivos de asignación de tipo de datos, consulte [¿Cómo asigna el asistente tipos de datos entre el origen y el destino?](Import%20and%20Export%20Data%20with%20the%20SQL%20Server%20Import%20and%20Export%20Wizard.md\#wizardMapping)  

## <a name="screen-shot-of-the-convert-types-page"></a>Captura de pantalla de la página Convertir tipos  
  
La siguiente captura de pantalla muestra un ejemplo de la página del asistente **Convertir tipos sin comprobar conversión**.

![Convertir tipos](../../integration-services/import-export-data/media/convert-types.png)

El problema es que el asistente no puede encontrar un archivo de asignación que asigne tipos de datos para el destino seleccionado.

La información de esta página no incluye el nombre del archivo de asignación que falta. Dado que el asistente no sabe si existe un archivo para el proveedor de datos especificado, no puede proporcionar un nombre para el archivo que falta.

## <a name="whats-next"></a>¿Qué debe hacer a continuación?  
 Después de hacer clic en **Siguiente** para continuar sin saber si las conversiones de tipos de datos se realizarán correctamente, la siguiente página es **Guardar y ejecutar paquete**. En esta página, especifique si quiere ejecutar la operación de copia inmediatamente. Según la configuración, también puede guardar el paquete de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creado por el asistente para personalizarlo y volver a usarlo más adelante. Para más información, vea [Guardar y ejecutar paquete](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md).  