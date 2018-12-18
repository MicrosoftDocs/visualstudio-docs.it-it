---
title: Struttura in un servizio di linguaggio Legacy | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b899f53ba6b2a0b58997cc51a83a0d9ca8480e63
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="outlining-in-a-legacy-language-service"></a>Struttura in un servizio di linguaggio Legacy
Struttura consente di comprimere un programma complesso in un panoramica o struttura. Ad esempio, in c# tutti i metodi possono essere compressi in una singola riga, che mostra solo la firma del metodo. Inoltre, strutture e classi possono essere compressi per mostrare solo i nomi delle classi e strutture. All'interno di un singolo metodo, una logica complessa può essere compressi per mostrare il flusso complessivo mostrando solo la prima riga di istruzioni, ad esempio `foreach`, `if`, e `while`.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori dettagli, vedere [procedura dettagliata: struttura](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a usare il nuovo editor di API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## <a name="enabling-support-for-outlining"></a>Abilitazione del supporto per la struttura  
 Il `AutoOutlining` voce del Registro di sistema è impostato su 1 per abilitare la struttura automatica. La struttura automatica consente di impostare l'analisi dell'intera origine quando un file viene caricato o modificato allo scopo di identificare le aree nascoste e visualizzare le icone della struttura. Struttura può anche essere controllata manualmente dall'utente.  
  
 Il valore della `AutoOutlining` voce del Registro di sistema può essere ottenuto tramite il <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> proprietà la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. Il `AutoOutlining` voce del Registro di sistema può essere inizializzato con un parametro denominato per il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attributo (vedere [la registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md) per informazioni dettagliate).  
  
## <a name="the-hidden-region"></a>L'area nascosta  
 Per fornire la struttura, il servizio di linguaggio deve supportare aree nascoste. Si tratta di intervalli di testo che possono essere espansi o compressi. Aree nascoste possono essere delimitate dai simboli di linguaggio standard, ad esempio le parentesi graffe, oppure i simboli personalizzati. In c#, ad esempio, ha un `#region` / `#endregion` coppia che delimita una regione.  
  
 Le aree nascoste vengono gestite da un gestore di regione, che viene esposto come il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> interfaccia.  
  
 Struttura utilizza aree nascoste di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> l'interfaccia e contengono l'intervallo di regione, lo stato di visualizzazione corrente e il messaggio da visualizzare quando l'intervallo è compressa.  
  
 Il parser del linguaggio del servizio utilizza il <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> metodo per aggiungere una nuova area nascosta con il comportamento predefinito per le aree nascoste, mentre il <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> metodo consente di personalizzare l'aspetto e comportamento della struttura. Una volta aree nascoste vengono concesse per la sessione di area nascosta, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestisce le aree nascoste per il servizio di linguaggio.  
  
 Se è necessario determinare quando la sessione di area nascosta viene eliminato definitivamente, viene modificata in un'area nascosta oppure è necessario assicurarsi che una determinata area nascosta è visibile; è necessario derivare una classe dalla classe di <xref:Microsoft.VisualStudio.Package.Source> classe ed eseguire l'override dei metodi appropriati, <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>, e <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>, rispettivamente.  
  
### <a name="example"></a>Esempio  
 Di seguito è riportato un esempio semplificato di creazione di aree nascoste per tutte le coppie di parentesi graffe. Si presuppone che il linguaggio fornisce corrispondenza parentesi graffe e che le parentesi graffe devono corrispondere almeno includano le parentesi graffe ({e}). Questo approccio è solo a scopo illustrativo. Un'implementazione completa avrebbe una gestione completa dei case in <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>. In questo esempio viene inoltre illustrato come impostare il <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> preferenza per `true` temporaneamente. In alternativa è possibile specificare il `AutoOutlining` denominato parametro nel `ProvideLanguageServiceAttribute` attributo nel pacchetto del linguaggio.  
  
 In questo esempio si presuppone che le regole di c# per i commenti, stringhe e valori letterali.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
  
    public class MyLanguageService : LanguageService  
    {  
        private LanguagePreferences m_preferences;  
  
        public override LanguagePreferences  GetLanguagePreferences()  
        {  
            if (m_preferences == null)  
            {  
                m_preferences = new LanguagePreferences(this.Site,  
                                                        typeof(MyLanguageService).GUID,  
                                                        Name);  
                m_preferences.Init();  
                // Temporarily enabled auto-outlining  
                m_preferences.AutoOutlining = true;  
            }  
            return m_preferences;  
        }  
  
        public override AuthoringScope  ParseSource(ParseRequest req)  
        {  
            Source source = (Source) this.GetSource(req.FileName);  
            switch (req.Reason)  
            {  
               case ParseReason.HighlightBraces:  
               case ParseReason.MatchBraces:  
               case ParseReason.MemberSelectAndHighlightBraces:  
                  if (source.Braces != null)  
                  {  
                      foreach (TextSpan[] brace in source.Braces)  
                      {  
                         if (brace.Length == 2)  
                         {  
                             if (req.Sink.HiddenRegions == true   
                                   && source.GetText(brace[0]).Equals("{")   
                                   && source.GetText(brace[1]).Equals("}"))  
                             {  
                                //construct a TextSpan of everything between the braces  
                                TextSpan hideSpan = new TextSpan();  
                                hideSpan.iStartIndex = brace[0].iStartIndex;  
                                hideSpan.iStartLine = brace[0].iStartLine;  
                                hideSpan.iEndIndex = brace[1].iEndIndex;  
                                hideSpan.iEndLine = brace[1].iEndLine;  
                                req.Sink.ProcessHiddenRegions = true;  
                                req.Sink.AddHiddenRegion(hideSpan);  
                             }  
                             req.Sink.MatchPair(brace[0], brace[1], 1);  
                         }  
                         else if (brace.Length >= 3)  
                             req.Sink.MatchTriple(brace[0], brace[1], brace[2], 1);  
                  }  
        }  
                   break;  
               default:  
                   break;  
      }  
            // Must always return a valid AuthoringScope object.  
            return new MyAuthoringScope();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità del linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)