---
title: Domande frequenti relative al debug snapshot | Documenti Microsoft
ms.date: 11/07/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8547c14cfd8a59d775c909edb06e3542b18710c8
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Domande frequenti per snapshot debug in Visual Studio

Di seguito è riportato un elenco di domande che potrebbe essere applicata durante il debug di applicazioni di Azure in tempo reale mediante il Debugger di Snapshot.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Che cos'è l'impatto sulle prestazioni di esecuzione di uno snapshot?

Quando il Debugger Snapshot acquisisce uno snapshot dell'app, è duplicazioni processo dell'applicazione e la sospensione della copia con fork. Quando si esegue il debug di uno snapshot, si esegue il debug con la copia con fork del processo. Questo processo accetta solo 10-20 millisecondi ma non la copia nell'heap completo dell'app; al contrario, viene copiata solo la tabella della pagina e si imposta le pagine da copiare durante la scrittura. Se alcuni degli oggetti dell'applicazione sulla modifica dell'heap, rispettive pagine vengono quindi copiate. Pertanto, ogni snapshot ha un costo in memoria molto piccolo (nell'ordine di centinaia di KB per la maggior parte delle App). 

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Cosa accade se dispone di un servizio di App di Azure di scalabilità orizzontale (più istanze dell'applicazione).

Quando si dispone di più istanze dell'app, snappoints vengano applicate a ogni singola istanza. Solo il primo snappoint venga raggiunto con le condizioni specificate crea uno snapshot. Se si dispone di più snappoints, snapshot successive provenire dalla stessa istanza che ha creato il primo snapshot. Logpoints inviato alla finestra di output verranno visualizzati solo i messaggi da un'istanza, mentre logpoints inviati ad registri applicazioni di inviare messaggi da ogni istanza. 

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>La modalità con cui il Debugger di Snapshot caricare i simboli?

Il Debugger di Snapshot è necessario avere i simboli corrispondenti per l'applicazione sia in locale o distribuita del servizio App di Azure (file PDB incorporati non sono attualmente supportate). Il Debugger di Snapshot vengono scaricati automaticamente simboli dal servizio App di Azure. A partire da Visual Studio 2017 versione 15.2, inoltre, la distribuzione di servizio App di Azure distribuisce i simboli dell'applicazione.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Il Debugger Snapshot funziona su build di rilascio dell'applicazione?

Sì, il Debugger di Snapshot è progettato per funzionare con le build di rilascio. Quando un snappoint viene posizionato in una funzione, viene ricompilata la funzione di una versione di debug, rendendo possibile eseguire il debug. Quando si arresta il Debugger di Snapshot, le funzioni vengono restituite per le build di rilascio. 

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Se logpoints possono avere effetti collaterali nell'applicazione di produzione?

No - Aggiungi all'app eventuali messaggi di log vengono valutate virtualmente. Non è possibile provocano effetti collaterali nell'applicazione. Tuttavia, alcune proprietà nativa non sia accessibile con logpoints. 

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Se il server è in condizioni di carico, il Debugger Snapshot funziona correttamente?

Sì, il debug di snapshot è possibile utilizzare per i server in condizioni di carico. Il Debugger Snapshot limita e non di acquisire snapshot nelle situazioni in cui è presente una bassa quantità di memoria disponibile sul server.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Come è possibile disinstallare il Debugger Snapshot?

È possibile disinstallare l'estensione del Debugger di Snapshot del sito nel servizio App con i passaggi seguenti:

1. Disattivare il servizio App tramite il Cloud Explorer in Visual Studio o il portale di Azure.
1. Passare al sito Kudu del servizio App (vale a dire yourappservice. **Gestione controllo servizi**. azurewebsites.net) e passare a **sito estensioni**.
1. Fare clic sulla X nell'estensione del Debugger di Snapshot del sito per rimuoverlo.

## <a name="see-also"></a>Vedere anche

[Debug in Visual Studio](../debugger/index.md)  
[Eseguire il debug in tempo reale App ASP.NET utilizzando il Debugger di Snapshot](../debugger/debug-live-azure-applications.md)  
[Risoluzione dei problemi e problemi noti per il debug dello snapshot](../debugger/debug-live-azure-apps-troubleshooting.md)
