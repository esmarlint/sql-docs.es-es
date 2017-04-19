---
title: "Portal web (modo nativo de SSRS) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "02/24/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
ms.assetid: 7349e626-6ed5-4d21-b05f-cf042ad9ad70
caps.latest.revision: 15
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 13
---
# Portal web (modo nativo de SSRS)
El [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] de Reporting Services es una experiencia basada en web que permite ver informes, informes móviles y KPI, así como navegar por los elementos que se encuentran en la instancia del servidor de informes. También puede usar el [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] para administrar una única instancia del servidor de informes.  
  
![ssRSPortal](../reporting-services/media/ssrsportal.png)  
  
En este tema:  
  
-   [¿Qué es el portal web?](#whatisportal)  
  
-   [Inicio y uso del portal web](#startanduse)  
  
-   [Agrupación por categorías](#categories)  
  
-   [Búsqueda de elementos](#search)  
  
-   [Tareas del portal web](#tasks)  
  
<a name="whatisportal"/>  
## ¿Qué es el [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]?  
  
Puede usar el [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] para realizar las siguientes tareas:  
  
-   Ver, buscar e imprimir informes, así como suscribirse a ellos.  
  
-   Crear, proteger y mantener la jerarquía de carpetas para organizar elementos en el servidor.  
  
-   Configurar una seguridad basada en roles que determine el acceso a elementos y operaciones.  
  
-   Configurar las propiedades de ejecución, el historial y los parámetros del informe.  
  
-   Crear programaciones compartidas y orígenes de datos compartidos para que las programaciones y las conexiones de orígenes de datos sean más fáciles de administrar.  
  
-   Crear suscripciones controladas por datos que distribuyan informes a una lista de destinatarios extensa.  
  
-   Crear informes vinculados para reutilizarlos y cambiar la finalidad de un informe existente de varias formas.  
  
-   Descargar herramientas comunes como Generador de informes y Publicador de informes móviles.  
  
-   [Crear KPI](../reporting-services/working-with-kpis-in-reporting-services.md).  
  
-   Enviar comentarios o solicitar nuevas características.  
  
Puede utilizar el [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] para examinar las carpetas del servidor de informes o buscar informes concretos. Puede ver un informe, sus propiedades generales y copias anteriores de este que se almacenan en el historial de informes. Dependiendo de los permisos que tenga, también podría suscribirse a informes para su entrega en una bandeja de entrada de correo electrónico o en una carpeta compartida del sistema de archivos.  
  
> [!NOTE] Para obtener información sobre los exploradores y versiones compatibles, vea [Compatibilidad del explorador de Reporting Services y Power View](../reporting-services/browser-support-for-reporting-services-and-power-view.md).  
  
El [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] solo se utiliza para un servidor de informes que se ejecuta en modo nativo. No se admite para un servidor de informes que se configure para el modo integrado de SharePoint.  
  
Algunas características del [!INCLUDE[ssNoVersion](../includes/ssnoversion.md)] solo están disponibles en determinadas ediciones de [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]. Para obtener más información, consulte [Vista previa de SQL Server 2016](Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.xml).  
  
En una instalación nueva, solo los administradores locales tienen permisos suficientes para trabajar con el contenido y la configuración. Para conceder permisos a otros usuarios, un administrador local debe crear asignaciones de roles que proporcionen acceso al servidor de informes. Las tareas y las páginas de aplicación a las que un usuario puede obtener acceso posteriormente dependerán de las asignaciones de roles para dicho usuario. Para obtener más información, consulte el artículo sobre cómo agregar un usuario al servidor de informes.  
  
> [!NOTE] Si va a examinar el portal web en la máquina local donde se ejecuta el servidor, aparecerá un mensaje que le indica que no tiene permiso para ver esta carpeta. Esto se debe al control de acceso universal (UAC) y a que no está ejecutando el explorador como administrador. No puede ejecutar Edge como administrador. Tendrá que utilizar Internet Explorer. Puede acceder al servidor de forma remota o iniciar Internet Explorer como administrador e ir al portal web. Si desea usar el portal web de forma remota, debe conceder a su cuenta de derechos de administrador de contenido para la carpeta.  
  
<a name="startanduse"/>  
## Inicio y uso del [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]  
  
El [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] es una aplicación web que abre escribiendo la URL del [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] en la barra de direcciones de la ventana del explorador. Al iniciar el [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)], las páginas, los vínculos y las opciones que se ven varían en función de los permisos que se tengan en el servidor de informes. Para realizar una tarea, debe estar asignado a un rol que incluya la tarea.  Un usuario asignado a un rol con permisos totales tiene acceso al conjunto completo de menús y páginas de la aplicación disponibles para administrar un servidor de informes. Un usuario asignado a un rol con permisos para ver y ejecutar informes solo ve los menús y las páginas que admiten dichas actividades. Cada usuario puede tener distintas asignaciones de roles para distintos servidores de informes o, incluso, para los distintos informes y carpetas almacenados en un único servidor de informes.  
  
Para obtener más información sobre los roles, consulte [Conceder permisos en un servidor de informes en modo nativo](../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md).  
  
### Inicio del [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]  
Para iniciar el [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] desde un explorador, siga estos pasos:  
  
1.  Abra el explorador web. Para ver una lista de los exploradores web compatibles, consulte [Planear la compatibilidad del explorador de Reporting Services y Power View (Reporting Services 2014)](../reporting-services/browser-support-for-reporting-services-and-power-view.md).  
  
2.  En la barra de direcciones del explorador web, escriba la URL del [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)].  
  
    De manera predeterminada, la URL es *http://[nombreDeEquipo]/reports*.  
  
    El servidor de informes se puede configurar para usar un puerto concreto. Por ejemplo, *http://[nombreDeEquipo]:80/reports* o *http://[nombreDeEquipo]:8080/reports*  
  
<a name="categories">  
## Agrupación por categorías  
  
El [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] agrupará los elementos en distintas categorías. Las categorías disponibles son las siguientes:  
  
-   KPI  
-   Mobile Reports (Informes móviles)  
-   Paginated Reports (Informes paginados)  
-   Power BI Desktop Reports (Informes de Power BI Desktop)  
-   Excel Workbooks (Libros de Excel)  
-   Conjuntos de datos  
-   Orígenes de datos  
-   Recursos  
  
Puede controlar lo que se muestra si selecciona **Vista** en la esquina superior derecha. Se mostrarán los elementos cuyas casillas estén activadas, si hay alguno disponible en esa carpeta concreta. Para ocultar elementos, puede desactivar sus casillas.  
  
![ssRSWebPortal-view](../reporting-services/media/ssrswebportal-view.png)  
   
Si selecciona Mostrar oculto, esos elementos se mostrarán en un color más claro.  
  
![ssRSWebPortal-hidden](../reporting-services/media/ssrswebportal-hidden.png)  
   
### Informes de Power BI Desktop y libros de Excel  
  
Puede cargar, organizar y administrar los permisos para los informes de Power BI Desktop y libros de Excel. Se agruparán juntos en el portal web.  
  
![ssRSWebPortal-view-pbi-and-excel](../reporting-services/media/ssrswebportal-view-pbi-and-excel.png)  
   
Los archivos se almacenan en Reporting Services, como sucede con otros archivos de recursos. Si selecciona uno de estos elementos, se descargará localmente en su escritorio. Puede guardar los cambios que ha efectuado volviendo a cargarlos al servidor de informes.  
  
<a name="search">  
## Búsqueda de elementos  
  
Puede escribir un término de búsqueda y podrá ver todos los elementos a los que tenga acceso. Los resultados se categorizan en KPI, informes, conjuntos de datos y otros elementos. Después, puede interactuar con los resultados y agregarlos a sus favoritos.  
  
![ssRSWebPortal-Search](../reporting-services/media/ssrswebportal-search.png)  
  
<a name="tasks">  
## Tareas del portal web  
  
[Personalización de marca del portal web](../reporting-services/branding-the-web-portal.md)  

[Trabajar con KPI](../reporting-services/working-with-kpis-in-reporting-services.md)
  
[Uso de los conjuntos de datos compartidos (portal web)](../reporting-services/working-with-shared-datasets-web-portal.md)  
  
## Vea también

[Creación y publicación de informes móviles con el Publicador de informes móviles de SQL Server](../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)
  
[Configurar una dirección URL (Administrador de configuración de SSRS)](../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)  
  
[Herramientas de Reporting Services](../reporting-services/tools/reporting-services-tools.md)  
  
[Planear la compatibilidad del explorador de Reporting Services](../reporting-services/browser-support-for-reporting-services-and-power-view.md)  
  
[Características compatibles con las ediciones de SQL Server 2016](Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.xml)  
  
  