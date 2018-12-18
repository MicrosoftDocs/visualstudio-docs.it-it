---
title: 'Procedura dettagliata: Creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 1 | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: dae92a4c20130425fa93a413856f3d2cb5a37387
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1"></a>Procedura dettagliata: Creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 1
  È possibile estendere il sistema di progetto SharePoint in Visual Studio mediante la creazione di tipi di elemento di progetto. In questa procedura dettagliata, si creerà un elemento di progetto che può essere aggiunto a un progetto di SharePoint per creare un'azione personalizzata in un sito di SharePoint. L'azione personalizzata aggiunge una voce di menu per il **Azioni sito** menu del sito di SharePoint.  
  
 In questa procedura dettagliata vengono descritte le attività seguenti:  
  
-   Creazione di un'estensione di Visual Studio che definisce un nuovo tipo di elemento di progetto SharePoint per un'azione personalizzata. Il nuovo tipo di elemento di progetto implementa numerose funzionalità personalizzate:  
  
    -   Menu di scelta rapida che funge da punto di partenza per altre attività correlate all'elemento del progetto, ad esempio la visualizzazione di una finestra di progettazione per l'azione personalizzata in Visual Studio.  
  
    -   Codice eseguito quando uno sviluppatore modifica alcune proprietà dell'elemento di progetto e il progetto che lo contiene.  
  
    -   Un'icona personalizzata che viene visualizzato accanto all'elemento di progetto in **Esplora**.  
  
-   Creazione di un modello di elemento di Visual Studio per l'elemento del progetto.  
  
-   Compilazione di un pacchetto di Visual Studio Extension (VSIX) per distribuire il modello di elemento di progetto e l'assembly dell'estensione.  
  
-   Il debug e test dell'elemento di progetto.  
  
 Si tratta di una procedura dettagliata autonoma. Dopo aver completato questa procedura dettagliata, è possibile migliorare l'elemento del progetto mediante l'aggiunta di una procedura guidata per il modello di elemento. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
> [!NOTE]  
>  È possibile scaricare un esempio che contiene i progetti completati, codice e altri file per questa procedura dettagliata dal seguente percorso: [http://go.microsoft.com/fwlink/?LinkId=191369](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Sono necessari i seguenti componenti nel computer di sviluppo per completare questa procedura dettagliata:  
  
-   Le edizioni supportate di Microsoft Windows, SharePoint e Visual Studio. Per ulteriori informazioni, vedere [requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Oggetto [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Questa procedura dettagliata Usa il **progetto VSIX** modello nel SDK per creare un pacchetto VSIX per distribuire l'elemento del progetto. Per ulteriori informazioni, vedere [estensione degli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Conoscere i concetti seguenti è utile, ma non obbligatorio, per completare la procedura dettagliata:  
  
-   Azioni personalizzate in SharePoint. Per ulteriori informazioni, vedere [l'azione personalizzata](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
-   Modelli di elemento in Visual Studio. Per altre informazioni, vedere [Creazione di modelli di progetti e di elementi](/visualstudio/ide/creating-project-and-item-templates).  
  
## <a name="creating-the-projects"></a>Creazione dei progetti  
 Per completare questa procedura dettagliata, è necessario creare tre progetti:  
  
-   Un progetto VSIX. Questo progetto crea il pacchetto VSIX per distribuire l'elemento di progetto SharePoint.  
  
-   Un progetto di modello di elemento. Questo progetto crea un modello di elemento che può essere utilizzato per aggiungere l'elemento del progetto SharePoint a un progetto SharePoint.  
  
-   Un progetto libreria di classi. Questo progetto implementa un'estensione di Visual Studio che definisce il comportamento dell'elemento di progetto SharePoint.  
  
 Avviare la procedura dettagliata creando i progetti.  
  
#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
3.  Nell'elenco nella parte superiore del **nuovo progetto** finestra di dialogo, assicurarsi che **.NET Framework 4.5** è selezionata.  
  
4.  Nel **nuovo progetto** finestra di dialogo espandere il **Visual c#** o **Visual Basic** nodi e quindi scegliere il **estendibilità** nodo.  
  
    > [!NOTE]  
    >  Il **estendibilità** nodo è disponibile solo se si installa Visual Studio SDK. Per ulteriori informazioni, vedere la sezione Prerequisiti in questo argomento.  
  
5.  Scegliere il **progetto VSIX** modello.  
  
6.  Nel **nome** immettere **CustomActionProjectItem**, quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Aggiunge il **CustomActionProjectItem** progetto **Esplora**.  
  
#### <a name="to-create-the-item-template-project"></a>Per creare il progetto di modello di elemento  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il nodo della soluzione, scegliere **Aggiungi**, quindi scegliere **nuovo progetto**.  
  
2.  Nell'elenco nella parte superiore del **nuovo progetto** finestra di dialogo, assicurarsi che **.NET Framework 4.5** è selezionata.  
  
3.  Nel **nuovo progetto** finestra di dialogo espandere il **Visual c#** o **Visual Basic** nodi e quindi scegliere il **estendibilità** nodo.  
  
4.  Nell'elenco dei modelli di progetto, scegliere il **il modello di elemento c#** o **il modello di elemento di Visual Basic** modello.  
  
5.  Nel **nome** immettere **ItemTemplate**, quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Aggiunge il **ItemTemplate** progetto alla soluzione.  
  
#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il nodo della soluzione, scegliere **Aggiungi**, quindi scegliere **nuovo progetto**.  
  
2.  Nell'elenco nella parte superiore del **nuovo progetto** finestra di dialogo, assicurarsi che **.NET Framework 4.5** è selezionata.  
  
3.  Nel **nuovo progetto** finestra di dialogo espandere il **Visual c#** o **Visual Basic** nodi, scegliere il **Windows** nodo e quindi scegliere il  **Libreria di classi** modello di progetto.  
  
4.  Nel **nome** immettere **ProjectItemDefinition**, quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Aggiunge il **ProjectItemDefinition** progetto alla soluzione e apre il file di codice predefinito Class1.  
  
5.  Eliminare il file di codice Class1 dal progetto.  
  
## <a name="configuring-the-extension-project"></a>Configurazione del progetto di estensione  
 Prima di scrivere codice per definire il tipo di elemento di progetto SharePoint, è necessario aggiungere i file di codice e i riferimenti ad assembly al progetto di estensione.  
  
#### <a name="to-configure-the-project"></a>Per configurare il progetto  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il **ProjectItemDefinition** del progetto, scegliere **Aggiungi**, quindi scegliere **nuovo elemento**.  
  
2.  Nell'elenco di elementi del progetto, scegliere **File di codice**.  
  
3.  Nel **nome** , immettere il nome **CustomAction** con l'appropriato estensione di file e quindi scegliere il **Aggiungi** pulsante.  
  
4.  In **Esplora**, aprire il menu di scelta rapida per il **ProjectItemDefinition** del progetto e quindi scegliere **Aggiungi riferimento**.  
  
5.  Nel **gestione riferimenti - ProjectItemDefinition** finestra di dialogo scegliere il **assembly** nodo, quindi scegliere il **Framework** nodo.  
  
6.  Selezionare la casella di controllo accanto a ogni degli assembly seguenti:  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
7.  Scegliere il **estensioni** nodo, selezionare la casella di controllo accanto all'assembly Microsoft.VisualStudio.Sharepoint e quindi scegliere il **OK** pulsante.  
  
## <a name="defining-the-new-sharepoint-project-item-type"></a>Definire il nuovo tipo di elemento di progetto SharePoint  
 Creare una classe che implementa il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfaccia per definire il comportamento del nuovo tipo di elemento di progetto. Implementare questa interfaccia ogni volta che si desidera definire un nuovo tipo di elemento di progetto.  
  
#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Per definire il nuovo tipo di elemento di progetto SharePoint  
  
1.  Nel progetto ProjectItemDefinition, aprire il file di codice CustomAction.  
  
2.  Sostituire il codice in questo file con il codice seguente.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb#1)]  
  
## <a name="creating-an-icon-for-the-project-item-in-solution-explorer"></a>Creazione di un'icona per l'elemento del progetto in Esplora soluzioni  
 Quando si crea un elemento di progetto SharePoint personalizzato, è possibile associare un'immagine (icona o bitmap) con l'elemento del progetto. Questa immagine viene visualizzata accanto all'elemento di progetto in **Esplora**.  
  
 Nella procedura seguente, creare un'icona per l'elemento del progetto e l'icona di incorporare nell'assembly di estensione. Questa icona fa riferimento il <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> del `CustomActionProjectItemTypeProvider` classe creata in precedenza.  
  
#### <a name="to-create-a-custom-icon-for-the-project-item"></a>Per creare un'icona personalizzata per l'elemento del progetto  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il **ProjectItemDefinition** del progetto, scegliere **Aggiungi**, quindi scegliere **nuovo elemento...** .  
  
2.  Nell'elenco di elementi del progetto, scegliere il **File icona** elemento.  
  
    > [!NOTE]  
    >  Nei progetti di Visual Basic, è necessario scegliere il **generale** nodo per visualizzare il **File icona** elemento.  
  
3.  Nel **nome** immettere **CustomAction_SolutionExplorer. ico**, quindi scegliere il **Aggiungi** pulsante.  
  
     Verrà visualizzata l'icona di nuovo nel **Editor di immagini**.  
  
4.  Modificare la versione di 16 x 16 del file icona in modo che abbia una struttura, è possibile riconoscere e quindi salvare il file dell'icona.  
  
5.  In **Esplora**, scegliere **CustomAction_SolutionExplorer. ico**.  
  
6.  Nel **proprietà** finestra, scegliere la freccia accanto al **azione di compilazione** proprietà.  
  
7.  Nell'elenco visualizzato, scegliere **risorsa incorporata**.  
  
## <a name="checkpoint"></a>Checkpoint  
 A questo punto la procedura dettagliata, tutto il codice per l'elemento del progetto è ora nel progetto. Compilare il progetto per verificare che l'operazione avvenga senza errori.  
  
#### <a name="to-build-your-project"></a>Per compilare il progetto  
  
1.  Aprire il menu di scelta rapida per il **ProjectItemDefinition** progetto e scegliere **compilare**.  
  
## <a name="creating-a-visual-studio-item-template"></a>Creazione di un modello di elemento di Visual Studio  
 Per consentire ad altri sviluppatori di utilizzare l'elemento di progetto, è necessario creare un modello di progetto o un modello di elemento. Gli sviluppatori di utilizzano tali modelli in Visual Studio per creare un'istanza dell'elemento di progetto tramite la creazione di un nuovo progetto o mediante l'aggiunta di un elemento a un progetto esistente. Questa procedura dettagliata, utilizzare il progetto ItemTemplate per configurare l'elemento di progetto.  
  
#### <a name="to-create-the-item-template"></a>Per creare il modello di elemento  
  
1.  Eliminare il file di codice Class1 dal progetto ItemTemplate.  
  
2.  Nel progetto ItemTemplate, aprire il file ItemTemplate.  
  
3.  Sostituire il contenuto del file con il codice XML seguente, quindi salvare e chiudere il file.  
  
    > [!NOTE]  
    >  Il codice XML seguente è per un modello di elemento Visual c#. Se si sta creando un modello di elemento di Visual Basic, sostituire il valore di `ProjectType` elemento con `VisualBasic`.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
      <TemplateData>  
        <DefaultName>CustomAction</DefaultName>  
        <Name>Custom Action</Name>  
        <Description>SharePoint Custom Action by Contoso</Description>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>1000</SortOrder>  
        <Icon>ItemTemplate.ico</Icon>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
      <TemplateContent>  
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\Elements.xml">Elements.xml</ProjectItem>  
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\SharePointProjectItem.spdata">CustomAction.spdata</ProjectItem>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
     Questo file definisce il contenuto e il comportamento del modello di elemento. Per ulteriori informazioni sul contenuto di questo file, vedere [riferimenti dello Schema dei modelli di Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference).  
  
4.  In **Esplora**, aprire il menu di scelta rapida per il **ItemTemplate** del progetto, scegliere **Aggiungi**, quindi scegliere **nuovo elemento**.  
  
5.  Nel **Aggiungi nuovo elemento** finestra di dialogo scegliere la **File di testo** modello.  
  
6.  Nel **nome** immettere **CustomAction. spdata**, quindi scegliere il **Aggiungi** pulsante.  
  
7.  Aggiungere il codice XML seguente al file CustomAction. spdata, quindi salvare e chiudere il file.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"   
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />  
      </Files>  
    </ProjectItem>  
    ```  
  
     Questo file contiene informazioni sui file contenuti nell'elemento di progetto. Il `Type` attributo del `ProjectItem` elemento deve essere impostato sulla stessa stringa che viene passato al <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> nella definizione di elemento di progetto (la `CustomActionProjectItemTypeProvider` classe creata precedentemente in questa procedura dettagliata). Per ulteriori informazioni sul contenuto dei file spdata, vedere [riferimenti dello Schema di elemento di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).  
  
8.  In **Esplora**, aprire il menu di scelta rapida per il **ItemTemplate** del progetto, scegliere **Aggiungi**, quindi scegliere **nuovo elemento**.  
  
9. Nel **Aggiungi nuovo elemento** finestra di dialogo scegliere la **File XML** modello.  
  
10. Nel **nome** immettere **Elements.xml**e quindi scegliere il **Aggiungi** pulsante.  
  
11. Sostituire il contenuto del file Elements.xml con il codice XML seguente, quindi salvare e chiudere il file.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="Replace this with a GUID or some other unique string"  
                    GroupId="SiteActions"  
                    Location="Microsoft.SharePoint.StandardMenu"  
                    Sequence="1000"  
                    Title="Replace this with your title"  
                    Description="Replace this with your description" >  
        <UrlAction Url="~site/Lists/Tasks/AllItems.aspx"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     Questo file definisce un'azione personalizzata predefinita che crea una voce di menu sul **Azioni sito** menu del sito di SharePoint. Quando un utente sceglie la voce di menu, l'URL specificato nella `UrlAction` elemento verrà visualizzata nel web browser. Per ulteriori informazioni sugli elementi XML è possibile utilizzare per definire un'azione personalizzata, vedere [le definizioni di azioni personalizzate](http://go.microsoft.com/fwlink/?LinkId=177801).  
  
12. Facoltativamente, aprire il file ItemTemplate. ico e modificarlo in modo che abbia una progettazione che è possibile riconoscere. Questa icona verrà visualizzata accanto all'elemento di progetto nel **Aggiungi nuovo elemento** la finestra di dialogo.  
  
13. In **Esplora**, aprire il menu di scelta rapida per il **ItemTemplate** del progetto e quindi scegliere **Scarica progetto**.  
  
14. Aprire il menu di scelta rapida per il **ItemTemplate** nuovo progetto e quindi scegliere **Modifica ItemTemplate. csproj** o **Modifica ItemTemplate**.  
  
15. Individuare la seguente `VSTemplate` elemento nel file di progetto.  
  
    ```  
    <VSTemplate Include="ItemTemplate.vstemplate">  
    ```  
  
16. Sostituire `VSTemplate` elemento con il codice XML seguente, quindi salvare e chiudere il file.  
  
    ```  
    <VSTemplate Include="ItemTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     Il `OutputSubPath` elemento specifica le cartelle aggiuntive nel percorso in cui viene creato il modello di elemento quando si compila il progetto. Le cartelle specificate assicurarsi che il modello di elemento sarà disponibile solo quando hanno aperto il **Aggiungi nuovo elemento** finestra di dialogo espandere il **SharePoint** nodo e quindi scegliere il **2010**  nodo.  
  
17. In **Esplora**, aprire il menu di scelta rapida per il **ItemTemplate** del progetto e quindi scegliere **Ricarica progetto**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-item"></a>Creazione di un pacchetto VSIX per distribuire l'elemento del progetto  
 Per distribuire l'estensione, è possibile utilizzare il progetto VSIX nella soluzione per creare un pacchetto VSIX. Innanzitutto, configurare il pacchetto VSIX modificando il file vsixmanifest incluso nel progetto VSIX. Quindi, creare il pacchetto VSIX per la compilazione della soluzione.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Per configurare e creare il pacchetto VSIX  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il **vsixmanifest** file nel progetto CustomActionProjectItem e quindi scegliere **aprire**.  
  
     Visual Studio apre il file nell'editor del manifesto. Il file vsixmanifest è la base per il file extension vsixmanifest che richiedono tutti i pacchetti VSIX. Per ulteriori informazioni su questo file, vedere [riferimento 1.0 dello Schema di estensione VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Nel **Product Name** immettere **elemento di progetto azione personalizzata**.  
  
3.  Nel **autore** immettere **Contoso**.  
  
4.  Nel **descrizione** immettere **SharePoint di un elemento di progetto che rappresenta un'azione personalizzata**.  
  
5.  Nel **asset** scheda, scegliere il **New** pulsante.  
  
     Il **Aggiungi nuovo Asset** viene visualizzata la finestra di dialogo.  
  
6.  Nel **tipo** scegliere **Microsoft.VisualStudio.ItemTemplate**.  
  
    > [!NOTE]  
    >  Questo valore corrisponde al `ItemTemplate` elemento nel file Extension. vsixmanifest. Questo elemento identifica la sottocartella nel pacchetto VSIX che contiene il modello di elemento di progetto. Per ulteriori informazioni, vedere [elemento ItemTemplate (schema VSX)](http://msdn.microsoft.com/en-us/1d489e54-c1c5-4f96-a510-6c2640867ff0).  
  
7.  Nel **origine** scegliere **un progetto nella soluzione corrente**.  
  
8.  Nel **progetto** scegliere **ItemTemplate**, quindi scegliere il **OK** pulsante.  
  
9. Nel **asset** scheda, scegliere il **New** nuovamente clic sul pulsante.  
  
     Il **Aggiungi nuovo Asset** viene visualizzata la finestra di dialogo.  
  
10. Nel **tipo** scegliere **MEFComponent**.  
  
    > [!NOTE]  
    >  Questo valore corrisponde al `MefComponent` elemento nel file Extension. vsixmanifest. Questo elemento specifica il nome di un assembly di estensione nel pacchetto VSIX. Per ulteriori informazioni, vedere [elemento MEFComponent (schema VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
11. Nel **origine** scegliere **un progetto nella soluzione corrente**.  
  
12. Nel **progetto** scegliere **ProjectItemDefinition**.  
  
13. Fare clic sul pulsante **OK** .  
  
14. Nella barra dei menu, scegliere **compilare**, **Compila soluzione**, quindi assicurarsi che il progetto venga compilato senza errori.  
  
15. Verificare che la cartella di output di compilazione per il progetto CustomActionProjectItem contenga il file CustomActionProjectItem.  
  
     Per impostazione predefinita, la cartella di output di compilazione è il... nella cartella \bin\Debug sotto la cartella che contiene il progetto CustomActionProjectItem.  
  
## <a name="testing-the-project-item"></a>L'elemento del progetto di test  
 A questo punto si è pronti per l'elemento del progetto di test. Innanzitutto, avviare il debug della soluzione CustomActionProjectItem nell'istanza sperimentale di Visual Studio. Testare quindi la **l'azione personalizzata** elemento in un progetto di SharePoint nell'istanza sperimentale di Visual Studio. Infine, compilare ed eseguire il progetto di SharePoint per verificare che l'azione personalizzata funzioni come previsto.  
  
#### <a name="to-start-debugging-the-solution"></a>Per avviare il debug della soluzione  
  
1.  Riavviare Visual Studio con credenziali amministrative e quindi aprire la soluzione CustomActionProjectItem.  
  
2.  Aprire il file di codice CustomAction e quindi aggiungere un punto di interruzione sulla prima riga di codice il `InitializeType` metodo.  
  
3.  Scegliere il **F5** tasto per avviare il debug.  
  
     Visual Studio installa l'estensione %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom Item\1.0 di progetto di azione e viene avviata un'istanza sperimentale di Visual Studio. L'elemento del progetto verrà testato in questa istanza di Visual Studio.  
  
#### <a name="to-test-the-project-item-in-visual-studio"></a>Per testare l'elemento del progetto in Visual Studio  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **File**, **New**, **progetto**.  
  
2.  Espandere **Visual c#** o **Visual Basic** (a seconda del linguaggio che supporta il modello di elemento), espandere **SharePoint**, quindi scegliere il **2010**  nodo.  
  
3.  Nell'elenco dei modelli di progetto, scegliere **progetto SharePoint 2010**.  
  
4.  Nel **nome** immettere **CustomActionTest**, quindi scegliere il **OK** pulsante.  
  
5.  Nel **Personalizzazione guidata SharePoint**, immettere l'URL del sito che si desidera utilizzare per il debug e quindi scegliere il **fine** pulsante.  
  
6.  In **Esplora**, aprire il menu di scelta rapida per il nodo del progetto, scegliere **Aggiungi**, quindi scegliere **nuovo elemento**.  
  
7.  Nel **Aggiungi nuovo elemento** finestra di dialogo scegliere la **2010** nodo sotto il **SharePoint** nodo.  
  
     Verificare che il **l'azione personalizzata** elemento viene visualizzato nell'elenco di elementi di progetto.  
  
8.  Scegliere il **l'azione personalizzata** elemento e quindi scegliere il **Aggiungi** pulsante.  
  
     Visual Studio aggiunge un elemento denominato **CustomAction1** al progetto e apre il file Elements.xml file nell'editor.  
  
9. Verificare che il codice in altra istanza di Visual Studio si arresta nel punto di interruzione impostato precedentemente nel `InitializeType` metodo.  
  
10. Scegliere il **F5** tasto per continuare il debug del progetto.  
  
11. Nell'istanza sperimentale di Visual Studio, in **Esplora soluzioni**, aprire il menu di scelta rapida per il **CustomAction1** nodo, quindi scegliere **azione personalizzata progettazione**.  
  
12. Verificare che viene visualizzata una finestra di messaggio e quindi scegliere il **OK** pulsante.  
  
     È possibile utilizzare questo menu di scelta rapida per fornire opzioni aggiuntive o i comandi per gli sviluppatori, ad esempio la visualizzazione di una finestra di progettazione per l'azione personalizzata.  
  
13. Nella barra dei menu, scegliere **vista**, **Output**.  
  
     Il **Output** verrà visualizzata la finestra.  
  
14. In **Esplora**, aprire il menu di scelta rapida per il **CustomAction1** elemento e quindi modificare il nome su **MyCustomAction**.  
  
     Nel **Output** verrà visualizzata la finestra, un messaggio di conferma. Questo messaggio viene scritto dal <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> definito nel gestore dell'evento di `CustomActionProjectItemTypeProvider` classe. È possibile gestire questo evento e altri eventi di elemento di progetto per implementare il comportamento personalizzato quando lo sviluppatore modifica l'elemento del progetto.  
  
#### <a name="to-test-the-custom-action-in-sharepoint"></a>Per testare l'azione personalizzata in SharePoint  
  
1.  Nell'istanza sperimentale di Visual Studio, aprire il file Elements.xml che è un figlio di **MyCustomAction** elemento del progetto.  
  
2.  Nel file Elements.xml, apportare le modifiche seguenti e quindi salvare il file:  
  
    -   Nel `CustomAction` elemento, impostare il `Id` dell'attributo a un GUID o un'altra stringa univoca come illustrato nell'esempio seguente:  
  
        ```  
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"  
        ```  
  
    -   Nel `CustomAction` elemento, impostare il `Title` attributo come illustrato nell'esempio seguente:  
  
        ```  
        Title="SharePoint Developer Center"  
        ```  
  
    -   Nel `CustomAction` elemento, impostare il `Description` attributo come illustrato nell'esempio seguente:  
  
        ```  
        Description="Opens the SharePoint Developer Center Web site."  
        ```  
  
    -   Nel `UrlAction` elemento, impostare il `Url` attributo come illustrato nell'esempio seguente:  
  
        ```  
        Url="http://msdn.microsoft.com/sharepoint/default.aspx"  
        ```  
  
3.  Premere il tasto F5.  
  
     L'azione personalizzata viene incluso nel pacchetto distribuito nel sito di SharePoint specificato nella **URL del sito** proprietà del progetto. Nel browser viene visualizzata la pagina predefinita del sito.  
  
    > [!NOTE]  
    >  Se il **debug degli Script disabilitato** viene visualizzata la finestra di dialogo, scegliere il **Sì** per continuare il debug del progetto.  
  
4.  Nel **Azioni sito** menu, scegliere **Centro per sviluppatori SharePoint**, verificare che il browser apre http://msdn.microsoft.com/sharepoint/default.aspx il sito Web e quindi chiudere il browser web.  
  
## <a name="cleaning-up-the-development-computer"></a>Pulizia dei Computer di sviluppo  
 Dopo aver completato l'elemento del progetto di test, rimuovere il modello di elemento di progetto dall'istanza sperimentale di Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Per pulire il computer di sviluppo  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **strumenti**, **estensioni e aggiornamenti**.  
  
     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.  
  
2.  Nell'elenco di estensioni, scegliere **elemento di progetto azione personalizzata**, quindi scegliere il **Disinstalla** pulsante.  
  
3.  Nella finestra di dialogo visualizzata, scegliere il **Sì** pulsante per confermare che si desidera disinstallare l'estensione.  
  
4.  Scegliere il **Riavvia ora** per completare la disinstallazione.  
  
5.  Chiudere l'istanza sperimentale di Visual Studio sia l'istanza in cui la soluzione CustomActionProjectItem è aperta.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Dopo aver completato questa procedura dettagliata, è possibile aggiungere una procedura guidata per il modello di elemento. Quando un utente aggiunge un elemento di progetto azione personalizzata a un progetto SharePoint, la procedura guidata raccoglie informazioni sull'azione (ad esempio la posizione e l'URL a cui passare quando viene scelto l'azione) e aggiunge al file Elements.xml nel nuovo elemento di progetto. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Definizione di tipi di elemento di progetto SharePoint personalizzato](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creazione di modelli di progetto e modelli di elemento per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Utilizzo del servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Riferimenti allo schema dei modelli di Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Image Editor for Icons](/cpp/windows/image-editor-for-icons)  (Editor di immagini per icone)  
 [Creazione di un'icona o altra immagine &#40; Editor di immagini per le icone &#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  