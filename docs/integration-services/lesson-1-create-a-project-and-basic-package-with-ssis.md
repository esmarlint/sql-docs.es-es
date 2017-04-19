---
title: "Lecci&#243;n 1: Crear un proyecto y un paquete b&#225;sico con SSIS | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 84d0b877-603f-4f8e-bb6b-671558ade5c2
caps.latest.revision: 35
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 35
---
# Lecci&#243;n 1: Crear un proyecto y un paquete b&#225;sico con SSIS
En esta lección, creará un paquete ETL simple que extrae datos de un único origen de archivo plano, transforma los datos usando dos componentes de la transformación de búsqueda y escribe dichos datos en la tabla de hechos **FactCurrency** de **AdventureWorksDW2012**. Como parte de esta lección, aprenderá a crear paquetes nuevos, agregar y configurar orígenes de datos y conexiones de destino, y trabajar con nuevos componentes de flujo de control y flujo de datos.  
  
> [!IMPORTANT]  
> Para este tutorial, se necesita la base de datos de ejemplo **AdventureWorksDW2012** . Para obtener más información sobre la instalación e implementación de **AdventureWorksDW2012**, consulte [Ejemplos de producto de Reporting Services en CodePlex](http://go.microsoft.com/fwlink/p/?LinkID=526910).  
  
## Descripción de los requisitos de paquete  
Este tutorial necesita Microsoft SQL Server Data Tools.  
  
Para obtener más información sobre cómo instalar SQL Server Data Tools, consulte [Descargar SQL Server Data Tools](http://msdn.microsoft.com/en-us/data/hh297027).  
  
Antes de crear un paquete, debe saber qué formato se utiliza en los datos de origen y de destino. Una vez que conozca ambos formatos de datos, estará listo para definir las transformaciones necesarias para asignar los datos de origen al destino.  
  
### Información sobre el origen  
En este tutorial, los datos de origen son un conjunto de datos de moneda históricos que se encuentra en el archivo plano SampleCurrencyData.txt. Los datos de origen tienen las cuatro columnas siguientes: tipo de cambio medio de la moneda, una clave de moneda, una clave de fecha y el tipo de cambio de final del día.  
  
A continuación se muestra un ejemplo de datos de origen del archivo SampleCurrencyData.txt:  
  
<pre>1.00070049USD9/3/05 0:001.001201442  
1.00020004USD9/4/05 0:001  
1.00020004USD9/5/05 0:001.001201442  
1.00020004USD9/6/05 0:001  
1.00020004USD9/7/05 0:001.00070049  
1.00070049USD9/8/05 0:000.99980004  
1.00070049USD9/9/05 0:001.001502253  
1.00070049USD9/10/05 0:000.99990001  
1.00020004USD9/11/05 0:001.001101211  
1.00020004USD9/12/05 0:000.99970009</pre>  
  
Cuando se trabaja con datos de origen de un archivo plano, es importante entender el modo en que el administrador de conexiones de archivos planos interpreta los datos del archivo plano. Si el origen de archivo plano es Unicode, el administrador de conexiones de archivos planos define todas las columnas como [DT_WSTR], con un ancho de columna predeterminado de 50. Si el origen de archivo plano tiene la codificación ANSI, las columnas se definen como [DT_STR], con un ancho de columna de 50. Es probable que tenga que cambiar estos valores predeterminados para que los tipos de columna de cadena sean más adecuados para los datos. Para ello, deberá saber cuál es el tipo de datos del destino en el que se escribirán los datos y luego elegir el tipo correcto dentro del administrador de conexiones de archivos planos.  
  
### Información sobre el destino  
El destino final de los datos de origen es la tabla de hechos **FactCurrency** de **AdventureWorksDW**. La tabla de hechos **FactCurrency** tiene cuatro columnas y tiene relaciones con dos tablas de dimensiones, como se muestra en la tabla siguiente.  
  
|Nombre de la columna|Tipo de datos|Tabla de búsqueda|Columna de búsqueda|  
|---------------|-------------|----------------|-----------------|  
|AverageRate|float|Ninguno|Ninguno|  
|CurrencyKey|int (FK)|DimCurrency|CurrencyKey (PK)|  
|DateKey|int (FK)|DimDate|DateKey (PK)|  
|EndOfDayRate|float|Ninguno|Ninguno|  
  
### Asignar datos de origen para que sean compatibles con el destino  
El análisis de los formatos de datos de origen y de destino indica que serán necesarias búsquedas para los valores **CurrencyKey** y **DateKey** . Las transformaciones que realizarán estas búsquedas obtendrán los valores de **CurrencyKey** y **DateKey** usando las claves alternativas de las tablas de dimensiones **DimCurrency** y **DimDate** .  
  
|Columna de archivo plano|Nombre de tabla|Nombre de la columna|Tipo de datos|  
|--------------------|--------------|---------------|-------------|  
|0|FactCurrency|AverageRate|float|  
|1|DimCurrency|CurrencyAlternateKey|nchar (3)|  
|2|DimDate|FullDateAlternateKey|date|  
|3|FactCurrency|EndOfDayRate|float|  
  
## Tareas de la lección  
Esta lección contiene las siguientes tareas:  
  
-   [Paso 1: Crear un nuevo proyecto de Integration Services](../integration-services/step-1-creating-a-new-integration-services-project.md)  
  
-   [Paso 2: agregar y configurar un administrador de conexiones de archivos planos](../integration-services/step-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
-   [Paso 3: agregar y configurar un administrador de conexiones OLE DB](../integration-services/step-3-adding-and-configuring-an-ole-db-connection-manager.md)  
  
-   [Paso 4: agregar una tarea de flujo de datos al paquete](../integration-services/step-4-adding-a-data-flow-task-to-the-package.md)  
  
-   [Paso 5: Agregar y configurar el origen de archivo plano](../integration-services/step-5-adding-and-configuring-the-flat-file-source.md)  
  
-   [Paso 6: Agregar y configurar transformaciones de búsqueda](../integration-services/step-6-adding-and-configuring-the-lookup-transformations.md)  
  
-   [Paso 7: agregar y configurar el destino de OLE DB](../integration-services/step-7-adding-and-configuring-the-ole-db-destination.md)  
  
-   [Paso 8: Facilitar la comprensión del paquete de la lección 1](../integration-services/step-8-making-the-lesson-1-package-easier-to-understand.md)  
  
-   [Paso 9: Probar el paquete del tutorial de la lección 1](../integration-services/step-9-testing-the-lesson-1-tutorial-package.md)  
  
## Iniciar la lección  
[Paso 1: Crear un nuevo proyecto de Integration Services](../integration-services/step-1-creating-a-new-integration-services-project.md)  
  