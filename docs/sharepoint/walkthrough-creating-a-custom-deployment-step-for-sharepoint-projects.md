---
title: 'Procedura dettagliata: Creazione di un passaggio di distribuzione personalizzato per i progetti SharePoint | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1538e68d29667eb7a1b3f0c976ddc5d77dab825b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects"></a>Procedura dettagliata: creazione di un passaggio di distribuzione personalizzato per progetti SharePoint
  Quando si distribuisce un progetto SharePoint, Visual Studio esegue una serie di passaggi di distribuzione in un ordine specifico. Visual Studio include numerosi passaggi di distribuzione predefinite, ma è anche possibile creare una propria.  
  
 In questa procedura dettagliata, si creerà un passaggio di distribuzione personalizzato per aggiornare le soluzioni in un server che esegue SharePoint. Visual Studio include fasi di distribuzione predefinite per molte attività, tale ritrazione o l'aggiunta di soluzioni, ma non include un passaggio di distribuzione per l'aggiornamento delle soluzioni. Per impostazione predefinita, quando si distribuisce una soluzione di SharePoint, Visual Studio innanzitutto ritrae la soluzione (se è già stata distribuita) e quindi ridistribuisce l'intera soluzione. Per ulteriori informazioni sui passaggi di distribuzione predefinite, vedere [distribuzione, pubblicazione e l'aggiornamento di pacchetti della soluzione SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
 In questa procedura dettagliata vengono descritte le attività seguenti:  
  
-   Creazione di un'estensione di Visual Studio che vengono eseguite due operazioni principali:  
  
    -   L'estensione di definire un passaggio di distribuzione personalizzato per aggiornare le soluzioni di SharePoint.  
  
    -   L'estensione crea un'estensione di progetto che definisce una nuova configurazione di distribuzione, è un set di passaggi di distribuzione che vengono eseguiti per un determinato progetto. La nuova configurazione di distribuzione include il passaggio di distribuzione personalizzate e diversi passaggi di distribuzione predefinite.  
  
-   Creazione di due comandi di SharePoint personalizzati che chiama l'assembly dell'estensione. I comandi di SharePoint sono metodi che possono essere chiamati da assembly di estensione, usare le API nel modello a oggetti server per SharePoint. Per ulteriori informazioni, vedere [chiamate ai modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Compilazione di un pacchetto di Visual Studio Extension (VSIX) per distribuire entrambi gli assembly.  
  
-   Testare il nuovo passaggio di distribuzione.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Sono necessari i seguenti componenti nel computer di sviluppo per completare questa procedura dettagliata:  
  
-   Le edizioni supportate di Windows, SharePoint e Visual Studio. Per ulteriori informazioni, vedere [requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio SDK. Questa procedura dettagliata Usa il **progetto VSIX** modello nel SDK per creare un pacchetto VSIX per distribuire l'estensione. Per ulteriori informazioni, vedere [estensione degli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Conoscere i concetti seguenti è utile, ma non obbligatorio, per completare la procedura dettagliata:  
  
-   Utilizzando il modello a oggetti server per SharePoint. Per ulteriori informazioni, vedere [utilizzando il modello a oggetti lato Server SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
-   Soluzioni di SharePoint. Per ulteriori informazioni, vedere [Cenni preliminari sulle soluzioni](http://go.microsoft.com/fwlink/?LinkId=169422).  
  
-   Aggiornamento delle soluzioni di SharePoint. Per ulteriori informazioni, vedere [l'aggiornamento di una soluzione](http://go.microsoft.com/fwlink/?LinkId=177802).  
  
## <a name="creating-the-projects"></a>Creazione dei progetti  
 Per completare questa procedura dettagliata, è necessario creare tre progetti:  
  
-   Un progetto VSIX per creare il pacchetto VSIX per distribuire l'estensione.  
  
-   Un progetto libreria di classi che implementa l'estensione. Questo progetto deve avere come destinazione di .NET Framework 4.5.  
  
-   Un progetto libreria di classi che definisce i comandi di SharePoint personalizzati. Questo progetto deve destinato a .NET Framework 3.5.  
  
 Avviare la procedura dettagliata creando i progetti.  
  
#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
3.  Nel **nuovo progetto** finestra di dialogo espandere il **Visual c#** o **Visual Basic** nodi e quindi scegliere il **estendibilità** nodo.  
  
    > [!NOTE]  
    >  Il **estendibilità** nodo è disponibile solo se si installa Visual Studio SDK. Per ulteriori informazioni, vedere la sezione Prerequisiti in questo argomento.  
  
4.  Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5** nell'elenco delle versioni di .NET Framework.  
  
5.  Scegliere il **progetto VSIX** modello, denominare il progetto **UpgradeDeploymentStep**, quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **UpgradeDeploymentStep** progetto **Esplora**.  
  
#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il nodo della soluzione UpgradeDeploymentStep, scegli **Aggiungi**, quindi scegliere **nuovo progetto**.  
  
2.  Nel **nuovo progetto** finestra di dialogo espandere il **Visual c#** o **Visual Basic** nodi, quindi scegliere il **Windows** nodo.  
  
3.  Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5** nell'elenco delle versioni di .NET Framework.  
  
4.  Scegliere il **libreria di classi** modello di progetto, denominare il progetto **DeploymentStepExtension**, quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **DeploymentStepExtension** progetto alla soluzione e apre il file di codice predefinito Class1.  
  
5.  Eliminare il file di codice Class1 dal progetto.  
  
#### <a name="to-create-the-sharepoint-command-project"></a>Per creare il progetto di comando di SharePoint  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il nodo della soluzione UpgradeDeploymentStep, scegli **Aggiungi**, quindi scegliere **nuovo progetto**.  
  
2.  Nel **nuovo progetto** finestra di dialogo espandere **Visual c#** o **Visual Basic**, quindi scegliere il **Windows** nodo.  
  
3.  Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 3.5** nell'elenco delle versioni di .NET Framework.  
  
4.  Scegliere il **libreria di classi** modello di progetto, denominare il progetto **SharePointCommands**, quindi scegliere il **OK** pulsante.  
  
     Visual Studio aggiunge il **SharePointCommands** progetto alla soluzione e apre il file di codice predefinito Class1.  
  
5.  Eliminare il file di codice Class1 dal progetto.  
  
## <a name="configuring-the-projects"></a>Configurazione dei progetti  
 Prima di scrivere codice per creare il passaggio di distribuzione personalizzati, è necessario aggiungere i file di codice e i riferimenti agli assembly, ed è necessario configurare i progetti.  
  
#### <a name="to-configure-the-deploymentstepextension-project"></a>Per configurare il progetto DeploymentStepExtension  
  
1.  Nel **DeploymentStepExtension** del progetto, aggiungere due file di codice che presentano i nomi seguenti:  
  
    -   UpgradeStep  
  
    -   DeploymentConfigurationExtension  
  
2.  Aprire il menu di scelta rapida del progetto DeploymentStepExtension e quindi scegliere **Aggiungi riferimento**.  
  
3.  Nel **Framework** , selezionare la casella di controllo per l'assembly System.  
  
4.  Nel **estensioni** scheda, selezionare la casella di controllo per l'assembly Microsoft.VisualStudio.SharePoint e quindi scegliere il **OK** pulsante.  
  
#### <a name="to-configure-the-sharepointcommands-project"></a>Per configurare il progetto SharePointCommands  
  
1.  Nel **SharePointCommands** del progetto, aggiungere un file di codice denominato comandi.  
  
2.  In **Esplora**, aprire il menu di scelta rapida nel **SharePointCommands** nodo del progetto e quindi scegliere **Aggiungi riferimento**.  
  
3.  Nel **estensioni** scheda, selezionare le caselle di controllo per gli assembly seguenti e quindi fare clic su Scegli il **OK** pulsante  
  
    -   Microsoft. SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
## <a name="defining-the-custom-deployment-step"></a>Definire il passaggio di distribuzione personalizzata  
 Creare una classe che definisce il passaggio di distribuzione dell'aggiornamento. Per definire la fase di distribuzione, la classe implementa il <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> interfaccia. Implementare questa interfaccia ogni volta che si desidera definire un passaggio di distribuzione personalizzati.  
  
#### <a name="to-define-the-custom-deployment-step"></a>Per definire il passaggio di distribuzione personalizzata  
  
1.  Nel **DeploymentStepExtension** del progetto, aprire il file di codice UpgradeStep e quindi incollare il codice seguente.  
  
    > [!NOTE]  
    >  Dopo che si aggiunge questo codice, il progetto avrà degli errori di compilazione, ma si sarà più visualizzato quando si aggiunge codice nei passaggi successivi.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]  
  
## <a name="creating-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>Creazione di una configurazione di distribuzione che include il passaggio di distribuzione personalizzata  
 Creare un'estensione di progetto per la nuova configurazione di distribuzione, che comprende diversi passaggi di distribuzione predefinite e il nuovo passaggio di distribuzione dell'aggiornamento. Creazione di questa estensione, consente agli sviluppatori di SharePoint da usare il passaggio di distribuzione dell'aggiornamento nei progetti SharePoint.  
  
 Per creare la configurazione della distribuzione, la classe implementa il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfaccia. Implementare questa interfaccia ogni volta che si desidera creare un'estensione di progetto SharePoint.  
  
#### <a name="to-create-the-deployment-configuration"></a>Per creare la configurazione della distribuzione  
  
1.  
  
2.  Nel **DeploymentStepExtension** del progetto, aprire il file di codice DeploymentConfigurationExtension e quindi incollare il codice seguente.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]  
  
## <a name="creating-the-custom-sharepoint-commands"></a>Creazione di comandi personalizzati di SharePoint  
 Creare due comandi personalizzati che effettuano chiamate nel modello a oggetti del server per SharePoint. Un comando determina se una soluzione è già stata distribuita; il comando Aggiorna una soluzione.  
  
#### <a name="to-define-the-sharepoint-commands"></a>Per definire i comandi di SharePoint  
  
1.  Nel **SharePointCommands** del progetto, aprire il file di codice i comandi e quindi incollare il codice seguente.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]  
  
## <a name="checkpoint"></a>Checkpoint  
 A questo punto la procedura dettagliata, tutto il codice per il passaggio di distribuzione personalizzate e i comandi di SharePoint sono ora nei progetti. Per assicurarsi che si esegue la compilazione senza errori di compilazione.  
  
#### <a name="to-build-the-projects"></a>Per compilare i progetti  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il **DeploymentStepExtension** del progetto e quindi scegliere **compilare**.  
  
2.  Aprire il menu di scelta rapida per il **SharePointCommands** del progetto e quindi scegliere **compilare**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-extension"></a>Creazione di un pacchetto VSIX per distribuire l'estensione  
 Per distribuire l'estensione, è possibile utilizzare il progetto VSIX nella soluzione per creare un pacchetto VSIX. Innanzitutto, configurare il pacchetto VSIX modificando il file vsixmanifest nel progetto VSIX. Quindi creare il pacchetto VSIX per la compilazione della soluzione.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Per configurare e creare il pacchetto VSIX  
  
1.  In **Esplora**, sotto il **UpgradeDeploymentStep** del progetto, aprire il menu di scelta rapida per il **vsixmanifest** file e quindi scegliere  **Aprire**.  
  
     Visual Studio apre il file nell'editor del manifesto. Il file vsixmanifest è la base per il file extension vsixmanifest che richiedono tutti i pacchetti VSIX. Per ulteriori informazioni su questo file, vedere [riferimento 1.0 dello Schema di estensione VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Nel **Product Name** immettere **passaggio di distribuzione dell'aggiornamento per i progetti SharePoint**.  
  
3.  Nel **autore** immettere **Contoso**.  
  
4.  Nel **descrizione** immettere **offre una procedura di distribuzione di aggiornamento personalizzata che può essere utilizzata nei progetti SharePoint**.  
  
5.  Nel **asset** scheda dell'editor, scegliere il **New** pulsante.  
  
     Il **Aggiungi nuovo Asset** viene visualizzata la finestra di dialogo.  
  
6.  Nel **tipo** scegliere **MEFComponent**.  
  
    > [!NOTE]  
    >  Questo valore corrisponde al `MefComponent` elemento nel file Extension. vsixmanifest. Questo elemento specifica il nome di un assembly di estensione nel pacchetto VSIX. Per ulteriori informazioni, vedere [elemento MEFComponent (schema VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  Nel **origine** scegliere **un progetto nella soluzione corrente**.  
  
8.  Nel **progetto** scegliere **DeploymentStepExtension**, quindi scegliere il **OK** pulsante.  
  
9. Nell'editor del manifesto, scegliere il **New** nuovamente clic sul pulsante.  
  
     Il **Aggiungi nuovo Asset** viene visualizzata la finestra di dialogo.  
  
10. Nel **tipo** immettere **v4**.  
  
    > [!NOTE]  
    >  Questo elemento specifica un'estensione personalizzata che si desidera includere nell'estensione di Visual Studio. Per ulteriori informazioni, vedere [elemento Asset (schema VSX)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. Nel **origine** scegliere **un progetto nella soluzione corrente**.  
  
12. Nel **progetto** scegliere **SharePointCommands**, quindi scegliere il **OK** pulsante.  
  
13. Nella barra dei menu, scegliere **compilare**, **Compila soluzione**, quindi assicurarsi che la soluzione venga compilata senza errori.  
  
14. Assicurarsi che la cartella di output di compilazione per il progetto UpgradeDeploymentStep contiene ora il file UpgradeDeploymentStep.  
  
     Per impostazione predefinita, la cartella di output di compilazione è il... nella cartella \bin\Debug sotto la cartella che contiene il file di progetto.  
  
## <a name="preparing-to-test-the-upgrade-deployment-step"></a>Preparazione per testare il passaggio di distribuzione dell'aggiornamento  
 Per testare il passaggio di distribuzione dell'aggiornamento, è necessario innanzitutto distribuire una soluzione di esempio al sito di SharePoint. Avviare il debug dell'estensione nell'istanza sperimentale di Visual Studio. Quindi creare una definizione di elenco e un'istanza di elenco da utilizzare per testare il passaggio di distribuzione e quindi distribuirli nel sito di SharePoint. Successivamente, modificare la definizione e l'istanza di elenco e ridistribuirle per illustrare come il processo di distribuzione predefinito sovrascrive le soluzioni nel sito di SharePoint.  
  
 Più avanti in questa procedura dettagliata, che si desidera modificare la definizione e l'istanza di elenco e quindi verrà aggiornarli nel sito di SharePoint.  
  
#### <a name="to-start-debugging-the-extension"></a>Per avviare il debug dell'estensione  
  
1.  Riavviare Visual Studio con credenziali amministrative e quindi aprire la soluzione UpgradeDeploymentStep.  
  
2.  Nel progetto DeploymentStepExtension, aprire il file di codice UpgradeStep e quindi aggiungere un punto di interruzione sulla prima riga di codice il `CanExecute` e `Execute` metodi.  
  
3.  Avviare il debug premendo il tasto F5 o, nella barra dei menu, scegliendo **Debug**, **Avvia debug**.  
  
4.  Visual Studio installa l'estensione in fase di distribuzione %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade for SharePoint Projects\1.0 e avvia un'istanza sperimentale di Visual Studio. Verrà testato il passaggio di distribuzione dell'aggiornamento di questa istanza di Visual Studio.  
  
#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>Per creare un progetto SharePoint con una definizione di elenco e un'istanza di elenco  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **File**, **New**, **progetto**.  
  
2.  Nel **nuovo progetto** finestra di dialogo espandere il **Visual c#** nodo o **Visual Basic** nodo, espandere il **SharePoint** nodo e quindi scegliere il **2010** nodo.  
  
3.  Nella parte superiore della finestra di dialogo, assicurarsi che **.NET Framework 3.5** viene visualizzato nell'elenco delle versioni di .NET Framework.  
  
     Progetti per [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] e [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] richiedono questa versione di .NET Framework.  
  
4.  Nell'elenco dei modelli di progetto, scegliere **progetto SharePoint 2010**, denominare il progetto **EmployeesListDefinition**, quindi scegliere il **OK** pulsante.  
  
5.  Nel **Personalizzazione guidata SharePoint**, immettere l'URL del sito che si desidera utilizzare per il debug.  
  
6.  In **qual è il livello di attendibilità per la soluzione SharePoint**, scegliere il **Distribuisci come soluzione farm** pulsante di opzione.  
  
    > [!NOTE]  
    >  Il passaggio di distribuzione dell'aggiornamento non supporta soluzioni create mediante sandbox.  
  
7.  Scegliere il **fine** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Crea il progetto EmployeesListDefinition.  
  
8.  Aprire il menu di scelta rapida per il progetto EmployeesListDefinition, scegliere **Aggiungi**, quindi scegliere **nuovo elemento**.  
  
9. Nel **Aggiungi nuovo elemento - EmployeesListDefinition** finestra di dialogo, espandere il **SharePoint** nodo, quindi scegliere il **2010** nodo.  
  
10. Scegliere il **elenco** modello di elemento, denominare l'elemento **elenco dipendenti**, quindi scegliere il **Aggiungi** pulsante.  
  
     Verrà visualizzata la personalizzazione guidata SharePoint  
  
11. Nel **scegliere le impostazioni dell'elenco** pagina, verificare le impostazioni seguenti e quindi scegliere il **fine** pulsante:  
  
    1.  **Elenco di dipendenti** viene visualizzato nel **nome che si desidera visualizzare per l'elenco?** casella.  
  
    2.  Il **creare un elenco personalizzabile in base a:** viene scelto il pulsante di opzione.  
  
    3.  **Predefinito (vuoto)** viene scelto nel **creare un elenco personalizzabile in base a:** elenco.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Crea la voce di elenco di dipendenti con una colonna del titolo e una singola istanza vuota e verrà visualizzata la finestra di progettazione di elenco.  
  
12. Nella finestra di progettazione di elenco sul **colonne** scheda, scegliere il **digitare un nome di colonna nuovo o esistente** di riga e quindi aggiungere le colonne seguenti nel **nome visualizzato colonna** elenco:  
  
    1.  Nome  
  
    2.  Company  
  
    3.  Telefono ufficio  
  
    4.  Posta elettronica  
  
13. Salvare tutti i file e quindi chiudere la finestra di progettazione di elenco.  
  
14. In **Esplora soluzioni**, espandere il **elenco dipendenti** nodo, quindi espandere il **istanza di elenco di dipendenti** nodo figlio.  
  
15. Nel file Elements.xml, sostituire il valore predefinito in questo file XML con il seguente codice XML. Questo codice XML viene modificato il nome dell'elenco per **dipendenti** e aggiunge le informazioni per un dipendente che ha chiamato Jim Hance.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
        <Data>  
          <Rows>  
            <Row>  
              <Field Name="Title">Hance</Field>  
              <Field Name="FirstName">Jim</Field>  
              <Field Name="Company">Contoso</Field>  
              <Field Name="Business Phone">555-555-5555</Field>  
              <Field Name="E-Mail">jim@contoso.com</Field>  
            </Row>  
          </Rows>  
        </Data>  
      </ListInstance>  
    </Elements>  
    ```  
  
16. Salvare e chiudere il file Elements.xml.  
  
17. Aprire il menu di scelta rapida per il progetto EmployeesListDefinition e quindi scegliere **aprire** o **proprietà**.  
  
     Verrà visualizzata la finestra di progettazione di proprietà.  
  
18. Nel **SharePoint** scheda, deseleziona il **ritrazione automatica dopo il debug** casella di controllo e quindi salvare le proprietà.  
  
#### <a name="to-deploy-the-list-definition-and-list-instance"></a>Per distribuire la definizione e l'istanza di elenco  
  
1.  In **Esplora**, scegliere il **EmployeesListDefinition** nodo del progetto.  
  
2.  Nel **proprietà** finestra, assicurarsi che il **configurazione distribuzione attiva** è impostata su **predefinito**.  
  
3.  Premere F5 oppure, nella barra dei menu, scegliere **Debug**, **Avvia debug**.  
  
4.  Verificare che il progetto venga compilato correttamente, che consente di aprire il browser al sito di SharePoint, che il **Elenca** include il nuovo elemento nella barra Avvio veloce **dipendenti** elenco e che il  **I dipendenti** elenco include la voce per Jim Hance.  
  
5.  Chiudere il Web browser.  
  
#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>Per modificare la definizione e l'istanza di elenco e rieseguire la distribuzione  
  
1.  Nel progetto EmployeesListDefinition, aprire il file Elements.xml che è un figlio di **istanza di elenco dipendente** elemento del progetto.  
  
2.  Rimuovere il `Data` elemento e i relativi elementi figlio per rimuovere la voce per Jim Hance dall'elenco.  
  
     Al termine, il file deve contenere il seguente codice XML.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
      </ListInstance>  
    </Elements>  
    ```  
  
3.  Salvare e chiudere il file Elements.xml.  
  
4.  Aprire il menu di scelta rapida per il **elenco dipendenti** dell'elemento di progetto e quindi scegliere **aprire** o **proprietà**.  
  
5.  Nella finestra di progettazione di elenco, scegliere il **viste** scheda.  
  
6.  Nel **colonne selezionate** scegliere **allegati**, quindi scegliere il < tasto per spostarsi di tale colonna il **colonne disponibili** elenco.  
  
7.  Ripetere il passaggio precedente per spostare il **telefono ufficio** colonna il **colonne selezionate** elenco il **colonne disponibili** elenco.  
  
     Questa azione rimuove la visualizzazione predefinita di questi campi di **dipendenti** elenco nel sito di SharePoint.  
  
8.  Avviare il debug premendo il tasto F5 o, nella barra dei menu, scegliendo **Debug**, **Avvia debug**.  
  
9. Verificare che il **conflitti di distribuzione** viene visualizzata la finestra di dialogo.  
  
     Questa finestra di dialogo viene visualizzata quando Visual Studio tenta di distribuire una soluzione (l'istanza di elenco) a un sito di SharePoint a cui è già stata distribuita la soluzione. Quando si esegue il passaggio di distribuzione dell'aggiornamento più avanti in questa procedura dettagliata, non verrà visualizzata questa finestra di dialogo.  
  
10. Nel **conflitti di distribuzione** finestra di dialogo scegliere la **Risolvi automaticamente** pulsante di opzione.  
  
     Visual Studio consente di eliminare l'istanza di elenco nel sito di SharePoint, distribuisce l'elemento di elenco nel progetto e quindi apre il sito di SharePoint.  
  
11. Nel **Elenca** sezione della barra di avvio veloce scegliere il **dipendenti** elenco e quindi verificare i dettagli seguenti:  
  
    -   Il **allegati** e **telefono abitazione** colonne non vengono visualizzati in questa visualizzazione dell'elenco.  
  
    -   L'elenco è vuoto. Quando si utilizza il **predefinito** configurazione della distribuzione per ridistribuire la soluzione, il **dipendenti** elenco è stato sostituito con il nuovo elenco vuoto nel progetto.  
  
## <a name="testing-the-deployment-step"></a>Il passaggio di distribuzione di test  
 A questo punto si è pronti testare il passaggio di distribuzione dell'aggiornamento. In primo luogo, aggiungere un elemento all'istanza di elenco in SharePoint. Modificare la definizione di elenco e l'istanza di elenco, l'aggiornamento nel sito di SharePoint e verificare che il passaggio di distribuzione dell'aggiornamento non sovrascriva il nuovo elemento.  
  
#### <a name="to-manually-add-an-item-to-the-list"></a>Per aggiungere manualmente un elemento all'elenco  
  
1.  Nella barra multifunzione nel sito di SharePoint, sotto il **strumenti elenco** scheda, scegliere il **elementi** scheda.  
  
2.  Nel **New** gruppo **nuovo elemento**.  
  
     In alternativa, è possibile scegliere di **Aggiungi nuovo elemento** collegamento in un elenco di elementi di se stesso.  
  
3.  Nel **dipendenti - nuovo elemento** finestra, nel **titolo** immettere **responsabile strutture**.  
  
4.  Nel **nome** immettere **Andy**.  
  
5.  Nel **aziendale** digitare **Contoso**.  
  
6.  Scegliere il **salvare** pulsante, verificare che il nuovo elemento viene visualizzato nell'elenco e quindi chiudere il browser web.  
  
     Più avanti in questa procedura dettagliata, si utilizzerà questo elemento per verificare che il passaggio di distribuzione dell'aggiornamento non sovrascriva il contenuto di questo elenco.  
  
#### <a name="to-test-the-upgrade-deployment-step"></a>Per testare il passaggio di distribuzione dell'aggiornamento  
  
1.  Nell'istanza sperimentale di Visual Studio, in **Esplora**, aprire il menu di scelta rapida per il **EmployeesListDefinition** nodo del progetto e quindi scegliere **proprietà**.  
  
     Verrà visualizzata la proprietà Editor/finestra di progettazione.  
  
2.  Nel **SharePoint** scheda, impostare il **configurazione distribuzione attiva** proprietà **aggiornamento**.  
  
     Questa configurazione di distribuzione personalizzato include il nuovo passaggio di distribuzione dell'aggiornamento.  
  
3.  Aprire il menu di scelta rapida per il **elenco dipendenti** dell'elemento di progetto e quindi scegliere **proprietà** o **aprire**.  
  
     Verrà visualizzata la proprietà Editor/finestra di progettazione.  
  
4.  Nel **viste** scheda, scegliere il **posta elettronica** colonna e quindi scegliere il **<** chiave per spostare la colonna dal **colonneselezionate**elenco il **colonne disponibili** elenco.  
  
     Questa azione rimuove la visualizzazione predefinita di questi campi di **dipendenti** elenco nel sito di SharePoint.  
  
5.  Avviare il debug premendo il tasto F5 o, nella barra dei menu, scegliendo **Debug**, **Avvia debug**.  
  
6.  Verificare che il codice in altra istanza di Visual Studio si arresta nel punto di interruzione impostato precedentemente nel `CanExecute` metodo.  
  
7.  Premere nuovamente F5 oppure, nella barra dei menu, scegliere **Debug**, **continua**.  
  
8.  Verificare che il codice si interrompe al punto di interruzione impostato in precedenza nel `Execute` metodo.  
  
9. Premere F5 oppure, nella barra dei menu, scegliere **Debug**, **continua** un'ultima volta.  
  
     Il browser web apre il sito di SharePoint.  
  
10. Nel **Elenca** sezione dell'area avvio veloce scegliere il **dipendenti** elenco e quindi verificare i dettagli seguenti:  
  
    -   L'elemento che sono stati aggiunti manualmente in precedenza (per Andy, la funzionalità di gestione) è ancora presente nell'elenco.  
  
    -   Il **telefono ufficio** e **indirizzo di posta elettronica** colonne non vengono visualizzati in questa visualizzazione dell'elenco.  
  
     Il **aggiornamento** modifica di configurazione di distribuzione esistenti **dipendenti** istanza di elenco nel sito di SharePoint. Se è stata utilizzata la **predefinito** configurazione della distribuzione anziché la **aggiornamento** configurazione, si potrebbe verificarsi un conflitto di distribuzione. Visual Studio potrebbe risolvere il conflitto sostituendo il **dipendenti** elenco e l'elemento per Andy, la funzionalità di gestione, verranno eliminati.  
  
## <a name="cleaning-up-the-development-computer"></a>Pulizia dei Computer di sviluppo  
 Dopo aver completato il passaggio di distribuzione dell'aggiornamento di test, rimuovere l'istanza e la definizione di elenco dal sito di SharePoint e rimuovere l'estensione di passaggio di distribuzione da Visual Studio.  
  
#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>Per rimuovere l'istanza di elenco dal sito di SharePoint  
  
1.  Aprire il **dipendenti** elenco nel sito di SharePoint, se l'elenco non è già aperto.  
  
2.  Nella barra multifunzione nel sito di SharePoint, scegliere il **strumenti elenco** scheda e quindi scegliere il **elenco** scheda.  
  
3.  Nel **impostazioni** gruppo, scegliere il **le impostazioni dell'elenco** elemento.  
  
4.  In **autorizzazioni e gestione**, scegliere il **eliminare questo elenco** comando, scegliere **OK** per confermare che si desidera inviare l'elenco per il Cestino e quindi chiudere il web Browser.  
  
#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>Per rimuovere la definizione di elenco dal sito di SharePoint  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **compilare**, **Retract**.  
  
     Visual Studio ritrae la definizione di elenco dal sito di SharePoint.  
  
#### <a name="to-uninstall-the-extension"></a>Per disinstallare l'estensione  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **strumenti**, **estensioni e aggiornamenti**.  
  
     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.  
  
2.  Nell'elenco di estensioni, scegliere **passaggio di distribuzione dell'aggiornamento per i progetti SharePoint**, quindi scegliere il **Disinstalla** comando.  
  
3.  Nella finestra di dialogo visualizzata, scegliere **Sì** per confermare che si desidera disinstallare l'estensione e quindi scegliere **Riavvia ora** per completare la disinstallazione.  
  
4.  Chiudere entrambe le istanze di Visual Studio (l'istanza sperimentale e l'istanza di Visual Studio in cui la soluzione UpgradeDeploymentStep è aperta).  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione della creazione di pacchetti e della distribuzione di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  