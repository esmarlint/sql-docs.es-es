---
title: "Configurar los niveles de gravedad de los archivos de registro de DQS | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dqs.admin.config.log.f1"
helpviewer_keywords: 
  - "niveles de gravedad"
  - "archivos de registro, niveles de gravedad"
  - "archivos de registro de dqs, niveles de gravedad"
  - "registrar, niveles de gravedad"
  - "configurar los niveles de gravedad"
ms.assetid: 66ffcdec-4bf7-4dd5-a221-fd9baefeeef4
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# Configurar los niveles de gravedad de los archivos de registro de DQS
  En este tema se describe cómo configurar los niveles de gravedad de las distintas actividades y módulos de [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) mediante [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Los niveles de gravedad definen la intensidad de los eventos que tienen lugar en DQS. Los eventos de DQS tienen los niveles de gravedad siguientes, en orden decreciente:  
  
-   **Grave**: errores críticos en tiempo de ejecución que podrían producir resultados graves e inesperados.  
  
-   **Error**: otros errores en tiempo de ejecución.  
  
-   **Warn**: advertencia sobre eventos que pueden provocar un error.  
  
-   **Info**: información sobre eventos en general; no se trata ni de un error ni de una advertencia. Por ejemplo, se ha iniciado un proceso de DQS.  
  
-   **Depurar**: (detallada) información detallada sobre el evento.  
  
 Cuando se configuran niveles de gravedad para las actividades y módulos de DQS, lo que se hace en realidad es filtrar la información que quedará registrada en el archivo de registro de DQS para la actividad o el módulo de DQS correspondiente. Por ejemplo, si establece el nivel de gravedad de una actividad DQS para **Advertir**, sólo advertencia y superior se registrarán los mensajes de gravedad (Error y Fatal) asociados con la actividad DQS.  
  
##  <a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 Para configurar niveles de gravedad, debe disponer del rol dqs_administrator en la base de datos DQS_MAIN.  
  
##  <a name="ConfigureActivity"></a> Configurar los niveles de gravedad en el nivel de actividad  
 Puede configurar los niveles de gravedad del registro para las siguientes actividades de DQS: administración de dominios, detección de conocimiento, directiva de coincidencia, limpieza de datos, coincidencia de datos y servicios de datos de referencia. Para ello:  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Ejecute la aplicación de cliente de calidad de datos](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  En la página de inicio de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , haga clic en **Configuración**.  
  
3.  A continuación, haga clic en la pestaña **Configuración del registro** . Se muestran las siguientes actividades DQS que puede seleccionar un nivel de gravedad: **Domain Management**, **detección de conocimiento**, **proyecto de limpieza (p. ej. RDS)**, **Directiva de búsqueda de coincidencias y proyecto**, y **RDS**.  
  
4.  Para una actividad de DQS, seleccione el nivel de gravedad que desea registrar. Puede seleccionar uno de los siguientes: **Fatal**, **Error**, **Warn**, **Info**y **Debug**. Por ejemplo, si desea que sólo los mensajes se escriban en los archivos de registro DQS para la actividad de detección de conocimiento graves, seleccione **Fatal** en la lista desplegable con los **detección de conocimiento** actividad.  
  
    > [!NOTE]  
    >  De forma predeterminada, todas las actividades tienen seleccionado el nivel de gravedad **Error** . Esto significa que, de forma predeterminada, en los archivos de registro de DQS se escribirán los mensajes de tipo Error y Fatal para todas las actividades.  
  
5.  Haga clic en **Cerrar**.  
  
##  <a name="ConfigureModule"></a> Configurar los niveles de gravedad en el nivel de módulo (Avanzadas)  
 La sección **Avanzadas** de la pestaña **Configuración del registro** permite configurar los niveles de gravedad del registro en el nivel de módulo. Los módulos son ensamblados del sistema de DQS que implementan funcionalidades en una característica de DQS. Por ejemplo, la actividad de administración de dominios contiene funcionalidades tales como la definición de reglas de dominio, la definición de condiciones de regla, la definición de reglas entre dominios para dominios compuestos, etc.  
  
 En ocasiones, el nivel de granularidad en el nivel de actividad no es suficiente. Es posible que desee investigar un problema que aparece en un determinado módulo de una actividad. Resulta de ayuda disponer de una opción que permita configurar los niveles de gravedad del registro en el nivel de módulo para poder aislar el problema y seguir su evolución con mayor precisión.  
  
 La configuración de los niveles de gravedad del registro en el nivel de actividad determina la configuración de los niveles de gravedad del registro de todos los módulos que constituyen la actividad. Sin embargo, si existe un conflicto entre la configuración de los niveles de gravedad del registro en el nivel de actividad y en el nivel de módulo, prevalecen los niveles de gravedad del registro en el nivel de módulo.  
  
> [!NOTE]  
>  -   De forma predeterminada, el módulo **Microsoft.Ssdqs.Core.Startup** se preconfigura en la sección **Avanzadas** con un nivel de gravedad **Info**. Esto tiene como finalidad habilitar el registro de los eventos con un nivel de gravedad Info o superior (Warn, Error y Fatal) que están relacionados con el inicio y finalización de los servicios de DQS.  
> -   Debe configurar los niveles de gravedad del registro en el nivel de módulo solo si es un usuario avanzado de DQS que está familiarizado con los ensamblados del sistema de DQS.  
  
 Para configurar los niveles de gravedad del registro en el nivel de módulo:  
  
1.  En la pestaña **Configuración del registro** , haga clic en la flecha abajo de **Avanzadas** para mostrar el área.  
  
2.  En la cuadrícula que aparece, seleccione un nombre de módulo de la lista desplegable en el **módulo** columna.  
  
3.  A continuación, seleccione un nivel de gravedad para el módulo de la lista desplegable en el **gravedad** columna. Puede seleccionar uno de los siguientes: **Fatal**, **Error**, **Warn**, **Info**y **Debug**.  
  
     Por ejemplo, en la actividad de administración de dominios, puede establecer un nivel de granularidad para la funcionalidad de definición de reglas de dominio distinto del de la actividad de administración de dominios; para ello, solo tiene que seleccionar el módulo **Microsoft.Ssdqs.DomainRules.Define** y elegir otro nivel de gravedad del registro. De forma similar, puede establecer un nivel de granularidad diferente para la funcionalidad de la regla entre dominios seleccionando la **Microsoft.Ssdqs.DomainRules.Condition.CrossDomain** módulo y seleccionar un nivel de gravedad del registro diferente.  
  
4.  Repita los pasos 2 y 3 para otros módulos, si procede. También puede agregar o eliminar filas de la cuadrícula haciendo clic en los iconos **Agregar módulo** y **Quitar módulo** .  
  
5.  Haga clic en **Cerrar**.  
  
## Vea también  
 [Configurar las opciones avanzadas de los archivos de registro de DQS](../data-quality-services/configure-advanced-settings-for-dqs-log-files.md)  
  
  