---
title: 'CA2225: Gli overload degli operatori hanno alternative con nome'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b6e95f73fbb037041aadcc95eb7336a5744ee2d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: Gli overload degli operatori hanno alternative con nome
|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 È stato rilevato un overload di operatore e il metodo alternativo denominato previsto non è stato trovato.

## <a name="rule-description"></a>Descrizione della regola
 Overload di operatori consente l'utilizzo di simboli per rappresentare i calcoli per un tipo. Ad esempio, un tipo che esegue l'overload il simbolo di segno più (+) per l'aggiunta in genere avrebbe un membro alternativo denominato 'Add'. Il membro alternativo denominato fornisce l'accesso per la stessa funzionalità come l'operatore e viene fornito per gli sviluppatori che programmano in linguaggi che non supportano gli operatori di overload.

 Questa regola esamina gli operatori elencati nella tabella seguente.

|C#|Visual Basic|C++|Nome alternativo|
|---------|------------------|-----------|--------------------|
|+ (binario)|+|+ (binario)|Aggiunta|
|+=|+=|+=|Aggiunta|
|&|E|&|BitwiseAnd|
|&=|E =|&=|BitwiseAnd|
|&#124;|Or|&#124;|BitwiseOr|
|&#124;=|O =|&#124;=|BitwiseOr|
|--|N/D|--|Operatore di conversione|
|/|/|/|Dividi|
|/=|/=|/=|Dividi|
|==|=|==|Equals|
|^|Xor|^|Xor|
|^=|Xor =|^=|Xor|
|>|>|>|Compare|
|>=|>=|>=|Compare|
|++|N/D|++|Operatore di incremento|
|<>|!=|Equals|
|<<|<<|<<|LeftShift|
|<<=|<<=|<<=|LeftShift|
|<|<|<|Compare|
|<=|<=|\<=|Compare|
|&&|N/D|&&|LogicalAnd|
|&#124;&#124;|N/D|&#124;&#124;|LogicalOr|
|!|N/D|!|LogicalNot|
|%|Mod|%|Mod o resto|
|%=|N/D|%=|Mod|
|* (binario)|*|*|Per|
|*=|N/D|*=|Per|
|~|non|~|OnesComplement|
|>>|>>|>>|Tasto|
=|N/D|>>=|Tasto|
|-(binario)|-(binario)|-(binario)|Sottrai|
|-=|N/D|-=|Sottrai|
|true|IsTrue|N/D|IsTrue (proprietà)|
|-(unario)|N/D|-|Negare|
|+ (unario)|N/D|+|Plus|
|False|IsFalse|False|IsTrue (proprietà)|

 N/d = = Impossibile eseguire l'overload nella lingua selezionata.

 La regola controlla anche gli operatori di cast impliciti ed espliciti in un tipo (`SomeType`) controllando i metodi denominati `ToSomeType` e `FromSomeType`.

 In c#, quando viene eseguito l'overload di un operatore binario, l'operatore di assegnazione corrispondente, se presente, viene anche in modo implicito l'overload.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare il metodo alternativo per l'operatore. il nome utilizzando il nome alternativo consigliato.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola se si implementa una libreria condivisa. Le applicazioni possono ignorare un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente definisce una struttura che viola questa regola. Per correggere l'esempio, aggiungere un pubblico `Add(int x, int y)` metodo alla struttura.

 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA1046: Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2226: Gli operatori devono avere overload simmetrici](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Eseguire l'override di Equals all'override dell'operatore](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: Eseguire l'override di GetHashCode all'override di Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)