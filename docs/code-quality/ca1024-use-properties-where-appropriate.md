---
title: 'CA1024: Utilizzare proprietà dove appropriato'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 03318241206b812f4ffb57dddfc6b4f021d600f1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: Utilizzare proprietà dove appropriato
|||
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo pubblico o protetto presenta un nome che inizia con `Get`, non accetta parametri e restituisce un valore che non è una matrice.

## <a name="rule-description"></a>Descrizione della regola
 Nella maggior parte dei casi, le proprietà rappresentano dati e i metodi eseguono azioni. Le proprietà sono accessibili come campi, che li rende più facile da utilizzare. Un metodo è un buon candidato per diventare una proprietà, se una delle seguenti condizioni è presente:

-   Non accetta argomenti e restituisce le informazioni sullo stato di un oggetto.

-   Accetta un solo argomento per impostare una parte dello stato di un oggetto.

 Le proprietà devono comportarsi come se fossero campi. Se il metodo non è possibile, non deve essere modificato in una proprietà. I metodi sono preferibili rispetto alle proprietà nelle situazioni seguenti:

-   Il metodo esegue un'operazione richiede molto tempo. Il metodo è sensibilmente più lento rispetto al tempo necessario per impostare o ottenere il valore di un campo.

-   Il metodo esegue una conversione. L'accesso a un campo non restituisce una versione convertita dei dati in essa contenuti.

-   Il metodo Get ha un effetto collaterale osservabile. Il recupero del valore di un campo non produce effetti collaterali.

-   L'ordine di esecuzione è importante. L'impostazione del valore di un campo non si basa sull'occorrenza da altre operazioni.

-   La chiamata al metodo due volte in successione crea risultati diversi.

-   Il metodo è statico ma restituisce un oggetto che può essere modificato dal chiamante. Il recupero del valore di un campo non consente al chiamante di modificare i dati archiviati in base al campo.

-   Il metodo restituisce una matrice.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare il metodo a una proprietà.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Escludere un avviso da questa regola se il metodo soddisfi almeno uno dei criteri elencati in precedenza.

## <a name="controlling-property-expansion-in-the-debugger"></a>Controllo dell'espansione di proprietà nel Debugger
 I programmatori di evitare l'utilizzo di una proprietà di uno dei motivi è perché non è richiesto il debugger espanda automaticamente. Ad esempio, la proprietà può comportare l'allocazione di un oggetto di grandi dimensioni o la chiamata di P/Invoke, ma potrebbe non avere effetti collaterali observable.

 È possibile impedire che il debugger di espansione automatica proprietà applicando <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>. Nell'esempio seguente viene illustrato questo attributo viene applicato a una proprietà dell'istanza.

```vb
Imports System
Imports System.Diagnostics

Namespace Microsoft.Samples

    Public Class TestClass

        ' [...]

        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _
        Public ReadOnly Property LargeObject() As LargeObject
            Get
                ' Allocate large object
                ' [...]
            End Get
        End Property

    End Class

End Namespace
```

```csharp

      using System;
using System.Diagnostics;

namespace Microsoft.Samples
{
    publicclass TestClass
    {
        // [...]

        [DebuggerBrowsable(DebuggerBrowsableState.Never)]
        public LargeObject LargeObject
        {
            get
            {
                // Allocate large object
                // [...]

        }
    }
}
```

## <a name="example"></a>Esempio
 Nell'esempio seguente contiene diversi metodi che devono essere convertiti in proprietà e diversi che è consigliabile non perché non si comportano come campi.

 [!code-csharp[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]