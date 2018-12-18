---
title: Completamento di membro in un servizio di linguaggio Legacy | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0cc22190c9228d2e166be94ed0d5cc78105e2404
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="member-completion-in-a-legacy-language-service"></a>Completamento di membro in un servizio di linguaggio Legacy
Il completamento di membro IntelliSense è una descrizione comando che consente di visualizzare un elenco di possibili membri di un ambito specifico, ad esempio una classe, struttura, enumerazione o dello spazio dei nomi. Ad esempio, in c#, se l'utente digita "this" seguito da un punto, un elenco di tutti i membri della classe o struttura nell'ambito corrente viene visualizzato un elenco da cui l'utente può selezionare.  
  
 Il framework di pacchetto gestito (MPF) fornisce supporto per la descrizione comando e la gestione dell'elenco nella descrizione comando; tutto ciò che serve è cooperazione dal parser per fornire i dati visualizzati nell'elenco.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori dettagli, vedere [estensione dell'Editor e i servizi di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a usare il nuovo editor di API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## <a name="how-it-works"></a>Come funziona  
 Di seguito sono indicati i due modi in cui viene visualizzato un elenco di membri utilizzando le classi MPF:  
  
-   Posizionare il punto di inserimento in un identificatore o dopo un carattere di completamento del membro e selezionando **Elenca membri** dal **IntelliSense** menu.  
  
-   Il <xref:Microsoft.VisualStudio.Package.IScanner> scanner rileva un carattere di completamento del membro e imposta un trigger di token <xref:Microsoft.VisualStudio.Package.TokenTriggers> per tale carattere.  
  
 Un carattere di completamento membro indica che un membro di classe, struttura o enumerazione consiste nel seguire. In c# o Visual Basic, ad esempio, il carattere di completamento del membro è un `.`, mentre in C++ il carattere è un `.` o `->`. Il valore trigger è impostato per l'analisi di carattere selezionare il membro.  
  
### <a name="the-intellisense-member-list-command"></a>Il comando di elenco di membri in IntelliSense  
 Il <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando avvia una chiamata al <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodo il <xref:Microsoft.VisualStudio.Package.Source> classe e il <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodo, a sua volta chiama il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> parser di metodo con il motivo di analisi di <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
 Il parser determina il contesto della posizione corrente, nonché il token in o immediatamente prima della posizione corrente. In base a questo token, viene presentato un elenco di dichiarazioni. Ad esempio, in c#, se si posiziona il cursore su un membro di classe e selezionare **Elenca membri**, viene visualizzato un elenco di tutti i membri della classe. Se si posiziona il cursore dopo un periodo che segue una variabile oggetto, si ottiene un elenco di tutti i membri della classe di tale oggetto rappresenta. Si noti che se il punto di inserimento viene posizionato su un membro quando viene visualizzato l'elenco dei membri, selezionarlo nell'elenco di un membro sostituisce il membro che il punto di inserimento si trova in con uno nell'elenco.  
  
### <a name="the-token-trigger"></a>Il Token Trigger  
 Il <xref:Microsoft.VisualStudio.Package.TokenTriggers> trigger avvia una chiamata al <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodo il <xref:Microsoft.VisualStudio.Package.Source> classe e <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodo chiama a sua volta, il parser con il motivo di analisi di <xref:Microsoft.VisualStudio.Package.ParseReason> (se il trigger di token è inoltre incluso il <xref:Microsoft.VisualStudio.Package.TokenTriggers> flag, il motivo di analisi è <xref:Microsoft.VisualStudio.Package.ParseReason> che combina selezione membro e l'evidenziazione delle parentesi graffe).  
  
 Il parser determina il contesto dell'oggetto corrente della posizione nonché digitato prima che il membro selezionare carattere. Tali informazioni, il parser crea un elenco di tutti i membri dell'ambito richiesto. Questo elenco di dichiarazioni viene archiviato nel <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto restituito dal <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo. Se vengono restituite tutte le dichiarazioni, viene visualizzata la descrizione comando del completamento di membro. La descrizione comandi sono gestito da un'istanza di <xref:Microsoft.VisualStudio.Package.CompletionSet> classe.  
  
## <a name="enabling-support-for-member-completion"></a>Abilitazione del supporto per il completamento di membro  
 È necessario disporre di `CodeSense` voce del Registro di sistema è impostato su 1 per supportare qualsiasi operazione IntelliSense. Questa voce del Registro di sistema può essere impostata con un parametro denominato passato per il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attributo utente associato al pacchetto di linguaggio. Le classi del servizio di linguaggio leggere il valore di questa voce del Registro di sistema dal <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> proprietà la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.  
  
 Se lo scanner restituisce il token trigger di <xref:Microsoft.VisualStudio.Package.TokenTriggers>, il parser restituisce un elenco di dichiarazioni, quindi viene visualizzato l'elenco di completamento del membro.  
  
## <a name="supporting-member-completion-in-the-scanner"></a>Lo Scanner di supporto di completamento di membro  
 Lo scanner deve essere in grado di rilevare un carattere di completamento del membro e imposta il token trigger di <xref:Microsoft.VisualStudio.Package.TokenTriggers> quando tale carattere viene analizzato.  
  
### <a name="example"></a>Esempio  
 Ecco un esempio semplificato di rilevare il carattere di completamento del membro e l'impostazione appropriata <xref:Microsoft.VisualStudio.Package.TokenTriggers> flag. Questo esempio è solo a scopo illustrativo. Si presuppone che lo scanner contiene un metodo `GetNextToken` che identifica e restituisce un token da una riga di testo. Nell'esempio di codice imposta semplicemente il trigger quando viene rilevato il tipo di carattere corretto.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char memberSelectChar = '.';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (c == memberSelectChar)  
                {  
                        tokenInfo.Trigger |= TokenTriggers.MemberSelect;  
                }  
            }  
            return foundToken;  
        }  
    }  
}  
```  
  
## <a name="supporting-member-completion-in-the-parser"></a>Il Parser di supporto di completamento membro  
 Per il completamento di membro, il <xref:Microsoft.VisualStudio.Package.Source> classe chiama il <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> metodo. È necessario implementare l'elenco in una classe derivata dalla <xref:Microsoft.VisualStudio.Package.Declarations> classe. Vedere la <xref:Microsoft.VisualStudio.Package.Declarations> classe per informazioni dettagliate sui metodi di cui è necessario implementare.  
  
 Il parser viene chiamato con <xref:Microsoft.VisualStudio.Package.ParseReason> o <xref:Microsoft.VisualStudio.Package.ParseReason> quando viene digitato un carattere di selezione del membro. Il percorso specificato <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto viene immediatamente dopo che il membro selezionare carattere. Il parser deve raccogliere i nomi di tutti i membri che possono essere visualizzati in un elenco di membri in tale particolare punto nel codice sorgente. Quindi il parser deve analizzare la riga corrente per determinare l'ambito in cui che l'utente desidera associato con il carattere di selezione del membro.  
  
 Questo ambito è in base al tipo dell'identificatore prima che il membro selezionare carattere. Nel linguaggio c#, si consideri ad esempio la variabile membro `languageService` che è di tipo `LanguageService`, digitando **languageService.** produce un elenco di tutti i membri del `LanguageService` classe. Anche in c#, digitare **questo.** produce un elenco di tutti i membri della classe nell'ambito corrente.  
  
### <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come popolare un <xref:Microsoft.VisualStudio.Package.Declarations> elenco. Questo codice presuppone che il parser costruisce una dichiarazione e lo aggiunge all'elenco chiamando un `AddDeclaration` metodo la `TestAuthoringScope` classe.  
  
```csharp  
using System.Collections;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    internal class TestDeclaration  
    {  
        public string Name;            // Name of declaration  
        public int     TypeImageIndex; // Glyph index  
        public string Description;     // Description of declaration  
  
        public TestDeclaration(string name, int typeImageIndex, string description)  
        {  
            this.Name = name;  
            this.TypeImageIndex = typeImageIndex;  
            this.Description = description;  
        }  
    }  
  
    //===================================================  
    internal class TestDeclarations : Declarations  
    {  
        private ArrayList declarations;  
  
        public TestDeclarations()  
            : base()  
        {  
            declarations = new ArrayList();  
        }  
  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            declarations.Add(declaration);  
        }  
  
        //////////////////////////////////////////////////////////////////////  
        // Declarations of class methods that must be implemented.  
        public override int GetCount()  
        {  
            // Return the number of declarations to show.  
            return declarations.Count;  
        }  
  
        public override string GetDescription(int index)  
        {  
            // Return the description of the specified item.  
            string description = "";  
            if (index >= 0 && index < declarations.Count)  
            {  
                description = ((TestDeclaration)declarations[index]).Description;  
            }  
            return description;  
        }  
  
        public override string GetDisplayText(int index)  
        {  
            // Determine what is displayed in the tool tip list.  
            string text = null;  
            if (index >= 0 && index < declarations.Count)  
            {  
                text = ((TestDeclaration)declarations[index]).Name;  
            }  
            return text;  
        }  
  
        public override int GetGlyph(int index)  
        {  
            // Return index of image to display next to the display text.  
            int imageIndex = -1;  
            if (index >= 0 && index < declarations.Count)  
            {  
                imageIndex = ((TestDeclaration)declarations[index]).TypeImageIndex;  
            }  
            return imageIndex;  
        }  
  
        public override string GetName(int index)  
        {  
            string name = null;  
            if (index >= 0 && index < declarations.Count)  
            {  
                name = ((TestDeclaration)declarations[index]).Name;  
            }  
            return name;  
        }  
    }  
  
    //===================================================  
    public class TestAuthoringScope : AuthoringScope  
    {  
        private TestDeclarations declarationsList;  
  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            if (declaration != null)  
            {  
                if (declarationsList == null)  
                {  
                    declarationsList = new TestDeclarations();  
                }  
                declarationsList.AddDeclaration(declaration);  
            }  
        }  
  
        public override Declarations GetDeclarations(IVsTextView view,  
                                                     int line,  
                                                     int col,  
                                                     TokenInfo info,  
                                                     ParseReason reason)  
        {  
            return declarationsList;  
        }  
  
        /////////////////////////////////////////////////  
        // Remainder of AuthoringScope methods not shown.  
        /////////////////////////////////////////////////  
    }  
  
    //===================================================  
    class TestLanguageService : LanguageService  
    {  
        public override AuthoringScope ParseSource(ParseRequest req)  
        {  
            TestAuthoringScope scope = new TestAuthoringScope();  
            if (req.Reason == ParseReason.MemberSelect ||  
                req.Reason == ParseReason.MemberSelectAndHighlightBraces)  
            {  
                // Gather list of declarations based on what the user  
                // has typed so far. In this example, this list is an array of  
                // MemberDeclaration objects (a helper class you might implement  
                // to hold member declarations).  
                // How this list is gathered is dependent on the parser  
                // and is not shown here.  
                MemberDeclarations memberDeclarations;  
                memberDeclarations = GetDeclarationsForScope();  
  
                // Now populate the Declarations list in the authoring scope.  
                // GetImageIndexBasedOnType() is a helper method you  
                // might implement to convert a member type to an index into  
                // the image list returned from the language service.  
                foreach (MemberDeclaration dec in memberDeclarations)  
                {  
                    scope.AddDeclaration(new TestDeclaration(  
                                             dec.Name,  
                                             GetImageIndexBasedOnType(dec.Type),  
                                             dec.Description));  
                }  
            }  
            return scope;  
        }  
    }  
}  
```