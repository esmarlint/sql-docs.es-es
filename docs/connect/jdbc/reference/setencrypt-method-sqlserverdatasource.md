---
title: Método setEncrypt (SQLServerDataSource) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- setEncrypt Method (SQLServerDataSource)
apilocation:
- setEncrypt Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 0c85a9c1-f27c-457e-8461-403cc03e2d17
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 723c5c5402fb32f0ad74bf303dd7c682b88d1c84
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32843210"
---
# <a name="setencrypt-method-sqlserverdatasource"></a>Método setEncrypt (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Establece un **booleano** valor que indica si está habilitada la propiedad de cifrado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public void setEncypt(boolean encrypt)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *Cifrar*  
  
 **True** si está habilitado el cifrado de capa de Sockets seguros (SSL) entre el cliente y el [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. De lo contrario, se devuelve el valor **False**.  
  
## <a name="remarks"></a>Comentarios  
 Si la propiedad encrypt se establece en **true**, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] garantiza que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] utiliza el cifrado SSL para todos los datos enviados entre el cliente y el servidor si el servidor tiene instalado un certificado. El valor predeterminado es **false**.  
  
 El controlador JDBC detecta la máquina virtual Java (JVM) que se está ejecutando cuando se intenta establecer un protocolo de enlace SSL.  
  
 Si la propiedad encrypt se establece en **true**, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] usa el proveedor de JVM predeterminado JSSE seguridad para negociar el cifrado SSL con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. El proveedor de seguridad predeterminado puede no admitir todas las características necesarias para negociar el cifrado SSL correctamente. Por ejemplo, el proveedor de seguridad predeterminado puede no admitir el tamaño de la clave pública RSA utilizada en el [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] certificado SSL. En este caso, el proveedor de seguridad predeterminado podría generar un error que ocasionará que el controlador JDBC termine la conexión. Para resolver este problema, intente una de las siguientes acciones:  
  
-   Configurar la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] con un certificado de servidor que tiene una clave pública RSA más pequeña  
  
-   Configurar la JVM para usar un proveedor de seguridad JSSE diferente en el "\<java-home > / lib/security/java.security" archivo de propiedades de seguridad  
  
-   Usar una JVM distinta  
  
 Si la propiedad de cifrado se no se especifica o se establece en **false**, el controlador no aplicará el [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] para admitir el cifrado SSL. Si el [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] instancia no está configurada para exigir el cifrado SSL, se establece una conexión sin cifrado. Si el [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] instancia está configurada para exigir el cifrado SSL, el [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] configurará automáticamente y habilitar el cifrado SSL cuando se ejecuta correctamente en configurado JVM, o bien se ha finalizado la conexión y el controlador generará un error.  
  
## <a name="see-also"></a>Vea también  
 [Miembros SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Clase SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
