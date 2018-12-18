---
title: 'Procedura dettagliata: Creazione di un programma di avvio automatico personalizzato per visualizzare l''informativa sulla Privacy dei messaggi di richiesta | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- dependencies [.NET Framework], custom bootstrapper package
- deploying applications [Visual Studio], custom prerequisites
- Windows Installer deployment, prerequisites
- prerequisites [.NET Framework], custom bootstrapper package
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 97b5ba379eb715c63e5432b22999e2c4f12bf50d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt"></a>Procedura dettagliata: creazione di un programma di avvio automatico per visualizzare un prompt di privacy
È possibile configurare le applicazioni ClickOnce per aggiornare automaticamente quando gli assembly con le versioni più recenti di file e le versioni di assembly disponibili. Per assicurarsi che i clienti di consenso per questo comportamento, è possibile visualizzare un prompt di privacy a essi. Quindi, è possibile scegliere se concedere l'autorizzazione per l'applicazione per aggiornare automaticamente. Se l'applicazione non è consentito l'aggiornamento automatico, non viene installato.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Visual Studio 2010.  
  
## <a name="creating-an-update-consent-dialog-box"></a>Creazione di una finestra di dialogo di consenso aggiornamento  
 Per visualizzare un prompt di privacy, creare un'applicazione che richiede il lettore per il consenso per gli aggiornamenti automatici per l'applicazione.  
  
#### <a name="to-create-a-consent-dialog-box"></a>Per creare una finestra di dialogo di consenso  
  
1.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
2.  Nel **nuovo progetto** la finestra di dialogo, fare clic su **Windows**, quindi fare clic su **WindowsFormsApplication**.  
  
3.  Per il **nome**, tipo **ConsentDialog**, quindi fare clic su **OK**.  
  
4.  Nella finestra di progettazione, fare clic sul form.  
  
5.  Nel **proprietà** finestra, modifica il **testo** proprietà **finestra di dialogo di consenso aggiornamento**.  
  
6.  Nel **della casella degli strumenti**, espandere **tutti i Windows Form**, trascinare un **etichetta** al form.  
  
7.  Nella finestra di progettazione, fare clic sul controllo label.  
  
8.  Nel **proprietà** finestra, modifica il **testo** proprietà in **aspetto** al seguente:  
  
     Controlla l'applicazione che si sta per installare gli aggiornamenti più recenti sul Web. Facendo clic su "Accetto", si autorizza l'applicazione per cercare e installare automaticamente gli aggiornamenti da Internet.  
  
9. Nel **della casella degli strumenti**, trascinare un **casella di controllo** controllo al centro della forma.  
  
10. Nel **proprietà** finestra, modifica il **testo** proprietà in **Layout** a **accetto**.  
  
11. Nel **della casella degli strumenti**, trascinare un **pulsante** controllo in basso a sinistra del modulo.  
  
12. Nel **proprietà** finestra, modifica il **testo** proprietà in **Layout** a **procedere**.  
  
13. Nel **proprietà** finestra, modifica il **(nome)** proprietà in **progettazione** a **ProceedButton**.  
  
14. Nel **della casella degli strumenti**, trascinare un **pulsante** controllo nella parte inferiore destra del form.  
  
15. Nel **proprietà** finestra, modifica il **testo** proprietà in **Layout** a **Annulla**.  
  
16. Nel **proprietà** finestra, modifica il **(nome)** proprietà in **progettazione** a **CancelButton**.  
  
17. Nella finestra di progettazione, fare doppio clic su di **accetto** casella di controllo per generare il gestore dell'evento CheckedChanged.  
  
18. Nel file di codice Form1, aggiungere il codice seguente per il gestore dell'evento CheckedChanged.  
  
     [!code-csharp[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]  
  
19. Aggiornare il costruttore della classe per disabilitare il **procedere** per impostazione predefinita.  
  
     [!code-csharp[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]  
  
20. Nel file di codice Form1, aggiungere il codice seguente per una variabile booleana rilevare se l'utente finale ha accettato le condizioni per gli aggiornamenti in linea.  
  
     [!code-csharp[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]  
  
21. Nella finestra di progettazione, fare doppio clic su di **procedere** pulsante per generare il gestore eventi Click.  
  
22. Nel file di codice Form1, aggiungere il codice seguente al gestore dell'evento Click per il **procedere** pulsante.  
  
     [!code-csharp[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]  
  
23. Nella finestra di progettazione, fare doppio clic su di **Annulla** pulsante per generare il gestore eventi Click.  
  
24. Nel file di codice Form1, aggiungere il codice seguente per il gestore eventi Click per il **Annulla** pulsante.  
  
     [!code-csharp[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]  
  
25. Aggiornare l'applicazione per restituire un errore se l'utente finale non consente gli aggiornamenti in linea.  
  
     Per solo gli sviluppatori di Visual Basic:  
  
    1.  In **Esplora**, fare clic su **ConsentDialog**.  
  
    2.  Nel **progetto** menu, fare clic su **Aggiungi modulo**, quindi fare clic su **Aggiungi**.  
  
    3.  Nel file di codice Module1. vb, aggiungere il codice seguente.  
  
         [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]  
  
    4.  Nel **progetto** menu, fare clic su **proprietà ConsentDialog**e quindi fare clic su di **applicazione** scheda.  
  
    5.  Deselezionare **Attiva framework applicazione**.  
  
    6.  Nel **oggetto di avvio** menu a discesa, seleziona **Module1**.  
  
        > [!NOTE]
        >  Disabilitando il framework applicazione disattiva le funzionalità, ad esempio gli stili di visualizzazione di Windows XP, gli eventi dell'applicazione, la schermata iniziale, un'applicazione a istanza singola e altro ancora. Per altre informazioni, vedere [Pagina Applicazione, Creazione progetti (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
     Per Visual c# solo per gli sviluppatori:  
  
     Aprire il file di codice Program.cs e aggiungere il codice seguente.  
  
     [!code-csharp[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]  
  
26. Nel **compilare** menu, fare clic su **Compila soluzione**.  
  
## <a name="creating-the-custom-bootstrapper-package"></a>Creazione del pacchetto del programma di avvio automatico personalizzato  
 Per visualizzare il prompt di privacy per gli utenti finali, è possibile creare un pacchetto del programma di avvio automatico personalizzato per l'applicazione della finestra di dialogo di consenso aggiornamento e includerlo come prerequisito in tutte le applicazioni ClickOnce.  
  
 Questa procedura viene illustrato come creare un pacchetto del programma di avvio automatico personalizzato creando i documenti seguenti:  
  
-   Un Product manifesto file per descrivere il contenuto del programma di avvio automatico.  
  
-   Un file manifesto package.xml per elencare gli aspetti specifici di localizzazione del pacchetto, ad esempio stringhe e le condizioni di licenza software.  
  
-   Un documento per le condizioni di licenza software.  
  
#### <a name="step-1-to-create-the-bootstrapper-directory"></a>Passaggio 1: Creare la directory del programma di avvio automatico  
  
1.  Creare una directory denominata **UpdateConsentDialog** in %PROGRAMFILES%\Microsoft Sdks\windows\v7.0A\Bootstrapper\Packages.  
  
    > [!NOTE]
    >  Privilegi di amministratore per creare la cartella potrebbe essere necessario.  
  
2.  Nella directory UpdateConsentDialog, creare una sottodirectory denominata en.  
  
    > [!NOTE]
    >  Creare una nuova directory per ciascuna lingua. Ad esempio, è possibile aggiungere le sottodirectory per le impostazioni locali fr e de. Queste directory conterrebbe il francese e tedesco stringhe e i language pack, se necessario.  
  
#### <a name="step-2-to-create-the-productxml-manifest-file"></a>Passaggio 2: Creare il file manifesto Product  
  
1.  Creare un file di testo denominato `product.xml`.  
  
2.  Nel file Product, aggiungere il codice XML seguente. Assicurarsi di non sovrascrivere il codice XML esistente.  
  
    ```  
    <Product  
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      ProductCode="Microsoft.Sample.EULA">  
      <!-- Defines the list of files to be copied on build. -->  
      <PackageFiles CopyAllPackageFiles="false">  
        <PackageFile Name="ConsentDialog.exe"/>  
      </PackageFiles>  
  
      <!-- Defines how to run the Setup package.-->  
      <Commands >  
        <Command PackageFile = "ConsentDialog.exe" Arguments=''>  
          <ExitCodes>  
            <ExitCode Value="0" Result="Success" />  
            <ExitCode Value="-1" Result="Fail" String="AU_Unaccepted" />  
            <DefaultExitCode Result="Fail"   
              FormatMessageFromSystem="true" String="GeneralFailure" />  
          </ExitCodes>  
        </Command>  
      </Commands>  
  
    </Product>  
    ```  
  
3.  Salvare il file nella directory del programma di avvio automatico UpdateConsentDialog.  
  
#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>Passaggio 3: Creare il manifesto package.xml file e il software di condizioni di licenza  
  
1.  Creare un file di testo denominato `package.xml`.  
  
2.  Nel file package.xml, aggiungere il codice XML seguente per definire le impostazioni locali e includere le condizioni di licenza software. Assicurarsi di non sovrascrivere il codice XML esistente.  
  
    ```  
    <Package   
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      Name="DisplayName"  
      Culture="Culture"  
      LicenseAgreement="eula.rtf">  
      <PackageFiles>  
        <PackageFile Name="eula.rtf"/>  
      </PackageFiles>  
  
      <!-- Defines a localizable string table for error messages. -->  
      <Strings>  
        <String Name="DisplayName">Update Consent Dialog</String>  
        <String Name="Culture">en</String>  
        <String Name="AU_Unaccepted">The automatic update agreement is not accepted.</String>  
        <String Name="GeneralFailure">A failure occurred attempting to launch the setup.</String>  
      </Strings>  
    </Package>  
    ```  
  
3.  Salvare il file nella sottodirectory en nella directory del programma di avvio automatico UpdateConsentDialog.  
  
4.  Creare un documento denominato eula.rtf per le condizioni di licenza software.  
  
    > [!NOTE]
    >  Le condizioni di licenza del software dovrebbero includere informazioni sulle licenze, le garanzie, passività e dalla legge locale. Questi file devono essere specifici delle impostazioni locali, quindi assicurarsi che il file viene salvato in un formato che supporta i caratteri MBCS o UNICODE. Consultare l'ufficio legale sul contenuto delle condizioni di licenza software.  
  
5.  Salvare il documento nella sottodirectory en nella directory del programma di avvio automatico UpdateConsentDialog.  
  
6.  Se necessario, creare un nuovo file manifesto di package e un nuovo documento eula.rtf per le condizioni di licenza software per ognuna delle impostazioni locali. Ad esempio, se si crea una sottodirectory per le impostazioni locali fr e de, creare i file manifesto separato package.xml e condizioni di licenza software e salvarli in sottodirectory fr e de.  
  
## <a name="setting-the-update-consent-application-as-a-prerequisite"></a>Impostazione dell'applicazione di consenso di aggiornamento come prerequisito  
 In Visual Studio, è possibile impostare l'applicazione di consenso all'aggiornamento come prerequisito.  
  
#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>Per impostare l'applicazione di consenso di aggiornamento come prerequisito  
  
1.  In **Esplora**, fare clic sul nome dell'applicazione che si desidera distribuire.  
  
2.  Nel **progetto** menu, fare clic su *ProjectName* **proprietà**.  
  
3.  Fare clic su di **pubblica** pagina e quindi fare clic su **prerequisiti**.  
  
4.  Selezionare **aggiornare finestra di dialogo di consenso**.  
  
    > [!NOTE]
    >  Potrebbe essere necessario chiudere e riaprire Visual Studio per visualizzare la finestra di dialogo di consenso aggiornamento nella finestra di dialogo Prerequisiti.  
  
5.  Fare clic su **OK**.  
  
## <a name="creating-and-testing-the-setup-program"></a>Creare e testare il programma di installazione  
 Dopo aver impostato l'applicazione di consenso all'aggiornamento come prerequisito, è possibile generare il programma di installazione e il programma di avvio automatico per l'applicazione.  
  
#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>Per creare e testare il programma di installazione, non fare clic su accetto  
  
1.  In **Esplora**, fare clic sul nome dell'applicazione che si desidera distribuire.  
  
2.  Nel **progetto** menu, fare clic su *ProjectName* **proprietà**.  
  
3.  Fare clic su di **pubblica** pagina e quindi fare clic su **pubblica**.  
  
4.  Se l'output di pubblicazione non viene aperto automaticamente, passare all'output di pubblicazione.  
  
5.  Eseguire il programma Setup.exe.  
  
     Il programma di installazione viene illustrato il contratto di licenza software Update finestra di dialogo di consenso.  
  
6.  Leggere il contratto di licenza software e quindi fare clic su **Accept**.  
  
     L'applicazione della finestra di dialogo di consenso aggiornamento verrà visualizzato il testo seguente: controlla l'applicazione che si sta per installare gli aggiornamenti più recenti sul Web. Facendo clic su accetto, si autorizza l'applicazione per cercare gli aggiornamenti automaticamente su Internet.  
  
7.  Chiudere l'applicazione o fare clic su Annulla.  
  
     L'applicazione viene visualizzato un errore: si è verificato un errore durante l'installazione dei componenti di sistema per *ApplicationName*. Impossibile continuare fino a quando non sono stati installati tutti i componenti di sistema.  
  
8.  Fare clic su Dettagli per visualizzare il seguente messaggio di errore: componente Update Consent Dialog non è riuscita per l'installazione con il seguente messaggio di errore: "il contratto di aggiornamento automatico non è accettato". Impossibile installare i componenti seguenti:-finestra di dialogo di consenso aggiornamento  
  
9. Fare clic su **Chiudi**.  
  
#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>Per creare e testare il programma di installazione, fare clic su accetto  
  
1.  In **Esplora**, fare clic sul nome dell'applicazione che si desidera distribuire.  
  
2.  Nel **progetto** menu, fare clic su *ProjectName* **proprietà**.  
  
3.  Fare clic su di **pubblica** pagina e quindi fare clic su **pubblica**.  
  
4.  Se l'output di pubblicazione non viene aperto automaticamente, passare all'output di pubblicazione.  
  
5.  Eseguire il programma Setup.exe.  
  
     Il programma di installazione viene illustrato il contratto di licenza software Update finestra di dialogo di consenso.  
  
6.  Leggere il contratto di licenza software e quindi fare clic su **Accept**.  
  
     L'applicazione della finestra di dialogo di consenso aggiornamento verrà visualizzato il testo seguente: controlla l'applicazione che si sta per installare gli aggiornamenti più recenti sul Web. Facendo clic su accetto, si autorizza l'applicazione per cercare gli aggiornamenti automaticamente su Internet.  
  
7.  Fare clic su **accetto**, quindi fare clic su **procedere**.  
  
     Avvio dell'applicazione per l'installazione.  
  
8.  Se viene visualizzata la finestra di dialogo Installazione dell'applicazione, fare clic su **installare**.  
  
## <a name="see-also"></a>Vedere anche  
 [Prerequisiti per la distribuzione dell'applicazione](../deployment/application-deployment-prerequisites.md)   
 [Creazione di pacchetti del programma di avvio](../deployment/creating-bootstrapper-packages.md)   
 [Procedura: creare un manifesto del prodotto](../deployment/how-to-create-a-product-manifest.md)   
 [Procedura: creare un manifesto di pacchetto](../deployment/how-to-create-a-package-manifest.md)   
 [Riferimenti dello schema di prodotti e package](../deployment/product-and-package-schema-reference.md)