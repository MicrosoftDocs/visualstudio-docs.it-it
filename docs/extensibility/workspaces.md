---
title: Aree di lavoro in Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3489592a-dc0c-4cd3-9b08-cd367626980a
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 0230201677fd2422817ca1fbeab6679a424e5c05
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="workspaces"></a>Workspaces

Un'area di lavoro è il modo in cui Visual Studio rappresenta una raccolta di file in [cartella aperta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), e viene rappresentato dal <xref:Microsoft.VisualStudio.Workspace.IWorkspace> tipo. Di per sé l'area di lavoro non comprensione del contenuto o le funzionalità relative ai file all'interno della cartella. Piuttosto, fornisce un set di API per le funzionalità e le estensioni per produrre e usare dati che altri utenti possa intervenire su Generale. I produttori sono composti da tramite il [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) utilizzando vari esportare gli attributi.

## <a name="workspace-providers-and-services"></a>Servizi e i provider dell'area di lavoro

Servizi e i provider dell'area di lavoro forniscono i dati e le funzionalità da reagire al contenuto di un'area di lavoro. Potrebbero fornire informazioni sui file contestuale, i simboli nei file di origine o la funzionalità di compilazione.

Entrambi i concetti utilizzano un [modello di factory](https://en.wikipedia.org/wiki/Factory_method_pattern) e siano stati importati tramite MEF nell'area di lavoro. Implementano tutti gli attributi di esportazione `IProviderMetadataBase` o `IWorkspaceServiceFactoryMetadata`, ma sono presenti tipi concreti che devono usare le estensioni per i tipi esportati.

Una differenza tra provider e i servizi è la loro relazione con l'area di lavoro. Un'area di lavoro può avere molti provider di un determinato tipo, ma viene creato un solo servizio di un determinato tipo per ogni area di lavoro. Ad esempio, un'area di lavoro include molti file scanner provider ma l'area di lavoro ha un solo servizio di indicizzazione per ogni area di lavoro.

Un'altra differenza principale è il consumo dei dati dal provider e i servizi. L'area di lavoro è il punto di ingresso per ottenere dati dai provider per due motivi. In primo luogo, i provider hanno in genere alcuni set di dati che creano "narrow". I dati potrebbero essere i simboli per un file di origine c# o compilare contesti di file per un _CMakeLists.txt_ file. L'area di lavoro corrisponderanno richiesta del consumer per i provider i cui metadati allineati con la richiesta. In secondo luogo, alcuni scenari consentano per molti provider contribuiscano a una richiesta mentre altri scenari di utilizzare il provider con priorità più alta.

Al contrario, le estensioni possono ottenere le istanze di e interagire direttamente con i servizi dell'area di lavoro. Metodi di estensione in `IWorkspace` sono disponibili per i servizi forniti da Visual Studio, ad esempio <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. L'estensione può offrire un servizio dell'area di lavoro per i componenti all'interno dell'estensione o delle altre estensioni da utilizzare. È preferibile utilizzare <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> o un metodo di estensione forniti nel `IWorkspace` tipo.

>[!WARNING]
> Non modificare i servizi che sono in conflitto con Visual Studio. Può generare problemi imprevisti.

## <a name="disposal-on-workspace-closure"></a>Disposizione sulla chiusura dell'area di lavoro

Sulla chiusura di un'area di lavoro, potrebbe essere necessario Extender dispose ma una chiamata asincrona codice. Il <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> interfaccia è disponibile per la scrittura di codice semplice.

## <a name="related-types"></a>Tipi correlati

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> è l'entità centrale per un'area di lavoro aperto, ad esempio una cartella aperta.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> Crea un provider per ogni area di lavoro creata un'istanza.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> Crea un servizio per ogni area di lavoro creata un'istanza.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> deve essere implementato nel provider e i servizi che devono eseguire codice asincrono durante l'eliminazione.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> fornisce metodi helper per l'accesso ai servizi noti o non autorizzato.

## <a name="workspace-settings"></a>Impostazioni dell'area di lavoro

Aree di lavoro hanno un' <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> servizio disponga di controllo semplice ma potenti su un'area di lavoro. Per una panoramica di base delle impostazioni, vedere [personalizzare compilazione ed eseguire il debug di attività](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

Le impostazioni per la maggior parte `SettingsType` sono tipi _JSON_ file, ad esempio _VSWorkspaceSettings.json_ e _tasks.vs.json_.

La potenza delle impostazioni dell'area di lavoro è incentrata sui "ambiti", che sono semplicemente i percorsi nell'area di lavoro. Quando un consumer chiama <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A>, tutti gli ambiti che includono il percorso richiesto e il tipo di impostazione vengono aggregati. Priorità di aggregazione di ambito è il seguente:

1. "Impostazioni locali", che è in genere la radice dell'area di lavoro `.vs` directory.
1. Il percorso richiesto stesso.
1. La directory padre del percorso richiesto.
1. Tutti ulteriormente padre delle directory e include la radice dell'area di lavoro.
1. "Impostazioni globali", ovvero in una directory utente.

Il risultato è un'istanza di <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings>. Questo oggetto contiene le impostazioni per un particolare tipo ed è possibile eseguire query per impostare i nomi delle chiavi archiviate come `string`. Il <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A> metodi e <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> i metodi di estensione prevede che il chiamante deve conoscere il tipo del valore dell'impostazione richiesto. Come la maggior parte dei file di impostazioni vengono rese persistenti come _JSON_ file, molte chiamate utilizzeranno `string`, `bool`, `int`e matrici di questi tipi. Sono supportati anche i tipi di oggetto. In questi casi, è possibile utilizzare `IWorkspaceSettings` se stesso come argomento di tipo. Ad esempio:

```json
{
  "intValue": 1,
  "stringValue": "s",
  "boolValue": true,
  "stringArray": [
    "s1",
    "s2"
  ],
  "nestedIWorkspaceSettings": {
    "nestedString": "ns"
  }
}
```

Presupponendo che queste impostazioni sono stati in cui un utente _VSWorkspaceSettings.json_, i dati può essere eseguito come:

```csharp
using System.Collections.Generic;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static void ReadSettings(IWorkspace workspace)
{
    IWorkspaceSettingsManager settingsManager = workspace.GetSettingsManager();
    IWorkspaceSettings settings = settingsManager.GetAggregatedSettings(SettingsTypes.Generic);

    // result == WorkspaceSettingsResult.Success
    WorkspaceSettingsResult result = settings.GetProperty("intValue", out int intValue);
    result = settings.GetProperty("stringValue", out string stringValue);
    result = settings.GetProperty("boolValue", out bool boolValue);
    result = settings.GetProperty("stringArray", out string[] stringArray);
    result = settings.GetProperty("nestedIWorkspaceSettings", out IWorkspaceSettings nestedIWorkspaceSettings);
    result = nestedIWorkspaceSettings.GetProperty("nestedString", out string nestedString);

    // Extension method alternative using default values.
    int intValueOrDefault = settings.Property("intValue", /* default */ 42);

    // Missing key. result == WorkspaceSettingsResult.Undefined
    result = settings.GetProperty("missing", out string missing);

    // Wrong type for a key. result == WorkspaceSettingsResult.Error
    result = settings.GetProperty("intValue", out IWorkspaceSettings notSettings);

    // Special ability to union "stringArray" across all scopes.
    IEnumerable<string> allStringArray = settings.UnionPropertyArray<string>("stringArray");
}
```

>[!NOTE]
>Non sono correlate alle API disponibile in queste impostazioni API il `Microsoft.VisualStudio.Settings` dello spazio dei nomi. Le impostazioni dell'area di lavoro sono indipendenti dell'host e utilizzano file di impostazioni specifiche dell'area di lavoro o i provider di impostazioni dinamiche.

### <a name="providing-dynamic-settings"></a>Fornire impostazioni dinamiche

Le estensioni possono fornire <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider>s. Questi provider in memoria consentono alle estensioni aggiungere impostazioni o eseguire l'override di altri utenti.

Esportazione di un `IWorkspaceSettingsProvider` è diverso da quello di altri provider di area di lavoro. La factory non è `IWorkspaceProviderFactory` e nessun tipo di attributo speciale. Diversamente, implementare <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> e usare `[Export(typeof(IWorkspaceSettingsProviderFactory))]`.

```csharp
// Common workspace provider factory pattern
[ExportFeatureProvider(some, args, to, export)]
internal class MyProviderFactory : IWorkspaceProviderFactory<IFeatureProvider>
{
     IFeatureProvider CreateProvider(IWorkspace workspace) => new Provider(workspace);
}

// IWorkspaceSettingsProvider pattern
[Export(typeof(IWorkspaceSettingsProviderFactory))]
internal class MySettingsProviderFactory : IWorkspaceSettingsProviderFactory
{
    // 100 is typically the value used by built-in settings providers. Lower value is higher priority.
    int Priority => 100;

    IWorkspaceSettingsProvider CreateSettingsProvider(IWorkspace workspace) => new MySettingsProvider(workspace);
}
```

>[!TIP]
>Quando si implementa i metodi che restituiscono `IWorkspaceSettingsSource` (ad esempio `IWorkspaceSettingsProvider.GetSingleSettings`), restituire un'istanza di `IWorkspaceSettings` anziché `IWorkspaceSettingsSource`. `IWorkspaceSettings` vengono fornite ulteriori informazioni che possono essere utili durante alcune aggregazioni di impostazioni.

### <a name="settings-related-apis"></a>API correlate alle impostazioni

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> impostazioni di letture e le aggregazioni per area di lavoro.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> Ottiene il `IWorkspaceSettingsManager` per un'area di lavoro.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> Ottiene le impostazioni per un determinato ambito aggregati in tutti gli ambiti sovrapposti.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> contiene le impostazioni per un particolare ambito.

## <a name="workspace-suggested-practices"></a>Area di lavoro suggerito procedure consigliate

- Restituire gli oggetti dal `IWorkspaceProviderFactory.CreateProvider` o le API simile che memorizza i relativi `Workspace` contesto quando creato. Interfacce di provider vengono scritti in attesa di che questo oggetto viene mantenuto al momento della creazione.
- Salvare le cache specifiche dell'area di lavoro o le impostazioni all'interno del percorso "Impostazioni locali" dell'area di lavoro. Creare un tracciato per i file tramite `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder` in Visual Studio 2017 15,6 o versione successiva. Per le versioni precedenti alla versione 15,6, usare il frammento seguente:

```csharp
using System.IO;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static string MakeRootedUnderWorkingFolder(IWorkspace workspace, string relativePath)
{
    string workingFolder = workspace.GetSettingsManager().GetAggregatedSettings(SettingsTypes.WorkspaceControlSettings).Property<string>("WorkingFolder");
    return Path.Combine(workingFolder, relativePath);
}
```

## <a name="solution-events-and-package-auto-load"></a>Gli eventi della soluzione e auto-caricamento del pacchetto

Possono implementare pacchetti caricati `IVsSolutionEvents7` e richiamare `IVsSolution.AdviseSolutionEvents`. Include eventi su apertura e chiusura di una cartella in Visual Studio.

Un contesto dell'interfaccia utente può essere utilizzato per caricare automaticamente il pacchetto. Il valore è `4646B819-1AE0-4E79-97F4-8A8176FDD664`.

## <a name="troubleshooting"></a>Risoluzione dei problemi

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>Il pacchetto SourceExplorerPackage non è stato caricato correttamente

Estensibilità dell'area di lavoro è molto frequentemente basate su MEF ed errore di composizione comporterà la generazione del pacchetto hosting Apri cartella in cui non caricato. Se, ad esempio, un'estensione consente di esportare un tipo con `ExportFileContextProviderAttribute`, ma il tipo implementa solo `IWorkspaceProviderFactory<IFileContextActionProvider>`, si verificherà un errore durante il tentativo di aprire una cartella in Visual Studio. I dettagli dell'errore sono reperibile nella _%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_id\ComponentModelCache\Microsoft.VisualStudio.Default.err_. Risolvere gli eventuali errori per i tipi implementati dall'estensione.

## <a name="next-steps"></a>Passaggi successivi

* [I contesti di file](workspace-file-contexts.md) -provider di contesto File portare intelligence codice per le aree di lavoro di cartella aperta. 
* [L'indicizzazione](workspace-indexing.md) -l'indicizzazione dell'area di lavoro raccoglie e mantiene le informazioni sull'area di lavoro.
