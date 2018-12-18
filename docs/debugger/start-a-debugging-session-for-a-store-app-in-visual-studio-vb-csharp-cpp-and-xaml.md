---
title: Avviare una sessione di debug per un'app UWP in Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 01/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VC.Project.IVCAppHostRemoteDebugPageObject.MachineName
- VC.Project.IVCAppHostRemoteDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostTetheredDebugPageObject.DebuggerType
- VC.Project.IVCAppHostLocalDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostRemoteDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.DebuggerType
- ImmersiveProjects.Properties.Debug
- VC.Project.IVCAppHostTetheredDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostLocalDebugPageObject.AllowLocalNetworkLoopback
- AppPackage.Properties.Debug
- VC.Project.IVCAppHostRemoteDebugPageObject.Authentication
- VC.Project.IVCAppHostRemoteDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.BreakpointBehavior
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: b298e2b17f1aa8805e0ab896c6978744c6c3bd53
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="start-a-debugging-session-for-a-uwp-app-in-visual-studio"></a>Avviare una sessione di debug per un'app UWP in Visual Studio
  
 In questo argomento viene descritto come avviare una sessione di debug per App UWP scritte in XAML e Visual C++, Visual c# o Visual Basic e per le app UWP scritte in HTML e JavaScript. Il debug di un'app comporta sia la configurazione della la sessione di debug che la scelta della modalità di avvio dell'app.  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a> Il modo più semplice per avviare il debug  
  
1.  Apri la soluzione dell'app in Visual Studio.  
  
2.  Premi F5.  
  
 Visual Studio compila e avvia l'app con il debugger collegato. L'esecuzione continua fino a raggiungere un punto di interruzione. Sospendi manualmente l'esecuzione e si verifica un'eccezione non gestita o l'app termina.  
  
##  <a name="BKMK_Choose_the_build_configuration_options"></a> Scegliere le opzioni di configurazione della compilazione  
  
1.   Dall'elenco a discesa elenco accanto al **Avvia debug** pulsante del debugger **Standard** sulla barra degli strumenti, scegliere **Debug**.  
  
2.  Dall'elenco **Piattaforma** seleziona la piattaforma di destinazione per cui eseguire la compilazione.  
  
##  <a name="BKMK_Choose_the_deployment_target"></a> Scegliere la destinazione di distribuzione  
  
È possibile distribuire ed eseguire il debug di un'app UWP in computer di Visual Studio, un dispositivo connesso, il simulatore di Visual Studio nel computer locale, un dispositivo remoto o un emulatore. Selezionare la destinazione di distribuzione dall'elenco a discesa a destra del **piattaforma** destinazione del debugger **Standard** barra degli strumenti.
  
![Selezionare una destinazione di distribuzione](../debugger/media/vsrun_select_target_device.png)  
  
Scegli una delle seguenti opzioni:  
  
|||  
|-|-|  
|**Computer locale**|Esegue il debug dell'app nella sessione corrente nel computer locale.|  
|**Simulatore**|Eseguire il debug dell'app nel simulatore di Visual Studio per App UWP. Il simulatore è una finestra del Desktop che consente di eseguire il debug delle funzionalità del dispositivo, ad esempio i movimenti tocco e rotazione del dispositivo, che potrebbe non essere disponibile nel computer locale. Questa opzione è disponibile solo se l'app **minima piattaforma di destinazione. Versione** è minore o uguale al sistema operativo nel computer di sviluppo. Vedere [UWP eseguire app nel simulatore](../debugger/run-windows-store-apps-in-the-simulator.md).|  
|**Computer remoto**|Esegue il debug dell'app in un dispositivo connesso al computer locale su una rete Intranet o collegato direttamente tramite un cavo Ethernet. Per eseguire il debug in modalità remota, Remote Tools per Visual Studio deve essere installato e in esecuzione sul dispositivo remoto. Vedere [App UWP eseguire in un computer remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
|**Dispositivo**|Eseguire il debug dell'app in un dispositivo USB-connected. Il dispositivo deve essere sbloccato dallo sviluppatore e avere la schermata sbloccata.|  
|**Emulatore di dispositivi mobili**|Avviare un emulatore con la configurazione specificata nel nome dell'emulatore, distribuire l'app e avviare il debug. Gli emulatori sono disponibili solo in computer Hyper-V abilitato.|  

##  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Scegli opzioni di debug aggiuntive  

Se è necessario configurare le opzioni di debug aggiuntive, aprire la pagina delle proprietà per il progetto.
  
1.  Selezionare il progetto in Esplora soluzioni. Scegli **Proprietà**dal menu di scelta rapida.  
  
2.  Eseguire questa operazione per aprire la pagina delle proprietà debug del progetto:  
  
    -   Per le app Visual C# e Visual Basic scegli **Debug**.  
  
         ![C&#35; &#47; pagina delle proprietà debug progetto VB](../debugger/media/dbg_csvb_debugpropertypage.png)  
  
    -   Per le app Visual C++ e JavaScript Espandi il **le proprietà di configurazione** nodo e quindi scegliere **debug**.  
  
         ![C&#43; &#43; app UWP pagina delle proprietà di debug](../debugger/media/dbg_cpp_debugpropertypage.png)  

###  <a name="BKMK_Choose_the_debugger_to_use"></a> Scegliere il debugger da utilizzare  
Per impostazione predefinita, Visual Studio esegue il debug del codice gestito nelle app Visual Basic e C#. Per le applicazioni C# e Visual Basic puoi scegliere di eseguire il debug di codice nativo e gestito C/C++ nell'app. Nelle App C++, Visual Studio esegue il debug del codice nativo per impostazione predefinita. Nelle App JavaScript, Visual Studio esegue il debug di script per impostazione predefinita. 
  
Per le app C++ e JavaScript, è possibile scegliere di eseguire il debug di tipi di codice specifici presenti nei componenti dell'app al posto o in aggiunta al codice nativo. Specifica il codice per cui eseguire il debug nell'elenco **Tipo di debugger** nella pagina delle proprietà **Debug** del progetto dell'app.  
  
Scegli uno di questi debugger dall'elenco **Processo applicativo** :  
  
|||  
|-|-|  
|**Solo gestito**|Esegue il debug del codice gestito nell'app. Il codice JavaScript e il codice C/C++ nativo vengono ignorati.|  
|**Solo nativo**|Esegue il debug del codice C/C++ nativo nell'app. Il codice gestito e il codice JavaScript vengono ignorati.|  
|**Misto (gestito e nativo)**|Esegue il debug sia del codice C++ nativo e del codice gestito nell'app. Il codice JavaScript viene ignorato. In progetti C++, questa opzione è denominata **(gestito e nativo)**.|  
|**Solo script**|Esegue il debug del codice JavaScript nell'app. Il codice gestito e il codice nativo vengono ignorati.|  
|**Script e Native**|Eseguire il debug di codice C/C++ nativo e il codice JavaScript nell'app. Il codice gestito viene ignorato. Disponibile solo progetti C++.|  
|**Solo GPU (C++ AMP)**|Esegue il debug del codice C++ nativo eseguito su un'unità di elaborazione grafica (GPU). Disponibile solo progetti C++.|  

Le app c# e Visual Basic, è inoltre possibile impostare lo stesso **tipo di Debugger** i valori per qualsiasi attività in background che fanno parte del progetto.
  
###  <a name="BKMK__Optional__Delay_starting_the_debug_session"></a> (Facoltativo) Ritardare l'avvio della sessione di debug  
 Per impostazione predefinita, Visual Studio avvia immediatamente l'app quando avvii il debug. Puoi anche avviare una sessione di debug ma ritardare l'avvio dell'app. Quando scegli questa opzione, l'app viene aperta nel debugger quando viene avviata dalla schermata Start o tramite un contratto di attivazione oppure quando viene avviata da un altro processo o metodo. Puoi ritardare l'avvio dell'app anche quando vuoi eseguire il debug di un'attività in background mentre l'app stessa non è in esecuzione.  
  
 Per ritardare l'avvio dell'app, puoi procedere come segue:  
  
-   Per le app Visual C# e Visual Basic seleziona **Non eseguire il codice utente, ma eseguine il debug all'avvio** nella pagina delle proprietà **Debug** .  
  
-   Per le app Visual C++ e JavaScript, scegliere **n** dal **Avvia applicazione** elenco il **debug** pagina delle proprietà.  
  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> (Facoltativo) Disabilitare i loopback di rete  
  
 Per motivi di sicurezza, un'app UWP che viene installata in modalità standard non è possibile effettuare chiamate di rete per il dispositivo in che cui è installata. Per impostazione predefinita, la distribuzione di Visual Studio crea una esenzione da questa regola per l'app distribuita. Questa esenzione ti consente di verificare le procedure di comunicazione in un singolo computer. Prima di inviare l'app a Microsoft Store, è consigliabile testare l'app senza l'esenzione.  
  
 Per rimuovere l'esenzione relativa al loopback della rete:  
  
-   Per le app Visual c# e Visual Basic, deseleziona la **Consenti loopback della rete locale** casella di controllo di **Debug** pagina delle proprietà.  
  
-   Per le app Visual C++ e JavaScript, scegliere **n** dal **Consenti Loopback della rete locale** elenco il **debug** pagina delle proprietà.  
  
###  <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> (Facoltativo) Reinstallare l'app all'avvio del debug  
 Per diagnosticare i problemi di installazione e configurazione iniziale dell'app in Visual C# o Visual Basic, scegli **Disinstalla e reinstalla il pacchetto** nella pagina delle proprietà **Debug**  per ricreare un'installazione originale all'avvio del debug. Questa opzione non è disponibile per i progetti Visual C++ e JavaScript.  
  
###  <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> (Facoltativo) Disabilitare il requisito di autenticazione per avviare il debugger remoto  
  
 Per impostazione predefinita, è necessario fornire le credenziali per eseguire il debugger remoto quando si seleziona **computer remoto** come destinazione di distribuzione.
  
> [!IMPORTANT]
>  È possibile scegliere di eseguire il debugger remoto senza autenticazione, ma è fortemente sconsigliata. perché priva di qualsiasi sicurezza di rete. Non selezionare Nessuna autenticazione solo se si è certi che la rete non è soggetta a rischi da traffico ostile o codice dannoso.  
  
 Per rimuovere il requisito di autenticazione:  
  
1.  Per le app Visual c# e Visual Basic, selezionare **computer remoto** come il **dispositivo di destinazione** sul **Debug** pagina delle proprietà e quindi impostare **modalità di autenticazione**  a **Nessuno** o **Universal (protocollo non crittografato)**.
  
2.  Per le app Visual C++ e JavaScript, selezionare **computer remoto** come il **dispositivo di destinazione** sul **debug** pagina delle proprietà e quindi impostare **richiedono Autenticazione** a **Nessuno** o **Universal (protocollo non crittografato)**.  

    **Universal (protocollo non crittografato)** viene utilizzato quando si distribuisce in un dispositivo remoto. Attualmente è per i dispositivi IoT, dispositivi Xbox e HoloLens dispositivi, nonché creatori di aggiornamento o PC più recente. Universal (protocollo non crittografato) deve essere utilizzato solo su reti attendibili. La connessione di debug è protetto da utenti malintenzionati in grado di intercettare e modificare i dati passati tra lo sviluppo e il computer remoto.  
  
##  <a name="BKMK_Start_the_debugging_session"></a> Avviare la sessione di debug  
  
###  <a name="BKMK_Start_debugging__F5_"></a> Avviare i debug (F5)  
 Quando si sceglie **Avvia debug** (tastiera: F5) sul **Debug** menu, Visual Studio avvia l'app con il debugger collegato. L'esecuzione continua fino a raggiungere un punto di interruzione. Sospendi manualmente l'esecuzione e si verifica un'eccezione o l'app termina.  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Avviare il debug (F5) ma ritardare l'avvio dell'app  
 Puoi impostare l'app per l'esecuzione in modalità di debug, ma avviarla con un metodo diverso dal debugger. Ad esempio, è necessario per il debug dell'avvio dell'app dal menu Start o eseguire il debug di un processo in background nell'app senza avviare l'app. Per ritardare l'avvio dell'app, eseguire questa operazione:  
  
-   Nel **Debug** pagina delle proprietà dell'app (**debug** in Visual C++ e JavaScript)  
  
    -   Per le app Visual C# e Visual Basic, scegli **Non eseguire il codice utente, ma eseguine il debug all'avvio**.  
  
    -   Per le app Visual C++ e JavaScript, scegliere **Sì** dal **Avvia applicazione** elenco.  
  
-   Scegliere **Avvia debug** sul **Debug** menu (tastiera: F5).  
  
-   Avvia l'app dal menu Start, da un contratto di esecuzione o da un'altra routine.  
  
 L'app viene avviata in modalità debug. L'esecuzione continua fino a raggiungere un punto di interruzione. Sospendi manualmente l'esecuzione e si verifica un'eccezione non gestita o l'app termina.  
  
 Per ulteriori informazioni sul debug di attività in background, vedere [Trigger sospendere, riprendere e gli eventi per App UWP in background)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
###  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Avviare un'app installata nel debugger  
Quando avvii il debug utilizzando F5, Visual Studio compila e distribuisce l'app, la imposta per l'esecuzione in modalità debug, quindi la avvia. Per avviare un'app già installata in un dispositivo, usare il **Debug pacchetto applicazione installato** la finestra di dialogo. Questa procedura è utile quando è necessario eseguire il debug di un'app installata da Microsoft Store o quando Disponi dei file di origine per l'app, ma non è un progetto di Visual Studio per l'app. Ad esempio, potresti disporre di un sistema di compilazione personalizzato che non utilizza progetti o soluzioni di Visual Studio.  
  
L'app può essere installata nel dispositivo locale oppure in un dispositivo remoto.  Puoi avviare l'app immediatamente oppure impostarla per l'esecuzione nel debugger quando viene avviata da un altro processo o metodo, ad esempio dal menu Start o da un contratto di attivazione. Puoi anche impostarne l'esecuzione in modalità debug per eseguire il debug di un processo in background senza avviare l'app. Per ulteriori informazioni, vedere [Trigger sospendere, riprendere e gli eventi per App UWP in background)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
Per avviare un'app installata nel debugger, scegliere **Debug**, quindi **altre destinazioni debug**e quindi **Debug pacchetto applicazione installato**. Per ulteriori istruzioni, vedere [eseguire il Debug di un pacchetto dell'app installato](../debugger/debug-installed-app-package.md).

###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Collegare il debugger a un'app UWP in esecuzione  

Per eseguire il debug di un'app UWP in esecuzione, scegliere **Debug**, quindi **altre destinazioni debug**e quindi **Debug pacchetto applicazione installato**. Per ulteriori istruzioni, vedere [eseguire il Debug di un pacchetto dell'app installato](../debugger/debug-installed-app-package.md).
  
###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Collegare il debugger a un'app di in esecuzione Windows 8. x
 Per collegare il debugger a un'app in [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] , devi utilizzare Debuggable Package Manager per impostare l'esecuzione dell'app in modalità debug. Debuggable Package Manager viene installato con Remote Tools per Visual Studio.  
  
 Il collegamento del debugger a un'app è utile quando devi eseguire il debug di un'app già installata, ad esempio un'app installata da [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]. Il collegamento è necessario quando disponi dei file di origine dell'app, ma non di un progetto di Visual Studio per l'app. Ad esempio, potresti disporre di un sistema di compilazione personalizzato che non utilizza progetti o soluzioni di Visual Studio.  
  
 Per collegare il debugger a un'app devi eseguire questi passaggi:  
  
1.  Imposta l'esecuzione dell'app in modalità debug. Questa operazione deve essere effettuata quando l'app non è in esecuzione.  
  
2.  Avvia l'app. Puoi avviare l'app dalla schermata Start, da un contratto di esecuzione o tramite un altro metodo.  
  
3.  Collega il debugger all'app in esecuzione.  
  
####  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Impostare l'esecuzione dell'app in modalità debug  
  
1.  Installare Remote Tools per Visual Studio sul dispositivo in cui è installata l'app. Vedere [installazione di remote tools](../debugger/remote-debugging.md).  
  
2.  Nella schermata Start cerca `Debuggable Package Manager` e avvialo.  
  
     Viene visualizzata una finestra di PowerShell correttamente configurata per il cmdlet AppxDebug.  
  
3.  Per abilitare il debug di un'app, devi specificare l'identificatore PackageFullName dell'app. Per visualizzare un elenco di tutte le app che includono PackageFullName, digita `Get-AppxPackage` al prompt di PowerShell.  
  
4.  Al prompt di PowerShell immetti `Enable-AppxDebug` *PackageFullName* in cui *PackageFullName* è l'identificatore PackageFullName dell'app.  
  
####  <a name="BKMK_Attach_the_debugger"></a> Collegare il debugger  
 Per collegare il debugger:  
  
1.  Scegliere **Connetti a processo** dal menu **Debug**.  
  
     Verrà visualizzata la finestra di dialogo **Connetti a processo** .  
  
2.  Per connetterti a un'app in un dispositivo remoto, specifica il dispositivo remoto nella casella **Qualificatore** . È possibile:  
  
    -   Immetti il nome nella casella **Qualificatore** .  
  
    -   Fai clic sulla freccia in giù nella casella **Qualificatore** , quindi scegli il dispositivo da un elenco di dispositivi collegati precedentemente.  
  
    -   Scegli **Trova** per selezionare il dispositivo da un elenco di dispositivi sulla subnet locale.  
  
3.  Specifica il tipo di codice di cui vuoi eseguire il debug nella casella **Connetti a** .  
  
     Scegli **Seleziona** , quindi effettua una delle seguenti operazioni:  
  
    -   Scegli **Determina automaticamente il tipo di codice di cui eseguire il debug**.  
  
    -   Scegli **Esegui il debug di questi tipi di codice** , quindi scegli uno o più tipi dall'elenco.  
  
4.  Nell'elenco **Processi disponibili**  scegli il processo dell'app.  

    > [!NOTE]
    >  A differenza di altri tipi di app, App JavaScript eseguito in un'istanza del processo wwahost.exe. Se vengono eseguite altre app JavaScript quando colleghi il debugger all'app, dovrai conoscere l'ID processo numerico (PID) del processo wwahost.exe in cui viene eseguita l'app.  
    >   
    >  Il modo più semplice per gestire questa situazione consiste nel chiudere tutte le altre app JavaScript. Altrimenti, puoi aprire Gestione attività di Windows prima di avviare l'app e annotare gli ID dei processi wwahost.exe. Quando si specifica il processo per allegare nella **processi disponibili** wwahost.exe dell'app nella finestra di dialogo avrà un id diverso da quelli annotati.  
  
5.  Scegliere **Connetti**.  
  
 Visual Studio collega il debugger al processo. L'esecuzione continua fino a raggiungere un punto di interruzione. Sospendi manualmente l'esecuzione e si verifica un'eccezione non gestita o l'app termina.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug delle App in Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   