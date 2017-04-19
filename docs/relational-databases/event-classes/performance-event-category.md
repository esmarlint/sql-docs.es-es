---
title: "Rendimiento (categor&#237;a de eventos) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "clases de eventos de SQL Server, categoría de evento Rendimiento"
  - "Rendimiento, categoría de eventos [SQL Server]"
  - "clases de eventos [SQL Server], categoría de evento Rendimiento"
ms.assetid: 708f3585-d8be-4980-bbff-672d7c59397e
caps.latest.revision: 32
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 32
---
# Rendimiento (categor&#237;a de eventos)
  Use la categoría de eventos **Performance** para supervisar las clases de eventos **Showplan** y las clases de eventos que se producen al ejecutar operadores de lenguaje de manipulación de datos (DML) de SQL.  
  
## En esta sección  
  
|Tema|Descripción|  
|-----------|-----------------|  
|[Auto Stats (clase de eventos)](../../relational-databases/event-classes/auto-stats-event-class.md)|Indica que se ha producido una actualización automática de las estadísticas de índices y columnas.|  
|[Degree of Parallelism &#40;7.0 Insert&#41; clase de eventos](../../relational-databases/event-classes/degree-of-parallelism-7-0-insert-event-class.md)|Indica que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha ejecutado una instrucción SELECT, INSERT, UPDATE o DELETE utilizando un plan serie o paralelo. Se informa también del número de CPUs utilizadas para realizar la operación.|  
|[Performance Statistics (clase de eventos)](../../relational-databases/event-classes/performance-statistics-event-class.md)|Supervisa el rendimiento de las consultas que se están ejecutando.|  
|[Showplan All (clase de eventos)](../../relational-databases/event-classes/showplan-all-event-class.md)|Identifica los operadores de **Showplan** de una instrucción SQL.|  
|[Showplan All for Query Compile (clase de eventos)](../../relational-databases/event-classes/showplan-all-for-query-compile-event-class.md)|Muestra los datos de tiempo de compilación de los operadores de **Showplan** .|  
|[Showplan Statistics Profile (clase de eventos)](../../relational-databases/event-classes/showplan-statistics-profile-event-class.md)|Muestra el costo estimado de una consulta.|  
|[Showplan XML (clase de eventos)](../../relational-databases/event-classes/showplan-xml-event-class.md)|Identifica los operadores de **Showplan** en una instrucción SQL. La clase de eventos almacena cada evento como un documento XML bien definido.|  
|[Showplan XML For Query Compile (clase de eventos)](../../relational-databases/event-classes/showplan-xml-for-query-compile-event-class.md)|Muestra los datos de tiempo de compilación de los operadores de **Showplan** en formato XML.|  
|[Showplan XML Statistics Profile (clase de eventos)](../../relational-databases/event-classes/showplan-xml-statistics-profile-event-class.md)|Identifica los operadores de **Showplan** asociados a una instrucción SQL. La salida es un documento XML.|  
|[SQL:FullTextQuery (clase de eventos)](../../relational-databases/event-classes/sql-fulltextquery-event-class.md)|Indica que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha ejecutado una consulta de texto completo.|  
|[Clase de evento Guía de plan correcta](../../relational-databases/event-classes/plan-guide-successful-event-class.md)|Indica que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generó correctamente un plan de ejecución para una consulta o lote que contenía una guía de plan.|  
|[Clase de eventos Plan Guide Unsuccessful](../../relational-databases/event-classes/plan-guide-unsuccessful-event-class.md)|Indica que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no pudo generar un plan de ejecución para una consulta o lote que contenía una guía de plan.|  
  
## Vea también  
 [Eventos extendidos](../../relational-databases/extended-events/extended-events.md)  
  
  