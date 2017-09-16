---
title: "Lección 4: Agregar redirección de flujo de Error con SSIS | Documentos de Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 0c8dbda2-75e3-4278-9b4e-dcd220c92522
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: cfe3634566a7ede28e3c1f5640cfe6e4caa1c351
ms.contentlocale: es-es
ms.lasthandoff: 08/03/2017

---
# <a name="lesson-4-add-error-flow-redirection-with-ssis"></a>Lección 4: Agregar redirección de flujo de errores con SSIS
Para administrar los errores que puedan aparecer en el proceso de transformación, [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ofrece la posibilidad de decidir para cada componente y cada columna cómo administrar los datos que no pueden transformarse. Puede optar por omitir un error en determinadas columnas, redireccionar toda la fila que ha generado el error o simplemente rechazar el componente debido a un error. De forma predeterminada, todos los componentes de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] están configurados para ser rechazados si se produce un error. Rechazar el componente debido a un error, causa, a su vez, que el paquete también genere un error y que todos los procesos subsiguientes se detengan.  
  
En lugar de dejar que los errores detengan la ejecución de los paquetes, es recomendable configurar y administrar los posibles errores de procesamiento como si se produjeran en la transformación. Si bien puede optar por omitir los errores a fin de garantizar que el paquete se ejecute correctamente, generalmente es mejor redireccionar la fila que genera el error a otra ruta de proceso en la que los datos y el error puedan persistir, puedan examinarse y puedan procesarse de nuevo más adelante.  
  
En esta lección, creará una copia del paquete que ha desarrollado en la [Lección 3: Agregar registro con SSIS](../integration-services/lesson-3-add-logging-with-ssis.md). Trabajando con este paquete nuevo, creará una versión dañada de los archivos de datos de ejemplo. El archivo dañado forzará la aparición de un error de proceso al ejecutar el paquete.  
  
Para administrar los datos del error, agregará y configurará un destino de archivo plano que escribirá en un archivo las filas que no puedan encontrar un valor de búsqueda en la transformación Lookup Currency Key.  
  
Antes de escribir los datos del error en el archivo, incluirá un componente de script que utiliza un script para obtener descripciones de error. A continuación, volverá a configurar la transformación Lookup Currency Key para redireccionar los datos que no hayan podido procesarse en la transformación Script.  
  
> [!IMPORTANT]  
> Para este tutorial, se necesita la base de datos de ejemplo **AdventureWorksDW2012** . Para obtener más información sobre cómo instalar e implementar **AdventureWorksDW2012**, [ejemplos de producto de Reporting Services en CodePlex](http://go.microsoft.com/fwlink/p/?LinkID=526910).  
  
## <a name="tasks-in-lesson"></a>Tareas de la lección  
Esta lección contiene las siguientes tareas:  
  
-   [Paso 1: Copiar el paquete de la lección 3](../integration-services/lesson-4-1-copying-the-lesson-3-package.md)  
  
-   [Paso 2: Crear un archivo dañado](../integration-services/lesson-4-2-creating-a-corrupted-file.md)  
  
-   [Paso 3: Agregar redirección de flujo de Error](../integration-services/lesson-4-3-adding-error-flow-redirection.md)  
  
-   [Paso 4: Agregar un destino de archivo sin formato](../integration-services/lesson-4-4-adding-a-flat-file-destination.md)  
  
-   [Paso 5: Probar el paquete del Tutorial lección 4](../integration-services/lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Iniciar la lección  
[Paso 1: Copiar el paquete de la lección 3](../integration-services/lesson-4-1-copying-the-lesson-3-package.md)  
  
  
  
