---
title: SqlPackage.exe | Microsoft Docs
ms.custom:
- SSDT
ms.date: 2018-06-27
ms.prod: sql-non-specified
ms.reviewer: alayu; sstein
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 198198e2-7cf4-4a21-bda4-51b36cb4284b
caps.latest.revision: 53
author: pensivebrian
ms.author: broneill
manager: craigg
ms.openlocfilehash: 4c206a60e0b494d4e060864eefcb50424d316938
ms.sourcegitcommit: 0dff9dd43e80eee900eb92d25df9ca18397f3485
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2018
ms.locfileid: "37080083"
---
# <a name="sqlpackageexe"></a>SqlPackage.exe

**SqlPackage.exe** es una utilidad de línea de comandos que automatiza las siguientes tareas de desarrollo de base de datos:  
  
- [Extraer](#help-for-the-extract-action): crea un archivo de instantáneas de base de datos (.dacpac) a partir de una SQL Database de SQL Server o Microsoft Azure.  
  
- [Publicar](#publish-parameters-properties-and-sqlcmd-variables): actualiza de forma incremental un esquema de la base de datos para que coincida con el esquema de un archivo .dacpac de origen. Si no existe la base de datos en el servidor, la operación de publicación la crea. En caso contrario, se actualiza una base de datos existente.  
  
- [Exportar](#export-parameters-and-properties): exporta una base de datos activa, incluidos los datos de usuario y el esquema de base de datos, desde SQL Server o Azure SQL Database a un paquete BACPAC (archivo.bacpac).  
  
- [Importar](#import-parameters-and-properties): importa los datos de esquema y tabla de un paquete BACPAC en una nueva base de datos de usuario en una instancia de SQL Server o Azure SQL Database.  
  
- [DeployReport](#deployreport-parameters-and-properties): crea un informe XML de los cambios que una acción de publicación realizarían.  
  
- [DriftReport](#driftreport-parameters): crea un informe XML de los cambios que se han realizado en una base de datos registrada desde que se registró por última vez.  
  
- [Script](#script-parameters-and-properties): crea un script de actualización incremental de Transact-SQL que actualiza el esquema de un destino para que coincida con el esquema de un origen.  
  
La línea de comandos **SqlPackage.exe** permite especificar estas acciones junto con parámetros y propiedades específicos de cada acción.  

**[Descargar la última versión](sqlpackage-download.md)**. Para obtener más información acerca de la versión más reciente, consulte el [notas de la versión](sqlpackage-release-notes.md).
  
## <a name="command-line-syntax"></a>Sintaxis de línea de comandos

**SqlPackage.exe** inicia las acciones especificadas usando los parámetros, las propiedades y las variables de SQLCMD especificadas en la línea de comandos.  
  
```
SqlPackage {parameters}{properties}{SQLCMD Variables}  
```
  
### <a name="help-for-the-extract-action"></a>Ayuda para la acción de extracción

|Parámetro|Forma corta|Valor|Descripción|
|---|---|---|---|
|**/Action:**|**/a**|Extract|Especifica la acción que se va a realizar. |
|**/Diagnostics:**|**/d**|{True&#124;False}|Especifica si la salida del registro de diagnóstico es la consola. De forma predeterminada es False. |
|**/ DiagnosticsFile:**|**/DF**|{string}|Especifica un archivo para almacenar los registros de diagnóstico. |
|**/ OverwriteFiles:**|**/of**|{True&#124;False}|Especifica si sqlpackage.exe debe sobrescribir los archivos existentes. Si se especifica False, sqlpackage.exe anula la acción si se encuentra un archivo existente. El valor predeterminado es True. |
|**/Properties:**|**/p**|{PropertyName}={Value}|Especifica un par de nombre y valor para una propiedad específica de acción; {PropertyName}={Value}. Remítase a la ayuda de una acción determinada para ver los nombres de propiedad de esa acción. Ejemplo: / Action sqlpackage.exe: publicar /?. |
|**/Quiet:**|**/q**|{True&#124;False}|Especifica si se suprimen los comentarios detallados. De forma predeterminada es False. |
|**/ SourceConnectionString:**|**/ SCS**|{string}|Especifica una cadena de conexión válida de SQL Server o SQL Azure para la base de datos de origen. Si se especifica este parámetro, lo usan exclusivamente los demás parámetros de origen. |
|**/SourceDatabaseName:**|**Export /**|{string}|Define el nombre de la base de datos de origen. |
|**/ SourceEncryptConnection:**|**/sec**|{True&#124;False}|Especifica si se debe usar cifrado SQL para la conexión de base de datos de origen. |
|**/SourcePassword:**|**/sp**|{string}|En escenarios de autenticación de SQL Server, define la palabra clave que se va a usar para acceder a la base de datos de origen. |
|**/ Nombreservidororigen:**|**/ssn**|{string}|Define el nombre del servidor que hospeda la base de datos de origen. |
|**/ SourceTimeout:**|**/st**|{int}|Especifica el tiempo de espera para establecer una conexión con la base de datos de origen, en segundos. |
|**/ SourceTrustServerCertificate:**|**/stsc**|{True&#124;False}|Especifica si se usará SSL para cifrar la conexión con la base de datos de origen y no tener que recorrer la cadena de certificados para validar la confianza. |
|**/SourceUser:**|**/su**|{string}|En escenarios de autenticación de SQL Server, define el usuario de SQL Server que se va a usar para acceder a la base de datos de origen. |
|**/ TargetFile:**|**/tf**|{string}| Especifica un archivo de destino (es decir, un archivo .dacpac) que se usará como el destino de acción en lugar de una base de datos. Si se usa este parámetro, el resto de parámetros de destino no serán válidos. Este parámetro será no válida para las acciones que admiten solo los destinos de base de datos.| 
|**/ TenantId:**|**/tid**|{string}|Representa el nombre de dominio o Id. de inquilino de Azure AD. Esta opción es necesaria para admitir a invitado o importa usuarios de Azure AD, así como cuentas de Microsoft como outlook.com, hotmail.com o live.com. Si se omite este parámetro, se usará de forma predeterminada, el Id. de inquilino para Azure AD, suponiendo que el usuario autenticado es un usuario nativo para este anuncio. Sin embargo, en este caso no se admiten cualquier invitado o los usuarios importados o cuentas de Microsoft hospedadas en este Azure AD y se producirá un error en la operación. <br/> Para obtener más información acerca de la autenticación Universal de Active Directory, consulte [autenticación Universal con SQL Database y SQL Data Warehouse (compatibilidad de SSMS con MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|
|**/ UniversalAuthentication:**|**/ua**|{True&#124;False}|Especifica si se debe usar la autenticación Universal. Cuando se establece en True, el protocolo de autenticación interactiva está activado compatible con MFA. Esta opción también puede utilizarse para la autenticación de Azure AD sin MFA, mediante un protocolo interactivo pedir al usuario que escriba su nombre de usuario y contraseña o autenticación integrada (credenciales de Windows). Cuando /UniversalAuthentication se establece en True, no se puede especificar ninguna autenticación de Azure AD en SourceConnectionString (/ scs). Cuando /UniversalAuthentication se establece en False, se debe especificar la autenticación de Azure AD en SourceConnectionString (/ scs). <br/> Para obtener más información acerca de la autenticación Universal de Active Directory, consulte [autenticación Universal con SQL Database y SQL Data Warehouse (compatibilidad de SSMS con MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|

### <a name="properties-specific-to-the-extract-action"></a>Propiedades específicas de la acción de extracción

|Propiedad|Valor|Descripción|
|---|---|---|
|**/p:**|CommandTimeout = (INT32 "60")|Especifica el tiempo de espera de comando en segundos cuando se ejecutan consultas en SQL Server.|
|**/p:**|DacApplicationDescription=(STRING)|Define la descripción de la aplicación que se va a guardar en los metadatos del DACPAC.|
|**/p:**|DacApplicationName=(STRING)|Define el nombre de la aplicación que se va a guardar en los metadatos del DACPAC. El valor predeterminado es el nombre de la base de datos.|
|**/p:**|DacMajorVersion = (INT32 '1')|Define la versión principal que se va a guardar en los metadatos del DACPAC.|
|**/p:**|DacMinorVersion = (INT32 "0")|Define la versión secundaria que se va a guardar en los metadatos del DACPAC.|
|**/p:**|ExtractAllTableData=(BOOLEAN)|Indica si se extraen los datos de todas las tablas de usuario. Si es 'true', se extraen los datos de todas las tablas de usuario y no se puede especificar las tablas de usuario individuales para extraer datos. Si es 'false', especifique una o varias tablas de usuario para extraer los datos.|
|**/p:**|ExtractApplicationScopedObjectsOnly = (booleano ' True')|Si se establece en true, solo se extraen los objetos con ámbito de aplicación para el origen especificado. Si se establece en false, se extraen todos los objetos para el origen especificado.|
|**/p:**|ExtractReferencedServerScopedElements = (booleano ' True')|Si se establece en true, se extraen los objetos de inicio de sesión, de auditoría de servidor y de credencial a los que hacen referencia los objetos de base de datos de origen.|
|**/p:**|ExtractUsageProperties=(BOOLEAN)|Especifica si las propiedades de uso, como el número de filas de tabla o el tamaño del índice, se extraerán de la base de datos.|
|**/p:**|IgnoreExtendedProperties=(BOOLEAN)|Especifica si se deben omitir las propiedades extendidas.|
|**/p:**|IgnorePermissions = (booleano ' True')|Especifica si se deben omitir los permisos.|
|**/p:**|IgnoreUserLoginMappings=(BOOLEAN)|Especifica si se omiten las relaciones entre usuarios e inicios de sesión.|
|**/p:**|Almacenamiento = ({archivo&#124;memoria} 'File')|Especifica el tipo de almacenamiento de seguridad para el modelo de esquema que se usa durante la extracción.|
|**/p:**|TableData=(STRING)|Indica la tabla desde el que se va a extraer datos. Especifique el nombre de tabla con o sin los corchetes que rodean las partes del nombre en el siguiente formato: nombre_esquema.identificador_tabla.|
|**/p:**|VerifyExtraction=(BOOLEAN)|Especifica si el archivo DACPAC que se extrajo debe comprobarse.|

## <a name="publish-parameters-properties-and-sqlcmd-variables"></a>Parámetros, propiedades y variables SQLCMD de publicación

Una operación de publicación de SqlPackage.exe actualiza incrementalmente el esquema de una base de datos de destino para que coincida con la estructura de una base de datos de origen. Al publicar un paquete de implementación que contiene datos de usuario de todas las tablas o un subconjunto de ellas, se actualizan los datos de la tabla, además del esquema. La implementación de datos sobrescribe el esquema y los datos de las tablas existentes de la base de datos de destino. La implementación de datos no modificará el esquema ni los datos de la base de datos de destino para las tablas que no se incluyen en el paquete de implementación.  

### <a name="help-for-publish-action"></a>Ayuda para la acción de publicación

|Parámetro|Forma corta|Valor|Descripción|
|---|---|---|---|
|**/Action:**|**/a**|Publicar|Especifica la acción que se va a realizar. |
|**/ AzureKeyVaultAuthMethod:**|**/akv**|{Interactivo&#124;ClientIdSecret}|Especifica qué método de autenticación se usa para acceder a Azure Key Vault |
|**/ClientId:**|**/CID**|{string}|Especifica el id. de cliente que se usará en la autenticación con Azure Key Vault, cuando sea necesario. |
|**/Diagnostics:**|**/d**|{True&#124;False}|Especifica si la salida del registro de diagnóstico es la consola. De forma predeterminada es False. |
|**/ DiagnosticsFile:**|**/DF**|{string}|Especifica un archivo para almacenar los registros de diagnóstico. |
|**/ OverwriteFiles:**|**/of**|{True&#124;False}|Especifica si sqlpackage.exe debe sobrescribir los archivos existentes. Si se especifica False, sqlpackage.exe anula la acción si se encuentra un archivo existente. El valor predeterminado es True. |
|**/Profile:**|**/pr**|{string}|Especifica la ruta de acceso a un archivo para un perfil de publicación DAC. El perfil define una colección de propiedades y variables que se usarán cuando se generen resultados.|
|**/Properties:**|**/p**|{PropertyName}={Value}|Especifica un par de nombre y valor para una propiedad específica de acción; {PropertyName}={Value}. Remítase a la ayuda de una acción determinada para ver los nombres de propiedad de esa acción. Ejemplo: / Action sqlpackage.exe: publicar /?.|
|**/Quiet:**|**/q**|{True&#124;False}|Especifica si se suprimen los comentarios detallados. De forma predeterminada es False.|
|**/Secret:**|**/secr**|{string}|Especifica el secreto de cliente que se usará en la autenticación con Azure Key Vault, cuando sea necesario. |
|**/ SourceConnectionString:**|**/ SCS**|{string}|Especifica una cadena de conexión válida de SQL Server o SQL Azure para la base de datos de origen. Si se especifica este parámetro, lo usan exclusivamente los demás parámetros de origen. |
|**/SourceDatabaseName:**|**Export /**|{string}|Define el nombre de la base de datos de origen. |
|**/ SourceEncryptConnection:**|**/sec**|{True&#124;False}|Especifica si se debe usar cifrado SQL para la conexión de base de datos de origen. |
|**/ SourceFile:**|**/sf**|{string}|Especifica un archivo de origen que se usará como origen de la acción en lugar de una base de datos. Si se usa este parámetro, el resto de parámetros de origen no serán válidos. |
|**/SourcePassword:**|**/sp**|{string}|En escenarios de autenticación de SQL Server, define la palabra clave que se va a usar para acceder a la base de datos de origen. |
|**/ Nombreservidororigen:**|**/ssn**|{string}|Define el nombre del servidor que hospeda la base de datos de origen. |
|**/ SourceTimeout:**|**/st**|{int}|Especifica el tiempo de espera para establecer una conexión con la base de datos de origen, en segundos. |
|**/ SourceTrustServerCertificate:**|**/stsc**|{True&#124;False}|Especifica si se usará SSL para cifrar la conexión con la base de datos de origen y no tener que recorrer la cadena de certificados para validar la confianza. |
|**/SourceUser:**|**/su**|{string}|En escenarios de autenticación de SQL Server, define el usuario de SQL Server que se va a usar para acceder a la base de datos de origen. |
|**/ TargetConnectionString:**|**/TCS**|{string}|Especifica una cadena de conexión válida de SQL Server o SQL Azure para la base de datos de destino. Si se especifica este parámetro, lo usan exclusivamente los demás parámetros de destino. |
|**/TargetDatabaseName:**|**/tdn**|{string}|Especifica una invalidación del nombre de la base de datos que es el destino de la acción sqlpackage.exe. |
|**/ TargetEncryptConnection:**|**/Tec**|{True&#124;False}|Especifica si se debe usar el cifrado de SQL para la conexión de base de datos de destino. |
|**/ ContraseñaDestino:**|**/tp**|{string}|En escenarios de autenticación de SQL Server, define la palabra clave que se va a usar para acceder a la base de datos de destino. |
|**/ TargetServerName:**|**/tsn**|{string}|Define el nombre del servidor que hospeda la base de datos de destino. |
|**/ TargetTimeout:**|**/tt**|{int}|Especifica el tiempo de espera para establecer una conexión con la base de datos de destino, en segundos. Para Azure AD, se recomienda que este valor sea mayor o igual a 30 segundos.|
|**/ TargetTrustServerCertificate:**|**/ttsc**|{True&#124;False}|Especifica si se usará SSL para cifrar la conexión con la base de datos de destino y no tener que recorrer la cadena de certificados para validar la confianza. |
|**/ TargetUser:**|**/tu**|{string}|En escenarios de autenticación de SQL Server, define el usuario de SQL Server que se va a usar para acceder a la base de datos de destino. |
|**/ TenantId:**|**/tid**|{string}|Representa el nombre de dominio o Id. de inquilino de Azure AD. Esta opción es necesaria para admitir a invitado o importa usuarios de Azure AD, así como cuentas de Microsoft como outlook.com, hotmail.com o live.com. Si se omite este parámetro, se usará de forma predeterminada, el Id. de inquilino para Azure AD, suponiendo que el usuario autenticado es un usuario nativo para este anuncio. Sin embargo, en este caso no se admiten cualquier invitado o los usuarios importados o cuentas de Microsoft hospedadas en este Azure AD y se producirá un error en la operación. <br/> Para obtener más información acerca de la autenticación Universal de Active Directory, consulte [autenticación Universal con SQL Database y SQL Data Warehouse (compatibilidad de SSMS con MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|
|**/ UniversalAuthentication:**|**/ua**|{True&#124;False}|Especifica si se debe usar la autenticación Universal. Cuando se establece en True, el protocolo de autenticación interactiva está activado compatible con MFA. Esta opción también puede utilizarse para la autenticación de Azure AD sin MFA, mediante un protocolo interactivo pedir al usuario que escriba su nombre de usuario y contraseña o autenticación integrada (credenciales de Windows). Cuando /UniversalAuthentication se establece en True, no se puede especificar ninguna autenticación de Azure AD en SourceConnectionString (/ scs). Cuando /UniversalAuthentication se establece en False, se debe especificar la autenticación de Azure AD en SourceConnectionString (/ scs). <br/> Para obtener más información acerca de la autenticación Universal de Active Directory, consulte [autenticación Universal con SQL Database y SQL Data Warehouse (compatibilidad de SSMS con MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|
|**/Variables:**|**/v**|{PropertyName}={Value}|Especifica un par de nombre y valor para una variable específica de acción; {VariableName}={Value}. El archivo DACPAC contiene la lista de variables SQLCMD válidas. Se produce un error si no se facilita un valor para cada variable. |

### <a name="properties-specific-to-the-publish-action"></a>Propiedades específicas de la acción de publicación

|Propiedad|Valor|Descripción|
|---|---|---|
|**/p:**|AdditionalDeploymentContributorArguments=(STRING)|Especifica los argumentos de colaborador de implementación adicionales para los colaboradores de implementación. Debe ser una lista de valores delimitada por punto y coma.|
|**/p:**|AdditionalDeploymentContributors=(STRING)|Especifica colaboradores de implementación adicionales que se deben ejecutar cuando se implementa el dacpac. Debe ser una lista delimitada por punto y coma de nombres completos o identificadores de los colaboradores de compilación.|
|**/p:**|AllowDropBlocking Assemblies=(BOOLEAN)|Esta propiedad se usa en la implementación de SqlClr para hacer que cualquier ensamblado de bloqueo se quite como parte del plan de implementación. De forma predeterminada, cualquier ensamblado de bloqueo o de referencia bloqueará la actualización de un ensamblado si el ensamblado de referencia tiene que quitarse.|
|**/p:**|AllowIncompatiblePlatform=(BOOLEAN)|Especifica si se intenta la acción a pesar de las posibles plataformas de SQL Server incompatibles.|
|**/p:**|AllowUnsafeRowLevelSecurityDataMovement=(BOOLEAN)|No bloquee la transferencia de datos en una tabla con Seguridad de nivel de fila si esta propiedad está establecida en true. El valor predeterminado es False.|
|**/p:**|BackupDatabaseBeforeChanges=(BOOLEAN)|Hace una copia de seguridad de la base de datos antes de implementar ningún cambio.|
|**/p:**|BlockOnPossibleDataLoss = (booleano ' True')|Especifica que se debe finalizar el episodio de publicación si existiera la posibilidad de que se perdieran datos a causa de la operación de publicación.|
|**/p:**|BlockWhenDriftDetected = (booleano ' True')|Especifica si bloquear la actualización de una base de datos cuyo esquema ha dejado de corresponderse con su registro o no está registrada.|
|**/p:**|CommandTimeout = (INT32 "60")|Especifica el tiempo de espera de comando en segundos cuando se ejecutan consultas en SQL Server.|
|**/p:**|CommentOutSetVarDeclarations=(BOOLEAN)|Especifica si la declaración de las variables SETVAR se incluyen entre comentarios en el script de publicación generado. Puede optar por esta opción si planea usar una herramienta como SQLCMD.EXE para especificar los valores de la línea de comandos al publicar.|
|**/p:**|CompareUsingTargetCollation=(BOOLEAN)|Esta configuración determina la forma en que se trata la intercalación de la base de datos durante la implementación; de forma predeterminada, la intercalación de la base de datos de destino se actualizará si no coincide con la especificada por el origen. Cuando se ha establecido esta opción, se usará la intercalación de la base de datos (o servidor) de destino.|
|**/p:**|CreateNewDatabase=(BOOLEAN)|Especifica si la base de datos de destino debe actualizarse o si se va a quitar para volver a crearse al publicar en una base de datos.|
|**/p:**|DatabaseEdition = ({Basic&#124;estándar&#124;Premium&#124;predeterminada} 'Default')|Define la edición de una base de datos de SQL Azure.|
|**/p:**|DatabaseMaximumSize=(INT32)|Define el tamaño máximo en GB de una instancia de Azure SQL Database.|
|**/p:**|DatabaseServiceObjective=(STRING)|Define el nivel de rendimiento de una instancia de Azure SQL Database, como "P0" o "S1".|
|**/p:**|DeployDatabaseInSingleUserMode=(BOOLEAN)|Si se establece en True, la base de datos se establecerá en modo de usuario único antes de implementarse.|
|**/p:**|DisableAndReenableDdlTriggers = (booleano ' True')|Especifica si los desencadenadores del Lenguaje de definición de datos (DDL) se deshabilitan al principio del proceso de publicación y se vuelven a habilitar al final de la acción de publicación.|
|**/p:**|DoNotAlterChangeDataCaptureObjects = (booleano ' True')|Si se establece en true, los objetos de captura de datos modificados no se verán alterados.|
|**/p:**|DoNotAlterReplicatedObjects = (booleano ' True')|Especifica si los objetos que se replican se van a identificar durante la comprobación.|
|**/p:**|DoNotDropObjectType=(STRING)|Un tipo de objeto que no debería quitarse si DropObjectsNotInSource es true. Los nombres de tipo de objeto válidos son: Aggregates, ApplicationRoles, Assemblies, AsymmetricKeys, BrokerPriorities, Certificates, ColumnEncryptionKeys, ColumnMasterKeys, Contracts, DatabaseRoles, DatabaseTriggers, Defaults, ExtendedProperties, ExternalDataSources, ExternalFileFormats, ExternalTables, Filegroups, FileTables, FullTextCatalogs, FullTextStoplists, MessageTypes, PartitionFunctions, PartitionSchemes, Permissions, Queues, RemoteServiceBindings, RoleMembership, Rules, ScalarValuedFunctions, SearchPropertyLists, SecurityPolicies, Sequences, Services, Signatures, StoredProcedures, SymmetricKeys, Synonyms, Tables, TableValuedFunctions, UserDefinedDataTypes, UserDefinedTableTypes, ClrUserDefinedTypes, Users, Views, XmlSchemaCollections, Audits, Credentials, CryptographicProviders, DatabaseAuditSpecifications, DatabaseScopedCredentials, Endpoints, ErrorMessages, EventNotifications, EventSessions, LinkedServerLogins, LinkedServers, Logins, Routes, ServerAuditSpecifications, ServerRoleMembership, ServerRoles, ServerTriggers.|
|**/p:**|DoNotDropObjectTypes=(STRING)|Lista delimitada por puntos y coma de tipos de objetos que no deberían quitarse si DropObjectsNotInSource es true. Los nombres de tipo de objeto válidos son: Aggregates, ApplicationRoles, Assemblies, AsymmetricKeys, BrokerPriorities, Certificates, ColumnEncryptionKeys, ColumnMasterKeys, Contracts, DatabaseRoles, DatabaseTriggers, Defaults, ExtendedProperties, ExternalDataSources, ExternalFileFormats, ExternalTables, Filegroups, FileTables, FullTextCatalogs, FullTextStoplists, MessageTypes, PartitionFunctions, PartitionSchemes, Permissions, Queues, RemoteServiceBindings, RoleMembership, Rules, ScalarValuedFunctions, SearchPropertyLists, SecurityPolicies, Sequences, Services, Signatures, StoredProcedures, SymmetricKeys, Synonyms, Tables, TableValuedFunctions, UserDefinedDataTypes, UserDefinedTableTypes, ClrUserDefinedTypes, Users, Views, XmlSchemaCollections, Audits, Credentials, CryptographicProviders, DatabaseAuditSpecifications, DatabaseScopedCredentials, Endpoints, ErrorMessages, EventNotifications, EventSessions, LinkedServerLogins, LinkedServers, Logins, Routes, ServerAuditSpecifications, ServerRoleMembership, ServerRoles, ServerTriggers.|
|**/p:**|DropConstraintsNotInSource = (booleano ' True')|Especifica si las restricciones que no existen en el archivo de la instantánea de base de datos (.dacpac) se van a quitar de la base de datos de destino al publicar en una base de datos.|
|**/p:**|DropDmlTriggersNotInSource = (booleano ' True')|Especifica si los desencadenadores DML que no existen en el archivo de la instantánea de base de datos (.dacpac) se van a quitar de la base de datos de destino al publicar en una base de datos.|
|**/p:**|DropExtendedPropertiesNotInSource = (booleano ' True')|Especifica si las propiedades extendidas que no existen en el archivo de instantánea de base de datos (.dacpac) se quitarán de la base de datos de destino al publicar en una base de datos.|
|**/p:**|DropIndexesNotInSource = (booleano ' True')|Especifica si los índices que no existen en el archivo de la instantánea de base de datos (.dacpac) se van a quitar de la base de datos de destino al publicar en una base de datos.|
|**/p:**|DropObjectsNotInSource=(BOOLEAN)|Especifica si los objetos que no existen en el archivo de instantánea de base de datos (.dacpac) se quitarán de la base de datos de destino al publicar en una base de datos. Este valor tiene prioridad sobre DropExtendedProperties.|
|**/p:**|DropPermissionsNotInSource=(BOOLEAN)|Especifica si los permisos que no existen en el archivo de la instantánea de base de datos (.dacpac) se van a quitar de la base de datos de destino al publicar actualizaciones en una base de datos.|
|**/p:**|DropRoleMembersNotInSource=(BOOLEAN)|Especifica si los miembros de rol que no se definieron en el archivo de la instantánea de base de datos (.dacpac) se van a quitar de la base de datos de destino al publicar actualizaciones en una base de datos.|
|**/p:**|DropStatisticsNotInSource = (booleano ' True')|Especifica si las estadísticas que no existen en el archivo de instantánea de base de datos (.dacpac) se quitarán de la base de datos de destino al publicar en una base de datos.|
|**/p:**|ExcludeObjectType=(STRING)|Un tipo de objeto que se debe omitir durante la implementación. Los nombres de tipo de objeto válidos son: Aggregates, ApplicationRoles, Assemblies, AsymmetricKeys, BrokerPriorities, Certificates, ColumnEncryptionKeys, ColumnMasterKeys, Contracts, DatabaseRoles, DatabaseTriggers, Defaults, ExtendedProperties, ExternalDataSources, ExternalFileFormats, ExternalTables, Filegroups, FileTables, FullTextCatalogs, FullTextStoplists, MessageTypes, PartitionFunctions, PartitionSchemes, Permissions, Queues, RemoteServiceBindings, RoleMembership, Rules, ScalarValuedFunctions, SearchPropertyLists, SecurityPolicies, Sequences, Services, Signatures, StoredProcedures, SymmetricKeys, Synonyms, Tables, TableValuedFunctions, UserDefinedDataTypes, UserDefinedTableTypes, ClrUserDefinedTypes, Users, Views, XmlSchemaCollections, Audits, Credentials, CryptographicProviders, DatabaseAuditSpecifications, DatabaseScopedCredentials, Endpoints, ErrorMessages, EventNotifications, EventSessions, LinkedServerLogins, LinkedServers, Logins, Routes, ServerAuditSpecifications, ServerRoleMembership, ServerRoles, ServerTriggers.|
|**/p:**|ExcludeObjectTypes=(STRING)|Lista delimitada por puntos y coma de tipos de objetos que se deben omitir durante la implementación. Los nombres de tipo de objeto válidos son: Aggregates, ApplicationRoles, Assemblies, AsymmetricKeys, BrokerPriorities, Certificates, ColumnEncryptionKeys, ColumnMasterKeys, Contracts, DatabaseRoles, DatabaseTriggers, Defaults, ExtendedProperties, ExternalDataSources, ExternalFileFormats, ExternalTables, Filegroups, FileTables, FullTextCatalogs, FullTextStoplists, MessageTypes, PartitionFunctions, PartitionSchemes, Permissions, Queues, RemoteServiceBindings, RoleMembership, Rules, ScalarValuedFunctions, SearchPropertyLists, SecurityPolicies, Sequences, Services, Signatures, StoredProcedures, SymmetricKeys, Synonyms, Tables, TableValuedFunctions, UserDefinedDataTypes, UserDefinedTableTypes, ClrUserDefinedTypes, Users, Views, XmlSchemaCollections, Audits, Credentials, CryptographicProviders, DatabaseAuditSpecifications, DatabaseScopedCredentials, Endpoints, ErrorMessages, EventNotifications, EventSessions, LinkedServerLogins, LinkedServers, Logins, Routes, ServerAuditSpecifications, ServerRoleMembership, ServerRoles, ServerTriggers.|
|**/p:**|GenerateSmartDefaults=(BOOLEAN)|Proporciona automáticamente un valor predeterminado cuando se actualiza una tabla que contiene datos con una columna que no admite valores NULL.|
|**/p:**|IgnoreAnsiNulls = (booleano ' True')|Especifica si las diferencias en la configuración ANSI NULLS se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreAuthorizer=(BOOLEAN)|Especifica si las diferencias en el autorizador se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreColumnCollation=(BOOLEAN)|Especifica si las diferencias en las intercalaciones de columnas se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreColumnOrder=(BOOLEAN)|Especifica si hay que omitir las diferencias en el orden de las columnas de una tabla o bien hay que actualizar al publicar en una base de datos.|
|**/p:**|IgnoreComments=(BOOLEAN)|Especifica si las diferencias en los comentarios se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreCryptographicProviderFilePath = (booleano ' True')|Especifica si las diferencias en la ruta de acceso del archivo del proveedor de servicios criptográficos se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreDdlTriggerOrder=(BOOLEAN)|Especifica si las diferencias en el orden de los desencadenadores de Data Definition Language (DDL) se deben ignorar o actualizar al publicar en una base de datos o en un servidor.|
|**/p:**|IgnoreDdlTriggerState=(BOOLEAN)|Especifica si las diferencias en el estado habilitado o deshabilitado de los desencadenadores de Data Definition Language (DDL) se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreDefaultSchema=(BOOLEAN)|Especifica si las diferencias en el esquema predeterminado se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreDmlTriggerOrder=(BOOLEAN)|Especifica si las diferencias en el orden de los desencadenadores del lenguaje de manipulación de datos (DML) se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreDmlTriggerState=(BOOLEAN)|Especifica si las diferencias en el estado habilitado o deshabilitado de los desencadenadores de DML se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreExtendedProperties=(BOOLEAN)|Especifica si las diferencias en las propiedades extendidas se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreFileAndLogFilePath = (booleano ' True')|Especifica si las diferencias en las rutas de acceso de los archivos y archivos de registro se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreFilegroupPlacement = (booleano ' True')|Especifica si las diferencias en la colocación de objetos en FILEGROUPs se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreFileSize = (booleano ' True')|Especifica si las diferencias en los tamaños de archivo se deben ignorar o si debe generarse una advertencia al publicar en una base de datos.|
|**/p:**|IgnoreFillFactor = (booleano ' True')|Especifica si las diferencias en el factor de relleno del almacenamiento de índices se deben ignorar o si debe generarse una advertencia al publicar en una base de datos.|
|**/p:**|IgnoreFullTextCatalogFilePath = (booleano ' True')|Especifica si las diferencias en la ruta de acceso al archivo del catálogo de texto completo se deben ignorar o si debe generarse una advertencia al publicar en una base de datos.|
|**/p:**|IgnoreIdentitySeed=(BOOLEAN)|Especifica si las diferencias en el valor de inicialización de una columna de identidad se deben ignorar o actualizar al publicar actualizaciones en una base de datos.|
|**/p:**|IgnoreIncrement=(BOOLEAN)|Especifica si las diferencias en el incremento de una columna de identidad se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreIndexOptions=(BOOLEAN)|Especifica si las diferencias en las opciones de índice se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreIndexPadding = (booleano ' True')|Especifica si las diferencias en el relleno de índice se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreKeywordCasing = (booleano ' True')|Especifica si las diferencias en el uso de mayúsculas y minúsculas en palabras clave se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreLockHintsOnIndexes=(BOOLEAN)|Especifica si las diferencias en las sugerencias de bloqueo en los índices se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreLoginSids = (booleano ' True')|Especifica si las diferencias en el número de identificación de seguridad (SID) se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreNotForReplication=(BOOLEAN)|Especifica si la configuración de no replicación se debe ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreObjectPlacementOnPartitionScheme = (booleano ' True')|Especifica si la colocación de un objeto en un esquema de partición se debe ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnorePartitionSchemes=(BOOLEAN)|Especifica si las diferencias en las funciones y los esquemas de particiones se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnorePermissions=(BOOLEAN)|Especifica si las diferencias en los permisos se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreQuotedIdentifiers = (booleano ' True')|Especifica si las diferencias en la configuración de identificadores entre comillas se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreRoleMembership=(BOOLEAN)|Especifica si se omitirán o se actualizarán las diferencias en las pertenencias a roles de los inicios de sesión al publicar en una base de datos.|
|**/p:**|IgnoreRouteLifetime = (booleano ' True')|Especifica si las diferencias en cuanto al periodo durante el cual SQL Server conserva la ruta en la tabla de enrutamiento se deben omitir o si hay que actualizar al publicar en una base de datos.|
|**/p:**|IgnoreSemicolonBetweenStatements = (booleano ' True')|Especifica si las diferencias en los caracteres de punto y coma entre las instrucciones T-SQL se ignorarán o se actualizarán al publicar en una base de datos.|
|**/p:**|IgnoreTableOptions=(BOOLEAN)|Especifica si las diferencias en las opciones de tabla se ignorarán o se actualizarán al publicar en una base de datos.|
|**/p:**|IgnoreUserSettingsObjects=(BOOLEAN)|Especifica si las diferencias en los objetos de configuración de usuario se ignorarán o se actualizarán al publicar en una base de datos.|
|**/p:**|IgnoreWhitespace = (booleano ' True')|Especifica si las diferencias en los espacios en blanco se ignorarán o se actualizarán al publicar en una base de datos.|
|**/p:**|IgnoreWithNocheckOnCheckConstraints=(BOOLEAN)|Especifica si las diferencias en el valor de la cláusula WITH NOCHECK de las restricciones CHECK se omiten o hay que actualizar al publicar.|
|**/p:**|IgnoreWithNocheckOnForeignKeys=(BOOLEAN)|Especifica si las diferencias en el valor de la cláusula WITH NOCHECK para las claves externas se ignorarán o se actualizarán al publicar en una base de datos.|
|**/p:**|IncludeCompositeObjects=(BOOLEAN)|Incluir todos los elementos compuestos como parte de una única operación de publicación.|
|**/p:**|IncludeTransactionalScripts=(BOOLEAN)|Especifica si las instrucciones transaccionales se deben usar siempre que sea posible al publicar en una base de datos.|
|**/p:**|NoAlterStatementsToChangeClrTypes=(BOOLEAN)|Especifica que la acción de publicación debe quitar y volver a crear siempre un ensamblado en lugar de emitir una instrucción ALTER ASSEMBLY.|
|**/p:**|PopulateFilesOnFileGroups = (booleano ' True')|Especifica si se crea también un nuevo archivo cuando se crea un nuevo FileGroup en la base de datos de destino.|
|**/p:**|RegisterDataTierApplication=(BOOLEAN)|Especifica si el esquema está registrado con el servidor de base de datos.|
|**/p:**|RunDeploymentPlanExecutors=(BOOLEAN)|Especifica si los colaboradores DeploymentPlanExecutor deben ejecutarse cuando se ejecutan otras operaciones.|
|**/p:**|ScriptDatabaseCollation=(BOOLEAN)|Especifica si las diferencias en la intercalación de la base de datos se deben omitir o actualizar al publicar en una base de datos.|
|**/p:**|ScriptDatabaseCompatibility=(BOOLEAN)|Especifica si las diferencias en la compatibilidad de la base de datos se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|ScriptDatabaseOptions = (booleano ' True')|Especifica si las propiedades de la base de datos deben establecerse o actualizarse como parte de la acción de publicación.|
|**/p:**|ScriptDeployStateChecks=(BOOLEAN)|Especifica si se generan instrucciones en el script de publicación para comprobar que el nombre de la base de datos y el nombre del servidor coinciden con los nombres especificados en el proyecto de base de datos.|
|**/p:**|ScriptFileSize=(BOOLEAN)|Controla si el tamaño se especifica cuando se agrega un archivo a un grupo de archivos.|
|**/p:**|ScriptNewConstraintValidation = (booleano ' True')|Al final de la publicación todas las restricciones se comprobarán como un conjunto, evitando los errores de datos causados por una comprobación o una restricción foreign key en medio de la publicación. Si esta opción es False, las restricciones se publican sin comprobar los datos correspondientes.|
|**/p:**|ScriptRefreshModule = (booleano ' True')|Incluye instrucciones de actualización al final del script de publicación.|
|**/p:**|Almacenamiento = ({archivo&#124;memoria})|Especifica la forma en que se almacenan los elementos cuando se genera el modelo de base de datos. Por motivos de rendimiento, el valor predeterminado es InMemory. Cuando se trata de bases de datos grandes, se requiere almacenamiento respaldado por archivos.|
|**/p:**|TreatVerificationErrorsAsWarnings=(BOOLEAN)|Especifica si publicación errores detectados durante la comprobación se debe tratar como advertencias. La comprobación se realiza con el plan de implementación generado antes de que el plan se ejecute con la base de datos de destino. El plan de comprobación detecta problemas, como la pérdida de objetos solo en el destino (como los índices) que deben quitarse para hacer un cambio. La comprobación también detecta situaciones en las que existen dependencias (como una tabla o vista) debido a una referencia a un proyecto compuesto, pero no existen en la base de datos de destino. Puede hacer esto para obtener una lista completa de todos los problemas, en lugar de tener la acción de publicación se detenga en el primer error.|**/p:**|UnmodifiableObjectWarnings = (booleano ' True')|Especifica si generar advertencias cuando se encuentren diferencias en los objetos que no se puedan modificar, por ejemplo, si el tamaño de archivo o las rutas de acceso a los archivos son diferentes para un archivo.|
|**/p:**|VerifyCollationCompatibility = (booleano ' True')|Especifica si se comprobó la compatibilidad de intercalación.|
|**/p:**|VerifyDeployment = (booleano ' True')|Especifica si realizar comprobaciones antes de la publicación que detengan la acción de publicación si hay problemas que pudieran impedir que la publicación se realizara correctamente. Por ejemplo, la acción de publicación podría detenerse si tiene claves externas en la base de datos de destino que no existan en el proyecto de base de datos, y eso provoca errores al publicar.|
|

### <a name="sqlcmd-variables"></a>Variables SQLCMD

En la tabla siguiente se describe el formato de la opción que puede usar para invalidar el valor de una variable de comando SQL (**sqlcmd**) que se usa durante una acción de publicación. Los valores de variable especificados en la línea de comandos invalidan otros valores asignados a la variable (por ejemplo, un perfil de publicación).  
  
|Parámetro|Valor predeterminado|Descripción|  
|-------------|-----------|---------------|  
|**/ Variables: {PropertyName} = {Value}**||Especifica un par de nombre y valor para una variable específica de acción; {VariableName}={Value}. El archivo DACPAC contiene la lista de variables SQLCMD válidas. Se produce un error si no se facilita un valor para cada variable.|  
  
## <a name="export-parameters-and-properties"></a>Exportación de parámetros y propiedades

Una acción de exportación de SqlPackage.exe exporta una base de datos activa de SQL Server o Azure SQL Database a un paquete BACPAC (archivo.bacpac). De forma predeterminada, los datos de todas las tablas se incluirán en el archivo .bacpac. Si lo desea, puede especificar solo un subconjunto de las tablas para exportar los datos. La validación de la acción de exportación garantiza la compatibilidad de Azure SQL Database para toda la base de datos de destino, incluso si se especifica un subconjunto de tablas para la exportación.  
  
### <a name="help-for-export-action"></a>Ayuda para la acción de exportación

|Parámetro|Forma corta|Valor|Descripción|
|---|---|---|---|
|**/Action:**|**/a**|Exportar|Especifica la acción que se va a realizar. |
|**/Diagnostics:**|**/d**|{True&#124;False}|Especifica si la salida del registro de diagnóstico es la consola. De forma predeterminada es False. |
|**/ DiagnosticsFile:**|**/DF**|{string}|Especifica un archivo para almacenar los registros de diagnóstico. |
|**/ OverwriteFiles:**|**/of**|{True&#124;False}|Especifica si sqlpackage.exe debe sobrescribir los archivos existentes. Si se especifica False, sqlpackage.exe anula la acción si se encuentra un archivo existente. El valor predeterminado es True. |
|**/Properties:**|**/p**|{PropertyName}={Value}|Especifica un par de nombre y valor para una propiedad específica de acción; {PropertyName}={Value}. Remítase a la ayuda de una acción determinada para ver los nombres de propiedad de esa acción. Ejemplo: / Action sqlpackage.exe: publicar /?.|
|**/Quiet:**|**/q**|{True&#124;False}|Especifica si se suprimen los comentarios detallados. De forma predeterminada es False.|
|**/ SourceConnectionString:**|**/ SCS**|{string}|Especifica una cadena de conexión válida de SQL Server o SQL Azure para la base de datos de origen. Si se especifica este parámetro, lo usan exclusivamente los demás parámetros de origen. |
|**/SourceDatabaseName:**|**Export /**|{string}|Define el nombre de la base de datos de origen. |
|**/ SourceEncryptConnection:**|**/sec**|{True&#124;False}|Especifica si se debe usar cifrado SQL para la conexión de base de datos de origen. |
|**/SourcePassword:**|**/sp**|{string}|En escenarios de autenticación de SQL Server, define la palabra clave que se va a usar para acceder a la base de datos de origen. |
|**/ Nombreservidororigen:**|**/ssn**|{string}|Define el nombre del servidor que hospeda la base de datos de origen. |
|**/ SourceTimeout:**|**/st**|{int}|Especifica el tiempo de espera para establecer una conexión con la base de datos de origen, en segundos. |
|**/ SourceTrustServerCertificate:**|**/stsc**|{True&#124;False}|Especifica si se usará SSL para cifrar la conexión con la base de datos de origen y no tener que recorrer la cadena de certificados para validar la confianza. |
|**/SourceUser:**|**/su**|{string}|En escenarios de autenticación de SQL Server, define el usuario de SQL Server que se va a usar para acceder a la base de datos de origen. |
|**/ TargetFile:**|**/tf**|{string}| Especifica un archivo de destino (es decir, un archivo .dacpac) que se usará como el destino de acción en lugar de una base de datos. Si se usa este parámetro, el resto de parámetros de destino no serán válidos. Este parámetro será no válida para las acciones que admiten solo los destinos de base de datos.|
|**/ TenantId:**|**/tid**|{string}|Representa el nombre de dominio o Id. de inquilino de Azure AD. Esta opción es necesaria para admitir a invitado o importa usuarios de Azure AD, así como cuentas de Microsoft como outlook.com, hotmail.com o live.com. Si se omite este parámetro, se usará de forma predeterminada, el Id. de inquilino para Azure AD, suponiendo que el usuario autenticado es un usuario nativo para este anuncio. Sin embargo, en este caso no se admiten cualquier invitado o los usuarios importados o cuentas de Microsoft hospedadas en este Azure AD y se producirá un error en la operación. <br/> Para obtener más información acerca de la autenticación Universal de Active Directory, consulte [autenticación Universal con SQL Database y SQL Data Warehouse (compatibilidad de SSMS con MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|
|**/ UniversalAuthentication:**|**/ua**|{True&#124;False}|Especifica si se debe usar la autenticación Universal. Cuando se establece en True, el protocolo de autenticación interactiva está activado compatible con MFA. Esta opción también puede utilizarse para la autenticación de Azure AD sin MFA, mediante un protocolo interactivo pedir al usuario que escriba su nombre de usuario y contraseña o autenticación integrada (credenciales de Windows). Cuando /UniversalAuthentication se establece en True, no se puede especificar ninguna autenticación de Azure AD en SourceConnectionString (/ scs). Cuando /UniversalAuthentication se establece en False, se debe especificar la autenticación de Azure AD en SourceConnectionString (/ scs). <br/> Para obtener más información acerca de la autenticación Universal de Active Directory, consulte [autenticación Universal con SQL Database y SQL Data Warehouse (compatibilidad de SSMS con MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|

### <a name="properties-specific-to-the-export-action"></a>Propiedades específicas de la acción de exportación

|Propiedad|Valor|Descripción|
|---|---|---|
|**/p:**|CommandTimeout = (INT32 "60")|Especifica el tiempo de espera de comando en segundos cuando se ejecutan consultas en SQL Server.|
|**/p:**|Almacenamiento = ({archivo&#124;memoria} 'File')|Especifica el tipo de almacenamiento de seguridad para el modelo de esquema que se usa durante la extracción.|
|**/p:**|TableData=(STRING)|Indica la tabla desde el que se va a extraer datos. Especifique el nombre de tabla con o sin los corchetes que rodean las partes del nombre en el siguiente formato: nombre_esquema.identificador_tabla.|
|**/p:**|TargetEngineVersion = ({predeterminada&#124;más reciente&#124;V11&#124;V12} "Latest")|Especifica la versión del motor de destino que se espera. Esto afecta a si se permiten objetos compatibles con servidores de Azure SQL Database con capacidades de V12, como las tablas optimizadas para memoria, en el archivo bacpac generado.|
|**/p:**|VerifyFullTextDocumentTypesSupported=(BOOLEAN)|Especifica si los tipos de documentos de texto completo admitidos para Microsoft Azure SQL Database v12 deben comprobarse.|
  
## <a name="import-parameters-and-properties"></a>Importación de parámetros y propiedades

Una acción de importación de SqlPackage.exe importa los datos de esquema y tabla de un paquete BACPAC (archivo.bacpac) en una base de datos nueva o vacía en SQL Server o Azure SQL Database. En el momento de la operación de importación a una base de datos existente, la base de datos de destino no puede contener ningún objeto de esquema definido por el usuario.  
  
### <a name="help-for-command-actions"></a>Ayuda para las acciones de comando

|Parámetro|Forma corta|Valor|Descripción|
|---|---|---|---|
|**/Action:**|**/a**|Importar|Especifica la acción que se va a realizar. |
|**/Diagnostics:**|**/d**|{True&#124;False}|Especifica si la salida del registro de diagnóstico es la consola. De forma predeterminada es False. |
|**/ DiagnosticsFile:**|**/DF**|{string}|Especifica un archivo para almacenar los registros de diagnóstico. |
|**/Properties:**|**/p**|{PropertyName}={Value}|Especifica un par de nombre y valor para una propiedad específica de acción; {PropertyName}={Value}. Remítase a la ayuda de una acción determinada para ver los nombres de propiedad de esa acción. Ejemplo: / Action sqlpackage.exe: publicar /?.|
|**/Quiet:**|**/q**|{True&#124;False}|Especifica si se suprimen los comentarios detallados. De forma predeterminada es False.|
|**/ SourceFile:**|**/sf**|{string}|Especifica un archivo de origen que se va a usar como origen de la acción. Si se usa este parámetro, el resto de parámetros de origen no serán válidos. |
|**/ TargetConnectionString:**|**/TCS**|{string}|Especifica una cadena de conexión válida de SQL Server o SQL Azure para la base de datos de destino. Si se especifica este parámetro, lo usan exclusivamente los demás parámetros de destino. |
|**/TargetDatabaseName:**|**/tdn**|{string}|Especifica una invalidación del nombre de la base de datos que es el destino de la acción sqlpackage.exe. |
|**/ TargetEncryptConnection:**|**/Tec**|{True&#124;False}|Especifica si se debe usar el cifrado de SQL para la conexión de base de datos de destino. |
|**/ ContraseñaDestino:**|**/tp**|{string}|En escenarios de autenticación de SQL Server, define la palabra clave que se va a usar para acceder a la base de datos de destino. |
|**/ TargetServerName:**|**/tsn**|{string}|Define el nombre del servidor que hospeda la base de datos de destino. |
|**/ TargetTimeout:**|**/tt**|{int}|Especifica el tiempo de espera para establecer una conexión con la base de datos de destino, en segundos. Para Azure AD, se recomienda que este valor sea mayor o igual a 30 segundos.|
|**/ TargetTrustServerCertificate:**|**/ttsc**|{True&#124;False}|Especifica si se usará SSL para cifrar la conexión con la base de datos de destino y no tener que recorrer la cadena de certificados para validar la confianza. |
|**/ TargetUser:**|**/tu**|{string}|En escenarios de autenticación de SQL Server, define el usuario de SQL Server que se va a usar para acceder a la base de datos de destino. |
|**/ TenantId:**|**/tid**|{string}|Representa el nombre de dominio o Id. de inquilino de Azure AD. Esta opción es necesaria para admitir a invitado o importa usuarios de Azure AD, así como cuentas de Microsoft como outlook.com, hotmail.com o live.com. Si se omite este parámetro, se usará de forma predeterminada, el Id. de inquilino para Azure AD, suponiendo que el usuario autenticado es un usuario nativo para este anuncio. Sin embargo, en este caso no se admiten cualquier invitado o los usuarios importados o cuentas de Microsoft hospedadas en este Azure AD y se producirá un error en la operación. <br/> Para obtener más información acerca de la autenticación Universal de Active Directory, consulte [autenticación Universal con SQL Database y SQL Data Warehouse (compatibilidad de SSMS con MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|
|**/ UniversalAuthentication:**|**/ua**|{True&#124;False}|Especifica si se debe usar la autenticación Universal. Cuando se establece en True, el protocolo de autenticación interactiva está activado compatible con MFA. Esta opción también puede utilizarse para la autenticación de Azure AD sin MFA, mediante un protocolo interactivo pedir al usuario que escriba su nombre de usuario y contraseña o autenticación integrada (credenciales de Windows). Cuando /UniversalAuthentication se establece en True, no se puede especificar ninguna autenticación de Azure AD en SourceConnectionString (/ scs). Cuando /UniversalAuthentication se establece en False, se debe especificar la autenticación de Azure AD en SourceConnectionString (/ scs). <br/> Para obtener más información acerca de la autenticación Universal de Active Directory, consulte [autenticación Universal con SQL Database y SQL Data Warehouse (compatibilidad de SSMS con MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|

Propiedades específicas de la acción de importación:
|Propiedad|Valor|Descripción|
|---|---|---|
|**/p:**|CommandTimeout = (INT32 "60")|Especifica el tiempo de espera de comando en segundos cuando se ejecutan consultas en SQL Server.|
|**/p:**|DatabaseEdition = ({Basic&#124;estándar&#124;Premium&#124;predeterminada} 'Default')|Define la edición de una base de datos de SQL Azure.|
|**/p:**|DatabaseMaximumSize=(INT32)|Define el tamaño máximo en GB de una instancia de Azure SQL Database.|
|**/p:**|DatabaseServiceObjective=(STRING)|Define el nivel de rendimiento de una instancia de Azure SQL Database, como "P0" o "S1".|
|**/p:**|ImportContributorArguments=(STRING)|Especifica los argumentos de colaborador de implementación para los colaboradores de implementación. Debe ser una lista de valores delimitada por punto y coma.|
|**/p:**|ImportContributors=(STRING)|Especifica los colaboradores de implementación que se deben ejecutar cuando se importa el dacpac. Debe ser una lista delimitada por punto y coma de nombres completos o identificadores de los colaboradores de compilación.|
|**/p:**|Almacenamiento = ({archivo&#124;memoria})|Especifica la forma en que se almacenan los elementos cuando se genera el modelo de base de datos. Por motivos de rendimiento, el valor predeterminado es InMemory. Cuando se trata de bases de datos grandes, se requiere almacenamiento respaldado por archivos.|
  
## <a name="deployreport-parameters-and-properties"></a>Parámetros y propiedades de DeployReport

Las acciones de informe **SqlPackage.exe** crean un informe XML de los cambios que se producirían al usar una acción de publicación.  
  
### <a name="help-for-deployreport-action"></a>Ayuda para la acción DeployReport

|Parámetro|Forma corta|Valor|Descripción|
|---|---|---|---|
|**/Action:**|**/a**|DeployReport|Especifica la acción que se va a realizar. |
|**/Diagnostics:**|**/d**|{True&#124;False}|Especifica si la salida del registro de diagnóstico es la consola. De forma predeterminada es False. |
|**/ DiagnosticsFile:**|**/DF**|{string}|Especifica un archivo para almacenar los registros de diagnóstico. |
|**/OutputPath:**|**/ Op.**|{string}|Especifica la ruta de acceso de archivo donde se generaron los archivos de salida. |
|**/ OverwriteFiles:**|**/of**|{True&#124;False}|Especifica si sqlpackage.exe debe sobrescribir los archivos existentes. Si se especifica False, sqlpackage.exe anula la acción si se encuentra un archivo existente. El valor predeterminado es True. |
|**/Profile:**|**/pr**|{string}|Especifica la ruta de acceso a un archivo para un perfil de publicación DAC. El perfil define una colección de propiedades y variables que se usarán cuando se generen resultados. |
|**/Properties:**|**/p**|{PropertyName}={Value}|Especifica un par de nombre y valor para una propiedad específica de acción; {PropertyName}={Value}. Remítase a la ayuda de una acción determinada para ver los nombres de propiedad de esa acción. Ejemplo: / Action sqlpackage.exe: publicar /?. |
|**/Quiet:**|**/q**|{True&#124;False}|Especifica si se suprimen los comentarios detallados. De forma predeterminada es False. |
|**/ SourceConnectionString:**|**/ SCS**|{string}|Especifica una cadena de conexión válida de SQL Server o SQL Azure para la base de datos de origen. Si se especifica este parámetro, lo usan exclusivamente los demás parámetros de origen. |
|**/SourceDatabaseName:**|**Export /**|{string}|Define el nombre de la base de datos de origen. |
|**/ SourceEncryptConnection:**|**/sec**|{True&#124;False}|Especifica si se debe usar cifrado SQL para la conexión de base de datos de origen. |
|**/ SourceFile:**|**/sf**|{string}|Especifica un archivo de origen que se usará como origen de la acción en lugar de una base de datos. Si se usa este parámetro, el resto de parámetros de origen no serán válidos. |
|**/SourcePassword:**|**/sp**|{string}|En escenarios de autenticación de SQL Server, define la palabra clave que se va a usar para acceder a la base de datos de origen. |
|**/ Nombreservidororigen:**|**/ssn**|{string}|Define el nombre del servidor que hospeda la base de datos de origen. |
|**/ SourceTimeout:**|**/st**|{int}|Especifica el tiempo de espera para establecer una conexión con la base de datos de origen, en segundos. |
|**/ SourceTrustServerCertificate:**|**/stsc**|{True&#124;False}|Especifica si se usará SSL para cifrar la conexión con la base de datos de origen y no tener que recorrer la cadena de certificados para validar la confianza. |
|**/SourceUser:**|**/su**|{string}|En escenarios de autenticación de SQL Server, define el usuario de SQL Server que se va a usar para acceder a la base de datos de origen. |
|**/ TargetConnectionString:**|**/TCS**|{string}|Especifica una cadena de conexión válida de SQL Server o SQL Azure para la base de datos de destino. Si se especifica este parámetro, lo usan exclusivamente los demás parámetros de destino. |
|**/TargetDatabaseName:**|**/tdn**|{string}|Especifica una invalidación del nombre de la base de datos que es el destino de la acción sqlpackage.exe. |
|**/ TargetEncryptConnection:**|**/Tec**|{True&#124;False}|Especifica si se debe usar el cifrado de SQL para la conexión de base de datos de destino. |
|**/ TargetFile:**|**/tf**|{string}|Especifica un archivo de destino (es decir, un archivo .dacpac) que se usará como el destino de acción en lugar de una base de datos. Si se usa este parámetro, el resto de parámetros de destino no serán válidos. Este parámetro será no válida para las acciones que admiten solo los destinos de base de datos.|
|**/ ContraseñaDestino:**|**/tp**|{string}|En escenarios de autenticación de SQL Server, define la palabra clave que se va a usar para acceder a la base de datos de destino. |
|**/ TargetServerName:**|**/tsn**|{string}|Define el nombre del servidor que hospeda la base de datos de destino. |
|**/ TargetTimeout:**|**/tt**|{int}|Especifica el tiempo de espera para establecer una conexión con la base de datos de destino, en segundos. Para Azure AD, se recomienda que este valor sea mayor o igual a 30 segundos.|
|**/ TargetTrustServerCertificate:**|**/ttsc**|{True&#124;False}|Especifica si se usará SSL para cifrar la conexión con la base de datos de destino y no tener que recorrer la cadena de certificados para validar la confianza. |
|**/ TargetUser:**|**/tu**|{string}|En escenarios de autenticación de SQL Server, define el usuario de SQL Server que se va a usar para acceder a la base de datos de destino. |
|**/ TenantId:**|**/tid**|{string}|Representa el nombre de dominio o Id. de inquilino de Azure AD. Esta opción es necesaria para admitir a invitado o importa usuarios de Azure AD, así como cuentas de Microsoft como outlook.com, hotmail.com o live.com. Si se omite este parámetro, se usará de forma predeterminada, el Id. de inquilino para Azure AD, suponiendo que el usuario autenticado es un usuario nativo para este anuncio. Sin embargo, en este caso no se admiten cualquier invitado o los usuarios importados o cuentas de Microsoft hospedadas en este Azure AD y se producirá un error en la operación. <br/> Para obtener más información acerca de la autenticación Universal de Active Directory, consulte [autenticación Universal con SQL Database y SQL Data Warehouse (compatibilidad de SSMS con MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|
|**/ UniversalAuthentication:**|**/ua**|{True&#124;False}|Especifica si se debe usar la autenticación Universal. Cuando se establece en True, el protocolo de autenticación interactiva está activado compatible con MFA. Esta opción también puede utilizarse para la autenticación de Azure AD sin MFA, mediante un protocolo interactivo pedir al usuario que escriba su nombre de usuario y contraseña o autenticación integrada (credenciales de Windows). Cuando /UniversalAuthentication se establece en True, no se puede especificar ninguna autenticación de Azure AD en SourceConnectionString (/ scs). Cuando /UniversalAuthentication se establece en False, se debe especificar la autenticación de Azure AD en SourceConnectionString (/ scs). <br/> Para obtener más información acerca de la autenticación Universal de Active Directory, consulte [autenticación Universal con SQL Database y SQL Data Warehouse (compatibilidad de SSMS con MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|
|**/Variables:**|**/v**|{PropertyName}={Value}|Especifica un par de nombre y valor para una variable específica de acción; {VariableName}={Value}. El archivo DACPAC contiene la lista de variables SQLCMD válidas. Se produce un error si no se facilita un valor para cada variable. |

## <a name="properties-specific-to-the-deployreport-action"></a>Propiedades específicas de la acción DeployReport

|Propiedad|Valor|Descripción|
|---|---|---|
|**/p:**|AdditionalDeploymentContributorArguments=(STRING)|Especifica los argumentos de colaborador de implementación adicionales para los colaboradores de implementación. Debe ser una lista de valores delimitada por punto y coma.|
|**/p:**|AdditionalDeploymentContributors=(STRING)|Especifica colaboradores de implementación adicionales que se deben ejecutar cuando se implementa el dacpac. Debe ser una lista delimitada por punto y coma de nombres completos o identificadores de los colaboradores de compilación.|
|**/p:**|AllowDropBlocking Assemblies=(BOOLEAN)|Esta propiedad se usa en la implementación de SqlClr para hacer que cualquier ensamblado de bloqueo se quite como parte del plan de implementación. De forma predeterminada, cualquier ensamblado de bloqueo o de referencia bloqueará la actualización de un ensamblado si el ensamblado de referencia tiene que quitarse.|
|**/p:**|AllowIncompatiblePlatform=(BOOLEAN)|Especifica si se intenta la acción a pesar de las posibles plataformas de SQL Server incompatibles.|
|**/p:**|AllowUnsafeRowLevelSecurityDataMovement=(BOOLEAN)|No bloquee la transferencia de datos en una tabla con Seguridad de nivel de fila si esta propiedad está establecida en true. El valor predeterminado es False.|
|**/p:**|BackupDatabaseBeforeChanges=(BOOLEAN)|Hace una copia de seguridad de la base de datos antes de implementar ningún cambio.|
|**/p:**|BlockOnPossibleDataLoss = (booleano ' True')|Especifica que se debe finalizar el episodio de publicación si existiera la posibilidad de que se perdieran datos a causa de la operación de publicación.|
|**/p:**|BlockWhenDriftDetected = (booleano ' True')|Especifica si bloquear la actualización de una base de datos cuyo esquema ha dejado de corresponderse con su registro o no está registrada. |
|**/p:**|CommandTimeout = (INT32 "60")|Especifica el tiempo de espera de comando en segundos cuando se ejecutan consultas en SQL Server. |
|**/p:**|CommentOutSetVarDeclarations=(BOOLEAN)|Especifica si la declaración de las variables SETVAR se incluyen entre comentarios en el script de publicación generado. Puede optar por esta opción si planea usar una herramienta como SQLCMD.EXE para especificar los valores de la línea de comandos al publicar. |
|**/p:**|CompareUsingTargetCollation=(BOOLEAN)|Esta configuración determina la forma en que se trata la intercalación de la base de datos durante la implementación; de forma predeterminada, la intercalación de la base de datos de destino se actualizará si no coincide con la especificada por el origen. Cuando se ha establecido esta opción, se usará la intercalación de la base de datos (o servidor) de destino. |
|**/p:**|CreateNewDatabase=(BOOLEAN)|Especifica si la base de datos de destino debe actualizarse o si se va a quitar para volver a crearse al publicar en una base de datos. |
|**/p:**|DatabaseEdition = ({Basic&#124;estándar&#124;Premium&#124;predeterminada} 'Default')|Define la edición de una base de datos de SQL Azure. |
|**/p:**|DatabaseMaximumSize=(INT32)|Define el tamaño máximo en GB de una instancia de Azure SQL Database.|
|**/p:**|DatabaseServiceObjective=(STRING)|Define el nivel de rendimiento de una instancia de Azure SQL Database, como "P0" o "S1". |
|**/p:**|DeployDatabaseInSingleUserMode=(BOOLEAN)|Si se establece en True, la base de datos se establecerá en modo de usuario único antes de implementarse. |
|**/p:**|DisableAndReenableDdlTriggers = (booleano ' True')| Especifica si los desencadenadores del Lenguaje de definición de datos (DDL) se deshabilitan al principio del proceso de publicación y se vuelven a habilitar al final de la acción de publicación.|
|**/p:**|DoNotAlterChangeDataCaptureObjects = (booleano ' True')|Si se establece en true, los objetos de captura de datos modificados no se verán alterados.|
|**/p:**|DoNotAlterReplicatedObjects = (booleano ' True')|Especifica si los objetos que se replican se van a identificar durante la comprobación.|
|**/p:**|DoNotDropObjectType=(STRING)|Un tipo de objeto que no debería quitarse si DropObjectsNotInSource es true. Los nombres de tipo de objeto válidos son: Aggregates, ApplicationRoles, Assemblies, AsymmetricKeys, BrokerPriorities, Certificates, ColumnEncryptionKeys, ColumnMasterKeys, Contracts, DatabaseRoles, DatabaseTriggers, Defaults, ExtendedProperties, ExternalDataSources, ExternalFileFormats, ExternalTables, Filegroups, FileTables, FullTextCatalogs, FullTextStoplists, MessageTypes, PartitionFunctions, PartitionSchemes, Permissions, Queues, RemoteServiceBindings, RoleMembership, Rules, ScalarValuedFunctions, SearchPropertyLists, SecurityPolicies, Sequences, Services, Signatures, StoredProcedures, SymmetricKeys, Synonyms, Tables, TableValuedFunctions, UserDefinedDataTypes, UserDefinedTableTypes, ClrUserDefinedTypes, Users, Views, XmlSchemaCollections, Audits, Credentials, CryptographicProviders, DatabaseAuditSpecifications, DatabaseScopedCredentials, Endpoints, ErrorMessages, EventNotifications, EventSessions, LinkedServerLogins, LinkedServers, Logins, Routes, ServerAuditSpecifications, ServerRoleMembership, ServerRoles, ServerTriggers. |
|**/p:**|DoNotDropObjectTypes=(STRING)|Lista delimitada por puntos y coma de tipos de objetos que no deberían quitarse si DropObjectsNotInSource es true. Los nombres de tipo de objeto válidos son: Aggregates, ApplicationRoles, Assemblies, AsymmetricKeys, BrokerPriorities, Certificates, ColumnEncryptionKeys, ColumnMasterKeys, Contracts, DatabaseRoles, DatabaseTriggers, Defaults, ExtendedProperties, ExternalDataSources, ExternalFileFormats, ExternalTables, Filegroups, FileTables, FullTextCatalogs, FullTextStoplists, MessageTypes, PartitionFunctions, PartitionSchemes, Permissions, Queues, RemoteServiceBindings, RoleMembership, Rules, ScalarValuedFunctions, SearchPropertyLists, SecurityPolicies, Sequences, Services, Signatures, StoredProcedures, SymmetricKeys, Synonyms, Tables, TableValuedFunctions, UserDefinedDataTypes, UserDefinedTableTypes, ClrUserDefinedTypes, Users, Views, XmlSchemaCollections, Audits, Credentials, CryptographicProviders, DatabaseAuditSpecifications, DatabaseScopedCredentials, Endpoints, ErrorMessages, EventNotifications, EventSessions, LinkedServerLogins, LinkedServers, Logins, Routes, ServerAuditSpecifications, ServerRoleMembership, ServerRoles, ServerTriggers.|
|**/p:**|DropConstraintsNotInSource = (booleano ' True')|Especifica si las restricciones que no existen en el archivo de la instantánea de base de datos (.dacpac) se van a quitar de la base de datos de destino al publicar en una base de datos.|
|**/p:**|DropDmlTriggersNotInSource = (booleano ' True')|Especifica si los desencadenadores DML que no existen en el archivo de la instantánea de base de datos (.dacpac) se van a quitar de la base de datos de destino al publicar en una base de datos.|
|**/p:**|DropExtendedPropertiesNotInSource = (booleano ' True')|Especifica si las propiedades extendidas que no existen en el archivo de instantánea de base de datos (.dacpac) se quitarán de la base de datos de destino al publicar en una base de datos.|
|**/p:**|DropIndexesNotInSource = (booleano ' True')|Especifica si los índices que no existen en el archivo de la instantánea de base de datos (.dacpac) se van a quitar de la base de datos de destino al publicar en una base de datos.|
|**/p:**|DropObjectsNotInSource=(BOOLEAN)|Especifica si los objetos que no existen en el archivo de instantánea de base de datos (.dacpac) se quitarán de la base de datos de destino al publicar en una base de datos. Este valor tiene prioridad sobre DropExtendedProperties.|
|**/p:**|DropPermissionsNotInSource=(BOOLEAN)|Especifica si los permisos que no existen en el archivo de la instantánea de base de datos (.dacpac) se van a quitar de la base de datos de destino al publicar actualizaciones en una base de datos.|
|**/p:**|DropRoleMembersNotInSource=(BOOLEAN)|Especifica si los miembros de rol que no se definieron en el archivo de la instantánea de base de datos (.dacpac) se van a quitar de la base de datos de destino al publicar actualizaciones en una base de datos.|
|**/p:**|DropStatisticsNotInSource = (booleano ' True')|Especifica si las estadísticas que no existen en el archivo de instantánea de base de datos (.dacpac) se quitarán de la base de datos de destino al publicar en una base de datos.|
|**/p:**|ExcludeObjectType=(STRING)|Un tipo de objeto que se debe omitir durante la implementación. Los nombres de tipo de objeto válidos son: Aggregates, ApplicationRoles, Assemblies, AsymmetricKeys, BrokerPriorities, Certificates, ColumnEncryptionKeys, ColumnMasterKeys, Contracts, DatabaseRoles, DatabaseTriggers, Defaults, ExtendedProperties, ExternalDataSources, ExternalFileFormats, ExternalTables, Filegroups, FileTables, FullTextCatalogs, FullTextStoplists, MessageTypes, PartitionFunctions, PartitionSchemes, Permissions, Queues, RemoteServiceBindings, RoleMembership, Rules, ScalarValuedFunctions, SearchPropertyLists, SecurityPolicies, Sequences, Services, Signatures, StoredProcedures, SymmetricKeys, Synonyms, Tables, TableValuedFunctions, UserDefinedDataTypes, UserDefinedTableTypes, ClrUserDefinedTypes, Users, Views, XmlSchemaCollections, Audits, Credentials, CryptographicProviders, DatabaseAuditSpecifications, DatabaseScopedCredentials, Endpoints, ErrorMessages, EventNotifications, EventSessions, LinkedServerLogins, LinkedServers, Logins, Routes, ServerAuditSpecifications, ServerRoleMembership, ServerRoles, ServerTriggers.|
|**/p:**|ExcludeObjectTypes=(STRING)|Lista delimitada por puntos y coma de tipos de objetos que se deben omitir durante la implementación. Los nombres de tipo de objeto válidos son: Aggregates, ApplicationRoles, Assemblies, AsymmetricKeys, BrokerPriorities, Certificates, ColumnEncryptionKeys, ColumnMasterKeys, Contracts, DatabaseRoles, DatabaseTriggers, Defaults, ExtendedProperties, ExternalDataSources, ExternalFileFormats, ExternalTables, Filegroups, FileTables, FullTextCatalogs, FullTextStoplists, MessageTypes, PartitionFunctions, PartitionSchemes, Permissions, Queues, RemoteServiceBindings, RoleMembership, Rules, ScalarValuedFunctions, SearchPropertyLists, SecurityPolicies, Sequences, Services, Signatures, StoredProcedures, SymmetricKeys, Synonyms, Tables, TableValuedFunctions, UserDefinedDataTypes, UserDefinedTableTypes, ClrUserDefinedTypes, Users, Views, XmlSchemaCollections, Audits, Credentials, CryptographicProviders, DatabaseAuditSpecifications, DatabaseScopedCredentials, Endpoints, ErrorMessages, EventNotifications, EventSessions, LinkedServerLogins, LinkedServers, Logins, Routes, ServerAuditSpecifications, ServerRoleMembership, ServerRoles, ServerTriggers.|
|**/p:**|GenerateSmartDefaults=(BOOLEAN)|Proporciona automáticamente un valor predeterminado cuando se actualiza una tabla que contiene datos con una columna que no admite valores NULL.|
|**/p:**|IgnoreAnsiNulls = (booleano ' True')|Especifica si las diferencias en la configuración ANSI NULLS se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreAuthorizer=(BOOLEAN)|Especifica si las diferencias en el autorizador se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreColumnCollation=(BOOLEAN)|Especifica si las diferencias en las intercalaciones de columnas se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreColumnOrder=(BOOLEAN)|Especifica si hay que omitir las diferencias en el orden de las columnas de una tabla o bien hay que actualizar al publicar en una base de datos.|
|**/p:**|IgnoreComments=(BOOLEAN)|Especifica si las diferencias en los comentarios se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreCryptographicProviderFilePath = (booleano ' True')|Especifica si las diferencias en la ruta de acceso del archivo del proveedor de servicios criptográficos se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreDdlTriggerOrder=(BOOLEAN)|Especifica si las diferencias en el orden de los desencadenadores de Data Definition Language (DDL) se deben ignorar o actualizar al publicar en una base de datos o en un servidor.|
|**/p:**|IgnoreDdlTriggerState=(BOOLEAN)|Especifica si las diferencias en el estado habilitado o deshabilitado de los desencadenadores de Data Definition Language (DDL) se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreDefaultSchema=(BOOLEAN)|Especifica si las diferencias en el esquema predeterminado se deben ignorar o actualizar al publicar en una base de datos. |
|**/p:**|IgnoreDmlTriggerOrder=(BOOLEAN)|Especifica si las diferencias en el orden de los desencadenadores del lenguaje de manipulación de datos (DML) se deben ignorar o actualizar al publicar en una base de datos.| 
|**/p:**|IgnoreDmlTriggerState=(BOOLEAN)|Especifica si las diferencias en el estado habilitado o deshabilitado de los desencadenadores de DML se deben ignorar o actualizar al publicar en una base de datos. |
|**/p:**|IgnoreExtendedProperties=(BOOLEAN)|Especifica si las diferencias en las propiedades extendidas se deben ignorar o actualizar al publicar en una base de datos. |
|**/p:**|IgnoreFileAndLogFilePath = (booleano ' True')|Especifica si las diferencias en las rutas de acceso de los archivos y archivos de registro se deben ignorar o actualizar al publicar en una base de datos. |
|**/p:**|IgnoreFilegroupPlacement = (booleano ' True')|Especifica si las diferencias en la colocación de objetos en FILEGROUPs se deben ignorar o actualizar al publicar en una base de datos.| 
|**/p:**|IgnoreFileSize = (booleano ' True')|Especifica si las diferencias en los tamaños de archivo se deben ignorar o si debe generarse una advertencia al publicar en una base de datos. |
|**/p:**|IgnoreFillFactor = (booleano ' True')|Especifica si las diferencias en el factor de relleno del almacenamiento de índices se deben ignorar o si debe generarse una advertencia al publicar en una base de datos.|
|**/p:**|IgnoreFullTextCatalogFilePath = (booleano ' True')|Especifica si las diferencias en la ruta de acceso al archivo del catálogo de texto completo se deben ignorar o si debe generarse una advertencia al publicar en una base de datos.| 
|**/p:**|IgnoreIdentitySeed=(BOOLEAN)|Especifica si las diferencias en el valor de inicialización de una columna de identidad se deben ignorar o actualizar al publicar actualizaciones en una base de datos. |
|**/p:**|IgnoreIncrement=(BOOLEAN)|Especifica si las diferencias en el incremento de una columna de identidad se deben ignorar o actualizar al publicar en una base de datos. |
|**/p:**|IgnoreIndexOptions=(BOOLEAN)|Especifica si las diferencias en las opciones de índice se deben ignorar o actualizar al publicar en una base de datos. |
|**/p:**|IgnoreIndexPadding = (booleano ' True')|Especifica si las diferencias en el relleno de índice se deben ignorar o actualizar al publicar en una base de datos. |
|**/p:**|IgnoreKeywordCasing = (booleano ' True')|Especifica si las diferencias en el uso de mayúsculas y minúsculas en palabras clave se deben ignorar o actualizar al publicar en una base de datos. |
|**/p:**|IgnoreLockHintsOnIndexes=(BOOLEAN)|Especifica si las diferencias en las sugerencias de bloqueo en los índices se deben ignorar o actualizar al publicar en una base de datos. |
|**/p:**|IgnoreLoginSids = (booleano ' True')| Especifica si las diferencias en el número de identificación de seguridad (SID) se deben ignorar o actualizar al publicar en una base de datos.| 
|**/p:**|IgnoreNotForReplication=(BOOLEAN)|Especifica si la configuración de no replicación se debe ignorar o actualizar al publicar en una base de datos. |
|**/p:**|IgnoreObjectPlacementOnPartitionScheme = (booleano ' True')|Especifica si la colocación de un objeto en un esquema de partición se debe ignorar o actualizar al publicar en una base de datos.|
 |**/p:**|IgnorePartitionSchemes=(BOOLEAN)|Especifica si las diferencias en las funciones y los esquemas de particiones se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnorePermissions=(BOOLEAN)|Especifica si las diferencias en los permisos se deben ignorar o actualizar al publicar en una base de datos. |
|**/p:**|IgnoreQuotedIdentifiers = (booleano ' True')|Especifica si las diferencias en la configuración de identificadores entre comillas se deben ignorar o actualizar al publicar en una base de datos. |
|**/p:**|IgnoreRoleMembership=(BOOLEAN)|Especifica si se omitirán o se actualizarán las diferencias en las pertenencias a roles de los inicios de sesión al publicar en una base de datos. |
|**/p:**|IgnoreRouteLifetime = (booleano ' True')|Especifica si las diferencias en el tiempo durante el cual SQL Server conserva la ruta en la tabla de enrutamiento se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreSemicolonBetweenStatements = (booleano ' True')|Especifica si las diferencias en los caracteres de punto y coma entre las instrucciones T-SQL se ignorarán o se actualizarán al publicar en una base de datos.| 
|**/p:**|IgnoreTableOptions=(BOOLEAN)|Especifica si las diferencias en las opciones de tabla se ignorarán o se actualizarán al publicar en una base de datos.| 
|**/p:**|IgnoreUserSettingsObjects=(BOOLEAN)|Especifica si las diferencias en los objetos de configuración de usuario se ignorarán o se actualizarán al publicar en una base de datos.|
|**/p:**|IgnoreWhitespace = (booleano ' True')|Especifica si las diferencias en los espacios en blanco se ignorarán o se actualizarán al publicar en una base de datos. |
|**/p:**|IgnoreWithNocheckOnCheckConstraints=(BOOLEAN)|Especifica si las diferencias en el valor de la cláusula WITH NOCHECK para las restricciones CHECK se ignorarán o se actualizarán al publicar en una base de datos.| 
|**/p:**|IgnoreWithNocheckOnForeignKeys=(BOOLEAN)|Especifica si las diferencias en el valor de la cláusula WITH NOCHECK para las claves externas se ignorarán o se actualizarán al publicar en una base de datos.| 
|**/p:**|IncludeCompositeObjects=(BOOLEAN)|Incluir todos los elementos compuestos como parte de una única operación de publicación.|
|**/p:**|IncludeTransactionalScripts=(BOOLEAN)|Especifica si las instrucciones transaccionales se deben usar siempre que sea posible al publicar en una base de datos.|
 |**/p:**|NoAlterStatementsToChangeClrTypes=(BOOLEAN)|Especifica que la acción de publicación debe quitar y volver a crear siempre un ensamblado en lugar de emitir una instrucción ALTER ASSEMBLY. |
|**/p:**|PopulateFilesOnFileGroups = (booleano ' True')|Especifica si se crea también un nuevo archivo cuando se crea un nuevo FileGroup en la base de datos de destino. |
|**/p:**|RegisterDataTierApplication=(BOOLEAN)|Especifica si el esquema está registrado con el servidor de base de datos. 
|**/p:**|RunDeploymentPlanExecutors=(BOOLEAN)|Especifica si los colaboradores DeploymentPlanExecutor deben ejecutarse cuando se ejecutan otras operaciones.|
|**/p:**|ScriptDatabaseCollation=(BOOLEAN)|Especifica si las diferencias en la intercalación de la base de datos se deben omitir o actualizar al publicar en una base de datos. |
|**/p:**|ScriptDatabaseCompatibility=(BOOLEAN)|Especifica si las diferencias en la compatibilidad de la base de datos se deben ignorar o actualizar al publicar en una base de datos. |
|**/p:**|ScriptDatabaseOptions = (booleano ' True')|Especifica si las propiedades de la base de datos deben establecerse o actualizarse como parte de la acción de publicación. |
|**/p:**|ScriptDeployStateChecks=(BOOLEAN)|Especifica si se generan instrucciones en el script de publicación para comprobar que el nombre de la base de datos y el nombre del servidor coinciden con los nombres especificados en el proyecto de base de datos.|
|**/p:**|ScriptFileSize=(BOOLEAN)|Controla si el tamaño se especifica cuando se agrega un archivo a un grupo de archivos. |
|**/p:**|ScriptNewConstraintValidation = (booleano ' True')|Al final de la publicación todas las restricciones se comprobarán como un conjunto, evitando los errores de datos causados por una comprobación o una restricción foreign key en medio de la publicación. Si esta opción es False, las restricciones se publican sin comprobar los datos correspondientes.|
|**/p:**|ScriptRefreshModule = (booleano ' True')|Incluye instrucciones de actualización al final del script de publicación.|
|**/p:**|Almacenamiento = ({archivo&#124;memoria})|Especifica la forma en que se almacenan los elementos cuando se genera el modelo de base de datos. Por motivos de rendimiento, el valor predeterminado es InMemory. Cuando se trata de bases de datos grandes, se requiere almacenamiento respaldado por archivos.|
|**/p:**|TreatVerificationErrorsAsWarnings=(BOOLEAN)|Especifica si publicación errores detectados durante la comprobación se debe tratar como advertencias. La comprobación se realiza con el plan de implementación generado antes de que el plan se ejecute con la base de datos de destino. El plan de comprobación detecta problemas, como la pérdida de objetos solo en el destino (como los índices) que deben quitarse para hacer un cambio. La comprobación también detecta situaciones en las que existen dependencias (como una tabla o vista) debido a una referencia a un proyecto compuesto, pero no existen en la base de datos de destino. Puede hacer esto para obtener una lista completa de todos los problemas, en lugar de tener la acción de publicación se detenga en el primer error. |
|**/p:**|UnmodifiableObjectWarnings = (booleano ' True')|Especifica si generar advertencias cuando se encuentren diferencias en los objetos que no se puedan modificar, por ejemplo, si el tamaño de archivo o las rutas de acceso a los archivos son diferentes para un archivo.| 
|**/p:**|VerifyCollationCompatibility = (booleano ' True')|Especifica si se comprobó la compatibilidad de intercalación.| 
|**/p:**|VerifyDeployment = (booleano ' True')|Especifica si realizar comprobaciones antes de la publicación que detengan la acción de publicación si hay problemas que pudieran impedir que la publicación se realizara correctamente. Por ejemplo, la acción de publicación podría detenerse si tiene claves externas en la base de datos de destino que no existan en el proyecto de base de datos, y eso provoca errores al publicar. |
  
## <a name="driftreport-parameters"></a>Parámetros DriftReport

Las acciones del informe **SqlPackage.exe** crean un informe XML de los cambios que se han realizado en una base de datos registrada desde que se registró por última vez.  
  
### <a name="help-for-driftreport-action"></a>Ayuda para la acción DriftReport

|Parámetro|Forma corta|Valor|Descripción|
|---|---|---|---|
|**/Action:**|**/a**|DriftReport|Especifica la acción que se va a realizar. |
|**/Diagnostics:**|**/d**|{True&#124;False}|Especifica si la salida del registro de diagnóstico es la consola. De forma predeterminada es False. |
|**/ DiagnosticsFile:**|**/DF**|{string}|Especifica un archivo para almacenar los registros de diagnóstico. |
|**/OutputPath:**|**/ Op.**|{string}|Especifica la ruta de acceso de archivo donde se generaron los archivos de salida. |
|**/ OverwriteFiles:**|**/of**|{True&#124;False}|Especifica si sqlpackage.exe debe sobrescribir los archivos existentes. Si se especifica False, sqlpackage.exe anula la acción si se encuentra un archivo existente. El valor predeterminado es True. |
|**/Quiet:**|**/q**|{True&#124;False}|Especifica si se suprimen los comentarios detallados. De forma predeterminada es False.|
|**/ TargetConnectionString:**|**/TCS**|{string}|Especifica una cadena de conexión válida de SQL Server o SQL Azure para la base de datos de destino. Si se especifica este parámetro, lo usan exclusivamente los demás parámetros de destino. |
|**/TargetDatabaseName:**|**/tdn**|{string}|Especifica una invalidación del nombre de la base de datos que es el destino de la acción sqlpackage.exe. |
|**/ TargetEncryptConnection:**|**/Tec**|{True&#124;False}|Especifica si se debe usar el cifrado de SQL para la conexión de base de datos de destino. |
|**/ ContraseñaDestino:**|**/tp**|{string}|En escenarios de autenticación de SQL Server, define la palabra clave que se va a usar para acceder a la base de datos de destino. |
|**/ TargetServerName:**|**/tsn**|{string}|Define el nombre del servidor que hospeda la base de datos de destino. |
|**/ TargetTimeout:**|**/tt**|{int}|Especifica el tiempo de espera para establecer una conexión con la base de datos de destino, en segundos. Para Azure AD, se recomienda que este valor sea mayor o igual a 30 segundos.|
|**/ TargetTrustServerCertificate:**|**/ttsc**|{True&#124;False}|Especifica si se usará SSL para cifrar la conexión con la base de datos de destino y no tener que recorrer la cadena de certificados para validar la confianza. |
|**/ TargetUser:**|**/tu**|{string}|En escenarios de autenticación de SQL Server, define el usuario de SQL Server que se va a usar para acceder a la base de datos de destino. |
|**/ TenantId:**|**/tid**|{string}|Representa el nombre de dominio o Id. de inquilino de Azure AD. Esta opción es necesaria para admitir a invitado o importa usuarios de Azure AD, así como cuentas de Microsoft como outlook.com, hotmail.com o live.com. Si se omite este parámetro, se usará de forma predeterminada, el Id. de inquilino para Azure AD, suponiendo que el usuario autenticado es un usuario nativo para este anuncio. Sin embargo, en este caso no se admiten cualquier invitado o los usuarios importados o cuentas de Microsoft hospedadas en este Azure AD y se producirá un error en la operación. <br/> Para obtener más información acerca de la autenticación Universal de Active Directory, consulte [autenticación Universal con SQL Database y SQL Data Warehouse (compatibilidad de SSMS con MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|
|**/ UniversalAuthentication:**|**/ua**|{True&#124;False}|Especifica si se debe usar la autenticación Universal. Cuando se establece en True, el protocolo de autenticación interactiva está activado compatible con MFA. Esta opción también puede utilizarse para la autenticación de Azure AD sin MFA, mediante un protocolo interactivo pedir al usuario que escriba su nombre de usuario y contraseña o autenticación integrada (credenciales de Windows). Cuando /UniversalAuthentication se establece en True, no se puede especificar ninguna autenticación de Azure AD en SourceConnectionString (/ scs). Cuando /UniversalAuthentication se establece en False, se debe especificar la autenticación de Azure AD en SourceConnectionString (/ scs). <br/> Para obtener más información acerca de la autenticación Universal de Active Directory, consulte [autenticación Universal con SQL Database y SQL Data Warehouse (compatibilidad de SSMS con MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|

## <a name="script-parameters-and-properties"></a>Parámetros y propiedades de script

Las acciones del script **SqlPackage.exe** crean un script de actualización incremental Transact-SQL que actualiza el esquema de una base de datos de destino para coincidir con el de una base de datos de origen.  
  
### <a name="help-for-the-script-action"></a>Ayuda para la acción de Script

|Parámetro|Forma corta|Valor|Descripción|
|---|---|---|---|
|**/Action:**|**/a**|Script|Especifica la acción que se va a realizar. |
|**/Diagnostics:**|**/d**|{True&#124;False}|Especifica si la salida del registro de diagnóstico es la consola. De forma predeterminada es False. |
|**/ DiagnosticsFile:**|**/DF**|{string}|Especifica un archivo para almacenar los registros de diagnóstico. |
|**/OutputPath:**|**/ Op.**|{string}|Especifica la ruta de acceso de archivo donde se generaron los archivos de salida. |
|**/ OverwriteFiles:**|**/of**|{True&#124;False}|Especifica si sqlpackage.exe debe sobrescribir los archivos existentes. Si se especifica False, sqlpackage.exe anula la acción si se encuentra un archivo existente. El valor predeterminado es True. |
|**/Profile:**|**/pr**|{string}|Especifica la ruta de acceso a un archivo para un perfil de publicación DAC. El perfil define una colección de propiedades y variables que se usarán cuando se generen resultados.|
|**/Properties:**|**/p**|{PropertyName}={Value}|Especifica un par de nombre y valor para una propiedad específica de acción; {PropertyName}={Value}. Remítase a la ayuda de una acción determinada para ver los nombres de propiedad de esa acción. Ejemplo: / Action sqlpackage.exe: publicar /?.|
|**/Quiet:**|**/q**|{True&#124;False}|Especifica si se suprimen los comentarios detallados. De forma predeterminada es False.|
|**/ SourceConnectionString:**|**/ SCS**|{string}|Especifica una cadena de conexión válida de SQL Server o SQL Azure para la base de datos de origen. Si se especifica este parámetro, lo usan exclusivamente los demás parámetros de origen. |
|**/SourceDatabaseName:**|**Export /**|{string}|Define el nombre de la base de datos de origen. |
|**/ SourceEncryptConnection:**|**/sec**|{True&#124;False}|Especifica si se debe usar cifrado SQL para la conexión de base de datos de origen. |
|**/ SourceFile:**|**/sf**|{string}|Especifica un archivo de origen que se va a usar como origen de la acción. Si se usa este parámetro, el resto de parámetros de origen no serán válidos. |
|**/SourcePassword:**|**/sp**|{string}|En escenarios de autenticación de SQL Server, define la palabra clave que se va a usar para acceder a la base de datos de origen. |
|**/ Nombreservidororigen:**|**/ssn**|{string}|Define el nombre del servidor que hospeda la base de datos de origen. |
|**/ SourceTimeout:**|**/st**|{int}|Especifica el tiempo de espera para establecer una conexión con la base de datos de origen, en segundos. |
|**/ SourceTrustServerCertificate:**|**/stsc**|{True&#124;False}|Especifica si se usará SSL para cifrar la conexión con la base de datos de origen y no tener que recorrer la cadena de certificados para validar la confianza. |
|**/SourceUser:**|**/su**|{string}|En escenarios de autenticación de SQL Server, define el usuario de SQL Server que se va a usar para acceder a la base de datos de origen. |
|**/ TargetConnectionString:**|**/TCS**|{string}|Especifica una cadena de conexión válida de SQL Server o SQL Azure para la base de datos de destino. Si se especifica este parámetro, lo usan exclusivamente los demás parámetros de destino. |
|**/TargetDatabaseName:**|**/tdn**|{string}|Especifica una invalidación del nombre de la base de datos que es el destino de la acción sqlpackage.exe. |
|**/ TargetEncryptConnection:**|**/Tec**|{True&#124;False}|Especifica si se debe usar el cifrado de SQL para la conexión de base de datos de destino. |
|**/ TargetFile:**|**/tf**|{string}| Especifica un archivo de destino (es decir, un archivo .dacpac) que se usará como el destino de acción en lugar de una base de datos. Si se usa este parámetro, el resto de parámetros de destino no serán válidos. Este parámetro será no válida para las acciones que admiten solo los destinos de base de datos.|
|**/ ContraseñaDestino:**|**/tp**|{string}|En escenarios de autenticación de SQL Server, define la palabra clave que se va a usar para acceder a la base de datos de destino. |
|**/ TargetServerName:**|**/tsn**|{string}|Define el nombre del servidor que hospeda la base de datos de destino. |
|**/ TargetTimeout:**|**/tt**|{int}|Especifica el tiempo de espera para establecer una conexión con la base de datos de destino, en segundos. Para Azure AD, se recomienda que este valor sea mayor o igual a 30 segundos.|
|**/ TargetTrustServerCertificate:**|**/ttsc**|{True&#124;False}|Especifica si se usará SSL para cifrar la conexión con la base de datos de destino y no tener que recorrer la cadena de certificados para validar la confianza. |
|**/ TargetUser:**|**/tu**|{string}|En escenarios de autenticación de SQL Server, define el usuario de SQL Server que se va a usar para acceder a la base de datos de destino. |
|**/ TenantId:**|**/tid**|{string}|Representa el nombre de dominio o Id. de inquilino de Azure AD. Esta opción es necesaria para admitir a invitado o importa usuarios de Azure AD, así como cuentas de Microsoft como outlook.com, hotmail.com o live.com. Si se omite este parámetro, se usará de forma predeterminada, el Id. de inquilino para Azure AD, suponiendo que el usuario autenticado es un usuario nativo para este anuncio. Sin embargo, en este caso no se admiten cualquier invitado o los usuarios importados o cuentas de Microsoft hospedadas en este Azure AD y se producirá un error en la operación. <br/> Para obtener más información acerca de la autenticación Universal de Active Directory, consulte [autenticación Universal con SQL Database y SQL Data Warehouse (compatibilidad de SSMS con MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|
|**/ UniversalAuthentication:**|**/ua**|{True&#124;False}|Especifica si se debe usar la autenticación Universal. Cuando se establece en True, el protocolo de autenticación interactiva está activado compatible con MFA. Esta opción también puede utilizarse para la autenticación de Azure AD sin MFA, mediante un protocolo interactivo pedir al usuario que escriba su nombre de usuario y contraseña o autenticación integrada (credenciales de Windows). Cuando /UniversalAuthentication se establece en True, no se puede especificar ninguna autenticación de Azure AD en SourceConnectionString (/ scs). Cuando /UniversalAuthentication se establece en False, se debe especificar la autenticación de Azure AD en SourceConnectionString (/ scs). <br/> Para obtener más información acerca de la autenticación Universal de Active Directory, consulte [autenticación Universal con SQL Database y SQL Data Warehouse (compatibilidad de SSMS con MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication).|
|**/Variables:**|**/v**|{PropertyName}={Value}|Especifica un par de nombre y valor para una variable específica de acción; {VariableName}={Value}. El archivo DACPAC contiene la lista de variables SQLCMD válidas. Se produce un error si no se facilita un valor para cada variable. |

### <a name="properties-specific-to-the-script-action"></a>Propiedades específicas de la acción de Script

|Propiedad|Valor|Descripción|
|---|---|---|
|**/p:**|AdditionalDeploymentContributorArguments=(STRING)|Especifica los argumentos de colaborador de implementación adicionales para los colaboradores de implementación. Debe ser una lista de valores delimitada por punto y coma.
|**/p:**|AdditionalDeploymentContributors=(STRING)|Especifica colaboradores de implementación adicionales que se deben ejecutar cuando se implementa el dacpac. Debe ser una lista delimitada por punto y coma de nombres completos o identificadores de los colaboradores de compilación.
|**/p:**|AllowDropBlockingAssemblies=(BOOLEAN)|Esta propiedad se usa en la implementación de SqlClr para hacer que cualquier ensamblado de bloqueo se quite como parte del plan de implementación. De forma predeterminada, cualquier ensamblado de bloqueo o de referencia bloqueará la actualización de un ensamblado si el ensamblado de referencia tiene que quitarse.
|**/p:**|AllowIncompatiblePlatform=(BOOLEAN)|Especifica si se intenta la acción a pesar de las posibles plataformas de SQL Server incompatibles.
|**/p:**|AllowUnsafeRowLevelSecurityDataMovement=(BOOLEAN)|No bloquee la transferencia de datos en una tabla con Seguridad de nivel de fila si esta propiedad está establecida en true. El valor predeterminado es False.
|**/p:**|BackupDatabaseBeforeChanges=(BOOLEAN)|Hace una copia de seguridad de la base de datos antes de implementar ningún cambio.
|**/p:**|BlockOnPossibleDataLoss = (booleano ' True')|Especifica que se debe finalizar el episodio de publicación si existiera la posibilidad de que se perdieran datos a causa de la operación de publicación.
|**/p:**|BlockWhenDriftDetected = (booleano ' True')|Especifica si bloquear la actualización de una base de datos cuyo esquema ha dejado de corresponderse con su registro o no está registrada.
|**/p:**|CommandTimeout = (INT32 "60")|Especifica el tiempo de espera de comando en segundos cuando se ejecutan consultas en SQL Server.
|**/p:**|CommentOutSetVarDeclarations=(BOOLEAN)|Especifica si la declaración de las variables SETVAR se incluyen entre comentarios en el script de publicación generado. Puede optar por esta opción si planea usar una herramienta como SQLCMD.EXE para especificar los valores de la línea de comandos al publicar.
|**/p:**|CompareUsingTargetCollation=(BOOLEAN)|Esta configuración determina la forma en que se trata la intercalación de la base de datos durante la implementación; de forma predeterminada, la intercalación de la base de datos de destino se actualizará si no coincide con la especificada por el origen. Cuando se ha establecido esta opción, se usará la intercalación de la base de datos (o servidor) de destino.|
|**/p:**|CreateNewDatabase=(BOOLEAN)|Especifica si la base de datos de destino debe actualizarse o si se va a quitar para volver a crearse al publicar en una base de datos.
|**/p:**|DatabaseEdition = ({Basic&#124;estándar&#124;Premium&#124;predeterminada} 'Default')|Define la edición de una base de datos de SQL Azure.
|**/p:**|DatabaseMaximumSize=(INT32)|Define el tamaño máximo en GB de una instancia de Azure SQL Database.
|**/p:**|DatabaseServiceObjective=(STRING)|Define el nivel de rendimiento de una instancia de Azure SQL Database, como "P0" o "S1".
|**/p:**|DeployDatabaseInSingleUserMode=(BOOLEAN)|Si se establece en True, la base de datos se establecerá en modo de usuario único antes de implementarse.
|**/p:**|DisableAndReenableDdlTriggers = (booleano ' True')| Especifica si los desencadenadores del Lenguaje de definición de datos (DDL) se deshabilitan al principio del proceso de publicación y se vuelven a habilitar al final de la acción de publicación.|
|**/p:**|DoNotAlterChangeDataCaptureObjects = (booleano ' True')|Si se establece en true, los objetos de captura de datos modificados no se verán alterados.
|**/p:**|DoNotAlterReplicatedObjects = (booleano ' True')|Especifica si los objetos que se replican se van a identificar durante la comprobación.
|**/p:**|DoNotDropObjectType=(STRING)|Un tipo de objeto que no debería quitarse si DropObjectsNotInSource es true. Los nombres de tipo de objeto válidos son: Aggregates, ApplicationRoles, Assemblies, AsymmetricKeys, BrokerPriorities, Certificates, ColumnEncryptionKeys, ColumnMasterKeys, Contracts, DatabaseRoles, DatabaseTriggers, Defaults, ExtendedProperties, ExternalDataSources, ExternalFileFormats, ExternalTables, Filegroups, FileTables, FullTextCatalogs, FullTextStoplists, MessageTypes, PartitionFunctions, PartitionSchemes, Permissions, Queues, RemoteServiceBindings, RoleMembership, Rules, ScalarValuedFunctions, SearchPropertyLists, SecurityPolicies, Sequences, Services, Signatures, StoredProcedures, SymmetricKeys, Synonyms, Tables, TableValuedFunctions, UserDefinedDataTypes, UserDefinedTableTypes, ClrUserDefinedTypes, Users, Views, XmlSchemaCollections, Audits, Credentials, CryptographicProviders, DatabaseAuditSpecifications, DatabaseScopedCredentials, Endpoints, ErrorMessages, EventNotifications, EventSessions, LinkedServerLogins, LinkedServers, Logins, Routes, ServerAuditSpecifications, ServerRoleMembership, ServerRoles, ServerTriggers.
|**/p:**|DoNotDropObjectTypes=(STRING)|Lista delimitada por puntos y coma de tipos de objetos que no deberían quitarse si DropObjectsNotInSource es true. Los nombres de tipo de objeto válidos son: Aggregates, ApplicationRoles, Assemblies, AsymmetricKeys, BrokerPriorities, Certificates, ColumnEncryptionKeys, ColumnMasterKeys, Contracts, DatabaseRoles, DatabaseTriggers, Defaults, ExtendedProperties, ExternalDataSources, ExternalFileFormats, ExternalTables, Filegroups, FileTables, FullTextCatalogs, FullTextStoplists, MessageTypes, PartitionFunctions, PartitionSchemes, Permissions, Queues, RemoteServiceBindings, RoleMembership, Rules, ScalarValuedFunctions, SearchPropertyLists, SecurityPolicies, Sequences, Services, Signatures, StoredProcedures, SymmetricKeys, Synonyms, Tables, TableValuedFunctions, UserDefinedDataTypes, UserDefinedTableTypes, ClrUserDefinedTypes, Users, Views, XmlSchemaCollections, Audits, Credentials, CryptographicProviders, DatabaseAuditSpecifications, DatabaseScopedCredentials, Endpoints, ErrorMessages, EventNotifications, EventSessions, LinkedServerLogins, LinkedServers, Logins, Routes, ServerAuditSpecifications, ServerRoleMembership, ServerRoles, ServerTriggers.
|**/p:**|DropConstraintsNotInSource = (booleano ' True')|Especifica si las restricciones que no existen en el archivo de la instantánea de base de datos (.dacpac) se van a quitar de la base de datos de destino al publicar en una base de datos.|
|**/p:**|DropDmlTriggersNotInSource = (booleano ' True')|Especifica si los desencadenadores de DML que no existen en el archivo de la instantánea de base de datos (.dacpac) se van a quitar de la base de datos de destino al publicar en una base de datos.|
|**/p:**|DropExtendedPropertiesNotInSource = (booleano ' True')|Especifica si las propiedades extendidas que no existen en el archivo de instantánea de base de datos (.dacpac) se quitarán de la base de datos de destino al publicar en una base de datos.|
|**/p:**|DropIndexesNotInSource = (booleano ' True')|Especifica si los índices que no existen en el archivo de la instantánea de base de datos (.dacpac) se van a quitar de la base de datos de destino al publicar en una base de datos.|
|**/p:**|DropObjectsNotInSource=(BOOLEAN)|Especifica si los objetos que no existen en el archivo de la instantánea de base de datos (.dacpac) se van a quitar de la base de datos de destino al publicar en una base de datos. Este valor tiene prioridad sobre DropExtendedProperties.|
|**/p:**|DropPermissionsNotInSource=(BOOLEAN)|Especifica si los permisos que no existen en el archivo de la instantánea de base de datos (.dacpac) se van a quitar de la base de datos de destino al publicar actualizaciones en una base de datos.|
|**/p:**|DropRoleMembersNotInSource=(BOOLEAN)|Especifica si los miembros de rol que no se definieron en el archivo de la instantánea de base de datos (.dacpac) se van a quitar de la base de datos de destino al publicar actualizaciones en una base de datos.|
|**/p:**|DropStatisticsNotInSource = (booleano ' True')|Especifica si las estadísticas que no existen en el archivo de instantánea de base de datos (.dacpac) se quitarán de la base de datos de destino al publicar en una base de datos.|
|**/p:**|ExcludeObjectType=(STRING)|Un tipo de objeto que se debe omitir durante la implementación. Los nombres de tipo de objeto válidos son Aggregates, ApplicationRoles, Assemblies, AsymmetricKeys, BrokerPriorities, Certificates, ColumnEncryptionKeys, ColumnMasterKeys, Contracts, DatabaseRoles, DatabaseTriggers, Defaults, ExtendedProperties, ExternalDataSources, ExternalFileFormats, ExternalTables, Filegroups, FileTables, FullTextCatalogs, FullTextStoplists, MessageTypes, PartitionFunctions, PartitionSchemes, Permissions, Queues, RemoteServiceBindings, RoleMembership, Rules, ScalarValuedFunctions, SearchPropertyLists, SecurityPolicies, Sequences, Services, Signatures, StoredProcedures, SymmetricKeys, Synonyms, Tables, TableValuedFunctions, UserDefinedDataTypes, UserDefinedTableTypes, ClrUserDefinedTypes, Users, Views, XmlSchemaCollections, Audits, Credentials, CryptographicProviders, DatabaseAuditSpecifications, DatabaseScopedCredentials, Endpoints, ErrorMessages, EventNotifications, EventSessions, LinkedServerLogins, LinkedServers, Logins, Routes, ServerAuditSpecifications, ServerRoleMembership, ServerRoles, ServerTriggers.
|**/p:**|ExcludeObjectTypes=(STRING)|Lista delimitada por puntos y coma de tipos de objetos que se deben omitir durante la implementación. Los nombres de tipo de objeto válidos son: Aggregates, ApplicationRoles, Assemblies, AsymmetricKeys, BrokerPriorities, Certificates, ColumnEncryptionKeys, ColumnMasterKeys, Contracts, DatabaseRoles, DatabaseTriggers, Defaults, ExtendedProperties, ExternalDataSources, ExternalFileFormats, ExternalTables, Filegroups, FileTables, FullTextCatalogs, FullTextStoplists, MessageTypes, PartitionFunctions, PartitionSchemes, Permissions, Queues, RemoteServiceBindings, RoleMembership, Rules, ScalarValuedFunctions, SearchPropertyLists, SecurityPolicies, Sequences, Services, Signatures, StoredProcedures, SymmetricKeys, Synonyms, Tables, TableValuedFunctions, UserDefinedDataTypes, UserDefinedTableTypes, ClrUserDefinedTypes, Users, Views, XmlSchemaCollections, Audits, Credentials, CryptographicProviders, DatabaseAuditSpecifications, DatabaseScopedCredentials, Endpoints, ErrorMessages, EventNotifications, EventSessions, LinkedServerLogins, LinkedServers, Logins, Routes, ServerAuditSpecifications, ServerRoleMembership, ServerRoles, ServerTriggers.
|**/p:**|GenerateSmartDefaults=(BOOLEAN)|Proporciona automáticamente un valor predeterminado cuando se actualiza una tabla que contiene datos con una columna que no admite valores NULL.
|**/p:**|IgnoreAnsiNulls = (booleano ' True')|Especifica si las diferencias en la configuración ANSI NULLS se deben ignorar o actualizar al publicar en una base de datos.
|**/p:**|IgnoreAuthorizer=(BOOLEAN)|Especifica si las diferencias en el autorizador se deben ignorar o actualizar al publicar en una base de datos.
|**/p:**|IgnoreColumnCollation=(BOOLEAN)|Especifica si las diferencias en las intercalaciones de columnas se deben ignorar o actualizar al publicar en una base de datos.
|**/p:**|IgnoreColumnOrder=(BOOLEAN)|Especifica si hay que omitir las diferencias en el orden de las columnas de una tabla o bien hay que actualizar al publicar en una base de datos.|
|**/p:**|IgnoreComments=(BOOLEAN)|Especifica si las diferencias en los comentarios se deben ignorar o actualizar al publicar en una base de datos.
|**/p:**|IgnoreCryptographicProviderFilePath = (booleano ' True')|Especifica si las diferencias en la ruta de acceso del archivo del proveedor de servicios criptográficos se deben ignorar o actualizar al publicar en una base de datos.
|**/p:**|IgnoreDdlTriggerOrder=(BOOLEAN)|Especifica si las diferencias en el orden de los desencadenadores de Data Definition Language (DDL) se deben ignorar o actualizar al publicar en una base de datos o en un servidor.|
|**/p:**|IgnoreDdlTriggerState=(BOOLEAN)|Especifica si las diferencias en el estado habilitado o deshabilitado de los desencadenadores de Data Definition Language (DDL) se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreDefaultSchema=(BOOLEAN)|Especifica si las diferencias en el esquema predeterminado se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreDmlTriggerOrder=(BOOLEAN)|Especifica si las diferencias en el orden de los desencadenadores del lenguaje de manipulación de datos (DML) se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreDmlTriggerState=(BOOLEAN)|Especifica si las diferencias en el estado habilitado o deshabilitado de los desencadenadores de DML se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreExtendedProperties=(BOOLEAN)|Especifica si las diferencias en las propiedades extendidas se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreFileAndLogFilePath = (booleano ' True')|Especifica si las diferencias en las rutas de acceso de los archivos y archivos de registro se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreFilegroupPlacement = (booleano ' True')|Especifica si las diferencias en la colocación de objetos en FILEGROUPs se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreFileSize = (booleano ' True')|Especifica si las diferencias en los tamaños de archivo se deben ignorar o si debe generarse una advertencia al publicar en una base de datos.|
|**/p:**|IgnoreFillFactor = (booleano ' True')|Especifica si las diferencias en el factor de relleno del almacenamiento de índices se deben omitir o si debe generarse una advertencia al publicar.|
|**/p:**|IgnoreFullTextCatalogFilePath = (booleano ' True')|Especifica si las diferencias en la ruta de acceso al archivo del catálogo de texto completo se deben ignorar o si debe generarse una advertencia al publicar en una base de datos.|
|**/p:**|IgnoreIdentitySeed=(BOOLEAN)|Especifica si las diferencias en el valor de inicialización de una columna de identidad se deben ignorar o actualizar al publicar actualizaciones en una base de datos.|
|**/p:**|IgnoreIncrement=(BOOLEAN)|Especifica si las diferencias en el incremento de una columna de identidad se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreIndexOptions=(BOOLEAN)|Especifica si las diferencias en las opciones de índice se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreIndexPadding = (booleano ' True')|Especifica si las diferencias en el relleno de índice se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreKeywordCasing = (booleano ' True')|Especifica si las diferencias en el uso de mayúsculas y minúsculas en palabras clave se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreLockHintsOnIndexes=(BOOLEAN)|Especifica si las diferencias en las sugerencias de bloqueo en los índices se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreLoginSids = (booleano ' True')| Especifica si las diferencias en el número de identificación de seguridad (SID) se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreNotForReplication=(BOOLEAN)|Especifica si la configuración de no replicación se debe ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreObjectPlacementOnPartitionScheme = (booleano ' True')|Especifica si la colocación de un objeto en un esquema de partición se debe ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnorePartitionSchemes=(BOOLEAN)|Especifica si las diferencias en las funciones y los esquemas de particiones se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnorePermissions=(BOOLEAN)|Especifica si las diferencias en los permisos se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreQuotedIdentifiers = (booleano ' True')|Especifica si las diferencias en la configuración de identificadores entre comillas se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|IgnoreRoleMembership=(BOOLEAN)|Especifica si se omitirán o se actualizarán las diferencias en las pertenencias a roles de los inicios de sesión al publicar en una base de datos.|
|**/p:**|IgnoreRouteLifetime = (booleano ' True')|Especifica si las diferencias en cuanto al periodo durante el cual SQL Server conserva la ruta en la tabla de enrutamiento se deben omitir o si hay que actualizar al publicar en una base de datos.|
|**/p:**|IgnoreSemicolonBetweenStatements = (booleano ' True')|Especifica si las diferencias en los caracteres de punto y coma entre las instrucciones T-SQL se ignorarán o se actualizarán al publicar en una base de datos.|
|**/p:**|IgnoreTableOptions=(BOOLEAN)|Especifica si las diferencias en las opciones de tabla se ignorarán o se actualizarán al publicar en una base de datos.|
|**/p:**|IgnoreUserSettingsObjects=(BOOLEAN)|Especifica si las diferencias en los objetos de configuración de usuario se ignorarán o se actualizarán al publicar en una base de datos.|
|**/p:**|IgnoreWhitespace = (booleano ' True')|Especifica si las diferencias en los espacios en blanco se ignorarán o se actualizarán al publicar en una base de datos.|
|**/p:**|IgnoreWithNocheckOnCheckConstraints=(BOOLEAN)|Especifica si las diferencias en el valor de la cláusula WITH NOCHECK de las restricciones CHECK se omiten o hay que actualizar al publicar.|
|**/p:**|IgnoreWithNocheckOnForeignKeys=(BOOLEAN)|Especifica si las diferencias en el valor de la cláusula WITH NOCHECK para las claves externas se ignorarán o se actualizarán al publicar en una base de datos.|
|**/p:**|IncludeCompositeObjects=(BOOLEAN)|Incluir todos los elementos compuestos como parte de una única operación de publicación.|
|**/p:**|IncludeTransactionalScripts=(BOOLEAN)|Especifica si las instrucciones transaccionales se deben usar siempre que sea posible al publicar en una base de datos.|
|**/p:**|NoAlterStatementsToChangeClrTypes=(BOOLEAN)|Especifica que la acción de publicación debe quitar y volver a crear siempre un ensamblado en lugar de emitir una instrucción ALTER ASSEMBLY.|
|**/p:**|PopulateFilesOnFileGroups = (booleano ' True')|Especifica si se crea también un nuevo archivo cuando se crea un nuevo FileGroup en la base de datos de destino.|
|**/p:**|RegisterDataTierApplication=(BOOLEAN)|Especifica si el esquema está registrado con el servidor de base de datos.|
|**/p:**|RunDeploymentPlanExecutors=(BOOLEAN)|Especifica si los colaboradores DeploymentPlanExecutor deben ejecutarse cuando se ejecutan otras operaciones.|
|**/p:**|ScriptDatabaseCollation=(BOOLEAN)|Especifica si las diferencias en la intercalación de la base de datos se deben omitir o actualizar al publicar en una base de datos.|
|**/p:**|ScriptDatabaseCompatibility=(BOOLEAN)|Especifica si las diferencias en la compatibilidad de la base de datos se deben ignorar o actualizar al publicar en una base de datos.|
|**/p:**|ScriptDatabaseOptions = (booleano ' True')|Especifica si las propiedades de la base de datos deben establecerse o actualizarse como parte de la acción de publicación.|
|**/p:**|ScriptDeployStateChecks=(BOOLEAN)|Especifica si se generan instrucciones en el script de publicación para comprobar que el nombre de la base de datos y el nombre del servidor coinciden con los nombres especificados en el proyecto de base de datos.|
|**/p:**|ScriptFileSize=(BOOLEAN)|Controla si el tamaño se especifica cuando se agrega un archivo a un grupo de archivos.|
|**/p:**|ScriptNewConstraintValidation = (booleano ' True')|Al final de la publicación todas las restricciones se comprobarán como un conjunto, evitando los errores de datos causados por una comprobación o una restricción foreign key en medio de la publicación. Si esta opción es False, las restricciones se publican sin comprobar los datos correspondientes.|
|**/p:**|ScriptRefreshModule = (booleano ' True')|Incluye instrucciones de actualización al final del script de publicación.|
|**/p:**|Almacenamiento = ({archivo&#124;memoria})|Especifica la forma en que se almacenan los elementos cuando se genera el modelo de base de datos. Por motivos de rendimiento, el valor predeterminado es InMemory. Cuando se trata de bases de datos grandes, se requiere almacenamiento respaldado por archivos.|
|**/p:**|TreatVerificationErrorsAsWarnings=(BOOLEAN)|Especifica si publicación errores detectados durante la comprobación se debe tratar como advertencias. La comprobación se realiza con el plan de implementación generado antes de que el plan se ejecute con la base de datos de destino. El plan de comprobación detecta problemas, como la pérdida de objetos solo en el destino (como los índices) que deben quitarse para hacer un cambio. La comprobación también detecta situaciones en las que existen dependencias (como una tabla o vista) debido a una referencia a un proyecto compuesto, pero no existen en la base de datos de destino. Puede hacer esto para obtener una lista completa de todos los problemas, en lugar de tener la acción de publicación se detenga en el primer error.|
|**/p:**|UnmodifiableObjectWarnings = (booleano ' True')|Especifica si generar advertencias cuando se encuentren diferencias en los objetos que no se puedan modificar, por ejemplo, si el tamaño de archivo o las rutas de acceso a los archivos son diferentes para un archivo.|
|**/p:**|VerifyCollationCompatibility = (booleano ' True')|Especifica si se comprobó la compatibilidad de intercalación.
|**/p:**|VerifyDeployment = (booleano ' True')|Especifica si realizar comprobaciones antes de la publicación que detengan la acción de publicación si hay problemas que pudieran impedir que la publicación se realizara correctamente. Por ejemplo, la acción de publicación podría detenerse si tiene claves externas en la base de datos de destino que no existan en el proyecto de base de datos, y eso provoca errores al publicar.|
  