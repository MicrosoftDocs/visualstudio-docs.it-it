---
title: 'Procedura dettagliata: visualizzazione di suggerimenti lampadina | Microsoft Docs'
description: Informazioni su come creare una lampadina nell'editor di Visual Studio che viene visualizzata nella parola corrente e due azioni consigliate tramite questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ad000d486b0808ea4ddc3311daa7178c6eda1231
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080320"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>Procedura dettagliata: visualizzare i suggerimenti della lampadina
Le lampadine sono icone nell'editor di Visual Studio che si espandono per visualizzare un set di azioni, ad esempio correzioni per i problemi identificati dagli analizzatori di codice predefiniti o dal refactoring del codice.

 Negli editor di Visual C# e Visual Basic è anche possibile usare l'.NET Compiler Platform ("Roslyn") per scrivere e creare pacchetti di analizzatori di codice personalizzati con azioni che visualizzano automaticamente le lampadine. Per altre informazioni, vedere:

- [Procedura: scrivere una correzione del codice e di diagnostica C#](https://github.com/dotnet/roslyn/blob/master/docs/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix.md)

- [Procedura: scrivere un Visual Basic di diagnostica e correzione del codice](https://github.com/dotnet/roslyn/blob/master/docs/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix.md)

  Altri linguaggi come C++ forniscono anche lampadine per alcune azioni rapide, ad esempio, un suggerimento per creare un'implementazione Stub della funzione.

  Ecco come appare una lampadina. In un progetto Visual Basic o Visual C#, una zigzag rossa viene visualizzata sotto il nome di una variabile quando non è valida. Se si posiziona il puntatore del mouse sull'identificatore non valido, accanto al cursore viene visualizzata una lampadina.

  ![lampadina](../extensibility/media/lightbulb.png "Lampadina")

  Se si fa clic sulla freccia rivolta verso il basso accanto alla lampadina, viene visualizzato un set di azioni suggerite insieme a un'anteprima dell'azione selezionata. In questo caso, vengono visualizzate le modifiche apportate al codice se si esegue l'azione.

  ![anteprima di lampadina](../extensibility/media/lightbulbpreview.png "LightBulbPreview")

  È possibile usare le lampadine per fornire le proprie azioni suggerite. Ad esempio, è possibile fornire azioni per spostare le parentesi graffe di apertura in una nuova riga o spostarle alla fine della riga precedente. Nella procedura dettagliata riportata di seguito viene illustrato come creare una lampadina visualizzata nella parola corrente con due azioni consigliate: **convertire in lettere** maiuscole e **convertirle in lettere** minuscole.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Creare un progetto di Managed Extensibility Framework (MEF)

1. Creare un progetto VSIX in C#. Nella finestra di dialogo **nuovo progetto** selezionare **Visual C#/extensibility**, quindi **progetto VSIX**. Assegnare un nome alla soluzione `LightBulbTest` .

2. Aggiungere un modello di elemento **classificatore editor** al progetto. Per altre informazioni, vedere [creare un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Eliminare i file di classe esistenti.

4. Aggiungere il riferimento seguente al progetto e impostare **Copy Local** su `False` :

     *Microsoft.VisualStudio.Language.Intellisense*

5. Aggiungere un nuovo file di classe e denominarlo **LightBulbTest**.

6. Aggiungere le seguenti direttive using:

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

## <a name="implement-the-light-bulb-source-provider"></a>Implementare il provider di origine lampadina

1. Nel file di classe *LightBulbTest. cs* eliminare la classe LightBulbTest. Aggiungere una classe denominata **TestSuggestedActionsSourceProvider** che implementi <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> . Esportarlo con un nome di **test di azioni suggerite** e un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "testo".

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. All'interno della classe del provider di origine importare <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> e aggiungerlo come proprietà.

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> metodo per restituire un <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> oggetto. L'origine viene illustrata nella sezione successiva.

    ```csharp
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)
    {
        if (textBuffer == null || textView == null)
        {
            return null;
        }
        return new TestSuggestedActionsSource(this, textView, textBuffer);
    }
    ```

## <a name="implement-the-isuggestedactionsource"></a>Implementare ISuggestedActionSource
 L'origine dell'azione suggerita è responsabile della raccolta del set di azioni suggerite e della relativa aggiunta nel contesto corretto. In questo caso, il contesto è la parola corrente e le azioni suggerite sono **UpperCaseSuggestedAction** e **LowerCaseSuggestedAction**, come illustrato nella sezione seguente.

1. Aggiungere una classe **TestSuggestedActionsSource** che implementi <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> .

    ```csharp
    internal class TestSuggestedActionsSource : ISuggestedActionsSource
    ```

2. Aggiungere campi privati di sola lettura per il provider di origine dell'azione suggerito, il buffer di testo e la visualizzazione di testo.

    ```csharp
    private readonly TestSuggestedActionsSourceProvider m_factory;
    private readonly ITextBuffer m_textBuffer;
    private readonly ITextView m_textView;
    ```

3. Aggiungere un costruttore che imposta i campi privati.

    ```csharp
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)
    {
        m_factory = testSuggestedActionsSourceProvider;
        m_textBuffer = textBuffer;
        m_textView = textView;
    }
    ```

4. Aggiungere un metodo privato che restituisce la parola attualmente sotto il cursore. Il metodo seguente esamina la posizione corrente del cursore e chiede allo strumento di navigazione della struttura del testo l'ambito della parola. Se il cursore si trova su una parola, <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> viene restituito nel parametro out. in caso contrario, il `out` parametro è `null` e il metodo restituisce `false` .

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

5. Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>. L'editor chiama questo metodo per verificare se visualizzare la lampadina. Questa chiamata viene eseguita spesso, ad esempio, ogni volta che il cursore si sposta da una riga a un'altra o quando il mouse passa su un errore zigzag. È asincrona per consentire l'esecuzione di altre operazioni dell'interfaccia utente mentre questo metodo funziona. Nella maggior parte dei casi, questo metodo deve eseguire alcune operazioni di analisi e analisi della riga corrente, quindi l'elaborazione potrebbe richiedere del tempo.

     In questa implementazione, ottiene in modo asincrono l'oggetto <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> e determina se l'extent è significativo, ad esempio, se contiene testo diverso da uno spazio vuoto.

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

6. Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> metodo, che restituisce una matrice di <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> oggetti che contengono i diversi <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> oggetti. Questo metodo viene chiamato quando la lampadina viene espansa.

    > [!WARNING]
    > È necessario assicurarsi che le implementazioni di `HasSuggestedActionsAsync()` e `GetSuggestedActions()` siano coerenti; ovvero, se `HasSuggestedActionsAsync()` restituisce `true` , `GetSuggestedActions()` deve disporre di alcune azioni da visualizzare. In molti casi, `HasSuggestedActionsAsync()` viene chiamato immediatamente prima `GetSuggestedActions()` , ma questo non è sempre il caso. Se, ad esempio, l'utente richiama le azioni della lampadina premendo (**CTRL +** .), viene chiamato solo il metodo `GetSuggestedActions()` .

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

7. Definire un `SuggestedActionsChanged` evento.

    ```csharp
    public event EventHandler<EventArgs> SuggestedActionsChanged;
    ```

8. Per completare l'implementazione, aggiungere le implementazioni per `Dispose()` i `TryGetTelemetryId()` metodi e. Non si vuole eseguire la telemetria, quindi è sufficiente restituire `false` e impostare il GUID su `Empty` .

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

## <a name="implement-light-bulb-actions"></a>Implementare azioni lampadina

1. Nel progetto aggiungere un riferimento a *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll* e impostare **Copia localmente** su `False` .

2. Creare due classi, denominate `UpperCaseSuggestedAction` e `LowerCaseSuggestedAction`. Entrambe le classi implementano <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     Le due classi sono simili, con l'unica eccezione che una chiama <xref:System.String.ToUpper%2A> e l'altra chiama <xref:System.String.ToLower%2A>. Anche se i passaggi seguenti descrivono solo la classe dell'azione per le maiuscole, è necessario implementarle entrambe. Usare i passaggi per l'implementazione dell'azione per le maiuscole come criterio per l'implementazione dell'azione per le minuscole.

3. Aggiungere le seguenti direttive using per queste classi:

    ```csharp
    using Microsoft.VisualStudio.Imaging.Interop;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Documents;
    using System.Windows.Media;

    ```

4. Dichiarare un set di campi privati.

    ```csharp
    private ITrackingSpan m_span;
    private string m_upper;
    private string m_display;
    private ITextSnapshot m_snapshot;
    ```

5. Aggiungere un costruttore che imposta i campi.

    ```csharp
    public UpperCaseSuggestedAction(ITrackingSpan span)
    {
        m_span = span;
        m_snapshot = span.TextBuffer.CurrentSnapshot;
        m_upper = span.GetText(m_snapshot).ToUpper();
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));
    }
    ```

6. Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> metodo in modo che visualizzi l'anteprima dell'azione.

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> metodo in modo che restituisca un' <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> enumerazione vuota.

    ```csharp
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)
    {
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);
    }
    ```

8. Implementare le proprietà nel modo indicato di seguito.

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

9. Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> sostituendo il testo nell'intervallo con l'equivalente in maiuscole.

    ```csharp
    public void Invoke(CancellationToken cancellationToken)
    {
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);
    }
    ```

    > [!WARNING]
    > Il metodo di **richiamo** dell'azione lampadina non è previsto per la visualizzazione dell'interfaccia utente. Se l'azione attiva la nuova interfaccia utente (ad esempio, una finestra di dialogo di anteprima o di selezione), non visualizzare l'interfaccia utente direttamente dall'interno del metodo **Invoke** ma pianificare per visualizzare l'interfaccia utente dopo la restituzione da **Invoke**.

10. Per completare l'implementazione, aggiungere i `Dispose()` `TryGetTelemetryId()` metodi e.

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

11. Non dimenticare di eseguire la stessa operazione per `LowerCaseSuggestedAction` modificare il testo visualizzato in "convertire" {0} in lettere minuscole "e la chiamata <xref:System.String.ToUpper%2A> a <xref:System.String.ToLower%2A> .

## <a name="build-and-test-the-code"></a>Compilare e testare il codice
 Per testare questo codice, compilare la soluzione LightBulbTest ed eseguirla nell'istanza sperimentale.

1. Compilare la soluzione.

2. Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

3. Creare un file di testo e digitare alcune parole. Dovrebbe essere visualizzata una lampadina a sinistra del testo.

     ![test della lampadina](../extensibility/media/testlightbulb.png "TestLIghtBulb")

4. Puntare alla lampadina. Verrà visualizzata una freccia verso il basso.

5. Quando si fa clic sulla lampadina, verranno visualizzate due azioni consigliate, insieme all'anteprima dell'azione selezionata.

     ![test della lampadina, espanso](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")

6. Se si fa clic sulla prima azione, tutto il testo nella parola corrente deve essere convertito in maiuscolo. Se si fa clic sulla seconda azione, tutto il testo deve essere convertito in minuscolo.
