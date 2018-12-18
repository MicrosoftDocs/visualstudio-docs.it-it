---
title: 'CA2118: Revisione di SuppressUnmanagedCodeSecurityAttribute | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6a6c5e60ed84a79e6e81d4cd066d75b1270bdb71
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: Verificare la sintassi di SuppressUnmanagedCodeSecurityAttribute
|||  
|-|-|  
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|  
|CheckId|CA2118|  
|Category|Microsoft.Security|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un membro o un tipo pubblico o protetto presenta il <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> attributo.  
  
## <a name="rule-description"></a>Descrizione della regola  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>modifica il comportamento di sistema di sicurezza predefinito per i membri che eseguono codice non gestito mediante la chiamata di piattaforma o l'interoperabilità COM. In genere, il sistema esegue un [dati e modellazione](/dotnet/framework/data/index) autorizzazione per codice non gestito. Questa richiesta avviene in fase di esecuzione per ogni chiamata del membro e controlla ogni chiamante nello stack di chiamate per l'autorizzazione. Quando l'attributo è presente, il sistema esegue un [le richieste di collegamento](/dotnet/framework/misc/link-demands) per l'autorizzazione: le autorizzazioni del chiamante immediato vengono controllate quando il chiamante viene compilato tramite JIT.  
  
 Questo attributo viene principalmente usato per aumentare le prestazioni. L'aumento delle prestazioni, tuttavia, comporta notevoli rischi in termini di sicurezza. Se si inserisce l'attributo su membri pubblici che chiamano metodi nativi, i chiamanti nello stack di chiamate (diverso dal chiamante immediato) non richiedono l'autorizzazione di codice non gestito per eseguire codice non gestito. A seconda del membro pubblico azioni e la gestione di input, è possibile che i chiamanti non attendibili per accedere alle funzionalità in genere limitate al codice attendibile.  
  
 Il [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] si basa sui controlli di sicurezza per impedire ai chiamanti di accedere direttamente allo spazio degli indirizzi del processo corrente. Poiché questo attributo ignora la sicurezza normale, il codice comporta una grave minaccia se può essere utilizzato per leggere o scrivere nella memoria del processo. Si noti che il rischio non è limitato ai metodi che forniscono intenzionalmente l'accesso per l'elaborazione di memoria. è inoltre presente in qualsiasi scenario in cui codice dannoso può ottenere accesso con qualsiasi mezzo, ad esempio, fornendo input sorprendente, in formato non valido o non valido.  
  
 I criteri di sicurezza predefinito non concedono l'autorizzazione per codice non gestito a un assembly a meno che non venga eseguito dal computer locale o un membro di uno dei seguenti gruppi:  
  
-   Il gruppo di codice di area Computer  
  
-   Gruppo di codice nome sicuro di Microsoft  
  
-   Gruppo di codice nome sicuro ECMA  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Leggere attentamente il codice per assicurarsi che l'attributo è assolutamente necessario. Se si ha familiarità con la sicurezza di codice gestito o non riconosce le implicazioni di sicurezza dell'utilizzo di questo attributo, rimuoverlo dal codice. Se l'attributo è obbligatorio, è necessario assicurarsi che i chiamanti non è possibile utilizzare il codice da utenti malintenzionati. Se il codice non dispone dell'autorizzazione per eseguire codice non gestito, questo attributo non ha alcun effetto e deve essere rimosso.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Per eliminare in modo sicuro un avviso da questa regola, è necessario assicurarsi che il codice non fornisce accesso a operazioni native o risorse che possono essere utilizzate in modo distruttivo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene violata la regola.  
  
 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, il `DoWork` metodo fornisce un percorso di codice accessibile pubblicamente per il metodo di chiamata `FormatHardDisk`.  
  
 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, il metodo pubblico `DoDangerousThing` provoca una violazione. Per risolvere la violazione, `DoDangerousThing` deve essere reso privato e l'accesso a esso deve essere tramite un metodo pubblico protetto da una richiesta di sicurezza, come illustrato di `DoWork` metodo.  
  
 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_3.cs)]  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>   
 [Linee guida di codice sicuro](/dotnet/standard/security/secure-coding-guidelines)   
 [Dati e modellazione](/dotnet/framework/data/index)  
 [Richieste di collegamento](/dotnet/framework/misc/link-demands)  
  