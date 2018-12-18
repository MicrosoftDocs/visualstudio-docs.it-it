---
title: 'Procedura dettagliata: Creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 1 | Documenti Microsoft'
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
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2266fc715322c024625e5f52f83805d0d582416b
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1"></a>Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 1
  I progetti SharePoint sono contenitori per una o più elementi di progetto SharePoint. È possibile estendere il sistema di progetto SharePoint in Visual Studio mediante la creazione di propri tipi di elemento di progetto SharePoint e quindi associarle a un modello di progetto. In questa procedura dettagliata, si definirà un tipo di elemento di progetto per la creazione di una colonna del sito e quindi si creerà un modello di progetto che può essere usato per creare un nuovo progetto che contiene un elemento di progetto colonna del sito.  
  
 In questa procedura dettagliata vengono descritte le attività seguenti:  
  
-   Creazione di un'estensione di Visual Studio che definisce un nuovo tipo di elemento di progetto SharePoint per una colonna del sito. Il tipo di elemento di progetto include una semplice proprietà personalizzata che viene visualizzato nel **proprietà** finestra.  
  
-   Creazione di un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] modello di progetto per l'elemento del progetto.  
  
-   La creazione di un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto Extension (VSIX) per distribuire il modello di progetto e l'assembly dell'estensione.  
  
-   Il debug e test dell'elemento di progetto.  
  
 Si tratta di una procedura dettagliata autonoma. Dopo aver completato questa procedura dettagliata, è possibile migliorare l'elemento del progetto mediante l'aggiunta di una procedura guidata per il modello di progetto. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
> [!NOTE]  
>  È possibile scaricare un esempio che contiene i progetti completati, codice e altri file per questa procedura dettagliata dal seguente percorso: [http://go.microsoft.com/fwlink/?LinkId=191369](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Sono necessari i seguenti componenti nel computer di sviluppo per completare questa procedura dettagliata:  
  
-   Le edizioni supportate di Microsoft Windows, SharePoint e [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Per ulteriori informazioni, vedere [requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Oggetto [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Questa procedura dettagliata Usa il **progetto VSIX** modello nel SDK per creare un pacchetto VSIX per distribuire l'elemento del progetto. Per ulteriori informazioni, vedere [estensione degli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Il concetto seguente è utile, ma non obbligatori, completare la procedura dettagliata:  
  
-   Colonne del sito di SharePoint. Per ulteriori informazioni, vedere [colonne](http://go.microsoft.com/fwlink/?LinkId=183547).  
  
-   Modelli di progetto in Visual Studio. Per altre informazioni, vedere [Creazione di modelli di progetti e di elementi](/visualstudio/ide/creating-project-and-item-templates).  
  
## <a name="creating-the-projects"></a>Creazione dei progetti  
 Per completare questa procedura dettagliata, è necessario creare tre progetti:  
  
-   Un progetto VSIX. Questo progetto crea il pacchetto VSIX per distribuire l'elemento di progetto colonna del sito e il modello di progetto.  
  
-   Un progetto di modello di progetto. Questo progetto crea un modello di progetto che può essere usato per creare un nuovo progetto di SharePoint che contiene l'elemento di progetto colonna del sito.  
  
-   Un progetto libreria di classi. Il progetto che implementa un'estensione di Visual Studio che definisce il comportamento dell'elemento di progetto colonna del sito.  
  
 Avviare la procedura dettagliata creando i progetti.  
  
#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
3.  Nella parte superiore del **nuovo progetto** finestra di dialogo, assicurarsi che **.NET Framework 4.5** viene scelto nell'elenco delle versioni di .NET Framework.  
  
4.  Espandere il **Visual Basic** o **Visual c#** nodi, quindi scegliere il **estendibilità** nodo.  
  
    > [!NOTE]  
    >  Il **estendibilità** nodo è disponibile solo se si installa Visual Studio SDK. Per ulteriori informazioni, vedere la sezione Prerequisiti in questo argomento.  
  
5.  Nell'elenco dei modelli di progetto, scegliere **progetto VSIX**.  
  
6.  Nel **nome** immettere **SiteColumnProjectItem**, quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Aggiunge il **SiteColumnProjectItem** progetto **Esplora**.  
  
#### <a name="to-create-the-project-template-project"></a>Per creare il progetto di modello di progetto  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il nodo della soluzione, scegliere **Aggiungi**, quindi scegliere **nuovo progetto**.  
  
2.  Nella parte superiore del **nuovo progetto** finestra di dialogo, assicurarsi che **.NET Framework 4.5** viene scelto nell'elenco delle versioni di .NET Framework.  
  
3.  Espandere il **Visual c#** o **Visual Basic** nodo, quindi scegliere il **estendibilità** nodo.  
  
4.  Nell'elenco dei modelli di progetto, scegliere il **il modello di progetto c#** o **il modello di progetto di Visual Basic** modello.  
  
5.  Nel **nome** immettere **SiteColumnProjectTemplate**, quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Aggiunge il **SiteColumnProjectTemplate** progetto alla soluzione.  
  
6.  Eliminare il file di codice Class1 dal progetto.  
  
7.  Se è stato creato un progetto Visual Basic, eliminare anche i file seguenti dal progetto:  
  
    -   MyApplication.Designer.vb  
  
    -   MyApplication.myapp  
  
    -   Resources.Designer.vb  
  
    -   Resources. resx  
  
    -   Settings.Designer.vb  
  
    -   Settings. Settings  
  
#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il nodo della soluzione, scegliere **Aggiungi**, quindi scegliere **nuovo progetto**.  
  
2.  Nella parte superiore del **nuovo progetto** finestra di dialogo, assicurarsi che **.NET Framework 4.5** viene scelto nell'elenco delle versioni di .NET Framework.  
  
3.  Espandere il **Visual c#** o **Visual Basic** nodi, scegliere il **Windows** nodo, quindi scegliere il **libreria di classi** modello.  
  
4.  Nel **nome** immettere **ProjectItemTypeDefinition** e quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Aggiunge il **ProjectItemTypeDefinition** progetto alla soluzione e apre il file di codice predefinito Class1.  
  
5.  Eliminare il file di codice Class1 dal progetto.  
  
## <a name="configuring-the-extension-project"></a>Configurazione del progetto di estensione  
 Aggiungere i file di codice e i riferimenti ad assembly per configurare il progetto di estensione.  
  
#### <a name="to-configure-the-project"></a>Per configurare il progetto  
  
1.  Nel progetto ProjectItemTypeDefinition, aggiungere un file di codice denominato **SiteColumnProjectItemTypeProvider**.  
  
2.  Nella barra dei menu scegliere **Progetto**, **Aggiungi riferimento**.  
  
3.  Nel **gestione riferimenti - ProjectItemTypeDefinition** finestra di dialogo espandere il **assembly** nodo, scegliere il **Framework** nodo e quindi selezionare il Casella di controllo System.  
  
4.  Scegliere il **estensioni** nodo, selezionare la casella di controllo accanto all'assembly Microsoft.VisualStudio.SharePoint e quindi scegliere il **OK** pulsante.  
  
## <a name="defining-the-new-sharepoint-project-item-type"></a>Definire il nuovo tipo di elemento di progetto SharePoint  
 Creare una classe che implementa il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfaccia per definire il comportamento del nuovo tipo di elemento di progetto. Implementare questa interfaccia ogni volta che si desidera definire un nuovo tipo di elemento di progetto.  
  
#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Per definire il nuovo tipo di elemento di progetto SharePoint  
  
1.  Nel **SiteColumnProjectItemTypeProvider** file di codice, sostituire il codice predefinito con il codice seguente e quindi salvare il file.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]  
  
## <a name="creating-a-visual-studio-project-template"></a>Creazione di un modello di progetto di Visual Studio  
 La creazione di un modello di progetto, si consentono ad altri sviluppatori di creare progetti di SharePoint che contengono elementi di progetto colonna del sito. Un modello di progetto SharePoint include i file necessari per tutti i progetti in Visual Studio, ad esempio con estensione csproj o vbproj e file. vstemplate e i file specifici per i progetti SharePoint. Per ulteriori informazioni, vedere [la creazione di modelli di elemento e i modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 In questa procedura creare un progetto SharePoint vuoto per generare i file che sono specifici dei progetti SharePoint. Aggiungere quindi questi file al progetto SiteColumnProjectTemplate in modo che sono stati inclusi nel modello che viene generato da questo progetto. È inoltre configurare il file di progetto SiteColumnProjectTemplate per specificare dove verrà visualizzato il modello di progetto di **nuovo progetto** la finestra di dialogo.  
  
#### <a name="to-create-the-files-for-the-project-template"></a>Per creare i file per il modello di progetto  
  
1.  Avviare una seconda istanza di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con credenziali amministrative.  
  
2.  Creare un progetto di SharePoint 2010 che è denominato **BaseSharePointProject**.  
  
    > [!IMPORTANT]  
    >  Nel **Personalizzazione guidata SharePoint**, non selezionare la **Distribuisci come soluzione farm** pulsante di opzione.  
  
3.  Aggiungere un elemento vuoto al progetto e quindi assegnare un nome elemento **Field1**.  
  
4.  Salvare il progetto e quindi chiudere la seconda istanza di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
5.  Nell'istanza di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con la soluzione SiteColumnProjectItem, in **Esplora**, aprire il menu di scelta rapida per il **SiteColumnProjectTemplate** nodo del progetto, scegliere  **Aggiungere**, quindi scegliere **elemento esistente**.  
  
6.  Nel **Aggiungi elemento esistente** la finestra di dialogo, aprire l'elenco di estensioni di file e quindi scegliere **tutti i file (\*.\*)** .  
  
7.  Nella directory che contiene il progetto BaseSharePointProject, selezionare il file snk e quindi scegliere il **Aggiungi** pulsante.  
  
    > [!NOTE]  
    >  In questa procedura dettagliata, il modello di progetto che crei utilizza lo stesso file key.snk per firmare ogni progetto creato utilizzando il modello. Per informazioni su come espandere questo esempio per creare un file key.snk diverso per ogni istanza del progetto, vedere [procedura dettagliata: creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
8.  Ripetere i passaggi da 5 a 8 per aggiungere i file seguenti dalle sottocartelle specificate nella directory BaseSharePointProject:  
  
    -   \Field1\Elements.Xml  
  
    -   \Field1\SharePointProjectItem.spdata  
  
    -   \Features\Feature1\Feature1.feature  
  
    -   \Features\Feature1\Feature1.Template.Xml  
  
    -   \Package\Package.package  
  
    -   \Package\Package.Template.Xml  
  
     Aggiungere questi file direttamente al progetto SiteColumnProjectTemplate. non ricreare le sottocartelle Field1, funzionalità o pacchetto nel progetto. Per ulteriori informazioni su questi file, vedere [la creazione di modelli di elemento e i modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>Per configurare come gli sviluppatori di individuare il modello di progetto nella finestra di dialogo Nuovo progetto  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il **SiteColumnProjectTemplate** nodo del progetto e quindi scegliere **Scarica progetto**. Se viene chiesto di salvare le modifiche ai file, scegliere il **Sì** pulsante.  
  
2.  Aprire il menu di scelta rapida per il **SiteColumnProjectTemplate** nodo nuovo, quindi scegliere **Modifica SiteColumnProjectTemplate. csproj** o **Modifica SiteColumnProjectTemplate**.  
  
3.  Nel file di progetto, individuare la seguente `VSTemplate` elemento.  
  
    ```  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
    ```  
  
4.  Sostituire l'elemento con il seguente codice XML.  
  
    ```  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     Il `OutputSubPath` elemento specifica le cartelle aggiuntive nel percorso in cui viene creato il modello di progetto quando si compila il progetto. Le cartelle specificate assicurarsi che il modello di progetto saranno disponibile solo quando hanno aperto il **nuovo progetto** finestra di dialogo espandere il **SharePoint** nodo e quindi scegliere il **2010**  nodo.  
  
5.  Salvare e chiudere il file.  
  
6.  In **Esplora**, aprire il menu di scelta rapida per il **SiteColumnProjectTemplate** del progetto e quindi scegliere **Ricarica progetto**.  
  
## <a name="editing-the-project-template-files"></a>Modifica dei file di modello di progetto  
 Nel progetto SiteColumnProjectTemplate, modificare i file seguenti per definire il comportamento del modello di progetto:  
  
-   File AssemblyInfo.cs o AssemblyInfo. vb  
  
-   Elements  
  
-   SharePointProjectItem  
  
-   Feature1. feature  
  
-   Package. package  
  
-   SiteColumnProjectTemplate  
  
-   Csproj o ProjectTemplate  
  
 Nelle procedure seguenti, aggiungerai parametri sostituibili per alcuni di questi file. Un parametro sostituibile è un token che inizia e termina con il segno di dollaro ($). Quando un utente utilizza questo modello di progetto per creare un progetto, Visual Studio sostituisce automaticamente questi parametri nel nuovo progetto con valori specifici. Per ulteriori informazioni, vedere [parametri sostituibili](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>Per modificare il file AssemblyInfo.cs o AssemblyInfo. vb.  
  
1.  Nel progetto SiteColumnProjectTemplate, aprire il file AssemblyInfo.cs o AssemblyInfo. vb e quindi aggiungere l'istruzione seguente all'inizio di esso:  
  
    ```vb  
    Imports System.Security  
    ```  
  
    ```csharp  
    using System.Security;  
    ```  
  
     Quando il **soluzione creata mediante sandbox** di un progetto SharePoint è impostata su **True**, Visual Studio aggiunge il <xref:System.Security.AllowPartiallyTrustedCallersAttribute> al file di codice AssemblyInfo. Tuttavia, non importa i file di codice AssemblyInfo nel modello di progetto di <xref:System.Security> dello spazio dei nomi per impostazione predefinita. È necessario aggiungere questo **utilizzando** o **importazioni** per impedire errori di compilazione.  
  
2.  Salvare e chiudere il file.  
  
#### <a name="to-edit-the-elementsxml-file"></a>Per modificare il file Elements.xml  
  
1.  Nel progetto SiteColumnProjectTemplate, sostituire il contenuto del file Elements.xml con il seguente codice XML.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
          Name="$safeprojectname$"   
          DisplayName="$projectname$"   
          Type="Text"   
          Group="Custom Columns">  
      </Field>  
    </Elements>  
    ```  
  
     Il nuovo XML aggiunge un `Field` elemento che definisce il nome della colonna del sito, il tipo di base e il gruppo in cui elencare la colonna del sito nella raccolta. Per ulteriori informazioni sul contenuto di questo file, vedere [Schema di definizione del campo](http://go.microsoft.com/fwlink/?LinkId=184290).  
  
2.  Salvare e chiudere il file.  
  
#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>Per modificare il file SharePointProjectItem  
  
1.  Nel progetto SiteColumnProjectTemplate, sostituire il contenuto del file SharePointProjectItem con il seguente codice XML.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"   
                 xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />  
      </Files>   
    </ProjectItem>  
    ```  
  
     Il nuovo XML apporta le modifiche seguenti al file:  
  
    -   Modifiche di `Type` attributo del `ProjectItem` elemento per la stessa stringa passata al <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> nella definizione di elemento di progetto (la `SiteColumnProjectItemTypeProvider` classe creata precedentemente in questa procedura dettagliata).  
  
    -   Rimuove il `SupportedTrustLevels` e `SupportedDeploymentScopes` gli attributi dal `ProjectItem` elemento. I valori degli attributi non sono necessari perché il livello di attendibilità e gli ambiti di distribuzione sono specificati nella `SiteColumnProjectItemTypeProvider` classe nel progetto ProjectItemTypeDefinition.  
  
     Per ulteriori informazioni sul contenuto dei file spdata, vedere [riferimenti dello Schema di elemento di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).  
  
2.  Salvare e chiudere il file.  
  
#### <a name="to-edit-the-feature1feature-file"></a>Per modificare il file Feature1. feature  
  
1.  Nel progetto SiteColumnProjectTemplate, sostituire il contenuto del file Feature1. feature con il seguente codice XML.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <feature xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="$guid4$" featureId="$guid4$"   
             imageUrl="" solutionId="00000000-0000-0000-0000-000000000000" title="Site Column Feature1" version=""  
             deploymentPath="$SharePoint.Project.FileNameWithoutExtension$_$SharePoint.Feature.FileNameWithoutExtension$"  
             xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/FeatureModel">  
      <projectItems>  
        <projectItemReference itemId="$guid2$" />  
      </projectItems>  
    </feature>  
    ```  
  
     Il nuovo XML apporta le modifiche seguenti al file:  
  
    -   Modifica i valori del `Id` e `featureId` gli attributi del `feature` elemento `$guid4$`.  
  
    -   Modifica i valori del `itemId` attributo del `projectItemReference` elemento `$guid2$`.  
  
     Per ulteriori informazioni sui file con estensione feature, vedere [la creazione di modelli di elemento e i modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
2.  Salvare e chiudere il file.  
  
#### <a name="to-edit-the-packagepackage-file"></a>Per modificare il file package. package  
  
1.  Nel progetto SiteColumnProjectTemplate, sostituire il contenuto del file package. package con il seguente codice XML.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"   
             Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"   
             xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">  
      <features>  
        <featureReference itemId="$guid4$" />  
      </features>  
    </package>  
    ```  
  
     Il nuovo XML apporta le modifiche seguenti al file:  
  
    -   Modifica i valori del `Id` e `solutionId` gli attributi del `package` elemento `$guid3$`.  
  
    -   Modifica i valori del `itemId` attributo del `featureReference` elemento `$guid4$`.  
  
     Per ulteriori informazioni sui file del pacchetto, vedere [la creazione di modelli di elemento e i modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
2.  Salvare e chiudere il file.  
  
#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>Per modificare il file SiteColumnProjectTemplate  
  
1.  Nel progetto SiteColumnProjectTemplate, sostituire il contenuto del file SiteColumnProjectTemplate con una delle sezioni di codice XML seguente.  
  
    -   Se si sta creando un modello di progetto Visual c#, utilizzare il seguente codice XML.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
      <TemplateData>  
        <Name>Site Column</Name>  
        <Description>Creates a new site column in SharePoint</Description>  
        <FrameworkVersion>3.5</FrameworkVersion>  
        <ProjectType>CSharp</ProjectType>  
        <CreateNewFolder>true</CreateNewFolder>  
        <CreateInPlace>true</CreateInPlace>  
        <ProvideDefaultName>true</ProvideDefaultName>  
        <DefaultName>SiteColumn</DefaultName>  
        <LocationField>Enabled</LocationField>  
        <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
        <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <Icon>SiteColumnProjectTemplate.ico</Icon>  
        <SortOrder>1000</SortOrder>  
      </TemplateData>  
      <TemplateContent>  
        <Project TargetFileName="SharePointProject1.csproj" File="ProjectTemplate.csproj" ReplaceParameters="true">  
          <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
        </Project>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
    -   Se si sta creando un modello di progetto Visual Basic, utilizzare il seguente codice XML.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
      <TemplateData>  
        <Name>Site Column</Name>  
        <Description>Creates a new site column in SharePoint</Description>  
        <FrameworkVersion>3.5</FrameworkVersion>  
        <ProjectType>VisualBasic</ProjectType>  
        <CreateNewFolder>true</CreateNewFolder>  
        <CreateInPlace>true</CreateInPlace>  
        <ProvideDefaultName>true</ProvideDefaultName>  
        <DefaultName>SiteColumn</DefaultName>  
        <LocationField>Enabled</LocationField>  
        <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
        <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <Icon>SiteColumnProjectTemplate.ico</Icon>  
        <SortOrder>1000</SortOrder>  
      </TemplateData>  
      <TemplateContent>  
        <Project TargetFileName="SharePointProject1.vbproj" File="ProjectTemplate.vbproj" ReplaceParameters="true">  
          <ProjectItem ReplaceParameters="true" TargetFileName="My Project\AssemblyInfo.vb">AssemblyInfo.vb</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
        </Project>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
     Il nuovo XML apporta le modifiche seguenti al file:  
  
    -   Imposta il `Name` elemento sul valore **colonna del sito**. (Questo nome viene visualizzato nel **nuovo progetto** la finestra di dialogo).  
  
    -   Aggiunge `ProjectItem` elementi per ogni filethat del inclusi in ogni istanza del progetto.  
  
    -   Usa lo spazio dei nomi "http://schemas.microsoft.com/developer/vstemplate/2005". Altri file di progetto in questa soluzione usano lo spazio dei nomi "http://schemas.microsoft.com/developer/msbuild/2003". Pertanto, verranno generati messaggi di avviso di XML schema, ma è possibile ignorare tali in questa procedura dettagliata.  
  
     Per ulteriori informazioni sul contenuto dei file con estensione vstemplate, vedere [riferimenti dello Schema dei modelli di Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference).  
  
2.  Salvare e chiudere il file.  
  
#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>Per modificare il file csproj o ProjectTemplate  
  
1.  Nel progetto SiteColumnProjectTemplate, sostituire il contenuto del file csproj o ProjectTemplate file con una delle sezioni di codice XML seguente.  
  
    -   Se si sta creando un modello di progetto Visual c#, utilizzare il seguente codice XML.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <SchemaVersion>2.0</SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <AppDesignerFolder>Properties</AppDesignerFolder>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{14822709-B5A1-4724-98CA-57A101D1B079};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineConstants>DEBUG;TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <DefineConstants>TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Web" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="Properties\AssemblyInfo.cs" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
    1.  Se si sta creando un modello di progetto Visual Basic, utilizzare il seguente codice XML.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <ProductVersion>  
        </ProductVersion>  
        <SchemaVersion>  
        </SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{D59BE175-2ED0-4C54-BE3D-CDAA9F3214C8};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>  
        <OptionExplicit>On</OptionExplicit>  
        <OptionCompare>Binary</OptionCompare>  
        <OptionStrict>Off</OptionStrict>  
        <OptionInfer>On</OptionInfer>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <OutputPath>bin\Debug\</OutputPath>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <DefineDebug>false</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Import Include="Microsoft.VisualBasic" />  
        <Import Include="System" />  
        <Import Include="System.Collections" />  
        <Import Include="System.Collections.Generic" />  
        <Import Include="System.Data" />  
        <Import Include="System.Diagnostics" />  
        <Import Include="System.Linq" />  
        <Import Include="System.Xml.Linq" />  
        <Import Include="Microsoft.SharePoint" />  
        <Import Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="My Project\AssemblyInfo.vb" />  
      </ItemGroup>  
      <ItemGroup>  
        <AppDesigner Include="My Project\" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
     Il nuovo XML apporta le modifiche seguenti al file:  
  
    -   Usa il `TargetFrameworkVersion` elemento per specificare .NET Framework 3.5, non 4.5.  
  
    -   Aggiunge `SignAssembly` e `AssemblyOriginatorKeyFile` elementi da firmare l'output del progetto.  
  
    -   Aggiunge `Reference` elementi per l'assembly fa riferimento a utilizzate nei progetti SharePoint.  
  
    -   Aggiunge il progetto, ad esempio file Elements.xml e SharePointProjectItem elementi per ogni file predefinita.  
  
2.  Salvare e chiudere il file.  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-template"></a>Creazione di un pacchetto VSIX per distribuire il modello di progetto  
 Per distribuire l'estensione, usare il progetto VSIX nel **SiteColumnProjectItem** soluzione per creare un pacchetto VSIX. Innanzitutto, configurare il pacchetto VSIX modificando il file vsixmanifest incluso nel progetto VSIX. Quindi, creare il pacchetto VSIX per la compilazione della soluzione.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Per configurare e creare il pacchetto VSIX  
  
1.  In **Esplora**nella **SiteColumnProjectItem** del progetto, aprire il file vsixmanifest nell'editor del manifesto.  
  
     Il file vsixmanifest è la base per il file extension vsixmanifest che richiedono tutti i pacchetti VSIX. Per ulteriori informazioni su questo file, vedere [riferimento 1.0 dello Schema di estensione VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Nel **Product Name** immettere **colonna del sito**.  
  
3.  Nel **autore** immettere **Contoso**.  
  
4.  Nel **descrizione** immettere **progetto SharePoint per la creazione di colonne del sito**.  
  
5.  Scegliere il **asset** scheda e quindi scegliere il **New** pulsante.  
  
     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.  
  
6.  Nel **tipo** scegliere **Microsoft.VisualStudio.ProjectTemplate**.  
  
    > [!NOTE]  
    >  Questo valore corrisponde al `ProjectTemplate` elemento nel file Extension. vsixmanifest. Questo elemento identifica la sottocartella nel pacchetto VSIX che contiene il modello di progetto. Per ulteriori informazioni, vedere [elemento ProjectTemplate (schema VSX)](http://msdn.microsoft.com/en-us/87add64c-9dcd-495f-8815-209dab182cb1).  
  
7.  Nel **origine** scegliere **un progetto nella soluzione corrente**.  
  
8.  Nel **progetto** elenco e scegliere **SiteColumnProjectTemplate**, quindi scegliere il **OK** pulsante.  
  
9. Scegliere il **New** nuovamente clic sul pulsante.  
  
     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.  
  
10. Nel **tipo** scegliere **MEFComponent**.  
  
    > [!NOTE]  
    >  Questo valore corrisponde al `MefComponent` elemento nel file Extension. vsixmanifest. Questo elemento specifica il nome di un assembly di estensione nel pacchetto VSIX. Per ulteriori informazioni, vedere [elemento MEFComponent (schema VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
11. Nel **origine** scegliere **un progetto nella soluzione corrente**.  
  
12. Nel **progetto** scegliere **ProjectItemTypeDefinition**, quindi scegliere il **OK** pulsante.  
  
13. Nella barra dei menu, scegliere **compilare**, **Compila soluzione**, quindi assicurarsi che il progetto venga compilato senza errori.  
  
## <a name="testing-the-project-template"></a>Il modello di progetto di test  
 A questo punto si è pronti testare il modello di progetto. Innanzitutto, avviare il debug della soluzione SiteColumnProjectItem nell'istanza sperimentale di Visual Studio. Testare quindi la **colonna del sito** progetto nell'istanza sperimentale di Visual Studio. Infine, compilare ed eseguire il progetto di SharePoint per verificare che la colonna del sito funzioni come previsto.  
  
#### <a name="to-start-debugging-the-solution"></a>Per avviare il debug della soluzione  
  
1.  Riavviare Visual Studio con credenziali amministrative e quindi aprire la soluzione SiteColumnProjectItem.  
  
2.  
  
3.  Nel file di codice SiteColumnProjectItemTypeProvider, aggiungere un punto di interruzione sulla prima riga di codice nel `InitializeType` (metodo), quindi scegliere il **F5** tasto per avviare il debug.  
  
     Visual Studio installa l'estensione in %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Site Column\1.0 e avvia un'istanza sperimentale di Visual Studio. Si testerà l'elemento del progetto in questa istanza di Visual Studio.  
  
#### <a name="to-test-the-project-in-visual-studio"></a>Per testare il progetto in Visual Studio  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **File**, **New**, **progetto**.  
  
2.  Espandere il **Visual c#** o **Visual Basic** nodo (a seconda del linguaggio che supporta il modello di progetto), espandere il **SharePoint** nodo, quindi scegliere il **2010** nodo.  
  
3.  Nell'elenco dei modelli di progetto, scegliere il **colonna del sito** modello.  
  
4.  Nel **nome** immettere **SiteColumnTest** e quindi scegliere il **OK** pulsante.  
  
     In **Esplora**, verrà visualizzato un nuovo progetto con un elemento di progetto denominato **Field1**.  
  
5.  Verificare che il codice in altra istanza di Visual Studio si arresta nel punto di interruzione impostato precedentemente nel `InitializeType` (metodo), quindi scegliere il **F5** tasto per continuare il debug del progetto.  
  
6.  In **Esplora**, scegliere il **Field1** nodo, quindi scegliere il **F4** chiave.  
  
     Il **proprietà** verrà visualizzata la finestra.  
  
7.  Nell'elenco, verificare che la proprietà **proprietà esempio** viene visualizzato.  
  
#### <a name="to-test-the-site-column-in-sharepoint"></a>Per testare la colonna del sito in SharePoint  
  
1.  In **Esplora**, scegliere il **SiteColumnTest** nodo.  
  
2.  Nel **proprietà** nella casella di testo accanto alla finestra di **URL del sito** proprietà, immettere **http://localhost**.  
  
     Questo passaggio consente di specificare il sito di SharePoint locale nel computer di sviluppo che si desidera utilizzare per il debug.  
  
    > [!NOTE]  
    >  Il **URL del sito** proprietà è vuota per impostazione predefinita, poiché il modello di progetto colonna del sito non offre una procedura guidata per la raccolta di questo valore quando viene creato il progetto. Per informazioni su come aggiungere una procedura guidata che richiede lo sviluppatore per questo valore e quindi configura questa proprietà nel nuovo progetto, vedere [procedura dettagliata: creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
3.  Premere **F5**.  
  
     La colonna del sito è incluso nel pacchetto e distribuita nel sito di SharePoint specificato nella **URL del sito** proprietà del progetto. Nel browser viene visualizzata la pagina predefinita del sito.  
  
    > [!NOTE]  
    >  Se il **debug degli Script disabilitato** viene visualizzata la finestra di dialogo, scegliere il **Sì** per continuare il debug del progetto.  
  
4.  Nel **Azioni sito** menu, scegliere **Impostazioni sito**.  
  
5.  Nel **Impostazioni sito** nella pagina di **raccolte** scegliere il **colonne sito** collegamento.  
  
6.  Nell'elenco delle colonne del sito, verificare che un **colonne personalizzate** gruppo contiene una colonna denominata **SiteColumnTest**.  
  
7.  Chiudere il Web browser.  
  
## <a name="cleaning-up-the-development-computer"></a>Pulizia dei Computer di sviluppo  
 Dopo aver completato i test del progetto, rimuovere il modello di progetto dall'istanza sperimentale di Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Per pulire il computer di sviluppo  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **strumenti**, **estensioni e aggiornamenti**.  
  
     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.  
  
2.  Nell'elenco di estensioni, scegliere il **colonna del sito** estensione, quindi scegliere il **Disinstalla** pulsante.  
  
3.  Nella finestra di dialogo visualizzata, scegliere il **Sì** pulsante per confermare che si desidera disinstallare l'estensione.  
  
4.  Scegliere il **Chiudi** per completare la disinstallazione.  
  
5.  Chiudere entrambe le istanze di Visual Studio (l'istanza sperimentale e l'istanza di Visual Studio in cui la soluzione SiteColumnProjectItem è aperta).  
  
## <a name="next-steps"></a>Passaggi successivi  
 Dopo aver completato questa procedura dettagliata, è possibile aggiungere una procedura guidata per il modello di progetto. Quando un utente crea un progetto di colonna del sito, la procedura guidata viene richiesto all'utente per l'URL del sito da utilizzare per il debug e se la nuova soluzione è in modalità sandbox, e la procedura guidata consente di configurare il nuovo progetto con queste informazioni. Inoltre, la procedura guidata raccoglie informazioni sulla colonna (ad esempio il tipo di base e il gruppo in cui elencare la colonna nella raccolta di colonne del sito) e aggiunge al file Elements.xml nel nuovo progetto. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Definizione di tipi di elemento di progetto SharePoint personalizzato](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creazione di modelli di progetto e modelli di elemento per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Salvataggio dei dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Associazione di dati personalizzati alle estensioni degli strumenti di SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  