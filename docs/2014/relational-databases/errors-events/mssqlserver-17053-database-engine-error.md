---
title: MSSQLSERVER_17053 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 17053 (Database Engine error)
ms.assetid: e0a01f3d-d0aa-4c38-8bcc-82e59de50512
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5ad2d2cd4d9cbe7536109cefe593933cfffd9166
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37414964"
---
# <a name="mssqlserver17053"></a>MSSQLSERVER_17053
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|17053|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|OS_ERROR|  
|Texto del mensaje|% ls: error %ls del sistema operativo.|  
  
## <a name="explanation"></a>Explicación  
 Se produjo un error genérico del sistema operativo.  No está claro cuál es el estado resultante.  
  
## <a name="user-action"></a>Acción del usuario  
 Normalmente este error se produce junto con algún otro y se debería usar como ayuda para diagnosticar dicho error. Algunos ejemplos incluirían las lecturas o escrituras de datos o archivos de registro en los que se producen errores, operaciones de lectura y escritura en el Registro u otros errores inesperados de Win32API.  
  
  
