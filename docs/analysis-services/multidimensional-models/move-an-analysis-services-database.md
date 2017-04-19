---
title: "Mover una base de datos de Analysis Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mover bases de datos [Analysis Services]"
  - "mover bases de datos"
  - "operaciones [Analysis Services - datos multidimensionales]"
ms.assetid: fa644e5d-e276-445e-98d9-673afcfb83fe
caps.latest.revision: 14
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 14
---
# Mover una base de datos de Analysis Services
  Con frecuencia, se producen situaciones en las que un administrador de base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] quiere mover una base de datos modelo multidimensional o tabular a otra ubicación. Estas situaciones suelen responder a necesidades empresariales, como mover la base de datos a otro disco para mejorar el rendimiento, disponer de más espacio para que la base de datos pueda crecer o actualizar un producto.  
  
 Una base de datos se puede mover de muchas maneras. En este documento se describen los siguientes escenarios comunes:  
  
-   Usar SSMS de forma interactiva  
  
-   Usar programación a través de AMO  
  
-   Usar script XMLA  
  
 En todos los escenarios se requiere que el usuario tenga acceso a la carpeta de la base de datos y que use un método para mover los archivos al destino final deseado.  
  
> [!NOTE]  
>  Si se separa una base de datos sin asignarla antes una contraseña, quedará desprotegida. Se recomienda asignar una contraseña a la base de datos para proteger la información confidencial. Además, se deberá aplicar la seguridad de acceso correspondiente a la carpeta, las subcarpetas y los archivos de la base de datos para impedir el acceso no autorizado.  
  
## Procedimientos  
  
#### Mover una base de datos interactivamente mediante SSMS  
  
1.  Localice la base de datos que desea mover en el panel izquierdo o derecho de SSMS.  
  
2.  Haga clic con el botón derecho del mouse en la base de datos y seleccione **Separar…**  
  
3.  Asigne una contraseña a la base de datos que se va separar y, a continuación, haga clic en **Aceptar** para ejecutar el comando Detach.  
  
4.  Use cualquier mecanismo del sistema operativo o el método que emplee normalmente para mover archivos con objeto de mover la carpeta de la base de datos a la nueva ubicación.  
  
5.  Localice la carpeta **Bases de datos** en el panel izquierdo o derecho de SSMS.  
  
6.  Haga clic con el botón derecho en la carpeta **Bases de datos** y seleccione **Asociar…**  
  
7.  En el cuadro de texto **Carpeta** , escriba la nueva ubicación de la carpeta de la base de datos. También puede usar el botón Examinar (**…**) para buscar la carpeta de la base de datos.  
  
8.  Seleccione el modo **ReadWrite** para la base de datos.  
  
9. Escriba la contraseña que se usó en el paso 3 y haga clic en **Aceptar** para ejecutar el comando Attach.  
  
#### Mover una base de datos mediante programación a través de AMO  
  
1.  En la aplicación C#, adapte el código de ejemplo siguiente y complete las tareas indicadas.  
  
 `private void MoveDb(Server server, string dbName,`  
  
 `string dbInitialLocation, string dbFinalLocation,`  
  
 `string dbPassword, ReadWriteMode dbReadWriteMode)`  
  
 `{`  
  
 `//Verify dbInitialLocation exists before continuing`  
  
 `if (server.Databases.ContainsName(dbName))`  
  
 `{`  
  
 `Database db;`  
  
 `//Save current cursor and change cursor to Cursors.WaitCursor`  
  
 `db = server.Databases[dbName];`  
  
 `db.Detach(dbPassword);`  
  
 `//Add your own code to copy the database files to the destination where you intend to attach the database`  
  
 `//Verify dbFinalLocation exists before continuing`  
  
 `server.Attach(dbFinalLocation, dbReadWriteMode, dbPassword);`  
  
 `//Restore cursor to its original`  
  
 `}`  
  
 `}`  
  
1.  En la aplicación C#, invoque `MoveDb()` con los parámetros necesarios.  
  
2.  Compile y ejecute el código para mover la base de datos.  
  
#### Mover una base de datos mediante script XMLA  
  
1.  Abra una nueva pestaña XMLA en SSMS.  
  
2.  Copie la plantilla de script siguiente para XMLA  
  
 `<Detach xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">`  
  
 `<Object>`  
  
 `<DatabaseID>%dbName%</DatabaseID>`  
  
 `<Password>%password%</Password>`  
  
 `</Object>`  
  
 `</Detach>`  
  
1.  Reemplace `%dbName%` por el nombre de la base de datos y `%password%` por la contraseña. Los caracteres % forman parte de la plantilla y se deben quitar.  
  
2.  Ejecute el comando XMLA.  
  
3.  Use cualquier mecanismo del sistema operativo o el método que emplee normalmente para mover archivos con objeto de mover la carpeta de la base de datos a la nueva ubicación.  
  
4.  Copie la plantilla de script siguiente para XMLA en una nueva pestaña XMLA  
  
 `<Attach xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">`  
  
 `<Folder>%dbFolder%</Folder>`  
  
 `<ReadWriteMode xmlns="http://schemas.microsoft.com/analysisservices/2008/engine/100">%ReadOnlyMode%</ReadWriteMode>`  
  
 `</Attach>`  
  
1.  Reemplace `%dbFolder%` por la ruta de acceso UNC completa de la carpeta de la base de datos, `%ReadOnlyMode%` por el valor **ReadOnly** o **ReadWrite** correspondiente, y `%password%` por la contraseña. Los caracteres % forman parte de la plantilla y se deben quitar.  
  
2.  Ejecute el comando XMLA.  
  
## Vea también  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Adjuntar y separar bases de datos de Analysis Services](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Ubicación de almacenamiento de las bases de datos](../../analysis-services/multidimensional-models/database-storage-location.md)   
 [Modos de la propiedad de base de datos ReadWriteMode](../../analysis-services/multidimensional-models/database-readwritemodes.md)   
 [Elemento Attach](../../analysis-services/xmla/xml-elements-commands/attach-element.md)   
 [Elemento Detach](../../analysis-services/xmla/xml-elements-commands/detach-element.md)   
 [Elemento ReadWriteMode](../../analysis-services/xmla/xml-elements-properties/readwritemode-element.md)   
 [Elemento DbStorageLocation](../../analysis-services/xmla/xml-elements-properties/dbstoragelocation-element.md)  
  
  