---
title: Creare soluzioni e progetti in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 02/06/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.openprojectfromweb
- vs.newproject
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 23e91f8c5908efb4eed942a9c2556de7778fda92
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="create-solutions-and-projects"></a>Creare soluzioni e progetti

I *progetti* sono contenitori logici di Visual Studio che contengono gli elementi necessari per compilare l'app, ad esempio file di codice sorgente, bitmap, icone e riferimenti a componenti e servizi. Quando si crea un nuovo progetto, Visual Studio crea una *soluzione* per ospitarlo. Se necessario è quindi possibile aggiungere altri progetti nuovi o esistenti alla soluzione. Le soluzioni possono anche contenere file non connessi ad alcun progetto specifico.

![Gerarchia soluzione/progetto](./media/vside-proj-soln.png)

È possibile visualizzare le soluzioni e i progetti in una finestra degli strumenti denominata **Esplora soluzioni**. La schermata seguente visualizza un esempio di soluzione in Esplora soluzioni (BikeSharing.Xamarin-UWP) contenente due progetti: BikeSharing.Clients.Core e BikeSharing.Clients.Windows. Ogni progetto contiene più file, cartelle e riferimenti. Il nome del progetto in grassetto indica il *progetto di avvio*, ovvero il progetto che viene avviato quando si esegue l'app. È possibile specificare quale progetto è il progetto di avvio.

![Esplora soluzioni con progetti](./media/vside-solution-explorer-projects.png)

È possibile creare autonomamente un progetto aggiungendo i file necessari. In alternativa Visual Studio offre una selezione di modelli di progetto per semplificare le fasi iniziali. Se si usa un modello è possibile ottenere un progetto con tutti gli elementi essenziali per il tipo di progetto scelto e rinominare i file o aggiungere codice nuovo o esistente e altre risorse in base alle esigenze.

In ogni caso non è obbligatorio usare le soluzioni e i progetti per sviluppare app in Visual Studio. È possibile aprire direttamente codice clonato da Git o scaricato da un'altra origine. Per altre informazioni, vedere [Sviluppare codice in Visual Studio senza progetti o soluzioni](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

> [!NOTE]
> Le descrizioni in questo argomento sono basate sull'edizione Visual Studio Community. Le finestre di dialogo e i comandi di menu visualizzati potrebbero non corrispondere a quelli descritti in questa sezione, in quanto dipendono dalle impostazioni o dall'edizione di Visual Studio. Per modificare le impostazioni, ad esempio per implementare le impostazioni **Generali** o **Visual C++**, scegliere **Strumenti**, **Importa/Esporta impostazioni** e quindi scegliere **Reimposta tutte le impostazioni**.

## <a name="to-create-a-project-from-a-project-template"></a>Per creare un progetto da un modello di progetto

1. Esistono vari metodi per creare un nuovo progetto in Visual Studio. Nella pagina iniziale immettere il nome di un modello di progetto nella casella **Cerca modelli di progetto** o scegliere il collegamento **Crea nuovo progetto** per aprire la finestra di dialogo **Nuovo progetto**. È anche possibile scegliere **File** > **Nuovo** > **Progetto** dalla barra dei menu o scegliere il pulsante **Nuovo progetto** sulla barra degli strumenti.

  ![Pagina iniziale](./media/vside-newproject1.png)

  Nella finestra di dialogo **Nuovo progetto** i modelli di progetto disponibili vengono visualizzati in un elenco sotto la categoria **Modelli**. I modelli sono organizzati per linguaggio di programmazione e tipo di progetto, ad esempio Visual C#, JavaScript e Azure Data Lake.

  ![Finestra di dialogo Nuovo progetto](./media/vside-newproject-templates-list.png)

  > [!NOTE]
  > L'elenco delle lingue disponibili e i modelli di progetto visualizzati dipendono dalla versione di Visual Studio in esecuzione e dai carichi di lavoro installati. Per informazioni su come installare altri carichi di lavoro, vedere [Modify Visual Studio 2017 by adding or removing workloads and components](../install/modify-visual-studio.md) (Modificare Visual Studio 2017 aggiungendo o rimuovendo carichi di lavoro e componenti).

1. Visualizzare l'elenco dei modelli per il linguaggio di programmazione che si vuole usare facendo clic sul triangolo accanto al nome del linguaggio, quindi scegliere un tipo di progetto.

  L'esempio seguente mostra i modelli di progetto disponibili per i progetti .NET Core di Visual C#.

  ![Modelli di progetto](./media/new-project-dialog-net-core.png)

1. Immettere il nome del nuovo progetto nella casella **Nome**. È possibile scegliere di salvare il progetto nel percorso predefinito del sistema oppure scegliere il pulsante **Sfoglia** per impostare un altro percorso.

  È anche possibile scegliere di modificare il nome della soluzione oppure aggiungere il nuovo progetto a un repository Git scegliendo **Aggiungi al controllo del codice sorgente**.

1. Scegliere il pulsante **OK** per creare la soluzione e il progetto.

1. Per aggiungere un altro progetto alla soluzione, scegliere il nodo della soluzione in Esplora soluzioni e quindi sulla barra dei menu scegliere **Progetto** > **Aggiungi nuovo elemento**.

## <a name="create-a-project-from-existing-code-files"></a>Creare un progetto da file di codice esistenti

Se è presente una raccolta di file di origine di codice è possibile aggiungerli facilmente a un progetto.

1. Nel menu scegliere **File** > **Nuovo** > **Progetto da codice esistente**.

1. In **Creazione guidata nuovo progetto da file di codice esistenti** scegliere il tipo di progetto desiderato nella casella di riepilogo a discesa **Specificare il tipo di progetto che si vuole creare** e quindi scegliere **Avanti**.

1. Nella procedura guidata, passare al percorso dei file e immettere un nome per il nuovo progetto nella casella **Nome**. Al termine scegliere il pulsante **Fine**.

> [!NOTE]
> Questa opzione risulta più adatta per raccolte di file relativamente semplici. Attualmente sono supportati solo i tipi di progetto Visual C++, Apache Cordova, Visual Basic e C#.

## <a name="add-files-to-a-solution"></a>Aggiungere file a una soluzione

Se è presente un file che può essere usato per più progetti, ad esempio un file Leggimi per la soluzione o altri file che appartengono al livello della soluzione più che a un progetto specifico, è possibile aggiungerli alla soluzione stessa. Per aggiungere un elemento a una soluzione fare clic con il pulsante destro del mouse sul nodo della soluzione in **Esplora soluzioni** e scegliere **Aggiungi** > **Nuovo elemento** o **Aggiungi** > **Elemento esistente**.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Creare un progetto .NET che usa una specifica versione di .NET Framework

Quando si crea un progetto è possibile indicare la versione specifica di .NET Framework che si vuole usare nel progetto stesso. Per specificare una versione di .NET Framework, scegliere il menu a discesa **Framework** nella finestra di dialogo **Nuovo progetto**.

![Elenco a discesa Framework nella finestra di dialogo Nuovo progetto](./media/vside-newproject-framework.png)

> [!NOTE]
> Per l'accesso alle versioni di .NET Framework precedenti a .NET Framework 4 è necessario che nel computer sia installato .NET Framework 3.5.

## <a name="create-empty-solutions"></a>Creare soluzioni vuote

È anche possibile creare soluzioni vuote che non includono alcun progetto. Questa opzione può risultare preferibile quando si vuole creare da zero la soluzione e i progetti.

### <a name="to-create-an-empty-solution"></a>Per creare una soluzione vuota

1. Scegliere **File** > **Nuovo** > **Progetto** dal menu.

1. Nel riquadro a sinistra (**Modelli**) scegliere **Altri tipi di progetto** > **Soluzioni di Visual Studio** nell'elenco espanso.

1. Nel riquadro centrale scegliere **Soluzione vuota**.

1. Immettere i valori **Nome** e **Percorso** per la soluzione e quindi fare clic su **OK**.

Dopo aver creato una soluzione vuota, è possibile aggiungervi progetti o elementi nuovi o esistenti scegliendo **Aggiungi nuovo elemento** o **Aggiungi elemento esistente** nel menu **Progetto**.

Come detto in precedenza, è anche possibile aprire file di codice senza usare un progetto o una soluzione. Per altre informazioni su questa modalità di sviluppo di codice, vedere [Sviluppare codice in Visual Studio senza progetti o soluzioni](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="create-a-temporary-project-c-and-visual-basic"></a>Creare un progetto temporaneo (C# e Visual Basic)

Se si crea un progetto basato su .NET senza specificare un percorso su disco, il progetto è temporaneo. I progetti temporanei consentono di acquisire familiarità con i progetti .NET. In qualsiasi momento mentre si lavora con il progetto temporaneo è possibile scegliere di salvarlo o rimuoverlo.

Per creare un progetto temporaneo, in primo luogo scegliere **Strumenti** > **Opzioni** > **Progetti e soluzioni** >  **Generale** e deselezionare la casella di controllo **Salva nuovi progetti alla creazione**. Aprire la finestra di dialogo **Nuovo progetto** come di consueto.

## <a name="delete-a-solution-project-or-item"></a>Eliminare una soluzione, un progetto o un elemento

È possibile eliminare definitivamente le soluzioni e il relativo contenuto, ma questa operazione non può essere eseguita con l'IDE Visual Studio. Quando si eliminano elementi all'interno di Visual Studio, questi vengono rimossi solo dalla soluzione o dal progetto corrente. Per eliminare definitivamente una soluzione o un altro componente dal sistema usare Esplora File per eliminare la cartella che contiene i file della soluzione con estensione sln e suo. Prima di eliminare definitivamente una soluzione è tuttavia consigliabile eseguire il backup dei progetti o dei file, che potrebbero tornare utili in futuro.

> [!NOTE]
> Il file con estensione suo è un file nascosto che non viene visualizzato nelle impostazioni predefinite di Esplora file. Per visualizzare i file nascosti, nel menu **Visualizza** di Esplora file selezionare la casella di controllo **Elementi nascosti**.

### <a name="to-permanently-delete-a-solution"></a>Per eliminare in modo permanente una soluzione

1. In **Esplora soluzioni** scegliere **Apri cartella in Esplora file** nel menu di scelta rapida della soluzione da eliminare.

1. In Esplora file spostarsi in alto di un livello.

1. Scegliere la cartella contenente la soluzione e quindi premere **Canc**.

## <a name="see-also"></a>Vedere anche

[Soluzioni e progetti](../ide/solutions-and-projects-in-visual-studio.md)  
[Repository open source Microsoft su GitHub](https://github.com/Microsoft)  
[Esempi di Visual Studio](../ide/visual-studio-samples.md)  
[Esempi di codice per sviluppatori](https://code.msdn.microsoft.com/)
