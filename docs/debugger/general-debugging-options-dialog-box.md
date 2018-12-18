---
title: Generale, debug, finestra di dialogo Opzioni | Documenti Microsoft
ms.custom: 
ms.date: 05/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords: Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
caps.latest.revision: "46"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c7f6983c2be5604867f729ed006eadb5257c3a43
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="general-debugging-options-dialog-box"></a>Generale, Debug, finestra di dialogo Opzioni
Il **strumenti > Opzioni > Debug > Generale** pagina consente di impostare le opzioni seguenti:  
  
**Chiedi prima di eliminare tutti i punti di interruzione**  
Richiede conferma prima dell'esecuzione di **eliminare tutti i punti di interruzione** comando.  
  
**Quando si interrompe un processo, interrompi tutti i processi**  
Interrompe simultaneamente tutti i processi a cui è connesso il debugger quando si verifica un'interruzione.  
  
**Interrompi quando le eccezioni superano il dominio dell'applicazione o i limiti gestiti/nativi**  
Durante il debug in modalità gestita o mista, Common Language Runtime è in grado di rilevare eccezioni che superano i limiti del dominio applicazione o i limiti gestiti/nativi quando sono vere le seguenti condizioni:  
  
1\) quando il codice nativo chiama codice gestito mediante interoperabilità COM e il codice gestito genera un'eccezione. Vedere [Introduzione all'interoperabilità COM](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).  
  
2\) quando il codice gestito in esecuzione nel dominio applicazione 1 chiama il codice gestito nel dominio applicazione 2 e il codice nel dominio applicazione 2 genera un'eccezione. Vedere [programmazione con i domini applicazione](/dotnet/articles/framework/app-domains/index).  

3\) quando viene richiamata la funzione tramite reflection e la funzione genera un'eccezione. Vedere [Reflection](/dotnet/framework/reflection-and-codedom/reflection).  
  
Nella condizione 2 e 3, l'eccezione viene talvolta intercettata dal codice gestito in `mscorlib` anziché da common language runtime. Questa opzione non influisce sull'interruzione di eccezioni intercettate da `mscorlib`.  
  
**Abilitare il debug a livello di indirizzo**  
 Abilita le funzionalità avanzate per il debug a livello di indirizzo (il **Disassembly** finestra il **registra** finestra e punti di interruzione).  
  
- **Mostra disassembly se l'origine non è disponibile**  
    Visualizza automaticamente la **Disassembly** finestra quando si tenta di eseguire il debug di codice per l'origine non è disponibile.  
  
**Abilita i filtri dei punti di interruzione**  
Consente di applicare filtri ai punti di interruzione in modo che abbiano effetto solo su determinati processi, thread o computer.  
 
**Utilizzare il nuovo Helper eccezioni**  
Abilita il supporto delle eccezioni (Visual Studio 2017) che sostituisce l'Assistente per l'eccezione.
  
> [!NOTE]
> Per codice gestito, questa opzione è stato precedentemente chiamata **Abilita informazioni sulle eccezioni** . 
  
**Abilitare Just My Code**  
Il debugger visualizza ed esegue solo il codice utente ("My Code"), ignorando il codice di sistema e altro codice ottimizzato o privo di simboli di debug.

- **Avvisa se il codice non utente all'avvio (solo gestito)**  
    Quando il debug viene avviato con Just My Code attivato, questa opzione determina la visualizzazione di un avviso se non è presente codice utente ("My Code"). 

**Abilitare .NET Framework esecuzione di istruzioni origine**  
Consente al debugger di eseguire l'origine di .NET Framework. L'abilitazione di questa opzione disabilita automaticamente Just My Code. I simboli .NET Framework saranno scaricati in un percorso della cache. È possibile modificare il percorso della cache nel **opzioni** nella finestra di dialogo **debug** categoria **simboli** pagina.  
  
**Esegui istruzione/routine di proprietà e operatori (solo gestito)**  
Impedisce al debugger di eseguire istruzioni di proprietà e operatori nel codice gestito.  
  
**Abilita valutazione delle proprietà e altre chiamate di funzioni implicite**  
Chiama attiva la valutazione automatica delle proprietà e di funzioni implicite nelle finestre delle variabili e **controllo immediato** la finestra di dialogo.  
  
- **Chiamare la funzione di conversione stringa sugli oggetti nelle finestre delle variabili (c# e JavaScript solo)**  
    Esegue una chiamata di conversione delle stringhe implicita durante la valutazione di oggetti nelle finestre delle variabili. Pertanto, il risultato viene visualizzato come stringa anziché come nome del tipo. Questa opzione è applicabile solo al debug in codice C#. Questa impostazione può essere sostituita dall'attributo DebuggerDisplay (vedere [utilizzando l'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).  
  
**Abilita il supporto di server di origine**  
Indica al debugger di Visual Studio di ottenere i file di origine da server di origine che implementano il protocollo di SrcSrv (`srcsrv.dll`). Team Foundation Server e gli strumenti di debug per Windows sono due server di origine che implementano il protocollo. Per ulteriori informazioni sull'installazione di SrcSrv, vedere il [SrcSrv](https://msdn.microsoft.com/library/windows/hardware/ff558791(v=vs.85).aspx) documentazione. Inoltre, vedere [specificare simboli (PDB) e file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
>  Poiché la lettura dei file PDB può determinare l'esecuzione del codice arbitrario nei file, assicurarsi di ritenere attendibile il server.  
  
- **Messaggi di diagnostica server di origine nella finestra di Output di stampa**  
    Quando è attivato il supporto per il server di origine, questa opzione attiva la visualizzazione dei messaggi di diagnostica.  
  
- **Consenti server origine per assembly parzialmente attendibili (solo gestito)**  
    Quando il supporto del server di origine è abilitato, questa impostazione esegue l'override del comportamento predefinito che non recupera le origini per gli assembly parzialmente attendibili.  

- **Abilita il supporto di origine collegamento**  
    Indica al debugger di Visual Studio per scaricare il file di origine per i file con estensione PDB che contengono informazioni sui collegamenti di origine. Per ulteriori informazioni sul collegamento di origine, vedere il [specifica di collegamento di origine](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

    > [!IMPORTANT]
    >  Poiché il collegamento di origine verranno scaricati i file tramite http o https, assicurarsi che si ritiene che il file con estensione pdb.  
  
**Evidenzia intera riga per i punti di interruzione e l'istruzione corrente (solo C++)**  
Quando il debugger evidenzia un punto di interruzione o l'istruzione corrente, estende l'evidenziazione all'intera riga.  
  
**Richiedono file di origine corrisponde esattamente alla versione originale**  
Indica al debugger di verificare che un file di origine corrisponda alla versione del codice sorgente utilizzato per compilare l'eseguibile sottoposto a debug. Se la versione non corrisponde, chiesto di trovare un'origine corrispondente. Se la ricerca ha esito negativo, il codice sorgente non verrà visualizzato durante il debug. 
  
**Reindirizza tutto il testo di finestra di Output nella finestra controllo immediata**  
Invia tutti i messaggi del debugger che normalmente verrebbero visualizzati di **Output** finestra per il **immediato** finestra invece.  
  
**Mostra struttura non elaborata degli oggetti nelle finestre delle variabili**  
Disattiva tutte le personalizzazioni di visualizzazione della struttura degli oggetti. Per ulteriori informazioni sulla personalizzazione delle visualizzazioni, vedere [creare viste personalizzate di oggetti .managed](../debugger/create-custom-views-of-dot-managed-objects.md).  
  
**Disattiva l'ottimizzazione JIT al caricamento del modulo (solo gestito)**  
Disabilita l'ottimizzazione JIT del codice gestito quando un modulo viene caricato e JIT viene compilato al momento della connessione al debugger. La disabilitazione dell'ottimizzazione JIT può semplificare il debug di determinati errori, anche se può avere effetti negativi sulle prestazioni. Se si usa Just My Code e si disattiva l'ottimizzazione JIT, è possibile che il codice non utente venga visualizzato come codice utente ("My Code").

**Abilitare il debug di JavaScript per ASP.NET (Chrome e Internet Explorer)** consente al debugger di script per le applicazioni ASP.NET. Al primo utilizzo in Chrome, è necessario accedere al primo utilizzo per abilitare le estensioni di colore che è stato installato il browser. Disabilitare questa opzione per ripristinare il comportamento legacy.    

**Carica esportazioni dll**  
Carica le tabelle di esportazione DLL. Le informazioni sui simboli delle tabelle di esportazione DLL possono essere utili se usano messaggi Windows, routine Windows (WindowProc), oggetti COM, marshalling o qualsiasi DLL per cui non sono disponibili simboli. La lettura di informazioni di esportazione DLL comporta un sovraccarico. Pertanto questa funzionalità è disattivata per impostazione predefinita.  
  
Per visualizzare i simboli sono disponibili nella tabella di esportazione di una dll, utilizzare `dumpbin /exports`. I simboli sono disponibili per tutte le DLL di sistema a 32 bit. Leggendo l'output di `dumpbin /exports` , è possibile visualizzare il nome esatto della funzione, compresi i caratteri non alfanumerici. Ciò risulta utile per impostare un punto di interruzione su una funzione. I nomi di funzione delle tabelle di esportazione DLL possono apparire troncati in altri punti del debugger. Le chiamate sono elencate nell'ordine di chiamata, con la funzione corrente (al più alto livello di annidamento) all'inizio dell'elenco. Per altre informazioni, vedere [dumpbin /exports](/cpp/build/reference/dash-exports).  
  
**Mostra diagramma di stack in parallelo dal basso in alto**  
Controlla la direzione in cui vengono visualizzati gli stack nella **stack in parallelo** finestra.  
  
**Ignora eccezioni di accesso di memoria GPU se i dati scritti non hanno modificato il valore**  
Ignora le race condition rilevate durante il debug se i dati non è stato modificato. Per ulteriori informazioni, vedere [debug del codice GPU](../debugger/debugging-gpu-code.md).  
  
**Utilizzare la modalità di compatibilità gestita**  
Sostituisce il motore di debug predefinito con una versione legacy per abilitare gli scenari seguenti:  
  
- Si utilizza un linguaggio .NET Framework diverso da C#, VB o F# che fornisce il proprio analizzatore di espressioni (questo include C++/CLI).  
  
- Si vuole abilitare Modifica e continuazione per i progetti C++ durante il debug in modalità mista.  
  
Si noti che scegliendo la modalità di compatibilità gestita vengono disabilitate alcune funzionalità implementate solo nel motore di debug predefinito. 

**Usare gli analizzatori di espressioni c# e VB legacy**  
Il debugger userà gli analizzatori di espressioni di Visual Studio 2013 C#/VB anziché quelli basati su Visual Studio 2015 Roslyn.    
  
**Avvisa quando si usano visualizzatori di debugger personalizzati in processi potenzialmente non sicuri (solo gestito)**  
Visual Studio genera avvisi quando si usa un visualizzatore di debugger personalizzato che esegue codice nel processo oggetto del debug perché potrebbe essere in esecuzione codice unsafe.  
  
**Abilita l'allocatore di heap di debug Windows (solo nativo)**  
Consente all'heap per il debug di Windows di migliorare la diagnostica dell'heap. L'abilitazione di questa opzione influirà sulle prestazioni di debug.  
  
**Abilita gli strumenti di debug per il codice XAML dell'interfaccia utente**  
Le finestre Struttura ad albero visuale attiva e Esplora proprietà attive vengono visualizzate quando si avvia il debug (F5) di un tipo di progetto supportato. Per ulteriori informazioni, vedere [proprietà controllare XAML durante il debug](../debugger/inspect-xaml-properties-while-debugging.md).  
  
- **Anteprima degli elementi selezionati in albero elementi visivi attivi**  
    L'elemento XAML è selezionato il cui contesto viene selezionato anche nel **albero elementi visivi attivi** finestra.  
  
- **Mostra strumenti di runtime nell'applicazione**  
    Viene illustrato il **albero elementi visivi attivi** comandi in una barra degli strumenti nella finestra principale dell'applicazione XAML in cui viene eseguito il debug. Questa opzione è stata introdotta in Visual Studio 2015 Update 2. 

- **Abilitare XAML modifica e continuazione** consente di utilizzare Modifica e continuazione di funzionalità per il codice XAML. 
  
**Abilita gli strumenti di diagnostica durante il debug**  
Il **strumenti di diagnostica** verrà visualizzata la finestra durante il debug.
  
**Mostra il perftip relativo al tempo trascorso durante il debug**  
La finestra di codice mostra il tempo trascorso di una specifica chiamata al metodo quando si esegue il debug.  
  
**Abilita modifica e continuazione**  
È possibile usare la funzionalità Modifica e continuazione durante il debug.  
  
- **Abilitare nativo modifica e continuazione**  
    È possibile usare la funzionalità Modifica e continuazione durante il debug del codice C++ nativo. Per ulteriori informazioni, vedere [modifica e continuazione (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
- **Applicare le modifiche durante la continuazione (solo nativo)**  
    Visual Studio compila e applica automaticamente le modifiche di codice in sospeso apportate quando il processo viene ripreso da uno stato di interruzione. Se non è selezionata, è possibile scegliere di applicare le modifiche utilizzando l'elemento "Applica modifiche del codice" nel menu Debug.  
  
- **Avvisa in codice non aggiornato (solo nativo)**  
    Consente di ricevere avvisi relativi al codice non aggiornato.    

**Mostra esecuzione fare clic sul pulsante nell'editor durante il debug** quando questa opzione è selezionata, il [eseguire fare clic su](debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) pulsante verrà visualizzato durante il debug.

## <a name="options-supported-in-older-versions-of-visual-studio"></a>Opzioni supportate nelle versioni precedenti di Visual Studio

Se si utilizza una versione precedente di Visual Studio, è possibile che alcune opzioni aggiuntive potrebbero essere presenti.

**Abilita informazioni sulle eccezioni**  
Per codice gestito, abilitare l'Assistente per l'eccezione. In Visual Studio 2017, l'Helper eccezioni sostituito informazioni sulle eccezioni.

**Rimuovi stack di chiamate su eccezioni non gestite**  
Determina il **Stack di chiamate** finestra rollback lo stack di chiamate al punto precedente l'eccezione non gestita. 

**Avvisa se non vi sono simboli all'avvio (solo nativo)**  
Visualizza una finestra di dialogo di avviso ogni volta che si prova a eseguire il debug di un programma per il quale il debugger non ha informazioni sui simboli. 

**Avvisa se il debug degli script è disabilitato all'avvio**  
Visualizza una finestra di dialogo di avviso ogni volta che il debugger viene avviato con il debug degli script disabilitato.

**Utilizzare la modalità di compatibilità nativa**  
Quando questa opzione è selezionata, il debugger usa il debugger nativo di Visual Studio 2010 anziché il nuovo debugger nativo.  
  
Usare questa opzione quando si esegue il debug di codice C++ .NET perché il nuovo motore di debug non supporta la valutazione delle espressioni C++ .NET. Tuttavia, l'abilitazione della modalità di compatibilità nativa disabilita molte funzionalità che dipendono dall'implementazione corrente del debugger per il funzionamento. Ad esempio, il motore legacy non ha molti dei visualizzatori per i tipi incorporati come `std::string` nei progetti di Visual Studio 2015.   Per un'esperienza di debug ottimale, in questi casi usare i progetti di Visual Studio 2013.
  
## <a name="see-also"></a>Vedere anche  
 [Debug in Visual Studio](../debugger/index.md)  
 [Tour delle funzionalità del debugger](../debugger/debugger-feature-tour.md)
