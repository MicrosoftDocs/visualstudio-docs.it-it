---
title: 'Procedura dettagliata: Distribuzione di una definizione di elenco attività di progetto | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fb7f8445cf43209ffed47140b1d8d204c68eaa4f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-deploying-a-project-task-list-definition"></a>Procedura dettagliata: distribuzione di una definizione di elenco attività del progetto

In questa procedura guidata viene illustrato come utilizzare [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] per creare, personalizzare, eseguire il debug e distribuire un elenco di SharePoint per tenere traccia delle attività del progetto.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti

- Edizioni supportate di Microsoft Windows e SharePoint. Per ulteriori informazioni, vedere [requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).

- Visual Studio 2017 o un'edizione di Visual Studio Application Lifecycle Management (ALM).

## <a name="CreatingListDef"></a> Creazione di un elenco SharePoint

Creare un progetto di elenco di SharePoint e associare la definizione dell'elenco alle attività.

1. Aprire il **nuovo progetto** finestra di dialogo espandere il **SharePoint** nodo e quindi scegliere il **2010** nodo.

2. Nel **modelli** riquadro, scegliere il **progetto SharePoint 2010** modello, denominare il progetto **ProjectTaskList**e quindi scegliere il **OK**pulsante.

     Il **Personalizzazione guidata SharePoint** viene visualizzato.

3. Specificare il sito di SharePoint locale utilizzato per il debug, scegliere il **Distribuisci come soluzione farm** pulsante di opzione e quindi scegliere il **fine** pulsante.

4. Aprire il menu di scelta rapida per il progetto e quindi scegliere **Aggiungi**, **nuovo elemento**.

5. Nel **modelli** riquadro, scegliere il **elenco** modello, quindi scegliere il **Aggiungi** pulsante.

     Il **Personalizzazione guidata SharePoint** viene visualizzato.

6. Nel **il nome che si desidera visualizzare per l'elenco?** immettere **elenco attività progetti**.

7. Scegliere il **creare un elenco non personalizzabile in base a un tipo di elenco esistente di** pulsante di opzione e quindi, nel relativo elenco scegliere **attività**, quindi scegliere il **fine** pulsante.

     Nell'elenco, funzionalità e pacchetto vengono visualizzati **Esplora**.

## <a name="AddEventRcvr"></a> Aggiunta di un ricevitore di eventi

Nell'elenco attività è possibile aggiungere un ricevitore di eventi tramite cui vengono impostate automaticamente la scadenza e la descrizione dell'attività. La procedura seguente aggiunge un gestore di evento semplice per l'istanza di elenco come un ricevitore di eventi.

1. Aprire il menu di scelta rapida per il nodo del progetto, scegliere **Aggiungi**, quindi scegliere **nuovo elemento**.

2. Nell'elenco dei modelli di SharePoint, scegliere il **ricevitore di eventi** modello, quindi denominarlo **ProjectTaskListEventReceiver**.

     Il **Personalizzazione guidata SharePoint** viene visualizzato.

3. Nel **scegliere le impostazioni del ricevitore di eventi** pagina, scegliere **eventi elementi elenco** come tipo di ricevitore di eventi nel **il tipo di ricevitore di eventi si desidera** elenco.

4. Nel **selezionare l'elemento deve essere l'origine evento** scegliere **attività**.

5. Nell'elenco di eventi da gestire, selezionare la casella di controllo accanto a **è stato aggiunto un elemento**, quindi scegliere il **fine** pulsante.

     Un nuovo nodo di ricevitore di eventi viene aggiunto al progetto con un file di codice denominato **ProjectTaskListEventReceiver**.

6. Aggiungere codice per il `ItemAdded` metodo il **ProjectTaskListEventReceiver** file di codice. Ogni volta che viene aggiunta una nuova attività, una scadenza predefinita e una descrizione viene aggiunto all'attività. La scadenza predefinita è di data 1 luglio 2009.

     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]

## <a name="CustomizeFeature"></a> Personalizzazione di Project Task List Feature

Quando si crea una soluzione di SharePoint, Visual Studio crea automaticamente le funzionalità per l'impostazione predefinita gli elementi di progetto. È possibile personalizzare le impostazioni di elenco attività di progetto per il sito di SharePoint utilizzando la finestra di progettazione di funzionalità.

1. In **Esplora**, espandere **funzionalità**.

2. Aprire il menu di scelta rapida per **Feature1**, quindi scegliere **Visualizza finestra di progettazione**.

3. Nel **titolo** immettere **Project Task List Feature**.

4. Nel **ambito** scegliere **Web**.

5. Nel **proprietà** finestra immettere **1.0.0.0** come valore per il **versione** proprietà.

## <a name="CustomizePackage"></a> Il pacchetto dell'elenco attività di progetto di personalizzazione

Quando si crea un progetto SharePoint, Visual Studio aggiunge automaticamente le funzionalità che contengono gli elementi di progetto predefiniti per il pacchetto. È possibile personalizzare le impostazioni di elenco attività di progetto per il sito di SharePoint utilizzando la finestra di progettazione del pacchetto.

1. In **SolutionExplorer**, aprire il menu di scelta rapida per **pacchetto**, quindi scegliere **Visualizza finestra di progettazione**.

2. Nel **nome** immettere **ProjectTaskListPackage**.

3. Selezionare il **Reimposta Server Web** casella di controllo.

## <a name="BuildTest"></a> Compilazione e l'elenco attività del progetto di test

Quando si esegue il progetto, viene aperto il sito di SharePoint. Tuttavia, è necessario passare manualmente alla posizione dell'elenco attività.

1. Premere F5 per compilare e distribuire l'elenco di attività del progetto.

     Apre il sito di SharePoint.

2. Scegliere il **Home** scheda.

3. Nella barra laterale sinistra, scegliere il **elenco attività progetti** collegamento.

     Viene visualizzata la pagina di elenco attività del progetto.

4. Nel **strumenti elenco** scheda, scegliere il **elementi** scheda.

5. Nel **elementi** gruppo, scegliere il **nuovo elemento** pulsante.

6. Nel **titolo** testo immettere **Attività1**.

7. Scegliere il **salvare** pulsante.

     Dopo aver aggiornato il sito, il **Attività1** viene visualizzata l'attività con una data di scadenza di 1/7/2009.

8. Scegliere **Attività1**.

     La visualizzazione dettagliata dell'attività, verrà visualizzato la descrizione "This is a un'attività critica".

## <a name="Deploy"></a> Elenco attività del progetto di distribuzione

Dopo aver compilato e l'elenco attività del progetto di test, è possibile distribuirlo per il *sistema locale* o *sistema remoto*. Il sistema locale è lo stesso computer in cui è stata sviluppata la soluzione, mentre un sistema remoto è un computer diverso.

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>Per distribuire l'elenco attività del progetto al sistema locale

Nella barra dei menu di Visual Studio, scegliere **compilare**, **Distribuisci soluzione**.

Visual Studio viene riciclato il pool di applicazioni IIS, le versioni esistenti della soluzione viene ritratta, copia il file di pacchetto (con estensione wsp) di soluzione SharePoint e quindi attiva le funzionalità. È ora possibile usare la soluzione in SharePoint. Per ulteriori informazioni sui passaggi di configurazione di distribuzione, vedere [procedura: modificare una configurazione di distribuzione di SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>Per distribuire l'elenco attività del progetto in un sistema remoto

1. Nella barra dei menu di Visual Studio, scegliere **compilare**, **pubblica**.

2. Nel **pubblica** finestra di dialogo scegliere la **pubblica su File System** pulsante di opzione.

     È possibile modificare il percorso di destinazione nel **pubblica** la finestra di dialogo facendo clic sul pulsante con i puntini di sospensione ![icona puntini di sospensione](../sharepoint/media/ellipsisicon.gif "i puntini di sospensione icona") e quindi passare a un'altra posizione.

3. Scegliere il **pubblica** pulsante.

     Viene creato un file con estensione wsp per la soluzione.

4. Copiare il file con estensione wsp nel sistema SharePoint remoto.

5. Utilizzare il comando PowerShell `Add-SPUserSolution` comando per installare il pacchetto in installazione di SharePoint remoto. (Per le soluzioni farm, utilizzare il `Add-SPSolution` comando.)

     Ad esempio `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.

6. Utilizzare il comando PowerShell `Install-SPUserSolution` comando per distribuire la soluzione. (Per le soluzioni farm, utilizzare il `Install-SPSolution` comando.)

     Ad esempio `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`.

     Per ulteriori informazioni sulla distribuzione remota, vedere [tramite soluzioni](http://go.microsoft.com/fwlink/?LinkId=217680) e [aggiunta e distribuzione di soluzioni con PowerShell in SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=217682).

## <a name="next-steps"></a>Passaggi successivi

Maggiori informazioni su come personalizzare e distribuire soluzioni di SharePoint i seguenti argomenti:

- [Procedura dettagliata: creare una colonna del sito, un tipo di contenuto e un elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [Procedura: Creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)

- [Windows PowerShell per SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=217684)

## <a name="see-also"></a>Vedere anche

[Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)