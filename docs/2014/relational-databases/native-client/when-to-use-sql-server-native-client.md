---
title: Cuándo usar SQL Server Native Client | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- SQLNCLI, about SQL Server Native Client
- data access [SQL Server Native Client], about SQL Server Native Client
ms.assetid: 08f18b36-209d-4cf7-9623-ebc61859a91d
caps.latest.revision: 36
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bfeee539be2afb80596f5638bc0420616cfc95ae
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411684"
---
# <a name="when-to-use-sql-server-native-client"></a>Cuándo debe utilizarse SQL Server Native Client
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client es una tecnología que puede utilizar para tener acceso a los datos de una base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Para obtener una explicación de las tecnologías de acceso a datos diferentes, consulte [mapa de carreteras de tecnologías de acceso a datos](http://go.microsoft.com/fwlink/?LinkID=179186)  
  
 A la hora de decidir si debe usar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client como la tecnología de acceso a datos de su aplicación, debe tener en cuenta varios factores.  
  
 En el caso aplicaciones nuevas, si está utilizando un lenguaje de programación administrado, como Microsoft Visual C# o Visual Basic, y necesita obtener acceso a las nuevas características introducidas en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], debería utilizar el proveedor de datos de .NET Framework para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], que forma parte de .NET Framework.  
  
 Si está desarrollando una aplicación basada en COM y necesita obtener acceso a las nuevas características introducidas en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], debería utilizar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Si no necesita obtener acceso a las nuevas características de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puede seguir utilizando Windows Data Access Components (WDAC).  
  
 En el caso de aplicaciones OLE DB y ODBC existentes, el problema principal es si necesita obtener acceso a las nuevas características de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si su aplicación es antigua y no necesita las nuevas características de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puede seguir usando WDAC. Sin embargo, si es necesario tener acceso a esas características nuevas, como el [tipo de datos xml](/sql/t-sql/xml/xml-transact-sql), debe usar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 Tanto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client como MDAC admiten el aislamiento de transacción de lectura confirmada mediante el uso de versiones de fila, pero solo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client admite el aislamiento de transacción de instantánea. (En términos de programación, el aislamiento de transacción de instantánea con versiones de fila es igual que la transacción de lectura confirmada).  
  
 Para obtener información sobre las diferencias entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client y MDAC, vea [actualizar una aplicación a SQL Server Native Client desde MDAC](../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md).  
  
## <a name="see-also"></a>Vea también  
 [Programación de SQL Server Native Client](../../relational-databases/native-client/sql-server-native-client-programming.md)   
 [Temas de procedimientos de ODBC](../native-client-odbc-how-to/odbc-how-to-topics.md)   
 [Temas de procedimientos de OLE DB](../native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  
