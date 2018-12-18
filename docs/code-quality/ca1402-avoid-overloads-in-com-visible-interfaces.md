---
title: 'CA1402: Evitare gli overload nelle interfacce visibili a COM'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 11c72fa5d64991931dc6c6d2d5506fd73a7cc59f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402: Evitare gli overload nelle interfacce visibili a COM
|||
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|Category|Microsoft.Interoperability|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un modello COM (Component Object) interfaccia ComVisible dichiara i metodi di overload.

## <a name="rule-description"></a>Descrizione della regola
 Quando i metodi sottoposti a overload vengono esposti ai client COM, solo il primo overload di metodo conserva il proprio nome. Gli overload successivi vengono rinominati in modo univoco aggiungendo al nome un carattere di sottolineatura '_' e un numero intero che corrisponde all'ordine di dichiarazione dell'overload. Si consideri ad esempio i metodi seguenti.

```
void SomeMethod(int valueOne);
void SomeMethod(int valueOne, int valueTwo, int valueThree);
void SomeMethod(int valueOne, int valueTwo);
```

 Questi metodi vengono esposti ai client COM come indicato di seguito.

```
void SomeMethod(int valueOne);
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);
void SomeMethod_3(int valueOne, int valueTwo);
```

 I client COM Visual Basic 6 non è possibile implementare i metodi di interfaccia con un carattere di sottolineatura nel nome.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rinominare i metodi di overload, in modo che i nomi siano univoci. In alternativa, rendere l'interfaccia visibile a COM modificando l'accessibilità `internal` (`Friend` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) o tramite l'applicazione di <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> attributo impostato su `false`.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata un'interfaccia che viola la regola e un'interfaccia che soddisfa la regola.

 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA1413: Evitare i campi non pubblici nei tipi valore visibili a COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Evitare i membri statici nei tipi visibili a COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Vedere anche
 [Interoperabilità con codice non gestito](/dotnet/framework/interop/index) [tipo di dati Long](/dotnet/visual-basic/language-reference/data-types/long-data-type)