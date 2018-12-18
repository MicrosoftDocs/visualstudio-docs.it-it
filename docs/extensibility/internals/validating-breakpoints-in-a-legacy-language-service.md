---
title: Convalida i punti di interruzione in un servizio di linguaggio Legacy | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03bf1534789ba24e1bbf597874ea427057073b61
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Convalida i punti di interruzione in un servizio di linguaggio Legacy
Un punto di interruzione indica che l'esecuzione del programma deve essere arrestata in un particolare punto mentre è in esecuzione in un debugger. Un utente può inserire un punto di interruzione in qualsiasi riga nel file di origine, poiché l'editor non ha alcuna conoscenza di ciò che costituisce una posizione valida per un punto di interruzione. Quando il debugger viene avviato, tutti i punti di interruzione contrassegnate (denominati in sospeso i punti di interruzione) vengono associati nella posizione appropriata nel programma in esecuzione. Allo stesso tempo che i punti di interruzione vengono convalidate per assicurarsi che vengono modificate le sezioni di codice valido. Ad esempio, un punto di interruzione in un commento non è valido, poiché non è presente codice in tale posizione nel codice sorgente. Il debugger disabilita i punti di interruzione non validi.  
  
 Poiché il servizio di linguaggio viene a conoscenza viene visualizzato il codice di origine, è possibile convalidare i punti di interruzione prima che il debugger viene avviato. È possibile eseguire l'override di <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> per restituire un intervallo che specifica un percorso valido per un punto di interruzione. La posizione del punto di interruzione ancora viene convalidata quando il debugger viene avviato, ma l'utente viene informato di punti di interruzione non validi senza attendere che il debugger da caricare.  
  
## <a name="implementing-support-for-validating-breakpoints"></a>Implementazione del supporto per la convalida dei punti di interruzione  
  
-   Il <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> metodo riceve la posizione del punto di interruzione. L'implementazione è necessario decidere se il percorso sia valido e indicare questo restituendo un intervallo di testo che identifica il codice associato alla posizione di riga del punto di interruzione.  
  
-   Restituire <xref:Microsoft.VisualStudio.VSConstants.S_OK> se il percorso sia valido, o <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> se non è valido.  
  
-   Se il punto di interruzione è valido e il punto di interruzione viene evidenziata l'intervallo di testo.  
  
-   Se il punto di interruzione non è valido, nella barra di stato viene visualizzato un messaggio di errore.  
  
### <a name="example"></a>Esempio  
 In questo esempio viene illustrata un'implementazione del <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> metodo che chiama il parser per ottenere l'intervallo di codice (se presente) in corrispondenza della posizione specificata.  
  
 Questo esempio si presuppone che sia stato aggiunto un `GetCodeSpan` metodo il <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe che convalida l'intervallo di testo e restituisce `true` in caso di un punto di interruzione valido.  
  
```csharp  
using Microsoft VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    class TestLanguageService : LanguageService  
    {  
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,  
                                                       int line,  
                                                       int col,  
                                                       TextSpan[] pCodeSpan)  
        {  
            int retval = VSConstants.S_FALSE;  
            if (pCodeSpan != null)  
            {  
                // Initialize span to current line by default.  
                pCodeSpan[0].iStartLine = line;  
                pCodeSpan[0].iStartIndex = col;  
                pCodeSpan[0].iEndLine = line;  
                pCodeSpan[0].iEndIndex = col;  
            }  
  
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
                                                              ParseReason.CodeSpan,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        TextSpan span = new TextSpan();  
                        if (sink.GetCodeSpan(out span))  
                        {  
                            pCodeSpan[0] = span;  
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
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità del linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)