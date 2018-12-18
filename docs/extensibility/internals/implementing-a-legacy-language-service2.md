---
title: Implementazione di un Service2 Language Legacy | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d54572bc3b105af01ed42b01a27f363da80d58de
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-a-legacy-language-service"></a>Implementazione di un servizio di linguaggio Legacy
Per implementare un servizio di linguaggio mediante il framework di pacchetto gestito (MPF), è necessario derivare una classe dalla classe di <xref:Microsoft.VisualStudio.Package.LanguageService> classe e implementare i seguenti metodi astratti e le proprietà:  
  
-   Metodo <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>  
  
-   Metodo <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>  
  
-   Metodo <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>  
  
-   Proprietà <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>  
  
 Vedere le sezioni appropriate per i dettagli sull'implementazione di questi metodi e proprietà.  
  
 Per supportare funzionalità aggiuntive, il servizio di linguaggio potrebbe essere necessario derivare una classe da una delle classi del servizio di linguaggio MPF; per supportare i comandi di menu aggiuntive, ad esempio, è necessario derivare una classe dalla classe di <xref:Microsoft.VisualStudio.Package.ViewFilter> classe ed eseguire l'override di molti dei metodi di gestione del comando (vedere <xref:Microsoft.VisualStudio.Package.ViewFilter> per informazioni dettagliate). La <xref:Microsoft.VisualStudio.Package.LanguageService> classe fornisce numerosi metodi che vengono chiamati per creare nuove istanze di classi diverse e si esegue l'override del metodo di creazione appropriato per fornire un'istanza della classe. Ad esempio, è necessario eseguire l'override di <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> metodo nel <xref:Microsoft.VisualStudio.Package.LanguageService> classe per restituire un'istanza personalizzata <xref:Microsoft.VisualStudio.Package.ViewFilter> classe. Per ulteriori dettagli, vedere "Creazione di istanze di classi personalizzate".  
  
 Il servizio di linguaggio è inoltre possibile fornire i proprio icone, che vengono utilizzati in più posizioni. Ad esempio, quando viene visualizzato un elenco di completamento IntelliSense, ogni elemento nell'elenco può avere un'icona a esso associata, contrassegnare l'elemento di un metodo, classe, spazio dei nomi, proprietà o qualunque sia necessario per la lingua. Queste icone vengono utilizzate in tutti gli elenchi di IntelliSense, il **barra di spostamento**e il **elenco errori** finestra delle attività. Vedere la sezione "Servizio di linguaggio immagini" di seguito per informazioni dettagliate.  
  
## <a name="getlanguagepreferences-method"></a>Metodo GetLanguagePreferences  
 Il <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> metodo restituisce sempre la stessa istanza di un <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. È possibile utilizzare la base <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe se non è necessaria alcuna preferenza aggiuntive per il servizio di linguaggio. Le classi del servizio di linguaggio MPF presuppongono la presenza di almeno il base <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.  
  
### <a name="example"></a>Esempio  
 In questo esempio viene illustrata un'implementazione tipica del <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> metodo. In questo esempio viene utilizzata la base <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private LanguagePreferences m_preferences;  
  
        public override LanguagePreferences GetLanguagePreferences()  
        {  
            if (m_preferences == null)  
            {  
                m_preferences = new LanguagePreferences(this.Site,  
                                                        typeof(TestLanguageService).GUID,  
                                                        this.Name );  
                m_preferences.Init();  
            }  
            return m_preferences;  
        }  
    }  
}  
```  
  
## <a name="getscanner-method"></a>Metodo GetScanner  
 Questo metodo restituisce un'istanza di un <xref:Microsoft.VisualStudio.Package.IScanner> oggetto che implementa un parser di riga o scanner utilizzato per ottenere i token e i relativi tipi e trigger. Viene utilizzato questo scanner di <xref:Microsoft.VisualStudio.Package.Colorizer> classe per la colorazione, ma lo scanner può essere usato per ottenere i tipi di token e i trigger come preludio di un'operazione di analisi più complessa. È necessario specificare la classe che implementa il <xref:Microsoft.VisualStudio.Package.IScanner> interfaccia e si devono implementare tutti i metodi sul <xref:Microsoft.VisualStudio.Package.IScanner> interfaccia.  
  
### <a name="example"></a>Esempio  
 In questo esempio viene illustrata un'implementazione tipica del <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metodo. Il `TestScanner` classe implementa il <xref:Microsoft.VisualStudio.Package.IScanner> interfaccia (non illustrato).  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private TestScanner m_scanner;  
  
        public override IScanner GetScanner(IVsTextLines buffer)  
        {  
            if (m_scanner == null)  
            {  
                m_scanner = new TestScanner(buffer);  
            }  
            return m_scanner;  
        }  
    }  
}  
    internal class TestScanner : IScanner  
    {  
        private IVsTextBuffer m_buffer;  
        string m_source;  
  
        public TestScanner(IVsTextBuffer buffer)  
        {  
            m_buffer = buffer;  
        }  
  
        bool IScanner.ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo, ref int state)  
        {  
            tokenInfo.Type = TokenType.Unknown;  
            tokenInfo.Color = TokenColor.Text;  
            return true;  
        }  
  
        void IScanner.SetSource(string source, int offset)  
        {  
            m_source = source.Substring(offset);  
        }  
    }  
  
```  
  
## <a name="parsesource-method"></a>Metodo ParseSource  
 Analizza il file di origine in base a una serie di motivi diversi. Questo metodo riceve un <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto che descrive quello previsto per una particolare operazione di analisi. Il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo richiama un parser più complesso che determina le funzionalità di token e di ambito. Il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo utilizzato nel supporto per le operazioni di IntelliSense, nonché a corrispondenza delle parentesi graffe. Anche se non si supportano tali operazioni avanzate, è comunque necessario restituire un valore valido <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto e che richiede di creare una classe che implementa il <xref:Microsoft.VisualStudio.Package.AuthoringScope> l'interfaccia e implementare tutti i metodi di tale interfaccia. È possibile restituire i valori null da tutti i metodi, ma il <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto stesso non deve essere un valore null.  
  
### <a name="example"></a>Esempio  
 In questo esempio viene illustrata un'implementazione minima del <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> (metodo) e <xref:Microsoft.VisualStudio.Package.AuthoringScope> (classe), sufficiente per consentire al servizio di linguaggio per la compilazione e funzionare senza effettivamente supportano le funzionalità più avanzate.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override AuthoringScope ParseSource(ParseRequest req)  
        {  
            return new TestAuthoringScope();  
        }  
    }  
  
    internal class TestAuthoringScope : AuthoringScope  
    {  
        public override string GetDataTipText(int line, int col, out TextSpan span)  
        {  
            span = new TextSpan();  
            return null;  
        }  
  
        public override Declarations GetDeclarations(IVsTextView view,  
                                                     int line,  
                                                     int col,  
                                                     TokenInfo info,  
                                                     ParseReason reason)  
        {  
            return null;  
        }  
  
        public override string Goto(VSConstants.VSStd97CmdID cmd, IVsTextView textView, int line, int col, out TextSpan span)  
        {  
            span = new TextSpan();  
            return null;  
        }  
  
        public override Methods GetMethods(int line, int col, string name)  
        {  
            return null;  
        }  
}  
```  
  
## <a name="name-property"></a>Nome proprietà  
 Questa proprietà restituisce il nome del servizio di linguaggio. Deve essere lo stesso nome specificato quando è stato registrato il servizio di linguaggio. Questo nome viene utilizzato in un numero di posizioni e più importante dei quali è la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe in cui il nome viene utilizzato per accedere al registro. Il nome restituito da questa proprietà non deve essere localizzato perché è usato per la voce del Registro di sistema e i nomi delle chiavi del Registro di sistema.  
  
### <a name="example"></a>Esempio  
 In questo esempio viene illustrata una possibile implementazione del <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> proprietà. Si noti che il nome è hardcoded: il nome effettivo deve essere ottenuto da un file di risorse e può essere utilizzato durante la registrazione di un servizio di linguaggio (vedere [la registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override string Name  
        {  
            get { return "Test Language"; }  
        }  
    }  
}  
```  
  
## <a name="instantiating-custom-classes"></a>Creazione di istanze di classi personalizzate  
 I metodi seguenti nelle classi specificate possono essere sostituiti per fornire alle istanze del propria versioni di ogni classe.  
  
### <a name="in-the-languageservice-class"></a>Nella classe LanguageService  
  
|Metodo|Classe restituite|Descrizione|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Per supportare le aggiunte personalizzate per la visualizzazione del testo.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Per supportare le proprietà personalizzate dei documenti.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Per supportare il **barra di spostamento**.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Per supportare le funzioni nel modello di frammento di codice.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Per supportare i frammenti di codice (questo metodo viene in genere non sottoposto a override).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Per supportare la personalizzazione del <xref:Microsoft.VisualStudio.Package.ParseRequest> struttura (questo metodo viene in genere non sottoposto a override).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Per supportare formattazione codice sorgente, specificando i caratteri di commento e firme dei metodi di personalizzazione.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Per supportare ulteriori comandi di menu.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Per supportare l'evidenziazione della sintassi (questo metodo viene in genere non sottoposto a override).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Per supportare l'accesso alle preferenze di lingua. Questo metodo deve essere implementato, ma può restituire un'istanza della classe di base.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Per fornire un parser utilizzato per identificare i tipi di token in una riga. Questo metodo deve essere implementato e <xref:Microsoft.VisualStudio.Package.IScanner> deve essere derivato da.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Per fornire un parser utilizzato per identificare la funzionalità e ambito di un intero file di origine. Questo metodo deve essere implementato e deve restituire un'istanza della versione del <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe. Se si desidera supportare è evidenziazione della sintassi (che richiede il <xref:Microsoft.VisualStudio.Package.IScanner> restituito dal parser di <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metodo), è possibile eseguire alcuna operazione in questo metodo diverso da restituire una versione del <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe i cui metodi tutti restituiranno valori null.|  
  
### <a name="in-the-source-class"></a>La classe di origine  
  
|Metodo|Classe restituite|Descrizione|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Per personalizzare la visualizzazione di elenchi di completamento IntelliSense (questo metodo viene in genere non sottoposto a override).|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Per il supporto di marcatori nell'elenco attività elenco errori. in particolare, supporto per funzionalità oltre l'apertura del file e passare alla riga che ha causato l'errore.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Per personalizzare la visualizzazione della descrizione comandi per informazioni di parametro di IntelliSense.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Per supportare l'aggiunta di commenti di codice.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Per raccogliere le informazioni durante l'operazione di analisi.|  
  
### <a name="in-the-authoringscope-class"></a>Nella classe AuthoringScope  
  
|Metodo|Classe restituite|Descrizione|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Fornisce un elenco di dichiarazioni di membri o tipi. Questo metodo deve essere implementato, ma può restituire un valore null. Se questo metodo restituisce un oggetto valido, l'oggetto deve essere un'istanza della versione del <xref:Microsoft.VisualStudio.Package.Declarations> classe.|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Fornisce un elenco di firme del metodo per un determinato contesto. Questo metodo deve essere implementato, ma può restituire un valore null. Se questo metodo restituisce un oggetto valido, l'oggetto deve essere un'istanza della versione del <xref:Microsoft.VisualStudio.Package.Methods> classe.|  
  
## <a name="language-service-images"></a>Immagini di servizio di linguaggio  
 Per fornire un elenco di icone da utilizzare in tutto il servizio di linguaggio, eseguire l'override di <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> metodo il <xref:Microsoft.VisualStudio.Package.LanguageService> classe e restituire un <xref:System.Windows.Forms.ImageList> contenente le icone. La base <xref:Microsoft.VisualStudio.Package.LanguageService> classe carica un set predefinito di icone. Poiché si specifica l'indice dell'immagine esatta in tali posizioni che devono icone, la disposizione proprio elenco di immagini è interamente dall'utente.  
  
### <a name="images-used-in-intellisense-completion-lists"></a>Immagini utilizzate negli elenchi di completamento IntelliSense  
 Per elenchi di completamento IntelliSense, l'indice dell'immagine è specificato per ogni elemento nella <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> metodo la <xref:Microsoft.VisualStudio.Package.Declarations> classe, è necessario eseguire l'override se si desidera specificare un indice delle immagini. Il valore restituito dal <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> metodo è un indice nell'elenco di immagine fornito per il <xref:Microsoft.VisualStudio.Package.CompletionSet> costruttore di classe e che è lo stesso elenco immagini restituiti dal <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> metodo nel <xref:Microsoft.VisualStudio.Package.LanguageService> classe (è possibile modificare l'elenco di immagini per utilizzare per il <xref:Microsoft.VisualStudio.Package.CompletionSet> se esegue l'override di <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> metodo nel <xref:Microsoft.VisualStudio.Package.Source> classe per fornire un elenco di immagini diverso).  
  
### <a name="images-used-in-the-navigation-bar"></a>Immagini utilizzate nella barra di spostamento  
 Il **barra di spostamento** Visualizza gli elenchi di tipi e membri e viene utilizzata per la navigazione rapida consente di visualizzare le icone. Queste icone vengono ottenute dal <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> metodo il <xref:Microsoft.VisualStudio.Package.LanguageService> classe e non può essere sottoposto a override in modo specifico per il **barra di spostamento**. Gli indici utilizzati per ogni elemento nelle caselle combinate vengono specificati quando vengono compilati gli elenchi che rappresentano le caselle combinate di <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodo il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> classe (vedere [il supporto per la barra di spostamento in un servizio di linguaggio Legacy](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Questi indici immagine vengono ottenuti in qualche modo dal parser, in genere tramite la versione del <xref:Microsoft.VisualStudio.Package.Declarations> classe. La modalità in cui vengono ottenuti gli indici è interamente responsabilità dell'utente.  
  
### <a name="images-used-in-the-error-list-task-window"></a>Immagini utilizzate nella finestra attività di elenco degli errori  
 Ogni volta che il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> parser (metodo) (vedere [Parser servizio di linguaggio Legacy e Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) rileva un errore e la passa tale errore per il <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> metodo il <xref:Microsoft.VisualStudio.Package.AuthoringSink> (classe), l'errore viene segnalato nel  **Elenco errori** finestra delle attività. Un'icona può essere associata a ogni elemento visualizzato nella finestra attività e tale icona proviene dallo stesso elenco di immagini restituito dal <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> metodo la <xref:Microsoft.VisualStudio.Package.LanguageService> classe. Il comportamento predefinito delle classi di MPF è non mostrare un'immagine con il messaggio di errore. Tuttavia, è possibile eseguire l'override di questo comportamento derivando una classe dal <xref:Microsoft.VisualStudio.Package.Source> classe e si esegue l'override di <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> metodo. In quel metodo, si crea un nuovo <xref:Microsoft.VisualStudio.Package.DocumentTask> oggetto. Prima di restituire tale oggetto, è possibile utilizzare il <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> proprietà il <xref:Microsoft.VisualStudio.Package.DocumentTask> per impostare l'indice dell'immagine. Questo aspetto è simile a quello nell'esempio seguente. Si noti che `TestIconImageIndex` è un'enumerazione che elenca tutte le icone ed è specifico per questo esempio. Potrebbe essere un modo diverso per identificare le icone nel servizio di linguaggio.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    class TestSource : Source  
    {  
        public override DocumentTask CreateErrorTaskItem(  
            TextSpan          span,  
            string            filename,  
            string            message,  
            TastPriority      priority,  
            TaskCategory      category,  
            MARKERTYPE        markerType,  
            TaskErrorCategory errorCategory)  
        {  
            DocumentTask taskItem = base.CreateErrorTaskItem(  
                                           span,  
                                           filename,  
                                           message,  
                                           priority,  
                                           category,  
                                           markerType,  
                                           errorCategory);  
            if (errorCategory == TaskErrorCategory.Error)  
            {  
                taskItem.ImageIndex = TestIconImageIndex.Error;  
            }  
            return taskItem;  
        }  
    }  
}  
```  
  
## <a name="the-default-image-list-for-a-language-service"></a>Elenco di immagini predefinito per un servizio di linguaggio  
 L'elenco di immagini predefiniti fornito con le classi del servizio di linguaggio MPF base contiene un numero di icone associate a elementi del linguaggio più comuni. La maggior parte di queste icone vengono disposte in gruppi di sei variazioni, corrispondenti ai concetti accesso pubblica, interna, friend, protected, private e menu di scelta. Ad esempio, è possibile disporre le icone diverse per un metodo se è pubblico, protetto o privato.  
  
 L'enumerazione seguente specifica i nomi standard per ogni set di icone e specifica l'indice associato. Ad esempio, in base all'enumerazione, è possibile specificare l'indice dell'immagine per un metodo protetto come `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`. È possibile modificare i nomi di questa enumerazione in base alle esigenze.  
  
```csharp  
public enum IconImageIndex  
        {  
            // access types  
            AccessPublic = 0,  
            AccessInternal = 1,  
            AccessFriend = 2,  
            AccessProtected = 3,  
            AccessPrivate = 4,  
            AccessShortcut = 5,  
  
            Base = 6,  
            // Each of the following icon type has 6 versions,  
            //corresponding to the access types  
            Class = Base + 0,  
            Constant = Base + 1,  
            Delegate = Base + 2,  
            Enumeration = Base + 3,  
            EnumMember = Base + 4,  
            Event = Base + 5,  
            Exception = Base + 6,  
            Field = Base + 7,  
            Interface = Base + 8,  
            Macro = Base + 9,  
            Map = Base + 10,  
            MapItem = Base + 11,  
            Method = Base + 12,  
            OverloadedMethod = Base + 13,  
            Module = Base + 14,  
            Namespace = Base + 15,  
            Operator = Base + 16,  
            Property = Base + 17,  
            Struct = Base + 18,  
            Template = Base + 19,  
            Typedef = Base + 20,  
            Type = Base + 21,  
            Union = Base + 22,  
            Variable = Base + 23,  
            ValueType = Base + 24,  
            Intrinsic = Base + 25,  
            JavaMethod = Base + 26,  
            JavaField = Base + 27,  
            JavaClass = Base + 28,  
            JavaNamespace = Base + 29,  
            JavaInterface = Base + 30,  
            // Miscellaneous icons with one icon for each type.  
            Error = 187,  
            GreyedClass = 188,  
            GreyedPrivateMethod = 189,  
            GreyedProtectedMethod = 190,  
            GreyedPublicMethod = 191,  
            BrowseResourceFile = 192,  
            Reference = 193,  
            Library = 194,  
            VBProject = 195,  
            VBWebProject = 196,  
            CSProject = 197,  
            CSWebProject = 198,  
            VB6Project = 199,  
            CPlusProject = 200,  
            Form = 201,  
            OpenFolder = 202,  
            ClosedFolder = 203,  
            Arrow = 204,  
            CSClass = 205,  
            Snippet = 206,  
            Keyword = 207,  
            Info = 208,  
            CallBrowserCall = 209,  
            CallBrowserCallRecursive = 210,  
            XMLEditor = 211,  
            VJProject = 212,  
            VJClass = 213,  
            ForwardedType = 214,  
            CallsTo = 215,  
            CallsFrom = 216,  
            Warning = 217,  
        }  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un servizio di linguaggio Legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Cenni preliminari sul servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-overview.md)   
 [Registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Scanner e parser dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)