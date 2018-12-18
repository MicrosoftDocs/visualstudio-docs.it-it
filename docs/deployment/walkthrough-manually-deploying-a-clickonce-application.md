---
title: "Procedura dettagliata: Distribuzione manuale di un'applicazione ClickOnce | Documenti Microsoft"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Mage.exe, manual ClickOnce deployments
- MageUI.exe, manual ClickOnce deployments
- deploying applications [ClickOnce], manual ClickOnce deployments
- ClickOnce deployment, manually
- ClickOnce deployment, SDK tools
- manual ClickOnce deployments
- manifests [ClickOnce]
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 71ab59e09f450d1656d77c551b3f44d0a60f1a57
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-manually-deploying-a-clickonce-application"></a>Procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce
Se non è possibile utilizzare Visual Studio per distribuire il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione oppure è necessario utilizzare funzionalità avanzate di distribuzione, ad esempio la distribuzione di applicazioni attendibili, è necessario utilizzare lo strumento da riga di comando Mage.exe per creare il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesti. Questa procedura dettagliata viene descritto come creare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione utilizzando la versione della riga di comando (Mage.exe) o la versione di grafica (MageUI.exe) dello strumento di modifica e la generazione del manifesto.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Questa procedura dettagliata presenta alcuni prerequisiti e le opzioni che è necessario scegliere prima di creare una distribuzione.  
  
-   Installare Mage.exe e MageUI.exe.  
  
     Mage.exe e MageUI.exe fanno parte di [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. È necessario disporre di [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] installato o la versione del [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] incluso in Visual Studio. Per ulteriori informazioni, vedere [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=158044) su MSDN.  
  
-   Fornire un'applicazione da distribuire.  
  
     Questa procedura dettagliata si presuppone che si è pronti per distribuire un'applicazione di Windows. Questa applicazione verrà considerata AppToDeploy.  
  
-   Determinare la modalità di distribuzione della distribuzione.  
  
     Le opzioni di distribuzione includono: Web, condivisione file o CD-ROM. Per altre informazioni, vedere [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).  
  
-   Determinare se l'applicazione richiede un livello di attendibilità elevato.  
  
     Se l'applicazione richiede l'attendibilità totale, ad esempio, accesso completo al sistema dell'utente, è possibile utilizzare il `-TrustLevel` opzione di Mage.exe per impostare questa proprietà. Se si desidera definire un set per l'applicazione, copiare la sezione autorizzazioni Internet o intranet dal manifesto di un altro, modificarlo in base alle esigenze e aggiungerlo al manifesto dell'applicazione utilizzando un editor di testo o MageUI.exe. Per altre informazioni, vedere [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
-   Ottenere un certificato Authenticode.  
  
     È necessario firmare la distribuzione con un certificato Authenticode. È possibile generare un certificato di prova utilizzando gli strumenti di Visual Studio, MageUI.exe, o MakeCert.exe e Pvk2Pfx.exe oppure è possibile ottenere un certificato da un'autorità di certificazione (CA). Se si sceglie di utilizzare la distribuzione di applicazioni attendibili, è inoltre necessario eseguire un'unica installazione del certificato in tutti i computer client. Per altre informazioni, vedere [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
    > [!NOTE]
    >  È anche possibile firmare la distribuzione con un certificato CNG che è possibile ottenere da un'autorità di certificazione.  
  
-   Assicurarsi che l'applicazione non dispone di un manifesto con informazioni di controllo dell'account utente.  
  
     È necessario determinare se l'applicazione contiene un manifesto con informazioni di controllo Account utente (UAC), ad esempio un `<dependentAssembly>` elemento. Per esaminare un manifesto dell'applicazione, è possibile utilizzare Windows Sysinternals [Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035) utilità.  
  
     Se l'applicazione contiene un manifesto con i dettagli dell'account, è necessario ricompilarla senza le informazioni di controllo dell'account utente. Per un progetto c# in Visual Studio, aprire le proprietà del progetto e selezionare la scheda applicazione. Nel **manifesto** elenco a discesa, seleziona **Crea applicazione senza manifesto**. Per un progetto di Visual Basic in Visual Studio, aprire le proprietà del progetto, selezionare la scheda applicazione e fare clic su **Visualizza impostazioni di controllo dell'account utente**. Nel file manifesto aperto, rimuovere tutti gli elementi all'interno del solo `<asmv1:assembly>` elemento.  
  
-   Determinare se l'applicazione richiede i prerequisiti nei computer client.  
  
     [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le applicazioni distribuite da Visual Studio possono includere un'installazione dei prerequisiti del programma di avvio (setup.exe) con la distribuzione. Questa procedura dettagliata crea due manifesti necessari per un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione. È possibile creare un programma di avvio automatico di prerequisiti usando il [GenerateBootstrapper (attività)](../msbuild/generatebootstrapper-task.md).  
  
### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>Per distribuire un'applicazione con lo strumento da riga di comando Mage.exe  
  
1.  Creare una directory in cui verranno archiviati i [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] file di distribuzione.  
  
2.  Nella directory di distribuzione che appena creata, creare una sottodirectory della versione. Se questa è la prima volta che si sta distribuendo l'applicazione, nome della sottodirectory versione **1.0.0.0**.  
  
    > [!NOTE]
    >  La versione della distribuzione può essere diverso da quello di versione dell'applicazione.  
  
3.  Copiare tutti i file dell'applicazione alla sottodirectory della versione, inclusi file eseguibili, assembly, risorse e i file di dati. Se necessario, è possibile creare ulteriori sottodirectory che contengono file aggiuntivi.  
  
4.  Aprire il [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] o un comando di Visual Studio prompt e passare alla sottodirectory della versione.  
  
5.  Creare il manifesto dell'applicazione con una chiamata di Mage.exe. L'istruzione seguente crea un manifesto dell'applicazione per il codice compilato per l'esecuzione sul processore Intel x86.  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    >  Assicurarsi di includere il punto (.) dopo il `-FromDirectory` opzione che indica la directory corrente. Se non si include il punto, è necessario specificare il percorso per i file dell'applicazione.  
  
6.  Firmare il manifesto dell'applicazione con il certificato Authenticode. Sostituire *mycert.pfx* con il percorso al file del certificato. Sostituire *passwd* con la password per il file del certificato.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
     Per firmare il manifesto dell'applicazione con un certificato CNG, usare il comando seguente. Sostituire *cngCert.pfx* con il percorso al file del certificato.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
7.  Passare alla radice della directory di distribuzione.  
  
8.  Generare il manifesto di distribuzione con una chiamata a Mage.exe. Per impostazione predefinita, Mage.exe contrassegnerà il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione come un'applicazione installata, in modo che non può essere eseguito sia online e offline. Per rendere l'applicazione disponibile solo quando l'utente è online, utilizzare il `-Install` opzione con un valore di `false`. Se si utilizza il valore predefinito, e gli utenti installeranno l'applicazione da un sito Web o una condivisione di file, assicurarsi che il valore di `-ProviderUrl` punti di opzione per il percorso dell'applicazione manifesto nel server Web o nella condivisione.  
  
    ```  
    mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
    ```  
  
9. Firmare il manifesto di distribuzione con il certificato Authenticode o CNG.  
  
    ```  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
     oppure  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
10. Copiare tutti i file nella directory di distribuzione di destinazione di distribuzione o del supporto. Potrebbe trattarsi di a una cartella su un sito Web o FTP del sito, una condivisione file o un CD-ROM.  
  
11. Fornire agli utenti con l'URL, un UNC o un supporto fisico, è necessario installare l'applicazione. Se si specifica un URL o un percorso UNC, è necessario assegnare agli utenti il percorso completo del manifesto di distribuzione. Ad esempio, se viene distribuito AppToDeploy http://webserver01/ nella directory AppToDeploy, il percorso URL completo dovrebbe essere http://webserver01/AppToDeploy/AppToDeploy.application.  
  
### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>Per distribuire un'applicazione con lo strumento con interfaccia grafica MageUI.exe  
  
1.  Creare una directory in cui verranno archiviati i [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] file di distribuzione.  
  
2.  Nella directory di distribuzione che appena creata, creare una sottodirectory della versione. Se questa è la prima volta che si sta distribuendo l'applicazione, nome della sottodirectory versione **1.0.0.0**.  
  
    > [!NOTE]
    >  La versione della distribuzione è probabilmente diverso da quello di versione dell'applicazione.  
  
3.  Copiare tutti i file dell'applicazione alla sottodirectory della versione, inclusi file eseguibili, assembly, risorse e i file di dati. Se necessario, è possibile creare ulteriori sottodirectory che contengono file aggiuntivi.  
  
4.  Avviare lo strumento con interfaccia grafico MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
5.  Creare un nuovo manifesto dell'applicazione selezionando **File**, **New**, **manifesto dell'applicazione** dal menu.  
  
6.  Predefinito **nome** , digitare il nome e numero di versione della distribuzione. Specificare anche il **processore** che la compilazione dell'applicazione, ad esempio x86.  
  
7.  Selezionare il **file** scheda e fare clic sui puntini di sospensione (**...** ) accanto al pulsante il **directory dell'applicazione** casella di testo. Verrà visualizzata una finestra di dialogo Sfoglia per cartelle.  
  
8.  Selezionare la sottodirectory della versione che contiene i file dell'applicazione e quindi fare clic su **OK**.  
  
9. Se si intende distribuire da Internet Information Services (IIS), selezionare il **quando la popolazione Aggiungi l'estensione. deploy a qualsiasi file che non hanno** casella di controllo.  
  
10. Fare clic su di **Popola** pulsante per aggiungere tutti i file dell'applicazione per l'elenco dei file. Se l'applicazione contiene più di un file eseguibile, contrassegnare il file eseguibile principale per la distribuzione dell'applicazione di avvio selezionando **punto di ingresso** dal **tipo di File** elenco a discesa. (Se l'applicazione contiene un solo file eseguibile, MageUI.exe verrà contrassegnarla per l'utente.)  
  
11. Selezionare il **delle autorizzazioni necessarie** e selezionare il livello di attendibilità che è necessario che l'applicazione per l'asserzione. Il valore predefinito è **FullTrust**, che può essere adatto per la maggior parte delle applicazioni.  
  
12. Selezionare **File**, **Salva con nome** dal menu. La finestra di dialogo Opzioni di firma viene visualizzata la richiesta di firmare il manifesto dell'applicazione.  
  
13. Se si dispone di un certificato archiviato come file nel file system, utilizzare il **firma con file di certificato** opzione e selezionare il certificato dal file system con i puntini di sospensione (**...** ) pulsante. Quindi digitare la password del certificato.  
  
     oppure  
  
     Se il certificato si trova in un archivio certificati accessibile dal computer, selezionare il **firma con certificato archiviato** opzione e selezionare il certificato dall'elenco fornito.  
  
14. Fare clic su **OK** per firmare il manifesto dell'applicazione. Verrà visualizzata la finestra di dialogo Salva con nome.  
  
15. Nella finestra di dialogo Salva con nome, specificare la directory della versione e quindi fare clic su **salvare**.  
  
16. Selezionare **File**, **New**, **manifesto della distribuzione** dal menu per creare il manifesto di distribuzione.  
  
17. Nel **nome** , specificare un nome e numero di versione per questa distribuzione (**1.0.0.0** in questo esempio). Specificare anche il **processore** che la compilazione dell'applicazione, ad esempio x86.  
  
18. Selezionare il **descrizione** scheda e specificare valori per **Publisher** e **prodotto * * * t**. (**Prodotto** è il nome assegnato all'applicazione nel menu Start di Windows quando l'applicazione viene installata in un computer client per l'utilizzo offline.)  
  
19. Selezionare il **opzioni di distribuzione** scheda e il **percorso iniziale** testo, specificare il percorso del manifesto dell'applicazione nel server Web o nella condivisione. Ad esempio, \\\myServer\myShare\AppToDeploy.application.  
  
20. Se l'estensione. deploy aggiunto nel passaggio precedente, selezionare anche **utilizzare estensione. deploy** qui.  
  
21. Selezionare il **opzioni aggiornamento** scheda e specificare la frequenza con cui si desidera che l'applicazione per l'aggiornamento. Se l'applicazione usa <xref:System.Deployment.Application.UpdateCheckInfo> per il controllo automatico degli aggiornamenti, deselezionare il **l'applicazione deve controllare disponibilità di aggiornamenti** casella di controllo.  
  
22. Selezionare il **riferimento all'applicazione** scheda e quindi fare clic su di **Seleziona manifesto** pulsante. Verrà visualizzata la finestra di dialogo Apri.  
  
23. Selezionare il manifesto dell'applicazione creata in precedenza e quindi fare clic su **aprire**.  
  
24. Selezionare **File**, **Salva con nome** dal menu. La finestra di dialogo Opzioni di firma viene visualizzata la richiesta di firmare il manifesto di distribuzione.  
  
25. Se si dispone di un certificato archiviato come file nel file system, utilizzare il **firma con file di certificato** opzione e selezionare il certificato dal file system con i puntini di sospensione (**...** ) pulsante. Quindi digitare la password del certificato.  
  
     oppure  
  
     Se il certificato si trova in un archivio certificati accessibile dal computer, selezionare il **firma con certificato archiviato** opzione e selezionare il certificato dall'elenco fornito.  
  
26. Fare clic su **OK** per firmare il manifesto della distribuzione. Verrà visualizzata la finestra di dialogo Salva con nome.  
  
27. Nel **Salva con nome** nella finestra di dialogo Sposta su una directory alla radice della distribuzione e quindi fare clic su **salvare**.  
  
28. Copiare tutti i file nella directory di distribuzione di destinazione di distribuzione o del supporto. Potrebbe trattarsi di a una cartella su un sito Web o FTP del sito, una condivisione file o un CD-ROM.  
  
29. Fornire agli utenti con l'URL, un UNC o un supporto fisico, è necessario installare l'applicazione. Se si specifica un URL o un percorso UNC, è necessario assegnare agli utenti il percorso completo, il manifesto di distribuzione. Ad esempio, se viene distribuito AppToDeploy http://webserver01/ nella directory AppToDeploy, il percorso URL completo dovrebbe essere http://webserver01/AppToDeploy/AppToDeploy.application.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Quando è necessario distribuire una nuova versione dell'applicazione, creare una nuova directory denominata in base alla nuova versione, ad esempio, 1.0.0.1 copiare i nuovi file di applicazione nella nuova directory. Successivamente, è necessario seguire i passaggi precedenti per creare e firmare manifesti di applicazione, aggiornare e firmare il manifesto della distribuzione. Assicurati di specificare la stessa versione superiore in entrambi i Mage.exe `-New` e `-Update` chiamate, come [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Aggiorna solo le versioni successive, con il valore integer più a sinistra più significativo. Se si utilizza MageUI.exe, è possibile aggiornare il manifesto di distribuzione aprendo il file, selezionando il **riferimento all'applicazione** scheda, fare clic su di **Seleziona manifesto** pulsante e quindi selezionando l'aggiornamento manifesto dell'applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (Manifest Generation and Editing Tool, client grafico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)