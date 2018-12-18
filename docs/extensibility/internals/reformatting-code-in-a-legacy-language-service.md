---
title: La formattazione di codice in un servizio di linguaggio Legacy | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 392afbafc2ce15dbf7ee347efdf24ce1f7fe2301
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>La formattazione di codice in un servizio di linguaggio Legacy

In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] possibile riformattare il codice sorgente per l'utilizzo di rientri e gli spazi vuoti di normalizzazione. Può trattarsi di inserimento o rimozione di spazi o tabulazioni all'inizio di ogni riga, aggiunta di nuove righe tra le righe o sostituendo gli spazi con tabulazioni o tabulazioni con spazi.  
  
>**Nota:** inserimento o l'eliminazione dei caratteri di nuova riga possono influenzare i marcatori, ad esempio i punti di interruzione e segnalibri, ma aggiungendo o rimuovendo spazi o tabulazioni non influisce sulla marcatori.  
  
Gli utenti possono avviare un'operazione riformattando selezionando **la selezione del formato** o **Formatta documento** dal **avanzate** menu il **modifica**menu. Un'operazione riformattando può anche essere attivata quando viene inserito un frammento di codice o un carattere specifico. Ad esempio, quando si digita una parentesi graffa di chiusura in c#, tutti gli elementi tra parentesi graffa di apertura corrispondente e la parentesi graffa di chiusura viene rientrato automaticamente per il livello appropriato.
  
Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] invia il **Selezione formato** o **Formatta documento** comando per il servizio di linguaggio, il <xref:Microsoft.VisualStudio.Package.ViewFilter> classe chiamate il <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metodo la <xref:Microsoft.VisualStudio.Package.Source> classe. Per supportare la formattazione è necessario eseguire l'override di <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metodo e fornire una formattazione di codice.  
  
## <a name="enabling-support-for-reformatting"></a>Abilitazione del supporto per la formattazione  

Per supportare la formattazione, le `EnableFormatSelection` parametro del <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> deve essere impostato su `true` quando si registra il pacchetto VSPackage. Consente di impostare il <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> proprietà `true`. Il <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> metodo restituisce il valore di questa proprietà. Se restituisce true, il <xref:Microsoft.VisualStudio.Package.ViewFilter> classe chiama il <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>.  
  
## <a name="implementing-reformatting"></a>Implementazione di riformattazione

Per implementare la riformattazione, è necessario derivare una classe dalla classe di <xref:Microsoft.VisualStudio.Package.Source> classe ed eseguire l'override di <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metodo. Il <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> descrive l'intervallo per formattare e <xref:Microsoft.VisualStudio.Package.EditArray> oggetto contiene le modifiche apportate all'intervallo. Si noti che questo intervallo può essere l'intero documento. Tuttavia, poiché sono presenti probabilmente più le modifiche apportate all'intervallo, tutte le modifiche devono essere reversibile in un'unica azione. A tale scopo, eseguire il wrapping di tutte le modifiche in un <xref:Microsoft.VisualStudio.Package.CompoundAction> (nella sezione "Utilizzo della classe CompoundAction" in questo argomento) dell'oggetto.

### <a name="example"></a>Esempio  

Nell'esempio seguente si che è uno spazio dopo ogni virgola della selezione, a meno che la virgola è seguita da una tabulazione o alla fine della riga. Gli spazi finali dopo l'eliminazione dell'ultima virgola in una riga. Vedere la sezione "Utilizzo della classe CompoundAction" in questo argomento per vedere come questo metodo viene chiamato dal <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metodo.  

```csharp 
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        private void DoFormatting(EditArray mgr, TextSpan span)  
        {  
            // Make sure there is one space after every comma unless followed  
            // by a tab or comma is at end of line.  
            IVsTextLines pBuffer = GetTextLines();  
            if (pBuffer != null)  
            {  
                int    startIndex = span.iStartIndex;  
                int    endIndex   = 0;  
                string line       = "";  
                // Loop over all lines in span  
                for (int i = span.iStartLine; i <= span.iEndLine; i++)  
                {  
                    if (i < span.iEndLine)  
                    {  
                        pBuffer.GetLengthOfLine(i, out endIndex);  
                    }  
                    else  
                    {  
                        endIndex = span.iEndIndex;  
                    }  
                    pBuffer.GetLineText(i, startIndex, i, endIndex, out line);  
  
                    if (line.Length > 0)  
                    {  
                        int index = 0;  
                        // Loop over all commas in line  
                        while ((index = line.IndexOf(',', index)) != -1)  
                        {  
                            int spaceIndex = index + 1;  
                            // Determine how many spaces after comma  
                            while (spaceIndex < line.Length && line[spaceIndex] == ' ')  
                            {  
                                ++spaceIndex;  
                            }  
  
                            int      spaceCount      = spaceIndex - (index + 1);  
                            string   replacementText = " ";  
                            bool     fDoEdit         = true;  
                            TextSpan editTextSpan    = new TextSpan();  
  
                            editTextSpan.iStartLine  = i;  
                            editTextSpan.iEndLine    = i;  
                            editTextSpan.iStartIndex = index + 1;  
  
                            if (spaceIndex == line.Length)  
                            {  
                                if (spaceCount > 0)  
                                {  
                                    // Delete spaces after a comma at end of line  
                                    editTextSpan.iEndIndex = spaceIndex;  
                                    replacementText = "";  
                                }  
                                else  
                                {  
                                    // Otherwise, do not add spaces if comma is  
                                    // at end of line.  
                                    fDoEdit = false;  
                                }  
                            }  
                            else if (spaceCount == 0)  
                            {  
                                if (spaceIndex < line.Length && line[spaceIndex] == '\t')  
                                {  
                                    // Do not insert space if a tab follows  
                                    // a comma.  
                                    fDoEdit = false;  
                                }  
                                else  
                                {  
                                    // No space after comma so add a space.  
                                    editTextSpan.iEndIndex = index + 1;  
                                }  
                            }  
                            else if (spaceCount > 1)  
                            {  
                                // More than one space after comma, replace  
                                // with a single space.  
                                editTextSpan.iEndIndex = spaceIndex;  
                            }  
                            else  
                            {  
                                // Single space after a comma and not at end  
                                // of the line, leave it alone.  
                                fDoEdit = false;  
                            }  
                            if (fDoEdit)  
                            {  
                                // Add edit operation  
                                mgr.Add(new EditSpan(editTextSpan, replacementText));  
                            }  
                            index = spaceIndex;  
                        }  
                    }  
                    startIndex = 0; // All subsequent lines start at 0  
                }  
                // Apply all edits  
                mgr.ApplyEdits();  
            }  
        }  
    }  
}  
```  
  
## <a name="using-the-compoundaction-class"></a>Utilizzo della classe CompoundAction  
 
La riformattazione eseguita su una sezione di codice deve essere reversibile in un'unica azione. Questa può essere eseguita tramite un <xref:Microsoft.VisualStudio.Package.CompoundAction> classe. Questa classe esegue il wrapping di un set di operazioni di modifica nel buffer di testo in un'operazione singola modifica.  
  
### <a name="example"></a>Esempio

Di seguito è riportato un esempio di come utilizzare la <xref:Microsoft.VisualStudio.Package.CompoundAction> classe. Vedere l'esempio nella sezione "Implementazione di supporto per la formattazione" in questo argomento per un esempio di `DoFormatting` metodo.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override void ReformatSpan(EditArray mgr, TextSpan span)  
        {  
            string description = "Reformat code";  
            CompoundAction ca = new CompoundAction(this, description);  
            using (ca)  
            {  
                ca.FlushEditActions();      // Flush any pending edits  
                DoFormatting(mgr, span);    // Format the span  
            }  
        }  
    }  
}  
```  

## <a name="see-also"></a>Vedere anche

[Funzionalità del linguaggio legacy](legacy-language-service-features1.md)