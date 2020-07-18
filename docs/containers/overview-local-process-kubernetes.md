---
title: Come funziona Processo locale con Kubernetes
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: conceptual
description: Descrive i processi per l'uso del processo locale con Kubernetes per connettere il computer di sviluppo al cluster Kubernetes
keywords: Processo locale con Kubernetes, Docker, Kubernetes, Azure, contenitori
monikerRange: '>=vs-2019'
ms.openlocfilehash: adde9d8ecab93bdb6f0aebbd74730ef60bd80cf6
ms.sourcegitcommit: 510a928153470e2f96ef28b808f1d038506cce0c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2020
ms.locfileid: "86454335"
---
# <a name="how-local-process-with-kubernetes-works"></a>Come funziona Processo locale con Kubernetes

Il processo locale con Kubernetes consente di eseguire ed eseguire il debug del codice nel computer di sviluppo, mentre è ancora connesso al cluster Kubernetes con il resto dell'applicazione o dei servizi. Ad esempio, se si dispone di un'architettura di microservizi di grandi dimensioni con molti servizi e database interdipendenti, la replica di tali dipendenze nel computer di sviluppo può essere difficile. Inoltre, la compilazione e la distribuzione di codice nel cluster Kubernetes per ogni modifica del codice durante lo sviluppo a ciclo interno possono essere lenti, dispendiose in termini di tempo e difficili da usare con un debugger.

Il processo locale con Kubernetes evita di dover compilare e distribuire il codice nel cluster creando invece una connessione direttamente tra il computer di sviluppo e il cluster. Connettendo il computer di sviluppo al cluster durante il debug è possibile testare e sviluppare rapidamente il servizio nel contesto dell'applicazione completa senza creare una configurazione Docker o Kubernetes.

Il processo locale con Kubernetes reindirizza il traffico tra il cluster Kubernetes connesso e il computer di sviluppo. Questo reindirizzamento del traffico consente il codice nel computer di sviluppo e i servizi in esecuzione nel cluster Kubernetes per comunicare come se fossero nello stesso cluster Kubernetes. Il processo locale con Kubernetes fornisce anche un modo per replicare le variabili di ambiente e i volumi montati disponibili per i Pod nel cluster Kubernetes nel computer di sviluppo. Fornire l'accesso alle variabili di ambiente e ai volumi montati nel computer di sviluppo consente di lavorare rapidamente sul codice senza dover replicare manualmente tali dipendenze.

## <a name="using-local-process-with-kubernetes"></a>Uso del processo locale con Kubernetes

Per usare il processo locale con Kubernetes in Visual Studio, è necessario [Visual studio 2019][visual-studio] versione 16,7 Preview 4 o successiva in esecuzione in Windows 10 con il carico di lavoro *sviluppo ASP.NET e Web* installato e l' [estensione del processo locale Kubernetes][lpk-extension] installata. Quando si usa il processo locale con Kubernetes per stabilire una connessione al cluster Kubernetes, è possibile scegliere di reindirizzare tutto il traffico da e verso un pod esistente nel cluster al computer di sviluppo.

> [!NOTE]
> Quando si usa il processo locale con Kubernetes, viene richiesto il nome del servizio da reindirizzare al computer di sviluppo. Questa opzione è un modo pratico per identificare un pod per il reindirizzamento. Tutto il reindirizzamento tra il cluster Kubernetes e il computer di sviluppo è per un pod.

Quando il processo locale con Kubernetes stabilisce una connessione al cluster:

* Viene richiesto di configurare il servizio per sostituire il cluster, la porta nel computer di sviluppo da usare per il codice e l'attività di avvio per il codice come azione singola.
* Sostituisce il contenitore nel Pod nel cluster con un contenitore agente remoto che reindirizza il traffico al computer di sviluppo.
* Esegue [kubectl porta-in avanti][kubectl-port-forward] nel computer di sviluppo per l'invio del traffico dal computer di sviluppo all'agente remoto in esecuzione nel cluster.
* Raccoglie le informazioni sull'ambiente dal cluster utilizzando l'agente remoto. Queste informazioni sull'ambiente includono variabili di ambiente, servizi visibili, montaggi di volumi e montaggi di segreti.
* Configura l'ambiente in Visual Studio in modo che il servizio nel computer di sviluppo possa accedere alle stesse variabili come se fosse in esecuzione nel cluster.  
* Aggiorna il file degli host per eseguire il mapping dei servizi nel cluster agli indirizzi IP locali nel computer di sviluppo. Queste voci di file host consentono al codice in esecuzione nel computer di sviluppo di effettuare richieste ad altri servizi in esecuzione nel cluster. Per aggiornare il file degli host, il processo locale con Kubernetes chiederà l'accesso come amministratore nel computer di sviluppo quando si connette al cluster.
* Avvia l'esecuzione e il debug del codice nel computer di sviluppo. Se necessario, il processo locale con Kubernetes libererà le porte necessarie nel computer di sviluppo arrestando i servizi o i processi che attualmente utilizzano tali porte.

Dopo aver stabilito una connessione al cluster, è possibile eseguire ed eseguire il debug del codice in modo nativo nel computer, senza contenitori e il codice può interagire direttamente con il resto del cluster. Qualsiasi traffico di rete ricevuto dall'agente remoto viene reindirizzato alla porta locale specificata durante la connessione, in modo che il codice in esecuzione a livello nativo possa accettare ed elaborare tale traffico. Le variabili di ambiente, i volumi e i segreti del cluster vengono resi disponibili per il codice in esecuzione nel computer di sviluppo. Inoltre, a causa delle voci del file hosts e del Port porting aggiunto al computer di sviluppo da un processo locale con Kubernetes, il codice può inviare il traffico di rete ai servizi in esecuzione nel cluster usando i nomi di servizio del cluster e il traffico viene inoltrato ai servizi in esecuzione nel cluster. Il traffico viene instradato tra il computer di sviluppo e il cluster per l'intera durata della connessione.

## <a name="diagnostics-and-logging"></a>Diagnostica e registrazione

Quando si usa il processo locale con Kubernetes per la connessione al cluster, i log di diagnostica del cluster vengono registrati nella [directory temporanea][azds-tmp-dir]del computer di sviluppo.

## <a name="limitations"></a>Limitazioni

Il processo locale con Kubernetes presenta le limitazioni seguenti:

* Il processo locale con Kubernetes reindirizza il traffico per un singolo servizio al computer di sviluppo. Non è possibile usare il processo locale con Kubernetes per reindirizzare più servizi nello stesso momento.
* Un servizio deve essere supportato da un singolo POD per potersi connettere a tale servizio. Non è possibile connettersi a un servizio con più POD, ad esempio un servizio con repliche.
* Un pod può avere un solo contenitore in esecuzione in tale Pod affinché il processo locale con Kubernetes possa connettersi. Il processo locale con Kubernetes non è in grado di connettersi ai servizi con Pod con contenitori aggiuntivi, ad esempio contenitori sidecar inseriti da mesh dei servizi.
* Il processo locale con Kubernetes richiede autorizzazioni elevate per l'esecuzione nel computer di sviluppo per modificare il file degli host.

## <a name="next-steps"></a>Passaggi successivi

Per iniziare a usare il processo locale con Kubernetes per connettersi al computer di sviluppo locale al cluster, vedere [usare il processo locale con Kubernetes](local-process-kubernetes.md).

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-latest
[local-process-kubernetes-vs]: local-process-kubernetes.md
[kubectl-port-forward]: https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#port-forward
[visual-studio]: https://visualstudio.microsoft.com/downloads/
[lpk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro