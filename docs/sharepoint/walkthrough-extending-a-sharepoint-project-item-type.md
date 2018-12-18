---
title: 'Procedura dettagliata: Estensione di un tipo di elemento di progetto SharePoint | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ed2c425af4127af443254bfdc269d58c653bb3c9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-extending-a-sharepoint-project-item-type"></a>Procedura dettagliata: estensione di un tipo di elemento di progetto SharePoint
  È possibile utilizzare il **modello di integrazione applicativa dei dati di Business** elemento di progetto per creare un modello per il servizio di integrazione applicativa dei dati (BDC) in SharePoint. Per impostazione predefinita, quando si crea un modello utilizzando l'elemento del progetto, i dati nel modello non viene visualizzati agli utenti. È inoltre necessario creare un elenco esterno in SharePoint per consentire agli utenti di visualizzare i dati.  
  
 In questa procedura dettagliata, si creerà un'estensione per il **modello di integrazione applicativa dei dati di Business** elemento del progetto. Gli sviluppatori possono utilizzare l'estensione per creare un elenco esterno del progetto che vengono visualizzati i dati nel modello di integrazione applicativa dei dati. In questa procedura dettagliata vengono descritte le attività seguenti:  
  
-   Creazione di un'estensione di Visual Studio che vengono eseguite due operazioni principali:  
  
    -   Genera un elenco esterno che visualizza i dati in un modello di integrazione applicativa dei dati. L'estensione utilizza il modello a oggetti per il sistema di progetto SharePoint per generare un file Elements.xml che definisce l'elenco. Aggiunge anche il file al progetto in modo che venga distribuito insieme al modello di integrazione applicativa dei dati.  
  
    -   Aggiunge una voce di menu di scelta rapida per il **modello di integrazione applicativa dei dati di Business** gli elementi nel progetto **Esplora**. Gli sviluppatori possono fare clic su questa voce di menu per generare un elenco esterno per il modello di integrazione applicativa dei dati.  
  
-   Compilazione di un pacchetto di Visual Studio Extension (VSIX) per distribuire l'assembly dell'estensione.  
  
-   Test dell'estensione.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Sono necessari i seguenti componenti nel computer di sviluppo per completare questa procedura dettagliata:  
  
-   Le edizioni supportate di Microsoft Windows, SharePoint e Visual Studio. Per ulteriori informazioni, vedere [requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Oggetto [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Questa procedura dettagliata Usa il **progetto VSIX** modello nel SDK per creare un pacchetto VSIX per distribuire l'elemento del progetto. Per ulteriori informazioni, vedere [estensione degli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Conoscere i concetti seguenti è utile, ma non obbligatorio, per completare la procedura dettagliata:  
  
-   Il servizio di integrazione applicativa dei dati in [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]. Per ulteriori informazioni, vedere [architettura di integrazione applicativa dei dati](http://go.microsoft.com/fwlink/?LinkId=177798).  
  
-   XML schema per i modelli di integrazione applicativa dei dati. Per ulteriori informazioni, vedere [infrastruttura del modello di integrazione applicativa dei dati](http://go.microsoft.com/fwlink/?LinkId=177799).  
  
## <a name="creating-the-projects"></a>Creazione dei progetti  
 Per completare questa procedura dettagliata, è necessario creare due progetti:  
  
-   Un progetto VSIX per creare il pacchetto VSIX per distribuire l'estensione di elemento di progetto.  
  
-   Un progetto libreria di classi che implementa l'estensione dell'elemento di progetto.  
  
 Avviare la procedura dettagliata creando i progetti.  
  
#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
3.  Nel **nuovo progetto** finestra di dialogo espandere il **Visual c#** o **Visual Basic** nodi e quindi scegliere il **estendibilità** nodo.  
  
    > [!NOTE]  
    >  Il **estendibilità** nodo è disponibile solo se si installa Visual Studio SDK. Per ulteriori informazioni, vedere la sezione Prerequisiti in questo argomento.  
  
4.  Nell'elenco nella parte superiore del **nuovo progetto** finestra di dialogo scegliere **.NET Framework 4.5**.  
  
     Le estensioni di strumenti di SharePoint richiedono funzionalità in questa versione di .NET Framework.  
  
5.  Scegliere il **progetto VSIX** modello.  
  
6.  Nel **nome** immettere **GenerateExternalDataLists**, quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **GenerateExternalDataLists** progetto **Esplora**.  
  
7.  Se il file vsixmanifest non viene aperto automaticamente, aprire il menu di scelta rapida nel progetto GenerateExternalDataLists e quindi scegliere **aprire**  
  
8.  Verificare che il file vsixmanifest disponga di una voce non vuote (invio di Contoso) per il campo dell'autore, salvare il file e chiuderlo.  
  
#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il **GenerateExternalDataLists** nodo della soluzione, scegliere **Aggiungi**, quindi scegliere **nuovo progetto**.  
  
2.  Nel **Aggiungi nuovo progetto** finestra di dialogo espandere il **Visual c#** o **Visual Basic** nodi, quindi scegliere il **Windows** nodo.  
  
3.  Nell'elenco nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5**.  
  
4.  Nell'elenco dei modelli di progetto, scegliere **libreria di classi**.  
  
5.  Nel **nome** immettere **BdcProjectItemExtension**, quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **BdcProjectItemExtension** progetto alla soluzione e apre il file di codice predefinito Class1.  
  
6.  Eliminare il file di codice Class1 dal progetto.  
  
## <a name="configuring-the-extension-project"></a>Configurazione del progetto di estensione  
 Prima di scrivere codice per creare l'estensione dell'elemento di progetto, aggiungere i file di codice e i riferimenti ad assembly al progetto di estensione.  
  
#### <a name="to-configure-the-project"></a>Per configurare il progetto  
  
1.  Nel progetto BdcProjectItemExtension, aggiungere due file di codice che presentano i nomi seguenti:  
  
    -   ProjectItemExtension  
  
    -   GenerateExternalDataLists  
  
2.  Scegliere il progetto BdcProjectItemExtension e quindi nella barra dei menu scegliere **progetto**, **Aggiungi riferimento**.  
  
3.  Sotto il **assembly** nodo, scegliere il **Framework** nodo e quindi selezionare la casella di controllo per ognuno degli assembly seguenti:  
  
    -   System.ComponentModel.Composition  
  
    -   WindowsBase  
  
4.  Sotto il **assembly** nodo, scegliere il **estensioni** nodo e quindi selezionare la casella di controllo per l'assembly seguente:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Fare clic sul pulsante **OK** .  
  
## <a name="defining-the-project-item-extension"></a>La definizione dell'estensione dell'elemento di progetto  
 Creare una classe che definisce l'estensione per il **modello di integrazione applicativa dei dati di Business** elemento del progetto. Per definire l'estensione, la classe implementa il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interfaccia. Implementare questa interfaccia ogni volta che si desidera estendere un tipo di elemento di progetto esistente.  
  
#### <a name="to-define-the-project-item-extension"></a>Per definire l'estensione dell'elemento di progetto  
  
1.  Incollare il codice seguente nel file di codice ProjectItemExtension.  
  
    > [!NOTE]  
    >  Dopo aver aggiunto questo codice, il progetto avrà degli errori di compilazione. Questi errori non verranno più visualizzato quando si aggiunge il codice nei passaggi successivi.  
  
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb#1)]  
  
## <a name="creating-the-external-data-lists"></a>Creazione degli elenchi di dati esterni  
 Aggiungere una definizione parziale della `GenerateExternalDataListsExtension` classe che crea un elenco di dati esterni per ogni entità nel modello di integrazione applicativa dei dati. Per creare l'elenco di dati esterni, questo codice legge innanzitutto i dati di entità nel modello di integrazione applicativa dei dati per l'analisi dei dati XML nel file di modello di integrazione applicativa dei dati. Quindi, crea un'istanza di elenco che è basata sul modello di integrazione applicativa dei dati e aggiunge questa istanza di elenco al progetto.  
  
#### <a name="to-create-the-external-data-lists"></a>Per creare elenchi di dati esterni  
  
1.  Incollare il codice seguente nel file di codice GenerateExternalDataLists.  
  
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs#2)]  
  
## <a name="checkpoint"></a>Checkpoint  
 A questo punto la procedura dettagliata, tutto il codice per l'estensione di elemento di progetto è ora nel progetto. Compilare la soluzione per assicurarsi che il progetto venga compilato senza errori.  
  
#### <a name="to-build-the-solution"></a>Per compilare la soluzione  
  
1.  Nella barra dei menu scegliere **Compilazione**, **Compila soluzione**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-item-extension"></a>Creazione di un pacchetto VSIX per distribuire l'estensione di elemento di progetto  
 Per distribuire l'estensione, è possibile utilizzare il progetto VSIX nella soluzione per creare un pacchetto VSIX. Innanzitutto, configurare il pacchetto VSIX modificando il file vsixmanifest incluso nel progetto VSIX. Quindi, creare il pacchetto VSIX per la compilazione della soluzione.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Per configurare e creare il pacchetto VSIX  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il file vsixmanifest nel progetto GenerateExternalDataLists e quindi scegliere **aprire**.  
  
     Visual Studio apre il file nell'editor del manifesto. Il file vsixmanifest è che la base per il file extension vsixmanifest richiesto da tutti i pacchetti VSIX. Per ulteriori informazioni su questo file, vedere [riferimento 1.0 dello Schema di estensione VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Nel **Product Name** immettere **External Data List Generator**.  
  
3.  Nel **autore** immettere **Contoso**.  
  
4.  Nel **descrizione** immettere **un'estensione per gli elementi di progetto di modello di integrazione applicativa dei dati di Business che può essere utilizzato per generare gli elenchi di dati esterni**.  
  
5.  Nel **asset** scheda dell'editor, scegliere il **New** pulsante.  
  
     Il **Aggiungi nuovo Asset** viene visualizzata la finestra di dialogo.  
  
6.  Nel **tipo** scegliere **MEFComponent**.  
  
    > [!NOTE]  
    >  Questo valore corrisponde al `MefComponent` elemento nel file Extension. vsixmanifest. Questo elemento specifica il nome di un assembly di estensione nel pacchetto VSIX. Per ulteriori informazioni, vedere [elemento MEFComponent (schema VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  Nel **origine** scegliere **un progetto nella soluzione corrente**.  
  
8.  Nel **progetto** scegliere **BdcProjectItemExtension**, quindi scegliere il **OK** pulsante.  
  
9. Nella barra dei menu scegliere **Compilazione**, **Compila soluzione**.  
  
10. Assicurarsi che il progetto viene compilato e venga compilata senza errori.  
  
11. Assicurarsi che la cartella di output di compilazione per il progetto GenerateExternalDataLists contiene ora il file GenerateExternalDataLists.  
  
     Per impostazione predefinita, la cartella di output di compilazione è il... nella cartella \bin\Debug sotto la cartella che contiene il file di progetto.  
  
## <a name="testing-the-project-item-extension"></a>Test dell'estensione di elemento di progetto  
 A questo punto si è pronti testare l'estensione dell'elemento di progetto. Innanzitutto, avviare il debug del progetto di estensione nell'istanza sperimentale di Visual Studio. Quindi, utilizzare l'estensione nell'istanza sperimentale di Visual Studio per generare un elenco esterno per un modello di integrazione applicativa dei dati. Infine, aprire l'elenco esterno nel sito di SharePoint per verificare se funziona come previsto.  
  
#### <a name="to-start-debugging-the-extension"></a>Per avviare il debug dell'estensione  
  
1.  Se necessario, riavviare Visual Studio con credenziali amministrative e quindi aprire la soluzione GenerateExternalDataLists.  
  
2.  Nel progetto BdcProjectItemExtension, aprire il file di codice ProjectItemExtension e quindi aggiungere un punto di interruzione alla riga di codice il `Initialize` metodo.  
  
3.  Aprire il file di codice GenerateExternalDataLists e quindi aggiungere un punto di interruzione sulla prima riga di codice nel `GenerateExternalDataLists_Execute` metodo.  
  
4.  Avviare il debug premendo il tasto F5 o, nella barra dei menu, scegliendo **Debug**, **Avvia debug**.  
  
     Visual Studio installa l'estensione per i dati elenco Generator\1.0 %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\External e avvia un'istanza sperimentale di Visual Studio. Si testerà l'elemento del progetto in questa istanza di Visual Studio.  
  
#### <a name="to-test-the-extension"></a>Per testare l'estensione  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **File**, **New**, **progetto**.  
  
2.  Nel **nuovo progetto** finestra di dialogo espandere il **modelli** nodo, espandere il **Visual c#** nodo, espandere il **SharePoint** nodo, quindi Scegliere **2010**.  
  
3.  Nell'elenco nella parte superiore della finestra di dialogo, assicurarsi che **.NET Framework 3.5** è selezionata. Progetti per [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] richiedono questa versione di .NET Framework.  
  
4.  Nell'elenco dei modelli di progetto, scegliere **progetto SharePoint 2010**.  
  
5.  Nel **nome** immettere **SharePointProjectTestBDC**, quindi scegliere il **OK** pulsante.  
  
6.  Nella personalizzazione guidata SharePoint, immettere l'URL del sito che si desidera utilizzare per il debug, scegliere **Distribuisci come soluzione farm**, quindi scegliere il **fine**pulsante.  
  
7.  Aprire il menu di scelta rapida per il progetto SharePointProjectTestBDC, scegliere **Aggiungi**, quindi scegliere **nuovo elemento**.  
  
8.  Nel **aggiungere NewItem - SharePointProjectTestBDC** finestra di dialogo espandere il nodo lingua installata, espandere il **SharePoint** nodo.  
  
9. Scegliere il **2010** nodo, quindi scegliere il **modello di integrazione applicativa dei dati di Business (solo soluzione Farm)** modello.  
  
10. Nel **nome** immettere **TestBDCModel**, quindi scegliere il **Aggiungi** pulsante.  
  
11. Verificare che il codice in altra istanza di Visual Studio si arresta nel punto di interruzione impostati nel `Initialize` (metodo) del file di codice ProjectItemExtension.  
  
12. Nell'istanza di interruzione di Visual Studio, scegliere il **F5** chiave o sulla barra dei menu, scegliere **Debug**, **continua** per continuare il debug del progetto.  
  
13. Nell'istanza sperimentale di Visual Studio, scegliere il **F5** chiave, o, nella barra dei menu, scegliere **Debug**, **Avvia debug** per compilare, distribuire ed eseguire il  **TestBDCModel** progetto.  
  
     Nel browser viene visualizzata la pagina predefinita del sito di SharePoint specificato per il debug.  
  
14. Verificare che il **Elenca** sezione nell'area avvio veloce non contiene ancora un elenco che è basato sul modello di integrazione applicativa dei dati predefinita nel progetto. È innanzitutto necessario creare un elenco di dati esterni, tramite l'interfaccia utente di SharePoint o tramite l'estensione di elemento di progetto.  
  
15. Chiudere il Web browser.  
  
16. Nell'istanza di Visual Studio con il progetto aperto TestBDCModel, aprire il menu di scelta rapida per il **TestBDCModel** nodo **Esplora soluzioni**, quindi scegliere **generare dati esterni Elenco**.  
  
17. Verificare che il codice in altra istanza di Visual Studio si arresta nel punto di interruzione impostati nel `GenerateExternalDataLists_Execute` metodo. Scegliere il **F5** chiave, o, nella barra dei menu, scegliere **Debug**, **continua** per continuare il debug del progetto.  
  
18. L'istanza sperimentale di Visual Studio aggiunge un'istanza di elenco denominato **Entity1DataList** per il TestBDCModel progetto e l'istanza genera inoltre una funzionalità denominata **Feature2** per un elenco istanza.  
  
19. Scegliere il **F5** chiave, o, nella barra dei menu, scegliere **Debug**, **Avvia debug** per compilare, distribuire ed eseguire il progetto TestBDCModel.  
  
     Nel browser viene visualizzata la pagina predefinita del sito di SharePoint che viene utilizzato per il debug.  
  
20. Nel **Elenca** sezione dell'area avvio veloce scegliere il **Entity1DataList** elenco.  
  
21. Verificare che l'elenco contiene colonne denominate Identifier1 e il messaggio, oltre a un elemento con un valore Identifier1 pari a 0 e il valore di messaggio Hello World.  
  
     Il **modello di integrazione applicativa dei dati di Business** modello di progetto genera il modello di integrazione applicativa dei dati predefinito che fornisce tutti i dati.  
  
22. Chiudere il Web browser.  
  
## <a name="cleaning-up-the-development-computer"></a>Pulizia dei Computer di sviluppo  
 Dopo aver completato il test dell'estensione dell'elemento di progetto, rimuovere l'elenco esterno e il modello di integrazione applicativa dei dati dal sito di SharePoint e rimuovere l'estensione di elemento di progetto da Visual Studio.  
  
#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>Per rimuovere l'elenco di dati esterni al sito di SharePoint  
  
1.  Nell'area avvio veloce del sito di SharePoint, scegliere il **Entity1DataList** elenco.  
  
2.  Nella barra multifunzione nel sito di SharePoint, scegliere il **elenco** scheda.  
  
3.  Nel **elenco** nella scheda il **impostazioni** gruppo **le impostazioni dell'elenco**.  
  
4.  In **autorizzazioni e gestione**, scegliere **eliminare questo elenco**, quindi scegliere **OK** per confermare che si desidera inviare l'elenco nel Cestino.  
  
5.  Chiudere il Web browser.  
  
#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>Per rimuovere il modello di integrazione applicativa dei dati dal sito di SharePoint  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **compilare**, **Retract**.  
  
     Visual Studio consente di rimuovere il modello di integrazione applicativa dei dati dal sito di SharePoint.  
  
#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>Per rimuovere l'estensione di elemento di progetto da Visual Studio  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **strumenti**, **estensioni e aggiornamenti**.  
  
     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.  
  
2.  Nell'elenco di estensioni, scegliere **External Data List Generator**, quindi scegliere il **Disinstalla** pulsante.  
  
3.  Nella finestra di dialogo visualizzata, scegliere **Sì** per confermare che si desidera disinstallare l'estensione.  
  
4.  Scegliere **Riavvia ora** per completare la disinstallazione.  
  
5.  Chiudere entrambe le istanze di Visual Studio (l'istanza sperimentale e l'istanza in cui la soluzione GenerateExternalDataLists è aperta).  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione del sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Creazione di un modello di integrazione applicativa dei dati di Business](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  