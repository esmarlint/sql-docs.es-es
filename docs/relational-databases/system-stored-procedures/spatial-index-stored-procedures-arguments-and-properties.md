---
title: Procedimientos almacenan de argumentos y las propiedades del índice espacial | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- spatial indexes [SQL Server], stored procedures
ms.assetid: ee26082b-c0ed-40ff-b5ad-f5f6b00f0475
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 20c747b51bd4fc20e21bedfed1f826005b1037a1
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33262898"
---
# <a name="spatial-index-stored-procedures---arguments-and-properties"></a>Procedimientos - argumentos y propiedades almacenados de índice espacial
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  En este tema se documentan los argumentos y propiedades de los procedimientos almacenados de índice espacial.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
 Para obtener la sintaxis específica de los procedimientos almacenados de índice espacial, consulte los temas siguientes:  
  
-   [sp_help_spatial_geometry_index &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-transact-sql.md)  
  
-   [sp_help_spatial_geometry_index_xml &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-xml-transact-sql.md)  
  
-   [sp_help_spatial_geography_index &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)  
  
-   [sp_help_spatial_geography_index_xml &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-xml-transact-sql.md)  
  
## <a name="arguments"></a>Argumentos  
 [  **@tabname =**] **'***tabname***'**  
 Es el nombre completo o incompleto de la tabla para la que se ha especificado el índice espacial.  
  
 Se requieren comillas únicamente si se especifica una tabla certificada. Si se proporciona un nombre completo, incluido el nombre de la base de datos, el nombre de la base de datos debe ser el de la base de datos actual. *TabName* es **nvarchar**(776) y no tiene ningún valor predeterminado.  
  
 [  **@indexname =** ] **'***indexname***'**  
 Es el nombre del índice espacial especificado. *IndexName* es **sysname** no tiene ningún valor predeterminado.  
  
 [  **@verboseoutput =** ] **'***verboseoutput***'**  
 Es el intervalo de nombres de propiedad y valores que se van a devolver.  
  
 0 = propiedades básicas  
  
 \>0 = todas las propiedades  
  
 *verboseoutput* es **tinyint** no tiene ningún valor predeterminado.  
  
 [  **@query_sample =** ] **'***query_sample***'**  
 Es un ejemplo de consulta representativo que se puede utilizar para probar la utilidad del índice. Puede ser un objeto representativo o una ventana de consulta. *query_sample* es **geometry** no tiene ningún valor predeterminado.  
  
 [  **@xml_output =** ] **'***xml_output***'**  
 Es un parámetro de salida que devuelve el conjunto de resultados de un fragmento XML. *xml_output* es **xml** no tiene ningún valor predeterminado.  
  
## <a name="properties"></a>Propiedades  
 Establecer **@verboseoutput** = 0 para devolver las propiedades básicas, como se muestra en la tabla siguiente; **@verboseoutput** > 0 para devolver todas las propiedades del índice espacial.  
  
 **Base_Table_Rows**  
 Número de filas de la tabla base. Valor es **bigint**.  
  
 **Columnas Bounding_Box_xmin**  
 Propiedades del índice espacial del cuadro de límite X mínimo **geometry** tipo. Valor de esta propiedad es NULL para **geography**tipo. Valor es **float**.  
  
 **Bounding_Box_ymin**  
 Propiedades del índice espacial del cuadro de límite Y mínimo **geometry** tipo. Valor de esta propiedad es NULL para **geography** tipo. Valor es **float**.  
  
 **Bounding_Box_xmax**  
 Propiedades del índice espacial del cuadro de límite X máximo **geometry** tipo. Valor de esta propiedad es NULL para **geography** tipo. Valor es **float**.  
  
 **Bounding_Box_ymax**  
 Propiedades del índice espacial del cuadro de límite Y máximo **geometry** tipo. Valor de esta propiedad es NULL para **geography** tipo. Valor es **float**.  
  
 **Grid_Size_Level_1**  
 Densidad de cuadrícula de nivel 1 del índice espacial:  
  
 16 para LOW  
  
 64 para MEDIUM  
  
 256 para HIGH  
  
 Valor es **int**.  
  
 **Grid_Size_Level_2**  
 Densidad de cuadrícula de nivel 2 del índice espacial:  
  
 16 para LOW  
  
 64 para MEDIUM  
  
 256 para HIGH  
  
 Valor es **int**.  
  
 **Grid_Size_Level_3**  
 Densidad de cuadrícula de nivel 3 del índice espacial:  
  
 16 para LOW  
  
 64 para MEDIUM  
  
 256 para HIGH  
  
 Valor es **int**.  
  
 **Grid_Size_Level_4**  
 Densidad de la cuadrícula de nivel 4 del índice espacial:  
  
 16 para LOW  
  
 64 para MEDIUM  
  
 256 para HIGH  
  
 Valor es **int**.  
  
 **Cells_Per_Object**  
 Número de celdas por cada objeto (propiedad de índice). Valor es **int**.  
  
 **Total_Primary_Index_Rows**  
 Número de filas del índice. Valor es **bigint**.  
  
 **Total_Primary_Index_Pages**  
 Número de páginas del índice. Valor es **bigint**.  
  
 **Average_Number_Of_Index_Rows_Per_Base_Row**  
 Número de filas de índice / número de filas de la tabla base. Valor es **bigint**.  
  
 **Total_Number_Of_ObjectCells_In_Level0_For_QuerySample**  
 Indica si el ejemplo de consulta representativo está fuera del cuadro de límite de la **geometry** índice y en la celda raíz (celda de nivel 0). Es 0 (no está en la celda de nivel 0) ó 1. Si está en la celda de nivel 0, el índice investigado no es adecuado para el ejemplo de consulta. Ésta es una propiedad básica. Valor es **bigint**.  
  
 **Total_Number_Of_ObjectCells_In_Level0_In_Index**  
 Número de celdas de objetos indizados que se teselan en el nivel 0 (celda raíz, fuera del cuadro de límite para **geometry**). Ésta es una propiedad básica. Valor es **bigint**.  
  
 Para **geometry** índices, esto ocurrirá si el cuadro de límite del índice es menor que el dominio de datos. Un gran número de objetos en el nivel 0 puede requerir filtros secundarios si la ventana de consulta está parcialmente fuera delimitador en el cuadro y reduzcan el rendimiento del índice (por ejemplo, **Total_Number_Of_ObjectCells_In_Level0_For_QuerySample** es 1). Si la ventana de consulta cae dentro del cuadro de límite, un número alto de objetos en el nivel 0 puede mejorar realmente el rendimiento del índice.  
  
 NULL y las instancias vacías se contabilizan en el nivel 0 pero no afectarán al rendimiento. El nivel 0 tendrá tantas celdas como NULL y las instancias vacías en la tabla base. Para **geography** índices, nivel 0 tendrá tantas celdas como NULL y la celda instancias vacías + 1, porque el ejemplo de consulta se cuenta como 1.  
  
 **Total_Number_Of_ObjectCells_In_Level1_In_Index**  
 Número de celdas de objetos indizados que se teselan con precisión de nivel 1. Ésta es una propiedad básica. Valor es **bigint**.  
  
 **Total_Number_Of_ObjectCells_In_Level2_In_Index**  
 Número de celdas de objetos indizados que se teselan con precisión de nivel 2. Ésta es una propiedad básica. Valor es **bigint**.  
  
 **Total_Number_Of_ObjectCells_In_Level3_In_Index**  
 Número de celdas de objetos indizados que se teselan con precisión de nivel 3. Ésta es una propiedad básica. Valor es **bigint**.  
  
 **Total_Number_Of_ObjectCells_In_Level4_In_Index**  
 Número de instancias de celdas de objetos indizados que se teselan con precisión de nivel 4. Ésta es una propiedad básica. Valor es **bigint**.  
  
 **Total_Number_Of_interior_ObjectCells_In_Level1_In_Index**  
 Número de celdas que están completamente cubiertas por un objeto en el nivel de teselación 1 y, por tanto, son interiores al objeto. (Cell_attributevalue es 2). Ésta es una propiedad básica. Valor es **bigint**.  
  
 **Total_Number_Of_interior_ObjectCells_In_Level2_In_Index**  
 Número de celdas que están completamente cubiertas por un objeto en el nivel de teselación 2 y, por tanto, son interiores al objeto. (El valor de Cell_attribute es 2). Ésta es una propiedad básica. Valor es **bigint**.  
  
 **Total_Number_Of_interior_ObjectCells_In_Level3_In_Index**  
 Número de celdas que están completamente cubiertas por un objeto en el nivel de teselación 3 y, por tanto, son interiores al objeto. (El valor de Cell_attribute es 2). Ésta es una propiedad básica. Valor es **bigint**.  
  
 **Total_Number_Of_interior_ObjectCells_In_Level4_In_Index**  
 Número de celdas que están cubiertas completamente por un objeto en el nivel 4 de teselación y, por lo tanto, son interiores al objeto. (El valor de Cell_attribute es 2). Ésta es una propiedad básica. Valor es **bigint**.  
  
 **Total_Number_Of_intersecting_ObjectCells_In_Level1_In_Index**  
 Número de celdas que intersecta un objeto en el nivel de teselación 1. (El valor de Cell_attribute es 1). Ésta es una propiedad básica. Valor es **bigint**.  
  
 **Total_Number_Of_intersecting_ObjectCells_In_Level2_In_Index**  
 Número de celdas que intersecta un objeto en el nivel de teselación 2. (El valor de Cell_attribute es 1). Ésta es una propiedad básica. Valor es **bigint**.  
  
 **Total_Number_Of_intersecting_ObjectCells_In_Level3_In_Index**  
 Número de celdas que intersecta un objeto en el nivel de teselación 3. (El valor de Cell_attribute es 1). Ésta es una propiedad básica. Valor es **bigint**.  
  
 **Total_Number_Of_intersecting_ObjectCells_In_Level4_In_Index**  
 Número de celdas que intersecta un objeto en el nivel 4 de teselación. (El valor de Cell_attribute es 1). Ésta es una propiedad básica. Valor es **bigint**.  
  
 **Total_Number_Of_Border_ObjectCells_In_Level0_For_QuerySample**  
 Indica si el ejemplo de consulta está en la celda raíz 0, fuera del cuadro de límite, pero tocándolo. Ésta es una propiedad básica. Valor es **bigint**.  
  
> [!NOTE]  
>  Esta información solo es útil para determinar si hay objetos que el cuadro de límite pueda echar mucho en falta.  
  
 **Total_Number_Of_Border_ObjectCells_In_Level0_In_Index**  
 El número de objetos del nivel 0 que tocan al cuadro de límite. (El valor de Cell_attribute es 0).  Valor es **bigint**.  
  
 **Total_Number_Of_Border_ObjectCells_In_Level1_In_Index**  
 Número de celdas de objeto que tocan un límite de celda de cuadrícula en el nivel de teselación 1. (El valor de Cell_attribute es 0). Ésta es una propiedad básica. Valor es **bigint**.  
  
 **Total_Number_Of_Border_ObjectCells_In_Level2_In_Index**  
 Número de celdas de objeto que tocan un límite de celda de cuadrícula en el nivel de teselación 2. (El valor de Cell_attribute es 0). Ésta es una propiedad básica. Valor es **bigint**.  
  
 **Total_Number_Of_Border_ObjectCells_In_Level3_In_Index**  
 Número de celdas de objeto que tocan un límite de celda de cuadrícula en el nivel de teselación 3. (El valor de Cell_attribute es 0). Ésta es una propiedad básica. Valor es **bigint**.  
  
 **Total_Number_Of_Border_ObjectCells_In_Level4_In_Index**  
 Número de celdas de objeto que tocan un límite de celda de cuadrícula en el nivel 4 de teselación. (El valor de Cell_attribute es 0). Ésta es una propiedad básica. Valor es **bigint**.  
  
 **Interior_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage**  
 Porcentaje del área total (celdas hoja totales) de la cuadrícula que contienen celdas hoja cubiertas por un objeto.  
  
 Por ejemplo, un objeto está teselado en 10 celdas en los 4 niveles de cuadrícula diferentes que abarcan un área que es equivalente a 100 celdas hoja en total. Suponga que hay 3 celdas interiores que están completamente cubiertas por el objeto. El área cubierta por las 3 celdas interiores es equivalente a 42 celdas hoja. Así, el porcentaje de área cubierta es del 42 por ciento. Esta es una buena medida de cómo se dividen los objetos en el índice.  
  
 Valor es **float**.  
  
 **Intersecting_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage**  
 Igual que **Interior_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage**, excepto en que éstas son celdas cubiertas parcialmente. Valor es **float**.  
  
 **Border_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage**  
 Igual que **Interior_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage** salvo que estas son celdas de borde. Valor es **float**.  
  
 **Average_Cells_Per_Object_Normalized_To_Leaf_Grid**  
 Promedio de celdas por objeto normalizadas en la cuadrícula hoja. Nos da una indicación del tamaño espacial del objeto o de la magnitud de los objetos. Valor es **float**.  
  
 **Average_Objects_PerLeaf_GridCell**  
 Grado de dispersión del índice. Número promedio de objetos por cada celda hoja. Valor es **float**.  
  
 **Number_Of_SRIDs_Found**  
 Número de SRID únicos en el índice y columna. Valor es **int**.  
  
 Dado que una columna puede contener más de un SRID y objetos de SRID diferentes que nunca intersecten, el número de SRID indica la selectividad del índice.  
  
 **Width_Of_Cell_In_Level1**  
 Propiedad de ancho de la celda en la cuadrícula de indización. La unidad de medida proporcionada por el índice y depende del SRID de los datos indizados. Valor es **float**.  
  
 **Width_Of_Cell_In_Level2**  
 Propiedad de ancho de la celda en la cuadrícula de indización. La unidad de medida proporcionada por el índice y depende del SRID de los datos indizados. Valor es **float**.  
  
 **Width_Of_Cell_In_Level3**  
 Propiedad de ancho de la celda en la cuadrícula de indización. La unidad de medida proporcionada por el índice y depende del SRID de los datos indizados. Valor es **float**.  
  
 **Width_Of_Cell_In_Level4**  
 Propiedad de ancho de la celda en la cuadrícula de indización. La unidad de medida la proporciona el índice y depende del SRID de los datos indizados. Valor es **float**.  
  
 **Height_Of_Cell_In_Level1**  
 Propiedad de alto de la celda en la cuadrícula de indización. La unidad de medida proporcionada por el índice y depende del SRID de los datos indizados. Valor es **float**.  
  
 **Height_Of_Cell_In_Level2**  
 Propiedad de alto de la celda en la cuadrícula de indización. La unidad de medida proporcionada por el índice y depende del SRID de los datos indizados. Valor es **float**.  
  
 **Height_Of_Cell_In_Level3**  
 Propiedad de alto de la celda en la cuadrícula de indización. La unidad de medida proporcionada por el índice y depende del SRID de los datos indizados. Valor es **float**.  
  
 **Height_Of_Cell_In_Level4**  
 Propiedad de alto de la celda en la cuadrícula de indización. La unidad de medida proporcionada por el índice y depende del SRID de los datos indizados. Valor es **float**.  
  
 **Area_Of_Cell_In_Level1**  
 Propiedad de área de la celda en la cuadrícula de indización. La unidad de medida proporcionada por el índice y depende del SRID de los datos indizados. Valor es **float**.  
  
 **Area_Of_Cell_In_Level2**  
 Propiedad de área de la celda en la cuadrícula de indización. La unidad de medida proporcionada por el índice y depende del SRID de los datos indizados. Valor es **float**.  
  
 **Area_Of_Cell_In_Level3**  
 Propiedad de área de la celda en la cuadrícula de indización. La unidad de medida proporcionada por el índice y depende del SRID de los datos indizados. Valor es **float**.  
  
 **Area_Of_Cell_In_Level4**  
 Propiedad de área de la celda en la cuadrícula de indización. La unidad de medida proporcionada por el índice y depende del SRID de los datos indizados. Valor es **float**.  
  
 **CellArea_To_BoundingBoxArea_Percentage_In_Level1**  
 El porcentaje de cobertura del cuadro de límite en una celda de nivel 1. Valor es **float**.  
  
 **CellArea_To_BoundingBoxArea_Percentage_In_Level2**  
 El porcentaje de cobertura del cuadro de límite en una celda de nivel 2. Valor es **float**.  
  
 **CellArea_To_BoundingBoxArea_Percentage_In_Level3**  
 El porcentaje de cobertura del cuadro de límite en una celda de nivel 3. Valor es **float**.  
  
 **CellArea_To_BoundingBoxArea_Percentage_In_Level4**  
 Porcentaje de cobertura del cuadro de límite por una celda de nivel 4. Valor es **float**.  
  
 **Number_Of_Rows_Selected_By_Primary_Filter**  
 Número de filas seleccionadas por el filtro primario. Ésta es una propiedad básica. Valor es **bigint.**  
  
 **Number_Of_Rows_Selected_By_Internal_Filter**  
 Número de filas seleccionadas por el filtro interno. No se llama al filtro secundario para estas filas. Ésta es una propiedad básica. Valor es **bigint.**  
  
 El número devuelto solo es aplicable para **STintersects**.  
  
 **Number_Of_Times_Secondary_Filter_Is_Called**  
 Número de veces que se llama al filtro secundario. Ésta es una propiedad básica. Valor es **bigint.**  
  
 **Percentage_Of_Rows_NotSelected_By_Primary_Filter**  
 Si hay N filas en la tabla base y el filtro primario selecciona P, devuelve (N-P)/N como porcentaje. Ésta es una propiedad básica. Valor es **float.**  
  
 **Percentage_Of_Primary_Filter_Rows_Selected_By_internal_Filter**  
 Si el filtro primario selecciona P filas y el filtro interno selecciona S filas, devuelve S/P como porcentaje. Cuanto mayor es el porcentaje, más eficaz es el índice evitando el filtro secundario con un rendimiento más caro. Ésta es una propiedad básica. Valor es **float.**  
  
 **Number_Of_Rows_Output**  
 Número de filas que produce la consulta. Ésta es una propiedad básica. Valor es **bigint.**  
  
 **Internal_Filter_Efficiency**  
 Si O es el número de filas de salida, devuelve S/O como porcentaje. Ésta es una propiedad básica. Valor es **float.**  
  
 **Primary_Filter_Efficiency**  
 Si el filtro primario y O selecciona P filas es el número de filas de salida, este returnsO/P, como un porcentaje. Cuanto más eficaz es el filtro primario, menos falsos positivos tiene que procesar el filtro secundario. Ésta es una propiedad básica. Valor es **float.**  
  
## <a name="permissions"></a>Permissions  
 Usuario debe ser un miembro de la **público** rol. Requiere el permiso READ ACCESS en el servidor y el objeto. Esto se aplica a todos los procedimientos almacenados de índice espacial.  
  
## <a name="remarks"></a>Comentarios  
 Las propiedades que contienen valores NULL están incluidas en el conjunto que se devuelve.  
  
## <a name="examples"></a>Ejemplos  
 Para obtener ejemplos, vea los siguientes temas:  
  
-   [sp_help_spatial_geometry_index &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-transact-sql.md)  
  
-   [sp_help_spatial_geometry_index_xml &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-xml-transact-sql.md)  
  
-   [sp_help_spatial_geography_index &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)  
  
-   [sp_help_spatial_geography_index_xml &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-xml-transact-sql.md)  
  
## <a name="requirements"></a>Requisitos  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos almacenados de índice espacial &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)   
 [sp_help_spatial_geometry_index &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-transact-sql.md)   
 [Información general sobre los índices espaciales](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [Conceptos básicos de XQuery](../../xquery/xquery-basics.md)   
 [Referencia del lenguaje XQuery &#40;SQL Server&#41;](../../xquery/xquery-language-reference-sql-server.md)  
  
  
