---
title: Tarea Sistema de archivos de Azure Data Lake Store | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: douglasl
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSTASK.F1
- SQL14.DTS.DESIGNER.AFPADLSTASK.F1
author: Lingxi-Li
ms.author: lingxl
manager: craigg
ms.openlocfilehash: 1308984c4d9ea5e66c927582241cb6d3d224a2ac
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2018
ms.locfileid: "35328889"
---
# <a name="azure-data-lake-store-file-system-task"></a>Tarea Sistema de archivos de Azure Data Lake Store

La tarea Sistema de archivos de Azure Data Lake Store permite que los usuarios realicen diversas operaciones del sistema de archivos en [Azure Data Lake Store (ADLS)](https://azure.microsoft.com/services/data-lake-store/).

La tarea Sistema de archivos de Azure Data Lake Store es un componente de [Feature Pack de SQL Server Integration Services (SSIS) para Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

## <a name="configure-the-azure-data-lake-store-file-system-task"></a>Configurar la tarea Sistema de archivos de Azure Data Lake Store

Para agregar una tarea Sistema de archivos de Azure Data Lake Store a un paquete, arrástrela desde el cuadro de herramientas de SSIS al lienzo del diseñador. Después, haga doble clic en la tarea, o clic con el botón derecho y seleccione **Editar**, para abrir el cuadro de diálogo **Azure Data Lake Store File System Task Editor** (Editor de la tarea Sistema de archivos de Azure Data Lake Store).

La propiedad **Operación** especifica la operación del sistema de archivos que se va a realizar. Seleccione una de las siguientes operaciones:

- **CopyToADLS:** cargar archivos a ADLS.
- **CopyToADLS:** descargar archivos de ADLS.

## <a name="configure-the-properties-for-the-operation"></a>Configurar las propiedades de la operación
Para cualquier operación, tendrá que especificar un administrador de conexiones de Azure Data Lake.

Estas son las propiedades específicas de cada operación:

### <a name="copytoadls"></a>CopyToADLS
- **LocalDirectory:** especifica el directorio de origen local que contiene los archivos que se cargarán.
- **FileNamePattern:** especifica un filtro de nombre de archivo para los archivos de código fuente. Se cargan solo los archivos cuyo nombre coincide con el patrón especificado. Se admite el uso de los caracteres comodín `*` y `?`.
- **SearchRecursively:** especifica si se deben buscar de forma recursiva en el directorio de origen los archivos para cargar.
- **AzureDataLakeDirectory:** especifica el directorio de destino de ADLS al que cargar archivos.
- **FileExpiry:** especifica una fecha y hora de expiración para los archivos cargados en ADLS. Deje esta propiedad en blanco para indicar que los archivos nunca expiran.

### <a name="copyfromadls"></a>CopyFromADLS
- **AzureDataLakeDirectory:** especifica el directorio de origen de ADLS que contiene los archivos que se descargarán.
- **SearchRecursively:** especifica si se deben buscar de forma recursiva en el directorio de origen archivos para descargar.
- **LocalDirectory:** especifica el directorio de destino para almacenar los archivos descargados.
