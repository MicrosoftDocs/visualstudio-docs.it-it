---
title: 'CA1060: Spostare P-richiama nella classe NativeMethods | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7805710c61e6a9fcf4ede2ebcbf69589b53141f9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060: Spostare i P/Invoke nella classe NativeMethods
|||  
|-|-|  
|TypeName|MovePInvokesToNativeMethodsClass|  
|CheckId|CA1060|  
|Category|Microsoft. Design|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un metodo utilizza i servizi di Platform Invoke per accedere al codice non gestito e non è un membro di uno del **NativeMethods** classi.  
  
## <a name="rule-description"></a>Descrizione della regola  
 I metodi di chiamata al sistema operativo, ad esempio quelli contrassegnati utilizzando il <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> attributi o metodi definiti mediante il `Declare` parola chiave in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], accedere a codice non gestito. Questi metodi devono essere una delle seguenti classi:  
  
-   **NativeMethods** -questa classe non elimina i percorsi stack per l'autorizzazione per codice non gestito. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> non deve essere applicata a questa classe.) Questa classe è per i metodi che possono essere utilizzati ovunque, perché verrà eseguita un'analisi dello stack.  
  
-   **SafeNativeMethods** -questa classe Elimina percorsi stack per l'autorizzazione per codice non gestito. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> viene applicato a questa classe.) Questa classe è per i metodi che sono sicuri per tutti gli utenti di chiamare. I chiamanti di questi metodi non è necessario eseguire una revisione di sicurezza avanzata per assicurarsi che l'utilizzo sia sicuro perché i metodi sono innocui per qualsiasi chiamante.  
  
-   **UnsafeNativeMethods** -questa classe Elimina percorsi stack per l'autorizzazione per codice non gestito. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> viene applicato a questa classe.) Questa classe è per i metodi potenzialmente pericolosi. Qualsiasi chiamante di questi metodi è necessario eseguire una revisione di sicurezza avanzata per assicurarsi che l'utilizzo sia sicuro perché verrà eseguito alcun percorso stack.  
  
 Queste classi vengono dichiarate come `internal` (`Friend`, in Visual Basic) e si dichiara un costruttore privato per impedire la creazione di nuove istanze. I metodi delle classi devono essere `static` e `internal` (`Shared` e `Friend` in Visual Basic).  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, spostare il metodo appropriato **NativeMethods** classe. Per la maggior parte delle applicazioni, lo spostamento di P/Invoke a una nuova classe denominata **NativeMethods** è sufficiente.  
  
 Tuttavia, se si stanno sviluppando librerie per l'uso in altre applicazioni, è consigliabile definire due altre classi che vengono chiamati **SafeNativeMethods** e **UnsafeNativeMethods**. Queste classi sono simili al **NativeMethods** classe; tuttavia, sono contrassegnati con un attributo speciale denominato **SuppressUnmanagedCodeSecurityAttribute**. Quando questo attributo viene applicato, il runtime non esegue un percorso stack completo per assicurarsi che tutti i chiamanti dispongano di **UnmanagedCode** autorizzazione. In genere, il runtime controlla questa autorizzazione all'avvio. Poiché il controllo non viene eseguito, è possibile migliorare notevolmente le prestazioni per le chiamate a questi metodi non gestiti, consente inoltre il codice che dispone di autorizzazioni limitate per chiamare questi metodi.  
  
 Tuttavia, si debba usare questo attributo con molta attenzione. Se implementato in modo non corretto può avere gravi rischi di protezione...  
  
 Per informazioni su come implementare i metodi, vedere il **NativeMethods** esempio **SafeNativeMethods** esempio e **UnsafeNativeMethods** esempio.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene dichiarato un metodo che viola questa regola. Per correggere la violazione, il **RemoveDirectory** P/Invoke devono essere spostati in una classe appropriata è progettata per contenere solo P/Invoke.  
  
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]  
  
## <a name="nativemethods-example"></a>Esempio NativeMethods  
  
### <a name="description"></a>Descrizione  
 Poiché il **NativeMethods** classe non deve essere contrassegnata utilizzando **SuppressUnmanagedCodeSecurityAttribute**, P/Invoke che vengono inseriti in essa contenuti richiederà **UnmanagedCode** autorizzazione. Poiché la maggior parte delle applicazioni vengono eseguite dal computer locale e l'esecuzione con attendibilità totale, ciò non costituisce generalmente un problema. Tuttavia, se si stanno sviluppando librerie riutilizzabili, considerare la definizione di un **SafeNativeMethods** o **UnsafeNativeMethods** classe.  
  
 Nell'esempio seguente un **Interaction. Beep** metodo che esegue il wrapping di **MessageBeep** funzione da User32. dll. Il **MessageBeep** P/Invoke viene inserito nella **NativeMethods** classe.  
  
### <a name="code"></a>Codice  
 [!code-csharp[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
 [!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]  
  
## <a name="safenativemethods-example"></a>Esempio SafeNativeMethods  
  
### <a name="description"></a>Descrizione  
 Metodi di P/Invoke che possono essere esposti a qualsiasi applicazione e che non dispongono di tutti gli effetti collaterali dovrebbero essere inseriti in una classe denominata **SafeNativeMethods**. Non è necessario richiedere autorizzazioni e non è necessario conoscere da dove vengono chiamati.  
  
 Nell'esempio seguente un **Environment. TickCount** proprietà che esegue il wrapping di **GetTickCount** funzione da kernel32.dll.  
  
### <a name="code"></a>Codice  
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]  
  
## <a name="unsafenativemethods-example"></a>Esempio UnsafeNativeMethods  
  
### <a name="description"></a>Descrizione  
 I metodi P/Invoke che non può essere chiamato in modo sicuro e che può causare effetti collaterali dovrebbero essere inseriti in una classe denominata **UnsafeNativeMethods**. Questi metodi devono essere controllati rigorosamente per assicurarsi che non sono esposti all'utente accidentalmente. La regola [CA2118: sintassi di SuppressUnmanagedCodeSecurityAttribute revisione](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) consente all'oggetto. In alternativa, i metodi devono avere un'altra autorizzazione richiesta invece di **UnmanagedCode** che li utilizzano.  
  
 Nell'esempio seguente un **Cursor. hide** metodo che esegue il wrapping di **ShowCursor** funzione da User32. dll.  
  
### <a name="code"></a>Codice  
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_4.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_4.cs)]  
  
## <a name="see-also"></a>Vedere anche  
 [Avvisi di progettazione](../code-quality/design-warnings.md)