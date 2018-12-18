---
title: "Utilità della riga di comando del visualizzatore di concorrenza (CVCollectionCmd) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.performance.cvcollectioncmd
ms.assetid: 476601be-1608-4014-af15-5aba6ccbed1c
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 53dd29671e20f19c0ef83d5920581c7038f32c9f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="concurrency-visualizer-command-line-utility-cvcollectioncmd"></a>Utilità della riga di comando del visualizzatore di concorrenza (CVCollectionCmd)
L'utilità riga di comando Visualizzatore di concorrenza (CVCollectionCmd.exe) permette di raccogliere tracce dalla riga di comando, in modo da poterle visualizzare nel Visualizzatore di concorrenza per Visual Studio. Questi strumenti possono essere usati nei computer in cui non è installato Visual Studio.  
  
> [!NOTE]
>  A partire da Visual Studio 2013, il Visualizzatore di concorrenza è un'estensione facoltativa. (In precedenza era stato incluso in Visual Studio.) È possibile scaricare gli [Strumenti di raccolta del visualizzatore di concorrenza per Visual Studio 2015](http://www.microsoft.com/en-in/download/details.aspx?id=49103) dall'Area download.  
  
## <a name="download-the-concurrency-visualizer-command-line-utility"></a>Scaricare l'utilità riga di comando Visualizzatore di concorrenza  
 Per scaricare e installare l'utilità riga di comando, passare a [Strumenti di raccolta del visualizzatore di concorrenza per Visual Studio 2015](http://www.microsoft.com/en-in/download/details.aspx?id=49103) e seguire le istruzioni. Per impostazione predefinita, CVCollectionCmd.exe è installato in %Programmi%\Microsoft Concurrency Visualizer Collection Tools\ (%Programmi(x86)%\Microsoft Concurrency Visualizer Collection Tools\ nei computer x64).  
  
## <a name="collect-a-trace-with-cvcollectioncmd"></a>Raccogliere una traccia con CVCollectionCmd  
 È possibile raccogliere una traccia avviando l'app con CVCollectionCmd oppure tramite una connessione all'app. Per le opzioni disponibili, vedere i riferimenti ai comandi seguenti. Esempio:  
  
```  
<Path>CVCollectionCmd /launch c:\myapp\myapp.exe /outdir c:\myapp\data  
```  
  
## <a name="commands-and-parameters"></a>Comandi e parametri  
 Per ottenere informazioni sui comandi e sui parametri nell'utilità da riga di comando, digitare quanto segue al prompt dei comandi:  
  
 **CvCollectionCmd /?**  
  
|Opzione|Descrizione|Parametri|Valori restituiti|  
|------------|-----------------|----------------|-------------------|  
|Query|Indica se è possibile avviare la raccolta.|nessuno|0 se la raccolta è pronta per l'avvio.<br /><br /> 1  se è già in corso una raccolta.<br /><br /> 2 se non è in corso alcuna raccolta, ma sono già state abilitate una o più delle sessioni [ETW](/dotnet/framework/wcf/samples/etw-tracing) necessarie.|  
|Launch|Esegue il processo specificato nel Visualizzatore di concorrenza.|Percorso del file eseguibile.|0 se l'esecuzione è riuscita.<br /><br /> 1 se l'esecuzione non è riuscita poiché non è stato possibile avviare l'applicazione di destinazione.<br /><br /> 13 se l'esecuzione non è riuscita poiché CVCollectionCmd non ha autorizzazioni sufficienti per scrivere nella directory di output specificata.|  
|Attach|Inizia la raccolta di una traccia a livello di sistema. In caso contrario, si connette a un processo, se ne è stato specificato uno.|Nessuno.|0 se la connessione è riuscita.<br /><br /> 1 se la connessione non è riuscita poiché il processo specificato non è valido o è ambiguo.<br /><br /> 13 se la connessione non è riuscita poiché CVCollectionCmd non ha autorizzazioni sufficienti per scrivere nella directory di output specificata.|  
|Detach|Arresta la raccolta.|Nessuno.|0 se la disconnessione è riuscita.<br /><br /> 1 se la disconnessione non è riuscita poiché la raccolta non è attualmente in corso.<br /><br /> 2 se la disconnessione non è riuscita poiché non è stato possibile arrestarla.|  
|Analyze|Analizza la traccia specificata.|Percorso completo del file CVTrace.|0 se l'analisi è riuscita.<br /><br /> 1 se non è possibile avviare l'analisi poiché la traccia specificata è a livello di sistema, ma non è stato specificato alcun processo di destinazione.<br /><br /> 2 se non è possibile avviare l'analisi poiché la traccia specificata non è a livello di sistema ed è stato specificato un processo.<br /><br /> 3  se l'analisi non è riuscita poiché il processo specificato non è valido.<br /><br /> 4 se l'analisi non è riuscita poiché il file CVTrace specificato non è valido.|  
|LaunchArgs|Specifica gli argomenti eseguibili di destinazione. Questa opzione è applicabile solo al comando Launch.|Argomenti da riga di comando per l'applicazione.|Nessuno.|  
|Outdir|Specifica la directory in cui salvare i file di traccia. Applicabile ai comandi Launch e Attach.|Percorso di directory o percorso relativo.|Nessuno.|  
|Process|Specifica il processo a cui connettersi quando si esegue il comando Attach o il processo in una traccia da analizzare quando si esegue il comando Analyze. Applicabile ai comandi Attach e Analyze.|PID o nome del processo.|Nessuno.|  
|Config|Specifica il percorso del file di configurazione, se si vogliono impostazioni di raccolta diverse da quelle predefinite.   Applicabile ai comandi Launch, Attach e Analyze.|Percorso di directory o percorso relativo del file di configurazione XML.|Nessuno.|  
  
## <a name="customizing-configuration-settings"></a>Personalizzazione delle impostazioni di configurazione  
 Se si usa CVCollectionCmd per raccogliere tracce e si vogliono personalizzare le impostazioni di raccolta, usare un file di configurazione per specificarle.  
  
> [!NOTE]
>  Quando si usa Visual Studio per raccogliere le tracce, è necessario non modificare direttamente il file di configurazione.  Per modificare le impostazioni, usare invece la finestra di dialogo [Impostazioni avanzate](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) .  
  
 Per modificare le impostazioni di raccolta, creare un file di configurazione nella macchina in cui sarà eseguita l'utilità CVCollectionCmd. È possibile creare un file di configurazione completamente nuovo oppure copiare il file di configurazione disponibile nel computer in cui è installato Visual Studio e modificarlo. Il nome del file è `UserConfig.xml` e il file si trova nella cartella **Local AppData** . Quando si esegue l'utilità, usare l'opzione Config insieme al comando Launch, Attach o Analyze.  Specificare il percorso del file di configurazione nel parametro associato all'opzione Config.  
  
### <a name="configuration-file-tags"></a>Tag del file di configurazione  
 Il file di configurazione è basato su XML. Di seguito sono riportati i tag e i valori validi:  
  
|Tag|Descrizione|Valori|  
|---------|-----------------|------------|  
|Config|Delimita il file di configurazione complessivo.|Deve contenere gli elementi seguenti:<br /><br /> -   MinorVersion<br />-   MajorVersion|  
|MajorVersion|Specifica la versione principale del file di configurazione.|Deve essere 1 per progetti [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] . Se è diverso da 1, l'utilità non funzionerà.|  
|MinorVersion|Specifica la versione secondaria del file di configurazione.|Deve essere 0 per progetti [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] . Se è diverso da 0, l'utilità non funzionerà.|  
|IncludeEnvSymbolPath|Imposta un valore che determina se è usato il percorso simboli di ambiente (_NT_SYMBOL_PATH).|-   True<br />-   False|  
|DeleteEtlsAfterAnalysis|Imposta un valore che determina se i file ETL sono eliminati dopo il completamento dell'analisi.|-   True<br />-   False|  
|SymbolPath|Specifica il percorso del server di simboli. Per altre informazioni, vedere [Usare il server di simboli Microsoft per ottenere il file di simboli di debug](http://go.microsoft.com/fwlink/?LinkID=149389).|Nome di directory o URL.|  
|Markers|Include l'elenco di provider marcatori.|Può includere zero o più elementi MarkerProvider.|  
|MarkerProvider|Specifica un singolo provider marcatori.|Deve contenere gli elementi seguenti:<br /><br /> -   Level<br />-   GUID<br />-   Name<br /><br /> Può includere questi elementi:<br /><br /> -   Categories<br />-   IsEnabled|  
|Livello|Imposta il livello di importanza di un MarkerProvider.|-   Basso<br />-   Normale<br />-   Alto<br />-   Critico<br />-   Tutto|  
|GUID|Identificatore univoco globale del provider marcatori ETW.|Un valore GUID.|  
|nome|Specifica la descrizione del provider marcatori.|Una stringa.|  
|Categories|Specifica le categorie raccolte per il provider marcatori.|Stringa delimitata da virgole che include numeri o intervalli di numeri.|  
|IsEnabled|Imposta un valore che determina se il provider marcatori è abilitato per la raccolta.|-   True<br />-   False|  
|FilterConfig|Specifica l'elenco di opzioni di configurazione degli eventi ETW filtrati dalla raccolta.|Può includere gli elementi seguenti:<br /><br /> -   CollectClrEvents<br />-   ClrCollectionOptions<br />-   CollectSampleEvents<br />-   CollectGpuEvents<br />-   CollectFileIO|  
|CollectClrEvents|Imposta un valore che determina se gli eventi CLR sono raccolti.|-   True<br />-   False|  
|ClrCollectionOptions|Specifica se raccogliere eventi CLR per app native e se raccogliere eventi di rundown NGEN.|Può includere uno, entrambi o nessuno dei valori seguenti:<br /><br /> -   CollectForNative<br />-   DisableNGenRundown|  
|CollectSampleEvents|Imposta un valore che determina se gli eventi campione sono raccolti.|-   True<br />-   False|  
|CollectGpuEvents|Imposta un valore che determina se gli eventi generati da DX sono raccolti.|-   True<br />-   False|  
|CollectFileIO|Imposta un valore che determina se gli eventi I/O su file sono raccolti.|-   True<br />-   False|  
|UserBufferSettings|Specifica l'elenco di parametri per impostazioni di buffer utente.|Deve contenere gli elementi seguenti:<br /><br /> -   BufferFlushTimer<br />-   BufferSize<br />-   MinimumBuffers<br />-   MaximumBuffers|  
|KernelBufferSettings|Specifica l'elenco di parametri per impostazioni di buffer kernel.|Deve contenere gli elementi seguenti:<br /><br /> -   BufferFlushTimer<br />-   BufferSize<br />-   MinimumBuffers<br />-   MaximumBuffers|  
|BufferFlushTimer|Specifica il timer di cancellazione dei buffer ETW.|Un numero intero positivo.|  
|BufferSize|Quantità di memoria allocata per ogni buffer di sessione di traccia di eventi, espressa in kilobyte.|Un numero compreso tra 0 e 1024.|  
|MinimumBuffers|Il numero minimo di buffer allocati per il pool di buffer della sessione di traccia degli eventi.|Un numero intero positivo maggiore di o uguale al doppio del numero di core logici.|  
|MaximumBuffers|Numero massimo di buffer allocati per il pool di buffer della sessione di traccia degli eventi.|Un numero maggiore di o uguale a MinimumBuffers.|  
|JustMyCode|Specifica l'elenco di directory Just My Code.|Un elenco di zero o più elementi MyCodeDirectory.|  
|MyCodeDirectory|Specifica una directory che include il codice dell'utente.|Un percorso assoluto.|  
  
### <a name="example"></a>Esempio  
 Invece di creare un file di configurazione completamente nuovo, è possibile copiare l'esempio seguente e quindi modificarlo in base alle proprie esigenze.  
  
```xml  
<?xml version="1.0"?>  
<LocalConfig xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" MajorVersion="1" MinorVersion="0">  
  
  <IncludeEnvSymbolPath>true</IncludeEnvSymbolPath>  
  
  <DeleteEtlsAfterAnalysis>true</DeleteEtlsAfterAnalysis>  
  
  <TraceLocation>C:\traces</TraceLocation>  
  
  <SymbolPath>http://symweb</SymbolPath>  
  
  <Markers>  
    <MarkerProvider Name="Default" Guid="8d4925ab-505a-483b-a7e0-6f824a07a6f0" Level="Low" />  
    <MarkerProvider Name="TPL" Guid="2e5dba47-a3d2-4d16-8ee0-6671ffdcd7b5" Level="Normal" />  
    <MarkerProvider Name="TPL Dataflow" Guid="16f53577-e41d-43d4-b47e-c17025bf4025" Level="Normal" />  
    <MarkerProvider Name="TPL Synchronization" Guid="ec631d38-466b-4290-9306-834971ba0217" Level="Normal" />  
    <MarkerProvider Name="PLINQ" Guid="159eeeec-4a14-4418-a8fe-faabcd987887" Level="Normal" />  
    <MarkerProvider Name="Concurrency Runtime" Guid="f7b697a3-4db5-4d3b-be71-c4d284e6592f" Level="Normal" />  
    <MarkerProvider Name="Scenario Markers" Guid="fb9244c9-f23a-4966-8a9c-97a51f8c355b" Level="Low" />  
  
    <!-- The IsEnabled and Categories elements are optional -->  
    <MarkerProvider Name="myMarker1" Guid="d0dbb3a3-895c-4ce6-96d9-28f69d664dc3" Level="Critical" IsEnabled="false" Categories="0,1,3-5,8" />  
    <MarkerProvider Name="myMarker2" Guid="03452127-a617-4302-9e30-c0d10442e4ee" Level="Low" IsEnabled="false" Categories="0,1,3-5,8-10,11-13" />  
  </Markers>  
  
  <FilterConfig>  
    <CollectClrEvents>true</CollectClrEvents>  
    <ClrCollectionOptions>CollectForNative DisableNGenRundown</ClrCollectionOptions>  
    <CollectSampleEvents>true</CollectSampleEvents>  
    <CollectGpuEvents>true</CollectGpuEvents>  
    <CollectFileIO>true</CollectFileIO>  
  </FilterConfig>  
  
  <UserBufferSettings>  
    <BufferFlushTimer>0</BufferFlushTimer>  
    <BufferSize>256</BufferSize>  
    <MinimumBuffers>512</MinimumBuffers>  
    <MaximumBuffers>1024</MaximumBuffers>  
  </UserBufferSettings>  
  
  <KernelBufferSettings>  
    <BufferFlushTimer>0</BufferFlushTimer>  
    <BufferSize>256</BufferSize>  
    <MinimumBuffers>512</MinimumBuffers>  
    <MaximumBuffers>1024</MaximumBuffers>  
  </KernelBufferSettings>  
  
  <!-- List of MyCodeDirectory directories -->  
  <JustMyCode>  
    <MyCodeDirectory>C:\myBinaries1</MyCodeDirectory>  
    <MyCodeDirectory>C:\myBinaries2</MyCodeDirectory>  
  </JustMyCode>  
</LocalConfig>  
  
```
