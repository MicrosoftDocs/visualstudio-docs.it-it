---
title: "Eseguire il debug di più processi | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7d0aaa97009662000bf1376c1684d9ca41a7133a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="debug-multiple-processes"></a>Procedura: eseguire il debug di più processi
Di seguito viene illustrato come avviare il debug di processi, passaggio tra processi, interrompere e continuare l'esecuzione, esaminare l'origine, interrompere il debug e terminare o disconnettersi dai processi.  
  
##  <a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>Configurare il comportamento di esecuzione di più processi  
 Per impostazione predefinita, quando più processi sono in esecuzione nel debugger, i comandi del debugger di interruzione, esecuzione delle istruzioni e arresto di solito interessano tutti i processi. Ad esempio, quando un processo viene sospeso in corrispondenza di un punto di interruzione, viene sospesa anche l'esecuzione di tutti gli altri processi. È possibile modificare questo comportamento predefinito per ottenere un maggiore controllo sulle destinazioni dei comandi di esecuzione.  
  
1.  Fare clic su **Debug > Opzioni e impostazioni**.  
  
2.  Nel **debug**, **generale** pagina, deseleziona il **quando si interrompe un processo, interrompi tutti i processi** casella di controllo.  
  
 ![Torna all'inizio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommario](#BKMK_Contents)  
  
##  <a name="BKMK_Find_the_source_and_symbol___pdb__files"></a>File di origine e di simboli (PDB)  
 Per esplorare il codice sorgente di un processo, il debugger deve accedere ai file di origine e di simboli del processo. Vedere [specifica simboli (PDB) e i file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Se è Impossibile accedere ai file per un processo, è possibile spostarsi utilizzando la finestra Disassembly. Vedere [procedura: utilizzare la finestra Disassembly](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![Torna all'inizio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommario](#BKMK_Contents)  
  
##  <a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a>Avviare più processi in una soluzione VS, connettersi a un processo, avviare automaticamente un processo nel debugger  
  
-   [Avviare il debug di più processi in una soluzione di Visual Studio](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution)  
  
-   [Modificare il progetto di avvio](#BKMK_Change_the_startup_project)  
  
-   [Avviare un progetto specifico in una soluzione](#BKMK_Start_a_specific_project_in_a_solution)  
  
-   [Avviare più progetti in una soluzione](#BKMK_Start_multiple_projects_in_a_solution)  
  
-   [Connettersi a un processo](#BKMK_Attach_to_a_process)  
  
-   [Avviare automaticamente un processo nel debugger](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
>  Il debugger non si connette automaticamente a un processo figlio che viene avviato da un processo sottoposto a debug, anche se il progetto figlio si trova nella stessa soluzione. Per eseguire il debug di un processo figlio:  
>   
>  -   Connettersi al processo figlio dopo averlo avviato.  
>   
>      oppure  
> -   Configurare Windows per avviare automaticamente il processo figlio in una nuova istanza del debugger.  
  
###  <a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a>Avviare il debug di più processi in una soluzione di Visual Studio  
 Quando sono presenti più progetti in una soluzione Visual Studio che è possibile eseguire in modo indipendente (progetti eseguiti in processi distinti), è possibile selezionare quali progetti vengono avviati dal debugger.  
  
 ![Modifica il tipo di avvio per un progetto](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
####  <a name="BKMK_Change_the_startup_project"></a>Modificare il progetto di avvio  
 Per modificare il progetto di avvio per una soluzione, selezionare il progetto in Esplora soluzioni e quindi scegliere **imposta come progetto di avvio** dal menu di scelta rapida.  
  
####  <a name="BKMK_Start_a_specific_project_in_a_solution"></a>Avviare un progetto specifico in una soluzione  
 Per avviare un progetto per una soluzione senza modificare il progetto di avvio predefinito, selezionare il progetto in Esplora soluzioni e quindi scegliere **Debug** dal menu di scelta rapida. È quindi possibile scegliere **Avvia nuova istanza** o **Esegui istruzione nuova istanza**.  
  
 ![Torna all'inizio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [avviare più processi in una soluzione VS, connettersi a un processo, avviare automaticamente un processo nel debugger](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Torna all'inizio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommario](#BKMK_Contents)  
  
####  <a name="BKMK_Start_multiple_projects_in_a_solution"></a>Avviare più progetti in una soluzione  
  
1.  Selezionare la soluzione in Esplora soluzioni, quindi scegliere **proprietà** nel menu di scelta rapida.  
  
2.  Selezionare **proprietà comuni**, **progetto di avvio** sul **proprietà** la finestra di dialogo.  
  
3.  Per ogni progetto che si desidera modificare, scegliere **avviare**, **Avvia senza eseguire debug**, o **Nessuno**.  
  
 ![Torna all'inizio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [avviare più processi in una soluzione VS, connettersi a un processo, avviare automaticamente un processo nel debugger](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Torna all'inizio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommario](#BKMK_Contents)  
  
###  <a name="BKMK_Attach_to_a_process"></a>Connettersi a un processo  
 Il debugger può inoltre *allegare* ai programmi in esecuzione in processi esterni a Visual Studio, inclusi i programmi in esecuzione in un dispositivo remoto. Dopo essersi connessi a un programma, è possibile usare i comandi di esecuzione del debugger, analizzare lo stato del programma e così via. La possibilità di analisi del programma dipende dall'eventualità che il programma sia stato generato con informazioni di debug, che si disponga dell'accesso al relativo codice sorgente e che il compilatore JIT di Common Language Runtime stia registrando informazioni di debug.  
  
 Vedere [connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) per ulteriori informazioni.  
  
 **Connettersi a un processo in esecuzione sul computer locale**  
  
 Fare clic su **Debug > Connetti a processo**. Nel **Connetti a processo** finestra di dialogo, selezionare il processo dal **processi disponibili** elenco e quindi scegliere **collegamento**.  
  
 ![Processo di dialogo Connetti a](../debugger/media/dbg_attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![Torna all'inizio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommario](#BKMK_Contents)  
  
###  <a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>Avviare automaticamente un processo nel debugger  
 In alcuni casi potrebbe essere necessario eseguire il debug del codice di avvio di un programma avviato da un altro processo. Può ad esempio trattarsi di servizi o operazioni di installazione personalizzate. In questi scenari è possibile avviare e connettere il debugger automaticamente all'avvio dell'applicazione.  
  
1.  Avviare l'Editor del Registro di sistema (**regedit.exe**).  
  
2.  Passare il **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options** cartella.  
  
3.  Selezionare la cartella dell'app da avviare nel debugger.  
  
     Se il nome dell'app non è elencato come cartella figlio, selezionare **Image File Execution Options** e quindi scegliere **New**, **chiave** nel menu di scelta rapida. Selezionare la nuova chiave, scegliere **rinominare** nel menu di scelta rapida e quindi immettere il nome dell'app.  
  
4.  Nel menu di scelta rapida della cartella delle app scegliere **New**, **valore stringa**.  
  
5.  Modificare il nome del nuovo valore da **nuovo valore** a `debugger`.  
  
6.  Nel menu di scelta rapida della voce del debugger scegliere **modifica**.  
  
7.  Nella finestra di dialogo Modifica stringa digitare `vsjitdebugger.exe` nel **dati valore** casella.  
  
     ![Modificare la finestra di dialogo stringa](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
 ![Voce di avvio automatico del debug in regedit.exe](../debugger/media/dbg_execution_automaticstart_result.png "DBG_Execution_AutomaticStart_Result")  
  
 ![Torna all'inizio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommario](#BKMK_Contents)  
  
##  <a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>Passare i processi, interrompere e continuare l'esecuzione, esaminare l'origine  
  
-   [Passaggio tra processi](#BKMK_Switch_between_processes)  
  
-   [Interrompere, eseguire e continuare i comandi](#BKMK_Break__step__and_continue_commands)  
  
###  <a name="BKMK_Switch_between_processes"></a>Passaggio tra processi  
 Nonostante durante il debug sia possibile connettersi a più processi, nel debugger è sempre attivo un solo processo in un dato momento. È possibile impostare attivo o *corrente* processo nella barra degli strumenti posizione di Debug o nel **processi** finestra. Per passare da un processo all'altro, entrambi i processi devono essere in modalità di interruzione.  
  
 **Per impostare il processo corrente**  
  
-   Sulla barra degli strumenti posizione di Debug, scegliere **processo** per visualizzare il **processo** casella di riepilogo. Selezionare il processo da designare come processo corrente.  
  
     ![Spostarsi tra i processi](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
     Se il **posizione di Debug** barra degli strumenti non è visibile, scegliere **strumenti**, **Personalizza**. Nel **barre degli strumenti** scegliere **posizione di Debug**.  
  
-   Aprire il **processi** finestra (scelta rapida **Ctrl + Alt + Z**), individuare il processo che si desidera impostare come corrente e fare doppio clic.  
  
     ![Finestra processi](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")  
  
     Il processo corrente è contrassegnato da una freccia gialla.  
  
 Quando si passa a un progetto esso viene impostato per il debug. In tutte le finestre del debugger visualizzate è mostrato lo stato del processo corrente e tutti i comandi per l'esecuzione di istruzioni interessano solo il processo corrente.  
  
 ![Torna all'inizio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [passare i processi, interrompere e continuare l'esecuzione, esaminare l'origine](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Torna all'inizio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommario](#BKMK_Contents)  
  
###  <a name="BKMK_Break__step__and_continue_commands"></a>Interrompere, eseguire e continuare i comandi  
  
> [!NOTE]
>  Per impostazione predefinita, i comandi del debugger per interrompere, continuare ed eseguire le istruzioni interessano tutti i processi sottoposti a debug. Per modificare questo comportamento, vedere [configurare il comportamento di esecuzione di più processi](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
||||  
|-|-|-|  
|**Comando**|**Quando si interrompe un processo, interrompi tutti i processi**<br /><br /> Selezionato (impostazione predefinita)|**Quando si interrompe un processo, interrompi tutti i processi**<br /><br /> Deselezionato|  
|**Eseguire il debug** menu:<br /><br /> -   **Interrompi tutto**|Interruzione di tutti i processi.|Interruzione di tutti i processi.|  
|**Eseguire il debug** menu:<br /><br /> -   **Continuare**|Ripresa di tutti i processi.|Ripresa di tutti i processi sospesi.|  
|**Eseguire il debug** menu:<br /><br /> -   **Esegui istruzione**<br />-   **Esegui istruzione/routine**<br />-   **Esci da istruzione**|Esecuzione di tutti i processi durante l'esecuzione delle istruzioni del processo corrente.<br /><br /> Successiva interruzione di tutti i processi.|Esecuzione delle istruzioni del processo corrente.<br /><br /> Ripresa dei processi sospesi.<br /><br /> Continuazione dei processi in esecuzione.|  
|**Eseguire il debug** menu:<br /><br /> -   **Esegui istruzione processo corrente**<br />-   **Esegui istruzione/routine processo corrente**<br />-   **Passaggio di processo corrente**|N/D|Esecuzione delle istruzioni del processo corrente.<br /><br /> Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|  
|Finestra di origine<br /><br /> -   **Punto di interruzione**|Interruzione di tutti i processi.|Interruzione solo del processo della finestra di origine.|  
|Menu di scelta rapida della finestra di origine:<br /><br /> -   **Esegui fino al cursore**<br /><br /> La finestra di origine deve essere nel processo corrente.|Esecuzione di tutti i processi mentre il processo della finestra di origine viene eseguito fino al cursore e quindi interrotto.<br /><br /> Successiva interruzione di tutti gli altri processi.|Esecuzione del processo della finestra di origine fino al cursore.<br /><br /> Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|  
|**Processi** menu di scelta rapida finestra:<br /><br /> -   **Interrompi processo**|N/D|Interruzione del processo selezionato.<br /><br /> Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|  
|**Processi** menu di scelta rapida finestra:<br /><br /> -   **Continuare**|N/D|Ripresa del processo selezionato.<br /><br /> Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|  
  
 ![Torna all'inizio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [passare i processi, interrompere e continuare l'esecuzione, esaminare l'origine](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Torna all'inizio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommario](#BKMK_Contents)  
  
##  <a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a>Arrestare il debug, terminare o disconnettersi dai processi  
  
-   [Interrompere, terminare e disconnettere i comandi](#BKMK_Stop__terminate__and_detach_commands)  
  
 Per impostazione predefinita, quando si sceglie **Debug**, **Termina debug** quando più processi sono aperti nel debugger, il debugger termina o disconnette da tutti i processi a seconda di come il processo è stato aperto il debugger:  
  
-   Se il processo corrente è stato avviato nel debugger, esso viene terminato.  
  
-   Se il debugger è stato connesso al processo corrente, viene disconnesso e il processo rimane in esecuzione.  
  
 Ad esempio, se si avvia il debug di un processo da una soluzione di Visual Studio, connettersi a un altro processo già in esecuzione e quindi scegliere **Termina debug**, la sessione di debug termina, il processo di cui è stato avviato in Visual Studio viene terminata, mentre il processo associato viene mantenuto in esecuzione. È possibile utilizzare le procedure seguenti per controllare la modalità di interruzione del debug.  
  
> [!NOTE]
>  Il **quando si interrompe un processo, interrompi tutti i processi** opzione influisce sull'interruzione del debug o di chiusura e disconnessione dai processi.  
  
 **Per modificare la modalità interrompere il debug su un singolo processo**  
  
-   Aprire il **processi** finestra (scelta rapida **Ctrl + Alt + Z**). Selezionare un processo e quindi selezionare o deselezionare il **Disconnetti al termine del debug** casella di controllo.  
  
###  <a name="BKMK_Stop__terminate__and_detach_commands"></a>Interrompere, terminare e disconnettere i comandi  
  
|||  
|-|-|  
|**Comando**|**Descrizione**|  
|**Eseguire il debug** menu:<br /><br /> -   **Arrestare il debug**|A meno che il comportamento è cambiato da **processi** finestra **Disconnetti al termine del debug** opzione:<br /><br /> 1.  I processi avviati dal debugger vengono terminati.<br />2.  I processi connessi vengono disconnessi dal debugger.|  
|**Eseguire il debug** menu:<br /><br /> -   **Termina tutto**|Tutti i processi vengono terminati.|  
|**Eseguire il debug** menu:<br /><br /> -   **Disconnetti tutto**|Il debugger si disconnette da tutti i processi.|  
|**Processi** menu di scelta rapida finestra:<br /><br /> -   **Disconnessione del processo**|Il debugger si disconnette da tutti i processi selezionati.<br /><br /> Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|  
|**Processi** menu di scelta rapida finestra:<br /><br /> -   **Terminare il processo**|Il processo selezionato viene terminato.<br /><br /> Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|  
|**Processi** menu di scelta rapida finestra:<br /><br /> -   **Disconnetti al termine del debug**|Attiva o disattiva il comportamento di **Debug**, **Termina debug** per il processo selezionato:<br /><br /> -Se si seleziona, Il debugger si disconnette dal processo.<br />-Opzione deselezionata: Il processo viene terminato.|  
  
 ![Torna all'inizio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [interrompere il debug, terminare o disconnettersi dai processi](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![Torna all'inizio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommario](#BKMK_Contents)  
  
## <a name="see-also"></a>Vedere anche  
 [Specificare i simboli (PDB) e file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Collegare a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Spostarsi nel codice con il Debugger](../debugger/navigating-through-code-with-the-debugger.md)   
 [Il debug Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)