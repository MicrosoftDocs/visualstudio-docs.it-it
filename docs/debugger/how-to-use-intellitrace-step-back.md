---
title: Visualizzare uno snapshot tramite il passaggio di IntelliTrace-back - Visual Studio | Documenti Microsoft
ms.description: Learn how to take snapshots, and view snapshots with IntelliTrace step-back
ms.custom: mvc
ms.date: 12/06/2017
ms.technology:
- vs-ide-debug
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc6450da4e103e5cd5a18f03df3116cb805a9983
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="view-snapshots-using-intellitrace-step-back-in-visual-studio"></a>Visualizzazione di snapshot tramite IntelliTrace passaggio-back in Visual Studio

Passaggio di IntelliTrace-back automaticamente un'istantanea dell'applicazione in ogni punto di interruzione e il debugger evento di passaggio. Gli snapshot registrati consentono di tornare indietro ai punti di interruzione o ai passaggi precedenti e visualizzare stati passati dell'applicazione. La funzionalità per tornare indietro di IntelliTrace può consentire di risparmiare tempo quando si vuole visualizzare uno stato precedente dell'applicazione senza riavviare il debug o ricreare lo stato dell'app desiderato.

Passaggio di IntelliTrace-back è disponibile a partire da Visual Studio Enterprise 2017 versione 15,5 e versioni successive e richiede l'aggiornamento Aniversary di Windows 10 o versione successiva. La funzionalità è attualmente supportata per il debug di ASP.NET, Windows Form, WPF, le applicazioni console gestito e librerie di classi gestite. A partire da preview 15.7 Visual Studio 2017 Enterprise versione 1, la funzionalità è supportata anche per ASP.NET Core e .NET Core. Debug di applicazioni UWP non è attualmente supportato.

In questa esercitazione si eseguono le attività seguenti:

> [!div class="checklist"]
> * Abilita gli snapshot e gli eventi di Intellitrace
> * Passare gli eventi utilizzando i comandi passaggio-back e forward passaggio
> * Visualizzare gli snapshot di evento
  
## <a name="enable-intellitrace-events-and-snapshots-mode"></a>Abilitare la modalità di eventi e le istantanee di IntelliTrace 

1. Aprire il progetto in Visual Studio Enterprise.

1. Aprire **Tools** > **opzioni** > **IntelliTrace** impostazioni, quindi selezionare l'opzione **IntelliTrace eventi e gli snapshot** . 

    ![Abilitare la modalità di eventi IntelliTrace e snapshot](../debugger/media/intellitrace-enable-snapshots.png "modalità attivare eventi di IntelliTrace e snapshot")

1. Nel progetto, impostare uno o più punti di interruzione e avviare il debug (premere **F5**), o avviare il debug, l'esecuzione passo passo del codice (**F10** oppure **F11**).

    IntelliTrace accetta uno snapshot del processo dell'applicazione nel debugger di ogni evento di passaggio e punto di interruzione. Questi eventi vengono registrati nella **eventi** nella scheda il **strumenti di diagnostica** finestra, insieme agli altri eventi di IntelliTrace. Per aprire questa finestra, scegliere **Debug** > **Windows** > **Mostra strumenti di diagnostica**.

    Viene visualizzata un'icona di fotocamera accanto agli eventi per il quale gli snapshot sono disponibili. 

    ![Scheda eventi con gli snapshot](../debugger/media/intellitrace-events-tab-with-snapshots.png "scheda eventi con snapshot in punti di interruzione e passaggi")

    Per motivi di prestazioni gli snapshot non vengono intraprese quando esegue l'istruzione molto rapidamente. Se nessuna icona fotocamera viene visualizzato accanto al passaggio, provare a esecuzione più lenta.

## <a name="navigate-and-view-snapshots"></a>Esplorare e visualizzare gli snapshot

1. Consente di spostarsi tra gli eventi utilizzando il **passo indietro (Alt + [)** e **passo avanti (Alt +])** pulsanti sulla barra degli strumenti di Debug.

    Questi pulsanti passare gli eventi che vengono visualizzati di **eventi** nella scheda il **finestra Strumenti di diagnostica**. Attiva l'esecuzione di istruzioni in avanti o indietro a un evento automaticamente [debug cronologico](../debugger/historical-debugging.md) sull'evento selezionato.

    ![Passo indietro pulsanti Avanti e indietro](../debugger/media/intellitrace-step-back-icons-description.png "pulsanti passo indietro e Avanti di un passaggio")

    Quando si passo indietro o passo avanti, Visual Studio passa alla modalità di debug cronologica. In questa modalità, il contesto del debugger consente di attivare l'ora in cui è stato registrato l'evento selezionato. Inoltre, Visual Studio sposta il puntatore alla riga di codice nella finestra di origine corrispondente. 

    In questa vista è possibile controllare i valori di **Stack di chiamate**, **variabili locali**, **Auto**, e **espressioni di controllo** windows. È anche possibile passare il mouse sulle variabili per visualizzare i suggerimenti dati ed eseguire la valutazione di espressioni nel **immediato** finestra. I dati visualizzati sono rispetto allo snapshot del processo dell'applicazione effettuato a questo punto nel tempo.

    In questo caso, ad esempio, se hai raggiunto un punto di interruzione ed eseguito un passaggio (**F10**), il **passo indietro** pulsante inserisce Visual Studio in modalità cronologiche alla riga di codice corrispondente al punto di interruzione. 

    ![Attivare la modalità cronologica su un evento con uno snapshot](../debugger/media/intellitrace-historical-mode-with-snapshot.png "attivare la modalità cronologica su un evento con uno snapshot")

2. Per tornare all'esecuzione in tempo reale, scegliere **continua (F5)** oppure fare clic su di **tornare al debug attivo** collegamento sulla barra informazioni. 

3. È inoltre possibile visualizzare uno snapshot dal **eventi** scheda. A tale scopo, selezionare un evento con uno snapshot e fare clic su **attivare debug cronologico**.

    ![Attiva debug cronologico su un evento](../debugger/media/intellitrace-activate-historical-debugging.png "attivare debug cronologico su un evento")

    A differenza di **Imposta istruzione successiva** comando, visualizzazione di uno snapshot non viene rieseguito il codice e offre una visualizzazione statica dello stato dell'applicazione in un punto nel tempo che si è verificato in precedenza.

    ![Panoramica del passaggio di IntelliTrace-back](../debugger/media/intellitrace-step-back-overview.png "Panoramica di IntelliTrace passaggio-back")

    Per ulteriori informazioni su come controllare le variabili in Visual Studio, vedere [tour delle funzionalità del Debugger](../debugger/debugger-feature-tour.md)  

## <a name="frequently-asked-questions"></a>Domande frequenti

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>Come passaggio di IntelliTrace-back è diversa dalla modalità di solo eventi IntelliTrace?

In modalità solo eventi IntelliTrace consente di attivare il debug cronologico in punti di interruzione e i passaggi del debugger. Tuttavia, IntelliTrace acquisisce solo i dati nel **variabili locali** e **Auto** windows, se sono aperte le finestre e acquisisce solo dati che viene espanso e nella visualizzazione. In modalità solo gli eventi, spesso non è una visualizzazione completa delle variabili e oggetti complessi. Inoltre, valutazione e la visualizzazione dati dell'espressione nel **espressioni di controllo** finestra non è supportata. 

In modalità di eventi e gli snapshot, IntelliTrace consente di acquisire l'intero snapshot del processo dell'applicazione, compresi gli oggetti complessi. Nella riga di codice, è possibile visualizzare le stesse informazioni come se non erano in esecuzione in un punto di interruzione (e non è importante se è stato espanso in precedenza le informazioni). Valutazione dell'espressione è supportata anche durante la visualizzazione di uno snapshot.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>Che cos'è l'impatto sulle prestazioni di questa funzionalità? 

L'impatto sulle prestazioni di debug passo a passo generale dipende dall'applicazione. L'overhead di acquisire uno snapshot è circa 30 minuti. Quando viene eseguito uno snapshot, il processo dell'app viene duplicato e la copia con fork viene sospeso. Quando si visualizza uno snapshot, Visual Studio si connette alla copia del processo di scenari. Per ogni snapshot, Visual Studio copia solo la tabella della pagina e imposta le pagine copy-on-write. Se gli oggetti nell'heap modifica tra i passaggi del debugger con gli snapshot associati, la tabella della pagina corrispondente viene quindi copiata, risultante in termini di costo di memoria minimo. Se Visual Studio rileva che non vi è memoria sufficiente per creare uno snapshot, non viene preso uno.
 
## <a name="known-issues"></a>Problemi noti  
* Se si utilizza la modalità di eventi e le istantanee di IntelliTrace nelle versioni di Windows precedente a Windows 10 rientrano creatori di aggiornamento (RS3) e se la piattaforma di destinazione di debug dell'applicazione è impostata su x86, IntelliTrace non istantanee.

    Soluzione alternativa:
    * Installare o eseguire l'aggiornamento a Windows 10 rientrano creatori di aggiornamento (RS3). 
    * In alternativa: 
        1. Installare il componente Set di strumenti VC++ 2015.3 versione 140 per desktop (x86, x64) dal programma di installazione di Visual Studio.
        2. Compilare l'applicazione di destinazione.
        3. Dalla riga di comando, utilizzare lo strumento editbin per impostare il `Largeaddressaware` flag per l'eseguibile di destinazione. Ad esempio, è possibile utilizzare questo comando (dopo aver aggiornato il percorso): "C:\Program Files (x86) \Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe" /Largeaddressaware "C:\Path\To\Application\app.exe".
        4. Premere **F5** per avviare il debug. A questo punto, di snapshot in punti di interruzione e i passaggi del debugger.

        > [!Note]
        > Il `Largeaddressaware` flag deve essere impostato ogni volta che il file eseguibile viene ricompilato con le modifiche.

* Quando viene eseguito uno snapshot del processo dell'applicazione in un'applicazione che utilizza un file mappato alla memoria persistente, il processo con lo snapshot contiene un blocco esclusivo sul file mappato alla memoria (anche dopo il processo padre ha rilasciato il blocco). Altri processi sono ancora in grado di leggere, ma non scrivere al file mappato alla memoria.

    Soluzione alternativa:
    * Deselezionare tutti gli snapshot e di terminare la sessione di debug. 

* Durante il debug di un'applicazione il cui processo ha un numero elevato di aree di memoria univoco, ad esempio un'applicazione che carica un numero elevato di DLL, potrebbe essere compromesso l'esecuzione di istruzioni delle prestazioni con gli snapshot abilitati. Questo problema verrà risolto in una versione futura di Windows. Se il problema, contattare Microsoft all'indirizzo stepback@microsoft.com. 

* Quando si salva un file con **Debug > IntelliTrace > sessione di IntelliTrace Salva** in modalità di eventi e gli snapshot, i dati aggiuntivi acquisiti da snapshot non sono disponibili nel file. iTrace. Nel punto di interruzione e il passaggio degli eventi, vedere le stesse informazioni come se il file è stato salvato in modalità solo gli eventi di IntelliTrace. 

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione appreso come utilizzare IntelliTrace passaggio-back. È possibile per altre informazioni sulle altre funzionalità di IntelliTrace.

> [!div class="nextstepaction"]
> [Funzionalità IntelliTrace](../debugger/intellitrace-features.md)
