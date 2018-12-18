---
title: 'CA2102: Individuare le eccezioni non CLSCompliant nei gestori generali | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords: CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 17238e140f8672e9d2d5a67594eb26b415c0b8d8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: Individuare le eccezioni non conformi a CLS nei gestori generali
|||  
|-|-|  
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|  
|CheckId|CA2102|  
|Category|Microsoft.Security|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Un membro in un assembly che non è contrassegnato con il <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> o è contrassegnato come `RuntimeCompatibility(WrapNonExceptionThrows = false)` contiene un blocco catch che gestisce <xref:System.Exception?displayProperty=fullName> e non contiene un blocco catch generale immediatamente successivo. Questa regola ignora [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] assembly.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Un blocco catch che gestisce <xref:System.Exception> intercetta tutte le eccezioni conforme a Common Language Specification (CLS). Tuttavia, non rileva eccezioni non CLS. Non conforme a CLS eccezioni possono essere generate da codice nativo o da codice gestito che è stato generato da Microsoft intermediate language (MSIL) dell'Assembler. Si noti che in c# e [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilatori non consente non conforme a CLS la generazione di eccezioni conforme e [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] non intercetta le eccezioni non CLS conformi. Se si intende del blocco catch per gestire tutte le eccezioni, utilizzare la seguente sintassi blocco catch generale.  
  
-   C#: `catch {}`  
  
-   C++: `catch(...) {}` o`catch(Object^) {}`  
  
 Un'eccezione conforme a CLS non gestita diventa un problema di sicurezza quando vengono rimosse le autorizzazioni concesse in precedenza nel blocco catch. Poiché non vengono intercettate eccezioni non CLS, un metodo dannoso che genera un'eccezione non CLS eccezione potrebbe eseguire con autorizzazioni elevate.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola quando si desidera rilevare tutte le eccezioni, sostituire o aggiungere un blocco catch generale o contrassegnare l'assembly `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Se le autorizzazioni vengono rimosse nel blocco catch, duplicato in generale la funzionalità di blocco catch. Se non si intende gestire tutte le eccezioni, sostituire il blocco catch che gestisce <xref:System.Exception> con blocchi catch che gestiscono i tipi di eccezione specifici.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare un avviso da questa regola se il blocco try non contiene istruzioni che potrebbero generare un'eccezione non CLS. Poiché qualsiasi codice nativo o gestito potrebbe eccezione non CLS conforme, è necessario conoscere tutto il codice che può essere eseguito in tutti i percorsi di codice all'interno del blocco try. Si noti che le eccezioni conformi non conforme a CLS non vengono generate da common language runtime.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrata una classe MSIL che genera un'eccezione non CLS.  
  
```  
.assembly ThrowNonClsCompliantException {}  
.class public auto ansi beforefieldinit ThrowsExceptions  
{  
   .method public hidebysig static void  
         ThrowNonClsException() cil managed  
   {  
      .maxstack  1  
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()  
      IL_0005:  throw  
   }  
}  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un metodo che contiene un blocco catch generale che soddisfa la regola.  
  
 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]  
  
 Compilare gli esempi precedenti, come indicato di seguito.  
  
```  
ilasm /dll ThrowNonClsCompliantException.il  
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs  
```  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1031: Non rilevare tipi di eccezione generali](../code-quality/ca1031-do-not-catch-general-exception-types.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Eccezioni e gestione delle eccezioni](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)   
 [Ilasm.exe (Assembler IL)](/dotnet/framework/tools/ilasm-exe-il-assembler)   
 [Indipendenza del linguaggio e componenti indipendenti dal linguaggio](/dotnet/standard/language-independence-and-language-independent-components)