---
title: 'Pdostatement:: Nextrowset | Documentos de Microsoft'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 048a6d8f-7fc4-449e-8161-19268c68f41d
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fd5f05fb3f63434d134289b52d3445d749066da2
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35308574"
---
# <a name="pdostatementnextrowset"></a>PDOStatement::nextRowset
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Mueve el cursor hasta el siguiente conjunto de resultados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
bool PDOStatement::nextRowset();  
```  
  
## <a name="return-value"></a>Valor devuelto  
Se devuelve True si se ejecuta correctamente; de lo contrario, se devuelve False.  
  
## <a name="remarks"></a>Notas  
En la versión 2.0 de los [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], se agregó compatibilidad con PDO.  
  
## <a name="example"></a>Ejemplo  
  
```  
<?php  
   $server = "(local)";  
   $database = "AdventureWorks";  
   $conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
   $query1 = "select * from Person.Address where City = 'Bothell';";  
   $query2 = "select * from Person.ContactType;";  
  
   $stmt = $conn->query( $query1 . $query2 );  
  
   $rowset1 = $stmt->fetchAll();  
   $stmt->nextRowset();  
   $rowset2 = $stmt->fetchAll();  
   var_dump( $rowset1 );  
   var_dump( $rowset2 );  
?>  
```  
  
## <a name="see-also"></a>Vea también  
[Clase PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
