---
title: 'Cómo: conectarse a un puerto específico | Documentos de Microsoft'
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connecting to the server, specifying a port
ms.assetid: 65a154d1-375c-439b-a653-7815c9d70ff3
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6dd90c68aa47f21c35c2f566a2a8206ba421ace6
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35307624"
---
# <a name="how-to-connect-on-a-specified-port"></a>Cómo conectarse a un puerto específico
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

En este tema se describe cómo conectarse a SQL Server en un puerto específico con los [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
### <a name="to-connect-on-a-specified-port"></a>Pasos para conectarse a un puerto específico  
  
1.  Compruebe el puerto en que el servidor está configurado para aceptar conexiones. Para obtener información acerca de cómo configurar un servidor para que acepte conexiones en un puerto específico, vea [Cómo: configurar un servidor para que escuche en un puerto de TCP específico (Administrador de configuración de SQL Server)](../../database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port.md).  
  
2.  Agregue el puerto deseado para la *$serverName* parámetro de la [sqlsrv_connect](../../connect/php/sqlsrv-connect.md) función. Separe el nombre del servidor y el puerto con una coma. Por ejemplo, las siguientes líneas de código utilizan el controlador SQLSRV para demostrar cómo conectarse a un servidor denominado *myServer* en el puerto 1521:  
  
    ```  
    $serverName = "myServer, 1521";  
    sqlsrv_connect( $serverName );  
    ```  
  
    Las siguientes líneas de código utilizan el controlador PDO_SQLSRV para demostrar cómo conectarse a un servidor denominado *myServer* en el puerto 1521:  
  
    ```  
    $serverName = "(local), 1521";  
    $database = "AdventureWorks";  
    $conn = new PDO( "sqlsrv:server=$serverName;Database=$database", "", "");  
    ```  
  
## <a name="see-also"></a>Vea también  
[Conexión al servidor](../../connect/php/connecting-to-the-server.md)

[Programación de guía para los controladores de Microsoft para PHP para SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Introducción a los controladores de Microsoft para PHP para SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Referencia de API del controlador SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Referencia del controlador PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  
