---
title: "Cambiar valores de dominio | Microsoft Docs"
ms.custom: ""
ms.date: "11/08/2011"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dqs.dm.values.f1"
ms.assetid: 8c90ab70-3aea-4eaf-a174-4159485c87d3
caps.latest.revision: 31
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 31
---
# Cambiar valores de dominio
  En este tema se describe cómo cambiar y aumentar los metadatos de una base de conocimiento de [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Una vez que haya generado conocimiento mediante la detección de conocimiento, haya importado conocimiento en la base de conocimiento o en los dominios, o haya basado una base de conocimiento en otra, podrá cambiar los valores de los datos de forma interactiva. La generación de la base de conocimiento no solo aprovecha los procesos asistidos por PC, sino que además pone a su disposición los medios necesarios para que pueda usar su propio conocimiento para comprobar los valores de los datos y cambiarlos de las formas siguientes:  
  
-   Agregar un valor de dominio a la lista de valores, o seleccionar un valor y eliminarlo de la lista  
  
-   Cambiar a correcto, erróneo o no válido el estado asignado a un valor de dominio por el proceso de detección de DQS  
  
-   Especificar un valor de reemplazo para un valor erróneo o no válido. Un valor no es válido si no pertenece al dominio; por ejemplo, si no se ajusta al tipo de datos del dominio o provoca un error en una regla de dominio. Un valor es erróneo si pertenece al dominio, pero tiene un error de sintaxis.  
  
-   Establecer dos o más valores como sinónimos y cambiar el valor inicial definido por el proceso de detección, con lo que el valor inicial reemplazará el valor del sinónimo si se estableció la propiedad **Usar valores iniciales** al crear el dominio  
  
-   Importar valores de dominio desde un archivo de Excel  
  
##  <a name="BeforeYouBegin"></a> Antes de empezar  
  
###  <a name="Prerequisites"></a> Requisitos previos  
 Para cambiar un valor de dominio, es necesario tener una base de conocimiento y un dominio abiertos en la actividad Administración de dominios.  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 Debe disponer del rol dqs_kb_editor o dqs_administrator en la base de datos DQS_MAIN para cambiar valores de dominio.  
  
##  <a name="Change"></a> Cambiar valores de dominio  
 La tabla **Valor** muestra el conocimiento agregado a la base de conocimiento para un dominio individual. Puede seleccionar otro dominio en la lista de dominios en cualquier momento para mostrar sus valores. Las columnas del campo son las siguientes:  
  
-   La columna **Valor** muestra todos los valores que el proceso de detección agregó al dominio seleccionado desde un campo de la muestra de datos. Cualquier valor proyectado como erróneo se mostrará como sinónimo de un valor proyectado como correcto.  
  
-   La columna **Tipo** muestra el estado del valor, tal como lo determina el proceso de detección. Una marca verde indica que el valor es correcto o se ha corregido; una cruz roja indica que el valor es erróneo; un triángulo naranja con un signo de exclamación indica que el valor no es válido. Un valor que no es válido no cumple los requisitos de los datos para el dominio. Un valor erróneo puede ser válido, pero no es el valor correcto a causa de los datos.  
  
-   La columna **Corregir a** muestra el valor correcto por el que se cambiará el valor original, marcado como erróneo o no válido. DQS puede proponer el valor correcto como resultado del proceso de detección.  
  
 Para cambiar valores, haga lo siguiente:  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Ejecute la aplicación de cliente de calidad de datos](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  En la página de inicio de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , abra o cree una base de conocimiento. Seleccione **Administración de dominios** como actividad y, a continuación, haga clic en **Abrir** o en **Crear**. Para obtener más información, consulte [Create a Knowledge Base](../data-quality-services/create-a-knowledge-base.md) o [Open a Knowledge Base](../data-quality-services/open-a-knowledge-base.md).  
  
    > [!NOTE]  
    >  La administración de dominios se realiza en una página del cliente de Data Quality Services que contiene cinco pestañas para distintas operaciones de administración de dominios. No se trata de un proceso controlado mediante asistentes; cada una de las operaciones de administración se puede realizar por separado.  
  
3.  En la **Lista de dominios** de la página **Administración de dominios** , seleccione el dominio cuyos valores desea cambiar o cree un nuevo dominio. Si necesita crear un nuevo dominio, vea [Create a Domain](../data-quality-services/create-a-domain.md). Haga clic en la pestaña **Valores del dominio** .  
  
4.  Muestre los valores que necesita modificar en la tabla **Valor** . Para obtener más información, vea [Cómo mostrar los valores adecuados](#Display) a continuación.  
  
5.  Para cambiar el estado de un valor, haga lo siguiente:  
  
    -   **Establecer como corregidos los valores de dominio seleccionados**: para cambiar el estado de un valor de Error o no válido a correcto, seleccione el valor y, a continuación, haga clic en el **establecer como corregidos seleccionados los valores de dominio** (comprobar) de la flecha hacia abajo en la barra de iconos o de la lista desplegable tipo. Si el valor erróneo o no válido está agrupado con un valor correcto, elimine ese valor después de la operación.  
  
    -   **Establecer los valores de dominio seleccionado como errores**: para cambiar el estado de un valor de correcto o no válido a Error, seleccione el valor y, a continuación, haga clic en el **establecer los valores de dominio seleccionados como errores** (cruz) icono de la flecha hacia abajo en la barra de iconos o de la lista desplegable tipo. Si lo desea, puede escribir una corrección en la columna **Corregir a** , o dejarla en blanco.  
  
    -   **Establecer los valores de dominio seleccionado como no válidos**: para cambiar el estado de un valor de correcto o Error es no válido, seleccione el valor y, a continuación, haga clic en el **establecer los valores de dominio seleccionados como no válidos** icono de (triángulo) de la flecha hacia abajo en la barra de iconos o de la lista desplegable tipo. Si lo desea, puede escribir una corrección en la columna **Corregir a** , o dejarla en blanco.  
  
    -   **Corregir a**: después de establecer un valor como erróneo o no válido, escriba un nuevo valor en la columna **Corregir a** . DQS agregará una nueva fila para el valor de reemplazo, lo designará como correcto y, a continuación, agrupará los dos valores. El nuevo valor se mostrará como el valor inicial, con el valor inicial en negrita y el valor erróneo o no válido con una sangría aplicada.  
  
6.  Para designar valores como un grupo de sinónimos, seleccione varios valores que sean correctos y haga lo siguiente:  
  
    -   **Establecer como sinónimos los valores de dominio seleccionados**: para establecer sinónimos, seleccione varios valores que sean correctos y, a continuación, haga clic en el icono **Establecer como sinónimos los valores de dominio seleccionados** . DQS agrupará los valores y designará uno de ellos como el valor inicial por el que se reemplazarán los demás valores. Tenga en cuenta que si se agrupan dos valores, pero uno de ellos es erróneo o no válido, los valores no son sinónimos.  
  
        > [!NOTE]  
        >  Si selecciona dos o más valores de un grupo y otro valor fuera de este y, a continuación, los establece como sinónimos, obtendrá un mensaje de error. Después de cerrar el cuadro emergente del mensaje de error, los valores se establecerán correctamente como sinónimos.  
  
    -   **Romper la relación entre los sinónimos seleccionados**: para deshacer la designación de sinónimos para dos o más valores, seleccione los valores y haga clic en el icono **Romper la relación entre los sinónimos seleccionados** . Para que la desagrupación de sinónimos funcione, los valores deben estar agrupados y ser correctos.  
  
    -   **Establecer el valor de dominio seleccionado como valor principal de su grupo**: para cambiar el valor inicial del grupo, seleccione un valor del grupo que no se haya designado como valor inicial y, a continuación, haga clic en el botón **Establecer el valor de dominio seleccionado como valor principal de su grupo** . De este modo, establecerá el valor inicial que sustituirá al otro valor. Esta operación solo funciona si tiene un grupo con dos o más valores y desea que el valor inicial sea uno distinto del valor designado por DQS. Tenga en cuenta que el valor inicial se muestra en negrita en una fila de color azul.  
  
7.  **Corrector ortográfico**: si un valor aparece subrayado con una línea ondulada de color rojo, significa que el corrector ortográfico está sugiriendo una corrección. Haga clic con el botón secundario en el valor subrayado y seleccione una corrección si es necesario. El tipo de valor se convierte en (o permanecerá como) error y la corrección se agregará a la **correcta de** columna. Haga clic en la flecha abajo para ver correcciones propuestas adicionales. Escriba manualmente una corrección para agregarla al diccionario del corrector ortográfico y poder seleccionarla como corrección. Para obtener más información, consulte [Use the DQS Speller](../data-quality-services/use-the-dqs-speller.md) y [Set Domain Properties](../data-quality-services/set-domain-properties.md).  
  
    > [!NOTE]  
    >  Para utilizar el corrector ortográfico, puede habilitar en la **Propiedades del dominio** página, o si está deshabilitado en el **Propiedades del dominio** página, puede hacer clic en el **Habilitar o deshabilitar el corrector ortográfico** situado en la **los valores de dominio** página para habilitar en la página.  
  
8.  **Agregar un nuevo valor de dominio**: haga clic aquí para agregar una fila al final de la tabla. Después de especificar un valor, la fila se volverá a colocar en orden alfabético e irá precedida por un símbolo de estrella.  
  
9. **Importar valores de dominio de Excel**: para agregar nuevos valores desde una hoja de cálculo de Excel, haga clic en la flecha abajo del icono **Importar valores** y, a continuación, seleccione **Importar valores de dominio de Excel**. Escriba el nombre del archivo, seleccione **Usar la primera fila como encabezado** si procede y, a continuación, haga clic en **Aceptar**. Para obtener más información, consulte [Import Values from an Excel File into a Domain](../data-quality-services/import-values-from-an-excel-file-into-a-domain.md).  
  
10. **Importar valores de proyecto**: para agregar nuevos valores desde un proyecto de calidad de datos, haga clic en la flecha abajo del icono **Importar valores** y, a continuación, seleccione **Importar valores de proyecto**. Escriba el nombre del archivo, seleccione **Usar la primera fila como encabezado** si procede y, a continuación, haga clic en **Aceptar**. Seleccione el proyecto del que desee importar los valores y, a continuación, haga clic en **Aceptar**. Se mostrarán los valores importados. Haga clic en **Finalizar**. Para obtener más información, vea Importar valores de un proyecto de limpieza en un dominio.  
  
11. **Eliminar los valores de dominio seleccionado**: para quitar uno o varios de los valores existentes en el dominio, seleccione los valores en la tabla valor y, a continuación, haga clic en el **eliminar los valores de dominio seleccionados** icono. Las entradas de DQS_NULL no se pueden eliminar, por lo que si opta por eliminar varios valores entre los que hay una de estas entradas, se producirá un error en la operación.  
  
12. Haga clic en **Finalizar** para finalizar la actividad de administración de dominios, tal como se describe en [End the Domain Management Activity](../Topic/End%20the%20Domain%20Management%20Activity.md).  
  
##  <a name="FollowUp"></a> Seguimiento: después de cambiar valores de dominio  
 Una vez cambiados los valores de dominio, puede realizar otras tareas de administración en el dominio, ejecutar la detección de conocimiento para agregar conocimiento al dominio o agregar a este una directiva de coincidencia. Para obtener más información, consulte [realizar la detección de conocimiento](../data-quality-services/perform-knowledge-discovery.md), [administrar un dominio](../data-quality-services/managing-a-domain.md), o [crear una directiva de coincidencia](../data-quality-services/create-a-matching-policy.md).  
  
##  <a name="Meaning"></a> El significado de los valores Correcto, Error y No válido  
 A cada valor de la tabla **Valor** de la página **Valores del dominio** se le asigna un **Tipo** : **Correcto**, **Error**o **No válido**. La actividad de detección de conocimiento es la que genera inicialmente el tipo del valor, y puede cambiarlo de acuerdo con sus necesidades. La actividad de limpieza es la que genera el tipo final, en función de los cambios interactivos y de detección. Estos valores tienen los significados siguientes:  
  
-   **Correcto:** es un valor que pertenece al dominio y no tiene ningún error de sintaxis. Por ejemplo, “Chicago” en un dominio City es un valor correcto.  
  
-   **Error:** es un valor que pertenece al dominio, pero es incorrecto. Por ejemplo, “Shicago” en lugar de “Chicago” en un dominio City es un valor erróneo. DQS designa un valor como erróneo si detecta un error de sintaxis y una corrección asociada en el proceso de detección. Los errores de sintaxis incluyen los errores de ortografía.  
  
-   **No válido:** es un valor que no pertenece al dominio y que no tiene una corrección. Por ejemplo, el valor “12345" en un dominio City es un valor no válido. DQS designa un valor como no válido cuando no cumple una regla de dominio.  
  
 Puede cambiar manualmente el tipo de un valor a cualquiera de los otros dos valores. DQS no aplica la semántica de errores y de validez en las operaciones manuales. Puede especificar una corrección para un valor no válido sin cambiar su estado. Puede designar un valor como no válido aunque haya cumplido las reglas de dominio. Puede designar un valor como erróneo aunque el proceso de detección no haya indicado que tiene un error de sintaxis. También puede quitar una corrección de un valor de error, que está marcado como correcto, sin cambiar su estado.  
  
 Cuando se realiza la limpieza en interactiva de datos el **administrar y ver resultados** página de la **limpieza** actividad, los valores no válidos y de error se incluyen en el **válido** ficha el **administrar y ver resultados** página.  
  
##  <a name="Display"></a> Cómo mostrar los valores adecuados  
 Puede modificar la presentación de la manera siguiente:  
  
-   **Filtro** los resultados que desea incluir en la tabla, en función de su estado, seleccionando el estado en el **filtro** lista desplegable.  
  
-   **Busque** los datos que desea comprobar o modificar especificando las letras que desea buscar en el cuadro de texto **Buscar** . Esto resaltará dichas letras dondequiera que aparezcan en los valores mostrados.  
  
-   Haga clic en **Mostrar solo nuevo** para restringir los valores mostrados en la tabla a aquellos que se detectaron en la sesión actual, no en las sesiones anteriores.  
  
-   Haga clic en el botón **Expandir todo** para mostrar todos los valores de los grupos de sinónimos cuando el estado actual es Contraído.  
  
-   Haga clic en el botón **Contraer todo** para ocultar todos los valores excepto el inicial en los grupos de sinónimos cuando el estado actual es Expandido.  
  
-   Haga clic en el **Mostrar u ocultar el Panel de historial de cambios de valores de dominio** botón para mostrar una vista previa emergente en la parte inferior de la tabla de valores que muestra los cambios recientes en el dominio de la colección de valores.  
  
##  <a name="Null"></a> Cómo administrar equivalentes del valor NULL  
 Cada tabla de valores de la **los valores de dominio** ficha incluye un valor DQS_NULL. El valor NULL de un origen de datos aparecerá como SQL_NULL en la tabla de valores. Puede establecer uno o varios equivalentes del valor NULL como sinónimos de DQS_NULL. Al hacer esto, todos los valores NULL y los equivalentes del valor NULL se procesarán como DQS_NULL.  
  
  