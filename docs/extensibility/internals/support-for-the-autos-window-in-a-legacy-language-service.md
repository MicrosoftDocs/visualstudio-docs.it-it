---
title: Supporto per la finestra Auto in un servizio di linguaggio Legacy | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: db6be625c671a508be3c2fd2f1697282af282bdd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Supporto per la finestra Auto in un servizio di linguaggio Legacy
Il **Auto** finestra vengono visualizzate le espressioni, ad esempio variabili e parametri che sono nell'ambito quando il programma in fase di debug è stato sospeso (a causa di un punto di interruzione o un'eccezione). Le espressioni possono includere variabili, locale o globale e i parametri che sono stati modificati nell'ambito locale. Il **Auto** finestra può includere anche creazioni di istanza di una classe, struttura o un altro tipo. Tutto ciò che un analizzatore di espressioni può valutare potenzialmente possono essere visualizzati nel **Auto** finestra.  
  
 Il framework di pacchetto gestito (MPF) fornisce un supporto diretto per il **Auto** finestra. Tuttavia, se esegue l'override di <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> (metodo), è possibile restituire un elenco di espressioni devono essere presentati nel **Auto** finestra.  
  
## <a name="implementing-support-for-the-autos-window"></a>Implementazione del supporto per la finestra Auto  
 È sufficiente per supportare il **Auto** finestra consiste nell'implementare il <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metodo la <xref:Microsoft.VisualStudio.Package.LanguageService> classe. L'implementazione deve decidere, specificando un percorso nel file di origine, le espressioni devono visualizzare nel **Auto** finestra. Il metodo restituisce un elenco di stringhe in cui ogni stringa rappresenta una singola espressione. Valore restituito di <xref:Microsoft.VisualStudio.VSConstants.S_OK> indica che l'elenco contiene espressioni, mentre <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> indica che non sono presenti espressioni da visualizzare.  
  
 Le espressioni effettive restituite sono i nomi dei variabili o dei parametri che vengono visualizzati in tale posizione nel codice. Questi nomi vengono passati per l'analizzatore di espressioni per ottenere i valori e tipi che vengono quindi visualizzati nel **Auto** finestra.  
  
### <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrata un'implementazione del <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metodo che ottiene un elenco di espressioni dal <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo utilizzando il motivo di analisi <xref:Microsoft.VisualStudio.Package.ParseReason>. Ogni espressione viene incluso come un `TestVsEnumBSTR` che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> interfaccia.  
  
 Si noti che il `GetAutoExpressionsCount` e `GetAutoExpression` metodi sono metodi personalizzati sul `TestAuthoringSink` dell'oggetto e sono stati aggiunti per supportare questo esempio. Rappresentano uno dei modi in cui espressioni aggiunto al `TestAuthoringSink` oggetto dal parser (chiamando il <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> metodo) sono accessibili all'esterno di parser.  
  
```csharp  
using Microsoft.VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override int GetProximityExpressions(IVsTextBuffer buffer,  
                                                    int line,  
                                                    int col,  
                                                    int cLines,  
                                                    out IVsEnumBSTR ppEnum)  
        {  
            int retval = VSConstants.E_NOTIMPL;  
            ppEnum = null;  
            if (buffer != null)  
            {  
                IVsTextLines textLines = buffer as IVsTextLines;  
                if (textLines != null)  
                {  
                    Source src = this.GetSource(textLines);  
                    if (src != null)  
                    {  
                        TokenInfo tokenInfo = new TokenInfo();  
                        string text = src.GetText();  
                        ParseRequest req = CreateParseRequest(src,  
                                                              line,  
                                                              col,  
                                                              tokenInfo,  
                                                              text,  
                                                              src.GetFilePath(),  
                                                              ParseReason.Autos,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        retval = VSConstants.S_FALSE;  
                        int spanCount = sink.GetAutoExpressionsCount();  
                        if (spanCount > 0) {  
                            TestVsEnumBSTR bstrList = new TestVsEnumBSTR();  
                            for (int i = 0; i < spanCount; i++)  
                            {  
                                TextSpan span;  
                                sink.GetAutoExpression(i, out span);  
                                string expression = src.GetText(span.iStartLine,  
                                                                span.iStartIndex,  
                                                                span.iEndLine,  
                                                                span.iEndIndex);  
                                bstrList.AddString(expression);  
                            }  
                            ppEnum = bstrList;  
                            retval = VSConstants.S_OK;  
                        }  
                    }  
                }  
            }  
            return retval;  
        }  
    }  
}  
```