---
title: Risoluzione dei problemi e problemi noti per il debug di snapshot | Documenti Microsoft
ms.date: 11/07/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7340b5f6ce7e9f8cbcbb0e2673b22712b3ab45a3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Risoluzione dei problemi e problemi noti per il debug di snapshot in Visual Studio

Se i passaggi descritti in questo argomento non risolvono il problema, contattare snaphelp@microsoft.com.

## <a name="issue-snappoint-does-not-turn-on"></a>Problema: Snappoint non attivata

Se viene visualizzata un'icona di avviso ![icona di avviso Snappoint](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "icona di avviso Snappoint") con il snappoint anziché l'icona normale snappoint, quindi il snappoint non è acceso.

![Non attivare Snappoint](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Snappoint non attiva")

Eseguire la procedura seguente:

1. Accertarsi di avere la stessa versione del codice sorgente utilizzato per compilare e distribuire il app.isua1. Verificare che il caricamento di simboli corretti per la distribuzione. A tale scopo, è possibile visualizzare il **moduli** finestra durante il debug di Snapshot e verificare la colonna del File di simboli viene illustrato un file con estensione pdb caricato per il modulo a cui si esegue il debug. Si noti che il Debugger Snapshot tenterà automaticamente di scaricare e usare i simboli per la distribuzione.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problema: I simboli non vengono caricati quando si apre uno Snapshot

Se viene visualizzato in seguito finestra, i simboli non è stato caricato.

![Non vengono caricati i simboli](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "non vengono caricati i simboli")

Eseguire la procedura seguente:

- Fare clic sul **modificare le impostazioni dei simboli...** collegamenti in questa pagina. Nel **Debug > simboli** impostazioni, aggiungere una directory cache dei simboli. Riavviare il debug di snapshot dopo aver impostato il percorso dei simboli.

   I simboli o file con estensione pdb, disponibili nel progetto devono corrispondere la distribuzione del servizio App. La maggior parte delle distribuzioni (distribuzione tramite Visual Studio, CI/CD con Visual Studio Team Services o Kudu, e così via) verranno pubblicare i file di simboli insieme al servizio App. Impostazione directory cache dei simboli consente a Visual Studio utilizzare questi simboli.

   ![Impostazioni dei simboli](../debugger/media/snapshot-troubleshooting-symbol-settings.png "le impostazioni dei simboli")

- In alternativa, se l'organizzazione utilizza un server di simboli o Elimina i simboli in un percorso diverso, è possibile utilizzare le impostazioni dei simboli per caricare i simboli appropriati per la distribuzione.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problema: non è possibile visualizzare l'opzione "Collega Debugger Snapshot" in Cloud Explorer

Eseguire la procedura seguente:

- Verificare che sia installato il componente del Debugger di Snapshot. Aprire il programma di installazione Visual Studio e controllare il **Debugger Snapshot** componente nel carico di lavoro Azure.
- Verificare che l'app sia supportato. Attualmente, solo ASP.NET (4.6.1+) e sono supportate le applicazioni ASP.NET Core (2.0 +) distribuite ai servizi di App di Azure.

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problema: vedere solo gli snapshot limitate negli strumenti di diagnostica

![Throttled snappoint](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "limitate snappoint")

Eseguire la procedura seguente:

- Gli snapshot occupano molto spazio di memoria, ma dispongono di un addebito di commit. Se il Debugger Snapshot rileva che il server è in condizioni di carico elevato della memoria, non passerà snapshot. È possibile eliminare gli snapshot già acquisiti interrompendo la sessione del Debugger di Snapshot e riprovare.

## <a name="known-issues"></a>Problemi noti

- Debug di snapshot con più client di Visual Studio con lo stesso servizio App non è attualmente supportato.
- Ottimizzazioni IL Roslyn non sono completamente supportate nei progetti ASP.NET Core. Per alcuni progetti ASP.NET Core, potrebbe non essere in grado di visualizzare alcune variabili o utilizzare alcune variabili nelle istruzioni condizionali. 
- Variabili speciali, ad esempio *$FUNCTION* o *$CALLER*, non può essere valutato nelle istruzioni condizionali o logpoints per i progetti ASP.NET Core.
- Debug di snapshot non funziona in servizi di App che hanno [memorizzazione nella cache locale](/azure/app-service/app-service-local-cache) acceso.
- Debug di App per le API di snapshot non è attualmente supportato.

## <a name="site-extension-upgrade"></a>Aggiornamento di estensione del sito

Debug di snapshot e Application Insights dipendono da un ICorProfiler Carica nel processo del sito che causa problemi di blocco del file durante l'aggiornamento. Si consiglia di questo processo per verificare che sia presente alcun tempo di inattività per il sito di produzione.

- Creare un [Slot di distribuzione](/azure/app-service/web-sites-staged-publishing) all'interno del servizio App e il sito è stato distribuito nello slot.
- Scambiare lo Slot di produzione da Cloud Explorer in Visual Studio o dal portale di Azure.
- Arrestare il sito di Slot. L'operazione richiederà alcuni secondi per terminare il processo w3wp.exe di sito da tutte le istanze.
- Aggiornare l'estensione di uno Slot del sito dal sito Kudu o il portale di Azure (*Pannello di servizio App > Strumenti di sviluppo > estensioni > aggiornamento*).
- Avviare il sito di Slot. Si consiglia di visitare il sito per il riscaldamento nuovamente.
- Scambiare lo Slot di produzione.

## <a name="see-also"></a>Vedere anche

[Debug in Visual Studio](../debugger/index.md)  
[Eseguire il debug in tempo reale App ASP.NET utilizzando il Debugger di Snapshot](../debugger/debug-live-azure-applications.md)  
[Domande frequenti sul debug di snapshot](../debugger/debug-live-azure-apps-faq.md)  
