---
title: Ssms (Utilidad) | Microsoft Docs
ms.custom: ''
ms.date: 12/08/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], opening
- command prompt utilities [SQL Server], sqlwb
- sqlwb utility
- Management Studio command line
- opening SQL Server Management Studio
ms.assetid: aafda520-9e2a-4e1e-b936-1b165f1684e8
caps.latest.revision: 50
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c8c64df36bef9012e91d444f9f5326a4e746b543
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36926476"
---
# <a name="ssms-utility"></a>Ssms (Utilidad)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  La utilidad **Ssms** abre [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Si se especifica, **Ssms** también establece una conexión con un servidor y abre consultas, scripts, archivos, proyectos y soluciones.  
  
 Puede especificar archivos que contienen consultas, proyectos o soluciones. Los archivos que contienen consultas se conectan automáticamente con un servidor si se proporciona información de conexión y el tipo de archivo está asociado con ese tipo de servidor. Por ejemplo, los archivos .sql abrirán una ventana del Editor de consultas de SQL en [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], y los archivos .mdx abrirán una ventana del Editor de consultas MDX en [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Las**Soluciones y proyectos de SQL Server** se abrirán en [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
> [!NOTE]  
>  La utilidad **Ssms** no ejecuta consultas. Para ejecutar consultas desde la línea de comandos, utilice la utilidad **sqlcmd** .  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Ssms  
    [scriptfile] [projectfile] [solutionfile]  
    [-S servername] [-d databasename] [-G] [-U username] [-P password]   
    [-E] [-nosplash] [-log [filename]?] [-?]  
```  
  
## <a name="arguments"></a>Argumentos  
 *scriptfile*  
 Especifica uno o más archivos de script para abrirlos. El parámetro debe contener la ruta completa a los archivos.  
  
 *projectfile*  
 Especifica un proyecto de script para abrirlo. El parámetro debe contener la ruta completa al archivo del proyecto de script.  
  
 *solutionfile*  
 Especifica una solución para abrirla. El parámetro debe contener la ruta completa al archivo de solución.  
  
 [**-S** *servername*]  
  Nombre del servidor  
  
 [**-d** *databasename*]  
  Nombre de la base de datos  

 [**-G**] Conexión con la autenticación de Azure Active Directory. El tipo de conexión se determina en función de si se incluye **-P** y **-U**.
 - Si **-U** y **-P** *no* se incluyen, se usa **Active Directory - Integrado** y no se mostrará ningún cuadro de diálogo.
 - Si se incluye tanto **-U** como **-P**, se usa **Active Directory - Contraseña**. **No se recomienda** usar esta opción, ya que hay que especificar una contraseña no cifrada en la línea de comandos, lo cual no es aconsejable.
 - Si se incluye **-U**, pero no **-P**, se abrirá el cuadro de diálogo de autenticación, pero todos los intentos de inicio de sesión serán infructuosos. 

  Es preciso decir que **Active Directory - Universal compatible con MFA** no se admite actualmente. 
  
[**-U** *username*]  
 Nombre de usuario cuando se conecta con "Autenticación de SQL" o "Active Directory - Contraseña".  
  
[**-P** *password*]  
 Contraseña cuando se conecta con "Autenticación de SQL" o "Active Directory - Contraseña".
  
[**-E**]  
 Conectar con la autenticación de Windows.  
  
[**-nosplash**]  
 Impide que [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] muestre el gráfico de la pantalla de presentación mientras se abre. Utilice esta opción cuando se conecte con un equipo que ejecute [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] mediante Terminal Services en una conexión con ancho de banda limitado. Este argumento no distingue entre mayúsculas y minúsculas y puede aparecer antes o después de otros argumentos.  
  
[**-registro***[nombre_de_archivo]?*]  
 Registra la actividad de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] en el archivo especificado para la solución de problemas  
  
[**-?**]  
 Muestra la ayuda de la línea de comandos.  
  
## <a name="remarks"></a>Notas  
 Todos los modificadores son opcionales y están separados por un espacio, excepto los archivos, que están separados por comas. Si no especifica modificadores, **Ssms** abre [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] según se especifica en la configuración de **Opciones** del menú **Herramientas** . Por ejemplo, si en la página **Entorno/General** , la opción **Al iniciar** especifica **Abrir nueva ventana de consulta**, **Ssms** se abrirá con un Editor de consultas en blanco.  
  
 El modificador **-log** debe aparecer al final de la línea de comandos, después de todos los demás modificadores. El argumento de nombre de archivo es opcional. Si se especifica un nombre de archivo y el archivo no existe, este se crea. Si no es posible crear el archivo, por ejemplo, debido a un acceso de escritura insuficiente, el registro se escribe en la ubicación APPDATA no localizada (ver más abajo). Si no se especifica el argumento de nombre de archivo, se escriben dos archivos en la carpeta de datos de la aplicación no localizada del usuario actual. La carpeta de datos de la aplicación no localizada para SQL Server se puede obtener de la variable de entorno APPDATA. Por ejemplo, para SQL Server 2012, la carpeta es \<unidadDelSistema:\Users\\<nombreDeUsuario\>\AppData\Roaming\Microsoft\AppEnv\10.0\\. De forma predeterminada, los dos archivos se denominan ActivityLog.xml y ActivityLog.xsl. El primero contiene los datos del registro de actividad y el segundo es una hoja de estilos XML que permite visualizar correctamente el archivo XML. Haga lo siguiente para ver el archivo de registro en el visor XML predeterminado, como Internet Explorer: haga clic en Inicio y, después, en Ejecutar...; luego, escriba “\<unidadDelSistema>:\Users\\<nombreDeUsuario\>\AppData\Roaming\Microsoft\AppEnv\10.0\ActivityLog.xml” en el campo proporcionado y, por último, pulse Entrar.  
  
 Los archivos que contienen consultas solicitarán la conexión con un servidor si se proporciona información de conexión y el tipo de archivo está asociado con ese tipo de servidor. Por ejemplo, los archivos .sql abrirán una ventana del Editor de consultas de SQL en [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], y los archivos .mdx abrirán una ventana del Editor de consultas MDX en [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Las**Soluciones y proyectos de SQL Server** se abrirán en [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
 La siguiente tabla asigna tipos de servidores a extensiones de archivos.  
  
|Tipo de servidor|Extensión|  
|-----------------|---------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|.sql|  
|SQL Server Analysis Services|.mdx<br /><br /> .xmla|  
  
## <a name="examples"></a>Ejemplos  
 El siguiente script abre [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] desde un símbolo del sistema con la configuración predeterminada:  
  
```  
Ssms  
  
```  
  
 El siguiente script abre [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] desde un símbolo del sistema por medio de *Active Directory - Integrado*:  
  
```  
Ssms.exe -S servername.database.windows.net -G
  
``` 


 El siguiente script abre [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] desde un símbolo del sistema, con autenticación de Windows, con el Editor de código establecido en el servidor `ACCTG and the database AdventureWorks2012,` sin mostrar la pantalla de presentación:  
  
```  
Ssms -E -S ACCTG -d AdventureWorks2012 -nosplash  
  
```  

 El siguiente script abre [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] desde un símbolo del sistema y abre el script de MonthEndQuery:  
  
```  
Ssms "C:\Documents and Settings\username\My Documents\SQL Server Management Studio Projects\FinanceScripts\FinanceScripts\MonthEndQuery.sql"  
  
```  
  
 El siguiente script abre [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] desde un símbolo del sistema y abre el proyecto NewReportsProject en el equipo denominado `developer`:  
  
```  
Ssms "\\developer\fin\ReportProj\ReportProj\NewReportProj.ssmssqlproj"  
  
```  
  
 El siguiente script abre [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] desde un símbolo del sistema y abre la solución MonthlyReports:  
  
```  
Ssms "C:\solutionsfolder\ReportProj\MonthlyReports.ssmssln"  
  
```  
 



## <a name="see-also"></a>Ver también  
 [Usar SQL Server Management Studio](http://msdn.microsoft.com/library/f289e978-14ca-46ef-9e61-e1fe5fd593be)  
  
  
