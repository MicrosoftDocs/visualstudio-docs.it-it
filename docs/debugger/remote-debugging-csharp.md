---
title: Il Debug remoto di un progetto c# o Visual Basic in Visual Studio | Documenti Microsoft
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: a9753fbb-e7f4-47f0-9dbe-9de90c6c8457
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 18cd64e24481111e22b3b9b842433bb1b1c19e0f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Debug di un progetto c# o Visual Basic in Visual Studio Remote
Per eseguire il debug di un'applicazione di Visual Studio che è stata distribuita in un altro computer, installare ed eseguire remote tools sul computer in cui è distribuita l'app, configurare il progetto per la connessione al computer remoto da Visual Studio e quindi eseguire l'app.

![I componenti del debugger remoto](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")
  
Per informazioni sulle app di Windows universale (UWP) di debug remoto, vedere [eseguire il Debug di un pacchetto dell'App installato](debug-installed-app-package.md).

## <a name="requirements"></a>Requisiti

Il debugger remoto è supportata in Windows 7 e versioni successive (non phone) e versioni di Windows Server a partire da Windows Server 2008 Service Pack 2. Per un elenco completo dei requisiti, vedere [requisiti](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Il debug tra due computer connessi tramite un proxy non è supportato. Il debug tramite una connessione di larghezza di banda ridotta, ad esempio di connessione remota a Internet, ad alta latenza o tramite Internet tra paesi non è consigliato e potrebbe non funzionare oppure essere inaccettabile.
  
## <a name="download-and-install-the-remote-tools"></a>Scaricare e installare remote tools

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> In alcuni scenari, può essere più efficiente per eseguire il debugger remoto da una condivisione file. Per ulteriori informazioni, vedere [eseguire il debugger remoto da una condivisione file](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a> Impostare il debugger remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se è necessario aggiungere le autorizzazioni per altri utenti, modificare la modalità di autenticazione o il numero di porta per il debugger remoto, vedere [configurare il debugger remoto](../debugger/remote-debugging.md#configure_msvsmon).
  
## <a name="remote_csharp"></a> Eseguire il debug remoto del progetto
Il debugger non può distribuire applicazioni desktop Visual C# o Visual Basic in un computer remoto, ma può comunque eseguirne il debug in modalità remota come illustrato di seguito. La procedura seguente si presuppone che si desidera eseguire il debug in un computer denominato **MJO DL**, come mostrato nell'illustrazione riportata di seguito.
  
1.  Creare un progetto WPF denominato **MyWpf**.  
  
2.  Impostare un punto di interruzione facilmente raggiungibile nel codice.  
  
     Ad esempio, è possibile impostare un punto di interruzione in un gestore pulsanti. A tale scopo, aprire MainWindow. XAML e aggiungere un pulsante dalla casella degli strumenti, quindi fare doppio clic sul pulsante per aprire il gestore.
  
3.  In Esplora soluzioni, fare clic sul progetto e scegliere **proprietà**.  
  
4.  Nel **proprietà** pagina, scegliere il **Debug** scheda.  
  
     ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5.  Verificare che il **directory di lavoro** casella di testo è vuota.  
  
6.  Scegliere **Usa computer remoto**e il tipo **MJO-DL:4022** nella casella di testo. (4022 è il numero di porta nella finestra del debugger remoto. Il numero di porta aumenta di 2 in ogni versione di Visual Studio).
  
7.  Assicurarsi che **Abilita debug codice nativo** non è selezionata.  
  
8.  Compilare il progetto.  
  
9. Creare una cartella nel computer remoto che è lo stesso percorso di **Debug** cartella nel computer di Visual Studio:  **\<percorso di origine > \MyWPF\MyWPF\bin\Debug**.  
  
10. Copiare il file eseguibile appena compilato dal computer di Visual Studio alla nuova cartella nel computer remoto.
  
    > [!CAUTION]
    >  Non apportare modifiche al codice o alla ricompilazione o è necessario ripetere questo passaggio. Il file eseguibile copiato nel computer remoto deve corrispondere esattamente all'origine locale e ai simboli.

    È possibile copiare manualmente il progetto, utilizzare Xcopy, Robocopy, Powershell o altre opzioni.
  
11. Assicurarsi che il debugger remoto è in esecuzione nel computer di destinazione (se non lo è, cercare **Debugger remoto** nel **avviare** menu). Finestra del debugger remoto è simile al seguente.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. In Visual Studio, avviare il debug (**Debug > Avvia debug**, o **F5**).  
  
13. Se richiesto, immettere le credenziali di rete per connettersi al computer remoto.  
  
     Le credenziali necessarie variano a seconda della configurazione della sicurezza della rete. In un computer di dominio, ad esempio, è possibile immettere il nome di dominio e la password. In un computer non appartenenti al dominio, è possibile immettere il nome del computer e un nome di account utente valido, ad esempio **MJO-DL\name@something.com**, con la password corretta.

     Dovrebbe essere che la finestra principale dell'applicazione WPF è aperta nel computer remoto.
  
14. Se necessario, intraprendere l'azione per il punto di interruzione. Il punto di interruzione dovrebbe essere attivo. In caso contrario, non sono stati caricati i simboli per l'applicazione. Ripetere e, se il problema persiste, ottenere informazioni sul caricamento dei simboli e come risolvere i problemi relativi all'indirizzo [le impostazioni dei simboli di informazioni sui file di simboli e Visual Studio](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/05/understanding-symbol-files-and-visual-studio-s-symbol-settings.aspx).
  
15. Nel computer di Visual Studio l'esecuzione viene arrestata in corrispondenza del punto di interruzione.
  
 Se sono presenti file non di codice che devono essere usati dall'applicazione, è necessario includerli nel progetto di Visual Studio. Creare una cartella di progetto per i file aggiuntivi (nel **Esplora**, fare clic su **Aggiungi > nuova cartella**). Quindi aggiungere i file nella cartella (nel **Esplora**, fare clic su **Aggiungi > elemento esistente**, quindi selezionare i file). Nel **proprietà** pagina per ogni file, impostare **copia nella Directory di Output di** a **Copia sempre**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurare il debug con simboli remoti 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Debug in Visual Studio](../debugger/index.md)  
 [Debugger Feature Tour](../debugger/debugger-feature-tour.md)  (Tour delle funzionalità del debugger)  
 [Configurare Windows Firewall per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Assegnazioni di porta del Debugger remoto](../debugger/remote-debugger-port-assignments.md)   
 [Debug remoto di ASP.NET in un computer remoto con IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)