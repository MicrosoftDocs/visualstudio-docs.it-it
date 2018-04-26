---
title: 'Creare un ambiente di sviluppo .NET Core con i contenitori usando Kubernetes nel cloud con Visual Studio - Passaggio 1: Installare gli strumenti | Microsoft Docs'
author: ghogen
ms.author: ghogen
ms.date: 04/05/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Sviluppo rapido Kubernetes con contenitori e microservizi in Azure
keywords: Docker, Kubernetes, Azure, AKS, servizio contenitore di Azure, contenitori
manager: douge
ms.openlocfilehash: b2edc476ffd4648f9ddb0e3d076f8eb400458242
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Introduzione a Connected Environment con .NET Core e Visual Studio

In questa guida si imparerà a:

1. Creare un ambiente basato su Kubernetes in Azure ottimizzato per lo sviluppo.
1. Sviluppare codice in modo iterativo nei contenitori con Visual Studio.
1. Sviluppare in modo indipendente due servizi distinti e usare l'individuazione del servizio DNS di Kubernetes per effettuare una chiamata a un altro servizio.
1. Sviluppare e testare in modo produttivo il codice in un ambiente di lavoro in team.

[!INCLUDE[](includes/see-troubleshooting.md)]

## <a name="install-the-connected-environment-cli"></a>Installare l'interfaccia della riga di comando di Connected Environment
Connected Environment richiede una configurazione minima del computer locale. La maggior parte della configurazione dell'ambiente di sviluppo viene archiviata nel cloud ed è condivisibile con altri utenti.

1. Scaricare ed eseguire il [programma di installazione dell'interfaccia della riga di comando di Connected Environment](https://aka.ms/get-vsce-windows). 

## <a name="get-kubernetes-debugging-tools"></a>Ottenere gli strumenti di debug di Kubernetes
Anche se è possibile usare l'interfaccia della riga di comando di Connected Environment come strumento autonomo, le funzionalità avanzate come il **debug di Kubernetes** sono disponibili per gli sviluppatori di .NET Core con **Visual Studio Code** o **Visual Studio** .

### <a name="visual-studio-debugging"></a>Debug in Visual Studio 
1. Installare la versione più recente di [Visual Studio 2017](https://www.visualstudio.com/vs/)
1. Nel programma di installazione di Visual Studio verificare che sia selezionato il carico di lavoro seguente:
    * Sviluppo ASP.NET e Web
1. Installare l'[estensione di Visual Studio per Connected Environment](https://aka.ms/get-vsce-visualstudio)

A questo punto si è pronti per creare un'app Web ASP.NET con Visual Studio.

> [!div class="nextstepaction"]
> [Creare un'app Web ASP.NET](get-started-netcore-visualstudio-02.md)
