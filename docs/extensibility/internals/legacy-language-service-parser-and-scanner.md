---
title: Parser servizio di linguaggio legacy e Scanner | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 755516fb9d341193005ad39e419e708b6d28867c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="legacy-language-service-parser-and-scanner"></a>Scanner e Parser servizio di linguaggio legacy
Il parser è il cuore del servizio di linguaggio. Le classi di lingua del file system distribuito (MPF, Managed Package Framework) richiedono un parser del linguaggio per selezionare le informazioni sul codice di visualizzazione. Un parser separa il testo in token lessicale e quindi identifica i token dal tipo e funzionalità.  
  
## <a name="discussion"></a>Discussione  
 Di seguito è un metodo c#.  
  
```csharp  
namespace MyNamespace  
{  
    class MyClass  
    {  
        public void MyFunction(int arg1)  
        {  
            int var1 = arg1;  
        }  
    }  
}  
```  
  
 In questo esempio, i token sono le parole e i segni di punteggiatura. Di seguito sono riportati i tipi di token.  
  
|Nome token|Tipo di token|  
|----------------|----------------|  
|spazio dei nomi, void pubblico, classe, int|keyword|  
|=|operator|  
|{ } ( ) ;|delimitatore|  
|MyNamespace, MyClass, MyFunction, arg1, var1|identifier|  
|MyNamespace|namespace|  
|MyClass|classe|  
|MyFunction|metodo|  
|arg1|parametro|  
|var1|variabile locale|  
  
 Il ruolo del parser consiste nell'identificare i token. Alcuni token può avere più di un tipo. Dopo che il parser ha identificato i token, è possibile utilizzare il servizio di linguaggio, le informazioni per fornire funzionalità utili, ad esempio l'evidenziazione della sintassi, delimitare tra parentesi graffe corrispondenti e le operazioni di IntelliSense.  
  
## <a name="types-of-parsers"></a>Tipi di parser  
 Il parser di un servizio di linguaggio non corrisponde un parser utilizzato come parte di un compilatore. Tuttavia, questo tipo di parser deve utilizzare uno scanner sia un parser, esattamente come un parser del compilatore.  
  
-   Uno scanner viene utilizzato per identificare i tipi di token. Queste informazioni vengono utilizzate per l'evidenziazione della sintassi e per l'identificazione rapida dei tipi di token che possono attivare altre operazioni, ad esempio, corrispondenza parentesi graffe. Questo programma è rappresentato dal <xref:Microsoft.VisualStudio.Package.IScanner> interfaccia.  
  
-   Un parser viene utilizzato per descrivere le funzioni e l'ambito dei token. Queste informazioni vengono utilizzate nelle operazioni di IntelliSense per identificare elementi del linguaggio, ad esempio metodi, variabili, parametri e le dichiarazioni e per fornire elenchi di membri e le firme del metodo in base al contesto. Il parser viene inoltre utilizzato per individuare coppie di elemento corrispondente di linguaggio, ad esempio le parentesi graffe e parentesi. Il parser si accede tramite il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo la <xref:Microsoft.VisualStudio.Package.LanguageService> classe.  
  
 Come implementare un scanner e parser per il servizio di linguaggio è responsabilità dell'utente. Sono disponibili varie risorse che descrivono il funzionamento di parser e come scrivere un parser personalizzato. Inoltre, sono disponibili i diversi prodotti gratuiti e a pagamento che facilitano la creazione di un parser.  
  
### <a name="the-parsesource-parser"></a>Il ParseSource Parser  
 A differenza di un parser che viene utilizzato come parte di un compilatore (in cui i token vengono convertiti in una forma di codice eseguibile), un parser del linguaggio del servizio può essere chiamato per motivi diversi e in molti contesti diversi. Modalità di implementazione di questo approccio nel <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo la <xref:Microsoft.VisualStudio.Package.LanguageService> classe è responsabilità dell'utente. È importante tenere presente che il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo può essere chiamato su un thread in background.  
  
> [!CAUTION]
>  Il <xref:Microsoft.VisualStudio.Package.ParseRequest> struttura contiene un riferimento al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> oggetto. Questo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> oggetto non può essere usato nel thread in background. In effetti, è Impossibile utilizzare molte delle classi base di MPF nel thread in background. Queste includono la <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> classi e qualsiasi altra classe che direttamente o indirettamente comunica con la visualizzazione.  
  
 Il parser è in genere analizza l'ora del file del primo intera origine viene chiamato o quando l'analisi motivo valore <xref:Microsoft.VisualStudio.Package.ParseReason> viene assegnato. Le chiamate successive al <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo gestire una piccola parte del codice analizzato e può essere eseguito più velocemente utilizzando i risultati dell'operazione di analisi completo precedente. Il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo comunica i risultati dell'operazione di analisi attraverso il <xref:Microsoft.VisualStudio.Package.AuthoringSink> e <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetti. Il <xref:Microsoft.VisualStudio.Package.AuthoringSink> oggetto viene utilizzato per raccogliere informazioni per un motivo specifico di analisi, ad esempio informazioni gli intervalli di firme dei metodi con elenchi di parametri o graffe. Il <xref:Microsoft.VisualStudio.Package.AuthoringScope> fornisce le raccolte delle dichiarazioni e le firme del metodo e il supporto per Vai a avanzati opzione Modifica (**Vai a definizione**, **Vai a dichiarazione**, **Vai a Fare riferimento a**).  
  
### <a name="the-iscanner-scanner"></a>Lo Scanner IScanner  
 È inoltre necessario implementare uno scanner che implementa <xref:Microsoft.VisualStudio.Package.IScanner>. Tuttavia, poiché questo scanner opera su una base di riga per riga tramite il <xref:Microsoft.VisualStudio.Package.Colorizer> (classe), è in genere più semplice da implementare. All'inizio di ogni riga, MPF consente la <xref:Microsoft.VisualStudio.Package.Colorizer> classe un valore da usare come una variabile di stato che viene passata allo scanner. Alla fine di ogni riga, lo scanner restituisce la variabile di stato aggiornato. Il Framework MPF memorizza nella cache di queste informazioni sullo stato per ogni riga in modo che lo scanner è possibile avviare l'analisi da tutte le righe senza dover dall'inizio del file di origine. Questa analisi veloce di una singola riga consente l'editor fornire commenti e suggerimenti rapidi all'utente.  
  
## <a name="parsing-for-matching-braces"></a>L'analisi per le parentesi graffe corrispondenti  
 Questo esempio viene illustrato il flusso di controllo per la corrispondenza di una parentesi graffa di chiusura specificato dall'utente. In questo processo, lo scanner utilizzato per la colorazione viene usato anche per determinare il tipo di token e se il token può attivare un'operazione di corrispondenza parentesi. Se il trigger viene trovato, il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo viene chiamato per trovare la parentesi graffa corrispondente. Infine, le due parentesi graffe vengono evidenziate.  
  
 Anche se le parentesi graffe vengono utilizzate nei nomi di trigger e analizzare i motivi, questo processo non è limitato a parentesi graffe effettive. Qualsiasi coppia di caratteri specificato da un corrispondente coppia è supportata. Esempi (e) \< e >, e [e].  
  
 Si supponga che il servizio di linguaggio supporta parentesi graffe corrispondenti.  
  
1.  L'utente digita una parentesi graffa di chiusura (}).  
  
2.  La parentesi graffa viene inserita in corrispondenza del cursore nel file di origine e il cursore viene spostato in uno.  
  
3.  Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> metodo la <xref:Microsoft.VisualStudio.Package.Source> classe viene chiamata con parentesi graffa di chiusura tipizzato.  
  
4.  Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> chiamate al metodo di <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> metodo la <xref:Microsoft.VisualStudio.Package.Source> classe per ottenere il token nella posizione della prima posizione corrente del cursore. Questo token corrisponde alla parentesi graffa di chiusura tipizzato).  
  
    1.  Il <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> chiamate al metodo di <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metodo il <xref:Microsoft.VisualStudio.Package.Colorizer> per ottenere tutti i token nella riga corrente.  
  
    2.  Il <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> chiamate al metodo di <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> metodo il <xref:Microsoft.VisualStudio.Package.IScanner> oggetto con il testo della riga corrente.  
  
    3.  Il <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metodo chiama ripetutamente il <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> metodo il <xref:Microsoft.VisualStudio.Package.IScanner> oggetto per raccogliere tutti i token dalla riga corrente.  
  
    4.  Il <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> chiama un metodo privato <xref:Microsoft.VisualStudio.Package.Source> classe per ottenere il token che contiene la posizione desiderata e passa l'elenco di token ottenuto dal <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metodo.  
  
5.  Di <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> metodo cerca un flag di trigger token del <xref:Microsoft.VisualStudio.Package.TokenTriggers> al token restituito dal <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> (metodo), vale a dire il token che rappresenta la parentesi graffa chiusa).  
  
6.  Se il trigger di flag di <xref:Microsoft.VisualStudio.Package.TokenTriggers> viene trovato, il <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> metodo la <xref:Microsoft.VisualStudio.Package.Source> classe viene chiamata.  
  
7.  Il <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> metodo avvia un'operazione di analisi con il valore di motivo di analisi di <xref:Microsoft.VisualStudio.Package.ParseReason>. Questa operazione chiama infine il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo la <xref:Microsoft.VisualStudio.Package.LanguageService> classe. Se l'analisi asincrono è abilitato, questa chiamata al <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo si verifica in un thread in background.  
  
8.  Quando l'operazione di analisi è terminata, un gestore di completamento interno (noto anche come un metodo di callback) denominato `HandleMatchBracesResponse` viene chiamato il <xref:Microsoft.VisualStudio.Package.Source> classe. Questa chiamata viene eseguita automaticamente dalla <xref:Microsoft.VisualStudio.Package.LanguageService> classe base, non dal parser.  
  
9. Il `HandleMatchBracesResponse` metodo consente di ottenere un elenco di intervalli dal <xref:Microsoft.VisualStudio.Package.AuthoringSink> oggetto archiviato nel <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto. (Un intervallo è un <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> struttura che specifica un intervallo di righe e di caratteri nel file di origine.) Questo elenco di intervalli contiene in genere due intervalli, uno per l'apertura e parentesi graffe di chiusura.  
  
10. Il `HandleBracesResponse` chiamate al metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> metodo il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> oggetto archiviato nel <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto. Consente di evidenziare gli intervalli specificati.  
  
11. Se il <xref:Microsoft.VisualStudio.Package.LanguagePreferences> proprietà <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> è abilitato, il `HandleBracesResponse` metodo ottiene il testo che è incluso in intervallo corrispondente e visualizza i primi 80 caratteri di tale intervallo nella barra di stato. Questa situazione è ideale se il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo include l'elemento di linguaggio che accompagna la coppia corrispondente. Per altre informazioni, vedere la proprietà <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.  
  
12. Operazione eseguita.  
  
### <a name="summary"></a>Riepilogo  
 L'operazione di corrispondenza parentesi graffe viene in genere limitata alle semplici coppie di elementi del linguaggio. Gli elementi più complessi, come la corrispondenza Triple ("`if(...)`","`{`"e"`}`", o "`else`","`{`"e"`}`"), può essere evidenziata come parte di un'operazione di completamento di parole. Ad esempio, quando la parola "else" è terminata, la corrispondenza "`if`" istruzione può essere evidenziata. Se fossero una serie di `if` / `else if` istruzioni, tutti gli elementi potrebbero essere evidenziate utilizzando lo stesso meccanismo come le parentesi graffe corrispondenti. Il <xref:Microsoft.VisualStudio.Package.Source> classe di base supporta già questa operazione, come indicato di seguito: lo scanner deve restituire il valore del token trigger <xref:Microsoft.VisualStudio.Package.TokenTriggers> combinato con il valore trigger <xref:Microsoft.VisualStudio.Package.TokenTriggers> per il token che precede la posizione del cursore.  
  
 Per ulteriori informazioni, vedere [corrispondenza delle parentesi graffe in un servizio di linguaggio Legacy](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-colorization"></a>L'analisi per colorazione  
 Colorare codice sorgente è semplice, identificare solo il tipo di informazioni di colore token e restituire informazioni sul tipo. La <xref:Microsoft.VisualStudio.Package.Colorizer> classe funge da intermediario tra l'editor e lo scanner per fornire informazioni di colore di ogni token. Il <xref:Microsoft.VisualStudio.Package.Colorizer> utilizzato dalla classe di <xref:Microsoft.VisualStudio.Package.IScanner> oggetto per colorare una riga e raccogliere informazioni sullo stato per tutte le righe nel file di origine. Nelle classi di servizio di linguaggio MPF, il <xref:Microsoft.VisualStudio.Package.Colorizer> classe non è necessario eseguire l'override perché comunica con lo scanner solo attraverso il <xref:Microsoft.VisualStudio.Package.IScanner> interfaccia. Si fornisce l'oggetto che implementa il <xref:Microsoft.VisualStudio.Package.IScanner> interfaccia eseguendo l'override di <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metodo il <xref:Microsoft.VisualStudio.Package.LanguageService> classe.  
  
 Il <xref:Microsoft.VisualStudio.Package.IScanner> scanner viene data una riga del codice sorgente tramite la <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> metodo. Le chiamate al <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> metodo vengono ripetuti per ottenere il token nella riga successivo fino all'esaurimento della riga di token. Per la colorazione, MPF gestisce tutto il codice sorgente come una sequenza di righe. Pertanto, lo scanner deve essere in grado di far fronte alle fuoriesca le righe di origine. Inoltre, qualsiasi riga può essere passata allo scanner in qualsiasi momento e l'unica garanzia è che lo scanner riceve la variabile di stato dalla riga di prima della riga per eseguire l'analisi.  
  
 La <xref:Microsoft.VisualStudio.Package.Colorizer> classe viene utilizzata anche per identificare i trigger di token. Questi trigger indicano MPF che il token può essere avviata un'operazione più complessa, ad esempio il completamento delle parole o le parentesi graffe corrispondenti. Poiché l'identificazione di tali trigger deve essere rapido e deve verificarsi in qualsiasi posizione, lo scanner è più adatto per questa attività.  
  
 Per ulteriori informazioni, vedere [colorazione della sintassi in un servizio di linguaggio Legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-functionality-and-scope"></a>L'analisi per la funzionalità e ambito  
 L'analisi per la funzionalità e ambito richiede uno sforzo maggiore solo l'identificazione dei tipi di token che vengono rilevati. Il parser deve identificare non solo il tipo di token, ma anche la funzionalità per il quale il token viene usato. Ad esempio, un identificatore è solo un nome, ma nella propria lingua, un identificatore potrebbe essere il nome di una classe, spazio dei nomi, metodo o variabile, a seconda del contesto. Il tipo generale del token potrebbe essere un identificatore, ma l'identificatore può contenere anche altri significati, a seconda che cos'è e in cui viene definito. Questa identificazione richiede il parser di conoscenza più approfondita sul linguaggio che viene eseguita l'analisi. Questa opzione è quando la <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe è disponibile in. Il <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe raccoglie informazioni su identificatori, metodi, coppie corrispondenti di lingua (ad esempio le parentesi graffe e parentesi) e linguaggio Triple (simile alle coppie di linguaggio, ad eccezione del fatto che non esistono tre parti, ad esempio, "`foreach()`" "`{`"e"`}`"). Inoltre, è possibile eseguire l'override di <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe per supportare l'identificazione di codice, che viene utilizzato in fase di convalida iniziali dei punti di interruzione in modo che il debugger non è necessario caricare, e **Auto** finestra di debug, che mostra locale variabili e parametri automaticamente quando un programma viene eseguito il debug e richiede il parser per identificare le variabili locali appropriate e i parametri oltre a quelli che presenta il debugger.  
  
 Il <xref:Microsoft.VisualStudio.Package.AuthoringSink> oggetto viene passato al parser come parte del <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto e un nuovo <xref:Microsoft.VisualStudio.Package.AuthoringSink> oggetto viene creato ogni volta che un nuovo <xref:Microsoft.VisualStudio.Package.ParseRequest> viene creato l'oggetto. Inoltre, il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo deve restituire un <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto, che viene utilizzata per gestire varie operazioni di IntelliSense. Il <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto mantiene un elenco per le dichiarazioni e l'elenco di metodi, ovvero di cui viene popolata, a seconda del motivo per l'analisi. La <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe deve essere implementata.  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un servizio di linguaggio Legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Cenni preliminari sul servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-overview.md)   
 [Colorazione della sintassi in un servizio di linguaggio Legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [Corrispondenza parentesi graffe in un servizio di linguaggio legacy](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)