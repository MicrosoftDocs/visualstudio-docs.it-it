---
title: Servizio di linguaggio e i punti di estensione di Editor | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d3c253ba52da1fd6bb9133e44ba6858e8f1a4151
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="language-service-and-editor-extension-points"></a>Servizio di linguaggio e i punti di estensione di Editor
L'editor fornisce punti di estensione che è possibile estendere come parti componente Managed Extensibility Framework (MEF), tra cui la maggior parte delle funzionalità di servizio del linguaggio. Ecco le categorie di punto di estensione principale:  
  
-   Tipi di contenuto  
  
-   Tipi di classificazione e i formati di classificazione  
  
-   Margini e le barre di scorrimento  
  
-   Tag  
  
-   Aree di controllo  
  
-   Processori di mouse  
  
-   Gestori di rilascio  
  
-   Opzioni  
  
-   IntelliSense  
  
## <a name="extending-content-types"></a>Estensione di tipi di contenuto  
 Tipi di contenuto sono riportate le definizioni dei tipi di testo gestito dall'editor, ad esempio, "text", "code" o "CSharp". Definire un nuovo tipo di contenuto dichiarando una variabile del tipo <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> e assegnando il nuovo tipo di contenuto di un nome univoco. Per registrare il tipo di contenuto con l'editor, esportarlo con gli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute> è il nome del tipo di contenuto.  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> è il nome del tipo di contenuto da cui deriva questo tipo di contenuto. Un tipo di contenuto può ereditare da più altri tipi di contenuto.  
  
 Poiché il <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> è una classe sealed, è possibile esportarlo con nessun parametro di tipo.  
  
 Nell'esempio seguente mostra gli attributi di esportazione su una definizione di tipo di contenuto.  
  
```  
[Export]  
[Name("test")]  
[BaseDefinition("code")]  
[BaseDefinition("projection")]  
internal static ContentTypeDefinition TestContentTypeDefinition;  
```  
  
 Tipi di contenuto possono essere basati su zero o più tipi di contenuto pre-esistenti. Questi sono i tipi predefiniti:  
  
-   Qualsiasi: il tipo di contenuto di base. Elemento padre di tutti gli altri tipi di contenuto.  
  
-   Text: il tipo base per il contenuto non proiezione. Eredita da "any".  
  
-   Testo normale: per il testo non di codice. Eredita da "text".  
  
-   Codice: per il codice di tutti i tipi. Eredita da "text".  
  
-   Inerte: esclude il testo da qualsiasi tipo di gestione. Testo di questo tipo di contenuto non è mai un qualsiasi estensione applicato.  
  
-   Proiezione: per il contenuto del buffer di proiezione. Eredita da "any".  
  
-   IntelliSense: per il contenuto di IntelliSense. Eredita da "text".  
  
-   Sighelp: supporto di firme. Eredita da "intellisense".  
  
-   Sighelp-doc: documentazione della Guida firma. Eredita da "intellisense".  
  
 Questi sono alcuni dei tipi di contenuto sono definiti da Visual Studio e alcune delle lingue che sono ospitate in Visual Studio:  
  
-   Basic  
  
-   C/C++  
  
-   ConsoleOutput  
  
-   CSharp  
  
-   CSS  
  
-   ENC  
  
-   FindResults  
  
-   F#  
  
-   HTML  
  
-   JScript  
  
-   XAML  
  
-   XML  
  
 Per individuare l'elenco di tipi di contenuto disponibili, importare il <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>, che gestisce la raccolta di tipi di contenuto per l'editor. Il codice seguente importa il servizio come una proprietà.  
  
```  
[Import]  
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }  
```  
  
 Per associare un tipo di contenuto con un'estensione di file, utilizzare <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>.  
  
> [!NOTE]
>  In Visual Studio, estensioni di file registrate utilizzando il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> in un pacchetto del servizio di linguaggio. Il <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> associa un tipo di contenuto MEF con un'estensione di file che è stata registrata in questo modo.  
  
 Per esportare l'estensione del nome file alla definizione del tipo di contenuto, è necessario includere gli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: specifica l'estensione del nome file.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: Specifica il tipo di contenuto.  
  
 Poiché il <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> è una classe sealed, è possibile esportarlo con nessun parametro di tipo.  
  
 Nell'esempio seguente mostra gli attributi di esportazione in un'estensione di file a una definizione del tipo di contenuto.  
  
```  
[Export]  
[FileExtension(".test")]  
[ContentType("test")]  
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;  
```  
  
 Il <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> gestisce le associazioni tra estensioni di file e tipi di contenuto.  
  
## <a name="extending-classification-types-and-classification-formats"></a>Formati di estensione di classificazione e tipi di classificazione  
 È possibile utilizzare i tipi di classificazione per definire i tipi di testo per il quale si desidera fornire una gestione diversa (ad esempio, colorazione verde il testo "parola chiave" blu e il testo "comment"). Definire un nuovo tipo di classificazione dichiarando una variabile di tipo <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> e assegnargli un nome univoco.  
  
 Per registrare il tipo di classificazione con l'editor, esportarlo con gli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: il nome del tipo di classificazione.  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: il nome del tipo di classificazione da cui eredita il tipo di classificazione. Tutti i tipi di classificazione ereditano da "text" e un tipo di classificazione può ereditare da più altri tipi di classificazione.  
  
 Poiché il <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> è una classe sealed, è possibile esportarlo con nessun parametro di tipo.  
  
 Nell'esempio seguente mostra gli attributi di esportazione su una definizione di tipo di classificazione.  
  
```  
[Export]  
[Name("csharp.test")]  
[BaseDefinition("test")]  
internal static ClassificationTypeDefinition CSharpTestDefinition;  
```  
  
 Il <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> fornisce l'accesso alle classificazioni standard. Questi tipi di classificazione predefinite:  
  
-   "text"  
  
-   "lingua" (deriva da "text")  
  
-   "linguaggio formale" (deriva da "text")  
  
-   "stringa" (deriva da "literal")  
  
-   "character" (deriva da "literal")  
  
-   "numerico" (deriva da "literal")  
  
 Ereditare da un set di tipi di errore diverso da <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>. Includono i tipi di errore seguente:  
  
-   "errore di sintassi"  
  
-   "Errore del compilatore"  
  
-   "altro errore"  
  
-   "avviso"  
  
 Per individuare l'elenco di tipi di classificazione disponibili, importare il <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>, che gestisce la raccolta di tipi di classificazione per l'editor. Il codice seguente importa il servizio come una proprietà.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }  
```  
  
 È possibile definire una definizione di formato di classificazione per il nuovo tipo di classificazione. Derivare una classe da <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> ed esportarlo con il tipo <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>, insieme con gli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: il nome del formato.  
  
-   <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: il nome visualizzato del formato.  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Specifica se il formato viene visualizzato nel **tipi di carattere e colori** pagina del **opzioni** finestra di dialogo.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: la priorità del formato. I valori validi sono da <xref:Microsoft.VisualStudio.Text.Classification.Priority>.  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: il nome della classificazione tipo per cui questo formato è stato eseguito il mapping.  
  
 Nell'esempio seguente mostra gli attributi di esportazione su una definizione di formato di classificazione.  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[ClassificationType(ClassificationTypeNames = "test")]  
[Name("test")]  
[DisplayName("Test")]  
[UserVisible(true)]  
[Order(After = Priority.Default, Before = Priority.High)]  
internal sealed class TestFormat : ClassificationFormatDefinition  
```  
  
 Per individuare l'elenco dei formati disponibili, importare il <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>, che gestisce la raccolta di formati per l'editor. Il codice seguente importa il servizio come una proprietà.  
  
```  
[Import]  
internal IEditorFormatMapService FormatMapService { get; set; }  
```  
  
## <a name="extending-margins-and-scrollbars"></a>Le barre di scorrimento e i margini di estensione  
 Margini e le barre di scorrimento sono gli elementi di visualizzazione principale dell'editor oltre la visualizzazione del testo. È possibile fornire un numero qualsiasi di margini oltre i margini standard che vengono visualizzati intorno alla visualizzazione di testo.  
  
 Implementare un <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> interfaccia per definire un margine. È inoltre necessario implementare la <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interfaccia per creare il margine.  
  
 Per registrare il provider di margine con l'editor, è necessario esportare il provider con gli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: il nome del margine.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l'ordine in cui viene visualizzata sul margine, rispetto a altro margine.  
  
     I margini predefiniti sono:  
  
    -   "Barra di scorrimento orizzontale Wpf"  
  
    -   "Barra di scorrimento verticale Wpf"  
  
    -   "Margine di numeri di riga Wpf"  
  
     I margini orizzontali che hanno un attributo di ordine di `After="Wpf Horizontal Scrollbar"` vengono visualizzati sotto il margine predefinito e i margini orizzontali che hanno un attributo di ordine di `Before ="Wpf Horizontal Scrollbar"` vengono visualizzati sopra il margine predefinito. I margini verticali che hanno un attributo di ordine di destra `After="Wpf Vertical Scrollbar"` vengono visualizzate a destra della barra di scorrimento. A sinistra i margini verticali che hanno un attributo di ordine di `After="Wpf Line Number Margin"` apparire a sinistra del margine di numeri di riga (se è visibile).  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: il tipo del margine (sinistro, destro, superiore o inferiore).  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: il tipo di contenuto (ad esempio, "text" o "code") per il quale un margine è valido.  
  
 Nell'esempio seguente mostra gli attributi di esportazione in un provider di margine di un margine che viene visualizzato a destra del margine di numeri di riga.  
  
```  
[Export(typeof(IWpfTextViewMarginProvider))]  
[Name("TestMargin")]  
[Order(Before = "Wpf Line Number Margin")]  
[MarginContainer(PredefinedMarginNames.Left)]  
[ContentType("text")]   
```  
  
## <a name="extending-tags"></a>Estensione di tag  
 I tag sono un modo per associare dati a diversi tipi di testo. In molti casi, i dati associati vengono visualizzati come un effetto visivo, ma non tutti i tag sono una rappresentazione visiva. È possibile definire un proprio tipo di tag implementando <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. È inoltre necessario implementare <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> per fornire i tag per un determinato set di intervalli di testo e un <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> per fornire il tagger. È necessario esportare il provider di tagger insieme agli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: il tipo di contenuto (ad esempio, "text" o "code") per il quale il tag è valido.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: il tipo di tag.  
  
 Nell'esempio seguente mostra gli attributi di esportazione in un provider di tagger.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 I tipi di tag seguenti sono incorporati:  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: associato un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: associati ai tipi di errore.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: associata a un'area di controllo.  
  
    > [!NOTE]
    >  Per un esempio di un <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, vedere la definizione di HighlightWordTag nella [procedura dettagliata: evidenziazione testo](../extensibility/walkthrough-highlighting-text.md).  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: associati alle aree che possono essere espansi o compressi nella struttura.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: definisce lo spazio occupato un'area di controllo in una visualizzazione di testo. Per ulteriori informazioni sulla negoziazione spazio ulteriori informazioni, vedere la sezione seguente.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: fornisce spaziatura automatica e ridimensionamento per l'area di controllo.  
  
 Per trovare e utilizzare tag per i buffer e le viste, importare il <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> o <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>, che consentono un <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> del tipo richiesto. Il codice seguente importa il servizio come una proprietà.  
  
```  
[Import]  
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }  
```  
  
#### <a name="tags-and-markerformatdefinitions"></a>Tag e MarkerFormatDefinitions  
 È possibile estendere la <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> classe per definire l'aspetto di un tag. È necessario esportare la classe (come un <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>) con gli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: il nome utilizzato per fare riferimento a questo formato  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: in questo modo, il formato da visualizzare nell'interfaccia utente  
  
 Nel costruttore, definire il nome visualizzato e l'aspetto del tag. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> definisce il colore di riempimento e <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> definisce il colore del bordo. Il <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> è il nome della definizione del formato localizzabile.  
  
 Di seguito è riportato un esempio di una definizione di formato:  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
[UserVisible(true)]  
internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
{  
    public HighlightWordFormatDefinition()  
    {  
        this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";   
        this.ZOrder = 5;  
    }  
}  
  
```  
  
 Per applicare questa definizione di formato a un tag, fare riferimento il nome impostato nell'attributo nome della classe (non il nome visualizzato).  
  
> [!NOTE]
>  Per un esempio di un <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, vedere la classe HighlightWordFormatDefinition in [procedura dettagliata: evidenziazione testo](../extensibility/walkthrough-highlighting-text.md).  
  
## <a name="extending-adornments"></a>Estensione delle aree di controllo  
 Le aree di controllo definiscono effetti visivi che possono essere aggiunti al testo visualizzato in una visualizzazione di testo o al testo della visualizzazione stessa. È possibile definire la propria area di controllo come qualsiasi tipo di <xref:System.Windows.UIElement>.  
  
 Nella classe dell'area di controllo, è necessario dichiarare un <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>. Per registrare il livello di area di controllo, esportarlo con gli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: il nome dell'area di controllo.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l'ordinamento dell'area di controllo rispetto ad altri livelli dell'area di controllo. La classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> definisce quattro livelli predefinito: testo, struttura, cursore e selezione.  
  
 Nell'esempio seguente mostra gli attributi di esportazione su una definizione di livello dell'area di controllo.  
  
```  
[Export]  
[Name("TestEmbeddedAdornment")]  
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testLayerDefinition;  
```  
  
 È necessario creare una seconda classe che implementa <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> e gestisce il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> eventi creando un'area di controllo. È necessario esportare questa classe insieme agli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: il tipo di contenuto (ad esempio, "text" o "code") per il quale l'area di controllo è valido.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: il tipo di visualizzazione di testo per il quale questa area di controllo è valido. La classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> è il set di ruoli di visualizzazione testo predefinito. Ad esempio, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> viene utilizzato principalmente per le viste dei file di testo. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> viene utilizzato per le visualizzazioni di testo che un utente può modificare o passare tramite mouse e tastiera. Esempi di <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> le visualizzazioni sono la visualizzazione dell'editor di testo e **Output** finestra.  
  
 Nell'esempio seguente mostra gli attributi di esportazione per il provider dell'area di controllo.  
  
```  
[Export(typeof(IWpfTextViewCreationListener))]  
[ContentType("csharp")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener  
```  
  
 Un'area di controllo di negoziazione spazio è quello che occupa spazio allo stesso livello del testo. Per creare questo tipo di area di controllo, è necessario definire una classe di tag che eredita da <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, che definisce la quantità di spazio che occupa l'area di controllo.  
  
 Come con tutte le aree di controllo, è necessario esportare la definizione del livello dell'area di controllo.  
  
```  
[Export]  
[Name("TestAdornment")]  
[Order(After = DefaultAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testAdornmentLayer;  
```  
  
 Per creare un'istanza dell'area di controllo di negoziazione spazio, è necessario creare una classe che implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, oltre alla classe che implementa <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (come con altri tipi di aree di controllo).  
  
 Per registrare il provider di tagger, è necessario esportarlo insieme agli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: il tipo di contenuto (ad esempio, "text" o "code") per il quale l'area di controllo è valido.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: il tipo di visualizzazione di testo per la quale il tag o dell'area di controllo è valido. La classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> è il set di ruoli di visualizzazione testo predefinito. Ad esempio, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> viene utilizzato principalmente per le viste dei file di testo. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> viene utilizzato per le visualizzazioni di testo che un utente può modificare o passare tramite mouse e tastiera. Esempi di <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> le visualizzazioni sono la visualizzazione dell'editor di testo e **Output** finestra.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: il tipo di tag o dell'area di controllo che sono state definite. È necessario aggiungere un secondo <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> per <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>.  
  
 Nell'esempio seguente mostra gli attributi di esportazione nel provider di tagger per un tag dell'area di controllo di negoziazione spazio.  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
[TagType(typeof(SpaceNegotiatingAdornmentTag))]  
[TagType(typeof(TestSpaceNegotiatingTag))]  
internal sealed class TestTaggerProvider : ITaggerProvider  
```  
  
## <a name="extending-mouse-processors"></a>Estensione di processori del Mouse  
 È possibile aggiungere una gestione speciale per l'input del mouse. Creare una classe che eredita da <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> ed eseguire l'override di eventi del mouse per l'input che si desidera gestire. È inoltre necessario implementare <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> in una seconda classe ed esportarlo con la <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> che specifica il tipo di contenuto (ad esempio, "text" o "code") per il quale il gestore del mouse è valido.  
  
 Nell'esempio seguente mostra gli attributi di esportazione in un provider di processore del mouse.  
  
```  
[Export(typeof(IMouseProcessorProvider))]  
[Name("test mouse processor")]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Interactive)]   
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider  
```  
  
## <a name="extending-drop-handlers"></a>Estensione di gestori di rilascio  
 È possibile personalizzare il comportamento dei gestori di rilascio per tipi specifici di testo tramite la creazione di una classe che implementa <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> e la classe che implementa <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> per creare il gestore di trascinamento. È necessario esportare il gestore di rilascio insieme agli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: il formato di testo per il quale il gestore di trascinamento è valido. In ordine di priorità, dal più alto al più basso vengono gestiti i formati seguenti:  
  
    1.  Qualsiasi formato personalizzato  
  
    2.  FileDrop  
  
    3.  EnhancedMetafile  
  
    4.  WaveAudio  
  
    5.  RIFF  
  
    6.  Diff  
  
    7.  Impostazioni locali  
  
    8.  Tavolozza  
  
    9. PenData  
  
    10. Serializzabile  
  
    11. SymbolicLink  
  
    12. XAML  
  
    13. XamlPackage  
  
    14. TIFF  
  
    15. Bitmap  
  
    16. DIB  
  
    17. MetafilePicture  
  
    18. CSV  
  
    19. System.String  
  
    20. Formato HTML  
  
    21. UnicodeText  
  
    22. OEMText  
  
    23. Testo  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: il nome del gestore di trascinamento.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l'ordinamento del gestore di rilascio, prima o dopo il gestore di rilascio predefinito. Il gestore di rilascio predefinito per Visual Studio è denominato "DefaultFileDropHandler".  
  
 Nell'esempio seguente mostra gli attributi di esportazione in un provider del gestore di rilascio.  
  
```  
[Export(typeof(IDropHandlerProvider))]  
[DropFormat("Text")]   
[Name("TestDropHandler")]  
[Order(Before="DefaultFileDropHandler")]   
internal class TestDropHandlerProvider : IDropHandlerProvider  
```  
  
## <a name="extending-editor-options"></a>Estensione delle opzioni dell'Editor  
 È possibile definire le opzioni per essere valido solo in un determinato ambito, ad esempio, in una visualizzazione di testo. L'editor fornisce questo set di opzioni predefinite: opzioni dell'editor, le opzioni di visualizzazione e le opzioni di visualizzazione di Windows Presentation Foundation (WPF). Queste opzioni sono disponibili <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>, <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>, e <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>.  
  
 Per aggiungere una nuova opzione, derivare una classe da una di queste classi di definizione di opzione:  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>  
  
 Nell'esempio seguente viene illustrato come esportare una definizione di opzione con un valore booleano.  
  
```  
[Export(typeof(EditorOptionDefinition))]  
internal sealed class TestOption : EditorOptionDefinition<bool>  
```  
  
## <a name="extending-intellisense"></a>Estensione di IntelliSense  
 IntelliSense è un termine generale per un gruppo di funzionalità che forniscono informazioni sul testo strutturato e per il completamento delle istruzioni. Queste funzionalità includono il completamento delle istruzioni, supporto di firme, informazioni rapide e lampadine. Completamento delle istruzioni consente agli utenti di digitare un nome di lingua parola chiave o un membro in modo corretto. Supporto di firma consente di visualizzare la firma o le firme del metodo di solo testo digitato dall'utente. Informazioni rapide visualizza una firma completa per un nome di tipo o membro quando il puntatore del mouse si sofferma su di esso. Lampadina specificare azioni aggiuntive per determinate gli identificatori in determinati contesti, ad esempio, la ridenominazione di tutte le occorrenze di una variabile, dopo avere rinominata un'occorrenza.  
  
 La progettazione di una funzionalità IntelliSense è molto simile in tutti i casi:  
  
-   Un IntelliSense *broker* è responsabile per il processo generale.  
  
-   Un IntelliSense *sessione* rappresenta la sequenza di eventi tra l'attivazione del relatore e il commit o l'annullamento della selezione. La sessione viene in genere attivata da un movimento dell'utente.  
  
-   Un IntelliSense *controller* è responsabile per decidere quando la sessione deve iniziare e terminare. Decide anche quando le informazioni devono essere eseguito il commit e quando la sessione deve essere annullata.  
  
-   Un IntelliSense *origine* fornisce il contenuto e stabilisce la corrispondenza migliore.  
  
-   Un IntelliSense *relatore* è responsabile per la visualizzazione del contenuto.  
  
 Nella maggior parte dei casi, è consigliabile specificare almeno un'origine e un controller. È anche possibile fornire un relatore se si desidera personalizzare la visualizzazione.  
  
### <a name="implementing-an-intellisense-source"></a>Implementazione di un'origine di IntelliSense  
 Per personalizzare un'origine, è necessario implementare uno o più delle interfacce di origine seguenti:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> è stato deprecato in favore di <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
 Inoltre, è necessario implementare un provider dello stesso tipo:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> è stato deprecato in favore di <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>.  
  
 È necessario esportare il provider con gli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: il nome dell'origine.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: il tipo di contenuto (ad esempio, "text" o "code") a cui si applica l'origine.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l'ordine in cui l'origine deve essere visualizzato (in relazione ad altre origini).  
  
-   Nell'esempio seguente mostra gli attributi di esportazione in un provider di origine di completamento.  
  
```  
Export(typeof(ICompletionSourceProvider))]  
[Name(" Test Statement Completion Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestCompletionSourceProvider : ICompletionSourceProvider  
```  
  
 Per ulteriori informazioni sull'implementazione delle origini di IntelliSense, vedere le procedure dettagliate seguenti:  
  
 [Procedura dettagliata: Visualizzazione delle informazioni rapide](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Procedura dettagliata: Visualizzazione della funzionalità di supporto alla firma](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Procedura dettagliata: Visualizzazione del completamento istruzioni](../extensibility/walkthrough-displaying-statement-completion.md)  
  
### <a name="implementing-an-intellisense-controller"></a>Implementazione di un Controller di IntelliSense  
 Per personalizzare un controller, è necessario implementare la <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> interfaccia. Inoltre, è necessario implementare un provider di controller insieme agli attributi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: il nome del controller.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: il tipo di contenuto (ad esempio, "text" o "code") a cui si applica il controller.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: l'ordine in cui il controller deve essere visualizzato (rispetto a altro controller).  
  
 Nell'esempio seguente mostra gli attributi di esportazione in un provider di controller di completamento.  
  
```  
Export(typeof(IIntellisenseControllerProvider))]  
[Name(" Test Controller Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider  
```  
  
 Per ulteriori informazioni sull'utilizzo di controller IntelliSense, vedere le procedure dettagliate seguenti:  
  
 [Procedura dettagliata: Visualizzazione delle informazioni rapide](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)