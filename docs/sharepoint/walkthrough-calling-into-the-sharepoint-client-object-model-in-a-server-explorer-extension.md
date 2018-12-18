---
title: "Procedura dettagliata: Chiamata nel modello a oggetti Client di SharePoint in un'estensione di Esplora Server | Documenti Microsoft"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint commands [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4951d9960a3027e8d72bb0fbc72d551f123993ce
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>Procedura dettagliata: chiamata al modello a oggetti del client di SharePoint in un'estensione di Esplora server
  Questa procedura dettagliata illustra come chiamare il modello a oggetti client SharePoint da un'estensione per il **connessioni di SharePoint** nodo **Esplora Server**. Per ulteriori informazioni su come usare il modello a oggetti client SharePoint, vedere [chiamate ai modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
 In questa procedura dettagliata vengono descritte le attività seguenti:  
  
-   Creazione di un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] estensione che consente di estendere il **connessioni di SharePoint** nodo di **Esplora Server** nei modi seguenti:  
  
    -   Aggiunge l'estensione un **raccolta Web Part** nodo in ogni nodo del sito di SharePoint in **Esplora Server**. Il nuovo nodo contiene nodi figlio che rappresentano ogni Web Part nella raccolta di Web Part nel sito.  
  
    -   L'estensione di definire un nuovo tipo di nodo che rappresenta un'istanza della Web Part. Questo nuovo tipo di nodo è la base per i nodi figlio sotto il nuovo **raccolta Web Part** nodo. Visualizza le informazioni in nuovo tipo di nodo di Web Part di **proprietà** finestra sulla Web Part che rappresenta il nodo.  
  
-   Compilazione di un pacchetto di Visual Studio Extension (VSIX) per distribuire l'estensione.  
  
-   Il debug e test dell'estensione.  
  
> [!NOTE]  
>  L'estensione che viene creato in questa procedura dettagliata è simile all'estensione che crea in [procedura dettagliata: estensione di Esplora Server per visualizzare Web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md). Tale procedura dettagliata Usa il modello a oggetti SharePoint server, ma questa procedura dettagliata è eseguita la stessa operazione usando il modello a oggetti client.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Sono necessari i seguenti componenti nel computer di sviluppo per completare questa procedura dettagliata:  
  
-   Le edizioni supportate di Windows, SharePoint e Visual Studio. Per ulteriori informazioni, vedere [requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio SDK. Questa procedura dettagliata Usa il **progetto VSIX** modello nel SDK per creare un pacchetto VSIX per distribuire l'estensione. Per ulteriori informazioni, vedere [estensione degli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
Conoscere i concetti seguenti è utile, ma non obbligatorio, per completare la procedura dettagliata:  
  
-   Utilizzo del modello di oggetto client di SharePoint. Per ulteriori informazioni, vedere [modello a oggetti Client gestito](http://go.microsoft.com/fwlink/?LinkId=177797).  
  
-   Web part in SharePoint. Per ulteriori informazioni, vedere [panoramica delle parti Web](http://go.microsoft.com/fwlink/?LinkId=177803).  
  
## <a name="creating-the-projects"></a>Creazione dei progetti  
 Per completare questa procedura dettagliata, è necessario creare due progetti:  
  
-   Un progetto VSIX per creare il pacchetto VSIX per distribuire il **Esplora Server** estensione.  
  
-   Un progetto libreria di classi che implementa il **Esplora Server** estensione.  
  
 Avviare la procedura dettagliata creando i progetti.  
  
#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
3.  Nel **nuovo progetto** finestra di dialogo espandere il **Visual c#** o **Visual Basic** nodi, quindi scegliere **estendibilità**.  
  
    > [!NOTE]  
    >  Il **estendibilità** nodo è disponibile solo se si installa Visual Studio SDK. Per ulteriori informazioni, vedere la sezione Prerequisiti in questo argomento.  
  
4.  Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5** nell'elenco delle versioni di .NET Framework.  
  
     Estensioni di strumenti di SharePoint richiedono caratteristiche disponibili in questa versione di .NET Framework.  
  
5.  Scegliere il **progetto VSIX** modello.  
  
6.  Nel **nome** digitare **WebPartNode**, quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **WebPartNode** progetto **Esplora**.  
  
#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il nodo della soluzione, scegliere **Aggiungi**, quindi scegliere **nuovo progetto**.  
  
2.  Nel **nuovo progetto** finestra di dialogo espandere il **Visual c#** o **Visual Basic** nodi, quindi scegliere **Windows**.  
  
3.  Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5** nell'elenco delle versioni di .NET Framework.  
  
4.  Nell'elenco dei modelli di progetto, scegliere **libreria di classi**.  
  
5.  Nel **nome** immettere **risorse**, quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **risorse** progetto alla soluzione e apre il file di codice predefinito Class1.  
  
6.  Eliminare il file di codice Class1 dal progetto.  
  
## <a name="configuring-the-extension-project"></a>Configurazione del progetto di estensione  
 Prima di scrivere codice per creare l'estensione, è necessario aggiungere i file di codice e i riferimenti ad assembly al progetto e sarà necessario aggiornare lo spazio dei nomi predefinito.  
  
#### <a name="to-configure-the-project"></a>Per configurare il progetto  
  
1.  Nel **risorse** del progetto, aggiungere due file di codice denominati SiteNodeExtension e WebPartNodeTypeProvider.  
  
2.  Aprire il menu di scelta rapida per il progetto di risorse e quindi scegliere **Aggiungi riferimento**.  
  
3.  Nel **gestione riferimenti - risorse** finestra di dialogo scegliere la **Framework** nodo e quindi selezionare le caselle di controllo per il ComponentModel e Forms assembly.  
  
4.  Scegliere il **estensioni** nodo, selezionare la casella di controllo per ognuno degli assembly seguenti e quindi scegliere il **OK** pulsante:  
  
    -   Microsoft.SharePoint.Client  
  
    -   Microsoft.SharePoint.Client.Runtime  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Aprire il menu di scelta rapida per il **risorse** del progetto e quindi scegliere **proprietà**.  
  
     Si apre la finestra **Creazione progetti**.  
  
6.  Scegliere la scheda **Applicazione**.  
  
7.  Nel **spazio dei nomi predefinito** casella (c#) o **spazio dei nomi radice** (Visual Basic), immettere **ServerExplorer.SharePointConnections.WebPartNode**.  
  
## <a name="creating-icons-for-the-new-nodes"></a>Creazione di icone per i nuovi nodi  
 Creare due icone per il **Esplora Server** estensione: un'icona per il nuovo **raccolta Web Part** nodo e un'altra icona per ogni nodo della Web Part figlio sotto il **raccolta Web Part** nodo. Più avanti in questa procedura dettagliata, verrà scritto il codice che associa queste icone con i nodi.  
  
#### <a name="to-create-icons-for-the-nodes"></a>Per creare le icone per i nodi  
  
1.  Nel **progettazione** risorse per il progetto, scegliere il **risorse** scheda.  
  
2.  Scegliere il collegamento **questo progetto non contiene un file di risorse predefinito. Fare clic qui per crearne uno.**  
  
     Visual Studio crea un file di risorse e verrà aperto nella finestra di progettazione.  
  
3.  Nella parte superiore della finestra di progettazione, scegliere la freccia di **Aggiungi risorsa** menu comando e quindi scegliere **Aggiungi nuova icona**.  
  
4.  Immettere **WebPartsNode** dell'icona di nuovo nome e quindi scegliere il **Aggiungi** pulsante.  
  
     Verrà visualizzata l'icona di nuovo nel **Editor di immagini**.  
  
5.  Modificare la versione di 16x16 dell'icona in modo che abbia una progettazione che è possibile riconoscere facilmente.  
  
6.  Aprire il menu di scelta rapida per la versione a 32 x 32 dell'icona e quindi scegliere **eliminare tipo di immagine**.  
  
7.  Ripetere i passaggi da 3 a 7 per aggiungere una seconda icona alle risorse del progetto e denominare questa icona **WebPart**.  
  
8.  In **Esplora**nella **risorse** cartella per il **risorse** del progetto, scegliere **WebPartNodeExtension**.  
  
9. Nel **proprietà** finestra, aprire il **azione di compilazione** elenco e quindi scegliere **risorsa incorporata**.  
  
10. Ripetere gli ultimi due passaggi per **WebPart**.  
  
## <a name="adding-the-web-part-gallery-node-to-server-explorer"></a>Aggiungere il nodo di raccolta Web Part a Esplora Server  
 Creare una classe che aggiunge il nuovo **raccolta Web Part** nodo per ogni nodo del sito di SharePoint. Per aggiungere il nuovo nodo, la classe implementa il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfaccia. Implementare questa interfaccia ogni volta che si desidera estendere il comportamento di un nodo esistente nel **Esplora Server**, ad esempio l'aggiunta di un nuovo nodo figlio a un nodo.  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Per aggiungere il nodo di raccolta Web Part a Esplora Server  
  
1.  Incollare il codice seguente nel **SiteNodeExtension** file di codice per il **risorse** progetto.  
  
    > [!NOTE]  
    >  Dopo aver aggiunto questo codice, il progetto avrà degli errori di compilazione. Questi errori non verranno più visualizzato quando si aggiunge il codice nei passaggi successivi.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="defining-a-node-type-that-represents-a-web-part"></a>Definisce un tipo di nodo che rappresenta una Web Part  
 Creare una classe che definisce un nuovo tipo di nodo che rappresenta una Web Part. Visual Studio utilizza questo nuovo tipo di nodo per visualizzare i nodi figlio sotto il **raccolta Web Part** nodo. Ognuno di questi nodi figlio rappresenta una singola parte Web nel sito di SharePoint.  
  
 Per definire il nuovo tipo di nodo, la classe implementa il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfaccia. Implementare questa interfaccia ogni volta che si desidera definire un nuovo tipo di nodo **Esplora Server**.  
  
#### <a name="to-define-the-web-part-node-type"></a>Per definire il tipo di nodo della Web Part  
  
1.  Incollare il codice seguente nel **WebPartNodeTypeProvider** file di codice per il **risorse** progetto.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## <a name="checkpoint"></a>Checkpoint  
 A questo punto della procedura dettagliata, tutto il codice per il **raccolta Web Part** nodo è nel progetto. Compilare il **risorse** progetto per assicurarsi che l'operazione avvenga senza errori.  
  
#### <a name="to-build-the-project"></a>Per compilare il progetto  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il **risorse** del progetto e quindi scegliere **compilare**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-extension"></a>Creazione di un pacchetto VSIX per distribuire l'estensione  
 Per distribuire l'estensione, è possibile utilizzare il progetto VSIX nella soluzione per creare un pacchetto VSIX. Innanzitutto, configurare il pacchetto VSIX modificando il file vsixmanifest incluso nel progetto. Quindi creare il pacchetto VSIX per la compilazione della soluzione.  
  
#### <a name="to-configure-the-vsix-package"></a>Per configurare il pacchetto VSIX  
  
1.  In **Esplora**nella **WebPartNode** progetto, aprire **vsixmanifest** file nell'editor del manifesto.  
  
     Il file vsixmanifest è la base per il file extension vsixmanifest che richiedono tutti i pacchetti VSIX. Per ulteriori informazioni su questo file, vedere [riferimento 1.0 dello Schema di estensione VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Nel **Product Name** immettere **nodo di raccolta Web Part per Esplora Server**.  
  
3.  Nel **autore** immettere **Contoso**.  
  
4.  Nel **descrizione** immettere **aggiunge un nodo di raccolta Web Part personalizzato al nodo Connessioni di SharePoint in Esplora Server**.  
  
5.  Nel **asset** scheda dell'editor, scegliere il **New** pulsante.  
  
6.  Nel **Aggiungi nuovo Asset** della finestra di dialogo di **tipo** scegliere **MEFComponent**.  
  
    > [!NOTE]  
    >  Questo valore corrisponde al `MefComponent` elemento nel file Extension. vsixmanifest. Questo elemento specifica il nome di un assembly di estensione nel pacchetto VSIX. Per ulteriori informazioni, vedere [elemento MEFComponent (schema VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  Nel **origine** scegliere **un progetto nella soluzione corrente**.  
  
8.  Nel **progetto** scegliere **risorse**, quindi scegliere il **OK** pulsante.  
  
9. Nella barra dei menu, scegliere **compilare**, **Compila soluzione**, quindi assicurarsi che la soluzione venga compilata senza errori.  
  
10. Assicurarsi che la cartella di output di compilazione per il progetto WebPartNode contiene ora il file WebPartNode.  
  
     Per impostazione predefinita, la cartella di output di compilazione è il... nella cartella \bin\Debug sotto la cartella che contiene il file di progetto.  
  
## <a name="testing-the-extension"></a>Test dell'estensione  
 A questo punto si è pronti testare il nuovo **raccolta Web Part** nodo **Esplora Server**. Innanzitutto, avviare il debug del progetto di estensione in un'istanza sperimentale di Visual Studio. Quindi usare il nuovo **Web part** nodo nell'istanza sperimentale di Visual Studio.  
  
#### <a name="to-start-debugging-the-extension"></a>Per avviare il debug dell'estensione  
  
1.  Riavviare Visual Studio con credenziali amministrative e quindi aprire il **WebPartNode** soluzione.  
  
2.  Nel progetto di risorse, aprire il **SiteNodeExtension** file di codice e quindi aggiungere un punto di interruzione per le righe di codice il `NodeChildrenRequested` e `CreateWebPartNodes` metodi.  
  
3.  Premere il tasto F5 per avviare il debug.  
  
     Visual Studio installa l'estensione per %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web Part Gallery Node Extension for Server Explorer\1.0 e avvia un'istanza sperimentale di Visual Studio. L'elemento del progetto verrà testato in questa istanza di Visual Studio.  
  
#### <a name="to-test-the-extension"></a>Per testare l'estensione  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **vista**, **Esplora Server**.  
  
2.  Verificare che il sito di SharePoint che si desidera utilizzare per il test venga visualizzato sotto il **connessioni di SharePoint** nodo **Esplora Server**. Se non è elencato, seguire questi passaggi:  
  
    1.  Aprire il menu di scelta rapida per **connessioni di SharePoint**, quindi scegliere **Aggiungi connessione**.  
  
    2.  Nel **Aggiungi connessione SharePoint** finestra di dialogo immettere l'URL per il sito di SharePoint a cui si desidera connettersi, quindi scegliere il **OK** pulsante.  
  
         Per specificare il sito di SharePoint nel computer di sviluppo, digitare **http://localhost**.  
  
3.  Espandere il nodo della connessione del sito, che visualizza l'URL del sito, e quindi espandere un nodo di sito figlio (ad esempio, **sito del Team**).  
  
4.  Verificare che il codice in altra istanza di Visual Studio si arresta nel punto di interruzione impostato precedentemente nel `NodeChildrenRequested` (metodo), quindi scegliere il tasto F5 per continuare il debug del progetto.  
  
5.  Nell'istanza sperimentale di Visual Studio, espandere il **raccolta Web Part** nodo, viene visualizzata sotto il nodo di sito di livello superiore.  
  
6.  Verificare che il codice in altra istanza di Visual Studio si arresta nel punto di interruzione impostato precedentemente nel `CreateWebPartNodes` (metodo), quindi scegliere il tasto F5 per continuare il debug del progetto.  
  
7.  Nell'istanza sperimentale di Visual Studio, verificare che tutte le Web part sul sito connesso vengono visualizzati sotto il **raccolta Web Part** nodo **Esplora Server**.  
  
8.  Aprire il menu di scelta rapida per una Web Part e quindi scegliere **proprietà**.  
  
9. Nel **proprietà** finestra, verificare che siano visualizzati i dettagli relativi alla Web Part.  
  
10. In **Esplora Server**, aprire il menu di scelta rapida per la stessa di Web Part e quindi scegliere **Visualizza un messaggio**.  
  
     Nella finestra di messaggio che viene visualizzato, scegliere il **OK** pulsante.  
  
## <a name="uninstalling-the-extension-from-visual-studio"></a>La disinstallazione dell'estensione da Visual Studio  
 Dopo aver completato l'estensione per il testing, disinstallarlo da Visual Studio.  
  
#### <a name="to-uninstall-the-extension"></a>Per disinstallare l'estensione  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **strumenti**, **estensioni e aggiornamenti**.  
  
     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.  
  
2.  Nell'elenco di estensioni, scegliere **nodo di raccolta Web Part per Esplora Server**, quindi scegliere il **Disinstalla** pulsante.  
  
3.  Nella finestra di dialogo visualizzata, scegliere il **Sì** pulsante.  
  
4.  Scegliere il **Riavvia ora** per completare la disinstallazione.  
  
     Viene disinstallato anche l'elemento del progetto.  
  
5.  Chiudere entrambe le istanze di Visual Studio (l'istanza sperimentale e l'istanza di Visual Studio in cui la soluzione WebPartNode è aperta).  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamate ai modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Estensione del nodo Connessioni di SharePoint in Esplora Server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Procedura dettagliata: Estensione di Esplora Server per visualizzare le Web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Image Editor for Icons](/cpp/windows/image-editor-for-icons)  (Editor di immagini per icone)  
 [Creazione di un'icona o un'altra immagine &#40;Editor di immagini per le icone&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  