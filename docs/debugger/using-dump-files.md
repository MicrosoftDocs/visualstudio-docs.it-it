---
title: Utilizzo di file Dump | Documenti Microsoft
ms.custom: H1HackMay2017
ms.date: 03/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.crashdump
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
caps.latest.revision: "53"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 179d66b80676cf47bb12e82fcd8e4ac00503a492
ms.sourcegitcommit: 5d43e9590e2246084670b79269cc9d99124bb3df
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="use-dump-files-with-visual-studio"></a>Utilizzo di file Dump con Visual Studio
File di dump con o senza heap; creare un file di dump. Aprire un file di dump. trovare i file binari, del file pdb e file di origine per un file di dump.
  
##  <a name="BKMK_What_is_a_dump_file_"></a>Che cos'è un file di dump?  
 Oggetto *file di dump* è uno snapshot di un'app in corrispondenza del punto nel tempo, viene eseguito il dump. Indica il processo in esecuzione e i moduli caricati. Se il dump è stato salvato con informazioni heap, contiene uno snapshot delle attività svolte nella memoria dell'app in quel momento. L'apertura di un file dump con un heap in Visual Studio è simile all'arresto in corrispondenza di un punto di interruzione in una sessione di debug. Sebbene non sia possibile continuare l'esecuzione, è possibile esaminare gli stack, i thread e i valori delle variabili dell'app al momento in cui si è verificato il dump.  
  
 Dump vengono utilizzati principalmente per il debug dei problemi che si verificano nei computer che lo sviluppatore non ha accesso a. Ad esempio, è possibile utilizzare un file di dump dal computer di un cliente quando non è possibile riprodurre l'arresto anomalo del sistema del cliente o di blocco nel computer. I dump vengono inoltre creati dai tester per salvare i dati relativi a un arresto anomalo o un blocco per eseguire altre verifiche nel computer di test. Il debugger di Visual Studio può salvare i file dump per il codice gestito o nativo. Il debugger può caricare i file dump creati da Visual Studio o da altri programmi che salvano i file nel *minidump* formato.  
  
##  <a name="BKMK_Dump_files__with_or_without_heaps"></a>File di dump, con o senza heap  
 È possibile creare file dump con o senza informazioni heap.  
  
-   **File dump con heap** contengono uno snapshot di memoria dell'app. Sono inclusi i valori delle variabili al momento della creazione del dump. Se si carica un file dump salvato con un heap, Visual Studio potrà caricare i simboli anche se il file binario dell'applicazione non è disponibile. Visual Studio salva inoltre i file binari dei moduli nativi caricati nel file dump, che possono semplificare il debug.  
  
-   **File dump senza heap** sono molto più piccoli dei dump con informazioni sull'heap. Il debugger deve tuttavia caricare i file binari dell'app per trovare informazioni sui simboli. I file binari devono corrispondere esattamente ai file binari utilizzati alla creazione del dump. Solo i valori delle variabili dello stack vengono salvati nei file dump senza dati dell'heap.  
  
##  <a name="BKMK_Requirements_and_limitations"></a>Requisiti e limitazioni  
  
-   Il debug di file dump del codice ottimizzato può generare confusione. Ad esempio, l'incorporamento di funzioni del compilatore può comportare stack di chiamate imprevisti e altre ottimizzazioni potrebbero modificare la durata delle variabili.  
  
-   Il debug dei file dump di computer a 64 bit deve essere eseguito in un'istanza di Visual Studio in esecuzione in un computer a 64 bit.  
  
-   Nelle versioni di Visual Studio precedenti a VS 2013, i dump delle app a 32 bit eseguite in computer a 64 bit raccolti da alcuni strumenti (ad esempio Gestione attività e WinDbg a 64 bit) potrebbero non essere aperti in Visual Studio. In VS 2013 questa limitazione è stata eliminata.  
  
-   Visual Studio può eseguire il debug dei file dump delle app native di dispositivi ARM. Visual Studio può inoltre eseguire il debug dei file dump di app gestite di dispositivi ARM, ma solo nel debugger nativo.  
  
-   Per eseguire il debug [in modalità kernel](http://msdn.microsoft.com/library/windows/hardware/ff551880.aspx) file dump, scaricare gli strumenti di debug per Windows che fa parte di [Windows Driver Kit (WDK)](/windows/hardware/windows-driver-kit). 
  
-   Visual Studio non è possibile eseguire il debug di file dump salvati nel formato dump precedente noto come un [dump completo in modalità utente](http://msdn.microsoft.com/library/windows/hardware/ff545506.aspx). Si noti che un dump completo in modalità utente non corrisponde a un dump con heap.  
  
-   Eseguire il debug con il [SOS.dll (estensione del debugger SOS)](/dotnet/framework/tools/sos-dll-sos-debugging-extension) in Visual Studio, è necessario installare gli strumenti di debug per Windows che fa parte di [Windows Driver Kit (WDK)](/windows/hardware/windows-driver-kit) 
  
##  <a name="BKMK_Create_a_dump_file"></a>Creare un file dump  
 Per creare un file dump con Visual Studio:  
  
-   Durante il debug di un processo in Visual Studio, è possibile salvare un file dump quando il debugger è stato arrestato in corrispondenza di un'eccezione o di un punto di interruzione. Scegliere **Debug**, quindi **Salva Dump con nome**, quindi **Debug**. Nel **Salva Dump con nome** della finestra di dialogo di **Salva come** elenco, è possibile selezionare **Minidump** o **Minidump con Heap** (impostazione predefinita).  
  
-   Con [debug JIT](../debugger/just-in-time-debugging-in-visual-studio.md) abilitato, è possibile collegare il debugger a un processo bloccato è in esecuzione all'esterno del debugger e quindi salvare un file di dump. Vedere [allegare a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
  
 È inoltre possibile creare file dump con qualsiasi programma che supporta il formato di minidump di Windows. Ad esempio, il **Procdump** l'utilità della riga di comando da [Windows Sysinternals](http://technet.microsoft.com/sysinternals/default) possibile creare file dump di arresto del processo basati su trigger o su richiesta. Vedere [requisiti e limitazioni](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) in questo argomento per ulteriori informazioni sull'utilizzo di altri strumenti per creare i file di dump. 
  
##  <a name="BKMK_Open_a_dump_file"></a>Aprire un file dump  
  
1.  In Visual Studio, scegliere **File**, **aprire**, **File**.  
  
2.  Nel **Apri** finestra di dialogo individuare e selezionare il file di dump. Il file dump in genere ha l'estensione dmp. Scegliere quindi **OK**.  
  
3.  Il **riepilogo File Dump** verrà visualizzata la finestra. In questa finestra è possibile visualizzare informazioni di riepilogo sul debug del file dump, impostare il percorso dei simboli, avviare il debug e copiare le informazioni di riepilogo negli Appunti.  
  
     ![Pagina di riepilogo minidump](../debugger/media/dbg_dump_summarypage.png "DBG_DUMP_SummaryPage")  
  
4.  Per avviare il debug, aprire il **azioni** sezione e scegliere **eseguire il Debug con solo gestito**, **eseguire il Debug con solo nativo** o **eseguire il Debug con misto**.  
  
##  <a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a>Trovare i file binari, i file di simboli (PDB) e i file di origine  
 Per utilizzare le funzionalità complete di Visual Studio per eseguire il debug di un file dump, è necessario accedere a:  
  
-   File exe per cui il dump è stato creato e altri file binari (DLL e così via) utilizzati nel processo del dump.  
  
     Se si esegue il debug di un dump con dati dell'heap, Visual Studio può ovviare alla mancanza dei file binari per alcuni moduli, ma deve disporre dei file binari per un numero sufficiente di moduli per generare stack di chiamate validi. Visual Studio include i moduli nativi in un file dump con heap.  
  
-   File di simboli (con estensione pdb) per il file con estensione exe e altri binari.  
  
-   File di origine dei moduli a cui si è interessati.  
  
     I file eseguibili e i file con estensione pdb devono corrispondere esattamente alla versione e alla compilazione dei file utilizzati alla creazione del dump.  
  
     È possibile eseguire il debug utilizzando il disassembly dei moduli se non si trova i file di origine,  
  
 **Percorsi di ricerca predefiniti per i file eseguibili**  
  
 Visual Studio cerca automaticamente questi percorsi per i file eseguibili che non sono inclusi nel file di dump:  
  
1.  Directory che contiene il file dump.  
  
2.  Il percorso del modulo specificato nel file dump. Si tratta del percorso del modulo nel computer in cui è stato recuperato il dump.  
  
3.  I percorsi di simboli specificati nella **debug**, **opzioni**, **simboli** pagina di Visual Studio **strumenti**, **opzioni**  la finestra di dialogo. È possibile aggiungere più posizioni per effettuare la ricerca in questa pagina.  
  
 **Utilizzando il binario n > simbolo > pagine di origine**  
  
 Se Visual Studio: Impossibile trovare i file necessari per eseguire il debug di un modulo nel dump, visualizzata una pagina appropriata (**Nessun file binario trovato**, **Nessun simbolo trovato**, o **Nessuna origine trovata**). Queste pagine forniscono informazioni dettagliate sulla causa del problema e vengono forniti collegamenti ad azioni che consentono di identificare il percorso corretto dei file. Vedere [specifica simboli (PDB) e i file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Il debug Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Specificare i simboli (PDB) e file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [IntelliTrace](../debugger/intellitrace.md)