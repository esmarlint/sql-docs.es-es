---
title: "Importar dominios desde un archivo de Excel a la detecci&#243;n del conocimiento | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4d3a3940-6c2a-4dc4-90eb-86f26012c165
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# Importar dominios desde un archivo de Excel a la detecci&#243;n del conocimiento
  En este tema se describe cómo importar uno o varios dominios desde un archivo de Excel a la actividad de detección de conocimiento de [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). El proceso de importación simplifica el proceso de generación del conocimiento, lo que permite ahorrar tiempo y esfuerzo. Permite a los usuarios que disponen de datos en un archivo de Excel o un archivo de texto crear una base de conocimiento con dichos datos. (Consulte [Importar valores desde un archivo de Excel en un dominio](../data-quality-services/import-values-from-an-excel-file-into-a-domain.md) para obtener más información sobre cómo importar valores en un dominio de una base de conocimiento existente.) No se admite la exportación a un archivo Excel.  
  
##  <a name="BeforeYouBegin"></a> Antes de empezar  
  
###  <a name="Prerequisites"></a> Requisitos previos  
 Para importar dominios desde un archivo de Excel, Excel debe instalarse en el equipo que el [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] está instalado; debe haber creado un archivo de Excel con valores de dominio (consulte [cómo funciona la importación](#How)); y debe haber creado y abierto una base de conocimiento para importar el dominio.  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 Debe disponer del rol dqs_kb_editor o dqs_administrator en la base de datos DQS_MAIN para poder importar dominios desde un archivo de Excel.  
  
##  <a name="Import"></a> Importar dominios desde un archivo de Excel a una base de conocimiento  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Ejecute la aplicación de cliente de calidad de datos](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  En la página de inicio de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , siga uno de estos procedimientos:  
  
    -   Cree una nueva base de conocimiento en la que realizar la importación; para ello, haga clic en **Nueva base de conocimiento**, escriba un nombre para la base de conocimiento, seleccione **Ninguno** para **Crear base de conocimiento a partir de**, seleccione la actividad **Detección de conocimiento** y, a continuación, haga clic en **Crear**.  
  
    -   Abra una base de conocimiento existente en la que realizar la importación; para ello, haga clic en **Abrir base de conocimiento**, seleccione la base de conocimiento, seleccione **Detección de conocimiento**y, a continuación, haga clic en **Siguiente**.  
  
3.  En la página **Asignación** , seleccione **Archivo de Excel** en **Origen de datos**.  
  
4.  Haga clic en **Examinar** en la línea **Archivo de Excel** .  
  
5.  En el cuadro de diálogo **Seleccione un archivo de Excel** , desplácese a la carpeta que contiene el archivo de Excel desde el que desea realizar la importación, seleccione dicho archivo y, a continuación, haga clic en **Abrir**.  
  
6.  Desde el **hoja de cálculo** lista desplegable, seleccione la hoja de cálculo en el archivo de Excel que desea importar.  
  
7.  Seleccione **Usar la primera fila como encabezado** si desea que la primera fila se considere como un encabezado de datos, y si desea que los valores de la primera fila se utilicen como nombres de columna. Anule la selección de **Usar primera fila como encabezado** Si desea que la primera fila se considere un valor de datos, en cuyo caso DQS utilizará los nombres de encabezado de Excel (letras en orden alfabético) para la columna.  
  
8.  Seleccione una columna y asígnela un dominio existente, o bien cree un nuevo dominio haciendo clic en el icono **Crear un dominio** , utilice el cuadro de diálogo **Crear un dominio** para crearlo y, a continuación, asígnelo a la columna. El tipo de datos del dominio debe coincidir con el tipo de datos de la columna. Repita el proceso para todas las columnas de la hoja de cálculo.  
  
9. Haga clic en **Siguiente**.  
  
10. En la página **Detectar** , haga clic en **Iniciar** para analizar los datos de la hoja de cálculo de Excel.  
  
    > [!NOTE]  
    >  Si abandona la página antes de que se hayan cargado los datos, el proceso de carga de archivos terminará.  
  
11. Compruebe que el análisis se ha realizado correctamente y, a continuación, haga clic en **Siguiente**.  
  
12. En la página **Administrar valores del dominio** , compruebe que aparecen los dominios correctos en la lista **Dominios** y que la tabla de dominios contiene valores.  
  
13. Haga clic en **Finalizar**y, a continuación, haga clic en **Publicar** para publicar la base de conocimiento, o en **No** para no publicarla.  
  
14. Compruebe que la base de conocimiento se ha publicado y haga clic en **Aceptar**.  
  
##  <a name="FollowUp"></a> Seguimiento: después de importar dominios desde un archivo de Excel  
 Después de importar dominios desde un archivo de Excel, puede agregar conocimiento a dichos dominios o utilizarlos en un proyecto de limpieza o de búsqueda de coincidencias, en función del contenido de los dominios. Para obtener más información, consulte [realizar la detección de conocimiento](../data-quality-services/perform-knowledge-discovery.md), [administrar un dominio](../data-quality-services/managing-a-domain.md), [administrar un dominio compuesto](../data-quality-services/managing-a-composite-domain.md), [crear una directiva de coincidencia](../data-quality-services/create-a-matching-policy.md), [la limpieza de datos](../data-quality-services/data-cleansing.md), o [coincidencia de datos](../data-quality-services/data-matching.md).  
  
##  <a name="How"></a> Cómo funciona la importación  
 En la operación de importación, DQS interpreta un archivo de Excel de la manera siguiente:  
  
-   Una columna representa un dominio  
  
-   Una fila representa un registro de datos  
  
-   La primera fila puede representar los nombres de dominio o el primer valor o registro de datos, dependiendo del valor de la casilla **Usar la primera fila como encabezado** .  
  
 Se aplican las reglas siguientes a la operación de importación:  
  
-   Esta operación importa valores de dominio en una base de conocimiento. No importa reglas de dominio ni directivas de coincidencia.  
  
-   El archivo de Excel puede tener la extensión .xlsx, .xls o .csv. Es necesario tener instalado Microsoft Excel en el equipo de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] para poder importar valores de dominio o un dominio completo. Se admiten las versiones 2003 y posteriores de Excel. Si se utiliza la versión de 64 bits de Excel, solo se admitirán los archivos de Excel 2003; los archivos de Excel 2007 o 2010 no son compatibles.  
  
-   Los archivos de Excel de tipo .xlsx no se admiten en una instalación de 64 bits de Excel. Si utiliza Excel de 64 bits, guarde el archivo de hoja de cálculo como un archivo .xls.  
  
-   En los archivos .xlsx y .xls, el tipo de datos de la columna está determinado por el tipo de datos más frecuente de las ocho primeras filas. Si una celda no se ajusta a dicho tipo de datos, se le asignará un valor NULL.  
  
-   En los archivos .csv, el tipo de datos está determinado por el tipo de datos más frecuente de las ocho primeras filas.  
  
-   Los valores de una hoja de cálculo de Excel que no se ajusten a una regla de dominio se importarán como valores no válidos.  
  
-   Si el archivo de Excel no tiene el formato correcto o está dañado, la operación de importación generará un error.  
  
  