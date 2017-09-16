---
title: Iniciar un seguimiento | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Profiler, stopping traces
- pausing traces
- Profiler [SQL Server Profiler], stopping traces
- Profiler [SQL Server Profiler], starting traces
- traces [SQL Server], starting
- SQL Server Profiler, pausing traces
- traces [SQL Server], stopping
- Profiler [SQL Server Profiler], pausing traces
- traces [SQL Server], pausing
- SQL Server Profiler, starting traces
- stopping traces
- starting traces
ms.assetid: aeeb38eb-229a-4c8b-ad66-57e9ce45fb6a
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5f06bb0ddcf6fdb8920dc260a9759ad605f6b6e9
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="start-a-trace"></a>Iniciar un seguimiento
  Una vez definida un nuevo seguimiento o creada una plantilla mediante el [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], puede iniciar, pausar o detener la captura de datos con la nueva definición de seguimiento o plantilla.  
  
## <a name="starting-a-trace"></a>Iniciar un seguimiento  
 Si inicia un seguimiento y el origen definido es una instancia del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] o [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crea una cola para colocar temporalmente los eventos de servidor capturados.  
  
 Si utiliza el [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] para tener acceso a Seguimiento de SQL, al iniciar un seguimiento se abre una nueva ventana de seguimiento (si aún no hay ninguna abierta) y los datos se capturan inmediatamente.  
  
 Si se utilizan los procedimientos almacenados del sistema [!INCLUDE[tsql](../../includes/tsql-md.md)] para tener acceso a Seguimiento de SQL, debe iniciar un seguimiento cada vez que se inicie una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para que los datos se capturen. Una vez iniciado el seguimiento, solo puede modificar el nombre de este.  
  
> [!NOTE]  
>  Si trabaja con seguimientos existentes, puede ver las propiedades, pero no modificarlas. Para modificar las propiedades, detenga o pause el seguimiento.  
  
## <a name="see-also"></a>Vea también  
 [Iniciar un seguimiento automáticamente después de conectarse a un servidor &#40; Analizador de SQL Server &#41;](../../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)   
 [Pausar un seguimiento &#40; Analizador de SQL Server &#41;](../../tools/sql-server-profiler/pause-a-trace-sql-server-profiler.md)   
 [Detener un seguimiento &#40; Analizador de SQL Server &#41;](../../tools/sql-server-profiler/stop-a-trace-sql-server-profiler.md)   
 [Borrar una ventana de seguimiento &#40; Analizador de SQL Server &#41;](../../tools/sql-server-profiler/clear-a-trace-window-sql-server-profiler.md)   
 [Ejecutar un seguimiento después de haberlo pausado o detenido &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)  
  
  