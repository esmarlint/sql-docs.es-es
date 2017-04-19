---
title: "Coincidir datos similares (Complemento MDS para Excel) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f6fd6fc1-3569-42a5-b6cb-87a921c88f3b
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# Coincidir datos similares (Complemento MDS para Excel)
  En el [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], use la funcionalidad Data Quality Services (DQS) para buscar similitudes en los datos.  
  
 Para realizar este procedimiento, puede:  
  
-   Usar la base de conocimiento de Data Quality Services predeterminada o  
  
-   Crear su propia base de conocimiento DQS personalizada y directiva correspondiente. Para más información, consulte [Create a Matching Policy](../../data-quality-services/create-a-matching-policy.md).  
  
## Requisitos previos  
  
-   Debe tener una hoja de cálculo activa que contenga los datos administrados por MDS. Para obtener más información, consulte [Exportar datos a Excel desde Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md).  
  
-   Opcional. Puede combinar otros datos con datos administrados con MDS antes de comprobar las similitudes. Para obtener más información, consulte [Combinar datos &#40;Complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/combine-data-mds-add-in-for-excel.md).  
  
### Para buscar similitudes con la base de conocimiento predeterminada  
  
1.  En la hoja de cálculo que contiene datos administrados con MDS, en el grupo **Data Quality**, haga clic en **Datos de coincidencia**.  
  
2.  En el cuadro de diálogo **Datos de coincidencia**, en la lista **DQS de Knowledge Base**, seleccione **Datos de DQS (predeterminado)**.  
  
3.  Para cada columna que contenga los datos que desee buscar, agregue una fila en el cuadro de diálogo. Para obtener información sobre los campos en este cuadro de diálogo, vea [How to Set Matching Rule Parameters](../../data-quality-services/create-a-matching-policy.md#MatchingRules).  
  
4.  Cuando el total de todos los valores de peso sea igual al 100 por ciento, haga clic en **Aceptar**.  
  
### Para buscar similitudes con una base de conocimiento personalizada  
  
1.  En la hoja de cálculo que contiene datos administrados con MDS, en el grupo **Data Quality**, haga clic en **Datos de coincidencia**.  
  
2.  En la lista **Base de conocimiento DQS** , seleccione el nombre de la base de conocimiento personalizada.  
  
3.  Para cada columna de la hoja de cálculo, seleccione un dominio DQS.  
  
4.  Cuando todos los dominios DQS se asignen a las columnas de la hoja de cálculo, haga clic en **Aceptar**.  
  
## Pasos siguientes  
  
-   Vea información adicional para determinar qué datos son similares. Para obtener más información, consulte [Columnas de coincidencia de calidad de datos &#40;Complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/data-quality-matching-columns-mds-add-in-for-excel.md).  
  
## Vea también  
 [Coincidencia de calidad de datos en el Complemento MDS para Excel](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Coincidencia de datos](../../data-quality-services/data-matching.md)  
  
  