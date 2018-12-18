---
title: "CA2115: Chiamare GC.KeepAlive durante l'utilizzo di risorse native"
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 3eea5a288dc907881b7eb444b26d7018e8008ad2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: Chiamare GC.KeepAlive durante l'utilizzo di risorse native
|||
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un metodo dichiarato in un tipo con un finalizzatore fa riferimento a un <xref:System.IntPtr?displayProperty=fullName> o <xref:System.UIntPtr?displayProperty=fullName> campo, ma non chiama <xref:System.GC.KeepAlive%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 Operazione di Garbage collection completa di un oggetto se non sono presenti più riferimenti a esso nel codice gestito. Riferimenti non gestiti a oggetti non impediscono l'operazione di garbage collection. Questa regola rileva gli errori che possono verificarsi qualora una risorsa non gestita venga completata mentre è ancora utilizzata da codice non gestito.

 Questa regola presuppone che <xref:System.IntPtr> e <xref:System.UIntPtr> campi archiviano i puntatori alle risorse non gestite. Poiché lo scopo di un finalizzatore è liberare le risorse non gestite, la regola presuppone che il finalizzatore consente di liberare la risorsa non gestita a cui fa riferimento a campi del puntatore. Questa regola si presuppone inoltre che il metodo fa riferimento il campo del puntatore per passare la risorsa non gestita a codice non gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere una chiamata a <xref:System.GC.KeepAlive%2A> al metodo, passando l'istanza corrente (`this` in c# e C++) come argomento. Posizionare la chiamata dopo l'ultima riga di codice in cui l'oggetto deve essere protetto da garbage collection. Immediatamente dopo la chiamata a <xref:System.GC.KeepAlive%2A>, l'oggetto viene nuovamente considerato pronto per l'operazione di garbage collection, supponendo che non sono presenti riferimenti gestiti a esso.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Questa regola consente di alcuni presupposti che possono comportare falsi positivi. È possibile eliminare un avviso da questa regola in modo sicuro se:

-   Il finalizzatore non libera di per il contenuto del <xref:System.IntPtr> o <xref:System.UIntPtr> campo a cui fa riferimento il metodo.

-   Il metodo non passa il <xref:System.IntPtr> o <xref:System.UIntPtr> campo a codice non gestito.

 Leggere attentamente gli altri messaggi prima di escluderli. Questa regola rileva gli errori che sono difficili da riprodurre ed eseguire il debug.

## <a name="example"></a>Esempio
 Nell'esempio seguente, `BadMethod` non include una chiamata a `GC.KeepAlive` e pertanto viola la regola. `GoodMethod` contiene il codice corretto.

> [!NOTE]
>  Questo esempio si trova nello pseudo-codice anche se il codice viene compilato ed eseguito, l'avviso non viene generato perché una risorsa non gestita non viene creata o liberata.

 [!code-csharp[FxCop.Security.IntptrAndFinalize#1](../code-quality/codesnippet/CSharp/ca2115-call-gc-keepalive-when-using-native-resources_1.cs)]

## <a name="see-also"></a>Vedere anche
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName> <xref:System.Object.Finalize%2A?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName> [Modello Dispose](/dotnet/standard/design-guidelines/dispose-pattern)