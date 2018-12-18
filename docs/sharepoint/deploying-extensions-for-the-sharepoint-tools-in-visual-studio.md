---
title: Distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio | Documenti Microsoft
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
helpviewer_keywords: SharePoint development in Visual Studio, deploying extensions
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 80cc884e45d9db10f6552fa44e611e87b7b4f801
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="deploying-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio
  Per distribuire un'estensione degli strumenti di SharePoint, creare un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto extension (VSIX) che contiene l'assembly dell'estensione e qualsiasi altro file che si desiderano distribuire con l'estensione. Un pacchetto VSIX è un file compresso che è conforme allo standard Open Packaging Conventions (OPC). Pacchetti VSIX hanno l'estensione VSIX.  
  
 Dopo aver creato un pacchetto VSIX, altri utenti possono eseguire il file VSIX per installare l'estensione. Quando un utente installa l'estensione, tutti i file vengono installati nella cartella %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions. Per distribuire l'estensione, è possibile caricare il pacchetto VSIX per la [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) sito Web oppure è possibile distribuire il pacchetto ai clienti con altri mezzi, ad esempio il pacchetto in una condivisione di rete o un altro sito Web di hosting.  
  
 Per ulteriori informazioni sulla creazione di pacchetti VSIX e la distribuzione per il [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847), vedere [Shipping estensioni di Visual Studio](/visualstudio/extensibility/shipping-visual-studio-extensions).  
  
 È possibile creare un pacchetto VSIX usando il **progetto VSIX** modello in Visual Studio o è possibile creare un pacchetto VSIX manualmente.  
  
## <a name="using-vsix-projects-to-create-vsix-packages"></a>Utilizzo di progetti VSIX per creare pacchetti VSIX  
 È possibile utilizzare il **progetto VSIX** modello fornito da Visual Studio SDK per creare pacchetti VSIX per estensioni degli strumenti di SharePoint. Utilizzo di un progetto VSIX offre diversi vantaggi rispetto creazione manuale di un pacchetto VSIX:  
  
-   Quando si compila il progetto, Visual Studio genera automaticamente il pacchetto VSIX. Attività, ad esempio aggiungendo i file di distribuzione per il pacchetto e creando il file [Content_Types] XML per il pacchetto vengono eseguite automaticamente.  
  
-   È possibile configurare il progetto VSIX per includere l'output di compilazione del progetto di estensione e altri file, ad esempio i modelli di progetto e modelli di elementi nel pacchetto VSIX.  
  
 Per ulteriori informazioni sull'utilizzo di un progetto VSIX, vedere [modello di progetto VSIX](/visualstudio/extensibility/vsix-project-template).  
  
### <a name="organizing-your-projects"></a>L'organizzazione dei progetti  
 Per impostazione predefinita, i progetti VSIX generano solo pacchetti VSIX, non gli assembly. Pertanto, in genere non si implementa un'estensione degli strumenti di SharePoint in un progetto VSIX. In genere si lavora con almeno due progetti:  
  
-   Un progetto VSIX.  
  
-   Un progetto libreria di classi che implementa l'estensione.  
  
 È anche possibile lavorare con progetti aggiuntivi per determinati tipi di estensioni:  
  
-   Un progetto libreria di classi che implementa i comandi di SharePoint che vengono utilizzati dall'estensione. Per una procedura dettagliata che illustra questo scenario, vedere [procedura dettagliata: estensione di Esplora Server per visualizzare Web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Un progetto di modello di elemento o modello di progetto che crea un modello di elemento o un modello di progetto, se l'estensione definisce un nuovo tipo di elemento di progetto SharePoint. Per una procedura dettagliata che illustra questo scenario, vedere [procedura dettagliata: creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
-   Un progetto libreria di classi che implementa una procedura guidata personalizzata per un modello di elemento o un modello di progetto, se l'estensione include un modello. Per una procedura dettagliata che illustra questo scenario, vedere [procedura dettagliata: creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
 Se si includono tutti i progetti nella stessa soluzione di Visual Studio, è possibile modificare il file vsixmanifest nel progetto VSIX per includere l'output di compilazione di progetti libreria di classi.  
  
### <a name="editing-the-vsix-manifest"></a>Modifica del manifesto VSIX  
 È necessario modificare il file vsixmanifest nel progetto VSIX per includere le voci per tutti gli elementi che si desidera includere nell'estensione. Quando si apre il file vsixmanifest dal menu di scelta rapida, il file viene visualizzato nella finestra di progettazione che fornisce un'interfaccia utente per modificare il codice XML nel file. Per ulteriori informazioni, vedere [progettazione del manifesto VSIX](/visualstudio/extensibility/vsix-manifest-designer).  
  
 È necessario aggiungere voci al file vsixmanifest per gli elementi seguenti:  
  
-   L'assembly dell'estensione.  
  
-   L'assembly che implementa i comandi di SharePoint che vengono utilizzati dall'estensione.  
  
-   Eventuali modelli di progetto o i modelli di elemento associati all'estensione.  
  
-   Creazione guidata personalizzata per un modello che è associato all'estensione.  
  
 Le procedure seguenti viene descritto come aggiungere voci al file vsixmanifest per ognuno di questi elementi.  
  
##### <a name="to-include-the-extension-assembly"></a>Per includere l'assembly dell'estensione  
  
1.  Nel progetto VSIX, aprire il menu di scelta rapida per il file vsixmanifest e quindi scegliere **aprire**.  
  
     Il file verrà aperto nella finestra di progettazione  
  
2.  Nel **asset** scheda dell'editor, scegliere il **New** pulsante.  
  
     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.  
  
3.  Nel **tipo** scegliere **MEFComponent**.  
  
4.  Nel **origine** elenco, eseguire una delle operazioni seguenti:  
  
    -   Se l'assembly dell'estensione viene compilato da un progetto che si trova nella stessa soluzione del progetto VSIX, scegliere **un progetto nella soluzione corrente**. Nel **progetto** elenco, scegliere il nome del progetto.  
  
    -   Se l'assembly dell'estensione è inclusa in un file nel progetto, scegliere **File in filesystem**. Nel **percorso** elenco, immettere il percorso completo del file di assembly di estensione o utilizzare il **Sfoglia** pulsante per individuare e selezionare il file di assembly.  
  
5.  Fare clic sul pulsante **OK** .  
  
##### <a name="to-include-a-sharepoint-command-assembly"></a>Per includere un assembly di comando di SharePoint  
  
1.  Nel progetto VSIX, aprire il menu di scelta rapida per il file vsixmanifest e quindi scegliere il **aprire** pulsante.  
  
     Il file verrà aperto nella finestra di progettazione.  
  
2.  Nel **asset** sezione dell'editor, scegliere il **New** pulsante.  
  
     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.  
  
3.  Nel **tipo** immettere **v4**.  
  
4.  Nel **origine** elenco, eseguire una delle operazioni seguenti:  
  
    -   Se l'assembly del comando viene compilato da un progetto che si trova nella stessa soluzione del progetto VSIX, scegliere **un progetto nella soluzione corrente**. Nel **progetto** elenco, scegliere il nome del progetto.  
  
    -   Se l'assembly del comando è inclusa in un file nel progetto, scegliere **File in filesystem**. Nel **percorso** elenco, immettere il percorso completo del file di assembly di estensione o utilizzare il **Sfoglia** pulsante per individuare e selezionare il file di assembly.  
  
5.  Fare clic sul pulsante **OK** .  
  
##### <a name="to-include-a-template-that-you-create"></a>Per includere un modello che si crea  
  
1.  Nel progetto VSIX, aprire il menu di scelta rapida per il file vsixmanifest e quindi scegliere il **aprire** pulsante.  
  
     Il file verrà aperto nella finestra di progettazione.  
  
2.  Nel **asset** sezione dell'editor, scegliere il **New** pulsante.  
  
     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.  
  
3.  Nel **tipo** scegliere **Microsoft.VisualStudio.ProjectTemplate** o **Microsoft.VisualStudio.ItemTemplate**.  
  
4.  Nel **origine** scegliere **un progetto nella soluzione corrente**.  
  
5.  Nel **progetto** elenco, scegliere il nome del progetto e quindi scegliere il **OK** pulsante.  
  
6.  In **Esplora**, aprire il menu di scelta rapida per il modello di progetto o modello di elemento di progetto e quindi scegliere **Scarica progetto**.  
  
7.  Aprire di nuovo il menu di scelta rapida per il nodo del progetto e quindi scegliere **modifica***NomeProgettoModello***csproj** o **modifica**  *NomeProgettoModello***vbproj**.  
  
8.  Individuare la seguente `VSTemplate` elemento nel file di progetto.  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
    ```  
  
9. Sostituire l'elemento con il seguente codice XML.  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     Il `OutputSubPath` elemento specifica le cartelle aggiuntive nel percorso in cui viene creato il modello di progetto quando si compila il progetto. Le cartelle specificate assicurarsi che il modello di elemento sarà disponibile solo quando hanno aperto il **Aggiungi nuovo progetto** finestra di dialogo espandere il **SharePoint** nodo e quindi scegliere il **2010**  nodo.  
  
10. Salvare e chiudere il file.  
  
11. In **Esplora**, aprire il menu di scelta rapida per il modello di progetto o modello di elemento di progetto e quindi scegliere **Ricarica progetto**.  
  
##### <a name="to-include-a-template-that-you-create-manually"></a>Per includere un modello creato manualmente  
  
1.  Nel progetto VSIX, aggiungere una nuova cartella per il progetto che contiene il modello.  
  
2.  In questa nuova cartella, creare le sottocartelle seguenti e quindi aggiungere il file di modello (con estensione zip) per il *ID delle impostazioni locali* cartella.  
  
     *YourTemplateFolder*  
  
     **SharePoint**  
  
     **SharePoint14**  
  
     *ID delle impostazioni locali*  
  
     *YourTemplateName*ZIP  
  
     Ad esempio, se si dispone di un modello di elemento denominato ContosoCustomAction. zip che supportano le impostazioni locali inglese (Stati Uniti), il percorso completo potrebbe essere ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip.  
  
3.  In **Esplora**, scegliere il file di modello (*YourTemplateName*con estensione zip).  
  
4.  Nel **proprietà** finestra, impostare il **azione di compilazione** proprietà **contenuto**.  
  
5.  Aprire il menu di scelta rapida per il file vsixmanifest e quindi scegliere **aprire**.  
  
     Il file verrà aperto nella finestra di progettazione.  
  
6.  Nel **asset** sezione dell'editor, scegliere il **New** pulsante.  
  
     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.  
  
7.  Nel **tipo** scegliere **Microsoft.VisualStudio.ItemTemplate** o **Microsoft.VisualStudio.ProjectTemplate**.  
  
8.  Nel **origine** scegliere **File in filesystem**.  
  
9. Nel **percorso** immettere il percorso completo dell'assembly (ad esempio, **ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip**, oppure utilizzare il **Sfoglia**per individuare e selezionare l'assembly e quindi scegliere il **OK** pulsante.  
  
##### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>Per includere una procedura guidata per un modello di progetto o un modello di elemento  
  
1.  Nel progetto VSIX, aprire il menu di scelta rapida per il file vsixmanifest e quindi scegliere **aprire**.  
  
     Il file verrà aperto nella finestra di progettazione.  
  
2.  Nel **asset** sezione dell'editor, scegliere il **New** pulsante.  
  
     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.  
  
3.  Nel **tipo** scegliere **Microsoft.VisualStudio.Assembly**.  
  
4.  Nel **origine** elenco, eseguire una delle operazioni seguenti:  
  
    -   Se l'assembly della procedura guidata viene compilato da un progetto che si trova nella stessa soluzione del progetto VSIX, scegliere **un progetto nella soluzione corrente**. Nel **progetto** elenco, scegliere il nome del progetto.  
  
    -   Se l'assembly della procedura guidata è inclusa in un file nel progetto, scegliere **File in filesystem**. Nel **percorso** campo, immettere il percorso completo del file di assembly o utilizzare il **Sfoglia** pulsante per individuare e selezionare l'assembly.  
  
5.  Fare clic sul pulsante **OK** .  
  
### <a name="related-walkthroughs"></a>Procedure dettagliate correlate  
 Nella tabella seguente sono elencate procedure dettagliate che illustrano come utilizzare un progetto VSIX per distribuire i diversi tipi di estensioni degli strumenti di SharePoint.  
  
|Tipo di estensione|Procedure dettagliate correlate|  
|--------------------|--------------------------|  
|Un'estensione che include solo l'assembly dell'estensione|[Procedura dettagliata: estensione di un tipo di elemento di progetto SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Procedura dettagliata: creazione di un'estensione di progetto SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Procedura dettagliata: chiamata al modello a oggetti del client di SharePoint in un'estensione di Esplora server](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|  
|Un'estensione che include i comandi di SharePoint|[Procedura dettagliata: creazione di un passaggio di distribuzione personalizzato per progetti SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Procedura dettagliata: estensione di Esplora server per visualizzare web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Procedura dettagliata: creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
|Un'estensione che include un modello di Visual Studio|[Procedura dettagliata: creazione di un elemento di progetto Azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Procedura dettagliata: creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|  
|Un'estensione che include una procedura guidata modello|[Procedura dettagliata: creazione di un elemento di progetto Azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Procedura dettagliata: creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
  
## <a name="creating-vsix-packages-manually"></a>Creazione di pacchetti VSIX manualmente  
 Se si desidera creare manualmente il pacchetto VSIX per l'estensione strumenti di SharePoint, eseguire i passaggi seguenti:  
  
1.  Creare il file extension vsixmanifest e il file [Content_Types] XML in una nuova cartella. Per ulteriori informazioni, vedere [Anatomia di un pacchetto VSIX](/visualstudio/extensibility/anatomy-of-a-vsix-package).  
  
2.  In Esplora risorse, fare clic sulla cartella che contiene i due file XML, fare clic su Invia a e quindi fare clic sulla cartella compressa. Rinominare il file ZIP risultante in Filename.vsix, in cui Filename è il nome del file ridistribuibile che installa il pacchetto.  
  
3.  Aggiungere l'assembly di estensioni per il pacchetto VSIX. Se l'estensione include un comando di SharePoint, è necessario aggiungere anche l'assembly che implementa il comando di SharePoint per il pacchetto VSIX.  
  
4.  Modificare il file Extension. vsixmanifest:  
  
    -   Aggiungere un `Microsoft.VisualStudio.MefComponent` elemento sotto il `Assets` elemento e quindi impostare il valore del nuovo elemento per il percorso relativo dell'assembly che implementa l'estensione del pacchetto VSIX. Per ulteriori informazioni, vedere [elemento MEFComponent (schema VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
    -   Se l'estensione include un comando di SharePoint che effettua chiamate nel modello a oggetti del server per SharePoint, aggiungere un `Microsoft.VisualStudio.Assembly` elemento sotto il `Assets` elemento. Impostare il valore del nuovo elemento per il percorso relativo dell'assembly che implementa il comando di SharePoint nel pacchetto VSIX. Per ulteriori informazioni, vedere [elemento Asset (schema VSX)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
    -   Se l'estensione include un modello di progetto o un modello di elemento, aggiungere un `ProjectTemplate` o `ItemTemplate` elemento sotto il `Assets` elemento. Impostare il valore del nuovo elemento per il percorso relativo della cartella che contiene il modello nel pacchetto VSIX. Per ulteriori informazioni, vedere [elemento ProjectTemplate (schema VSX)](http://msdn.microsoft.com/en-us/87add64c-9dcd-495f-8815-209dab182cb1) e [elemento ItemTemplate (schema VSX)](http://msdn.microsoft.com/en-us/1d489e54-c1c5-4f96-a510-6c2640867ff0).  
  
    -   Se l'estensione include una procedura guidata personalizzata per un modello di progetto o un modello di elemento, aggiungere un `Assembly` elemento sotto il `Assets` elemento. Impostare il valore del nuovo elemento per il percorso relativo dell'assembly nel pacchetto VSIX e quindi impostare il `AssemblyName` attributo per il nome completo dell'assembly (inclusi versione, impostazioni cultura e token di chiave pubblica). Per ulteriori informazioni, vedere [elemento Dependency (schema VSX)](http://msdn.microsoft.com/en-us/1f63f60a-98ad-48ec-8e44-4eba383d3e37).  
  
### <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato il contenuto di un file Extension. vsixmanifest per un'estensione degli strumenti di SharePoint. L'estensione è implementata in un assembly denominato Contoso.ProjectExtension.dll. L'estensione include un assembly di comandi di SharePoint è denominato Contoso.ExtensionCommands.dll e un modello di elemento in una cartella denominata **ItemTemplates** nel pacchetto VSIX. In questo esempio si presuppone che entrambi gli assembly nella stessa cartella del file Extension. vsixmanifest nel pacchetto VSIX.  
  
```  
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">  
  <Metadata>  
    <Identity Id="CustomActionProjectItem.Microsoft.b99efe4d-cef3-4afd-b9af-034ca0c52743" Version="1.0" Language="en-US" Publisher="Microsoft" />  
    <DisplayName>CustomActionProjectItem</DisplayName>  
    <Description>Empty VSIX Project.</Description>  
  </Metadata>  
  <Installation>  
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="11.0" />  
  </Installation>  
  <Dependencies>  
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" Version="4.5" />  
  </Dependencies>  
  <Assets>  
    <Asset Type="Microsoft.VisualStudio.ItemTemplate" Path="ItemTemplates" />  
    <Asset Type="Microsoft.VisualStudio.MefComponent" Path="ProjectItemDefinition.dll" />  
  </Assets>  
</PackageManifest>  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione del sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Estensione del nodo Connessioni di SharePoint in Esplora Server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Chiamate ai modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Debug delle estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  