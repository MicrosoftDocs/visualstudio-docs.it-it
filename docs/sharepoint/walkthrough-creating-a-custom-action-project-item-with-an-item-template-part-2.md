---
title: 'Procedura dettagliata: Creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 2 | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 264decc53d8ba2d818562a9513ecfa2aab6f882c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2"></a>Procedura dettagliata: creazione di un elemento di progetto Azione personalizzata con un modello di elemento, parte 2
  Dopo aver definito un tipo di elemento di progetto SharePoint personalizzato e associarlo a un modello di elemento in Visual Studio, è inoltre possibile fornire una procedura guidata per il modello. È possibile utilizzare la procedura guidata per raccogliere informazioni dagli utenti quando utilizzano il modello per aggiungere una nuova istanza dell'elemento di progetto a un progetto. Per inizializzare l'elemento del progetto, è possono utilizzare le informazioni raccolte.  
  
 In questa procedura dettagliata si aggiungerà una procedura guidata per l'elemento di progetto azione personalizzata che viene dimostrata in [procedura dettagliata: creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Quando un utente aggiunge un elemento di progetto azione personalizzata a un progetto SharePoint, la procedura guidata raccoglie informazioni sull'azione personalizzata (ad esempio la posizione e l'URL a cui passare quando un utente finale sceglie) e aggiunge queste informazioni per il file Elements.xml nel nuovo elemento di progetto.  
  
 In questa procedura dettagliata vengono descritte le attività seguenti:  
  
-   Creazione di una procedura guidata per un tipo di elemento di progetto SharePoint personalizzato associato a un modello di elemento.  
  
-   Definizione di una procedura guidata personalizzata dell'interfaccia utente simile a procedure guidate predefinite per gli elementi di progetto SharePoint in Visual Studio.  
  
-   Utilizzo dei parametri sostituibili per inizializzare i file di progetto SharePoint con i dati raccolti nella procedura guidata.  
  
-   Il debug e test della procedura guidata.  
  
> [!NOTE]  
>  È possibile scaricare un esempio che contiene i progetti completati, codice e altri file per questa procedura dettagliata dal seguente percorso: [file di progetto per le procedure dettagliate estensibilità di strumenti di SharePoint](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura dettagliata, è innanzitutto necessario creare la soluzione CustomActionProjectItem completando [procedura dettagliata: creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
 È necessario anche i componenti seguenti nel computer di sviluppo per completare questa procedura dettagliata:  
  
-   Le edizioni supportate di Windows, SharePoint e Visual Studio. Per ulteriori informazioni, vedere [requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio SDK. Questa procedura dettagliata Usa il **progetto VSIX** modello nel SDK per creare un pacchetto VSIX per distribuire l'elemento del progetto. Per ulteriori informazioni, vedere [estensione degli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Conoscere i concetti seguenti è utile, ma non obbligatorio, per completare la procedura dettagliata:  
  
-   Procedure guidate per i modelli di progetto e di elemento in Visual Studio. Per ulteriori informazioni, vedere [procedura: utilizzare procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md) e <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaccia.  
  
-   Azioni personalizzate in SharePoint. Per ulteriori informazioni, vedere [l'azione personalizzata](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
## <a name="creating-the-wizard-project"></a>Creazione del progetto della procedura guidata  
 Per completare questa procedura dettagliata, è necessario aggiungere un progetto alla soluzione CustomActionProjectItem creati in [procedura dettagliata: creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Verrà implementata la <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> l'interfaccia e definire l'interfaccia utente della procedura guidata in questo progetto.  
  
#### <a name="to-create-the-wizard-project"></a>Per creare il progetto della procedura guidata  
  
1.  In Visual Studio, aprire la soluzione CustomActionProjectItem  
  
2.  In **Esplora**, aprire il menu di scelta rapida per il nodo della soluzione, scegliere **Aggiungi**, quindi scegliere **nuovo progetto**.  
  
3.  Nel **nuovo progetto** finestra di dialogo espandere il **Visual c#** o **Visual Basic** nodi, quindi scegliere il **Windows** nodo.  
  
4.  Nella parte superiore del **nuovo progetto** finestra di dialogo, assicurarsi che **.NET Framework 4.5** viene scelto nell'elenco delle versioni di .NET Framework.  
  
5.  Scegliere il **libreria di controlli utente WPF** modello di progetto, denominare il progetto **ItemTemplateWizard**, quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **ItemTemplateWizard** progetto alla soluzione.  
  
6.  Eliminare l'elemento UserControl1 dal progetto.  
  
## <a name="configuring-the-wizard-project"></a>Configurazione di progetto della procedura guidata  
 Prima di creare la procedura guidata, è necessario aggiungere una finestra di Windows Presentation Foundation (WPF), un file di codice e riferimenti ad assembly al progetto.  
  
#### <a name="to-configure-the-wizard-project"></a>Per configurare il progetto della procedura guidata  
  
1.  In **Esplora**, aprire il menu di scelta rapida di **ItemTemplateWizard** nodo del progetto, quindi fare clic **proprietà**.  
  
2.  Nel **progettazione**, assicurarsi che il framework di destinazione sia impostato su .NET Framework 4.5.  
  
     Per i progetti Visual c#, è possibile impostare questo valore sul **applicazione** scheda. Per i progetti di Visual Basic, è possibile impostare questo valore sul **compilare** scheda. Per altre informazioni, vedere [Procedura: Destinare una versione di .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
3.  Nel **ItemTemplateWizard** del progetto, aggiungere un **finestra (WPF)** elemento al progetto e quindi assegnare un nome elemento **nome WizardWindow**.  
  
4.  Aggiungere due file di codice denominati CustomActionWizard e stringhe.  
  
5.  Aprire il menu di scelta rapida per il **ItemTemplateWizard** del progetto e quindi scegliere **Aggiungi riferimento**.  
  
6.  Nel **gestione riferimenti - ItemTemplateWizard** nella finestra di dialogo di **assembly** nodo, scegliere il **estensioni** nodo.  
  
7.  Selezionare le caselle di controllo accanto agli assembly seguenti e quindi scegliere il **OK** pulsante:  
  
    -   EnvDTE  
  
    -   11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
8.  In **Esplora**nella **riferimenti** cartella per il progetto ItemTemplateWizard, scegliere il **EnvDTE** riferimento.  
  
9. Nel **proprietà** finestra, modificare il valore della **incorpora tipi di interoperabilità** proprietà **False**.  
  
## <a name="defining-the-default-location-and-id-strings-for-custom-actions"></a>Definire le stringhe di ID e il percorso predefinito per le azioni personalizzate  
 Per ogni azione personalizzata è un percorso e un ID specificato nella `GroupID` e `Location` gli attributi del `CustomAction` elemento nel file Elements.xml. In questo passaggio si definiscono alcune stringhe valide per questi attributi nel progetto ItemTemplateWizard. Dopo aver completato questa procedura dettagliata, tali stringhe vengono scritte nel file Elements.xml nell'elemento di progetto azione personalizzata quando gli utenti di specificare un percorso e un ID nella procedura guidata.  
  
 Per semplicità, in questo esempio supporta solo un sottoinsieme di percorsi predefiniti disponibili e ID. Per un elenco completo, vedere [percorsi di azione personalizzati predefiniti e gli ID](http://go.microsoft.com/fwlink/?LinkId=181964).  
  
#### <a name="to-define-the-default-location-and-id-strings"></a>Per definire le stringhe di ID e il percorso predefinito  
  
1.  aprire.  
  
2.  Nel **ItemTemplateWizard** del progetto, sostituire il codice nel file di codice stringhe con il codice seguente.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]  
  
## <a name="creating-the-wizard-ui"></a>Creazione guidata dell'interfaccia utente  
 Aggiungere codice XAML per definire l'interfaccia utente della procedura guidata e aggiungere codice per associare alcuni controlli della procedura guidata per le stringhe di ID. La procedura guidata che crei assomiglia la procedura guidata predefinita per i progetti SharePoint in Visual Studio.  
  
#### <a name="to-create-the-wizard-ui"></a>Per creare l'interfaccia utente della procedura guidata  
  
1.  Nel **ItemTemplateWizard** del progetto, aprire il menu di scelta rapida per il **WizardWindow** file e quindi scegliere **aprire** per aprire la finestra nella finestra di progettazione.  
  
2.  Nella visualizzazione XAML, sostituire il codice XAML corrente con il seguente codice XAML. Il codice XAML definisce un'interfaccia utente che include un'intestazione, i controlli per specificare il comportamento dell'azione personalizzata e pulsanti di navigazione nella parte inferiore della finestra.  
  
    > [!NOTE]  
    >  Dopo aver aggiunto questo codice, il progetto avrà degli errori di compilazione. Questi errori non verranno più visualizzato quando si aggiunge il codice nei passaggi successivi.  
  
     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]  
  
    > [!NOTE]  
    >  La finestra che viene creata in questo codice XAML è derivata dalla <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> classe di base. Quando si aggiunge una finestra di dialogo WPF personalizzata a Visual Studio, è consigliabile derivare da questa classe di stile coerenza con altre finestre di dialogo in Visual Studio e per evitare problemi che potrebbero verificarsi con finestre di dialogo modale la finestra di dialogo. Per ulteriori informazioni, vedere [creazione e la gestione delle finestre di dialogo modale](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).  
  
3.  Se stai sviluppando un progetto Visual Basic, rimuovere il `ItemTemplateWizard` dello spazio dei nomi dal `WizardWindow` nel nome della classe di `x:Class` attributo del `Window` elemento. Questo elemento è nella prima riga del codice XAML. Al termine, la prima riga deve assomigliare al codice seguente:  
  
    ```  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  Nel file code-behind per il file WizardWindow, sostituire il codice corrente con il codice seguente.  
  
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]  
  
## <a name="implementing-the-wizard"></a>Implementazione della procedura guidata  
 Definire le funzionalità della procedura guidata implementando il <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaccia.  
  
#### <a name="to-implement-the-wizard"></a>Per implementare la procedura guidata  
  
1.  Nel **ItemTemplateWizard** progetto, aprire il **CustomActionWizard** file di codice e quindi sostituire il codice corrente in questo file con il codice seguente:  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]  
  
## <a name="checkpoint"></a>Checkpoint  
 A questo punto la procedura dettagliata, tutto il codice per la procedura guidata è ora nel progetto. Compilare il progetto per assicurarsi che l'operazione avvenga senza errori.  
  
#### <a name="to-build-your-project"></a>Per compilare il progetto  
  
1.  Nella barra dei menu scegliere **Compilazione**, **Compila soluzione**.  
  
## <a name="associating-the-wizard-with-the-item-template"></a>Associazione della procedura guidata con il modello di elemento  
 Dopo aver implementato la procedura guidata, è necessario associarlo con il **l'azione personalizzata** modello di elemento completando tre passaggi principali:  
  
1.  Firmare l'assembly della procedura guidata con un nome sicuro.  
  
2.  Ottenere la chiave pubblica token per l'assembly della procedura guidata.  
  
3.  Aggiungere un riferimento all'assembly della procedura guidata nel file. vstemplate per il **l'azione personalizzata** modello di elemento.  
  
#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Per firmare l'assembly della procedura guidata con un nome sicuro  
  
1.  In **Esplora**, aprire il menu di scelta rapida di **ItemTemplateWizard** nodo del progetto, quindi fare clic **proprietà**.  
  
2.  Nel **firma** , selezionare il **firmare l'assembly** casella di controllo.  
  
3.  Nel **Scegli un file chiave con nome sicuro** scegliere  **\<nuovo … >**.  
  
4.  Nel **Crea chiave con nome sicuro** finestra di dialogo immettere un nome, deselezionare il **Proteggi file di chiave con una password** casella di controllo e quindi scegliere il **OK** pulsante.  
  
5.  Nella barra dei menu scegliere **Compilazione**, **Compila soluzione**.  
  
#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Per ottenere la chiave pubblica token per l'assembly della procedura guidata  
  
1.  In una finestra del prompt dei comandi di Visual Studio, eseguire il seguente comando, sostituendo *PathToWizardAssembly* con il percorso completo per l'assembly compilato ItemTemplateWizard. dll per il progetto ItemTemplateWizard nello sviluppo computer.  
  
    ```  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     Il token di chiave pubblica per l'assembly ItemTemplateWizard. dll è scritta per la finestra del Prompt dei comandi di Visual Studio.  
  
2.  Mantenere aperta la finestra del Prompt dei comandi di Visual Studio. È necessario il token di chiave pubblica per completare la procedura successiva.  
  
#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Per aggiungere un riferimento all'assembly della procedura guidata nel file vstemplate  
  
1.  In **Esplora**, espandere il **ItemTemplate** nodo del progetto e quindi aprire il file ItemTemplate.  
  
2.  Verso la fine del file, aggiungere il seguente `WizardExtension` elemento tra le `</TemplateContent>` e `</VSTemplate>` tag. Sostituire il *YourToken* valore il `PublicKeyToken` attributo con il token di chiave pubblica ottenuto nella procedura precedente.  
  
    ```  
    <WizardExtension>  
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>  
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Per ulteriori informazioni sul `WizardExtension` elemento, vedere [WizardExtension (elemento) &#40;modelli di Visual Studio&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).  
  
3.  Salvare e chiudere il file.  
  
## <a name="adding-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>Aggiunta di parametri sostituibili nel file Elements.xml nel modello di elemento  
 Aggiungere diversi parametri sostituibili nel file Elements.xml nel progetto ItemTemplate. Questi parametri vengono inizializzati nel `PopulateReplacementDictionary` metodo la `CustomActionWizard` classe definita in precedenza. Quando un utente aggiunge un elemento di progetto azione personalizzata a un progetto, Visual Studio questi parametri nel file Elements.xml nel nuovo elemento di progetto vengono sostituiti automaticamente con i valori specificati nella procedura guidata.  
  
 Un parametro sostituibile è un token che inizia e termina con il segno di dollaro ($). Inoltre, per definire i propri parametri sostituibili, è possibile utilizzare i parametri predefiniti che definisce il sistema di progetto SharePoint e la inizializza. Per ulteriori informazioni, vedere [parametri sostituibili](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Per aggiungere parametri sostituibili nel file Elements.xml  
  
1.  Nel progetto ItemTemplate, sostituire il contenuto del file Elements.xml con il seguente codice XML.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="$IdValue$"  
                    GroupId="$GroupIdValue$"  
                    Location="$LocationValue$"  
                    Sequence="1000"  
                    Title="$TitleValue$"  
                    Description="$DescriptionValue$" >  
        <UrlAction Url="$UrlValue$"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     Il nuovo codice XML modifica i valori del `Id`, `GroupId`, `Location`, `Description`, e `Url` attributi a parametri sostituibili.  
  
2.  Salvare e chiudere il file.  
  
## <a name="adding-the-wizard-to-the-vsix-package"></a>Aggiunta della procedura guidata per il pacchetto VSIX  
 Nel file vsixmanifest nel progetto VSIX, aggiungere un riferimento a progetto della procedura guidata in modo che venga distribuito con il pacchetto VSIX che contiene l'elemento del progetto.  
  
#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Per aggiungere la procedura guidata per il pacchetto VSIX  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida di **vsixmanifest** file nel progetto CustomActionProjectItem e quindi scegliere **aprire** per aprire il file nell'editor del manifesto.  
  
2.  Nell'editor del manifesto, scegliere il **asset** tab, quindi scegliere il **New** pulsante.  
  
     Il **Aggiungi nuovo Asset** viene visualizzata la finestra di dialogo.  
  
3.  Nel **tipo** scegliere **Microsoft.VisualStudio.Assembly**.  
  
4.  Nel **origine** scegliere **un progetto nella soluzione corrente**.  
  
5.  Nel **progetto** scegliere **ItemTemplateWizard**, quindi scegliere il **OK** pulsante.  
  
6.  Nella barra dei menu, scegliere **compilare**, **Compila soluzione**, quindi assicurarsi che la soluzione venga compilata senza errori.  
  
## <a name="testing-the-wizard"></a>Test della procedura guidata  
 A questo punto si è pronti testare la procedura guidata. Innanzitutto, avviare il debug della soluzione CustomActionProjectItem nell'istanza sperimentale di Visual Studio. Testare quindi la procedura guidata per l'elemento di progetto azione personalizzata in un progetto di SharePoint nell'istanza sperimentale di Visual Studio. Infine, compilare ed eseguire il progetto di SharePoint per verificare che l'azione personalizzata funzioni come previsto.  
  
#### <a name="to-start-to-debug-the-solution"></a>Per avviare il debug della soluzione  
  
1.  Riavviare Visual Studio con credenziali amministrative e quindi aprire la soluzione CustomActionProjectItem.  
  
2.  Nel progetto ItemTemplateWizard, aprire il file di codice CustomActionWizard e quindi aggiungere un punto di interruzione sulla prima riga di codice il `RunStarted` metodo.  
  
3.  Nella barra dei menu, scegliere **Debug**, **eccezioni**.  
  
4.  Nel **eccezioni** finestra di dialogo, assicurarsi che il **generata** e **gestita dall'utente** caselle di controllo per **eccezioni Common Language Runtime**vengono cancellati e quindi scegliere il **OK** pulsante.  
  
5.  Avviare il debug premendo il tasto F5 oppure, nella barra dei menu, scegliendo **Debug**, **Avvia debug**.  
  
     Visual Studio installa l'estensione %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Item\1.0 di progetto di azione e viene avviata un'istanza sperimentale di Visual Studio. L'elemento del progetto verrà testato in questa istanza di Visual Studio.  
  
#### <a name="to-test-the-wizard-in-visual-studio"></a>Per testare la procedura guidata in Visual Studio  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **File**, **New**, **progetto**.  
  
2.  Espandere il **Visual c#** o **Visual Basic** nodo (a seconda del linguaggio che supporta il modello di elemento), espandere il **SharePoint** nodo, quindi scegliere il **2010** nodo.  
  
3.  Nell'elenco dei modelli di progetto, scegliere **progetto SharePoint 2010**, denominare il progetto **CustomActionWizardTest**, quindi scegliere il **OK** pulsante.  
  
4.  Nel **Personalizzazione guidata SharePoint**, immettere l'URL del sito che si desidera utilizzare per il debug e quindi scegliere il **fine** pulsante.  
  
5.  In **Esplora**, aprire il menu di scelta rapida per il nodo del progetto, scegliere **Aggiungi**, quindi scegliere **nuovo elemento**.  
  
6.  Nel **Aggiungi nuovo elemento - CustomItemWizardTest** finestra di dialogo espandere il **SharePoint** nodo, quindi espandere il **2010** nodo.  
  
7.  Nell'elenco di elementi del progetto, scegliere il **l'azione personalizzata** elemento e quindi scegliere il **Aggiungi** pulsante.  
  
8.  Verificare che il codice in altra istanza di Visual Studio si arresta nel punto di interruzione impostato precedentemente nel `RunStarted` metodo.  
  
9. Continuare il debug del progetto, premere F5 oppure sulla barra dei menu, scegliendo **Debug**, **continua**.  
  
     Verrà visualizzata la personalizzazione guidata SharePoint.  
  
10. In **percorso**, scegliere il **elenco modificare** pulsante di opzione.  
  
11. Nel **ID gruppo** scegliere **comunicazioni**.  
  
12. Nel **titolo** immettere **Centro per sviluppatori SharePoint**.  
  
13. Nel **descrizione** immettere **apre il sito Web di SharePoint Developer Center**.  
  
14. Nel **URL** , immettere **http://msdn.microsoft.com/sharepoint/default.aspx**, quindi scegliere il **fine** pulsante.  
  
     isual Studio aggiunge un elemento denominato **CustomAction1** al progetto e apre il file Elements.xml file nell'editor. Verificare che Elements.xml contiene i valori specificati nella procedura guidata.  
  
#### <a name="to-test-the-custom-action-in-sharepoint"></a>Per testare l'azione personalizzata in SharePoint  
  
1.  Nell'istanza sperimentale di Visual Studio, premere il tasto F5 oppure, nella barra dei menu, scegliere **Debug**, **Avvia debug**.  
  
     L'azione personalizzata viene incluso nel pacchetto e distribuita nel sito di SharePoint specificato per il **URL del sito** proprietà del progetto e il browser viene visualizzata la pagina predefinita del sito.  
  
    > [!NOTE]  
    >  Se il **debug degli Script disabilitato** viene visualizzata la finestra di dialogo, scegliere il **Sì** pulsante.  
  
2.  Nell'area di elenchi del sito di SharePoint, scegliere il **attività** collegamento.  
  
     Il **attività - tutte le attività** verrà visualizzata la pagina.  
  
3.  Nel **strumenti elenco** scheda della barra multifunzione, scegliere il **elenco** scheda, quindi il **impostazioni** gruppo, scegliere **le impostazioni dell'elenco**.  
  
     Il **le impostazioni dell'elenco** verrà visualizzata la pagina.  
  
4.  Sotto il **comunicazioni** intestazione nella parte superiore della pagina, scegliere il **Centro per sviluppatori SharePoint** collegare, verificare che il browser apre il sito Web http://msdn.microsoft.com/sharepoint/default.aspxe quindi chiudere il browser.  
  
## <a name="cleaning-up-the-development-computer"></a>Pulizia dei Computer di sviluppo  
 Dopo aver completato l'elemento del progetto di test, rimuovere il modello di elemento di progetto dall'istanza sperimentale di Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Per pulire il computer di sviluppo  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **strumenti**, **estensioni e aggiornamenti**.  
  
     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.  
  
2.  Nell'elenco di estensioni, scegliere il **elemento di progetto azione personalizzata** estensione, quindi scegliere il **Disinstalla** pulsante.  
  
3.  Nella finestra di dialogo visualizzata, scegliere il **Sì** pulsante per confermare che si desidera disinstallare l'estensione e quindi scegliere il **Riavvia ora** per completare la disinstallazione.  
  
4.  Chiudere entrambe le istanze di Visual Studio (l'istanza sperimentale e l'istanza di Visual Studio in cui la soluzione CustomActionProjectItem è aperta).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Definizione di tipi di elemento di progetto SharePoint personalizzato](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creazione di modelli di elementi e modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Riferimenti allo schema dei modelli di Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Procedura: utilizzare procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md)   
 [Gli ID e i percorsi predefiniti azione personalizzata](http://go.microsoft.com/fwlink/?LinkId=181964)  
  
  