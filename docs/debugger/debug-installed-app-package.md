---
title: Eseguire il debug di un pacchetto dell'app installato (UWP) | Documenti Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 07/17/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.remote.connection
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- app package, debug
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: ffddb3f49f4603c6f09bb12ef81d4c45bf0210c7
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="debug-an-installed-app-package-in-visual-studio-uwp"></a>Eseguire il debug di un pacchetto di applicazione installata in Visual Studio (UWP)

È possibile eseguire il debug di qualsiasi pacchetto dell'app installata, fare clic su **Debug > altre destinazioni Debug > Debug pacchetto applicazione installato**. Questo metodo di debug è disponibile per le app di Windows universale (UWP) su questi dispositivi:

* Windows 10 (per telefoni non supportato)
* XBox
* HoloLens
* IoT

Per ulteriori informazioni su queste funzionalità, vedere il post di blog sugli aggiornamenti per [il debug di pacchetti di app installati](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/30/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) e il post su [compilazione di App di Windows universale (UWP)](https://blogs.msdn.microsoft.com/visualstudio/2016/08/02/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-app-package-or-running-app-on-a-local-machine-or-device"></a>Eseguire il debug di un pacchetto dell'App installato o applicazione in esecuzione in un dispositivo o computer locale

1. Con il progetto UWP aperto in Visual Studio, fare clic su **Debug > altre destinazioni Debug > Debug pacchetto applicazione installato**.

2. Selezionare l'opzione **computer locale** o **dispositivo**.

     Se si sceglie **dispositivo**, il computer deve essere fisicamente connesso a un dispositivo Windows 10.

     ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

     Attualmente in esecuzione installato app pacchetti visualizzati sotto il **esecuzione** nodo. Installare pacchetti di app che non sono in esecuzione Mostra backup con **non è in esecuzione**.

3. Selezionare il nome dell'app che si desidera eseguire il debug in **esecuzione** o **non è in esecuzione** e scegliere **avviare** o, se l'app è già in esecuzione, scegliere **collegamento**.

     Se si seleziona **non devono essere avviate, ma il debug del codice quando viene avviata**, in questo modo il debugger di Visual Studio possa connettersi all'App all'avvio in un momento personalizzato. Si tratta di un metodo efficace per eseguire il debug dei percorsi di controllo da [avvio diversi metodi](/windows/uwp/xbox-apps/automate-launching-uwp-apps), ad esempio attivazione protocollo con parametri personalizzati.

> [!NOTE]
> Visual Studio può anche collegare qualsiasi processo di app UWP in esecuzione selezionando **Debug**e quindi **Connetti a processo**. Connessione a un processo in esecuzione non richiede il progetto originale di Visual Studio, tuttavia il caricamento dei simboli del processo sarà in modo significativo quando un processo che non è necessario il codice originale per il debug.
  
## <a name="remote"></a> Debug di un'App installata oppure è in esecuzione in un Computer remoto 

Quando si esegue il debug di un pacchetto dell'app installata in un computer remoto per la prima volta, Visual Studio installa la versione corretta di remote tools per il dispositivo di destinazione. Il dispositivo di destinazione deve essere un computer Windows 10, un dispositivo XBox, HoloLens e IoT.

1. Nel dispositivo Windows 10, abilitare [modalità sviluppatore](/windows/uwp/get-started/enable-your-device-for-development).

2. Se ci si connette a un PC remoto che esegue innanzitutto manualmente versione pre-del creatore dell'aggiornamento di Windows 10, [installare e avviare il debugger remoto](../debugger/remote-debugging.md).

     Per un dispositivo XBox, HoloLens e IoT e ai dispositivi Windows che eseguono l'aggiornamento del creatore di Windows 10, è necessario installare manualmente il debugger remoto. Remote tools verrà installato automaticamente quando si distribuisce l'app.

3. Fare clic su **Debug > altre destinazioni Debug > Debug pacchetto applicazione installato**.

4. Dal primo elenco a discesa, scegliere **computer remoto**.

5. Digitare il nome o indirizzo IP del computer che si desidera connettersi.

     ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

     Se non è possibile allegare l'utilizzo del nome computer (dopo aver scelto **avviare**), usare l'indirizzo IP. Usare l'indirizzo IP per i dispositivi XBox, HoloLens e IoT.

5. Scegliere la modalità di autenticazione selezionando un'opzione in **modalità di autenticazione**.

    Per la maggior parte delle applicazioni, mantenere il valore predefinito, **Universal (protocollo non crittografato)**.

6. Selezionare il nome dell'app che si desidera eseguire il debug in **esecuzione** o **non è in esecuzione** e scegliere **avviare** o (per le applicazioni in esecuzione) **collegamento**.

     Se si seleziona **non devono essere avviate, ma il debug del codice quando viene avviata**, in questo modo il debugger di Visual Studio possa connettersi al pacchetto di app quando viene avviata in un momento personalizzato. Si tratta di un metodo efficace per eseguire il debug dei percorsi di controllo da [avvio diversi metodi](/windows/uwp/xbox-apps/automate-launching-uwp-apps), ad esempio attivazione protocollo con parametri personalizzati.

     Quando si esegue il debug di un pacchetto di applicazione installata in un dispositivo XBox, HoloLens e IoT collegato per la prima volta, Visual Studio installa la versione corretta del debugger remoto per il dispositivo di destinazione. L'operazione potrebbe richiedere un po' di tempo e verrà visualizzato un messaggio ``Starting remote debugger`` mentre questo è il problema.

     > [!NOTE]
> È presente, XBox o HoloLens dispositivo verrà riavviato l'app con il debugger collegato se è già in esecuzione.

Per informazioni sulle opzioni avanzate per la distribuzione remota di App UWP, vedere [distribuzione e debug di App UWP](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps.md#advanced-remote-deployment-options). 
  
## <a name="see-also"></a>Vedere anche  
 [Debug in Visual Studio](../debugger/index.md)  
 [Tour delle funzionalità del debugger](../debugger/debugger-feature-tour.md)  
 [Debug remoto](../debugger/remote-debugging.md)  
 [Configurare Windows Firewall per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md)  
 [Assegnazioni delle porte del debugger remoto](../debugger/remote-debugger-port-assignments.md)  
 [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)