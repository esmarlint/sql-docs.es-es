---
title: "Agregar o editar combinaciones | Microsoft Docs"
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
  - "sql13.rep.newpubwizard.addeditjoin.f1"
ms.assetid: 3b546560-720f-48b8-9d63-cf159290e9d4
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# Agregar o editar combinaciones
  Los cuadros de diálogo **Agregar combinación** y **Editar combinación** permiten agregar y editar filtros de combinación en publicaciones de combinación.  
  
> [!NOTE]  
>  La edición de un filtro en una publicación existente requiere una nueva instantánea para la publicación. Si una publicación tiene suscripciones, es necesario reinicializar las suscripciones. Para obtener más información acerca de los cambios de propiedad, vea [Propiedades de artículo y publicación de cambio](../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
 Un filtro de combinación permite filtrar una tabla en función de cómo se haya filtrado una tabla relacionada en la publicación. Normalmente, una tabla primaria se filtra utilizando un filtro de filas con parámetros; por tanto, los filtros de combinación se definen de manera muy similar a como se define una combinación entre tablas. Los filtros de combinación amplían el filtro de filas de modo que los datos de las tablas relacionadas solo se replican si coinciden con la cláusula del filtro de combinación.  
  
 Normalmente, los filtros de combinación siguen las relaciones entre clave principal y clave externa definidas para las tablas en las que se aplican, aunque no se limitan estrictamente a dichas relaciones. Un filtro de combinación puede estar basado en cualquier lógica que compare datos relacionados en dos tablas de artículos.  
  
> [!IMPORTANT]  
>  Los filtros de combinación pueden implicar un número ilimitado de tablas, pero los filtros con un gran número de tablas pueden producir un efecto en el rendimiento durante el proceso de mezcla. Si va a generar filtros de combinación de cinco tablas o más, considere otras soluciones, como no filtrar tablas pequeñas, que no estén sometidas a cambios o que sean principalmente tablas de búsqueda. Utilice los filtros de combinación solo entre tablas que se deben dividir en particiones entre suscriptores.  
  
## Opciones  
 Este cuadro de diálogo implica un proceso de tres pasos para crear un filtro de combinación entre dos tablas. Para crear varios filtros de combinación, es necesario pasar varias veces por el cuadro de diálogo.  
  
1.  **Compruebe la tabla filtrada y seleccione la tabla combinada**  
  
    -   Si va a agregar una nueva combinación, compruebe que la tabla en la **tabla filtrados** cuadro de texto es correcta (si no es correcta, haga clic en **Cancelar**, seleccione la tabla correcta en el **filtrar filas de tabla** página y haga clic en **Agregar combinación** para volver a este cuadro de diálogo). A continuación, seleccione una tabla desde el **tabla combinada** cuadro de lista desplegable.  
  
    -   Si está editando una combinación existente, los nombres de las tablas ya estarán especificados y no se podrán cambiar. Para cambiar las tablas implicadas en la combinación, debe eliminar el filtro de combinación existente en la página **Filtrar filas de tabla** y crear una nueva combinación entre otras tablas.  
  
2.  **Cree la instrucción de combinación**  
  
    -   Si está agregando una nueva combinación, seleccione **Usar generador de instrucciones para crear la instrucción** o **Escribir instrucción de combinación manualmente**. Si empieza a escribir la combinación manualmente, no podrá utilizar el generador.  
  
         Si selecciona utilizar el generador, use las columnas de la cuadrícula (**junto**, **columna de tabla filtrada**, **operador**, y **columna de tabla combinada**) para generar una instrucción de combinación. Cada columna de la cuadrícula contiene un cuadro de lista desplegable que permite seleccionar dos columnas y un operador (**=**, **<>**, **<=**, **\<**, **>=**, **>**, **como**). Los resultados se muestran en el área de texto **Vista previa** . Si la combinación implica más de un par de columnas, seleccione una conjunción (**AND** o **o**) desde el **junto** columna y, a continuación, escriba dos columnas más y otro operador.  
  
         Si selecciona escribir la instrucción manualmente, escriba la instrucción de combinación en el área de texto **Instrucción de combinación** . Utilice los cuadros de lista **Columna de tabla filtrada** y **Columnas de tabla combinada** para arrastrar y colocar columnas en el área de texto **Instrucción de combinación** .  
  
    -   Si está editando una combinación existente, debe realizar los cambios manualmente.  
  
3.  **Especifique las opciones de combinación**  
  
    -   Si la columna en la que combina la tabla filtrada es única, seleccione **Clave única**. El proceso de mezcla dispone de optimizaciones de rendimiento especiales si la columna es exclusiva.  
  
        > [!CAUTION]  
        >  Al seleccionar esta opción indica que la relación entre la tabla principal y la secundaria de un filtro de combinación es de uno a uno o de uno a varios. Seleccione esta opción únicamente si tiene una restricción en la columna combinada en la tabla primaria que garantiza la exclusividad. Si la opción no se establece correctamente, se podría producir la no convergencia de datos.  
  
    -   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] y versiones posteriores. De manera predeterminada, la replicación de mezcla procesa los cambios fila a fila durante la sincronización. Para hacer que los cambios relacionados se procesen como una unidad, seleccione **Registro lógico**. Esta opción solo está disponible si se cumplen los requisitos del artículo y de la publicación para utilizar registros lógicos. Para obtener más información, vea la sección "Consideraciones para utilizar registros lógicos" en [grupo cambios en las filas relacionadas con registros lógicos](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
 Una vez agregado o editado un filtro, haga clic en **Aceptar** para guardar los cambios y cerrar el cuadro de diálogo. El filtro que ha especificado se analiza y se ejecuta según la tabla de la cláusula SELECT. Si la instrucción de filtro contiene errores de sintaxis u otros problemas, se le notificará y podrá modificar dicha instrucción.  
  
## Vea también  
 [Crear una publicación](../../relational-databases/replication/publish/create-a-publication.md)   
 [Ver y modificar propiedades de publicación](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Filtrar datos publicados](../../relational-databases/replication/publish/filter-published-data.md)   
 [Filtros de combinación](../../relational-databases/replication/merge/join-filters.md)   
 [Filtros de fila con parámetros](../../relational-databases/replication/merge/parameterized-row-filters.md)   
 [Publicar datos y objetos de base de datos](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  