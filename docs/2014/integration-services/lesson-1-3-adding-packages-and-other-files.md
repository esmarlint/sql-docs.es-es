---
title: 'Paso 3: Agregar paquetes y otros archivos | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a7e6ec9c-d31d-4613-9525-8947a7b358f7
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4b2f66f8a8c5002d37948d110bd4b420c432d37b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37229315"
---
# <a name="step-3-adding-packages-and-other-files"></a>Paso 3: agregar paquetes y otros archivos
  En esta tarea, agregará paquetes existentes, archivos auxiliares que admitan paquetes individuales y un archivo Léame al proyecto Deployment Tutorial que ha creado en la tarea anterior. Por ejemplo, agregará un archivo de datos XML que contiene los datos de un paquete y un archivo de texto que proporciona información del archivo Léame sobre todos los paquetes del proyecto.  
  
 Cuando se implementan paquetes a un entorno de prueba o producción, normalmente no se incluyen los archivos de datos en la implementación, sino que se utilizan configuraciones para actualizar las rutas de acceso de los orígenes de datos para tener acceso a las versiones de prueba o producción de las bases de datos o los archivos de datos. Para explicar las instrucciones, este tutorial incluye archivos de datos en la implementación de paquetes.  
  
 Los paquetes y los datos de ejemplo que utilizan los paquetes se instalan junto con los ejemplos de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Agregará los siguientes paquetes al proyecto Deployment Tutorial:  
  
-   **DataTransfer.** Paquete básico que extrae datos de un archivo plano, evalúa valores de columnas para mantener filas en el conjunto de datos condicionalmente y carga datos en una tabla de la base de datos AdventureWorks.  
  
-   **LoadXMLData.** Paquete de transferencia de datos que extrae datos de un archivo de datos XML, evalúa y agrega valores de columnas y carga datos en una tabla de la base de datos AdventureWorks.  
  
 Para admitir la implementación de estos paquetes, agregará los siguientes archivos auxiliares al proyecto Deployment Tutorial.  
  
|Paquete|Archivo|  
|-------------|----------|  
|DataTransfer|NewCustomers.txt|  
|LoadXMLData|orders.xml y orders.xsd|  
  
 También agregará un archivo Léame, archivo de texto que proporciona información sobre el proyecto Deployment Tutorial.  
  
 Las rutas de acceso que se utilizan en los procedimientos siguientes suponen que los ejemplos de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] se instalaron en la ubicación predeterminada, [!INCLUDE[ssSampPathIS](../includes/sssamppathis-md.md)]. Si instaló los ejemplos en otra ubicación, debe utilizar esa ubicación en los procedimientos.  
  
 En la siguiente tarea, agregará configuraciones a los paquetes DataTransfer y LoadXMLData. Todas las configuraciones se almacenan en archivos XML y utilizará una variable de entorno del sistema para especificar la ubicación de los archivos. Después de crear los archivos de configuración, los agregará al proyecto.  
  
### <a name="to-add-packages-to-the-deployment-tutorial-project"></a>Para agregar paquetes al proyecto Deployment Tutorial  
  
1.  Si [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] no está abierto, haga clic en **Inicio**, seleccione **Todos los programas**, **Microsoft SQL Server**y luego haga clic en **SQL Server Data Tools**.  
  
2.  En el menú **Archivo** , haga clic en **Abrir**y, en **Proyecto o solución**, haga clic en la carpeta **Deployment Tutorial** , haga clic en **Abrir**y, después, haga doble clic en **Deployment Tutorial.sln**.  
  
3.  En el Explorador de soluciones, haga clic con el botón derecho en Deployment Tutorial, haga clic en **Agregar**y, después, en **Paquete existente**.  
  
4.  En el cuadro de diálogo **Agregar copia de paquete existente** , en **Ubicación del paquete**, seleccione **Sistema de archivos**.  
  
5.  Haga clic en el botón Examinar **(…)** , vaya a C:\Archivos de programa\Microsoft SQL Server\100\Samples\Integration ServicesTutorial\Deploying Packages\Completed Packages, seleccione **DataTransfer.dtsx**y luego haga clic en **Abrir**.  
  
6.  Haga clic en **Aceptar**.  
  
7.  Repita los pasos 3 a 6 y, en este momento, agregue LoadXMLData.dtsx, que se encuentra en C:\Archivos de programa\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Completed Packages.  
  
### <a name="to-add-ancillary-files-to-the-deployment-tutorial-project"></a>Para agregar archivos auxiliares al proyecto Deployment Tutorial  
  
1.  En el Explorador de soluciones, haga clic con el botón derecho en Deployment Tutorial, haga clic en **Agregar**y, después, en **Elemento existente**.  
  
2.  En el cuadro de diálogo **Agregar elemento existente - Deployment Tutorial** , vaya a C:\Archivos de programa\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deployment Packages\Sample Data, seleccione orders.xml, orders.xsd y NewCustomers.txt y luego haga clic en **Agregar**.  
  
3.  En el cuadro de diálogo **Agregar elemento existente - Deployment Tutorial** , vaya a C:\Archivos de programa\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deployment Packages\\, seleccione Readme.txt y haga clic en **Agregar**.  
  
4.  En el menú Archivo, haga clic en **Guardar todo**.  
  
## <a name="next-task-in-lesson"></a>Siguiente tarea de la lección  
 [Paso 4: Agregar configuraciones de paquetes](../integration-services/lesson-1-4-adding-package-configurations.md)  
  
![Icono de Integration Services (pequeño)](media/dts-16.gif "icono de Integration Services (pequeño)")**mantenerse actualizado con Integration Services** <br /> Para obtener las descargas, artículos, ejemplos y vídeos más recientes de Microsoft, así como soluciones seleccionadas de la comunidad, visite la página de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] en MSDN:<br /><br /> [Visite la página de Integration Services en MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Para recibir notificaciones automáticas de estas actualizaciones, suscríbase a las fuentes RSS disponibles en la página.  
  
  
