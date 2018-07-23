---
title: Solucionar problemas de conexión al Motor de base de datos de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 02/07/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- troubleshooting, connecting to Database Engine
- connecting to Database Engine, troubleshooting
ms.assetid: 474c365b-c451-4b07-b636-1653439f4b1f
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: fda5188298c2cae3b56bdb4119ae1bbc96679a2f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32870810"
---
# <a name="troubleshoot-connecting-to-the-sql-server-database-engine"></a>Solucionar problemas de conexión al motor de base de datos de SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Aquí se proporciona una lista exhaustiva de técnicas de solución de problemas que se pueden usar cuando no es posible conectarse al motor de base de datos de SQL Server. Los problemas no están ordenados de más habituales a menos, sino de más básicos a más complejos. Se da por sentado que se está conectando a SQL Server desde otro equipo mediante el protocolo TCP/IP, que es la situación más habitual. Estos pasos están escritos para SQL Server 2016 con SQL Server y las aplicaciones cliente con Windows 10, pero normalmente se aplican a otras versiones de SQL Server y otros sistemas operativos con solo ligeras modificaciones.

Estas instrucciones resultan de especial utilidad con el error "**Conectar con el servidor**", que puede tener el número: 11001 (o 53), gravedad: 20, estado: 0, y con mensajes de error como:

*   "Error relacionado con la red o específico de la instancia mientras se establecía una conexión con el servidor SQL Server. El servidor no se encontró o no estaba accesible. Compruebe que el nombre de instancia es correcto y que SQL Server está configurado para permitir conexiones remotas. " 

*   "(proveedor: proveedor de canalizaciones con nombre, error: 40 - No se pudo abrir la conexión con SQL Server) (Microsoft SQL Server, Error: 53)" o "(proveedor: proveedor de TCP, error: 0 - Este host es desconocido) (Microsoft SQL Server, Error: 11001)" 

Este error normalmente significa que no se encuentra el equipo de SQL Server o que el número de puerto TCP es desconocido, no es el número de puerto correcto o está bloqueado por un firewall.

>  [!TIP]
>  En [Solving Connectivity errors to SQL Server](https://support.microsoft.com/help/4009936/solving-connectivity-errors-to-sql-server) (Resolver errores de conectividad de SQL Server) encontrará una página interactiva de solución de problemas de los servicios de soporte al cliente de [!INCLUDE[msCoName_md](../../includes/msconame-md.md)].

### <a name="not-included"></a>No incluido

* En este tema no se incluye información sobre los errores SSPI. Para ver los errores SSPI, consulte [Cómo solucionar el mensaje de error "No se puede generar contexto SSPI"](http://support.microsoft.com/kb/811889).  
* En este tema no se incluye información sobre los errores Kerberos. Para obtener ayuda, vea [Microsoft Kerberos Configuration Manager para SQL Server](http://www.microsoft.com/download/details.aspx?id=39046).
* En este tema no se incluye información sobre la conectividad de SQL Azure. Para obtener ayuda, vea [Solucionar problemas de conectividad con Microsoft Azure SQL Database](https://support.microsoft.com/help/10085/troubleshooting-connectivity-issues-with-microsoft-azure-sql-database). 

## <a name="gathering-information-about-the-instance-of-sql-server"></a>Recopilación de información sobre la instancia de SQL Server

En primer lugar, debe recopilar información básica sobre el motor de base de datos.

1. Confirme que la instancia del motor de base de datos de SQL Server está instalada y en ejecución.
    1.  Inicie sesión en el equipo que hospeda la instancia de SQL Server.
    2.  Inicie el Administrador de configuración de SQL Server. (El Administrador de configuración se instala automáticamente en el equipo al instalar SQL Server. Las instrucciones para iniciar el Administrador de configuración varían ligeramente según la versión de SQL Server y Windows. Para obtener ayuda para iniciar el Administrador de configuración, vea [Administrador de configuración de SQL Server](../../relational-databases/sql-server-configuration-manager.md)).
    3.  En el panel izquierdo del Administrador de configuración, seleccione **Servicios de SQL Server**. En el panel derecho, confirme que la instancia del motor de base de datos está presente y en ejecución. Una instancia denominada **SQL Server (MSSQLSERVER)** es una instancia predeterminada (sin nombre). Solo puede haber una instancia predeterminada. Los nombres de otras instancias (con nombre) aparecerán en la lista entre paréntesis. SQL Server Express usa el nombre **SQL Server (SQLEXPRESS)** como nombre de instancia, a menos que alguien le diera otra denominación durante la instalación. Anote el nombre de la instancia a la que está intentando conectarse. Además, confirme que la instancia se está ejecutando. Para ello, busque la flecha verde. Si la instancia tiene un cuadrado rojo, haga clic en ella con el botón derecho y luego haga clic en **Iniciar**. Debería volverse verde.
     4. Si está intentando conectarse a una instancia con nombre, asegúrese de que se esté ejecutando el servicio SQL Server Browser.
 

2.  Obtenga la dirección IP del equipo.
    1. En el menú Iniciar, haga clic en **Ejecutar**. En la ventana **Ejecutar** , escriba **cmd**y haga clic en **Aceptar**.
    2.  En la ventana del símbolo del sistema, escriba **ipconfig** y pulse ENTRAR. Anote la dirección **IPv4** y la dirección **IPv6** . (SQL Server puede conectarse mediante el protocolo IP versión 4 anterior o el protocolo IP versión 6 más reciente. La red podría permitir uno o ambos. La mayoría de los usuarios comienza por solucionar los problemas de la dirección **IPv4** . Es más corta y más fácil de escribir).


3.  Obtenga el número de puerto TCP usado por SQL Server. En la mayoría de los casos la conexión al motor de base de datos se realiza desde otro equipo mediante el protocolo TCP.
    1.  Con SQL Server Management Studio en el equipo que ejecuta SQL Server, conéctese a la instancia de SQL Server. En el Explorador de objetos, expanda **Administración**, **Registros de SQL Server**y luego haga doble clic en el registro actual.
    2.  En el Visor de registros, haga clic en el botón **Filtrar** de la barra de herramientas. En el cuadro **El mensaje contiene texto** , escriba **El servidor está escuchando en**, haga clic en **Aplicar filtro**y luego en **Aceptar**.
    3.  Debería aparecer un mensaje similar a **El servidor está escuchando en [ 'any' \<ipv4> 1433]**. Este mensaje indica que esta instancia de SQL Server está escuchando en todas las direcciones IP de este equipo (para IP versión 4) y está escuchando al puerto TCP 1433. (El puerto TCP 1433 suele ser el que usa el motor de base de datos. Solo una instancia de SQL Server puede usar un puerto, por lo que si hay más de una instancia de SQL Server instalada, algunas instancias deben usar otros números de puerto). Anote el número de puerto usado por la instancia de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] a la que está intentando conectarse. 

    >    [!NOTE] 
    >    Probablemente aparezca la dirección IP 127.0.0.1. Se llama dirección de adaptador de bucle invertido y solo se puede conectar a ella desde procesos del mismo equipo. Puede ser útil para solucionar problemas, pero no se puede usar para conectarse desde otro equipo.

## <a name="enable-protocols"></a>Habilitar protocolos

En algunas instalaciones de SQL Server, no se puede conectar al motor de base de datos desde otro equipo a menos que un administrador use el Administrador de configuración para permitirlo. Para habilitar conexiones desde otro equipo:

1.  Abra el Administrador de configuración de SQL Server como se explicó anteriormente. 
2.  En el panel izquierdo del Administrador de configuración, expanda **Configuración de red de SQL Server** y luego seleccione la instancia de SQL Server a la que quiere conectarse. El panel derecho muestra los protocolos de conexión disponibles. Normalmente la memoria compartida está habilitada. Solo se puede usar desde el mismo equipo, por lo que en la mayoría de las instalaciones se deja habilitada. Para conectarse a SQL Server desde otro equipo, normalmente se usa TCP/IP. Si TCP/IP no está habilitado, haga clic con el botón derecho en **TCP/IP**y luego haga clic en **Habilitar**. 
3.  Si modificó la configuración habilitada de cualquier protocolo, debe reiniciar el motor de base de datos. En el panel izquierdo, seleccione **Servicios de SQL Server**. En el panel derecho, haga clic con el botón derecho en la instancia del motor de base de datos y luego haga clic en **Reiniciar**. 

## <a name="testing-tcpip-connectivity"></a>Prueba de la conectividad TCP/IP

La conexión a SQL Server mediante TCP/IP exige que Windows pueda establecerla. Use la herramienta `ping` para probar TCP.
1.  En el menú Iniciar, haga clic en **Ejecutar**. En la ventana **Ejecutar** , escriba **cmd**y haga clic en **Aceptar**. 
2.  En la ventana del símbolo del sistema, escriba `ping` y luego la dirección IP del equipo con SQL Server. Por ejemplo, `ping 192.168.1.101` con una dirección IPv4 o `ping fe80::d51d:5ab5:6f09:8f48%11` con una dirección IPv6. (Debe reemplazar los números después de hacer ping con las direcciones IP que recopiló anteriormente en el equipo). 
3.  Si la red está configurada correctamente, recibirá una respuesta como **Respuesta desde \<dirección IP>** seguida de alguna información adicional. Si recibe un error como **Host de destino inaccesible** o **Tiempo de espera agotado para la solicitud**, significa que TCP/IP no está configurado correctamente. (Compruebe que la dirección IP es correcta y que se escribió correctamente). Los errores en este punto podrían indicar un problema con el equipo cliente, el equipo servidor o algo relacionado con la red, como un enrutador. Internet cuenta con muchos recursos para solucionar problemas de TCP/IP. Un buen lugar para comenzar es este artículo de 2006: [How to Troubleshoot Basic TCP/IP Problems (Cómo solucionar problemas básicos de TCP/IP)](http://support.microsoft.com/kb/169790).
4.  Después, si la prueba de ping mediante la dirección IP fue correcta, compruebe que el nombre del equipo se pueda resolver en la dirección TCP/IP. En el equipo cliente, en la ventana del símbolo del sistema, escriba `ping` y luego el nombre del equipo con SQL Server. Por ejemplo, `ping newofficepc` 
5.  Si pudiera hacer ping a la dirección IP, pero recibe ahora un error como **Host de destino inaccesible.** o **Tiempo de espera agotado para la solicitud**, es posible que tenga información antigua de resolución de nombres (obsoleta) almacenada en caché en el equipo cliente. Escriba `ipconfig /flushdns` para borrar la caché DNS (resolución de nombres dinámica). Luego vuelva a hacer ping al equipo por nombre. Con la caché DNS vacía, el equipo cliente buscará la información más reciente sobre la dirección IP del equipo servidor. 
6.  Si la red está configurada correctamente, recibirá una respuesta como **Respuesta desde \<dirección IP>** seguida de alguna información adicional. Si puede hacer ping correctamente al equipo servidor por dirección IP pero recibe un error como **Host de destino inaccesible** o **Tiempo de espera agotado para la solicitud** al hacer ping por nombre de equipo, la resolución de nombres no está configurada correctamente. (Para obtener más información, vea el artículo de 2006 mencionado anteriormente: [How to Troubleshoot Basic TCP/IP Problems [Cómo solucionar problemas básicos de TCP/IP]](http://support.microsoft.com/kb/169790)). La resolución de nombres correcta no es necesaria para conectarse a SQL Server, pero si no se puede resolver el nombre del equipo en una dirección IP, se debe especificar la dirección IP para realizar las conexiones. No es una situación ideal, pero la resolución de nombres se puede arreglar más adelante.
  
  
## <a name="testing-a-local-connection"></a>Prueba de una conexión local

Antes de solucionar un problema de conexión desde otro equipo, pruebe la capacidad de conectarse desde una aplicación cliente instalada en el equipo con SQL Server. (Esto evitará problemas de firewall). En este procedimiento se usa SQL Server Management Studio. Si no tiene instalado Management Studio, consulte [Descarga de SQL Server Management Studio (SSMS)](../../ssms/download-sql-server-management-studio-ssms.md). (Si no puede instalar Management Studio, puede probar la conexión con la utilidad `sqlcmd.exe` que se instala con el motor de base de datos. Para obtener información sobre `sqlcmd.exe`, vea [sqlcmd (utilidad)](../../tools/sqlcmd-utility.md)).
1.  Inicie sesión en el equipo donde está instalado SQL Server con un inicio de sesión que tenga permiso para acceder a SQL Server. (Durante la instalación, SQL Server necesita que se especifique al menos un inicio de sesión como administrador de SQL Server. Si no conoce ningún administrador, consulte [Conectarse a SQL Server cuando los administradores del sistema no tienen acceso](http://msdn.microsoft.com/library/dd207004.aspx)).
2.   En la página Iniciar, escriba **SQL Server Management Studio**, o bien, en el menú Inicio de versiones anteriores de Windows, seleccione **Todos los programas**, **Microsoft SQL Server**y luego haga clic en **SQL Server Management Studio**.
3.  En el cuadro de diálogo **Conectar con el servidor** , en el cuadro de tipo **Servidor** , seleccione **Motor de base de datos**. En el cuadro **Autenticación** , seleccione **Autenticación de Windows**. En el cuadro **Nombre del servidor** , escriba una de las siguientes opciones:

|Conectar con:|Tipo:|Ejemplo:|
|-----------------|---------------|-----------------|
|Instancia predeterminada|Nombre del equipo|ACCNT27|
|Instancia con nombre|Nombre del equipo\nombre de la instancia|ACCNT27\PAYROLL|

>  [!NOTE] 
>  Al conectarse a SQL Server desde una aplicación cliente del mismo equipo, se usa el protocolo de memoria compartida. La memoria compartida es un tipo de canalización local con nombre, así que a veces se producen errores relacionados con las canalizaciones.

Si aparece un error en este punto, tendrá que resolverlo antes de continuar. Hay muchos aspectos que podrían plantear problemas. El inicio de sesión podría no estar autorizado a conectarse. Podría faltar la base de datos predeterminada.

>    [!NOTE] 
>    Algunos mensajes de error que se pasan al cliente no proporcionan suficiente información para solucionar el problema a propósito. Se trata de una característica de seguridad para evitar proporcionar información sobre SQL Server a cualquier atacante. Para ver la información completa sobre el error, busque en el registro de errores de SQL Server. Allí se proporcionan los detalles. Si recibe el error **18456 Error de inicio de sesión para el usuario**, el tema de los Libros en pantalla [MSSQLSERVER_18456](http://msdn.microsoft.com/library/cc645917) contiene información adicional sobre los códigos de error. Además, el blog de Aaron Bertrand ofrece una lista muy amplia de códigos de error en [Troubleshooting Error 18456 (Solucionar el error 18456)](http://www2.sqlblog.com/blogs/aaron_bertrand/archive/2011/01/14/sql-server-v-next-denali-additional-states-for-error-18456.aspx). Puede ver el registro de errores con SSMS (si se puede conectar), en la sección Administración del Explorador de objetos. De lo contrario, puede ver el registro de errores con el programa Bloc de notas de Windows. La ubicación predeterminada varía en función de la versión y se puede cambiar durante la instalación. La ubicación predeterminada de [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] es `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Log\ERRORLOG`.  

4.   Si puede conectar con la memoria compartida, pruebe la conexión mediante TCP. Puede forzar una conexión TCP si especifica **tcp:** antes del nombre. Por ejemplo:

|Conectar con:|Tipo:|Ejemplo:|
|-----------------|---------------|-----------------|
|Instancia predeterminada|tcp: nombre del equipo|tcp:ACCNT27|
|Instancia con nombre|tcp: nombre del equipo\nombre de la instancia|tcp:ACCNT27\PAYROLL|
  
Si puede conectar con la memoria compartida pero no con TCP, debe solucionar el problema de TCP. Lo más probable es que TCP no esté habilitado. Para habilitar TCP, consulte los pasos anteriores de **Habilitar protocolos** .

5.   Si su objetivo es conectar con una cuenta que no sea la de un administrador, una vez que pueda conectarse como administrador, vuelva a probar la conexión con el inicio de sesión de autenticación de Windows o el inicio de sesión de autenticación de SQL Server que va a usar la aplicación cliente.

## <a name="opening-a-port-in-the-firewall"></a>Apertura de un puerto del firewall

Desde hace ya muchos años, a partir de Windows XP Service Pack 2, Firewall de Windows está activado y bloquea las conexiones desde otros equipos. Para conectar con TCP/IP desde otro equipo, tiene que configurar el firewall en el equipo de SQL Server de modo que permita las conexiones al puerto TCP usado por el motor de base de datos. Como se mencionó anteriormente, la instancia predeterminada suele escuchar en el puerto TCP 1433. Si tiene instancias con nombre o ha cambiado el valor predeterminado, es posible que el puerto TCP [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] escuche en otro puerto. Consulte la sección inicial sobre cómo recopilar la información para determinar el puerto.  
Si se conecta a una instancia con nombre o a un puerto distinto al puerto TCP 1433, también debe abrir el puerto UDP 1434 del servicio SQL Server Browser. Para obtener instrucciones paso a paso sobre la apertura de un puerto de Firewall de Windows, consulte [Configurar Firewall de Windows para el acceso al motor de base de datos](https://msdn.microsoft.com/library/ms175043).

## <a name="testing-the-connection"></a>Prueba de la conexión

Una vez que se pueda conectar con TCP en el mismo equipo, es hora de intentar conectar desde el equipo cliente. En teoría, podría usar cualquier aplicación cliente, pero para evitar más complejidad, instale las herramientas de administración de SQL Server en el cliente y realice el intento con SQL Server Management Studio.

1. En el equipo cliente, con SQL Server Management Studio, intente conectarse mediante la dirección IP y el número de puerto TCP en el formato dirección IP coma número de puerto. Por ejemplo, **192.168.1.101,1433** ; si esto no funciona, es probable que tenga uno de los siguientes problemas:

    * El**ping** de la dirección IP no funciona, lo que indica un problema de configuración general de TCP. Vuelva a la sección **Prueba de la conectividad TCP/IP**. 
    *   SQL Server no está escuchando en el protocolo TCP. Vuelva a la sección **Habilitar protocolos**. 
    *   SQL Server está escuchando en un puerto distinto al especificado. Vuelva a la sección **Recopilación de información sobre la instancia de SQL Server**. 
    *   El firewall está bloqueando el puerto TCP de SQL Server. Vuelva a la sección **Apertura de un puerto del firewall**.


2. Una vez que se pueda conectar con el número de puerto y la dirección IP, intente conectarse con la dirección IP y sin número de puerto. En el caso de una instancia predeterminada, use solo la dirección IP. En el caso de una instancia con nombre, use la dirección IP y el nombre de instancia en el formato dirección IP barra diagonal inversa nombre de instancia, por ejemplo, **192.168.1.101\PAYROLL** ; si esto no funciona, es probable que tenga uno de los siguientes problemas:

    *   Si se conecta a la instancia predeterminada, podría estar escuchando en un puerto distinto al puerto TCP 1433 y el cliente no estaría intentando conectarse al número de puerto correcto.
    *   Si se conecta a una instancia con nombre, el número de puerto no se devuelve al cliente.  

Ambos problemas están relacionados con el servicio SQL Server Browser, que proporciona el número de puerto al cliente. Las soluciones son:

  * Inicie el servicio SQL Server Browser. Vuelva a la sección 1.d de **Recopilación de información sobre la instancia de SQL Server**.
  * El firewall está bloqueando el servicio SQL Server Browser. Abra el puerto UDP 1434 del firewall. Vuelva a la sección **Apertura de un puerto del firewall**. (Asegúrese de estar abriendo un puerto UDP, no un puerto TCP. Son cosas diferentes).
  * Un enrutador está bloqueando la información del puerto UDP 1434. La comunicación UDP (protocolo de datagramas de usuario) no está diseñada para pasar a través de enrutadores. Esto evita que la red se llene de tráfico de baja prioridad. Es posible que pueda configurar el enrutador para reenviar el tráfico UDP. También puede optar por proporcionar siempre el número de puerto al conectarse.
  * Si el equipo cliente usa Windows 7 o Windows Server 2008 (o un sistema operativo más reciente), el sistema operativo cliente podría eliminar el tráfico UDP porque la respuesta del servidor se devuelve desde una dirección IP diferente a la que se consultó. Esta es una característica de seguridad que bloquea la "asignación de origen no estricta". Para obtener más información, consulte la sección **Varias direcciones IP de servidor** del tema de los Libros en pantalla [Solucionar problemas de tiempo de espera expirado](http://msdn.microsoft.com/library/ms190181.aspx). Se trata de un artículo de SQL Server 2008 R2, pero las entidades de seguridad aún son válidas. Es posible que pueda configurar el cliente para usar la dirección IP correcta. También puede optar por proporcionar siempre el número de puerto al conectarse.
     
3. Una vez que se pueda conectar con la dirección IP (o la dirección IP y el nombre de instancia de una instancia con nombre), intente conectarse con el nombre de equipo (o el nombre de equipo y el nombre de instancia de una instancia con nombre). Coloque `tcp:` delante del nombre del equipo para forzar una conexión TCP/IP. Por ejemplo, en el caso de la instancia predeterminada en un equipo denominado `ACCNT27`, use `tcp:ACCNT27` ; en el caso de una instancia con nombre denominada `PAYROLL`en ese equipo, use `tcp:ACCNT27\PAYROLL` . Si puede conectarse con la dirección IP pero no con el nombre de equipo, entonces tiene un problema de resolución de nombres. Vuelva a la sección 4 de **Prueba de la conectividad TCP/IP**.

4. Una vez que se conecte mediante el nombre de equipo al forzar TCP, intente conectarse con el nombre de equipo pero sin forzar TCP. Por ejemplo, en el caso de una instancia predeterminada, use solo el nombre de equipo como `CCNT27` ; en el caso de una instancia con nombre, use el nombre de equipo y el nombre de instancia como `ACCNT27\PAYROLL` . Si puede conectarse al forzar TCP, pero no sin hacerlo, es probable que el cliente esté usando otro protocolo (por ejemplo, canalizaciones con nombre).

    1. En el equipo cliente, en el panel izquierdo del Administrador de configuración de SQL Server, expanda **Configuración** *version* **Configuration**, and then select **Client Protocols**.
    2. En el panel derecho, asegúrese de que TCP/IP esté habilitado. Si TCP/IP está deshabilitado, haga clic con el botón derecho en **TCP/IP** y luego haga clic en **Habilitar**.
    3. Asegúrese de que el orden de protocolo de TCP/IP sea un número menor que el de los protocolos de canalizaciones con nombre (o VIA en versiones anteriores). Por lo general, debería dejar la memoria compartida como orden 1 y TCP/IP como orden 2. La memoria compartida solo se usa cuando el cliente y SQL Server se están ejecutando en el mismo equipo. Todos los protocolos habilitados se prueban por orden hasta que se establece la conexión, aunque la memoria compartida se omite cuando la conexión no está en el mismo equipo. 

