---
title: Informazioni generali sul rapporto di prestazioni | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools, about performance rerports
- performance, reports
- performance reports, about performance reports
ms.assetid: 7324c24c-fd09-479b-b2ad-e0c3b613e040
caps.latest.revision: "45"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 915f7f3cbbee87f72c4643b8c5a2b4497bbd69dd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="performance-report-overview"></a>Informazioni generali sul rapporto di prestazioni
È possibile visualizzare i dati di profilatura di una sessione di prestazioni nella finestra **Rapporto di prestazioni** dell'ambiente di sviluppo integrato (IDE) di Visual Studio Team System Development Edition. I dati di profilatura vengono salvati in file con estensione vsp e vsps. Le finestre delle visualizzazioni dei rapporti consentono di visualizzare e analizzare i problemi relativi alle prestazioni delle applicazioni.  
  
> [!CAUTION]
>  Un file di dati di profilatura contiene informazioni riservate quali il nome del computer, la versione del sistema operativo, i percorsi dei file, le informazioni sulla memoria e altri dati relativi alle impostazioni del computer. È necessario un controllo rigoroso della distribuzione dei dati, sia nel formato nativo con estensione vsp che nel formato di esportazione in un file con estensione csv o xml.  
>   
>  Se durante la sessione di prestazioni vengono raccolti dati di traccia eventi, è possibile che nel file di log di traccia eventi (con estensione etl) siano visualizzate informazioni aggiuntive, come il nome utente e il dominio. Sarà pertanto necessario controllare rigorosamente anche la distribuzione del file di log.  
  
## <a name="performance-report-window"></a>Finestra Rapporto di prestazioni  
 La finestra Rapporto di prestazioni fornisce gli strumenti per visualizzare, gestire e filtrare i dati sulle prestazioni e include un controllo query personalizzabile.  
  
 Nella barra degli strumenti principale della finestra Rapporto di prestazioni è possibile accedere a ognuna delle visualizzazioni. Fare clic sulla freccia accanto all'elenco **Visualizzazione corrente** per visualizzare e selezionare le singole visualizzazioni disponibili.  
  
 La finestra Rapporto di prestazioni offre le visualizzazioni di dati seguenti:  
  
### <a name="summary-view"></a>Visualizzazione Riepilogo  
 Per impostazione predefinita, i dati di profilatura vengono visualizzati nella visualizzazione Riepilogo, che rappresenta il punto di partenza per la ricerca finalizzata all'identificazione dei problemi di prestazioni. Da ogni riga della visualizzazione Riepilogo è possibile passare a visualizzazioni più dettagliate facendo clic con il pulsante destro del mouse sul nome della funzione o del modulo. Per altre informazioni, vedere [Visualizzazione Riepilogo](../profiling/summary-view.md).  
  
### <a name="callercallee-view"></a>Visualizzazione Chiamante/chiamato  
 La visualizzazione Chiamante/chiamato consente di visualizzare un albero delle chiamate per una singola funzione. La visualizzazione è suddivisa in tre sezioni:  
  
-   La funzione di destinazione viene riportata nella parte centrale della visualizzazione.  
  
-   Le funzioni che hanno chiamato la funzione (chiamanti) vengono visualizzate sopra la funzione di destinazione.  
  
-   Le funzioni che sono chiamate dalla funzione di destinazione (chiamate) sono visualizzate sotto la destinazione.  
  
 È possibile selezionare una funzione diversa facendo doppio clic su qualsiasi funzione nell'elenco delle funzioni chiamanti o chiamate. Per altre informazioni, vedere [Visualizzazione Chiamante/chiamato](../profiling/caller-callee-view.md).  
  
### <a name="call-tree-view"></a>Visualizzazione Albero delle chiamate  
 La visualizzazione Albero delle chiamate consente di visualizzare i percorsi di esecuzione della funzione usati nell'applicazione profilata. La radice dell'albero è il punto di ingresso nell'applicazione o nel componente. Per ogni nodo della funzione vengono elencate tutte le funzioni chiamate e i dati delle prestazioni delle relative chiamate di funzione.  
  
 Nella visualizzazione Albero delle chiamate è anche possibile espandere ed evidenziare il percorso di esecuzione di una funzione che ha richiesto più tempo o che è stata campionata con maggiore frequenza. Per visualizzare il percorso più attivo, fare clic con il pulsante destro del mouse sulla funzione e quindi scegliere **Espandi percorso critico**. Per altre informazioni, vedere [Visualizzazione Albero delle chiamate](../profiling/call-tree-view.md).  
  
### <a name="process-view"></a>Visualizzazione Processo  
 La visualizzazione Processo consente di visualizzare i dati sulle prestazioni per ogni processo e thread profilato. Per altre informazioni, vedere [Visualizzazione Processo](../profiling/process-view.md).  
  
### <a name="modules-view"></a>Visualizzazione Moduli  
 La visualizzazione Moduli elenca i moduli nel progetto e presenta i dati di profilatura per ogni modulo. Espandere o comprimere il nome del modulo per visualizzare i dati di profilatura della funzione. Quando i dati vengono raccolti tramite campionamento, sono disponibili anche i dati di profilatura delle righe del codice sorgente e dei puntatori alle istruzioni. Per altre informazioni, vedere [Visualizzazione Moduli](../profiling/modules-view.md).  
  
### <a name="functions-view"></a>Visualizzazione Funzioni  
 La visualizzazione Funzioni elenca le funzioni chiamate durante la profilatura. Per altre informazioni, vedere [Visualizzazione Funzioni](../profiling/functions-view.md).  
  
### <a name="line-view"></a>Visualizzazione Righe  
 La visualizzazione Righe consente di visualizzare le righe del codice sorgente specifiche che sono state eseguite durante la profilatura di campionamento. Per altre informazioni, vedere [Visualizzazione Righe](../profiling/lines-view.md).  
  
### <a name="instruction-pointer-ip-view"></a>Visualizzazione Puntatore all'istruzione  
 La visualizzazione Puntatore all'istruzione consente di visualizzare istruzioni specifiche eseguite durante la profilatura del campionamento. Per altre informazioni, vedere [Visualizzazione Puntatore all'istruzione](../profiling/instruction-pointers-ips-view.md).  
  
### <a name="allocation-view"></a>Visualizzazione Allocazione  
 La visualizzazione Allocazione è disponibile se è stata selezionata l'opzione **Raccogliere le informazioni sull'allocazione dell'oggetto .NET** nella pagina **Generale** della finestra di dialogo delle proprietà **Sessione prestazioni**. Vedere [Panoramica delle sessioni di prestazioni](../profiling/performance-session-overview.md). La visualizzazione Allocazione elenca gli oggetti .NET che sono stati allocati dall'applicazione o dal componente. Quando si espande una riga dell'oggetto, viene visualizzato un albero delle chiamate, che indica i percorsi di esecuzione usati per la creazione dell'oggetto. Nell'albero delle chiamate vengono anche visualizzate le informazioni sul numero delle allocazioni inclusive ed esclusive per ogni funzione. Nella visualizzazione Allocazione è anche possibile espandere ed evidenziare il percorso di esecuzione di una funzione che ha allocato il maggior numero di oggetti. Per visualizzare il percorso più attivo, fare clic con il pulsante destro del mouse sulla funzione e quindi scegliere **Espandi percorso critico**. Per altre informazioni, vedere [Raccolta di dati di durata e allocazione di memoria .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) e [Visualizzazione Allocazioni](../profiling/dotnet-memory-allocations-view.md).  
  
### <a name="objects-lifetime-view"></a>Visualizzazione Durata oggetti  
 La visualizzazione Durata oggetti è disponibile se sono state selezionate le opzioni **Raccogliere le informazioni sull'allocazione dell'oggetto .NET** e **Raccogliere anche le informazioni sulla durata dell'oggetto .NET** nella pagina **Generale** della finestra di dialogo delle proprietà **Sessione prestazioni**.  
  
 La visualizzazione Durata oggetti consente di visualizzare il numero totale di istanze di ogni tipo e il numero di oggetti raccolti in ogni generazione di Garbage Collection. Per altre informazioni, vedere [Visualizzazione Durata oggetti](../profiling/object-lifetime-view.md).  
  
## <a name="customizable-filter-control"></a>Controllo filtro personalizzabile  
 Il controllo filtro personalizzabile presenta le opzioni seguenti:  
  
-   **Importa filtro**: recupera una query personalizzata precedentemente salvata.  
  
-   **Esporta filtro**: salva la query personalizzata nel percorso specificato.  
  
-   **Esegui query**: esegue la query come visualizzata nel controllo query personalizzato.  
  
-   **Interrompi query**: interrompe l'esecuzione di una query in esecuzione. Questo pulsante non è disponibile se non è in esecuzione alcuna query.  
  
-   **Mostra query**: mostra/nasconde il controllo query personalizzato.  
  
-   **Salva dati analizzati**: salva il rapporto con l'analisi corrente come file con estensione vsps.  
  
-   **Esporta**: salva il rapporto corrente come file in formato cvs o xml, con opzioni per salvare le diverse visualizzazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Analisi dei dati degli strumenti per le prestazioni](../profiling/analyzing-performance-tools-data.md)   
 [Visualizzazioni dei rapporti di prestazioni](../profiling/performance-report-views.md)