---
title: Collegare a processi in esecuzione con il Debugger di Visual Studio | Documenti Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 05/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- CSharp
- FSharp
- C++
- VB
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
caps.latest.revision: "53"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 28126f9c832f55d63bd1b477599cf83ac8a57d59
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Connessione a processi in esecuzione con il debugger di Visual Studio
È possibile collegare il debugger di Visual Studio a un processo in esecuzione in un computer locale o remoto. Dopo l'esecuzione del processo, fare clic su **Debug > Connetti a processo** (o premere **CTRL + ALT + P**) per aprire la **Connetti a processo** la finestra di dialogo.

È possibile utilizzare questa funzionalità per eseguire il debug di App in esecuzione in un computer locale o remoto, debug simultaneo di più processi o eseguire il debug di un'applicazione che non è stata creata in Visual Studio. È spesso utile quando si desidera eseguire il debug di un'app, ma (per qualsiasi motivo) non è stato avviato l'app da Visual Studio con il debugger collegato. Ad esempio, se si esegue l'app senza il debugger e un'eccezione di passaggi, potrebbe essere quindi allegare al processo di esecuzione dell'applicazione per avviare il debug.

> [!TIP]
> Non si è certi se è necessario utilizzare **Connetti a processo** per lo scenario di debug? Vedere [comuni scenari di debug](#BKMK_Scenarios). Se si desidera eseguire il debug di applicazioni ASP.NET che sono stati distribuiti in IIS, vedere [ASP.NET di debug remoto in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

##  <a name="BKMK_Attach_to_a_running_process"></a>Connettersi a un processo in esecuzione nel computer locale  
 Per connettersi a un processo, è necessario conoscere il nome del processo (vedere [comuni scenari di debug](#BKMK_Scenarios) per alcuni nomi di processo comuni).
  
1.  In Visual Studio, selezionare **Debug > Connetti a processo** (o premere **CTRL + ALT + P**).

    Se si desidera eseguire rapidamente ricollegare invece a un processo, vedere [ricollegare al processo](#BKMK_reattach).
  
2.  Nella finestra di dialogo **Connetti a processo** individuare il programma con il quale si desidera stabilire una connessione nell'elenco **Processi disponibili** .  

     Per selezionare rapidamente il processo di cui che si desidera, digitare la prima lettera del nome del processo. Se non si conosce il nome del processo, vedere [comuni scenari di debug](#BKMK_Scenarios).
     
     ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process") 
  
     Se il processo viene eseguito con un account utente diverso, selezionare la casella di controllo **Mostra processi di tutti gli utenti** .
  
3.  Nella casella **Connetti a** verificare che sia presente il tipo di codice di cui eseguire il debug. L'impostazione predefinita **Automatico** tenta di determinare il tipo di codice di cui si desidera eseguire il debug. Per impostare manualmente il tipo di codice, eseguire le operazioni seguenti  
  
    1.  Nella finestra di dialogo **Connetti a** scegliere **Seleziona**.  
  
    2.  Nella finestra di dialogo **Seleziona tipo di codice** fare clic su **Esegui il debug di questi tipi di codice** e selezionare i tipi da sottoporre a debug.  
  
    3.  Fare clic su **OK**.  
  
4.  Scegliere **Connetti**.

##  <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a>Connettersi a un processo in un computer remoto  
 Per connettersi a un processo, è necessario conoscere il nome del processo (vedere [comuni scenari di debug](#BKMK_Scenarios) per alcuni nomi di processo comuni). Per istruzioni più complete per le applicazioni ASP.NET che sono stati distribuiti in IIS, vedere [ASP.NET di debug remoto in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Per le altre applicazioni, è possibile trovare il nome del processo in Gestione attività.
  
 Quando si usa la finestra di dialogo **Connetti a processo** , è possibile selezionare un altro computer configurato per il debug remoto. Per ulteriori informazioni, vedere [il debug remoto](../debugger/remote-debugging.md). Dopo avere selezionato un computer remoto, è possibile visualizzare l'elenco dei processi disponibili in esecuzione in tale computer e connettersi a uno o più di questi processi per eseguire il debug.
  
 **Per selezionare un computer remoto:**  

1. In Visual Studio, selezionare **Debug > Connetti a processo** (o premere **CTRL + ALT + P**).

    Se si desidera eseguire rapidamente ricollegare invece a un processo, vedere [ricollegare al processo](#BKMK_reattach).

2.  Nella finestra di dialogo **Connetti a processo** selezionare il tipo di connessione appropriato nell'elenco **Trasporto** . Per la maggior parte dei casi è possibile usare l'impostazione**Predefinito** .

    L'impostazione **Trasporto** viene mantenuta tra una sessione di debug e l'altra. 
  
3.  Usare la casella di riepilogo **Qualificatore** per scegliere il nome del computer remoto in uno dei seguenti modi:  
  
    1.  Digitare il nome nella casella di riepilogo **Qualificatore** .
    
        >**Nota** se nei passaggi successivi, è possibile connettersi utilizzando il nome del computer remoto, utilizzare l'indirizzo IP. (Il numero di porta potrebbe essere visualizzato automaticamente dopo aver selezionato il processo. È possibile inoltre inserire manualmente. Nell'illustrazione seguente, 4020 è la porta predefinita per il debugger remoto.)  

        Se si desidera utilizzare il **trovare** pulsante, potrebbe essere necessario [aprire la porta UDP 3702](../debugger/remote-debugger-port-assignments.md) sul server.
  
    2.  Fare clic sulla freccia a discesa della casella di riepilogo **Qualificatore** e selezionare il nome del computer dall'elenco a discesa.  
  
    3.  Scegliere il pulsante **Trova** accanto all'elenco**Qualificatore** per aprire la finestra di dialogo **Seleziona connessione debugger remoto** . Nella finestra di dialogo **Seleziona connessione debugger remoto** sono elencati tutti i dispositivi presenti nella subnet locale e qualsiasi dispositivo connesso direttamente al computer tramite un cavo Ethernet. Fare clic sul computer o sul dispositivo desiderati e scegliere **Seleziona**. 
  
     L'impostazione **Qualificatore** viene invece mantenuta tra due sessioni di debug solo il qualificatore consente di stabilire correttamente una connessione di debug.
     
4.  Fare clic su **Aggiorna**.

      L'elenco **Processi disponibili** viene visualizzato automaticamente quando si apre la finestra di dialogo **Processi** . I processi possono essere avviati e interrotti in background mentre la finestra di dialogo è aperta. È quindi possibile che il contenuto non sia sempre aggiornato. Per visualizzare i processi correnti, è possibile aggiornare l'elenco in qualsiasi momento usando il pulsante **Aggiorna**. 
     
4.  Nella finestra di dialogo **Connetti a processo** individuare il programma con il quale si desidera stabilire una connessione nell'elenco **Processi disponibili** .

     Per selezionare rapidamente il processo di cui che si desidera, digitare la prima lettera del nome del processo. Se non si conosce il nome del processo, vedere [comuni scenari di debug](#BKMK_Scenarios).
  
     Se il processo viene eseguito con un account utente diverso, selezionare la casella di controllo **Mostra processi di tutti gli utenti** .
     
5.  Scegliere **Connetti**.

## <a name="BKMK_reattach"></a>Riconnettersi al processo

È possibile ricollegare rapidamente a processi che erano in precedenza associato a scegliendo **Debug > ricollegare al processo...** (**Maiusc + Alt + P**). Quando si sceglie questo comando, il debugger proverà immediatamente e l'ultimo collegare i processi associati all'utilizzo di **Connetti a processo** la finestra di dialogo.

Il debugger verrà ricollegare tentando innanzitutto di corrisponde all'ID di processo precedente e quindi, se il problema persiste, creando una corrispondenza tra il nome di processo precedente. Se non vengono trovate corrispondenze oppure se sono presenti più processi con lo stesso nome, la **Connetti a processo** verrà visualizzata la finestra di dialogo in cui è possibile selezionare il processo corretto.

> [!NOTE]
> Il **ricollegare al processo** command è una novità in Visual Studio 2017.

## <a name="additional-info"></a>Informazioni aggiuntive

Durante l'esecuzione del debug è possibile essere connessi a più di un programma, ma in un dato momento solo uno di tali programmi potrà essere attivo nel debugger. È possibile impostare il programma attivo nella barra degli strumenti **Posizione di debug** o nella finestra **Processi** .  
  
Se si tenta di connettersi a un processo appartenente a un account utente non attendibile, verrà visualizzata una finestra di dialogo contenente un avviso di sicurezza per chiedere conferma dell'operazione. Per ulteriori informazioni vedere [avviso di sicurezza: la connessione a un processo appartenente a un utente non attendibile può essere pericolosa. Se le informazioni seguenti risultano sospette o non si è certi, non connettersi a questo processo](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md).  
  
In alcuni casi, quando viene eseguito il debug in una sessione di Desktop remoto (Servizi terminal), nell'elenco **Processi disponibili** non vengono visualizzati tutti i processi disponibili. Se si esegue Visual Studio con un account utente limitato, nell'elenco **Processi disponibili** non verranno visualizzati i processi in esecuzione nella Sessione 0 utilizzata per i servizi e gli altri processi del server, incluso w3wp.exe. È possibile risolvere il problema eseguendo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] con un account amministratore o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dalla console del server invece di una sessione di Servizi Terminal. Se non è possibile adottare una di queste soluzioni alternative, una terza opzione consiste nel connettersi al processo eseguendo `vsjitdebugger.exe -p` *ProcessId* dalla riga di comando di Windows. È possibile determinare l'ID processo usando tlist.exe. Per ottenere tlist.exe, scaricare e installare gli strumenti di debug per Windows disponibili in  [Download di WDK e WinDbg](http://go.microsoft.com/fwlink/?LinkId=168279).

## <a name="BKMK_Scenarios"></a>Scenari di debug comuni

Per identificare se è necessario utilizzare **Connetti a processo** e sui processi a cui connettersi, di seguito sono riportati alcuni scenari di debug comuni (l'elenco non è completo). Dove sono disponibili altre istruzioni, vengono forniti i collegamenti.

Per alcuni tipi di app (ad esempio le app UWP), è non connettersi direttamente a un nome di processo, ma utilizzare il **Debug pacchetto applicazione installato** menu opzione (vedere la tabella).

> [!NOTE]
> Per informazioni sulla base di debug in Visual Studio, vedere [Introduzione al debugger](../debugger/getting-started-with-the-debugger.md).

|Scenario|Eseguire il debug (metodo)|Nome processo|Note e i collegamenti|
|-|-|-|-|
|Debug di un'app gestita o nativa nel computer locale|Utilizzare Connetti a processo o [debug standard](../debugger/getting-started-with-the-debugger.md)|*appname*.exe|Per accedere rapidamente la finestra di dialogo, utilizzare **CTRL + ALT + P** e quindi digitare la prima lettera del nome del processo.|
|Debug di applicazioni ASP.NET nel computer locale dopo l'avvio dell'app senza il debugger|Utilizzare Connetti a processo|iiexpress.exe|Ciò può risultare utile per rendere l'app di caricare più veloce, ad esempio, ad esempio, durante la profilatura. |
|Eseguire il debug remoto ASP.NET 4 o 4.5 in un server IIS|Utilizzare gli strumenti remoti e connettersi al processo|w3wp.exe|Vedere [ASP.NET di debug remoto in un computer remoto di IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Eseguire il debug remoto ASP.NET Core in un server IIS|Utilizzare gli strumenti remoti e connettersi al processo|dotnet.exe|Per la distribuzione di app, vedere [pubblica in IIS](https://docs.asp.net/en/latest/publishing/iis.html). Per il debug, vedere [remoto il debug di ASP.NET Core in un computer remoto di IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|Eseguire il debug di altri tipi di app supportata in un processo del server|Utilizzare gli strumenti remoti (se è remoto i server) e connettersi al processo|Iexplore.exe o altri processi|Se necessario, utilizzare Gestione attività per identificare il processo. Vedere [il debug remoto](../debugger/remote-debugging.md) e nelle sezioni successive di questo argomento|
|Debug remoto di un'applicazione desktop di Windows|Remote tools e F5|N/D| Vedere [debug remoto](../debugger/remote-debugging.md)|
|Un'app UWP (Universal), OneCore, HoloLens e IoT di debug remoto|Eseguire il debug pacchetto applicazione installata|N/D|Vedere [eseguire il Debug di un pacchetto dell'App installato](debug-installed-app-package.md) anziché **Connetti a processo**|
|Debug di un'app di App di Windows universale (UWP), OneCore, HoloLens e IoT che non è stato avviato da Visual Studio|Eseguire il debug pacchetto applicazione installata|N/D|Vedere [eseguire il Debug di un pacchetto dell'App installato](debug-installed-app-package.md) anziché **Connetti a processo**|  
  
> [!NOTE]
>  Affinché il debugger possa connettersi a codice scritto in C++, è necessario che venga generato l'elemento `DebuggableAttribute`. È possibile aggiungere automaticamente questo elemento al codice mediante il collegamento all'opzione del linker [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) .

## <a name="what-debugger-features-can-i-use"></a>Le funzionalità del debugger è possibile usare?

Per utilizzare le funzionalità complete del debugger di Visual Studio (ad esempio raggiungere i punti di interruzione) quando si collega a un processo, il file eseguibile deve corrispondere esattamente all'origine locale e simboli (ovvero, il debugger deve essere in grado di caricare il corretto [(.pbd) file di simboli ](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). Per impostazione predefinita, questo richiede una build di debug.

Per gli scenari di debug remoti, è necessario disporre del codice sorgente (o una copia del codice sorgente) già aperto in Visual Studio. I file binari compilati app nel computer remoto devono provenire dalla stessa compilazione come nel computer locale.

In alcuni scenari di debug locale, è possibile eseguire il debug in Visual Studio senza accesso all'origine se i file di simboli corretti sono presenti con l'app (per impostazione predefinita, è necessaria una build di debug). Per altre informazioni, vedere [specificare simboli e file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  
##  <a name="BKMK_Troubleshoot_attach_errors"></a>Risolvere gli errori di connessione  
 I processi in esecuzione a cui il debugger tenta di connettersi possono contenere uno o più tipi di codice. I tipi di codice a cui il debugger può connettersi vengono visualizzati e selezionati nella finestra di dialogo **Seleziona tipo di codice** .  
  
 In alcuni casi il debugger riesce a connettersi a un tipo di codice ma non a un altro. Questa situazione può verificarsi quando si tenta di stabilire una connessione a un processo in esecuzione in un computer remoto, nel quale potrebbero essere stati installati i componenti per il debug remoto solo per alcuni tipi di codice. Può inoltre verificarsi quando si tenta di stabilire una connessione a due o più processi per il debug diretto di un database. Durante il debug SQL è supportata esclusivamente la connessione a un singolo processo.  
  
 Se il debugger è in grado di connettersi solo ad alcuni tipi di codice, verrà visualizzato un messaggio che identifica i tipi per i quali la connessione ha avuto esito negativo.  
  
 Se il debugger riesce a connettersi ad almeno un tipo di codice, è possibile procedere con il debug del processo. Sarà possibile eseguire il debug solo dei tipi di codice con i quali è stata stabilita una connessione. Il messaggio di esempio sopra riportato segnala che non è stato possibile stabilire una connessione al tipo di codice di script. Non sarà quindi possibile eseguire il debug del codice di script nel processo. Il codice di script del processo verrà comunque eseguito, ma non sarà possibile impostare punti di interruzione, visualizzare dati o eseguire altre operazioni di debug nello script.  
  
 Se si desidera ottenere informazioni più specifiche sulla causa che ha impedito al debugger di connettersi a un tipo di codice, è possibile provare a ripetere la connessione solo a quel tipo di codice.  
  
 **Per ottenere informazioni specifiche sulla causa dell'errore associare un tipo di codice**  
  
1.  Disconnettersi dal processo. Scegliere **Disconnetti tutto** dal menu **Debug**.  
  
2.  Riconnettersi al processo, selezionando un solo tipo di codice.  
  
    1.  Nella finestra di dialogo **Connetti a processo** selezionare il processo nell'elenco **Processi disponibili** .  
  
    2.  Fare clic su **Seleziona**.  
  
    3.  Nella finestra di dialogo **Seleziona tipo di codice** selezionare il pulsante di opzione **Esegui il debug di questi tipi di codice** e il tipo di codice per cui si è verificato il problema di connessione. Deselezionare tutti gli altri codici.  
  
    4.  Fare clic su **OK**. La finestra di dialogo **Seleziona tipo di codice** verrà chiusa.  
  
    5.  Nella finestra di dialogo **Connetti a processo** scegliere **Connetti**.  
  
     La connessione non verrà eseguita e verrà visualizzato un messaggio di errore specifico.  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire il debug di più processi](../debugger/debug-multiple-processes.md)   
 [Il debug Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Debug remoto](../debugger/remote-debugging.md)