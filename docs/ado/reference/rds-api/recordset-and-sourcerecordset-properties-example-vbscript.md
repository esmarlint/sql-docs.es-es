---
title: Ejemplo de propiedades de SourceRecordset (VBScript) y el conjunto de registros | Documentos de Microsoft
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: sql
ms.prod_service: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Source property [ADO], VBScript example
- Recordset property [ADO], VBScript example
ms.assetid: 95175316-cd10-4cf7-96ba-2a226fd97701
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2cce066348b8bf711993f4296fcc38fec285e91a
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35288504"
---
# <a name="recordset-and-sourcerecordset-properties-example-vbscript"></a>Ejemplo de propiedades de SourceRecordset (VBScript) y el conjunto de registros
> [!IMPORTANT]
>  A partir de Windows 8 y Windows Server 2012, componentes de servidor RDS ya no están incluidos en el sistema operativo Windows (consulte Windows 8 y [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) para obtener más detalles). Componentes de cliente RDS se quitará en una versión futura de Windows. Evite utilizar esta característica en nuevos trabajos de desarrollo y tenga previsto modificar las aplicaciones que actualmente la utilizan. Las aplicaciones que utilizan RDS deben migrar a [servicio de datos de WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 En el ejemplo siguiente se muestra cómo establecer los parámetros necesarios de la [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) objeto de negocio predeterminado en tiempo de ejecución.  
  
 Para probar este ejemplo, corte y pegue este código entre las \<cuerpo > y \</cuerpo > etiquetas en una HTML normal de documento y asígnele el nombre **RecordsetVBS.asp**. Secuencia de comandos ASP identificará el servidor.  
  
```  
<!-- BeginRecordSetVBS -->  
<%@ Language=VBScript %>  
<html>  
<head>  
    <meta name="VI60_DefaultClientScript"  content=VBScript>  
    <meta name="GENERATOR" content="Microsoft Visual Studio 6.0">  
    <title>Recordset and SourceRecordset Properties Example (VBScript)</title>  
<style>  
<!--  
body {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
.thead {  
   background-color: #008080;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.thead2 {  
   background-color: #800000;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.tbody {   
   text-align: center;  
   background-color: #f7efde;  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
    }  
-->  
</style>  
</head>  
  
<body>  
<h1>Recordset and SourceRecordset Properties Example (VBScript)</h1>  
  
<Center>  
<H2>RDS API Code Examples</H2>  
<HR>  
<H3>Using SourceRecordset and Recordset with RDSServer.DataFactory</H3>  
<!-- RDS.DataSpace ID RDS1 -->  
<OBJECT ID="RDS1" WIDTH=1 HEIGHT=1   
CLASSID="CLSID:BD96C556-65A3-11D0-983A-00C04FC29E36">  
</OBJECT>  
  
<!-- RDS.DataControl with parameters set at Run Time -->  
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"  
   ID=RDC WIDTH=1 HEIGHT=1>  
</OBJECT>  
  
<TABLE DATASRC=#RDC>  
   <TR>  
      <TD> <INPUT DATAFLD="FirstName" SIZE=15> </TD>  
      <TD> <INPUT DATAFLD="LastName" SIZE=15></TD>  
   </TR>  
</TABLE>  
<HR>  
<Input Size=70 Name="txtServer" Value="http://<%=Request.ServerVariables("SERVER_NAME")%>"><BR>  
<Input Size=70 Name="txtConnect" Value="Provider='sqloledb';Integrated Security='SSPI';Initial Catalog='Northwind'"><BR>  
<Input Size=70 Name="txtSQL" Value="SELECT FirstName, LastName FROM Employees">  
<HR>  
<INPUT TYPE=BUTTON NAME="Run" VALUE="Run"><BR>  
  
</Center>  
<Script Language="VBScript">  
  
   Dim rdsDF  
   Dim strServer  
   strServer = "http://<%=Request.ServerVariables("SERVER_NAME")%>"  
  
   Sub Run_OnClick()  
  
      Dim rs           
      ' Create RDSServer.DataFactory Object  
      Set rdsDF = RDS1.CreateObject("RDSServer.DataFactory", strServer)                 
      ' Get Recordset  
      Set rs = rdsDF.Query(txtConnect.Value,txtSQL.Value)  
  
      ' Set parameters of RDS.DataControl at run time  
      RDC.Server = txtServer.Value  
      RDC.SQL = txtSQL.Value  
      RDC.Connect = txtConnect.Value  
      RDC.Refresh  
  
   End Sub  
  
</Script>  
  
</body>  
</html>  
<!-- EndRecordsetVBS -->  
```  
  
## <a name="see-also"></a>Vea también  
 [Objeto DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)   
 [Propiedades Recordset y SourceRecordset (RDS)](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md)



