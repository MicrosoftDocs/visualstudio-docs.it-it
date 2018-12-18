---
title: Colorazione della sintassi in un servizio di linguaggio Legacy | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1d82a85958fd979a3d9d44375656b08356ef09d9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Colorazione della sintassi in un servizio di linguaggio Legacy
La colorazione della sintassi è una funzionalità che determina i diversi elementi di un linguaggio di programmazione da visualizzare in un file di origine in diversi colori e stili. Per supportare questa funzionalità, è necessario fornire un parser o lo scanner in grado di identificare i tipi di elementi lessicali o token nel file. Molti linguaggi di distinguono le parole chiave, delimitatori (ad esempio le parentesi o parentesi graffe) e commenti per colorare li in modi diversi.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori dettagli, vedere [estensione dell'Editor e i servizi di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a usare il nuovo editor di API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## <a name="implementation"></a>Implementazione  
 Per supportare la colorazione, il framework di pacchetto gestito (MPF) include il <xref:Microsoft.VisualStudio.Package.Colorizer> classe che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaccia. Questa classe interagisce con un <xref:Microsoft.VisualStudio.Package.IScanner> per determinare il token e i colori. Per ulteriori informazioni su scanner, vedere [Parser servizio di linguaggio Legacy e Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). La <xref:Microsoft.VisualStudio.Package.Colorizer> classe quindi contrassegna ogni carattere del token con le informazioni di colore e lo restituisce le informazioni all'editor la visualizzazione del file di origine.  
  
 Le informazioni di colore restituite nell'editor sono un indice in un elenco di colori. Ogni elemento colorabile specifica un valore di colore e un set di attributi di tipo di carattere, ad esempio grassetto o barrato. L'editor fornisce un set di elementi di colore predefiniti che è possibile utilizzare il servizio di linguaggio. È necessario eseguire è specificare l'indice di colore appropriato per ogni tipo di token. Tuttavia, è possibile fornire un set di elementi di colori personalizzati e gli indici che è fornire per i token e fare riferimento a un elenco personalizzato di elementi colorabili anziché l'elenco predefinito. È necessario impostare anche la `RequestStockColors` voce del Registro di sistema su 0 (o non si specifica il `RequestStockColors` voce in tutti) per supportare i colori personalizzati. È possibile impostare questa voce del Registro di sistema con un parametro denominato per il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> degli attributi definiti dall'utente. Per ulteriori informazioni sulla registrazione di un servizio di linguaggio e impostando le relative opzioni, vedere [la registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
## <a name="custom-colorable-items"></a>Elementi di colori personalizzati  
 Per fornire i propri elementi di colori personalizzati, è necessario eseguire l'override di <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> e <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> metodo la <xref:Microsoft.VisualStudio.Package.LanguageService> classe. Il primo metodo restituisce il numero di elementi di colori personalizzati che supporta il servizio di linguaggio e il secondo Ottiene l'elemento colorabile predefinito in base all'indice. Creare l'elenco predefinito di elementi di colori personalizzati. Nel costruttore del servizio di linguaggio, è sufficiente eseguire è specificare ogni elemento colorabile predefinito con un nome. Visual Studio gestisce automaticamente il caso in cui l'utente seleziona un diverso set di colori. Questo nome è quello visualizzato nel **tipi di carattere e colori** nella pagina delle proprietà di **opzioni** la finestra di dialogo (disponibile da Visual Studio **strumenti** menu) e questo nome determina quale colore di che un utente ha eseguito l'override. Le scelte dell'utente sono archiviate in una cache nel Registro di sistema e a cui accede il nome del colore. Il **tipi di carattere e colori** pagina delle proprietà sono elencati tutti i nomi di colore in ordine alfabetico, pertanto è possibile raggruppare i colori personalizzati facendo precedere il nome di ogni colore con il nome del linguaggio; ad esempio, "**TestLanguage commento**"e"**TestLanguage - parola chiave**". Oppure è possibile raggruppare gli elementi colorabile predefiniti dal tipo, "**commento (TestLanguage)**"e"**(parola chiave) (TestLanguage)**". Il raggruppamento in base al nome di lingua è preferito.  
  
> [!CAUTION]
>  Si consiglia di includere il nome della lingua nel nome dell'elemento colorabile predefinito per evitare conflitti con i nomi di elemento colorabile esistenti.  
  
> [!NOTE]
>  Se si modifica il nome di uno dei colori durante lo sviluppo, è necessario reimpostare la cache che Visual Studio ha creato la prima volta che erano accessibili i colori. È possibile farlo eseguendo il **ripristinare l'Hive sperimentale** dal menu di programma Visual Studio SDK.  
  
 Si noti che il primo elemento nell'elenco di colori non viene mai fatto riferimento. Visual Studio fornisce sempre gli attributi per l'elemento e i colori predefiniti del testo. Il modo più semplice di gestire questa consiste nel fornire un elemento colorabile segnaposto come primo elemento.  
  
### <a name="high-color-colorable-items"></a>Elementi colorabile High Color  
 Colori supporta anche i valori di colore a 24 bit o ad alta tramite il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaccia. Il Framework MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> classe supporta il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaccia e i colori a 24 bit vengono specificati nel costruttore con i colori normali. Per ulteriori dettagli, vedere la classe <xref:Microsoft.VisualStudio.Package.ColorableItem>. Nell'esempio seguente viene illustrato come impostare i colori a 24 bit per parole chiave e i commenti. Vengono utilizzati i colori a 24 bit quando colore a 24 bit è supportato sul desktop dell'utente. in caso contrario, vengono utilizzati i colori di testo normale.  
  
 Tenere presente che questi sono i colori predefiniti per il linguaggio. l'utente può modificare i colori come desiderano.  
  
### <a name="example"></a>Esempio  
 In questo esempio viene illustrato come dichiarare e popola una matrice di elementi di colori personalizzati utilizzando la <xref:Microsoft.VisualStudio.Package.ColorableItem> classe. In questo esempio i colori della parola chiave e il commento utilizzando colori a 24 bit.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private ColorableItem[] m_colorableItems;  
  
        TestLanguageService() : base()  
        {  
            m_colorableItems = new ColorableItem[] {  
                new ColorableItem("TestLanguage - Text",  
                                  "Text",  
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.Empty,  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT),  
                new ColorableItem("TestLanguage - Keyword",  
                                  "Keyword",  
                                  COLORINDEX.CI_MAROON,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.FromArgb(192,32,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_BOLD),  
                new ColorableItem("TestLanguage - Comment",  
                                  "Comment",  
                                  COLORINDEX.CI_DARKGREEN,  
                                  COLORINDEX.CI_LIGHTGRAY,  
                                  System.Drawing.Color.FromArgb(32,128,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT)  
                // ...  
                // Add as many colorable items as you want to support.  
            };  
        }  
    }  
}  
```  
  
## <a name="the-colorizer-class-and-the-scanner"></a>La classe di rappresentazione e lo Scanner  
 La base <xref:Microsoft.VisualStudio.Package.LanguageService> classe dispone di un <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> metodo tale instantiantes la <xref:Microsoft.VisualStudio.Package.Colorizer> classe. Lo scanner restituito dal <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> viene passato per il <xref:Microsoft.VisualStudio.Package.Colorizer> costruttore della classe.  
  
 È necessario implementare la <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> nella versione del metodo di <xref:Microsoft.VisualStudio.Package.LanguageService> classe. La <xref:Microsoft.VisualStudio.Package.Colorizer> classe utilizza lo scanner per ottenere tutte le informazioni di token di colore.  
  
 Lo scanner è necessario popolare un <xref:Microsoft.VisualStudio.Package.TokenInfo> struttura per ogni token si trova. Questa struttura contiene informazioni quali occupa l'intervallo, il token, l'indice di colore da utilizzare, il tipo è il token e token di trigger (vedere <xref:Microsoft.VisualStudio.Package.TokenTriggers>). Solo l'indice dell'intervallo e colore sono necessari per la colorazione dalla <xref:Microsoft.VisualStudio.Package.Colorizer> classe.  
  
 L'indice di colore archiviato nel <xref:Microsoft.VisualStudio.Package.TokenInfo> struttura in genere è un valore compreso il <xref:Microsoft.VisualStudio.Package.TokenColor> enumerazione, che fornisce un numero di indici denominati corrispondente a vari elementi del linguaggio, ad esempio parole chiave e operatori. Se l'elenco di elementi di colori personalizzati corrispondenze gli elementi presentati nel <xref:Microsoft.VisualStudio.Package.TokenColor> enumerazione, è possibile semplicemente utilizzare l'enumerazione come colore per ogni token. Tuttavia, se si dispone di ulteriori elementi colorabili o non si desidera utilizzare i valori esistenti in tale ordine, è possibile ordinare l'elenco di elementi di colori personalizzati per soddisfare le esigenze e restituire l'indice appropriato nell'elenco. Assicurarsi di eseguire il cast dell'indice per un <xref:Microsoft.VisualStudio.Package.TokenColor> quando si archiviano nel <xref:Microsoft.VisualStudio.Package.TokenInfo> struttura; [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] vede solo sull'indice.  
  
### <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come lo scanner potrebbe identificare tre tipi di token: identificatori (tutto ciò che non è un numero o la punteggiatura), segni di punteggiatura e numeri. Questo esempio è solo a scopo illustrativo e non rappresenta un'implementazione completa di parser e scanner. Si presuppone che esista un `Lexer` classe con un `GetNextToken()` metodo che restituisce una stringa.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    private Lexer lex;  
  
    public class TestScanner : IScanner  
    {  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false;  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                char firstChar = token[0];  
                if (Char.IsPunctuation(firstChar))  
                {  
                    tokenInfo.Type = TokenType.Operator;  
                    tokenInfo.Color = TokenColor.Keyword;  
                }  
                else if (Char.IsNumber(firstChar))  
                {  
                    tokenInfo.Type = TokenType.Literal;  
                    tokenInfo.Color = TokenColor.Number;  
                }  
                else  
                {  
                    tokenInfo.Type = TokenType.Identifier;  
                    tokenInfo.Color = TokenColor.Identifier;  
                }  
            }  
            return foundToken;  
        }  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità del linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)   
 [Scanner e Parser servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [Registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)