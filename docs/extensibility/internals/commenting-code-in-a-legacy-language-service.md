---
title: Commento di codice in un servizio di linguaggio Legacy | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e6dfeb31ab062d5182b56ba450450d41a6dab807
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="commenting-code-in-a-legacy-language-service"></a>Commento di codice in un servizio di linguaggio Legacy
Linguaggi di programmazione in genere forniscono un mezzo per inserire annotazioni o commenti nel codice. Un commento è una sezione di testo che fornisce informazioni aggiuntive sul codice, ma viene ignorato durante la compilazione o interpretazione.  
  
 Le classi di pacchetto gestito (MPF) framework forniscono supporto per commenti e rimozione dei commenti sul testo selezionato.  
  
## <a name="comment-styles"></a>Stili di commento  
 Esistono due stili generale di commento:  
  
1.  Commenti a riga, in cui il commento è una singola riga.  
  
2.  Commenti del blocco, dove il commento può includere più righe.  
  
 I commenti a riga in genere dispongono di un carattere iniziale (o caratteri), mentre i commenti del blocco di caratteri di inizio e di fine. Ad esempio, in c#, un commento a riga inizia con / /, e inizia un blocco di commento con / * e finisce con \*/.  
  
 Quando l'utente seleziona il comando **Commenta selezione** dal **modifica** -> **avanzate** menu, il comando viene indirizzato al <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> metodo il <xref:Microsoft.VisualStudio.Package.Source> classe. Quando l'utente seleziona il comando **rimuovere il commento selezione**, il comando viene indirizzato al <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> metodo.  
  
## <a name="supporting-code-comments"></a>Commenti del codice di supporto  
 È possibile disporre i commenti di codice lingua supporto servizio mediante il `EnableCommenting` denominato parametro del <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Consente di impostare il <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> proprietà la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. Per ulteriori informazioni sull'impostazione language servicce funzionalità, vedere [la registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
 È inoltre necessario eseguire l'override di <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> per restituire un <xref:Microsoft.VisualStudio.Package.CommentInfo> struttura con i caratteri di commento per la propria lingua. C#-caratteri di commento stile linea sono l'impostazione predefinita.  
  
### <a name="example"></a>Esempio  
 Ecco un esempio di implementazione del <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> metodo.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override CommentInfo GetCommentFormat() {  
            CommentInfo info = new CommentInfo();  
            info.LineStart       = "//";  
            info.BlockStart      = "/*";  
            info.BlockEnd        = "*/";  
            info.UseLineComments = true;  
            return info;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità del linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)