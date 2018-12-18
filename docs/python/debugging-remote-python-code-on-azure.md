---
title: Debug remoto di Azure con Python | Microsoft Docs
description: Come configurare un servizio app di Azure per l'uso di Visual Studio per il debug remoto di un'applicazione Python.
ms.custom: ''
ms.date: 07/12/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: d74e4425bfcaefbd1bb13e368ee719acaa3bae80
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="remotely-debugging-python-code-on-azure"></a>Debug remoto di codice Python in Azure

Il [supporto per Python in Visual Studio](installing-python-support-in-visual-studio.md) include la possibilità di eseguire il debug in remoto del codice Python in esecuzione in Servizio app di Azure. Diversamente dal semplice debug remoto, il computer di destinazione in questo scenario non è accessibile direttamente tramite TCP, quindi Visual Studio fornisce un proxy che espone il protocollo del debugger tramite HTTP. I progetti creati con il modello Web configurano automaticamente questo proxy nel file `web.debug.config` generato. Il debug remoto viene abilitato anche quando si pubblica una configurazione per il debug del progetto, come descritto in [Publishing to Azure App Service](python-web-application-project-templates.md#publishing-to-azure-app-service) (Pubblicazione in Servizio app di Azure).

Dato che il debug remoto di Azure usa WebSocket, è necessario abilitare i socket per il servizio app tramite il [portale di Azure](https://portal.azure.com). Passare a **Impostazioni > Impostazioni applicazione** e impostare **Impostazioni generali > Web Socket** su **Attivato**, quindi selezionare **Salva** per applicare la modifica. (Si noti che le impostazioni **Debug** non sono valide per il debug di Python.)

![Abilitazione di WebSocket nel portale di Azure](media/azure-remote-debugging-enable-web-sockets.png)

Dopo aver distribuito correttamente il progetto e aver abilitato WebSocket, è possibile collegarsi al servizio app da **Esplora server** in Visual Studio (**Visualizza > Esplora server**). Individuare il sito in **Azure > Servizio app** e il gruppo di risorse applicabile, fare clic con il pulsante destro del mouse e scegliere **Collega debugger (Python)**. Il comando **Collega debugger** è per le applicazioni .NET in esecuzione in IIS e risulta utile solo se si ospita codice .NET insieme all'app Python.

Visual Studio potrebbe indirizzare a un set di istruzioni per il collegamento diretto, come descritto di seguito in [Collegamento senza Esplora server](#attaching-without-server-explorer). Se il comando **Collega debugger (Python)** non viene visualizzato o Visual Studio non riesce a collegarsi al sito, vedere [Risoluzione dei problemi di debug remoto di Azure](debugging-remote-python-code-on-azure-troubleshooting.md).

Se il collegamento ha esito positivo, Visual Studio passa a una vista del debugger. La barra degli strumenti indica il processo sottoposto a debug, ad esempio un URI `wss://`:

![Debug di un sito Web di Servizio app di Azure](media/azure-remote-debugging-attached.png)

Dopo aver attivato il collegamento, l'esperienza di debug è fondamentalmente uguale al normale debug remoto, con alcune restrizioni. In particolare, il server Web IIS che gestisce le richieste in ingresso e le delega al codice Python attraverso FastCGI ha un timeout per la gestione delle richieste, pari a 90 secondi per impostazione predefinita. Se la gestione della richiesta richiede più tempo del timeout, ad esempio perché il processo viene sospeso in un punto di interruzione, IIS termina il processo, interrompendola sessione di debug. 

## <a name="attaching-without-server-explorer"></a>Collegamento senza Esplora server

Per collegare il debugger direttamente al servizio app, seguire le istruzioni fornite nella pagina di informazioni sul proxy WebSocket che Visual Studio distribuisce nel sito all'indirizzo `<site_url>/ptvsd`, ad esempio `ptvsdemo.azurewebsites.net/ptvsd`. Quando si visita questa pagina viene anche eseguita una verifica della corretta configurazione del proxy:

![Pagina di informazioni sul proxy per il debug remoto in Azure](media/azure-remote-debugging-proxy-info-page.png)

Come indicato, costruire un URL usando il segreto da `web.debug.config`, che viene rigenerato a ogni pubblicazione del progetto. Questo file è nascosto per impostazione predefinita in Esplora soluzioni e non è incluso nel progetto, pertanto è necessario visualizzare tutti i file oppure aprirlo in un editor separato. Dopo aver aperto il file, osservare il valore dell'appSetting `WSGI_PTVSD_SECRET`:

![Determinazione dell'endpoint del debugger in Servizio app di Azure](media/azure-remote-debugging-secret.png)

L'URL ora necessario è nel formato `wss://<secret>@<site_name>.azurewebsites.net/ptvsd` dove &lt;secret&gt; e &lt;site_name&gt; nella stringa devono essere sostituiti con i valori specifici.

Per collegare il debugger, selezionare **Debug > Connetti a processo**, selezionare **Debug remoto Python** nell'elenco a discesa **Trasporto**, immettere l'URL nella casella di testo **Qualificatore** e premere INVIO. Se Visual Studio riesce a connettersi correttamente al servizio app, viene visualizzato un singolo processo Python nell'elenco. Selezionarlo e quindi selezionare **Associa** per avviare il debug:

![Uso della finestra di dialogo Connetti a processo per collegarsi a un sito Web di Azure](media/azure-remote-debugging-manual-attach.png)
