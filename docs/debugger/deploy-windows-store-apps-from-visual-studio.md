---
title: Distribuire le app UWP da Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 01/16/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 28b1897fad45ae0c2bd174c39433645caf011f09
ms.sourcegitcommit: 5d43e9590e2246084670b79269cc9d99124bb3df
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>Distribuire le app UWP da Visual Studio
  
 La funzionalità di distribuzione di Visual Studio compila e registra App UWP che vengono create con Visual Studio su un dispositivo di destinazione. Il modo in cui viene registrata l'app è determinato dal tipo di dispositivo, ovvero se è locale o remoto:  
  
-   Quando la destinazione è il computer Visual Studio locale, Visual Studio registra l'app dalla cartella della build dell'app stessa.  
  
-   Quando la destinazione è un dispositivo remoto, Visual Studio copia i file necessari nel computer remoto e registra l'app su questo dispositivo.  
  
 La distribuzione avviene automaticamente quando si esegue il debug dell'app da Visual Studio usando il **Avvia debug** opzione (tastiera: F5) o **Avvia senza eseguire debug** opzione (tastiera: CTRL + F5). Puoi distribuire l'app anche manualmente. Ecco gli scenari in cui la distribuzione manuale può essere utile:  
  
-   Test ad hoc su un computer locale o remoto.  
  
-   Distribuzione di un'app che avvia un'altra app di cui vuoi eseguire il debug.  
  
-   Distribuzione di un'app di cui viene eseguito il debug quando viene avviata da un'altra app o da un altro metodo.
  
##  <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a>Come distribuire un'app UWP  
 La distribuzione manuale di un'app è un processo facile:  
  
1.  Se esegui la distribuzione in un dispositivo remoto, specifica il nome o l'indirizzo IP del dispositivo nella pagina delle proprietà del progetto di avvio dell'app. I passaggi necessari sono elencati più avanti in questo argomento.  
  
2.  Sulla barra degli strumenti Visual Studio del debugger seleziona la destinazione di distribuzione nell'elenco a discesa accanto al pulsante **Avvia debug** .  
  
     ![Eseguire sul computer locale](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")  
  
3.  Scegli **Distribuzione** dal menu **Compilazione**.  
  
##  <a name="BKMK_How_to_specify_a_remote_device"></a> Come specificare un dispositivo remoto  

**Prerequisiti**  
  
In un dispositivo remoto Windows 10, è necessario abilitare [modalità sviluppatore](/windows/uwp/get-started/enable-your-device-for-development). Nei dispositivi Windows 10 che eseguono l'aggiornamento del creatore o versione successiva, gli strumenti remoti vengono installati automaticamente quando si distribuisce l'app. Per ulteriori informazioni, vedere [eseguire il Debug di un pacchetto dell'app installato](../debugger/debug-installed-app-package.md).

> [!NOTE]
> Nelle versioni di aggiornamento di pre-del creatore di Windows 10, Remote Tools per Visual Studio deve essere installato nel dispositivo remoto e il debugger remoto deve essere in esecuzione.
  
La distribuzione usa il canale di rete del debugger remoto per inviare i file dell'app al dispositivo remoto.  
  
#### <a name="to-specify-a-remote-device"></a>Per specificare un dispositivo remoto  
  
1.  Nella pagina delle proprietà Debug del progetto di avvio specifica il nome o l'indirizzo IP di una destinazione di distribuzione remota.  
  
2.  Per aprire la pagina delle proprietà Debug, seleziona il progetto in Esplora soluzioni e scegli **Proprietà** dal menu di scelta rapida.  
  
3.  Seleziona il nodo **Debug** nella finestra della pagina delle proprietà.

4. Per **dispositivo di destinazione**selezionare **computer remoto**.

5. In **computer remoto**, fare clic su **trovare**.
  
4.  È possibile digitare il nome o indirizzo IP del dispositivo remoto oppure è possibile scegliere il dispositivo di **connessione remota** la finestra di dialogo.  
  
     ![Finestra di dialogo Seleziona connessione Debugger remoto](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
     Il **connessione remota** la finestra di dialogo Visualizza i dispositivi sulla subnet della rete locale e qualsiasi dispositivo connesso direttamente al computer con Visual Studio tramite un cavo Ethernet.  
  
 **Indicazione del dispositivo remoto nella pagina di un progetto JavaScript o Visual C++**  
  
 ![C &#43; &#43; le proprietà per il debug remoto di progetto](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1.  Scegliere **Debugger remoto** dall'elenco **Debugger da avviare** .  
  
2.  Immetti il nome di rete del dispositivo remoto nella casella **Nome computer** . In alternativa, puoi fare clic sulla freccia in giù della casella per selezionare il dispositivo nella finestra di dialogo Seleziona connessione debugger remoto.  
  
 **Indicazione del dispositivo remoto nella pagina di un progetto Visual C# o Visual Basic**  
  
 ![Proprietà del progetto per il debug remoto gestito](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1.  Scegliere **Computer remoto** dall'elenco **Dispositivo di destinazione** .  
  
2.  Immetti il nome di rete del dispositivo remoto nella casella **Computer remoto** o fai clic su **Trova** per scegliere il dispositivo nella finestra di dialogo **Seleziona connessione debugger remoto** .  
  
##  <a name="BKMK_Deployment_options"></a> Opzioni di distribuzione  
 Di seguito sono indicate le opzioni di distribuzione che puoi impostare nella pagina delle proprietà Debug del progetto di avvio.  
  
 **Consenti loopback della rete locale**  
 Per motivi di sicurezza UWP o [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] app installata in modalità standard non è consentito effettuare chiamate di rete per il dispositivo in cui è installata. Per impostazione predefinita, la distribuzione di Visual Studio crea una esenzione da questa regola per l'app distribuita. Questa esenzione ti consente di verificare le procedure di comunicazione in un singolo computer. Prima di inviare l'app a [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)], dovrai testarla senza l'esenzione.  
  
 Per rimuovere l'esenzione relativa al loopback della rete:  
  
-   Nella pagina delle proprietà Debug in C# e Visual Basic, deseleziona la casella di controllo **Consenti loopback della rete locale** .  
  
-   Nella pagina delle proprietà Debug in JavaScript e C++ imposta il valore di **Consenti loopback della rete locale** su **No**.  
  
 **Non eseguire il codice utente, ma eseguine il debug all'avvio (C# e Visual Basic)/Avvia applicazione (JavaScript e C++)**  
 Per configurare la distribuzione in modo da avviare automaticamente una sessione di debug all'avvio dell'app:  
  
-   Nella pagina delle proprietà Debug in C# e Visual Basic seleziona la casella di controllo **Non eseguire il codice utente, ma eseguine il debug all'avvio** .  
  
-   Nella pagina delle proprietà Debug in JavaScript e C++ imposta il valore di **Avvia applicazione** su **Sì**.  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni di distribuzione remota avanzate](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)  
 [Eseguire il debug di un pacchetto dell'app installata](../debugger/debug-installed-app-package.md)   
 [Eseguire app da Visual Studio](../debugger/run-store-apps-from-visual-studio.md)