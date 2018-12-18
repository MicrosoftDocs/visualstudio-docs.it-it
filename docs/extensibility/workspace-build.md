---
title: Area di lavoro di compilazione in Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 813f7a5e-f298-4469-9f4c-a5bddf5a6e14
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: f7415c99c68436519f9bab721fe88a48f750fa1c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="workspace-build"></a>Compilazione dell'area di lavoro

Supporto per la compilazione [Apri cartella](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) scenari richiede un'estensione per fornire [indicizzata](workspace-indexing.md) e [contesto file](workspace-file-contexts.md) i dati per il [dell'area di lavoro](workspaces.md), come nonché l'azione di compilazione da eseguire.

Di seguito è riportata una descrizione dell'estensione necessità degli.

## <a name="build-file-context"></a>Contesto del file di compilazione

- Factory del provider
  - `ExportFileContextProviderAttribute` associare `supportedContextTypeGuids` modo di tutte le applicabili `string` costanti `BuildContextTypes`
  - Implementa `IWorkspaceProviderFactory<IFileContextProvider>`
  - Provider di contesto di file
    - Restituire un `FileContext` per ogni compilazione configurazione supportata e l'operazione
      - `contextType` Da <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` implementa <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> con il `Configuration` proprietà come la configurazione di compilazione (ad esempio `"Debug|x86"`, `"ret"`, o `null` se non applicabile). In alternativa, utilizzare un'istanza di <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext>. Il valore di configurazione **necessario** corrisponde alla configurazione rispetto al valore di dati di file indicizzati.

## <a name="indexed-build-file-data-value"></a>Valore dei dati di file indicizzati compilazione

- Factory del provider
  - `ExportFileScannerAttribute` attributo con `IReadOnlyCollection<FileDataValue>` come un tipo supportato
  - Implementa `IWorkspaceProviderFactory<IFileScanner>`
- Analisi dei file in `ScanContentAsync<T>`
  - Restituisce i dati quando `FileScannerTypeConstants.FileDataValuesType` è costituito dall'argomento di tipo
  - Restituisce un valore di dati di file per ogni configurazione costruito con:
    - `type` come `BuildConfigurationContext.ContextTypeGuid`
    - `context` come la configurazione di compilazione (ad esempio `"Debug|x86"`, `"ret"`, o `null` se non applicabile). Questo valore **necessario** corrisponde alla configurazione dal contesto del file.

## <a name="build-file-context-action"></a>Azione rapida di file di compilazione

- Factory del provider
  - `ExportFileContextActionProvider` associare `supportedContextTypeGuids` modo di tutte le applicabili `string` costanti `BuildContextTypes`
  - Implementa `IWorkspaceProviderFactory<IFileContextActionProvider>`
- Provider di azioni su `IFileContextActionProvider.GetActionsAsync`
  - Restituisce un `IFileContextAction` che corrisponde al determinato `FileContext.ContextType` valore
- Azione rapida di file
  - Implementa `IFileContextAction` e <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` restituisce proprietà `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` viene `0x1000` per la compilazione, `0x1010` per la ricompilazione, o `0x1020` per eseguire la pulizia

>[!NOTE]
>Poiché il `FileDataValue` devono essere indicizzati, sia la stessa quantità di tempo tra l'apertura di area di lavoro e il punto in corrispondenza del quale il file viene analizzato per la funzionalità di compilazione completa. Verrà visualizzato il ritardo la prima apertura di una cartella, perché è disponibile alcun indice precedentemente memorizzata nella cache.

## <a name="reporting-messages-from-a-build"></a>Messaggi di report da una compilazione

La compilazione, può verificarsi i messaggi di errore, avviso e informazioni agli utenti uno dei due modi. La più semplice consiste nell'utilizzare il <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> e fornire un <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>, come illustrato di seguito:

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Build;

private static void OutputBuildMessage(IWorkspace workspace)
{
    IBuildMessageService buildMessageService = workspace.GetBuildMessageService();

    if (buildMessageService != null)
    {
      // Example error build message. See the documentation for BuildMessage for more information.
      var message = new BuildMessage()
      {
          Type = BuildMessage.TaskType.Error,
          Code = "MY1001",
          TaskText = "This is a sample error",
          ProjectFile = "buildfile.bld",
          File = "sourcefile.src"
          LogMessage = $"This is sample text that will only go to the Build output window pane.\n"

          // And any other properties to set
      };

      buildMessageService.ReportBuildMessages(new BuildMessage[] { message });
    }
}
```

`BuildMessage.Type` e `BuildMessage.LogMessage` controllano il comportamento di in cui le informazioni verranno presentate all'utente. Qualsiasi `BuildMessage.TaskType` valore diverso da `None` produrrà un **elenco errori** voce con i dettagli specificati. `LogMessage` verranno sempre restituiti nel **compilare** riquadro del **Output** finestra degli strumenti.

In alternativa, le estensioni possono interagire direttamente con il **elenco errori** oppure **compilare** riquadro. Esiste un bug nelle versioni precedenti alla versione 15.7 2017 di Visual Studio in cui il `pszProjectUniqueName` argomento di <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> viene ignorato.

>[!WARNING]
>I chiamanti del `IFileContextAction.ExecuteAsync` può fornire implementazioni sottostante arbitrarie per il `IProgress<IFileContextActionProgressUpdate>` argomento. Non richiamare `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` direttamente. Non esistono attualmente alcuna le linee guida generali per l'utilizzo di questo argomento, ma queste linee guida sono soggetti a modifiche.

## <a name="build-related-apis"></a>Compilare le API correlate

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> Fornisce i dettagli di configurazione di compilazione.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> Mostra <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>s agli utenti.

## <a name="tasksvsjson-and-launchvsjson"></a>Tasks.VS.JSON e launch.vs.json

Per informazioni sulla creazione di un file tasks.vs.json o launch.vs.json, vedere [personalizzare compilazione ed eseguire il debug di attività](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

## <a name="next-steps"></a>Passaggi successivi

* [Protocollo Server Language](language-server-protocol.md) -informazioni su come integrare i server di linguaggio in Visual Studio.