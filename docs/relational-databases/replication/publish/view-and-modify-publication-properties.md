---
title: "Ver y modificar propiedades de publicaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ver propiedades de replicación"
  - "modificar las propiedades de replicación, artículos"
  - "artículos [replicación de SQL Server], modificar"
  - "publicaciones [replicación de SQL Server], propiedades"
  - "artículos [replicación de SQL Server], propiedades"
  - "modificar propiedades de replicación, publicaciones"
  - "publicaciones [replicación de SQL Server], modificar"
ms.assetid: 27d72ea4-bcb6-48f2-b4aa-eb1410da7efc
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Ver y modificar propiedades de publicaci&#243;n
  En este tema se describe cómo ver y modificar las propiedades de publicación en [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] o Replication Management Objects (RMO).  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Limitaciones y restricciones](#Restrictions)  
  
     [Recomendaciones](#Recommendations)  
  
-   **Para ver y modificar las propiedades de publicación con:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Replication Management Objects (RMO)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="Restrictions"></a> Limitaciones y restricciones  
  
-   Algunas propiedades no se pueden modificar después de crearlas, y otras no se pueden modificar si existen suscripciones a la publicación. Las propiedades que no se pueden modificar se muestran como de solo lectura.  
  
###  <a name="Recommendations"></a> Recomendaciones  
  
-   Una vez creada una publicación, algunos cambios de las propiedades requieren una nueva instantánea. Si una publicación tiene suscripciones, algunos cambios también requieren reinicializar todas las suscripciones. Para obtener más información, consulte [Propiedades de artículo y publicación de cambio](../../../relational-databases/replication/publish/change-publication-and-article-properties.md) y [Agregar y quitar artículos de publicaciones existentes](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
##  <a name="SSMSProcedure"></a> Usar SQL Server Management Studio  
 Ver y modificar las propiedades de la publicación en la **Propiedades de la publicación - \< publicación>** cuadro de diálogo, que está disponible en [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] y Monitor de replicación. Para obtener información acerca de cómo iniciar el Monitor de replicación, consulte [iniciar el Monitor de replicación](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
 El **Propiedades de la publicación - \< publicación>** cuadro de diálogo incluye las siguientes páginas:  
  
-   La página **General** incluye el nombre y la descripción de la publicación, el nombre de la base de datos, el tipo de publicación y los valores de expiración de la suscripción.  
  
-   La página **Artículos** corresponde a la página **Artículos** del Asistente para nueva publicación. Utilice esta página para agregar y eliminar artículos, y para cambiar propiedades y el filtro de columna de artículos.  
  
-   La página **Filtrar filas** corresponde a la página **Filtrar filas de tabla** del Asistente para nueva publicación. Utilice esta página para agregar, editar y eliminar filtros de fila estáticos de todos los tipos de publicaciones, y para agregar, editar y eliminar filtros de fila con parámetros y filtros de combinación de publicaciones de combinación.  
  
-   La página **Instantánea** permite especificar el formato y la ubicación de la instantánea, si la instantánea debe comprimirse y si los scripts deben ejecutarse antes y después de aplicar la instantánea.  
  
-   El **instantánea de FTP** página (de instantáneas y publicaciones transaccionales y publicaciones de mezcla para publicadores que ejecutan versiones anteriores a SQL Server 2005) le permite especificar si los suscriptores pueden descargar los archivos de instantáneas a través del protocolo de transferencia de archivos (FTP).  
  
-   El **instantánea de FTP e Internet** página (para publicaciones de mezcla de publicadores que ejecutan SQL Server 2005 o posterior) le permite especificar si los suscriptores pueden descargar los archivos de instantáneas mediante FTP, y si los suscriptores pueden sincronizar suscripciones a través de HTTPS.  
  
-   La página **Opciones de suscripción** permite establecer diversas opciones que se aplican a todas las suscripciones. Las opciones varían según el tipo de publicación.  
  
-   La página **Lista de acceso a la publicación** permite especificar qué inicios de sesión y grupos pueden tener acceso a una publicación.  
  
-   La página **Seguridad del agente** le permite tener acceso a la configuración para las cuentas con las que se ejecutan los agentes siguientes y realizan conexiones a los equipos en una topología de replicación: el Agente de instantáneas para todas las publicaciones, el Agente de registro del LOG para todas las publicaciones transaccionales y el Agente de lectura de cola para las publicaciones transaccionales que permiten las suscripciones de actualización en cola.  
  
-   El **particiones de datos** página (para publicaciones de mezcla de publicadores que ejecutan SQL Server 2005 o posterior) le permite especificar si los suscriptores de publicaciones con filtros parametrizados pueden solicitar una instantánea si no está disponible. También permite generar instantáneas de una o varias particiones, solo una vez o varias veces.  
  
#### Para ver y modificar propiedades de una publicación en Management Studio  
  
1.  Conéctese al publicador en [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]y, a continuación, expanda el nodo del servidor.  
  
2.  Expanda la carpeta **Replicación** y, a continuación, expanda la carpeta **Publicaciones locales** .  
  
3.  Haga clic en una publicación y, a continuación, haga clic en **propiedades**.  
  
4.  Modifique las propiedades si es necesario y, a continuación, haga clic en **Aceptar**.  
  
#### Para ver y modificar propiedades de una publicación en el Monitor de replicación  
  
1.  Expanda un grupo de publicador en el panel izquierdo del Monitor de replicación y, a continuación, expanda un publicador.  
  
2.  Haga clic en una publicación y, a continuación, haga clic en **propiedades**.  
  
3.  Modifique las propiedades si es necesario y, a continuación, haga clic en **Aceptar**.  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
 Se puede modificar las publicaciones y devolver sus propiedades mediante programación utilizando procedimientos almacenados de replicación. Los procedimientos almacenados que utilice dependerán del tipo de publicación.  
  
#### Para ver las propiedades de una instantánea o publicación transaccional  
  
1.  Ejecutar [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md), especificando el nombre de la publicación para el **@publication** parámetro. Si no especifica este parámetro, se devuelve información sobre todas las publicaciones del publicador.  
  
#### Para cambiar las propiedades de una instantánea o publicación transaccional  
  
1.  Ejecutar [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), especificando la propiedad de publicación para cambiar la **@property** parámetro y el nuevo valor de esta propiedad en el **@value** parámetro.  
  
    > [!NOTE]  
    >  Si el cambio requiere la generación de una nueva instantánea, también debe especificar un valor de **1** para **@force_invalidate_snapshot**, y si el cambio requiere que se reinicialicen suscriptores, debe especificar un valor de **1** para **@force_reinit_subscription**. Para obtener más información acerca de las propiedades que, si se cambian, requieren una nueva instantánea o reinicialización, vea [Propiedades de artículo y publicación de cambio](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
#### Para ver las propiedades de una publicación de combinación  
  
1.  Ejecutar [sp_helpmergepublication](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), especificando el nombre de la publicación para el **@publication** parámetro. Si no especifica este parámetro, se devuelve información sobre todas las publicaciones del publicador.  
  
#### Para cambiar las propiedades de una publicación de combinación  
  
1.  Ejecutar [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), especificando la propiedad de publicación que se va a cambiar en el **@property** parámetro y el nuevo valor de esta propiedad en el **@value** parámetro.  
  
    > [!NOTE]  
    >  Si el cambio requiere la generación de una nueva instantánea, también debe especificar un valor de **1** para **@force_invalidate_snapshot**, y si el cambio requiere que se reinicialicen suscriptores, debe especificar un valor de **1** para **@force_reinit_subscription** para obtener más información acerca de las propiedades que, si se cambian, requieren una nueva instantánea o reinicialización, vea [cambiar la publicación y las propiedades del artículo](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
#### Para ver las propiedades de una instantánea  
  
1.  Ejecutar [sp_helppublication_snapshot](../../../relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql.md), especificando el nombre de la publicación para el **@publication** parámetro.  
  
#### Para cambiar las propiedades de una instantánea  
  
1.  Ejecutar [sp_changepublication_snapshot](../../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md), especificar una o varias de las nuevas propiedades de instantánea de los parámetros de instantánea adecuados.  
  
###  <a name="TsqlExample"></a> Ejemplos (Transact-SQL)  
 Este ejemplo de replicación transaccional devuelve las propiedades de la publicación.  
  
 [!code-sql[HowTo#sp_helppublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_1.sql)]  
  
 Este ejemplo de replicación transaccional deshabilita la replicación de esquema para la publicación.  
  
 [!code-sql[HowTo#sp_changepublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_2.sql)]  
  
 Este ejemplo de replicación de mezcla devuelve las propiedades de la publicación.  
  
 [!code-sql[HowTo#sp_helpmergepublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_3.sql)]  
  
 Este ejemplo de replicación de mezcla deshabilita la replicación de esquema para la publicación.  
  
 [!code-sql[HowTo#sp_changemergepublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_4.sql)]  
  
##  <a name="RMOProcedure"></a> Usar Replication Management Objects (RMO)  
 Puede modificar publicaciones y obtener acceso mediante programación a sus propiedades utilizando Replication Management Objects (RMO). Las clases RMO que usa para ver o modificar las propiedades de publicación dependen del tipo de publicación.  
  
#### Para ver o modificar las propiedades de una publicación transaccional o de instantáneas  
  
1.  Crear una conexión al publicador mediante la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> clase.  
  
2.  Cree una instancia de la <xref:Microsoft.SqlServer.Replication.TransPublication> clase, establezca el <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> y <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Propiedades de la publicación y establezca el <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propiedad en la conexión creada en el paso 1.  
  
3.  Llame a la <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> método para obtener las propiedades del objeto. Si este método devuelve **false**, significa que las propiedades de publicación del paso 2 se definieron incorrectamente, o bien que la publicación no existe.  
  
4.  (Opcional) Para cambiar las propiedades, establezca un nuevo valor para una o más de las propiedades que se pueden establecer. Utilice el operador AND lógico (**&** en Microsoft Visual C# y **y** en Microsoft Visual Basic) para determinar si un determinado <xref:Microsoft.SqlServer.Replication.PublicationAttributes> el valor para el <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> propiedad. Utilice el operador lógico OR inclusivo (**|** en Visual C# y **o** en Visual Basic) y el operador lógico OR exclusivo (**^** en Visual C# y **Xor** en Visual Basic) para cambiar la <xref:Microsoft.SqlServer.Replication.PublicationAttributes> los valores para el <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> propiedad.  
  
5.  (Opcional) Si especifica un valor de **true** para <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, llame a la <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> método para confirmar los cambios en el servidor. Si especifica un valor de **false** para <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (valor predeterminado), cambios se envían al servidor inmediatamente.  
  
#### Para ver o modificar las propiedades de una publicación de combinación  
  
1.  Crear una conexión al publicador mediante la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> clase.  
  
2.  Cree una instancia de la <xref:Microsoft.SqlServer.Replication.MergePublication> clase, establezca el <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> y <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Propiedades de la publicación y establezca el <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propiedad en la conexión creada en el paso 1.  
  
3.  Llame a la <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> método para obtener las propiedades del objeto. Si este método devuelve **false**, significa que las propiedades de publicación del paso 2 se definieron incorrectamente, o bien que la publicación no existe.  
  
4.  (Opcional) Para cambiar las propiedades, establezca un nuevo valor para una o más de las propiedades que se pueden establecer. Utilice el operador AND lógico (**&** en Visual C# y **y** en Visual Basic) para determinar si un determinado <xref:Microsoft.SqlServer.Replication.PublicationAttributes> el valor para el <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> propiedad. Utilice el operador lógico OR inclusivo (**|** en Visual C# y **o** en Visual Basic) y el operador lógico OR exclusivo (**^** en Visual C# y **Xor** en Visual Basic) para cambiar la <xref:Microsoft.SqlServer.Replication.PublicationAttributes> los valores para el <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> propiedad.  
  
5.  (Opcional) Si especifica un valor de **true** para <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, llame a la <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> método para confirmar los cambios en el servidor. Si especifica un valor de **false** para <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (valor predeterminado), cambios se envían al servidor inmediatamente.  
  
###  <a name="PShellExample"></a> Ejemplos (RMO)  
 Este ejemplo establece los atributos de publicación para una publicación transaccional. Los cambios están almacenados en memoria caché hasta que se envían explícitamente al servidor.  
  
 [!code-csharp[HowTo#rmo_ChangeTranPub_cached](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changetranpub_cached)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeTranPub_cached](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changetranpub_cached)]  
  
 Este ejemplo deshabilita la replicación de DDL para una publicación de combinación.  
  
 [!code-csharp[HowTo#rmo_ChangeMergePub_ddl](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changemergepub_ddl)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergePub_ddl](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changemergepub_ddl)]  
  
## Vea también  
 [Publicar datos y objetos de base de datos](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Cambiar las propiedades de la publicación y de los artículos](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Realizar cambios de esquema en bases de datos de publicaciones](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)   
 [Conceptos sobre los procedimientos almacenados del sistema de replicación](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Agregar y quitar artículos de una publicación & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-a-publication.md)   
 [Ver la información y realizar tareas para una publicación & #40; Monitor de replicación & #41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)   
 [Ver y modificar las propiedades de un artículo](../../../relational-databases/replication/publish/view-and-modify-article-properties.md)  
  
  