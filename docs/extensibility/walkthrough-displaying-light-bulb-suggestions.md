---
title: 'Procedura dettagliata: Visualizzazione dei suggerimenti lampadina | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 97ab32d4bfe0772d7b50ea1ca5a0b0ec143ed536
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-displaying-light-bulb-suggestions"></a>Procedura dettagliata: Visualizzazione dei suggerimenti lampadina
Le lampadine sono icone utilizzate nell'editor di Visual Studio che si espandono per visualizzare un set di azioni, ad esempio correzioni per i problemi identificati dagli analizzatori di codice incorporato o refactoring del codice.  
  
 Negli editor di Visual c# e Visual Basic, è inoltre possibile utilizzare .NET Compiler Platform ("Roslyn") per scrivere e raggruppare i propri analizzatori di codice con azioni che consentono di visualizzare le lampadine automaticamente. Per altre informazioni, vedere:  
  
-   [Procedura: Scrivere un c# diagnostica e la correzione del codice](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
-   [Procedura: Scrivere una correzione del codice e diagnostica di Visual Basic](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
 Altri linguaggi come C++ forniscono anche le lampadine per alcune azioni rapide, ad esempio un suggerimento per creare un'implementazione stub della funzione.  
  
 Ecco come appare una lampadina. In un progetto di Visual Basic o Visual c#, una sottolineatura ondulata rossa viene visualizzata in un nome di variabile quando non è valido. Quando si passa il mouse sull'identificatore non valido, viene visualizzata una lampadina accanto al cursore.  
  
 ![lampadina](../extensibility/media/lightbulb.png "lampadina")  
  
 Se si fa clic sulla freccia rivolta verso il basso per la lampadina, viene visualizzato un set di azioni suggerite, insieme a un'anteprima dell'azione selezionata. In questo caso, Mostra le modifiche che verranno apportate al codice se si esegue l'azione.  
  
 ![Anteprima di lampadina](../extensibility/media/lightbulbpreview.png "LightBulbPreview")  
  
 È possibile utilizzare le lampadine per fornire la propria azioni suggerite. Ad esempio, è possibile fornire azioni per spostare parentesi graffe aperte in una nuova riga o li si sposta alla fine della riga precedente. La procedura dettagliata seguente viene illustrato come creare una lampadina visualizzata sulla parola corrente e contenente due azioni consigliate: **convertire in lettere maiuscole** e **convertire in lettere minuscole**.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Creazione di un progetto Managed Extensibility Framework (MEF)  
  
1.  Creare un progetto VSIX in c#. (Nel **nuovo progetto** finestra di dialogo Seleziona **Visual c# / Extensibility**, quindi **progetto VSIX**.) Denominare la soluzione `LightBulbTest`.  
  
2.  Aggiungere un **classificatore Editor** modello di elemento al progetto. Per ulteriori informazioni, vedere [creazione di un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Eliminare i file di classe esistenti.  
  
4.  Aggiungere il seguente riferimento al progetto e impostare **Copia localmente** a `False`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
5.  Aggiungere un nuovo file di classe e assegnargli il nome **LightBulbTest**.  
  
6.  Aggiungere le seguenti istruzioni using:  
  
    ```csharp  
    using System;  
    using System.Linq;  
    using System.Collections.Generic;  
    using System.Threading.Tasks;  
    using Microsoft.VisualStudio.Language.Intellisense;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Operations;  
    using Microsoft.VisualStudio.Utilities;  
    using System.ComponentModel.Composition;  
    using System.Threading;  
  
    ```  
  
## <a name="implementing-the-light-bulb-source-provider"></a>Implementazione del Provider di origine di lampadina  
  
1.  Nel file di classe LightBulbTest.cs, eliminare la classe LightBulbTest. Aggiungere una classe denominata **TestSuggestedActionsSourceProvider** che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>. Esportarla con un nome di **azioni suggerite Test** e <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> impostato su "text".  
  
    ```csharp  
    [Export(typeof(ISuggestedActionsSourceProvider))]  
    [Name("Test Suggested Actions")]  
    [ContentType("text")]  
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider  
    ```  
  
2.  All'interno della classe di provider di origine, importare il <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> e aggiungerla come una proprietà.  
  
    ```csharp  
    [Import(typeof(ITextStructureNavigatorSelectorService))]  
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }  
    ```  
  
3.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> per restituire un <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> oggetto. Si parlerà di origine nella sezione successiva.  
  
    ```csharp  
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)  
    {  
        if (textBuffer == null && textView == null)  
        {  
            return null;  
        }  
        return new TestSuggestedActionsSource(this, textView, textBuffer);  
    }  
    ```  
  
## <a name="implementing-the-isuggestedactionsource"></a>Implementazione di ISuggestedActionSource  
 L'origine di azione suggerita è responsabile per la raccolta di set di azioni suggerite e aggiungerli nel contesto corretto. In questo caso il contesto è la parola corrente e le azioni consigliate sono **UpperCaseSuggestedAction** e **LowerCaseSuggestedAction**, che verranno descritte nella sezione seguente.  
  
1.  Aggiungere una classe **TestSuggestedActionsSource** che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
    ```csharp  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2.  Aggiungere campi privati di sola lettura per il provider di origine di azione suggerita, il buffer di testo e la visualizzazione del testo.  
  
    ```csharp  
    private readonly TestSuggestedActionsSourceProvider m_factory;  
    private readonly ITextBuffer m_textBuffer;  
    private readonly ITextView m_textView;  
    ```  
  
3.  Aggiungere un costruttore che imposta i campi privati.  
  
    ```csharp  
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)  
    {  
        m_factory = testSuggestedActionsSourceProvider;  
        m_textBuffer = textBuffer;  
        m_textView = textView;  
    }  
    ```  
  
4.  Aggiungere un metodo privato che restituisce la parola sotto il cursore. Il metodo seguente esegue la ricerca in corrispondenza della posizione del cursore e chiede lo strumento di navigazione di struttura di testo per l'estensione della parola. Se il cursore si trova su una parola, la <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> viene restituito nel parametro out; in caso contrario il `out` parametro `null` e il metodo restituisce `false`.  
  
    ```csharp  
    private bool TryGetWordUnderCaret(out TextExtent wordExtent)  
    {  
        ITextCaret caret = m_textView.Caret;  
        SnapshotPoint point;  
  
        if (caret.Position.BufferPosition > 0)  
        {  
            point = caret.Position.BufferPosition - 1;  
        }  
        else  
        {  
            wordExtent = default(TextExtent);  
            return false;  
        }  
  
        ITextStructureNavigator navigator = m_factory.NavigatorService.GetTextStructureNavigator(m_textBuffer);  
  
        wordExtent = navigator.GetExtentOfWord(point);  
        return true;  
    }  
    ```  
  
5.  Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>. L'editor chiama questo metodo per verificare che visualizzare la lampadina. Questa chiamata viene eseguita, molto spesso, ad esempio, ogni volta che il cursore si sposta da una riga a un altro o quando il mouse passa su una sottolineatura a zigzag di errore. È asincrono per consentire di esercitare quando questo metodo è in funzione delle altre operazioni dell'interfaccia utente. Nella maggior parte dei casi, che questo metodo deve eseguire alcune analisi e l'analisi della riga corrente, pertanto l'elaborazione potrebbe richiedere alcuni minuti.  
  
     Nell'implementazione ottiene in modo asincrono il <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> e determina se l'extent è significativo, ad esempio, se dispone di un testo diverso da spazi vuoti.  
  
    ```csharp  
    public Task<bool> HasSuggestedActionsAsync(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        return Task.Factory.StartNew(() =>  
        {  
            TextExtent extent;  
            if (TryGetWordUnderCaret(out extent))  
            {  
                // don't display the action if the extent has whitespace  
                return extent.IsSignificant;  
              }  
            return false;  
        });  
    }  
    ```  
  
6.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> metodo, che restituisce una matrice di <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> oggetti che contengono i diversi <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> oggetti. Questo metodo viene chiamato quando viene espanso la lampadina.  
  
    > [!WARNING]
    >  È necessario assicurarsi che le implementazioni di `HasSuggestedActionsAsync()` e `GetSuggestedActions()` sono coerente; ovvero, se `HasSuggestedActionsAsync()` restituisce `true`, quindi `GetSuggestedActions()` deve disporre di alcune azioni per la visualizzazione. In molti casi `HasSuggestedActionsAsync()` viene chiamato appena prima `GetSuggestedActions()`, ma questo non avviene sempre. Ad esempio, se l'utente richiama le azioni di lampadina premendo (CTRL +.) solo `GetSuggestedActions()` viene chiamato.  
  
    ```csharp  
    public IEnumerable<SuggestedActionSet> GetSuggestedActions(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        TextExtent extent;  
        if (TryGetWordUnderCaret(out extent) && extent.IsSignificant)  
        {  
            ITrackingSpan trackingSpan = range.Snapshot.CreateTrackingSpan(extent.Span, SpanTrackingMode.EdgeInclusive);  
            var upperAction = new UpperCaseSuggestedAction(trackingSpan);  
            var lowerAction = new LowerCaseSuggestedAction(trackingSpan);  
            return new SuggestedActionSet[] { new SuggestedActionSet(new ISuggestedAction[] { upperAction, lowerAction }) };  
        }  
        return Enumerable.Empty<SuggestedActionSet>();  
    }   
    ```  
  
7.  Definire un `SuggestedActionsChanged` evento.  
  
    ```csharp  
    public event EventHandler<EventArgs> SuggestedActionsChanged;  
    ```  
  
8.  Per completare l'implementazione, aggiungere le implementazioni per le `Dispose()` e `TryGetTelemetryId()` metodi. Non si desidera eseguire telemetria, è pertanto sufficiente restituire false e impostare il GUID vuoto.  
  
    ```csharp  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample provider and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
## <a name="implementing-light-bulb-actions"></a>Implementazione di azioni di lampadina  
  
1.  Nel progetto, aggiungere un riferimento a Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll e set **Copia localmente** a `False`.  
  
2.  Creare due classi, denominate `UpperCaseSuggestedAction` e il secondo denominato `LowerCaseSuggestedAction`. Entrambe le classi implementano <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.  
  
    ```csharp  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     Entrambe le classi sono simile, ad eccezione del fatto che una chiama <xref:System.String.ToUpper%2A> e l'altra chiama <xref:System.String.ToLower%2A>. Anche se i passaggi seguenti descrivono solo la classe dell'azione per le maiuscole, è necessario implementarle entrambe. Usare i passaggi per l'implementazione dell'azione per le maiuscole come criterio per l'implementazione dell'azione per le minuscole.  
  
3.  Aggiungere le seguenti istruzioni using per queste classi:  
  
    ```csharp  
    using Microsoft.VisualStudio.Imaging.Interop;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Documents;  
    using System.Windows.Media;  
  
    ```  
  
4.  Dichiarare un set di campi privati.  
  
    ```csharp  
    private ITrackingSpan m_span;  
    private string m_upper;  
    private string m_display;  
    private ITextSnapshot m_snapshot;  
    ```  
  
5.  Aggiungere un costruttore che imposta i campi.  
  
    ```csharp  
    public UpperCaseSuggestedAction(ITrackingSpan span)  
    {  
        m_span = span;  
        m_snapshot = span.TextBuffer.CurrentSnapshot;  
        m_upper = span.GetText(m_snapshot).ToUpper();  
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));  
    }  
    ```  
  
6.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> metodo in modo che venga visualizzato l'anteprima di azione.  
  
    ```csharp  
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)  
    {  
        var textBlock = new TextBlock();  
        textBlock.Padding = new Thickness(5);  
        textBlock.Inlines.Add(new Run() { Text = m_upper });  
        return Task.FromResult<object>(textBlock);  
    }  
    ```  
  
7.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> metodo in modo che restituisca un oggetto vuoto <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> enumerazione.  
  
    ```csharp  
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)  
    {  
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);  
    }  
    ```  
  
8.  Implementare le proprietà nel modo indicato di seguito.  
  
    ```csharp  
    public bool HasActionSets  
    {  
        get { return false; }  
    }  
    public string DisplayText  
    {  
        get { return m_display; }  
    }  
    public ImageMoniker IconMoniker  
    {  
       get { return default(ImageMoniker); }  
    }  
    public string IconAutomationText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public string InputGestureText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public bool HasPreview  
    {  
        get { return true; }  
    }  
    ```  
  
9. Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> metodo sostituendo il testo nell'intervallo con il relativo equivalente in caratteri maiuscoli.  
  
    ```csharp  
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    >  L'azione di lampadina **Invoke** metodo non è previsto per visualizzare l'interfaccia utente.  Se l'azione visualizzata la nuova interfaccia utente (ad esempio una finestra di anteprima o la selezione), non viene visualizzata l'interfaccia utente direttamente dall'interno di **Invoke** metodo ma pianificare invece per visualizzare l'interfaccia utente dopo la restituzione da **Invoke**.  
  
10. Per completare l'implementazione, aggiungere il `Dispose()` e `TryGetTelemetryId()` metodi.  
  
    ```csharp  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample action and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
11. Non dimenticare di eseguire la stessa operazione `LowerCaseSuggestedAction` modifica del testo visualizzato "Convertire '{0}' in lettere minuscole" e la chiamata <xref:System.String.ToUpper%2A> a <xref:System.String.ToLower%2A>.  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione LightBulbTest ed eseguirlo nell'istanza sperimentale.  
  
1.  Compilare la soluzione.  
  
2.  Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
3.  Creare un file di testo e digitare alcune parole. Verrà visualizzata una lampadina a sinistra del testo.  
  
     ![test della lampadina](../extensibility/media/testlightbulb.png "TestLIghtBulb")  
  
4.  Posizionare la lampadina. Verrà visualizzata una freccia rivolta verso il basso.  
  
5.  Quando si sceglie la lampadina, due azioni suggerite devono essere visualizzate, con l'anteprima dell'azione selezionata.  
  
     ![test della lampadina, espanso](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")  
  
6.  Se si fa clic sulla prima azione, tutto il testo nella parola corrente verrà convertito in maiuscole. Se si fa clic sulla seconda azione, tutto il testo nella parola corrente verrà convertito in minuscole.  
  