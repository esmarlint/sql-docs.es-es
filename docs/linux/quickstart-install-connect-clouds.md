---
title: Introducción a SQL Server 2017 en la nube | Microsoft Docs
description: En este tutorial rápido se muestra cómo ejecutar el SQL Server 2017 en Linux en la nube de su elección.
author: annashres
ms.author: annashres
manager: craigg
ms.date: 10/25/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.custom: sql-linux
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: f63fc385171469ad13d21fd844bb130ac0e6e7cd
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39084197"
---
# <a name="quickstart-run-the-sql-server-2017-in-the-cloud"></a>Inicio rápido: Ejecute el SQL Server 2017 en la nube

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

En este tutorial, se instalará SQL Server 2017 en Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES) o Ubuntu en la nube de su elección. Vaya a [aprovisionar una máquina virtual de Linux con SQL Server en Azure portal](https://docs.microsoft.com/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json) para ejecutar SQL Server en Linux en Azure.

    > [!NOTE]
    > If you choose to run a paid edition of SQL Server then you need to bring your own license (BYOL)

## <a name="amazon-web-services"></a>Servicios Web de Amazon
1.  Crear un AMI Linux con al menos 2 GB de memoria de marketplace 
    * [RHEL 7.3 +](https://aws.amazon.com/marketplace/pp/B00KWBZVK6)
    * [SLES v12 SP2](https://aws.amazon.com/marketplace/pp/B00PMM99PI)
    * [Ubuntu 16.04](https://aws.amazon.com/marketplace/pp/B01JBL2M0O)
1.  Conectarse a la AMI con ssh
1.  Siga la Guía de inicio rápido para la distribución de Linux elegida: 
    * [RHEL](quickstart-install-connect-red-hat.md)
    * [SLES](quickstart-install-connect-suse.md)
    * [Ubuntu](quickstart-install-connect-ubuntu.md)
1.  Configurar para las conexiones remotas: 
    * Abra el [consola de Amazon EC2]( https://console.aws.amazon.com/ec2/)
    * En el panel de navegación, elija **grupos de seguridad**. 
    * Elija **entrante, editar, Agregar regla**
    * Agregar una regla de entrada para permitir el tráfico en el puerto en el que SQL Server escucha (puerto TCP predeterminado 1433)

    
## <a name="digital-ocean"></a>Digital Ocean
1. Inicie sesión en el [panel de control](https://cloud.digitalocean.com/login) y haga clic en crear una gota
1. Elija una gota de Ubuntu 16.04 con al menos 2 GB de memoria
1. Conectarse a la gota con ssh
1. Siga el [inicio rápido de Ubuntu](quickstart-install-connect-ubuntu.md)
1. Configurar para las conexiones remotas:
    * En la parte superior del Panel de Control, siga el **redes** vincular y, a continuación, seleccione **Firewalls**
    * Agregar una regla de entrada para permitir el tráfico en el puerto en el que SQL Server escucha (puerto TCP predeterminado 1433)
    
## <a name="google-cloud-platform"></a>Plataforma de nube de Google
1.  Crear una imagen de Linux con al menos 2 GB de memoria desde el selector en la nube 
    * [RHEL 7.3 +](https://console.cloud.google.com/launcher/details/rhel-cloud/rhel-7)
    * [SLES v12 SP2](https://console.cloud.google.com/launcher/details/suse-cloud/sles-12)
    * [Ubuntu 16.04](https://console.cloud.google.com/launcher/details/ubuntu-os-cloud/ubuntu-xenial)
1.  Conectarse a la imagen con ssh
1.  Siga la Guía de inicio rápido para la distribución de Linux elegida: 
    * [RHEL](quickstart-install-connect-red-hat.md)
    * [SLES](quickstart-install-connect-suse.md)
    * [Ubuntu](quickstart-install-connect-ubuntu.md)
1.  Configurar para las conexiones remotas: 
    * Vaya a la [reglas de Firewall](https://console.cloud.google.com/networking/firewalls)
    * Agregar una regla de entrada para permitir el tráfico en el puerto en el que escucha SQL Server (predeterminado tcp: 1433)
