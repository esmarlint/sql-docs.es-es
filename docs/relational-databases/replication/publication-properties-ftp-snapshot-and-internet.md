---
title: "Propiedades de la publicaci&#243;n, Instant&#225;nea de FTP e Internet | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.pubproperties.internetsynchronization.f1"
ms.assetid: 8e0198c3-5e4e-418c-9920-78ccbbfc1323
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# Propiedades de la publicaci&#243;n, Instant&#225;nea de FTP e Internet
  Esta página permite:  
  
-   Establecer propiedades para entregar la instantánea mediante FTP (Protocolo de transferencia de archivos). Para obtener más información, consulte [Transferir instantáneas mediante FTP](../../relational-databases/replication/transfer-snapshots-through-ftp.md). Si desea usar el FTP para la entrega de instantáneas deberá configurar un servidor FTP. Vea la documentación de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows para obtener más información.  
  
    > [!NOTE]  
    >  Si realiza algún cambio en la configuración del FTP deberá generar una nueva instantánea.  
  
-   Establecer propiedades de sincronización web para replicaciones de mezcla en [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] y versiones posteriores, lo que permite sincronizar las suscripciones mediante HTTPS (Protocolo de transferencia de hipertexto seguro). Para poder utilizar la sincronización web deberá configurar un servidor de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS). Para más información, consulte [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md).  
  
## Opciones  
 **Obtener acceso a archivos de instantánea a través de FTP**  
 Seleccione **Permitir a los suscriptores descargar archivos de instantáneas mediante FTP (Protocolo de transferencia de archivos)**, y especifique **nombre del servidor FTP**, **número de puerto**, **ruta de acceso de la carpeta raíz FTP**, **Inicio de sesión**, y **contraseña**, para permitir que los suscriptores utilicen FTP para entregar instantáneas.  
  
 Esta opción permite a los suscriptores usar el FTP para recuperar archivos de instantáneas, pero no les obliga a hacerlo. Si se selecciona esta opción, el Asistente para nueva suscripción establece de forma predeterminada que el suscriptor debe recuperar los archivos de instantáneas mediante el FTP. Puede cambiar esta configuración en el cuadro de diálogo **Propiedades de suscripción** . Si permite a los suscriptores tener acceso a los archivos de instantáneas mediante el FTP, debe especificar la carpeta FTP y la ubicación de los archivos de instantáneas en la página **Instantánea** del cuadro de diálogo **Propiedades de la publicación** . Al hacerlo de esta forma, el Agente de instantáneas actualiza automáticamente los archivos en la carpeta FTP cuando se genera una nueva instantánea. Si no establece la carpeta FTP como ubicación, deberá actualizar manualmente los archivos al generar nuevas instantáneas. Para obtener más información, consulte [entregar una instantánea mediante FTP](../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md).  
  
 **Sincronización web**  
 Solo replicación de mezcla. Active **Permitir a los suscriptores sincronizarse mediante la conexión a un servidor web**y especifique la dirección de un servidor web para permitir a los suscriptores de mezcla utilizar la sincronización web. El servidor web debe usar SSL (Capa de sockets seguros) y la dirección web debe ser completa (por ejemplo, https://servidor.dominio.com/sincronizar). Para más información, consulte [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md).  
  
## Vea también  
 [Crear una publicación](../../relational-databases/replication/publish/create-a-publication.md)   
 [Ver y modificar propiedades de publicación](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Ver y modificar las propiedades de una suscripción de extracción](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [Ver y modificar las propiedades de una suscripción de inserción](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [Crear y aplicar la instantánea inicial](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [Publicar datos y objetos de base de datos](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  