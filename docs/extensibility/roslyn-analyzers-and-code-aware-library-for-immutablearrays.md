---
title: Gli analizzatori di Roslyn e compatibile con codice di libreria per ImmutableArrays | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6ebafdd09e6fca0e1266c4eb03c4f6cb66554d06
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Gli analizzatori di Roslyn e compatibile con codice di libreria per ImmutableArrays

Il [.NET Compiler Platform](https://github.com/dotnet/roslyn) ("Roslyn") consente di creare raccolte basate su codice.  Una libreria di codice offre funzionalità che è possibile utilizzare e strumenti (Roslyn analizzatori) che consentono di utilizzare la libreria nel miglior modo o per evitare errori.  In questo argomento viene illustrato come compilare un analizzatore Roslyn reali per intercettare gli errori comuni quando si utilizza il [Immutable](https://www.nuget.org/packages/System.Collections.Immutable) pacchetto NuGet.  Nell'esempio viene inoltre illustrato come fornire una correzione del codice per un problema di codice rilevato dall'analizzatore.  Gli utenti visualizzeranno le correzioni del codice in Visual Studio lampadina dell'interfaccia utente ed è possono applicare una correzione per il codice automaticamente.

## <a name="getting-started"></a>Introduzione

È necessario quanto segue per compilare questo esempio:

* Visual Studio 2015 (non una versione Express Edition) o versione successiva.  È possibile utilizzare la versione gratuita [Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)
* [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  È inoltre possibile, quando si installa Visual Studio, verificare gli strumenti di estendibilità di Visual Studio in strumenti comuni per installare il SDK allo stesso tempo.  Se è già stato installato Visual Studio, è anche possibile installare questo SDK, passare al menu principale **File &#124; nuovo &#124;progetto...** , scegliendo c# nel riquadro di spostamento a sinistra e quindi estendibilità.  Quando si sceglie il "**installare strumenti di estendibilità di Visual Studio**" modello di progetto di navigazione, viene richiesto di scaricare e installare il SDK.
* [.NET compiler Platform ("Roslyn") SDK](http://aka.ms/roslynsdktemplates).  È inoltre possibile installare questo SDK, passare al menu principale **File &#124; nuovo &#124; progetto...** , scegliendo **c#** nel riquadro di spostamento a sinistra e quindi scegliere **estendibilità**.  Quando si sceglie "**scaricare il SDK della piattaforma del compilatore .NET**" modello di progetto di navigazione, viene richiesto di scaricare e installare il SDK.  Questo SDK include il [Roslyn sintassi Visualizzatore](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer).  In questo modo, strumento estremamente utile capire quali tipi di modello di codice deve cercare nell'analizzatore.  Le chiamate di infrastruttura analyzer nel codice per tipi di modello di codice specifico, in modo che il codice solo viene eseguito quando necessario e possibile concentrarsi solo sull'analisi codice pertinente.

## <a name="whats-the-problem"></a>Qual è il problema?

Si supponga è fornire una libreria con ImmutableArray (ad esempio, <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>) supportano.  Gli sviluppatori c# hanno molta esperienza con le matrici di .NET.  Tuttavia, a causa della natura delle tecniche ImmutableArrays e ottimizzazione utilizzata nell'implementazione, intuitions di sviluppatori c# provocare agli utenti della libreria di scrivere codice danneggiato, come illustrato di seguito.  Inoltre, gli utenti non vengono visualizzati gli errori in fase di esecuzione, non è l'esperienza di qualità che consentono di Visual Studio con .NET.

Gli utenti hanno familiarità con la scrittura di codice simile al seguente:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

Creazione di matrici vuote da riempire con le successive righe di codice e utilizzando la sintassi dell'inizializzatore di raccolta sono molto note agli sviluppatori di c#.  Tuttavia, scrivere lo stesso codice per un ImmutableArray arrestato in modo anomalo in fase di esecuzione:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

Il primo errore è dovuto a ImmutableArray dell'implementazione utilizzando una struttura per eseguire il wrapping dell'archivio dati sottostante. Struct devono disporre di costruttori senza parametri in modo che `default(T)` le espressioni possono restituire le strutture con tutti zero o null membri.  Quando il codice accede `b1.Length`, è presente un valore null alla fase di esecuzione di dereferenziazione errore perché non vi è alcun array di archiviazione sottostante nello struct ImmutableArray.  È il modo corretto per creare un ImmutableArray vuoto `ImmutableArray<int>.Empty`.

L'errore con inizializzatori di raccolta si verifica perché il metodo ImmutableArray.Add restituisce nuove istanze ogni volta che è possibile chiamare.  Poiché ImmutableArrays non cambiano mai, quando si aggiunge un nuovo elemento, verrà restituito un nuovo oggetto ImmutableArray (che può condividere l'archiviazione per motivi di prestazioni con un ImmutableArray già esistente).  Poiché `b2` punta al primo ImmutableArray prima di chiamare `Add()` cinque volte, `b2` è ImmutableArray predefinito.  La chiamata lunghezza su tale anche arresti anomali del sistema con un valore null dereferenziare l'errore.  Il modo corretto per inizializzare un ImmutableArray senza chiamata di Add manualmente, è possibile utilizzare `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.

## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Ricerca di tipi di nodo sintassi pertinente per attivare l'analizzatore

 Per iniziare a creare l'analizzatore, innanzitutto determinare il tipo di SyntaxNode si desidera cercare. Avviare il Visualizzatore di sintassi dal menu **View &#124; altre finestre &#124; Roslyn sintassi Visualizzatore**.

Posizionare il cursore dell'editor della riga che dichiara `b1`.  Si noterà che il Visualizzatore sintassi Mostra incluso in un `LocalDeclarationStatement` nodo della struttura di sintassi.  Questo nodo ha un `VariableDeclaration`, che a sua volta ha un `VariableDeclarator`, che a sua volta ha un `EqualsValueClause`e infine è disponibile un `ObjectCreationExpression`.  Quando fa clic nella struttura della sintassi visualizzatore dei nodi, la sintassi nella finestra dell'editor evidenzia per visualizzare il codice rappresentato da tale nodo.  I nomi dei tipi di sub SyntaxNode corrispondere i nomi utilizzati nella grammatica del linguaggio c#.

## <a name="creating-the-analyzer-project"></a>Creazione del progetto Analyzer

Nel menu principale scegliere **File &#124; nuovo &#124; progetto...** .  Nel **nuovo progetto** finestra di dialogo, in **c#** progetti nella barra di spostamento a sinistra, scegliere estendibilità e nel riquadro destro scegliere il **Analyzer con codice correggere** progetto modello.  Immettere un nome e la finestra di dialogo di conferma.

Il modello verrà aperto un file DiagnosticAnalyzer.cs.  Scegliere l'editor in questione come scheda di buffer.  Questo file contiene una classe analyzer (formato assegnato dal nome del progetto) che deriva da `DiagnosticAnalyzer` (un tipo di Roslyn API).  La nuova classe ha un `DiagnosticAnalyzerAttribute` dichiarando l'analizzatore è rilevante per il linguaggio c# in modo che il compilatore individua e carica l'analizzatore.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

È possibile implementare un analizzatore utilizzando Visual Basic che ha come destinazione del codice c#, e viceversa.  È più importante in DiagnosticAnalyzerAttribute per scegliere se l'analizzatore è destinato a una lingua o entrambi.  Analizzatori più sofisticati che richiedono modellazione dettagliata della lingua possono avere come destinazione solo una sola lingua.  Se l'analizzatore, controlli, ad esempio, solo i nomi dei tipi o i nomi dei membri pubblici, è possibile utilizzare il modello comune di linguaggio che roslyn offre in Visual Basic e c#.  Ad esempio, FxCop avverte che una classe implementa <xref:System.Runtime.Serialization.ISerializable>, ma la classe non dispone di <xref:System.SerializableAttribute> attributo è indipendente dal linguaggio e funziona per il codice Visual Basic e c#.

## <a name="initalizing-the-analyzer"></a>Inizializzazione dell'analizzatore

 Scorrere verso il basso un po' di `DiagnosticAnalyzer` classe per visualizzare il `Initialize` metodo.  Il compilatore chiama questo metodo quando si attiva un analizzatore.  Il metodo accetta un `AnalysisContext` oggetto che consente l'analizzatore per ottenere informazioni sul contesto e per registrare i callback per gli eventi per i tipi di codice che si desidera analizzare.

```csharp
public override void Initialize(AnalysisContext context) {}

```

Aprire una nuova riga in questo metodo e il tipo "contesto". Per visualizzare un elenco di completamento IntelliSense.  È possibile visualizzare nell'elenco di completamento sono disponibili molti `Register...` metodi per gestire diversi tipi di eventi.  Ad esempio, il primo, `RegisterCodeBlockAction`, richiama il codice per un blocco, di cui è in genere codice tra parentesi graffe.  La registrazione di un blocco anche richiama il codice per l'inizializzatore di campo, il valore assegnato a un attributo o il valore di un parametro facoltativo.

Se ad esempio `RegisterCompilationStartAction`, richiama il codice all'inizio di una compilazione, che risulta utile quando è necessario raccogliere lo stato in numerose posizioni.  È possibile creare una struttura di dati, ad esempio, per raccogliere tutti i simboli utilizzati, e ogni volta che viene richiamato l'analizzatore per alcune sintassi o di un simbolo, è possibile salvare informazioni su ogni posizione nella struttura di dati.  Quando è chiamato nuovamente a causa la chiusura di compilazione, è possibile analizzare tutti i percorsi di salvataggio, ad esempio, per segnalare i simboli nel codice viene utilizzato da ogni `using` istruzione.

Utilizzo di **sintassi Visualizzatore**, si è appreso che si desidera essere chiamato quando il compilatore elabora un ObjectCreationExpression.  Utilizzare questo codice per impostare il callback:

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Si registra per un nodo della sintassi e il filtro per solo nodi di sintassi creazione oggetto.  Per convenzione, gli autori di Analizzatore utilizzare un'espressione lambda quando si registra azioni, che consente di mantenere gli analizzatori senza stato.  È possibile utilizzare la funzionalità di Visual Studio **generazione dall'utilizzo** per creare il `AnalyzeObjectCreation` metodo.  Questo genera il tipo di parametro di contesto corretto troppo.

## <a name="setting-properties-for-users-of-your-analyzer"></a>Impostazione delle proprietà per gli utenti dell'analizzatore

In modo che l'analizzatore visualizzato nell'interfaccia utente di Visual Studio in modo appropriato, cercare e modificare la riga seguente di codice per identificare l'analizzatore:

```csharp
internal const string Category = "Naming";
```

Change `"Naming"` to `"API Guidance"`.

Quindi trovare e aprire il `Resources.resx` file nel progetto usando il **Esplora**.  È possibile inserire in una descrizione per l'analizzatore, titolo, e così via.  È possibile modificare il valore per tutti i componenti su `"Don't use ImmutableArray<T> constructor"` per ora.  È possibile inserire una stringa di formattazione della stringa ({0}, \\{1 \\} e così via), argomenti e versioni successive, quando si chiama `Diagnostic.Create()`, è possibile fornire un `params` matrice di argomenti da passare.

## <a name="analyzing-an-object-creation-expression"></a>L'analisi di un'espressione di creazione di oggetti

Il `AnalyzeObjectCreation` metodo accetta un tipo diverso di contesto fornito dal framework analyzer codice.  Il metodo Initialize `AnalysisContext` consente di registrare i callback di azione per impostare l'analizzatore.  Il `SyntaxNodeAnalysisContext`, ad esempio, ha un `CancellationToken` che è possibile passare intorno.  Se un utente avvia l'editor, Roslyn annullerà analizzatori in esecuzione per salvare lavoro e migliorare le prestazioni.  Ad esempio, questo contesto è una proprietà dei nodi che restituisce il nodo di sintassi di creazione di oggetti.

Ottenere il nodo, che è possibile presupporre che è il tipo per cui è applicato l'azione di nodo di sintassi:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launching-visual-studio-with-your-analyzer-the-first-time"></a>Avvio di Visual Studio con la prima volta l'analizzatore

Avviare Visual Studio compilando ed eseguendo l'analizzatore (premere **F5**).  Poiché nel progetto di avvio di **Esplora soluzioni** il progetto VSIX, che esegue le compilazioni di codice, il codice e un progetto VSIX e quindi avvia Visual Studio con tale estensione VSIX installato.  Quando si avvia Visual Studio in questo modo, viene avviato un hive del Registro di sistema distinti in modo che l'utilizzo principale di Visual Studio non sarà interessata da istanze di test durante la compilazione analizzatori.  La prima volta che si avvia in questo modo, Visual Studio esegue le inizializzazioni più simile a quando primo avvio di Visual Studio dopo l'installazione.

Creare un progetto console e quindi immettere il codice a matrice nel metodo Main applicazioni console:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

Le righe di codice con `ImmutableArray` avere linee a zigzag, perché è necessario ottenere il pacchetto NuGet non modificabile e aggiungere un `using` istruzione al codice.  Premere il pulsante destro del puntatore sul nodo del progetto nel **Esplora** e scegliere **Gestisci pacchetti NuGet...** .  In Gestione NuGet, digitare "Immutabile" nella casella di ricerca e scegliere l'elemento "Immutable" (non si sceglie "Immutable") nel riquadro sinistro e premere il pulsante installa nel riquadro di destra.  Il pacchetto di installazione aggiunge un riferimento ai riferimenti del progetto.

Viene comunque visualizzato le sottolineature rosse sotto `ImmutableArray`, pertanto, posizionare il cursore nell'identificatore e premere **CTRL +.** (punto) per visualizzare il menu di correzione suggerita e scegliere di aggiungere appropriata `using` istruzione.

**Salva tutto e chiudere** la seconda istanza di Visual Studio per il momento di inserire in uno stato pulito per continuare.

## <a name="finishing-the-analyzer-using-edit-and-continue"></a>Terminare l'analizzatore utilizzando Modifica e continuazione

Nella prima istanza di Visual Studio, impostare un punto di interruzione all'inizio del `AnalyzeObjectCreation` metodo premendo **F9** con il punto di inserimento alla prima riga.

Avviare l'analizzatore con **F5**e nella seconda istanza di Visual Studio, aprire nuovamente l'applicazione console creata l'ultima volta.

Poiché il compilatore Roslyn visto un'espressione di creazione di oggetti e ha l'analizzatore, tornare alla prima istanza di Visual Studio nel punto di interruzione.

**Ottenere il nodo di creazione di oggetti.** Passare alla riga che imposta il `objectCreation` variabile premendo **F10**e il **finestra controllo immediato** valutare l'espressione `"objectCreation.ToString()"`.  Si noti che il nodo della sintassi a cui fa riferimento la variabile è il codice `"new ImmutableArray<int>()"`, solo ciò che si sta cercando.

**Ottenere ImmutableArray < T\> oggetto tipo.** È necessario verificare se il tipo creato è ImmutableArray.  In primo luogo, si ottiene l'oggetto che rappresenta questo tipo.  Controllare i tipi di utilizzo del modello semantico per assicurarsi di avere esattamente il tipo corretto e non si confronta la stringa da ToString ().  Immettere la seguente riga di codice alla fine della funzione:

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

Specificare i tipi generici in metadati con backquotes (') e il numero di parametri generici.  Motivo per cui non viene visualizzato "... ImmutableArray\<T > "nel nome dei metadati.

Il modello semantico presenta molte operazioni utili che consentono di porre domande sui simboli, flusso di dati, la durata delle variabili e così via.  Roslyn separa i nodi di sintassi dal modello semantico per vari motivi engineering (prestazioni, modellazione codice errato e così via).  Si desidera il modello di compilazione per cercare le informazioni contenute nei riferimenti per il confronto accurato.

È possibile trascinare il puntatore di esecuzione giallo sul lato sinistro della finestra dell'editor.  Trascinarlo fino alla riga che imposta il `objectCreation` variabile ed Esegui istruzione/routine di nuova riga di codice usando **F10**.  Se si posiziona il puntatore del mouse sulla variabile `immutableArrayOfType`, vedrai che è stato rilevato il tipo esatto nel modello semantico.

**Ottenere il tipo dell'espressione per la creazione di oggetti.** "Tipo" viene usato in vari modi in questo articolo, ma questo significa che se è "Foo nuovo" espressione, è necessario ottenere un modello di Foo.  È necessario ottenere il tipo dell'espressione di creazione oggetto per verificare se è ImmutableArray\<T > tipo.  Utilizzare il modello semantico nuovamente per ottenere informazioni sui simboli per il simbolo di tipo (ImmutableArray) nell'espressione di creazione oggetto.  Immettere la seguente riga di codice alla fine della funzione:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

Perché l'analizzatore deve gestire errate o incomplete codice nell'editor buffer (ad esempio, manca un `using` istruzione), è consigliabile ricercare `symbolInfo` da `null`.  È necessario ottenere un tipo denominato (INamedTypeSymbol) dall'oggetto di informazioni sul simbolo per completare l'analisi.

**Confrontare i tipi.** Poiché è un tipo generico aperto di T che si sta cercando e il tipo nel codice è un tipo generico concreto, cercare le informazioni sul simbolo per il tipo è stato costruito da (un tipo generico aperto) e di confrontare il risultato con `immutableArrayOfTType`.  Immettere quanto segue alla fine del metodo:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Report diagnostica.** La diagnostica di Reporting è piuttosto semplice.  Utilizzare la regola creata nel modello di progetto, definito prima il metodo Initialize.  Poiché questa situazione nel codice non è un errore, è possibile modificare la riga che inizializzato regola sostituire `DiagnosticSeverity.Warning` (linee a zigzag verde) con `DiagnosticSeverity.Error` (sottolineatura ondulata rossa).  Il resto della regola Inizializza le risorse che nella parte iniziale della procedura dettagliata è stato modificato.  È necessario anche il percorso per linee a zigzag, ovvero la posizione della specifica del tipo dell'espressione di creazione oggetto del report.  Immettere il codice di `if` blocco:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

La funzione dovrebbe essere simile al seguente (ad esempio formattato in modo diverso):

```csharp
private void AnalyzeObjectCreation(SyntaxNodeAnalysisContext context)
{
    var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
    var immutableArrayOfTType =
        context.SemanticModel
               .Compilation
               .GetTypeByMetadataName(
                   "System.Collections.Immutable.ImmutableArray`1");
    var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as
        INamedTypeSymbol;
    if (symbolInfo != null &&
        symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
    {
        context.ReportDiagnostic(
            Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
    }
}
```

Rimuovere il punto di interruzione in modo che è possibile vedere il lavoro analyzer (e interrompere la restituzione alla prima istanza di Visual Studio).  Trascinare il puntatore di esecuzione all'inizio del metodo, premere **F5** per continuare l'esecuzione.  Quando si passa alla seconda istanza di Visual Studio, il compilatore inizieranno a esaminare di nuovo il codice e chiamerà l'analizzatore.  È possibile visualizzare una sottolineatura ondulata sotto `ImmutableType<int>`.

## <a name="adding-a-code-fix-for-the-code-issue"></a>Aggiunta di una correzione del codice"" per il problema di codice

Prima di iniziare, chiudere la seconda istanza di Visual Studio e arrestare il debug nella prima istanza di Visual Studio (in cui si sta sviluppando l'analizzatore).

**Aggiungere una nuova classe.** Utilizzare il menu di scelta rapida (pulsante destro del puntatore) sul nodo del progetto in Esplora soluzioni e scegliere di aggiungere un nuovo elemento.  Aggiungere una classe denominata `BuildCodeFixProvider`.  Questa classe deve derivare da `CodeFixProvider`, e sarà necessario utilizzare **CTRL +.** (punto) per richiamare la correzione del codice che aggiunge il corretto `using` istruzione.  Questa classe deve inoltre essere annotato con `ExportCodeFixProvider` attributo ed è necessario aggiungere un `using` istruzione per risolvere il `LanguageNames` enum.  È necessario disporre di un file di classe con il codice seguente:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**Eliminare i membri derivati.** A questo punto, posizionare il cursore dell'editor nell'identificatore `CodeFixProvider` e premere **CTRL +.** (punto) per eliminare i l'implementazione per questa classe di base astratta.  Questo genera una proprietà e un metodo.

**Implementa la proprietà.** Compilare il `FixableDiagnosticIds` della proprietà `get` corpo con il codice seguente:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn riunisce diagnostica e corregge creando una corrispondenza tra questi identificatori, che sono semplicemente delle stringhe.  Il modello di progetto generato un ID di diagnostica e sia possibile modificarlo.  Il codice nella proprietà restituisce solo l'ID dalla classe analyzer.

**Il metodo RegisterCodeFixAsync accetta un contesto.** Il contesto è importante perché diagnostica più possibile applicare una correzione del codice, o su una riga di codice potrebbe essere più di un problema.  Se si digita "contesto". nel corpo del metodo, l'elenco di completamento IntelliSense visualizzerà è alcuni membri utili.  È un membro oggetto CancellationToken che è possibile verificare se si desidera annullare la correzione.  È un membro di documento che presenta un numero elevato di membri utili e consente di ottenere gli oggetti modello di progetto e soluzione.  È un membro di intervallo che corrisponde all'inizio e fine del percorso del codice specificato quando è riportata la diagnostica.

**Rendere il metodo di essere asincrono.** La prima cosa è necessario eseguire è correggere la dichiarazione di metodo generato da un `async` metodo.  La correzione del codice per la generazione di stub di implementazione di una classe astratta non include il `async` (parola chiave) anche se il metodo restituisce un `Task`.

**Ottenere la radice dell'albero della sintassi.** Per modificare il codice che necessari per creare una nuova struttura di sintassi in base alle modifiche rende la correzione del codice.  È necessario il `Document` dal contesto per chiamare `GetSyntaxRootAsync`.  Questo è un metodo asincrono in quanto è ottenere l'albero della sintassi, inclusi eventualmente ottenere il file dal disco, analizzarlo e compilazione del modello di codice Roslyn per tale lavoro sconosciuto.  Durante questo periodo, utilizzare l'interfaccia utente di Visual Studio deve essere reattiva `async` consente.  Sostituire la riga di codice nel metodo con le operazioni seguenti:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Trovare il nodo con il problema.** Passare nell'intervallo del contesto, ma il nodo che si trova potrebbe non essere il codice che si desidera modificare.  Diagnostica restituita, l'intervallo viene fornita solo per l'identificatore di tipo (in cui apparteneva linee a zigzag), ma è necessario sostituire l'espressione di creazione oggetto intero, inclusi il `new` (parola chiave) all'inizio e le parentesi alla fine.  Aggiungere il codice seguente al metodo (e utilizzare **CTRL +.** Per aggiungere un `using` istruzione per `ObjectCreationExpressionSyntax`):

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**Registrare la correzione del codice per la lampadina dell'interfaccia utente.** Quando si registra la correzione del codice, Roslyn si collega la lampadina Visual Studio dell'interfaccia utente automaticamente.  Verrà visualizzato agli utenti finali possono usare **CTRL +.** (punto) quando l'analizzatore zigzag un' bad `ImmutableArray<T>` Usa costruttore.  Poiché il provider di correzione del codice viene eseguita solo quando si verifica un problema, è possibile presupporre che è l'espressione di creazione oggetto cercata.  Dal parametro di contesto, è possibile registrare la correzione del codice nuova aggiungendo il codice seguente alla fine di `RegisterCodeFixAsync` metodo:

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

È necessario posizionare il cursore dell'editor nell'identificatore `CodeAction`, quindi utilizzare **CTRL +.** (punto) per aggiungere le istruzioni `using` istruzione per questo tipo.

Quindi posizionare il cursore dell'editor nel `ChangeToImmutableArrayEmpty` identificatore e utilizzare **CTRL +.** per generare questo stub del metodo per l'utente.

Questo frammento di codice ultimo aggiunto registra la correzione del codice passando un `CodeAction` e l'ID di diagnostica per il tipo di problema rilevato.  In questo esempio è disponibile un solo ID di diagnostica questo codice fornisce correzioni per, pertanto è possibile passare solo il primo elemento della matrice ID di diagnostica.  Quando si crea il `CodeAction`, si passa il testo che deve usare la lampadina dell'interfaccia utente come una descrizione della correzione del codice.  È inoltre possibile passare in una funzione che accetta un oggetto CancellationToken e restituisce un nuovo documento.  Il nuovo documento è una nuova struttura di sintassi che include il codice corretto che chiama `ImmutableArray.Empty`.  Frammento di codice seguente usa un'espressione lambda in modo che è possibile chiudere il nodo objectCreation e documento del contesto.

**Creare la nuova struttura di sintassi.** Nel `ChangeToImmutableArrayEmpty` metodo il cui stub generato in precedenza, immettere la riga di codice: `ImmutableArray<int>.Empty;`.  Se si visualizza di nuovo la finestra degli strumenti del Visualizzatore di sintassi, è possibile visualizzare che questa sintassi è un nodo SimpleMemberAccessExpression.  Ovvero requisiti di questo metodo per creare e restituire un nuovo documento.

La prima modifica `ChangeToImmutableArrayEmpty` consiste nell'aggiungere `async` prima `Task<Document>` perché i generatori di codice non possono presupporre il metodo deve essere asincrono.

Compilare il corpo con il codice seguente in modo che il metodo è simile al seguente:

```csharp
private async Task<Document> ChangeToImmutableArrayEmpty(
    ObjectCreationExpressionSyntax objectCreation, Document document,
    CancellationToken c)
{
    var generator = SyntaxGenerator.GetGenerator(document);
    var memberAccess =
        generator.MemberAccessExpression(objectCreation.Type, "Empty");
    var oldRoot = await document.GetSyntaxRootAsync(c);
    var newRoot = oldRoot.ReplaceNode(objectCreation, memberAccess);
    return document.WithSyntaxRoot(newRoot);
}
```

È necessario inserire il cursore dell'editor nel `SyntaxGenerator` identificatore e utilizzare **CTRL +.** (punto) per aggiungere le istruzioni `using` istruzione per questo tipo.

Questo codice Usa `SyntaxGenerator`, che è un tipo particolarmente utile per la creazione di nuovo codice.  Dopo il recupero di un generatore per il documento che presenta il problema di codice, `ChangeToImmutableArrayEmpty` chiamate `MemberAccessExpression`, passando il tipo che include il membro che si desidera accedere a e il nome del membro come una stringa.

Successivamente, il metodo recupera la radice del documento e, poiché ciò può implicare lavoro arbitrario nel caso generale, il codice attende la chiamata e passa il token di annullamento.  Modelli di codice Roslyn sono immutabili, all'utilizzo di una stringa di .NET. Quando si aggiorna la stringa, viene visualizzato in un nuovo oggetto stringa.  Quando si chiama `ReplaceNode`, verrà restituito un nuovo nodo radice.  La maggior parte dell'albero della sintassi è condiviso (perché è non modificabile), ma la `objectCreation` nodo viene sostituito con il `memberAccess` nodo, nonché tutti i nodi padre fino alla radice dell'albero di sintassi.

## <a name="trying-your-code-fix"></a>Tentativo di correzione del codice

È ora possibile premere **F5** per eseguire l'analizzatore in una seconda istanza di Visual Studio.  Aprire il progetto console usata in precedenza.  Ora dovrebbero apparire la lampadina in cui l'espressione di creazione del nuovo oggetto è per `ImmutableArray<int>`.  Se si preme **CTRL +.** (periodo), quindi verrà visualizzato il codice correggere, per visualizzare un'anteprima di differenza del codice generato automaticamente nella lampadina dell'interfaccia utente.  Roslyn crea automaticamente questo.

**Suggerimento Pro:** se si avvia la seconda istanza di Visual Studio, non viene visualizzata la lampadina con la correzione del codice, quindi potrebbe essere necessario cancellare la cache dei componenti di Visual Studio.  Cancellazione della cache impone a Visual Studio per esaminare nuovamente i componenti, in modo da Visual Studio deve quindi prelevare il componente più recente.  In primo luogo, arrestare la seconda istanza di Visual Studio.  In Esplora risorse, passare alla directory dell'utente (c:\users\\< userid\>) e individuare AppData\Local\Microsoft\VisualStudio\14.0Roslyn\\.  In questa directory, eliminare la directory di sub ComponentModelCache.  Le modifiche alla versione con Visual Studio "14".

## <a name="talk-video-and-finish-code-project"></a>Video di conversazione e il progetto di codice di fine

È possibile visualizzare in questo esempio viene sviluppato e descritti più avanti nel [questa discussione](http://channel9.msdn.com/events/Build/2015/3-725).  La conversazione viene illustrato l'analizzatore di lavoro e viene illustrata la creazione.

È possibile visualizzare tutto il codice completato [qui](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers).  Sottocartelle DoNotUseImmutableArrayCollectionInitializer e DoNotUseImmutableArrayCtor dispongano di un file c# per la ricerca di problemi e un file c# che implementa le correzioni del codice che compaiono nella lampadina Visual Studio dell'interfaccia utente.  Si noti che il codice completato è un po' più astrazione per evitare il recupero di massa ImmutableArray\<T > tipo di oggetto più volte.  Usa le azioni registrate nidificate per salvare l'oggetto di tipo in un contesto che è disponibile ogni volta che le azioni di sub (analizzare la creazione di oggetti e analizzare le inizializzazioni di raccolta) eseguire.

## <a name="see-also"></a>Vedere anche

* [\\Talk \Build 2015](http://channel9.msdn.com/events/Build/2015/3-725)
* [Codice completato su GitHub](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [Alcuni esempi su GitHub, raggruppati in tre tipi di analizzatori](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [Altri documenti nel sito di SharePoint Server GitHub](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [Regole FxCop implementate con gli analizzatori di Roslyn su GitHub](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
