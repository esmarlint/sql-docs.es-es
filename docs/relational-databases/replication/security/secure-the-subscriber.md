---
title: "Proteger el suscriptor | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "suscripciones [replicación de SQL Server], seguridad"
  - "Suscriptores [replicación de SQL Server], seguridad"
  - "seguridad [replicación de SQL Server], Suscriptores"
ms.assetid: c8f0d62a-8b5d-4a21-9aec-223da52bb708
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# Proteger el suscriptor
  Los agentes de mezcla y de distribución se conectan al suscriptor. Estas conexiones pueden realizarse en el contexto de un inicio de sesión de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] o de Windows. Es importante proporcionar un inicio de sesión apropiado para estos agentes, al mismo tiempo que se sigue el principio de conceder los derechos mínimos necesarios y proteger el almacenamiento de todas las contraseñas. Para obtener información acerca de los permisos necesarios para cada agente, vea [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## Agente de distribución  
 Hay un Agente de distribución por suscripción (un agente independiente, predeterminado para las publicaciones creadas en el Asistente para nueva publicación), o un Agente de distribución por par de base de datos de publicaciones y base de datos de suscripciones (un agente compartido). T  
  
 Para especificar información de conexión para suscripciones de inserción, vea [crear una suscripción de inserción](../../../relational-databases/replication/create-a-push-subscription.md).  
  
 Para especificar información de conexión para suscripciones de extracción, consulte [crear una suscripción de extracción](../../../relational-databases/replication/create-a-pull-subscription.md)  
  
## Agente de mezcla  
 Cada suscripción de mezcla tiene su propio Agente de mezcla que conecta y actualiza el publicador y el suscriptor.  
  
 Para especificar información de conexión para suscripciones de inserción, vea [crear una suscripción de inserción](../../../relational-databases/replication/create-a-push-subscription.md).  
  
 Para especificar información de conexión para suscripciones de extracción, consulte [crear una suscripción de extracción](../../../relational-databases/replication/create-a-pull-subscription.md).  
  
## Suscripciones de actualización inmediata  
 Al configurar una suscripción de actualización inmediata, se especifica una cuenta en el suscriptor con la que se realizan las conexiones al publicador. Las conexiones las utilizan los desencadenadores que se activan en el suscriptor y propagan los cambios al publicador. Hay tres opciones disponibles para el tipo de conexión:  
  
-   Un servidor vinculado que crea la replicación; la conexión se establece con las credenciales especificadas durante la configuración.  
  
-   Un servidor vinculado que crea la replicación; la conexión se establece con las credenciales del usuario que realiza el cambio en el suscriptor.  
  
-   Un servidor vinculado o un servidor remoto previamente definido.  
  
> [!IMPORTANT]  
>  Para especificar información de conexión, utilice el procedimiento almacenado [sp_link_publication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md). También puede utilizar el **Inicio de sesión para suscripciones actualizables** página del Asistente de suscripción nueva, que llama a **sp_link_publication**. En ciertas condiciones, este procedimiento almacenado puede producir un error si el suscriptor ejecuta el Service Pack 1 (SP1) de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o posterior y el publicador ejecuta una versión anterior. Si el procedimiento almacenado produce un error en estas circunstancias, actualice el publicador a [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] SP1 o posterior.  
  
 Para obtener más información, consulte [crear una suscripción actualizable a una publicación transaccional](../../../relational-databases/replication/publish/create-an-updatable-subscription-to-a-transactional-publication.md) y [Ver y modificar la configuración de seguridad de replicación](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
> [!IMPORTANT]  
>  La cuenta especificada para la conexión solo debe tener permiso para insertar, actualizar y eliminar datos en las vistas que crea la replicación en la base de datos de publicaciones; no debe tener ningún permiso adicional. Conceder permisos en las vistas en la base de datos de publicación que se denominan con el formato **syncobj_***\< númerohexadecimal>* a la cuenta configurada en cada suscriptor.  
  
## Suscriptores de actualización en cola  
 Al configurar suscripciones de actualización en cola, hay dos áreas relacionadas con la seguridad que debe tener en cuenta:  
  
-   Solo hay un Agente de lectura de cola para cada distribuidor. Para cada distribuidor, se recomienda configurar como máximo una publicación habilitada para las suscripciones de actualización en cola.  
  
-   El Agente de lectura de cola establece las conexiones con el distribuidor, el publicador y cada suscriptor:  
  
    -   La cuenta con la que se ejecuta el agente y establece conexiones con el distribuidor se especifica al crear el agente (si utiliza el Asistente para nueva publicación, el agente se crea al crear una publicación habilitada para suscripciones de actualización).  
  
    -   La cuenta con la que el agente establece conexiones con el publicador se especifica al configurar la distribución para un publicador. Especifique la cuenta de Windows con la que se ejecuta el agente o una cuenta de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
    -   La cuenta con la que el agente establece conexiones con el suscriptor se especifica al crear la suscripción.  
  
    > [!IMPORTANT]  
    >  Utilice la autenticación de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] para las conexiones con los suscriptores y especifique una cuenta distinta para la conexión con cada suscriptor. Si utiliza una suscripción de extracción, la replicación establece siempre la conexión para que utilice la autenticación de Windows (en las suscripciones de extracción, la replicación no tiene acceso a los metadatos de un suscriptor que deba usar la autenticación de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]). En este caso, cambie la conexión para que use la autenticación de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] después de configurar la suscripción.  
  
     Para obtener más información, vea Cómo: crear una suscripción de actualización en una publicación transaccional (SQL Server Management Studio) y [Ver y modificar la configuración de seguridad de replicación](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
## Vea también  
 [Habilitar conexiones cifradas en el motor de base de datos & #40; Administrador de configuración de SQL Server & #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md)   
 [Prácticas recomendadas de seguridad de replicación](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Seguridad y protección & #40; Replicación y nº 41;](../../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  