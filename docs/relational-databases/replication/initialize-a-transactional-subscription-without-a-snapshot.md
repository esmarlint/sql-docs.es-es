---
title: "Inicializar una suscripci&#243;n transaccional sin una instant&#225;nea | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "replicación transaccional, inicializar"
  - "replicación [SQL Server], inicializar"
  - "inicializar suscripciones [replicación de SQL Server], sin instantáneas"
ms.assetid: 75c8c1f8-60bc-44a8-944b-d18d1f6bda11
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Inicializar una suscripci&#243;n transaccional sin una instant&#225;nea
  De forma predeterminada, una suscripción a una publicación transaccional se inicializa con una instantánea generada por el Agente de instantáneas y aplicada por el Agente de distribución. En algunos escenarios, como aquellos en los que intervienen grandes conjuntos de datos iniciales, es preferible inicializar una suscripción mediante otro método. Otros métodos para inicializar un suscriptor incluyen:  
  
-   Especificar una copia de seguridad. Se restaura la copia de seguridad en el suscriptor y, a continuación, el Agente de distribución copia los metadatos de replicación y los procedimientos del sistema necesarios. La inicialización con una copia de seguridad es la forma más rápida de entregar datos al suscriptor, además de resultar cómoda, ya que se puede utilizar cualquier copia de seguridad reciente si se ha realizado después de que se habilitara la publicación para inicialización mediante una copia de seguridad.  
  
-   Copiar un conjunto de datos inicial en el suscriptor mediante otro mecanismo, como adjuntar una base de datos. Debe asegurarse de que los datos y el esquema correctos se encuentran en el suscriptor. A continuación, el Agente de distribución copia los metadatos y los procedimientos del sistema necesarios.  
  
## Inicializar una suscripción con una copia de seguridad  
 Una copia de seguridad contiene una base de datos completa; por esa razón, cada base de datos de suscripciones contendrá una copia completa de la base de datos de publicación cuando se inicialice.  
  
-   La copia de seguridad incluye tablas no especificadas como artículos de la publicación.  
  
-   La copia de seguridad incluye todos los datos, incluso si se han especificado filtros de fila o columna en una tabla.  
  
 Es responsabilidad del administrador o la aplicación quitar los objetos o los datos no deseados una vez restaurada la copia de seguridad. En las sincronizaciones posteriores, las modificaciones de los datos solo se replican si se aplican a las tablas especificadas como artículos y si estas modificaciones cumplen los criterios de filtrado especificados.  
  
> [!NOTE]  
>  Al restaurar una copia de seguridad, si desea que el suscriptor se sincronice automáticamente, debe asegurarse de que dicha copia proviene del publicador. Los valores de número de secuencia de registro (LSN) de la copia de seguridad (que se utilizan para establecer el punto en el que se inicia la sincronización) son específicos del publicador.   
  
 **Para inicializar una suscripción con una copia de seguridad**  
  
 Para inicializar una suscripción con una copia de seguridad, primero debe habilitar la opción al crear una publicación y, a continuación, al crear una suscripción, especificar valores para una serie de opciones. Las publicaciones se pueden habilitar mediante el Asistente para nueva publicación o mediante programación. Sin embargo, los valores necesarios para las opciones de suscripción solo se pueden especificar mediante programación.  
  
-   [! INCLUIR [ssManStudioFull] (.. / Token/ssManStudioFull_md.md)]: [Enable Initialization with a Backup for Transactional Publications &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/enable initialization with backup for transactional publications.md)  
  
-   Programación de Transact-SQL de la replicación: [inicializar una suscripción transaccional desde una copia de seguridad y Nº 40; Programación de replicación Transact-SQL & #41;](../../relational-databases/replication/initialize a transactional subscription from a backup.md)  
  
> [!NOTE]  
>  Si una suscripción se inicializa sin una instantánea, la cuenta con la que se ejecuta el servicio SQL Server en el publicador debe contar con permisos de escritura en la carpeta de instantáneas en el distribuidor. Para obtener más información sobre los permisos, vea [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
### Asegurar la idoneidad de una copia de seguridad  
 Una copia de seguridad es adecuada para inicializar un suscriptor si todas las transacciones que se producen después de realizar la copia de seguridad se almacenan en el distribuidor. Si la copia de seguridad no es adecuada, la replicación mostrará un mensaje de error.  
  
 Para ayudar a asegurar que una copia de seguridad es adecuada, siga estas directrices:  
  
-   Utilice la última copia de seguridad disponible. Si ésta fuera más antigua que el período máximo de retención de distribución, cree una nueva antes de intentar inicializar una suscripción con una copia de seguridad. Para obtener más información acerca del período de retención, vea [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
-   De forma predeterminada, el trabajo de limpieza de distribución borra de la base de datos de distribución aquellas transacciones que superan las 72 horas. La limpieza se basa en el período de retención establecido para la publicación. Si realiza la sincronización con copias de seguridad más antiguas, considere la posibilidad de deshabilitar el trabajo de forma temporal antes de restaurar la copia de seguridad y volver a habilitarlo después de que la suscripción se haya creado correctamente. Esto evita la eliminación de transacciones de la base de datos de distribución que pudieran ser necesarias para sincronizar correctamente desde la copia de seguridad. Para obtener información acerca de cómo ejecutar trabajos de limpieza, vea [Ejecutar trabajos de mantenimiento de replicación & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/administration/run-replication-maintenance-jobs-sql-server-management-studio.md).  
  
 En algunos casos, deberá realizar personalizaciones de forma manual en la base de datos del suscriptor restaurada después de configurar las suscripciones inicializadas con una copia de seguridad. En general, las modificaciones manuales en la base de datos del suscriptor restaurada son necesarias si la publicación está definida de tal modo que se espera que el contenido de la base de datos del suscriptor sea diferente al de la base de datos del publicador.  
  
-   Las vistas indizadas de la base de datos restaurada deben convertirse en tablas si se publican como artículos de vista indizada a tabla basados en registros.  
  
-   Columnas de marca de tiempo suscritas en la base de datos restaurada deben convertirse a **Binary (8)** columnas: copie el contenido de las tablas que contienen columnas de marca de tiempo a las tablas nuevas con la coincidencia de esquemas excepto tener **Binary (8)** columnas en lugar de las columnas de marca de tiempo, colocar las tablas originales y cambiar el nombre de las tablas nuevas con los mismos nombres que las tablas originales.  
  
## Inicializar una suscripción con un método alternativo  
 Es posible inicializar una suscripción mediante cualquier método que permita copiar el esquema y los datos de la base de datos de publicación en el suscriptor, como [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Cuando se utiliza un método alternativo para inicializar el suscriptor, los objetos de soporte de replicación se copian en el suscriptor.  
  
 A diferencia de lo que ocurre al inicializar con una copia de seguridad, el usuario o la aplicación debe asegurarse de que los datos y el esquema se han sincronizado correctamente en el momento de agregar la suscripción. Por ejemplo, si se produce actividad en el publicador entre el momento en que se copian los datos y el esquema en el suscriptor y el momento en que se agrega la suscripción, es posible que los cambios que resulten de dicha actividad no se repliquen en el suscriptor.  
  
 Para inicializar una suscripción con un método alternativo, vea [Initialize a Subscription Manually](../../relational-databases/replication/initialize-a-subscription-manually.md).  
  
## Vea también  
 [Inicializar una suscripción](../../relational-databases/replication/initialize-a-subscription.md)  
  
  