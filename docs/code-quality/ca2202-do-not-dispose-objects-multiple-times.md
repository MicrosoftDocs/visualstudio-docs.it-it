---
title: 'CA2202: Non eliminare oggetti più volte'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ea736d142a79ee3dcc470dc4fec4261005c97189
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: Non eliminare oggetti più volte
|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Implementazione di un metodo contiene percorsi del codice che potrebbero comportare più chiamate a <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> o a un equivalente di Dispose, ad esempio un metodo Close () per alcuni tipi, sullo stesso oggetto.

## <a name="rule-description"></a>Descrizione della regola
 Una corretta implementata <xref:System.IDisposable.Dispose%2A> metodo può essere chiamato più volte senza generare un'eccezione. Tuttavia, questo non è garantito e per evitare di generare un <xref:System.ObjectDisposedException?displayProperty=fullName> non è necessario chiamare <xref:System.IDisposable.Dispose%2A> più di una volta su un oggetto.

## <a name="related-rules"></a>Regole correlate
 [CA2000: Eliminare gli oggetti prima di perdere l'ambito](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare l'implementazione in modo che indipendentemente dal percorso del codice, <xref:System.IDisposable.Dispose%2A> viene chiamato solo una volta per l'oggetto.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Anche se <xref:System.IDisposable.Dispose%2A> per l'oggetto è noto a essere chiamato in modo sicuro più volte, l'implementazione potrebbe cambiare in futuro.

## <a name="example"></a>Esempio
 Annidati `using` istruzioni (`Using` in Visual Basic) possono provocare violazioni dell'avviso CA2202. Se la risorsa IDisposable dell'interna annidata `using` istruzione contiene la risorsa di esterna `using` istruzione, il `Dispose` metodo della risorsa annidata rilascia la risorsa contenuta. Quando si verifica questa situazione, il `Dispose` metodo esterna `using` istruzione tenta di eliminare la risorsa per una seconda volta.

 Nell'esempio seguente, un <xref:System.IO.Stream> oggetto creato in un outer utilizzando l'istruzione viene rilasciato alla fine dell'istruzione nel metodo Dispose interna di <xref:System.IO.StreamWriter> oggetto che contiene il `stream` oggetto. Alla fine di esterna `using` istruzione, il `stream` oggetto viene rilasciato un secondo momento. La seconda versione costituisce una violazione di CA2202.

```
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}

```

## <a name="example"></a>Esempio
 Per risolvere questo problema, utilizzare un `try` / `finally` blocco anziché esterna `using` istruzione. Nel `finally` di blocco, assicurarsi che il `stream` risorsa non è null.

```
Stream stream = null;
try
{
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);
    using (StreamWriter writer = new StreamWriter(stream))
    {
        stream = null;
        // Use the writer object...
    }
}
finally
{
    if(stream != null)
        stream.Dispose();
}

```

## <a name="see-also"></a>Vedere anche
 <xref:System.IDisposable?displayProperty=fullName> [Modello Dispose](/dotnet/standard/design-guidelines/dispose-pattern)