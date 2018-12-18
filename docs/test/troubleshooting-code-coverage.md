---
title: Risoluzione dei problemi di code coverage | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 10fc7fe674e73ab1c81721048a50db80d1dd6fdd
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="troubleshooting-code-coverage"></a>Risoluzione dei problemi di code coverage
Lo strumento di analisi della copertura del codice in Visual Studio raccoglie dati per assembly nativo e gestito (file .dll o .exe). Tuttavia, in alcuni casi, la finestra dei risultati della copertura del codice visualizza un errore simile a "Generati risultati vuoti: ...." Esistono vari motivi possibili per cui questo può verificarsi. Questo argomento è progettato per aiutare a risolvere quei problemi.  
  
## <a name="what-you-should-see"></a>Cosa si dovrebbe vedere  
 Se si sceglie un comando **Analizza code coverage** dal menu Test e se la compilazione e i test vengono eseguiti correttamente, nella finestra di code coverage verrà visualizzato un elenco di risultati. Potrebbe essere necessario espandere gli elementi per visualizzare il dettaglio.  
  
 ![Risultati del code coverage con colorazione](../test/media/codecoverage1.png "CodeCoverage1")  
  
 Per altre informazioni, vedere [Uso di code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Cause possibili per la restituzione di nessun risultato o di risultati obsoleti  
  
### <a name="do-you-have-the-right-edition-of-visual-studio"></a>L'edizione di Visual Studio in uso è corretta?  
 È necessario Visual Studio Enterprise.  
  
### <a name="no-tests-were-executed"></a>Nessun test è stato eseguito  
 Analisi  
 Verificare la finestra di output. Nell'elenco a discesa **Mostra output di** scegliere **Test**. Verificare se sono presenti avvisi o errori registrati.  
  
 Descrizione  
 L'analisi del code coverage viene effettuata mentre i test sono in esecuzione. Include solo gli assembly caricati in memoria quando i test vengono eseguiti. Se nessun test viene eseguito allora il code coverage non ha nulla da riportare.  
  
 Risoluzione  
 In Esplora test scegliere **Esegui tutto** per verificare che i test vengano eseguiti correttamente. Correggere eventuali errori prima di usare l'opzione **Analizza code coverage**.  
  
### <a name="youre-looking-at-a-previous-result"></a>È visualizzato un risultato precedente  
 Quando si modificano e si rieseguono i test, i risultati di un code coverage precedente possono rimanere visibile, inclusa la colorazione del codice dell'esecuzione precedente.  
  
1.  Eseguire Analizza code coverage.  
  
2.  Verificare che sia stato selezionato il set di risultati più recente nella finestra dei risultati del code coverage.  
  
### <a name="pdb-symbol-files-are-unavailable"></a>I file con estensione pdb (simbolo) non sono disponibili  
 Analisi  
 Aprire la cartella di destinazione della compilazione (in genere bin\debug) e verificare che per ogni assembly esista un file con estensione pdb nella stessa directory del file con estensione dll o exe.  
  
 Descrizione  
 Il motore di code coverage richiede che ogni assembly abbia un proprio file con estensione pdb associato accessibile durante l'esecuzione del test. Se non esiste alcun file con estensione pdb per un particolare assembly, tale assembly non verrà analizzato.  
  
 Il file con estensione pdb deve essere generato dalla stessa compilazione dei file con estensione dll o exe.  
  
 Risoluzione  
 Verificare che le impostazioni di compilazione generino il file con estensione pdb. Se i file con estensione pdb non vengono aggiornati quando viene compilato il progetto, aprire le proprietà del progetto, selezionare la pagina **Compila**, scegliere **Avanzate** e controllare **Informazioni di debug**.  
  
 Se i file con estensione pdb e dll o exe sono in posizioni diverse, copiare il file con estensione pdb nella stessa directory. È inoltre possibile configurare il motore di code coverage per cercare i file con estensione pdb in un'altra posizione. Per altre informazioni, vedere [Personalizzazione dell'analisi code coverage](../test/customizing-code-coverage-analysis.md).  
  
### <a name="using-an-instrumented-or-optimized-binary"></a>Utilizzo di un binario instrumentato o ottimizzato  
 Analisi  
 Determinare se il binario è stato sottoposto a qualche forma di ottimizzazione avanzata, come l'ottimizzazione PGO, o è stato instrumentato da uno strumento di profilatura come vsinstr.exe o vsperfmon.exe.  
  
 Descrizione  
 Se l'assembly è già stato instrumentato o ottimizzato da un altro strumento di profilatura, l'assembly viene omesso dall'analisi di code coverage.  
  
 L'analisi di code coverage non può essere eseguita su tali assembly.  
  
 Risoluzione  
 Disattivare l'ottimizzazione e usare una nuova compilazione.  
  
### <a name="code-is-not-managed-net-or-native-c-code"></a>Codice non gestito (.NET) o codice nativo (C++)  
 Analisi  
 Verificare che vengano eseguiti alcuni test sul codice gestito o C++.  
  
 Descrizione  
 L'analisi di code coverage in Visual Studio è disponibile solo nel codice gestito e nativo (C++). Se si utilizzano strumenti di terze parti, il codice può essere eseguito parzialmente o totalmente su una piattaforma diversa.  
  
 Risoluzione  
 Non disponibile.  
  
### <a name="assembly-has-been-installed-by-ngen"></a>L'assembly è stato installato da NGen  
 Analisi  
 Verificare che l'assembly non venga caricato dalla cache delle immagini native.  
  
 Descrizione  
 Per motivi di prestazioni, gli assembly di immagini native non vengono analizzate. Per altre informazioni, vedere [Ngen.exe (Native Image Generator)](/dotnet/framework/tools/ngen-exe-native-image-generator).  
  
 Risoluzione  
 Utilizzare una versione MSIL dell'assembly. Non elaborarlo con NGen.  
  
### <a name="custom-runsettings-file-with-bad-syntax"></a>File personalizzato con estensione runsettings con sintassi non valida  
 Analisi  
 Un file personalizzato con estensione runsettings potrebbe contenere un errore di sintassi.  
  
 Di conseguenza, nessun code coverage verrà eseguito. La finestra di code coverage non viene visualizzata alla fine dell'esecuzione del test oppure vengono visualizzati risultati obsoleti.  
  
 Descrizione  
 È possibile eseguire gli unit test con un file personalizzato con estensione runsettings per configurare le opzioni di code coverage. Le opzioni consentono di includere o escludere i file. Per altre informazioni, vedere [Personalizzazione dell'analisi code coverage](../test/customizing-code-coverage-analysis.md).  
  
 Risoluzione  
 Esistono due possibili tipi di errori:  
  
-   **Errore XML**  
  
     Aprire il file con estensione runsettings nell'editor XML di Visual Studio. Individuare le indicazioni degli errori.  
  
-   **Errore di espressione regolare**  
  
     Ogni stringa del file è un'espressione regolare. Rivederle singolarmente per individuare gli errori, in particolare cercare:  
  
    -   Parentesi non corrispondenti (...) o parentesi non precedute da un carattere di escape \\(...\\). Se si desidera trovare la corrispondenza con una parentesi nella stringa di ricerca, è necessario utilizzare caratteri di escape. Ad esempio, per trovare la corrispondenza con una funzione, usare `.*MyFunction\(double\)`  
  
    -   L'asterisco o il segno più all'inizio di un'espressione. Per cercare una stringa di caratteri, utilizzare un punto seguito da un asterisco: `.*`  
  
### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>File personalizzato con estensione runsettings con esclusioni non corrette  
 Analisi  
 Se si utilizza un file personalizzato con estensione runsettings, assicurarsi di sia incluso nell'assembly.  
  
 Descrizione  
 È possibile eseguire gli unit test con un file personalizzato con estensione runsettings per configurare le opzioni di code coverage. Le opzioni consentono di includere o escludere i file. Per altre informazioni, vedere [Personalizzazione dell'analisi code coverage](../test/customizing-code-coverage-analysis.md).  
  
 Risoluzione  
 Rimuovere tutti i nodi `Include` dal file con estensione runsettings quindi rimuovere tutti i nodi `Exclude`. Se in tal modo si risolve il problema, riportare i nodi nelle fasi.  
  
 Assicurarsi che il nodo DataCollectors specifichi Code coverage. Confrontarlo con l'esempio presente in [Personalizzazione dell'analisi code coverage](../test/customizing-code-coverage-analysis.md).  
  
## <a name="some-code-is-always-shown-as-not-covered"></a>Il codice verrà sempre visualizzato come parzialmente non analizzato  
  
### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>Il codice di inizializzazione nelle DLL native viene eseguito prima della strumentazione  
 Analisi  
 Nel codice nativo collegato in modo statico, parte della funzione di inizializzazione **DllMain** e il codice che chiama vengono talvolta visualizzati come non analizzati, anche se il codice è stato eseguito.  
  
 Descrizione  
 Lo strumento di code coverage funziona inserendo la strumentazione in un assembly immediatamente prima dell'avvio dell'applicazione. Nell'assembly caricato in precedenza, il codice di inizializzazione in **DllMain** viene eseguito non appena viene caricato l'assembly e prima che venga eseguita l'applicazione. Il codice risulterà non analizzato.  
  
 In genere, questo si applica agli assembly caricati in modo statico.  
  
 Risoluzione  
 Nessuno.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
