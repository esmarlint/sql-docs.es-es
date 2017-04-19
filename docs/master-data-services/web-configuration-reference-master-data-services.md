---
title: "Referencia de la configuraci&#243;n web (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "referencia de la configuración web [Master Data Services]"
ms.assetid: b8cc9a35-97ab-4fe0-ab4b-c07f13d9793a
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# Referencia de la configuraci&#243;n web (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] usa un archivo Web.config para contener la configuración que permite a Internet Information Services (IIS) hospedar la aplicación web de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] y el servicio web. Este archivo Web.config se encuentra en la carpeta WebApplication de la ruta de instalación de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Para obtener más información sobre la ruta y los permisos, consulte [Permisos de carpetas y archivos &#40;Master Data Services&#41;](../master-data-services/folder-and-file-permissions-master-data-services.md).  
  
## Elementos de Web.Config  
 El archivo Web.config contiene un elemento de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] personalizado, **\<masterDataServices>**, además de elementos de configuración de Windows Communication Foundation (WCF), IIS estándar, .NET Framework y ASP.NET. En la siguiente tabla se describen los elementos incluidos en el archivo Web.config.  
  
|Elemento de configuración|Description|  
|---------------------------|-----------------|  
|**masterDataServices**|Elemento personalizado. Conecta el servicio web de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] a una base de datos de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|**connectionStrings**|Elemento de ASP.NET. Para obtener más información, consulte [Elemento connetionStrings (Esquema de configuración de ASP.NET)](http://go.microsoft.com/fwlink/?LinkId=178347) en MSDN Library.|  
|**system.web**|Elemento de ASP.NET. Para obtener más información, consulte [Elemento system.web (Esquema de configuración de ASP.NET)](http://go.microsoft.com/fwlink/?LinkId=178348) en MSDN Library.|  
|**startup**|Elemento de .NET Framework. Para obtener más información, consulte [Elemento \<startup>](http://go.microsoft.com/fwlink/?LinkId=178349) en MSDN Library.|  
|**en tiempo de ejecución**|Elemento de .NET Framework. Para obtener más información, consulte [Elemento \<runtime>](http://go.microsoft.com/fwlink/?LinkId=178350) en MSDN Library.|  
|**system.codedom**|Elemento de .NET Framework. Para obtener más información, consulte [\<system.codedom> (Elemento)](http://go.microsoft.com/fwlink/?LinkId=178351) en MSDN Library.|  
|**system.web.extensions**|Elemento de ASP.NET. Para obtener más información, consulte [system.web.extensions (Elemento, Esquema de configuración de ASP.NET)](http://go.microsoft.com/fwlink/?LinkId=178352) en MSDN Library.|  
|**system.webServer**|Grupo de sección que contiene los elementos IIS. Para obtener más información, consulte [system.webServer Section Group \[IIS 7 Settings Schema\]](http://go.microsoft.com/fwlink/?LinkId=178353) (Grupo de sección system.webServer [esquema de configuración de IIS 7]) en MSDN Library.|  
|**system.serviceModel**|Elemento de WCF. Para obtener más información, consulte [\<system.serviceModel>](http://go.microsoft.com/fwlink/?LinkId=178354) en MSDN Library.|  
|**system.diagnostics**|Elemento de .NET Framework. Para obtener más información, consulte [Elemento \<system.diagnostics>](http://go.microsoft.com/fwlink/?LinkId=178355) en MSDN Library.|  
|**appSettings**|Elemento de ASP.NET. Para obtener más información, consulte [Elemento appSetings (Esquema de configuración general)](http://go.microsoft.com/fwlink/?LinkId=178356) en MSDN Library.|  
  
## Elemento masterDataServices  
 El elemento **\<masterDataServices>** es un elemento personalizado que se usa para conectar un servicio web de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] a una base de datos de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
### Sintaxis  
  
```  
<masterDataServices>  
   <instance virtualPath="path" siteName="name" connectionName="name" serviceName="name" />  
</masterDataServices>  
```  
  
### Atributos y elementos  
  
|Elemento|Description|  
|----------|-----------------|  
|**instancia**|Elemento secundario. Contiene atributos que especifican información para el servicio web y la cadena de conexión a bases de datos.|  
|**virtualPath**|Atributo. Especifica la ruta de acceso virtual de la aplicación web y servicio de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Este valor corresponde al atributo **path** del elemento **\<application>** en el elemento **\<site>** del archivo IIS ApplicationHost.config.|  
|**siteName**|Atributo. Especifica el nombre del sitio que hospeda la aplicación web y servicio de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Este valor corresponde al atributo **name** del elemento **\<site>** en el elemento **\<sites>** del archivo IIS ApplicationHost.config.|  
|**connectionName**|Atributo. Especifica el nombre del administrador de conexiones que se va a usar. Este valor corresponde al atributo **name** del elemento **\<add>** en el elemento **\<connectionStrings>** del archivo Web.config.|  
|**serviceName**|Atributo. Especifica el nombre del servicio web. Este valor corresponde al atributo **name** del elemento **\<service>** en el elemento **\<services>** del archivo Web.config.|  
  
### Ejemplo  
 El siguiente ejemplo muestra un servicio denominado MDS1 en el sitio de Contoso y la ruta de acceso /MDS que usa una cadena de conexión especificada por MDSDB.  
  
```  
<masterDataServices>  
   <instance virtualPath="/MDS" siteName="Contoso" connectionName="MDSDB" serviceName="MDS1" />  
</masterDataServices>  
```  
  
  