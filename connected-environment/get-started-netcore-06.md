---
title: 'Creare un ambiente di sviluppo .NET Core con i contenitori usando Kubernetes nel cloud - Passaggio 6: Informazioni sullo sviluppo in team | Microsoft Docs'
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Sviluppo rapido Kubernetes con contenitori e microservizi in Azure
keywords: Docker, Kubernetes, Azure, AKS, servizio contenitore di Azure, contenitori
manager: ghogen
ms.openlocfilehash: 80e02e6ce1299278ba1abf530f38cb10b9f36c51
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Introduzione a Connected Environment con .NET Core

Passaggio precedente: [Chiamare un altro contenitore](get-started-netcore-05.md)

[!INCLUDE[](includes/team-development-1.md)]

Eccolo in azione:
1. Passare alla finestra di Visual Studio Code per `mywebapi` e apportare una modifica al codice del metodo `string Get(int id)`, ad esempio:

```csharp
[HttpGet("{id}")]
public string Get(int id)
{
    return "mywebapi now says something new";
}
```

[!INCLUDE[](includes/team-development-2.md)]

> [!div class="nextstepaction"]
> [avanti](get-started-netcore-07.md)
