---
title: 'CA1049: I tipi delle risorse native devono essere Disposable'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 6484d6d6313db543f0e80a1e66c3051839fe0a06
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: I tipi delle risorse native devono essere Disposable
|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Fa riferimento a un tipo di un <xref:System.IntPtr?displayProperty=fullName> campo, un <xref:System.UIntPtr?displayProperty=fullName> , campo o un <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> campo, ma non implementa <xref:System.IDisposable?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola presuppone che <xref:System.IntPtr>, <xref:System.UIntPtr>, e <xref:System.Runtime.InteropServices.HandleRef> campi archiviano i puntatori alle risorse non gestite. I tipi che allocano risorse non gestite devono implementare <xref:System.IDisposable> per consentire ai chiamanti di rilasciare quelle risorse su richiesta e ridurre la durata degli oggetti che contengono le risorse.

 Il modello di progettazione consigliata per pulire le risorse non gestite consiste nel fornire sia un mezzi impliciti ed espliciti per liberare le risorse tramite il <xref:System.Object.Finalize%2A?displayProperty=fullName> (metodo) e <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> metodo, rispettivamente. Il garbage collector chiama la <xref:System.Object.Finalize%2A> metodo di un oggetto in un determinato momento dopo l'oggetto viene identificato come non raggiungibile. Dopo aver <xref:System.Object.Finalize%2A> viene chiamato, un altro processo di garbage collection è necessaria per liberare l'oggetto. Il <xref:System.IDisposable.Dispose%2A> metodo consente al chiamante di rilasciare esplicitamente le risorse su richiesta, prima di quando sarebbe rilasciate al garbage collector. Dopo che pulisce le risorse non gestite, <xref:System.IDisposable.Dispose%2A> deve chiamare il <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> metodo per consentire al garbage collector di sapere che <xref:System.Object.Finalize%2A> non è necessario chiamare; Ciò elimina la necessità di ulteriori garbage collection e riduce il durata dell'oggetto.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il tipo non fa riferimento a una risorsa non gestita. In caso contrario, non escludere un avviso da questa regola perché non si implementa <xref:System.IDisposable> può rendere disponibili o sottoutilizzate le risorse non gestite.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che implementa <xref:System.IDisposable> per pulire una risorsa non gestita.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]

## <a name="related-rules"></a>Regole correlate
 [CA2115: Chiamare GC.KeepAlive durante l'uso di risorse native](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: Chiamare GC.SuppressFinalize correttamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: I tipi Disposable devono dichiarare un finalizzatore](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: I tipi proprietari di campi Disposable devono essere Disposable](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Vedere anche
 [Pulizia delle risorse non gestite](/dotnet/standard/garbage-collection/unmanaged) [modello Dispose](/dotnet/standard/design-guidelines/dispose-pattern)