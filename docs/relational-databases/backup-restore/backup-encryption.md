---
title: "Cifrado de copia de seguridad | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 334b95a8-6061-4fe0-9e34-b32c9f1706ce
caps.latest.revision: 18
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 16
---
# Cifrado de copia de seguridad
  Este tema proporciona información general sobre las opciones de cifrado para las copias de seguridad de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Incluye detalles del uso, los beneficios y las prácticas recomendadas para el cifrado durante la copia de seguridad.  
  
 **En este tema:**  
  
-   [Información general](../../relational-databases/backup-restore/backup-encryption.md#Overview)  
  
-   [Ventajas](#Benefits)  
  
-   [Requisitos previos](../../relational-databases/backup-restore/backup-encryption.md#Prerequisites)  
  
-   [Restricciones](#Restrictions)  
  
-   [Permisos](../../relational-databases/backup-restore/backup-encryption.md#Permissions)  
  
-   [Métodos de cifrado de copia de seguridad](../../relational-databases/backup-restore/backup-encryption.md#Methods)  
  
-   [Prácticas recomendadas](../../relational-databases/backup-restore/backup-encryption.md#RecommendedPractices)  
  
-   [Tareas relacionadas](#RelatedTasks)  
  
##  <a name="Overview"></a> Información general  
 A partir de [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], SQL Server tiene la capacidad de cifrar los datos mientras crea una copia de seguridad. Al especificar el algoritmo y el sistema de cifrado (un certificado o una clave asimétrica) al crear una copia de seguridad, puede crear un archivo de copia de seguridad cifrado. Todos los destinos de almacenamiento: se admite el almacenamiento de Windows Azure y local. Además, las opciones de cifrado se pueden configurar para las operaciones de [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)], una característica nueva presentada en [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
 Para cifrar durante la copia de seguridad, debe especificar un algoritmo y un sistema cifrado para proteger la clave de cifrado. A continuación se exponen las opciones admitidas de cifrado:  
  
-   **Algoritmo de cifrado:** los algoritmos de cifrado admitidos son: AES 128, AES 192, AES 256 y Triple DES  
  
-   **Sistema de cifrado:** un certificado o una clave asimétrica  
  
> [!CAUTION]  
>  Es muy importante realizar una copia de seguridad del certificado o la clave asimétrica, y preferiblemente en una ubicación diferente de la que se usó para cifrar el archivo de copia de seguridad. Sin el certificado o la clave asimétrica, no puede restaurar la copia de seguridad, lo que deja inutilizable el archivo de copia de seguridad.  
  
 **Restaurar la copia de seguridad cifrada:** la restauración de SQL Server no requiere que se especifiquen parámetros de cifrado durante la restauración. Requiere que el certificado o la clave simétrica utilizada para cifrar el archivo de copia de seguridad esté disponible en la instancia en la que está realizando la restauración. La cuenta de usuario que realiza la restauración debe tener permisos de **VIEW DEFINITION** en el certificado o la clave. Si restaura la copia de seguridad cifrada en una instancia diferente, debe asegurarse de que el certificado esté disponible en esa instancia.  
  
 Si va a restaurar una copia de seguridad desde una base de datos cifrada TDE, el certificado TDE debe estar disponible en la instancia en la que va a restaurar.  
  
##  <a name="Benefits"></a> Ventajas  
  
1.  Cifrar las copias de seguridad de la base de datos ayuda a proteger los datos: SQL Server proporciona la opción de cifrar los datos de copia de seguridad al crear una copia de seguridad.  
  
2.  El cifrado se puede utilizar también para las bases de datos que se cifran mediante TDE.  
  
3.  El cifrado se admite para las copias de seguridad realizadas por [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)], lo que proporciona una seguridad adicional para las copias de seguridad fuera de las instalaciones.  
  
4.  Esta característica admite varios algoritmos de cifrado, hasta AES de 256 bits. Esto ofrece la opción de seleccionar un algoritmo que se adapte a sus requisitos.  
  
5.  Puede integrar las claves de cifrado con los proveedores de Administración extensible de claves (EKM).  
  
 [&#91;Principio&#93;](#Top)  
  
##  <a name="Prerequisites"></a> Requisitos previos  
 Estos son los requisitos previos para cifrar una copia de seguridad:  
  
1.  **Crear una clave maestra de base de datos para la base de datos maestra:** la clave maestra de base de datos es una clave simétrica que se usa para proteger las claves privadas de certificados y las claves asimétricas presentes en la base de datos. Para obtener más información, vea [SQL Server y claves de cifrado de base de datos &#40;motor de base de datos&#41;](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md).  
  
2.  Cree un certificado o clave asimétrica para utilizarla en el cifrado de copia de seguridad. Para obtener más información sobre cómo crear un certificado, vea [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md). Para obtener más información sobre cómo crear una clave asimétrica, vea [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md).  
  
    > [!IMPORTANT]  
    >  Solo se admiten las claves asimétricas que residan en una Administración extensible de claves (EKM).  
  
##  <a name="Restrictions"></a> Restricciones  
 A continuación se exponen las restricciones que se aplican a las opciones de cifrado:  
  
-   Si utiliza una clave asimétrica para cifrar los datos de copia de seguridad, solo se admiten las claves asimétricas que residan en el proveedor EKM.  
  
-   SQL Server Express y SQL Server Web no admiten el cifrado durante la copia de seguridad. Sin embargo, sí se admite la restauración de una copia de seguridad cifrada en una instancia de SQL Server Express o SQL Server Web.  
  
-   Las versiones anteriores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no pueden leer copias de seguridad cifradas.  
  
-   La opción de anexar a un conjunto de copia de seguridad existente no se admite para las copias de seguridad cifradas.  
  
 [&#91;Principio&#93;](#Top)  
  
##  <a name="Permissions"></a> Permisos  
 **Para cifrar una copia de seguridad o restaurarla desde una copia de seguridad cifrada:**  
  
 El permiso**VIEW DEFINITION** en el certificado o la clave asimétrica que se usa para cifrar la copia de seguridad de base de datos.  
  
> [!NOTE]  
>  El acceso al certificado TDE no es necesario para realizar una copia de seguridad o restaurar una base de datos protegida por TDE.  
  
##  <a name="Methods"></a> Métodos de cifrado de copia de seguridad  
 Las secciones siguientes proporcionan una introducción breve a los pasos para cifrar los datos durante la copia de seguridad. Para ver un tutorial completo de los diferentes pasos para cifrar la copia de seguridad mediante Transact-SQL, vea [Crear una copia de seguridad cifrada](../../relational-databases/backup-restore/create-an-encrypted-backup.md).  
  
### Usar SQL Server Management Studio  
 Puede cifrar una copia de seguridad al crear la copia de seguridad de una base de datos en alguno de los siguientes cuadros de diálogo:  
  
1.  [Copia de seguridad de la base de datos &#40;página Opciones de copia de seguridad&#41;](../../relational-databases/backup-restore/back-up-database-backup-options-page.md) En la página **Opciones de copia de seguridad**, puede seleccionar **Cifrado** y especificar el algoritmo de cifrado y el certificado o la clave asimétrica que va a usar para el cifrado.  
  
2.  [Usar el Asistente para planes de mantenimiento](../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure) Al seleccionar una tarea de copia de seguridad, en la pestaña **Opciones** de la página **Definir la tarea de copia de seguridad**, puede seleccionar **Cifrado de copia de seguridad** y especificar el algoritmo de cifrado y el certificado o la clave que se usarán para el cifrado.  
  
### Usar Transact SQL:  
 La siguiente es una instrucción Transact-SQL de ejemplo para cifrar el archivo de copia de seguridad:  
  
```  
BACKUP DATABASE [MYTestDB]  
TO DISK = N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
WITH  
  COMPRESSION,  
  ENCRYPTION   
   (  
   ALGORITHM = AES_256,  
   SERVER CERTIFICATE = BackupEncryptCert  
   ),  
  STATS = 10  
GO  
  
```  
  
 Para obtener la sintaxis completa de la instrucción Transact-SQL, vea [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md).  
  
### Usar PowerShell  
 En este ejemplo se crean las opciones de cifrado y se usan como valor de parámetro en el cmdlet **Backup-SqlDatabase** para crear una copia de seguridad cifrada.  
  
```  
C:\PS>$encryptionOption = New-SqlBackupEncryptionOption -Algorithm Aes256 -EncryptorType ServerCertificate -EncryptorName "BackupCert"  
```  
  
```  
C:\PS>Backup-SqlDatabase -ServerInstance . -Database "MyTestDB" -BackupFile "MyTestDB.bak" -CompressionOption On -EncryptionOption $encryptionOption  
```  
  
##  <a name="RecommendedPractices"></a> Prácticas recomendadas  
 Cree una copia de seguridad del certificado de cifrado y las claves en una ubicación distinta del equipo local donde la instancia esté instalada. Para tener en cuenta escenarios de recuperación de desastres, considere almacenar una copia de seguridad del certificado o la clave en una ubicación fuera de las instalaciones. No puede restaurar una copia de seguridad cifrada sin el certificado usado para cifrarla.  
  
 Para restaurar una copia de seguridad cifrada, el certificado original utilizado cuando se realizó la copia de seguridad con la huella digital coincidente debe estar disponible en la instancia en la que va a realizar la restauración. Por consiguiente, el certificado no debe renovarse al caducar ni cambiarse de forma alguna. La renovación puede provocar la actualización el certificado, lo que desencadenaría el cambio de la huella digital y, por consiguiente, invalidaría el certificado para el archivo de copia de seguridad. La cuenta que realiza la restauración debe tener los permisos VIEW DEFINITION en el certificado o la clave simétrica utilizada para cifrar durante la copia de seguridad.  
  
 Las copias de seguridad de bases de datos del grupo de disponibilidad se suelen realizar en la réplica de copia de seguridad preferida.  Si va a restaurar una copia de seguridad en una réplica distinta de aquella en la que se creó la copia de seguridad, asegúrese de que el certificado original usado para la copia de seguridad está disponible en la réplica donde va a realizar la restauración.  
  
 Si la base de datos está habilitada para usar TDE, elija distintos certificados o claves asimétricas para cifrar la base de datos y la copia de seguridad a fin de aumentar la seguridad.  
  
##  <a name="RelatedTasks"></a> Tareas relacionadas  
  
|Tema y tarea|Descripción|  
|-----------------|-----------------|  
|[Crear una copia de seguridad cifrada](../../relational-databases/backup-restore/create-an-encrypted-backup.md)|Describe los pasos básicos necesarios para crear una copia de seguridad cifrada|  
|[Administración extensible de claves con el Almacén de claves de Azure &#40;SQL Server&#41;](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)|Proporciona un ejemplo de creación de una copia de seguridad cifrada protegida por claves en el almacén de claves de Azure.|  
  
## Vea también  
 [Información general de copia de seguridad &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md)  
  
  