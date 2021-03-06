---
title: ASP.NET Core di debug remoto in IIS e Azure | Microsoft Docs
description: Informazioni su come configurare e configurare un'app di Visual Studio ASP.NET Core, distribuirla in IIS usando Azure e collegarla da Visual Studio.
ms.custom: remotedebugging
ms.date: 05/06/2020
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 619f1f1cc99cbab425bc1bcb2bac181e09db8fc4
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/06/2021
ms.locfileid: "102250055"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>ASP.NET Core di debug remoto in IIS in Azure in Visual Studio

Questa guida illustra come configurare e configurare un'app ASP.NET Core di Visual Studio, distribuirla in IIS usando Azure e collegarla da Visual Studio.

Il metodo consigliato per eseguire il debug remoto in Azure dipende dallo scenario:

* Per eseguire il debug di ASP.NET Core nel servizio app Azure, vedere [eseguire il debug di app di Azure con il snapshot debugger](../debugger/debug-live-azure-applications.md). Questo è il metodo consigliato.
* Per eseguire il debug di ASP.NET Core in app Azure servizio usando funzionalità di debug più tradizionali, seguire la procedura descritta in questo argomento (vedere la sezione [debug remoto sul servizio app Azure](#remote_debug_azure_app_service)).

    In questo scenario, è necessario distribuire l'app da Visual Studio in Azure, ma non è necessario installare o configurare manualmente IIS o il debugger remoto (questi componenti sono rappresentati da linee tratteggiate), come illustrato nella figura seguente.

    ![Diagramma che mostra la relazione tra Visual Studio, app Azure servizio e un'app ASP.NET. IIS e il debugger remoto sono rappresentati da linee tratteggiate.](../debugger/media/remote-debugger-azure-app-service.png)

* Per eseguire il debug di IIS in una macchina virtuale di Azure, seguire la procedura descritta in questo argomento (vedere la sezione [debug remoto in una macchina virtuale di Azure](#remote_debug_azure_vm)). In questo modo è possibile utilizzare una configurazione personalizzata di IIS, ma i passaggi di installazione e distribuzione sono più complicati.

    Per una macchina virtuale di Azure, è necessario distribuire l'app da Visual Studio in Azure ed è inoltre necessario installare manualmente il ruolo IIS e il debugger remoto, come illustrato nella figura seguente.

    ![Diagramma che mostra la relazione tra Visual Studio, una macchina virtuale di Azure e un'app ASP.NET. IIS e il debugger remoto sono rappresentati con linee continue.](../debugger/media/remote-debugger-azure-vm.png)

* Per eseguire il debug di ASP.NET Core in Azure Service Fabric, vedere [eseguire il debug di un'applicazione Service Fabric remota](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Assicurarsi di eliminare le risorse di Azure create al termine della procedura descritta in questa esercitazione. In questo modo è possibile evitare di incorrere in addebiti superflui.

## <a name="prerequisites"></a>Prerequisiti

::: moniker range=">=vs-2019"
Visual Studio 2019 è necessario per seguire i passaggi illustrati in questo articolo.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 è necessario per seguire i passaggi illustrati in questo articolo.
::: moniker-end

### <a name="network-requirements"></a>Requisiti di rete

Il debug tra due computer connessi tramite un proxy non è supportato. Non è consigliabile eseguire il debug su una connessione a larghezza di banda elevata o a bassa latenza, ad esempio Internet remoto, o su Internet tra paesi, e potrebbe avere esito negativo o essere inaccettabile. Per un elenco completo dei requisiti, vedere [requisiti](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Creare l'applicazione ASP.NET Core nel computer di Visual Studio

1. Creare una nuova applicazione Web ASP.NET Core.

    ::: moniker range=">=vs-2019"
    In Visual Studio 2019, scegliere **Crea un nuovo progetto** nella finestra Start. Se la finestra di avvio non è aperta, scegliere  >  **finestra di avvio** file. Digitare **app Web**, scegliere **C#** come lingua, quindi scegliere **ASP.NET Core applicazione Web (Model-View-Controller)**, quindi scegliere **Avanti**. Nella schermata successiva denominare il progetto **MyASPApp**, quindi scegliere **Avanti**.

    Scegliere il Framework di destinazione consigliato (.NET Core 3,1) o .NET 5, quindi scegliere **Crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017 scegliere **File > nuovo progetto >**, quindi selezionare **Visual C# > Web > ASP.NET Core applicazione Web**. Nella sezione modelli di ASP.NET Core selezionare **applicazione Web (Model-View-Controller)**. Assicurarsi che sia selezionata l'opzione ASP.NET Core 2,1, che **Abilita supporto Docker** non sia selezionata e che **l'autenticazione** sia impostata su **Nessuna autenticazione**. Denominare il progetto **MyASPApp**.
    ::: moniker-end

1. Aprire il file About.cshtml.cs e impostare un punto di interruzione nel `OnGet` Metodo (nei modelli precedenti, aprire HomeController.cs e impostare il punto di interruzione nel `About()` metodo).

## <a name="remote-debug-aspnet-core-on-an-azure-app-service"></a><a name="remote_debug_azure_app_service"></a> ASP.NET Core di debug remoto in un servizio app Azure

Da Visual Studio è possibile pubblicare rapidamente ed eseguire il debug dell'app in un'istanza con provisioning completo di IIS. Tuttavia, la configurazione di IIS è preimpostata e non è possibile personalizzarla. Per istruzioni più dettagliate, vedere [distribuire un'app web ASP.NET Core in Azure con Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Se è necessario avere la possibilità di personalizzare IIS, provare a eseguire il debug in una [macchina virtuale di Azure](#remote_debug_azure_vm).

#### <a name="to-deploy-the-app-and-remote-debug-using-cloud-explorer"></a>Per distribuire l'app e il debug remoto usando Cloud Explorer

1. In Visual Studio fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **pubblica**.

    Se sono stati configurati dei profili di pubblicazione, viene visualizzato il riquadro **Pubblica**. Selezionare **nuovo** o **nuovo profilo**.

1. Creare un nuovo profilo di pubblicazione.

    ::: moniker range=">=vs-2019"
    Scegliere **Azure** dalla finestra di dialogo **pubblica** e fare clic su **Avanti**. Quindi scegliere **servizio app Azure (Windows)**, fare clic su **Avanti** e seguire le istruzioni per creare un profilo.

    :::image type="content" source="../debugger/media/vs-2019/remotedbg-azure-app-service-profile.png" alt-text="Distribuire un'app Web ASP.NET Core in Azure con Visual Studio":::
    ::: moniker-end
    ::: moniker range="vs-2017"

    Scegliere **servizio app Azure** dalla finestra di dialogo **pubblica** , selezionare **Crea nuovo** e seguire le istruzioni per creare un profilo.

    ![Eseguire la pubblicazione nel servizio app di Azure](../debugger/media/remotedbg_azure_app_service_profile.png)
    ::: moniker-end

    Per istruzioni più dettagliate, vedere [distribuire un'app web ASP.NET Core in Azure con Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

1. Nella finestra Pubblica scegliere **modifica configurazione** e passare a una configurazione di debug, quindi scegliere **pubblica**.

   Per eseguire il debug dell'app, è necessaria una configurazione di debug.

1. Aprire **Cloud Explorer** (**Visualizza**  >  **Cloud Explorer**), fare clic con il pulsante destro del mouse sull'istanza del servizio app e scegliere **Connetti debugger**.

   Se Cloud Explorer non è disponibile, aprire Esplora server. Quindi, fare clic con il pulsante destro del mouse sull'istanza del servizio app in Esplora server e scegliere **Connetti debugger**.

1. Nell'applicazione ASP.NET in esecuzione fare clic sul collegamento alla pagina **About** .

    Il punto di interruzione verrà raggiunto in Visual Studio.

    Questo è tutto. Il resto dei passaggi descritti in questo argomento si applica al debug remoto in una macchina virtuale di Azure.

## <a name="remote-debug-aspnet-core-on-an-azure-vm"></a><a name="remote_debug_azure_vm"></a> ASP.NET Core di debug remoto in una macchina virtuale di Azure

È possibile creare una macchina virtuale di Azure per Windows Server, quindi installare e configurare IIS e gli altri componenti software necessari. Questa operazione richiede più tempo rispetto alla distribuzione in un servizio app Azure e richiede di seguire i passaggi rimanenti di questa esercitazione.

Queste procedure sono state testate in queste configurazioni del server:

* Windows Server 2012 R2 e IIS 8
* Windows Server 2016 e IIS 10
* Windows Server 2019 e IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>L'app è già in esecuzione in IIS nella macchina virtuale di Azure?

Questo articolo include i passaggi per configurare una configurazione di base di IIS in Windows Server e la distribuzione dell'app da Visual Studio. Questi passaggi sono inclusi per assicurarsi che nel server siano installati i componenti necessari, che l'app possa essere eseguita correttamente e che si sia pronti a eseguire il debug remoto.

* Se l'app è in esecuzione in IIS e si vuole solo scaricare il debugger remoto e avviare il debug, vedere [scaricare e installare Remote Tools in Windows Server](#BKMK_msvsmon).

* Per assicurarsi che l'applicazione sia configurata, distribuita ed eseguita correttamente in IIS in modo che sia possibile eseguire il debug, seguire tutti i passaggi descritti in questo argomento.

  * Prima di iniziare, seguire tutti i passaggi descritti in [installare ed eseguire IIS](/azure/virtual-machines/windows/quick-create-portal).

  * Quando si apre la porta 80 nel gruppo di sicurezza di rete, aprire anche la [porta corretta](#bkmk_openports) per il debugger remoto (4024 o 4022). In questo modo, non sarà necessario aprirlo in un secondo momento. Se si usa Distribuzione Web, aprire anche la porta 8172.

### <a name="update-browser-security-settings-on-windows-server"></a>Aggiornare le impostazioni di sicurezza del browser in Windows Server

Se in Internet Explorer è abilitata la configurazione della sicurezza avanzata (abilitata per impostazione predefinita), potrebbe essere necessario aggiungere alcuni domini come siti attendibili per consentire il download di alcuni componenti del server Web. Aggiungere i siti attendibili passando a **Opzioni Internet > sicurezza > siti attendibili > siti**. Aggiungere i seguenti domini.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Quando si Scarica il software, è possibile ottenere richieste per concedere l'autorizzazione per caricare varie risorse e script del sito Web. Alcune di queste risorse non sono necessarie, ma per semplificare il processo fare clic su **Aggiungi** quando richiesto.

### <a name="install-aspnet-core-on-windows-server"></a>Installare ASP.NET Core in Windows Server

1. Installare il bundle di hosting .NET Core nel sistema di hosting. L'aggregazione installa il runtime di .NET Core, la libreria di .NET Core e il modulo ASP.NET Core. Per istruzioni più dettagliate, vedere la pagina relativa [alla pubblicazione in IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    Per .NET Core 3, installare il [bundle di hosting .NET Core](https://dotnet.microsoft.com/permalink/dotnetcore-current-windows-runtime-bundle-installer).
    Per .NET Core 2, installare l' [hosting di .NET Core Windows Server](https://aka.ms/dotnetcore-2-windowshosting).

    > [!NOTE]
    > Se nel sistema non è presente una connessione a Internet, ottenere e installare *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* prima di installare l'aggregazione di Hosting di .NET Core Windows Server.

2. Riavviare il sistema o eseguire **net stop was /y** seguito da **net start w3svc** da un prompt dei comandi per visualizzare una modifica al percorso di sistema.

## <a name="choose-a-deployment-option"></a>Scegliere un'opzione di distribuzione

Se è necessario assistenza per la distribuzione dell'app in IIS, prendere in considerazione le opzioni seguenti:

* Eseguire la distribuzione creando un file di impostazioni di pubblicazione in IIS e importando le impostazioni in Visual Studio. In alcuni scenari, si tratta di un modo rapido per distribuire l'app. Quando si crea il file delle impostazioni di pubblicazione, le autorizzazioni vengono configurate automaticamente in IIS.

* Eseguire la distribuzione pubblicando in una cartella locale e copiando l'output in base a un metodo preferito in una cartella dell'app preparata in IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>Opzionale Eseguire la distribuzione usando un file di impostazioni di pubblicazione

È possibile usare questa opzione per creare un file di impostazioni di pubblicazione e importarlo in Visual Studio.

> [!NOTE]
> Questo metodo di distribuzione utilizza Distribuzione Web, che deve essere installato nel server. Se si desidera configurare Distribuzione Web manualmente anziché importare le impostazioni, è possibile installare Distribuzione Web 3,6 anziché Distribuzione Web 3,6 per i server di hosting. Tuttavia, se si configura Distribuzione Web manualmente, sarà necessario assicurarsi che una cartella dell'app nel server sia configurata con i valori e le autorizzazioni corretti (vedere [configurare il sito Web ASP.NET](#BKMK_deploy_asp_net)).

### <a name="configure-the-aspnet-core-web-site"></a>Configurare il sito Web di ASP.NET Core

1. In Gestione IIS fare clic su **pool di applicazioni** nel riquadro sinistro in **connessioni**. Aprire **DefaultAppPool** e impostare la **versione .NET CLR** su **nessun codice gestito**. Questa operazione è necessaria per ASP.NET Core. Il sito Web predefinito utilizza DefaultAppPool.

2. Arrestare e riavviare il DefaultAppPool.

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Installare e configurare Distribuzione Web per i server di hosting in Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Creare il file delle impostazioni di pubblicazione in IIS in Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importare le impostazioni di pubblicazione in Visual Studio e distribuire

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

> [!NOTE]
> Se si riavvia una macchina virtuale di Azure, l'indirizzo IP potrebbe cambiare.

Quando la distribuzione è completata, l'app viene avviata automaticamente. Se l'app non viene avviata da Visual Studio, avviare l'app in IIS per verificare che venga eseguita correttamente. Per ASP.NET Core, è anche necessario assicurarsi che il campo pool di applicazioni per **DefaultAppPool** sia impostato su **nessun codice gestito**.

1. Nella finestra di dialogo **Impostazioni** abilitare il debug facendo clic su **Avanti**, scegliere una configurazione di **debug** , quindi scegliere **Rimuovi file aggiuntivi nella destinazione** sotto le opzioni di **pubblicazione file** .

    > [!IMPORTANT]
    > Se si sceglie una configurazione di versione, si disabilita il debug nel file di *web.config* durante la pubblicazione.

1. Fare clic su **Save (Salva** ) e quindi pubblicare nuovamente l'app.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>Opzionale Eseguire la distribuzione tramite la pubblicazione in una cartella locale

È possibile usare questa opzione per distribuire l'app se si vuole copiare l'app in IIS usando PowerShell, RoboCopy o si desidera copiare manualmente i file.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a> Configurare il sito Web di ASP.NET Core nel computer Windows Server

Se si importano le impostazioni di pubblicazione, è possibile ignorare questa sezione.

1. Aprire **Gestione Internet Information Services (IIS)** e andare in **Siti**.

2. Fare clic con il pulsante destro del mouse sul nodo **Sito Web predefinito** e scegliere **Aggiungi applicazione**.

3. Impostare il campo **alias** su **MyASPApp** e il campo pool di applicazioni su **nessun codice gestito**. Impostare il **percorso fisico** su **C:\publish** (dove si distribuirà successivamente il progetto di ASP.NET Core).

4. Con il sito selezionato in Gestione IIS, scegliere **modifica autorizzazioni** e verificare che IUSR, IIS_IUSRS o l'utente configurato per il pool di applicazioni sia un utente autorizzato con lettura & Esegui diritti.

    Se non viene visualizzato uno di questi utenti con accesso, seguire la procedura per aggiungere IUSR come utente con i diritti di esecuzione di lettura &.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Opzionale Pubblicare e distribuire l'app pubblicando in una cartella locale da Visual Studio

Se non si usa Distribuzione Web, è necessario pubblicare e distribuire l'app usando il file system o altri strumenti. È possibile iniziare creando un pacchetto usando il file system, quindi distribuire il pacchetto manualmente o usare altri strumenti come PowerShell, Robocopy o XCopy. In questa sezione si presuppone che si stia copiando manualmente il pacchetto se non si usa Distribuzione Web.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a> Scaricare e installare Remote Tools in Windows Server

Scaricare la versione di Remote Tools corrispondente alla versione di Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a> Configurare il debugger remoto in Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se è necessario aggiungere autorizzazioni per utenti aggiuntivi, modificare la modalità di autenticazione o il numero di porta per il debugger remoto, vedere [configurare il debugger remoto](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a> Connettersi all'applicazione ASP.NET dal computer che esegue Visual Studio

1. Nel computer di Visual Studio aprire la soluzione di cui si sta provando a eseguire il debug (**MyASPApp** se si seguono i passaggi descritti in questo articolo).
2. In Visual Studio fare clic su **Debug > Connetti a processo** (CTRL + ALT + P).

    > [!TIP]
    > In Visual Studio 2017 e versioni successive, è possibile ricollegarsi allo stesso processo collegato in precedenza utilizzando **Debug > Riconnetti a processo...** (MAIUSC + ALT + P).

3. Impostare il campo qualificatore su **\<remote computer name>** e premere **invio**.

    Verificare che in Visual Studio venga aggiunta la porta richiesta al nome del computer, che viene visualizzato nel formato: **\<remote computer name> :p Ort**

    ::: moniker range=">=vs-2019"
    In Visual Studio 2019 dovrebbe essere visualizzato **\<remote computer name> : 4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017 dovrebbe essere visualizzato **\<remote computer name> : 4022**
    ::: moniker-end
    La porta è obbligatoria. Se il numero di porta non è visibile, aggiungerlo manualmente.

4. Fare clic su **Aggiorna**.
    Nella finestra **Processi disponibili** verranno visualizzati alcuni processi.

    Se non vengono visualizzati processi, provare a usare l'indirizzo IP anziché il nome del computer remoto (la porta è obbligatoria). È possibile usare `ipconfig` in una riga di comando per ottenere l'indirizzo IPv4.

    Se si vuole usare il pulsante **trova** , potrebbe essere necessario aprire la [porta UDP 3702](#bkmk_openports) sul server.

5. Selezionare  **Mostra i processi di tutti gli utenti**.

6. Digitare la prima lettera del nome del processo per trovare rapidamente l'app.

    * Se si usa il [modello di hosting in-process](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models) in IIS, selezionare il processo di **w3wp.exe** corretto. A partire da .NET Core 3, si tratta dell'impostazione predefinita.

    * In caso contrario, selezionare il processo **dotnet.exe** . Si tratta del modello di hosting out-of-process.

    Se sono presenti più processi che mostrano *w3wp.exe* o *dotnet.exe*, controllare la colonna **nome utente** . In alcuni scenari, nella colonna **nome utente** viene visualizzato il nome del pool di applicazioni, ad esempio **IIS APPPOOL\DefaultAppPool**. Se viene visualizzato il pool di app, ma non è univoco, creare un nuovo pool di app denominato per l'istanza dell'app di cui si vuole eseguire il debug, quindi è possibile trovarlo facilmente nella colonna **nome utente** .

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Scegliere **Connetti**.

8. Aprire il sito Web del computer remoto. In un browser passare a **http:// \<remote computer name>**.

    Verrà visualizzata la pagina Web ASP.NET.
9. Nell'applicazione ASP.NET in esecuzione fare clic sul collegamento alla pagina **About** .

    Il punto di interruzione verrà raggiunto in Visual Studio.

### <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> Risoluzione dei problemi Aprire le porte necessarie in Windows Server

Nella maggior parte delle configurazioni, le porte obbligatorie vengono aperte mediante l'installazione di ASP.NET e del debugger remoto. Tuttavia, per risolvere i problemi di distribuzione e l'app è ospitata dietro un firewall, potrebbe essere necessario verificare che le porte corrette siano aperte.

In una macchina virtuale di Azure è necessario aprire le porte tramite il [gruppo di sicurezza di rete](/azure/virtual-machines/windows/nsg-quickstart-portal).

Porte obbligatorie:

* 80-obbligatorio per IIS
::: moniker range=">=vs-2019"
* 4024: richiesto per il debug remoto da Visual Studio 2019. per ulteriori informazioni, vedere le [assegnazioni delle porte del debugger remoto](../debugger/remote-debugger-port-assignments.md) .
::: moniker-end
::: moniker range="vs-2017"
* 4022: richiesto per il debug remoto da Visual Studio 2017. per ulteriori informazioni, vedere le [assegnazioni delle porte del debugger remoto](../debugger/remote-debugger-port-assignments.md) .
::: moniker-end
* UDP 3702-(facoltativo) la porta di individuazione consente di **accedere** al pulsante trova quando ci si connette al debugger remoto in Visual Studio.

Inoltre, queste porte devono essere già aperte dall'installazione di ASP.NET:
- 8172-(facoltativo) necessario per Distribuzione Web distribuire l'app da Visual Studio
