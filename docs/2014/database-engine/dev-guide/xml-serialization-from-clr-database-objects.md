---
title: Serialización XML de objetos de base de datos CLR | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- serialization
- XML serialization [CLR integration]
- common language runtime [SQL Server], XML serialization
- XmlSerializer class
ms.assetid: ac84339b-9384-4710-bebc-01607864a344
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ad6b9ebaba9f05b0a927cd65f788cdbdb672a6d5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36204660"
---
# <a name="xml-serialization-from-clr-database-objects"></a>Serialización XML de objetos de base de datos de CLR
  La serialización XML se requiere para dos situaciones:  
  
-   Invocar los servicios web desde los objetos de Common Language Runtime (CLR).  
  
-   Convertir un tipo definido por el usuario (UDT) en XML.  
  
 La realización de la serialización XML invocando la clase `XmlSerializer` genera normalmente un ensamblado de serialización adicional que se sobrecarga en el proyecto con el ensamblado de origen. Sin embargo, por razones de seguridad, esta sobrecarga está deshabilitada en CLR. Por lo tanto, para llamar a un servicio web o realizar la conversión de UDT a XML en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], se debe crear el ensamblado manualmente mediante una herramienta denominada **Sgen.exe** proporcionada con .NET Framework que genera la necesaria ensamblados de serialización. Al invocar `XmlSerializer`, se debe crear el ensamblado de serialización manualmente siguiendo estos pasos:  
  
1.  Ejecute el **Sgen.exe** herramienta que se proporciona con .NET Framework SDK para crear el ensamblado que contiene los serializadores XML para el ensamblado de origen.  
  
2.  Registre el ensamblado generado en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con la instrucción `CREATE ASSEMBLY`.  
  
 Para obtener información acerca de los errores que puede recibir al realizar la serialización XML, consulte el siguiente artículo de Microsoft Support: ["No se puede cargar el ensamblado de serialización generado dinámicamente"](http://support.microsoft.com/kb/913668).  
  
 Para obtener información sobre los tipos de datos no admitidos por XMLSerializer, consulte Compatibilidad con enlaces del esquema XML en .NET Framework en la documentación de .NET Framework.  
  
## <a name="see-also"></a>Vea también  
 [Acceso a datos desde objetos de base de datos CLR](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)   
 [CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql)  
  
  