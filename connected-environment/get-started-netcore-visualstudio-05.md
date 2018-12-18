---
title: 'Creare un ambiente di sviluppo .NET Core con i contenitori usando Kubernetes nel cloud con Visual Studio - Passaggio 5: Chiamare un altro contenitore | Microsoft Docs'
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Sviluppo rapido Kubernetes con contenitori e microservizi in Azure
keywords: Docker, Kubernetes, Azure, AKS, servizio contenitore di Azure, contenitori
manager: ghogen
ms.openlocfilehash: 8b0a0c78496b8f57764383d737e2a1cebb2dd6b9
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Introduzione a Connected Environment con .NET Core e Visual Studio

Passaggio precedente: [Eseguire il debug di un contenitore in Kubernetes](get-started-netcore-visualstudio-04.md)

## <a name="call-another-container"></a>Chiamare un altro contenitore
In questa sezione verrà creato un secondo servizio, `mywebapi`, chiamato da `webfrontend`. Ogni servizio verrà eseguito in contenitori separati. Il debug verrà quindi eseguito su entrambi i contenitori.

![](media/multi-container.png)

## <a name="download-sample-code-for-mywebapi"></a>Scaricare il codice di esempio per *mywebapi*
Per risparmiare tempo, il codice di esempio verrà scaricato da un repository di GitHub. Passare a https://github.com/Azure/vsce e selezionare **Clone or download** (Clona o scarica) per scaricare il repository di GitHub. Il codice per questa sezione è in `vsce/samples/dotnetcore/getting-started/mywebapi`.

## <a name="run-mywebapi"></a>Eseguire *mywebapi*
1. Aprire il progetto `mywebapi` in una *finestra di Visual Studio separata*.
1. Selezionare **Connected Environment for AKS** (Connected Environment per AKS) nell'elenco a discesa delle impostazioni di avvio, come in precedenza per il progetto `webfrontend`. Invece di creare un nuovo ambiente di sviluppo, questa volta selezionare lo stesso già creato. Come prima, lasciare lo spazio impostato sul valore predefinito `mainline` e fare clic su **OK**. Nella finestra Output si potrebbe notare che Visual Studio inizia il "riscaldamento" di questo nuovo servizio nell'ambiente di sviluppo per velocizzare le operazioni al momento di avviare il debug.
1. Premere F5 e attendere che il servizio venga compilato e distribuito. Si saprà che è pronto quando la barra di stato di Visual Studio diventa arancione.
1. Prendere nota dell'URL dell'endpoint visualizzato nel riquadro **Connected Environment for AKS** (Connected Environment per AKS) nella finestra **Output**, simile a http://localhost:\<numeroporta\>. Potrebbe sembrare che il contenitore sia in esecuzione in locale, ma in realtà è in esecuzione nell'ambiente di sviluppo in Azure.
1. Quando `mywebapi` è pronto, aprire il browser all'indirizzo localhost e accodare `/api/values` all'URL per richiamare l'API GET predefinita per `ValuesController`. 
1. Se tutti i passaggi sono stati completati correttamente, verrà visualizzata una risposta dal servizio `mywebapi` simile a questa.

    ![](images/WebAPIResponse.png)

## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>Effettuare una richiesta da *webfrontend* a *mywebapi*
Si scriverà ora codice in `webfrontend` per effettuare una richiesta a `mywebapi`. Passare alla finestra di Visual Studio con il progetto `webfrontend`. Nel file `HomeController.cs` *sostituire* il codice del metodo About con il codice seguente:

 ```csharp
    public async Task<IActionResult> About()
    {
        ViewData["Message"] = "Hello from webfrontend";
        
        // Use HeaderPropagatingHttpClient instead of HttpClient so we can propagate
        // headers in the incoming request to any outgoing requests
        using (var client = new HeaderPropagatingHttpClient(this.Request))
        {
            // Call *mywebapi*, and display its response in the page
            var response = await client.GetAsync("http://mywebapi/api/values/1");
            ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
        }
    
        return View();
    }

```

Si noti come viene usata l'individuazione del servizio DNS di Kubernetes per fare riferimento al servizio come `http://mywebapi`. **Il codice nell'ambiente di sviluppo verrà eseguito esattamente come nell'ambiente di produzione**.

L'esempio di codice precedente usa anche una classe `HeaderPropagatingHttpClient`. Questa classe helper è il file `HeaderPropagation.cs` aggiunto al progetto al momento della configurazione per l'uso di Connected Environment. `HeaderPropagatingHttpClient` deriva dalla classe nota `HttpClient` e aggiunge funzionalità per propagare intestazioni specifiche da un oggetto ASP .NET HttpRequest esistente in un oggetto HttpRequestMessage in uscita. Si vedrà più avanti come questa tecnica favorisca un'esperienza di sviluppo più produttiva negli scenari di lavoro in team.

## <a name="debug-across-multiple-services"></a>Eseguire il debug tra più servizi
1. A questo punto, `mywebapi` dovrebbe essere ancora in esecuzione con il debugger collegato. In caso contrario, premere F5 nel progetto `mywebapi`.
1. Impostare un punto di interruzione nel metodo `Get(int id)` nel file `ValuesController.cs` che gestisce le richieste GET `api/values/{id}`.
1. Nel progetto `webfrontend` in cui è stato incollato il codice precedente, impostare un punto di interruzione prima di inviare una richiesta GET a `mywebapi/api/values`.
1. Premere F5 nel progetto `webfrontend`. Visual Studio aprirà di nuovo un browser sulla porta localhost appropriata e verrà visualizzata l'app Web.
1. Fare clic sul collegamento "**About**" nella parte superiore della pagina per attivare il punto di interruzione nel progetto `webfrontend`. 
1. Premere F10 per continuare. Verrà ora attivato il punto di interruzione nel progetto `mywebapi`.
1. Premere F5 per continuare. Si tornerà al codice nel progetto `webfrontend`.
1. Premere F5 ancora una volta per completare la richiesta e restituire una pagina nel browser. Nell'app Web, la pagina About visualizzerà un messaggio concatenato dai due servizi: "Hello from webfrontend and Hello from mywebapi".

Le operazioni per questo passaggio sono completate. È ora disponibile un'applicazione multi-contenitore in cui ogni contenitore può essere sviluppato e distribuito separatamente.

> [!div class="nextstepaction"]
> [Informazioni sullo sviluppo in team](get-started-netcore-visualstudio-06.md)

