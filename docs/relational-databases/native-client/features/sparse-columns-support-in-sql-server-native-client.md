---
title: Compatibilidad con columnas dispersas en SQL Server Native Client | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sparse columns, ODBC
- sparse columns, SQL Server Native Client
- sparse columns, OLE DB
ms.assetid: aee5ed81-7e23-42e4-92d3-2da7844d9bc3
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4754553f3ceaab83497287f613fa18c5b324c4b3
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37432634"
---
# <a name="sparse-columns-support-in-sql-server-native-client"></a>Compatibilidad con columnas dispersas en SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client admite las columnas dispersas. Para obtener más información sobre las columnas dispersas en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], consulte [usar columnas dispersas](../../../relational-databases/tables/use-sparse-columns.md) y [usar conjuntos de columnas](../../../relational-databases/tables/use-column-sets.md).  
  
 Para obtener más información sobre columnas dispersas compatibilidad en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, vea [las columnas dispersas admiten &#40;ODBC&#41; ](../../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md) y [las columnas dispersas admiten &#40;OLE DB&#41; ](../../../relational-databases/native-client/ole-db/sparse-columns-support-ole-db.md) .  
  
 Para obtener información acerca de las aplicaciones de ejemplo que muestran esta característica, consulte [ejemplos de programación de datos de SQL Server](http://msftdpprodsamples.codeplex.com/).  
  
## <a name="user-scenarios-for-sparse-columns-and-sql-server-native-client"></a>Escenarios de usuarios de columnas dispersas y SQL Server Native Client  
 En la tabla siguiente se resumen los escenarios comunes de usuario para los usuarios de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client con columnas dispersas:  
  
|Escenario|Comportamiento|  
|--------------|--------------|  
|**Seleccione \* desde tabla** o IOpenRowset:: OpenRowset.|Devuelve todas las columnas que no son miembros de disperso **column_set**, más una columna XML que contiene los valores de todas las columnas no nulas que son miembros de disperso **column_set**.|  
|Hacer referencia a una columna por nombre.|Se puede hacer referencia a la columna independientemente de su estado de la columna dispersa o **column_set** pertenencia.|  
|Acceso **column_set** columnas de miembros a través de una columna XML calculada.|Las columnas que son miembros de disperso **column_set** puede obtenerse mediante la selección del **column_set** por su nombre y pueden tener valores insertan y actualizan al actualizar el XML en el **column_set** columna.<br /><br /> El valor debe ajustarse al esquema de **column_set** columnas.|  
|Recuperar metadatos para todas las columnas de una tabla a través de SQLColumns con un patrón de búsqueda de la columna de NULL o '%' (ODBC); o a través del conjunto de filas de esquema DBSCHEMA_COLUMNS sin restricciones de columna (OLE DB).|Devuelve una fila para todas las columnas que no son miembros de un **column_set**. Si la tabla tiene un dispersas **column_set**, se devolverá una fila para él.<br /><br /> Tenga en cuenta que esto no devuelve metadatos para las columnas que son miembros de un **column_set**.|  
|Recuperar metadatos para todas las columnas, independientemente de la dispersión o la pertenencia a un **column_set**. Esto podría devolver un número muy grande de filas.|Establezca el campo de descriptor SQL_SOPT_SS_NAME_SCOPE en SQL_SS_NAME_SCOPE_EXTENDED y llame a [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md) (ODBC).<br /><br /> Llame a IDBSchemaRowset:: GetRowset para el conjunto de filas de esquema DBSCHEMA_COLUMNS_EXTENDED (OLE DB).<br /><br /> Este escenario no es posible en una aplicación que utiliza [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client en una versión anterior a [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Sin embargo, este tipo de aplicación podría consultar directamente las vistas del sistema.|  
|Recuperar metadatos solo para las columnas que son miembros de un **column_set**. Esto podría devolver un número muy grande de filas.|Establezca el campo de descriptor SQL_SOPT_SS_NAME_SCOPE en SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET y llamar a SQLColumns (ODBC).<br /><br /> Llame a IDBSchemaRowset:: GetRowset para el conjunto de filas de esquema DBSCHEMA_SPARSE_COLUMN_SET (OLE DB).<br /><br /> Este escenario no es posible en una aplicación que utiliza [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client en una versión anterior a [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Sin embargo, este tipo de aplicación podría consultar las vistas del sistema.|  
|Determinar si una columna es dispersa.|Consulte la columna SS_IS_SPARSE del conjunto de resultados SQLColumns (ODBC).<br /><br /> Consulte la columna SS_IS_SPARSE del conjunto de filas de esquema DBSCHEMA_COLUMNS (OLE DB).<br /><br /> Este escenario no es posible en una aplicación que utiliza [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client en una versión anterior a [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Sin embargo, este tipo de aplicación podría consultar las vistas del sistema.|  
|Determinar si una columna es una **column_set**.|Consulte la columna SS_IS_COLUMN_SET del conjunto de resultados SQLColumns. O bien, consulte el atributo de columna SQL_CA_SS_IS_COLUMN_SET específico de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (ODBC).<br /><br /> Consulte la columna SS_IS_COLUMN_SET del conjunto de filas de esquema DBSCHEMA_COLUMNS. O bien, consulte *dwFlags* devueltos por IColumnsInfo:: GetColumnInfo o DBCOLUMNFLAGS del conjunto de filas devuelto por IColumnsRowset:: GetColumnsRowset. Para **column_set** columnas, establecerá DBCOLUMNFLAGS_SS_ISCOLUMNSET (OLE DB).<br /><br /> Este escenario no es posible en una aplicación que utiliza [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client en una versión anterior a [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Sin embargo, este tipo de aplicación podría consultar las vistas del sistema.|  
|Importar y exportar columnas dispersas en BCP de una tabla sin **column_set**.|Ningún cambio en el comportamiento desde las versiones anteriores de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|Importar y exportar columnas dispersas en BCP de una tabla con un **column_set**.|El **column_set** se importa y exporta de la misma manera que XML; es decir, como **varbinary (max)** si enlaza como un tipo binario, o como **nvarchar (max)** si han vinculado como un **char** o **wchar** tipo.<br /><br /> Las columnas que son miembros de disperso **column_set** no se exportan como columnas distintas; solo se exportan en el valor de la **column_set**.|  
|**Queryout** comportamiento para BCP.|Ningún cambio en el tratamiento de columnas nombradas explícitamente desde las versiones anteriores de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.<br /><br /> Los escenarios que implican la importación y exportación entre tablas con esquemas diferentes pueden requerir un tratamiento especial.<br /><br /> Para obtener más información acerca de BCP, vea Compatibilidad de la copia masiva (BCP) con columnas dispersas, más adelante en este tema.|  
  
## <a name="down-level-client-behavior"></a>Comportamiento del cliente de nivel inferior  
 Los clientes de nivel inferior devolverán los metadatos solo para las columnas que no son miembros de disperso **column_set** para SQLColumns y DBSCHMA_COLUMNS. Las filas de esquema OLE DB adicionales introducidos en [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client no estarán disponible, ni tampoco las modificaciones de SQLColumns de ODBC a través de SQL_SOPT_SS_NAME_SCOPE.  
  
 Los clientes de nivel inferior pueden tener acceso a las columnas que son miembros de disperso **column_set** por nombre y el **column_set** columna será accesible como una columna XML para [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] los clientes.  
  
## <a name="bulk-copy-bcp-support-for-sparse-columns"></a>Compatibilidad de la copia masiva (BCP) con columnas dispersas  
 No hay ningún cambio en la API de BCP en ODBC u OLE DB para las columnas dispersas o **column_set** características.  
  
 Si una tabla tiene un **column_set**, las columnas dispersas no se tratan como columnas distintas. Los valores de todas las columnas dispersas están incluidos en el valor de la **column_set**, que se exporta de la misma manera que una columna XML; es decir, como **varbinary (max)** si enlaza como un tipo binario, o como  **nvarchar (max)** si han vinculado como un **char** o **wchar** tipo). En la importación, el **column_set** valor debe ajustarse al esquema de la **column_set**.  
  
 Para **queryout** operaciones, no hay ningún cambio en el tratamiento de las columnas de forma explícita que se hace referencia. **COLUMN_SET** columnas tienen el mismo comportamiento que las columnas XML y dispersión no tiene ningún efecto en el tratamiento de las columnas dispersas indicadas.  
  
 Sin embargo, si **queryout** se usa para la exportación y hace referencia a columnas dispersas que son miembros de la columna dispersa establecida por su nombre, no se puede realizar una importación directa en una tabla con estructura similar. Esto es porque BCP utiliza metadatos coherentes con un **seleccione \***  operación para la importación y no se puede hacer coincidir **column_set** columnas de miembros con estos metadatos. Para importar **column_set** columnas miembro individualmente, debe definir una vista en la tabla que hace referencia a deseado **column_set** columnas y se debe realizar la operación de importación con la vista.  
  
## <a name="see-also"></a>Vea también  
 [Programación de SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  
