---
title: "Detecci&#243;n y resoluci&#243;n de conflictos de replicaci&#243;n de mezcla avanzada | Microsoft Docs"
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
  - "resolución de conflictos de replicación de mezcla [replicación de SQL Server], acerca de la resolución de conflictos"
  - "solucionador de conflictos predeterminado"
  - "seguimiento de conflictos a nivel de columna"
  - "seguimiento de conflictos a nivel de fila"
  - "ver conflictos de replicación de mezcla"
  - "solucionar conflictos de replicación de mezcla"
  - "seguimiento de conflictos a nivel de registro lógico [replicación de SQL Server]"
  - "resolución de conflictos [replicación de SQL Server], replicación de mezcla"
ms.assetid: 063d3d9c-ccb5-4fab-9d0c-c675997428b4
caps.latest.revision: 46
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 46
---
# Detecci&#243;n y resoluci&#243;n de conflictos de replicaci&#243;n de mezcla avanzada
  Cuando un publicador y un suscriptor se conectan y se produce la sincronización, el Agente de mezcla detecta si existen conflictos. Si se detectan conflictos, el Agente de mezcla utiliza un solucionador de conflictos (que se especifica cuando se agrega un artículo a una publicación) para determinar qué datos se aceptarán y se propagarán a otros sitios.  
  
> [!NOTE]  
>  Aunque un suscriptor se sincronice con el publicador, suelen producirse conflictos entre las actualizaciones que se realizan en suscriptores diferentes, en vez de entre las actualizaciones que se realizan en un suscriptor y en el publicador.  
  
 El comportamiento de la detección y resolución de conflictos depende de las siguientes opciones, que se describen en este tema:  
  
-   Si especifica seguimiento por columna, seguimiento por filas o seguimiento por registro lógico.  
  
-   Si especifica el mecanismo de resolución basado en la prioridad predeterminada o especifica un solucionador de artículos. Un solucionador de artículos puede ser:  
  
    -   Un *controlador de lógica de negocios* escrito en código administrado  
  
    -   Basado en COM *resolución personalizada*.  
  
    -   Un solucionador basado en COM proporcionado por [!INCLUDE[msCoName](../../../includes/msconame-md.md)]  
  
     Si se utiliza el mecanismo de resolución predeterminado, el tipo de suscripción utilizada (cliente o servidor) determina el comportamiento.  
  
## Detección de conflictos  
 Si un cambio de datos se califica como un conflicto o no depende del tipo de seguimiento de conflictos que ha especificado para un artículo:  
  
-   Si selecciona seguimiento de conflictos por columna, se considera un conflicto si los cambios se realizan en la misma columna de la misma fila en más de un nodo de replicación.  
  
-   Si selecciona seguimiento de conflictos por filas, se considera un conflicto si los cambios se realizan en cualquier columna de la misma fila en más de un nodo de replicación (las columnas afectadas en las filas correspondientes no tienen que ser las mismas).  
  
-   Si selecciona seguimiento de conflictos por registro lógico, se considera un conflicto si los cambios se realizan en cualquier fila del mismo registro lógico en más de un nodo de replicación (las columnas afectadas en las filas correspondientes no tienen que ser las mismas).  
  
 Para más información, consulte [Detecting and Resolving Conflicts in Logical Records](../../../relational-databases/replication/merge/detecting-and-resolving-conflicts-in-logical-records.md).  
  
 Para especificar el seguimiento de conflictos y el nivel de resolución para un artículo, vea [Specify the Conflict Tracking and Resolution Level for Merge Articles](../../../relational-databases/replication/publish/specify-the-conflict-tracking-and-resolution-level-for-merge-articles.md).  
  
## Resolución de conflictos  
 Una vez detectado un conflicto, el Agente de mezcla inicia el solucionador de conflictos seleccionado y lo utiliza para determinar el ganador. La fila ganadora se aplica en el publicador y en el suscriptor, y los datos de la fila perdedora se escriben en una tabla de conflictos. Los conflictos se resuelven inmediatamente después de ejecutarse el solucionador, a menos que seleccione solucionar los conflictos de forma interactiva.  
  
### Tipos de solucionador  
 En la replicación de mezcla, la resolución de conflictos tiene lugar en el nivel de artículo. En el caso de publicaciones compuestas de varios artículos, es posible tener varios solucionadores de conflictos que proporcionen servicio a diferentes artículos o un mismo solucionador de conflictos que proporcione servicio a un artículo, a varios artículos o a todos los artículos que componen la publicación.  
  
 Si va a utilizar el solucionador de conflictos basado en prioridad predeterminado, no tendrá que establecer la propiedad de solucionador de los artículos. Si desea utilizar un solucionador de artículos en lugar del solucionador predeterminado, deberá establecer la propiedad de solucionador del artículo que lo utilizará seleccionando un solucionador personalizado disponible en el publicador. Cualquier información específica que se deba pasar al solucionador puede especificarse también en la propiedad de información de solucionador.  
  
 La replicación de mezcla ofrece cuatro tipos de solucionadores de conflictos:  
  
-   El solucionador de conflictos predeterminado basado en prioridad  
  
     El mecanismo de resolución predeterminada se comporta de forma diferente, dependiendo de si se trata de una suscripción de cliente o una suscripción de servidor. Asigne valores de prioridad a suscriptores individuales que utilizan suscripciones de servidor; los cambios realizados en el nodo con la máxima prioridad ganan en cualquier conflicto. En suscripciones de cliente, el primer cambio escrito en el publicador gana el conflicto.  
  
     Después de crear una suscripción, no se puede cambiar de un tipo a otro.  
  
-   Un controlador de lógica de negocios  
  
     El marco de trabajo de controladores de lógica de negocios permite escribir un ensamblado de código administrado al que se llama durante el proceso de sincronización de mezcla. El ensamblado incluye la lógica de negocios que puede responder a conflictos y a otras condiciones durante la sincronización. Para obtener más información, consulte [ejecutar lógica de negocios durante la sincronización mezcla](../../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md).  
  
-   Un solucionador personalizado basado en COM  
  
     La replicación de mezcla propociona una API para escribir solucionadoes como objetos COM en lenguajes como [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] o [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]. Para obtener más información, consulte [basada en COM personalizada resoluciones](../../../relational-databases/replication/merge/com-based-custom-resolvers.md).  
  
-   Un solucionador basado en COM proporcionado por [!INCLUDE[msCoName](../../../includes/msconame-md.md)]  
  
     [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] incluye varios solucionadores basados en COM. Para obtener más información, consulte [solucionadores basados en COM de Microsoft](../../../relational-databases/replication/merge/microsoft-com-based-resolvers.md).  
  
 Para obtener información sobre cómo seleccionar el tipo adecuado de resolución, consulte [Elegir una resolución](../../../relational-databases/replication/merge/choose-a-resolver.md).  
  
> [!NOTE]  
>  Algunos solucionadores de artículos están escritos para controlar conflictos solo en determinadas operaciones. Por ejemplo, una resolución puede controlar actualizaciones, pero no inserciones o eliminaciones. El solucionador de conflictos predeterminado basado en prioridad controla los conflictos que no controla el solucionador de artículos.  
  
 Para especificar un tipo de suscripción de mezcla y la prioridad de resolución de conflictos, vea  
  
-   [! INCLUIR [ssManStudioFull] (.. / Token/ssManStudioFull_md.md)]: [Specify a Merge Subscription Type and Conflict Resolution Priority &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/specify a merge subscription type and conflict resolution priority.md)  
  
-   Replicación [!INCLUDE[tsql](../../../includes/tsql-md.md)] programación y la programación de Replication Management Objects (RMO): [crear una suscripción de extracción](../../../relational-databases/replication/create-a-pull-subscription.md) y [crear una suscripción de inserción](../../../relational-databases/replication/create-a-push-subscription.md)  
  
### Solucionador interactivo  
 La replicación proporciona una interfaz de usuario Solucionador interactivo que se puede utilizar junto con el solucionador de conflictos basado en prioridad predeterminado o un solucionador de artículos. Cuando se ejecuta una sincronización a petición a través del Administrador de sincronización de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows, el Solucionador interactivo muestra los datos en conflicto en tiempo de ejecución y permite elegir la forma de solucionar los conflictos. Para obtener más información acerca de cómo habilitar la resolución interactiva e iniciar el Solucionador interactivo, vea [Interactive Conflict Resolution](../../../relational-databases/replication/merge/interactive-conflict-resolution.md).  
  
## Ver conflictos  
 La forma más directa de ver conflictos es utilizar el Visor de conflictos de replicación, disponible en [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] también proporciona procedimientos almacenados que permiten consultar tablas de conflictos). El Visor de conflictos y el Solucionador interactivo son herramientas parecidas, pero el Solucionador interactivo permite solucionar los conflictos cuando se realiza la sincronización, mientras que el Visor de conflictos está diseñado para ver los conflictos después de haberlos resuelto. Si los metadatos en conflicto aún están disponibles en las tablas del sistema (los metadatos en conflicto se conservan, de forma predeterminada, durante 14 días), puede reemplazar el resultado de la resolución de conflictos en el Visor de conflictos, pero si se requiere con frecuencia una intervención directa, debe considerar la posibilidad de utilizar el Solucionador interactivo.  
  
> [!NOTE]  
>  Los conflictos que implican registros lógicos no se muestran en el Visor de conflictos. Para ver información acerca de estos conflictos, utilice procedimientos almacenados de replicación. Para obtener más información, consulte [Ver la información de conflictos para publicaciones de mezcla & #40; Programación de Transact-SQL de replicación & #41;](../../../relational-databases/replication/view conflict information for merge publications.md).  
  
 El Visor de conflictos muestra información de tres tablas del sistema:  
  
-   La replicación crea una tabla de conflictos para cada tabla en un artículo de mezcla con un nombre en el formulario **MSmerge_conflict_ \< Nombredepublicación>_ \< Nombredeartículo>**.  
  
     Las tablas de conflictos tienen la misma estructura que las tablas en las que se basan. Una fila de una de estas tablas consta de la versión perdedora de una fila de conflictos (la versión ganadora de esta fila se encuentra en la tabla real del usuario).  
  
-   El **MSmerge_conflicts_info** tabla proporciona información sobre cada conflicto, incluido el tipo de conflicto.  
  
-   En la tabla **sysmergearticles** se identifican las tablas del usuario que tienen tablas de conflictos y se proporciona información sobre ellas.  
  
 De manera predeterminada, la información del conflicto se almacena:  
  
-   En el publicador y en el suscriptor, si el nivel de compatibilidad de la publicación es igual o superior a 90RTM.  
  
-   En el publicador, si el nivel de compatibilidad de la publicación es inferior a 80RTM.  
  
-   En el publicador, si los suscriptores utilizan [!INCLUDE[ssEW](../../../includes/ssew-md.md)]. No se pueden almacenar datos en conflicto en los suscriptores de [!INCLUDE[ssEW](../../../includes/ssew-md.md)] .  
  
 **Para ver conflictos**  
  
-   [! INCLUIR [ssManStudioFull] (.. / Token/ssManStudioFull_md.md)]: [View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/view and resolve data conflicts for merge publications.md)  
  
-   Replicación [!INCLUDE[tsql](../../../includes/tsql-md.md)] Programming: [Ver la información de conflictos para publicaciones de mezcla & #40; Programación de replicación Transact-SQL & #41;](../../../relational-databases/replication/view conflict information for merge publications.md)  
  
## Vea también  
 [Sincronizar datos](../../../relational-databases/replication/synchronize-data.md)  
  
  