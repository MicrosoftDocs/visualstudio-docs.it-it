---
title: 'CA1400: i Punti di ingresso P-Invoke devono esistere'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 125a9d93085cd82e32dd08a053fdaa98cc1af5cf
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: I punti di ingresso P/Invoke devono esistere
|||
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|Category|Microsoft.Interoperability|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un metodo pubblico o protetto è contrassegnato con il <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Non è possibile individuare la libreria non gestita né associare il metodo a una funzione nella libreria. Se non è possibile trovare il nome del metodo esattamente come specificato, la ricerca di versioni ANSI o caratteri "wide" del metodo aggiungendo il nome del metodo con 'A' o 'W'. Se viene trovata alcuna corrispondenza, la regola tenta di individuare una funzione usando il formato del nome di stdcall (_MyMethod@12, dove 12 rappresenta la lunghezza degli argomenti). Se viene trovata alcuna corrispondenza e il nome del metodo inizia con '#', viene cercata la funzione come un riferimento ordinale anziché un riferimento al nome.

## <a name="rule-description"></a>Descrizione della regola
 Nessun controllo in fase di compilazione è disponibile per assicurarsi che i metodi contrassegnati con <xref:System.Runtime.InteropServices.DllImportAttribute> si trovano nella DLL non gestita a cui fa riferimento. Se nessuna funzione con il nome specificato nella libreria o gli argomenti al metodo non corrispondono agli argomenti della funzione, common language runtime genera un'eccezione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, correggere il metodo che presenta il <xref:System.Runtime.InteropServices.DllImportAttribute> attributo. Assicurarsi che la libreria non gestita esista e sia nella stessa directory dell'assembly che contiene il metodo. Se la raccolta è presente e un riferimento corretto, verificare che il nome del metodo, il tipo restituito e la firma dell'argomento corrispondano alla funzione di libreria.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola quando la libreria non gestita è nella stessa directory dell'assembly gestito che vi fa riferimento. Potrebbe essere possibile eliminare un avviso da questa regola nel caso in cui non sia possibile individuare la libreria non gestita.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola. Nessuna funzione denominata `DoSomethingUnmanaged` si verifica in Kernel32.

 [!code-csharp[FxCop.Interoperability.DLLExists#1](../code-quality/codesnippet/CSharp/ca1400-p-invoke-entry-points-should-exist_1.cs)]

## <a name="see-also"></a>Vedere anche
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>