---
title: Area di lavoro in Visual Studio di indicizzazione | Documenti Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3163e98c-1c79-48a7-813f-7923be894ba1
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 5004db0d895d1fdc697c18606c346c24cd484527
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="workspace-indexing"></a>L'indicizzazione dell'area di lavoro

In una soluzione, sistemi di progetto sono responsabili per fornire funzionalità per la compilazione, debug, **GoTo** la ricerca di simboli e altro ancora. Sistemi di progetto possono eseguire questa operazione, perché comprendono la relazione e la funzionalità del file all'interno di un progetto. Un' [Apri cartella](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) dell'area di lavoro richiede le stesse informazioni per fornire funzionalità IDE avanzate anche. La raccolta e l'archiviazione permanente dei dati è un processo denominato l'indicizzazione dell'area di lavoro. Questi dati indicizzati è possibile eseguire query tramite un set di API asincrone. Extender può partecipare al processo di indicizzazione, fornendo <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner>che sa come gestire determinati tipi di file.

## <a name="types-of-indexed-data"></a>Tipi di dati indicizzati

Esistono tre tipi di dati indicizzati. Si noti il tipo previsto dagli scanner di file diverso dal tipo deserializzato dall'indice.

|Dati|Tipo di file scanner|Tipo di risultato di query di indice|Tipi correlati|
|--|--|--|--|
|Riferimenti|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Simboli|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> deve essere usato al posto della `IIndexWorkspaceService` per le query|
|Valori dei dati|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Esecuzione di query per i dati indicizzati

Esistono due tipi asincroni disponibili per accedere ai dati persistenti. Il primo consiste nell'utilizzare <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData>. Fornisce l'accesso di base per un singolo file `FileReferenceResult` e `FileDataResult` i dati e lo memorizza nella cache i risultati. Il secondo è il <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> che non usa la memorizzazione nella cache, ma consente ulteriori funzionalità di query.

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Indexing;

private static IIndexWorkspaceData GetCachedIndexedData(IWorkspace workspace)
{
    // Gets access to indexed data wrapped in a cache.
    return workspace?.GetIndexWorkspaceDataService()?.CreateIndexWorkspaceData();
}

private static IIndexWorkspaceService GetDirectIndexedData(IWorkspace workspace)
{
    // Gets direct access to indexed data.
    // Can also be casted to IIndexWorkspaceService2.
    return workspace?.GetIndexWorkspaceService();
}
```

## <a name="participating-in-indexing"></a>Che fanno parte di indicizzazione

L'indicizzazione dell'area di lavoro segue approssimativamente la sequenza seguente:

1. Individuazione e la persistenza delle entità di sistema di file nell'area di lavoro (solo in analisi di apertura iniziale).
1. Per ogni file, il provider di corrispondenza con la priorità più alta è richiesto per la ricerca `FileReferenceInfo`s.
1. Per ogni file, il provider di corrispondenza con la priorità più alta è richiesto per la ricerca `SymbolDefinition`s.
1. Per ogni file, tutti i provider richiesto di fornire `FileDataValue`s.

Le estensioni è possono esportare uno scanner implementando `IWorkspaceProviderFactory<IFileScanner>` ed esportare il tipo con <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute>. Il `SupportedTypes` l'argomento di attributo deve essere uno o più valori da <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants>. Per uno scanner di esempio, vedere il SDK di Visual Studio [esempio](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs).

> [!WARNING]
> Non esportare uno scanner di file che supporta il `FileScannerTypeConstants.FileScannerContentType` tipo. Viene utilizzato per Microsoft interno, a solo scopo.

In casi avanzati, un'estensione in modo dinamico potrebbe supportare un set arbitrario di tipi di file. Invece di esportazione MEF `IWorkspaceProviderFactory<IFileScanner>`, un'estensione può esportare `IWorkspaceProviderFactory<IFileScannerProvider>`. Quando l'indicizzazione viene avviata, questo tipo di factory verrà importato, crea un'istanza e hanno relativo <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> metodo richiamato. `IFileScanner` le istanze che supportano un valore compreso tra `FileScannerTpeConstants` verrà tenuto in considerazione, non solo i simboli.

## <a name="next-steps"></a>Passaggi successivi

* [Aree di lavoro e servizi di linguaggio](workspace-language-services.md) -informazioni su come integrare servizi di linguaggio in un'area di lavoro di cartella aperta.
* [Compilazione dell'area di lavoro](workspace-build.md) -Apri cartella supporta sistemi, ad esempio makefile e MSBuild di compilazione.