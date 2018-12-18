---
title: Aggiunta di un'estensione del protocollo di lingua del Server | Documenti Microsoft
ms.custom: ''
ms.date: 11/14/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bb6c82eab6878e99c9840ed593d9b9993056d391
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="adding-a-language-server-protocol-extension"></a>Aggiunta di un'estensione del protocollo di lingua del Server

Il protocollo Server Language (LSP) è un protocollo comune, nel formato v 2.0 RPC JSON, utilizzato per fornire funzionalità di servizio diversi editor di codice di lingua. Utilizza il protocollo, gli sviluppatori possono scrivere un server singolo linguaggio per fornire funzionalità quali IntelliSense, diagnostica degli errori del servizio di linguaggio, trovare tutti i riferimenti, e così via per diversi editor di codice che supportano il LSP. In genere, è possibile aggiungere servizi di linguaggio in Visual Studio mediante utilizzo dei file di grammatica TextMate per fornire funzionalità di base, ad esempio l'evidenziazione della sintassi o mediante la scrittura di servizi di linguaggio personalizzato utilizzando il set completo di API di estendibilità di Visual Studio per fornire dati più completi. A questo punto, il supporto per il LSP offre una terza opzione.

![servizio del protocollo server linguaggio in Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Protocollo di lingua del Server

Per ulteriori informazioni sul protocollo stesso, vedere la documentazione [qui](https://github.com/Microsoft/language-server-protocol). Implementazione del Visual Studio linguaggio del protocollo del Server è in anteprima e deve essere considerato il supporto sperimentale. La versione di anteprima è nel formato di un'estensione ([Language Server protocollo Client Preview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)), **ma questa estensione può essere installata solo in anteprima del canale di Visual Studio**. Una versione successiva di Visual Studio include supporto incorporato per il protocollo Server Language, in quale momento verrà eliminato il flag di anteprima. **Utilizzare l'anteprima non ai fini della produzione.**

Per ulteriori informazioni su come creare un server di esempio Java o come integrare un server esistente di linguaggio in Visual Studio Code, vedere la documentazione [qui](https://code.visualstudio.com/docs/extensions/example-language-server).

![implementazione del protocollo server Language](media/lsp-implementation.png)

In questo articolo viene descritto come creare un'estensione di Visual Studio che utilizza un server basato su LSP language. Presuppone che sia già stato creato un server basato su LSP in lingua e limitarsi a integrarlo in Visual Studio.

Per il supporto in Visual Studio, i server di linguaggio possono comunicare con il client (Visual Studio) tramite i meccanismi seguenti:

* Flussi di input/output standard
* Named pipe
* socket

Lo scopo del LSP e il relativo supporto in Visual Studio è per i servizi di linguaggio incorporata che non fanno parte del prodotto di Visual Studio. Non è progettato per estendere i servizi di linguaggio esistente (ad esempio c#) in Visual Studio. Per estendere i linguaggi esistenti, fare riferimento alla Guida di estendibilità del servizio di linguaggio (ad esempio, il ["Roslyn".NET Compiler Platform](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)).

## <a name="language-server-protocol-features-supported"></a>Funzionalità del protocollo Server linguaggio è supportata

Le seguenti funzionalità LSP sono supportate in Visual Studio fino a questo punto:

Messaggio | Offre supporto in Visual Studio
--- | ---
inizializzare | sì
inizializzato | sì
chiusura della sessione | sì
Uscita | sì
$/ cancelRequest | sì
finestra/showMessage | sì
window/showMessageRequest | sì
window/logMessage | sì
evento di telemetria / |
client/registerCapability |
client/unregisterCapability |
workspace/didChangeConfiguration | sì
area di lavoro/didChangeWatchedFiles | sì
area di lavoro/simboli | sì
area di lavoro/executeCommand | sì
area di lavoro/applyEdit | sì
textDocument/publishDiagnostics | sì
textDocument/didOpen | sì
textDocument/didChange | sì
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | sì
textDocument/didClose | sì
textDocument/completamento | sì
completamento/risoluzione | sì
textDocument/passaggio del mouse | sì
textDocument/signatureHelp | sì
textDocument e riferimenti | sì
textDocument/documentHighlight |
textDocument/documentSymbol | sì
textDocument/formattazione | sì
textDocument/rangeFormatting | sì
textDocument/onTypeFormatting |
textDocument/definizione | sì
textDocument/codeAction | sì
textDocument/codeLens |
codeLens/resolve |
textDocument/documentLink |
documentLink/risoluzione |
textDocument/rinominare | sì

## <a name="getting-started"></a>Introduzione

### <a name="create-a-vsix-project"></a>Creare un progetto VSIX

Per creare un'estensione del servizio di linguaggio utilizza un server basato su LSP language, assicurarsi innanzitutto di avere il **lo sviluppo di estensioni di Visual Studio** carico di lavoro installata per l'istanza di Visual Studio.

Successivamente, creare un nuovo VSIXProject vuoto, passare a **File** > **nuovo progetto** > **Visual c#**  >   **Estendibilità** > **progetto VSIX**:

![creare il progetto vsix](media/lsp-vsix-project.png)

Per la versione di anteprima, il supporto di Visual Studio per il LSP sarà sotto forma di un progetto VSIX ([Microsoft.VisualStudio.LanguageServer.Client.Preview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)). Gli sviluppatori di estensione che desiderano creare un'estensione tramite il server di linguaggio LSP devono accettare una dipendenza questo VSIX. Di conseguenza, i clienti che desiderano installare un'estensione del linguaggio server **necessario installare prima il progetto VSIX anteprima di linguaggio Server protocollo Client.**

Per definire la dipendenza VSIX, aprire la finestra di progettazione del manifesto VSIX per il progetto VSIX (facendo doppio clic sul file vsixmanifest nel progetto) e passare a **dipendenze**:

![Aggiungi riferimento al linguaggio server protocollo client](media/lsp-reference-lsp-dependency.png)

Creare una nuova dipendenza simile al seguente:

![definire una dipendenza di linguaggio server protocollo client](media/lsp-define-lsp-dependency.png)

* **Origine**: definiti manualmente
* **Nome**: anteprima del linguaggio Server protocollo Client
* **Identifier**: Microsoft.VisualStudio.LanguageServer.Client.Preview
* **Intervallo di versioni**: [1.0,2.0)
* **È come dipendenza viene risolta**: installato dall'utente
* **Scaricare URL**: [https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)

> [!NOTE]
> Il **URL di Download** deve essere compilato in modo che gli utenti che installano l'estensione come installare la dipendenza richiesta.

### <a name="language-server-and-runtime-installation"></a>Installazione di server e di runtime del linguaggio

Per impostazione predefinita, le estensioni create per supportare i server basati su LSP linguaggio in Visual Studio non include i server language o dei runtime necessari per l'esecuzione. Gli sviluppatori di estensione sono responsabili per la distribuzione i server di linguaggio e dei runtime necessiti. Esistono diversi modi per eseguire questa operazione:

* Server di linguaggio possono essere incorporati nel progetto VSIX come file di contenuto.
* Creare un file MSI per installare il server di lingua e/o runtime necessari.
* Vengono fornite istruzioni per gli utenti segnalano Marketplace come ottenere i server di runtime e della lingua.

### <a name="textmate-grammar-files"></a>File di grammatica TextMate

Il LSP non include specifiche su come fornire colorazione di testo per lingue. Per fornire la colorazione personalizzata per le lingue in Visual Studio, gli sviluppatori di estensione possono utilizzare un file di grammatica TextMate. Per aggiungere file di grammatica o tema TextMate personalizzati, seguire questi passaggi:

1. Creare una cartella denominata "Grammatiche" all'interno dell'estensione o può essere il nome desiderato.

2. All'interno della cartella "Grammatiche", includere i *.tmlanguage, *.plist, *.tmtheme, *. JSON file e si desidera che fornisce la colorazione personalizzata.

3. Fare doppio clic sul file e selezionare **proprietà**. Modificare l'azione di compilazione in **contenuto** e **Includi in VSIX** proprietà su true.

4. Creare un file. pkgdef e aggiungere una riga simile alla seguente:

  ```xml
  [$RootKey$\TextMate\Repositories]
  "MyLang"="$PackageFolder$\Grammars"
  ```

5. Fare doppio clic sul file e selezionare **proprietà**. Modificare l'azione di compilazione in **contenuto** e **Includi in VSIX** proprietà su true.

Dopo aver completato i passaggi precedenti, viene aggiunta una cartella "Grammatiche" installazione del pacchetto directory come un'origine di repository denominata 'MyLang' ('MyLang' è un nome per la risoluzione dell'ambiguità e può essere qualsiasi stringa univoca). Tutte le grammatiche (file .tmlanguage) e il tema file (.tmtheme) in questa directory vengono prelevate come potenziali e sostituiscono le grammatiche predefinite fornite con TextMate. Se le estensioni dichiarato del file di grammatica corrispondano l'estensione del file viene aperto, TextMate passerà.

## <a name="creating-a-simple-language-client"></a>Creazione di un client di un linguaggio semplice

### <a name="main-interface---ilanguageclientdotnetapimicrosoftvisualstudiolanguageserverclientilanguageclientviewvisualstudiosdk-2017"></a>Interfaccia principale - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

Dopo aver creato il progetto VSIX, aggiungere i seguenti pacchetti NuGet al progetto:

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Quando si utilizza una dipendenza sul pacchetto NuGet dopo aver completato i passaggi precedenti, i pacchetti di newtonsoft. JSON e StreamJsonRpc vengono aggiunti anche al progetto. **Non aggiornare i pacchetti a meno che non si è certi che le nuove versioni verranno installati nella versione di Visual Studio che le destinazioni di estensione**. Gli assembly non deve essere inclusi nel progetto VSIX, invece, essi verranno prelevati dalla directory di installazione di Visual Studio. Se si fa riferimento a una versione più recente degli assembly rispetto a ciò che viene installato nel computer dell'utente, l'estensione *non funzionerà*.

È quindi possibile creare una nuova classe che implementa il [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) interfaccia, l'interfaccia principale necessario per la connessione a un server di linguaggio basato su LSP ai client di linguaggio.

Di seguito è riportato un esempio:

```csharp
namespace MockLanguageExtension
{
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
        public string Name => "Bar Language Extension";

        public IEnumerable<string> ConfigurationSections => null;

        public object InitializationOptions => null;

        public IEnumerable<string> FilesToWatch => null;

        public event AsyncEventHandler<EventArgs> StartAsync;
        public event AsyncEventHandler<EventArgs> StopAsync;

        public async Task<Connection> ActivateAsync(CancellationToken token)
        {
            await Task.Yield();

            ProcessStartInfo info = new ProcessStartInfo();
            info.FileName = Path.Combine(Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location), "Server", @"MockLanguageServer.exe");
            info.Arguments = "bar";
            info.RedirectStandardInput = true;
            info.RedirectStandardOutput = true;
            info.UseShellExecute = false;
            info.CreateNoWindow = true;

            Process process = new Process();
            process.StartInfo = info;

            if (process.Start())
            {
                return new Connection(process.StandardOutput.BaseStream, process.StandardInput.BaseStream);
            }

            return null;
        }

        public async Task OnLoadedAsync()
        {
            await StartAsync?.InvokeAsync(this, EventArgs.Empty);
        }

        public async Task OnServerInitializeFailedAsync(Exception e)
        {
            return Task.CompletedTask;
        }

        public async Task OnServerInitializedAsync()
        {
            return Task.CompletedTask;
        }
    }
}
```

I metodi principali che devono essere implementate sono [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) e [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017). [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) viene chiamato quando l'estensione è caricata in Visual Studio e il server di lingua è pronto per essere avviata. In questo metodo, è possibile richiamare il [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) delegato immediatamente per segnalare che il server in lingua deve essere avviato o è possibile eseguire la logica aggiuntiva e richiamare [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) in un secondo momento. **Per attivare il server di lingua, è necessario chiamare StartAsync a un certo punto.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) è il metodo richiamato infine chiamando il [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) delegare; contiene la logica per avviare il server di linguaggio e stabilire la connessione. Deve essere restituito un oggetto connessione contenente flussi per la scrittura nel server e la lettura dal server. Tutte le eccezioni generate qui vengono intercettate e visualizzate all'utente tramite un messaggio sulla barra informazioni in Visual Studio.

### <a name="activation"></a>Attivazione

Dopo aver implementata la classe di client di lingua, è necessario definire due attributi per la definizione come verrà caricato in Visual Studio e attivato:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio Usa [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) per gestire i relativi punti di estendibilità. Il [esportare](https://msdn.microsoft.com/library/system.componentmodel.composition.exportattribute(v=vs.110).aspx) attributo indica a Visual Studio che questa classe deve essere prelevata come punto di estensione e caricata al momento appropriato.

Per utilizzare MEF, è necessario definire anche MEF come Asset nel manifesto VSIX.

Aprire la finestra di progettazione del manifesto VSIX e passare il **asset** scheda:

![Aggiungere asset MEF](media/lsp-add-asset.png)

Fare clic su Nuovo per creare un nuovo Asset:

![definire asset MEF](media/lsp-define-asset.png)

* **Tipo**: MefComponent
* **Origine**: un progetto nella soluzione corrente
* **Progetto**: [progetto]

### <a name="content-type-definition"></a>Definizione del tipo di contenuto

Attualmente l'unico modo per caricare l'estensione del linguaggio basato su LSP server è dal tipo di contenuto di file. Vale a dire, quando si definisce la classe client language (che implementa l'interfaccia [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)), è necessario definire i tipi di file che, quando aperto, farà sì che l'estensione da caricare. Se vengono aperti i file corrispondenti al tipo di contenuto definito, l'estensione non verrà caricata.

Questa operazione viene eseguita tramite la definizione di uno o più classi ContentTypeDefinition:

```csharp
namespace MockLanguageExtension
{
    public class BarContentDefinition
    {
        [Export]
        [Name("bar")]
        [BaseDefinition(CodeRemoteContentDefinition.CodeRemoteContentTypeName)]
        internal static ContentTypeDefinition BarContentTypeDefinition;


        [Export]
        [FileExtension(".bar")]
        [ContentType("bar")]
        internal static FileExtensionToContentTypeDefinition BarFileExtensionDefinition;
    }
}
```

Nell'esempio precedente, viene creata una definizione di tipo di contenuto per i file che terminano con `.bar` estensione di file. La definizione di tipo di contenuto è fornita la barra"nome" e **deve** derivano da [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017).

Dopo l'aggiunta di una definizione di tipo di contenuto, è possibile definire quando caricare l'estensione del linguaggio client nella classe del client di lingua:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

Aggiunta del supporto per i server di linguaggio LSP non richiede l'implementazione di sistema di progetto in Visual Studio. I clienti possono aprire un singolo file o una cartella in Visual Studio per iniziare a utilizzare il servizio di linguaggio. In realtà, il supporto per i server di linguaggio LSP è progettato per funzionare solo in scenari di cartelle e file aperti. Se viene implementato un sistema di progetto personalizzati, alcune funzionalità (ad esempio impostazioni) non funzionerà.

## <a name="advanced-features"></a>Funzionalità avanzate

### <a name="settings"></a>Impostazioni

Il supporto per le impostazioni specifiche della lingua server personalizzate è disponibile per la versione di anteprima del supporto LSP in Visual Studio, ma è ancora in corso viene migliorata. Le impostazioni sono specifiche per i quali il server di linguaggio supporta e in genere come server di linguaggio genera dati di controllo. Ad esempio, un server di lingua può avere un'impostazione per il numero massimo di errori segnalati. Gli autori delle estensioni potrebbero definire un valore predefinito, che può essere modificato dagli utenti per progetti specifici.

Eseguire la procedura seguente per aggiungere il supporto per le impostazioni per l'estensione del servizio di linguaggio LSP:

1. Aggiungere un file JSON (ad esempio, "MockLanguageExtensionSettings.json") nel progetto che contiene le impostazioni e i valori predefiniti. Ad esempio:

  ```json
  {
    "foo.maxNumberOfProblems": -1
  }
  ```
2. Fare clic con il pulsante destro sul file JSON e selezionare **proprietà**. Modifica il **compilare** azione "Contenuto" e "Includi in VSIX' impostata su true.

3. Implementare ConfigurationSections e restituire l'elenco di prefissi per le impostazioni definite nel file JSON (nel codice di Visual Studio, questo consente il mapping al nome di sezione di configurazione nel file package. JSON):

  ```csharp
  public IEnumerable<string> ConfigurationSections
  {
      get
      {
          yield return "foo";
      }
  }
  ```
4. Aggiungere al progetto un file. pkgdef (Aggiungi nuovo file di testo e impostare l'estensione di file. pkgdef). Il file pkgdef deve contenere queste info:

  ```xml
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
  ```

5. Fare clic con il pulsante destro sul file. pkgdef e selezionare **proprietà**. Modifica il **compilare** azione su "Contenuto" e la proprietà "Includi in VSIX" su true.

6. Aprire il `source.extension.vsixmanifest` file e aggiungere una risorsa nel **Asset** scheda:

  ![Modifica risorsa vspackage](media/lsp-add-vspackage-asset.png)

  * **Tipo**: Microsoft.VisualStudio.VsPackage
  * **Origine**: File nel file System
  * **Percorso**: [percorso al file pkgdef]

### <a name="user-editing-of-settings-for-a-workspace"></a>Utente di modifica delle impostazioni per un'area di lavoro

1. Utente apre un'area di lavoro contenente i file che server è proprietaria.
2. Utente aggiunge un file nella cartella "VS" chiamata "VSWorkspaceSettings.json".
3. Utente aggiunge una riga nel file VSWorkspaceSettings.json per un'impostazione che di server sono disponibili. Ad esempio:

  ```json
  {
    "foo.maxNumberOfProblems": 10
  }
  ```
### <a name="enabling-diagnostics-tracing"></a>Abilitazione della traccia di diagnostica
Traccia di diagnostica può essere abilitata per tutti i messaggi tra client e server, che può essere utile durante il debug di problemi di output.  Per abilitare la traccia diagnostica, eseguire le operazioni seguenti:

1. Aprire o creare il file di impostazioni dell'area di lavoro "VSWorkspaceSettings.json" (vedere "L'utente modifica delle impostazioni per un'area di lavoro").
2. Aggiungere la riga seguente nel file di impostazioni json:

```json
{
    "foo.server.trace": "Off"
}
```

Esistono tre possibili valori per il livello di dettaglio di traccia:
* "Off": la traccia viene completamente disattivato
* "Messages": traccia attivata ma solo metodo per nome e la risposta ID vengono tracciati.
* "Verbose": traccia attivata viene tracciato il messaggio intero rpc.

Quando il contenuto è attivata la traccia viene scritto in un file nella directory "% temp%\VisualStudio\LSP".  Il log viene indicato il formato di denominazione `[LanguageClientName]-[Datetime Stamp].log`.  Attualmente, la traccia può essere abilitata solo per gli scenari di cartella aperta.  Apertura di un singolo file per attivare un server di linguaggio non dispone di supporto di traccia di diagnostica.

### <a name="custom-messages"></a>Messaggi personalizzati

Sono disponibili le API disponibili per facilitare il passaggio di messaggi a e ricezione di messaggi dal server di linguaggio che non fanno parte del protocollo server linguaggio standard. Per gestire messaggi personalizzati, implementare [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) interfaccia nella classe del client di linguaggio. [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) libreria viene utilizzata per la trasmissione dei messaggi personalizzati tra il client di lingua e il server di linguaggio. Poiché l'estensione del client LSP linguaggio è come qualsiasi altra estensione di Visual Studio, è possibile decidere aggiungere ulteriori funzionalità (che non sono supportate da di Layered Service Provider) per Visual Studio (tramite le API di altri Visual Studio) nell'estensione tramite messaggi personalizzati.

#### <a name="receiving-custom-messages"></a>Ricezione di messaggi personalizzata

Per ricevere messaggi personalizzati dal server di lingua, implementare il [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) proprietà [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) e restituire un oggetto che sa come gestire i messaggi personalizzati . Esempio riportato di seguito:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public object CustomMessageTarget
    {
        get;
        set;
    }

    public class CustomTarget
    {
        public void OnCustomNotification(JToken arg)
        {
            // Provide logic on what happens OnCustomNotification is called from the language server
        }

        public string OnCustomRequest(string test)
        {
            // Provide logic on what happens OnCustomRequest is called from the language server
        }
    }
}
```

#### <a name="sending-custom-messages"></a>L'invio di messaggi personalizzato

Per inviare messaggi personalizzati per il server di lingua, implementare il [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) metodo [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017). Questo metodo viene richiamato quando il server di lingua è avviato e pronto a ricevere messaggi. Oggetto [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) oggetto viene passato come parametro, che è quindi possibile mantenere per inviare messaggi al server di linguaggio mediante [VS StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) API. Esempio riportato di seguito:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public async Task AttachForCustomMessageAsync(JsonRpc rpc)
    {
        await Task.Yield();

        this.customMessageRpc = rpc;
    }

    public async Task SendServerCustomNotification(object arg)
    {
        await this.customMessageRpc.NotifyWithParameterObjectAsync("OnCustomNotification", arg);
    }

    public async Task<string> SendServerCustomMessage(string test)
    {
        return await this.customMessageRpc.InvokeAsync<string>("OnCustomRequest", test);
    }
}
```

### <a name="middle-layer"></a>Livello intermedio

Uno sviluppatore di estensione può talvolta intercettare LSP i messaggi inviati e ricevuti dal server di linguaggio. Uno sviluppatore di estensione può ad esempio, si decida di modificare il parametro del messaggio inviato per un determinato messaggio LSP o modificare i risultati restituiti dal server di lingua per una funzionalità di Layered Service Provider (ad esempio i completamenti). Quando questo è necessario, agli sviluppatori di estensioni è possono utilizzare l'API MiddleLayer per intercettare i messaggi LSP.

Ogni messaggio LSP ha la propria interfaccia di livello intermedio per l'intercettazione. Per intercettare un messaggio specifico, creare una classe che implementa l'interfaccia di livello intermedio per il messaggio. Implementare quindi il [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) interfaccia nella classe del client di lingua e restituire un'istanza dell'oggetto nel [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) proprietà. Esempio riportato di seguito:

```csharp
public class MockLanguageClient: ILanguageClient, ILanguageClientCustomMessage
{
    public object MiddleLayer => MiddleLayerProvider.Instance;

    private class MiddleLayerProvider : ILanguageClientWorkspaceSymbolProvider
    {
        internal readonly static MiddleLayerProvider Instance = new MiddleLayerProvider();

        private MiddleLayerProvider()
        {
        }

        public async Task<SymbolInformation[]> RequestWorkspaceSymbols(WorkspaceSymbolParams param, Func<WorkspaceSymbolParams, Task<SymbolInformation[]>> sendRequest)
        {
            // Send along the request as given
            SymbolInformation[] symbols = await sendRequest(param);

            // Only return symbols that are "files"
            return symbols.Where(sym => string.Equals(new Uri(sym.Location.Uri).Scheme, "file", StringComparison.OrdinalIgnoreCase)).ToArray();
        }
    }
}
```

La funzionalità di livello intermedio è ancora in fase di sviluppo e non è ancora completa.

## <a name="sample-lsp-language-server-extension"></a>Estensione di esempio LSP lingua server

Per visualizzare il codice sorgente di un'estensione di esempio tramite la API client LSP in Visual Studio, vedere esempi di estendibilità di VSSDK [esempio LSP](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>Domande frequenti

**Come è possibile compilare un sistema di progetto personalizzati per integrare il server di linguaggio LSP per fornire un supporto di funzionalità in Visual Studio, come è possibile passare riguardo che?**

Supporto per server basati su LSP linguaggio in Visual Studio si basa sul [funzionalità Apri cartella](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/) ed è progettato specificamente per non richiedere un sistema di progetto personalizzati. È possibile compilare il sistema di progetto personalizzati attenendosi alle istruzioni [qui](https://github.com/Microsoft/VSProjectSystem), ma alcune funzionalità, ad esempio impostazioni, potrebbe non funzionare. La logica di inizializzazione predefinito per i server di linguaggio LSP consiste nel passare nel percorso della cartella radice della cartella attualmente aperta, pertanto se si utilizza un sistema di progetto personalizzati, è necessario fornire la logica personalizzata durante l'inizializzazione per garantire una lingua server possibile avviato correttamente.

**Come è possibile aggiungere il supporto del debugger?**

Si fornirà il supporto per il [comune debug protocollo](https://code.visualstudio.com/docs/extensionAPI/api-debugging) in una versione futura.

**Se è già presente un servizio di linguaggio supportato VS installato (ad esempio, JavaScript), è possibile comunque installare un'estensione del server di linguaggio LSP che offre funzionalità aggiuntive (ad esempio linting)?**

Sì, ma non tutte le funzionalità funzionerà correttamente. L'obiettivo finale per le estensioni del server di linguaggio LSP è per abilitare i servizi di linguaggio non supportati da Visual Studio. È possibile creare estensioni che offrono supporto aggiuntivo utilizzando LSP language server, ma alcune funzionalità (ad esempio IntelliSense) non sarà un'esperienza uniforme. In generale, è consigliabile che le estensioni del server LSP linguaggio utilizzato per fornire nuove esperienze di lingua, non si estende quelli esistenti.

**In cui pubblicare il server di linguaggio LSP VSIX completato**

Vedere le istruzioni di Marketplace [qui](walkthrough-publishing-a-visual-studio-extension.md).
