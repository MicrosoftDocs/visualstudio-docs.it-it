---
title: 'Procedura dettagliata: Creazione di un''estensione di progetto SharePoint | Documenti Microsoft'
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
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a03dd09525d29aaea31ef5c376814bd09747f90e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-sharepoint-project-extension"></a>Procedura dettagliata: creazione di un'estensione di progetto SharePoint
  Questa procedura dettagliata viene illustrato come creare un'estensione per i progetti SharePoint. È possibile utilizzare un'estensione di progetto per rispondere agli eventi a livello di progetto, ad esempio quando un progetto viene aggiunto, eliminato o rinominato. È anche possibile aggiungere proprietà personalizzate o rispondere quando un valore di proprietà viene modificato. A differenza delle estensioni di elemento di progetto, le estensioni di progetto non possono essere associate a un particolare tipo di progetto SharePoint. Quando si crea un'estensione di progetto, l'estensione viene caricato quando si apre qualsiasi tipo di progetto SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 In questa procedura dettagliata, si creerà una proprietà booleana personalizzata che viene aggiunto a qualsiasi progetto SharePoint creato nel [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Se impostato su **True**, aggiunge la nuova proprietà o esegue il mapping, una cartella di risorse immagini al progetto. Se impostato su **False**, la cartella delle immagini viene rimosso, se presente. Per ulteriori informazioni, vedere [procedura: aggiungere e rimuovere cartelle mappata](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 In questa procedura dettagliata vengono descritte le attività seguenti:  
  
-   Creazione di un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] estensione per i progetti SharePoint che esegue le operazioni seguenti:  
  
    -   Aggiunge una proprietà di progetto personalizzato alla finestra Proprietà. La proprietà si applica a qualsiasi progetto SharePoint.  
  
    -   Usa il modello oggetto di progetto SharePoint per aggiungere una cartella mappata a un progetto.  
  
    -   Usa il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] modello a oggetti di automazione (DTE) per eliminare una cartella mappata dal progetto.  
  
-   La creazione di un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto Extension (VSIX) per distribuire assembly di estensioni per della proprietà progetto.  
  
-   Debug e la proprietà del progetto di test.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Sono necessari i seguenti componenti nel computer di sviluppo per completare questa procedura dettagliata:  
  
-   Le edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)], SharePoint e [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Per ulteriori informazioni, vedere [requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Oggetto [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Questa procedura dettagliata Usa il **progetto VSIX** modello il [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] per creare un pacchetto VSIX per distribuire l'estensione di proprietà del progetto. Per ulteriori informazioni, vedere [estensione degli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="creating-the-projects"></a>Creazione dei progetti  
 Per completare questa procedura dettagliata, è necessario creare due progetti:  
  
-   Un progetto VSIX per creare il pacchetto VSIX per distribuire l'estensione di progetto.  
  
-   Un progetto libreria di classi che implementa l'estensione di progetto.  
  
 Avviare la procedura dettagliata creando i progetti.  
  
#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
3.  Nel **nuovo progetto** finestra di dialogo espandere il **Visual c#** o **Visual Basic** nodi e quindi scegliere il **estendibilità** nodo.  
  
    > [!NOTE]  
    >  Questo nodo è disponibile solo se si installa Visual Studio SDK. Per ulteriori informazioni, vedere la sezione Prerequisiti in questo argomento.  
  
4.  Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5** nell'elenco delle versioni di .NET Framework, quindi scegliere il **progetto VSIX** modello.  
  
5.  Nel **nome** immettere **ProjectExtensionPackage**, quindi scegliere il **OK** pulsante.  
  
     Il **ProjectExtensionPackage** progetto verrà visualizzato in **Esplora**.  
  
#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il nodo della soluzione, scegliere **Aggiungi**, quindi scegliere **nuovo progetto**.  
  
2.  Nel **nuovo progetto** finestra di dialogo espandere il **Visual c#** o **Visual Basic** nodi, quindi scegliere **Windows**.  
  
3.  Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5** nell'elenco delle versioni di .NET Framework, quindi scegliere il **libreria di classi** modello di progetto.  
  
4.  Nel **nome** immettere **ProjectExtension**, quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Aggiunge il **ProjectExtension** progetto alla soluzione e apre il file di codice predefinito Class1.  
  
5.  Eliminare il file di codice Class1 dal progetto.  
  
## <a name="configuring-the-project"></a>Configurazione del progetto  
 Prima di scrivere codice per creare l'estensione di progetto, aggiungere i file di codice e i riferimenti ad assembly al progetto di estensione.  
  
#### <a name="to-configure-the-project"></a>Per configurare il progetto  
  
1.  Aggiungere un file di codice denominato **CustomProperty** al progetto ProjectExtension.  
  
2.  Aprire il menu di scelta rapida per il **ProjectExtension** del progetto e quindi scegliere **Aggiungi riferimento**.  
  
3.  Nel **gestione riferimenti - CustomProperty** finestra di dialogo scegliere la **Framework** nodo e quindi selezionare la casella di controllo accanto agli assembly System e Forms.  
  
4.  Scegliere il **estensioni** nodo, selezionare la casella di controllo accanto agli assembly Microsoft.VisualStudio.SharePoint ed EnvDTE e quindi scegliere il **OK** pulsante.  
  
5.  In **Esplora**, sotto il **riferimenti** cartella per il **ProjectExtension** del progetto, scegliere **EnvDTE**.  
  
6.  Nel **proprietà** finestra, modifica il **incorpora tipi di interoperabilità** proprietà **False**.  
  
## <a name="defining-the-new-sharepoint-project-property"></a>Che definisce la nuova proprietà di progetto SharePoint  
 Creare una classe che definisce l'estensione di progetto e il comportamento della nuova proprietà di progetto. Per definire la nuova estensione di progetto, la classe implementa il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfaccia. Implementare questa interfaccia ogni volta che si desidera definire un'estensione per un progetto SharePoint. Inoltre, aggiungere il <xref:System.ComponentModel.Composition.ExportAttribute> alla classe. Questo attributo consente [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] di individuare e caricare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementazione. Passare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> tipo al costruttore dell'attributo.  
  
#### <a name="to-define-the-new-sharepoint-project-property"></a>Per definire la nuova proprietà di progetto SharePoint  
  
1.  Incollare il codice seguente nel file di codice CustomProperty.  
  
     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]  
  
## <a name="building-the-solution"></a>Compilare la soluzione  
 Successivamente, compilare la soluzione per assicurarsi che l'operazione avvenga senza errori.  
  
#### <a name="to-build-the-solution"></a>Per compilare la soluzione  
  
1.  Nella barra dei menu scegliere **Compilazione**, **Compila soluzione**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-property-extension"></a>Creazione di un pacchetto VSIX per distribuire l'estensione di proprietà di progetto  
 Per distribuire l'estensione di progetto, è possibile utilizzare il progetto VSIX nella soluzione per creare un pacchetto VSIX. Innanzitutto, configurare il pacchetto VSIX modificando il file vsixmanifest incluso nel progetto VSIX. Quindi, creare il pacchetto VSIX per la compilazione della soluzione.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Per configurare e creare il pacchetto VSIX  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il file vsixmanifest e quindi scegliere il **aprire** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Apre il file nella finestra di progettazione del manifesto. Le informazioni visualizzate nel **metadati** scheda viene visualizzato anche nella **estensioni e aggiornamenti**. Tutti i pacchetti VSIX è richiesto il file Extension. vsixmanifest. Per ulteriori informazioni su questo file, vedere [riferimento 1.0 dello Schema di estensione VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Nel **Product Name** immettere **Custom Project Property**.  
  
3.  Nel **autore** immettere **Contoso**.  
  
4.  Nel **descrizione** immettere **una proprietà di progetto SharePoint personalizzata che attiva o disattiva il mapping della cartella di risorse immagini al progetto**.  
  
5.  Scegliere il **asset** scheda e quindi scegliere il **New** pulsante.  
  
     Il **Aggiungi nuovo Asset** viene visualizzata la finestra di dialogo.  
  
6.  Nel **tipo** scegliere **MEFComponent**.  
  
    > [!NOTE]  
    >  Questo valore corrisponde al `MEFComponent` elemento nel file Extension. vsixmanifest. Questo elemento specifica il nome di un assembly di estensione nel pacchetto VSIX. Per ulteriori informazioni, vedere [elemento MEFComponent (schema VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  Nel **origine** scegliere il **un progetto nella soluzione corrente** pulsante di opzione.  
  
8.  Nel **progetto** scegliere **ProjectExtension**.  
  
     Questo valore identifica il nome dell'assembly che si sta creando il progetto.  
  
9. Scegliere **OK** per chiudere la **Aggiungi nuovo Asset** la finestra di dialogo.  
  
10. Nella barra dei menu, scegliere **File**, **Salva tutto** quando si finisce e quindi chiudere la finestra di progettazione del manifesto.  
  
11. Nella barra dei menu, scegliere **compilare**, **Compila soluzione**, quindi assicurarsi che il progetto venga compilato senza errori.  
  
12. In **Esplora**, aprire il menu di scelta rapida per il **ProjectExtensionPackage** del progetto e scegliere il **Apri cartella in Esplora File** pulsante.  
  
13. In **Esplora File**, aprire la cartella di output di compilazione del progetto ProjectExtensionPackage e quindi verificare che la cartella contenga un file denominato ProjectExtensionPackage.  
  
     Per impostazione predefinita, la cartella di output di compilazione è il... nella cartella \bin\Debug sotto la cartella che contiene il file di progetto.  
  
## <a name="testing-the-project-property"></a>La proprietà del progetto di test  
 A questo punto si è pronti testare la proprietà di progetto personalizzati. È più facile eseguire il debug e testare la nuova estensione di proprietà di progetto in un'istanza sperimentale di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Questa istanza di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] viene creato quando si esegue un progetto VSIX o un altro progetto di estendibilità. Dopo il debug del progetto, è possibile installare l'estensione del sistema e quindi continuare a eseguire il debug e di eseguirne il test in una normale istanza [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>Eseguire il debug e testare l'estensione in un'istanza sperimentale di Visual Studio  
  
1.  Riavviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con credenziali amministrative e quindi aprire la soluzione ProjectExtensionPackage.  
  
2.  Avviare una build di debug del progetto scegliendo il **F5** chiave oppure sulla barra dei menu, scegliendo **Debug**, **Avvia debug**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Installa l'estensione in %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Project Property\1.0 e avvia un'istanza sperimentale di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
3.  Nell'istanza sperimentale di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], creare un progetto di SharePoint per una soluzione farm e utilizzare i valori predefiniti per gli altri valori nella procedura guidata.  
  
    1.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
    2.  Nella parte superiore del **nuovo progetto** finestra di dialogo scegliere **.NET Framework 3.5** nell'elenco delle versioni di .NET Framework.  
  
         Estensioni di strumenti di SharePoint richiedono funzionalità in questa versione di [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
    3.  Sotto il **modelli** nodo, espandere il **Visual c#** o **Visual Basic** nodo, scegliere il **SharePoint** nodo e quindi scegliere il **2010** nodo.  
  
    4.  Scegliere il **progetto SharePoint 2010** modello, quindi immettere **ModuleTest** come il nome del progetto.  
  
4.  In **Esplora**, scegliere il **ModuleTest** nodo del progetto.  
  
     Una nuova proprietà personalizzata **cartella immagini mappa** è presente il **proprietà** finestra con un valore predefinito di **False**.  
  
5.  Modificare il valore di quella proprietà **True**.  
  
     Una cartella di risorse immagini viene aggiunto al progetto SharePoint.  
  
6.  Il valore della proprietà di nuovo su **False**.  
  
     Se si sceglie il **Sì** pulsante il **eliminare la cartella immagini?** la finestra di dialogo, le immagini di risorsa viene eliminata dal progetto SharePoint.  
  
7.  Chiudere l'istanza sperimentale di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di progetti SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Procedura: aggiungere una proprietà ai progetti SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Conversione tra tipi di sistema di progetto SharePoint e altri tipi di progetto di Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Salvataggio dei dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Associazione di dati personalizzati alle estensioni degli strumenti di SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  