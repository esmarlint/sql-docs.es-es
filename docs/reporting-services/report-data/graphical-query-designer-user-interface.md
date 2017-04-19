---
title: "Interfaz de usuario del dise&#241;ador gr&#225;fico de consultas | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "10012"
  - "sql13.rtp.rptdesigner.dataview.vdtquerydesigner.f1"
helpviewer_keywords: 
  - "diseñador gráfico de consultas [Reporting Services]"
  - "orígenes de datos [Reporting Services], crear"
  - "diseñador de consultas basado en texto [Reporting Services]"
  - "diseñadores de consultas [Reporting Services]"
  - "Reporting Services, diseñadores de consultas"
ms.assetid: 5022ae33-03a3-48de-8ac1-82742f48cebe
caps.latest.revision: 54
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 54
---
# Interfaz de usuario del dise&#241;ador gr&#225;fico de consultas
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] proporciona un diseñador gráfico de consultas y un diseñador de consultas basado en texto con los que se pueden crear consultas y recuperar datos de una base de datos relacional para un conjunto de datos de informe del Diseñador de informes. Use el diseñador gráfico de consultas para generar una consulta de forma interactiva y ver los resultados para los tipos de orígenes de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Oracle, OLE DB y ODBC. Use el diseñador de consultas basado en texto para especificar varias instrucciones de [!INCLUDE[tsql](../../includes/tsql-md.md)], sintaxis compleja de consultas o comandos, y consultas basadas en expresiones. Para más información, vea [Interfaz de usuario del Diseñador de consultas basado en texto](../Topic/Text-based%20Query%20Designer%20User%20Interface.md). Para más información sobre cómo trabajar con tipos de orígenes de datos específicos, vea [Conjuntos de datos de informe &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md).  
  
 .  
  
## Diseñador gráfico de consultas  
 Este diseñador gráfico de consultas admite tres tipos de comandos de consulta: **Text**, **StoredProcedure**o **TableDirect**. Antes de crear una consulta para el conjunto de datos, debe seleccionar una opción de tipo de comando en la página Consulta del cuadro de diálogo [Propiedades del conjunto de datos](../Topic/Dataset%20Properties%20Dialog%20Box,%20Query.md) .  
  
 Dispone de tres tipos de consultas:  
  
-   El tipo**Text** admite texto de consultas estándar de [!INCLUDE[tsql](../../includes/tsql-md.md)] para orígenes de datos de bases de datos relacionales, incluidas las extensiones de procesamiento de datos para [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y Oracle.  
  
-   El tipo**TableDirect** selecciona todas las columnas de la tabla especificada. Por ejemplo, para una tabla denominada Customers, éste es el equivalente de la instrucción `SELECT * FROM Customers` de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   El tipo**StoredProcedure** admite llamadas a procedimientos almacenados en el origen de datos. Para usar esta opción, el administrador de la base de datos debe haberle concedido permiso de ejecución en el procedimiento almacenado para el origen de datos.  
  
 El tipo de comando predeterminado es **Text**.  
  
> [!NOTE]  
>  No todas las extensiones de procesamiento de datos admiten todos los tipos. El proveedor de datos subyacentes debe admitir un tipo de comando antes de que la opción esté disponible.  
  
### Tipo de comando Text  
 En el tipo **Text** , el diseñador gráfico de consultas presenta cuatro áreas o paneles. En una consulta de [!INCLUDE[tsql](../../includes/tsql-md.md)] , puede especificar columnas, alias, valores de ordenación y valores de filtro. Asimismo, puede ver el texto de consulta generado a partir de las selecciones, ejecutar la consulta y ver el conjunto de resultados. La figura siguiente muestra los cuatro paneles.  
  
 ![Diseñador gráfico de consultas para consultas SQL](../../reporting-services/report-data/media/rsqd-dsaw-sql.gif "Diseñador gráfico de consultas para consultas SQL")  
  
 En la siguiente tabla se describe la función de cada panel.  
  
|Panel|Función|  
|----------|--------------|  
|Diagrama|Muestra las representaciones gráficas de las tablas de la consulta. Utilice este panel para seleccionar campos y definir relaciones entre tablas.|  
|Cuadrícula|Muestra una lista de los campos devueltos por la consulta. Use este panel para definir alias, criterios de ordenación, filtros, grupos y parámetros.|  
|SQL|Muestra la consulta de [!INCLUDE[tsql](../../includes/tsql-md.md)] representada mediante los paneles de diagrama y de cuadrícula. Use este panel para escribir o actualizar una consulta mediante [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
|Resultado|Muestra los resultados de la consulta. Para ejecutar la consulta, haga clic con el botón derecho en cualquier panel y, después, haga clic en **Ejecutar**, o bien haga clic en el botón **Ejecutar** en la barra de herramientas.|  
  
 Si cambia información en cualquiera de los tres primeros paneles, dichos cambios aparecerán en los demás paneles. Por ejemplo, si agrega una tabla en el panel Diagrama, ésta se agregará automáticamente a la consulta de [!INCLUDE[tsql](../../includes/tsql-md.md)] del panel de SQL. Si se agrega un campo a la consulta del panel de SQL, se agrega automáticamente el campo a la lista del panel Cuadrícula y se actualiza la tabla del panel Diagrama.  
  
 Para más información, vea [Herramientas Diseñador de consultas y vistas &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md).  
  
#### Barra de herramientas del diseñador gráfico de consultas  
 La barra de herramientas del diseñador gráfico de consultas proporciona botones que le ayudan a diseñar consultas de [!INCLUDE[tsql](../../includes/tsql-md.md)] mediante la interfaz gráfica.  
  
|Botón|Description|  
|------------|-----------------|  
|**Editar como texto**|Alterna entre el diseñador de consultas basado en texto y el diseñador gráfico de consultas.|  
|**Importar**|Importe una consulta existente de un archivo o informe. Solo se admiten los tipos de archivos .sql y .rdl. Para más información, vea [Conjuntos de datos incrustados y compartidos de informe &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).|  
|![Botón de alternancia Mostrar u ocultar panel de diagrama](../../reporting-services/report-data/media/rsqdicon-showhidediagram.png "Botón de alternancia Mostrar u ocultar panel de diagrama")|Muestra u oculta el panel Diagrama.|  
|![Botón de alternancia Mostrar u ocultar panel de cuadrícula](../../reporting-services/report-data/media/rsqdicon-showhidegrid.png "Botón de alternancia Mostrar u ocultar panel de cuadrícula")|Muestra u oculta el panel Cuadrícula.|  
|![Botón de alternancia Mostrar u ocultar panel de SQL](../../reporting-services/report-data/media/rsqdicon-showhidesql.png "Botón de alternancia Mostrar u ocultar panel de SQL")|Muestra u oculta el panel de SQL.|  
|![Botón de alternancia Mostrar u ocultar panel de resultados](../../reporting-services/report-data/media/rsqdicon-showhideresult.png "Botón de alternancia Mostrar u ocultar panel de resultados")|Muestra u oculta el panel Resultado.|  
|![Ejecutar la consulta](../../reporting-services/report-data/media/rsqdicon-run.png "Ejecutar la consulta")|Ejecuta la consulta.|  
|![Botón Comprobar SQL en el panel de SQL](../../reporting-services/report-data/media/rsqdicon-verifysql.png "Botón Comprobar SQL en el panel de SQL")|Comprueba que la sintaxis del texto de consulta sea correcta.|  
|![Establecer orden ascendente en el campo seleccionado](../../reporting-services/report-data/media/rsqdicon-sortascending.png "Establecer orden ascendente en el campo seleccionado")|Establece el criterio de ordenación en **Orden ascendente** para la columna seleccionada en el panel Diagrama.|  
|![Establecer orden descendente en el campo seleccionado](../../reporting-services/report-data/media/rsqdicon-sortdescending.png "Establecer orden descendente en el campo seleccionado")|Establece el criterio de ordenación en **Orden descendente** para la columna seleccionada en el panel Diagrama.|  
|![Quitar filtro del campo seleccionado](../../reporting-services/report-data/media/rsqdicon-removefilter.png "Quitar filtro del campo seleccionado")|Quita el filtro de la columna seleccionada en el panel Diagrama que está marcada como poseedora de filtro (![Gráfico de filtro junto a la columna de filtro seleccionada](../../reporting-services/report-data/media/rsqdicon-filter.png "Gráfico de filtro junto a la columna de filtro seleccionada")).|  
|![Usar Agrupar por para el campo seleccionado](../../reporting-services/report-data/media/rsqdicon-usegroupby.png "Usar Agrupar por para el campo seleccionado")|Muestra u oculta la columna **Agrupar por** en el panel Cuadrícula. Cuando el botón de alternancia **Agrupar por** está activado, aparece una columna adicional llamada **Agrupar por** en el panel Cuadrícula; cada valor de las columnas seleccionadas de la consulta tiene el valor predeterminado **Agrupar por**, que hace que la columna seleccionada se incluya en una cláusula GROUP BY del texto SQL. Utilice el botón Agrupar por para agregar automáticamente una cláusula GROUP BY que incluya todas las columnas en la cláusula SELECT. Cuando la cláusula SELECT incluya llamadas de función de agregado (por ejemplo, SUM(nombreDeColumna)), incluya cada columna que no sea de agregado en la cláusula GROUP BY si desea que aparezca en el conjunto de resultados.<br /><br /> Para que aparezca en el panel Resultado, cada columna de la consulta debe tener una función de agregado definida para utilizarse en el cálculo del valor que se mostrará en dicho panel. De lo contrario, la columna de la consulta debe especificarse en la cláusula GROUP BY de la consulta SQL.|  
|![Agregar una nueva tabla al panel de diagrama](../../reporting-services/report-data/media/rsqdicon-addtable.png "Agregar una nueva tabla al panel de diagrama")|Agrega una nueva tabla del origen de datos al panel Diagrama.<br /><br /> **Nota** Cuando agrega una nueva tabla, el diseñador de consultas intenta hacer que coincidan las relaciones de clave externa del origen de datos. Después de agregar una tabla, confirme que las relaciones de clave externa, representadas por los vínculos entre las tablas, sean correctas.|  
  
#### Ejemplo  
 La siguiente consulta devuelve la lista de apellidos de la tabla [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] Person **de la base de datos** :  
  
```  
SELECT LastName FROM Person.Person;  
```  
  
 También puede ejecutar procedimientos almacenados desde el panel de SQL. La siguiente consulta ejecuta el procedimiento almacenado **uspGetWhereUsedProductID** de la base de datos [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] :  
  
```  
EXEC uspGetEmployeeManagers '1';  
```  
  
### Tipo de comando TableDirect  
 En el tipo **TableDirect**, el diseñador gráfico de consultas muestra una lista desplegable de las tablas disponibles del origen de datos y el panel Resultado. Si selecciona una tabla y hace clic en el botón **Ejecutar** , se devolverán todas las columnas de dicha tabla.  
  
> [!NOTE]  
>  la característica TableDirect solo es compatible con los tipos de orígenes de datos **OLE DB** y **ODBC**.  
  
 En la siguiente tabla se describe la función de cada panel.  
  
|Panel|Función|  
|----------|--------------|  
|Lista desplegable de tablas|Muestra todas las tablas disponibles del origen de datos. Seleccione uno de la lista para activarlo.|  
|Resultado|Muestra todas las columnas de la tabla seleccionada. Para ejecutar la consulta de tabla, haga clic en el botón **Ejecutar** de la barra de herramientas.|  
  
#### Botones de la barra de herramientas del tipo de comando TableDirect  
 La barra de herramientas del diseñador gráfico de consultas proporciona una lista desplegable de tablas en el origen de datos. La tabla siguiente contiene una lista con todos los botones y sus funciones.  
  
|Botón|Description|  
|------------|-----------------|  
|**Editar como texto**|Alterna entre el diseñador de consultas basado en texto y el diseñador gráfico de consultas.|  
|**Importar**|Importe una consulta existente de un archivo o informe. Solo se admiten los tipos de archivos .sql y .rdl. Para más información, vea [Conjuntos de datos incrustados y compartidos de informe &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).|  
|![Icono del botón Diseñador de consultas genérico](../../reporting-services/report-data/media/icongenericquerydesigner.png "Icono del botón Diseñador de consultas genérico")|Alterna el diseñador de consultas genérico y el diseñador gráfico de consultas, a la vez que mantiene el texto de consulta o la vista del procedimiento almacenado.|  
|![Ejecutar la consulta](../../reporting-services/report-data/media/rsqdicon-run.png "Ejecutar la consulta")|Selecciona todas las columnas de la tabla seleccionada.|  
  
### Tipo de comando StoredProcedure  
 En el tipo **StoredProcedure**, el diseñador gráfico de consultas muestra una lista desplegable de los procedimientos almacenados disponibles del origen de datos y el panel Resultado. En la siguiente tabla se describe la función de cada panel.  
  
|Panel|Función|  
|----------|--------------|  
|Lista desplegable de procedimientos almacenados|Muestra todos los procedimientos almacenados disponibles del origen de datos. Seleccione uno de la lista para activarlo.|  
|Resultado|Muestra el resultado de la ejecución del procedimiento almacenado. Para ejecutar el procedimiento almacenado seleccionado, haga clic en el botón **Ejecutar** de la barra de herramientas.|  
  
#### Botones de la barra de herramientas del tipo de comando StoredProcedure  
 La barra de herramientas del diseñador gráfico de consultas proporciona una lista desplegable de procedimientos almacenados en el origen de datos. La tabla siguiente contiene una lista con todos los botones y sus funciones.  
  
|Botón|Description|  
|------------|-----------------|  
|**Editar como texto**|Alterna entre el diseñador de consultas basado en texto y el diseñador gráfico de consultas.|  
|**Importar**|Importe una consulta existente de un archivo o informe. Solo se admiten los tipos de archivos .sql y .rdl. Para más información, vea [Conjuntos de datos incrustados y compartidos de informe &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).|  
|![Ejecutar la consulta](../../reporting-services/report-data/media/rsqdicon-run.png "Ejecutar la consulta")|Ejecuta el procedimiento almacenado.|  
|Lista desplegable de procedimientos almacenados|Haga clic en la flecha abajo para mostrar una lista de procedimientos almacenados disponibles del origen de datos. Haga clic en un procedimiento almacenado de la lista para seleccionarlo.|  
  
#### Ejemplo  
 El siguiente procedimiento almacenado llama a una lista de cargos de los administradores de la base de datos [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Este procedimiento almacenado acepta *BusinessEntityID* como parámetro. Puede especificar un entero pequeño.  
  
 `uspGetEmployeeManagers '1';`  
  
## Vea también  
 [Herramientas de diseño de consulta &#40;SSRS&#41;](../../reporting-services/report-data/query-design-tools-ssrs.md)   
 [Conjuntos de datos de informe &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [Tipo de conexión de SQL Server &#40;SSRS&#41;](../../reporting-services/report-data/sql-server-connection-type-ssrs.md)   
 [Tipo de conexión OLE DB &#40;SSRS&#41;](../../reporting-services/report-data/ole-db-connection-type-ssrs.md)   
 [Conjuntos de datos de informe &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [Tipo de conexión de Oracle &#40;SSRS&#41;](../../reporting-services/report-data/oracle-connection-type-ssrs.md)   
 [Archivo de configuración RSReportDesigner](../../reporting-services/report-server/rsreportdesigner-configuration-file.md)   
 [Temas de procedimientos de diseño de consultas y vistas &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  