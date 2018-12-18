---
title: Profilare le prestazioni delle applicazioni in Visual Studio | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 02/27/2017
ms.technology: vs-ide-debug
ms.topic: tutorial
f1_keywords:
- vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
- CPU Usage
- Diagnostics Tools
ms.assetid: da2fbf8a-2d41-4654-a509-dd238532d25a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f4415956aaa819881584b4298285ff878c1d7ccf
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="profile-application-performance-in-visual-studio"></a>Profilare le prestazioni delle applicazioni in Visual Studio
È possibile usare gli strumenti di profilatura di Visual Studio per analizzare i problemi di prestazioni nell'applicazione. Questa procedura illustra come usare la scheda **Utilizzo CPU** della finestra Strumenti di diagnostica per ottenere i dati relativi alle prestazioni per l'applicazione. Gli strumenti di diagnostica sono supportati per lo sviluppo di .NET in Visual Studio, incluso ASP.NET, e per lo sviluppo nativo/C++.
  
Durante le pause del debug, lo strumento **Utilizzo CPU** raccoglie informazioni sulle funzioni in esecuzione nell'applicazione. Vengono indicate le funzioni che stavano eseguendo un'operazione e un grafico della sequenza temporale consente di concentrarsi su segmenti specifici della sessione di campionamento.

L'hub diagnostica include numerose altre opzioni per eseguire e gestire la sessione di diagnostica. Se **Utilizzo CPU** non offre i dati necessari, gli [altri strumenti di profilatura](../profiling/Profiling-Tools.md) mettono a disposizione diversi di informazioni che possono risultare utili. In molti casi il collo di bottiglia delle prestazioni dell'applicazione può dipendere da un fattore diverso dalla CPU, ad esempio la memoria, il rendering dell'interfaccia utente o il tempo di richiesta di rete. L'hub diagnostica offre molte altre opzioni per la registrazione e l'analisi di questo tipo di dati.

|         |         |
|---------|---------|
|  ![icona della telecamera](../install/media/video-icon.png "Guardare un video")  |    [Guardare un video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Profiling-with-Diagnostics-Tools-in-Visual-Studio-2017-daHnzMD6D_9211787171) sull'uso degli strumenti di diagnostica che illustra come analizzare l'utilizzo della CPU e l'utilizzo della memoria. |

In questo argomento viene illustrata l'analisi dell'utilizzo della CPU nel normale flusso di lavoro di debug. È anche possibile analizzare l'utilizzo della CPU senza un debugger collegato o usando un'app in esecuzione. Per altre informazioni, vedere [Raccogliere dati di profilatura senza il debug](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) in [Eseguire gli strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

> [!NOTE]
> Per .NET Core e ASP.NET Core, lo strumento Utilizzo CPU non offre attualmente risultati accurati con i file PBD portabili. Usare invece file PDB completi.

In questa esercitazione si eseguono le attività seguenti:

> [!div class="checklist"]
> * Raccogliere i dati di Utilizzo CPU
> * Analizzare i dati d'uso della CPU
  
##  <a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Passaggio 1: Raccogliere i dati di profilatura 
  
1.  Aprire il progetto per cui si vuole eseguire il debug in Visual Studio e impostare un punto di interruzione nell'applicazione in corrispondenza del punto in cui si vuole esaminare l'utilizzo della CPU.

2.  Impostare un secondo punto di interruzione alla fine della funzione o dell'area di codice da analizzare.

    > [!TIP]
    > Impostando i due punti di interruzione è possibile limitare la raccolta dei dati per le parti di codice che si vuole analizzare.
  
3.  La finestra **Strumenti di diagnostica** viene visualizzata automaticamente, a meno che non sia stata disattivata. Per visualizzare di nuovo la finestra, fare clic su **Debug/Windows/Mostra strumenti di diagnostica**.

4.  È possibile scegliere se visualizzare **Utilizzo CPU**, [Utilizzo memoria](../profiling/Memory-Usage.md) o entrambi usando l'impostazione **Seleziona strumenti** della barra degli strumenti. Se si usa Visual Studio Enterprise, è anche possibile abilitare o disabilitare IntelliTrace in **Strumenti/Opzioni/IntelliTrace**.

     ![Mostra strumenti di diagnostica](../profiling/media/DiagToolsSelectTool.png "DiagToolsSelectTool")

     In questa sede ci si occupa principalmente dell'utilizzo della CPU, quindi verificare che l'opzione **Utilizzo CPU** è abilitata (è abilitata per impostazione predefinita).

5.  Fare clic su **Debug / Avvia debug** (o **Avvia** sulla barra degli strumenti o **F5**).

     Al termine del caricamento dell'applicazione viene visualizzato il riepilogo degli strumenti di diagnostica.

     ![Strumenti di diagnostica Scheda Riepilogo](../profiling/media/DiagToolsSummaryTab.png "DiagToolsSummaryTab")

     Per altre informazioni sugli eventi, vedere l'articolo relativo a come [eseguire ricerche e applicare filtri nella scheda Eventi della finestra Strumenti di diagnostica](http://blogs.msdn.com/b/visualstudioalm/archive/2015/11/12/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window.aspx)

6.  Eseguire lo scenario in cui viene raggiunto il primo punto di interruzione.

7.  Quando il debugger è in pausa, abilitare la raccolta dei dati relativi all'utilizzo della CPU e quindi aprire la scheda **Utilizzo CPU**.

     ![Strumenti di diagnostica - Abilitare profilatura CPU](../profiling/media/DiagToolsEnableCPUProfiling.png "DiagToolsEnableCPUProfiling")

     Quando si sceglie **Registra profilo CPU** Visual Studio avvia la registrazione delle funzioni e del tempo necessario per eseguirle. È possibile visualizzare i dati raccolti solo quando l'applicazione viene interrotta in un punto di interruzione.

8.  Premere F5 per eseguire l'applicazione fino al secondo punto di interruzione.

     Ora si hanno a disposizione i dati relativi alle prestazioni per l'applicazione, precisamente per l'area di codice compresa tra i due punti di interruzione.

9.  Selezionare l'area da analizzare nella sequenza temporale della CPU (deve essere un'area che indica dati di profilatura).

     ![Strumenti di diagnostica Selezione di un segmento di tempo](../profiling/media/DiagToolsSelectTimeSegment.png "DiagToolsSelectTimeSegment")

     Il profiler inizia a preparare i dati di thread. Attendere il completamento.

     ![Strumenti di diagnostica - Preparazione thread](../profiling/media/DiagToolsPreparingThreads.png "DiagToolsPreparingThreads")
  
     Lo strumento Utilizzo CPU consente di visualizzare il report nella scheda **Utilizzo CPU**.
  
     ![Strumenti di diagnostica - Scheda Utilizzo CPU](../profiling/media/DiagToolsCPUUsageTab.png "DiagToolsCPUUsageTab")

     A questo punto, è possibile iniziare ad analizzare i dati.

## <a name="Step2"></a> Passaggio 2: Analizzare i dati di utilizzo della CPU

È consigliabile iniziare ad analizzare i dati esaminando l'elenco di funzioni in Utilizzo CPU, identificando le funzioni che svolgono la maggior parte del lavoro e quindi concentrandosi su ognuna di esse.

1. Nell'elenco delle funzioni esaminare le funzioni che eseguono il maggior numero di operazioni.

    ![Strumenti di diagnostica Elenco funzioni di Utilizzo CPU](../profiling/media/DiagToolsCPUUsageFunctionList.png "DiagToolsCPUUsageFunctionList")

    > [!TIP]
    > Le funzioni sono elencate in ordine a partire da quelle che svolgono la maggior parte del lavoro (non sono in ordine di chiamata). Ciò consente di identificare rapidamente le funzioni in esecuzione da più tempo.

2. Nell'elenco delle funzioni fare doppio clic su una delle funzioni dell'applicazione che esegue molte operazioni.

    Quando si fa doppio clic su una funzione viene aperta la visualizzazione **Chiamante/Chiamato** nel riquadro a sinistra. 

    ![Strumenti di diagnostica Visualizzazione Chiamante Chiamato](../profiling/media/DiagToolsCallerCallee.png "DiagToolsCallerCallee")

    In questa visualizzazione la funzione selezionata viene visualizzata nell'intestazione e nella casella **Funzione corrente** (GetNumber, in questo esempio). La funzione che ha chiamato la funzione corrente viene visualizzata a sinistra, sotto **Funzioni chiamanti**, e tutte le funzioni chiamate dalla funzione corrente sono riportate nella casella **Funzioni chiamate** sulla destra. Selezionare una delle due caselle per modificare la funzione corrente.

    Questa visualizzazione indica il tempo totale (ms) e la percentuale del tempo complessivo di esecuzione dell'applicazione dedicato al completamento della funzione.
    **Corpo funzione** indica anche la quantità totale di tempo (e la percentuale di tempo) impiegata nel corpo della funzione, escluso il tempo dedicato alle funzioni chiamanti e chiamate. In questo esempio 3713 su 3729 ms sono stati usati nel corpo della funzione e i 16 ms rimanenti nel codice esterno chiamato dalla funzione.

    > [!TIP]
    > Valori elevati in **Corpo funzione** possono indicare un collo di bottiglia delle prestazioni all'interno della funzione stessa.

3. Per una visualizzazione di livello superiore in cui appaia l'ordine in cui le funzioni vengono chiamate, selezionare **Albero delle chiamate** dall'elenco a discesa nella parte superiore del riquadro.
 
    Ogni area numerata nella figura si riferisce a un passaggio della procedura.
  
    ![Strumenti di diagnostica Albero delle chiamate](../profiling/media/DiagToolsCallTree.png "DiagToolsCallTree")
  
|||
|-|-|
|![Passaggio 1](../profiling/media/ProcGuid_1.png "ProcGuid_1")|Il nodo di livello principale nell'albero delle chiamate di Utilizzo CPU è uno pseudo-nodo|  
|![Passaggio 2](../profiling/media/ProcGuid_2.png "ProcGuid_2")|Nella maggior parte delle app, quando l'opzione [Mostra codice esterno](#BKMK_External_Code) è disabilitata, il nodo di secondo livello è un nodo **[Codice esterno]** contenente il codice di sistema e di framework che avvia e arresta l'app, disegna l'interfaccia utente, controlla la pianificazione dei thread e fornisce altri servizi di basso livello all'app.|  
|![Passaggio 3](../profiling/media/ProcGuid_3.png "ProcGuid_3")|Gli elementi figlio del nodo di secondo livello sono i metodi del codice utente e le routine asincrone che vengono chiamati o creati dal codice di sistema o di framework di secondo livello.|
|![Passaggio 4](../profiling/media/ProcGuid_4.png "ProcGuid_4")|I nodi figlio di un metodo contengono i dati solo per le chiamate del metodo padre. Quando l'opzione **Mostra codice esterno** è disabilitata, i metodi dell'app possono contenere anche un nodo **[Codice esterno]** .|

Di seguito sono riportate altre informazioni sui valori di colonna:

- **CPU totale** indica la quantità di lavoro svolta dalla funzione e dalle funzioni chiamate dalla funzione. Valori elevati di CPU totale indicano le funzioni più dispendiose in generale.
  
- **CPU auto** indica la quantità di operazioni eseguite dal codice nel corpo della funzione, escluse quelle eseguite dalle funzioni chiamate dalla funzione. Valori elevati di **CPU auto** possono indicare un collo di bottiglia delle prestazioni all'interno della funzione stessa.

- **Moduli** Nome del modulo contenente la funzione o numero dei moduli contenenti le funzioni in un nodo [Codice esterno].

## <a name="BKMK_External_Code"></a> Visualizzare codice esterno

Il codice esterno rappresenta funzioni nei componenti del sistema e del framework che vengono eseguite dal codice scritto. Include funzioni che avviano e arrestano l'app, disegnano l'interfaccia utente, controllano il threading e forniscono altri servizi di basso livello all'app. Nella maggior parte dei casi il codice esterno è poco interessante, per questo motivo lo strumento Utilizzo CPU raccoglie le funzioni esterne di un metodo utente in un unico nodo **[Codice esterno]** .
  
Per visualizzare i percorsi delle chiamate del codice esterno, scegliere **Mostra codice esterno** dall'elenco **Visualizzazione filtro** e quindi scegliere **Applica**.  
  
![Scegliere Visualizzazione filtro, quindi Mostra codice esterno](../profiling/media/DiagToolsShowExternalCode.png "DiagToolsShowExternalCode")  
  
Tieni presente che numerose catene di chiamate del codice esterno sono molto annidate, pertanto la larghezza della colonna Nome funzione può superare la larghezza di visualizzazione in quasi tutti i monitor, ad eccezione di quelli più grandi. Quando ciò si verifica, i nomi delle funzioni sono visualizzati come **[…]**.
  
Usare la casella di ricerca per trovare un nodo che si sta cercando, quindi usare la barra di scorrimento orizzontale per visualizzare i dati.

> [!TIP]
> Se si profila il codice esterno che chiama le funzioni di Windows, è necessario verificare di avere i file PDB più aggiornati. Senza questi file, le visualizzazioni dei rapporti elencherà i nomi delle funzioni di Windows enigmatici e difficile da comprendere. Per altre informazioni su come verificare di avere i file necessari, vedere [Specify Symbol (.pdb) and Source Files in the Debugger](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) (Specificare file di simboli (PDB) e di origine nel debugger).

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come raccogliere e analizzare i dati d'uso della CPU. Se è già stato completata la [presentazione del profiler](../profiling/profiling-feature-tour.md), è possibile vedere come analizzare l'uso della memoria nelle app di Windows.

> [!div class="nextstepaction"]
> [Analizzare l'uso della memoria](../profiling/memory-usage.md) 
