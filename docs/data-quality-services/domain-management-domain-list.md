---
title: "Administraci&#243;n de dominios: lista de dominios | Microsoft Docs"
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
  - "sql13.dqs.dm.domainlist.f1"
ms.assetid: 8df305f0-97ea-4226-811b-979ed862e1f0
caps.latest.revision: 13
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 13
---
# Administraci&#243;n de dominios: lista de dominios
  En este tema se describe los controles de la lista de dominios de la **Domain Management** página [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Utilice este panel para seleccionar el dominio en el que va a realizar las operaciones de administración. Este mismo panel se utiliza en todas las páginas con pestañas de la página **Administración de dominios** .  
  
## Opciones  
  
### Lista de dominios  
 **Dominio**  
 Esta lista muestra todos los dominios de la base de conocimiento. Las operaciones que realice en las páginas con pestañas del panel derecho también se realizarán en el dominio seleccionado en la lista. Para obtener más información, vea  
  
 **Crear un dominio compuesto**  
 Crea un nuevo dominio compuesto en la base de conocimiento. Este comando muestra el cuadro de diálogo **Crear un dominio compuesto** . Este comando está disponible al hacer clic con el botón secundario en un dominio o al hacer clic en el icono situado encima de la lista de dominios. Para más información, consulte [Create a Composite Domain](../data-quality-services/create-a-composite-domain.md).  
  
 **Crear un dominio**  
 Crea un nuevo dominio en la base de conocimiento. Este comando muestra el cuadro de diálogo **Crear dominio** . Este comando está disponible al hacer clic con el botón secundario en un dominio o al hacer clic en el icono situado encima de la lista de dominios. Para obtener más información, consulte [Create a Domain](../data-quality-services/create-a-domain.md).  
  
 **Crear una copia del dominio seleccionado**  
 Crea una copia exacta del dominio seleccionado y lo agrega a la base de conocimiento. El nombre del nuevo dominio estará formado por el nombre del dominio a partir del cual se creó, más la palabra “ – Copia” agregada al nombre. Este comando está disponible con el botón secundario de un dominio y, a continuación, haciendo clic en **crear una copia**, o haciendo clic en el icono situado encima de la lista de dominios. No está disponible para un dominio compuesto.  
  
 **Importar dominio del archivo de datos**  
 Importa un dominio desde un archivo .dqs. Este comando muestra el cuadro de diálogo **Importar de archivo de datos** , que permite examinar el sistema de archivos y seleccionar un archivo .dqs para un dominio individual o para un dominio compuesto. Este comando está disponible cuando se hace clic en el icono situado encima de la lista de dominios. Para más información, consulte [Import a Domain from a .dqs File](../data-quality-services/import-a-domain-from-a-dqs-file.md).  
  
 **Eliminar dominio**  
 Elimina el dominio seleccionado de la base de conocimiento. Este comando muestra el cuadro de diálogo **SQL Server Data Quality Services** . Si hace clic en **Sí**, el dominio y todos sus datos se eliminarán permanentemente. Este comando está disponible al hacer clic con el botón secundario en un dominio o al hacer clic en el icono situado encima de la lista de dominios.  
  
 **Crear dominio vinculado**  
 Crea un dominio vinculado al dominio seleccionado. Este comando muestra el cuadro de diálogo **Crear dominio** . Este comando está disponible haciendo clic en un dominio y, a continuación, haga clic en **crear un dominio vinculado** que está vinculado al dominio seleccionado. El dominio al que está vinculando el nuevo dominio aparece en el cuadro de diálogo Crear dominio. El comando no está disponible para un dominio compuesto. No existe ningún comando que permita desvincular dos dominios; para hacerlo, deberá eliminar el dominio vinculado. No se puede crear un dominio vinculado a otro dominio vinculado. Para más información, consulte [Create a Linked Domain](../data-quality-services/create-a-linked-domain.md).  
  
 Un dominio vinculado tiene los mismos valores que el dominio al que está vinculado. Solo varían el nombre y las propiedades del dominio. Si cambia una regla de dominio, un valor de dominio, una relación basada en términos o un vínculo de datos de referencia vinculado, también cambiará la regla de dominio, el valor de dominio, la relación basada en términos o el vínculo de datos de referencia del dominio vinculado. Además, si cambia un valor en el dominio vinculado, el cambio también se realizará en el dominio al que está vinculado dicho dominio.  
  
 **Exportar base de conocimiento**  
 Exporta la base de conocimiento completa a un archivo .dqs. Este comando muestra el cuadro de diálogo **Exportar a un archivo de datos** . Este comando está disponible cuando se hace clic en el icono **Exportar datos de la base de conocimiento** , situado en la parte superior de la página, o debajo de **Exportar** en el menú contextual del panel de la lista de dominios. Para más información, consulte [Export a Knowledge Base to a .dqs File](../data-quality-services/export-a-knowledge-base-to-a-dqs-file.md).  
  
 **Exportar dominio**  
 Exporta el dominio a un archivo .dqs. Este comando muestra el cuadro de diálogo **Exportar a un archivo de datos** . Este comando está disponible en la **exportar** menú en la barra de menús en la parte superior de la página, o bien con el botón secundario en el panel de lista de dominio. Para más información, consulte [Export a Domain to a .dqs File](../data-quality-services/export-a-domain-to-a-dqs-file.md).  
  
  