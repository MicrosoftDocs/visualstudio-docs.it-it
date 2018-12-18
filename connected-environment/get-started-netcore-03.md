---
title: "Creare un ambiente di sviluppo .NET Core con i contenitori usando Kubernetes nel cloud - Passaggio 3: Creare un'app Web ASP.NET Core | Microsoft Docs"
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Sviluppo rapido Kubernetes con contenitori e microservizi in Azure
keywords: Docker, Kubernetes, Azure, AKS, servizio contenitore di Azure, contenitori
manager: ghogen
ms.openlocfilehash: f858a013e4b0c2ce1c30b8f26f2dc33eebf19c27
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Introduzione a Connected Environment con .NET Core

Passaggio precedente: [Creare un ambiente di sviluppo Kubernetes in Azure](get-started-netcore-02.md)

## <a name="create-an-aspnet-core-web-app"></a>Creare un'app Web ASP.NET Core
Se [.NET Core](https://www.microsoft.com/net) è installato, è possibile creare rapidamente un'app Web ASP.NET Core in una cartella denominata `webfrontend`.
```cmd
dotnet new mvc --name webfrontend
```

In alternativa **scaricare il codice di esempio da GitHub**: passare a https://github.com/Azure/vsce e selezionare **Clone or download** (Clona o scarica) per scaricare il repository GitHub nell'ambiente locale. Il codice per questa guida è disponibile in `vsce/samples/dotnetcore/getting-started/webfrontend`.

[!INCLUDE[](includes/vsce-init.md)]

[!INCLUDE[](includes/ensure-env-created.md)]

[!INCLUDE[](includes/build-and-run-in-k8s-cli.md)]

## <a name="update-a-content-file"></a>Aggiornare un file di contenuto
Connected Environment non significa semplicemente la possibilità di eseguire il codice in Kubernetes, ma si tratta di riuscire a vedere applicate rapidamente e in modo iterativo le modifiche al codice in un ambiente Kubernetes nel cloud.

1. Individuare il file `./Views/Home/Index.cshtml` e apportare una modifica al codice HTML. Ad esempio, modificare la riga 70 `<h2>Application uses</h2>` come segue: `<h2>Hello k8s in Azure!</h2>`
1. Salvare il file. Alcuni momenti più tardi, nella finestra del terminale verrà visualizzato un messaggio che informa che è stato aggiornato un file nel contenitore in esecuzione.
1. Passare al browser e aggiornare la pagina. Verrà visualizzata la pagina Web con il codice HTML aggiornato.

Cosa è successo? Le modifiche apportate ai file di contenuto, come HTML e CSS, non richiedono la ricompilazione in un'app Web .NET Core, quindi un comando `vsce up` attivo sincronizzerà automaticamente qualsiasi file di contenuto modificato nel contenitore in esecuzione in Azure, offrendo così un modo rapido per visualizzare le modifiche al contenuto.

## <a name="update-a-code-file"></a>Aggiornare un file di codice
L'aggiornamento di file di codice richiede più lavoro, perché un'app .NET Core deve essere ricompilata per produrre file binari dell'applicazione aggiornati.

1. Nella finestra del terminale premere `Ctrl+C` (per arrestare `vsce up`).
1. Aprire il file di codice denominato `Controllers/HomeController.cs` e modificare il messaggio che verrà visualizzato nella pagina About: `ViewData["Message"] = "Your application description page.";`
1. Salvare il file.
1. Eseguire `vsce up` nella finestra del terminale. 

Viene così ricompilata l'immagine del contenitore e ridistribuito il grafico Helm. Per visualizzare le modifiche al codice applicate nell'applicazione in esecuzione, passare al menu About nell'app Web.


Esiste però un *metodo ancora più rapido* per lo sviluppo del codice, che verrà presentato nella prossima sezione. 
> [!div class="nextstepaction"]
> [Eseguire il debug di un contenitore in Kubernetes](get-started-netcore-04.md)

