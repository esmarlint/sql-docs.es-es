---
title: "Configurar las opciones avanzadas de los archivos de registro de DQS | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "archivos de registro, configuración avanzada"
  - "archivos de registro dqs, configuración avanzada"
ms.assetid: 1d565748-9759-425c-ae38-4d2032a86868
caps.latest.revision: 13
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 13
---
# Configurar las opciones avanzadas de los archivos de registro de DQS
  En este tema se describe cómo realizar la configuración avanzada para los archivos de registro de [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] y [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , como configurar el límite de tamaño del archivo gradual de los archivos de registro, establecer el patrón de marca de tiempo de los eventos, etc.  
  
> [!NOTE]  
>  Estas actividades no se pueden realizar mediante [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], y están dirigidas exclusivamente a los usuarios expertos.  
  
##  <a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
  
-   La cuenta de usuario de Windows debe ser miembro del rol fijo de servidor sysadmin en la instancia de SQL Server para modificar la configuración de la tabla A_CONFIGURATION de la base de datos DQS_MAIN.  
  
-   Debe haber iniciado sesión como miembro del grupo Administradores en el equipo donde está modificando el archivo DQLog.Client.xml para configurar los valores de registro de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] .  
  
##  <a name="DQSServer"></a> Configurar los valores de registro de Data Quality Server  
 El [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] configuración de registro está presente en un formato XML en el **valor** columna de la **ServerLogging** fila en la tabla A_CONFIGURATION de la base de datos DQS_MAIN. Puede ejecutar la consulta SQL siguiente para ver la información de configuración:  
  
```  
select * from DQS_MAIN.dbo.A_CONFIGURATION where NAME='ServerLogging'  
```  
  
 Debe actualizar la información correspondiente en la columna **VALUE** de la fila **ServerLogging** para cambiar la configuración del registro de [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] . En este ejemplo, actualizaremos los valores de registro de [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] para establecer el límite de tamaño del archivo gradual en 25000 kB (el valor predeterminado es 20000 kB).  
  
1.  Inicie Microsoft SQL Server Management Studio y conéctese a la instancia adecuada de SQL Server.  
  
2.  En el Explorador de objetos, haga clic en el servidor y, a continuación, haga clic en **nueva consulta**.  
  
3.  En la ventana del editor de consultas, copie las instrucciones SQL siguientes:  
  
    ```  
    -- Begin the transaction.  
    BEGIN TRAN  
    GO  
    -- set the XML value field for the row with name=ServerLogging  
    update DQS_MAIN.dbo.A_CONFIGURATION   
    set VALUE='<configuration>  
      <configSections>  
        <section name="loggingConfiguration" type="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.LoggingSettings, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" />  
      </configSections>  
      <loggingConfiguration name="Logging Application Block" tracingEnabled="true" defaultCategory="" logWarningsWhenNoCategoriesMatch="true">  
        <listeners>  
          <add fileName="###REPLACE_THIS_WITH_SQL_SERVER_INSTANCE_LOG_FOLDER_NAME###DQServerLog.###REPLACE_THIS_WITH_SQL_CATALOG_NAME###.log" footer="" formatter="Custom Text Formatter" header="" rollFileExistsBehavior="Increment" rollInterval="None" rollSizeKB="25000" timeStampPattern="yyyy-MM-dd" listenerDataType="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.RollingFlatFileTraceListenerData, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" traceOutputOptions="None" filter="All" type="Microsoft.Practices.EnterpriseLibrary.Logging.TraceListeners.RollingFlatFileTraceListener, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="Rolling Flat File Trace Listener" />  
        </listeners>  
        <formatters>  
          <add template="{timestamp(local)}|[{threadName}]|{dictionary({value}|)}{message}" type="Microsoft.Practices.EnterpriseLibrary.Logging.Formatters.TextFormatter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="Custom Text Formatter" />  
        </formatters>  
        <logFilters>  
          <add enabled="true" type="Microsoft.Practices.EnterpriseLibrary.Logging.Filters.LogEnabledFilter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="LogEnabled Filter" />  
        </logFilters>  
        <categorySources />  
        <specialSources>  
          <allEvents switchValue="All" name="All Events" />  
          <notProcessed switchValue="All" name="Unprocessed Category" />  
          <errors switchValue="All" name="Logging Errors & Warnings">  
            <listeners>  
              <add name="Rolling Flat File Trace Listener" />  
            </listeners>  
          </errors>  
        </specialSources>  
      </loggingConfiguration>  
    </configuration>'  
    WHERE NAME='ServerLogging'  
    GO  
    -- check the result  
    select * from DQS_MAIN.dbo.A_CONFIGURATION where NAME='ServerLogging'  
  
    -- Commit the transaction.  
    COMMIT TRAN  
  
    ```  
  
4.  Presione F5 para ejecutar las instrucciones. Vea el panel **Resultados** para comprobar que las instrucciones se han ejecutado correctamente.  
  
5.  Para aplicar los cambios realizados en la configuración de registro de [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], debe ejecutar las instrucciones Transact-SQL siguientes. Abra una nueva ventana del editor de consultas y pegue las instrucciones Transact-SQL siguientes:  
  
    ```  
    USE [DQS_MAIN]  
    GO  
    DECLARE @return_value int  
    EXEC @return_value = [internal_core].[RefreshLogSettings]  
    SELECT 'Return Value' = @return_value  
    GO  
  
    ```  
  
6.  Presione F5 para ejecutar las instrucciones. Vea el panel **Resultados** para comprobar que las instrucciones se han ejecutado correctamente.  
  
> [!NOTE]  
>  El [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] es configuración de registro generada dinámicamente y se almacena en el DQS_MAIN. Archivo de registro, que suele estar disponible en C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\MSSQL\Log si ha instalado la instancia predeterminada de SQL Server. Sin embargo, los cambios realizados directamente en este archivo no se conservan, y serán reemplazados por la configuración de la tabla A_CONFIGURATION de la base de datos DQS_MAIN.  
  
##  <a name="DQSClient"></a> Configurar los valores de registro de Data Quality Client  
 El [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] archivo de configuración para la configuración de registro, DQLog.Client.xml, está generalmente disponible en C:\Program Files\Microsoft SQL Server\130\Tools\Binn\DQ\config. El contenido del archivo XML es similar al del archivo XML que modificó con anterioridad para los valores de configuración del registro de [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] . Para configurar los valores de registro de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] :  
  
1.  Ejecute cualquier herramienta de edición de XML o el Bloc de notas como administrador.  
  
2.  Abra el archivo DQLog.Client.xml en la herramienta o en el Bloc de notas.  
  
3.  Realice los cambios necesarios y guarde el archivo para aplicarlos.  
  
## Vea también  
 [Configurar los niveles de gravedad de los archivos de registro de DQS](../data-quality-services/configure-severity-levels-for-dqs-log-files.md)  
  
  