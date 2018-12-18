---
title: 'Procedura dettagliata: Creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 2 | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f0472688f9f36d2b14c89cc904bf6ce4badd6ca6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2"></a>Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 2
  Dopo aver definito un tipo di elemento di progetto SharePoint personalizzato e associarlo a un modello di progetto in Visual Studio, è inoltre possibile fornire una procedura guidata per il modello. È possibile utilizzare la procedura guidata per raccogliere informazioni dagli utenti quando utilizzano il modello per creare un nuovo progetto che contiene l'elemento del progetto. Per inizializzare l'elemento del progetto, è possono utilizzare le informazioni raccolte.  
  
 In questa procedura dettagliata si aggiungerà una procedura guidata per il modello di progetto colonna del sito che viene dimostrato in [procedura dettagliata: creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md). Quando un utente crea un progetto di colonna del sito, la procedura guidata raccoglie informazioni sulla colonna del sito (ad esempio il tipo di base e gruppo) e aggiunge al file Elements.xml nel nuovo progetto.  
  
 In questa procedura dettagliata vengono descritte le attività seguenti:  
  
-   Creazione di una procedura guidata per un tipo di elemento di progetto SharePoint personalizzato associato a un modello di progetto.  
  
-   Definizione di una procedura guidata personalizzata dell'interfaccia utente simile le procedure guidate incorporate per i progetti SharePoint in Visual Studio.  
  
-   Creazione di due *i comandi di SharePoint* che vengono utilizzati per effettuare chiamate nel sito di SharePoint locale, mentre è in esecuzione la procedura guidata. Comandi di SharePoint sono metodi che possono essere utilizzati dalle estensioni di Visual Studio per chiamare le API nel modello a oggetti server SharePoint. Per ulteriori informazioni, vedere [chiamate ai modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Utilizzo dei parametri sostituibili per inizializzare i file di progetto SharePoint con i dati raccolti nella procedura guidata.  
  
-   Creazione di un nuovo file con estensione snk in ogni nuova istanza di progetto colonna del sito. Questo file viene utilizzato per firmare il progetto in modo che l'assembly della soluzione SharePoint può essere distribuito nella global assembly cache di output.  
  
-   Il debug e test della procedura guidata.  
  
> [!NOTE]  
>  È possibile scaricare un esempio che contiene i progetti completati, codice e altri file per questa procedura dettagliata dal seguente percorso: [http://go.microsoft.com/fwlink/?LinkId=191369](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura dettagliata, è innanzitutto necessario creare la soluzione SiteColumnProjectItem completando [procedura dettagliata: creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  
  
 È necessario anche i componenti seguenti nel computer di sviluppo per completare questa procedura dettagliata:  
  
-   Le edizioni supportate di Windows, SharePoint e Visual Studio. Per ulteriori informazioni, vedere [requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio SDK. Questa procedura dettagliata Usa il **progetto VSIX** modello nel SDK per creare un pacchetto VSIX per distribuire l'elemento del progetto. Per ulteriori informazioni, vedere [estensione degli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Conoscere i concetti seguenti è utile, ma non obbligatorio, per completare la procedura dettagliata:  
  
-   Procedure guidate per i modelli di progetto e di elemento in Visual Studio. Per ulteriori informazioni, vedere [procedura: utilizzare procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md) e <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaccia.  
  
-   Colonne del sito di SharePoint. Per ulteriori informazioni, vedere [colonne](http://go.microsoft.com/fwlink/?LinkId=183547).  
  
##  <a name="wizardcomponents"></a>Informazioni sui componenti della procedura guidata  
 La procedura guidata illustrata in questa procedura dettagliata contiene diversi componenti. Nella tabella seguente vengono descritti questi componenti.  
  
|Componente|Descrizione|  
|---------------|-----------------|  
|Implementazione della procedura guidata|Si tratta di una classe, denominata `SiteColumnProjectWizard`, che implementa il <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaccia. Questa interfaccia definisce i metodi chiamati da Visual Studio quando inizia e termina e in determinati momenti durante la procedura guidata viene eseguita la procedura guidata.|  
|Creazione guidata dell'interfaccia utente|Si tratta di una finestra di WPF, denominata `WizardWindow`. Questa finestra include due controlli utente, denominati `Page1` e `Page2`. Questi controlli utente rappresentano le due pagine della procedura guidata.<br /><br /> In questa procedura dettagliata, il <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> metodo di implementazione della procedura guidata consente di visualizzare l'interfaccia utente della procedura guidata.|  
|Modello di data di creazione guidata|Questa è una classe intermedia, denominata `SiteColumnWizardModel`, che fornisce un livello tra l'interfaccia utente della procedura guidata e l'implementazione della procedura guidata. In questo esempio utilizza questa classe per consentire la separazione dell'implementazione e la relativa interfaccia utente tra loro; Questa classe non è un componente necessario per tutte le procedure guidate.<br /><br /> In questa procedura dettagliata, l'implementazione della procedura guidata passa un `SiteColumnWizardModel` oggetto alla finestra della procedura guidata quando viene visualizzata la procedura guidata dell'interfaccia utente. L'interfaccia utente della procedura guidata Usa i metodi di questo oggetto per salvare i valori dei controlli nell'interfaccia utente e per eseguire attività quali la verifica che l'URL del sito di input sia valido. Dopo che l'utente termina la procedura guidata, l'implementazione della procedura guidata utilizza il `SiteColumnWizardModel` oggetto per determinare lo stato finale dell'interfaccia utente.|  
|Firma responsabile di progetto|Si tratta di una classe helper denominata `ProjectSigningManager`, utilizzato dall'implementazione della procedura guidata per creare un nuovo file snk in ogni nuova istanza del progetto.|  
|SharePoint (comandi)|Questi sono i metodi utilizzati dal modello di dati della procedura guidata per effettuare chiamate nel sito di SharePoint locale, mentre è in esecuzione la procedura guidata. Poiché i comandi di SharePoint devono destinati a .NET Framework 3.5, questi comandi vengono implementati in un assembly diverso rispetto al resto del codice della procedura guidata.|  
  
## <a name="creating-the-projects"></a>Creazione dei progetti  
 Per completare questa procedura dettagliata, è necessario aggiungere più progetti alla soluzione SiteColumnProjectItem creati in [procedura dettagliata: creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md):  
  
-   Un progetto WPF. Verrà implementata la <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> l'interfaccia e definire l'interfaccia utente della procedura guidata in questo progetto.  
  
-   Un progetto libreria di classi che definisce i comandi di SharePoint. Questo progetto deve avere come destinazione.NET Framework 3.5.  
  
 Avviare la procedura dettagliata creando i progetti.  
  
#### <a name="to-create-the-wpf-project"></a>Per creare il progetto WPF  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], aprire la soluzione SiteColumnProjectItem.  
  
2.  In **Esplora**, aprire il menu di scelta rapida per il **SiteColumnProjectItem** nodo della soluzione, scegliere **Aggiungi**, quindi scegliere **nuovo progetto**.  
  
3.  Nella parte superiore del **Aggiungi nuovo progetto** finestra di dialogo, assicurarsi che **.NET Framework 4.5** viene scelto nell'elenco delle versioni di .NET Framework.  
  
4.  Espandere il **Visual c#** nodo o **Visual Basic** nodo, scegliere il **Windows** nodo.  
  
5.  Nell'elenco dei modelli di progetto, scegliere **libreria di controlli utente WPF**, denominare il progetto **ProjectTemplateWizard**, quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Aggiunge il **ProjectTemplateWizard** progetto alla soluzione e apre il file UserControl1. XAML predefinito.  
  
6.  Eliminare il file UserControl1 dal progetto.  
  
#### <a name="to-create-the-sharepoint-commands-project"></a>Per creare il progetto di comandi di SharePoint  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il nodo della soluzione SiteColumnProjectItem, scegli **Aggiungi**, quindi scegliere **nuovo progetto**.  
  
2.  Nella parte superiore del **Aggiungi nuovo progetto** finestra di dialogo scegliere **.NET Framework 3.5** nell'elenco delle versioni di .NET Framework.  
  
3.  Espandere il **Visual c#** nodo o **Visual Basic** nodo, quindi scegliere il **Windows** nodo.  
  
4.  Scegliere il **libreria di classi** modello di progetto, denominare il progetto **SharePointCommands**, quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Aggiunge il **SharePointCommands** progetto alla soluzione e apre il file di codice predefinito Class1.  
  
5.  Eliminare il file di codice Class1 dal progetto.  
  
## <a name="configuring-the-projects"></a>Configurazione dei progetti  
 Prima di creare la procedura guidata, è necessario aggiungere alcuni file di codice e i riferimenti ad assembly per i progetti.  
  
#### <a name="to-configure-the-wizard-project"></a>Per configurare il progetto della procedura guidata  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il **ProjectTemplateWizard** nodo del progetto e quindi scegliere **proprietà**.  
  
2.  Nel **progettazione**, scegliere il **applicazione** scheda per un progetto Visual c# o **compilare** scheda per un progetto di Visual Basic.  
  
3.  Assicurarsi che il framework di destinazione sia impostato su .NET Framework 4.5, non .NET Framework 4.5 Client Profile.  
  
     Per altre informazioni, vedere [Procedura: Destinare una versione di .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
4.  Aprire il menu di scelta rapida per il **ProjectTemplateWizard** del progetto, scegliere **Aggiungi**, quindi scegliere **nuovo elemento**.  
  
5.  Scegliere il **finestra (WPF)** articolo, nome elemento **nome WizardWindow**, quindi scegliere il **Aggiungi** pulsante.  
  
6.  Aggiungere due **controllo utente (WPF)** elementi al progetto e assegnare loro un nome **Page1** e **Pagina2**.  
  
7.  Aggiungere quattro file di codice al progetto e fornire loro i nomi seguenti:  
  
    -   SiteColumnProjectWizard  
  
    -   SiteColumnWizardModel  
  
    -   ProjectSigningManager  
  
    -   CommandIds  
  
8.  Aprire il menu di scelta rapida per il **ProjectTemplateWizard** nodo del progetto e quindi scegliere **Aggiungi riferimento**.  
  
9. Espandere il **assembly** nodo, scegliere il **estensioni** nodo e quindi selezionare le caselle di controllo accanto agli assembly seguenti:  
  
    -   EnvDTE  
  
    -   Interop  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   11.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.10.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
10. Scegliere il **OK** pulsante per aggiungere gli assembly al progetto.  
  
11. In **Esplora**, sotto il **riferimenti** cartella per il **ProjectTemplateWizard** del progetto, scegliere **EnvDTE**.  
  
12. Nel **proprietà** finestra, modificare il valore della **incorpora tipi di interoperabilità** proprietà **False**.  
  
13. Se si sviluppa un progetto Visual Basic, importare lo spazio dei nomi ProjectTemplateWizard al progetto utilizzando il **progettazione**.  
  
     Per ulteriori informazioni, vedere [procedura: aggiungere o rimuovere spazi dei nomi importati &#40; Visual Basic &#41; ](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md).  
  
#### <a name="to-configure-the-sharepointcommands-project"></a>Per configurare il progetto SharePointCommands  
  
1.  In **Esplora**, scegliere il **SharePointCommands** nodo del progetto.  
  
2.  Nella barra dei menu, scegliere **progetto**, **Aggiungi elemento esistente**.  
  
3.  Nel **Aggiungi elemento esistente** la finestra di dialogo, selezionare la cartella che contiene i file di codice per il progetto ProjectTemplateWizard, quindi scegliere il **CommandIds** file di codice.  
  
4.  Scegliere la freccia accanto al **Aggiungi** e quindi scegliere il **Aggiungi come collegamento** opzione dal menu visualizzato.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Aggiunge il file di codice per il **SharePointCommands** progetto come un collegamento. Il file di codice si trova nel **ProjectTemplateWizard** anche progetto, ma il codice nel file viene compilato nel **SharePointCommands** progetto.  
  
5.  Nel **SharePointCommands** del progetto, aggiungere un altro file di codice denominato comandi.  
  
6.  Scegliere il progetto SharePointCommands e quindi nella barra dei menu scegliere **progetto**, **Aggiungi riferimento**.  
  
7.  Espandere il **assembly** nodo, scegliere il **estensioni** nodo e quindi selezionare le caselle di controllo accanto agli assembly seguenti:  
  
    -   Microsoft. SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
8.  Scegliere il **OK** pulsante per aggiungere gli assembly al progetto.  
  
## <a name="creating-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>Creazione del modello di procedura guidata, la firma di gestione e gli ID di comando di SharePoint  
 Aggiungere al progetto ProjectTemplateWizard per implementare i componenti seguenti nell'esempio di codice:  
  
-   L'ID di comando di SharePoint. Queste stringhe di identificano i comandi di SharePoint che utilizza la procedura guidata. Più avanti in questa procedura dettagliata, si aggiungerà codice al progetto SharePointCommands per implementare i comandi.  
  
-   Il modello di dati di procedura guidata.  
  
-   Firma il project manager.  
  
 Per ulteriori informazioni su questi componenti, vedere [informazioni sui componenti della procedura guidata](#wizardcomponents).  
  
#### <a name="to-define-the-sharepoint-command-ids"></a>Per definire gli ID di comando di SharePoint  
  
1.  Nel progetto ProjectTemplateWizard, aprire il file di codice CommandIds e quindi sostituire tutto il contenuto di questo file con il codice seguente.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb#5)]  
  
#### <a name="to-create-the-wizard-model"></a>Per creare il modello di procedura guidata  
  
1.  Aprire il codice SiteColumnWizardModel e sostituire tutto il contenuto di questo file con il codice seguente.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]  
  
#### <a name="to-create-the-project-signing-manager"></a>Per creare il project manager firma  
  
1.  Aprire il file di codice ProjectSigningManager e quindi sostituire tutto il contenuto di questo file con il codice seguente.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb#8)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs#8)]  
  
## <a name="creating-the-wizard-ui"></a>Creazione guidata dell'interfaccia utente  
 Aggiungere codice XAML per definire l'interfaccia utente della finestra della procedura guidata e i due controlli utente che forniscono all'interfaccia utente per le pagine della procedura guidata e aggiungere il codice per definire il comportamento dei controlli finestra e utente. La procedura guidata che crei assomiglia la procedura guidata predefinita per i progetti SharePoint in Visual Studio.  
  
> [!NOTE]  
>  Nei passaggi seguenti nel progetto saranno presenti alcuni errori di compilazione dopo aver aggiunto XAML o il codice al progetto. Questi errori non verranno più visualizzato quando si aggiunge il codice nei passaggi successivi.  
  
#### <a name="to-create-the-wizard-window-ui"></a>Per creare la finestra della procedura guidata dell'interfaccia utente  
  
1.  Nel progetto ProjectTemplateWizard, aprire il menu di scelta rapida per il file WizardWindow e quindi scegliere **aprire** per aprire la finestra nella finestra di progettazione.  
  
2.  Nella visualizzazione della finestra di progettazione XAML, sostituire il codice XAML corrente con il seguente codice XAML. Il codice XAML definisce un'interfaccia utente che include un'intestazione, un <xref:System.Windows.Controls.Grid> che contiene le pagine della procedura guidata e pulsanti di navigazione nella parte inferiore della finestra.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml#10)]  
  
    > [!NOTE]  
    >  La finestra che viene creata in questo codice XAML è derivata dalla <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> classe di base. Quando si aggiunge una finestra di dialogo WPF personalizzata a Visual Studio, è consigliabile che la finestra di dialogo si deriva da questa classe di stile coerenza con altre finestre di dialogo di Visual Studio e per evitare problemi di finestra di dialogo modale che potrebbero verificarsi in caso contrario. Per ulteriori informazioni, vedere [creazione e la gestione delle finestre di dialogo modale](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).  
  
3.  Se stai sviluppando un progetto Visual Basic, rimuovere il `ProjectTemplateWizard` dello spazio dei nomi dal `WizardWindow` nel nome della classe di `x:Class` attributo del `Window` elemento. Questo elemento è nella prima riga del codice XAML. Al termine, la prima riga dovrebbe essere analogo al seguente.  
  
    ```  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  Aprire il file code-behind per il file WizardWindow.  
  
5.  Sostituire il contenuto di questo file, ad eccezione di `using` dichiarazioni nella parte superiore del file, con il codice seguente.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb#4)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs#4)]  
  
#### <a name="to-create-the-first-wizard-page-ui"></a>Per creare la prima pagina della procedura guidata dell'interfaccia utente  
  
1.  Nel progetto ProjectTemplateWizard, aprire il menu di scelta rapida per il file Page1 e quindi scegliere **aprire** per aprire il controllo utente nella finestra di progettazione.  
  
2.  Nella visualizzazione della finestra di progettazione XAML, sostituire il codice XAML corrente con il seguente codice XAML. Il codice XAML definisce un'interfaccia utente che include una casella di testo in cui gli utenti possono immettere l'URL dei siti locali da utilizzare per il debug. L'interfaccia utente include inoltre i pulsanti di opzione con cui gli utenti possono specificare se il progetto è in modalità sandbox.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml#11)]  
  
3.  Se si sviluppa un progetto Visual Basic, rimuovere il `ProjectTemplateWizard` dello spazio dei nomi dal `Page1` nel nome della classe di `x:Class` attributo del `UserControl` elemento. Questa è la prima riga del codice XAML. Al termine, la prima riga dovrebbe essere simile al seguente.  
  
    ```  
    <UserControl x:Class="Page1"  
    ```  
  
4.  Sostituire il contenuto del file Page1, fatta eccezione per il `using` dichiarazioni nella parte superiore del file, con il codice seguente.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs#2)]  
  
#### <a name="to-create-the-second-wizard-page-ui"></a>Per creare la seconda pagina della procedura guidata dell'interfaccia utente  
  
1.  Nel progetto ProjectTemplateWizard, aprire il menu di scelta rapida per il file Page2. XAML e quindi scegliere **aprire**.  
  
     Il controllo utente viene visualizzato nella finestra di progettazione.  
  
2.  Nella visualizzazione XAML, sostituire il codice XAML corrente con il seguente codice XAML. Il codice XAML definisce un'interfaccia utente che include un elenco di riepilogo a discesa per la scelta del tipo di base di una casella di testo per specificare il nome della colonna del sito, la colonna del sito e una casella combinata per la specifica di un gruppo incorporato o personalizzato in cui visualizzare la colonna del sito nella raccolta.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml#12)]  
  
3.  Se si sviluppa un progetto Visual Basic, rimuovere il `ProjectTemplateWizard` dello spazio dei nomi dal `Page2` nel nome della classe di `x:Class` attributo del `UserControl` elemento. Questa è la prima riga del codice XAML. Al termine, la prima riga dovrebbe essere simile al seguente.  
  
    ```  
    <UserControl x:Class="Page2"  
    ```  
  
4.  Sostituire il contenuto del file code-behind per il file Page2. XAML, ad eccezione di `using` dichiarazioni nella parte superiore del file, con il codice seguente.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb#3)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs#3)]  
  
## <a name="implementing-the-wizard"></a>Implementazione della procedura guidata  
 Definire la funzionalità principale della procedura guidata implementando il <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaccia. Questa interfaccia definisce i metodi chiamati da Visual Studio quando inizia e termina e in determinati momenti durante la procedura guidata viene eseguita la procedura guidata.  
  
#### <a name="to-implement-the-wizard"></a>Per implementare la procedura guidata  
  
1.  Nel progetto ProjectTemplateWizard, aprire il codice SiteColumnProjectWizard.  
  
2.  Sostituire l'intero contenuto di questo file con il codice seguente.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]  
  
## <a name="creating-the-sharepoint-commands"></a>Creazione di comandi di SharePoint  
 Creare due comandi personalizzati che effettuano chiamate nel modello a oggetti di SharePoint server. Un comando determina se l'URL del sito che l'utente digita nella procedura guidata è valido. Il comando Ottiene tutti i tipi di campo dal sito di SharePoint specificato in modo che gli utenti possono selezionare quello da utilizzare come base per la nuova colonna del sito.  
  
#### <a name="to-define-the-sharepoint-commands"></a>Per definire i comandi di SharePoint  
  
1.  Nel **SharePointCommands** del progetto, aprire il file di codice i comandi.  
  
2.  Sostituire l'intero contenuto di questo file con il codice seguente.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb#9)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs#9)]  
  
## <a name="checkpoint"></a>Checkpoint  
 A questo punto la procedura dettagliata, tutto il codice per la procedura guidata è ora nel progetto. Compilare il progetto per assicurarsi che l'operazione avvenga senza errori.  
  
#### <a name="to-build-your-project"></a>Per compilare il progetto  
  
1.  Nella barra dei menu scegliere **Compilazione**, **Compila soluzione**.  
  
## <a name="removing-the-keysnk-file-from-the-project-template"></a>Rimozione File key.snk al modello di progetto  
 In [procedura dettagliata: creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md), il modello di progetto creato contiene un file key.snk che viene utilizzato per firmare ogni istanza di progetto colonna del sito. Questo file snk non è più necessario perché la procedura guidata genera ora un nuovo file key.snk per ogni progetto. Rimuovere il file snk dal modello di progetto e rimuovere i riferimenti a questo file.  
  
#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>Per rimuovere il file snk dal modello di progetto  
  
1.  In **Esplora soluzioni**, sotto il **SiteColumnProjectTemplate** nodo, aprire il menu di scelta rapida per il **key.snk** file, quindi fare clic **eliminare**.  
  
2.  Nella finestra di dialogo di conferma visualizzata, scegliere il **OK** pulsante.  
  
3.  Sotto il **SiteColumnProjectTemplate** nodo, aprire il file SiteColumnProjectTemplate e quindi rimuovere l'elemento seguente.  
  
    ```  
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
    ```  
  
4.  Salvare e chiudere il file.  
  
5.  Sotto il **SiteColumnProjectTemplate** nodo, aprire il file csproj o ProjectTemplate e quindi rimuovere il seguente `PropertyGroup` elemento da esso.  
  
    ```  
    <PropertyGroup>  
      <SignAssembly>true</SignAssembly>  
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
    </PropertyGroup>  
    ```  
  
6.  Rimuovere il seguente `None` elemento.  
  
    ```  
    <None Include="key.snk" />  
    ```  
  
7.  Salvare e chiudere il file.  
  
## <a name="associating-the-wizard-with-the-project-template"></a>Associazione della procedura guidata con il modello di progetto  
 Dopo aver implementato la procedura guidata, è necessario associare la procedura guidata con le **colonna del sito** modello di progetto. Esistono tre procedure, che è necessario completare per eseguire questa operazione:  
  
1.  Firmare l'assembly della procedura guidata con un nome sicuro.  
  
2.  Ottenere la chiave pubblica token per l'assembly della procedura guidata.  
  
3.  Aggiungere un riferimento all'assembly della procedura guidata nel file. vstemplate per il **colonna del sito** modello di progetto.  
  
#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Per firmare l'assembly della procedura guidata con un nome sicuro  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il **ProjectTemplateWizard** del progetto e quindi scegliere **proprietà**.  
  
2.  Nel **firma** , selezionare il **firmare l'assembly** casella di controllo.  
  
3.  Nel **Scegli un file chiave con nome sicuro** scegliere  **\<nuovo … >**.  
  
4.  Nel **Crea chiave con nome sicuro** finestra di dialogo immettere un nome per il nuovo file di chiave, deselezionare il **Proteggi file di chiave con una password** casella di controllo e quindi scegliere il **OK** pulsante.  
  
5.  Aprire il menu di scelta rapida per il **ProjectTemplateWizard** del progetto e quindi scegliere **compilare** per creare il file ProjectTemplateWizard. dll.  
  
#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Per ottenere la chiave pubblica token per l'assembly della procedura guidata  
  
1.  Nel **Menu Start**, scegliere **tutti i programmi**, scegliere **Microsoft Visual Studio**, scegliere **Visual Studio Tools**, quindi scegliere  **Prompt dei comandi per sviluppatori**.  
  
     Verrà visualizzata una finestra del prompt dei comandi di Visual Studio.  
  
2.  Eseguire il comando seguente, sostituendo *PathToWizardAssembly* con il percorso completo per l'assembly compilato ProjectTemplateWizard. dll per il progetto ProjectTemplateWizard nel computer di sviluppo:  
  
    ```  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     Il token di chiave pubblica per l'assembly ProjectTemplateWizard. dll è scritta per la finestra del Prompt dei comandi di Visual Studio.  
  
3.  Mantenere aperta la finestra del Prompt dei comandi di Visual Studio. È necessario il token di chiave pubblica durante la procedura seguente.  
  
#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Per aggiungere un riferimento all'assembly della procedura guidata nel file vstemplate  
  
1.  In **Esplora**, espandere il **SiteColumnProjectTemplate** nodo del progetto e aprire il file SiteColumnProjectTemplate.  
  
2.  Verso la fine del file, aggiungere il seguente `WizardExtension` elemento tra le `</TemplateContent>` e `</VSTemplate>` tag. Sostituire il *il token* valore il `PublicKeyToken` attributo con il token di chiave pubblica ottenuto nella procedura precedente.  
  
    ```  
    <WizardExtension>  
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>  
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Per ulteriori informazioni sul `WizardExtension` elemento, vedere [WizardExtension (elemento) &#40; Modelli di Visual Studio &#41; ](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).  
  
3.  Salvare e chiudere il file.  
  
## <a name="adding-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>Aggiunta di parametri sostituibili nel file Elements.xml nel modello di progetto  
 Aggiungere il file Elements.xml nel progetto SiteColumnProjectTemplate diversi parametri sostituibili. Questi parametri vengono inizializzati nel `RunStarted` metodo la `SiteColumnProjectWizard` classe definita in precedenza. Quando un utente crea un progetto di colonna del sito, Visual Studio sostituisce automaticamente questi parametri nel file Elements.xml nel nuovo progetto con i valori specificati nella procedura guidata.  
  
 Un parametro sostituibile è un token che inizia e finisce con il segno di dollaro ($). Inoltre, per definire i propri parametri sostituibili, è possibile utilizzare i parametri predefiniti che vengono definiti e inizializzati dal sistema del progetto SharePoint. Per ulteriori informazioni, vedere [parametri sostituibili](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Per aggiungere parametri sostituibili nel file Elements.xml  
  
1.  Nel progetto SiteColumnProjectTemplate, sostituire il contenuto del file Elements.xml con il seguente codice XML.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
             Name="$fieldname$"   
             DisplayName="$fieldname$"   
             Type="$selectedfieldtype$"   
             Group="$selectedgrouptype$">  
      </Field>  
    </Elements>  
    ```  
  
     Il nuovo codice XML modifica i valori del `Name`, `DisplayName`, `Type`, e `Group` attributi a parametri sostituibili personalizzati.  
  
2.  Salvare e chiudere il file.  
  
## <a name="adding-the-wizard-to-the-vsix-package"></a>Aggiunta della procedura guidata per il pacchetto VSIX  
 Per distribuire la procedura guidata con il pacchetto VSIX che contiene il modello di progetto colonna del sito, aggiungere riferimenti al progetto della procedura guidata e il progetto di comandi di SharePoint per il file vsixmanifest nel progetto VSIX.  
  
#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Per aggiungere la procedura guidata per il pacchetto VSIX  
  
1.  In **Esplora**nella **SiteColumnProjectItem** del progetto, aprire il menu di scelta rapida per il **vsixmanifest** file e quindi scegliere **Aprire**.  
  
     Visual Studio apre il file nell'editor del manifesto.  
  
2.  Nel **asset** scheda dell'editor, scegliere il **New** pulsante.  
  
     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.  
  
3.  Nel **tipo** scegliere **Microsoft.VisualStudio.Assembly**.  
  
4.  Nel **origine** scegliere **un progetto nella soluzione corrente**.  
  
5.  Nel **progetto** scegliere **ProjectTemplateWizard**, quindi scegliere il **OK** pulsante.  
  
6.  Nel **asset** scheda dell'editor, scegliere il **New** nuovamente clic sul pulsante.  
  
     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.  
  
7.  Nel **tipo** immettere **v4**.  
  
8.  Nel **origine** scegliere **un progetto nella soluzione corrente**.  
  
9. Nel **progetto** scegliere il **SharePointCommands** del progetto e quindi scegliere il **OK** pulsante.  
  
10. Nella barra dei menu, scegliere **compilare**, **Compila soluzione**, quindi assicurarsi che la soluzione venga compilata senza errori.  
  
## <a name="testing-the-wizard"></a>Test della procedura guidata  
 A questo punto si è pronti testare la procedura guidata. Innanzitutto, avviare il debug della soluzione SiteColumnProjectItem nell'istanza sperimentale di Visual Studio. Testare quindi la procedura guidata per il progetto colonna del sito nell'istanza sperimentale di Visual Studio. Infine, compilare ed eseguire il progetto per verificare che la colonna del sito funzioni come previsto.  
  
#### <a name="to-start-debugging-the-solution"></a>Per avviare il debug della soluzione  
  
1.  Riavviare Visual Studio con credenziali amministrative e quindi aprire la soluzione SiteColumnProjectItem.  
  
2.  Nel progetto ProjectTemplateWizard, aprire il codice SiteColumnProjectWizard e quindi aggiungere un punto di interruzione sulla prima riga di codice il `RunStarted` metodo.  
  
3.  Nella barra dei menu, scegliere **Debug**, **eccezioni**.  
  
4.  Nel **eccezioni** finestra di dialogo, assicurarsi che il **generata** e **gestita dall'utente** caselle di controllo per **eccezioni Common Language Runtime**vengono cancellati e quindi scegliere il **OK** pulsante.  
  
5.  Avviare il debug scegliendo il **F5** chiave oppure sulla barra dei menu, scegliendo **Debug**, **Avvia debug**.  
  
     Visual Studio installa l'estensione per %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0 e avvia un'istanza sperimentale di Visual Studio. L'elemento del progetto verrà testato in questa istanza di Visual Studio.  
  
#### <a name="to-test-the-wizard-in-visual-studio"></a>Per testare la procedura guidata in Visual Studio  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **File**, **New**, **progetto**.  
  
2.  Espandere il **Visual c#** nodo o **Visual Basic** nodo (a seconda del linguaggio che supporta il modello di progetto), espandere il **SharePoint** nodo e quindi scegliere il **2010** nodo.  
  
3.  Nell'elenco dei modelli di progetto, scegliere **colonna del sito**, denominare il progetto **SiteColumnWizardTest**, quindi scegliere il **OK** pulsante.  
  
4.  Verificare che il codice in altra istanza di Visual Studio si arresta nel punto di interruzione impostato precedentemente nel `RunStarted` metodo.  
  
5.  Continuare il debug del progetto scegliendo il **F5** chiave oppure sulla barra dei menu, scegliendo **Debug**, **continua**.  
  
6.  Nel **Personalizzazione guidata SharePoint**, immettere l'URL del sito che si desidera utilizzare per il debug e quindi scegliere il **Avanti** pulsante.  
  
7.  Nella seconda pagina della finestra di **Personalizzazione guidata SharePoint**, effettuare le selezioni seguenti:  
  
    -   Nel **tipo** scegliere **booleano**.  
  
    -   Nel **gruppo** scegliere **colonne Sì/No personalizzate**.  
  
    -   Nel **nome** immettere **colonna Sì/No personale**, quindi scegliere il **fine** pulsante.  
  
     In **Esplora**, un nuovo progetto verrà visualizzato e contiene un elemento di progetto denominato **Field1**, e Visual Studio apre il file Elements.xml del progetto nell'editor.  
  
8.  Verificare che Elements.xml contiene i valori specificati nella procedura guidata.  
  
#### <a name="to-test-the-site-column-in-sharepoint"></a>Per testare la colonna del sito in SharePoint  
  
1.  Nell'istanza sperimentale di Visual Studio, premere il tasto F5.  
  
     La colonna del sito viene incluso nel pacchetto e distribuita in SharePoint del sito che il **URL del sito** specifica proprietà del progetto. Nel browser viene visualizzata la pagina predefinita del sito.  
  
    > [!NOTE]  
    >  Se il **debug degli Script disabilitato** viene visualizzata la finestra di dialogo, scegliere il **Sì** per continuare il debug del progetto.  
  
2.  Nel **Azioni sito** menu, scegliere **Impostazioni sito**.  
  
3.  Nella pagina Impostazioni sito in **raccolte**, scegliere il **colonne sito** collegamento.  
  
4.  Nell'elenco delle colonne del sito, verificare che un **colonne Sì/No personalizzate** gruppo contiene una colonna denominata **colonna Sì/No personale**e quindi chiudere il browser web.  
  
## <a name="cleaning-up-the-development-computer"></a>Pulizia dei Computer di sviluppo  
 Dopo aver completato l'elemento del progetto di test, rimuovere il modello di progetto dall'istanza sperimentale di Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Per pulire il computer di sviluppo  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **strumenti**, **estensioni e aggiornamenti**.  
  
     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.  
  
2.  Nell'elenco di estensioni, scegliere **colonna del sito**, quindi scegliere il **Disinstalla** pulsante.  
  
3.  Nella finestra di dialogo visualizzata, scegliere il **Sì** pulsante per confermare che si desidera disinstallare l'estensione e quindi scegliere il **Riavvia ora** per completare la disinstallazione.  
  
4.  Chiudere l'istanza sperimentale di Visual Studio sia l'istanza in cui la soluzione CustomActionProjectItem è aperta.  
  
     Per informazioni su come distribuire [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] estensioni, vedere [Shipping estensioni di Visual Studio](/visualstudio/extensibility/shipping-visual-studio-extensions).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Definizione di tipi di elemento di progetto SharePoint personalizzato](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creazione di modelli di progetto e modelli di elemento per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Riferimenti allo schema dei modelli di Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Procedura: Usare procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md)  
  
  