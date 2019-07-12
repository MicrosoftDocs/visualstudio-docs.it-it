---
title: 'Procedura dettagliata: Estensione di Esplora Server per visualizzare le Web part | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint commands
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1c84cfcde4a5ffac1e1563a4d2b141bd6240b772
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67821996"
---
# <a name="walkthrough-extend-server-explorer-to-display-web-parts"></a>Procedura dettagliata: Estendere Esplora Server per visualizzare le web part
  In Visual Studio, è possibile usare la **connessioni di SharePoint** nodo **Esplora Server** per visualizzare i componenti nei siti di SharePoint. Tuttavia **Esplora Server** non visualizza alcuni componenti per impostazione predefinita. In questa procedura dettagliata verrà illustrato come estendere **Esplora Server** in modo che venga visualizzato della raccolta Web Part in ciascuna connessa sito di SharePoint.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di un'estensione di Visual Studio che estende **Esplora Server** nei modi seguenti:

  - L'estensione aggiunge un **raccolta Web Part** nodo in ogni nodo nel sito di SharePoint **Esplora Server**. Il nuovo nodo contiene i nodi figlio che rappresentano ogni Web Part nella raccolta di Web Part sul sito.

  - L'estensione definisce un nuovo tipo di nodo che rappresenta un'istanza di Web Part. Questo nuovo tipo di nodo è la base per i nodi figlio sotto la nuova **raccolta Web Part** nodo. Il nuovo tipo di nodo di Web Part Visualizza le informazioni nel **proprietà** finestra sulla Web Part da essa rappresentato. Il tipo di nodo include anche una voce di menu di scelta rapida personalizzati che è possibile usare come punto di partenza per l'esecuzione di altre attività correlate alla Web Part.

- Creare due comandi di SharePoint personalizzati che chiama l'assembly dell'estensione. I comandi di SharePoint sono metodi che possono essere chiamati dagli assembly di estensione per usare le API nel modello a oggetti server per SharePoint. In questa procedura dettagliata, è creare i comandi che recuperano informazioni di Web Part dal sito di SharePoint locale nel computer di sviluppo. Per altre informazioni, vedere [chiamare i modelli a oggetti SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

- Creazione di un pacchetto di Visual Studio Extension (VSIX) per distribuire l'estensione.

- Il debug e l'estensione per il testing.

> [!NOTE]
> Per una versione alternativa di questa procedura dettagliata che usa il modello a oggetti client di SharePoint anziché il modello a oggetti server, vedere [procedura dettagliata: Chiamare il modello a oggetti client SharePoint in un'estensione di Esplora Server](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).

## <a name="prerequisites"></a>Prerequisiti
 Sono necessari i componenti seguenti nel computer di sviluppo per completare questa procedura dettagliata:

- Edizioni supportate di Windows, SharePoint e Visual Studio.

- Visual Studio SDK. Questa procedura dettagliata Usa il **progetto VSIX** modello nel SDK per creare un pacchetto VSIX per distribuire l'elemento del progetto. Per altre informazioni, vedere [estendere gli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Conoscenza dei concetti seguenti è utile, ma non obbligatorio, completare la procedura dettagliata:

- Usando il modello a oggetti server per SharePoint. Per altre informazioni, vedere [usando il modello a oggetti lato Server SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177796).

- Web part in soluzioni di SharePoint. Per altre informazioni, vedere [Web Parts Overview](http://go.microsoft.com/fwlink/?LinkId=177803).

## <a name="create-the-projects"></a>Creare i progetti
 Per completare questa procedura dettagliata, è necessario creare tre progetti:

- Un progetto VSIX per creare il pacchetto VSIX per distribuire l'estensione.

- Un progetto libreria di classi che implementa l'estensione. Questo progetto deve avere come destinazione .NET Framework 4.5.

- Un progetto libreria di classi che definisce i comandi di SharePoint personalizzati. Questo progetto deve avere come destinazione.NET Framework 3.5.

  Avviare la procedura dettagliata mediante la creazione di progetti.

#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**.

3. Nel **nuovo progetto** finestra di dialogo espandere il **Visual c#** o **Visual Basic** nodi e quindi scegliere il **estendibilità** nodo.

    > [!NOTE]
    > Il **estendibilità** nodo è disponibile solo se si installa Visual Studio SDK. Per altre informazioni, vedere la sezione prerequisiti più indietro in questo argomento.

4. Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5** nell'elenco delle versioni di .NET Framework.

5. Scegliere il **progetto VSIX** modello, nome del progetto **WebPartNode**, quindi scegliere il **OK** pulsante.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **WebPartNode** progetto al **Esplora soluzioni**.

#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione

1. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il nodo della soluzione, scegliere **Add**, quindi scegliere **nuovo progetto**.

2. Nel **nuovo progetto** finestra di dialogo espandere il **Visual c#** nodo o **Visual Basic** nodo, quindi scegli **Windows** nodo.

3. Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 4.5** nell'elenco delle versioni di .NET Framework.

4. Nell'elenco dei modelli di progetto, scegliere **libreria di classi**, denominare il progetto **risorse**, quindi scegliere il **OK** pulsante.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **risorse** progetto alla soluzione e apre il file di codice predefinita Class1.

5. Eliminare il file di codice Class1 dal progetto.

#### <a name="to-create-the-sharepoint-commands-project"></a>Per creare il progetto di comandi di SharePoint

1. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il nodo della soluzione, scegliere **Add**, quindi scegliere **nuovo progetto**.

2. Nel **nuovo progetto** finestra di dialogo espandere il **Visual c#** nodo o **Visual Basic** nodo e quindi scegliere il **Windows** nodo.

3. Nella parte superiore della finestra di dialogo, scegliere **.NET Framework 3.5** nell'elenco delle versioni di .NET Framework.

4. Nell'elenco dei modelli di progetto, scegliere **libreria di classi**, denominare il progetto **WebPartCommands**, quindi scegliere il **OK** pulsante.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **WebPartCommands** progetto alla soluzione e apre il file di codice predefinita Class1.

5. Eliminare il file di codice Class1 dal progetto.

## <a name="configure-the-projects"></a>Configurare i progetti
 Prima di scrivere codice per creare l'estensione, è necessario aggiungere i file di codice e i riferimenti agli assembly e configurare le impostazioni del progetto.

#### <a name="to-configure-the-webpartnodeextension-project"></a>Per configurare il progetto di risorse

1. Nel progetto di risorse, aggiungere quattro file di codice con i nomi seguenti:

    - SiteNodeExtension

    - WebPartNodeTypeProvider

    - WebPartNodeInfo

    - WebPartCommandIds

2. Aprire il menu di scelta rapida per il **risorse** del progetto e quindi scegliere **Aggiungi riferimento**.

3. Nel **gestione riferimenti - risorse** finestra di dialogo scegliere la **Framework** scheda e quindi selezionare la casella di controllo per ognuno degli assembly seguenti:

    - System.ComponentModel.Composition

    - System.Windows.Forms

4. Scegliere il **Extensions** scheda, selezionare la casella di controllo per l'assembly Microsoft.VisualStudio.SharePoint e quindi scegliere il **OK** pulsante.

5. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **risorse** nodo del progetto e quindi scegliere **proprietà**.

     Si apre la finestra **Creazione progetti**.

6. Scegliere la scheda **Applicazione**.

7. Nel **spazio dei nomi predefinito** finestra (c#) o **spazio dei nomi radice** casella ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), immettere **ServerExplorer.SharePointConnections.WebPartNode**.

#### <a name="to-configure-the-webpartcommands-project"></a>Per configurare il progetto webpartcommands

1. Nel progetto WebPartCommands, aggiungere un file di codice denominato WebPartCommands.

2. In **Esplora soluzioni**, aprire il menu di scelta rapida per il **WebPartCommands** nodo del progetto, scegliere **Add**, quindi scegliere **elemento esistente**.

3. Nel **Aggiungi elemento esistente** nella finestra di dialogo passare alla cartella che contiene i file di codice risorse per il progetto e quindi scegliere i file di codice WebPartNodeInfo e WebPartCommandIds.

4. Scegliere la freccia accanto al **Add** pulsante e quindi scegliere **Aggiungi come collegamento** nel menu visualizzato.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge i file di codice al progetto WebPartCommands come collegamenti. Di conseguenza, i file di codice si trovano nel progetto di risorse, ma il codice nei file vengono inoltre compilati nel progetto WebPartCommands.

5. Aprire il menu di scelta rapida per il **WebPartCommands** nuovo progetto e scegliere **Aggiungi riferimento**.

6. Nel **gestione riferimenti - WebPartCommands** finestra di dialogo scegliere la **estensioni** scheda, selezionare la casella di controllo per ognuno degli assembly seguenti e quindi scegliere il **OK** pulsante:

    - Microsoft.SharePoint

    - Microsoft.VisualStudio.SharePoint.Commands

7. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **WebPartCommands** nuovo progetto e quindi scegliere **proprietà**.

     Si apre la finestra **Creazione progetti**.

8. Scegliere la scheda **Applicazione**.

9. Nel **spazio dei nomi predefinito** finestra (c#) o **spazio dei nomi radice** casella ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), immettere **ServerExplorer.SharePointConnections.WebPartNode**.

## <a name="create-icons-for-the-new-nodes"></a>Creazione di icone per i nuovi nodi
 Creare due icone per il **Esplora Server** estensione: un'icona per il nuovo **raccolta Web Part** nodo e un'altra icona per ogni nodo della Web Part figlio sotto il **raccolta Web Part** nodo. Più avanti in questa procedura dettagliata, si scriverà codice che associa tali icone con i nodi.

#### <a name="to-create-icons-for-the-nodes"></a>Per creare le icone per i nodi

1. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **risorse** del progetto e quindi scegliere **proprietà**.

2. Si apre la finestra **Creazione progetti**.

3. Scegliere il **le risorse** scheda e quindi scegliere il **questo progetto non contiene un file di risorse predefinito. Fare clic qui per crearne uno** collegamento.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Crea un file di risorse e lo apre nella finestra di progettazione.

4. Nella parte superiore della finestra di progettazione, scegliere la freccia accanto al **Aggiungi risorsa** dal menu di comando e quindi scegliere **Aggiungi nuova icona** nel menu visualizzato.

5. Nel **Aggiungi nuova risorsa** della finestra di dialogo Nome sull'icona Nuovo **WebPartsNode**e quindi scegliere il **Add** pulsante.

     Viene aperta la nuova icona nel **Editor di immagini**.

6. Modificare la versione di 16x16 dell'icona in modo che includa una progettazione che è possibile riconoscere facilmente.

7. Aprire il menu di scelta rapida per la versione a 32 x 32 dell'icona e quindi scegliere **eliminare tipo di immagine**.

8. Ripetere i passaggi da 5 a 8 per aggiungere una seconda icona Risorse del progetto e denominare questa icona **WebPart**.

9. Nella **Esplora soluzioni**, sotto il **risorse** cartella per il **risorse** del progetto, aprire il menu di scelta rapida per **WebPartNodeExtension**.

10. Nel **delle proprietà** finestra, scegliere la freccia accanto a **azione di compilazione**e quindi scegliere **risorsa incorporata** nel menu visualizzato.

11. Ripetere gli ultimi due passaggi per la **WebPart**.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Aggiungere il nodo di raccolta Web Part a Esplora Server
 Creare una classe che aggiunge la nuova **raccolta Web Part** nodo per ogni nodo del sito di SharePoint. Per aggiungere il nuovo nodo, la classe implementa il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfaccia. Implementare questa interfaccia ogni volta che si desidera estendere il comportamento di un nodo esistente nel **Esplora Server**, ad esempio l'aggiunta di un nodo figlio a un nodo.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Per aggiungere il nodo di raccolta Web Part a Esplora Server

1. Nel progetto di risorse, aprire il file di codice SiteNodeExtension e quindi incollare il codice seguente al suo interno.

    > [!NOTE]
    > Dopo che si aggiunge questo codice, il progetto avrà alcuni errori di compilazione, ma scompariranno quando si aggiunge codice nei passaggi successivi.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]

## <a name="define-a-node-type-that-represents-a-web-part"></a>Definire un tipo di nodo che rappresenta una web part
 Creare una classe che definisce un nuovo tipo di nodo che rappresenta una Web Part. Visual Studio Usa questo nuovo tipo di nodo per visualizzare i nodi figlio sotto il **raccolta Web Part** nodo. Ogni nodo figlio rappresenta una singola parte Web nel sito di SharePoint.

 Per definire il nuovo tipo di nodo, la classe implementa il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfaccia. Implementare questa interfaccia ogni volta che si vuole definire un nuovo tipo di nodo **Esplora Server**.

#### <a name="to-define-the-web-part-node-type"></a>Per definire il tipo di nodo di web part

1. Nel progetto di risorse, aprire il file di codice WebPartNodeTypeProvider e quindi incollare il codice seguente al suo interno.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]

## <a name="define-the-web-part-data-class"></a>Definire la classe di dati web part
 Definire una classe che contiene i dati su una singola parte Web nel sito di SharePoint. Più avanti in questa procedura dettagliata, si creerà un comando di SharePoint personalizzato che recupera i dati su ogni Web Part sul sito e quindi assegna i dati alle istanze di questa classe.

#### <a name="to-define-the-web-part-data-class"></a>Per definire la classe di dati web part

1. Nel progetto di risorse, aprire il file di codice WebPartNodeInfo e quindi incollare il codice seguente al suo interno.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]

## <a name="define-the-ids-for-the-sharepoint-commands"></a>Definire gli ID per i comandi di SharePoint
 Definire diverse stringhe che identificano i comandi di SharePoint personalizzati. Questi comandi si implementerà più avanti in questa procedura dettagliata.

#### <a name="to-define-the-command-ids"></a>Per definire gli ID di comando

1. Nel progetto di risorse, aprire il file di codice WebPartCommandIds e quindi incollare il codice seguente al suo interno.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]

## <a name="create-the-custom-sharepoint-commands"></a>Creare i comandi di SharePoint personalizzati
 Creare i comandi personalizzati che effettuano chiamate nel modello a oggetti server per SharePoint recuperare i dati sulle Web part sul sito di SharePoint. Ogni comando è un metodo che presenta il <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> applicato.

#### <a name="to-define-the-sharepoint-commands"></a>Per definire i comandi di SharePoint

1. Nel progetto WebPartCommands, aprire il file di codice WebPartCommands e quindi incollare il codice seguente al suo interno.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]

## <a name="checkpoint"></a>Checkpoint
 A questo punto della procedura dettagliata, tutto il codice per il **raccolta Web Part** nodo e i comandi di SharePoint sono ora nei progetti. Compilare la soluzione per assicurarsi che entrambi i progetti vengano compilati senza errori.

#### <a name="to-build-the-solution"></a>Per compilare la soluzione

1. Nella barra dei menu scegliere **Compila** > **Compila soluzione**.

    > [!WARNING]
    > A questo punto, il progetto WebPartNode può avere un errore di compilazione perché il file manifesto VSIX non ha un valore per l'autore. Questo errore scompare quando si aggiunge un valore nei passaggi successivi.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Creare un pacchetto VSIX per distribuire l'estensione
 Per distribuire l'estensione, usare il progetto VSIX nella soluzione per creare un pacchetto VSIX. Configurare innanzitutto il pacchetto VSIX, modificando il file vsixmanifest nel progetto VSIX. Quindi, creare il pacchetto VSIX per la compilazione della soluzione.

#### <a name="to-configure-the-vsix-package"></a>Per configurare il pacchetto VSIX

1. Nelle **Esplora soluzioni**, sotto il progetto WebPartNode, aprire il **vsixmanifest** file nell'editor del manifesto.

     Il file vsixmanifest costituisce la base per il file extension vsixmanifest che richiedono tutti i pacchetti VSIX. Per altre informazioni su questo file, vedere [riferimenti su VSIX Extension Schema 1.0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. Nel **Product Name** casella, immettere **nodo di raccolta Web Part di Esplora Server**.

3. Nel **Author** casella, immettere **Contoso**.

4. Nel **Description** immettere **aggiunge un nodo di raccolta Web Part personalizzato al nodo Connessioni di SharePoint in Esplora Server. Questa estensione Usa un comando di SharePoint personalizzato per chiamare il modello a oggetti server.**

5. Scegliere il **asset** della scheda dell'editor e quindi scegliere il **New** pulsante.

     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.

6. Nel **tipo** casella di riepilogo **MEFComponent**.

    > [!NOTE]
    > Questo valore corrisponde al `MefComponent` elemento nel file Extension. vsixmanifest. Questo elemento specifica il nome di un assembly di estensione del pacchetto VSIX. Per altre informazioni, vedere [MEFComponent Element (Schema di VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Nel **origine** casella di riepilogo **un progetto nella soluzione corrente**.

8. Nel **progetto** casella di riepilogo **risorse** e quindi scegliere il **OK** pulsante.

9. Nell'editor del manifesto, scegliere il **New** nuovamente clic sul pulsante.

     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.

10. Nel **tipo** casella, immettere **v4**.

    > [!NOTE]
    > Questo elemento specifica un'estensione personalizzata che si desidera includere nell'estensione di Visual Studio. Per altre informazioni, vedere [Asset Element (Schema di VSX)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).

11. Nel **origine** scegliere i **un progetto nella soluzione corrente** elemento dell'elenco.

12. Nel **progetto** scegliere **WebPartCommands**, quindi scegliere il **OK** pulsante.

13. Nella barra dei menu, scegliere **compilare** > **Compila soluzione**, quindi assicurarsi che la soluzione venga compilata senza errori.

14. Assicurarsi che la cartella di output di compilazione per il progetto WebPartNode contiene ora il file WebPartNode.

     Per impostazione predefinita, la cartella di output di compilazione è di... nella cartella \bin\Debug sotto la cartella che contiene il file di progetto.

## <a name="test-the-extension"></a>Testare l'estensione
 A questo punto si è pronti testare le nuove **raccolta Web Part** nodo **Esplora Server**. Innanzitutto, avviare il debug dell'estensione in un'istanza sperimentale di Visual Studio. Quindi, usare il nuovo **Web part** nodo nell'istanza sperimentale di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

#### <a name="to-start-debugging-the-extension"></a>Per avviare il debug dell'estensione

1. Riavviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con credenziali amministrative e quindi aprire la soluzione WebPartNode.

2. Nel progetto di risorse, aprire il file di codice SiteNodeExtension e quindi aggiungere un punto di interruzione per la prima riga del codice nel `NodeChildrenRequested` e `CreateWebPartNodes` metodi.

3. Scegliere il **F5** chiave per avviare il debug.

     Visual Studio installa l'estensione %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web Part Gallery nodo Extension for Server Explorer\1.0 e avvia un'istanza sperimentale di Visual Studio. Si testerà l'elemento del progetto in questa istanza di Visual Studio.

#### <a name="to-test-the-extension"></a>Per testare l'estensione

1. Nell'istanza sperimentale di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], nella barra dei menu, scegliere **View** > **Esplora Server**.

2. Eseguire la procedura seguente se il sito di SharePoint che si desidera usare per il test non viene visualizzato sotto il **connessioni di SharePoint** nodo **Esplora Server**:

    1. Nelle **Esplora Server**, aprire il menu di scelta rapida **connessioni di SharePoint**, quindi scegliere **Aggiungi connessione**.

    2. Nel **Aggiungi connessione SharePoint** finestra di dialogo immettere l'URL per il sito di SharePoint a cui si desidera connettersi, quindi scegliere il **OK** pulsante.

         Per specificare il sito di SharePoint nel computer di sviluppo, immettere **http://localhost** .

3. Espandere il nodo di connessione del sito, che visualizza l'URL del sito, e quindi espandere un nodo del sito figlio (ad esempio, **sito del Team**).

4. Verificare che il codice in altra istanza del [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] si arresta nel punto di interruzione impostato in precedenza nella `NodeChildrenRequested` metodo e quindi scegliere **F5** per continuare il debug del progetto.

5. Nell'istanza sperimentale di Visual Studio, verificare che un nuovo nodo denominato **raccolta Web Part** viene visualizzato sotto il nodo di sito di livello superiore e quindi espandere il **raccolta Web Part** nodo.

6. Verificare che il codice in altra istanza di Visual Studio si arresta nel punto di interruzione impostato in precedenza nella `CreateWebPartNodes` metodo e quindi scegliere il **F5** un tasto per continuare il debug del progetto.

7. Nell'istanza sperimentale di Visual Studio, verificare che tutte le Web part sul sito connesso appaiano sotto le **raccolta Web Part** nodo **Esplora Server**.

8. Nelle **Esplora Server**, aprire il menu di scelta rapida per una delle Web part e quindi scegliere **proprietà**.

9. Nell'istanza di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] che sta eseguendo il debug, verificare che siano visualizzati i dettagli sulla Web Part i **proprietà** finestra.

## <a name="uninstall-the-extension-from-visual-studio"></a>Disinstallare l'estensione da Visual Studio
 Dopo aver completato l'estensione per il testing, disinstallare l'estensione da Visual Studio.

#### <a name="to-uninstall-the-extension"></a>Per disinstallare l'estensione

1. Nell'istanza sperimentale di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], nella barra dei menu, scegliere **Tools** > **estensioni e aggiornamenti**.

     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

2. Nell'elenco delle estensioni, scegliere **estensione di Web Part raccolta nodo di Esplora Server**, quindi scegliere il **Disinstalla** pulsante.

3. Nella finestra di dialogo visualizzata, scegliere il **Yes** per confermare che si desidera disinstallare l'estensione e quindi scegliere il **Riavvia ora** pulsante per completare la disinstallazione.

4. Chiudere entrambe le istanze di Visual Studio (l'istanza sperimentale e l'istanza di Visual Studio in cui la soluzione WebPartNode è aperta).

## <a name="see-also"></a>Vedere anche
- [Estensione del nodo Connessioni di SharePoint in Esplora Server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Procedura dettagliata: Chiamare il modello a oggetti client SharePoint in un'estensione di Esplora Server](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)
- [Editor di immagini per le icone](/cpp/windows/image-editor-for-icons)
- [Creazione di un'icona o un'altra immagine &#40;Image Editor for Icons&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)
