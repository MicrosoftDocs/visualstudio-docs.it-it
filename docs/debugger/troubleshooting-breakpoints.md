---
title: Risolvere i punti di interruzione nel Debugger di Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 01/23/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d587809a9690e312e923ba184c9d90c38405a5d6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Risolvere i punti di interruzione nel Debugger di Visual Studio

## <a name="breakpoint-warnings"></a>Avvisi di punto di interruzione

Durante il debug, un punto di interruzione ha due possibili stati di visualizzazione: un cerchio rosso a tinta unita e un vuoto (bianco compilato) cerchio. Se il debugger è in grado di impostare correttamente un punto di interruzione nel processo di destinazione, rimarrà un cerchio rosso a tinta unita. Se il punto di interruzione è un cerchio vuoto, il punto di interruzione è disabilitato o avviso durante il tentativo di impostare il punto di interruzione. Per determinare la differenza, passare il mouse sul punto di interruzione e verificare se esiste un messaggio di avviso.

Due sezioni seguenti vengono descritti gli avvisi principali e come risolverli. 

### <a name="no-symbols-have-been-loaded-for-this-document"></a>"Nessun simbolo è stato caricato per il documento" 

Passare al **moduli** finestra (**Debug** > **Windows** > **moduli**) e verificare se un modulo caricato.  
* Se il modulo viene caricato, controllare il **stato simboli** colonna per vedere se sono stati caricati simboli. 
  * Se non sono caricati i simboli, controllare lo stato di simboli per diagnosticare il problema. Dal menu di scelta rapida per un modulo di **moduli** finestra, fare clic su **informazioni sul caricamento simboli...**  per vedere in cui il debugger aveva per tentare di caricare i simboli. Per ulteriori informazioni sul caricamento simboli, vedere [specificare simboli (PDB) e file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  * Se vengono caricati i simboli, ciò significa che il file PDB non contiene informazioni sui file di origine. Ecco alcune possibili cause: 
    * Se i file di origine aggiunti di recente, verificare che venga caricata una versione aggiornata del modulo.  
    * È possibile creare i PDB rimossi utilizzando il **/PDBSTRIPPED** l'opzione del linker. I PDB rimossi non contengono informazioni sui file di origine. Confermare che si sta utilizzando una procedura completa di file PDB e non un file PDB rimossi.  
    * Il file PDB è parzialmente danneggiato. Provare a eliminare il file e l'esecuzione di una compilazione pulita del modulo per verificare se questo risolve il problema. 

* Se non è caricato il modulo, verificare quanto segue per individuare la causa: 
  * Confermare che si esegue il debug del processo appropriato. 
  * Verificare che si esegue il debug del tipo appropriato di codice. È possibile trovare il tipo di codice, il debugger è configurato per eseguire il debug nel **processi** finestra (**Debug** > **Windows**  >  **Processi**). Ad esempio, se si sta tentando di eseguire il debug del codice c#, verificare che il debugger è configurato per il tipo appropriato di .NET Framework (ad esempio, gestito (v4\*) e gestito (v2\*/v3\*) e gestito (CoreCLR)). 

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… il codice sorgente corrente è diverso dalla versione incorporata..." 

Se è stato modificato un file di origine e l'origine non corrisponde più il codice in cui che si esegue il debug, il debugger non imposterà i punti di interruzione nel codice per impostazione predefinita. In genere, questo problema si verifica quando viene modificato un file di origine, ma il codice sorgente non è stato ricompilato. Per risolvere questo problema, ricompilare il progetto. Se il sistema di compilazione ritiene che il progetto è già aggiornato anche se non lo è, è possibile forzare il sistema del progetto per ricompilare per salvare il file di origine o la pulizia del progetto compilare output prima della compilazione. 

In rari casi si desidera eseguire il debug senza codice di origine corrispondente. Questo può comportare un'esperienza di debug molto ambiguo, assicurarsi che sia la modalità di procedere.  

Per disabilitare questi controlli di sicurezza, effettuare una delle operazioni seguenti: 
* Per modificare un singolo punto di interruzione, passare il mouse sull'icona di punto di interruzione nell'editor e fare clic sull'icona Impostazioni (ingranaggio). Una finestra di anteprima viene aggiunto all'editor. Nella parte superiore della finestra di anteprima è un collegamento ipertestuale che indica la posizione del punto di interruzione. Fare clic sul collegamento ipertestuale per consentire la modifica della posizione punto di interruzione e controllare **il codice sorgente può essere diverso dall'originale**.
* Per modificare questa impostazione per tutti i punti di interruzione, passare a **Debug** > **opzioni e impostazioni**. Nella pagina **Debug/Generale** deselezionare l'opzione **Richiedi corrispondenza esatta dei file di origine con la versione originale** . Assicurarsi di abilitare di nuovo questa opzione dopo aver terminato il debug. 

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>Il punto di interruzione è stato impostato correttamente (nessun avviso), ma non è stato raggiunto 

In questa sezione vengono fornite informazioni per risolvere i problemi quando il debugger non è visualizzati tutti gli avvisi: il punto di interruzione è un cerchio rosso a tinta unita durante il debug, ma non viene raggiunto il punto di interruzione. 

Ecco alcuni aspetti da controllare: 
1. Se il codice viene eseguito in più di un processo o più computer, assicurarsi che si esegue il debug di processo corretto o il computer.  
2. Verificare che il codice sia in esecuzione. Per eseguire questa verifica consiste nell'aggiungere una chiamata a `System.Diagnostics.Debugger.Break` (C# /VB) o `__debugbreak` (C++) per la riga di codice in cui si sta tentando di impostare il punto di interruzione e quindi ricompilare il progetto. 
3. Se si esegue il debug di codice ottimizzato, assicurarsi che la funzione in cui è impostato il punto di interruzione non viene resa inline in un'altra funzione. Il `Debugger.Break` test descritto il controllo precedente possono essere usati per testare anche questa operazione. 

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Un punto di interruzione è stato eliminato ma si continua a raggiungerlo quando si avvia nuovamente il debug 

Se è stato eliminato un punto di interruzione durante il debug, è possibile riscontrare il punto di interruzione nuovamente al successivo che avvio del debug. Per evitare di raggiungere il punto di interruzione, accertarsi che tutte le istanze del punto di interruzione vengano rimosse dalla finestra **Punti di interruzione** .  
