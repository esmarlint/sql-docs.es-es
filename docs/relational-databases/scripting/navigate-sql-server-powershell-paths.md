---
title: "Navegar por las rutas de acceso de SQL Server PowerShell | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d68aca48-d161-45ed-9f4f-14122ed30218
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# Navegar por las rutas de acceso de SQL Server PowerShell
  El proveedor de PowerShell de [!INCLUDE[ssDE](../../includes/ssde-md.md)] expone el conjunto de objetos de una instancia de SQL Server en una estructura similar a una ruta de acceso del archivo. Puede usar los cmdlets de Windows PowerShell para navegar por la ruta de acceso del proveedor y crear las unidades personalizadas para acortar la ruta de acceso que tiene que escribir.  
  
## Antes de comenzar  
 Windows PowerShell implementa cmdlets para navegar por la estructura de ruta de acceso que representa la jerarquía de objetos compatible con un proveedor de PowerShell. Cuando ha navegado a un nodo de la ruta de acceso, puede usar otros cmdlets para realizar operaciones básicas en el objeto actual. Dado que los cmdlets se usan con frecuencia, tienen alias canónicos cortos. También hay un conjunto de alias que asigna los cmdlets a comandos del símbolo del sistema similares, y otro conjunto para los comandos shell de UNIX.  
  
 El proveedor de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implementa un subconjunto de los cmdlets de proveedor, que se muestran en la tabla siguiente.  
  
|cmdlet|Alias canónico|Alias de cmd|Alias de shell de UNIX|Descripción|  
|------------|---------------------|---------------|----------------------|-----------------|  
|**Get-Location**|**gl**|**pwd**|**pwd**|Obtiene el nodo actual.|  
|**Set-Location**|**sl**|**cd, chdir**|**cd, chdir**|Cambia el nodo actual.|  
|**Get-ChildItem**|**gci**|**dir**|**ls**|Enumera los objetos almacenados en el nodo actual.|  
|**Get-Item**|**gi**|||Devuelve las propiedades del elemento actual.|  
|**Rename-Item**|**rni**|**rn**|**ren**|Cambia el nombre de un objeto.|  
|**Remove-Item**|**ri**|**del, rd**|**rm, rmdir**|Quita un objeto.|  
  
> [!IMPORTANT]  
>  Algunos identificadores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (nombres de objeto) contienen caracteres que Windows PowerShell no admite en los nombres de ruta de acceso. Para obtener más información sobre cómo usar nombres que contengan estos caracteres, vea [SQL Server Identifiers in PowerShell](../../relational-databases/scripting/sql-server-identifiers-in-powershell.md).  
  
### Información de SQL Server devuelta por Get-ChildItem  
 La información devuelta por **Get-ChildItem** (o sus alias **dir** e **ls**) depende de la ubicación en una ruta de acceso de SQLSERVER.  
  
|Ubicación de la ruta de acceso|Resultados de Get-ChildItem|  
|-------------------|----------------------------|  
|SQLSERVER:\SQL|Devuelve el nombre del equipo local. Si ha usado SMO o WMI para conectarse a las instancias de [!INCLUDE[ssDE](../../includes/ssde-md.md)] en otros equipos, esos equipos también se enumeran.|  
|SQLSERVER:\SQL\\*nombreDeEquipo*|Lista de instancias del [!INCLUDE[ssDE](../../includes/ssde-md.md)] en el equipo.|  
|SQLSERVER:\SQL\\*nombreDeEquipo*\\*nombreDeInstancia*|Lista de tipos de objeto de nivel superior en la instancia, como Extremos, Certificados y Bases de datos.|  
|Nodo de clase de objeto, como Databases|Lista de objetos de ese tipo, como la lista de bases de datos: master, model, AdventureWorks2008R2.|  
|Nodo de nombre de objeto, como AdventureWorks2012|Lista de los tipos de objeto contenidos en el objeto. Por ejemplo, una base de datos mostraría tipos de objeto como tablas y vistas.|  
  
 De forma predeterminada, **Get-ChildItem** no muestra ningún objeto del sistema. Use el parámetro *Force* para ver los objetos del sistema, como los objetos del esquema **sys** .  
  
### Unidades personalizadas  
 Windows PowerShell deja que los usuarios definan las unidades virtuales, a las que se hace referencia como unidades de PowerShell. Estas se asignan en los nodos de inicio de una instrucción de ruta de acceso. Se suelen usar para acortar las rutas de acceso que se escriben con frecuencia. Las rutas de acceso de SQLSERVER: pueden requerir mucho tiempo y espacio en la ventana de Windows PowerShell, así como mucho esfuerzo para escribirlas. Si va a trabajar mucho en un nodo de ruta de acceso determinado, puede definir una unidad de Windows PowerShell personalizada que se asigne a ese nodo.  
  
## Use Alias de Cmdlet de PowerShell  
 **Use un alias de cmdlet**  
  
-   En lugar de escribir un nombre completo de cmdlet, escriba un alias más corto que se asigna a un comando de símbolo de sistema.  
  
### Ejemplo de Alias (PowerShell)  
 Por ejemplo, puede usar uno de los conjuntos de cmdlets o alias siguientes para recuperar una lista de las instancias de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disponibles para navegar a la carpeta SQLSERVER:\SQL y solicitar la lista de elementos secundarios de la misma:  
  
```  
## Shows using the full cmdet name.  
Set-Location SQLSERVER:\SQL  
Get-ChildItem  
  
## Shows using canonical aliases.  
sl SQLSERVER:\SQL  
gci  
  
## Shows using command prompt aliases.  
cd SQLSERVER:\SQL  
dir  
  
## Shows using Unix shell aliases.  
cd SQLSERVER:\SQL  
ls  
```  
  
## Uso de Get-ChildItem  
 **Devuelve información mediante Get-Childitem**  
  
1.  Navegue hasta el nodo para el que desea obtener una lista de childrem  
  
2.  Ejecuta Get-Childitem para obtener la lista.  
  
### Ejemplo de Get-ChildItem (PowerShell)  
 Estos ejemplos muestran la información devuelta por Get-Childitem para varios nodos en una ruta de acceso del proveedor de SQL Server.  
  
```  
## Return the current computer and any computer  
## to which you have made a SQL or WMI connection.  
Set-Location SQLSERVER:\SQL  
Get-ChildItem  
  
## List the instances of the Database Engine on the local computer.  
  
Set-Location SQLSERVER:\SQL\localhost  
Get-ChildItem  
  
## Lists the categories of objects available in the  
## default instance on the local computer.  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT  
Get-ChildItem  
  
## Lists the databases from the local default instance.  
## The force parameter is used to include the system databases.  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases  
Get-ChildItem -force  
```  
  
## Crea una unidad personalizada  
 **Cree y use una unidad personalizada**  
  
1.  Use **New-PSDrive** para definir una unidad personalizada. Use el parámetro de **Root** para especificar la ruta de acceso representada por el nombre de la unidad personalizada.  
  
2.  Haga referencia al nombre de la unidad personalizada en cmdlets de navegación de la ruta de acceso como **Set-Location**.  
  
### Ejemplo de unidad personalizada (PowerShell)  
 Este ejemplo crea una unidad virtual denominada AWDB que asigna al nodo de una copia implementada de la base de datos de ejemplo de AdventureWorks2012. La unidad virtual se usa para navegar a una tabla de la base de datos.  
  
```  
## Create a new virtual drive.  
New-PSDrive -Name AWDB -Root SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012  
  
## Use AWDB: to navigate to a specific table.  
Set-Location AWDB:\Tables\Purchasing.Vendor  
```  
  
## Vea también  
 [Proveedor de PowerShell de SQL Server](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [Trabajar con rutas acceso de SQL Server PowerShell](../../relational-databases/scripting/work-with-sql-server-powershell-paths.md)   
 [Convertir URN en rutas de acceso del proveedor de SQL Server](../../relational-databases/scripting/convert-urns-to-sql-server-provider-paths.md)   
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  