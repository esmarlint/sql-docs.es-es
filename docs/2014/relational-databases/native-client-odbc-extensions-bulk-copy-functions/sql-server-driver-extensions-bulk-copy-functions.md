---
title: Funciones de copia masiva | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], functions
- ODBC, bulk copy operations
- functions [ODBC]
ms.assetid: 6526b892-1d58-4f55-8335-f09887f6ea02
caps.latest.revision: 39
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bab3c80749bc7fedb721e7f0a8d776c98a3f312d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425894"
---
# <a name="bulk-copy-functions"></a>Bulk Copy Functions
  La extensión de la API de copia masiva específica de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] del controlador ODBC de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client permite que las aplicaciones cliente agreguen filas de datos a una tabla de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rápidamente o las extraigan de ella.  
  
 Al utilizar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, puede hacer referencia a las funciones de copia masiva (BCP) de SQLNCLI11.LIB y SQLNCLI.H.  
  
 Una aplicación que usa llamadas de funciones de la API BCP debe vincularse a la biblioteca (.lib) que se incluye con el controlador (.dll) que usa la aplicación. Una aplicación BCP no debe vincularse a más de una biblioteca de controlador.  
  
## <a name="in-this-section"></a>En esta sección  
  
-   [bcp_batch](bcp-batch.md)  
  
-   [bcp_bind](bcp-bind.md)  
  
-   [bcp_colfmt](bcp-colfmt.md)  
  
-   [bcp_collen](bcp-collen.md)  
  
-   [bcp_colptr](bcp-colptr.md)  
  
-   [bcp_columns](bcp-columns.md)  
  
-   [bcp_control](bcp-control.md)  
  
-   [bcp_done](bcp-done.md)  
  
-   [bcp_exec](bcp-exec.md)  
  
-   [bcp_getcolfmt](bcp-getcolfmt.md)  
  
-   [bcp_gettypename](bcp-gettypename.md)  
  
-   [bcp_init](bcp-init.md)  
  
-   [bcp_moretext](bcp-moretext.md)  
  
-   [bcp_readfmt](bcp-readfmt.md)  
  
-   [bcp_sendrow](bcp-sendrow.md)  
  
-   [bcp_setbulkmode](bcp-setbulkmode.md)  
  
-   [bcp_setcolfmt](bcp-setcolfmt.md)  
  
-   [bcp_writefmt](bcp-writefmt.md)  
  
## <a name="see-also"></a>Vea también  
 [Extensiones del controlador SQL Server](../../database-engine/dev-guide/sql-server-driver-extensions.md)   
 [Realizar operaciones de copia masiva &#40;ODBC&#41;](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
