---
title: Abilitare il debug per le applicazioni ASP.NET | Documenti Microsoft
ms.custom: H1HackMay2017
ms.date: 09/21/17
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 3418e1d2e05d687f8cb73a7857178ae1060d56f8
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="debug-aspnet-applications-in-visual-studio"></a>Debug di applicazioni ASP.NET in Visual Studio

È possibile eseguire il debug di applicazioni ASP.NET da Visual Studio.

## <a name="requirements"></a>Requisiti

Per seguire le istruzioni in questo argomento, è necessario:

- IIS Express, incluso per impostazione predefinita in Visual Studio 2012 e versioni successive

    oppure

- Una variabile locale IIS web server (versione 8.0 o versioni successive) che è configurato correttamente ed eseguire l'applicazione ASP.NET senza errori.

Se il server è remoto, il debugger remoto deve essere in esecuzione nel computer remoto. Per eseguire il debug in un server IIS remoto, vedere [ASP.NET di eseguire il Debug remoto in un Computer IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). 

## <a name="configure-debug-settings"></a>Configurare le impostazioni di debug

### <a name="enable-aspnet-debugging-in-the-project-properties"></a>Abilitare il debug di ASP.NET nelle proprietà del progetto

1. Aprire il progetto ASP.NET in Visual Studio.

2. Fare clic sul progetto in **Esplora**, scegliere **proprietà**, quindi fare clic sul **Web** scheda.

    Per alcuni tipi di progetto, selezionare **proprietà > Debug** invece. Per un progetto di Web Form ASP.NET, fare clic sul progetto e selezionare **pagine delle proprietà > Opzioni di avvio**.
  
3.  In **Debugger**selezionare la casella di controllo **ASP.NET** .

    ![Impostazioni correlate al debugger](../debugger/media/dbg-aspnet-enable-debugging.png "impostazioni correlate al Debugger")

> [!NOTE]
> Se si crea un nuovo progetto ASP.NET (**File > Nuovo progetto**), le impostazioni di debug sono già configurate correttamente.

### <a name="enable-debugging-in-the-webconfig-file"></a>Abilitare il debug nel file Web. config  

Per eseguire il debug di un'app web, è necessario configurare correttamente il file Web. config dell'applicazione. Se si ospita l'applicazione in IIS o IIS Express, è necessario un file Web. config.

Per ASP.NET Core, il file Web. config viene creato automaticamente quando l'applicazione viene distribuita (se non è già presente).

> [!TIP]
> Il processo di distribuzione può aggiornare le impostazioni di Web. config. Pertanto, prima di tentare di eseguire il debug, verificare l'impostazione di Web. config nel server.
  
1.  In Visual Studio, aprire il file Web. config del progetto.  
  
    > [!NOTE]  
    > È Impossibile accedere al file di Web. config in modalità remota tramite un Web browser. Per motivi di sicurezza [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] configura Microsoft IIS per impedire l'accesso diretto del browser ai file Web. config. Se si tenta di accedere a un file di configurazione utilizzando un browser, è visualizzato un errore di accesso HTTP 403 (accesso negato).  
  
2.  Individuare l'elemento `configuration/system.web/compilation` . Se l'elemento di compilazione non esiste, è necessario crearlo.

    Web.config è un file XML e di conseguenza contiene sezioni annidate contrassegnate da tag.
  
3.  Se l'elemento `compilation` non contiene un attributo `debug` , aggiungere l'attributo all'elemento.  
  
4.  Verificare che il valore dell'attributo `debug` sia impostato su `true`.  
  
Il file Web. config dovrebbe essere analogo al seguente:

> [!NOTE]
> In questo esempio è un file Web. config parziale. Le sezioni aggiuntive XML sono in genere presenti tra la configurazione e gli elementi di System. Web. L'elemento di compilazione potrebbe contenere anche altri attributi ed elementi.
  
#### <a name="example"></a>Esempio  
  
```  
<configuration>  
    ...  
    <system.web>  
        <compilation  
            debug="true"  
            ...  
        >  
        ...  
        </compilation>  
    </system.web>  
</configuration>  
```

Se si utilizza un server esterno anziché il server predefinito di IIS Express, è necessario anche assicurarsi che il `targetFramework` valore dell'attributo corrisponde alla configurazione sul server.

> [!IMPORTANT]
> Per prestazioni ottimali, impostare un'app di produzione `debug=false` e specificare una build di rilascio quando si compila e pubblicare l'app.

## <a name="configure-project-settings-for-the-server"></a>Configurare le impostazioni di progetto per il server

Per il debug su un server web locale, impostare le proprietà del progetto. Per il debug in un server remoto, seguire le istruzioni più complete descritto in [ASP.NET di debug remoto in IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) invece.

1. Nel **Web** scheda del progetto selezionare proprietà, **IIS Express** o **Server esterno** sotto il **Server** impostazioni. (Per alcuni tipi di progetto, queste impostazioni vengono visualizzati sotto il **Debug** scheda invece.)

    ![Le impostazioni del server](../debugger/media/dbg-aspnet-server-settings.png "le impostazioni del Server")

    IIS Express è il server predefinito per ASP.NET e in genere non richiede alcuna configurazione speciale. Questo è il modo più semplice per eseguire il debug di un'applicazione ASP.NET.

    Per un progetto di Web Form ASP.NET, fare clic sul progetto, scegliere **pagine delle proprietà > Opzioni di avvio**e selezionare **Usa server Web predefinito** o **Usa server personalizzato** ( invece di **Server esterno**).

    ![Impostazioni del server per app di Web Form](../debugger/media/dbg-aspnet-server-settings-webforms.png "impostazioni del Server per app di Web Form")

2. Se si sceglie un server esterno (personalizzato), immettere l'URL corretto nel **URL progetto** (o **URL di Base**) campo.

    Se il server esterno IIS locale, IIS deve essere installato e configurato correttamente. Ad esempio, la versione corretta di ASP.NET deve essere configurata in IIS. Per ulteriori informazioni, vedere [IIS 8.0 usando ASP.NET 3.5 e ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45). Se si desidera testare la distribuzione, nonché il debug, vedere [distribuzione per eseguire il test](/aspnet/web-forms/overview/deployment/visual-studio-web-deployment/deploying-to-iis).

    Se il server esterno [remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md), connettersi al processo invece e queste impostazioni di progetto non vengono utilizzate per il debug.

## <a name="local-iis-web-server-configure-iis"></a>(Server web IIS locale) Configurazione di IIS

Per IIS Express, non è necessario configurare il server web (ignorare questa sezione). IIS Express è consigliato per il test iniziale.

Se si utilizza il server web IIS locale, seguire questi passaggi.

1. Assicurarsi che IIS sia installato correttamente. Per ulteriori informazioni, vedere [IIS 8.0 usando ASP.NET 3.5 e ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    * Assicurarsi di installare la versione corretta di ASP.NET sul server. Utilizzare l'installazione guidata piattaforma Web (WebPI) per installare ASP.NET 4.5 (scegliere il nodo del Server in Windows Server 2012 R2, **ottenere nuovi componenti della piattaforma Web** e quindi cercare ASP.NET). Per installare ASP.NET Core, vedere [la pubblicazione in IIS](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration).

    > [!NOTE]
    > Se si utilizza Windows Server 2008 R2, installare ASP.NET 4 invece con il seguente comando:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Aprire il **Gestione Internet Information Services (IIS)**. (Nel riquadro sinistro di Server Manager, selezionare **IIS**. Il server e scegliere **Gestione Internet Information Services (IIS)**.)

3. In **connessioni** nel riquadro a sinistra, passare a **siti**.

4. Fare clic con il pulsante destro del mouse sul nodo **Sito Web predefinito** e scegliere **Aggiungi applicazione**.

5. Impostare il **Alias** campo **MyASPApp**, accettare il valore predefinito di Pool di applicazioni (**DefaultAppPool**) e impostare il **percorso fisico** a  **C:\inetpub\myNewFolder** (creare una nuova cartella per l'app).

6. In **connessioni**selezionare **pool di applicazioni**. Aprire **DefaultAppPool** e impostare il campo pool di applicazioni per il valore corretto per l'applicazione (utilizzare ASP.NET 4 per ASP.NET 4.5. Utilizzare **nessun codice gestito** per ASP.NET di base).

## <a name="local-iis-web-server-deploy-the-app"></a>(Server web IIS locale) Distribuire l'app

Per IIS Express, l'app web viene distribuito automaticamente quando si avvia il debug (ignorare questa sezione).

Se si utilizza il server web IIS locale, seguire questi passaggi. Esistono diversi modi per pubblicare l'applicazione in IIS. Nei passaggi seguenti è illustrato come creare e utilizzare un profilo di pubblicazione in modo che è possibile distribuire con il file system.

1. Riavviare Visual Studio come amministratore.

    Per distribuire utilizzando questo metodo, sono necessari privilegi di amministratore.

2. In Visual Studio, fare clic sul progetto e scegliere **pubblica** (per Web Form, utilizzare **pubblicare App Web**).

3. Scegliere **IIS, FTP, e così via** e fare clic su **pubblica**.

    ![La pubblicazione in IIS](../debugger/media/dbg-aspnet-local-iis.png "la pubblicazione in IIS")

    Per un'app Web Form, scegliere **personalizzato** nella finestra di dialogo pubblica, immettere un nome di profilo e scegliere **OK**.

4. Nel **metodo di pubblicazione** selezionare **File system**.

5. Per il **percorso di destinazione**, fare clic su di **Sfoglia** pulsante.

6. (ASP.NET Core) Scegliere **File System** e selezionare la cartella in cui creato in precedenza per l'app.

6. (ASP.NET) Scegliere **IIS locale**e selezionare il sito web creato in precedenza e quindi fare clic su **aprire**.

    ![La pubblicazione in IIS](../debugger/media/dbg-aspnet-local-iis-select-site.png "la pubblicazione in IIS")

    > [!TIP]
    > Se viene visualizzato un messaggio che indica il server web che non è configurato correttamente, assicurarsi che sia installata la versione corretta di ASP.NET per IIS.

7. Fare clic su **Avanti** e scegliere un **Debug** configurazione.

    > [!NOTE]
    > Se si distribuisce con una configurazione di rilascio, imposta `debug=false` nel file Web. config del server.

8. Fare clic su **salvare** per salvare le impostazioni di pubblicazione e quindi fare clic su **pubblica**.

    > [!CAUTION]
    >  Se è necessario apportare modifiche al codice o di ricompilazione, è necessario ripubblicare e ripetere questo passaggio. Il file eseguibile copiato nel computer remoto deve corrispondere esattamente all'origine locale e ai simboli.

## <a name="set-a-breakpoint-and-start-debugging"></a>Impostare un punto di interruzione e avviare il debug

1. Nel progetto in Visual Studio, verrà eseguito un punto di interruzione nel codice che si è certi di set.

2. Per avviare il debug, premere **F5** (**Debug > Avvia debug**).

3. Eseguire azioni per eseguire il codice che contiene il punto di interruzione.

    Le pause di debugger in cui è stato impostato il punto di interruzione.

### <a name="local-iis-troubleshooting-cannot-hit-the-breakpoint"></a>(IIS) locali Risoluzione dei problemi: Non è il punto di interruzione

1. Avviare l'app web da IIS e verificare che venga eseguito correttamente. Lasciare l'app web in esecuzione.

2. Da Visual Studio, selezionare **Debug > Connetti a processo** e connettersi al processo ASP.NET (in genere **w3wp.exe** o **dotnet.exe**). Per ulteriori informazioni, vedere [Connetti a processo](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

    Se si è in grado di connettersi utilizzando **Connetti a processo** e possono raggiungere un punto di interruzione, ma non è possibile avviare il debug tramite **F5**, è probabile che un'impostazione non è corretta nelle proprietà del progetto. Se si utilizza un file host, verificare che sia configurato correttamente.

  
## <a name="robust-programming"></a>Programmazione efficiente  
[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] automaticamente rileva modifiche al file Web. config e applica le nuove impostazioni di configurazione. Non è necessario riavviare il computer o il server IIS server perché le modifiche abbiano effetto.  
  
Un sito Web può contenere più directory e sottodirectory virtuali, ognuna delle quali può includere file Web.config. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] le applicazioni ereditano le impostazioni dai file Web. config a livelli superiori nel percorso URL. File di configurazione gerarchici permettono di modificare le impostazioni per diverse [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] applicazioni nello stesso momento, ad esempio per tutte le applicazioni sottostanti nella gerarchia. Tuttavia, se `debug` è impostato in un file di livello inferiore nella gerarchia, viene eseguito l'override di valore più alto.  
  
Ad esempio, è possibile specificare `debug="true"` in www.microsoft.com/aaa/Web.config, qualsiasi applicazione presente nella cartella aaa e in qualsiasi sottocartella di aaa eredita tale impostazione. Pertanto, se il [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] applicazione www.microsoft.com/aaa/bbb, eredita tale impostazione, così come qualsiasi [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] applicazioni in www.microsoft.com/aaa/ccc, www.microsoft.com/aaa/ddd e così via. L'unica eccezione si verifica se una di queste applicazioni esegue l'ovveride dell'impostazione per mezzo del proprio file Web.config di livello inferiore.  
  
> [!IMPORTANT]
> Abilitazione della modalità di debug notevolmente le prestazioni dei [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dell'applicazione. Ricordare di disabilitare la modalità di debug prima di distribuire un'applicazione commerciale o di condurre misurazioni delle prestazioni.  
  
## <a name="see-also"></a>Vedere anche  
[Debug di ASP.NET: requisiti di sistema](aspnet-debugging-system-requirements.md)   
[Procedura: eseguire il processo di lavoro con un account utente](how-to-run-the-worker-process-under-a-user-account.md)   
[Procedura: trovare il nome del processo ASP.NET](how-to-find-the-name-of-the-aspnet-process.md)   
[Eseguire il debug di applicazioni Web distribuite](debugging-deployed-web-applications.md)   
[Procedura dettagliata: Debug di un Web Form](walkthrough-debugging-a-web-form.md)   
[Procedura: Debug di eccezioni ASP.NET](how-to-debug-aspnet-exceptions.md)   
[Eseguire il debug di applicazioni Web: errori e risoluzione dei problemi](debugging-web-applications-errors-and-troubleshooting.md)
  