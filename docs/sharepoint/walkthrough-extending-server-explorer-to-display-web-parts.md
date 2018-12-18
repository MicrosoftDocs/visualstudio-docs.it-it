---
title: 'Procedura dettagliata: Estensione di Esplora Server per visualizzare Web part | Documenti Microsoft'
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
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint commands
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e8b613f19a23bdb60452b50cf927af08b399d180
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-extending-server-explorer-to-display-web-parts"></a>Procedura dettagliata: estensione di Esplora server per visualizzare web part
  In Visual Studio, è possibile utilizzare il **connessioni di SharePoint** nodo di **Esplora Server** per visualizzare i componenti nei siti di SharePoint. Tuttavia, **Esplora Server** non visualizza alcuni componenti per impostazione predefinita. In questa procedura dettagliata, è possibile estendere **Esplora Server** in modo che venga visualizzato della raccolta Web Part in ciascuno connesso a un sito di SharePoint.  
  
 In questa procedura dettagliata vengono descritte le attività seguenti:  
  
-   Creazione di un'estensione di Visual Studio che estende **Esplora Server** nei modi seguenti:  
  
    -   Aggiunge l'estensione un **raccolta Web Part** nodo in ogni nodo del sito di SharePoint in **Esplora Server**. Il nuovo nodo contiene nodi figlio che rappresentano ogni Web Part nella raccolta di Web Part nel sito.  
  
    -   L'estensione di definire un nuovo tipo di nodo che rappresenta un'istanza della Web Part. Questo nuovo tipo di nodo è la base per i nodi figlio sotto il nuovo **raccolta Web Part** nodo. Visualizza le informazioni in nuovo tipo di nodo di Web Part di **proprietà** finestra sulla Web Part che rappresenta. Il tipo di nodo include anche una voce di menu di scelta rapida personalizzati che è possibile utilizzare come punto di partenza per l'esecuzione di altre attività relative alla Web Part.  
  
-   La creazione di due comandi di SharePoint che le chiamate di assembly di estensione. I comandi di SharePoint sono metodi che possono essere chiamati da assembly di estensione, usare le API nel modello a oggetti server per SharePoint. In questa procedura dettagliata, è creare comandi che recuperano informazioni del Web Part dal sito di SharePoint locale nel computer di sviluppo. Per ulteriori informazioni, vedere [chiamate ai modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Compilazione di un pacchetto di Visual Studio Extension (VSIX) per distribuire l'estensione.  
  
-   Il debug e test dell'estensione.  
  
> [!NOTE]  
>  Per una versione alternativa di questa procedura dettagliata che utilizza il modello a oggetti client per SharePoint anziché il modello a oggetti server, vedere [procedura dettagliata: chiamata al modello di oggetto Client di SharePoint in un'estensione di Esplora Server](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Sono necessari i seguenti componenti nel computer di sviluppo per completare questa procedura dettagliata:  
  
-   Le edizioni supportate di Windows, SharePoint e Visual Studio. Per ulteriori informazioni, vedere [requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio SDK. Questa procedura dettagliata Usa il **progetto VSIX** modello nel SDK per creare un pacchetto VSIX per distribuire l'elemento del progetto. Per ulteriori informazioni, vedere [estensione degli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Conoscere i concetti seguenti è utile, ma non obbligatorio, per completare la procedura dettagliata:  
  
-   Utilizzando il modello a oggetti server per SharePoint. Per ulteriori informazioni, vedere [utilizzando il modello a oggetti lato Server SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
-   Web part di soluzioni di SharePoint. Per ulteriori informazioni, vedere [panoramica delle parti Web](http://go.microsoft.com/fwlink/?LinkId=177803).  
  
## <a name="creating-the-projects"></a>Creazione dei progetti  
 Per completare questa procedura dettagliata, è necessario creare tre progetti:  
  
-   Un progetto VSIX per creare il pacchetto VSIX per distribuire l'estensione.  
  
-   Un progetto libreria di classi che implementa l'estensione. Questo progetto deve avere come destinazione di .NET Framework 4.5.  
  
-   Un progetto libreria di classi che definisce i comandi di SharePoint personalizzati. Questo progetto deve avere come destinazione.NET Framework 3.5.  
  
 Avviare la procedura dettagliata creando i progetti.  
  
#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
3.  Nel **nuovo progetto** finestra di dialogo espandere il **Visual c#** o **Visual Basic** nodi e quindi scegliere il **estendibilità** nodo.  
  
    > [!NOTE]  
    >  Il **estendibilità** nodo è disponibile solo se si installa Visual Studio SDK. Per ulteriori informazioni, vedere la sezione Prerequisiti in questo argomento.  
  
4.  Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5** nell'elenco delle versioni di .NET Framework.  
  
5.  Scegliere il **progetto VSIX** modello, denominare il progetto **WebPartNode**, quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Aggiunge il **WebPartNode** progetto **Esplora**.  
  
#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il nodo della soluzione, scegliere **Aggiungi**, quindi scegliere **nuovo progetto**.  
  
2.  Nel **nuovo progetto** finestra di dialogo espandere il **Visual c#** nodo o **Visual Basic** nodo, quindi scegli **Windows** nodo.  
  
3.  Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5** nell'elenco delle versioni di .NET Framework.  
  
4.  Nell'elenco dei modelli di progetto, scegliere **libreria di classi**, denominare il progetto **risorse**, quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Aggiunge il **risorse** progetto alla soluzione e apre il file di codice predefinito Class1.  
  
5.  Eliminare il file di codice Class1 dal progetto.  
  
#### <a name="to-create-the-sharepoint-commands-project"></a>Per creare il progetto di comandi di SharePoint  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il nodo della soluzione, scegliere **Aggiungi**, quindi scegliere **nuovo progetto**.  
  
2.  Nel **nuovo progetto** finestra di dialogo, espandere il **Visual c#** nodo o **Visual Basic** nodo, quindi scegliere il **Windows** nodo.  
  
3.  Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 3.5** nell'elenco delle versioni di .NET Framework.  
  
4.  
  
5.  Nell'elenco dei modelli di progetto, scegliere **libreria di classi**, denominare il progetto **WebPartCommands**, quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Aggiunge il **WebPartCommands** progetto alla soluzione e apre il file di codice predefinito Class1.  
  
6.  Eliminare il file di codice Class1 dal progetto.  
  
## <a name="configuring-the-projects"></a>Configurazione dei progetti  
 Prima di scrivere codice per creare l'estensione, è necessario aggiungere i file di codice e i riferimenti agli assembly e configurare le impostazioni di progetto.  
  
#### <a name="to-configure-the-webpartnodeextension-project"></a>Per configurare il progetto di risorse  
  
1.  Nel progetto di risorse, aggiungere quattro file di codice che presentano i nomi seguenti:  
  
    -   SiteNodeExtension  
  
    -   WebPartNodeTypeProvider  
  
    -   WebPartNodeInfo  
  
    -   WebPartCommandIds  
  
2.  Aprire il menu di scelta rapida per il **risorse** del progetto e quindi scegliere **Aggiungi riferimento**.  
  
3.  Nel **gestione riferimenti - risorse** finestra di dialogo scegliere la **Framework** scheda e quindi selezionare la casella di controllo per ognuno degli assembly seguenti:  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
4.  Scegliere il **estensioni** scheda, selezionare la casella di controllo per l'assembly Microsoft.VisualStudio.SharePoint e quindi scegliere il **OK** pulsante.  
  
5.  In **Esplora**, aprire il menu di scelta rapida per il **risorse** nodo del progetto e quindi scegliere **proprietà**.  
  
     Si apre la finestra **Creazione progetti**.  
  
6.  Scegliere la scheda **Applicazione**.  
  
7.  Nel **spazio dei nomi predefinito** casella (c#) o **spazio dei nomi radice** casella ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), immettere **ServerExplorer.SharePointConnections.WebPartNode**.  
  
#### <a name="to-configure-the-webpartcommands-project"></a>Per configurare il progetto WebPartCommands  
  
1.  Nel progetto WebPartCommands, aggiungere un file di codice denominato WebPartCommands.  
  
2.  In **Esplora**, aprire il menu di scelta rapida per il **WebPartCommands** nodo del progetto, scegliere **Aggiungi**, quindi scegliere **elemento esistente**.  
  
3.  Nel **Aggiungi elemento esistente** nella finestra di dialogo selezionare la cartella che contiene i file di codice risorse per il progetto e quindi scegliere i file di codice WebPartNodeInfo e WebPartCommandIds.  
  
4.  Scegliere la freccia accanto al **Aggiungi** e quindi scegliere **Aggiungi come collegamento** nel menu visualizzato.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Aggiunge i file di codice al progetto WebPartCommands come collegamenti. Di conseguenza, i file di codice si trovano nel progetto di risorse, ma il codice nei file vengono compilati nel progetto WebPartCommands.  
  
5.  Aprire il menu di scelta rapida per il **WebPartCommands** nuovo progetto e scegliere **Aggiungi riferimento**.  
  
6.  Nel **gestione riferimenti - WebPartCommands** finestra di dialogo scegliere la **estensioni** scheda, selezionare la casella di controllo per ognuno degli assembly seguenti e quindi scegliere il **OK** pulsante:  
  
    -   Microsoft. SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
7.  In **Esplora**, aprire il menu di scelta rapida per il **WebPartCommands** nuovo progetto e quindi scegliere **proprietà**.  
  
     Si apre la finestra **Creazione progetti**.  
  
8.  Scegliere la scheda **Applicazione**.  
  
9. Nel **spazio dei nomi predefinito** casella (c#) o **spazio dei nomi radice** casella ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), immettere **ServerExplorer.SharePointConnections.WebPartNode**.  
  
## <a name="creating-icons-for-the-new-nodes"></a>Creazione di icone per i nuovi nodi  
 Creare due icone per il **Esplora Server** estensione: un'icona per il nuovo **raccolta Web Part** nodo e un'altra icona per ogni nodo della Web Part figlio sotto il **raccolta Web Part** nodo. Più avanti in questa procedura dettagliata, si scriverà il codice che associa queste icone con i nodi.  
  
#### <a name="to-create-icons-for-the-nodes"></a>Per creare le icone per i nodi  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il **risorse** del progetto e quindi scegliere **proprietà**.  
  
2.  Si apre la finestra **Creazione progetti**.  
  
3.  Scegliere il **risorse** scheda e quindi scegliere il **questo progetto non contiene un file di risorse predefinito. Fare clic qui per crearne uno** collegamento.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Crea un file di risorse, che verrà aperto nella finestra di progettazione.  
  
4.  Nella parte superiore della finestra di progettazione, scegliere la freccia accanto al **Aggiungi risorsa** menu comando e quindi scegliere **Aggiungi nuova icona** nel menu visualizzato.  
  
5.  Nel **Aggiungi nuova risorsa** sull'icona Nuovo nome nella finestra di dialogo **WebPartsNode**, quindi scegliere il **Aggiungi** pulsante.  
  
     Verrà visualizzata l'icona di nuovo nel **Editor di immagini**.  
  
6.  Modificare la versione di 16x16 dell'icona in modo che abbia una progettazione che è possibile riconoscere facilmente.  
  
7.  Aprire il menu di scelta rapida per la versione a 32 x 32 dell'icona e quindi scegliere **eliminare tipo di immagine**.  
  
8.  Ripetere i passaggi da 5 a 8 per aggiungere una seconda icona alle risorse del progetto e denominare questa icona **WebPart**.  
  
9. In **Esplora**, sotto il **risorse** cartella per il **risorse** del progetto, aprire il menu di scelta rapida per **WebPartNodeExtension**.  
  
10. Nel **proprietà** finestra, scegliere la freccia accanto a **azione di compilazione**, quindi scegliere **risorsa incorporata** dal menu visualizzato.  
  
11. Ripetere gli ultimi due passaggi per **WebPart**.  
  
## <a name="adding-the-web-part-gallery-node-to-server-explorer"></a>Aggiungere il nodo di raccolta Web Part a Esplora Server  
 Creare una classe che aggiunge il nuovo **raccolta Web Part** nodo per ogni nodo del sito di SharePoint. Per aggiungere il nuovo nodo, la classe implementa il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfaccia. Implementare questa interfaccia ogni volta che si desidera estendere il comportamento di un nodo esistente nel **Esplora Server**, ad esempio l'aggiunta di un nodo figlio a un nodo.  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Per aggiungere il nodo di raccolta Web Part a Esplora Server  
  
1.  Nel progetto di risorse, aprire il file di codice SiteNodeExtension e quindi incollare il codice seguente.  
  
    > [!NOTE]  
    >  Dopo che si aggiunge questo codice, il progetto avrà degli errori di compilazione, ma si sarà più visualizzato quando si aggiunge codice nei passaggi successivi.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="defining-a-node-type-that-represents-a-web-part"></a>Definisce un tipo di nodo che rappresenta una Web Part  
 Creare una classe che definisce un nuovo tipo di nodo che rappresenta una Web Part. Visual Studio utilizza questo nuovo tipo di nodo per visualizzare i nodi figlio sotto il **raccolta Web Part** nodo. Ogni nodo figlio rappresenta un singolo Web Part nel sito di SharePoint.  
  
 Per definire il nuovo tipo di nodo, la classe implementa il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfaccia. Implementare questa interfaccia ogni volta che si desidera definire un nuovo tipo di nodo **Esplora Server**.  
  
#### <a name="to-define-the-web-part-node-type"></a>Per definire il tipo di nodo della Web Part  
  
1.  Nel progetto di risorse, aprire il file di codice WebPartNodeTypeProvider e quindi incollare il codice seguente.  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]  
  
## <a name="defining-the-web-part-data-class"></a>Definizione della classe di dati di Web Part  
 Definire una classe che contiene dati su una singola parte Web nel sito di SharePoint. Più avanti in questa procedura dettagliata, si creerà un comando di SharePoint personalizzato che recupera i dati su ogni Web Part nel sito e quindi assegna i dati a istanze di questa classe.  
  
#### <a name="to-define-the-web-part-data-class"></a>Per definire la classe di dati di Web Part  
  
1.  Nel progetto di risorse, aprire il file di codice WebPartNodeInfo e quindi incollare il codice seguente.  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]  
  
## <a name="defining-the-ids-for-the-sharepoint-command"></a>Definizione degli ID per il comando di SharePoint  
 Definire varie stringhe che identificano i comandi di SharePoint personalizzati. Questi comandi verrà implementata più avanti in questa procedura dettagliata.  
  
#### <a name="to-define-the-command-ids"></a>Per definire gli ID di comando  
  
1.  Nel progetto di risorse, aprire il file di codice WebPartCommandIds e quindi incollare il codice seguente.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]  
  
## <a name="creating-the-custom-sharepoint-commands"></a>Creazione di comandi personalizzati di SharePoint  
 Creare controlli personalizzati che effettuano chiamate nel modello a oggetti server per SharePoint recuperare i dati sulle Web part nel sito di SharePoint. Ogni comando è un metodo che presenta il <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> applicato.  
  
#### <a name="to-define-the-sharepoint-commands"></a>Per definire i comandi di SharePoint  
  
1.  Nel progetto WebPartCommands, aprire il file di codice WebPartCommands e quindi incollare il codice seguente.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]  
  
## <a name="checkpoint"></a>Checkpoint  
 A questo punto della procedura dettagliata, tutto il codice per il **raccolta Web Part** nodo e i comandi di SharePoint sono ora nei progetti. Compilare la soluzione per assicurarsi che entrambi i progetti compilato senza errori.  
  
#### <a name="to-build-the-solution"></a>Per compilare la soluzione  
  
1.  Nella barra dei menu scegliere **Compilazione**, **Compila soluzione**.  
  
    > [!WARNING]  
    >  A questo punto, il progetto WebPartNode riscontrino un errore di compilazione perché il file manifesto VSIX non contenga un valore per l'autore. Questo errore non verrà più visualizzato quando si aggiunge un valore nei passaggi successivi.  
  
## <a name="creating-a-vsix-package-to-deploy-the-extension"></a>Creazione di un pacchetto VSIX per distribuire l'estensione  
 Per distribuire l'estensione, è possibile utilizzare il progetto VSIX nella soluzione per creare un pacchetto VSIX. Innanzitutto, configurare il pacchetto VSIX modificando il file vsixmanifest nel progetto VSIX. Quindi, creare il pacchetto VSIX per la compilazione della soluzione.  
  
#### <a name="to-configure-the-vsix-package"></a>Per configurare il pacchetto VSIX  
  
1.  In **Esplora**, sotto il progetto WebPartNode, aprire il **vsixmanifest** file nell'editor del manifesto.  
  
     Il file vsixmanifest è la base per il file extension vsixmanifest che richiedono tutti i pacchetti VSIX. Per ulteriori informazioni su questo file, vedere [riferimento 1.0 dello Schema di estensione VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Nel **Product Name** immettere **nodo di raccolta Web Part per Esplora Server**.  
  
3.  Nel **autore** immettere **Contoso**.  
  
4.  Nel **descrizione** immettere **aggiunge un nodo di raccolta Web Part personalizzato al nodo Connessioni di SharePoint in Esplora Server. Questa estensione Usa un comando di SharePoint personalizzato per effettuare chiamate nel modello a oggetti server.**  
  
5.  Scegliere il **asset** scheda dell'editor, quindi scegliere il **New** pulsante.  
  
     Il **Aggiungi nuovo Asset** viene visualizzata la finestra di dialogo.  
  
6.  Nel **tipo** scegliere **MEFComponent**.  
  
    > [!NOTE]  
    >  Questo valore corrisponde al `MefComponent` elemento nel file Extension. vsixmanifest. Questo elemento specifica il nome di un assembly di estensione nel pacchetto VSIX. Per ulteriori informazioni, vedere [elemento MEFComponent (schema VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  Nel **origine** scegliere **un progetto nella soluzione corrente**.  
  
8.  Nel **progetto** scegliere **risorse** e quindi scegliere il **OK** pulsante.  
  
9. Nell'editor del manifesto, scegliere il **New** nuovamente clic sul pulsante.  
  
     Il **Aggiungi nuovo Asset** viene visualizzata la finestra di dialogo.  
  
10. Nel **tipo** immettere **v4**.  
  
    > [!NOTE]  
    >  Questo elemento specifica un'estensione personalizzata che si desidera includere nell'estensione di Visual Studio. Per ulteriori informazioni, vedere [elemento Asset (schema VSX)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. Nel **origine** scegliere il **un progetto nella soluzione corrente** voce di elenco.  
  
12. Nel **progetto** scegliere **WebPartCommands**, quindi scegliere il **OK** pulsante.  
  
13. Nella barra dei menu, scegliere **compilare**, **Compila soluzione**, quindi assicurarsi che la soluzione venga compilata senza errori.  
  
14. Assicurarsi che la cartella di output di compilazione per il progetto WebPartNode contiene ora il file WebPartNode.  
  
     Per impostazione predefinita, la cartella di output di compilazione è il... nella cartella \bin\Debug sotto la cartella che contiene il file di progetto.  
  
## <a name="testing-the-extension"></a>Test dell'estensione  
 Si è ora pronti per testare il nuovo **raccolta Web Part** nodo **Esplora Server**. Innanzitutto, avviare il debug dell'estensione in un'istanza sperimentale di Visual Studio. Quindi, usare il nuovo **Web part** nodo nell'istanza sperimentale di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-start-debugging-the-extension"></a>Per avviare il debug dell'estensione  
  
1.  Riavviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con credenziali amministrative e quindi aprire la soluzione WebPartNode.  
  
2.  Nel progetto di risorse, aprire il file di codice SiteNodeExtension e quindi aggiungere un punto di interruzione sulla prima riga di codice il `NodeChildrenRequested` e `CreateWebPartNodes` metodi.  
  
3.  Premere il tasto F5 per avviare il debug.  
  
     Visual Studio installa l'estensione per %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web Part Gallery Node Extension for Server Explorer\1.0 e avvia un'istanza sperimentale di Visual Studio. Si testerà l'elemento del progetto in questa istanza di Visual Studio.  
  
#### <a name="to-test-the-extension"></a>Per testare l'estensione  
  
1.  Nell'istanza sperimentale di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], sulla barra dei menu, scegliere **vista**, **Esplora Server**.  
  
2.  Eseguire la procedura seguente se il sito di SharePoint che si desidera utilizzare per il test non viene visualizzato sotto il **connessioni di SharePoint** nodo **Esplora Server**:  
  
    1.  In **Esplora Server**, aprire il menu di scelta rapida per **connessioni di SharePoint**, quindi scegliere **Aggiungi connessione**.  
  
    2.  Nel **Aggiungi connessione SharePoint** finestra di dialogo immettere l'URL per il sito di SharePoint a cui si desidera connettersi, quindi scegliere il **OK** pulsante.  
  
         Per specificare il sito di SharePoint nel computer di sviluppo, immettere **http://localhost**.  
  
3.  Espandere il nodo della connessione del sito, che visualizza l'URL del sito, e quindi espandere un nodo di sito figlio (ad esempio, **sito del Team**).  
  
4.  Verificare che il codice in altra istanza di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] si interrompe al punto di interruzione impostati in precedenza il `NodeChildrenRequested` (metodo) e premi F5 per continuare il debug del progetto.  
  
5.  Nell'istanza sperimentale di Visual Studio, verificare che un nuovo nodo denominato **raccolta Web Part** sotto il nodo di sito di livello superiore e quindi espandere il **raccolta Web Part** nodo.  
  
6.  Verificare che il codice in altra istanza di Visual Studio si arresta nel punto di interruzione impostato precedentemente nel `CreateWebPartNodes` (metodo), quindi scegliere il tasto F5 per continuare il debug del progetto.  
  
7.  Nell'istanza sperimentale di Visual Studio, verificare che tutte le Web part sul sito connesso siano visualizzate sotto il **raccolta Web Part** nodo **Esplora Server**.  
  
8.  In **Esplora Server**, aprire il menu di scelta rapida per una delle Web part e quindi scegliere **proprietà**.  
  
9. Nell'istanza di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] che si esegue il debug, verificare che siano visualizzati i dettagli relativi alla Web Part di **proprietà** finestra.  
  
## <a name="uninstalling-the-extension-from-visual-studio"></a>La disinstallazione dell'estensione da Visual Studio  
 Dopo aver completato l'estensione per il testing, è possibile disinstallare l'estensione da Visual Studio.  
  
#### <a name="to-uninstall-the-extension"></a>Per disinstallare l'estensione  
  
1.  Nell'istanza sperimentale di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], sulla barra dei menu, scegliere **strumenti**, **estensioni e aggiornamenti**.  
  
     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.  
  
2.  Nell'elenco di estensioni, scegliere **nodo raccolta Web Part Extension per Esplora Server**, quindi scegliere il **Disinstalla** pulsante.  
  
3.  Nella finestra di dialogo visualizzata, scegliere il **Sì** pulsante per confermare che si desidera disinstallare l'estensione e quindi scegliere il **Riavvia ora** per completare la disinstallazione.  
  
4.  Chiudere entrambe le istanze di Visual Studio (l'istanza sperimentale e l'istanza di Visual Studio in cui la soluzione WebPartNode è aperta).  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione del nodo Connessioni di SharePoint in Esplora Server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Procedura dettagliata: Chiamata nel modello a oggetti Client di SharePoint in un'estensione di Esplora Server](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)   
 [Image Editor for Icons](/cpp/windows/image-editor-for-icons)  (Editor di immagini per icone)  
 [Creazione di un'icona o altra immagine &#40; Editor di immagini per le icone &#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  