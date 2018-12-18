---
title: Contesti di file dell'area di lavoro in Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7aaa0e65-f492-49ea-a845-35bd14910ca7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: cdb013bb10c72041b03fce43e115806ecb3faeac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="workspace-file-contexts"></a>Contesti di file dell'area di lavoro

Tutte le informazioni dettagliate sui [cartella aperta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) aree di lavoro avvisi vengono generati da "file provider di contesto" che implementano il <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> interfaccia. Queste estensioni potrebbero cercare modelli nelle cartelle o file, leggere i file di MSBuild e makefile, rilevare le dipendenze dei pacchetti e così via per accumulare le informazioni che necessarie per definire un contesto di file. Un contesto di file da sola non esegue alcuna azione, ma fornisce dati che può quindi utilizzare un'altra estensione.

Ogni <xref:Microsoft.VisualStudio.Workspace.FileContext> ha un `Guid` associato che identifica il tipo di dati esegue. Un'area di lavoro utilizza questo `Guid` in un secondo momento per confrontarli con le estensioni che usano i dati tramite il <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> proprietà. Un provider di contesto file viene esportato con metadati che identifica il contesto del file `Guid`s può produrre i dati per.

Una volta definito, un contesto di file può essere associato a un numero qualsiasi di file o cartelle nell'area di lavoro. Un file specificato o una cartella può essere associato con qualsiasi numero di contesti di file. È una relazione molti-a-molti.

Gli scenari più comuni per i contesti di file sono correlati alla compilazione, debug e i servizi di linguaggio. Per altre informazioni, vedere gli altri argomenti relativi a questi scenari.

## <a name="file-context-lifecycle"></a>Contesto del ciclo di vita del file

Cicli di vita per un `FileContext` sono non deterministici. In qualsiasi momento, un componente può richiedere in modo asincrono per alcuni set di tipi di contesto. I provider che supportano un subset dei tipi di contesto richiesta verranno eseguita la query. Il `IWorkspace` istanza agisce come middle-man tra il consumer e provider tramite il <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> metodo. I consumer potrebbe essere un contesto della richiesta ed eseguire un'azione a breve termine basata sul contesto, mentre altri potrebbero richiedere un contesto e mantenere un riferimento lunga. 

Potrebbero verificarsi modifiche ai file che causano un contesto di file diventi obsoleto. Il provider può generare un evento sul `FileContext` notificare consumer degli aggiornamenti. Ad esempio, se una modifica nel disco invalida tale contesto viene fornito un contesto di compilazione per alcuni file tuttavia il producer originale può richiamare l'evento. Consumer ancora riferimento che `FileContext` quindi è possibile rieseguire la query per un nuovo `FileContext`.

>[!NOTE]
>Non è disponibile alcun modello push ai consumer. I consumer non riceveranno una notifica di un provider new `FileContext` dopo la richiesta.

## <a name="expensive-file-context-computations"></a>Calcoli di contesto file dispendiosa

Contenuto del file durante la lettura da disco può essere costosa, soprattutto quando un provider deve risolvere la relazione tra i file. Ad esempio, può richiedere un provider di contesto del alcuni file di origine file, ma il contesto del file dipende i metadati da un file di progetto. L'analisi del file di progetto o valutarlo con MSBuild è dispendiosa. In alternativa, è possibile esportare l'estensione un' `IFileScanner` per creare `FileDataValue` dati durante l'indicizzazione dell'area di lavoro. Ora quando viene richiesto per i contesti di file, il `IFileContextProvider` possono effettuare rapidamente query per tali dati indicizzati. Per ulteriori informazioni sugli indici, vedere la [dell'area di lavoro indicizzazione](workspace-indexing.md) argomento.

>[!WARNING]
>Prestare attenzione in altri modi di `FileContext` può essere conveniente da calcolare. Alcune interazioni dell'interfaccia utente sono sincroni e si basano su un volume elevato di `FileContext` richieste. Esempi includono aprendo una scheda editor e un **Esplora soluzioni** menu di scelta rapida. Queste azioni apportano molte contesto di compilazione digitare le richieste.

## <a name="file-context-related-apis"></a>API correlate al contesto di file

- <xref:Microsoft.VisualStudio.Workspace.FileContext> contiene i dati e metadati.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> e <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> creare il contesto di file.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> Esporta un provider di contesto di file.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> viene usata per i consumer per ottenere i contesti di file.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> Definisce i tipi di contesto di compilazione che verrà utilizzata dalla cartella aperta.

## <a name="file-context-actions"></a>Azioni del contesto file

Mentre un `FileContext` costituisce solo i dati su alcuni file, un <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> è un modo per express e agire su tali dati. `IFileContextAction` è flessibile e relativo utilizzo. Due dei relativi casi più comuni sono compilazione e debug.

## <a name="reporting-progress"></a>Creazione di report stato di avanzamento

Il <xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A> viene passato `IProgress<IFileContextActionProgressUpdate>`, ma l'argomento non deve essere usato come quel tipo. `IFileContextActionProgressUpdate` è un'interfaccia vuota e richiamando `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` potrebbe generare `NotImplementedException`. Al contrario, il `IFileContextAction` deve eseguire il cast l'argomento a un altro tipo in base alle esigenze per lo scenario.

Per informazioni sui tipi forniti da Visual Studio, vedere la documentazione del rispettivo scenario.

## <a name="file-context-action-related-apis"></a>API correlate all'azione di contesto di file

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> esegue il comportamento in base a un `FileContext`.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> Crea istanze di `IFileContextAction`.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> il tipo esportato `IWorkspaceProviderFactory<IFileContextActionProvider>`.

## <a name="file-watching"></a>Controllo dei file

Un'area di lavoro è in attesa di notifiche di cambiamento file e fornisce le <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> tramite <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. Gli eventi di notifica di file non producono file corrisponda a quella "ExcludedItems". Una soglia tra gli eventi viene utilizzata per semplificare le operazioni di notifica e riduzione duplicata. Quando è necessario rispondere a una modifica di file, è necessario sottoscrivere questo servizio.

>[!TIP]
>Un'area di lavoro [servizio di indicizzazione](workspace-indexing.md) sottoscrive gli eventi dei file per impostazione predefinita. Aggiunte di file e le modifiche causerà rilevanti `IFileScanner`eventi s da richiamare per i nuovi dati per quel file. L'eliminazione di file rimuoverà i dati indicizzati. Non è necessario sottoscrivere il `IFileScanner` nel servizio di controllo file.

## <a name="next-steps"></a>Passaggi successivi

* [L'indicizzazione](workspace-indexing.md) -l'indicizzazione dell'area di lavoro raccoglie e mantiene le informazioni sull'area di lavoro.
* [Aree di lavoro](workspaces.md) -rivedere i concetti dell'area di lavoro e l'archiviazione delle impostazioni.
