---
title: Compatibilidad con columnas dispersas (OLE DB) | Documentos de Microsoft
description: Compatibilidad con columnas dispersas (OLE DB)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 5acd9fc1a368f9f7701468887263129495b046e1
ms.sourcegitcommit: 354ed9c8fac7014adb0d752518a91d8c86cdce81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/14/2018
ms.locfileid: "35611930"
---
# <a name="sparse-columns-support-ole-db"></a>Compatibilidad con columnas dispersas (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Este tema proporciona información sobre el controlador OLE DB para SQL Server admiten columnas dispersas. Para obtener más información sobre las columnas dispersas, vea [Sparse Columns Support in controlador OLE DB para SQL Server](../../oledb/features/sparse-columns-support-in-oledb-driver-for-sql-server.md). Para obtener un ejemplo, vea [columna de presentación y los metadatos de catálogo para columnas dispersas &#40;OLE DB&#41;](../../oledb/ole-db-how-to/display-column-and-catalog-metadata-for-sparse-columns-ole-db.md).  
  
## <a name="ole-db-statement-metadata"></a>Metadatos de instrucción OLE DB  
 A partir de [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], está disponible un nuevo valor de marca DBCOLUMNFLAGS, DBCOLUMNFLAGS_SS_ISCOLUMNSET. Este valor debe establecerse para columnas que son **column_set** valores. La marca DBCOLUMNFLAGS se puede recuperar mediante el *dwFlags* parámetro de IColumnsInfo:: GetColumnsInfo y la columna DBCOLUMN_FLAGS del conjunto de filas devuelto por IColumnsRowset:: GetColumnsRowset.  
  
## <a name="ole-db-catalog-metadata"></a>Metadatos de catálogo OLE DB  
 Se han agregado dos columnas adicionales específicas de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a DBSCHEMA_COLUMNS.  
  
|Nombre de columna|Tipo de datos|Valor/comentarios|  
|-----------------|---------------|---------------------|  
|SS_IS_SPARSE|DBTYPE_BOOL|Si la columna es una columna dispersa, esto tiene el valor VARIANT_TRUE; de lo contrario, VARIANT_FALSE.|  
|SS_IS_COLUMN_SET|DBTYPE_BOOL|Si la columna es disperso **column_set** columna, esto tiene el valor VARIANT_TRUE; de lo contrario, VARIANT_FALSE.|  
  
 También se han agregado dos conjuntos de filas de esquema adicionales. Estos conjuntos de filas tienen la misma estructura que DBSCHEMA_COLUMNS pero devuelven contenido diferente. DBSCHEMA_COLUMNS_EXTENDED devuelve todas las columnas con independencia de **column_set** pertenencia. DBSCHEMA_SPARSE_COLUMN_SET únicamente devuelve columnas que son miembros de disperso **column_set**.  
  
## <a name="ole-db-datatypecompatibility-behavior"></a>Comportamiento de OLE DB DataTypeCompatibility  
 Comportamiento con **DataTypeCompatibility = 80** (en la cadena de conexión) es coherente con un [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] cliente, como se indica a continuación:  
  
-   Los nuevos conjuntos de filas de esquema no están visibles y no hay ninguna fila para ellos en el conjunto de filas de conjuntos de filas de esquema.  
  
-   Las columnas nuevas en el conjunto de filas COLUMNS no están visibles.  
  
-   DBCOLUMNFLAGS_SS_ISCOLUMNSET no está establecido para **column_set** columnas.  
  
-   DBCOMPUTEMODE_NOTCOMPUTED está establecido para **column_set** columnas.  
  
## <a name="ole-db-support-for-sparse-columns"></a>Compatibilidad de OLE DB con columnas dispersas  
 Las siguientes interfaces OLE DB se han modificado en el controlador OLE DB para SQL Server admitir columnas dispersas:  
  
|Tipo o función de miembro|Descripción|  
|-----------------------------|-----------------|  
|IColumnsInfo::GetColumnsInfo|DBCOLUMNFLAGS_SS_ISCOLUMNSET está establecido para el valor de marca de una nueva DBCOLUMNFLAGS **column_set** columnas en *dwFlags*.<br /><br /> DBCOLUMNFLAGS_WRITE está establecido para **column_set** columnas.|  
|IColumsRowset::GetColumnsRowset|Un nuevo valor de marca DBCOLUMNFLAGS, DBCOLUMNFLAGS_SS_ISCOLUMNSET, está establecido para **column_set** columnas en DBCOLUMN_FLAGS.<br /><br /> DBCOLUMN_COMPUTEMODE está establecido en dbcomputemode_dynamic para las **column_set** columnas.|  
|IDBSchemaRowset::GetSchemaRowset|DBSCHEMA_COLUMNS devuelve dos nuevas columnas: SS_IS_COLUMN_SET y SS_IS_SPARSE.<br /><br /> DBSCHEMA_COLUMNS únicamente devuelve columnas que no son miembros de un **column_set**.<br /><br /> Se han agregado dos nuevos conjuntos de filas de esquema: DBSCHEMA_COLUMNS_EXTENDED devolverá todas las columnas independientemente de la dispersión de **column_set** pertenencia. DBSCHEMA_SPARSE_COLUMN_SET únicamente devuelve columnas que son miembros de un **column_set**. Estos nuevos conjuntos de filas tienen las mismas columnas y restricciones que DBSCHEMA_COLUMNS.|  
|IDBSchemaRowset::GetSchemas|IDBSchemaRowset:: GetSchemas incluye los GUID de los nuevos conjuntos de filas DBSCHEMA_COLUMNS_EXTENDED y DBSCHEMA_SPARSE_COLUMN_SET en la lista de conjuntos de filas de esquema disponibles.|  
|ICommand::Execute|Si **seleccione \* de** *tabla* es utilizada, devuelve todas las columnas que no son miembros de disperso **column_set**, más una columna XML que contiene los valores de todos los las columnas no nulas que son miembros de disperso **column_set**, si está presente.|  
|IOpenRowset::OpenRowset|IOpenRowset:: OpenRowset devuelve un conjunto de filas con las mismas columnas que ICommand:: Execute, con un **seleccione \***  consulta en la misma tabla.|  
|ITableDefinition|No hay ningún cambio en esta interfaz para las columnas dispersas o para **column_set** columnas. Las aplicaciones que tienen que realizar modificaciones de esquema deben ejecutar directamente el [!INCLUDE[tsql](../../../includes/tsql-md.md)] adecuado.|  
  
## <a name="see-also"></a>Vea también  
 [Programación del controlador OLE DB para SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
