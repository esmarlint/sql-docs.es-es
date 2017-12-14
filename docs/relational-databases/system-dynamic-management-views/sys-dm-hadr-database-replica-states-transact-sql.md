---
title: Sys.dm_hadr_database_replica_states (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 11/08/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_database_states_TSQL
- sys.dm_hadr_database_states
- dm_hadr_database_states
- dm_hadr_database_states_TSQL
dev_langs: TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_hadr_database_replica_states dynamic management view
ms.assetid: 1a17b0c9-2535-4f3d-8013-cd0a6d08f773
caps.latest.revision: "84"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 4b57d7550f007eb4a85f7db698aae84f133726c9
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmhadrdatabasereplicastates-transact-sql"></a>sys.dm_hadr_database_replica_states (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Devuelve una fila para cada base de datos que participa en un grupo de disponibilidad AlwaysOn para el que la instancia local de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hospeda una réplica de disponibilidad. Esta vista de administración dinámica expone información de estado en las réplicas principal y secundaria. En una réplica secundaria, esta vista devuelve una fila por cada base de datos secundaria de la instancia de servidor. En la réplica principal, esta vista devuelve una fila por cada base de datos principal y una fila adicional para la base de datos secundaria correspondiente.  
  
> [!IMPORTANT]
> Dependiendo de la acción y los estados de nivel superior, la información del estado de la base de datos puede no estar disponible u obsoleta. Además, los valores solo tienen relevancia local. Por ejemplo, en la réplica principal, el valor de la **last_hardened_lsn** columna refleja la información sobre una base de datos secundaria que esté disponible para la réplica principal, no el LSN reforzado real de los valores que el réplica secundaria puede tener actualmente.  
   
|Nombre de columna|Tipo de datos|Descripción (en la réplica principal)|  
|-----------------|---------------|----------------------------------------|  
|**database_id**|**int**|Identificador de la base de datos, único en una instancia de SQL Server. Este es el mismo valor, como se muestra en el [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) vista de catálogo.|  
|**group_id**|**uniqueidentifier**|Identificador del grupo de disponibilidad al que pertenece la base de datos.|  
|**replica_id**|**uniqueidentifier**|Identificador de la réplica de disponibilidad dentro del grupo de disponibilidad.|  
|**group_database_id**|**uniqueidentifier**|Identificador de la base de datos dentro del grupo de disponibilidad. Este identificador es idéntico en cada réplica al que está unido esta base de datos.|  
|**is_local**|**bit**|Si la base de datos de disponibilidad es local, uno de los siguientes:<br /><br /> 0 = La base de datos no es local en la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> 1 = La base de datos es local en la instancia de servidor.|  
|**is_primary_replica**|**bit**|Devuelve 1 si la réplica principal o 0 si se trata de una réplica secundaria. Es aplicable a SQL Server 2014 y versiones posteriores.|  
|**synchronization_state**|**tinyint**|Estado de movimiento de datos, uno de los siguientes valores.<br /><br /> 0 = no se están sincronizando. En una base de datos principal, indica que la base de datos no está lista para sincronizar su registro de transacciones con las bases de datos secundarias correspondientes. En una base de datos secundaria, indica que la base de datos no ha iniciado la sincronización del registro debido a un problema de conexión, se está suspendiendo o está pasando por estados de transición durante el inicio o en una conmutación de roles.<br /><br /> 1 = la sincronización. En una base de datos principal, indica que la base de datos está lista para aceptar una solicitud de examen de una base de datos secundaria. En una base de datos secundaria, indica que se está produciendo un movimiento de datos activo para la base de datos.<br /><br /> 2 = Synchronized. Una base de datos principal muestra SYNCHRONIZED en lugar de SYNCHRONIZING. Una base de datos secundaria de confirmación sincrónica se muestra como sincronizado cuando la memoria caché local indica que la base de datos está lista para la conmutación por error y está en proceso de sincronización.<br /><br /> 3 = revertir. Indica la fase en el proceso de reversión cuando una base de datos secundaria está obteniendo activamente páginas de la base de datos principal. **Precaución:** cuando una base de datos en una réplica secundaria está en estado REVERTING, forzar la conmutación por error a la réplica secundaria deja la base de datos en un estado en el que no se puede iniciar como base de datos principal. O la base de datos tendrá que volverse a conectar como base de datos secundaria, o deberá aplicar las nuevas entradas del registro de una copia de seguridad de registros.<br /><br /> 4 = inicializar. Indica la fase de reversión cuando el registro de transacciones necesario para la puesta al día de una base de datos secundaria respecto al LSN de reversión se envía y se protege en una réplica secundaria. **Precaución:** cuando una base de datos en una réplica secundaria está en estado INITIALIZING, forzar la conmutación por error a la réplica secundaria deja la base de datos en un estado donde se inicia como una base de datos principal. O la base de datos tendrá que volverse a conectar como base de datos secundaria, o deberá aplicar las nuevas entradas del registro de una copia de seguridad de registros.|  
|**synchronization_state_desc**|**nvarchar (60)**|Descripción del estado de movimiento de datos, uno de los siguientes:<br /><br /> NOT SYNCHRONIZING<br /><br /> SYNCHRONIZING<br /><br /> SYNCHRONIZED<br /><br /> REVERTING<br /><br /> INITIALIZING|  
|**is_commit_participant**|**bit**|0 = La confirmación de la transacción no está sincronizada con respecto a esta base de datos.<br /><br /> 1 = La confirmación de la transacción está sincronizada con respecto a esta base de datos.<br /><br /> Para una base de datos de una réplica de disponibilidad de confirmación asincrónica, este valor siempre es 0.<br /><br /> Para una base de datos en una replicación de disponibilidad de confirmación sincrónica, este valor es preciso solo en la base de datos principal.|  
|**synchronization_health**|**tinyint**|Refleja la intersección entre el estado de sincronización de una base de datos que se ha unido al grupo de disponibilidad en la réplica de disponibilidad y el modo de disponibilidad de la réplica de disponibilidad (modo de confirmación sincrónica o asincrónica), uno de los valores siguientes.<br /><br /> 0 = no correcto. El **synchronization_state** de la base de datos es 0 (no se están SINCRONIZANDO).<br /><br /> 1 = parcialmente correcto. Una base de datos en una réplica de disponibilidad de confirmación sincrónica se considera parcialmente correcta si **synchronization_state** es 1 (SYNCHRONIZING).<br /><br /> 2 = correcto. Una base de datos en una réplica de disponibilidad de confirmación sincrónica se considera correcta si **synchronization_state** es 2 (SYNCHRONIZED) y una base de datos en una réplica de disponibilidad de confirmación asincrónica se considera correcta si **synchronization_state** es 1 (SYNCHRONIZING).|  
|**synchronization_health_desc**|**nvarchar (60)**|Descripción de la **synchronization_health** de la base de datos de disponibilidad.<br /><br /> NOT_HEALTHY<br /><br /> PARTIALLY_HEALTHY<br /><br /> HEALTHY|  
|**database_state**|**tinyint**|0 = En línea<br /><br /> 1 = Restaurándose<br /><br /> 2 = En recuperación<br /><br /> 3 = Recuperación pendiente<br /><br /> 4 = Sospechosa<br /><br /> 5 = Emergencia<br /><br /> 6 = Sin conexión<br /><br /> **Nota:** igual que **estado** columna en sys.databases.|  
|**database_state_desc**|**nvarchar (60)**|Descripción de la **database_state** de la réplica de disponibilidad.<br /><br /> ONLINE<br /><br /> RESTORING<br /><br /> RECOVERING<br /><br /> RECOVERY_PENDING <br /><br /> SUSPECT<br /><br /> EMERGENCY<br /><br /> OFFLINE<br /><br /> **Nota:** igual que **estado** columna en sys.databases.|  
|**is_suspended**|**bit**|Estado de la base de datos, uno de los siguientes:<br /><br /> 0 = Reanudada<br /><br /> 1 = Suspendida|  
|**suspend_reason**|**tinyint**|Si la base de datos está suspendida, el motivo de este estado; uno de los siguientes:<br /><br /> 0 = Acción del usuario<br /><br /> 1 = Suspender desde el asociado<br /><br /> 2 = Rehacer<br /><br /> 3 = Capturar<br /><br /> 4 = Aplicar<br /><br /> 5 = Reiniciar<br /><br /> 6 = Deshacer<br /><br /> 7 = Revalidación<br /><br /> 8 = Error en el cálculo del punto de sincronización de la réplica secundaria.|  
|**suspend_reason_desc**|**nvarchar (60)**|Descripción del motivo del estado suspendido de la base de datos, uno de los siguientes:<br /><br /> SUSPEND_FROM_USER = Un usuario suspendió manualmente el movimiento de datos<br /><br /> SUSPEND_FROM_PARTNER = La réplica de base de datos se suspende tras una conmutación por error forzada<br /><br /> SUSPEND_FROM_REDO = Error durante la fase Rehacer<br /><br /> SUSPEND_FROM_APPLY = Error al escribir el registro en el archivo (vea el registro de errores)<br /><br /> SUSPEND_FROM_CAPTURE = Error al capturar el registro en la réplica principal<br /><br /> SUSPEND_FROM_RESTART = La réplica de base de datos se suspendió antes de que la base de datos se reiniciara (vea el registro de errores)<br /><br /> SUSPEND_FROM_UNDO = Error durante la fase Rehacer (vea el registro de errores)<br /><br /> SUSPEND_FROM_REVALIDATION = La coincidencia de cambios de registro se detecta en la reconexión (vea el registro de errores)<br /><br /> SUSPEND_FROM_XRF_UPDATE = No se puede encontrar el punto común de registro (vea el registro de errores)|  
|**recovery_lsn**|**numeric(25,0)**|En la réplica principal, el final del registro de transacciones antes de que la base de datos principal escriba nuevas entradas de registro después de la recuperación o la conmutación por error. Para una base de datos secundaria, si este valor es menor que el LSN reforzado actual (last_hardened_lsn), el recovery_lsn es el valor con el que esta base de datos secundaria necesitaría volver a sincronizar (es decir, revertir y reinicializar). Si este valor es mayor o igual que el LSN reforzado actual, sería innecesaria una resincronización y no se produciría.<br /><br /> **recovery_lsn** refleja un identificador de bloque de registro rellenado con ceros. No es un número de secuencia de registro (LSN) real. Para obtener información acerca de cómo se deriva este valor, consulte [descripción de los valores de columna LSN](#LSNcolumns), más adelante en este tema.|  
|**truncation_lsn**|**numeric(25,0)**|En la réplica principal, para la base de datos principal, refleja el LSN de truncamiento del registro mínimo a través de todas las bases de datos secundarias correspondientes. Si el truncamiento de registro local está bloqueado (como mediante una operación de copia de seguridad), este LSN podría ser mayor que el LSN de truncamiento local.<br /><br /> En una base de datos secundaria dada, refleja el punto de truncamiento de esa base de datos.<br /><br /> **truncation_lsn** refleja un identificador de bloque de registro rellenado con ceros. No es un número de secuencia de registro real.|  
|**last_sent_lsn**|**numeric(25,0)**|El identificador de bloque de registro que indica el punto en el que todos los bloques de registro han sido enviados por el elemento principal. Es el identificador del bloque de registro siguiente que se enviará, en lugar del identificador del bloque de registro enviado más recientemente.<br /><br /> **last_sent_lsn** refleja un identificador de bloque de registro rellenado con ceros, no es un número de secuencia de registro real.|  
|**last_sent_time**|**datetime**|Hora en que se envió el último bloque de registro.|  
|**last_received_lsn**|**numeric(25,0)**|Identificador de bloque de registro que identifica el punto en el que todos los bloques de registro han sido recibidor por la réplica secundaria que hospeda esta base de datos secundaria.<br /><br /> **last_received_lsn** refleja un identificador de bloque de registro rellenado con ceros. No es un número de secuencia de registro real.|  
|**last_received_time**|**datetime**|Hora en que el identificador de bloque de registro del último mensaje recibido se leyó en la réplica secundaria.|  
|**last_hardened_lsn**|**numeric(25,0)**|Inicio del bloque de registro que contiene los registros del último LSN reforzado en una base de datos secundaria.<br /><br /> En una base de datos principal de confirmación asincrónica o en una base de datos de confirmación sincrónica cuya directiva actual sea "retrasar", el valor es NULL. Para otras bases de datos principales de confirmación sincrónica, **last_hardened_lsn** indica la longitud mínima del LSN reforzado a través de todas las bases de datos secundarias.<br /><br /> **Nota: last_hardened_lsn** refleja un identificador de bloque de registro rellenado con ceros. No es un número de secuencia de registro real. Para obtener más información, consulte [descripción de los valores de columna LSN](#LSNcolumns), más adelante en este tema.|  
|**last_hardened_time**|**datetime**|En una base de datos secundaria, hora del identificador de bloque de registro para el último LSN protegido (**last_hardened_lsn**). En una base de datos principal, refleja la hora que corresponde al LSN reforzado mínimo.|  
|**last_redone_lsn**|**numeric(25,0)**|El número de secuencia de registro real de la última entrada de registro que se rehízo en la base de datos secundaria. **last_redone_lsn** es siempre menor que **last_hardened_lsn**.|  
|**last_redone_time**|**datetime**|Hora en que la última entrada de registro se rehízo en la base de datos secundaria.|  
|**log_send_queue_size**|**bigint**|Cantidad de entradas de registro de la base de datos principal que no se han enviado a las bases de datos secundarias, en kilobytes (kB).|  
|**log_send_rate**|**bigint**|Promedio de tasa en los datos de instancia que se envían de réplica principal durante el último período activo, en kilobytes (KB) / seg.|  
|**redo_queue_size**|**bigint**|Cantidad de entradas de registro en los archivos de registro de la réplica secundaria que no se han rehecho todavía, en kilobytes (KB).|  
|**redo_rate**|**bigint**|Velocidad a la que las entradas de registro se rehacen en una base de dato secundaria, en kilobytes (kB)/segundo.|  
|**filestream_send_rate**|**bigint**|Velocidad a la que los archivos FILESTREAM se envían a la réplica secundaria, en kilobytes (KB)/segundo.|  
|**end_of_log_lsn**|**numeric(25,0)**|Fin local del LSN de registro. LSN actual correspondiente a la última entrada de registro en la memoria caché del registro en las bases de datos principal y secundaria. En la réplica principal, las filas secundarias reflejan el final del LSN de registro de los mensajes de progreso más recientes que las réplicas secundarias han enviado a la principal.<br /><br /> **end_of_log_lsn** refleja un identificador de bloque de registro rellenado con ceros. No es un número de secuencia de registro real. Para obtener más información, consulte [descripción de los valores de columna LSN](#LSNcolumns), más adelante en este tema.|  
|**last_commit_lsn**|**Numeric(25,0)**|Número de secuencia de registro real correspondiente al último registro de confirmación del registro de transacciones.<br /><br /> En la base de datos principal, corresponde al último registro de confirmación procesado. Las filas para las bases de datos secundarias muestran el número de secuencia de registro que la réplica secundaria ha enviado a la principal.<br /><br /> En la réplica secundaria, es el último registro de confirmación que se rehízo.|  
|**last_commit_time**|**datetime**|Hora correspondiente al último registro de confirmación.<br /><br /> En la base de datos secundaria, esta hora es igual la misma que para la base de datos principal.<br /><br /> En la réplica principal, cada fila de la base de datos secundaria muestra la hora que la réplica secundaria que hospeda dicha base de datos secundaria ha notificado a la réplica principal. La diferencia de la hora entre la fila de la base de datos principal y una fila determinada de la base de datos secundaria representa aproximadamente el objetivo de tiempo de recuperación (RPO), suponiendo que el proceso de rehacer está puesto al día y que la réplica secundaria ha notificado el progreso a la réplica principal.|  
|**low_water_mark_for_ghosts**|**bigint**|Un número que aumenta regularmente para la base de datos que indica una marca de límite inferior utilizada por la limpieza de registros fantasma en la base de datos principal. Si este número no aumenta con el tiempo, implica que no puede producirse la limpieza de registros fantasma. Para decidir qué filas fantasma se han de limpiar, la réplica principal utiliza el valor mínimo de esta columna para esta base de datos en todas las réplicas de disponibilidad (incluida la réplica principal).|  
|**secondary_lag_seconds**|**bigint**|El número de segundos que la réplica secundaria está detrás de la réplica principal durante la sincronización.|  
  
##  <a name="LSNcolumns"></a>Descripción de los valores de columna LSN  
 Los valores de la **end_of_log_lsn**, **last_hardened_lsn**, **last_received_lsn**, **last_sent_lsn**, **recuperación _lsn**, y **truncation_lsn** columnas no son números de secuencia de registro real (LSN). En su lugar, cada uno de estos valores refleja un identificador de bloque de registro rellenado con ceros.  
  
 **end_of_log_lsn**, **last_hardened_lsn**, y **recovery_lsn** son LSN de vaciado. Por ejemplo, **last_hardened_lsn** indica el inicio del bloque siguiente más allá de los bloques que ya están en el disco.  Por lo tanto, cualquier LSN < el valor de **last_hardened_lsn** está en el disco.  Los LSN que son >= este valor no se vacían.  
  
 De los valores LSN devueltos por **sys.dm_hadr_database_replica_states**, solo **last_redone_lsn** es un LSN real.  
  
## <a name="security"></a>Seguridad  
  
### <a name="permissions"></a>Permissions  
 es necesario contar con el permiso VIEW SERVER STATE en el servidor.  
  
## <a name="see-also"></a>Vea también  
 [Grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Supervisar grupos de disponibilidad &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)  
  
  